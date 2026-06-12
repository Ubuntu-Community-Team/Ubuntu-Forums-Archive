---
title: "recording interface and hifi listening"
date: 2010-10-09
forum: Ubuntu Studio
---

### Post by Hans Gruber on 2010-10-09
Hello,

I am getting a new computer very soon and would like to run ubuntu on it. I am an audiophile and a musician. So my computer will be used a source for music. I have never had ubuntu before so I have some questions....

1. I would like to have my computer as part of my head phone setup. Is Foobar and ubuntu compatible? (thats my favorite music program) Also the DAC I would be using with my computer would be the Audio GD FUN. it connects through usb so it can bypass the computer sound card. Does ubuntu instead of windows affect how that works will it still work? 

2. I like to dabble in recording. So how good is Ardour? (in comparison to pro tools LE?)
Also I think an interface would be good to have if I want to get any recording done.:P
 I have an old Aardvark direct pro does this work? I don't care about the aardvark software since  it is ancient. Is it possible for me to just plug the interface into the computer and bypass the the card or is there way for me to use the card? It was  really expensive back in the day and has very high quality components just really old software.

sorry I don't no very much about ubuntu. Thanks for the help guys.
peace,
Matt

---

### Post by cchhrriiss121212 on 2010-10-10
Foobar is a Windows program so that means you will have to run it through WINE, I've heard it runs OK but I advise you to use native programs when they are there: Quod Libet, Deadbeef, Guayadeque, Amorak, Rhythmbox these are all capable audio players.

The hardware you will have to try and see, I'd say your DAC has a better chance of running in Ubuntu as it is somewhat new. To try it out run a live cd with the device connected and check the preferences>sound app.
The Aardvark seems to be unsupported as the company has gone bust and also refused to release the source code. But you could always try it out.

Hardware support on Ubuntu and other Linux OSs is not the greatest as it is a comparatively small user base, so companies are reluctant to spend time designing drivers. 
Linux is open source however, which means if the company agrees to release the source code of how their products work, people in the linux community can make their own drivers and build them into the kernel. Some manufacturers are good with this and others are not so good, so make sure you research before buying anything like printers, soundcards, GPUs and other peripherals.

---

### Post by Hans Gruber on 2010-10-10
Ok thanks that helps me understand linux better. 
thanks for the post it is very helpful.
peace,
Matt

---

### Post by Pablo_F on 2010-10-10
> Today, Linux works with more devices than any other OS in the history of the world. However, this is no comfort when there's no support for the device you need to use.

Unfortunately so.

The full article:

[http://www.linuxfoundation.org/collaborate/workgroups/technical-advisory-board-tab/linuxdevicedrivermodel](http://www.linuxfoundation.org/collaborate/workgroups/technical-advisory-board-tab/linuxdevicedrivermodel)

Cheers! Pablo

---

### Post by Hans Gruber on 2010-10-10
Would it be possible for me to use wine for the aardvark or does that not work, because the source code was not given. It would work on windows 2000 or 1998 I think. I think it worked on my xp too. Would be possible to run it in an older OS. Then put the signal into Ardour? Because you can use windows inside linux right?
peace,
Matt

---

### Post by Pablo_F on 2010-10-10
With wine you can run windows apps in Linux, but afaik it is useless for hardware drivers. 

You can also run Windows inside of Linux in a virtual machine, but I don't see a neat way for recording from your card in the windows VM to ardour in Linux. I don't say it is impossible but it could be very tricky and there would be too many software layers, some of them unclear to me. 

Afaik, the best pro audio PCI cards that work fine in linux are some RME cards. 

This is the alsa project, kudos to them:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Cheers! Pablo

---

