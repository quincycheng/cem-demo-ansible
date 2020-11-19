# CEM Demo Setup 
Setting up CEM demo on cloud platforms using Ansible

## What resources & operations will be created?
### AWS 
- Standard Demo Resources
   - 4 Users (Mike, John, Robert & YOURSELF) will be created
   - 2 Groups (Developers & Admins)
   - 1 IAM Role
   - 1 SAML Provider
   - 1 IDP Role 
   - 1 S3 Bucket Policy
   - 1 S3 Bucket

- Operation
   - Robert
     - Create a dummy policy
     - List S3 buckets

## Prerequisite
1. Download this repo
2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html)
3. Install collections by executing `ansible-galaxy collection install -r config/requirement.yml`

## Setup Demo on AWS
1. Create a pair of access-key & secret key if you don't have one
2. Set the environment for AWS

   - CLI
```
export AWS_ACCESS_KEY_ID=[Your AWS Access Key]
export AWS_SECRET_ACCESS_KEY=[Your AWS Secret Key]
```
    - Summon
      Please refer to https://github.com/cyberark/summon to prepare `secrets.yml`

3. Copy `config/cem-sample.config` as `config/cem.config` and update the configurations
   The variables should be self-explanatory.
```
AWS_YOURSELF: REPLACE-YOUR-NAME-HERE
AWS_ACCOUNT_NO: 123456789012

AWS_SAML_PROVIDER_NAME: CYBR-DUMMY-IDP
AWS_SAML_PROVIDER_METADATA: dummy-idp-metadata.xml
```
4. Setup the demo environment on AWS 
   - CLI: Execute `ansible-playbook aws/aws-setup.yml` 
   - Summon: Execute `summon ansible-playbook aws/aws-setup.yml` 

## Clean up Demo on AWS
  - CLI: Execute `ansible-playbook aws/aws-cleanup.yml` to remove the demo environment on AWS.   
  - Summon: Execute `summon ansible-playbook aws/aws-cleanup.yml` to remove the demo environment on AWS.   

## Tips
### Ansible
1. Set `export ANSIBLE_NOCOWS=1` to disable the cows 
2. Set `export ANSIBLE_COW_SELECTION=random` to have more drawings than cows 
