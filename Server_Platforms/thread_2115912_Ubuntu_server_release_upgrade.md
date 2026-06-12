---
title: "Ubuntu server release upgrade"
date: 2013-02-14
forum: Server Platforms
---

### Post by SAngeli on 2013-02-14
Hi,
I run current Ubuntu 12.04.2 LTS \n \l and wish to learn how to upgrade to most current version.

I am not so expert with Linux and ubuntu and do not know if i can go from 12 to 14 (as an example). I do not know if this is feasible, if this will cause issues on a server running all configured and so on.

I wish to also ask how to mark a thread I post as [SOLVED]

Please let me know.

Thank you,
Spiro

---

### Post by tgalati4 on 2013-02-14
How many services are you running on your server?  If a lot, then you should stay with your current, long-term-support (LTS) version.  Is there a framework (such as PHP or ruby) that forces you to upgrade?  If no, then you should stay at your current version.

When 14 comes out (presumably 14.04, the next LTS), then there will be a provision to upgrade, but it's usually better to perform a clean install.  Since 12.04 is supported for 5 years and if all of your current services are running OK, then there is no reason to upgrade for the next 5 years.

If you need a newer framework for development work (Drupal9 for instance), then upgrading would be required.

What are your requirements?

---

### Post by SAngeli on 2013-02-14
Hi,
the reason for asking this question is because I would assume that new release means better services and new functionalities.
So far, this local small server has been built for being a local NAS and for web development, trying to better learn CMS and so on.

my current distro will be supported for 5 years, meaning until when?
Also, in the mean time, does it mean that whatever ver 14 and upper ones have also my current one will?
I find difficulties understanding this.

Also, on my current server I run mdadm with raid-1 HD. Reinstalling all from scratch how would impact on the current content of the HDs considering that I would have to install mdadm array again?

to keep my distro updated is it sufficient that I would run, from time to time, sudo apt-get dist-upgrade ?

Thank you,
Spiro

---

### Post by tgalati4 on 2013-02-14
Yes, you might have to rebuild your arrays.  RAID is not a backup solution.  And you can't be sure that your RAID will run properly by reassembling under a 2-year newer operating system.

The server operating system will get security updates for 5 years.  12.04 to 17.04.  That is April 2017.  That's a long time.  The next LTS will probably be 14.04, and it will also have 5 years of support.  The kernel version and supporting utilities will change between LTS, so 12.04 is not a subset of 14.04.  Think of 12.04 as being "frozen" in time.  A snapshot of Linux in April 2012.  It will stay that way, with some fixes applied.  14.04 will be a snapshot of Linux in April 2014.  Who knows what crazy changes will take place.  Your hardware may not even run on 14.04.  New things are added, old things are dropped.  So no one can really answer your question until 14.04 is release.  Then you can burn a disk and try a live version and see if it works.

Don't run dist-upgrade.  It will probably break things if you don't know what you are doing.  Dist-upgrade is for upgrading your distribution from 12.04 to 12.10.  Do you want to risk trashing your RAID?  Do you have a full data backup?  Do you have the time to fix things that might break?  If you answered no to any of those, then don't do it.  Simple.

For the next five years:

```
sudo apt-get update
sudo apt-get upgrade
```

Pay attention to what packages get updated, because sometimes *regressions* are introduced.  Those are updates that break things that were working previously.  It's rare but it happens.  You should really only need to update once every 6 months on a server or sooner if you have increased security concerns.

dist-upgrade will assign dependencies to your current version, but if you have added an PPA's or added a newer Ubuntu repository--to get a newer library function--it will seriously mess up your installation.  Use this switch with care.

Being Italian, I can appreciate your Vespa attitude. *(Living dangerously.)*

---

### Post by SAngeli on 2013-02-23
Hi,
thank you for your reply. Sorry for the late reply.
What I dislike about Ubuntu, if I correctly understand the reply, is that if I setup a new server in order to upgrade to a new distribution let's say from 12.04 to 14.04 I have to reinstall all from scratch and this could be a lot of work to do.
Rather, with other distro, again if I am not wrok, all I have to do is upgrade.

Can you please tell me if this is correct or not? I do realize that perhaps the hardware could not be compatible anymore (I doubt it) but why than other distro do not have this inconvenience?

I wish to better understand as I find ubuntu being quite easy and very well documented. Hence, I wish to kepp usign it compared to other distros.

Thank you for the reply,
Spiro

---

### Post by snowpine on 2013-02-23
Hi Spiro,

You can always find the latest upgrade instructions at this site: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

To go from 10.04 (the previous LTS) to 12.04 (the current LTS), the following procedure was recommended: [https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29](https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29)

It is likely that the upgrade procedure from 12.04 to 14.04 (the next LTS, scheduled for April 2014) will be similar.

However, 12.04 is supported through April 2017, so there is no rush to upgrade to 14.04 if your 12.04 system continues to meet your needs.

The correct commands to keep your 12.04 system up to date with the latest patches and bug fixes are:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Contrary to popular belief, 'sudo apt-get dist-upgrade' will **not** upgrade you to the next release---this is a myth, as you can confirm with 'man apt-get'. :)

Upgrades should always be approached sensibly and cautiously. You should read upgrade testimonials on these forums, create a full backup, and test any mission-critical scripts or services with the new release **before** you commit to an irreversible upgrade on a production machine. Many users feel that, despite the easy upgrade procedure Ubuntu supplies, it is more reliable and saves time in the long run to do a fresh reinstall. That is not a topic I personally have a strong opinion on, one way or the other, but it is a frequently-asked question, so you can read many existing discussions on these forums about "upgrade vs. reinstall?" if you wish to learn more.

---

### Post by CharlesA on 2013-02-23
> **snowpine said:**
> The correct commands to keep your 12.04 system up to date with the latest patches and bug fixes are:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Contrary to popular belief, 'sudo apt-get dist-upgrade' will **not** upgrade you to the next release---this is a myth, as you can confirm with 'man apt-get'. :)

Well, it won't upgrade you to the next release unless you mess with your sources.list file. ;)

dist-upgrade installs packages that are "new" and not updates of currently installed packages - kernel updates are one example.

> Upgrades should always be approached sensibly and cautiously. You should read upgrade testimonials on these forums, create a full backup, and test any mission-critical scripts or services with the new release **before** you commit to an irreversible upgrade on a production machine.

+1. I've had issues with kernel updates and third party modules before but I think that was a problem with the newer kernels and the source of the drive I was trying to compile via DKMS. An updated driver fixed those issues.

---

