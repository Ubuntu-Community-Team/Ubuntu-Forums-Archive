---
title: "Ubuntu 9.10 NBR on Samsung n310"
date: 2009-11-04
forum: Ubuntu Moblin Remix
---

### Post by shaunmenzies on 2009-11-04
I bought a Samsung n310 in Europe which is identical to the Samsung Go except the European version only has a 4 cell instead of a 6 cell battery (which is most annoying actually). It's a great netbook, bar the battery life which is, IMHO, it's only drawback.

I have been booting Ubunto 9.10 Netbook Remix from a USB drive to put it through it's paces and i'm very impressed. So I now want to install it as my main OS with a second small partition for XP Home for those "just in case" moments.

My questions are:

1. Can I configure the n310 to dual boot Ubuntu and XP ? And if so could some kind person give me a link to a "how to" page ?

2. I cannot change the Brightness with the blue Funtion Key combo. I have read that a bios upgrade fixes the issue on the NC10. Unfortunately the latest BIOS on the Samsung site for the n310 is 04BA. Does anyone know how to fix the brightness function keys ? I also here NC10 scripts might help but is there a n310 equivalent ?

3. The blue function keys for Wireless ON/OFF and Screen ON/Off do not work either. I would very much like a fix for these too if possible as they both help save battery life.

That's about it.....I really do reccomend people move to Ubuntu Netbook Remix....it's just perfect for Netbooks.

All the best and thanks in advance for any help.

Shaun.

---

### Post by Karos on 2009-11-04
There is a similar problem on Samsung NC10 netbook. However with the newest bios update (11CA) I can control brightness level in Ubuntu 9.10 without any addition scripts. Didn't try UNB yet, however. Maybe you could try updating your bios, if there's an update available.

If that doesn't work there are still [these]("https://launchpad.net/~voria/+archive/ppa") packages for NC10 and might work for your Sammy as well.

---

### Post by shaunmenzies on 2009-11-04
Hi Karos, 

Thanks for your feedback. Unfortunately there is no 11CA bios for the n310, the latest is 04BA which i've installed.

I installed the packages for the NC10 that you recommended, mainly NC-10 scripts and NC10-backlight etc which fix the blue function key problems on the NC10 but were unable to notice any effect on the n310. HOWEVER...i'm currently booting Ubuntu from a USB drive and feel it is not taking persisting the newly installed packages between reboots so i can't actually confirm or not whether these packages fix my problem.

It looks like i'll have to go ahead and install Ubuntu NBR on the actual harddrive; which brings me to me next question.....can I dual boot Ubuntu NBR and Windows XP ? 

If so, can anyone reccomend a "how to" link ?

Many thanks, 
Shaun.

---

### Post by shaunmenzies on 2009-11-04
I've taken the plunge and am now installing Ubuntu NBR 9.10 on the n310 (after Windows XP Home installed). I've assigned 20gb for WinXp and the rest for Ubuntu. This should give me a GRUB at boot with both Ubuntu and WinXP boot options available.

I will repeat the installation of the NC10 packages as described earlier but would first like to back up the installed Ubuntu image onto the USB drive so i can return to it if anything goes wrong. 

I will keep this topic informed of my progress just in case anyone else has a n310 or Samsung GO out there who also wants to install Ubuntu.

Cheers, Shaun.

---

### Post by feicipet on 2009-11-04
Hi,

Since you have a n310 and your wireless is working, I would like to request a small favor.

