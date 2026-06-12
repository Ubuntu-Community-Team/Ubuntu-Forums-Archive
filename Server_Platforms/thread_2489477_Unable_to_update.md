---
title: "Unable to update"
date: 2023-08-01
forum: Server Platforms
---

### Post by debruti on 2023-08-01
Hello all, greetings from a spaniard in Japan!

I'm trying to update my ubuntu server 20.04 but I get this message: 

```
root@bloodstone:~# apt-get update
Get:1 http://archive.ubuntu.com focal Release.gpg [1554B]
Get:2 http://archive.ubuntu.com focal-updates Release.gpg [1554B]
Get:3 http://archive.ubuntu.com focal-security Release.gpg [1554B]
Get:4 http://old-releases.ubuntu.com groovy Release.gpg [819B]
Get:5 http://old-releases.ubuntu.com groovy-updates Release.gpg [819B]
Get:6 http://old-releases.ubuntu.com groovy-backports Release.gpg [819B]
Get:7 http://archive.canonical.com focal Release.gpg [1554B]
Hit http://old-releases.ubuntu.com groovy Release
Get:8 http://archive.ubuntu.com focal-backports Release.gpg [1554B]
Hit http://archive.ubuntu.com focal Release
Get:9 http://archive.ubuntu.com focal-updates Release [112kB]
Ign http://old-releases.ubuntu.com groovy Release
Ign http://archive.ubuntu.com focal Release
Ign http://jp.archive.ubuntu.com breezy-updates Release.gpg
Ign http://jp.archive.ubuntu.com breezy Release.gpg
Hit http://old-releases.ubuntu.com groovy-updates Release
Hit http://archive.canonical.com focal Release
Ign http://old-releases.ubuntu.com groovy-updates Release
Ign http://archive.canonical.com focal Release
Ign http://jp.archive.ubuntu.com breezy-updates Release
Hit http://old-releases.ubuntu.com groovy-backports Release
Ign http://old-releases.ubuntu.com groovy-backports Release
Ign http://archive.canonical.com focal/partner Packages
Ign http://jp.archive.ubuntu.com breezy Release
Ign http://old-releases.ubuntu.com groovy/main Packages
Ign http://old-releases.ubuntu.com groovy/restricted Packages
Ign http://old-releases.ubuntu.com groovy/universe Packages
Ign http://old-releases.ubuntu.com groovy/multiverse Packages
Ign http://jp.archive.ubuntu.com breezy-updates/main Packages
Ign http://jp.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://jp.archive.ubuntu.com breezy-updates/main Sources
Ign http://jp.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://old-releases.ubuntu.com groovy-updates/main Packages
Ign http://archive.canonical.com focal/partner Sources
Get:10 http://archive.ubuntu.com focal-security Release [112kB]
Ign http://archive.ubuntu.com focal-updates Release
Ign http://jp.archive.ubuntu.com breezy/universe Packages
Ign http://jp.archive.ubuntu.com breezy/universe Sources
Err http://jp.archive.ubuntu.com breezy-updates/main Packages
  404 Not Found [IP: 91.189.91.81 80]
Err http://jp.archive.ubuntu.com breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.91.81 80]
Err http://jp.archive.ubuntu.com breezy-updates/main Sources
  404 Not Found [IP: 91.189.91.81 80]
Hit http://archive.canonical.com focal/partner Packages
Ign http://old-releases.ubuntu.com groovy-updates/restricted Packages
Ign http://old-releases.ubuntu.com groovy-updates/universe Packages
Ign http://old-releases.ubuntu.com groovy-updates/multiverse Packages
Ign http://old-releases.ubuntu.com groovy-backports/main Packages
Get:11 http://archive.ubuntu.com focal-backports Release [107kB]
Ign http://archive.ubuntu.com focal-security Release
Err http://jp.archive.ubuntu.com breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.91.81 80]
Err http://jp.archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.91.81 80]
Ign http://old-releases.ubuntu.com groovy-backports/restricted Packages
Ign http://old-releases.ubuntu.com groovy-backports/universe Packages
Ign http://old-releases.ubuntu.com groovy-backports/multiverse Packages
Hit http://old-releases.ubuntu.com groovy/main Packages
Hit http://old-releases.ubuntu.com groovy/restricted Packages
Hit http://old-releases.ubuntu.com groovy/universe Packages
Ign http://archive.ubuntu.com focal/main Packages
Ign http://archive.ubuntu.com focal-backports Release
Err http://jp.archive.ubuntu.com breezy/universe Sources
  404 Not Found [IP: 91.189.91.81 80]
Hit http://archive.canonical.com focal/partner Sources
Hit http://old-releases.ubuntu.com groovy/multiverse Packages
Hit http://old-releases.ubuntu.com groovy-updates/main Packages
Hit http://old-releases.ubuntu.com groovy-updates/restricted Packages
Hit http://old-releases.ubuntu.com groovy-updates/universe Packages
Hit http://old-releases.ubuntu.com groovy-updates/multiverse Packages
Hit http://old-releases.ubuntu.com groovy-backports/main Packages
Hit http://old-releases.ubuntu.com groovy-backports/restricted Packages
Hit http://old-releases.ubuntu.com groovy-backports/universe Packages
Hit http://old-releases.ubuntu.com groovy-backports/multiverse Packages
Ign http://archive.ubuntu.com focal/restricted Packages
Ign http://archive.ubuntu.com focal/universe Packages
Ign http://archive.ubuntu.com focal/multiverse Packages
Ign http://archive.ubuntu.com focal/main Sources
Ign http://archive.ubuntu.com focal/restricted Sources
Ign http://archive.ubuntu.com focal/universe Sources
Ign http://archive.ubuntu.com focal/multiverse Sources
Ign http://archive.ubuntu.com focal-updates/main Packages
Ign http://archive.ubuntu.com focal-updates/restricted Packages
Ign http://archive.ubuntu.com focal-updates/universe Packages
Ign http://archive.ubuntu.com focal-updates/multiverse Packages
Ign http://archive.ubuntu.com focal-updates/main Sources
Ign http://archive.ubuntu.com focal-updates/restricted Sources
Ign http://archive.ubuntu.com focal-updates/universe Sources
Ign http://archive.ubuntu.com focal-updates/multiverse Sources
Ign http://archive.ubuntu.com focal-security/main Packages
Ign http://archive.ubuntu.com focal-security/restricted Packages
Ign http://archive.ubuntu.com focal-security/universe Packages
Ign http://archive.ubuntu.com focal-security/multiverse Packages
Ign http://archive.ubuntu.com focal-security/main Sources
Ign http://archive.ubuntu.com focal-security/restricted Sources
Ign http://archive.ubuntu.com focal-security/universe Sources
Ign http://archive.ubuntu.com focal-security/multiverse Sources
Hit http://archive.ubuntu.com focal/main Packages
Ign http://archive.ubuntu.com focal-backports/main Packages
Ign http://archive.ubuntu.com focal-backports/restricted Packages
Ign http://archive.ubuntu.com focal-backports/universe Packages
Ign http://archive.ubuntu.com focal-backports/multiverse Packages
Ign http://archive.ubuntu.com focal-backports/main Sources
Ign http://archive.ubuntu.com focal-backports/restricted Sources
Ign http://archive.ubuntu.com focal-backports/universe Sources
Ign http://archive.ubuntu.com focal-backports/multiverse Sources
Hit http://archive.ubuntu.com focal/restricted Packages
Hit http://archive.ubuntu.com focal/universe Packages
Hit http://archive.ubuntu.com focal/multiverse Packages
Hit http://archive.ubuntu.com focal/main Sources
Hit http://archive.ubuntu.com focal/restricted Sources
Hit http://archive.ubuntu.com focal/universe Sources
Hit http://archive.ubuntu.com focal/multiverse Sources
Get:12 http://archive.ubuntu.com focal-updates/main Packages [1064kB]
Get:13 http://archive.ubuntu.com focal-updates/restricted Packages [40.9kB]
Get:14 http://archive.ubuntu.com focal-updates/universe Packages [917kB]
Get:15 http://archive.ubuntu.com focal-updates/multiverse Packages [9598B]
Get:16 http://archive.ubuntu.com focal-updates/main Sources [710kB]
Get:17 http://archive.ubuntu.com focal-updates/restricted Sources [64.8kB]
Get:18 http://archive.ubuntu.com focal-updates/universe Sources [420kB]
Get:19 http://archive.ubuntu.com focal-updates/multiverse Sources [28.0kB]
Get:20 http://archive.ubuntu.com focal-security/main Packages [774kB]
Get:21 http://archive.ubuntu.com focal-security/restricted Packages [38.9kB]
Get:22 http://archive.ubuntu.com focal-security/universe Packages [750kB]
Get:23 http://archive.ubuntu.com focal-security/multiverse Packages [8170B]
Get:24 http://archive.ubuntu.com focal-security/main Sources [362kB]
Get:25 http://archive.ubuntu.com focal-security/restricted Sources [64.8kB]
Get:26 http://archive.ubuntu.com focal-security/universe Sources [229kB]
Get:27 http://archive.ubuntu.com focal-security/multiverse Sources [15.8kB]
Get:28 http://archive.ubuntu.com focal-backports/main Packages [43.4kB]
Get:29 http://archive.ubuntu.com focal-backports/restricted Packages [40B]
Get:30 http://archive.ubuntu.com focal-backports/universe Packages [15.4kB]
Get:31 http://archive.ubuntu.com focal-backports/multiverse Packages [40B]
Get:32 http://archive.ubuntu.com focal-backports/main Sources [10.9kB]
Get:33 http://archive.ubuntu.com focal-backports/restricted Sources [40B]
Get:34 http://archive.ubuntu.com focal-backports/universe Sources [11.6kB]
Get:35 http://archive.ubuntu.com focal-backports/multiverse Sources [40B]
Fetched 5919kB in 17s (331kB/s)
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.81 80]
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.81 80]
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.91.81 80]
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.91.81 80]
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.81 80]
Failed to fetch http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  404 Not Found [IP: 91.189.91.81 80]
Reading package lists... Error!
E: Malformed provides line
E: Error occurred while processing apt (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_focal_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

I've tried deleting the file[COLOR=#0000cd] /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_focal_main_binary-i386_Packages[/COLOR]
I have also tried to add 8.8.8.8 as a secondary nameserver (the main one being our LAN gateway). I've also tried running commands like apt-get clean, etc.
I am going to reboot the server by the end of this day, but I wanted to know if anybody could please suggest anything else that I should try?

Thank you very much in advance!

---

### Post by deadflowr on 2023-08-01
Your sources are a mess.
You need to remove the breezy and possibly the groovy sources.
However, as you now have groovy sources, it may no longer be a focal 20.04 install anymore.
But you definitely want to remove the breezy listings.

Have you ever updated it since you added the groovy sources?

If no, then there is a chance to redeem it as a focal (2004) install.
In that case you could just delete the entries for those two in your sources.list file.

If yes, then it's a groovy system now. And the best options are to either backup and do a clean install, or push through it and try to update it to 22.04.
First option would be quicker, since to upgrade to 22.04 would require upgrading it thrice from 20.10 to 21.04 to 21.10 to 22.04.

If you're not sure, then first option to backup and do a clean install is still the best option.
When you do not know, trying to fix it can, and usually does, make a bigger mess and waste more time than it really should.

---

### Post by debruti on 2023-08-01
Thanks for your reply!

I just deleted the breezy entries from the [COLOR=#000000]sources.list file. The problem is that I'm still getting the same error at the end (no other errors before, though):

```
[/COLOR]root@bloodstone:/etc/apt# apt-get updateGet:1 http://archive.ubuntu.com focal Release.gpg [1554B]
Get:2 http://archive.ubuntu.com focal-updates Release.gpg [1554B]
Get:3 http://archive.ubuntu.com focal-security Release.gpg [1554B]
Get:4 http://archive.ubuntu.com focal-backports Release.gpg [1554B]
Hit http://archive.ubuntu.com focal Release
Ign http://archive.ubuntu.com focal Release
Get:5 http://archive.canonical.com focal Release.gpg [1554B]
Get:6 http://archive.ubuntu.com focal-updates Release [112kB]
Get:7 http://old-releases.ubuntu.com groovy Release.gpg [819B]
Get:8 http://old-releases.ubuntu.com groovy-updates Release.gpg [819B]
Hit http://archive.canonical.com focal Release
Ign http://archive.canonical.com focal Release
Get:9 http://archive.ubuntu.com focal-security Release [112kB]
Get:10 http://old-releases.ubuntu.com groovy-backports Release.gpg [819B]
Hit http://old-releases.ubuntu.com groovy Release
Ign http://archive.ubuntu.com focal-updates Release
Ign http://archive.canonical.com focal/partner Packages
Ign http://old-releases.ubuntu.com groovy Release
Get:11 http://archive.ubuntu.com focal-backports Release [107kB]
Ign http://archive.ubuntu.com focal-security Release
Hit http://old-releases.ubuntu.com groovy-updates Release
Hit http://old-releases.ubuntu.com groovy-backports Release
Ign http://old-releases.ubuntu.com groovy-updates Release
Ign http://archive.canonical.com focal/partner Sources
Ign http://old-releases.ubuntu.com groovy-backports Release
Ign http://archive.ubuntu.com focal/main Packages
Ign http://archive.ubuntu.com focal/restricted Packages
Ign http://archive.ubuntu.com focal/universe Packages
Ign http://archive.ubuntu.com focal/multiverse Packages
Ign http://archive.ubuntu.com focal/main Sources
Ign http://archive.ubuntu.com focal/restricted Sources
Ign http://archive.ubuntu.com focal/universe Sources
Ign http://archive.ubuntu.com focal/multiverse Sources
Ign http://archive.ubuntu.com focal-updates/main Packages
Ign http://archive.ubuntu.com focal-backports Release
Ign http://archive.ubuntu.com focal-updates/restricted Packages
Ign http://archive.ubuntu.com focal-updates/universe Packages
Ign http://archive.ubuntu.com focal-updates/multiverse Packages
Ign http://archive.ubuntu.com focal-updates/main Sources
Ign http://archive.ubuntu.com focal-updates/restricted Sources
Ign http://archive.ubuntu.com focal-updates/universe Sources
Ign http://archive.ubuntu.com focal-updates/multiverse Sources
Ign http://archive.ubuntu.com focal-security/main Packages
Ign http://archive.ubuntu.com focal-security/restricted Packages
Ign http://old-releases.ubuntu.com groovy/main Packages
Hit http://archive.canonical.com focal/partner Packages
Ign http://archive.ubuntu.com focal-security/universe Packages
Ign http://archive.ubuntu.com focal-security/multiverse Packages
Ign http://archive.ubuntu.com focal-security/main Sources
Ign http://archive.ubuntu.com focal-security/restricted Sources
Ign http://archive.ubuntu.com focal-security/universe Sources
Ign http://archive.ubuntu.com focal-security/multiverse Sources
Hit http://archive.ubuntu.com focal/main Packages
Ign http://old-releases.ubuntu.com groovy/restricted Packages
Ign http://old-releases.ubuntu.com groovy/universe Packages
Ign http://old-releases.ubuntu.com groovy/multiverse Packages
Hit http://archive.canonical.com focal/partner Sources
Hit http://archive.ubuntu.com focal/restricted Packages
Hit http://archive.ubuntu.com focal/universe Packages
Hit http://archive.ubuntu.com focal/multiverse Packages
Hit http://archive.ubuntu.com focal/main Sources
Hit http://archive.ubuntu.com focal/restricted Sources
Hit http://archive.ubuntu.com focal/universe Sources
Hit http://archive.ubuntu.com focal/multiverse Sources
Get:12 http://archive.ubuntu.com focal-updates/main Packages [1064kB]
Ign http://old-releases.ubuntu.com groovy-updates/main Packages
Ign http://old-releases.ubuntu.com groovy-updates/restricted Packages
Ign http://old-releases.ubuntu.com groovy-updates/universe Packages
Ign http://old-releases.ubuntu.com groovy-updates/multiverse Packages
Ign http://archive.ubuntu.com focal-backports/main Packages
Ign http://archive.ubuntu.com focal-backports/restricted Packages
Ign http://archive.ubuntu.com focal-backports/universe Packages
Ign http://archive.ubuntu.com focal-backports/multiverse Packages
Ign http://archive.ubuntu.com focal-backports/main Sources
Ign http://archive.ubuntu.com focal-backports/restricted Sources
Ign http://archive.ubuntu.com focal-backports/universe Sources
Ign http://archive.ubuntu.com focal-backports/multiverse Sources
Get:13 http://archive.ubuntu.com focal-updates/restricted Packages [40.9kB]
Ign http://old-releases.ubuntu.com groovy-backports/main Packages
Get:14 http://archive.ubuntu.com focal-updates/universe Packages [917kB]
Ign http://old-releases.ubuntu.com groovy-backports/restricted Packages
Ign http://old-releases.ubuntu.com groovy-backports/universe Packages
Ign http://old-releases.ubuntu.com groovy-backports/multiverse Packages
Hit http://old-releases.ubuntu.com groovy/main Packages
Hit http://old-releases.ubuntu.com groovy/restricted Packages
Hit http://old-releases.ubuntu.com groovy/universe Packages
Hit http://old-releases.ubuntu.com groovy/multiverse Packages
Hit http://old-releases.ubuntu.com groovy-updates/main Packages
Hit http://old-releases.ubuntu.com groovy-updates/restricted Packages
Hit http://old-releases.ubuntu.com groovy-updates/universe Packages
Hit http://old-releases.ubuntu.com groovy-updates/multiverse Packages
Hit http://old-releases.ubuntu.com groovy-backports/main Packages
Hit http://old-releases.ubuntu.com groovy-backports/restricted Packages
Hit http://old-releases.ubuntu.com groovy-backports/universe Packages
Hit http://old-releases.ubuntu.com groovy-backports/multiverse Packages
Get:15 http://archive.ubuntu.com focal-updates/multiverse Packages [9598B]
Get:16 http://archive.ubuntu.com focal-updates/main Sources [710kB]
Get:17 http://archive.ubuntu.com focal-updates/restricted Sources [64.8kB]
Get:18 http://archive.ubuntu.com focal-updates/universe Sources [420kB]
Get:19 http://archive.ubuntu.com focal-updates/multiverse Sources [28.0kB]
Get:20 http://archive.ubuntu.com focal-security/main Packages [774kB]
Get:21 http://archive.ubuntu.com focal-security/restricted Packages [38.9kB]
Get:22 http://archive.ubuntu.com focal-security/universe Packages [750kB]
Get:23 http://archive.ubuntu.com focal-security/multiverse Packages [8170B]
Get:24 http://archive.ubuntu.com focal-security/main Sources [362kB]
Get:25 http://archive.ubuntu.com focal-security/restricted Sources [64.8kB]
Get:26 http://archive.ubuntu.com focal-security/universe Sources [229kB]
Get:27 http://archive.ubuntu.com focal-security/multiverse Sources [15.8kB]
Get:28 http://archive.ubuntu.com focal-backports/main Packages [43.4kB]
Get:29 http://archive.ubuntu.com focal-backports/restricted Packages [40B]
Get:30 http://archive.ubuntu.com focal-backports/universe Packages [15.4kB]
Get:31 http://archive.ubuntu.com focal-backports/multiverse Packages [40B]
Get:32 http://archive.ubuntu.com focal-backports/main Sources [10.9kB]
Get:33 http://archive.ubuntu.com focal-backports/restricted Sources [40B]
Get:34 http://archive.ubuntu.com focal-backports/universe Sources [11.6kB]
Get:35 http://archive.ubuntu.com focal-backports/multiverse Sources [40B]
Fetched 5919kB in 8s (694kB/s)
Reading package lists... Error!
E: Malformed provides line
E: Error occurred while processing apt (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_focal_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[COLOR=#000000]
```

To be honest, it wasn't me who installed this server, but I'm sort of in charge of it now lol. I remember adding manually the groovy sources last week trying to apply solutions from here and there, but it seems that I've messed it up. I'll back up everything and I will try to set it up in a newer machine with the needed settings (not too big, it's hosting just a small asterisk service).

Thanks again for your time![/COLOR]

---

### Post by guiverc on 2023-08-01
Why do you have [http://archive.canonical.com/](http://archive.canonical.com/)  as you should be using [http://archive.ubuntu.com/](http://archive.ubuntu.com/) for Ubuntu.

You can look at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) if you want alternate mirrors.

A correctly updated Ubuntu 20.04 system should report itself as 20.04.6, but I suspect your system may not; due in part to *broken* or *poorly maintained* sources.

I hope you keep the system offline.  *groovy* was 20.10 which **was **the first [*interim*] release on the two year *development* cycle working towards 22.04; ie. it won't help a 20.04 system (*just add security holes unless you upgraded to 22.04* *which you'd started doing by adding groov**y; though if you only added it recently you won't have damaged anything - except potentially via your other non-focal sources*)

---

### Post by debruti on 2023-08-01
[FONT=lucida sans unicode]Ok, I'm starting to realize the mess that I've been making instead of solving the issue...

The system was not poorly maintained... it wasn't being maintained at all! #-o

Regarding [http://archive.ubuntu.com/](http://archive.ubuntu.com/)[/FONT][COLOR=#000000][FONT=lucida sans unicode] it's throwing a 404 Not found message when I run the apt-get update command (apart of the previous error).
[SIZE=2]
I also think that the best option it's going to be the backup and setup in a newer machine, because...[/SIZE][/FONT]

[/COLOR]> root@bloodstone:/etc/apt# lsb_release -a
LSB Version: n/a
Distributor ID: Ubuntu
Description: Ubuntu (The Breezy Badger Release)
Release: 5.10
Codename: breezy

So it wasn't a 20.04 as I was told, but waaaaaaaaaaaaaaay older. Sorry everyone. I should have started there. Apologies! ](*,)

---

### Post by guiverc on 2023-08-01
From your provided details, you're [Ubuntu 5.10 (Breezy)]("https://fridge.ubuntu.com/2005/10/19/5-10-server-released/"), which was the 2005-October release (ie. 5.10 tells you the 2005-October release due to *year.month* format; you add 2000 to year).

It had a single upgrade path, to Ubuntu 6.06 LTS, which closed when 6.06 reached its EOL in 2011.  (see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) which gives the EOL date as April 2007.


Your system should **only** used offline, you're so far EOL & have no upgrade path; I'd recommend saving all data you have (*whilst offline*), and then testing *supported* releases of Ubuntu in VM or other hardware and explore restoration of that data onto applications on a system that is 16+ years newer & thus *supported*.  This is exactly as you realized yourself anyway.

---

### Post by debruti on 2023-08-01
Indeed.

Thankfully, it has only a small asterisk with just a few extensions, so it's not a big deal.

Thank you everyone for all your time and help, I really appreciate it.

---

### Post by LHammonds on 2023-08-01
Keep in mind that with bare-metal installs, you can do a test-run with a newer system such as 22.04 by installing it on your PC in a virtual environment to see what steps are generally needed to setup the system in a similar way and test to see if what you backed up can be restored and work in a newer system.

Once you become familiar with a new install and how to restore the data with confidence, it will be much less stress to wipe out the old hardware and re-install a fresh OS on top of it.

LHammonds

---

### Post by debruti on 2023-08-01
True, but we are going to get a newer desktop PC to work as the new asterisk server. My boss was laughing out loud when I told him about how old the ubuntu version was and he said "yeah, I remember that we installed it and, since it worked, we barely touched it... until now!" :lol:
I think that I will set up a cron job that runs the update and upgrade commands by the end of each Friday or Saturday mornings or something like that.

---

### Post by MAFoElffen on 2023-08-03
Just FYI for members on systems using this in their sources.list
```

deb http://archive.canonical.com <release> <whatever>

```
That repo is for partners and vendors... My experience with using that repo is that it is also used by HP, Lenovo, and HP for device drivers. especially for their servers. It also contains non-standard "ports" packages.

If you go to [http://archive.canonical.com/dists/focal/partner/](http://archive.canonical.com/dists/focal/partner/), that is a partner "ports" repo... For other ARCH Platforms.

What "IS" this Server related to being "hardware platform" wise?

---

### Post by LHammonds on 2023-08-05
> **debruti said:**
> True, but we are going to get a newer desktop PC to work as the new asterisk server. My boss was laughing out loud when I told him about how old the ubuntu version was and he said "yeah, I remember that we installed it and, since it worked, we barely touched it... until now!" :lol:
I think that I will set up a cron job that runs the update and upgrade commands by the end of each Friday or Saturday mornings or something like that.
We don't have that luxury (allowed risk) where I work.  To conform to required standards, all servers must not have any outstanding security patches older than 30 days.   So every 2 weeks, we make sure 1/2 of the oldest patches are applied.

---

### Post by debruti on 2023-08-07
> **LHammonds said:**
> We don't have that luxury (allowed risk) where I work.  To conform to required standards, all servers must not have any outstanding security patches older than 30 days.   So every 2 weeks, we make sure 1/2 of the oldest patches are applied.

I agree. The thing is that since the company is small and this asterisk server is still working fine the people working before myself didn't think that it would be needed to do very much more apart of closing all the non-used ports and implementing some rules at the firewall. This is a case of "don't worry, I don't think that anything will happen..." until it happens.

Anyway, I am still taking some time to set up the new one, so as I said earlier once I'm done with that I will set up a cron job to run the apt-get update && apt-get upgrade command at least once a week.

Thanks a lot for your replies!

---

