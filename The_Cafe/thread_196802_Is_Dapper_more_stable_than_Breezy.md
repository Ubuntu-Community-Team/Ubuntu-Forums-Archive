---
title: "Is Dapper more stable than Breezy?"
date: 2006-06-14
forum: The Cafe
---

### Post by Nonno Bassotto on 2006-06-14
It's sorry for me to say this, I had great hopes for Dapper, but I can't really understand how Dapper can be considered a stable system. Just today, it crashed two times, and I didn't play with Xgl or anything. :( I also did a clean install, so I should not have problems.
I can live with crashes, but is this the linux stability? I was happy with Hoary and then Breezy; Dapper is in my experience far more unstable than Windows ever was. I hope other people had different experiences, and show this in the poll. I will hardly be able to persuade anyone to use Linux if I have a crash while showing it (anyone remember Bill Gates' BSOD?).

---

### Post by aysiu on 2006-06-14
Based on my own experiences and the experiences of those I've seen in these forums, I'd say Dapper is quite stable... once it's installed.

A lot of the instability appears to be in the new Ubiquity Desktop CD installer and accompanying GParted partitioning utility.

---

### Post by Azrael on 2006-06-14
The over the top options make this poll completely useless. Why can't I vote for "haven't noticed any difference"? ](*,)

---

### Post by Nonno Bassotto on 2006-06-14
This should be option three: "Crashes?!? Does Ubuntu ever crash??". I choose not to put an option which said something like "They both crash", hope this does not happen.

---

### Post by Turgon on 2006-06-14
My two systems keeps crashing randomly (both are perfectly stable in windows and breezy).

---

### Post by djsroknrol on 2006-06-14
aysiu...

> A lot of the instability appears to be in the new Ubiquity Desktop CD installer and **accompanying GParted partitioning utility**.

What part of it is instable?

Here I'm ready to repartition and use partimage to do some major moving, and I need to be concerned about Gparted?...which one..the one on the installer or is [**this** ]("http://www.psychocats.net/ubuntu/partimage.html")way safe. Or safer maybe?

---

### Post by IYY on 2006-06-14
On one of my machines, Breezy crashed constantly, and Dapper never did. It's a hardware issue, so I don't blame Breeezy (I got nasty blue screens in XP as well), but for me Dapper has been perfect.

---

### Post by aysiu on 2006-06-14
The link you put in your post is to something called PartImage, which makes a backup copy of your partition. It is not a partitioning program; it's a backup program.

A partitioning program takes your existing partitions and resizes them, deletes them, creates new ones, etc.

Generally, I think GParted and QTParted don't always work the way they're supposed to. Sometimes they grey out options that should not be greyed out. Sometimes GParted will fail for no particular reason or tell you you can't format a particular partition because it's mounted (even if it's not mounted).

I don't know if it's because people have had to actually *use* GParted more that there seem to be more GParted-in-the-installer problems or if it has something to do with the way GParted is integrated with the Ubiquity installer that's causing problems...

... or people are just complaining. I don't know. But I have seen a lot of threads over the last three weeks complaining about the new live CD installer--crashing, freezing, failing.

Does it happen to everyone? Certainly not. It hasn't happened to me. I'm just going based off what I've seen. Relative to Breezy and Hoary, I've seen a lot more complaining about Ubiquity and GParted than the text-based installers of the past (well, you can still use it with the Dapper Alternate Installer CD).

The only foolproof partitioning program I've used is DiskDrake on PCLinuxOS and Mandriva. I highly recommend it all the time, but people don't want to download another distro just to partition.

---

### Post by djsroknrol on 2006-06-14
> The link you put in your post is to something called PartImage, which makes a backup copy of your partition. It is not a partitioning program; it's a backup program.

A partitioning program takes your existing partitions and resizes them, deletes them, creates new o

Sorry...I put a link in there that was erronious..What I meant to ask was if the installer CD has issues with Gparted, is there a better or safer way to repartition by way of Ubuntu? Your way sounds best as I've heard of DiskDrake from others,  but it is a hastle to d/l another distro.

---

### Post by jimrz on 2006-06-14
i installed using the dapper rc "alternate" cd, after seeing quite a few comments/questions here re problems with the gui installer, to both my desktop and laptop and have had NO crashes or any other signs of instability on either thus far. this seems to support aysiu's statement and my own observation regarding all the traffic here about the new intaller.

  To be fair, having run breezy from Oct thru May on both boxes i only had 1 crash and it was due to a bad bash cmd (my sometime sloppy typing / inattention to detail being entireyl to blame) on the lt. even then, after a hard freeze (had to remove the bat to pwr down), i was able to boot in recovery mode, correct my error and got right back to problem free breezy operation.

---

### Post by John.Michael.Kane on 2006-06-14
Stability is not based on software alone. the endusers hardware also plays a part as well. sure Hoary/Breezy were stable, and Dapper is to however this is on the hardware i use. another enduser who's hardware would be diffrent then mine might not have such a great end result. for the OP to ask is dapper more stable then xyz os he/she should also ask is it stable or not on the hardware being run. dapper may crap out for one user yet suse/fedora/gentoo may work out the gate.


just my thoughts..

---

### Post by aysiu on 2006-06-15
[QUOTE=djsroknrol]Sorry...I put a link in there that was erronious..What I meant to ask was if the installer CD has issues with Gparted, is there a better or safer way to repartition by way of Ubuntu? Your way sounds best as I've heard of DiskDrake from others,  but it is a hastle to d/l another distro.[/QUOTE] I don't think GParted is unsafe. I haven't read any threads about it damaging anyone's hard drive. Mainly, it just doesn't appear to do what people want it to do (won't resize, won't create a new partition, etc.).

Very few people think it's worth downloading another distro, but if you have broadband and a CD burner, it's not that big a deal. You just start downloading the PCLinuxOS ISO before you go to sleep. In the morning, it's ready to go. PCLinuxOS is also a fun distro to have around--it's another live CD that can install, and it comes with proprietary codecs.

I happen to use Ubuntu because of the forums, and because PCLinuxOS can't detect my sound card or USB mouse, but it's got a hell of a partitioning program!

---

