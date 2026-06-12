---
title: "Ubuntu Server 18.04 - Difference between &quot;live&quot; and &quot;alternative&quot;"
date: 2018-05-02
forum: Server Platforms
---

### Post by LHammonds on 2018-05-02
The [Ubuntu 18.04 Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") mentions the following as a difference between the "live" and "alternative" server ISO images:

> The next generation Subiquity server installer, brings the comfortable live session and speedy install of Ubuntu Desktop to server users at last.

N.B., If you require LVM, RAID, multipath, vlans, bonds, or the ability to re-using existing partitions, you will want to continue to use the alternate installer which can be downloaded from [http://cdimage.ubuntu.com/releases/18.04/release/](http://cdimage.ubuntu.com/releases/18.04/release/)

Yet there are other differences beyond that.  Anyone that has information about those differences, please reply here so we can keep a running tab on what they are and to also find out if they are just oversites during the ISO creation or if they are intentional.

[SIZE=5]Difference #1
[/SIZE]Changing the hostname will revert back to the original name after reboot on an install using "live" unless the following is changed:

Edit "/etc/cloud/cloud.cfg" and change "preserve_hostname" to "true"

[SIZE=5]Difference #2[/SIZE]
On a "live" install, the following mount exists:

```
/dev/loop0 88704 88704 0 100% /snap/core/4486
```

[SIZE=5] Difference #3[/SIZE]
On the "live" install the settings for auto updates are in /etc/apt/apt.conf.d/20auto-upgrades while on "alternative" install they are in a different config file (just grep /etc for "Update-Package-Lists" string)

[SIZE=5]Difference #4[/SIZE]
The "live" install asks the user on the first login to install a language pack:

```
sudo apt-get install language-pack-en
```

[SIZE=5]Difference #5[/SIZE]
The "cloud-init" package is not installed by default with the "alternative" ISO but it is with the "live" ISO.

[SIZE=5]Difference #6[/SIZE]
In partition setup the defaults are different.  But "Guided - Use entire  Disk" is one partition on the alt, and 2 partitions with one for Grub  BIOS on the Live install.

[SIZE=5]Difference #7[/SIZE]
Netplan has saner defaults.  On the Live CD, all network cards are  enumerated in /etc/netplan/50-cloud-init.yaml, and any unplugged result  in a 5 minute delay on start up.  The alt has only selected network  cards are enumerated in  /etc/netplan/01-netcfg.yaml so there is no  ridiculous boot delay.

[SIZE=5]Difference #8[/SIZE]
Regarding packages, the Live version has cloud-init and eatmydata and gdisk and thermald. The alt has the English languages packs installed.

[SIZE=5]Difference #9[/SIZE]
>> INSERT HERE <<


LHammonds

---

### Post by bluexmas on 2018-05-02
Thank you [COLOR=#000000]LHammonds for the follow up topic.

[/COLOR][SIZE=5][COLOR=#000000]Difference #3[/COLOR][/SIZE][COLOR=#000000]

On the "live" install the settings for auto updates are in [/COLOR]/etc/apt/apt.conf.d/20auto-upgrades while on "alternative" install they are in a different config file (just grep /etc for "Update-Package-Lists" string)

[COLOR=#000000][SIZE=5]Difference #4[/SIZE]
[/COLOR][COLOR=#000000]
The "live" install asks the user on the first login to install a language pack:

[/COLOR]> sudo apt-get install language-pack-en

This never happens on "alternative" install but it's somehow understandable, subiquity installer never asks for the country.

**Off topic**: I am working on migration procedures for all my servers to 18.04. I use kvm and while the host servers os will be provided by the datacenter, it's really hard to decide what to use between the "live" and "alternative" on the guests. (I am really curious what the datacenter will deploy on the hosts). The concern is what if Canonical will properly maintain the "live" one in the future, since they refer to "alternative" as "[http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/)[COLOR=#333333][FONT=&amp] (Less Popular Ubuntu Images)"?

i'll get back with more feedback after I test my procedures on "alternative" (lamp stack, pdns, pureftp, postfix, dovecot, spamassassin, nfs, etc).[/FONT][/COLOR]

---

### Post by LHammonds on 2018-05-03
> **bluexmas said:**
> 
**Off topic**: I am working on migration procedures for all my servers to 18.04. I use kvm and while the host servers os will be provided by the datacenter, it's really hard to decide what to use between the "live" and "alternative" on the guests. (I am really curious what the datacenter will deploy on the hosts). The concern is what if Canonical will properly maintain the "live" one in the future, since they refer to "alternative" as "[http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/)[COLOR=#333333][FONT=&amp] (Less Popular Ubuntu Images)"?[/FONT][/COLOR]
Thanks for the info, it is now added to 1st post.

I can't imagine they would eventually strip away the ability to configure RAID and LVM during install.  If they do, I'll be forced to use a different flavor of Linux.  All of my servers utilize LVM and that practice keeps my servers online...and growth issues are many times handled automatically using my "check space" scripts to auto-grow the FS if it gets low on space.

My plan to upgrade the dozen 16.04 servers I have is to install new servers, get the software working on it, then copy the data over to make sure it will run as the new server.  Then do the same thing after testing and documentation is done to migrate the data to the new server and simply swap the IP address to make the new 18.04 live.  Depending on the size of the data and how I migrate it, downtime is usually not much more than a couple minutes.  I NEVER do in-place upgrades.  I like having good install and migration documentation that I make for the CURRENT version of the production systems.

LHammonds

---

### Post by bluexmas on 2018-05-03
yes, I follow up the same path of upgrading, I build up new machines, document the install procedures and test, then migrate the platforms and data. I'll also purchase coffeelake hosts, so I wanna run 18.04 on the hosts also, since I need the new versions of qemu and libvirt.

I deployed the "alternative" today and tested out the procedures, the behaviour is the same as on "live". I only finished the documentation for lamp stack, pdns+poweradmin and pureftp. mail server components are a bit of a challenge and will work on the procedures during the weekend, I have other commitments by then.

I asked the datacenter what iso they will use for the bare-metal they provide and got a response, that I want to share here:

> [COLOR=#000000][FONT=Helvetica]Dear Client,[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]we used the non live server iso to create our image. The live server image does use the new subiquity installer and does not allow to do a minimal install.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Kind regards

[/FONT][/COLOR]I have time in the next couple of weeks to observe the behaviour of the "alternative" iso, since I think it will be the winner to deploy on the guests. Will get back here on any relevant extra information I will have.

Our forum colleague cruzer001 opened up a nice bug on launchpad :)
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1768900](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1768900) [COLOR=#000000][FONT=Helvetica]

[/FONT][/COLOR]

---

### Post by LHammonds on 2018-06-04
Added entry #5 about cloud-init based on [this thread](https://ubuntuforums.org/showthread.php?t=2393393).  I also verified that cloud-init was not installed on my 18.04 servers that were installed with the alternative ISO image.

LHammonds

---

### Post by bbiandov on 2018-10-26
ok but the latest LTS is ONLY published as live and I can't seem to find the traditional installer, just the ISO the way it was before. They only publish ubuntu-18.04.1-live-server-amd64.iso
 now?

Thanks

---

### Post by Morbius1 on 2018-10-27
[http://cdimage.ubuntu.com/releases/18.04.1/release/ubuntu-18.04.1-server-amd64.iso](http://cdimage.ubuntu.com/releases/18.04.1/release/ubuntu-18.04.1-server-amd64.iso)

---

### Post by houstonbofh on 2019-03-27
In partition setup the defaults are different.  But "Guided - Use entire Disk" is one partition on the alt, and 2 partitions with one for Grub BIOS on the Live install.  This is on the 18.04-2 release.  Will compare packages next...

---

### Post by houstonbofh on 2019-03-27
Netplan has saner defaults.  On the Live CD, all network cards are enumerated in /etc/netplan/50-cloud-init.yaml, and any unplugged result in a 5 minute delay on start up.  The alt has only selected network cards are enumerated in  /etc/netplan/01-netcfg.yaml so there is no ridiculous boot delay.

---

### Post by houstonbofh on 2019-03-27
Packages

The Live version has cloud-init and eatmydata and gdisk and thermald.
The alt has the English languages packs installed.

---

### Post by phantom_ on 2019-06-09
BUG!!!
For PXE installations; Live image fails displaying a *cannot download from mirror* message. However, there is NO 404 Not Found HTTP error at the installation file server. The only message is found at tty4 which displays the syslog message **bad d-i Packages file from local mirror**.
The above problem does NOT exist with the alternative image PXE install. This is the related [Stack Overflow]("https://stackoverflow.com/questions/50689224/ubuntu-18-04-bad-d-i-packages-file-from-local-mirror") page

---

