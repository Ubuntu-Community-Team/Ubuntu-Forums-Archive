---
title: "esxi mounted drives"
date: 2011-06-26
forum: Server Platforms
---

### Post by thetopcat2010 on 2011-06-26
Hi all 
May I say thanks for all the help I can have on this...
 
I have ESXI 4.1 installed with Unbuntu Server 11.04, Gnome.
 
I have 8 SATA drives installed they show up in unbuntu as removable media
 
I wish to share them to my windows users on my lan using samba.
 
The problem is it will not allow me to change the permissions for the shares and as such when my windows clients try to access the shares they are told asscess denied.
 
Samba will share folders created on my desktop ok, I have tryed sharing a folder in the draws but it still did not work.
 
Many Thanks
IAN

---

### Post by spynappels on 2011-06-27
Is Ubuntu installed on top of ESXi as a VM?
Does normal networking work fine, ping, net access, etc.?

---

### Post by thetopcat2010 on 2011-06-28
Yes unbuntu is installed as a VM on ESXI and yes Networking all works ok Ping WWW ect it even works if I create a draw on the desktop and share that it just does not work when shareing a removable media drive, This is the classification it gives sata drives with in the server box.

---

### Post by rubylaser on 2011-06-28
Are you using passthrough for the hard drives from your ESXi host to the Ubuntu VM, or are these hard drives shared to it via NFS/ISCSI from another host?  An fdisk -l could be helpful for use to see.  Also, what do you have in your /etc/samba/smb.conf file, and what are the permissions on the directories you're trying to share?

---

### Post by tgalati4 on 2011-06-28
In Ubuntu, open a terminal and post the output of:

sudo fdisk -l
cat /etc/fstab
cat /etc/mtab

and scrub as necessary before posting:

/etc/samba/smb.conf

You might have hit an Ubuntu limitation on how removable drives are handled. Normally you would set up a large NAS or SAN with your disk drives in a separate enclosure and then set up drive (NAS or SAN) mounts on each VM.  The array NAS or SAN operating system handles the permissions.  It's not normal to allow one VM to control the drive shares because whenever that VM goes down or needs restarting, all drive shares are absent until that VM goes live.

I would either use Xen/Citrix hypervisor for this or try [http://freenas.org](http://freenas.org) in a VM and see if that can share the drives properly.

---

