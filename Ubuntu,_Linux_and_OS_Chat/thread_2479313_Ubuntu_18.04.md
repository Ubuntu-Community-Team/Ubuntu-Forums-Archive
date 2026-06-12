---
title: "Ubuntu 18.04"
date: 2022-09-20
forum: Ubuntu, Linux and OS Chat
---

### Post by gordie692 on 2022-09-20
Hi guys I found the perfect laptop was thinking 18.04 thats still secured till 2028 right

---

### Post by TheFu on 2022-09-20
> **gordie692 said:**
> Hi guys I found the perfect laptop was thinking 18.04 thats still secured till 2028 right

Standard support for most 18.04 flavors ended in 2021.
Ubuntu Server and "Ubuntu Desktop" which is the default DE, not any others, has 5 yrs of standard support (Apr 2023) with the option of paid 5 more years of support.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm) it isn't the same type of support as during the 3 or 5 yrs of standard support. Beware.

> Canonical provides Ubuntu Advantage Essential subscriptions, which include ESM, free of charge for individuals on up to 3 machines.


At this point, new installs should be using 20.04 or 22.04 (if you have new hardware and need new kernels).  Anyone still on 18.04, should be planning their migration to 20.04 to complete before April.

---

### Post by gordie692 on 2022-09-20
okay thanks so if I installed I'm good but after this year use the paid for 5 more years

---

### Post by TheFu on 2022-09-20
> **gordie692 said:**
> okay thanks so if I installed I'm good but after this year use the paid for 5 more years

I fear you've over simplified the rules a bit too much.
For Ubuntu Server 18.04, yes.  For any Desktops, it gets complicated.

---

### Post by gordie692 on 2022-09-20
Okay sorry guys just really like the 18.04 some reason just not a fan of 20.04 and on unless I choose another distro with Ubuntu repository

---

### Post by TheFu on 2022-09-20
> **gordie692 said:**
> Okay sorry guys just really like the 18.04 some reason just not a fan of 20.04 and on unless I choose another distro with Ubuntu repository

Agreed. There are some good things in 20.04 which will become more and more of an issue going forward because 18.04 doesn't have them.  I've been seeing incompatibilities since 20.04 came out, between python versions and php upgrades.  Don't know if end users would notice the php thing, but the python thing most definitely **is** an issue.

OTOH, it is your system and only you can decide if the level of support is sufficient for the attacks on your system(s).
To see the current status for supported vs non-supported packages, run
```
$ ubuntu-support-status
```
On my 18.04 system, 57% of the packages are supported until Apr 2023 by Canonical.  The rest are either dead or unsupported.  There's no simple answer, especially if you use non-core packages or any PPAs.

---

### Post by gordie692 on 2022-09-20
Thanks guys

---

### Post by lammert-nijhof on 2022-09-22
The Extended Security Service (ESM) of Ubuntu 18.04 will be free. I think for max 3 PCs.  I have done the same for Ubuntu 16.04 ESM and I nicely receive security updates each week for $0.00 till April 2026 :) :)

---

### Post by guiverc on 2022-09-22
Don't forget that ESM doesn't include all packages, only 'main' packages, with some provided via *snap* or *deb* package as gets documented prior to ESM starting; ie. look at 16.04 for clues on what to expect with 18.04 (*just as you looked at 14.04 as to what to expect with 16.04*)

If using a desktop system on 16.04 for example, to keep getting updates using ESM; you needed to change some of the *deb* packages (which weren't included in ESM) to *snap* packages, refer [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04) where libreoffice, thunderbird, firefox get security fixes only if *snap* is used. 

ESM support differs to LTS support.

---

### Post by gordie692 on 2022-09-22
Thanks guys for all help I've decided to bare and I installed 20.04 on my Lenovo Thinkpad T510 with a sata 500 hd and 4 gigs ram dvd don't work I'm exchanging that for dvd cradle for a second hd but everything running on 20.04 just in the software center where you update the software not letting me do the snapstore says 15 day thing never saw this before but when second hd goes in I'm installing Kubuntu 20.04

---

### Post by grahammechanical on 2022-09-25
> just in the software center where you update the software not letting me  do the snapstore says 15 day thing never saw this before

This is new. Up to now if we update/upgrade using Software Updater then any installed snap apps are refreshed/updated at the end of the update/upgrade of the deb packaged apps. That process still happens but there is a change. Maintainers of certain snap packaged apps are pushing the refresh of their snaps apart from the operation of Software Updater or the use of the snap refresh command. They do give the user notice of when the automatic refresh will take place and there is a count down. I imagine this is because of users who rarely update their systems but continue using apps that connect to the internet. These apps may have security vulnerabilities that are not being fixed. This puts all users of the internet at risk.

P.S. I am starting to think that the pushing of snap refresh by the maintainers is an aspect of Over The Air (OTA) updates. 

Regards

---

