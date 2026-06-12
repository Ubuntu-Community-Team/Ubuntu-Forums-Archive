---
title: "i dont get all the fuss about snaps, i think it's great!"
date: 2023-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by m3ideh on 2023-05-18
i've heard people describe snaps as god-awful

but in the latest versions of ubuntu, the worst i've had to suffer is a small wait before opening programs

I actually think it's fine, and seems to be getting better as each version is released

---

### Post by TheFu on 2023-05-18
Nothing is perfect for everyone. If you have limited storage and/or limited RAM, like many chromebook users have, snaps are extremely wasteful with space and RAM.

If you work in a corporate environment with 'hot-desking', ... where there are computers at desks that you get based on your arrival order in the morning, then your HOME directory is likely mounted via NFS and place under /u1/{username} or /u2/{username} or /nfs/{username} or anywhere else, except /home.  Snaps don't work at all without a HOME directory under /home/.  In a corporation with thousands of servers and thousands of users, changing how your HOME directories get mounted just for 1 OS isn't going to happen.  Did you know that /home/ isn't a mandated requirement for user's HOME directories?  It is only recently that people late to Unix have decided that all account HOMEs should be under /home/.  Historically, that area was only for local user accounts, never when LDAP+NFS was used.

By default, snap packages update when they want.  This can interrupt a productive workday.  In a corporate environment, having the version of software changed without weeks-months of prior planning is completely unacceptable.  "New" isn't always better. Workflow changed need to be coordinated, tested, validated before being allowed to rollout and that would never happen on a weekday.  Snaps can be forced to delay deployments until the weekend, but that isn't the default.  

I know of no "approved" method to delay snap updates indefinitely.  That's probably just my ignorance.  I've tried to force some servers (deployed as snaps) to stay with a specific version that was stable, but those suggestions to the snap subsystem were ignored.  I needed to keep nextcloud on v24 after the default upgrade moved my deployment to v25.  Fine. that was my fault because I was set to get latest/stable channel updates.  I reverted to v24/stable and it seemed to take. Things started working again.  About a month later, I noticed an addon broke and discovered that my nextcloud had been pushed to v25 channel again.  Something is broke with snaps. That's not the issue, really. Software breaks all the time, but because snaps install automatically weekly, without any real schedule and seem to ignore specific channel requests, it is a no-go for corporate use.

I can see where snap's automatic install infrastructure would be very helpful for home non-power, desktop users and for IoT devices. For power-users and people in a corporate environment, the defaults are all wrong.   With this information, can you see why some people may not appreciate snaps being forced?

Snaps need to provide local control over all the major choices.  Until that is provided, I think they are _broken by design._

What is it that you prefer from snaps that wasn't already working with standard APT packages?

---

### Post by zebra2 on 2023-05-18
I like my Ubuntu 23.10 just exactly as installed.  No changes needed.  Snap and Deb both work just fine.  In addition, every corporate computer I have used was locked down tight.  It was setup to the conditions of the IT department that didn't ask for my advise.  Generally IT was too busy setting up printers and other hardware and dealing with virus's and employees clicking on fake emails to get involved in OS design theory.   
Snap is evolving just fine.  A bit of patience is in order. Some parts may need to be fixed but the concept is here to stay.  I do get that change can create adjustment problems though. Kind of like switching from Windows to Linux in the first place.  I'm just eager to see what the next crisis will be.

---

### Post by TheFu on 2023-05-18
23.10?  You live in the future?

---

### Post by ian-weisser on 2023-05-18
> **m3ideh said:**
> I actually think it's fine, and seems to be getting better as each version is released

Thanks for voicing the feelings of a lot of people!

---

### Post by zebra2 on 2023-05-18
Yes I do! but I disclosed that because the OP's statement was that Snap continues to improve. I can verify that it certainly does. FYI, 23.10 has only been on the buffet for circa 20 days and more than a third of the 5G has been updated.  I have been more than pleased with Ubuntu's security over the years and haven't even gone to the effort of activating much of it.  However any computer user has to be concerned about the advances the wrong doers have accomplished. I would hate to think that Canonical was sleeping at the wheel. There has been a release to release evolution to every new thing that has got us to today with Ubuntu. This snap thing is just a deja vu.  Soon enough it will be a forgotten problem. Or not!

