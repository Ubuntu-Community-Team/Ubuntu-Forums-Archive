---
title: "GiMP, PCManFM, [others] seg faulting"
date: 2013-07-18
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-07-18
Wanted to ask if others are experiencing seg faults lately.

Here are two proggies that I use every day [there may be others -haven't tested everything]:

```
vindsl@Zuul:~$ apt-cache policy gimp
gimp:
  Installed: 2.8.6-0raring1~ppa
  Candidate: 2.8.6-0raring1~ppa
  Version table:
 *** 2.8.6-0raring1~ppa 0
        500 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     2.8.4-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages

vindsl@Zuul:~$ gimp
Segmentation fault

vindsl@Zuul:~$ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.1.0+bzr920+201307171945~raring1
  Candidate: 1.1.0+bzr920+201307171945~raring1
  Version table:
 *** 1.1.0+bzr920+201307171945~raring1 0
        500 http://ppa.launchpad.net/lubuntu-dev/lubuntu-daily/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1.1.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages

vindsl@Zuul:~$ pcmanfm
Segmentation fault
vindsl@Zuul:~$
```
This cropped up yesterday, after incremental upgrades.

Maybe I need to 'downgrade' them to the saucy version(s).  Hasn't been a prob before.

I'll do some digging, after I submit this post.

---

### Post by slickymaster on 2013-07-18
Regarding PCManFM I can't be of any help, since I use Thunar, but as for what Gimp is concerned I haven't experienced anything problematic. But contrary to you I'm running the 2.8.4-1 version, which I think is the Saucy proposed.```
~$ apt-cache policy gimp
gimp:
  Installed: 2.8.4-1ubuntu1
  Candidate: 2.8.4-1ubuntu1
  Version table:
 *** 2.8.4-1ubuntu1 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
```Maybe you're right when you say you need to 'downgrade' them to the saucy version(s).

---

### Post by VinDSL on 2013-07-18
> **slickymaster said:**
> Maybe you're right when you say you need to 'downgrade' them to the saucy version(s).
Thanks for the reply.

Unfortunately, no worky for me...

```
vindsl@Zuul:~$ apt-cache policy gimp
gimp:
  Installed: 2.8.4-1ubuntu1
  Candidate: 2.8.4-1ubuntu1
  Version table:
 *** 2.8.4-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ gimp
Segmentation fault
vindsl@Zuul:~$
```

Hrm...

It's doing it in GNOME3 Staging, GNOME Classic, LXDE/Openbox, et cetera.

Gonna have to think about this, for a while.  :)

---

### Post by slickymaster on 2013-07-18
Yeah, it's odd.
Also, I'm running the 3.11rc1 kernel, but I'm sure you're also running under it.
Keep us posted.

---

### Post by VinDSL on 2013-07-18
> **slickymaster said:**
> 3.11rc1 kernel, but I'm sure you're also running under it.
Keep us posted.
Will do.

3.11-rc1 had issues, on this box.

Last night, I discovered that zram was installed on this machine.  I have a *feeling* there was a conflict between zram and zswap (enabled by default in 3.11), but I've already wiped 3.11, so I cannot test it.  I'm back to 3.10 Final & 3.10 Mainline, at the moment.  These apps are seg faulting on both kernels, regardless of the DE used.

Anyway, I'll keep hacking away at it.

Thanks, again.

---

### Post by mc4man on 2013-07-18
the otto gimp works fine here though only using that ppa & a personal saucy one.

As far as pcmanfm, it may be because of  libmenu-cache ( the cuurnet here is libmenu-cache.so.3 & pcmanfm may be looking for the .2 version

---

### Post by VinDSL on 2013-07-18
Thanks!

I'll check it out...  ;)

I need to run, for a few minutes.  When I'm back, I'll check my logs for clues.

---

### Post by mc4man on 2013-07-18
> **VinDSL said:**
> Thanks!

I'll check it out...  ;)

I need to run, for a few minutes.  When I'm back, I'll check my logs for clues.
I took a look at your 2 ppa's - 
otto's gimp has saucy build's, maybe try switching over to saucy
the lubuntu one also has pcmanfm for saucy but their last build failed, I'm sure they'll rectify shortly, 

(- i've got pcmanfm, (bzr920+201307171945),  in my sacy-tests ppa but for the most part the packages in there aren't for you 
(several are skewed towards using the modded nautilus-3.8 in there

Worst case you coud try the pcmanfm in there, i386 is available, amd64 later today - , this should dl or just go there & take pcmanfm package only if inclined not to wait for your ppa
```
wget https://launchpad.net/~mc3man/+archive/sacy-tests/+build/4806064/+files/pcmanfm_1.1.0%2Bbzr920%2B201307171945%7Esaucy2_i386.deb


```

---

### Post by VinDSL on 2013-07-18
> **mc4man said:**
> Worst case you could try the pcmanfm in there [...][/CODE]
Just got home...

I'll work my way backwards (hate it when things just work).  :D

```
vindsl@Zuul:~$ apt-cache policy pcmanfm
pcmanfm:
  Installed: 1.1.0+bzr920+201307171945~saucy2
  Candidate: 1.1.0+bzr920+201307171945~saucy2
  Version table:
 *** 1.1.0+bzr920+201307171945~saucy2 0
        100 /var/lib/dpkg/status
     1.1.0-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages
vindsl@Zuul:~$ 
```

This fired up, just fine, but as soon as I click anything, it disappears to null.

I'll try the conventional versions in a few.

Thanks, as always!

---

### Post by mc4man on 2013-07-19
> **VinDSL said:**
> Just got home...

I'll work my way backwards (hate it when things just work).  :D

This fired up, just fine, but as soon as I click anything, it disappears to null.

I'll try the conventional versions in a few.

Thanks, as always!
With no gnome3 or rico ppas at all, just sacy, otto, & an mplayer one, see no issues with that pcman in unity & gnome* sessions. 
Maybe ck your local log for gnome-session or .xsession-errors (where or which can vary..

---

### Post by VinDSL on 2013-07-19
> **mc4man said:**
> Maybe ck your local log for gnome-session or .xsession-errors (where or which can vary..
Will do.  Thanks!

---

### Post by mc4man on 2013-07-19
> **VinDSL said:**
> Will do.  Thanks!
As far as I know gdm keeps it's own log, should be easy to find
lightdm uses .xsession-errors for gnome* sessions & .cache/upstart for unity session

---

### Post by VinDSL on 2013-07-19
Heh!  Sorry, for digressing, but I'm going through various logs, and...

My fire-breathing, flamethrower, P4EE CPU is throttling like crazy.  LoL!  :D

I turn my CPU cooler fan speed down, in the winter, so I don't have to listen to it.

It's triple-digits here, now.  Guess I better crank it up, all the way.

Okay, back on topic.

Still going through my logs, looking for a clue...  ;)

---

### Post by VinDSL on 2013-07-19
Eureka!  :)

```

Jul 19 09:29:20 Zuul kernel: [ 7593.301489] pcmanfm[24222]: segfault at 0 ip b6d105e6 sp bfe55350 error 4 in libgobject-2.0.so.0.3705.0[b6d04000+52000]

Jul 19 09:29:37 Zuul kernel: [ 7610.023152] gimp[24298]: segfault at 0 ip b6aee5e6 sp bfb26e30 error 4 in libgobject-2.0.so.0.3705.0[b6ae2000+52000]

Jul 19 09:50:05 Zuul kernel: [ 8837.964883] chrome[24305]: segfault at 0 ip b23715e6 sp bfa71360 error 4 in libgobject-2.0.so.0.3705.0[b2365000+52000]

```

Didn't realize Chromium was seg faulting, too.

Actually, I *think* the Chromium seg fault was due to the flash plug-in running out of memory.  That happens quite often, when I'm playing Zynga flash games on FB. Flash performance, on  a machine with 1GB RAM is rather dodgy.

Er... I play Cafe World, for testing purposes only (fingers crossed behind back).  ;)

---

### Post by mc4man on 2013-07-19
You're breaking on the glib you've installed from a ppa, likely  - 
2.37.5~git20130714.8ead9055-0ubuntu1~13.10~ricotz1
So for a while you probably won't be able to use pcmanfm until it's fixed for 2.37.5 or higher
(unless you downgrade to a lesser version of glib which may or may not affect other ppa packages...

the simple crash title is - 
pcmanfm crashed with SIGSEGV in g_cclosure_marshal_generic()

---

### Post by VinDSL on 2013-07-19
Agreed!

I don't see any good options, at this point, except waiting.  ;)

---

### Post by VinDSL on 2013-07-20
That didn't take long!  :D

> **zika said:**
> Lot of design/user_interface changes today...

```
vindsl@Zuul:~$ apt-cache policy libglib2.0-0
libglib2.0-0:
  Installed: 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1
  Candidate: 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1
  Version table:
 *** 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     2.37.3-1ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ 
```

Solved all of my glib probs.  GiMP, PCManFM, [everything] is working fine now.  Didn't even have to restart.

Thanks, for the help!  ;)

---

### Post by mc4man on 2013-07-20
It was a bug in glib - 
[https://bugzilla.gnome.org/show_bug.cgi?id=704267](https://bugzilla.gnome.org/show_bug.cgi?id=704267)

---

### Post by VinDSL on 2013-07-20
> **mc4man said:**
> It was a bug in glib - 
[https://bugzilla.gnome.org/show_bug.cgi?id=704267](https://bugzilla.gnome.org/show_bug.cgi?id=704267)
Yeah, these (ricotz) glib packages were included in this morning's incremental upgrade(s):

```
Commit Log for Sat Jul 20 09:09:39 2013

Upgraded the following packages:

libglib2.0-data (2.37.5~git20130714.8ead9055-0ubuntu1~13.10~ricotz1) to 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1

libglib2.0-dev (2.37.5~git20130714.8ead9055-0ubuntu1~13.10~ricotz1) to 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1

libglib2.0-doc (2.37.5~git20130714.8ead9055-0ubuntu1~13.10~ricotz1) to 2.37.5~git20130719.8753df9d-0ubuntu1~13.10~ricotz1


```

I had a *good* feeling about it.  Worked a treat!  :)

---

