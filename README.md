role-render-rocky10-kickstart-template
=========

Renders kickstart template for a Rocky 10 VM.
Assumed drive patitioning:
- primary drive:
  - no swap
  - all OS files reside on a single parition

Requirements
------------

None

Role Variables
--------------
- `vm_name`: used to name the resulting kickstart file
- `ipv4_addr:` IPv4 addres to be assigned to the VM
- `ipv4_mask:` IPv4 network mask to be assigned to the VM
- `ipv4_gate:` IPv4 gateway to be assigned to the VM
- `extra_drive:` whether extra virtual drive will be provisioned
- `default_user:` default user account to be created for provisioned VM
- `default_user_password_hash`: Linux password hash for default user
- `default_user_ssh_pubkey`: key to add to `~/.ssh/authorized_keys` 
- `default_user_can_sudo_without_password:` yes/no (self explanatory)
- `secondary_drive_size_gb:` size of extra drive (if provisioned)
- `kickstart_output_directory:` kickstart template is rendered here


Dependencies
------------

None

Example Playbook
----------------

```yaml
- name: Render Kickstart Templates
  become: false
  gather_facts: false
  
  roles:
  - role: role-render-rocky10-kickstart-template
    vars:
      vm_name: my-rocky-vm
      ipv4_addr: 192.168.1.2
      ipv4_mask: 255.255.255.0
      ipv4_gate: 192.168.1.1
      default_user: admin
      default_user_ssh_pubkey: "$6$salt$hash"
      default_user_can_sudo_without_password: true
      kickstart_output_directory: /path/to/kickstart/directory
```


License
-------

BSD

Author Information
------------------

https://vlads.tech
---
