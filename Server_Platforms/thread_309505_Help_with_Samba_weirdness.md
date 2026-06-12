---
title: "Help with Samba weirdness"
date: 2006-11-29
forum: Server Platforms
---

### Post by skirkpatrick on 2006-11-29
I've got a small server here at home that's been running RedHat 8 just fine.  It's mostly used as a file server with Samba.  I also have several Turtle Beach Audiotrons around the house that access the server to play music.  As I said, everything has been working fine.

I decided to upgrade the server to replace the drives and install Ubuntu Server 6.04.  Installation went smoothly and I setup Samba.  All the computers in the house (Ubuntu and Windows) access the Samba shares just fine (much quicker than RH 8).  However, the Audiotrons (which run Windows CE) are now having problems.  The can search the server to discover all the music files but when they go to play the files, they complain about not being able to find the server.  One piece of information that should point me in the right direction is the IP address of the server that the Audiotrons are reporting.  It should be 192.168.0.2 but they are reporting it as 69.xx.xx.xx.  I have no idea how they are getting that IP address or even if it has anything to do with Samba.

Anybody have any thoughts on how to track down the problem?  The wife is getting a little cranky about not having her music :)

---

### Post by apjone on 2006-11-30
cat you get into and edit the Windows\system32\drivers\etc\hosts file on the windows  ce device's?

---

### Post by skirkpatrick on 2006-11-30
Nope, it's a completely closed system.

---

### Post by apjone on 2006-11-30
this is strange. have you power cycled the device's?

---

### Post by skirkpatrick on 2006-11-30
Yep, that's when they started acting funny.  The devices were powered up and had talked to the old RH8 server.  I took the server down, rebuilt it, powered it back up, and the devices worked just fine.  I had to power down one of the devices and when it came back up, it shows the problem.

---

