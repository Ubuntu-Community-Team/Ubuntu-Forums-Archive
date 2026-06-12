---
title: "Daily build"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Thomas1477 on 2012-08-21
Cannot run Quantal 12.10 from a dvd from the daily build of 08/20/12, 4 downloads, and 08/21/12, 2 downloads. Anyone able to do it?

---

### Post by Curtis6767 on 2012-08-21
No luck with daily build for since 8/16. Won't bother trying again until this xorg bug gets fixed.

---

### Post by fjgaude on 2012-08-21
The daily built didn't boot on my Intel graphics box. I will simply wait until an upgrade does.

---

### Post by jerrylamos on 2012-08-22
> **fjgaude said:**
> The daily built didn't boot on my Intel graphics box. I will simply wait until an upgrade does.
I tried yesterday with 
VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics ControlleR
using external VGA monitor, a 15" 1366x768 TV.

What a wild ride!  Pieces of windows scattered all over.  I fought for quite a while trying to get the cursor on whatever selection and gave up.  Trying to fight through drop down windows to connect to wireless WPA was hopeless.  Running Apport totally out of the question.

Tried updating the .iso today and no change, sure enough the daily build is still yesterday's.  

Jerry

---

### Post by Xgen on 2012-08-22
With daily builds the installation consistently fails like clockwork with this message using flashdrive or dvd:

```
 The installer encountered an error copying
 files to the hard disk: [Errno 5] Input/output
 error This is often due to a faulty CD/DVD disk or
 drive, or a faulty hard disk. It may help to clean
 the CD/DVD, to burn the CD/DVD at a lower speed,
 to clean the CD/DVD drive lens (cleaning kits are
 often available from electronics suppliers), to
 check whether the hard disk is old and in need of
 replacement, or to move the system to a cooler
 environment.
```

Seems to work with alphas...at least the installation part.  Setting up my video card is for another thread...

---

### Post by philinux on 2012-08-23
Spent 2 hours yesterday trying to get it to boot from live usb. Artifacts and flickering screen. Hangs so gave up. I'll sync Friday and try again.

---

### Post by jerrylamos on 2012-08-23
> **philinux said:**
> Spent 2 hours yesterday trying to get it to boot from live usb. Artifacts and flickering screen. Hangs so gave up. I'll sync Friday and try again.
Tuesday, same problem.  Flashing back and forth between drop down windows devil of a time. 

Submit a bug?  No way I could get wireless WPA connected with the flashing window disease.

Wednesday still flashing like mad, was able to complete install, but to the wrong partition!  Oh, well.  

This was with netbook running 1366x768 TV.  Up and running fine today, Ubuntu with LXDE desktop.  I use Firefox, Libre Office writer, etc. Ubuntu applications launched from LXDE.

Last night, still a bit of a battle but did get install on 3.3 gHz tower,  Not so much problem.  12.10 with LXDE desktop.

Are we having fun yet?

---

### Post by fjgaude on 2012-08-23
An upgraded install is working fine, once the defaults are adjusted to my liking. Very fast, gthperf = 3.56, much faster than anything I've ever seen on this box, my main one. Intel rules. <smile>

I still cannot boot a daily from a USB flash drive. I can wait until I can. <sigh>

Unity is looking up with the new Nautilus!

---

### Post by mc4man on 2012-08-23
The daily builds work here but Only on a desktop machine that has no Ubuntu installs/grub, ect.
Then they boot to the live session fine though do use the shift > enter > enter method

---

### Post by fjgaude on 2012-08-23
> **mc4man said:**
> The daily builds work here but Only on a desktop machine that has no Ubuntu installs/grub, ect.
Then they boot to the live session fine though do use the shift > enter > enter method

Pray, tell, what is the shift > enter > enter method?

---

### Post by mc4man on 2012-08-23
> **fjgaude said:**
> Pray, tell, what is the shift > enter > enter method?

When the live  usb is booting shift brings up the options screen
enter dismisses the lang. selector, enter picks the choice "try ....'

For some reason was more consistent then going to the default options window.

