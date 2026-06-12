---
title: "Installing VMware Tools on Ubuntu Server 7.10"
date: 2007-12-07
forum: Virtualisation
---

### Post by markerman on 2007-12-07
Here are the steps I took....
    
   sudo aptitude update  (Successful)

    sudo aptitude install build-essential linux-headers-$(uname -r) (Successfull)

Click the VM/Install VMware Tools menu item in VMware Server, got VMware Server notice "Installing the VMware Tools package will greatly enhance graphics and mouse performance in your virtual machine."  Clicked "Install"

Ran the below command....

    cp -a /media/cdrom/VMwareTools* /tmp/ (Fails with error - cp: cannot stat `/media/cdrom/VMwareTools*': No such file or directory)

I cd into the cdrom and there is nothing there. I tried it with the CD set to the host, same thing. I tried it with the cdrom disconnected. It was reconnected after clicking "VM/Install VMware Tools" 

Can anyone help?

Thanks.

---

### Post by bodhi.zazen on 2007-12-07
You may need to manually mount the cdrom 

See if this link helps at all :

[https://help.ubuntu.com/community/VMware/Tools#head-a1b3ae21647c7e747a61cbcb1ac2358351cc1f6a](https://help.ubuntu.com/community/VMware/Tools#head-a1b3ae21647c7e747a61cbcb1ac2358351cc1f6a)

---

### Post by javierfh on 2008-02-26
Hi,

i have the same problem as the first poster here and i have tried the second link but still nothing.
Does anyone know where i can get these files that i need to copy to the temp directory?
In my case the Cd/DVD appears monted in the ui, but then in practice it is empty.

any ideas would be more than appreciated :D

Javi

---

### Post by javierfh on 2008-02-26
this got solved...
i rebooted the machine and there there was.
So now should be fixed.

Javi

---

