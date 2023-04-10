# Links

## Registry

https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance


### Important Note

Note that every region has a different AMI ID. The AMI ID's keeps on changing so make sure you use the latest AMI ID from the AWS console similar to the way it is shown in the video.

### Documentation Referred:

https://registry.terraform.io/

https://registry.terraform.io/providers/hashicorp/aws/latest/docs

### first_ec2.tf

```sh
provider "aws" {
  region     = "us-west-2"
  access_key = "PUT-YOUR-ACCESS-KEY-HERE"
  secret_key = "PUT-YOUR-SECRET-KEY-HERE"
}

resource "aws_instance" "myec2" {
   ami = "ami-082b5a644766e0e6f"
   instance_type = "t2.micro"
}
```
### Commands:

```sh
terraform init
terraform plan
terraform apply
```

### GIT HUB PROVIDER

```tf
terraform {
  required_providers {
    github = {
      source  = "integrations/github"
      version = "~> 5.0"
    }
  }
}

# Configure the GitHub Provider
provider "github" {
  token = "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"
}  

```

### Terraform Destroy

```tf
## Destruir tudo
terraform destroy

terraform destroy -target 

## Example target destroy
terraform destroy -target aws_instance.myec2

```

![image](https://user-images.githubusercontent.com/91738714/230953978-35c60193-c21a-4276-9ec4-d324b7e7d087.png)

### TFSTATE
Tfstate file contem todo o estado do que foi aplicado via terraform. Este arquivo possui todos os detalhes do que foi deployado, se ele for perdido sua automação ficará quebrada.É importante ter um backup desse arquivo para ambientes produtivos aprovsionados.

### Refresh

terraform refresh

Este comando atualiza informações com o tfstate quando uma alteração é realizada de forma manual no ambiente. Por exemplo, vc tem uma instância tipo t2.micro e precisa aumentar os recursos desta. Ao invés de aumentar via terraform, vc aumentou o recurso via AWS console. 

Para sincronizar esta alteração com o tfstate é necessário rodar o (terraform refresh) do contrário ao utilizar o terraform novamente esta alteração será revertida para o desired state.
