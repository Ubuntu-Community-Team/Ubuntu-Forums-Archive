---
title: "Quantal Quetzal no display with installer"
date: 2012-09-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Hydrohs on 2012-09-25
I'm trying to install Quantal to test it out but I get no display. I tried both Beta 1 and the most recent daily. The system has an Nvidia GT330M. Tried doing some Googling but didn't come across anything. Anyone else have the same issue or some suggestions?

---

### Post by overdrank on 2012-09-25
Moved to Ubuntu +1 (Quantal Quetzal)

---

### Post by sgage on 2012-09-25
> **Hydrohs said:**
> I'm trying to install Quantal to test it out but I get no display. I tried both Beta 1 and the most recent daily. The system has an Nvidia GT330M. Tried doing some Googling but didn't come across anything. Anyone else have the same issue or some suggestions?

What do you mean by "get no display"? Describe the scenario a bit more...

---

### Post by mc4man on 2012-09-25
You may want to try with different boot options
The first to try is to remove 'splash' (& while there I'd remove 'quiet' also)
This will give the normal live session and or installer vs. below

If that doesn't work then add the 'nomodeset' option
Depending on what you used to create the live usb/cd get to the options screen
(I think tab with unetbootin, with usb creator it's  - press any key when boot up starts, enter to set lang. Then use arrow/backspace keys to remove splash & quiet.

If nomodeset is needed then at the above options screen go F6 & enable.
(not sure about nomodeset in unetbootin

Alt means to remove  quiet splash (or nomodeset
Both unetbootin & usb-creator store the boot up options in editable files on a usb, just different places

To do, insert usb boot drive, open in nautilus

For unetbootin
The file is right there, syslinux.cfg - scr. 1
Open it up in a text editor & remove quiet splash as needed, I'd just remove all instances, - scr. 2 (removed 1st. instance, highlighted 2nd, ect.
save & then boot with

For usb-creator
A bit deeper, open syslinux/txt.cfg
Remove all instances of quiet splash, save, boot with - scr. 3

For nomodeset with above just add to line where quiet splash are before the --
(leave a space before & after

---

### Post by Hydrohs on 2012-09-25
> **sgage said:**
> What do you mean by "get no display"? Describe the scenario a bit more...

I mean I get no display, nothing displays on the screen at any point xD

Well, 'nothing' isn't completely accurate. I get black and white blocks on the lower half of the screen.

> **mc4man said:**
> You may want to try with different boot options
The first to try is to remove 'splash' (& while there I'd remove 'quiet' also)
This will give the normal live session and or installer vs. below

If that doesn't work then add the 'nomodeset' option
Depending on what you used to create the live usb/cd get to the options screen
(I think tab with unetbootin, with usb creator it's  - press any key when boot up starts, enter to set lang. Then use arrow/backspace keys to remove splash & quiet.

If nomodeset is needed then at the above options screen go F6 & enable.
(not sure about nomodeset in unetbootin

Alt means to remove  quiet splash (or nomodeset
Both unetbootin & usb-creator store the boot up options in editable files on a usb, just different places

To do, insert usb boot drive, open in nautilus

For unetbootin
The file is right there, syslinux.cfg - scr. 1
Open it up in a text editor & remove quiet splash as needed, I'd just remove all instances, - scr. 2 (removed 1st. instance, highlighted 2nd, ect.
save & then boot with

For usb-creator
A bit deeper, open syslinux/txt.cfg
Remove all instances of quiet splash, save, boot with - scr. 3

For nomodeset with above just add to line where quiet splash are before the --
(leave a space before & after

I'll give this a shot, but I think the issue is graphics drivers. I can hear the login chime once the live environment finishes loading, but there's still nothing displaying.

However I might be able to at least see errors this way.

EDIT: I took a picture of my screen to show what's going on. And I'd never tried before, but if I switch to one of the terminals with Ctrl+Alt+F* it appears just fine. Is there any way I can run the installer from the terminal?

---

### Post by cariboo on 2012-09-25
Your issue is a graphics driver, if you see the little man & keyboard when booting, press any key, then select your language, and once at the menu screen, press F6 and select nomodeset, then just start as you always do, you should be taken to the desktop.

---

### Post by Hydrohs on 2012-09-25
Yeah, I did some more searching after trying it on my desktop and experiencing the same issue and discovered this thread which describes pretty well the same issue: [http://ubuntuforums.org/showthread.php?p=12254331](http://ubuntuforums.org/showthread.php?p=12254331). As it sounds like there's a fair amount of issues right now I'll just stick with Precise until Quantal is released.

---

### Post by nm_geo on 2012-09-25
That screen display is close to the one I get if I do not set nomodeset before going into the plymouth (scroll dots).. I have a Thinkpad that has nVidia graphics and that is the present work around for me.  Mc4man examples and write-up should allow you to find a live session possibility.  After getting the install completed I am having no trouble with my nVidia graphic it is just getting there..

---

### Post by Hydrohs on 2012-09-25
Is this an issue that's only happening with Nvidia devices? Both my laptop and desktop use Nvidia cards but in the other thread it seemed like it was more widespread.

---

### Post by nm_geo on 2012-09-25
Most intel graphics are doing fine.  I am installing right now on the Thinkpad (nVidia) problems and a Samsung (Intel) no problems at all.

It really has not cause me that much strife and after getting to the live session and doing the install my Thinkpad does just fine.
In fact let's see I have done a least 3 installs on the Lubuntu desktop Amd64 Beta 2 version in the latest three hours. Of course the Thinkpad is really just for testing not a production machine.

---

### Post by cariboo on 2012-09-25
It seems to be Nvidia, that is the problem, more than AMD/ATI. mc4man posted work arounds that work, although it may be more than a casual tester may want to get involved in.

I should say that it is the nouveau driver, that is used by default with the Live CD, the closed source driver works with zero problems.

---

### Post by Hydrohs on 2012-09-25
> **cariboo907 said:**
> It seems to be Nvidia, that is the problem, more than AMD/ATI. mc4man posted work arounds that work, although it may be more than a casual tester may want to get involved in.

I should say that it is the nouveau driver, that is used by default with the Live CD, the closed source driver works with zero problems.

I use the proprietary driver anyway, I don't mind going through a few hurdles during the initial installation.

---

### Post by mc4man on 2012-09-25
In any event here is a current bug on I have for nvidia. The black & white 'art deco' is  what usually shows, sometimes it's a mosiac of backgrounds & other stuff in the video mem.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)
(there are 2 screens there that at least one should be familiar.

I used to use nomodeset which is ok for just installing but almost worthless in a live session.
I'd say most nvidia users affected by this will find removing the splash option to work quite well & produce an direct accelerated live session with nouveau

---

### Post by Hydrohs on 2012-09-25
Yup, removing the splash option worked perfectly. Going through the install now, I'll report back if I encounter any quirks with an installed system.

---

### Post by mc4man on 2012-09-25
> **Hydrohs said:**
> Yup, removing the splash option worked perfectly. Going through the install now, I'll report back if I encounter any quirks with an installed system.
Nothing related to removing splash will affect your install, any quirks will be par for the current course.

If they can't fix this shortly, (likely fixed in the 3.6*rc6 kernel though I don't see 12.10 using) I may file another bug requesting that splash be removed from the install images (if it can be, will have to try a re-master here & see.
Overall the plymouth splash experience has been a bust for many users, especially with nouveau. 
(and generally only shows for a few sec.'s for the boot splash, at least here with 8400 & 7800 nvidia

---

### Post by Hydrohs on 2012-09-25
> **mc4man said:**
> Overall the plymouth splash experience has been a bust for many users, especially with nouveau. 
(and generally only shows for a few sec.'s for the boot splash, at least here with 8400 & 7800 nvidia

Back when it was first introduced it worked flawlessly (for me) as long as I was running the Nouveau drivers. But as of either 11.04 or 11.10 it's done exactly as you described.

---

### Post by nm_geo on 2012-09-25
Mc4man you are absolutely correct removing splash works like a champ I have been using the nomodeset because really the low graphic did not bother me at all as I was testing the iso installs on Lubuntu (low resources) anyway.

Anyway, I also followed the removal of splash & quiet .. Work well to live with native graphics.

Just removed splash and it worked well also with proper graphics.

Guess I better zsync up a Ubuntu and Xubuntu iso and see those as well.

---

### Post by nm_geo on 2012-09-25
> **mc4man said:**
> Nothing related to removing splash will affect your install, any quirks will be par for the current course.

I<snip>  I may file another bug requesting that splash be removed from the install images (if it can be, will have to try a re-master here & see.
Overall the plymouth splash experience has been a bust for many users, especially with nouveau. 
(and generally only shows for a few sec.'s for the boot splash, at least here with 8400 & 7800 nvidia

I will certainly me too on that bug request. +1

---

### Post by mc4man on 2012-09-26
> **nm_geo said:**
> 
Just removed splash and it worked well also with proper graphics.
.

Yeah - only splash is in need of removal, suggested quiet in case there was/is any other issue, users may catch something.
(remove quiet here as I'd rather see something other than purple/black, ect..

---

