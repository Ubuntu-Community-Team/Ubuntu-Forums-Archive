---
title: "Script to check security advisories?"
date: 2008-06-24
forum: Security
---

### Post by Root Moose on 2008-06-24
Maybe I can't see the forest for the trees; I'm a newish Ubuntu user coming from a Gentoo background.

In Gentoo there is a little script called "glsa-check" that would check the installed packages on a host and tell you if any of the packages had a security advisory against them.

From there you could upgrade as appropriate.

Is there a similar tool under Ubuntu? 

It doesn't seem to be something built into apt-get. Synaptic and Aptitude have some functionality but I'd like something that can be scripted, put in cron and send me an email in the AM letting me know what needs analysis.

FWIW, I'm running 8.04.

TIA

---

### Post by tubbygweilo on 2008-06-24
Can you make use of the Update manager via System > Administration > Update Manager as iirc when updates relate to security type matters they are offered first (at the top of the page) and you can then along with other updates select the ones you may wish to apply. I know this is not the script method you are seeking but it might be worth considering until someone offers you a script to do exactly what you wish.

---

### Post by Root Moose on 2008-06-24
Yeah, I'd really rather not get into X-windowing into a couple dozen machines every morning if I can avoid it.

Thanks

---

### Post by Nullack on 2008-06-25
As soon as Ubuntu issues a security notice its published on the security mailing list. On the ubuntu desktop atleast the default is a check once a day. A manual check is

sudo apt-get update

---

### Post by Root Moose on 2008-06-25
Correct me if this is incorrect.

An apt-get update will upgrade everything in the stream regardless of whether there is a security advisory or not.

I don't want to upgrade servers willy-nilly because some new version of some package came out. I just want to upgrade because of security advisories.

TIA

---

### Post by Nepherte on 2008-06-26
apt-get update will refresh your sources. apt-get upgrade will upgrade all the packages installed on your system. You could for example only enable the hardy-security repository. That way you will only get security updates.

---

### Post by Root Moose on 2008-06-26
> **Nepherte said:**
> You could for example only enable the hardy-security repository. That way you will only get security updates.

Ahh, good point.

Thanks!

---

### Post by ttys0 on 2009-08-10
> **Root Moose said:**
> 

Is there a similar tool under Ubuntu? 



I think you're looking for apticron. It's a shell script that runs and apt-get update daily and sends out an email report about what packages need to be updated. It also includes some security update info. All in all, it's quite similar to glsa-check.

---

