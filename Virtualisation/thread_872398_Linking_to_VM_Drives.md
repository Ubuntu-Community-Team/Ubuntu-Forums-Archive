---
title: "Linking to VM Drives"
date: 2008-07-27
forum: Virtualisation
---

### Post by jsblackmaro on 2008-07-27
Hello all.  I am running HardyHeron, with Virtual Box Vm's.  I have an XP VM ( I need Photoshop!!!) and I was wondering if I could route to the C drive of it in Ubuntu, so I cn grab my pictures.  the VM is stored on an External 250 GB drive so I can keep the file system drive clear..  Is this possible???  I know I can do it between XP and XP.  I used to do that at work!!  HELP!!!

Thanks!

Josh

---

### Post by dmizer on 2008-07-28
A lot of that depends on how you have networking set up.  If you have network bridging enabled, then you simply need to set up a file share from your XP virtual machine which can then be accessed by your Ubuntu host.

---

### Post by jsblackmaro on 2008-07-28
Im not sure if I have a network bridge setup.  I know I shared the folder in Ubuntu, and had to install Samba.  I then went into the XP VM, and did the net use, and also tried to map the drive.  Neither worked.  How can I check if its bridged?  I dont see it on the network page.  Unless Im blind!!  I also have the folder shared in Virtual Box.

---

### Post by bodhi.zazen on 2008-07-28
See if this link helps :

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

