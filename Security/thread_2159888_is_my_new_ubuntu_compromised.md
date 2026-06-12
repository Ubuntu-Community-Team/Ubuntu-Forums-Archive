---
title: "is my new ubuntu compromised?"
date: 2013-07-04
forum: Security
---

### Post by johnny redd on 2013-07-04
Im very new to this but learning rather quickly...after installing 13.04rr for xubuntu i noticed every day it has been asking for updates...installed and restart... i have only  instaled netflix other than that its what ubuntu sent me, what Im concerned about is after checking rkhunter i git several warning labels and need to figure out what they are and what to do about them, below is a screenshot thanks and gotta say I love ubuntu! way easier than windows oddly enough

---

### Post by Irihapeti on 2013-07-04
Welcome to the forums.

rkhunter and chkrootkit are notorious for false positives. It's very likely that nothing is wrong with your installation. I've even had rkhunter complain about files on a freshly-booted liveCD!

From what I've seen, rkhunter seems to create more anxiety than anything else. If you want to run it regularly and keep track of unexpected changes, it might be useful if you are running a server. In other circumstances, reading and following the basic security advice will be more useful. See [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

The two main issues that come up regularly on these forums are ssh servers that are inadequately secured, and enabling remote desktop (VNC), often without realising it.

---

### Post by cariboo on 2013-07-05
> **johnny redd said:**
> Im very new to this but learning rather quickly...after installing 13.04rr for xubuntu i noticed every day it has been asking for updates...installed and restart... i have only  instaled netflix other than that its what ubuntu sent me, what Im concerned about is after checking rkhunter i git several warning labels and need to figure out what they are and what to do about them, below is a screenshot thanks and gotta say I love ubuntu! way easier than windows oddly enough

If you are running Ubuntu without any added repositories (ppas) you really shouldn't have anything to worry about, and unless something strange seems to be going on, on your system, there isn't any need to run rkhunter. As a matter of fact, unless you've read the rkhunter documentation, and run the rkhunter database update, as a baseline, it is a pretty useless application. 

As Irihapeti said, false positives will show up after almost every update. and the best thing you can do is to learn how to use your Ubuntu system, instead of looking for replacement Windows anti-malware applications.

The stickies at the top of this sub-forum, are a great place to start learning about securing your installation, as they have been written and kept up-to-date by several Ubuntu security experts.

---