---

### Post by exploder on 2023-05-20
The fuss about snaps revolves around the issues they have! The snap store NEVER updates by itself on my system, always have to run commands to stop the service so it will finally update. I can not uninstall apps using the snap store either, I end up using the command line or synaptic. 

They fixed the Firefox snap, it loads faster now. Can not say the same for other snaps. The snap store saves a copy of each installed snap, that takes up quite a lot of space! I ran a script to remove the older snaps, they had used over 1 GB of space! The only snap I had installed was VLC, the others were stock. 

I tried installing the Celluloid snap a couple of days ago, what a joke! The two snaps available were both the same version and not current... After installing the package, it took a while to load and the program displayed the github file name rather than the application name. Quality control issues perhaps?

If you are going to use a proprietary system shouldn't it have advantages over competing formats? Mint managed to integrate flatpacks into their update manager and you have control over their updates. Snaps update automatically and my system has completely crashed on three occasions because of this. This should NEVER happen, period. 

At the least, snaps should be opt in packages rather than being included by default.

---

### Post by zebra2 on 2023-05-20
> **exploder said:**
> 
At the least, snaps should be opt in packages rather than being included by default.

They are already opt-in.  The Gnome Software Store has every app in snap or deb or either format.  Take your pick.  Some are only available in snap, some are only available in deb. It is the app developers that are creating the apps.  Canonical provides Snap for whatever sandboxing is available.  Firefox is only available in Ubuntu as a Snap.  That's not a problem for me because I use Brave Browser that is available as both a snap and a deb but can be installed from the terminal via Brave's install scripts. I don't get the drive space issue. back in the nineties we had to download two hundred meg just to install a HP or Brother printer in Windows.  I am unaware of the space consumption due to snap on my multiple computers. It just doesn't matter because that is what drive space is for. It is the equivalent of protesting the demise of the CD-ROM 650M install disk.

---

### Post by exploder on 2023-05-20
> They are already opt-in. The Gnome Software Store has every app in snap or deb or either format. Take your pick. Some are only available in snap, some are only available in deb. It is the app developers that are creating the apps. Canonical provides Snap for whatever sandboxing is available. Firefox is only available in Ubuntu as a Snap. That's not a problem for me because I use Brave Browser that is available as both a snap and a deb but can be installed from the terminal via Brave's install scripts. I don't get the drive space issue. back in the nineties we had to download two hundred meg just to install a HP or Brother printer in Windows. I am unaware of the space consumption due to snap on my multiple computers. It just doesn't matter because that is what drive space is for. It is the equivalent of protesting the demise of the CD-ROM 650M install disk. 

Should we have two of every app just in case the new app is broken? It's a waste of space regardless of how much space you have. Every time the snap store is updated I have to run this in the command line.

> sudo pkill snap-store && sudo snap refresh snap-store 

Really, the install script can't do this? 

Who checks these snap packages? Who ever packaged Celluloid did a real crappy job! Two of the same package and the app name displays in the top panel as the github title complete with underscores... Isn't one of the advantages supposed to be up to date apps? Quality control is poor.

Here is the script to clean duplicate snaps.

[HTML]#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

LANG=C snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
[/HTML]

The problems with snaps far outweigh any benefit they have in their current form.

---

### Post by zebra2 on 2023-05-20
> **exploder said:**
> 
The problems with snaps far outweigh any benefit they have in their current form.

I don't know what release you are using but I don't do any of the things that you are reporting. On a day to day or even weekly scale I don't even think about snaps at all.  It is kind of like QT5 or Libhandy there is nothing I actually do aside from installing the app that I want in the first place.  I install them all except Brave from the Gnome Software Store. Some as deb and some as snap depending on what is available. After that I don't even think about it.

