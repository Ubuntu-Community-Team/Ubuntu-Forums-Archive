---
title: "Osmo crashes with Pipelight installed"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by crcarson on 2014-04-03
Looking for assistance on my bug report [https://bugs.launchpad.net/ubuntu/+source/osmo/+bug/1297872](https://bugs.launchpad.net/ubuntu/+source/osmo/+bug/1297872).  Summary of this problem is that after installing Pipelight to view Netflix the application Osmo won't start correctly.  The Osmo window starts full screen with many window components incorrect, missing, or invalid.  Also receive a Segmentation fault on termination.  Getting and compiling the 0.2.10 source from the Osmo site will result in no failures on the system with Pipelight. Don't know what I can do since I don't have access to 14.04 source level of Osmo.

---

### Post by crcarson on 2014-04-03
Let me start the speculation on my own post.  Think the problem is caused by a call to the GDK functions doing some cross-platform operations.  Think these calls with the Pipelight installed are passing back some invalid information which is causing the window_size_x and window_size_y to be set with invalid information.  You can see the result in the config.xml configuration file.

---

