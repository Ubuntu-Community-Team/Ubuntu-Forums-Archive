---
title: "Simple sharing frustration"
date: 2010-05-25
forum: Ubuntu Moblin Remix
---

### Post by rymar115 on 2010-05-25
This may seem like a dumb question, however here it is...how do I do simple file sharing between my netbook running 10.4 netbook version and a desktop running 10.4? The desktop has a number of files on it I would like to be able to have access to.The shares are working on the desktop because I can access them via a windows computer. Seems odd that it's easier to share files with Windows that with another Ubuntu machine.

---

### Post by VastOne on 2010-05-25
> **rymar115 said:**
> This may seem like a dumb question, however here it is...how do I do simple file sharing between my netbook running 10.4 netbook version and a desktop running 10.4? The desktop has a number of files on it I would like to be able to have access to.The shares are working on the desktop because I can access them via a windows computer. Seems odd that it's easier to share files with Windows that with another Ubuntu machine.

Right click on any folder or file and select sharing options.  First time through it will install the needed packages to get you going...

---

### Post by Thomas Garman on 2010-05-25
The previous poster is correct except that there is a bug in 10.04 that will not really allow the share to work.  Install Samba and then you have to also install from synaptic:
 
apache2.2-bin
libapache2-mod-dnssd
 
Google "Sharing does not work with Ubuntu 10.04" and you will find all of the various bug reports that will tell you that you need the packages above.

---

### Post by VastOne on 2010-05-25
> **Thomas Garman said:**
> The previous poster is correct except that there is a bug in 10.04 that will not really allow the share to work.  Install Samba and then you have to also install from synaptic:
 
apache2.2-bin
libapache2-mod-dnssd
 
Google "Sharing does not work with Ubuntu 10.04" and you will find all of the various bug reports that will tell you that you need the packages above.

I saw this in many threads as well, but I have setup 10+ Lucid machines with sharing and have yet to run into this issue. I do not know why I have not and just wanted to point it out....

Well done for letting the OP know about it...

Personally I like ssh ...

---

### Post by cariboo on 2010-05-26
I'm with VastOne, sharing didn't work properly during the Lucid testing cycle, but it has been fixed, and I have no problem accessing shared files on other systems. I use a combination of NFS for sharing with other Linux based systems and samba for sharing with Windows systems.

---

### Post by rymar115 on 2010-09-21
I have enabled sharing to work using ssh, however it shows my entire file system on the desktop computer which is not what I really want. I would like to be able to share just the folders I have designated. I'll keep picking away at it until it does work

---

### Post by luvshines on 2010-09-22
I have recently shifted to Ubuntu from Fedora and didn't get a chance to try Samba sharing on Ubuntu

But, IMHO 'nfs' can be a much simpler option for folder/files sharing between Linux machines

---