Also here of an Ubuntu multiboot the live usb doesn't work but how it fails seems to depend on whether 12.10 is installed, which install has grub-pc configured on & what version of Xorg is on 12,10

---

### Post by fjgaude on 2012-08-23
Okay and thanks... I have an install on one of the drives but grub points to an install on another drive.

Strange, strange... I'll keep trying to get a daily to boot.

---

### Post by philinux on 2012-08-23
I can get to the desktop ok but it's just too unstable to do anything. Must be graphics xorg / nouveaux or something.

---

### Post by fjgaude on 2012-08-23
> **philinux said:**
> I can get to the desktop ok but it's just too unstable to do anything. Must be graphics xorg / nouveaux or something.

I get the same thing with Intel HD3000. So... xorg!

---

### Post by jerrylamos on 2012-08-23
> **fjgaude said:**
> Okay and thanks... I have an install on one of the drives but grub points to an install on another drive.

Strange, strange... I'll keep trying to get a daily to boot.

On Lucid, Maverick, my ide boot drive is a: and the sata 2nd drive is b:

On Narwhal since, the ide boot drive is b: and the sata 2nd drive is a:

Go figure.  Wrote bugs a long time ago no Development interest.

Where it gets messy is booting a .iso and trying to figure out which is what.  I mostly sort out from the size of the hard drive.

Every once in a while during Alpha the .iso would start up with one drive assignment then switch partway thru and get confused and quit.

Grub on occacion gets all screwed up.  It's looking for a UUID on one drive and absolultely refuses to look at the other drive where the UUID actually is.  Super Grub2 to the rescue.

I have no idea how Development puts up with this.

---

### Post by nm_geo on 2012-08-23
I have been primarily testing the Lubuntu 12.10, but decided to test the live CD session  Ubuntu 12.10 amd64 current daily build 20120822.  Like Mc4man I can get the live session working by the shift>enter>enter going to the splash screen select english then Try...

If I do not go this route it ends in blank dark screen each time.

Going to try looking at terminal lines during plymouth and see what might be happening.

---

### Post by philinux on 2012-08-24
Wow just kicked of a zsync and it said "Target 6.1% complete".

That's some major change.

---

### Post by jerrylamos on 2012-08-24
Philinix, I haven't seen anything Quantal less than 700 MB ever, How's 628M.

quantal-desktop-i386.iso 24-Aug-2012 10:03  628M  Desktop CD for PC (Intel x86)

Wonder what got left out.....

Jerry

---

### Post by cariboo on 2012-08-24
Removed double post by jerrylamos

---

### Post by PaulW2U on 2012-08-24
> **philinux said:**
> Wow just kicked of a zsync and it said "Target 6.1% complete".

That's some major change.

A similar change noted in the Kubuntu ISO.

---

### Post by philinux on 2012-08-24
Just tried booting it and only icons on desktop are examples and install.

This was Try ubuntu. No top panel and no unity icons.

Also attempting to install over previous borked version gives incorrect partition sizes so ubiquity wants to do a resize.
Not doing an install until this is fixed. I'm downloading a new iso.

---

### Post by coffeecat on 2012-08-24
I managed to install from the 22nd August daily today to an Intel graphics laptop using a live USB created by dd-ing the ISO directly to the stick. It booted up to a functional live desktop OK, ran Gparted and the installer OK, but the installation hung at the end "copying log files". After xkill-ing the Ubiquity window the machine rebooted into a usable Quantal installation. So I guess I can do without the log files!

Different story with my newer nvidia GeForce 410M laptop. While the nvidia-current xorg incompatibility continues, I can't even use the nouveau driver. I get the unusable flickering desktop with this particular nvidia card + nouveau in Quantal at the moment.

---

### Post by grahammechanical on 2012-08-24
I also tried the 24/08/2012 ISO. I had to use nomodeset to get to the Install Welcome dialog box. I should not need to do that on my machine.

It installed all right but after login there was no desktop and it cannot be updated even from the Recovery mode Root prompt. It wont unlock some file or other.

Could this be a deliberate scheme to get some of us doing daily ISO image testing? :)

Or, is it a little bit of carelessness because 12.10 is not an LTS? Or, perhaps tiredness after all the effort that went into making 12.04 a suitable LTS?

