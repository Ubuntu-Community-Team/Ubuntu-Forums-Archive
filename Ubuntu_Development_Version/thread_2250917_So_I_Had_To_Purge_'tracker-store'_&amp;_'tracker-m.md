---
title: "So I Had To Purge 'tracker-store' &amp; 'tracker-miner-fs'"
date: 2014-10-31
forum: Ubuntu Development Version
---

### Post by VinDSL on 2014-10-31
My Vivid machine has been performing horribly the past few days -- 80-90% CPU load -- HDD churning away -- HDD LED lit-up solid, et cetera.

I finally had enough of it today and did some forensics.  The culprits were 'tracker-store' & 'tracker-miner-fs'.

I tried various settings in dconf-editor to no avail. Nothing would tame the tiger, so I killed it.

First of all, I stopped these processes using 'System Monitor'.

Then, I wiped the cruft off the drive via CLI:

```
tracker-control -r
```

And, finally, I purged 'tracker-store' & 'tracker-miner-fs' using 'Synaptic':

```
Commit Log for Fri Oct 31 16:07:28 2014

Completely removed the following packages:
tracker
tracker-extract
tracker-miner-fs
tracker-utils
libtracker-control-1.0-0
libtracker-miner-1.0-0

```

Everything is back to normal now and performing nicely.

Maybe I'll re-install again, in a few months... or not.   ;)

---

### Post by sammiev on 2014-10-31
> **VinDSL said:**
> My Vivid machine has been performing horribly the past few days -- 80-90% CPU load -- HDD churning away -- HDD LED lit-up solid, et cetera.

I finally had enough of it today and did some forensics.  The culprits were 'tracker-store' & 'tracker-miner-fs'.

I tried various settings in dconf-editor to no avail. Nothing would tame the tiger, so I killed it.

First of all, I stopped these processes using 'System Monitor'.

Then, I wiped the cruft off the drive via CLI:

```
tracker-control -r
```

And, finally, I purged 'tracker-store' & 'tracker-miner-fs' using 'Synaptic':

```
Commit Log for Fri Oct 31 16:07:28 2014

Completely removed the following packages:
tracker
tracker-extract
tracker-miner-fs
tracker-utils
libtracker-control-1.0-0
libtracker-miner-1.0-0

```

Everything is back to normal now and performing nicely.

Maybe I'll re-install again, in a few months... or not.   ;)

Thanks like usual. It will be helpful. ;)

---

### Post by VinDSL on 2014-11-01
Welcome!

I really don't see any need for 'tracker', especially since it's just running amuck and creating havoc.  

All it's doing is chewing up CPU cycles and mercilessly thrashing the HD.  It *felt* like I was running 'Vista'. 

Luckily, 'tracker' isn't wrapped around Ubuntu like a hydra.  Purging it hasn't had any negative affects.

---

### Post by zika on 2014-11-01
Did You install that Yourself or...?
I do not have any trace of tracker on this install, did not purge it or disable in any way.```
:~$ sudo apt-get purge -s tracker
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'tracker' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
:~$ sudo apt-get install -s tracker
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libgsf-1-114 libgsf-1-common libmediaart-1.0-0 libtracker-control-1.0-0 libtracker-miner-1.0-0 libtracker-sparql-1.0-0 tracker-extract tracker-miner-fs tracker-utils
Suggested packages:
  tracker-gui
The following NEW packages will be installed:
  libgsf-1-114 libgsf-1-common libmediaart-1.0-0 libtracker-control-1.0-0 libtracker-miner-1.0-0 libtracker-sparql-1.0-0 tracker tracker-extract tracker-miner-fs tracker-utils
0 upgraded, 10 newly installed, 0 to remove and 1 not upgraded.
Inst libmediaart-1.0-0 (0.7.0-2 Ubuntu:15.04/vivid [amd64])
Inst libtracker-sparql-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst libtracker-control-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst libtracker-miner-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst libgsf-1-common (1.14.27-2ubuntu2 Ubuntu:15.04/vivid [all])
Inst libgsf-1-114 (1.14.27-2ubuntu2 Ubuntu:15.04/vivid [amd64])
Inst tracker (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst tracker-extract (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst tracker-miner-fs (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Inst tracker-utils (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf libmediaart-1.0-0 (0.7.0-2 Ubuntu:15.04/vivid [amd64])
Conf libtracker-sparql-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf libtracker-control-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf libtracker-miner-1.0-0 (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf libgsf-1-common (1.14.27-2ubuntu2 Ubuntu:15.04/vivid [all])
Conf libgsf-1-114 (1.14.27-2ubuntu2 Ubuntu:15.04/vivid [amd64])
Conf tracker (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf tracker-extract (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf tracker-miner-fs (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
Conf tracker-utils (1.2.2-2ubuntu2 Ubuntu:15.04/vivid-proposed [amd64])
```It might be helpfull to You to see what is a difference i.e. what other packages came with tracker.

