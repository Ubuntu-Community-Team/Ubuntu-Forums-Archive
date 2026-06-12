---
title: "Ubuntu 21.10"
date: 2021-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by eipapp on 2021-11-02
Just curious as to how many folks are actually excited enough about Gnome 40 to upgrade or install Ubuntu 21.10.
I for one, and I may be missing something, do NOT intend to upgrade and am not sure what all the excitement is about.
Basically it seems that they moved the work spaces from a vertical view to a horizontal view, so like a big deal ???
I don't know, like I said maybe I just don't get it.
Would like others input but for now, I'm staying with Ubuntu 20.04.
Any thoughts, comments ???

---

### Post by T6&amp;sfpER35% on 2021-11-02
i myself also wouldn't use anything else than a LTS release.

---

### Post by grahammechanical on 2021-11-02
Some people get drawn to the "It new" and "Its the latest" claim. Some are new to Ubuntu and when they go to Ubuntu.com and click Downloads they are offered the newest release and the last LTS release. Ubuntu 20.04 is eighteen months older than 21.10. So, I imagine that they choose the new release and not the old release.

In the past I always upgraded to the next version. Now I have an LTS release as my main working OS and a development release as well as some other distributions. At some point we will have to upgrade to 22.04 (LTS) and that will have Gnome 40 and bits of Gnome 41. I have no idea how the Gnome developers reach their design decisions. I certainly would not want to be part of the design discussion group.

Regards

---

### Post by GhX6GZMB on 2021-11-02
I stick with LTS. It works, and that's the main point. I've never suffered from "upgradeitis".

---

### Post by guiverc on 2021-11-02
I *bump* my box about 30 hours after release; so I'm no longer on *impish* on this box, but have been using *jammy* for weeks now.

I'm involved with QA, so it's beneficial for this box to be on the *development* cycle; which is likely the only reason I'm using it. Personally I like *stability* and *consistency* (no changes!).

I'm using Lubuntu/LXQt, but I also have Xubuntu/XFCE & Ubuntu/GNOME installed, so when I need a change; I login using another DE for a couple of day(s)/session(s).

Qt 5.12.8 LTS has an *non-security* bug that I'm impacted by with Lubuntu because of how I've positioned my monitors.. That maybe a reason for me not to use 20.04 (& Lubuntu/LXQt) but it doesn't impact my other DEs (GNOME or Xfce which are GTK3). The *non-security* nature meant the fix wasn't back-ported; though in the *focal* cycle I discovered you can change settings many times & the issue goes away for good! *(&* *leading devs to theorize it's an improperly initialized value; it was found & fixed in later Qt releases*).

GNOME has changed; I'll agree with that, but to me it still feels like GNOME, which isn't my cup of tea, so I use it for a session or two, then return to my normal LXQt. I prefer Xfce to GNOME; Xfce doesn't change much :P

I can't say I like or dislike the GNOME changes; it's just different to me. GNOME maybe efficient, and I can use it, but I still go back to LXQt or Xfce.


Note: my experience isn't the same; as the changes are gradual being on the *development* release, rather than logging in every six months and getting those six months of changes all together.  My *release-upgrade* *bump* from 21.10 to *jammy* consisted only of a version name change (*it didn't even require me to reboot :P*)

---

### Post by TheFu on 2021-11-02
20.04 - THAT's too new for me.  Too many forced config/backend changes.
21.xx switched to Wayland which breaks many of my workflows. There is fallback to X11 still.

New is the enemy of stable.  Who wants to install a new OS every 6 months?  Not me.  Rather than move to a new release, even on relatively new hardware that isn't supported by 5.10 or earlier kernels, I've elected to only use a newer, unsupported, kernel as the lessor of all the evils in "new". Guess that's the price for having a Ryzen 5xxxG APU.  On 1+ yr old hardware, the normal kernels from the supported LTS work great. Further, there are fewer patches to older systems.  Every week, a list of updates for each release gets posted.  You'll note that newer releases, with newer software have many more updates for bugs and security needs than older releases.

```
$ uname -r
5.11.20-051120-generic
```
But I must say that glxgears on the Ryzen APU is 1200-1600 fps compared to less than 60 fps running an nVidia GT 1030 - on a Ryzen 2xxx. I would never have expected such a huge performance difference in those two GPUs.  Both are very stable running 18.04.
```
$ uptime                    # 5.11.x unsupported kernel
 20:43:00 up 10 days,  7:53,  3 users,
$ uptime                               # 5.4.x HWE kernel.
 20:43:13 up 9 days,  7:29, 
```
Very stable. Both.

GUIs don't matter to me.  I don't use DEs. They are all too bloated.  Still rocking **fvwm** here.

---

### Post by Dennis N on 2021-11-03
I have all supported releases as VMs. I'm interested in them, but not excited. I see no stability problems with Ubuntu 21.10 after upgrading from 21.04 which was equally stable.
.

---

### Post by ugjka on 2021-11-03
glxgears is not a benchmark tool

---

### Post by lammert-nijhof on 2021-11-04
My Host OS moved to Ubuntu 21.10 from 21.04. I moved to 21.04, because I boot from ZFS and I wanted to use the first OpenZFS with its permanent SSD caching and better compatibility with FreeBSD (my backup server). 

