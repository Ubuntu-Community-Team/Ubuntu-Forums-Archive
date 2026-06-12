---
title: "XP crashes with samba"
date: 2007-06-08
forum: Server Platforms
---

### Post by kms254 on 2007-06-08
Background
I have been setting up a web/file/print server for myself. I have the OS on one small hard drive with the web files, and the file sharing on a second 300gb hard drive. The 300gb Drive is fat32, So i can take it with me on trips if i need to, and plug it into windows machines. 

The good:

I have everything working right, Website is up and running(locally), I have my users created, They access their individual folders and have access to the common folder. Everything is great. I can log in under me or any of the users, Drag and drop files into their folders or the common folder and no issues. Its pretty quick everything is happy. Working 100%!!

The Bad:
So if i am any user, in either Common, or their own folder and i right click and say make new folder, XP crashes(hard and quick). Now after reboot i go and try to change the name of the folder or drag files in XP will crash. This is in common or user profile's folder, under any user. I can SSH Secure File transfer to it and delete the "doomed" folder or add files with no issues. 

Anyone know what I am doing wrong?

---

### Post by pjbgravely on 2007-06-08
Sounds like a network issue with SMB. Say the client tried to create a folder on the host and the host never answered back that it happened then the client would hang. In this case the client is the shell, and when the shell goes the kernel goes too, though crashing not locking is a strange reaction. I would look for a firewall problem with the clients.

Paul

---

### Post by kms254 on 2007-06-08
Ok, let me clairify, the client(xp machine) is the one crashing. I mean its like it takes the powercord out of the back of the computer. The server is fine. Doesn't seem to mind it one bit. Every time the client trys to access that file, bam it crashes again. Its total weird. I mean every other operation is A ok, just creating a new folder.

---

### Post by pjbgravely on 2007-06-10
Sorry I confused you. Yes I know the client is Microsoft Windows xp where the desktop manager, the shell and the kernel crash as one.


  The power off you described sounds like a hardware problem, almost as if wake on LAN is going in reverse. The first thing I would to is to swap out the eithernet card. If that doesn't help then try another xp box on the same server. If it does the same thing then it sounds like an kernel bug on the client, maybe searching the bug reports for Samba wuld help find a work around. 

Paul

---

### Post by kms254 on 2007-06-12
Ok I tried it on two more computers and neither of them had issues. So I think it is related to this machine. I have the novell client on this machine so maybe something is getting confused? But I am chalking it up to that and until i can recreate the problem on another machine i am going to do the good old fashion skill of acting like it doesn't exist! :popcorn:

---

### Post by coquimbo on 2007-12-05
I'm having the same problem, wondering if any solution has been found.  I can confirm that an XP computer without the Novell Client works just fine with the Samba share, while an XP computer with Novell Client crashes hard when trying to change the name of a document or folder.  Any clues?

---

### Post by geddeth on 2008-04-24
Same problem here, on three different XP boxes, all with Novell Client on. I experience the issue also when saving files onto the Samba share or using e.g. TortoiseSVN on a working copy on the Samba share.

So. Did anyone find the fault?

---

