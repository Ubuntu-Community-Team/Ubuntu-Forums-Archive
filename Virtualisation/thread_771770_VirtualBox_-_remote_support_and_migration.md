---
title: "VirtualBox - remote support and migration"
date: 2008-04-27
forum: Virtualisation
---

### Post by amorangi on 2008-04-27
I'm suffering the 6 monthly pain of dealing with VMware upgrades due to Ubuntu upgrades. Currently I use VMware server on my server, and use the remote console on my laptop and main PC to use the VMs. I mainly use it for desktop application purposes. However I'm getting tired of the hassles so I am considering a switch to Virtualbox.

Am I able to run Virtualbox VMs from a remote machine? 

Is there a way to transfer a VMware VM to Virtualbox without a great deal of hassle?

---

### Post by amorangi on 2008-04-28
Reply to my own questions here. Migration instructions are:

```
wget http://www.virtualbox.org/download/testcase/vditool
chmod +x vditool
mv vditool /usr/local/bin/
qemu-img convert -f vmdk vmachine.vmdk -O raw vmachine.img
/usr/local/bin/vditool DD vmachine.vdi vmachine.img
```

However I can't get the vditool to run - ldd vdtool has  ```
libuuid.so.1 => not found
```

However libuuid1 is installed according to synaptic. What can  do to get this dependency?

---

### Post by tuneable on 2008-05-07
Just had the same problem. Solved it by installing the lib32 version of liuuid1. 

The .deb for "libuuid1" for "i368" can be found [with the package search]("http://packages.ubuntu.com/hardy/libuuid1"). I then used "dpkg-deb -x <file>" to extract the content of the .deb and moved files in the extracted lib/ directory to /lib32/.

---

