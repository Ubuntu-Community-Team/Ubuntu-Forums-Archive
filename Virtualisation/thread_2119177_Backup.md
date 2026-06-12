---
title: "Backup"
date: 2013-02-23
forum: Virtualisation
---

### Post by slkamath on 2013-02-23
Hi,

How to setup automated Backup in Ubuntu? (i.e. when user click on the shut down button it starts backup and after that it has to shut down).

Can anyone tell me which software I need to install?

Thanks in advance.

Regards

Lokesh Kamath

---

### Post by satyamM on 2013-02-24
I too need this. But I doubt if this is possible easily. Expert advice needed.

---

### Post by lmarmisa on 2013-02-24
> **slkamath said:**
> Hi,

How to setup automated Backup in Ubuntu? (i.e. when user click on the shut down button it starts backup and after that it has to shut down).

Can anyone tell me which software I need to install?

Thanks in advance.

Regards

Lokesh Kamath

The procedure you are proposing is very difficult and perhaps not reliable.

I  recommend a very simple backup procedure for any Ubuntu virtual machine. 

Backup the entire folder of you virtual machine after the shutdown of the VM. This folder will contain the virtual disk(s) file(s). You have to make this  backup on host computer, of course and when the VM is stopped.

In the case of VirtualBox, if you wish to know where the folder containing the VMs is located, open VB menu and then select File -> Preferences -> Default Machine Folder.

I recommend two tools for backups.

If you host is a Ubuntu system, you can use the command rsync:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

If your host is a Windows computer, I recommend the program SyncBack Free:

[http://download.cnet.com/SyncBackFree/3000-2242_4-10413802.html](http://download.cnet.com/SyncBackFree/3000-2242_4-10413802.html)

---

### Post by slkamath on 2013-03-04
Thanks for your information.

But I am running backup in normal ubuntu machine. We have nearly 63+desktop's(not vm's). Each and every user not puttingsystem for backup every single day also it's difficult for me to go to all the system and take a backup. So I need solution for this. Do you have any alternate solution for this??


Thanks in advance.

Regards

Lokesh Kamath

---

