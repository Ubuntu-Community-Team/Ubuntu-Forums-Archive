---
title: "Latest version of ClamAV"
date: 2008-02-19
forum: Security Discussions
---

### Post by ikt on 2008-02-19
Hi there,

When in terminal I do: 

```
sudo freshclam
```

I get the following:

```
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.91.2 Recommended version: 0.92.1
```

How does one go about updating to 0.92.1 ?

---

### Post by ikt on 2008-02-19
Is this lack of responses and lack of other topics on the issue suggest all ubuntu servers are running an out of date clamav?

---

### Post by euler_fan on 2008-02-20
I suggest reading the stickied thread about Ubuntu Security and also reading up on how to install ClamAV from source if you care to keep an updated version on hand. Their manual is pretty good but needs a little translating from Fedora/Suse to Ubuntu.

---

### Post by astrotech226 on 2008-02-21
This is pretty common on just about every flavor of Linux.  Takes time to get the packages built and tested.

But don't confuse this message with your virus definitions being outdated.  This is telling you the "engine" is not of the newest version.  For the most part, that's not too big a deal.  If you have to wait a few weeks to get caught up it's fine as long as if you are still updating the virus definitions themselves.

---

### Post by tubezninja on 2008-02-21
Stupid Question Time:  Most software packages I'm familiar with increment **upwards** with successive new releases.  Is this NOT true with clamAV?

In other words, 0.92.2 is indeed OLDER than 0.92.1?

---

### Post by euler_fan on 2008-02-22
> **scaredpoet said:**
> Stupid Question Time:  Most software packages I'm familiar with increment **upwards** with successive new releases.  Is this NOT true with clamAV?

In other words, 0.92.2 is indeed OLDER than 0.92.1?

0.92.2 is an update from 0.92.1.

---

### Post by tubezninja on 2008-02-22
Just thought I'd make sure, because the error the OP is getting (and I've seen it as well) is:

WARNING: Local version: 0.91.**2** Recommended version: 0.92.**1**

In other words, the error message is saying that 0.92.2 is out of date, and 0.92.1 is current. :)

---

### Post by ikt on 2008-02-22
> **scaredpoet said:**
> Just thought I'd make sure, because the error the OP is getting (and I've seen it as well) is:

WARNING: Local version: 0.91.**2** Recommended version: 0.92.**1**

In other words, the error message is saying that 0.92.2 is out of date, and 0.92.1 is current. :)

Missing the number in the middle,

the version on our machines: 91.2
the latest version:----------------      92.1

> This is pretty common on just about every flavor of Linux. Takes time to get the packages built and tested.

But don't confuse this message with your virus definitions being outdated. This is telling you the "engine" is not of the newest version. For the most part, that's not too big a deal. If you have to wait a few weeks to get caught up it's fine as long as if you are still updating the virus definitions themselves.

I like to be as up to date as possible :)

> I suggest reading the stickied thread about Ubuntu Security and also reading up on how to install ClamAV from source if you care to keep an updated version on hand. Their manual is pretty good but needs a little translating from Fedora/Suse to Ubuntu.

cheers, I will look at installing clamav from source.

Thanks for all your help guys :)

---

### Post by tubezninja on 2008-02-22
> **ikt said:**
> Missing the number in the middle,

the version on our machines: 91.2
the latest version:----------------      92.1

Ah!  My dyslexia gets the worst of me. :)

---

