---
title: "64bit jackd, wineasio-x, wineasio64, I'm confused"
date: 2009-06-28
forum: Ubuntu Studio
---

### Post by oedipuss on 2009-06-28
I'm not having much luck with wineasio-x and jackbridge on a 64bit system... It used to kind of work (crashed and was generally a hassle) but now it doesn't produce any sound at all, and I can't find out why or what's different. 

Also, there's _[this thread]("http://forum.jacklab.net/viewtopic.php?f=32&t=768")_, which mentions wineasio64, but then claims that there isn't any need for a special wineasio for 64bit systems anymore, and links to a jack related post that says that as of version 0.114 a 64bit jack server can handle 32bit guests (0.117 is in jaunty). 
However, I can't compile the regular wineasio : 
```

Relocatable linking with relocations from format elf32-i386 (asio.o) to format elf64-x86-64

```

I'm confused :confused:... Could someone explain what the preferred method currently is for running 32 bit applications with wineasio and connecting them to a 64bit jack server?

---

### Post by sgx on 2009-06-28
As a non-expert, I would recomend not mixing compiled and non-compiled installs. I would use synaptic to uninstall wine, libwine, wineasio, libjack, and jackd, (some distros have wine and libwine all in one, some use 'jackit' or 'jackstart' for jackd, so apply logic as needed)

I would stick to the RT kernel from Ubuntu Studio 8.04, and consider doing a reinstall with 8.04 with separate /home partition, to make future reinstalls utilize your configurations by choosing to not reformat /home.
Cheers

---