---

### Post by exploder on 2023-05-20
@ zebra2

Running 22.04 LTS since release. You would think an LTS release would not have these kinds of issues. If problems have been addressed in current releases, shouldn't the fixes be backported to the LTS?

---

### Post by zebra2 on 2023-05-20
@exploder
Just thinking about it, the point of the OP is that Snap is improving with newer versions.  I just happen to remember that when I was using 22.04 and also later on I was getting notice popups telling me that snap updates were needed or waiting to install. I was compelled at the time to do something about that but eventually just ignored it. Since upgrading to 23.10 I haven't received any of those notices. I'm not suggesting you upgrade to 23.10 because it is a still to be released OS, but I think that some of these improvements I am experiencing well be arriving in the former releases eventually or not.  Probably the cleaner and un-tampered you keep you system in the mean time may help.  I personally run a out of the box default Ubuntu/Gnome/Wayland OS.  As a rule of thumb I don't doctor it at all.

---

### Post by ian-weisser on 2023-05-20
> **exploder said:**
> If problems have been addressed in current releases, shouldn't the fixes be backported to the LTS?

No, often they should not.

The whole point of an LTS release, going back all the way to the first LTS in 2006, is that the software changes as little as possible. The reason for that minimal-change philosophy is to reduce the number and severity of new bugs that are invariably introduced.

So LTS doesn't break workflows. It doesn't change applications. It doesn't change settings. It doesn't surprise you.  

And minimal-change means that LTS releases get security patches (obviously). And LTS releases get high-priority bugfixes backported to them. But LTS releases DON'T usually get low-priority bugfixes backported to them.

---

### Post by exploder on 2023-05-20
> No, often they should not.

The whole point of an LTS release, going back all the way to the first LTS in 2006, is that the software changes as little as possible. It doesn't break workflows. It doesn't change applications. It doesn't change settings. It doesn't surprise you.

So LTS releases get security patches (obviously). And LTS releases get high-priority bugfixes backported to them. But LTS releases DON'T usually get low-priority bugfixes backported to them. 

The software center in 22.04 was broken on release and still is. Running a command EVERY time the software center is updated is more than a minor bug! 

I am clearly not alone in thinking the software center is a mess.

[https://distrowatch.com/weekly.php?issue=20220502#ubuntu](https://distrowatch.com/weekly.php?issue=20220502#ubuntu)

I can see why flatpacks are so much more popular!

---

### Post by ajgreeny on 2023-05-20
Just my 2 penny-worth; I have never ever in my 18 years of Ubuntu use felt a need to make use of the Software-Centre or whatever it used to be called.  Originally I used synaptic for most things but now tend to use that only for searching for packages, and apart from that I use terminal only for installs, updates and upgrades; it's so much quicker and simpler than any GUI application.

Incidentally, I have absolutely no snap packages nor any of the snap infrastructure on my machines which are all too old and slow with spinning rust hard disks on which snaps are far too slow to startup first time in any session.  Luckily for me there are alternative ways to install everything I want, either .deb packages, or Firefox using the direct download of the .tar.gz from Mozilla, one or two using PPAs or appimages, and finally a very few from source, just because I wanted to try out source installs.

---

### Post by poorguy on 2023-05-20
> **zebra2 said:**
> 
  Probably  the cleaner and un-tampered you keep you system in the mean time may  help.  I personally run a out of the box default Ubuntu/Gnome/Wayland  OS.  As a rule of thumb I don't doctor it at all.


I believe that makes the difference of having problems and not having problems.

I opt for the minimal install and use OOTB and I don't have any problems.

---

### Post by TheFu on 2023-05-20
> **zebra2 said:**
> They are already opt-in.  The Gnome Software Store has every app in snap or deb or either format.  Take your pick.  Some are only available in snap, some are only available in deb. It is the app developers that are creating the apps.  Canonical provides Snap for whatever sandboxing is available.  Firefox is only available in Ubuntu as a Snap.  That's not a problem for me because I use Brave Browser that is available as both a snap and a deb but can be installed from the terminal via Brave's install scripts. I don't get the drive space issue. back in the nineties we had to download two hundred meg just to install a HP or Brother printer in Windows.  I am unaware of the space consumption due to snap on my multiple computers. It just doesn't matter because that is what drive space is for. It is the equivalent of protesting the demise of the CD-ROM 650M install disk.

Snaps waste disk storage.  By default, 3 copies of every snap are installed and retained.  It is possible to set that to just 2.  I've done that.  Eating an extra GB on a 16 GB total storage system **is** a huge issue.  I have a few systems with 16GB SSDs.  Should those be thrown away?  One is less than 10 yrs old. The other less than 15 yrs. Both support VTx and are 64-bit.

I'd love to have the non-snap version of lxd and lxc in ubuntu.  Canonical is the dev team for those and only releases them as snaps.  Soon, debian stable will have a non-Snap version of lxd/lxc and I'll be switching when that comes.  I do like lxc/lxd.

I have hundreds of 650 CDROMs and 3.5inch floppies too.  Great that you are so modern.  Fortunately we don't have to throw out old hardware to keep using current versions of Linux, unlike those other commercial OSes.  Win11 support will be tied to systems that support TPM 2.  OSX will be (if it already hasn't been) dropped for x86 computers.  I like having a choice.  Just wish Canonical was pro-choice, but it is their OS. They can do what they want.  

