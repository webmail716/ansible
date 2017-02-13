####Setup instructions for Ansible (w/VirtualBox VM)

To install ansible:
```
brew install ansible
```
To start (and provision) VM:
```
vagrant up
```
To reboot the VM:
```
vagrant reload
```

To ssh into the VM:
```
vagrant ssh
```

To see ssh info for the VM (identity file location, etc):
```
vagrant ssh-config
```

To install an ansible role (see install_roles.sh):
```
ansible-galaxy install <role>
```
To edit passwords in the vault file:
```
ansible-vault edit vault.yml
```
**Note:** Before running load_db.yml, copy a database backup file (.bz2) to the files folder and remove any older copies.

####All steps to set up a VM:
```
brew install ansible
./install_roles.sh
vagrant up
ansible-playbook -i hosts provision.yml --vault-password-file ~/.vault_pass.webmail716.txt
ansible-playbook -i hosts load_db.yml --vault-password-file ~/.vault_pass.webmail716.txt
ansible-playbook -i hosts deploy.yml --vault-password-file ~/.vault_pass.webmail716.txt
```
