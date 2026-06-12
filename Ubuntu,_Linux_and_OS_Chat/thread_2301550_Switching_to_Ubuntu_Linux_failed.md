---
title: "Switching to Ubuntu Linux failed"
date: 2015-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Kljuka on 2015-11-03
I've been planing to switch from Windows to Ubuntu desktop for a while now (also due to MS snooping lately). But I failed miserably (and I'm not a linux newbie at all)... Here's my experience with Ubuntu desktop:

1. Problems with monitor positions: I have 3 monitors: 2 are connected "directly to CPU" (i5-3570k has on board graphics card for 2 monitors). 3rd monitor is connected to an old PCI graphics card (Radeon X550). Booting worked, but monitors were in wrong order (left one was on the right side) so I reordered them (which is a pain because some combinations just don't work. You have to remove them all then add one by one). After restart one monitor (the one connected to old Radeon X550) just keeps the initial image (boot image) and doesn't cooperate any more; on login screen it works as expected. After the successful login it keeps login image, mouse pointer doesn't show on it at all nor anything else. Just static login image.

2. Mounting NTFS: NTFS partition doesn't auto mount. So when I go to terminal (eg.: midnight commander) I can't browse the files. I have to first click on Ubuntu File manager which mounts the partition. Only then can I access it.

3. Moving program windows between monitors can't be done with keyboard. Sure I can do it with my mouse, but no matter how much I messed with compizconfig-settings-manager I can't convince it to use my keyboard combination (with arrow keys - it only works without them).


I have to say I'm a bit disappointed with Canonical. Am I the only one with that many problems in the first hour of Ubuntu usage. And I haven't even started really using Ubuntu. Googling for quite some hours didn't solve my problems. Then I had to move on to stay productive.

---

### Post by krishnan t s on 2015-11-03
Dont know about 1 and 3. But install and run ntfs-3g once. All ntfs drives auto mount on boot :)

---

### Post by mastablasta on 2015-11-03
why not troubleshoot at the forums?

does GPU manufacturer support your setup in Linux with their drivers and GPU utilities?

---

### Post by mJayk on 2015-11-03
2) ntfs-3g  as above 

