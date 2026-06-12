---
title: "Thoughts from a Windows SysAdmin..."
date: 2008-10-31
forum: Testimonials &amp; Experiences
---

### Post by MilesCrew on 2008-10-31
I have a Dell Latitude D610 that I installed Intrepid on yesterday. I'm a Windows SysAdmin but somewhat a Linux noob so I've been learning a lot. I'm loving Ubuntu! I would love to see Linux take off and really become widespread. After a day in Intrepid, I thought I would throw down some thoughts to everyone as to some intial problems I had that may want to be discussed in order to better serve those new to Linux. Again, these are not "bashes", but things I think would be cool to better help those migrating to Linux and satisfying their first impressions.
 
1.) I am running Ubuntu on a Dell Latitude D610. One thing I think should be looked at is the default setting for "When laptop lid is closed" in Power Management. The default was set to "Blank Screen". I may be mistaken, but I would think most laptop users want their laptop to Standby/Suspend when closing the lid. Mine didn't at first until I figured this out and changed it.
 
2.) When I plug in my Logitech Quickcam Pro I get no notification that it is recognized or anything. As in Windows, there is a Removable Devices icon in the system tray. At first I thought my camera wasn't working. However, I installed Skype and it seemed to work just fine. I do see that flash drives are put on the desktop so that is a good notification on those.
 
3.) Setting the audio input/output settings should be more user friendly. Once I installed Skype, the audio in and out did not work. So, as I tried to set it in options I noticed that there isn't a "generic" name for my sound card to be able to choose it. Instead, I see things like "Intel ICH6 with STAC9750.51 blah blah" (there are about 5 of these entries) and for my webcam "USB Device 0x46d:0x991 USB Audio (ALSA)". I had to choose several different options before I got one that worked. It should be easier-reading such as "SigmaTel Integrated Sound" (with only one entry) and "USB Logitech Webcam Microphone" or something like that.
 
4.) Trying to get on my corporate WPA-secured wireless was another one (albeit this is not really a entry-level thing to do anyway). We have a self-signed CA certificate for our Exchange server. It took some searching to get it installed to /etc/ssl/certs (maybe have a default program that installs it on a double-click?). Once I did, I created a wireless profile for it but the Network Connections manager would not keep my setting for the certificate. Once I saved the profile it would keep all other information. However, if I close it and reopen the profile properties the certificate field was blank. The only way I could get it to work was to delete the profile and create it via the "Connect to a hidden network" option. Then it saved it and I'm on the corporate WiFi now beautifully.
 
5.) Why can't I create a VPN connection? When I go to the VPN tab in Network Connections all buttons are grayed out. We also have a VPN on our corporate network that I need to connect to. **UPDATE: **I did just find these two pages that describe my problem...
 
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...pn/+bug/258185[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/258185")
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...er/+bug/273932[/COLOR]]("https://bugs.launchpad.net/ubuntu/+s...er/+bug/273932")
 
These two links seem to hit the fact that VPN is not part of the OOB (out of the box) experience as could be interpreted by the VPN tab. There is a feature request for 9.04 that would tell the user that they need to first install some NM add-ons to enable VPN access.
 
6.) I think there may be a bug in Power Management. The default setting for putting the display to sleep is 40 minutes on AC and 15 minutes on battery. I've noticed twice this morning that my screen has gone blank in about 15 minutes even though I'm connected to AC.
 
I hope these thoughts can help Ubuntu move along even more. I'm a Windows developer so I'm beginning to look into Linux development so that maybe one day I can help fix things like this. Anyway, thanks for listening!

---

### Post by Sarmacid on 2008-10-31
> **MilesCrew said:**
> 5.) Why can't I create a VPN connection? When I go to the VPN tab in Network Connections all buttons are grayed out. We also have a VPN on our corporate network that I need to connect to.
I can only help you with this one. All of the administration tools are grayed out, but there's a button that says unlock. Hit it and it will ask for your pass, input your pass and you should be able to interact with it now.

Hope you really enjoy Ubuntu!

---

### Post by MilesCrew on 2008-10-31
Sarmacid,

Thanks for the advice, however I do not see an unlock button. However, I did just find these two pages that describe my problem...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/258185]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/258185")

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273932]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273932")

These two links seem to hit the fact that VPN is not part of the OOB (out of the box) experience as could be interpreted by the VPN tab. There is a feature request for 9.04 that would tell the user that they need to first install some NM add-ons to enable VPN access.