---

### Post by ventrical on 2014-11-01
> **VinDSL said:**
> Welcome!

All it's doing is chewing up CPU cycles and mercilessly thrashing the HD.  It *felt* like I was running 'Vista'. 


What a nightmare that was . :)  Well . it's Halloween after all :) lol

---

### Post by sammiev on 2014-11-01
This is what I had:

```
sudo apt-get purge -s tracker
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'tracker' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by zika on 2014-11-01
> **sammiev said:**
> This is what I had:

```
sam@sam-L650:~$ sudo apt-get purge -s tracker
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-documents* tracker* tracker-extract* tracker-miner-fs* tracker-utils*
  ubuntu-gnome-desktop*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg ubuntu-gnome-desktop [0.34]
Purg gnome-documents [3.12.1-1ubuntu3]
Purg tracker-utils [1.0.4-0ubuntu2]
Purg tracker-miner-fs [1.0.4-0ubuntu2]
Purg tracker [1.0.4-0ubuntu2] [tracker-extract:amd64 ]
Purg tracker-extract [1.0.4-0ubuntu2]
sam@sam-L650:~$ 
```Great, now we have &#8222;culprit&#8220; i.e. how come I do not have it and You do. You (both, I suppose) have installed ubuntu-gnome-desktop package, after vanilla install of Ubuntu proper.

---

### Post by sammiev on 2014-11-01
> **zika said:**
> Great, now we have „culprit“ i.e. how come I do not have it and You do. You (both, I suppose) have installed ubuntu-gnome-desktop package, after vanilla install of Ubuntu proper.

Sorry zika,

I had it on 14.10

I updated my post and 15.04 had no traces of it with Unity.

I will install ubuntu-gnome later today and check to see if I get there.

---

### Post by sammiev on 2014-11-01
> **zika said:**
> Great, now we have „culprit“ i.e. how come I do not have it and You do. You (both, I suppose) have installed ubuntu-gnome-desktop package, after vanilla install of Ubuntu proper.

I installed gnome vivid and here is the output of the above command. You are correct about ubuntu-gnome-desktop.

```
sudo apt-get purge -s tracker
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-documents* tracker* tracker-extract* tracker-miner-fs* tracker-utils*
  ubuntu-gnome-desktop*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg ubuntu-gnome-desktop [0.34]
