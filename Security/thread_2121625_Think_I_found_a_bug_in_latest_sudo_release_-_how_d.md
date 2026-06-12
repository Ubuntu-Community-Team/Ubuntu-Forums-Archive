---
title: "Think I found a bug in latest sudo release - how do I report?"
date: 2013-03-02
forum: Security
---

### Post by Contrarian on 2013-03-02
I'm not sure where to post this so looking for guidance on where to report this.  

Last week I built a 12.10 server template and created two clones "mail2" and "mail3".  They are all running on Hyper-V.  This morning I found when I SSH'd into "mail2" and ran "sudo su", it immediately disconnected my session.  However, connecting via  Hyper-V through tty, sudo works fine.  Oddly enough, this same behavior can't be replicated in "mail3".  I saw "mail3" had 11 updates pending, so I updated it.  Sure enough, the same behavior started happening on "mail3".  

Looking in dpkg.log,  one of the 11 updates was: **sudo:amd64 1.8.5p2-1ubutnu1.1**, and googling says this was released on Thursday. 

Where would I go to report that this release might be breaking ubuntu installations on hyper-v installations?

Update: I was able to correct this on "mail3" by downloading and installing **sudo_1.8.6-8_amd64.deb** from [http://www.sudo.ws](http://www.sudo.ws).  However, doesn't change that there looks like a bug in the latest release of sudo being sent out via ubuntu.

---

### Post by duke.tim on 2013-03-02
Check out this sticky from General Support
It is a guide to reporting bugs and helps to make a determination of what is a bug.[URL="http://ubuntuforums.org/showthread.php?t=1011078"]
http://ubuntuforums.org/showthread.php?t=1011078[/URL]

Also bugs are reported at launch pad
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by Contrarian on 2013-03-03
Thanks

---

