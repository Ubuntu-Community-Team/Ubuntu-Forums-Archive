---
title: "Ice_cone's ideas for Ubuntu"
date: 2007-12-15
forum: Ubuntu Brainstorm
---

### Post by Ice_cone on 2007-12-15
1) A built-in compact look(gtk theme), the icons and toolbars in the built-in themes use WAY too much space (Click here if you do not understand : [http://ubuntuforums.org/showthread.php?t=639936](http://ubuntuforums.org/showthread.php?t=639936))
2) A default beautiful frame, icons and toolbars should be more colorful and glossy.
3) Prompt for popular essential proprietary software installation during setup ubuntu installation.  Softwares like Adobe Flash Player, Sun Java are really popular, but many people do not know how to install them.
4) Built-in audio and video codecs.  Many people do watch video, it's quite annoying to download the codecs before watching, and they are small in size anyway.
5) In the Right click menu of files in desktop/nautilus, add a "open as root" option, allow easy editing of system files. (without using sudo nautilus or gksudo gedit ...)
6) Better fonts - viewing Traditional Chinese in any built-in fonts is terrible.
7) Better network management.  Linux graphical network management is pretty poor.  I have no idea how I can disable a specific connection in Gutsy.  (in windows it's much better, and status like "disabled", "network cable unplugged" are shown clearly)
8 ) Don't use swap if there is ram!  auto reallocate the swap to ram once ram is freed again! 
9) Easier way to compiled and install applications from source code and .rpm.
10) Official hardware.  What makes macs work?  an OS which works on a few hardware.  I don't like OS that can only work in little hardware, but 1 of the major problem of ubuntu is no hardware supports it.  Almost none of the notebooks (dell is still shipping Feisty, and system76 is not available anywhere outside NA) fully support it (especially features like suspend, hibernate and compiz fusion)  It would be nice if there is some hardware that fully supports the best os in the world.


Thanks for reading.

---

### Post by smartboyathome on 2007-12-15
1) Thunar sports that compact look, try it instead of Nautilus. Try using [this guide]("http://www.psychocats.net/ubuntu/nonautilusplease") to do it.
2) Beauty is in the eye of the beholder. Something you may think looks good may not look good to someone else.
3) This is being taken care of with Ubufox. Ubuntu technically CAN'T do that because of the meathods used for installation and the fact that it is illegal to distribute them (for now).
4) Like above, it is illegal to build in the codecs because in some countries (like the US) they are illegal.
5) This has been discussed before, and the resolution was that instead we should elliminate the need to open a file as root (as that can be a powerful option and can screw your computer up).
6) I don't know Chinese, so I have no comment.
7) The network manager is being worked on, and will be WAY better in hardy.
8) I like using SWAP because I don't have much (512 MB) ram and it gives me more ram to work with (I have a HUGE hard drive, anyway).
9) Ubuntu's solution is to elliminate the need to compile. They will probably never include a way to compile things from source or RPM. :(
10) There are tons of hardware that Linux supports, though there is also tons that doesn't. If Ubuntu went the way that Mac did, then it would probably die out quickly. My view is that we try to make the hardware support as good as possible, and eventually more users will come. Once we get enough users, more hardware manufacturers will make drivers for Linux, and the cycle continues.

---

### Post by SunnyRabbiera on 2007-12-15
> **Ice_cone said:**
> 1) A built-in compact look(gtk theme), the icons and toolbars in the built-in themes use WAY too much space (Click here if you do not understand : [http://ubuntuforums.org/showthread.php?t=639936](http://ubuntuforums.org/showthread.php?t=639936))

well maybe there should be to decrease the size of the icons, like what you can do in KDE where you can adjust the size of the icons

> 2) A default beautiful frame, icons and toolbars should be more colorful and glossy.
well not everyone likes glossy or glassy themes, but it is easy to install new themes though if you dont like the default looks.the cool thing with ubuntu and linux in general is you can dress it up in whatever way you want.
> 3) Prompt for popular essential proprietary software installation during setup ubuntu installation.  Softwares like Adobe Flash Player, Sun Java are really popular, but many people do not know how to install them.
4) Built-in audio and video codecs.  Many people do watch video, it's quite annoying to download the codecs before watching, and they are small in size anyway.