---

### Post by billgoldberg on 2008-10-31
I'm not on Ubuntu at the moment and don't use vpn, but if the previous user says you need to unlock it and there is no unlock button, try opening the app as root.

in a terminal 

gksudo applicationname


--

You make some valid points. 

You could make some bug reports on launchpad.

---

### Post by Joeb454 on 2008-10-31
Moved to Testimonials & Experiences :)

Nice to hear you're enjoying it (even if you are having a few issues)

---

### Post by MilesCrew on 2008-10-31
Thanks for the move. I glanced at the many categories, but must have overlooked this one.

---

### Post by armandh on 2008-10-31
as a total ubuntu noob, as we all once were, be advised that the day after general release you are an early adopter and that after a month or two in the wider testing world you will find [after the updates] most all things to be a lot more polished.

the most polished being the LTS ver. just B4 support expires

---

### Post by MilesCrew on 2008-10-31
Yeah, that sounds about right. Same as what I'm used to with Windows. Just thought I'd give some "initial" thoughts. Thanks!

---

### Post by koruptid on 2008-10-31
#3 is a problem I've been fighting with for a couple days now.... I'm a developer and sysadmin as well and I'm having the same frustration with the layout of PulseAudio and the way it identifies hardware.... it seems clear that the current hardware identifiers are geared toward "linux geeks" rather than a layman's understanding of hardware.

#5... no guarantees that it will work completely (I'm having issues with PPTP and being able to properly authenticate) but you need to install the following packages:
```

pptp-linux
network-manager-pptp

```

---

### Post by autocrosser on 2008-10-31
Glad you are liking it--I'm one of the alpha/beta testers --all involved worked hard to make this one look/work/feel good--there were about 87 known bugs at release--I generally tell my people to wait about 2~3 weeks after release to jump in. Most of the uncaught bugs are found in that time---

Network-Manager 0.7 has had a bumpy ride this time thru--you might take a look at the closed Intrepid development forum--I remember some talk about the VPN issue & you might find some insight there....

---

### Post by autocrosser on 2008-10-31
If you like development work, think about getting involved with alpha/beta testing--we get to play with the shiny new toys & fix things when they break--I run 2 testing installs during--1 back-dated 1 week behind the other.....We have a really good testing community--everyone helps each other :).

Jaunty development will be starting about a month from now--Beta will come in about Feb/March--good time to see what it is about:guitar:

---

### Post by MilesCrew on 2008-10-31
On the note of development, I've tried looking to see how development is done in Linux. It seems that core languages are often C++ or Python with GUI coming from Qt or GTK. Is that pretty much the consensus?

---

### Post by loell on 2008-10-31
> **MilesCrew said:**
> On the note of development, I've tried looking to see how development is done in Linux. It seems that core languages are often C++ or Python with GUI coming from Qt or GTK. Is that pretty much the consensus?

core development is in C, the desktop development is mostly done in GTK or QT with a much wider range of languages (python c++ C ..)

desktop with C/gtk is still more popular.

---

### Post by Thelasko on 2008-10-31
> **MilesCrew said:**
> 1.) I am running Ubuntu on a Dell Latitude D610. One thing I think should be looked at is the default setting for "When laptop lid is closed" in Power Management. The default was set to "Blank Screen". I may be mistaken, but I would think most laptop users want their laptop to Standby/Suspend when closing the lid. Mine didn't at first until I figured this out and changed it.
There are some issues with suspend and hibernate.  It doesn't work on every machine; I think it's a BIOS issue.  I suspect the developers left the default setting as "blank screen" as a workaround.  I'm still not sure why it's "blank screen" and not something like "screen off."

---

### Post by wolfen69 on 2008-10-31
kudos to the OP for a well thought out "initial impression" post. welcome to linux, and above all, have fun.

---

### Post by VoodooLoveDog on 2008-10-31
As with the OP, I to am a win sysadmin running a Dell D610. I've been running Ubuntu on the box since it was in version 7.10. I love using the OS. However, I would like to add my 2 cents.

1) I installed the software (mostly 8.04) on several machines: Dell Dimensions, white boxes, HP/Compaq laptops. While I haven't done a fresh install of 8.10, I know from 8.04 that if I install the OS on a machine with a given monitor and then replace the monitor, I lose the splash screen. Now I figured out via these awesome forums how to fix it, but I still think the process should be streamlined. 