I've installed Karmic on my N310 and wiped out Windows in the process. After installing, I found that my wireless didn't work (it didn't work on the live CD as well but I thought I could resolve that).

Now, no matter what I do, I still can't get Karmic to detect my wireless device. What I suspect is that, the wireless device was switched off when I last shutdown XP and when I rebooted in Ubuntu, it stayed off and I can't switch it on again.

So, if you could spare the time, could you just turn off the wifi in XP and restart using the live CD in Ubuntu? See if what I'm hypothesizing is correct? 

I've filed a forum post asking about the wireless issue here: [http://ubuntuforums.org/showthread.php?p=8239688#post8239688](http://ubuntuforums.org/showthread.php?p=8239688#post8239688)

Thanks,
Wong

---

### Post by shaunmenzies on 2009-11-04
I have Ubuntu booting well in Grub and have installed the NC-10 scripts. They appear to work in the command line in terminal but not via the blue function keys. I imagine I need to set up some sort of keybinding somewhere.....any ideas anyone ?

@feicipet
I would suggest booting to Bios and ensuring the wireless is set to "enabled" in the bios then re-installing Ubuntu. It should pick it up this time. Let me know if this works for you. If not i'll try and help once i've got my install working and imaged on a backup device.

Cheers, Shaun.

---

### Post by shaunmenzies on 2009-11-04
Argghhhhh.....sorry.

Just cannot get these bloody function keys working. The commands work in the terminal but not using the function keys. 

Keys that dont work

Fn+F9 = Toggle Wireless
Fn+F5 = Toggle Screen Backlight
Fn+Up = Increase Brightness
Fn+Down = Decrease Brightness

Keys that do work
Fn+F6 = Toggle Mute Sound
Fn+F10 = Toggle Touc Pad
Fn+Left =  Decrease Volumn
Fn+Right = Increase Volumn

I've installed CompizConfig Settings Manager and ensured the Commands Plugin is activated. Indeed I can see the command bindings to the correct commands too (e.g. Command Line 2 bound to **sudo nc10 wifi**, which is the command that works in the terminal). I can even edit the Key Binding to "Super + F9" and that toggles the Wifi perfectly.

So the problem appears to be that the Fn + F9 combo is just not talking to the OS.

I wonder how people with far less IT knowledge than me are struggling through this. Oh well....

---

### Post by feicipet on 2009-11-04
> **shaunmenzies said:**
> 
@feicipet
I would suggest booting to Bios and ensuring the wireless is set to "enabled" in the bios then re-installing Ubuntu. It should pick it up this time. Let me know if this works for you. If not i'll try and help once i've got my install working and imaged on a backup device.

Cheers, Shaun.

Done that, unfortunately. Only hope I have now is to upgrade the BIOS (I have 03B) and well, upgrading the BIOS when you don't have Windows is a pain in itself :( I only hope the Samsung site was kidding when it listed "XP/Windows 7" as the platform to run the BIOS update. If it doesn't run in FreeDOS, I'm well and truly screwed.

Well, hope things are better for you. Do try out what I requested if you have the time.

Thanks,
Wong

---

### Post by feicipet on 2009-11-04
> **feicipet said:**
> Done that, unfortunately. Only hope I have now is to upgrade the BIOS (I have 03B) and well, upgrading the BIOS when you don't have Windows is a pain in itself :( I only hope the Samsung site was kidding when it listed "XP/Windows 7" as the platform to run the BIOS update. If it doesn't run in FreeDOS, I'm well and truly screwed.

Well, hope things are better for you. Do try out what I requested if you have the time.

Thanks,
Wong

Gah. The BIOS update does seem like it was build to run on Windows only. I am *so* screwed.

---

### Post by shaunmenzies on 2009-11-04
You should have received a Samsung recover CD which has XP on it. Install XP then upgrade the bios and do a dual boot install of Ubuntu (you'll need XP for any future bios upgrades so 10GB partition should suffice).

Anyone have any info on getting the brightness function keys working ? It surely can't be hard, I mean its a standard netbook feature after all.

Cheers, Shaun.

---

### Post by feicipet on 2009-11-04
> **shaunmenzies said:**
> You should have received a Samsung recover CD which has XP on it. Install XP then upgrade the bios and do a dual boot install of Ubuntu (you'll need XP for any future bios upgrades so 10GB partition should suffice).

Anyone have any info on getting the brightness function keys working ? It surely can't be hard, I mean its a standard netbook feature after all.

Cheers, Shaun.

Shaun, I took a brief look at the CD. It was labelled "System Software Media" and I did not have any other CDs. Unless XP is inside one of the many sub-folders in it, I don't think I have one. Can I check if yours sound/look the same?

Thanks,
Wong

---

### Post by feicipet on 2009-11-08
Ok. Finally I found out what the friggin' problem was.

My version of the N310 did not have Atheros wifi chip after all. What it had was a Realtek 8192, which needed ndiswrapper to enable it using the Windows drivers. 

Every single Samsung product literature and review site listed it as having the Atheros and somehow, someone forgot to mention that in certain countries, it was replaced with another chip. I did see the Realtek in my lspci output but I thought it was for the Ethernet interface.

Blah. This has wasted enough of my time. Now to start **using** my netbook instead of fussing over it.

---

### Post by shaunmenzies on 2009-11-09
Glad you got it sorted mate. Sorry i couldn't be more helpfull, still having problems with clitchy and erratic touchpad and function keys. I managed to map the Windows Key + UP/DOWN to the the Brightness Control applet but still can't find solutions for other function keys. What we need is a complete Samsung n310 solution for ALL the function keys by way of scripts akin to the Nc-10 Scripts or by way of some kind of support from Samsung.....I doubt the latter will hapen though. They make great netbooks but they have no insterest in operating system support or indeed releasing a desperatelely needed 6-cell battery for the n310 in Europe. 

Thats my rant over with.....back to wandering in the poppy fields.

---

### Post by feicipet on 2009-11-09
> **shaunmenzies said:**
> Glad you got it sorted mate. Sorry i couldn't be more helpfull, still having problems with clitchy and erratic touchpad and function keys. I managed to map the Windows Key + UP/DOWN to the the Brightness Control applet but still can't find solutions for other function keys. What we need is a complete Samsung n310 solution for ALL the function keys by way of scripts akin to the Nc-10 Scripts or by way of some kind of support from Samsung.....I doubt the latter will hapen though. They make great netbooks but they have no insterest in operating system support or indeed releasing a desperatelely needed 6-cell battery for the n310 in Europe. 

Thats my rant over with.....back to wandering in the poppy fields.

So how did ya manage to set the brightness control anyway? I guess that would be my next target :)

Thanks!
Wong

---

### Post by shaunmenzies on 2009-11-10
You'll need to install CompizConfig Settings Manager from the Ubunto Software Center (if it's not already installed) the and open it (from System) and activate the "Opacity, Brightness and Saturation" applet in Accessibility. Open that and configure your preferred key combo for the brightness increase/decrease in the Brightness tab.

Last night I installed Kernel 2.6.32 to see if the Samsung Fn key fix contained within works or not....alas it didn't :-(

Very frustrating these Fn key issues.....yet I know there must be a solution as it's surely only a matter of forcing the Fn Key to produce key-released events.

---

### Post by shaunmenzies on 2009-11-10
After installing the 2.6.32 kernal and following the very informative instructions detailed here: [http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys](http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys) 

I found that the following keys on the Samsung have scan codes but are not configured:
 

Fn+UP = 0x88 (e008)
Fn+Down = 0x89 (e009)
Fn+F2 = 0x83 (e003)
Fn+F4 = 0x82 (e002)
Fn+F5 = 0x84 (e004)
Fn+F7 = 0xb1 (e031)
Fn+F8 = 0xb3 (e033)
Fn+F9 = 0x86 (e006)


This is also noted in the following launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399911?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399911?comments=all)


