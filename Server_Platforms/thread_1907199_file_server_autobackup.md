---
title: "file server autobackup"
date: 2012-01-10
forum: Server Platforms
---

### Post by homebuddy on 2012-01-10
hi,

I wanted to setup a server wherein it will automatically backup my "shared folders" from my other PCs (i.e. Windows 7 and XP) once I log onto to the server... Is it possible? Can I configure RSYNC to do it? if no what should I use?

I'm doing this so I would not have to backup my wife and kids laptops and PCs every now and then. I want it done automagically and seemlessly on the server side. Thank you so much in advance.

---

### Post by Mia1990 on 2012-01-11
The easiest way to back up your PC's to the file server is to install the back up software on the pc's then just point to the location (that will be your file server) and save the back up there.

---

### Post by Lars Noodén on 2012-01-11
How are the shared folders set up?  Are they on the laptops/desktops or on the server itself?

---

### Post by homebuddy on 2012-01-12
Lars Noodén:

I don't exactly understand what you mean :) But, what I'm planning to do is share my laptop/desktop folders to the server so it can access it and make a backup whenever it detects its presence.

Mia1990:

What you propose is indeed easy but my wife, kids and others may not be that computer savvy and fail to backup their files at least regularly.

---

### Post by Lars Noodén on 2012-01-12
The solution will probably use rsync but the trick there will be to have the server detect the presence of the other computers and to correctly guess which ones.  What kind of services do they connect to on your server, Samba, DHCP, SSHFS?

---