Taking away options will drive the users where snap package aren't flexible enough for use away from Ubuntu. More and more completely new-to-Linux users inside my LUG are choosing other distros.  I find myself recommending other distros so these users don't have to deal with the limitations of snaps while they are still learning.  When multi-app workflows don't work, new users get frustrated.  Snaps are still causing problems due to how only specific app-to-app interfaces are supported ... that and the entire "you can only use files in your HOME" problem.  Try explaining that to new users trying to access their existing Samba files over the network, when it doesn't work for any snap installed programs. They get frustrated and don't want to deal with the problem, ever.  For them, the answer is to use a different distro.  

On my desktop, I already switches away over snaps.  Next up, my 20-ish servers.  That will take years, but only 2 really **need** to switch to Debian. The rest are virtual and don't need lxc/lxd support inside to do their job.

Ubuntu does so many things really, really, well. It is extremely flexible for all needs at all levels ... except with snap constraints. Sigh.

---

### Post by ian-weisser on 2023-05-20
> **TheFu said:**
> More and more completely new-to-Linux users inside my LUG are choosing other distros.

In my own LUG, I have watched the tide rise and fall several times. Some years folks are talking up their current favorite. Other years most are running Ubuntu. It comes and goes.

---

### Post by ardouronerous on 2023-05-21
Snap still needs improvements though, some quality of life improvements, here are some bug reports and I and others have made:

