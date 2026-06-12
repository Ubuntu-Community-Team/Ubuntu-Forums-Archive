---
title: "Dapper drake not user friendly: Kernel upgrade, ACX driver"
date: 2006-06-16
forum: The Cafe
---

### Post by robert114 on 2006-06-16
Hi, first of all I apologize for my language.

But as a Linux enthusiasm i'm kind a disappointed in dapper drake! the wireless support for ACX cards is really.... well just below what i expect from a great distro like Ubuntu.
[B]
wireless ACX[/B]
first my card which worked with breezy doesn't work well in dapper i have to make symlinks to the right driver which need to be done every time after the kernel gets an update this aint a problem for me but it's kind a hard to explain it to people that linux is a lot better and user friendly than windows is!

you can read an other ACX tread on ([http://ubuntuforums.org/showthread.php?t=186782](http://ubuntuforums.org/showthread.php?t=186782))

To make matters worse i use an AMD proc and I've just upgraded the kernel to the 2.6.15-25-k7 kernel and the acx drivers were just gone!!!! how unbelievable they aren't included in this package WHY???
Again, copying the drivers from the old kernel to the new one is not a problem for me! but it's not easily done by a regular user like my mom! And if Ubuntu wants to be a user friendly OS this kind of things just can't occur!
[B]
Kernel upgrade[/B]
secondly why do i have to manual install new kernel packages like the AMD specific packages (2.6.15-25-k7) after an update? the i386 packages do flawlessly get an automatic upgrade but the k7 packages not! I can't ask my mom to do this manually! she just knows how the computer boots and she barely knows how to upgrade the machine. but i can't ask her to install a new kernel! it is easy i know! but you just don't ask your mum or an other person who isn't familiar with computers to just install a kernel!

I hope I've made some attention to the leading Ubuntu people because these problems I'm suffering here are in my opinion just irritating! and not user friendly. I hope this tread will start some discussion because I really feel the quality of Ubuntu is going downwards

I've seen more complains about Ubuntu (Dapper Drake), and i can't say i disagree just read this from tectonic:
[http://www.tectonic.co.za/view.php?src=rss&id=1026](http://www.tectonic.co.za/view.php?src=rss&id=1026)
I really wish these problems didn't occur because I love Linux and especially the Ubuntu spirit! It is indeed a great OS for me. But I can't let others enjoy Ubuntu if there are problems like I've described above!

Edit:  Zpelingtcheek maake tings mush mor reedabbly 4 U

---

### Post by Gustav on 2006-06-16
If you install the meta package linux-image-k7 (or linux-k7 if you want the restricted packages as well) upgrades will be done automaticly.

---

### Post by tseliot on 2006-06-16
Installing **linux-k7** will make sure you always (automatically) get the latest restricted modules together with the kernel.

---

### Post by prizrak on 2006-06-16
There is very little point in the optimized kernel. The 386 kernel has the same performance as the 686 and the K7 kernels, so that's hardly an issue. ACX card I'm not too sure about but you should create a bug report as it is DEFINETLY a bug, there is no reason for it to have to be symlinked to the right driver. 
Best Linux machines for newbies are System76 and Emperor Linux machines, as they are the equivalent of Dell for the Linux world, everything is guaranteed to work.

---

### Post by DoctorMO on 2006-06-16
Interestigly I had to recompile the acx driver from source because of a bug with master mode, they had changed the name from acx-pci to just acx and all that was required was a change in modules.conf and an updating of my kernel headers (although I dout anyone will have to do that here).

I do hope they have put the fix I require into the kernel now, it was getting anoying to loose master mode every time the kernel upgraded it's self (you have to ping the machines you want to connect from to connect, what a bug!) not to mind but it was a one line change when I spoke to the acx developers.

---

### Post by Alpha_toxic on 2006-06-16
[QUOTE=prizrak]There is very little point in the optimized kernel. The 386 kernel has the same performance as the 686 and the K7 kernels, so that's hardly an issue.[/QUOTE]
Come and see my 2xCPU box with the 386 and 686-smp kernels...

---

### Post by prizrak on 2006-06-16
[QUOTE=Alpha_toxic]Come and see my 2xCPU box with the 386 and 686-smp kernels...[/QUOTE]
Have you tried it with a 386-smp kernel? There is obviously a difference between a single threaded and a multithreaded kernel. I wouldn't say that a K8 kernel would make no difference for an Athlon64.

---

### Post by robert114 on 2006-06-20
Well, i'd like to start a discussion about the quality and user friendliness  of Ubuntu's dapper drake. My problem concerning the above described problems may be due to inexperience with Linux and therefore Ubuntu.

But these minor problems may move people (back) to Windows. Like it is a painfull job to configure my wireless card on the laptop.
Another example are my two soundcards one time my AC97 card is the default and an other my creative Live card. I know how to solve this problem because I've been willing to search the forums but these problems do not exist on the Windows platform(It has been a while since i used it on my machine).

Anyway adding these problems, makes me to once again delay the deploy of Ubuntu on machines of friends and family!

I'm not bashing here, but the problems such as described here need to be polished before a version should be send in the world. I know it's an allmost impossible and pain staking job to do it! But it is realy nessecary to bring Linux to the people who can stap over from Windows.

What do you think about these things described above?

Do you think the development period for a Ubuntu version may be to short to solve these problems?
I do realy think it is, for an LTS version!

---

### Post by WildTangent on 2006-06-20
[QUOTE=robert114]Another example are my two soundcards one time my AC97 card is the default and an other my creative Live card. I know how to solve this problem because I've been willing to search the forums but these problems do not exist on the Windows platform(It has been a while since i used it on my machine).[/QUOTE]
If you're not using it, disable it in the BIOS. I was having all sorts of problems in Linux AND Windows when I left my integrated sound enabled after installing my Audigy card.

-Wild

---

### Post by cbahimsa on 2006-06-21
> To make matters worse i use an AMD proc and I've just upgraded the kernel to the 2.6.15-25-k7 kernel and the acx drivers were just gone!!!! how unbelievable they aren't included in this package WHY???
Again, copying the drivers from the old kernel to the new one is not a problem for me! but it's not easily done by a regular user like my mom! And if Ubuntu wants to be a user friendly OS this kind of things just can't occur!

Do you mind posting or emailing me your instructions for how to copy the drivers. I have the same problem with my AMD laptop and DWL625 card. Works great with 368 kernel but zero wireless with KZ. Thanks.

---

### Post by jan on 2006-06-21
Well i had trouble with sound after upgrade to dapper final system updates solved that after two weeks... :(

---

### Post by cbahimsa on 2006-06-21
> 
Quote:
To make matters worse i use an AMD proc and I've just upgraded the kernel to the 2.6.15-25-k7 kernel and the acx drivers were just gone!!!! how unbelievable they aren't included in this package WHY???
Again, copying the drivers from the old kernel to the new one is not a problem for me! but it's not easily done by a regular user like my mom! And if Ubuntu wants to be a user friendly OS this kind of things just can't occur!

Do you mind posting or emailing me your instructions for how to copy the drivers. I have the same problem with my AMD laptop and DWL625 card. Works great with 368 kernel but zero wireless with KZ. Thanks.

No need actually. Installing the restricted module added the driver. There may be a good reason why they are separate installs but at least it works now.

---

### Post by nalmeth on 2006-06-22
Seeing as the OP wanted to start a discussion about the user-friendliness of Ubuntu, don't you think we should oblige him at least little? :p

Honestly, I don't think your mom would need to fetch the specified kernel for that processor, and as long as there was someone around to setup the wireless for her (she might not be able to do it in windows either) she probably wouldn't need much more help beyond that. As mentioned, the i386 will "just work" and probably "work *well*" for most people. 

Naturally, linux is in development, and there is no tangible, lofty peak of ultimate user (or idiot) friendliness. At every advancing stage, people have to be willing to learn at least a *little* about computers to use them. 

You had to learn how to use a keyboard and mouse didn't you? 

If these are the types of things that discourage you from spreading linux, I think you should reflect on whether less-technical people (the ones who would be scared off by the kernel updates) would need or even want to update their kernel, and update the modules for their wireless driver everytime. 

You have a point about the wireless working out of the box though, you should file a bug report about that one. :-)

---

### Post by prizrak on 2006-06-22
I think that you (as many) forget that Windows is normally preinstalled. You cannot have a debate about how easy an OS is for a user if the said user has to install the OS in the first place to even try it. Few regular users can install Windows from something other than a restore CD we cannot expect them to install Linux.
That said installing Dapper on fully supported hardware (as I have) is extremely easy and requires very little tinkering. I mean I had to put my WPA key in to configure the wireless and transfer my address book and bookmarks but on the technical side everything worked well :)

---

