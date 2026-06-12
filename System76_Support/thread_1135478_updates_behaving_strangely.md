---
title: "updates behaving strangely"
date: 2009-04-24
forum: System76 Support
---

### Post by xakh on 2009-04-24
I can't seem to update. When I try, some packages fail to download, which I don't like, since I don't like to install without some packages. Then, when I attempt to do it again, it fails over and over, and the updates fail to contact like half the servers. Is it just Canonical's servers being overloaded, or do I have a problem?

---

### Post by Synthros on 2009-04-24
I believe it's just the heavy load on the servers due to the new release.  I've had a couple updates fail over the last day, and installing apps has been EXTREMELY slow.

---

### Post by Mike_IronFist on 2009-04-24
> **xakh said:**
> I can't seem to update. When I try, some packages fail to download, which I don't like, since I don't like to install without some packages. Then, when I attempt to do it again, it fails over and over, and the updates fail to contact like half the servers. Is it just Canonical's servers being overloaded, or do I have a problem?

I am having the same problem. I'm thinking it must be the servers having problems, but I'm not entirely sure myself.

So my question goes out as well: is it a bug or is it the servers?

---

### Post by chrisinspace on 2009-04-24
Yeah.  I've been trying to upgrade to 9.04 all morning, but I can't get past 'Setting up new software channels'.  The Ubuntu servers are TAXED!

---

### Post by Mike_IronFist on 2009-04-24
It sounds to me like the servers are the only logical explanation if so many users on wide varieties of hardware have this problem. If so it's a temporary problem, which is good news!
Thanks for all the input, folks.

---

### Post by bcschmerker on 2009-04-24
> **Synthros said:**
> I believe it's just the heavy load on the servers due to the new release.  I've had a couple updates fail over the last day, and installing apps has been EXTREMELY slow.I concur; regular Database Updates for my ECS-reequipped Everex running 8.04-LTS take up to two minutes to start, and the same applies to new Package downloads (no malfunctions at my local system for Synaptic).  With Canonical Ltd. handling tons of download traffic for 9.04 Jaunty, such slowdowns come with the territory.

---

### Post by thomasaaron on 2009-04-24
Yes, this happens with every new version. Everybody rushes to upgrade, Ubuntu's servers start getting taxed and upgrades end up corrupted.

Never fails.

---

### Post by xakh on 2009-04-24
Good. I thought it was a failure on s76's part, which would have made me sad.

---

### Post by Derath on 2009-04-24
You could try this (assuming you're not dist-upgrading yet), in software sources, go to the "Download from", hit the down arrow, select "Other" and hit the "Select Best Server".

This will go through the servers and select the one with the lowest lag time. Then apt/synaptic will use that server instead of the main ubuntu server.

Again, I wouldn't do that for dist-upgrades (I'm waiting for a while), but if you need recent updates, that worked for me.

---

### Post by MarkID on 2009-04-24
Or, if you can wait, just do the updates next week.

---

### Post by ctsdownloads on 2009-04-24
If and when I do any Ubuntu upgrade, I use [their alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors") rather than the main one. Download, burn, insert to system to be upgraded, wait for package manager prompt, choose **NOT** TO INCLUDE INTERNET updates, then upgrade away. It is much easier and less likely to bork a system. ;)

---

