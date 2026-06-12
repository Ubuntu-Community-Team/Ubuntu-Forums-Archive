---
title: "Dappar drake, another painless upgrade!"
date: 2006-06-02
forum: Testimonials &amp; Experiences
---

### Post by PatrickMay16 on 2006-06-02
Yes!

I installed Ubuntu on this machine back in September 20, 2005, version Hoary 5.04. Then Breezy came around and I upgraded then just fine. On this same Breezy system it was finally time to upgrade to Dapper, and it went painless again. There were some dependency problems with some old package I had which got in the way, but that was easily solved.

I'd like to say a great big thanks to the forum and community. Without all of you I'd never have been able to make much use of Ubuntu. Also a great thanks to all the developers.

---

### Post by Adam (NZ) on 2006-06-03
Subject line says it all!

I did a fresh install over an old 5.04 setup. As before, Ubuntu found my router, my Windows network and my (shared) printer - just like that! It even downloaded and installed Samba for me when I tried connecting to the (Windows) network.

I'm a web developer, so next step was Apache/PHP5/MySQL. I though I may have to do a LAMP install for this, but NO! Just marked it all in Synaptic and let her rip! Quite unbelievably, I fired up Firefox with a phpinfo() page and the whole thing just worked. I have yet to go near either a terminal window or an ini script - it's been a *totally* GUI experience so far. This is impressive stuff! Of course I'll be tweaking things from here, but to work instantly with the basic defaults if nothing short of fantastic.

This really has to knock the "geek" Linux stereotype on the head once and for all. I wish all concerned with Ubuntu all the luck in the world - they deserve it.

Adam (NZ)

Where men are men, sheep are sheep, and diallup is faster then broadband!

---

### Post by geoguy on 2006-06-03
In contarst, I did not think that this upgrade experience was very good. As a matter of fact it sucked.
Last time when I did a fresh install from 5.04 to 5.10, I backed up my entire data on /home, which is on a separate partition, just incase something might happen to it. Nothing did, everything was all where I left it. The new install was so easy.
This time though, the install is shocking. I don't like the fact that you boot into the OS, everything goes much slower. The installation is also a lot less customisable than last time, and it seems like you are forced to format every partition that is to be used on the filesystem. Maybe I did something wrong, but it looked like it would go fine to me. But it wanted to format /dev/hda4 when all it had to do was mount it under /home. what is going on here?
I'm quite disapointed at the usability of this install. No distro at all that I have used has had such a difficult installer.
Well I didn't back up my data, and in the summary of what it was going to do to my system it told me /dev/hda2 and /dev/hda4 were going to be formated. When I clicked install i assumed /dev/hda4 was / (because i assumed that it should be formating this as ext3), I realised /dev/hda2 was swap because it was being formated as swap. Just after I clicked continue, i realised that /dev/hda4 was my home folder. I clicked cancel/abort but this was too late though.
I don't think I like ubuntu much anymore :( I haven't decided yet.

---

### Post by Jammy_Stuff on 2006-06-03
You don't have to format. When you assign the partitions assign the home partition to the correct one and make sure that the Format? checkbox is unchecked.

---

