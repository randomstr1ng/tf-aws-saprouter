# SAPRouter Terraform Module 
Terraform Module for SAProuter deployment on AWS Cloud. This terraform deployment will setup a OpenSUSE Leap AWS EC2 Instance will allows to run an SAPRouter.

The routing file will be downloaded from specified location via `routtab-file-url` variable.

# How to use

```terraform
module "saprouter" {
  source = "./modules/saprouter"

  security_group_name = var.srt-security_group_name
  routtab-file-url    = var.routtab-file-url
  ec2_name            = var.saprouter_ec2_name
  vpc-id              = aws_vpc.vpc.id
  keypair-id          = aws_key_pair.key_pair.id
  subnet-id           = aws_subnet.subnet.id
}

# Output
output "saprouter_private_ip" {
  description = "SAPRouter Instance Private IP"
  value = module.saprouter.private_ip
}
```
