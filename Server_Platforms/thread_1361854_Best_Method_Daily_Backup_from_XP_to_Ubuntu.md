---
title: "Best Method: Daily Backup from XP to Ubuntu"
date: 2009-12-22
forum: Server Platforms
---

### Post by localfiend on 2009-12-22
Hi all.

I have several off site XP computers that have folders I would like synced with my Ubuntu web server.  There are about a hundred different ways of getting this done, so I thought I'd ask and see if anyone had opinions on the best (I.E. Least clunky) method.  

My thinking right now is that I could set up an FTP client on each computer that would run at midnight and sync the files.  But, before I do something like that I figured I'd check and see if there was a better more secure way.

---

### Post by dyous87 on 2009-12-22
I would definitely go for SFTP over standard FTP. Same exact thing only it uses port 22 instead and is definitely much more secure as all information is sent encrypted.

---

### Post by Thirtysixway on 2009-12-22
How about using samba?

---

### Post by dyous87 on 2009-12-22
Samba will work between off location computers? I thought samba could only be used on a network.

---