2) I really wish hiberate would work reliably on my laptop. It is one of the last remaining problems with it. I do however realize that some of the problem is beyond the dev staff's control (BIOS issues, Video drivers).

3) Changing resolutions is somewhat of a pain in the OS too. I installed the OS on a whitebox with a 7600 Nvidia card. The default comes up at 640x480. Without editing the config file, this made changing the res very difficult. 

For one, the 'Screens and Graphics' menu item is by default hidden. I don't understand why it's hidden and it's placement. Why isn't this menu item under 'System -> Preferences'.

Second, one I could get to the menu item, the size of it made it almost impossible to confirm my new settings. 


I'm sure there are other little nuances that I'm forgetting, but all in all I love using the software. Thanks for a great OS!

---

### Post by autocrosser on 2008-10-31
I think you 'aught to check out 8.10--screen config is gone--the new X uses HAL to "create" a xorg.conf--you will only find a basic file listed--This has been both good & bad, depends on your hardware....

I have heard that suspend "finally" works--not sure myself (only desktops right now), but I was reading several posts in the development forum--you might cruise thru: [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)  and do a search--the forun is closed, but theres is a wealth of info there as we went thru the cycle.

---

### Post by autocrosser on 2008-10-31
I have several posts about working with the new Xorg is the closed forum--there is a link to the Wiki page that is in works.....

---

### Post by steveneddy on 2008-10-31
Post back when you get those issues ironed out.

---

### Post by MilesCrew on 2008-10-31
> **autocrosser said:**
> ...8.10--screen config is gone--the new X uses HAL to "create" a xorg.conf--you will only find a basic file listed

I read about this as well. I've tried earlier versions of Ubuntu/Kubuntu and have had to deal with that xorg.conf file several times. Definitely a pain. But, everything display-wise works straight out of the box for me on this laptop.

> **autocrosser said:**
> I have heard that suspend "finally" works

Yes, it works for me beautifully (once I changed the default setting in Power Management of course).

---

### Post by lancest on 2008-10-31
> **VoodooLoveDog said:**
> 
3) Changing resolutions is somewhat of a pain in the OS too. I installed the OS on a whitebox with a 7600 Nvidia card. The default comes up at 640x480. Without editing the config file, this made changing the res very difficult. 

For one, the 'Screens and Graphics' menu item is by default hidden. I don't understand why it's hidden and it's placement. Why isn't this menu item under 'System -> Preferences'.


The Linux Nvidia proprietary driver provides an applet called nvidia-settings that makes it very easy to configure resolutions.
(binary blob driver)
Just make sure it's installed. Makes it easy for me. 
Glad you like Ubuntu!

---

### Post by -kg- on 2008-10-31
I too have recently installed Ubuntu 8.04 on a laptop (Toshiba Satellite A135-S4487) and am extremely happy with the results.  So far, everything I've tested is working flawlessly.

Though I'm not a SysAdmin of any type of system, I have been "hacking" at computers since the DOS 2.X days (I won't go into the "et.al." here) and had a couple of comments on your excellent post:

> 2.) When I plug in my Logitech Quickcam Pro I get no notification that it is recognized or anything. As in Windows, there is a Removable Devices icon in the system tray. At first I thought my camera wasn't working. However, I installed Skype and it seemed to work just fine. I do see that flash drives are put on the desktop so that is a good notification on those.

I kind of wondered about this as well.  I have an external "TB" drive connected via FireWire which I've had occasion to "eject" and remove, then later hot-reconnect it.  I didn't know whether it had actually detected and installed it until I pulled up Nautilus to check to see if the drive was present (it was, of course).  It would kind of be nice to have the little pop-up windows, "Linux has (detected/installed) new hardware" so one (and especially a newbie) would at least know that the device had been properly detected and the drivers installed for it.

There are situations where one might not plug something in correctly, or a connector is damaged, and the only way you really have (at least, a newbie) is to launch an associated program and *hope* that it doesn't go into an endless loop or (heaven forbid!) cause damage because of incomplete connection.

