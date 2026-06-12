---
title: "Mysql error"
date: 2010-07-18
forum: Server Platforms
---

### Post by =ChAoS= on 2010-07-18
Hi i have installed lamp and phpmyadmin on a remote ubuntu server with a clean 64bit install but when i go into phpmyadmin i see this ... 
 
***The additional features for working with linked tables have been deactivated. To find out why click here***
 
When i click in the here link i get this at the bottom of the list ... 
 
**$cfg['Servers'][$i]['tracking'] ... NOT ok tracking disabled**
 
I've tried looking this stuff up but its all alien to me and i'm wondering if its why i have database issues when i try to install invision power board to run a forum?
 
Any help would be great. 
 
Thanks =ChAoS=

---

### Post by Ryan Dwyer on 2010-07-18
That's safe to ignore. I get that notification all the time as well.

What error do you get when you try to install IPB?

---

### Post by =ChAoS= on 2010-07-18
Thanks for the reply. 
 
I haven't tried to install it again yet after the re install of the server os but i'm going to try now. I'll post back when i have. I'm ok with running a forum and last time it was on a small hosting package but its the first time i have run my own rented remote server and tried to install these kind of things.
 
=ChAoS=

---

### Post by stmiller on 2010-09-05
Fix is found here:

[https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/565627](https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/565627)

---

