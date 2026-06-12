---
title: "Share folders with Windows"
date: 2010-09-03
forum: Server Platforms
---

### Post by Breindahl on 2010-09-03
Hello all, i am new at this forum and this is my first thread, so be friendly, thanks.
 
I have been through a lot of sites and googled allmost everything to get an answer about sharing folders on a Ubuntu Server with Windows clients.
 
Every site tells me, that the only way to get from windows to the shared folders on a ubuntu server, is by using some extra software, installed on the windows machine.
Is this correct?

---

### Post by Smart Viking on 2010-09-03
Hello. It is kinda true, it is normal to install linux on ext file system, and windows(obviously) cannot read ext file system by default.

But you can also install linux on NTFS file system(same as windows uses) and windows would be able to read it, however i don't know how compitable linux is with NTFS, should not be a problem though.
:)

---

### Post by pricetech on 2010-09-03
No.  I don't know where your getting your information from but it's incorrect.

What you need is Samba running on your Ubuntu box.  If your using a Desktop version, or have a desktop installed on the server version:
System - Administration - Synaptic Package Manager
Search for system-config-samba which will install Samba and a GUI configuration tool.

If you don't have a desktop installed, you should probably install one to help you along until you get used to the command line.

---

### Post by pricetech on 2010-09-03
> **Smart Viking said:**
> Hello. It is kinda true, it is normal to install linux on ext file system, and windows(obviously) cannot read ext file system by default.

But you can also install linux on NTFS file system(same as windows uses) and windows would be able to read it, however i don't know how compitable linux is with NTFS, should not be a problem though.
:)

One of us is reading wrong.

OP: are you talking about windows accessing files over the network ??  That's how I'm reading it.

---

### Post by Breindahl on 2010-09-03
Hi Viking
 
I added 2 threads for a minute ago and you helped me with both in no time at all, thank you so much. :D

---

### Post by Morbius1 on 2010-09-03
To further complicate the issue you could have been hanging around with the NFS crowd. Then you would in fact need to bolt something onto the Windows machine to get that to work. 

I know very little about NFS so please don't ask me any follow-up questions.:p

---

### Post by Breindahl on 2010-09-03
Well, I want to create a networkfolder on my Vistamachine, that connects to my Ubuntu Server. The networkfolder should show me the inside of the shared folder on the ubuntu server.
 
I hope you will understand my way of describing the problem.

---

### Post by pricetech on 2010-09-03
Unless there's something I don't know about, you can only map a drive, not a folder.  For this  you'll use the "net use" command, or you can go to Tools - Map Network Drive in Windows Explorer.

Either way you'll still need Samba working on your Ubuntu box.

---

### Post by Smart Viking on 2010-09-03
> **pricetech said:**
> One of us is reading wrong.

OP: are you talking about windows accessing files over the network ??  That's how I'm reading it.

Yeah i guess i was the one reading wrong. :P

---