[Bug #2017926 "Unused content snaps not autoremoved"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2017926")
[Bug #2018626 "Unused dependencies not removed when uninstalling a snap program"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2018626")
[Bug #2018627 "[Feature Rquest] '--no-cache' command to not cache during uninstallation of snaps"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2018627")

I don't really have a problem with Canonical forcing snap on it's users, but I do have a problem if the snap platform isn't ready and it's being forced on us, and it's not ready based on the problems I experienced. I really want to love and use snaps, but Canonical needs to fix these issues:


1. Uninstalling snaps is a pain in the ass. In apt and flatpak, they have options to auto-remove the software and it's dependencies, but snap doesn't have that, you have to know beforehand what snaps were installed alongside the main snap and one by one uninstall these snaps.


As a test, I've installed KompoZer. Before I installed KompoZer, this is what my snap list output looks like:


```
Name               Version          Rev    Tracking         Publisher   Notes
bare               1.0              5      latest/stable    canonical&#10003;  base
core               16-2.58.3        14946  latest/stable    canonical&#10003;  core
core20             20230404         1879   latest/stable    canonical&#10003;  base
firefox            112.0.2-1        2605   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004    0+git.6f39565    140    latest/stable  canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.59.1           18933  latest/stable    canonical&#10003;  snapd
```


After I installed KompoZer, these dependencies were installed: core18 and gtk2-common-themes.


After I uninstalled KompoZer, the dependencies for KompoZer were still listed in `snap list`:


```
Name                Version          Rev    Tracking         Publisher   Notes
bare                1.0              5      latest/stable    canonical&#10003;  base
core                16-2.58.3        14946  latest/stable    canonical&#10003;  core
core18              20230320         2721   latest/stable    canonical&#10003;  base
core20              20230404         1879   latest/stable    canonical&#10003;  base
firefox             112.0.2-1        2605   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004     0+git.6f39565    140    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes   0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
gtk2-common-themes  0.1              13     latest/stable    canonical&#10003;  -
snapd               2.59.1           18933  latest/stable    canonical&#10003;  snapd
```


Snap leaves behind unused dependencies. Snap doesn't have an auto-remove unused dependencies command, you have to remember what dependencies were installed and remove them one by one, which leads me to my second problem.


2. No history.log for snaps. Apt has history.log, which records what dependencies were installed alongside the software, which I use as a reference in uninstalling software and it's dependencies, in snap, you have to do this manually:


```
sudo snap install kompozer && snap tasks --last=install --abs-time >> /home/ardouronerous/.snap_history.log
```


This command will create a log file that will tell me what dependencies were installed alongside KompoZer, so if I want to uninstall KompoZer, I can uninstall it and all it's unused dependencies using this log file as reference. A log file should be created by default without user intervention.


3. Snap keeps a cache of uninstalled software so you don't have to download the snaps if you decide to reinstall. You could see this as a feature, but if you are low on disk space, this becomes a problem, to remedy this issue, as noted in this [AskUbuntu post]("https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache"), users have to run this command in the Terminal to clear the snap cache:


```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```


This cleared about 2GB of space for me. A '--no-cache' command to not cache during uninstallation of a snap should be an option for users who are low on disk space.

---

### Post by TheFu on 2023-05-21
> **ian-weisser said:**
> In my own LUG, I have watched the tide rise and fall several times. Some years folks are talking up their current favorite. Other years most are running Ubuntu. It comes and goes.

Agreed.  The big shifts, if you want to call them that, were when Unity DE became the default and much, much, less so, when systemd was forced.  
With systemd, there really wasn't anywhere else to go, since all the major distros took it.  In 5-10 more yrs, systemd might be production ready ... or perhaps replaced by something more like init.d/, which I miss, but not enough to jump to niche distros like MXLinux or devian.

With Unity, Canonical provided other DEs for the masses, so nobody was really forced to use it.

Snaps are different.  There are other distros as viable choices as Canonical **mandates** snaps more and more.  OTOH, if the constraint settings became locally controlled and snap packages become optional, organizations like mine wouldn't need ... be forced ... to seek alternatives.  It is a little sad, actually.  

Flatpaks provide local control, so we know it can be done. It is purely a management choice. Every non-trivial setup is a little different. They aren't cookie cutter when integrated into a corporate infrastructure.

---

### Post by mikodo on 2023-05-22
> **TheFu said:**
> 
I can see where snap's automatic install infrastructure would be very helpful for home non-power, desktop users ... 

I don't think so, when I read things like Debian's Security Warning, on Flatpaks and Snaps:

[https://wiki.debian.org/Flatpak#Security_Warning_Note](https://wiki.debian.org/Flatpak#Security_Warning_Note)

---

### Post by lammert-nijhof on 2023-05-22
I like snaps and I use many of them without any issues, like Firefox; Caprine; Whatsie; Skype; Thunderbird and LibreOffice. LibreOffice loads slow, but I can live with it, since afterwards I spend a lot of time on that document. 
I still run Ubuntu 16.04 ESM and I love to run the latest stable snaps of Firefox; Thunderbird and LibreOffice. 

I think most of my snaps run great and if there is an issue with an update I can roll it back and block that version. I love the extra security provided by the snaps, one secure repository and snaps having the security advantages of containers. 

There are always Canonical haters, that have a hobby in biting the hand, that feeds them. We have seen it with Unity; Snaps and recently Ubuntu Pro. Consequently I'm very proud that I combined all those 3 products in my Ubuntu 16.04 ESM Virtualbox VM, that I use exclusively for my financial stuff.

---

### Post by ardouronerous on 2023-05-22
> **lammert-nijhof said:**
> I think most of my snaps run great and if there is an issue with an update I can roll it back and block that version. I love the extra security provided by the snaps, one secure repository and snaps having the security advantages of containers.

I agree, snap runs great now, there was a time when Firefox's snap would take longer to load but that was fixed by Canonical in later revisions, but what I'm criticizing snap on is unease of uninstallation of snap apps and it's dependencies.

Back in 20.04 I used snaps, but when I uninstalled some snap packages that I no longer needed, my thoughts are that when I uninstall snaps, it would also restore my disk space to before I installed the snap packages, but that didn't happen, I only got back half of my previous disk space.

I researched the issue and found this [post]("https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache"), snap apparently keeps a cache of uninstalled snaps in '***/var/lib/snapd/cache/***' so you don't have to download the snaps if you decide to reinstall, so users have to run this command to clear the cache:

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

Problem solved, surely, but no, my previous disk space isn't restored at all, then I ran `***snap list***` and discovered that snap keeps unused dependencies even after I uninstalled the snaps that were using them, I realized that in order to fully uninstall a snap package and it's dependencies, I have to remember what was installed alongside the snap package and removed them one by one and I did, I was able to get back my previous disk space.

My problems with snap is that snap lacks a  `***sudo apt autoremove***` command and also a lacks a **history.log**. In apt, apt has a **history.log**, which records what dependencies were installed alongside the software which I use as a reference in uninstalling software and it's dependencies, snap doesn't have this, I have to do it manually:

```
sudo snap install kompozer && snap tasks --last=install --abs-time >> /home/ardouronerous/.snap_history.log
```

Canonical needs to fix these issues.

---

### Post by poorguy on 2023-05-22
> **ardouronerous said:**
> 
I researched the issue and found this [post]("https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache"), snap apparently keeps a cache of uninstalled snaps in '***/var/lib/snapd/cache/***' so you don't have to download the snaps if you decide to reinstall, so users have to run this command to clear the cache:

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```



Am I understanding correctly if I just want to clear Snap cache without removing any Snaps this command will do it. 

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

---

### Post by ardouronerous on 2023-05-22
> **poorguy said:**
> Am I understanding correctly if I just want to clear Snap cache without removing any Snaps this command will do it. 

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

After uninstalling a snap, a copy of the uninstalled snap is stored in ***/var/lib/snapd/cache/*** and overtime after many uninstallations, it gets populated, mine was about 2GB, so clearing this restored 2GB of disk space.

---

### Post by poorguy on 2023-05-22
> **poorguy said:**
> Am I understanding correctly if I just want to clear Snap cache without removing any Snaps this command will do it. 

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

> **ardouronerous said:**
> After uninstalling a snap, a copy of the uninstalled snap is stored in ***/var/lib/snapd/cache/***  and overtime after many uninstallations, it gets populated, mine was  about 2GB, so clearing this restored 2GB of disk space.

So that command only clears Snap cache for removed Snaps and not installed Snaps.

---

### Post by ardouronerous on 2023-05-22
> **poorguy said:**
> So that command only clears Snap cache for removed Snaps and not installed Snaps.

AFAIK, yes. On the same thread, there's a command to remove old revisions of snaps:

>  Also note that snap does not only keep removed snaps, but also up to  20 older versions of that snap (standard is 3 versions). So for me,  cleaning up those remaining copies resulted in far more reclaimed  storage than cleaning the cache (5GB vs 1GB). [This website]("https://www.debugpoint.com/2021/03/clean-up-snap/") has a nice script which I used for that:

 ```
#!/bin/bash
#Removes old revisions of snaps
#CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu
LANG=en_US.UTF-8 snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done

```                                                                                         [URL="https://askubuntu.com/a/1378620"]

Share[/URL]     [Improve this answer]("https://askubuntu.com/posts/1378620/edit")     Follow     [edited Dec 13, 2021 at 16:07]("https://askubuntu.com/posts/1378620/revisions")     

                                              answered Dec 1, 2021 at 15:15     
              [URL="https://askubuntu.com/users/1097837/bjrne"][IMG]https://www.gravatar.com/avatar/502d68816b3e7521374f3ae571aa5b4c?s=64&d=identicon&r=PG[/IMG]
[/URL]
              [bjrne]("https://askubuntu.com/users/1097837/bjrne")                      34222 silver badges8 

---

### Post by poorguy on 2023-05-23
I saw Ask Ubuntu link.
[https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache](https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache)

Somehow I missed this link which explains a lot more.
[https://www.debugpoint.com/clean-up-snap/](https://www.debugpoint.com/clean-up-snap/)



Thanks

---

### Post by zebra2 on 2023-05-23
I tested the script on on of my 23.10 systems. It worked exactly according to the discription given and my snapd folder is exactly the same size that it was to start.  In addition I have 20 Gig of my 34 Gig root free.  I use a swap partition so I don't have a swapfile taking up space in my /root.  

I'm going to get away from this entire subject. It is unreasonable for me to think that snap should not take up the space that it needs to work properly and I don't think it is doing any more than that. It is using 2.6 Gig of my 34Gig root and I don't see that as a problem in terms of a threat to my boot process.  My 34 Gig root that I allocated in my setup for the purpose that it was intended by Canonical is working properly.

But thanks for the script link. I put it in my /bin.

---

### Post by VMC on 2023-05-23
> **poorguy said:**
> Am I understanding correctly if I just want to clear Snap cache without removing any Snaps this command will do it. 

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

Is the above command in a script? If not, then why not just:
```
sudo rm -rf /var/lib/snapd/cache/*'
```

---

### Post by TheFu on 2023-05-24
> **zebra2 said:**
> But thanks for the script link. I put it in my /bin.

I hope you mean ~/bin/, not /bin/   Polluting places where the package manager installs OS files is a poor practice. If you want to make it available for everyone, use /usr/local/bin/ for the script, just be certain that you include /usr/local/ in your backups.

---

### Post by zebra2 on 2023-05-24
> **TheFu said:**
> I hope you mean ~/bin/, not /bin/   Polluting places where the package manager installs OS files is a poor practice. If you want to make it available for everyone, use /usr/local/bin/ for the script, just be certain that you include /usr/local/ in your backups.

I don't want to hijack this thread but FYI the scripts in my /bin are personal scripts not related to OS.  I have a path in bashrc that routes my sh requests to /bin.  I use the development versions of Ubuntu for my main system and I do a couple of dozen of ISO reinstall's every six months. Therefor I don't want my script folder in a partition that is regularly reformatted.  My /home is on it's own partition and I don't format it during a reinstall. Incidentally I have this /home folder duplicated on multiple systems for convenience reasons and really don't think I'm going to lose anything.

---

### Post by TheFu on 2023-05-24
> **zebra2 said:**
> I don't want to hijack this thread but FYI the scripts in my /bin are personal scripts not related to OS.  I have a path in bashrc that routes my sh requests to /bin.  I use the development versions of Ubuntu for my main system and I do a couple of dozen of ISO reinstall's every six months. Therefor I don't want my script folder in a partition that is regularly reformatted.  My /home is on it's own partition and I don't format it during a reinstall. Incidentally I have this /home folder duplicated on multiple systems for convenience reasons and really don't think I'm going to lose anything.

/bin has 2300+ OS programs in it.  Could you be confusing /bin - an absolute path with $HOME/bin?  Lurkers are here and will see these posts for the next 10+ yrs, so being accurate and correct matters.

---

