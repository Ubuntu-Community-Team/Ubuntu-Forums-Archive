---
title: "Ubuntu mirror problem"
date: 2005-11-07
forum: Server Platforms
---

### Post by ryanmunz on 2005-11-07
Howdy, my problem is this. I have a machine setup to mirror ubuntu for a college group. It needs to be able to work with http and ftp traffic. I used the debmirror script to pull all of breezy (main through multiverse plus sources) which, while i had a bit of trouble with it for awhile, is now done. Apt-get updating against it works through ftp. However, when I try to do the same with http I get an unknown gpgv error. The specific error is listed below. I'm using apache2 and proftpd.

Reading package lists... Done
W: GPG error: [ftp://pclug.pct.edu](ftp://pclug.pct.edu) breezy Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

**never mind, I'm an idiot. the problem is fixed however I can't figure out how to delete this thread!

---

