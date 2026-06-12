---
title: "libpango mess..."
date: 2013-05-27
forum: Ubuntu Development Version
---

### Post by zika on 2013-05-27
```
:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
Suggested packages:
  ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp
The following NEW packages will be installed:
  libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/199 kB of archives.
After this operation, 1,050 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 273454 files and directories currently installed.)
Unpacking libpango-1.0-0:amd64 (from .../libpango-1.0-0_1.32.5-5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libpango-1.0-0_1.32.5-5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0', which is also in package libpango1.0-0:amd64 1.33.9-0ubuntu1~raring0
Unpacking libpangoft2-1.0-0:amd64 (from .../libpangoft2-1.0-0_1.32.5-5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libpangoft2-1.0-0_1.32.5-5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0', which is also in package libpango1.0-0:amd64 1.33.9-0ubuntu1~raring0
Unpacking libpangocairo-1.0-0:amd64 (from .../libpangocairo-1.0-0_1.32.5-5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libpangocairo-1.0-0_1.32.5-5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0', which is also in package libpango1.0-0:amd64 1.33.9-0ubuntu1~raring0
Errors were encountered while processing:
 /var/cache/apt/archives/libpango-1.0-0_1.32.5-5_amd64.deb
 /var/cache/apt/archives/libpangoft2-1.0-0_1.32.5-5_amd64.deb
 /var/cache/apt/archives/libpangocairo-1.0-0_1.32.5-5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by dino99 on 2013-05-27
Got the same mess (but its not a show stopper)

---

### Post by jppr on 2013-05-27
I updated the system just in synaptic and didn´t have any problem and any mess.

---

### Post by zika on 2013-05-27
> **jppr said:**
> I updated the system just in synaptic and didn´t have any problem and any mess.
Amd64 or i386?
Just tried with Synaptic and got the same error as in #1...

---

### Post by cariboo on 2013-05-27
I just updated my AMD64 system using synaptic, and didn't run into any problems either.

---

### Post by zika on 2013-05-27
libpango from Ricotz PPAs could be the source of my mess... ;)

---

### Post by cariboo on 2013-05-27
The only ppas here are for:

[LIST]
[*]Handbrake
[*]My weatner indicator
[*]100 scopes from unity-experimental- certified
[*]Jitsi
[/LIST]

everything else is from the regular Saucy repo's

---

### Post by zika on 2013-05-27
> **cariboo907 said:**
> The only ppas here are for:

[LIST]
[*]Handbrake 
[*]My weatner indicator 
[*]100 scopes from unity-experimental- certified 
[*]Jitsi 
[/LIST]

everything else is from the regular Saucy repo'sI'm guilty as charged of having PPAs turned on... I'm ready for penalty... ;)

---

### Post by Harry33 on 2013-05-27
> **zika said:**
> libpango from Ricotz PPAs could be the source of my mess... ;)

Yes it is.
So do not upgrade pango nor vte3 if you have Gnome3 Staging PPA enabled.
Ricotz GnomeTesting PPA, however, does have a new pango (1.34.1-0ubuntu1) now, use that one.

---

### Post by zika on 2013-05-27
That is why I love aptitude...
It pulled me out of this mess, with RicoTz on my side...
Thank You...

---

### Post by VinDSL on 2013-05-27
> **zika said:**
> That is why I love aptitude...
It pulled me out of this mess, with RicoTz on my side...
Thank You...
Synaptic pulled my ["libpango mess..."] out of the fire, a few minutes ago.  ;)

Had to use a combination of 'default' & 'smart' upgrades in Synaptic.  

After dancing_on_the_keyboard for a while, everything was sorted.  

Whew!  That was a good one...  :)

---

### Post by Harry33 on 2013-05-28
> **VinDSL said:**
> Synaptic pulled my ["libpango mess..."] out of the fire, a few minutes ago.  ;)

Had to use a combination of 'default' & 'smart' upgrades in Synaptic.  

After dancing_on_the_keyboard for a while, everything was sorted.  

Whew!  That was a good one...  :)

Both Ricotz Cnome Testing PPA and Gnome3 Staging PPA now have a new pango1.0 (1.34.1), which solve the libpango mess.

---

### Post by VinDSL on 2013-05-28
> **Harry33 said:**
> Both Ricotz Cnome Testing PPA and Gnome3 Staging PPA now have a new pango1.0 (1.34.1), which solve the libpango mess.
Right. I installed the Ricotz version(s)...

```
vindsl@Zuul:~$ apt-cache policy libpango-1.0-0
libpango-1.0-0:
  Installed: 1.34.1-0ubuntu1~13.10~ricotz0
  Candidate: 1.34.1-0ubuntu1~13.10~ricotz0
  Version table:
 *** 1.34.1-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.34.1-0ubuntu1~13.04~ricotz0 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
     1.32.5-5 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ 

```

It just took a bit of doing.

Sometimes, Synaptic wanted to remove 10s or 100s of packages. Sometimes, it wanted to do a partial upgrade.

Eventually, I came up with a suitable upgrade path that fixed Pango without destroying the rest of my system, e.g. it wasn't a simple point n' click affair.  ;)

---

### Post by seruling on 2013-06-23
I always get error while upgrade/install/remove/purge.
Now, I can't do anything with apt-get because of libpango. 
My post here [http://ubuntuforums.org/showthread.php?t=2155910](http://ubuntuforums.org/showthread.php?t=2155910)
I must reinstall my ubuntu soon.

---

### Post by zika on 2013-06-24
You have 13.04 not U+1...?
(We are in U+1 forum)
Looking into Your message (URL given by You) I can conclude that Your problem (in 13.04) is a bit different from the one we had here. Even though, I think You could get out of that with good bookkeeping and patience...

---

