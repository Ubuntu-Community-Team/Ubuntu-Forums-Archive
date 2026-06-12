---
title: "High disk-memory-cpu usage.."
date: 2010-08-19
forum: Server Platforms
---

### Post by BugBuster on 2010-08-19
Hi,
I am running latest apache2 available in the lucid repos on my desktop. All packages are updated as of this moment.

Now..in the root of my web server I have placed several soft links that point to folders on another ext3/ntfs partitions on the same disk. When I try to download any large file (say above 500M)on this server using firefox, when the 'save' window appears, my desktop freezes, I notice very high cpu-ram-disk usage, even though I have not yet clicked on 'ok' to save the file. This issue is not present when the file size is small. Note that firefox and the webserver are running on the same computer.

Also I have tried nginx and lighttpd and the issue is present there as well. When I tried downloading the same files using Internet Explorer 6.0 using a XP VM the issue is not present. However on Windows as well using Firefox the issue recurs.

Any suggestions?

---

### Post by arrrghhh on 2010-08-19
2 things.  Are you getting to the site by just going to [http://localhost?](http://localhost?)

Second, have you tried hitting the site from another machine on the LAN or even WAN?

---

### Post by BugBuster on 2010-08-19
> **arrrghhh said:**
> 2 things.  Are you getting to the site by just going to [http://localhost?](http://localhost?)
yes
> 
Second, have you tried hitting the site from another machine on the LAN or even WAN?

No ..will try when I have access to a friends laptop.

---

### Post by BugBuster on 2010-08-20
I think I have pin-pointed the cause of this issue. When I try to download anything with Firefox it automatically starts downloading the file in background with a .part extension (on linux in /tmp and on windows in %temp% directory), while the "open with/save as" window is still active and we have not yet clicked on 'OK' to start downloading. I have tested this on Ubuntu 10.04 with Firefox 3.6.8 and on WinXp with Firefox 4.0b3 and in both the behaviour is same.

Now the question is can I disable this feature in Firefox and how?

---

