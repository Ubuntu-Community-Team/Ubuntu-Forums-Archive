---
title: "rkhunter/ chkrootkit and exim4"
date: 2010-05-07
forum: Security
---

### Post by Soul-Sing on 2010-05-07
When installing these progs on Lucid it comes with exim4,I noticed this in the terminal output. What has exim4 to do with rkhunter and/or chkrootkit?
Anyone?

---

### Post by styxcoverbnd on 2010-05-07
> **leoquant said:**
> When installing these progs on Lucid it comes with exim4,I noticed this in the terminal output. What has exim4 to do with rkhunter and/or chkrootkit?
Anyone?

It is installed with rkhunter. It's used to email rkhunter output to you. I've found rkhunter/chkrootkit pretty useless, but I did like looking at all the rkhunter log info to see what I can learn. When I was testing Lucid I installed rkhunter and found that exim was constantly talking to my router clogging up the sys and messages logs so when I installed Lucid on a production PC I did not install rkhunter

---

### Post by Soul-Sing on 2010-05-07
> **styxcoverbnd said:**
> It is installed with rkhunter. It's used to email rkhunter output to you. I've found rkhunter/chkrootkit pretty useless, but I did like looking at all the rkhunter log info to see what I can learn. When I was testing Lucid I installed rkhunter and found that exim was constantly talking to my router clogging up the sys and messages logs so when I installed Lucid on a production PC I did not install rkhunter

Thank you. I didn't know about this till now. On 8.04.4 exim leaves an open port on desktop computer after a nmap (intense).Pretty weird imo.

---

### Post by MechaMechanism on 2010-05-08
> **leoquant said:**
> Thank you. I didn't know about this till now. On 8.04.4 exim leaves an open port on desktop computer after a nmap (intense).Pretty weird imo.Exim4 only leaves a port open if you have configured exim4 as an Internet site.

Do the commands below and configure things properly.

sudo dpkg-reconfigure exim4-config


sudo dpkg-reconfigure rkhunter


sudo dpkg-reconfigure chkrootkit

As long as you don't configure Exim4 as an Internet site you are not open to outside world.

---