Purg gnome-documents [3.12.1-1ubuntu3]
Purg tracker-utils [1.2.2-2ubuntu2]
Purg tracker-miner-fs [1.2.2-2ubuntu2]
Purg tracker [1.2.2-2ubuntu2] [tracker-extract:amd64 ]
Purg tracker-extract [1.2.2-2ubuntu2]
```

---

### Post by VinDSL on 2014-11-01
> **zika said:**
> [H]ow come I do not have it and You do?

Aha!  Who_Done_It solved.

Check the history:  [https://launchpad.net/ubuntu/+source/tracker/1.2.2-2ubuntu2](https://launchpad.net/ubuntu/+source/tracker/1.2.2-2ubuntu2)

Looks like the 'culprit' snuck in the back door, during an update (I presume '-proposed')...    :p

---

### Post by zika on 2014-11-01
> **VinDSL said:**
> Aha!  Who_Done_It solved.

Check the history:  [https://launchpad.net/ubuntu/+source/tracker/1.2.2-2ubuntu2](https://launchpad.net/ubuntu/+source/tracker/1.2.2-2ubuntu2)

Looks like the 'culprit' snuck in the back door, during an update (I presume '-proposed')...    :pI might be old and ill-sighted but I did not find answer in history.
My all gates are open, proposed has not been closed since 14.10 install on this machine and yet it not manage to sneak through any door, it did not even knock on any door here, yet... Update/upgrade is every several minutes... I'm waiting for &#8222;culprit&#8220;...
Ups, sorry, I've missed sign [gnome] on this thread... ;)

---

### Post by VinDSL on 2014-11-01
I just added a 'me too' over here:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/1377877](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/1377877)

Probably won't help them much, but it's better than being a silent witness.  ;)

---

### Post by VinDSL on 2014-11-01
> **zika said:**
> Ups, sorry, I've missed sign [gnome] on this thread... ;)

No prob.

Maybe your eyes were fixed on the smiley with the sunglasses.  :KS

I *thought* about leaving that off, but I was in a whimsical mood, having just caught the perp in the act.

---

### Post by zika on 2014-11-01
> **VinDSL said:**
> No prob. Maybe your eyes were fixed on the smiley with the sunglasses.  :KS.Did not see tat either, until now that You've mentioned it. Tunnel visioned on topic, 40+ years of training.

---

### Post by VinDSL on 2014-11-01
> **zika said:**
> Tunnel visioned on topic, 40+ years of training.

LoL!  I've always been that way, too.  :D

Total concentration, to the exclusion of everything else, is a blessing and a curse.

I *suppose* that's why I don't need a 'tracker'...

---

### Post by mc4man on 2014-11-01
> **VinDSL said:**
> I just added a 'me too' over here:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/1377877](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/1377877)

Probably won't help them much, but it's better than being a silent witness.  ;)
That's probably due for a "It's an upstream bug so please file one"  with the jolly gnome redhats & it can then languish in peace.

---

### Post by VinDSL on 2014-11-01
> **mc4man said:**
> That's probably due for a "It's an upstream bug so please file one"  with the jolly gnome redhats & it can then languish in peace.
Yes, I suspect that will be the likely course and outcome.

At least there's a workaround.

---

### Post by harry332 on 2014-11-02
Vivid still has old nautilus (3.10).
However, nautilus versions 3.12 and 3.14 depend on libtracker-sparql-1.0-0.
Nautilus_3.12 can be found on Gnome3 PPA and nautilus_3.14 on Gnome3 Staging PPA.

---

### Post by VinDSL on 2014-11-02
> **harry332 said:**
> Vivid still has old nautilus (3.10).
However, nautilus versions 3.12 and 3.14 depend on libtracker-sparql-1.0-0.
Nautilus_3.12 can be found on Gnome3 PPA and nautilus_3.14 on Gnome3 Staging PPA.

Good catch!

```
vindsl@Zuul:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:3.12.2-0ubuntu1~trusty3
  Candidate: 1:3.12.2-0ubuntu1~trusty3
  Version table:
 *** 1:3.12.2-0ubuntu1~trusty3 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ vivid/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.10.1-0ubuntu15 0
        500 http://mirror.hmc.edu/ubuntu/ vivid/main i386 Packages

```
I use PCManFM, mostly.

```

vindsl@Zuul:~$ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.2.3-1
  Candidate: 1.2.3-1
  Version table:
 *** 1.2.3-1 0
        500 http://mirror.hmc.edu/ubuntu/ vivid/universe i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 
```
Regardless, I left libtracker-sparql intact, since nautilus is still intertwined in Ubuntu.  ;)

```
vindsl@Zuul:~$ apt-cache policy libtracker-sparql-1.0-0:i386
libtracker-sparql-1.0-0:
  Installed: 1.2.2-2ubuntu2
  Candidate: 1.2.2-2ubuntu2
  Version table:
 *** 1.2.2-2ubuntu2 0
        500 http://mirror.hmc.edu/ubuntu/ vivid/main i386 Packages
        100 /var/lib/dpkg/status
     1.0.5-0ubuntu1~utopic1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ vivid/main i386 Packages
vindsl@Zuul:~$ 
```
Actually,  libtracker-sparql is the only 'tracker' library that's still installed in my rig...

---

### Post by mc4man on 2014-11-02
libtracker-sparql ends up on many installs via grilo-plugins for some time now  & hasn't caused any issues with cpu or otherwise

---

### Post by VinDSL on 2014-11-03
> **mc4man said:**
> libtracker-sparql ends up on many installs via grilo-plugins for some time now  & hasn't caused any issues with cpu or otherwise

Interesting.

I hadn't thought about the grilo framework, but upon reflection, that makes sense.  ;)

> This package contains the set of plugins officially distributed with Grilo:
  * Apple Trailers
  * Blip.tv
  * dLeyna
  * DMAP
  * Filesystem
  * Flickr
  * Freebox
  * Gravatar
  * Jamendo
  * Last.fm (for album art)
  * Local metadata (album art and thumbnails)
  * Lua Factory
  * Magnatune
  * Metadata Store
  * Optical Media
  * Pocket
  * Podcasts
  * Rai.tv
  * SHOUTcast
  * TMDb
  * Tracker
  * Vimeo
  * Youtube

I guess I'll re-install 'tracker' every week or so, and see how it pans out.

Thx

---

