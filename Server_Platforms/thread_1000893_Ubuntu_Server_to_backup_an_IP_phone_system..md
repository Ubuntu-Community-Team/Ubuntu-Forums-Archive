---
title: "Ubuntu Server to backup an IP phone system."
date: 2008-12-03
forum: Server Platforms
---

### Post by boogiepop88 on 2008-12-03
Hello all,


I need your help. I'm looking at creating an Ubuntu Server to solely backup our phone system and help out our Telecommunications Specialist. We have about 2 Terabytes that we need to back up. (Main system server, backup server system, and all subsystems.) Our layout here is primarily Microsoft, and using Symantec BackupExec to our only 3TB SANS is not an option, as our exchange backups, NAS, mission critical databases are housed for backup there. We are also on a budget crunch, so i think Open Source will be the way to go for us. Which leads to my question, what is the best backup suite any of you could suggest? Our phone system is a custom built *nix system running on a custom image of RHEL4 on top of a VMWare ESX Server. I have a small VM instance of Ubuntu Server 8.04 running that i am testing using Webmin. I've looked at the backup system that is in place now, but i believe i will need more. There are a total of maybe 20 HDD's that need backed up to a restorable image.  I've looked at a couple Amanda, Mondo, to name a few, but i always have recieved great advice from everyone here at UF.org. I am by no means to the engineer level in Linux but I am completely comfortable on the command line and have years of experience .  I was hoping to have something that Webmin could interpret as I need to train out to our Telecommunications Specialist as well, his knowledge of the Linux is very slight at best. If i can get this system up in our 1000$ budget i could be looking at being our first Linux Administrator, and implementing more low TCO open source options. So any ideas would be great. Thanks!

---

### Post by Dr Small on 2008-12-03
What are you doing, recording phone conversations?

---

### Post by boogiepop88 on 2008-12-03
Well the IP system we have now we do record calls and voice mails which is done within the system and stored locally within the system for our Quality Assurance people to use.  Basically I'm looking to do Full+ Incrimentals as well as be able to snapshot. As to why it is so huge, im not really sure. We have the main system as well as a failsafe backup system. Which as finicky as the vendors are about doing updates and code-mods to their own system, a backup is something we want to have for complete disaster.

Thanks for the reply!

---

### Post by boogiepop88 on 2008-12-04
/bump   [-o<

---

