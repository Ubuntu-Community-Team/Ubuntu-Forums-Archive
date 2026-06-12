---
title: "Constructive Criticism Gutsy"
date: 2007-10-24
forum: Testimonials &amp; Experiences
---

### Post by orthorim on 2007-10-24
First off, congrats on making a linux distribution that my neighbor installed! That is a major achievement as my neighbor is A) not a geek B) doesn't know very much about computers at all and C) certainly doesn't follow "what's hot" in the world of computers.

So it's amazing that he heard of Ubuntu. It's amazing that he heard very good things about Ubuntu, from a friend who was just dissatisfied with Windows (not me). And that he proceeded to install it which was kind of successful and he was able to use it and liked it.

The catch? He innocently tried to install Ubuntu on an external hard disk, thinking that if everything goes haywire, at least he didn't destroy his Windows install. However, what happened was just the opposite: He destroyed his Windows install. Because grub looks for its config file now on the external hard drive and his is a laptop, when the external hard drive is not plugged in he gets a black screen with an error message (this is when he called me rather desperately)

So here is what's missing to make Ubuntu ready for the desktop:
1 - Grub install needs to either install its menu.1st and other config files somewhere on an internal disk, or it needs to pop up big warning dialogs when users try to install it on external disks or USB sticks. As it is, Ubuntu will happily install on a USB stick or an external hard drive without any warnings whatsoever, and you only find out what it did when it's too late - that external drive now has become a permanent part of your computer system or you won't boot. Grub needs to be a lot better, or at least whatever is installing. People need to be able to try installing Ubuntu on external hard disks.

I don't think this is just a minor issue - I think this is THE issue. Because the first and most important thing about any software is that it doesn't destroy the user's data or systems. That it leaves what's already running untouched.

2 - my ATI X1600 mobility was detected, but I could still not set the screen resolution correctly. That's weird because it all worked automatically in Feisty. In Gutsy, I had to resort to some command line Voodoo to get my screen resolution and 3D acceleration to work.

3 - the attitude towards "restricted" drivers needs to improve. I applaud that these are now automatically downloaded on demand, that's great. Well, it's also needed, there really isn't any other choice. But I think the warnings when using restricted devices are way over the top - I don't need a lesson in free software when installing an operating system. The only thing that matters to me, as a user, is whether or not my hardware works. The how and why is absolutely secondary, restricted driver or whatever, I don't care. 

If the ATI drivers don't work - and I think there is much hostility in the open source community towards ATI, most of it probably justified - then I want to complain. To ATI. However, I don't want to complain or see warnings if the ATI drivers just happen to be not open source - it's ATI's choice, it pisses off OS people but honestly I, the user, don't want to be involved. I would appreciate if ATI played nice with open source, but I don't need the warnings etc when installing these drivers. 
It's not like I can make a statement by not installing these drivers - I need them for the hardware to work. The dialogs may as well say "I don't like your face". Ok, well, maybe you don't like my face but I can't change it so it's kind of useless to point this out. It serves no purpose.

All for the best, peace - Orthorim.

---

### Post by zero244 on 2007-10-24
Actually its a fluke accident that I am using Ubuntu. I hadnt even heard of it.......a freind gave me a Dapper CD which I tried out.
I installed it and used it for a day or so and liked it so much I did some research and eventually upgraded to Edgy, which was the latest release at that time.
I am still using Edgy on this machine and it runs beautifully.
If my friend hadn't of lent me the Dapper CD I would still be using XP for everything.
I had no intension of ever going to Vista.
So finding Ubuntu was really good timing.

---

### Post by 3rdalbum on 2007-10-26
1. I agree - GRUB needs a bit of work. Unfortunately, what it can do is constrained by the ancient concept of the BIOS. The PC vendors really need to scrap BIOS and replace it with one of the competing, technically-light-years-ahead systems for managing the boot process. (EFI, OpenFirmware, LinuxBIOS or something else).

3. I installed Feisty onto a friend's laptop, and quickly got annoyed with having the Restricted Drivers Manager complaining on every login. Many people hate it when Windows nags you about every little thing ("New USB device detected", "A network cable was unplugged", etc), so this is really something that the Ubuntu developers need to reconsider. RDM is the first thing I remove from the startup programs on all new installs.

---

### Post by armandh on 2007-10-26
the driver warning is not about today
it is a reminder that with tomorrows problems you are on your own.
yes I use restricted drivers and codex but I am sticking with 7.04 for a while. 
I tried 7.10 studio just for fun and it loaded fine to a spare hdd. 
Ill play with it and gutsy but why change what ain't broke?
just not an early adopter I guess.

still I think Ubuntu is the best Linux distro for us noobs
many thanks to the teams for an OS that really is ready for civilian desktop.

---

