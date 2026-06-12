---
title: "network config (static IP) via cloud-init"
date: 2020-02-22
forum: Virtualisation
---

### Post by wintermute000 on 2020-02-22
I've googled this to hell and back and attempted to read the official cloud-init documentation but no dice... (the documentation is ALL OVER THE PLACE)

I'm simply trying to set a static IP via cloud-init for KVM. The objective is to be able to dish out static IPs for cloned VMs in a scripted fashion without using DHCP / MAC reservations. 

I'm starting with a VM which I clone after issuing ```
sudo cloud-init clean.
```

After that I make the ISO and attach it to the CD-ROM.

```
cloud-localds -N network-config.yml xenial-user-data.img user-data.yml
```

meta-data.yml
```
dsmode: local
```

user-data.yml
```
#cloud-config
# Hostname management
preserve_hostname: False
hostname: testvm-linux
fqdn: testvm-linux.xxxxxxxx.com
 
# Setup Users with ssh keys so that I can log in into new machine
users:
    - default
    - name: xxxxxxxx
      groups: ['wheel','sudo']
      shell: /bin/bash
      sudo: ALL=(ALL) ALL
      lock_passwd: False
      passwd: xxxxxxxx
      ssh-authorized-keys:
        - ssh-rsa xxxxxxxxx

# Configure where output will go
output:
  all: ">> /var/log/cloud-init.log"
 
# configure interaction with ssh server
ssh_genkeytypes: ['ed25519', 'rsa']
 
 
# set timezone for VM
timezone: xxx/xxx
 
# Reset network
runcmd:
  - systemctl stop network && systemctl start network


```

network-config.yml
```
version: 2
ethernets:
  ens3:
    addresses:
      - 192.168.0.101/24
    gateway4: 192.168.0.1
    nameservers:
      search: [xxxxxx.com]
      addresses: [8.8.8.8]
```

Just does nothing. I still end up with DHCP and only a single file in /etc/netplan which is 01-network-manager-all.yaml

I've read these threads too and I'm doing all their 'fixes'
[https://gist.github.com/Informatic/0b6b24374b54d09c77b9d25595cdbd47](https://gist.github.com/Informatic/0b6b24374b54d09c77b9d25595cdbd47)
[https://gist.github.com/itzg/2577205f2036f787a2bd876ae458e18e](https://gist.github.com/itzg/2577205f2036f787a2bd876ae458e18e)

What am I doing wrong???

---

