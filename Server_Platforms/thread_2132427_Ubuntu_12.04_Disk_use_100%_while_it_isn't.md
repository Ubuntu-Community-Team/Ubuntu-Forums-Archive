---
title: "Ubuntu 12.04 Disk use 100% while it isn't"
date: 2013-04-04
forum: Server Platforms
---

### Post by Seb_Boffen on 2013-04-04
Hello, I've got a strange issue going on, the space on my / file system gives 100% in use because my mounted raid array is 100% in use. In fact the / file system has got 129GB free out of the +- 140GB, the raid array had just used 6.1TB out of the 15TB. Has somebody got a clue what is wrong here? Any help would be appreciated.
 [IMG]http://www.boffensysteembeheer.nl/assets/image/ubuntu%20space%20issue.jpg[/IMG]                                                                                                                                                                                               Kind regards, Seb

---

### Post by deadflowr on 2013-04-04
Disk usage analyzer's bar graph is showing the total for used space.
In such cases, the top bar for root (/) always says 100%.
It breaks down where the space is being used, from highest to lowest.

---

### Post by Seb_Boffen on 2013-04-04
Thank you, I have this issue, this is a clean new install I've had the same setup before and never saw this diagram go up to 100% while there is 8.9TB of free space. Last morning when I woke up my / file system was at 100% in use, I noticed because backups did not run last night so I've started investigating where the issue is coming from and I think part of it has got to do with this. This morning after a restart the / file system had free space again and I could manually rerun my backups and receive emails again.

---

