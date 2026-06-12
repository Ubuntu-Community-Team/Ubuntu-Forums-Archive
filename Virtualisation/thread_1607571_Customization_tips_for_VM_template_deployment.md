---
title: "Customization tips for VM template deployment"
date: 2010-10-27
forum: Virtualisation
---

### Post by albertwt on 2010-10-27
Hi Everyone,

I'd like to create a VM template for Ubuntu Linux 10.04  LTS,

what I've done is:

1. install it w/o any software package.
2. configure the proxy
3. set IP to be DHCP
4. make standardize username
5. Install VMware tools

So in order to customize the new VM after it is deployed from the template, do i just initiate:

1. ```
hostname NEW_NAME
```
2. make necessary changes in the IP address using ```
vi /etc/network/interfaces
```
4. ```
sudo apt-get update
```

please let me know if I'm missing something here or this can be automated with better ways.

Thanks

---