3) 1st link on google [http://askubuntu.com/questions/141752/keyboard-shortcut-to-move-windows-between-monitors](http://askubuntu.com/questions/141752/keyboard-shortcut-to-move-windows-between-monitors)

---

### Post by mystics on 2015-11-03
> **Kljuka said:**
> Am I the only one with that many problems in the first hour of Ubuntu usage.

No. I would say that most, if not all, of the people I talk to have various issues with a brand new install. Certain computers do have more problems than others, and certain problems are more common than others, but problems are to be expected. And it would be very difficult to get a perfect Windows-like (or even more so Mac-like) experience where you just turn it on and everything works. The computer you buy in the store was designed to run Windows (or Mac). Linux users aren't getting those benefits. We're trying to force an OS onto a computer that wasn't originally designed to work with that OS. It's just not realistic to expect it to be a perfectly smooth experience and/or an easy way to fix problems you have with your computer's pre-installed OS.

The good news is, we do have support areas on the forums where you can find help in getting your computer to accept Linux: [http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

Just pick whatever subject you feel your problem best falls under.

---

### Post by Kljuka on 2015-11-03
Thanks for all replies.

@krishnan t s : the ntfs-3g was already installed. I've added the mounts manually through /etc/fstab. So mounting NTFS is solved :)
@mastablasta : Ubuntu help page assures that my graphics card is supported ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)). I've checked agan and I have AMD/ATI RV370 (Radeon X300) - which is on the list. But whenever I reorder the displays the monitor connected to Radeon freezes.
@mJayk: I've found the you provided myself as well. But the Ctrl+Alt+Shift+Right combination (and "Left") didn't work. And there's no notification which command uses it (and I have no clue how to find out what is using that key combination). Also there were quite some freezes while I was trying to set this up but now I've successfully mapped Ctrl+Shift+Right (without Alt). So this is solved somehow. (Also something crashed while setting it up - Ubuntu "there was a problem window").
@mystics: unfortunately you're completely right. I've tried Ubuntu already on my laptop (Samsung Ativ Book 9) but wasn't satisfied with the results (shorter battery life, sleep didn't work well, etc). So I thought the desktop computer could be a perfect Ubuntu candidate (when I was buying it I already made sure I bought all components that wouldn't be problematic: Gigabyte motherboard, Intel CPU, etc and no special hardware). I would be very happy if Ubuntu did have a page where they recommended the hardware that really works great (for each price range) - I would definitely buy only hardware on that list.

Well... just now I got a new completely absurd problem... on my middle screen (the one connected to Intel i5 motherboard graphics card) the mouse cursor is BEHIND the terminal window (if I minimize the terminal window I can see the mouse, otherwise not)?!? Opening new terminal window behaves OK...

---

### Post by Kljuka on 2015-11-03
I've changed the additional graphics card now (threw out AMD/ATI RV370 (Radeon X300) and inserted NVIDIA GT215 [GeForce GT 240]). The problem with frozen screen has vanished :)

Hmmm... Ubuntu is a bit unpolished in some ways. Now the "Displays" window wouldn't get visible (when clicking on icon from minimized state) so I had to close it and run again.

---

### Post by Bucky Ball on 2015-11-03
We'd love to give you some help getting to the bottom of any issues you are having if you'd like to post a thread with a descriptive title and as good a description of the issue as you can give in an appropriate support area. We can't do much here apart from watch your trevails as this area is not for support. :)

I'll add this, though: Once you do have your Ubuntu system set up and purring, you may not experience issues for quite some time. I stick to the LTS (long-term support) releases and have a basic system that is set up specifically for what I need my machine to do, and it just does what it's supposed to and has since not long after the install. Which is good because that is vital and one of the reasons I use Ubuntu. Sometimes my machine needs to be on for a long period of time and I haven't shut it down completely for a month, at a guess. 

I have other partitions, playthings for other releases/OSs, and sometimes test things as virtual machines (though not for awhile).

Much depends on the hardware, and unfortunately, Linux/Ubuntu can't do much about that. Only consumers can do something currently by using hardware that is known to be compatible with Linux. I've designed and built systems and just install Ubuntu and away you go. Everything works 'out of the box'. :D

PS: But feel free to chat on here, of course!

---

### Post by QIII on 2015-11-03
Just want to tag on to Bucky Ball.

I reiterate:  this chat area is not for support.  Please use the support areas for support.

When you post in the support areas, ask for help with one item per post.  Laundry list help queries get confusing and some users who would otherwise help just move on.

We're here to help, so ask for what you need!

Cheers!

---

### Post by Kljuka on 2015-11-03
Thanks guys. I really appreciate it.

---

### Post by mystics on 2015-11-03
> **Kljuka said:**
> @mystics: unfortunately you're completely right. I've tried Ubuntu already on my laptop (Samsung Ativ Book 9) but wasn't satisfied with the results (shorter battery life, sleep didn't work well, etc). So I thought the desktop computer could be a perfect Ubuntu candidate (when I was buying it I already made sure I bought all components that wouldn't be problematic: Gigabyte motherboard, Intel CPU, etc and no special hardware). I would be very happy if Ubuntu did have a page where they recommended the hardware that really works great (for each price range) - I would definitely buy only hardware on that list.

I'm not sure how useful it will be, but Ubuntu does have a list of certified desktops and laptops: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by Geoffrey_Arndt on 2015-11-04
> **mystics said:**
> I'm not sure how useful it will be, but Ubuntu does have a list of certified desktops and laptops: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

In addition to the above listing, for new users thinking about using Ubuntu (or any Linux OS) . . . . the experience and results can be equal or better than going to the local "big-box" store and buying the *most awsome-est* Apple product, or the latest and greatest version of of  Vista 10.    Since Linux (except Chromebooks) are generally not available at these retailers . . . the "Linux Stores" are available ONLINE. 

Last year in December I decided I didn't really want (or need to) tackle a new Linux install in the "UEFI" hardware environment.   Too many OEM's were (and still are) not complying with the UEFI standards - particularly some such as HP, Toshiba and others were not allowing for non-Windows OS's to be installed (dual-boot or sole-OS).    So . . . . I knew there were at 25 or 30 small companies that do pre-design, pre-configure linux tested hardware, and even write support drivers.  Consequently, I purchased a System76 Galago Ultra Pro 14" laptop.    To make a long story short,  EVERYTHING worked out of the box and setup took maybe 10 minutes.   No issues with graphics, printers, hibernation, audio, yada, yada, yada.

So, when we, as experienced Ubuntu users and hopefully, Linux advocates (*or at least purveyors of accurate info*) - - advise new users . . we can let them know there is a path to running Ubuntu without major issues or hassles.  


Just point your browser to [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by mystics on 2015-11-04
I agree that if someone wants to go full Linux, and if they have considered the ramifications of not having Windows or OS X on the computer, that they should really consider getting a computer with Linux pre-installed. That's the safest way to go, and it also puts Linux and Windows on more equal footing. Not to mention, it keeps money in the community you want to support.

But again, I think it is best to consider the ramifications of that. I don't know how many others are in the same position I'm in, but I constantly run into situations where I need access to Windows, and some of my hobbies are just simply better served on Windows (or are made better if I don't cut Windows off). That said, if someone has carefully determined that they aren't in that position or have an alternative way to get to Windows (e.g. old or cheap computer, virtual machine), then by all means, they really should look at the sites linked to on Linux Pre-Loaded.

---

### Post by Geoffrey_Arndt on 2015-11-04
So to be clear . . . . if someone wants Linux pre-installed, but needs Windows also:

>  Install either Virtual Box or VmWare.    Just need 6 or more GB ram on the PC so the performance will be acceptable.  Then, use your licensed Windows media or image and install away.

Virtual Box is available via the Ubuntu Software Center.

There are several good tutorials at Youtube or other websites that provide the ABC's of how to do the install.    It's often easier than installing a dual-boot on a modern UEFI machine.   Unless you're a gamer, this option works for millions of customers and companies every day.    For the more technically adept, there is also the newer Docker (Containers) - great for large firms but probably over-kill for consumer devices.

Note this also works the other way around, the host OS can be Windows - - so you're VM (virtual machine) will be running Ubuntu in virtual environment.   Probably a better solution for trying Ubuntu than using "Live Media" (which provides a slow and limited experience).

---

### Post by mystics on 2015-11-04
Just to add on: Also be sure you have the resources to run the virtual machine well enough for use. Sadly, my computer can't handle a VM, even giving it the maximum amount of resources I can. I'm not sure just how good 6 GB would be, but given that 4 GB on my computer is almost good enough, I'd imagine 6 GB should work. 

The good news is, it's very easy and free to test out, so it is worth it for anyone to try.

---

### Post by Bucky Ball on 2015-11-05
There must be something amiss with your machine, mystics, as I have no issue whatever running a vm on my i3 machine with 4Gb of RAM. I read a thread the other day where someone was assigning 1Gb to a vm and getting away with it (must have been a light OS I guess). 6Gb, not should be, is ample. If it doesn't run with 2 or 3Gb assigned to it, and you are getting insufficient RAM issues, I'd be digging deeper. :)

---

### Post by mastablasta on 2015-11-05
> **Kljuka said:**
> @mastablasta : Ubuntu help page assures that my graphics card is supported ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)). I've checked agan and I have AMD/ATI RV370 (Radeon X300) - which is on the list. But whenever I reorder the displays the monitor connected to Radeon freezes.


