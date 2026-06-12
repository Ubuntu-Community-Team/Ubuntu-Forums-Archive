---
title: "Can you download whole repositories?"
date: 2005-09-29
forum: Repositories &amp; Backports
---

### Post by MetalMusicAddict on 2005-09-29
Im wondering if its possiable to download all the ubuntu repos. Well not the security or update ones. Just Main, Non-free or ones that dont change. My thinking is to download them, put it on a network and add it to synaptic somehow.

The Ubuntu DVDs just have Main on them right? No non-free?

---

### Post by heimo on 2005-09-29
Instead of mirroring whole repository, you may want to use apt-proxy (of course this depends on your needs).
[https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)

Is this something you're looking for?

---

### Post by MetalMusicAddict on 2005-09-29
[QUOTE=heimo]Instead of mirroring whole repository, you may want to use apt-proxy (of course this depends on your needs).
[https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)
Is this something you're looking for?[/QUOTE]
Looks like exactly what Im looking for. Thanx man. ;) I basically want to put the repos on my network so when I want something it pulls from my network. Thanx for the info.
Real quick. I dont see if the repos have to be stored on a linux machine or not. I was planning on putting the repo on a spare drive on my windows-based server. (sorry :))

---

### Post by wrrrrrrrrrr on 2008-06-15
> **MetalMusicAddict said:**
> Im wondering if its possiable to download all the ubuntu repos. Well not the security or update ones. Just Main, Non-free or ones that dont change. My thinking is to download them, put it on a network and add it to synaptic somehow.

The Ubuntu DVDs just have Main on them right? No non-free?

hello there

please tell me, how to download all the packages from selected repositories to the apt cache?
I tried this with synaptic by marking selected packages to install but it keeps verifying dependencies every time I do that and with hundreds of packages this takes too long or it can't be done because synaptic crashes or freezes. when I say download and mark for install I mean marking selected packages to install and then choosing them only to download.

there is also a problem with package conflicts solving mechanism. some of the packages can't be marked for install at the same tame, so if I want to have them all in cache I have to mark and download them separately. I understand they can't be installed at the same time, but why the heck it's impossible to __only download__ them at the same time? it's very annoying. what I want to acomplish is to select all the packeges in a selected section or even all the packages that are available in the repos and then to download them onto my hdd, but with synaptic it's impossible because of that package conflict solving and dependency verifying (auto)functionality. can this be turned off somehow so I could download i.e. all packeges from "editors" section at once not bothering that there are some packages that can't be install all at the same time (because I don't want them to be installed at all)?

---

### Post by Xavieran on 2008-06-16
I think that the dependency solving goes beyond synaptic and into the actual debian packaging system itself.

You could try a quick search on google for "Download ubuntu repo's" or "Making your own repo"?

Emmanuel

---

