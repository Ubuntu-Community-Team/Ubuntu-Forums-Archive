---
title: "Cant install VMware Server 2 on Ubuntu server 64-bit"
date: 2011-07-21
forum: Virtualisation
---

### Post by GOSSSAMER on 2011-07-21
I was able to before but for some reason cant get it to work now.
 
My setup:
Ubuntu 10.10 64-bit server
UFW port 22 open for SSH
a static address
 
I was able to get it working using these instructions in the past:
 
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35)
 
Ive done this setup successfully several times; however when I try to do it now it doesnt work. 
 
I've also tried these instructions with no luck at all:
 
[http://radu.cotescu.com/vmware-server-kernel-2-6-38/](http://radu.cotescu.com/vmware-server-kernel-2-6-38/)
 
I simply want an Ubuntu 10.10 64-bit server running VMware Server 2. 
 
I also tried with version 10.04 LTS 64-bit but got the same error:
 
The error:
You have VMware Server archive: 
VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.35-28-generic package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmci module
Found .tar file for vmmon-temp module
Found .tar file for vmnet-temp module
Found .tar file for vmmon module
Found .tar file for vsock module
Found .tar file for vmci-temp module
Found .tar file for vsock-temp module
Found .tar file for vmnet module
Extracting .tar files in order to apply the patch...
Untarring /home/arsh/Downloads/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/arsh/Downloads/vmware-server-distrib/lib/modules/source/vmmon-temp.tar
vmmon-temp.tar tarball failed to extract in the directory vmmon-temp-only.
 
 
I'm also tempted to see if I can get it to work in 11.04 Server.
 
Please help

---

### Post by wazhapen on 2011-07-23
I'm currently running Ubuntu server 64-bit and successfully installed VMWare Server 2. I have been able to use these instructions to install VMWare Server on both 10.10 and now 11.04 Natty. Try this below and let me know if it works for you...

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35-p2](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35-p2)

---

### Post by GOSSSAMER on 2011-07-24
> **wazhapen said:**
> I'm currently running Ubuntu server 64-bit and successfully installed VMWare Server 2. I have been able to use these instructions to install VMWare Server on both 10.10 and now 11.04 Natty. Try this below and let me know if it works for you...
 
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35-p2](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35-p2)
 
 
Many Thanks.  That worked with no issues at all.  
 
I did a clean Ubuntu Server 11.04 64-bit install and followed the instructions in your link and it works like a charm.  
 
Thanks Wazhapen

---

