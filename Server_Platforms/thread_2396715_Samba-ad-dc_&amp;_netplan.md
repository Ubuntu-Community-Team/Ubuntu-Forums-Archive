---
title: "Samba-ad-dc &amp; netplan"
date: 2018-07-19
forum: Server Platforms
---

### Post by restemayer on 2018-07-19
Can someone explain this to me, and then maybe give me a clue as to how to fix it?

I had an active domain setup on 16.04, and it worked ok.  I'm creating a new, more streamlined one in 18.04, and it works... kinda.  It's acting weird, and I'm pretty sure its related to the upgrade to using netplan.

The samba internal dns will not work on boot.  I can't login to a domain user.  I can su into a domain user, but they can't do anything.  Kerberos host isn't found.  In order to get it working I have to log in under a local user and run 'netplan apply'.  I don't have to change anything, just apply it, and then everything runs like silk.  What is going on here? I mean, now that I know what's up, its easy enough to do it when I turn the system on (its not going to be rebooted that often), but it is kind of annoying, ya know?  I'd much rather have it working on boot.

[IMG]https://s33.postimg.cc/shriphimn/Screenshot_20180719_191127.png[/IMG]

---

### Post by LHammonds on 2018-07-19
I don't know what NetPlan is doing but will it work if you add a line in root's crontab that says to run the "/usr/sbin/netplan apply" command @REBOOT?

LHammonds

---

### Post by restemayer on 2018-07-19
> **LHammonds said:**
> I don't know what NetPlan is doing but will it work if you add a line in root's crontab that says to run the "/usr/sbin/netplan apply" command @REBOOT?

LHammonds

That was my first thought to correct the issue too, but no dice.

I don't have access to that specific server right now, but I should be back to it in about 10 minutes; I'll check to make sure I didn't make a typo in my crontab command just to make sure, but I'm pretty sure I got it right.

---

