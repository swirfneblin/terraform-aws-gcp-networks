# Automated Network Deployment: Multicloud VPN - GCP-AWS VPN

Disclaimer: This is not an official Google product.

Demonstration of Terraform for automated deployment of network infrastructure in
both Google Cloud Platform (GCP) and Amazon Web Services (AWS). This is a
multi-cloud VPN setup.

## Quick Start

### Download project

```
curl -O https://storage.googleapis.com/bootcamp-gcp-public/hands-on-tcb-bmc-gcp.zip
unzip hands-on-tcb-bmc-gcp.zip
rm hands-on-tcb-bmc-gcp.zip
cd hands-on-tcb-bmc-gcp
chmod +x \*.sh
```

### Set vars on clouds GCP e AWS

The requirements to set those credentials are create keys on GCP and AWS, so saving on respective files

```
./gcp_set_credentials.sh gcp-serviceaccount-key.json
./aws_set_credentials.sh tcb-aws-gcp-automation_accessKeys.csv
```

### Configure GCP project

```
gcloud config set project [NAME_YOUR_PROJECT]
./gcp_set_project.sh
```

### Create ssh keys

```
ssh-keygen -t rsa -f ~/.ssh/vm-ssh-key -C username
```

### Set permissions

```
chmod 400 ~/.ssh/vm-ssh-key
```

### Configure CGP key

```
gcloud compute config-ssh --ssh-key-file=~/.ssh/vm-ssh-key
```

### Configure AWS Key

```
Import your key inside AWS ssh Keys
```

### Terraform commands

```
terraform init
terraform validate
terraform plan
terraform apply

# To destroy all resources
terraform destroy
```

## References

- [GCP Cloud VPN Overview](https://cloud.google.com/compute/docs/vpn/overview)
- [GCP Creating a
  VPN](https://cloud.google.com/compute/docs/vpn/creating-vpns)
- [GCP VPN Interoperability
  Guides](https://cloud.google.com/compute/docs/vpn/interop-guides)
- [AWS VPN
  Connections](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpn-connections.html)

## License

Copyright 2017 Google Inc.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this file except in compliance with the License. You may obtain a copy of the
License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed
under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.