Regards.

---

### Post by balloons on 2012-08-24
Expect breakage to carry into the next week. I updated the [notice board]("http://iso.qa.ubuntu.com/") to shed a bit more light onto this. Unity is landing, compiz is landing, webapps are landing, lots and lots of changes at once.. 

FYI, also images are sometimes failing to build. For instance many flavors cannot build right now due to an issue with gtk2 indicators...

---

### Post by twipley on 2012-08-24
I have installed from alpha-3 quantal, and when upgrading through the update manager then rebooting, menu bars and whatnot all have disappeared.

Not being able to drive it anywhere, I downloaded the current daily build and performed another fresh installation, which led to the same issue.

I would also advise anyone to refrain from using the daily builds... at least until future notice!

---

### Post by philinux on 2012-08-24
> **guitara said:**
> Expect breakage to carry into the next week. I updated the [notice board]("http://iso.qa.ubuntu.com/") to shed a bit more light onto this. Unity is landing, compiz is landing, webapps are landing, lots and lots of changes at once.. 

FYI, also images are sometimes failing to build. For instance many flavors cannot build right now due to an issue with gtk2 indicators...

Thats it till next week then. Even Boris Grishenko want solve it.

---

### Post by Stinger on 2012-08-24
> **philinux said:**
> Thats it till next week then. Even Boris Grishenko want solve it.
Now that's what I call a broken desktop :-&, but nothing a few tweaks and patches can't handle ?? :rolleyes: geesh !
Cheers !

---

### Post by philinux on 2012-08-24
> **Stinger said:**
> Now that's what I call a broken desktop :-&, but nothing a few tweaks and patches can't handle ?? :rolleyes: geesh !
Cheers !

If you notice the top bit on the right is a bit of Firefox back to front. That must be from residual memory too.
>·<

---

### Post by xeizo on 2012-08-24
I reverted to an older daily, 2012-07-31, and locked all X11/Xorg-packages to that version. Now I can only upgrade through Synaptic, otherwise this lifesaver will break, but it's a working compromise.

But, after locking X everything I could install the latest nvidia-current-updates and run Xubuntu again - and run 3D-games through Wine again.

Even Mozilla works!

At least I run the latest daily packages now, except X, and I have a working desktop(xfce). But, the current daily images seems to be severely broken so I'll wait before I test any again. At least not until there's a new Nvidia-driver which doesn't kill things. I hope they are in a hurry!

---

### Post by nm_geo on 2012-08-24
Just got today's 20120824 Lubuntu amd64 running on a persistent USB and it appears to be pretty clean a panel indicator applet bug that was expected.. Running on Intel graphic Dell D620 currently and will try my Lenovo T61p with Nvidia later< that should be interesting.

---

### Post by philinux on 2012-08-25
I got my netbook rescued via alpha 3 and updated. Back to testing.

---

### Post by kuvanito on 2012-08-25
gave up
will give another week b4 next clean install
it is a mess 4 now

---

### Post by fjgaude on 2012-08-25
> **philinux said:**
> I got my netbook rescued via alpha 3 and updated. Back to testing.

I did the same thing on a partition on my main box. Can't believe how the video continues to get faster, **gtkperf=2.55**. In 12.04 it is only 6.0 or so. Running Intel HD3000.

**UPDATE**: After updating 12.04 to the latest I got **4.65** w/ gtkperf. So even 12.04.1 is good.

---

### Post by ventrical on 2012-08-25
> **guitara said:**
> Expect breakage to carry into the next week. I updated the [notice board]("http://iso.qa.ubuntu.com/") to shed a bit more light onto this. Unity is landing, compiz is landing, webapps are landing, lots and lots of changes at once.. 

FYI, also images are sometimes failing to build. For instance many flavors cannot build right now due to an issue with gtk2 indicators...

Xubuntu is completely destroyed as far as trying to get that updated. The menu bars, ff and most programs just suddenly disappear.

  I haven't zsynced an .iso since the xorg/nvidia debacle... so alpha 3  is working ok still.

---

