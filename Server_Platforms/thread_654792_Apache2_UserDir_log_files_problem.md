---
title: "Apache2 UserDir log files problem"
date: 2007-12-31
forum: Server Platforms
---

### Post by kaotix on 2007-12-31
I have been trying to work out how to setup log files while using the UserDir module in Apache2. I've noticed that regardless of my settings in the main virtualhost config the access/errors are still logged to the main apache log files when a user is using the ~username directory.

Am i missing something here, or is this the case when using the UserDir module? I need the log files to calculate stats and bandwidth for my hosting panel, and a user could easily redirect their entire domain to the UserDir enabled directory of their site and bypass all bandwidth restrictions.

Please could someone help me out here? Thanks

---

