---
title: "InterNetNews server. Can't rebuild history file."
date: 2012-03-03
forum: Server Platforms
---

### Post by LMW on 2012-03-03
Hi folks,

I transferred inn2 server from an old Gentoo server to Ubuntu 10.04. However, I can't get it running. When I try to rebuild history file and overview database process starts and looks like it is running (and, by the way, using system resources), but with no result after ~ 4 hours of such activity. 
I did the following to transfer old files to a new server:
1. Moved old files located in /var/spool/news to a new server;
2. Moved config files;
3. Copied old files from news/articles, news/overview and from news/db to corresponding folders on a new server;
4. Tried to rebuild history and overview files;  
The following command work fine: "makehistory -f newfilename", but when I start news service CPU utilization flies up and stays at the top until I kill it.
If I try to rebuild overview database with "makehistory -O" it looks like it is running, but with no result at the end (as I described earlier).

What could be wrong?
Any help would be appreciated!

---