So, it appears as if the key_release patch is indeed in the kernel, which means the next step should be to assign the above scan codes to actual keys and functions (such as adjust brightness etc).


Cheers, Shaun.

---

### Post by shaunmenzies on 2009-11-10
Update:

After installing 2.6.32 kernal I added the following line to /etc/rc.local
echo 130,131,132,134,136,137,177,179,247,249 > /sys/devices/platform/i8042/serio0/force_release

This forces the missing Fn key scancodes, mentioned above, to produce a key release event.

Then I edited /lib/udev/rules.d/95-keymap.rules and after the 'LABEL="keyboard_vendorcheck"'section I added |*N310*| toe the Samsung vendor line that already contained |*NC10*| and |*NC20*|

Then installed the NC-10 scripts as detailed here: [http://www.voria.org/forum/viewtopic.php?t=67](http://www.voria.org/forum/viewtopic.php?t=67)

Then installed CompizConfig and enabled the Commands applet

Then mapped the Fn+keys to the NC10 sctript commands

And hey presto...
ALL MY FUNCTION KEYS ARE NOW WORKING!!!!


What a palarva! So the next kernal release should indeed fix the Samsung keyboard function key issues.


Cheers. Shaun.

---

### Post by shaunmenzies on 2009-11-10
I'm now going to try and get all the Fn keys working on current 9.10 Ubuntu release (i.e. without doing a Kernel Upgrade), if it works i'll attach a simple "How To".

---

### Post by shaunmenzies on 2009-11-10
Okay, you have to install the latest Kernel else the lack of key_release events just causes chaos when trying to use the Fn keys. Shame this small patch can't be released to the community prior to official release of 2.6.32 Kernel which I believe will be April 2010.


Untill then Samsung users will have to suffer.


_FINAL INSTRUCTIONS_



Install Ubuntu 9.10 Netbook Remix
  Ensure all packages are up to date via Update Manager.
   
Upgrade the Kernel to 2.6.32

Add the following line to /etc/rc.local
echo 130,131,132,134,136,137,177,179,247,249 > /sys/devices/platform/i8042/serio0/force_release

  Open the file **/etc/default/acpi-support** in your favourite editor and change the line
  ENABLE_LAPTOP_MODE=false (change to true)
   
  Follow instructions to install the **nc10-scripts** and **nc10-backlight** from here: [http://www.voria.org/forum/viewtopic.php?f=3&t=296](http://www.voria.org/forum/viewtopic.php?f=3&t=296)
   
  Use Synaptic Package Manager to install  compizconfig-settings-manager
   
  Open up CompizConfig Settings Manager and ensure the Commands applet is checked. Open the Commands applet and you should see 5 commands bound to command line 0 to 4. These are the NC10 script commands.
   
  Edit /lib/udev/rules.d/95-keymap.rules and after the 'LABEL="keyboard_vendorcheck"' section add |*N310*| to the Samsung vendor line after |*NC10*|*NC20*|
   
  Reboot yer Netbook

---

### Post by shaunmenzies on 2009-11-11
I am now looking at re-compiling 2.6.31 kernel and then applying the force_release patch. This should ensure I maintain a Ubuntu supported kernel whilst also fixing all the function key problems.

It should be noted that the problems are not due to Ubuntu or indeed linux; they are due to some hardware manufacturers not ensuring their keyboards send the necessary key release event when the key is no longer pressed. Samsung keyboards appear to be largely affected by this.

Cheers, Shaun.

---

### Post by shaunmenzies on 2009-11-12
Downloading the latest source for Ubuntu Kernel 2.6.31 (-14 when I did it) and applying the force_release patch by Sergy then rebuilding the Kernel WORKS!!!!!

Thus concluding this topic thread and hopefully helping any Samsung Netbook owner out there whose Fn buttons dont work.

Remember though, this will be completely fixed in the next Ubuntu release.

Cheers, Shaun.

---

### Post by Red_48 on 2009-11-13
Would 9.10 NBR perform well from a SDHC? If so any particular class/speed?

What changes might I have to make to get the N310 to boot from the SDHC?

Thanks

---

### Post by shaunmenzies on 2009-11-19
I have no idea to be honest. If you can boot from the SDHC then you'll certainly be able to boot Ubuntu NBR 9.10. You might have to customise it a bit to your liking before burning the final image to the card though. 

As for timings, I suggest you give it a go and report back in this thread. Would certainly be interesting to hear how you get on.

Cheers.

---

### Post by bonesinc on 2009-11-21
First of all, I'm a new member. The primary reason for registering to this forum is this thread.

> **shaunmenzies said:**
> Downloading the latest source for Ubuntu Kernel 2.6.31 (-14 when I did it) and applying the force_release patch by Sergy then rebuilding the Kernel WORKS!!!!!

Thus concluding this topic thread and hopefully helping any Samsung Netbook owner out there whose Fn buttons dont work.

Remember though, this will be completely fixed in the next Ubuntu release.

Cheers, Shaun.

Thank you for your very useful input Shaun.

I've tried to patch and compile that kernel myself but ran into a few problems, which I won't explain here. Instead I'm running the Ubuntu Kernel 2.6.32-rc7. Which does work, as you stated earlier, but (besides lack of update support) I'm experiencing some sort of video bug. The screen flashes every now and then, which is very irritating.
So, not that useful for now. But...that's why it's a rc-version.

To make a long story short: Is there any way that you could (and would) share me your own patched and compiled, working kernel (2.6.31-x)? It would be much appreciated!

It's not that I'm lazy but I'd like to start using my N310, instead of trying to get it working the way I want it to. Already spend the larger part of the last three days on it.

Thank you in advance,
Matthieu

---

### Post by shaunmenzies on 2009-11-23
Hi Matthieu,

I found that there were few in this community that were willing to offer advice when I first tried to solve the n310 problems, so I concluded there were not many Samsung Ubuntu users - hence my posts. Glad you found them usefull ;)

Compiling the Kernel on the n310 took quite a few hours so I'm now setting up VMWare on my windows work desktop so I can create a Ubuntu virtual machine and configure it purely for compiling my own custom n310 UBuntu NBR. 

The first task will be to recompile the latest 2.6.31 kernel and apply the force_release patch. Once this is done I will upload the ISO image onto my server and send you a link.

The next task will be to customise the Ubuntu NBR Install to include a few usefull features for the n310, such as a better touch pad configurator etc. I'll keep you posted on updates.

Hope you don't mind waiting a day or two though....

All the best, 

Shaun.

---

### Post by bonesinc on 2009-11-23
Shaun, by all means: Take your time.

I know my way around Ubuntu/Linux, the way someone knows how to order a loaf of bread (or a beer) in a foreign country.
I can get around but recompiling kernels and such is a little bit over my head.

So, I'm very grateful and until you are finished I'll just use XP (brrr). I don't mind waiting for something good.

Here's 5 stars to motivate you: :KS:KS:KS:KS:KS

Cheers,
Matthieu

P.S.
If you need me to do something for you to help, just drop me a pm.

---

### Post by pjhaas on 2009-11-23
I own a Samsung N140 netbook and am a first time Ubuntu user (erased the disk, got rid of XP and installed 9.10 a week ago). Not being able to adjust the screen brightness is my only problem. Now, I've seen fixes for other Samsung netbooks, but not the N140. I don't mind waiting a bit for a fix.

> Remember though, this will be completely fixed in the next Ubuntu release.

Cheers, Shaun.

This would be great, but what Ubuntu release are we talking about? An update of 9.10 or the next version? How many months do I have to wait for a fix? Not being able to adjust the screen brightness is especially annoying on battery power when the screen is too dim in the sun light.

And isn't it strange I cannot adjust the screen brightness in system preferences? Why rely solely on the Fn-keys?

Thank you,

Peter Jan

---

### Post by shaunmenzies on 2009-11-24
@Mathius
Thanks for the motivational stars ;-)