> 3.) Setting the audio input/output settings should be more user friendly. Once I installed Skype, the audio in and out did not work. So, as I tried to set it in options I noticed that there isn't a "generic" name for my sound card to be able to choose it. Instead, I see things like "Intel ICH6 with STAC9750.51 blah blah" (there are about 5 of these entries) and for my webcam "USB Device 0x46d:0x991 USB Audio (ALSA)". I had to choose several different options before I got one that worked. It should be easier-reading such as "SigmaTel Integrated Sound" (with only one entry) and "USB Logitech Webcam Microphone" or something like that.

I've experienced this as well, but hadn't given it much thought.  The only problem with what you're proposing here is it's difficult to include nicely entitled drivers for every single device out there that someone might have in their systems.  To do so would turn at least that distro that tried into as much of a piece of bloatware as Windows has become.

Even Windows doesn't have *everything* out there.  When I reinstalled XP this last time, I hadn't remembered, but there's not a driver for the Ethernet chips on my motherboard.  It's fortunate that I have other computers.  I had to go to one of my other computers, find and download the drivers, then transport them to my desk top (White Box...I built it myself).  I couldn't download them directly to the desktop because I get my internet connection through Ethernet.

Heck, XP doesn't even always work right *with* the drivers installed.  I recently installed two SATA devices in my box (the reason for the XP reinstall).  I fresh-reinstalled XP, installing the drivers at the appropriate point in the installation process.  While I finally got XP to see the SATA DVD burner (my old one had bit the dust and I decided to get a SATA drive to replace it), I had also installed a SATA hard drive.  There is no way I can get XP to recognize the SATA hard drive, and I tried everything.  No problem, though...I'm migrating to Linux, and Linux recognizes both drives natively (even booted to the LiveCD).

I too find it a bit cumbersome...on my desktop I *still* haven't figured out how to get my system sounds set up, though most everything else (in sound) works, like the music/media players.  I'm sure it's just something I'm missing, as all the sound works on the laptop without configuration.

> 4.) Trying to get on my corporate WPA-secured wireless was another one (albeit this is not really a entry-level thing to do anyway).

Quite true, and the entry level part is fairly easy, though not too terribly well documented.  It took some searching before I found much about setting up WEP (or WPA) security on the client computer, and then it was none too clear (as in, no step-by-step that would really be useful for a true newbie).  It was fortunate that I have set many of these systems up and fairly well knew how to do it and what settings to use.

> 6.) I think there may be a bug in Power Management. The default setting for putting the display to sleep is 40 minutes on AC and 15 minutes on battery. I've noticed twice this morning that my screen has gone blank in about 15 minutes even though I'm connected to AC.


That is my thought, as well.  Though I suppose that blanking and/or turning off a monitor *is* the "green" thing to do, it is unnecessary as far as saving a monitor from "burn-in" in today's IT world, as they are by and large TFT-diode type flat panel displays.  I have the monitor settings on both of my computers set to "never turn off", but they seem to get blanked or turned off after a time in spite of it.  I also have it set to not dim the display, but it does that anyway, as well.  This can get annoying at times, especially when you're viewing something for some period of time and then the screen gets blanked and disturbs your concentration.

All in all though, I'm enjoying my migration to Linux and Ubuntu.  I'm reading and studying as fast as I can to make the skills migration, then I may study up on some of the programming languages as well.  I haven't written any programs since my DOS days, and I'm sure some of the compilers are easier to use than they once were.  It's one of the things I like about Linux...it's highly configurable, stable, and once you've gotten over the learning curve, I'm sure it's highly (de- and re-) compilable.

---

### Post by MilesCrew on 2008-11-01
-kg-,

Great thoughts! Thanks for the post. It's good to see people other than myself that are getting their feet wet in Linux and trying to figure out how we can better it.

---

### Post by Stu09 on 2008-11-03
> **MilesCrew said:**
> Sarmacid,

Thanks for the advice, however I do not see an unlock button. However, I did just find these two pages that describe my problem...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/258185]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/258185")

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273932]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273932")

These two links seem to hit the fact that VPN is not part of the OOB (out of the box) experience as could be interpreted by the VPN tab. There is a feature request for 9.04 that would tell the user that they need to first install some NM add-ons to enable VPN access.

You need to install network-manager-openvpn to make the add button become active.
```
 sudo apt-get install network-manager-openvpn
```

---

### Post by MilesCrew on 2008-11-03
Yes, after I saw the posts I referenced, I installed the PPTP plugin for network manager. However, I still have yet to get it to work. I haven't had much time to deal with it the past few days.

---

