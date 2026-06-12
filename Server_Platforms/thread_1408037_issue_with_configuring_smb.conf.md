---
title: "issue with configuring smb.conf"
date: 2010-02-15
forum: Server Platforms
---

### Post by associates on 2010-02-15
Hi, I was wondering if I can get some help here regarding Ubuntu Server 9.10. I have the latest Ubuntu Server up and running on my PC and would like to get familiarized with it. I am new to this system and am very keen to learn. The reason for this is that i plan to replace my Server running on microsoft SBS 2003 with Ubuntu Server. As I was trying to configure the smb.conf file on the Ubuntu Server, i was unsure as to which i should change or leave them as they are. 

I wonder if anyone might be able to give me a bit of guidance so that i can get the user authentication to work, domain, file sharing, printing, share definition, etc.

By the way, all our other PCs that are connected to SBS Server, run on XP Pro. 

Any help would be greatly appreciated.

Thank you in advance

---

### Post by chuina on 2010-02-15
Sarting with [[COLOR="Purple"]this Guide[/COLOR]]("https://help.ubuntu.com/9.10/serverguide/C/windows-networking.html") may helpful.

---

### Post by Iowan on 2010-02-16
Make a backup copy of /etc/samba/smb.conf before you begin editing it. Then, you can delete some of the unneeded sections/comments from your working copy, but still have a reference copy on which to fall back.

---

