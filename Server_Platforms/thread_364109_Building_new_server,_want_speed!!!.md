---
title: "Building new server, want speed!!!"
date: 2007-02-17
forum: Server Platforms
---

### Post by z33k3r on 2007-02-17
Hey guys, looking to build a new server and would like to have it running as fast as possible. I have the hardware covered, but was wondering what you guys might suggest as far as the software goes... I have been using ISPConfig with Mysql and apache. I would like to know if any body has used this setup etc and what i can do to improve the speed as the new server will have quite a bit of traffic on it.

Box will contain dual opty's, 4gigs of ram, 4x 250gig SATA-II drives, etc...

---

### Post by elst on 2007-02-18
Your biggest limitations are likely to be the application, the database config, and the end user's bandwidth - the hardware and services are more than good enough. Make sure that mod_deflate is enabled, as this can significantly reduce the amount of bandwidth used. 

Also read the MySQL configuration and make that it's making full use of your hardware - feel free to increase the buffer sizes etc. Once it's all up and running check the MySQL logs periodically to see how the application is working with the database, and tune as necessary.

---