I have moved my work to virtual machines (VMs), so I use the following main VMs
[LIST]
[*]Xubuntu 20.04 LTS for email, whatsapp. messenger, torrents, KDE-Connect and other communication stuff. 
[*]Ubuntu 16.04 ESM for banking and PayPal with the latest snaps for Firefox and LibreOffice. Encrypted by Virtualbox. 
[*]Ubuntu Studio 20.04 LTS for multimedia. 
[*]Ubuntu 20.04 LTS for experiments and try-outs. 
[*]Windows 10 Pro, for Windows stuff. 
[/LIST]
I have a number of VM to prepare for the future:
[LIST]
[*]Ubuntu 22.04 on OpenZFS running a nested version of Virtualbox to test my future Host OS. 
[*]Xubuntu 22.04 with all the communication stuff. 
[*]Ubuntu Studio 22.04 to check whether I like the transfer to KDE or stick to 20.04 and XFCE. 
[*]Ubuntu Mate 22.04 with QEMU/KVM nested on top of Virtualbox of the Host. Checking whether it is feasible to move from Virtualbox to QEMU/KVM. 
[*]Ubuntu Budgie 22.04 
[*]Windows 11 Pro 
[/LIST]
My hardware is a Ryzen 3 2200G (OC 3.7GHz); 16GB DDR4 (3000MHz); 512GB SP nvme-SSD (3400/2300MB/s); 2 HDDs (500GB + 1TB) and a 128GB sata-SSD as L2ARC/ZIL cache for the HDDs.
ZFS has 3 datapools:
[LIST]
[*]one on the nvme-SSD; 
[*]one striped over both HDDs (2 x 500GB partitions) supported by 95GB L2ARC/ZIL (SSD Cache) and 
[*]one 500GB partition at the end of the 1TB supported by 33GB L2ARC/ZIL. 
[/LIST]
 All datapools are supported by a 3GB L1ARC memory cache. Note that all storage and all caches are lz4 compressed with a compression ratio close to 2, so it results in ~4TB of storage space; ~256GB of SSD cache space for the HDDs and ~4.7GB of L1ARC memory cache space, the other L1ARC space is for uncompressed stuff like directories etc.

In general I stick to the LTS releases, but on occasion I stick to an older version, like I might not like the shift of Studio to KDE from XFCE or I like to keep 16.04 Unity release somewhat longer using the Extended Security Maintenance :) 
 I only move to an intermediate release for a specific reason, like in 2019 to get the latest AMD drivers or in 2021 to get the first OpenZFS release with a permanent SSD cache.

---

### Post by poorguy on 2021-11-08
I've always use the LTS release but today for the hell of it I installed 21.10 because I don't recall ever having used a non LTS release.

It all seems to work well and I don't know what all software are Snaps or Snapd although I know Firefox is a Snap and it seems to be working fine.

Additional software was downloaded from the software center (briefcase with the A in the middle) and what I didn't find there I installed using the terminal.

As for the new Gnome 40 can't say it's exciting a bit different though does what it's supposed to do.

 Wayland seems to be working without issue on my old 2010 Frankenstein computer.

I figure if you don't ever try something you haven't than you ought to and than you really know if it's as bad or as good as you read about and so far it's all good and I have no complaints.

---

### Post by grahammechanical on 2021-11-08
To find out what snaps are installed try this command

```
snap list
```

Some of the snaps are there to provide libraries for other snap applications so that those applications do not to included those libraries in the snap. It avoids duplication of downloaded code. For example, you will see - core18; core20. and as I am running that command on 20.04 I see - gnome-3-34-10804 & gnome-3-38-2004. You will see references to gnome 40 I expect.

Regards

---

### Post by poorguy on 2021-11-08
It doesn't appear I have as many Snaps as I thought.

```


$ snap list
Name               Version             Rev    Tracking         Publisher   Notes
bare               1.0                 5      latest/stable    canonical&#10003;  base
core               16-2.52.1           11993  latest/stable    canonical&#10003;  core
core18             20211015            2246   latest/stable    canonical&#10003;  base
core20             20210928            1169   latest/stable    canonical&#10003;  base
firefox            94.0.1-1            701    latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-34-1804    0+git.3556cb3       72     latest/stable    canonical&#10003;  -
gnome-3-38-2004    0+git.6ba6040       76     latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-59-g7bca6ae     1519   latest/stable/&#8230;  canonical&#10003;  -
snap-store         3.38.0-64-g23c4c77  547    latest/stable/&#8230;  canonical&#10003;  -
vlc                3.0.16              2344   latest/stable    videolan&#10003;   -


```

---

### Post by Shibblet on 2021-11-10
> **eipapp said:**
> Just curious as to how many folks are actually excited enough about Gnome 40 to upgrade or install Ubuntu 21.10.
I for one, and I may be missing something, do NOT intend to upgrade and am not sure what all the excitement is about.
Basically it seems that they moved the work spaces from a vertical view to a horizontal view, so like a big deal ???
I don't know, like I said maybe I just don't get it.
Would like others input but for now, I'm staying with Ubuntu 20.04.
Any thoughts, comments ???

I have been a huge Kubuntu fan for the longest time.  I really enjoy everything KDE has to offer.  So... to answer your question:

Nope.  Gnome 40 doesn't make me excited at all.  ;-)

---

### Post by vicshrike on 2021-11-16
Reacquainting myself with Ubuntu and 21.10, sweet so far.

---

