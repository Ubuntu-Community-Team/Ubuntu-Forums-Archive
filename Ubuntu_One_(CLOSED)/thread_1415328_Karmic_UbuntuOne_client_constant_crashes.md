---
title: "Karmic UbuntuOne client constant crashes"
date: 2010-02-24
forum: Ubuntu One (CLOSED)
---

### Post by Dasani on 2010-02-24
Hi,
My UbuntuOne client on my karmic crashes 4 out of 5 times when I either single click or double click on it. It launches the Apport utility to submit a bug report.

I have since seen similar bugs submitted several times over to launchpad, and in several of the bug forums, I see messages such as "fixed now" etc... going back to Nov 2009,
but mine is still in the same state. My karmic is up to date.

In fact, my client used to work perfectly fine until about 3 weeks ago. I assume it was an update that changed this, but I can't figure out what to do now.

Any help?

thnx

---

### Post by joshuahoover on 2010-02-24
> **Dasani said:**
> Hi,
My UbuntuOne client on my karmic crashes 4 out of 5 times when I either single click or double click on it. It launches the Apport utility to submit a bug report.

I have since seen similar bugs submitted several times over to launchpad, and in several of the bug forums, I see messages such as "fixed now" etc... going back to Nov 2009,
but mine is still in the same state. My karmic is up to date.

In fact, my client used to work perfectly fine until about 3 weeks ago. I assume it was an update that changed this, but I can't figure out what to do now.

Any help?

thnx

Can you let me know what bug # was created? It's hard to say why this crash started to occur without some log files to look at. One thing to possibly try is to delete the following configuration file: ~/.config/ubuntuone/syncdaemon.conf and restart the Ubuntu One client. If you'd like some real time help, I'm available on #ubuntuone on Freenode IRC Monday-Friday, 14:00-22:00 UTC. Just ask for joshuahoover on there. Otherwise, we'll do the troubleshooting through the bug report.

Thank you,

Joshua

---

### Post by Dasani on 2010-02-24
See this is why I love Linux.

Thanks for the quick response Joshua...

I removed the syncdaemon file and so far (3 restarts), it seems to have fixed the problem. I'll definitely come back here and let you know if it happens again, but so far so good.

For your information though, this is the bug report that I had 'attached' to:
[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/489985](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/489985)

Again, thanks for the help...but in the meanwhile, I'm going to tag this thread solved.

take care

> **joshuahoover said:**
> Can you let me know what bug # was created? It's hard to say why this crash started to occur without some log files to look at. One thing to possibly try is to delete the following configuration file: ~/.config/ubuntuone/syncdaemon.conf and restart the Ubuntu One client. If you'd like some real time help, I'm available on #ubuntuone on Freenode IRC Monday-Friday, 14:00-22:00 UTC. Just ask for joshuahoover on there. Otherwise, we'll do the troubleshooting through the bug report.

Thank you,

Joshua

---

### Post by Dasani on 2010-02-25
ok..it's back in the 4th restart, lol

I'll try and catch you in the irc channels Joshua...

---