@Peter Jan
> I own a Samsung N140 netbook and am a first time Ubuntu user (erased the disk, got rid of XP and installed 9.10 a week ago). Not being able to adjust the screen brightness is my only problem. Now, I've seen fixes for other Samsung netbooks, but not the N140. I don't mind waiting a bit for a fix.

I would keep a small Windows XP partition on the netbook for Samsung BIOS upgrades as Samsung have not yet released a bios upgrade deployable from Ubuntu.

Most of the Samsung netbooks are similar and, as such, suffer from the dodgy keyboards that don't send a release key event when you let go of a pressed key. The next Ubuntu release is labeled 10.4 which means it's scheduled for release in April 2010 (hence the 10.4). If you dont want to go through the pain of compiling a patched kernel (and it is a pain because the Ubuntu doc on compiling the kernel is not clear or indeed consise) then I would suggest you also download and install the ISO image i'm currently building (should be ready in a day or two).

For any other Samsung users who happen to wander into this topic....the ISO image i'm building will consist of Ubuntu 9.10 Netbook Remix patched with the force_release kernel fix and configured to use NC scripts - i.e. all your function keys should work out of the box.

Please wait patiently whilst I build and test this ISO image.....

Thanks, Shaun.

---

### Post by shaunmenzies on 2009-11-26
This is taking longer than I would like so if you're bored or want to attempt it yourself, here is a very good document on building the kernel:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

