---
title: "Security updates"
date: 2009-01-29
forum: Security
---

### Post by timon_vdm on 2009-01-29
Hi,

Is it possible to automate security updates with cron? And what are the risks for running this on a (web)server. Im afraid my server will become unusable if for instance php5 is installed over php4.

Thanx in advance

---

### Post by Dr Small on 2009-01-29
The best approach in to manually install security updates, so if something breaks, you will be there to see what happened and to know how to fix it.

---

### Post by Nepherte on 2009-01-29
You can indeed schedule automatic updates with cron, but as you have already stipulated, it might break your system. Considering it's a server, you may want to update once a week or only once a month manually and see if you're server still works.

---

### Post by timon_vdm on 2009-01-30
Thanx for your response!

But how do i make sure when i use apt-get upgrade it only fetches the security updates? And is there a way to rollback these updates if something goes wrong?

---

### Post by Tubes6al4v on 2009-01-30
You could use synaptic. I am sure there is a way to do it with apt-get or aptitude, but gui is just too simple to pass up for me.

---

### Post by timon_vdm on 2009-01-30
Synaptic would be nice of i had any GUI on my server....

---

### Post by Nepherte on 2009-01-30
Edit /etc/apt/sources.list to only include the security repository. That way only security updates will be updated. This also means you can only install packages from the security repository. If you need a package from another repository, enable it again.

You can install an earlier version of a package but I forgot how. I suggest you look at the man pages of apt-get.

---

### Post by koenn on 2009-01-30
> **timon_vdm said:**
> Hi,

Is it possible to automate security updates with cron? And what are the risks for running this on a (web)server. Im afraid my server will become unusable if for instance php5 is installed over php4.

Thanx in advance
an upgrade from php4 to php5 wouldn't be included in a security update, security updates would always be miner virsion increments (they fix security problems, they don't do majior version upgrades)

Other than that, I agree with others here that you should upgrade manually, or you could consider upgrading automatically with only the security repo enabled.

Ideally, you'd test the results of any patch/fix/update on a (virtual) copy of your server before applying it to your (production) server, but that's not always feasible and you rely on the testing done by devs and packagers. In that case, the closer your server is to a default Ubuntu config, the better the odds that the upgrade will succeed without trouble.

---

### Post by cariboo on 2009-01-30
I use apticron on my server, it emails you when updates are available, with change logs.  You still have to manually do the updates, but that way there aren't any surprises.

Jim

---

### Post by jgoguen on 2009-02-01
[This page](https://help.ubuntu.com/community/AutomaticSecurityUpdates) gives a few methods of automating security updates.  I recommend the cron method, IMO it's the lowest maintenance method.  The benefits are that you get security updates applied weekly without even thinking about it.  The potential problems are, as you've identified, that an update may break something.  Some security updates require a reboot to fully apply.  These are both things you have to consider even if you manually apply updates, but if an update breaks while you're there applying it you know sooner and you can start fixing it sooner.  Overall, whether or not to automate security updates is really a tradeoff, and you have to decide whether the potential benefits outweigh the potential problems.

---

### Post by timon_vdm on 2009-02-02
thanx for all your reply's! This will be enough food for thought and i will try your solutions.

---

### Post by timon_vdm on 2009-03-17
Oke, for anyone who wants to know.

The final solution I used was altering /etc/apt/sources.list so apt only finds security updates (dapper-security). After that I installed apticron and added it to my cron so that it checks for security updates weekly. 

When apticron tells me there are important security updates I install them by hand. This way i control these updates and can roll them back IF something goes wrong. This costs me more work but for about 10 servers it is doable.

---

