---
title: "How long before a 3rd party package upgrade shows in Software Center"
date: 2014-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Cbhihe on 2014-10-15
Hi,
I just saw that Apple released the long awaited CUPS 2.0.0. Currently Canonicals does not offer it in its Software Center on Trusty although it claims that..
> Canonical provides critical updates for Common UNIX Printing System(tm) - PPD/driver support, web interface until May 2019.
What is the time scale for that to happen ? 
What are the internal review mechanisms in Canonical? 
Any insider's knowledge welcome.
-ced

---

### Post by SeijiSensei on 2014-10-15
Versions with "Long-Term Support" like 14.04 will not replace an existing package with newer versions.  Only updates to the existing packages are released.  Even [14.10]("https://launchpad.net/ubuntu/+source/cups") (Utopic) includes 1.75, which isn't too surprising since it will be released later this month.  So you're probably looking at 15.04 for the earliest release to include CUPS 2.

---

### Post by sammiev on 2014-10-15
Testing will begin soon for 15.04 now 14.10 is almost here. ):P

---

### Post by slickymaster on 2014-10-15
> **SeijiSensei said:**
> Versions with "Long-Term Support" like 14.04 will not replace an existing package with newer versions.  Only updates to the existing packages are released.  Even [14.10]("https://launchpad.net/ubuntu/+source/cups") (Utopic) includes 1.75, which isn't too surprising since it will be released later this month.  So you're probably looking at 15.04 for the earliest release to include CUPS 2.

This ^^^

Currently in 14.10 the included CUPS package is **1.7.5-3ubuntu1**:```
~$ apt-cache policy cups
cups:
  Installed: 1.7.5-3ubuntu1
  Candidate: 1.7.5-3ubuntu1
  Version table:
 *** 1.7.5-3ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
        100 /var/lib/dpkg/status
``````
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
3.16.0-22-generic
```

---

### Post by Cbhihe on 2014-10-15
&#12354;&#12426;&#12364;&#12392; SeijiSensei. ... the which means that if users want or need the newer version for any given package not being updated for security reasons, they need to install it from the .tar or in a best case scenario from the .deb files  ?
Thank you for your reply.

---

### Post by Cbhihe on 2014-10-15
@sammeiv: thanks, but how does one find out ? If there a DB listing out all package version support (past, present and future) that I can query ? Or do mere mortals need to be born knowing it ?

@slickymaster: thanks. I was not familiar with 'apt-cache policy [package]'. 
Can you tell what  500 and 100 mean in the print-out ?

---

### Post by grahammechanical on 2014-10-15
"Critical updates" mostly refers to security patches and not upgrading to newer versions of packages. The code would have to be audited. Which is a time consuming process. The aim of Ubuntu developers is stability. Especially for LTS releases. Imagine getting this newer version and finding out that your printer no longer works. That is what the developers aim to avoid happening.

Ubuntu 14.04 will get 4 major upgrades called point releases between the released date of 14.04 and the release date of 16.04. We have just had the 14.04.1 upgrade. These point releases keep the LTS up to date with Linux kernels and firmware that are going into the Interim releases. It may be that during one of those point releases that 14.04 will get the newly released CUPS version.

Regards.

---

### Post by slickymaster on 2014-10-16
> **Cbhihe said:**
> <---snip--->
@slickymaster: thanks. I was not familiar with 'apt-cache policy [package]'. 
Can you tell what  500 and 100 mean in the print-out ?

500 and 100 are the priority numbers. 500 corresponds to installable, 100 means installed. From the man page:> 
If the target release has not been specified then APT simply assigns priority 100 to all installed package versions and priority 500 to all uninstalled package versions.
The *** just means installed, as far as I know. Once it has been installed, you see both 500 and 100, corresponding to the version in the archives and the locally installed version respectively.

---

### Post by Cbhihe on 2014-10-16
> From the man page: [QUOTE]If the target release has not been specified then APT simply assigns  priority 100 to all installed package versions and priority 500 to all  uninstalled package versions.[/QUOTE]Thanks, but I wonder what man-page(s) you consulted. If I do a [FONT=courier new]man apt-cache[/FONT] (as I had done), no information on the meaning of those priority codes shows. Weird.

---

### Post by slickymaster on 2014-10-16
> **Cbhihe said:**
> Thanks, but I wonder what man-page(s) you consulted. If I do a [FONT=courier new]man apt-cache[/FONT] (as I had done), no information on the meaning of those priority codes shows. Weird.
```
man apt_preferences
```

---

### Post by ian-weisser on 2014-10-16
Here is one way to find out how long it will take to get CUPS 2.0.0 into the Ubuntu Repositories:

First, look at the source of the package. Is it directly contributed? Or does it come from Debian?
```
$ apt-cache show cups | grep Original-Maintainer
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
```

The 'cups' package is imported from Debian every six months.

Next, let's go upstream to see if Debian has it yet: [https://tracker.debian.org/pkg/cups](https://tracker.debian.org/pkg/cups)
You can see that the released version of 2.0.0 hasn't been detected yet; the newest version is 2.0~rc1.

So the process will roughly be:
1) The Debian package tracker will detect 2.0.0's availability, and ping members of the Debian Printing Team.
2) The Debian Printing Team will package the software and load it into Debian Testing.
3) After a couple weeks, if the software is reasonably stable, Debian will migrate the software to Debian Unstable.
4) Ubuntu imports packages from Debian Unstable during the (approximate) periods Nov 1 - Feb 1 and May 1 - August 1. Those imports go into the next release of Ubuntu (April and October).

As others have said, new releases do not get backported to existing versions of Ubuntu without a really good reason.

So if the Debian Printing Team packages the software reasonably soon, and the software has no major problems and the package builds properly, it may indeed show up in Ubuntu 15.04. If the package doesn't reach Debian Unstable until mid-February 15, then it will show up in Ubuntu 15.10.

---

### Post by Cbhihe on 2014-10-16
Klasse ! Ian. Thanks very much. 
That is exactly what I was looking for. It affords us, learners, a little bit more autonomy in dealing and planning with release and upcoming features. 
I am definitely bookmarking this  for future reference.
-ced

---

### Post by vasa1 on 2014-10-16
> **Cbhihe said:**
> Klasse ! Ian. Thanks very much. ...
I am definitely bookmarking this  for future reference.
-ced
+1. Great answer :)

---

### Post by mikodo on 2014-10-16
> **ian-weisser said:**
> 
<snip>

So the process will roughly be:
1) The Debian package tracker will detect 2.0.0's availability, and ping members of the Debian Printing Team.
2) The Debian Printing Team will package the software and load it into Debian Testing.
3) After a couple weeks, if the software is reasonably stable, Debian will migrate the software to Debian Unstable.
4) Ubuntu imports packages from Debian Unstable during the (approximate) periods Nov 1 - Feb 1 and May 1 - August 1. Those imports go into the next release of Ubuntu (April and October).

As others have said, new releases do not get backported to existing versions of Ubuntu without a really good reason.

<snip>

hmm ... Good stuff!

I always thought, newer packages in Debian migrated thusly: Experimental -> Unstable -> Testing -> Stable, and that Ubuntu got all its' Debian packages from Testing. I need to read more. (Maybe the update process, is different for 3rd Party package upgrades). I don't know, and for me, it doesn't matter.

Good to know the Ubuntu importing process. I know now for my 'buntu system, I will try to install each new LTS, when available. Rather than remaining with it, towards the whole supported time period. This provides for some newer packaging, with an extra layer of Ubuntu stability. For my Debian install, I will use the Stable releases, with its' tested and unchanging packages.

---