well there is legal reasoning and philosophical reasoning too on why ubuntu does not include this by default, buy maybe we could have better documentation on directing people on how to install these things.
But there are distros that do load these by default, but they do it at thier own risk.

> 5) In the Right click menu of files in desktop/nautilus, add a "open as root" option, allow easy editing of system files. (without using sudo nautilus or gksudo gedit ...)

Now this is an idea I really like to see some day, I agree there should be a GUI way of using nautilus or another app with administration privileges inseam of having to use the terminal... but one day they might do this so who knows.

> 6) Better fonts - viewing Traditional Chinese in any built-in fonts is terrible.

eh, well it is improving though, internalization is getting better by the minute.

> 7) Better network management.  Linux graphical network management is pretty poor.  I have no idea how I can disable a specific connection in Gutsy.  (in windows it's much better, and status like "disabled", "network cable unplugged" are shown clearly)

Yeh this does need work I agree, but progress is being made... trust me network management in linux is better now then it has been before and there is  a chance it will get even more better as time goes.

> 8 ) Don't use swap if there is ram!  auto reallocate the swap to ram once ram is freed again! 

well swap is good to have if you have lower memory specs like I do, so i cannot fully agree with this one.

>  9) Easier way to compiled and install applications from source code and .rpm.

well there was an app that did use a GUI shell to install source code apps but I forget what it was called plus there was issues of it.
but maybe a gui for alien would be nice

> 10) Official hardware.  What makes macs work?  an OS which works on a few hardware.  I don't like OS that can only work in little hardware, but 1 of the major problem of ubuntu is no hardware supports it.  Almost none of the notebooks (dell is still shipping Feisty, and system76 is not available anywhere outside NA) fully support it (especially features like suspend, hibernate and compiz fusion)  It would be nice if there is some hardware that fully supports the best os in the world.

the issue here comes more from manufacturers then us, remember most hardware out there only has MS or sometimes apple but really linux doesnt have any real market share to make the major hardware companies pay any real attention to us.
But as time goes there will be more companies that will eventually support linux  in the future... patience is a virtue.

---

### Post by Ice_cone on 2007-12-15
Thanks
for no. 8, I don't mean abolishing swap, just used all free ram before you start using swap, the harddisk is way slower than ram.  And if ram is very ram and swap is still used, automatically reallocate the memory in the swap to the ram (like swapoff /dev/sda2, and then swapon)
for no.10, I don't mean ubuntu only on specific hardware, but just release some official computers

ADD 11) Ability to search for a file!

---

### Post by smartboyathome on 2007-12-15
Canonical isn't trying to make money, and I still like swap because it extends my memory (and I wouldn't like to have my computer slow down to a crawl first before it realises that it needs to use SWAP).

About 11), this has been done with Tracker, though if Google would release Google Desktop under the GPL, then I would say include that!

---

### Post by Ice_cone on 2007-12-18
Look at the attachment.  I have plenty of free ram, but it is using swap instead of ram, which seriously slows down my computer.

---

### Post by Denis on 2007-12-18
> **Ice_cone said:**
> Look at the attachment.  I have plenty of free ram, but it is using swap instead of ram, which seriously slows down my computer.

The Linux kernel uses a "swappiness" value to determine how to balance swap vs. RAM. Swappiness ranges from 0 to 100. Lower values mean less swap usage. 

I don't remember the Ubuntu default, you can check yours with "cat /proc/sys/vm/swappiness"

You can change the value this way: 
[LIST]
[*]sudo gedit /etc/sysctl.conf
[*]add the line "vm.swappiness=x"
[*]when you reboot, your swappiness will be x
[/LIST]

Personaly I now use a swappiness of 10, which means using very little swap. You may want to set it this way too. I noticed a considerable change in memory usage after reducing the swappiness.

Remember that this is a personal preference, users with little RAM may prefer to use a little more swap to keep more important thinks in RAM. Maybe this value could be a little lower by default. Or a GUI option could be included to change the value.

---

