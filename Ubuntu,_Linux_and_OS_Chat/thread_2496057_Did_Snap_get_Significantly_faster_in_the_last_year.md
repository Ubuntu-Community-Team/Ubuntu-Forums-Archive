---
title: "Did Snap get Significantly faster in the last year..?"
date: 2024-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by heliophane on 2024-03-12
Howdy all!

I recently installed 23.10 on my laptop after being forced to use Windows by a class at my uni. I haven;t touched Ubuntu since around November of 2022, and I gotta say, snaps feel MUCH faster to launch than I remember. I used to be the kind of guy that would only user snap on servers and stick to flatpak for the most part on desktop, but man, the speed of Firefox especially has made me much more charitable to snaps. Has anyone else experienced this? Props to the snapcraft team, even in the last year snap feels like it's come a long way

Props the the desktop team as a whole actually, with how amazing 23.10 is, 24.04 is shaping up to be the best LTS yet, and I couldn't be happier to be back home with Ubuntu :)

---

### Post by Dennis N on 2024-03-12
I notice this too in 23.10. The Firefox snap opens in a fraction of a second - almost instantly, so I am now keeping it to use. Previously, I had been switching Firefox to Flatpak.

---

### Post by erlkonig on 2024-04-30
Snap still rejects my NFS-mounted directory because it isn't in the non-standard /home, not that it would matter because big sites can't put all their users in /home period, because that stupid approach doesn't scale.  Snap devs have heard about this before, but apparently can't think outside of Mom&Pop companies or something.  Back to finding a debian or just compiling Thunderbird and Firefox again.  Until they fix this, snaps are a non-starter for many.

And it's stupid to ship an OS with snaps that don't work because a couple of developers can't see outside of their own limited experience.  24.04 is a failure here for this reason, and there are tons of glitches even in the basic UI to add the sadness.

---

### Post by deadflowr on 2024-04-30
> **erlkonig said:**
> Snap still rejects my NFS-mounted directory because it isn't in the non-standard /home, not that it would matter because big sites can't put all their users in /home period, because that stupid approach doesn't scale.  Snap devs have heard about this before, but apparently can't think outside of Mom&Pop companies or something.  Back to finding a debian or just compiling Thunderbird and Firefox again.  Until they fix this, snaps are a non-starter for many.

And it's stupid to ship an OS with snaps that don't work because a couple of developers can't see outside of their own limited experience.  24.04 is a failure here for this reason, and there are tons of glitches even in the basic UI to add the sadness.

Did you set the homedirs option:
[https://snapcraft.io/docs/home-outside-home](https://snapcraft.io/docs/home-outside-home)

> Back to finding a debian or just compiling Thunderbird and Firefox again.

Mozilla now provides a repository for firefox, at least (not sure about thunderbird)
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-deb-package-for-debian-based-distributions)

---

### Post by #&amp;thj^% on 2024-04-30
> **deadflowr said:**
> 
Mozilla now provides a repository for firefox, at least (not sure about thunderbird)


It's there:
> 
Firefox ESR and Thunderbird stable builds
PPA description

Mozilla Team's Firefox stable + 115 ESR and Thunderbird 115 stable builds

Support for Ubuntu 16.04 / 18.04 ESM is included for 115 ESR based releases only.

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

[S]Now that said, snap still wants to upgrade it to a snap, I'm still working with them to get this cleaned up. (I have not found a pin priory that works just yet)
To explain more with the PPA and snap disabled and removed, it will still try and pull the snap system back[/S].....Grrrr.

