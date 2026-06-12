---
title: "Webalizer Problem"
date: 2011-01-07
forum: Server Platforms
---

### Post by d3fau1t on 2011-01-07
Hey everybody!

I set up a server with multiple virtual hosts as instructed [here]("http://ubuntuforums.org/showthread.php?p=10016541").

Webalizer was working, but I was messing around with something, and now it doesn't update or read the logs anymore. It just shows info from a month ago (which is when I started having this problem).

Does anybody know how I could get it working again?

---

### Post by d3fau1t on 2011-01-09
*bump*

---

### Post by d3fau1t on 2011-01-10
*bump*

---

### Post by d3fau1t on 2011-01-11
*bump*

---

### Post by d3fau1t on 2011-01-12
Well thanks everyone, you've been *so* helpful. :rolleyes:

In case this helps anyone, this fixed it:

Delete all instances of webalizer.conf.

Purge and reinstall webalizer using apt-get.

Edit webalizer.conf in /etc/webalizer to the log file in apache2 you want, or use the default.

Restart apache.

sudo webalizer

---

