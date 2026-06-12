---
title: "PCI on Emachines T3508"
date: 2008-01-06
forum: The Cafe
---

### Post by BLTicklemonster on 2008-01-06
I have an emachines T3508 that was messed up, but I've got it limping along now (much better than the computer I was using before, so I'm really interested in getting it working better than it is) and the problem I have is that the on board ATI video is - well, it's ATI. The only game I really ever play is Unreal Tournament and ATI pretty much stinks in UT. I have a PCI card that is an Nvidia that I'd like to try to use, but alas, it appears as though it does not wish to work. I can't get to my desktop at all. I can get in to the command line in recovery but if I reconfigure xserver-xorg, I reboot, and still can't get to the desktop.

(have yet to try removing fglrx, then installing nvidia, and booting, though)

Anyway, even tough the bios settings for video have pci listed as an option, I wonder if it will actually work.

Does anyone out there have any experience with this? I intend to get a pci express card later on, but want to try to get this pci working in the interim.

(btw, ubuntu works great on this machine. and yes, I have the latest ati drivers installed)

---

### Post by BLTicklemonster on 2008-01-06
Okay, I got closer. By removing the xorg-driver-fglrx using synaptic... which actually did not remove it, but gave an error, so I hit ctrl alt f1, and tried it manually, whereupon I saw that it would not remove it with compiz-manager error, so I tried removing compiz-manager, and it nutted up, so I tried removing compiz, and what do you know, it said it could not find the xorg-driver-fglrx, so I reckon I got along somewhere to removing the driver, as is evidenced by the following) I got to actually show it as nv in /etc/X11/xorg.conf but it still won't boot, nor will it go into the fail safe mode. the var/log file shows it still recognizes there being an ati card along with the nvidia, so that may be a problem. I have looked over the info on grant county 1 rc410 mother boards to see if there's a jumper to set to disable the onboard, but the only info available on installing a pci card is to set it in bios. 

Trying times, these. That's what I get for trying to upgrade to a nicer machine, I guess.

:)

Oh, and I can't even use the live cd with the card. I get the old timey x won't start, blah blah message at the command line. And yes, the card is fine, I took it out of a working machine.

---

### Post by el_ricardo on 2008-01-06
have you pointed your xorg.conf to the PCI-ID? it should look something like "0:2:0", and whatever it is, you add "Option "PCI:0:2:0" to the devices section

EDIT

forgot about this command, try this in recovery mode:

```

sudo dpkg-reconfigure xserver-xorg

```

and follow the instructions (the majority of it can be left as default)

---

### Post by mips on 2008-01-06
Disable the onboard ati in bios.
First try and use the 'vesa' driver with the card before trying the 'nv' or 'nvidia' ones.

---

### Post by BLTicklemonster on 2008-01-06
I've tried 

dpkg-reconfigure xserver-xorg, and it still gives me the error that x won't start at the command line.

I've disabled the onboard and chosen the pci from the bios. but I dont' think I tried vesa. I'll have to give it a go later on. I just now got back to ati on the desktop, and will have to cook supper, and get a fire going (brrr) before I can come back and work on it more. BTW, hi mips, good to see you again.

I'm thinking I'm not removing the ati drivers efficiently enough or something, and ubuntu is confused.

