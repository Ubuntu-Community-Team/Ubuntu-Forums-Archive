---
title: "Setting up server share"
date: 2008-05-09
forum: Server Platforms
---

### Post by Geekboy on 2008-05-09
Can someone point me to a HowTo for setting up a network share?  

I have a Hardy Heron server and a Gutsy Pc.  I want to share a folder so that I can transfer my Gutsy Home folder to the network (I want to upgrade the PC :)).  

I'll do either a NFS or a Samba share (samba preferably), which ever is easier.

I need to warn you,  I need help with the whole process.  I'm a Windows Server admin, but I'm totally lost with Linux servers.  I tried setting up Samba, and when I browse the network I do see a folder but I get an error message.  It states : The Folder contents could not be displayed and that Perhaps it has recently been deleted.

---

### Post by diaa on 2008-05-09
How about this?
[Samba: How to share files for your LAN without user/password]("http://www.debuntu.org/guest-file-sharing-with-samba")

---

### Post by Geekboy on 2008-05-13
I just reinstalled my server (actually I wanted a clean version of Hardy) and I still can not figure out how to share a folder from the Command Line.  

I currently have a fresh install of Hardy with only the LAMP and SAMBA options chosen.  I also installed SSH so that I could remotely admin the box.

I really only want to share out some space so that I can back up my PC.  Is there any walkthroughs on how to do this at the command line?

---

### Post by scxtt on 2008-05-13
edit /etc/samba/smb.conf and add something like this:

[<name of share>]
path = <path to share>
available = yes
browsable = yes
public = yes
writable = yes

anything in <> is a variable and needs to have a value inserted ...

then restart samba.

---