### Post by ventrical on 2012-08-25
I zsynced quantal-alternate-i386.iso and just did a fresh instal (nomodeset) and it worked just awesomely. I actually got the llvmpipe (Unity 3D) on an old nvidia card  that is not suppossed to produce Unity 3D (mind you it is very slow)  but I see where they are going with this now.

Gnome-session is working just great also.!!

---

### Post by nuttzo31 on 2012-08-26
> **grahammechanical said:**
> I also tried the 24/08/2012 ISO. I had to use nomodeset to get to the Install Welcome dialog box. I should not need to do that on my machine.

It installed all right but after login there was no desktop and it cannot be updated even from the Recovery mode Root prompt. It wont unlock some file or other.

Could this be a deliberate scheme to get some of us doing daily ISO image testing? :)

Or, is it a little bit of carelessness because 12.10 is not an LTS? Or, perhaps tiredness after all the effort that went into making 12.04 a suitable LTS?

Regards.

I got this as well, there's no desktop because you have to install unity from one of the tty's.Once you install unity and restart it works fine i am using 12.10 on my main machine and it is reasonably stable at the moment.

---

### Post by kuvanito on 2012-08-26
i got it....
instead of daily build i used daily alternate and it worked.
i am back testing quantal like there is no tomorrow :)

---

### Post by jerrylamos on 2012-08-26
> **nuttzo31 said:**
> I got this as well, there's no desktop because you have to install unity from one of the tty's.Once you install unity and restart it works fine i am using 12.10 on my main machine and it is reasonably stable at the moment.No desktop here as well with 8/25 Daily. I've got wireless WPA, even with desktop Quetzel Unity has problems connecting as it is, long standing bug written.  No Development interest.  Precise et. al. easily connect automatically.   

Only thing that works with 8/25 build is Ctrl-Alt-F1 command line.  I haven't had any luck using CLI to search for hidden network and set encryption keys et. all. to connect to download a desktop.
 
Daily Live is 628M must be over 100M missing. There's always tomorrow...

---

### Post by grahammechanical on 2012-08-26
> there's no desktop because you have to install unity from one of the tty's.

Ah, now I understand. Give the user an install CD that

a) does not install a desktop
b) does not explain how to install a desktop
c) does not give any means of installing a desktop
d) does not give any means of switching off the OS

And what version of Ubuntu is this? 0.0.0.1?

I am upset because at the same time as removing Unity 2D from an existing install they broke the desktop.

I choose to install Unity 2D specifically for those times when a Compiz update would break the desktop. I do not think it right to remove software that a user has chosen to install without first getting his agreement.

All this would not be so bad but it is proving impossible to re-install. What is happening now is telling that there needs to be a re-think on how things are done during the development process.

Regards.

---

### Post by twipley on 2012-08-26
> **grahammechanical said:**
> All this would not be so bad but it is proving impossible to re-install. What is happening now is telling that there needs to be a re-think on how things are done during the development process.
There needs to be a re-think (and more management) if I am to test alpha releases back again in the future, because as it is right now it will be a long time for me to install such releases back again -- and to report bugs I am stumbling upon in relation to it.

However, the issue probably is springing from a problem developers had not anticipated would emerge, so I am thinking it as "out of the norm."

---

### Post by twipley on 2012-08-26
> **twipley said:**
> There needs to be a re-think (and more management) if I am to test alpha releases back again in the future, because as it is right now it will be a long time for me to install such releases back again -- and to report bugs I am stumbling upon in relation to it.

However, the issue probably is springing from a problem developers had not anticipated would emerge, so I am thinking it as "out of the norm."

