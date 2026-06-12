---
title: "Is setting up the following on one server asking for too much?"
date: 2009-07-25
forum: Server Platforms
---

### Post by majdi on 2009-07-25
Is setting up the following on one server asking for too much?

**Services**
LAMP
LDAP
SAMBA
File & Print Server

**Usage**
Users: 100 user access (mixed environment)
2 CMS Websites running on LAN

**Hardware**
Intel® Xeon® E5502, 1.8 6Ghz , 4M Cache, 4.8 6 E5502
GT/s QPI, 4GB Memory, HD 500GB x 2

---

### Post by bacil on 2009-07-25
No, you will be fine, well depends what your 100 users will be doing ;-)

---

### Post by majdi on 2009-07-26
Just file sharing, printing and accessing the websites.

---

### Post by torsson on 2009-07-26
It should work just fine in my eyes

---

### Post by tubezninja on 2009-07-26
Yeah, should work just fine.

What's your storage situation looking like, file systems had setup etc?

---

### Post by R.Bucky on 2009-07-26
I would think that the number of concurrent users would be in question. If all 100 users were active with 10 printing and 90 moving files, the CPU would need attention. Also, you would need to increase the php memory limit depending on the scripts that you are running. 100 users is fine, but how many concurrent processes are running is the more important question.

---

### Post by majdi on 2009-07-29
That sounds great, has anyone tested this kind of setup with ubuntu 9.04?

---

### Post by Thirtysixway on 2009-07-31
It's not as though you're running thin-clients on there, so I would think that those resources would work fine with those applications.

---

### Post by majdi on 2009-08-01
Ok, so now we have established that this can be done on one server, the question now is how;

I'm looking for a web based GUI that can handle setup, configuration and management of these services, right now I'm looking at [eBox]("http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server") which is based on Ubuntu Server 8.04.

Can I get some feedback from anyone who has set this up using eBox or an alternative app.

---

### Post by Thirtysixway on 2009-08-02
I use webmin to manage my server ocasionally.  Learning the command line is the fun part :D

---

