---
title: "[SOLVED] shared folder problem"
date: 2008-08-26
forum: Virtualisation
---

### Post by dmagett on 2008-08-26
I have Virtual Box installed on Win XP Pro SP3 Host and Ubuntu 8.04 LTS as a guest. I have a shared folder set up (It shows up in Virtual Box as shard folder). I can't seem to get Ubuntu to access it. I am new to Ubuntu. 
Any ideas?

---

### Post by AClark on 2008-08-27
> **dmagett said:**
> I have Virtual Box installed on Win XP Pro SP3 Host and Ubuntu 8.04 LTS as a guest. I have a shared folder set up (It shows up in Virtual Box as shard folder). I can't seem to get Ubuntu to access it. I am new to Ubuntu. 
Any ideas?

From the VirtualBox User Manual:

[U][I]"Then, you can mount the shared folder from inside a VM the same way as you would mount an ordinary network share:

 In a Linuxguest, use the following command:
mount -t vboxsf [-oOPTIONS] sharename mountpoint"[/I][/U]

In other words you access them the same way you would access a Windows share on another computer.  As far as your Linux guest is concerned the shared folder **is** on a different computer.

I don't have any experience using Vbox on a Windows host but with a Linux host and a Windows guest once you have set up the shared folder in Vbox settings for the VM you right click on My Computer in Explorer and Map a network drive just like you would when setting up a normal share in Windows.

I have never had any luck using the GUI in Ubuntu to set up shares.  But have always been able to do it from the command line using a command similar to the one I quoted from the manual.

Sorry I don't have the exact syntax for you - I'm not near any of my Linux machines right now.

From the command line:

man mount 

May help if you aren't familiar with the mount command.

SAMBA is the sytem that deals with Windows shares and is installed by default in Ubuntu but I remember that I recently had to install one more part of it to get Win shares working but I'm not where I can look that up.

There are plenty of threads in the forums on Samba and accessing Windows shares from Ubuntu if you need more help.

Good Luck!

---

### Post by dmagett on 2008-08-27
Thanks, I had tried that and it didn't work. Here is what I did.
I had to make a directory first...
sudo mkdir /mnt/name       (name is subdirectory under mnt)

sudo mount.vboxsf dloads /mnt/name    (dloads is my shared folder in xp)

Making the directory it what helped.

Problem solved.

---

### Post by AClark on 2008-08-27
> **dmagett said:**
> 
sudo mkdir /mnt/name   


Glad your problem is solved.

In linuxspeak I believe it's called "creating a mount point" :)

In case you don't already know, if you create your mount point under /media - Example: /media/sharename

An icon for the share will magically appear on your desktop.

Not always desirable but good to know.

---

### Post by dmagett on 2008-08-27
Thanks, I didn't know.

---

### Post by jhayes on 2008-08-29
what dmagett said is spot on,
thanks so much
new here and now i can see my stuff inside my ubuntu virtualbox

---

