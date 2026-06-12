---
title: "Extended Support Maintenance and Those Magnificent Snaps"
date: 2021-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2021-10-01
I moved my "work" to Virtual Machines. Recently I detected, that I could get a free Extended Support Maintenance for Ubuntu 14.04 and 16.04 and I subscribed to it. Begin of the year I used Ubuntu 16.04 for my Banking/PayPal/Newegg/Ebay work, but I moved it to Ubuntu Mate 20.04 before April. Now with the support till Apr 2026 I decided to move it back. Unfortunately the applications will not be updated, so I decided to use snaps for Firefox and LibreOffice. In this way I can run the latest versions of those Apps on Ubuntu 16.04 :)

I run Ubuntu 16.04 LTS in Virtualbox on top of Ubuntu 21.04 on OpenZFS 2.0. I use a Ryzen 3 2200G and 16GB DDR4 with a lz4 compressed 512GB SP nvme-SSD (3400/2300MB/s). The whole desktop did cost me a whopping $349. By the way the whole Ubuntu 16.04 virtual disk is encrypted :)

The first time I load Firefox or LibreOffice after a boot of the Hosts OS and Ubuntu VM, it will take 2 to 3 seconds, afterwards I load both Apps in  <1 second, even when I reboot the VM. The whole complaints about snaps have a high anti-canonical and anti-science sentiment. Also the first download takes somewhat more time, but for the update canonical only sends binary patches with the changed content, which saves transfer time and which gives them the possibility to save the replaced content in a snapshot. So if the developer makes an error, you can revert locally to the previous working version of the app in ~0 seconds after pressing return :) 