Also this to mow over: [https://www.linuxcapable.com/how-to-install-thunderbird-on-ubuntu-linux/](https://www.linuxcapable.com/how-to-install-thunderbird-on-ubuntu-linux/)

Ha It's fixed now ie:
Before:
```
apt policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 2:1snap1-0ubuntu3
  Version table:
     2:1snap1-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```
Now with no special Pin:
```
  apt policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:115.10.1+build1-0ubuntu0.24.04.1~mt1
  Version table:
     2:1snap1-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
     1:115.10.1+build1-0ubuntu0.24.04.1~mt1 1001
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu noble/main amd64 Packages

```
:P
```
systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)

```

---

### Post by gezzer2 on 2024-05-01
Ubuntu 24.04 seems to have certain snaps running in the background.
you can check which ones in setting/apps ..

---

### Post by TheFu on 2024-05-01
> **erlkonig said:**
> Snap still rejects my NFS-mounted directory because it isn't in the non-standard /home, not that it would matter because big sites can't put all their users in /home period, because that stupid approach doesn't scale.  Snap devs have heard about this before, but apparently can't think outside of Mom&Pop companies or something.  Back to finding a debian or just compiling Thunderbird and Firefox again.  Until they fix this, snaps are a non-starter for many.

And it's stupid to ship an OS with snaps that don't work because a couple of developers can't see outside of their own limited experience.  24.04 is a failure here for this reason, and there are tons of glitches even in the basic UI to add the sadness.

Testify!  Enterprises use NFS for home directories across many different platforms/architectures.  Expecting them to change just for 1 OS is uncooperative, at best.  I see the homedirs option, so perhaps this issue is solved!  

A way around the firefox snap problem, if you have it, is to use the Firefox ESR PPA.

I installed Xubuntu 24.04 on Sunday in front of 20 people at my LUG.  Within 20 minutes, it locked up 3 times.  I accepted all the defaults (next/next/next/....)  There's a known bug immediately after install, so it was just 2 unknown times that it locked up.  After the last one, we decided 24.04 wasn't ready for use and needed a month or 2 before we'd try again.  I have Lubuntu 24.,04 and Ubuntu Server to try still. I'm hopeful.  This was my first use of a v6.x kernel. Don't know if that is related or not.

Ok, just tried to install Lubuntu 24.04.  The installer locked up about 8% into copying files.  To be fair, I did a custom disk layout.  I'll try it without a custom layout.  Need to go kill the installer now.  Trying again with all defaults....  so far, so good.  No lockups in the first 10 minutes.
```
$ df -Th -x tmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   25G  6.8G   17G  30% /
```

I did some standard things post install. Switched to networkd from network manager, purged nano, purged network-manager*, set a static IP, changed the mouse so focus follows it and patched the system.  Also setup the sudoers so 3 specific patch commands don't prompt for a password.  All that went well. nice and stable.

Launched firefox - which took 7 seconds - and felt harassed by the questions. Had to press "skip" like 5 times just to get to a browser window. Firefox won't let me save downloads to /tmp/  /tmp/ is THE place for downloads.  No doubt, a snap problem that the snap team decided wasn't to be allowed.

Just saw the homedirs snap config thing.  For small sites, that could be a good solution.  For larger sites with 20-150 different storage areas for HOME depending on the username, I have to wonder if there's an arbitrary limit for the number of HOME NFS mounts allowed.
```
~$ sudo snap set system homedirs=/home,/u1/h,/export/home
~$ sudo snap get system homedirs
/home,/u1/h,/export/home

```
I still need to do more testing, but that is a start.  _homedirs_ option should work for 24.04, since it has snap 2.62+24.04build1.  22.04 and 20.04 both have snap version 2.62 as well, so it could work. I need to test more. The first complaint about this that I remember seeing the snap team downplay was in 2017.  Think they did some things to address NFS issues last year too. Nice.

Now the only real remaining complaint is that locally configured storage needs to be configurable.  I want all snaps to have read-write access to /tmp/ and some other NFS locations not under /mnt/ nor /media/.  Did I miss those changes too?    I'm encouraged, if the HOME directory issue has been solved.

---

### Post by TheFu on 2024-05-01
[https://forum.snapcraft.io/t/accessing-tmp-from-snaps/22384](https://forum.snapcraft.io/t/accessing-tmp-from-snaps/22384) doesn't provide a solution to accessing /tmp/. Just says to use a different directory instead.  Too bad.

---

