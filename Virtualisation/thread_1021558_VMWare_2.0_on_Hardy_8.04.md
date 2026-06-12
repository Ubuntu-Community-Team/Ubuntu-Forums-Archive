---
title: "VMWare 2.0 on Hardy 8.04"
date: 2008-12-25
forum: Virtualisation
---

### Post by jamesdcarroll on 2008-12-25
I'm trying to install VMWare Version 2.0.0 build 122956 on Hardy 8.04.1 (kernal 2.6.24-22-generic/ gcc 4.2.4 (i486-linux-gnu) following the instructions at [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server), but I am getting an error. 

Here's what I did:

**jim@Cheyenne:~$** sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**jim@Cheyenne:~$** sudo apt-get install xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**jim@Cheyenne:~$** cd Programs/VMWare/vmware-server-distrib
**jim@Cheyenne:~/Programs/VMWare/vmware-server-distrib$** . vmware-install.pl
bash: use: command not found
bash: use: command not found
bash: no: command not found
bash: my: command not found
bash: my: command not found
bash: vmware-install.pl: line 25: syntax error near unexpected token `('
bash: vmware-install.pl: line 25: `my @cKernelModules = qw(vmblock vmdesched vmhgfs vmmemctl vmxnet vmci vmmon vmnet);'
**jim@Cheyenne:~/Programs/VMWare/vmware-server-distrib$**

Any ideas on what I'm doing wrong?  It seemed so simple.... 

Thanks!

---

### Post by bodhi.zazen on 2008-12-26
Try this guide : [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

```
sudo ./vmware-install.pl
```

do not forget the . in ./vmware-install.pl

---