### Post by Grishka on 2009-06-28
unfortunately, JACK in Ubuntu repositories is compiled without mixed 32/64-bit mode support. your best option would be compiling JACK with mixed mode from source (configure with "--mixed"). or you can grab JACK packages from [my ppa](https://launchpad.net/~thir/+archive/ppa). they work for me, but should be considered experimental (svn version linked against new versions of some sound libraries that didn't even make it to karmic yet). so use it at your own risk.

---

### Post by sgx on 2009-06-29
> **oedipuss said:**
> I'm not having much luck with wineasio-x and jackbridge on a 64bit system... It used to kind of work (crashed and was generally a hassle) but now it doesn't produce any sound at all, and I can't find out why or what's different. 

Also, there's _[this thread]("http://forum.jacklab.net/viewtopic.php?f=32&t=768")_, which mentions wineasio64, but then claims that there isn't any need for a special wineasio for 64bit systems anymore, and links to a jack related post that says that as of version 0.114 a 64bit jack server can handle 32bit guests (0.117 is in jaunty). 
However, I can't compile the regular wineasio : 
```

Relocatable linking with relocations from format elf32-i386 (asio.o) to format elf64-x86-64

```

I'm confused :confused:... Could someone explain what the preferred method currently is for running 32 bit applications with wineasio and connecting them to a 64bit jack server?

If you want to make music, stick to 32bit ubuntu studio 8.04, and known stable 32bit apps, or a similar known-to-work distro/apps. It works. All this wrangling over compiling this and having the newest build of that won't help you reach for the record button, and that is the button that counts. I'm all for progress, but any definition of progress that defies
your being able to play and record music, is very deeply flawed.
Cheers

(just ignore this, if you don't want to make music ;) )

---

### Post by glurgle on 2009-07-02
> **sgx said:**
> If you want to make music, stick to 32bit ubuntu studio 8.04, and known stable 32bit apps, or a similar known-to-work distro/apps. It works. All this wrangling over compiling this and having the newest build of that won't help you reach for the record button, and that is the button that counts. I'm all for progress, but any definition of progress that defies
your being able to play and record music, is very deeply flawed.
Cheers

(just ignore this, if you don't want to make music ;) )

This makes perfect sense if your sole purpose for the machine is music. If, however, you prefer/need to use your computer for more than just one thing, limiting yourself to software selections that are a 18 months out of date just to avoid compiling a single package (and you know, maybe *learning* how your distro packaging tools work) is silly. I mean, why not just use windows at that point? Hell of a lot easier.

---

### Post by sgx on 2009-07-02
> **glurgle said:**
> This makes perfect sense if your sole purpose for the machine is music. If, however, you prefer/need to use your computer for more than just one thing, limiting yourself to software selections that are a 18 months out of date just to avoid compiling a single package (and you know, maybe *learning* how your distro packaging tools work) is silly. I mean, why not just use windows at that point? Hell of a lot easier.
I started my post 'If you want to make music', as the OP seems to be posting in a multi-media forum, about making music. If 18 month old things work better to actually make music, than the flawed kernels and pulse-audio vs jackd debacle that Ubuntu released in the interim, so be it. If someone insists on doing things the hard way, or enjoys persevering a daunting learning curve, to gain knowledge, then so be it. But to suggest that by not compiling a needed/desired app, one must use either outdated software, or windoze, is insulting, and implies some inherant defect in software based only on its age, or the impossibility of finding a working .deb or .rpm based solution, neither of which is accurate in this case. This forum seems well supplied with musicians unsuccessfully trying the exotic and esoteric, when the simple and basic will do just fine, allowing all that creative energy to be diverted to actually making music, instead of endlessly making a system to make music.

---

### Post by oedipuss on 2009-07-03
Thanks for your suggestions. It would certainly be easier to just stick to a 32bit installation. I'd like to see if I can figure out wineasio on my 64bit installation first, though.

It is kind of misleading to say that a current 64bit system is simply unsuitable. The _only_ thing that confuses me is wineasio, everything else just works, including vsts (with dssi-vst and fst, or through wine hosts), wine and jack. 

Grishka thanks for the ppa, but are you sure the version of jackd in the jaunty repos is incapable of mixed mode? Windows vsts (32bit) through dssi-vst work fine, and connect to jack with no issues at all. If I remember correctly this wasn't possible a while ago. 

As for my problem, it seems I was supposed to do JACKBRIDGE=name, both before running jackbridge and before running wine, so they could connect to each other I suppose.
 I just want some information on what the current status of wineasio is. For all I know the thing with jackbridge might be the way it works now on 32bit systems as well. Or it might be completely abandoned, in favor of something else. That thread I linked to seemed to suggest that wineasio-x is deprecated.

---

### Post by sgx on 2009-07-03
> **oedipuss said:**
> Thanks for your suggestions. It would certainly be easier to just stick to a 32bit installation. I'd like to see if I can figure out wineasio on my 64bit installation first, though.

It is kind of misleading to say that a current 64bit system is simply unsuitable. The _only_ thing that confuses me is wineasio, everything else just works, including vsts (with dssi-vst and fst, or through wine hosts), wine and jack. 

Grishka thanks for the ppa, but are you sure the version of jackd in the jaunty repos is incapable of mixed mode? Windows vsts (32bit) through dssi-vst work fine, and connect to jack with no issues at all. If I remember correctly this wasn't possible a while ago. 

As for my problem, it seems I was supposed to do JACKBRIDGE=name, both before running jackbridge and before running wine, so they could connect to each other I suppose.
 I just want some information on what the current status of wineasio is. For all I know the thing with jackbridge might be the way it works now on 32bit systems as well. Or it might be completely abandoned, in favor of something else. That thread I linked to seemed to suggest that wineasio-x is deprecated.

Hi, here ia the wineasio forum to ask the author(s):

[http://forum.jacklab.net/viewforum.php?f=32](http://forum.jacklab.net/viewforum.php?f=32)

I don't recall saying anything about 64bit xxx being unsuitable for any given task, only that musicians can play and record easily and at high quality using stable 32bit linux/vsts apps and systems,  given usage of
the limited range of supported soundcards.
Cheers

---

### Post by Grishka on 2009-07-03
> **oedipuss said:**
> Grishka thanks for the ppa, but are you sure the version of jackd in the jaunty repos is incapable of mixed mode? Windows vsts (32bit) through dssi-vst work fine, and connect to jack with no issues at all. If I remember correctly this wasn't possible a while ago.

ahh, you're right. 0.116 in the repos is JACK1 (it can't be 0.117, 'cos the last JACK1 version is 0.116), which doesn't need any special compilation options for the 32/64-bit mode, it seems. sorry, I've been using JACK2 for a while, and I've forgotten about the differences. I've checked Ubuntu JACK build logs, saw no reference to mixed mode anywhere, and assumed that it's not compiled in. sorry for the confusion. about your problem... perhaps you could try using an older version of wineasio, since you say it did work for you in the past. perhaps something was broken in 0.7.4. or ask the wineasio author, as suggested.

---