see also this table: [http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)

in any case something is missing in driver. or at leats the feature you nee di smissing or not implemented properly. you could try and report a bug.

---

also regarding virtualbox here is a nice and easy to follow instruction: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

and I run it on a 11 year old single core CPU with 4 GB ram (had to increase it a bit but it ran ok on 2 Gb as well). host OS is winXP and guest is Linux. ok, I can't really run Ubuntu that well, but Xubuntu, Lubuntu and similar run just fine.

---

### Post by mystics on 2015-11-06
> **Bucky Ball said:**
> There must be something amiss with your machine, mystics, as I have no issue whatever running a vm on my i3 machine with 4Gb of RAM. I read a thread the other day where someone was assigning 1Gb to a vm and getting away with it (must have been a light OS I guess). 6Gb, not should be, is ample. If it doesn't run with 2 or 3Gb assigned to it, and you are getting insufficient RAM issues, I'd be digging deeper. :)

I've always gotten VMs to run, and I can generally get by. I've just never found the experience smooth or fast enough to be something I'd advise without caution. I've had similar problems setting up VMs on other people's computers.

Perhaps I just have ridiculously high standards.

---

### Post by rewyllys on 2015-11-08
I'm running LinuxMint 17.2 with 8 GB of RAM.  For those unavoidable Windows uses (e.g., US income-tax return), I use Windows 10 in VirtualBox, assigning 4 GB to it.

The result is annoyingly slow.

For my next computer, I'm dreaming of specifying 32 GB of RAM.

---

### Post by mystics on 2015-11-08
> **rewyllys said:**
> For my next computer, I'm dreaming of specifying 32 GB of RAM.

Quite a bit of future proofing going on there!

---

### Post by mastablasta on 2015-11-09
> **rewyllys said:**
> I'm running LinuxMint 17.2 with 8 GB of RAM.  For those unavoidable Windows uses (e.g., US income-tax return), I use Windows 10 in VirtualBox, assigning 4 GB to it.

The result is annoyingly slow.


is there some classic desktop in win10? the kidn that doesn't need 2D acceleration? if not then is the 3D acceleration enabled? I am guessing it is what gives the slow result in vbox. 4 GB should be enough for 10.

---