### Post by Denis on 2007-12-18
Now that I'm at it, I might as wel comment on Ice_cone's remarks. Thanks for sharing them in the first place. 

1) I don't really think this is an issue. With monitors getting bigger and resolutions higher, I think people may even prefer bigger icons in the future. 

2) I would also like a consistent, good looking theme etc. I think the developers are working on that. Besides people differ in what they find "beautiful". 

3) I like the idea of Ubuntu trying to be a "free" operating system, so I don't support suggesting non-free software during the install. An easier way to install such software would be useful however. 

4) The same remark as above. If it is legally possible an easier way to install such codecs could be included. Also developers are working on that, if I'm not mistaking. 

5) That's a good idea, as long as the option is not "sitting in your way" all the time. Since most of the time you will not use it. 

6) I don't use Chinese characters, so I can't tell

7) I don't really use those tools, but the Network Settings tool looks all right. Can't you uncheck the checkbox to disable a connection? You probably want more options, which I can understand since the program looks pretty minimalistic. 

8 ) Check my reply above. Default value could be lowered with current machines. 

9) It would be great if someone made an easy program to compile (better even, to compile and create a deb-package for it). But compiling can be difficult and lots of thinks can go wrong. I think automating it isn't easy. As for rpm, it's better that users aren't encouraged to use it, since it doesn't always work. Maybe it could be opened with the deb installer, with a prompt to convert it to deb (with a warning added). 

10) I agree with that. Shops should sell "Ubuntu-proof" PC's and components should have a "Ubuntu-proof" label on them. But I think this will only be done when Ubuntu has a larger market share.;)

---

### Post by Asham on 2008-01-08
> **Ice_cone said:**
> 1) A built-in compact look(gtk theme), the icons and toolbars in the built-in themes use WAY too much space (Click here if you do not understand : [http://ubuntuforums.org/showthread.php?t=639936](http://ubuntuforums.org/showthread.php?t=639936))
2) A default beautiful frame, icons and toolbars should be more colorful and glossy.
3) Prompt for popular essential proprietary software installation during setup ubuntu installation.  Softwares like Adobe Flash Player, Sun Java are really popular, but many people do not know how to install them.
4) Built-in audio and video codecs.  Many people do watch video, it's quite annoying to download the codecs before watching, and they are small in size anyway.
5) In the Right click menu of files in desktop/nautilus, add a "open as root" option, allow easy editing of system files. (without using sudo nautilus or gksudo gedit ...)
6) Better fonts - viewing Traditional Chinese in any built-in fonts is terrible.
7) Better network management.  Linux graphical network management is pretty poor.  I have no idea how I can disable a specific connection in Gutsy.  (in windows it's much better, and status like "disabled", "network cable unplugged" are shown clearly)
8) Don't use swap if there is ram!  auto reallocate the swap to ram once ram is freed again! 
9) Easier way to compiled and install applications from source code and .rpm.
10) Official hardware.  What makes macs work?  an OS which works on a few hardware.  I don't like OS that can only work in little hardware, but 1 of the major problem of ubuntu is no hardware supports it.  Almost none of the notebooks (dell is still shipping Feisty, and system76 is not available anywhere outside NA) fully support it (especially features like suspend, hibernate and compiz fusion)  It would be nice if there is some hardware that fully supports the best os in the world.


Thanks for reading.

You bring up some good points. Thank you.

I'd like to share my thoughts after having read your post:

1) Agreed! Some applications barley fit the screen if you have a screen that is limited to a screen resolution of <1024x768.
2) More colorful icons and a nicer, more distinguished application title bar/window border would go a long way.
3) For me synaptic is good enough.
4) As an earlier poster said, it's due to legal issues. And that's too bad. :(
5) This would be HUGE! Less terminal -- easier for most (human) users. ;)
6) Don't know about this, so no comment. Sorry.
7) Agree. Good to know it's known and being improved on.
8] Don't know enough to comment. Sorry.
9) Don't know enough to comment. Sorry.
10) Agreed! I am ponding buying myself another computer so that I can get rid of the drag of dual booting whenever I have too,  It sure could be esier finding out about hardware compatibility.

---

