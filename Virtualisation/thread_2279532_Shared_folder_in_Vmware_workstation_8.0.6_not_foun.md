---
title: "Shared folder in Vmware workstation 8.0.6 not found in server 14.04.2"
date: 2015-05-24
forum: Virtualisation
---

### Post by stesosaso on 2015-05-24
Hi,

[Edit :  Forgotten to specify : My computer is running Win 7 Pro x64 and Vmware workstation 8.0.6 where Ubuntu Server 14.04.2 is virtualized]

I have tried installing VMware tools : no succes
I have tried installing open-vm-tools ans open-vm-dkms
but the following command : 
```
sudo mount -t vmhgfs .host:/VM_partage /mnt/VM_partage
```
returns me the following error :
```
Error: cannot mount filesystem: No such device
```

What am I doing wrong ?

/mnt/VM_partage is created
the folder VM_partage is declared in the virtual machine settings (shared folder set to "always enabled")

the command ```
vmware-hgfsclient
``` returns me the right folder...

have no clue about whats going on here...

if somebody has an idea, or needs more informations, i'll be happy to read you
Many Thanks in advance for your help and advise,

Please excuse my English as it is not my mother language, I am French.

---

### Post by stesosaso on 2015-05-30
Nobody has any idea ? even a little one ? just a point where starting searching...

---