Just learn about snaps and at least the following sub commands: snap list; snap find; snap install; snap refresh and snap revert. If you run Software and the Software Updater Apps, they will automate most of that work. Also the central repository is an advantage, because the integration between repository and OS is superior. Fortunately I don't have to shop in many partly dubious websites like with Windows, till I find the flatpak/snap I'm looking for :(

---

### Post by grahammechanical on 2021-10-01
> The whole complaints about snaps have a high anti-canonical and anti-science sentiment.

You may be right. I will not argue with you about that point of view. We have choice. And I am not paid to do PR for Canonical.

Regards

---

### Post by ajgreeny on 2021-10-01
In my view the biggest problem with snaps is simply the complete lack of control that the user has on saving or use of any files if it is outside your own home, and the removal of any ability to choose whether, and when, to upgrade the snap applications.

I do not use NFS but I believe that snaps are unable to see or use such storage, making them pretty useless for some users.

As **grahammechanical** says, we do have choice, and can if we wish, choose to remove all snaps and use alternative packages as I have done, having had problems with chromium-snap when I first installed it using apt, which installed the snap version, which was impossible to use in the manner I wished to use.

---

### Post by lammert-nijhof on 2021-10-01
1. You have complete control over the snap updates, you can choose between N times per day (default is 4) or the time in the day, the week, the month or probably even the year, it should do the update. 
2. The Network File System (NFS) can be used with any Linux client also ones using Appimage; Flatpak or Snaps. I use snaps with Virtualbox Shared Folders and with the Samba Network File System. It is a complete different level of abstraction.

I agree with your last point. It is your choice, you can do it the easy way or the difficult way.

---

### Post by ajgreeny on 2021-10-02
My comments in post #3 were partly from my own experience with chromium, and I accept that situation may have moved on by now, and also regarding NFS from the experie ces and knowledge of TheFu in his post at [https://ubuntuforums.org/showthread.php?t=2467199&p=14059735&viewfull=1#post14059735](https://ubuntuforums.org/showthread.php?t=2467199&p=14059735&viewfull=1#post14059735)

I fully respect his huge knowledge of things such as NFS so I now wonder who is right and who is wrong; or have things moved on a lot from the time when I last tried snaps?

---

### Post by lammert-nijhof on 2021-10-02
TheFu does not explain anything about NFS and why it is not working with snaps. I explained, why it should work. Applications work with file systems by calling OS functions. If the OS and Application use the same API version it works, besides Linux is very fanatical in keeping the APIs compatible over the years. Packaging like snap or flatpak have no influence on those APIs. However if the creator of the snap or flatpak makes and error and e.g includes an outdated package to call NFS, then it might not work. The same is true for the home directory, if you want it work, you have to follow the rules as defined by Linux. Snaps or flatpaks follow those rules, so people who deviate from those rules will run into problems using snaps or flatpaks. That is the effect of standardization, adapt or become obsolete. 

I give a simple example of a real issue with snaps and flatpaks.  LibreOffice supports language packs and using the classical system you can add and delete languages. In flatpaks and snaps those languages are included in the snap or flatpak and you can't change them anymore. That is why they have approx 10 languages in those snaps or flatpaks.  They will find a better solution for it and hopefully the same for all package formats.
In LibreOffice I installed Dutch; English German and Spanish, because I use those languages occasionally. I can get all those languages except Dutch in the snap, so trade off was:
- to live with the latest LibreOffice release in a snap, because I probably will not use Dutch with Newegg, US/Chinese Ebay; my Spanish Bank and Paypal or
- use the old Ubuntu 16.04 version of LibreOffice, one that is not really updated anymore.

---

### Post by TheFu on 2021-10-03
> **lammert-nijhof said:**
> TheFu does not explain anything about NFS and why it is not working with snaps. I explained, why it should work. Applications work with file systems by calling OS functions. If the OS and Application use the same API version it works, besides Linux is very fanatical in keeping the APIs compatible over the years. Packaging like snap or flatpak have no influence on those APIs. Of course if the creator of the snap of flatpak can use an outdated package to call NFS, then it might not work. The same is true for the home directory, if you want it work, you have to follow the rules as defined by the kernel and followed by the snap or flatpak. That is the effect of standardization. 

I give a simple example LibreOffice supports language packs and using the classical system you can add and delete languages. In flatpaks and snaps those languages are included in the snap or flatpak and you can't change them anymore. That is why they have approx 10 languages in those snaps or flatpaks.  They will find a better solution for it.

The snap folks have hard-coded specific locations like /home, /media/ and /mnt for the possible use of snap data.  Only /home is automatically allowed in most snaps.  Not all snaps allow access to /media/ or /mnt/ - the packager has to pick that option, if they want it. Many teams do not.
 [https://forum.snapcraft.io/t/snaps-and-nfs-home/438](https://forum.snapcraft.io/t/snaps-and-nfs-home/438) tried to explain the issue with NFS and snaps.
> NFS support is tagged for 2.29 and I hope it can be a part of the release.  Current snapd is 2.51.1+20.04ubuntu2 on 20.04.  So it should be working.  From reading some other discord posts, it appeared that there was no plan to ever support NFS at all in snaps.

Normally, I use autofs to mount that disk to /d/D1/ .... trying to print a PDF to the same disk, using NFS, using the same browser, fails.  They hard coded /media/ and /mnt/ and /home/.   Programming 101 says NEVER, EVER, do that.  I'm sure that every programmer was taught not to hard code directories, unless it was an industrial, embedded, device involved.

In general, I don't mount stuff under /media/ because that is the wrong place for most storage.  Same for /mnt/  Those are both the wrong places.
From: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)
```
    /media	Mount points for removable media such as CD-ROMs (appeared in FHS-2.3 in 2004).
    /mnt 	Temporarily mounted filesystems. 

```
NFS isn't removable media nor temporary. The "official" LFSH doc was updated last in 2015, I think. 

Businesses mount NFS home directories under 
[LIST]
[*]/export/u/{username} or 
[*]/export/home/{username} or 
[*]/u/{username} or 
[*]/nfs/u/{username} or 
[*]something like that.  
[/LIST]
At places with thousands of users, it is common to split up user HOME directories under different NFS mounts .... /u1/{username},  /u2/{username}, ... to spread the I/O over different disks.  None of those places can use Ubuntu due to snaps, without avoiding a few specific, snap-only, packages.

When I'm on a system with user HOME directories on NFS mounts, let's say /export/home/tf ... and try to run any snap.  There's the error:
```
$ echo $HOME
/export/home/tf

tf@romulus:~$ snap list
Name      Version   Rev    Tracking       Publisher     Notes
core18    20210722  2128   latest/stable  canonical&#10003;    base
core20    20210702  1081   latest/stable  canonical&#10003;    base
lxd       4.18      21497  latest/stable  canonical&#10003;    -
snapd     2.51.7    13170  latest/stable  canonical&#10003;    snapd
wormhole  0.12.0    349    latest/stable  snapcrafters  -

tf@romulus:~$ lxc list
Command 'lxc' is available in '/snap/bin/lxc'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxc: command not found

tf@romulus:~$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.

```
That link is pretty clear.  /home is hard coded. [https://forum.snapcraft.io/t/support-for-non-home-homedirs/11209](https://forum.snapcraft.io/t/support-for-non-home-homedirs/11209) 
They don't provide a "why".  The snap team's workaround is to make the HOME use /home/.

If I change to a local user with a HOME that is local and /home.
```
$ sudo -i -u tflocal 

tflocal@romulus:~$ echo $HOME
/home/tflocal

tflocal@romulus:~$ snap list
Name      Version   Rev    Tracking       Publisher     Notes
core18    20210722  2128   latest/stable  canonical&#10003;    base
core20    20210702  1081   latest/stable  canonical&#10003;    base
lxd       4.18      21497  latest/stable  canonical&#10003;    -
snapd     2.51.7    13170  latest/stable  canonical&#10003;    snapd
wormhole  0.12.0    349    latest/stable  snapcrafters  -

tflocal@romulus:~$ lxc list
+-----------+---------+---------------------+------+-----------+-----------+
|   NAME    |  STATE  |        IPV4         | IPV6 |   TYPE    | SNAPSHOTS |
+-----------+---------+---------------------+------+-----------+-----------+
| back-2004 | RUNNING | 172.22.22.16 (eth0) |      | CONTAINER | 0         |
+-----------+---------+---------------------+------+-----------+-----------+

```
Why can't snaps just the storage location from the getent or getpwent() tools? The entire OS does.

The only workaround for not having user HOME directories under /home is to put them there using a **bind mount** and modify the password DB to reflect the /home/ location. A symlink from /nfs/thefu --> /home/thefu is not sufficient.

Tried to start chromium-brower in a pwd on NFS storage:
```
/media/d1$ !chrom
chromium-browser 
cannot open path of the current working directory: Permission denied
```

I'm very happy that NFS seems to work now with snaps, if one location is used. Don't know when that happened.
I need to look up how to prevent snaps from updating and the command to update them like I do during patch sessions.  I looked for that about a year ago and found a blog article from someone on the snap team which said it wasn't possible. At least that's my memory today.

Looks like this is the answer to have snaps only updated on Saturdays:
```
$ sudo snap set system refresh.timer=sat
```
I don't know if that will actually work or not.  Seems we NEED to know about another package manager and there isn't a choice because it doesn't honor the settings we've put into place for APT.

I'm not actually anti-snap and it does appear they've been listening to complaints.  Seeing that chromium automatically has the non-HOME storage enabled is better than what I recall from last year when I looked at all this stuff.  I need control over the directory locations AND over where HOME directories are located.  For a single-user, or non-corporate setup, these things may seem minor.  We're looking at switching distros over Canonical's mandated use of snaps. It is that serious.  Strict defaults are fine. That isn't really the complaint. We need local control.

---

### Post by lammert-nijhof on 2021-10-03
You are not complaining about the snap mechanism itself, but about the errors or choices made by the creators of specific snaps. More specifically, they did not allow the type of home directory structure on NFS envisaged by some administrators. Snaps and flatpak are de-facto standards, they make live much easier for developers and distro maintainers, but they take away some freedom for the users. That is what happens with new standards, in 20 years nobody will remember these discussions. I know, since I started in ICT in 1969. 

I have comparable issues with LibreOffice. Note that I have the same issue with the deb and snap versions.  I hate the way, they force you to open "remote" files. I never use that BS. I take nautilus and right click the remote file or I drag the remote file in LibreOffice. Afterwards they are in the recent file list. You will find comparable solutions for your directory structure issues.

---

