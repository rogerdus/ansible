# Ansible

This is Ansible's repository!

Below it's the main structure

```bash
ansible-project/
│── inventories/
│   ├── test.ini
│── group_vars/
│── roles/
│── playbooks/
│   ├── install_cert.yml
│── ansible.cfg
│── requirements.yml
```
# In this structure you can found:

    inventories/ → Contain diferents inventories (production.ini, staging.ini).
    group_vars/ → variables for diferents servers.
    roles/ →  Module Roles for specific task .
    playbooks/ → Playbooks calling main roles.
    ansible.cfg → Ansible's configuration.
    requirements.yml → Dependencies of roles.

# Steps before start

* First of all you should create a public key for authentication with:

    ```bash
    ssh-keygen -t ed25519 -C "ansible"
    ```

* You should adding the ssh keys to each server for manage it with ansible
    ```bash
    ssh-copy-id -i ~/.ssh/ansible.pub user@ip_address
    ```
* Maybe before run either playbook, test your inventory
    ```
    ansible all --key-file ~/.ssh/ansible -i inventories/file.ini -m ping
    ```

# Run playbook


```bash
 ansible-playbook --ask-become-pass -i inventories/dev.ini playbooks/install_cert.yml
```