Also, I have tons of ati cards laying around, agp and pci, both, but not a single other nvidia pci to try it with. :(

I also find it interesting that the live cd won't boot with this card being used.

on a side note, I can't boot to windows, ntldr is missing. I try to boot with the xp install disk, but all I see it checking devices or whatever is the first thing to come up, then nothing. This is with either disk I have, both of which work fine in another computer! And the dvd drive works fine.

I may be just stuck with ati, I don't know. I hope not!

---

### Post by BLTicklemonster on 2008-01-06
Okay, it's PCI:2:4:0, so now I'm at my desktop with the nvidia card in Vesa.

I tried to enable the restricted driver for it, but I can't shake the xorg-driver-fglrx. I'll keep messing with that for now. Oh, and my mouse won't scroll (probably fix that with xorg.conf edit and my sound appears dead. There's a "no" symbol over the speaker icon on my bar. Hovering over it only says that my front mic is muted. I looked at it in more detail, and it had chosen to be HDA SB (Alsa Mixer), not SB Live 5.1 like it should have been. Changing it to SB LIve 5.1 didn't do any good. I'll play with removing the xorg-driver-fglrx and see what I can do.

Any help is and would be and has been appreciated.


*edit:

Okay, this thread [http://ubuntuforums.org/showthread.php?p=4087731#post4087731](http://ubuntuforums.org/showthread.php?p=4087731#post4087731) fixed that for me. Now to get the sound to work!!! Oh, using my old mouse settings from an earlier xorg.conf got my mouse wheel and buttons working right.

---

### Post by BLTicklemonster on 2008-01-06
Sound issue resolved. I ran alsamixer and it showed the realtek sound card, and that got me to wondering if it was somehow enabled in bios (which it wasn't earler).

Lo and behold the gremlins tried one last time. It was enabled. I disbled it, and have sound back, so this thread is resloved now.

(I've never gotten gears this high before:

glticklemonster@ticklemonster-desktop:~$ glxgears
5268 frames in 5.0 seconds = 1053.566 FPS
5269 frames in 5.0 seconds = 1053.790 FPS
5262 frames in 5.0 seconds = 1052.325 FPS
5268 frames in 5.0 seconds = 1053.412 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
ticklemonster@ticklemonster-desktop:~$ 

usually only in the mid hundreds at best, ever)

thanks again to everyone.

---

### Post by mips on 2008-01-07
> **BLTicklemonster said:**
> Okay, it's PCI:2:4:0, so now I'm at my desktop with the nvidia card in Vesa.

I tried to enable the restricted driver for it, but I can't shake the xorg-driver-fglrx. I'll keep messing with that for now. 

Search for posts by 'tseliot' and maybe check out his website/blog. He is quite the wizard when it comes to the video stuff.

---

### Post by BLTicklemonster on 2008-01-07
It's all good now. Runs smoother than before, and everything is working perfect. 



This thread [http://ubuntuforums.org/showthread.php?p=4087731#post4087731](http://ubuntuforums.org/showthread.php?p=4087731#post4087731) fixed it for me. Reinstalled compiz, and it does something I haven't seen since Beryl.

[[IMG]http://img412.imageshack.us/img412/6205/peelbackcj0.th.jpg[/IMG]](http://img412.imageshack.us/my.php?image=peelbackcj0.jpg)

I didn't know compiz did that peel the corner thing.
Thanks for the help!

---

### Post by mips on 2008-01-07
Glad to hear you got it working.

The link you posted does not work, maybe fix it incase others have the same issue.

What happened to your old avatar? I kinda remember people by their avatars ;)

---

### Post by BLTicklemonster on 2008-01-07
:) which avatar? :)

[http://ubuntuforums.org/showthread.php?p=4087731#post4087731](http://ubuntuforums.org/showthread.php?p=4087731#post4087731)

wherein it is stated:

>  insert_name_here  insert_name_here is offline
Just Give Me the Beans!
	  	
Join Date: Nov 2006
Beans: 73
Thanks: 0
Thanked 0 Times in 0 Posts
Can't uninstall xorg-driver-fglrx
I'm trying to uninstall xorg-driver-fglrx.

However, when using either the Synaptic GUI or with aptitude on the command line, I get an error message:

Quote:
merrillj@merrillj-laptop:~$ sudo aptitude remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages will be REMOVED:
xorg-driver-fglrx
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 27.0MB will be freed.
Writing extended state information... Done
(Reading database ... 119592 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
__________________
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
insert_name_here
View Public Profile
Send a private message to insert_name_here
Find all posts by insert_name_here
Add insert_name_here to Your Buddy List
  #2   Report Post  
Old 2 Weeks Ago
insert_name_here insert_name_here is offline
Just Give Me the Beans!
	  	
Join Date: Nov 2006
Beans: 73
Thanks: 0
Thanked 0 Times in 0 Posts
Re: Can't uninstall xorg-driver-fglrx
Oh hey look.

Manually deleting the /etc/xdg/compiz/compiz-manager.ubuntu fixes it, although it probably erased my settings. Oh well.

so I just deleted /etc/xdg/compiz/compiz-manager.ubuntu, then

sudo aptitude remove compiz

 which removed ubuntu-desktop which panicked me for a second, then once that was done, I 

sudo aptitude install compiz gnome-desktop 

and all was well again.

---