You should apply the force release patch just before the "git commit".

Once the kernel has been patched and rebuilt, and installed, it is simply a matter of doing the following: 

1. Add the following line to /etc/rc.local
echo 130,131,132,134,136,137,177,179,247,249 > /sys/devices/platform/i8042/serio0/force_release

2. Open the file **/etc/default/acpi-support** in your favourite editor and change the line
  ENABLE_LAPTOP_MODE=false (change to true)
   
  3.Follow instructions to install the **nc10-scripts** and **nc10-backlight** from here: [http://www.voria.org/forum/viewtopic.php?f=3&t=296](http://www.voria.org/forum/viewtopic.php?f=3&t=296)
   
4. Use Synaptic Package Manager to install  compizconfig-settings-manager
   
5. Open up CompizConfig Settings Manager and ensure the Commands applet is checked. Open the Commands applet and you should see 5 commands bound to command line 0 to 4. These are the NC10 script commands.
   
6. Edit /lib/udev/rules.d/95-keymap.rules and after the 'LABEL="keyboard_vendorcheck"' section add |*N310*| to the Samsung vendor line after |*NC10*|*NC20*|


PS: It's ironic that one has to go away from Ubuntu website in order to find decent documentation on Karmic.

---

### Post by johnbrod on 2009-11-27
> **shaunmenzies said:**
> For any other Samsung users who happen to wander into this topic....the ISO image i'm building will consist of Ubuntu 9.10 Netbook Remix patched with the force_release kernel fix and configured to use NC scripts - i.e. all your function keys should work out of the box.

Please wait patiently whilst I build and test this ISO image.....


Hi Shaun, this thread and your input is very helpful. I'm exactly one of those wandering samsung users on an N130. I've got the wireless up and running but not the Fn keys so will check back next week.
much appreciated
John

---

### Post by yannickroy on 2009-11-30
Hello. I am a new N310 owner and I have followed all the instructions above for getting my function keys working. Thanks for posting the info , that's a life saver - especially for a linux newb.

Everything now works as it should except using the brightness controls crashes the system.

If I adjust the brightness up or down, I get the same result : pressing the key combo once causes the brightness to either adjust all the way down or all the way up and then the on-screen brightness indicator will flash for 2-3 minutes as if you were pressing the key combination about 200 times.

after this the system is unusable and must be rebooted.

If you boot up and avoid changing the brightness, the system is rock solid but as soon as you change the brightness, it is toast.

I have not observed this behavior with any other Fn+ key combo, only the brightness is acting up.

I have kernel 2.6.32 and followed all of the latest instructions from Shaun.

Does anyone have any suggestions on how I can fix this? I am hoping to avoid the complete rebuild scenario.

thanks

---

### Post by yannickroy on 2009-11-30
Turns out I haven't followed all instructions as I did not rebuild the kernel with the force_release patch. 

So I'll give the kernel rebuild approach a go and see how that goes.

---

### Post by ADMoral on 2009-11-30
Hi, I'm a new Samsung GO owner myself and I have to say I'm very thankful I decided to Google a possible HOW TO for my specific machine. I'm a complete Linux Newb so I'm very intrigued by this patch. Thank you so much for all the effort!

Just to get something clear, the only difference between the GO and the European N310 is the battery size, right?


Thanks again for your help. Cheers!

---

### Post by bonesinc on 2009-12-01
> **ADMoral said:**
> Just to get something clear, the only difference between the GO and the European N310 is the battery size, right?

Yes, the only difference seems to be the battery size.

Stupid Samsung. I would have loved a bigger battery for my N310. :???:

Matthieu

---

### Post by pjhaas on 2009-12-03
> **shaunmenzies said:**
> 
@Peter Jan
I would keep a small Windows XP partition on the netbook for Samsung BIOS upgrades as Samsung have not yet released a bios upgrade deployable from Ubuntu.

Oops. Too late. I already did a clean install with Ubuntu 9.10. Does this mean I will never be able to update the BIOS on my Samsung N140? (unless I buy a new Windows copy) It seems unlikely that Samsung will publish a BIOS-updater for Ubuntu..

It's not clear to me whether running the 'old' BIOS has anything to do with the proper functioning of the Fn-keys. Will everything be okay in april 2010 when 9.10.4 is out? Or do I still need to update the BIOS? Sorry for these newbie questions. I've been using OS X since 2001. Decided to jump into the Linux pool head first.

---

### Post by pjsmetana on 2009-12-03
> **shaunmenzies said:**
> ...booting Ubuntu 9.10 Netbook Remix from a USB drive...
My questions are:

1. Can I configure the n310 to dual boot Ubuntu and XP ? ...

2. I cannot change the Brightness with the blue Funtion Key combo.... Does anyone know how to fix the brightness function keys ?...

3. The blue function keys for Wireless ON/OFF and Screen ON/Off do not work...
...

1. Yes, when you install it from your USB stick, it will ask you if you want to then guide you through the process. Very Very simple. I dual boot UNR and XP.

2. Should be "fn" plus one of the F keys somewhere on the right 1/2 of the KB.

3. They will work after full install. I had the same issue with my HP Mini 110-1030nr till I did the full install.

---

### Post by bonesinc on 2009-12-03
> **pjsmetana said:**
> 1. Yes, when you install it from your USB stick, it will ask you if you want to then guide you through the process. Very Very simple. I dual boot UNR and XP.

2. Should be "fn" plus one of the F keys somewhere on the right 1/2 of the KB.

3. They will work after full install. I had the same issue with my HP Mini 110-1030nr till I did the full install.

After a full install on hd the fn keys for screen on/of and wireless on/off DO work.
However, the fn keys for e.g. adjusting the brightness DO NOT work correctly.
The OS doesn't know when you let go of the fn brightness key, as a result the OS keeps trying to increase or decrease the brightness. Only a reboot can get you out of that.

If I remember correctly there was a firmware update for the NC10 which resolved this but there is none for the N310.

So YES, number 3 is correct.
Number 2 sadly doesn't work.
That's why we need a patched kernel.

Cheers,
Matthieu

---

### Post by shaunmenzies on 2009-12-07
KERNEL REBUILD
I'm still having problems setting up a kernel compiling system on my desktop which is quite annoying to be honest. Its not so much the lack of ability but rather the lack of decent documentation. I could of course compile on the netbook itself but it is very slow and I don't really want to clutter it with all the necessary compiler tools.

Given the stage i'm at and impending christmas and my 8yr old's needs I would, at this time, suggest people download the kernel source and recompile with the force_release_patch on their netbooks. The end result WILL fix your brightness control issues, somewhat essential if you wish to conserve battery life whilst away from wall sockets.


SAMSUNG BIOS UPDATES
I very much doubt Samsung will make BIOS upgrades available for Linux. They haven't even made the NC10 bios upgrade which fixes the force release events available for other Samsung machines yet so I imagine the cost of maintaining them, when set against their 'perceived' linux install base, is considered prohibitive. Silly really but thats the reality of corporates these days.

So I strongly suggest everyone installs a miminal Windows XP partition on their Samsungs.


I'll post back when I have some news but for now please fo try and recompile the kernel yourselves, it isn't that hard....I had never done it before buying the Samsung so have a crack at it!

Cheers, Shaun.

---

### Post by bonesinc on 2009-12-07
Thank you, Shaun.

I completely understand what you're saying.

Funny thing, I had also problems setting up a good kernel compiling system. I got kernels with over 200 MB in file size and such. But I'll give it another go.

I wish I knew which compiling settings would be optimal for a kernel for a N310...

Well, I'm going to gather documents and try compiling the kernel once more.

If I'm able to pull it of, I'll share it with you all. But it's a **big** **IF**!

Matthieu

---

### Post by shaunmenzies on 2009-12-08
@Matthieu

I've had to restart from scratch - using VMWare, I installed ISO image of NBR 9.10 and then ran an update to get the .16 kernel version. I'm now going through the following processes:

[http://mmlinux.wordpress.com/2009/07/30/how-to-compile-kernel-in-karmic/](http://mmlinux.wordpress.com/2009/07/30/how-to-compile-kernel-in-karmic/)
 
and 

[http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)

Trouble is, I have had to restart from scratch a number of times already due to Ubuntu changes in Kernel compilation procedures and, well, scant documentation.

Oh well, tis the loife of an IT bloke. 

I'll keep you posted....and if you beat me then fair play to you ;-)

---

### Post by shaunmenzies on 2009-12-09
And again the kernel failed to build for many reasons....I managed to get all the way to making the packages but then hit an error that I couldn't solve.

I'm giving up on this now, I think 6 attempts to cross-compile a kernel is enough really. I'll wait till the people that make Ubuntu decide to provide Ubuntu users with decent documentation on the issue.

I can understand now why so many people still stay with Windows even though Ubuntu is better. Samsung users should stay with Windows if they want their keyboards to function as intended. They can try Ubuntu next April if they like, when the force_release patch should be in the kernel, but I imagine by then you'll have so much stuff on your netbook you probably wont make the switch.

A lost opportunity for Ubuntu IMHO. Oh well....

---

### Post by pjhaas on 2009-12-09
> **shaunmenzies said:**
> Samsung users should stay with Windows if they want their keyboards to function as intended. They can try Ubuntu next April if they like, when the force_release patch should be in the kernel, but I imagine by then you'll have so much stuff on your netbook you probably wont make the switch.

A lost opportunity for Ubuntu IMHO. Oh well....

Thanks for the trouble Shaun. I agree it will be a lost opportunity regarding some Samsung owners. I've already deleted XP in favor of Ubuntu 9.10 so I'll suck it up until april 30 when 10.4 will be released. My netbook isn't my prime machine, otherwise I would have bought Win 7 and forget about Ubuntu.  Almost 5 months to go...

By the way. My only problem is the screen brightness on battery power. I'm not interested in dimming the screen, I actually want it on 100%, even on battery power. Forget about the Fn-keys, is there a way to set the screen brightness to maximum on battery power? I have a Samsung N140 and run Ubuntu 9.10.

---

### Post by shaunmenzies on 2009-12-10
Have you tried rebooting and then pressing F2 whilst it boots to get into the bios config ? You should set the brightness control to 'User Controlled' instead of 'Automatic'.

Also, take a look at the power manager app in System, there should be an option to diasable screen dimming when under battery load.

Let me know how you get on.

I posted an open question to ubuntu for a doc on cross compiling ubuntu as none of the existing docs are up to date. Alas no susbtantial resplies as yet. If there's one area that Ubuntu fails its got to be Documentation. The official stance is to palm it off to the community.....well that will never work :(.

Oh well....life goes on.

---

### Post by pjhaas on 2009-12-10
Ow, I feel so silly. I booted into the BIOS and changed the setting to 'user controlled'. That did the trick. I'm a happy camper. At least I can use my Samsung in bright sunlight. Thanks!

By the way:
In the power manager app I can't find an option to disable screen dimming, just an option to "reduce backlight brightness". When I un-tick this option nothing happens.

---

### Post by shaunmenzies on 2009-12-10
Yeah, its not that well explained byt dimming and backlight brightness are two different things...I don't know why but they are. As long as it's working the way you want it to then thats great. 

If you need any more help then let me know....within reason of course ;-)

---

### Post by voria on 2010-01-11
Hi, I'm the mantainer of the 'Linux On My Samsung' project, located at [http://www.voria.org/forum](http://www.voria.org/forum).

Because I'm already building a kernel with the FN keys release patch applied for the Samsung N140, I can easily add patches for other models too.
All I need is someone for testing it, since I have a NC10.
If anyone is interested, the patched kernel (and the patched udev, needed to get the FN keys correctly mapped) are available [on my experimental repository]("https://launchpad.net/~voria/+archive/archive/") (well, they will be in a few hours).

---

### Post by bonesinc on 2010-01-11
That sounds great!

I'm willing to test it on my N310. Just tell me what I should do to help you.

Cheers,
Matthieu

---

### Post by voria on 2010-01-11
The patched kernel for Samsung N310 is being built right now, it will be available in a few hours on my experimental repository (linked in the previous post).
You'll have to install it, along with the fixed udev packages (also available on the repository).

Please report back the results here:
[http://www.voria.org/forum/viewtopic.php?f=3&t=358](http://www.voria.org/forum/viewtopic.php?f=3&t=358)
so I can keep track of them easier.

Thank you. ;)

---

### Post by endless on 2010-01-12
I am willing to test this as well on my new Samsung N310 Go!

---

### Post by monxster on 2010-01-12
Great news.  I am willing to test on my N140.  

@Voria:  In the Samsung N140 build will you be applying the patches mentioned in this wiki: [http://wiki.archlinux.org/index.php/Samsung_N140](http://wiki.archlinux.org/index.php/Samsung_N140) to avoid hard drive freezing problems and screen brightness or freeze issues some have experienced? 

I am happy to test any time if you are willing to guide me a bit in what I must do to get it working if it all goes wrong.  ;)

Best,
Monxster

---

### Post by voria on 2010-01-13
The current kernel build available [on the repository]("https://launchpad.net/~voria/+archive/archive/") just fixes the FN keys release problem for the Samsung N140.
I'm uploading right now a new kernel containing the patch you pointed, it will be available in a few hours.

If any problem while testing the packages (I hope not ;)), just step by the 'Linux On My Samsung' forum ([link]("http://www.voria.org/forum/")), I will be glad to help you.