EDIT: this thread appears to be a viable solution to most of those issues: [http://ubuntuforums.org/showthread.php?t=2047301](http://ubuntuforums.org/showthread.php?t=2047301)

---

### Post by critin on 2012-08-26
> **jerrylamos said:**
> I tried yesterday with 
VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics ControlleR
using external VGA monitor, a 15" 1366x768 TV.

What a wild ride!  Pieces of windows scattered all over.  I fought for quite a while trying to get the cursor on whatever selection and gave up.  Trying to fight through drop down windows to connect to wireless WPA was hopeless.  Running Apport totally out of the question.

Tried updating the .iso today and no change, sure enough the daily build is still yesterday's.  

Jerry

That's what was happening to me on the day I decided my poor Dell just couldn't handle it anymore.  Maybe it was this bug and not poor Dell after all?  I'm running xubuntu just fine.  

I'll keep my eyes open and try again when someone says go.

Thanks for this info...

---

### Post by jerrylamos on 2012-08-26
> **grahammechanical said:**
> All this would not be so bad but it is proving impossible to re-install. Patience, Hortense.  I've been testing since Dapper Drake Beta, and yes I get upset when something that just worked doesn't any more (like install or startup disk creator or desktop or Nautilus or ..)  So I've got multiple  partitions with various levels and can usually get something running.  Install clobbered Grub2 a couple days ago rendering nothing bootable.  Super Grub2 CD to the rescue.  Worked this time.

Now I do get hot under the collar when a major feature is removed forever. So far after the dust settles I find a way around it, although frequently with a permanent "de-provement".

Tens, hundreds, thousands of people are throwing packages and changes into the pot it's amazing to me that it works.  Right now, it doesn't, awaiting fixes and missing packages.

---

### Post by ventrical on 2012-08-26
> **kuvanito said:**
> i got it....
instead of daily build i used daily alternate and it worked.
i am back testing quantal like there is no tomorrow :)

 I guess that is the key for now. There is always somthing ready to work out there. We can lead a horse to water but we can't make him drink it. ! :) lol

---

### Post by sammiev on 2012-08-26
I'm going to wait for alpha1 as QQ seems to be running very good here at this time. Much better than 12.04 so far and I have noticed many improvements. Finally product looks like a winner!

---

### Post by jerrylamos on 2012-08-27
quantal-desktop-i386.iso              27-Aug-2012 08:29  747M 
Hey!  Daily build just gained a lot of weight, up from 659M (as reported by ls -l)
Just for giggles I'll see if I get a working desktop of some sort.
zsync reports 3.9% complete so it'll take a while at my relatively cheap 1.5M download speed. 

p.s. A lot of Ubuntu reports M as 1000000 and in other places M is 1048576 and it is up to us to figure out which....

---

### Post by ventrical on 2012-08-27
> **jerrylamos said:**
> quantal-desktop-i386.iso              27-Aug-2012 08:29  747M 
Hey!  Daily build just gained a lot of weight, up from 659M (as reported by ls -l)
Just for giggles I'll see if I get a working desktop of some sort.
zsync reports 3.9% complete so it'll take a while at my relatively cheap 1.5M download speed. 

p.s. A lot of Ubuntu reports M as 1000000 and in other places M is 1048576 and it is up to us to figure out which....

Jerry,

Try the quantal-alternate-i386.iso.

Got that working really good.

---

### Post by jerrylamos on 2012-08-27
Daily Build desktop that actually functioned!  Installed and running.
Ctrl-Alt-F1 did get me a usable terminal screen.
Now the "Install Ubuntu" icon was flaky, appeared, disappeared, pieces displayed, finally long enough to start Ubiquity.
This is a 1366x769 VGA which Ubiquity treated as 800x600 everything worked.
Once rebooted set up hidden wireless WPA O.K. usual for this Atom setup v e r y long drop  down menu response but it did work.
Now I do use an xorg.conf and also a .xprofile like so:

#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"

so I'm up and running at chosen resolution.

Drop down menus typically appear blank, either black or grey, until moused over then a couple tries and the selections appear and work.

As is my choice installed a second desktop as well, LXDE.

Away we go for the moment....

---

### Post by jerrylamos on 2012-08-27
A couple curios.  I choose a jpg from Pictures as wallpaper, this time my wife coming up the beach from a triathlon.

Unity displays the wallpaper as 1366x768 and then overlays another copy of the wallpaper 800x600 on top left.  ?

Also note, Unity shows two copies of the log off, restrt, switch off menu drop down.  The left 800x600 one works, the right 1366x768 one doesn't.  ?

Not showstoppers.  I'll let the Unity buffs see if they have any problems worth reporting.
 
LXDE working normally. 

Jerry

---

