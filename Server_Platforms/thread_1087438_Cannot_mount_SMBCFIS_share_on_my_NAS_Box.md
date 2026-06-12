---
title: "Cannot mount SMB/CFIS share on my NAS Box"
date: 2009-03-05
forum: Server Platforms
---

### Post by quinnteq on 2009-03-05
Ok, so I'm trying to get my Linux Server with Torrentflux installed on it to mount a SMB/CIFS share on my FreeNAS box. It wont mount. I use the command

> sudo mount.smbfs //192.168.1.250/Archive /home/quinton/torrents -o username=quinton,password=mypass
The output is as follows...

> [36896.941130] CFIS  VFS: Send error in SessSetup=-13
[36896.941214] CFIS VFS: cifs_mount failed w/return code=-13
mount error 13= Permission  Denied
 

I dunno what im doing wrong, the UIDs of the users match on both machines, i am using hte correct password (at first it gave me errors saying it was too long, so i changed it) I  have read that there are bugs in the recent kernel that can cause this, but I dunno what to try as a work around.   I  did read that you have to add a domain to it, but what do i use as my domain? I'm on a home network. I used MSHOME, and mshome at the end after password "...password=mypass,domain=MSHOME..." things of that nature. It still gives me a permission denied error... I dont know what to do! Please, anyone with suggestions on where to go it would be GREATLY  appreciated. I worked on this for like three hours today and found no solution. All i want to do is mount a SMB/CFIS  Share on Ubuntu linux server edition.

Here is my system specs for the machine im using:

Linux kernel 2.6.27-11-server
Ubuntu Server Intrepid Ibex
10GB HDD
AMD  Duron Processor
128MB  Memory

---

### Post by capscrew on 2009-03-05
Make sure you have smbfs installed

```
sudo apt-get install smbfs
```

Use this format to mount the share.```
sudo mount -t cifs //192.168.1.250/Archive /home/quinton/torrents -o username=quinton,password=mypass 
```

---

### Post by quinnteq on 2009-03-05
Ok, tried your suggestions. Plus changed the permissions around (thinking maybe there was somthing set wrong)... then back again, still no go. Same error.

---

### Post by capscrew on 2009-03-05
What perms did you change?

---

### Post by quinnteq on 2009-03-05
I tried changing the remote user on the FreeNAS box to different user groups, then back, still no luck.

I dont get why it doesnt work in the server edition, it works just fine in gnome with abslutely no added configuration. Here though, i dont need a desktop, so doing it though the command line is the only option.

---

### Post by capscrew on 2009-03-05
> **quinnteq said:**
> I tried changing the remote user on the FreeNAS box to different user groups, then back, still no luck.

I dont get why it doesnt work in the server edition, it works just fine in gnome with abslutely no added configuration. Here though, i dont need a desktop, so doing it though the command line is the only option.

Gnome uses different libs (gvfs) talk to the NAS.  I'm not sure how to overcome this situation.  What is happening is the request for auth is being ignored.

The OS you are using does not have anyway to form the request as the NAS is expecting it to.  You may have to config the NAS to speak smbfs for it to work.

---

### Post by Hamster1910 on 2009-03-06
What version of smbfs do you have?

Try upgrading Samba-common, smbclient & libsmbclient to 3:2.3.2-1ubuntu3.5 
(See intrepid-proposed & intrepid-backports sources).

Also try adding 'nounix' option to your mount command.

These fixed my problems mounting shares on a LANdisk NAS after I upgraded from Hardy to Intrepid

---

### Post by quinnteq on 2009-03-06
Sorry about the delay, work and job interviews.

Alrighty... Ill give that a try...

How would you go about updating those? (kinda just gettin my feet wet in a pure CLI)

Ill try adding the "nounix" switch to that... but the NAS box i have is FreeBSD based, its actually a FreeNAS box.
[http://freenas.org/](http://freenas.org/)
Thats their site...

Ok gunna give these a shot... let ya know how it works out.

---

### Post by Hamster1910 on 2009-03-07
I am a relative noob myself and have learned loads in the last couple of weeks, (i.e. since I upgraded Hardy to Intrepid) and hit problems. I have got most information from the Ubuntu forums and worked out the missing bits by experimenting.

I am not sure how to get the proposed and backport repositories with CLI as I used Synaptic GUI on Gnome. Perhaps a trawl on the forums will help?
This looks promising....
[https://help.ubuntu.com/community/UbuntuBackports#Installing%20a%20single%20package]("https://help.ubuntu.com/community/UbuntuBackports#Installing%20a%20single%20package")

I noticed you were using FreeNAS and wondered why you want to use SMB/CIFS to connect it to Ubuntu.

Samba was designed to get Linux to operate with Windows smb protocol. I gather the *proper* way to connect Linux to Linux is using NFS. (I saw someone saying connecting Linux to Linux with smb is like getting two native English speakers to communicate in French which seems like a good analogy)
However, I have no experience of NFS so suggest you trawl the forums for more advice.(I have only connected smb shares as my NAS box only supports smb or FTP).

Incidentally I was playing around yesterday mounting smb shares with Hardy by adding to fstab. I found I need the nounix option for that too, although Nautilus mounts no problem. As I had to install smbfs, I'm guessing Nautilus is using gvfs. I used the standard LTS supported version of smbfs and it works fine proving this is an Intrepid issue.

---

### Post by quinnteq on 2009-03-10
Ok, so now that I know not to use SMB/CIFS, and I have installed the NFS client stuff using this tutorial... [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)

Now, I use the command 

sudo mount 192.168.1.250:/Torrents /home/quinton/torrents

All i get is:

mount.nfs: internal error

what can i do to fix that? Is there a permission error i dont know about?

---

### Post by Hamster1910 on 2009-03-11
Hmmm, as I said, I'm not familiar with NFS. Although looking around the forums others have had this problem.
One suggestion is to try adding port=2049 to your mount options.

Did you try smb with the updated files?

---

### Post by ssammy on 2009-04-14
Try this 

[http://www.blowyouros.com/2009/04/how-to-mount-your-lacie-ethernet-mini-to-ubuntu-server/](http://www.blowyouros.com/2009/04/how-to-mount-your-lacie-ethernet-mini-to-ubuntu-server/)

---