---

### Post by helliewm on 2010-01-13
Thanks for this Voria just talking about you in another thread! 

[http://ubuntuforums.org/showthread.php?t=1321340&page=4]("http://ubuntuforums.org/showthread.php?t=1321340&page=4")

I have an N130 and am happy to test any scripts for you.

Helen

---

### Post by monxster on 2010-01-13
@Voria:

I have just registered on your site which looks to be very informative and as mentioned will be happy to test any scripts and builds for you on my netbook and provide any feedback necessary to help improve the support for the N140 and other similar models. 

I will wait for you to let me know when I can get the kernel with the patches I mentioned and I will proceed to load and test for you.  

Please note though that I am away on business from today until Friday so will not be able to post any concrete results until Monday 18th as I will not have time to experiment very much before the weekend.

Best, 
Monxster

---

### Post by helliewm on 2010-01-13
@voria

Just joined your Linux on my Samsung forum. Same user name as here: helliewm as on the Ubuntu forums. See my previous post I have an N130 and am happy to test for you.

Helen

---

### Post by voria on 2010-01-13
> **monxster said:**
> 
I will wait for you to let me know when I can get the kernel with the patches I mentioned and I will proceed to load and test for you.
The kernel is already available on [the experimental repository]("https://launchpad.net/~voria/+archive/archive/"). Changelog:
```
linux (2.6.31-17.55~ppa3~nc10~karmic) karmic; urgency=low
  ...
  * Fix FN keys release on Samsung N140.
  * Fix FN keys release on Samsung N310.
  * Apply 'libata-ata_piix-clear-spurious-IRQ.patch' to fix the
    SATA freezing problem on Samsung N130/N140.
```
You can install it along with the needed udev packages by temporary adding the repository to your sources.list (then remove it when done) and then updating your system. The repository contains other stuff too, you just need to install the packages related to the kernel and udev.

> **helliewm said:**
> 
See my previous post I have an N130 and am happy to test for you.
Is the N130 affected by the same FN keys release problem as the other models?

---

### Post by helliewm on 2010-01-13
@voria. 

Yes it is affected plus I have the brightness issue too. I believe the N130 is almost identical to the N140. N140 has little extras like better speakers and battery life.

There also seems to be a minor graphics issue with compiz, sometimes the system freezes. I have not investigated this yet. 

Wifi was my biggest pain. I am more than happy to test scripts etc for you. I have used Ubuntu 100% of the time(no dual booting  :D) for over 3 years so am reasonable confident.

Helen

EDit: Installed your experimental ppa. Still same problem with FN keys and brightness. The freezing seems to have improved I wonder if its related to the SATA issue?

---

### Post by voria on 2010-01-13
> **helliewm said:**
> 
Yes it is affected plus I have the brightness issue too. I believe the N130 is almost identical to the N140. N140 has little extras like better speakers and battery life.
...
Installed your experimental ppa. Still same problem with FN keys and brightness.

I'm uploading a new kernel on the repository containing the FN keys release fix for the N130 too. It will be available in a few hours. Here is the changelog:
```

linux (2.6.31-17.55~ppa4~nc10~karmic) karmic; urgency=low
  ...
  * Fix FN keys release on Samsung N130.
  * Fix FN keys release on Samsung N140.
  * Fix FN keys release on Samsung N310.
  * Apply 'libata-ata_piix-clear-spurious-IRQ.patch' to fix the
    SATA freezing problem on Samsung N130/N140.

```
You'll probably need to install the 'nc10-backlight' package too, to enable the backlight control.

> **helliewm said:**
> 
Wifi was my biggest pain.
Are you using the 'n140-wireless' package from the repository? Any problem with it? I'm waiting for more reports, if it's ok I'll move it to the official 'Linux On My Samsung' repository.

> **helliewm said:**
> The freezing seems to have improved I wonder if its related to the SATA issue?
Probably.
Anyway, what do you mean when you say it has improved? The freezing happens yet or the problem is completely solved?

---

### Post by helliewm on 2010-01-14
@voria

Re Wifi your package worked beautifully. No problems.

The freezing did not happen so often yesterday evening, only once. However it has already happened as I booted up this morning.

Hope this helps.

Helen

---

### Post by bonesinc on 2010-02-02
It's been a long time...

Unfortunately I haven't been able to try the new kernel due to time constraints but I did notice there is a new firmware for the Samsung N310.

However I'm having a problem running the bios update application.
It runs on XP or Win7. I never deleted the XP partition (I did shrink it though) so I'm able to run the bios update 06BA from Samsung on my N310.

Whenever I try to run the Win_N310_06BA.exe Windows tells me that it is not a valid Win32 application (it IS a .exe file).

Did anyone of you guys manage to update their N310 bios?
Does anyone know if this update does anything useful for our fn keys in Ubuntu?

Cheers,
Matthieu

Edit UPDATE:
Just today I found out that Samsung updated the firmware update utility.
It's working now. Make sure your battery has at least 30% left or else the program will not run (no matter if you have your netbook attached to AC power).
A first look in the bios doesn't show anything new. 
Right now it says that the bios version is 05BA and the micom version is 06BA (don't know what micom is).

---

### Post by MiisTran2010 on 2010-02-04
That's a very interesting topic.
But this field is still new to me. 
It will be grateful if you give me some
more information about it. 
Thanks in advance.:KS

---

### Post by bonesinc on 2010-02-06
I'm happy to say that the combination of the new bios firmware and the latest standard, unmodified kernel (2.6.31-19) WORKS!!!!

Just install the needed CompizConfig Settings Manager and the Samsung scripts (howto: [http://www.voria.org/forum/viewtopic.php?f=3&t=296](http://www.voria.org/forum/viewtopic.php?f=3&t=296)).

I'm so happy!

Matthieu

---

### Post by trixmoto on 2010-08-05
> **feicipet said:**
> My version of the N310 did not have Atheros wifi chip after all. What it had was a Realtek 8192, which needed ndiswrapper to enable it using the Windows drivers.

I also have the N310 with Realtek 8192 - can you be more specific about how you got this working please?

---

### Post by pedrohagan on 2011-08-05
> **helliewm said:**
> Thanks for this Voria just talking about you in another thread! 

[http://ubuntuforums.org/showthread.php?t=1321340&page=4]("http://ubuntuforums.org/showthread.php?t=1321340&page=4")

I have an N130 and am happy to test any scripts for you.

Helen

New to this dont know if im gatecrashing or not.
I have a n140 and I cant get the vga to work. Dont know if its a problem with fn button or what.
Any help would be greatly appreciated

---

### Post by iamhimay on 2011-08-09
Just a quick heads up: You won't get an answer to your question here. Just start a fresh thread and be terse, but specific, in the subject line. So others who know things will be able to assess if they can help you or not. Good luck.

---

