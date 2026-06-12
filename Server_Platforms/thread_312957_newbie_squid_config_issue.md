---
title: "newbie squid config issue"
date: 2006-12-05
forum: Server Platforms
---

### Post by mrgomeg on 2006-12-05
I'm a newbie to ubuntu (and linux in general), trying to set up a router/content filter for our school with Squid and Dansguardian.  I followed some instructions for setting up Squid, but now I can only access secure websites (https).  All http sites give me the error: "Access control configuration prevents your request from being allowed at this time."  Any ideas?  Should I post my config file, or does somebody know what I did wrong?

---

### Post by bmathis on 2006-12-10
yes... please post your conf file so I can see whats wrong. I'm fairly versed with Squid and DansGaurdian.

---

### Post by technodigifreak on 2006-12-11
Actually, I had been thinking about implementing a Squid cache on an upcoming project and was curious if there was a general reference book on Squid that covered it adequately.  I looked, but there didn't seem to be an O'Reilly book on the topic, maybe another publisher has covered it?

---

### Post by bmathis on 2006-12-11
O'Reilly published "Squid - The Definitive Guide" back in 04. If you PM me, I might be able to hook you up with a copy.

---

### Post by modulok on 2006-12-18
you could always rename your squid.conf and load up the default conf file and do a "squid -k reconfigure"...then check to see you can access http:// web sites.

---

