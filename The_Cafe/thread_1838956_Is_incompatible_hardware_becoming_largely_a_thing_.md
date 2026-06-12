---
title: "Is incompatible hardware becoming largely a thing of the past?"
date: 2011-09-04
forum: The Cafe
---

### Post by kaldor on 2011-09-04
Linux has traditionally been labled as an OS that just simply doesn't work with much modern hardware. I've really beginning to feel that this is no longer true. I posted my experience a few times in different posts, but thought it would be kinda interesting to see where the rest of the community stands on this. This isn't Windows vs Linux either. The reason I am posting this is simply because I never have to alter or mess around with anything; I buy something, it just works. Other people often tend to complain about how nothing works, and I'm kinda confused about it.

Wireless works out of the box on most PCs that I've used it on. For example, I tried my Ubuntu 11.04 live USB on a few (5 or 6; dunno the card) computers at a store before buying one. Every PC had working wireless except one. I bought the one that did not have an out of the box wireless support; a Google search revealed the latest kernel already included it. It is already working on the Oneiric beta. 

Graphics cards were also a weak point in Linux before. From my experience, both NVIDIA and ATI/AMD are excellent in this department. My Ubuntu dual boot seems to have comparable FPS to that on  Windows 7; in some cases, it's even better. Open source NVIDIA and AMD are good for out of the box setups on desktops these days also. Not ready for laptops yet, but will get there soon I assume.

My audio seems to have about par quality between Windows 7 and Natty. I think Windows 7 works slightly better here, but in general I only notice it in some very specific places. Overall, sound quality is nearly identical.

I haven't found a printer yet which hasn't worked with the generic drivers available in Ubuntu or Fedora. My scanner also works out of the box with no tinkering. My cameras all work fine and are instantly detected by Shotwell. 

Are my needs just very limited, or is the old stigma no longer true? Please, post your experiences on machines made within the last 3 years.

This isn't a "praise Linux" thread, so please don't post *WorksForMe* or anti-Windows/Apple replies. Some people get lucky, some don't. The point of this thread is to get community feedback as to where Ubuntu stands when buying a new PC or peripheral. It'll probably end up in Recurring, though.

tl;dr: Does Linux still suck with your hardware?

Edit: Just a reminder that I am mainly talking about modern machines. As in if you go out and buy a new PC or device, will it work or not.

---

### Post by aeronutt on 2011-09-04
My experience; Linux lags (state of the art) hardware by at least 1 yr.

Details: ~10 months ago, purchased a new Dell Vostro with i3 Intel processor and AMD discrete GPU. 10.04LTS and 10.10 simply didn't work on the new hardware. 11.04 worked somewhat, and the AMD graphics is not supported.  Just in the last few weeks, 11.04 is now working pretty well, except for the AMD GPU.

Now, throw in the power bug in the latest kernels, and one could argue that Ubuntu/Linus is still not where it should be.

---

### Post by texaswriter on 2011-09-04
I'm not sure I would generalize like that, mostly because it takes a lot of hard work by a lot of people to ensure that. Because some hardware manufacturers don't even bother trying to write Linux drivers or releasing much in the way of specs, it unfortunately does take hard work with some of the hardware. 

You do see this "open source hardware" thing developing, so I guess we'll see where that takes us.

---

### Post by texaswriter on 2011-09-04
> **aeronutt said:**
> My experience; Linux lags (state of the art) hardware by at least 1 yr.

Details: ~10 months ago, purchased a new Dell Vostro with i3 Intel processor and AMD discrete GPU. 10.04LTS and 10.10 simply didn't work on the new hardware. 11.04 worked somewhat, and the AMD graphics is not supported.  Just in the last few weeks, 11.04 is now working pretty well, except for the AMD GPU.

I know some people are particular about only using non-proprietary drivers and software, but if I bought proprietary hardware (read: any hardware), I'm going to accept a "proprietary" driver if it works. As such, I always use the ATI (AMD now) drivers for my graphics cards (same as a built-in gpu) and have never had problems.

---

### Post by aeronutt on 2011-09-04
> **texaswriter said:**
> I know some people are particular about only using non-proprietary drivers and software, but if I bought proprietary hardware (read: any hardware), I'm going to accept a "proprietary" driver if it works. As such, I always use the ATI (AMD now) drivers for my graphics cards (same as a built-in gpu) and have never had problems.

Neither non-proprietary or proprietary drivers are working with my AMD GPU. If I knew then what I know now, I would have upgraded from the i3 to and i5 or i7  processor, and dropped the AMD GPU.

---

### Post by hakermania on 2011-09-04
No, as long as new hardware comes out there will be problems

---

### Post by kaldor on 2011-09-04
> **aeronutt said:**
> Neither non-proprietary or proprietary drivers are working with my AMD GPU. If I knew then what I know now, I would have upgraded from the i3 to and i5 or i7  processor, and dropped the AMD GPU.

For comparison's sake, which GPU?

> I'm not sure I would generalize like that...

Not sure if that was directed at me or not, but I am going based on 5 computers in my home as well as another handful when testing at a store. Everything I checked was always working out of the box.

---

### Post by texaswriter on 2011-09-04
> **aeronutt said:**
> Neither non-proprietary or proprietary drivers are working with my AMD GPU. If I knew then what I know now, I would have upgraded from the i3 to and i5 or i7  processor, and dropped the AMD GPU.

Downloading the driver (32/64 bit).
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

Installation instructions for the driver on Natty.
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")

If you have another version of Linux, you can find the installation instructions here. 
[http://wiki.cchtml.com/index.php/Category:Installation_Documentation]("http://wiki.cchtml.com/index.php/Category:Installation_Documentation")

Verify the install.
[http://wiki.cchtml.com/index.php/Verifying]("http://wiki.cchtml.com/index.php/Verifying")

Configure the installation.
[http://wiki.cchtml.com/index.php/Configuring]("http://wiki.cchtml.com/index.php/Configuring")

Troubleshooting. (Uninstall all ATI drivers from system from previous installation attempts AND THEN try ALL the above steps in all the links before troubleshooting). 
[http://wiki.cchtml.com/index.php/Troubleshooting]("http://wiki.cchtml.com/index.php/Troubleshooting")

---

### Post by Oxwivi on 2011-09-04
Quite old Pentium IV here, but with the exception of the nVidia GPU, everything runs great.

---

### Post by keithpeter on 2011-09-04
Hello All

There is also the question of support for older hardware, as some drivers are dropped or will not compile/install on current releases of the kernel. 

I'm thinking of some of the older nvidia cards &c

[http://mark.pilgrim.usesthis.com/](http://mark.pilgrim.usesthis.com/)

Scroll down to the 'dream setup' section. I'd like a hardware that I could just use for 10 years, with fully updated system  hardware. I've got four years on this AMD box with nvidia 6150 graphics. Its running Debian 6 and when that drops off the end of old stable I might move sideways to CentOS 6.

---

### Post by aeronutt on 2011-09-04
> **kaldor said:**
> For comparison's sake, which GPU?

AMD Radeon HD 6630M (128-bit) 1GB Graphic

---

### Post by aeronutt on 2011-09-04
> **texaswriter said:**
> Downloading the driver (32/64 bit).
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

Installation instructions for the driver on Natty.
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")

If you have another version of Linux, you can find the installation instructions here. 
[http://wiki.cchtml.com/index.php/Category:Installation_Documentation]("http://wiki.cchtml.com/index.php/Category:Installation_Documentation")

Verify the install.
[http://wiki.cchtml.com/index.php/Verifying]("http://wiki.cchtml.com/index.php/Verifying")

Configure the installation.
[http://wiki.cchtml.com/index.php/Configuring]("http://wiki.cchtml.com/index.php/Configuring")

Troubleshooting. (Uninstall all ATI drivers from system from previous installation attempts AND THEN try ALL the above steps in all the links before troubleshooting). 
[http://wiki.cchtml.com/index.php/Troubleshooting]("http://wiki.cchtml.com/index.php/Troubleshooting")

Thanks, I appreciate the help. But I've tried them all. And many others. And many complete reloads of the OS. :):)

---

### Post by Iowan on 2011-09-04
I'm 1 for 3 in webcam department, so far. The Labtec works, the Microsoft and Logitech - not so much. (The Microsoft didn't work on a Windows box, either - but the Logitech did).

---

### Post by kaldor on 2011-09-04
> **Iowan said:**
> I'm 1 for 3 in webcam department, so far. The Labtec works, the Microsoft and Logitech - not so much. (The Microsoft didn't work on a Windows box, either - but the Logitech did).

Just to compare with my own stuff, I found an old Webcam that I bought back around 2004. It's a generic, very low quality one, but when I plugged it into my PC it worked automatically. Same goes for my laptop's webcam (magically stopped working in Lucid for some reason though).

---

### Post by beew on 2011-09-04
> **aeronutt said:**
> My experience; Linux lags (state of the art) hardware by at least 1 yr.
.

I year behind state of the art is not a big deal for most people, in fact even on Windows forums they advise people to stay ~ a year behind state of the art because things are more likely to not work if hardware is too new and price drops quite a bit after one year.

---

### Post by JustinR on 2011-09-04
nVidia Optimus technology (unsupported in Linux) largely makes your expensive dedicated graphics card useless and is becoming much more common, especially at Dell.

Some TV Tuners/Fingerprint readers also come to mind.

---

### Post by rjbl on 2011-09-05
> **kaldor said:**
> Linux has traditionally been labled as an OS that just simply doesn't work with much modern hardware. I've really beginning to feel that this is no longer true. I posted my experience a few times in different posts, but thought it would be kinda interesting to see where the rest of the community stands on this. This isn't Windows vs Linux either. The reason I am posting this is simply because I never have to alter or mess around with anything; I buy something, it just works. Other people often tend to complain about how nothing works, and I'm kinda confused about it.

Wireless works out of the box on most PCs that I've used it on. For example, I tried my Ubuntu 11.04 live USB on a few (5 or 6; dunno the card) computers at a store before buying one. Every PC had working wireless except one. I bought the one that did not have an out of the box wireless support; a Google search revealed the latest kernel already included it. It is already working on the Oneiric beta. 

Graphics cards were also a weak point in Linux before. From my experience, both NVIDIA and ATI/AMD are excellent in this department. My Ubuntu dual boot seems to have comparable FPS to that on  Windows 7; in some cases, it's even better. Open source NVIDIA and AMD are good for out of the box setups on desktops these days also. Not ready for laptops yet, but will get there soon I assume.

My audio seems to have about par quality between Windows 7 and Natty. I think Windows 7 works slightly better here, but in general I only notice it in some very specific places. Overall, sound quality is nearly identical.

I haven't found a printer yet which hasn't worked with the generic drivers available in Ubuntu or Fedora. My scanner also works out of the box with no tinkering. My cameras all work fine and are instantly detected by Shotwell. 

Are my needs just very limited, or is the old stigma no longer true? Please, post your experiences on machines made within the last 3 years.

This isn't a "praise Linux" thread, so please don't post *WorksForMe* or anti-Windows/Apple replies. Some people get lucky, some don't. The point of this thread is to get community feedback as to where Ubuntu stands when buying a new PC or peripheral. It'll probably end up in Recurring, though.

tl;dr: Does Linux still suck with your hardware?

Edit: Just a reminder that I am mainly talking about modern machines. As in if you go out and buy a new PC or device, will it work or not.

[I]Are my needs just very limited, or is the old stigma no longer true?

[/I]Personally, I've never found much truth in the 'old stigma' that GNU/Linux ain't much good on the bleeding edge of hardware. It is probably true that current GNU/Linux does noticeably better on old kit* than current Windows does *- that dates back to the days of  RedHat 5 and 486 processors. 

'Twas always so and probably ain't going to change much in the foreseeable future. GNU/Linux has *always* been supported by a very competent and very keen hardware driver writing community to very good effect. I have never known a failure in any of the generic drivers - since about 1995/6. OK so proprietary drivers more often enable the full capabilities of the h/w to be exploited but, there again, in all current distros the relevant proprietary drivers are trivially easy to locate and install.

*Edit: Just a reminder that I am mainly talking about modern machines. As  in if you go out and buy a new PC or device, will it work or  not.[/QUOTE]*

The Exam Question: In my experience the answer is yes; but that has been true for about the last ten or fifteen years. *All* the sweaty moments that I can recall involving h/w driver angst have actually been in Windows systems - in which I worked as a pro since 1985.

rjbl

---

### Post by NightwishFan on 2011-09-05
> **kaldor said:**
> Linux has traditionally been labled as an OS that just simply doesn't work with much modern hardware.
Linux sometimes has support for hardware before it is even physically available. The only problem is when the specs are not open for some hardware. Or (optimus?) they make it hard to run on Linux.

---

### Post by smellyman on 2011-09-05
I think we can all agree it has come a looooooooonnng way.
 
My first experience with linux in 02 was a nightmare and I quickly gave up since nothing would work.  No NIC, no modem, bad video etc...
 
Now it is very rare that I have an issue, actually the only issue I had in the last couple of years was a broadcom wireless card, but now that seems to work on every distro now.
 
if I have a retail copy of windows and a linux distro, the chances of everything working ootb is greater on Linux.  Espcicially since the windows dirvers quickly become outdated on the cd.  Getting a wireless card or a wired NIC to work on windows can be a pain.  I have to download dirvers for it on linux and move to the Windows pc via usb stick......

---

### Post by Legendary_Bibo on 2011-09-05
No...no it's not. My wireless card didn't just work out of the box I had to edit a configuration file, and install some stuff, and my graphics card on my other laptop (ATI card) has poor performance.

---

### Post by NightwishFan on 2011-09-05
> **Legendary_Bibo said:**
> No...no it's not. My wireless card didn't just work out of the box I had to edit a configuration file, and install some stuff, and my graphics card on my other laptop (ATI card) has poor performance.

I have been lucky so far. My laptop is supported with no non free firmware files on Debian's stock .32 kernel (amd64). Soundcard works input/output, webcam works (and is automatically flipped so the image isn't upside down), my graphics get great performance, I am able to play Urban Terror at 60+ frames solid, I also have native kernel modesetting and 1 second resume from suspend, wireless works, cdrom drive passes cdparanoia tests, Multi-monitor output works, and I get my advertised 4hrs of battery life.

I like Asus, if not Zareason, I am always buying from Asus.

---

### Post by ninjaaron on 2011-09-05
Ha.  No, it is not a thing of the past.

I have a netbook with a Broadcom Crystal HD card, which has an open source driver, that isn't in the kernel for some reason.  It has an egalax multitouch screen which does have a driver in the kernel, and it doesn't do multitouch.  There is no driver for the accelerometer.  Out of box, touchscreen is completely broken, but there is a tweak.  Same with headphone jack and internal mic.

So, in my experience, there are still plenty of problems.  My other computer has always worked perfectly with Linux, however.  It just has some generic Intel motherboard without any extras.  Boring, but you know it will work.  Intel does it right.

---

### Post by kaldor on 2011-09-05
> **Legendary_Bibo said:**
> No...no it's not. My wireless card didn't just work out of the box I had to edit a configuration file, and install some stuff, and my graphics card on my other laptop (ATI card) has poor performance.

Which wireless and graphics cards? As for wireless, I think a large number of Realtek and Broadcom cards will "just work" with recent Linux distros these days. Realtek usually had out of the box support, and Broadcom's open source drivers are trickling into the kernel.

Edit:

I've also heard some people say things along the lines of "good luck getting your multimedia keyboard/multibutton mouse working under Linux", which for me and a few other Linux users I know disagree with. I use a logitech mouse with 9 buttons and it works identically in Windows and Linux without any additional tweaking. An older multimedia keyboard I have works out of the box as well and all of the shortcut keys work with no tinkering. 

Sorry if it sounds like I'm trying to disprove anything, btw. I'm well aware of the problems a lot of people tend to have, but I still think a large lot of it is FUD (not directed at anyone here) based on the experiences of myself and others.

---

### Post by forrestcupp on 2011-09-05
Try recording audio using ASIO for an M-Audio Fast Track external sound card. It ain't gonna happen. In Windows 7, I just plug it in, and it works. If I install the drivers, it works very well.

> **smellyman said:**
> I think we can all agree it has come a looooooooonnng way.
I do agree that things have come a long way.

---

### Post by disabledaccount on 2011-09-05
> **forrestcupp said:**
> Try recording audio using ASIO for an  M-Audio Fast Track external sound card. It ain't gonna happen. In  Windows 7, I just plug it in, and it works. If I install the drivers, it  works very well.Just for curiosity I've asked uncle Google about this sound card and He told me something different:
[http://alsa.opensrc.org/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/M-Audio_FastTrack_Pro)
[http://thread.gmane.org/gmane.linux.alsa.devel/42396](http://thread.gmane.org/gmane.linux.alsa.devel/42396)
Low-latency tweaks/patches for usbaudio are also available.
Peoples are able to get it working in simultaneous 2in/4out mode and main "tweak" that allows to use basic functionality is to add device id.

It's not very surprising that not every piece of HW will work OOTB just after lauching OS from pendrive.

---

### Post by forrestcupp on 2011-09-06
> **tomazzi said:**
> Just for curiosity I've asked uncle Google about this sound card and He told me something different:
[http://alsa.opensrc.org/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/M-Audio_FastTrack_Pro)
[http://thread.gmane.org/gmane.linux.alsa.devel/42396](http://thread.gmane.org/gmane.linux.alsa.devel/42396)
Low-latency tweaks/patches for usbaudio are also available.
Peoples are able to get it working in simultaneous 2in/4out mode and main "tweak" that allows to use basic functionality is to add device id.
Windows 7 - plug it in, open up your recording software, lay some tracks

Linux - plug it in, scour the web to find different patches to get each individual problem to work, spend hours trying to learn how to patch the kernel with multiple patches, remove Pulse audio because it gets in the way of the required Alsa, try to get your sound to even work after removing Pulse, try to set up all the different parts of Jack and unsuccessfully try to figure out how it all works together, open up your recording software, find out that it's still a PITA to figure out how to get Ardour to interface with the right sound card, after consuming a couple of bottles of Excedrin, try to lay some tracks.

Trust me. I didn't just come up with a Google link, I spent some time on this. Even if it's possible, it isn't worth it.

---

### Post by el_koraco on 2011-09-06
> **forrestcupp said:**
> try to get your sound to even work after removing Pulse, 

Isn't that just a one line in gconf-editor in Gnome?

---

### Post by forrestcupp on 2011-09-06
> **el_koraco said:**
> Isn't that just a one line in gconf-editor in Gnome?

Windows 7 - plug it in, open up your recording software, lay some tracks.

---

### Post by el_koraco on 2011-09-06
I'm not comparing stuff, I'm just wondering about the Pulse to Alsa escape. I don't have Pulse on my machine, but I did try it for a day or so, and installing and removing it was extremely easy. That was Openbox, though, not Gnome.

---

### Post by NightwishFan on 2011-09-06
You know what never mind.

---

### Post by forrestcupp on 2011-09-06
> **el_koraco said:**
> I'm not comparing stuff, I'm just wondering about the Pulse to Alsa escape. I don't have Pulse on my machine, but I did try it for a day or so, and installing and removing it was extremely easy. That was Openbox, though, not Gnome.

I wish I would have known about that when I was beating my brains out. :)

---

### Post by el_koraco on 2011-09-06
> **forrestcupp said:**
> I wish I would have known about that when I was beating my brains out. :)

I think your problems were due to all the Gnome apps integrating with Gstreamer, which is closely tied to Pulseaudio in Gnome (and KDE more recently). You gotta make sure all the Gstreamer channels point to Alsa, and you also gotta get rid of the default sound indicator and stuff like that. It might very well be problematic in Gnome. 

However, audio apps that aren't DE specific, like VLC, mplayer, Audacious and gang let you choose which sound system you want to use. Ditto for Flash, it should just be piped through any audio sink available.

---

### Post by disabledaccount on 2011-09-06
> **forrestcupp said:**
> Windows 7 - plug it in, open up your recording software, lay some tracks

Linux - plug it in, scour the web to find different patches to get each individual problem to work, spend hours trying to learn how to patch the kernel with multiple patches, remove Pulse audio because it gets in the way of the required Alsa, try to get your sound to even work after removing Pulse, try to set up all the different parts of Jack and unsuccessfully try to figure out how it all works together, open up your recording software, find out that it's still a PITA to figure out how to get Ardour to interface with the right sound card, after consuming a couple of bottles of Excedrin, try to lay some tracks.

Trust me. I didn't just come up with a Google link, I spent some time on this. Even if it's possible, it isn't worth it.You've suggested that this card is unusable on Linux while in fact it's fully supported by open source driver.

It took me maybe 20 secs to find the patch - so please. Patching kernel with ready to use patch is not more complicated than f.e. compiling wine. But generally it's special case - normally it's completely oposite situation:

Linux - boot to live session from pendrive run install, click 6 times forward and watch Your favorite YouTube songs/movies or check whats new on ubuntuforums.org - almost none of existing PC's will make troubles.

Windows7/Vista/XP (still very popular on older machines):
After long installation not much HW works OOTB, except keyboard, mouse and limitted VGA support, limitted sound drivers (if You have AC97). You have to install each additional driver separately and if You are lucky then maybe it wont be necessary to search for older versions of drivers after it becomes clear that newest are broken (like f.e. Intel WiFi). In case of XP searching for drivers is rather time-consuming task these days, as most manufacturers are not providing them on main dowload sites.

In last Year I had maybe ~40 different laptops which I've boosted with ubuntu - almost everything worked flawlessly OOTB with FULL HW functionality, even such exotic like DELL XPS M1710 (with the "magic" back and ambient lights)

---

### Post by kaldor on 2011-09-06
There are lots of workarounds for incompatible stuff, but not many people are going to really bother with it. My thread isn't really about stuff that "may" work, but rather things that will just work and work properly. 

Like forrestcupp said, "Even if it's possible, it isn't worth it". Things need to just work or else nobody is going to bother with it. That's the hard fact when dealing with most users.

---

### Post by disabledaccount on 2011-09-06
> **kaldor said:**
> There are lots of workarounds for incompatible stuff, but not many people are going to really bother with it. My thread isn't really about stuff that "may" work, but rather things that will just work and work properly. 

Like forrestcupp said, "Even if it's possible, it isn't worth it". Things need to just work or else nobody is going to bother with it. That's the hard fact when dealing with most users.
1. I think You have wrong understanding of term "compatible"
2. drivers not included in mainstream are still drivers.
3. Workarounds are needed in every existing OS on the planet - they are preceding final solutions/bug fixes.
4. You should title Your topic like "Does Linux supports all the existing hardware?" or "Is it easier to install Utra-Jtag-PCI-analyser under Linux or under windows" (or something in this sense), but answer for current topic is simply: **yes, because most commonly used HW works OOTB (what in practice means ~98%) and in almost all other cases drivers are available to users, just not always included in mainstream.**

---

### Post by Legendary_Bibo on 2011-09-06
> **tomazzi said:**
> You've suggested that this card is unusable on Linux while in fact it's fully supported by open source driver.

It took me maybe 20 secs to find the patch - so please. Patching kernel with ready to use patch is not more complicated than f.e. compiling wine. But generally it's special case - normally it's completely oposite situation:

Linux - boot to live session from pendrive run install, click 6 times forward and watch Your favorite YouTube songs/movies or check whats new on ubuntuforums.org - almost none of existing PC's will make troubles.

Windows7/Vista/XP (still very popular on older machines):
After long installation not much HW works OOTB, except keyboard, mouse and limitted VGA support, limitted sound drivers (if You have AC97). You have to install each additional driver separately and if You are lucky then maybe it wont be necessary to search for older versions of drivers after it becomes clear that newest are broken (like f.e. Intel WiFi). In case of XP searching for drivers is rather time-consuming task these days, as most manufacturers are not providing them on main dowload sites.

In last Year I had maybe ~40 different laptops which I've boosted with ubuntu - almost everything worked flawlessly OOTB with FULL HW functionality, even such exotic like DELL XPS M1710 (with the "magic" back and ambient lights)

Protip: Install Windows 7 with an internet connection.

---

### Post by disabledaccount on 2011-09-06
> **Legendary_Bibo said:**
> Protip: Install Windows 7 with an internet connection.OOTB stands for "**O**ut **O**f **T**he **B**ox".
Try linux with internet connection... :)

---

### Post by Legendary_Bibo on 2011-09-06
> **tomazzi said:**
> OOTB stands for "**O**ut **O**f **T**he **B**ox".
Try linux with internet connection... :)

Yeah linux doesn't let my wireless card function OOTB so yeah I would if I could.

---

### Post by NightwishFan on 2011-09-06
> **Legendary_Bibo said:**
> Yeah linux doesn't let my wireless card function OOTB so yeah I would if I could.

Then buy a wireless card that works and stop complaining.

---

### Post by Neken on 2011-09-06
> **NightwishFan said:**
> Then buy a wireless card that works and stop complaining.

protip: you can't buy wireless cards for most laptops.

---

### Post by NightwishFan on 2011-09-06
> **Neken said:**
> protip: you can't buy wireless cards for most laptops.

Sad. 1. Buy a laptop that works.  2. There are usb wireless adapters.

---

### Post by kaldor on 2011-09-06
> **NightwishFan said:**
> Sad. 1. Buy a laptop that works.  2. There are usb wireless adapters.

Like I said before, I found that the wireless worked on most new PCs I've tried it on.

---

### Post by user1397 on 2011-09-06
I thought this was largely the case until I bought a Gateway laptop a few months ago.

I had never had any real hardware problems with Linux especially Ubuntu before, but this laptop has given me my share of headaches.

For one, it wouldn't even boot correctly (or it did, but the screen would be black) until I messed with some grub settings (like setting acpi=off)

Also, even though under ubuntu my wifi worked out of the box (although it was a lot more flaky then on Windows 7), I could not get it to work at all under kubuntu, which was what I really wanted to install.

I tried a few other distro to see if it wasn't an ubuntu only issue, and it sure wasn't.

Now I know that you're thinking oh well that's just one model, but I believe it is actually most of the Gateway and Acer models that came out this year, either AMD or Intel, as I have gotten similar results on my sister's Acer which is almost identical to my Gateway.  I should definitely have checked more how compatible it was with Linux, but since I never had to before I forgot to do it.  This is the first computer I've had in the last 5 years that I feel more comfortable on Windows than on Linux, and that makes me sad :(

***EDIT: This thread prompted me to give ubuntu a try again, and going against my previous 5 year mentality I decided to forgo the latest and greatest and give the current LTS a try (10.04) and voila! 0 problems, completely flawless and seamless install...ah the ubuntu I know :)  I guess I'll stick to this release for a while, at least until I know my hardware works perfectly under the new ubuntu.

---

### Post by cariboo on 2011-09-07
> **Neken said:**
> protip: you can't buy wireless cards for most laptops.

How about [these]("http://discountechnology.com/Products/Wireless-Network-Interface-Cards-NIC")?

There are a lot more available from other manufacturers.

---

### Post by dpny on 2011-09-07
> **cariboo907 said:**
> How about [these]("http://discountechnology.com/Products/Wireless-Network-Interface-Cards-NIC")?

There are a lot more available from other manufacturers.

I think you're actually making his point: odds are that with Windows (and definitely with OS X) the wireless card would work OOTB: no need to google or patch a kernel or buy something else.

So long as Linux remains what it is--an open source OS with no centralized control--it will continue to have hardware problems Windows and OS X don't have. Apple and MS collectively employ thousands of people whose job it is to flog hardware to make sure things work OOTB. Linux doesn't have this.

This isn't to say that one is better than the other, but that the development ecosystems of these respective OSes result in different end-user experiences.

---

### Post by el_koraco on 2011-09-07
> **dpny said:**
> 
So long as Linux remains what it is--an open source OS with no centralized control--it will continue to have hardware problems Windows and OS X don't have. Apple and MS collectively employ thousands of people whose job it is to flog hardware to make sure things work OOTB. Linux doesn't have this.


MS doesn't emplov thousands of people to work on drivers themselves, they employ people to work on their driver model and do some work for their generic drivers. The rest is done by manufacturers.

---

### Post by beew on 2011-09-07
> **dpny said:**
> I think you're actually making his point: odds are that with Windows (and definitely with OS X) the wireless card would work OOTB: no need to google or patch a kernel or buy something else.
.


If you google for PC problems most of the hits you get are for Windows, that is a fact. What do you think Windows forums are for? 
Do you believe that usb wireless cards are bought only by Linux users? 

If Windows work out of the box why are there so many third party tweaks even for simple things like unattaching an external drive? (I used to use a thing called "unlocker" or something like that in XP because when you attached an external drive you just can't stop it from Windows) Just switch to Windows 7 at work and printer has stopped working.

---

### Post by ninjaaron on 2011-09-07
It's actually kind of weird to think that kernel developers have to work on drivers at all.  Hardware manufacturers are usually supposed to make sure their **** works with a variety of systems.  While a lot of companies do provide the source for their drivers these days, there are still relatively few that actually port them to Linux themselves.

Then again, that's pretty much what the kernel is.  Just a layer that talks to the hardware, manages it's resources, gets instructions from the programs for the hardware.  Any user environment, including the console shell, is a separate program.  As far as I know, the user never actually interacts with the kernel directly.

I don't know what this has to do with driver support anymore.  I'm rambling.  Bye.

---

### Post by el_koraco on 2011-09-07
> **ninjaaron said:**
> It's actually kind of weird to think that kernel developers have to work on drivers at all.  Hardware manufacturers are usually supposed to make sure their **** works with a variety of systems.  While a lot of companies do provide the source for their drivers these days, there are still relatively few that actually port them to Linux themselves.

Different development models. One of the biggest complaints against Linux, when it comes to proprietary drivers, is the lack of a stable API and ABI that drivers can be written against. Otoh, when dealing with open source drivers, the Linux kernel model makes life easier for hw manufacturers, because all they have to do is get the driver into the main tree, and the kernel guys handle the maintenance. There's an old document by the kernel devs named The Stable API nonsense, which adresses some of this stuff. 

It's questionable whether a change in the model would intice manufacturers to provide better quality proprietary drivers - it would be more similar to the Windows model, so I guess they'd be on more familiar ground, but it's not like a lot of companies employ dozens of people to write Linux drivers - and it's pretty obvious what advantages the model provides for open source drivers, but ya know, whatever.

---

### Post by forrestcupp on 2011-09-07
> **tomazzi said:**
> 
Windows7/Vista/XP (still very popular on older machines):
After long installation not much HW works OOTB, except keyboard, mouse and limitted VGA support, limitted sound drivers (if You have AC97). You have to install each additional driver separately and if You are lucky then maybe it wont be necessary to search for older versions of drivers after it becomes clear that newest are broken (like f.e. Intel WiFi). In case of XP searching for drivers is rather time-consuming task these days, as most manufacturers are not providing them on main dowload sites.I won't argue that installing XP from scratch really sucks. But it began to change with Vista. 

I've installed 7 on a lot of machines. On each different machine, everything necessary worked perfectly out of the box, then when it connected to the internet, it automatically installed working drivers for everything, including my all-in-one printer, and fully working, hardware accelerated video drivers. I'm not trying to argue which is better; I'm just trying to point out that what you said isn't very accurate, except for the XP part.

> **kaldor said:**
> 
Like forrestcupp said, "Even if it's possible, it isn't worth it". Things need to just work or else nobody is going to bother with it. That's the hard fact when dealing with most users.Exactly. There are some things that just aren't worth beating your brains out when it just works easily in the Windows that came installed on my machine. For everything else, Linux is probably better.


> **tomazzi said:**
> OOTB stands for "**O**ut **O**f **T**he **B**ox".
Try linux with internet connection... :)
Try Linux with*out* internet connection. ;) It royally sucks.

---

### Post by dpny on 2011-09-07
> **beew said:**
> If you google for PC problems most of the hits you get are for Windows, that is a fact. What do you think Windows forums are for? Do you believe that usb wireless cards are bought only by Linux users?

And if you read Linux forms you will see an endless list of hardware problems, major and minor. I'm not sure what your point was. 

>  Just switch to Windows 7 at work and printer has stopped working.

No problems with the Windows 7 install at work, or the XP installs, for that matter.

As I said, the hardware issues with Linux are a result of the development model, and are unlikely to go away. Canonical has solved some of them by focusing on making Ubuntu as painless as possible--and it's the most painless Linux install I've seen--but even then, as the forums show, there are many, many problems getting it to work.

There really is no way to avoid this entirely. The only solution is the Apple model, complete control of hardware and software. And, even there, it's not 100% successful.

---

### Post by kaldor on 2011-09-07
> **beew said:**
> If you google for PC problems most of the hits you get are for Windows, that is a fact. What do you think Windows forums are for? 
Do you believe that usb wireless cards are bought only by Linux users? 

If Windows work out of the box why are there so many third party tweaks even for simple things like unattaching an external drive? (I used to use a thing called "unlocker" or something like that in XP because when you attached an external drive you just can't stop it from Windows) Just switch to Windows 7 at work and printer has stopped working.

Of course most problems are toward Windows. Less than 10% of people do not use Windows on a desktop or workstation. If people buy a USB wireless device, it's most likely going to work on Windows... because that's what it was intended for.

I use a few external drives and they all work just fine under Windows 7.

---

### Post by Oxwivi on 2011-09-07
Speaking of USBs, every single model needs to install drivers on Windows. On the other hand, Linux's fantastic generic USB driver means no need to install anything.

---

### Post by dpny on 2011-09-07
> **Oxwivi said:**
> Speaking of USBs, every single model needs to install drivers on Windows. On the other hand, Linux's fantastic generic USB driver means no need to install anything.

Every single model? Mine plugs into Windows and OS X with no problems.

---

### Post by kaldor on 2011-09-07
> **Oxwivi said:**
> Speaking of USBs, every single model needs to install drivers on Windows. On the other hand, Linux's fantastic generic USB driver means no need to install anything.

This is one of the things that drove me absolutely insane on Windows XP. Every time I plugged in a new device (mouse, keyboard, anything) it would freeze up for a while before a window popping up saying something about drivers. I don't remember this ever happening on my new Win7 system.

---

### Post by MG&amp;TL on 2011-09-07
Well, I don't really think that you can say that all the old hardware works, either. my Nvidia graphics card works OK-ish on 10.04 and 10.10, in that it runs 3d-acceleration, but not compiz or anything effects-ish (it seems to be blacklisted :confused: (I gave up on it long ago, don't worry))

But on 11.04 I have to install the nouveau driver (which gives about 1/3 of the performance), or else it doesn't boot. And the nouveau driver kills Unity 3d.

However, on my newer laptop, everything works fine,except for hideously slow internet on 10.10.

Sheesh, we aren't here because it's easy.

---

### Post by forrestcupp on 2011-09-07
> **Oxwivi said:**
> Speaking of USBs, every single model needs to install drivers on Windows. On the other hand, Linux's fantastic generic USB driver means no need to install anything.

What do you mean by USB? Try plugging in a Lexmark All-in-One printer and tell me if the generic USB driver makes it work.

---

### Post by NightwishFan on 2011-09-07
I used Linux for years without an internet connection. Just download a dvd with all the debs/rpms (I bought a boxed OpenSUSE 10.3 DVD). Had all I needed for office work, music work, etc.

---

### Post by beew on 2011-09-07
> **kaldor said:**
> Of course most problems are toward Windows. Less than 10% of people do not use Windows on a desktop or workstation. If people buy a USB wireless device, it's most likely going to work on Windows... because that's what it was intended for.

I use a few external drives and they all work just fine under Windows 7.


Doesn't matter what %, if everything works out of the box you shouldn't be seeing any complaint or problem regarding Windows at all. So the proportional argument fails.

I use a few external drives and they work in WIndows, just that you cannot stop them even when you want to, I am sure I was not the only person with that problem, otherwise no one would have created a program (the unlocker) just for that purpose.

---

### Post by beew on 2011-09-07
> And if you read Linux forms you will see an endless list of hardware problems, major and minor. I'm not sure what your point was. But you claim Windows always work out of the box, so why all the complaints? I never said Linux always does. 

> No problems with the Windows 7 install at work, or the XP installs, for that matter.
So because you don't have problem that means OOTB for everyone?  Just told you we have had no printer since we installed Windows7. Today the technician came to tried to install the driver but still no luck, he said he would come take another look tomorrow, that is not OOTB.

> As I said, the hardware issues with Linux are a result of the development model, and are unlikely to go away. Canonical has solved some of them by focusing on making Ubuntu as painless as possible--and it's the most painless Linux install I've seen--but even then, as the forums show, there are many, many problems getting it to work.It is lack of manufacturer supports, nothing to do with developmental model. Given the lack of support Linux's hardware compatibility is actually quite awesome. I would like to see how well the "WIndows model" would work if the hardware manufactures decide to give them the same level of support as they do Linux.

,

---

### Post by dpny on 2011-09-07
> **beew said:**
> But you claim Windows always work out of the box, so why all the complaints? I never said Linux always does.

Windows works better OOTB on a wider range of hardware than Linux. Just the way it is.

> I would like to see how well the "WIndows model" would work if the hardware manufactures decide to give them the same level of support as they do Linux.

This makes no sense, and doesn't matter.

Linux will always have this issue. It's just the way it is.

---

### Post by NightwishFan on 2011-09-07
> **dpny said:**
> Windows works better OOTB on a wider range of hardware than Linux. Just the way it is.
Citation needed.



> This makes no sense, and doesn't matter.
I guess English isn't your first language. At least I hope that is why you do not understand.

> Linux will always have this issue. It's just the way it is.
I suppose you **are** the expert. Oh wait...

---

### Post by beew on 2011-09-07
> **dpny said:**
> Windows works better OOTB on a wider range of hardware than Linux. Just the way it is.

It is because many hardware manufacturers practically work for MS and the OEMs who do all the testings before they put the computers together. How is that surprising?



> Linux will always have this issue. It's just the way it is.Why? It is just a bald assertion and should be dismissed simply.

---

### Post by dpny on 2011-09-08
> **beew said:**
> Why? It is just a bald assertion and should be dismissed simply.

Because Linux isn't a product: it's a community supported effort. This means:

1) The various groups which produce Linux don't get access to hardware before it's released like Apple and Microsoft do. They have to wait until the hardware is released to work on it;
2) Because it's a community effort there is are no large teams of people working solely on new hardware compatibility as there are with Apple and Microsoft. There are groups of people working on various things, but there is no central, coordinated effort like Apple and Microsoft;
3) There is no one person directing these efforts to make new hardware compatibility a priority. The community sets the priorities, and new hardware compatibility (or old hardware compatibility, for that matter) isn't always the priority.

And so forth.

I'm not saying that the hardware problems in Linux are a bad thing. There are just a by product a community-supported development effort. There are advantages to centralized, corporate OSes like Windows and Apple, and there are advantages to OSS efforts like Linux.

---

### Post by Khakilang on 2011-09-08
> **dpny said:**
> Windows works better OOTB on a wider range of hardware than Linux. Just the way it is.

To my experience Window doesn't work OOTB or has the latest driver. You  need the hardware CD drivers or else it won't work.

---

### Post by NightwishFan on 2011-09-08
> **dpny said:**
> Because Linux isn't a product: it's a community supported effort. This means:
Thank you for winning any semblance of argument for me. Ever hear of Novell, Red Hat, Canonical, Google, IBM, Intel, Microsoft? All of them are contributors to the Linux kernel and some have full time workers paid to do so.

Ever hear of Android?

> 1) The various groups which produce Linux don't get access to hardware before it's released like Apple and Microsoft do. They have to wait until the hardware is released to work on it;
[http://www.linux.com/news/hardware/peripherals/278579-linux-and-usb-30](http://www.linux.com/news/hardware/peripherals/278579-linux-and-usb-30)
[https://secure.wikimedia.org/wikipedia/en/wiki/X86-64#Linux](https://secure.wikimedia.org/wikipedia/en/wiki/X86-64#Linux)

Linux had supported x86_64 in long mode and USB 3.0 before the hardware was even physically available to consumers.
> 
2) Because it's a community effort there is are no large teams of people working solely on new hardware compatibility as there are with Apple and Microsoft. There are groups of people working on various things, but there is no central, coordinated effort like Apple and Microsoft;
Wrong. :P See above.

> 3) There is no one person directing these efforts to make new hardware compatibility a priority. The community sets the priorities, and new hardware compatibility (or old hardware compatibility, for that matter) isn't always the priority.
This may be more of an issue, but it also leads to more of a crowd sourced development model where multiple organizations and individuals can contribute.

> And so forth.
And this is how my story ends....

> I'm not saying that the hardware problems in Linux are a bad thing. There are just a by product a community-supported development effort. There are advantages to centralized, corporate OSes like Windows and Apple, and there are advantages to OSS efforts like Linux.
Then what are you saying? Why not just say this to begin with?

---

### Post by Legendary_Bibo on 2011-09-08
> **beew said:**
> If you google for PC problems most of the hits you get are for Windows, that is a fact. What do you think Windows forums are for? 
Do you believe that usb wireless cards are bought only by Linux users?

Ummm...I think marketshare plays a big role in this...just saying.

> If Windows work out of the box why are there so many third party tweaks even for simple things like unattaching an external drive? (I used to use a thing called "unlocker" or something like that in XP because when you attached an external drive you just can't stop it from Windows) Just switch to Windows 7 at work and printer has stopped working.

I just plugged in my HP Printer (notorious for not working with Windows 7) and I could print stuff. It's a network printer, and Ubuntu at least sees it, but I've yet to figure out to make it print.

---

### Post by dpny on 2011-09-08
> **NightwishFan said:**
> Thank you for winning any semblance of argument for me. Ever hear of Novell, Red Hat, Canonical, Google, IBM, Intel, Microsoft? All of them are contributors to the Linux kernel and some have full time workers paid to do so.

Ever hear of Android?

Install Android on your desktop. Is Android Linux? Yes. Does it count for this thread? No.

Do some companies have people contributing to Linux? Yes. Are those people dedicated to making sure you can install Ubuntu on any laptop? 

No.

> Linux had supported x86_64 in long mode and USB 3.0 before the hardware was even physically available to consumers.

Yet you can't go into a Best Buy, pick a laptop and be sure it will work with Ubuntu OOTB. Once again, support for one piece of tech is not the same as what this thread is about. 

The basic fact: if you want to be sure that your flavor of Linux will run, you need to research the hardware you want to buy.

> Then what are you saying? Why not just say this to begin with?

Because I thought it was obvious.

I'm not saying one OS is better than the other: I don't care. I'm saying that different organizational models will give different results. Apple's strict, top-down integration means that, for the most part, things will just work. Microsoft's massive investment in working with OEMs means that Windows runs on a wide variety of hardware with relatively few problems. And the open source model of Linux means it's free, open and almost infinitely configurable. However, it also means that, depending on your combination of kernel, desktop environment, etc., you may find your wireless card not working, your GPU giving terrible results, or your trackpad deciding it's not interesting in working.

Different models, different results.
Different advantages, different drawbacks.
Different folks, different strokes.

---

### Post by NightwishFan on 2011-09-08
> **dpny said:**
>  Is Android Linux? Yes.
Yup.
> Do some companies have people contributing to Linux? Yes.
Quite so.



> Yet you can't go into a Best Buy, pick a laptop and be sure it will work with Ubuntu OOTB.
I don't shop at Best Buy so I wouldn't know.

 > Once again, support for one piece of tech is not the same as what this thread is about
No it is about "Incompatible hardware becoming largely a thing of the past".

> The basic fact: if you want to be sure that your flavor of Linux will run, you need to research the hardware you want to buy.
Or just buy it from a company that specializes in Linux hardware. They do exist.

> I'm not saying one OS is better than the other: I don't care.
You seem to care a great deal more than I do.

> I'm saying that different organizational models will give different results. Apple's strict, top-down integration means that, for the most part, things will just work.
The existence of Apple tech support says otherwise.


> However, it also means that, depending on your combination of kernel, desktop environment, etc., you may find your wireless card not working, your GPU giving terrible results, or your trackpad deciding it's not interesting in working.
The same is true for any hardware an operating system does not support.

> Different models, different results.
Different advantages, different drawbacks.
Different folks, different strokes.
Different troll same argument.

---

### Post by dpny on 2011-09-08
> **NightwishFan said:**
> Or just buy it from a company that specializes in Linux hardware. They do exist.

So, in order to avoid hardware incompatibility, I should look for a company which specializes in hardware guaranteed to work with Linux?

So we agree.

Let's make a bet: I bet that, in two years, the threads here will still be filled with posts asking how to make hardware work with the then-current Ubuntu.

I like Linux: I screw around with it for no reason other than curiosity. But I'm not required to turn a blind eye to its shortcomings.

---

### Post by NightwishFan on 2011-09-08
> **dpny said:**
> So, in order to avoid hardware incompatibility, I should look for a company which specializes in hardware guaranteed to work with Linux?
That is one option.

> So we agree.
We may agree on some things.

> Let's make a bet: I bet that, in two years, the threads here will still be filled with posts asking how to make hardware work with the then-current Ubuntu.
I am certain there will still be tech support and Windows forums talking about those same issues.

> I like Linux: I screw around with it for no reason other than curiosity. But I'm not required to turn a blind eye to its shortcomings.
Likewise for Windows 7. Only I do not care enough to troll their forums about it. :)

---

### Post by Oxwivi on 2011-09-08
> **dpny said:**
> Every single model? Mine plugs into Windows and OS X with no problems.
Dunno about Macs, but Windows will need to install something the first time, regardless of what kind of device it is. Unlike Linux - if it has support it supports. If it doesn't, well, I'm inexperienced with such hardwares.

> **forrestcupp said:**
> What do you mean by USB? Try plugging in a Lexmark All-in-One printer and tell me if the generic USB driver makes it work.
Well, I admit I wasn't clear, but I was referring to those simple devices, i.e. storage, keyboard/mouse, cameras, etc.

Not my personal experience, but I've read in the forums that some people can't run Microsoft devices on Windows. And other devices, even with operating system support mentioning Windows, it doesn't work.

> **kaldor said:**
> This is one of the things that drove me absolutely insane on Windows XP. Every time I plugged in a new device (mouse, keyboard, anything) it would freeze up for a while before a window popping up saying something about drivers. I don't remember this ever happening on my new Win7 system.
Never freezed for me on XP, but on WIndows 7 they still install drivers the first time around. Only now they look for the drivers on the Internet before complaining of missing drivers.

---

### Post by CarlosFerreira on 2011-09-08
I am afraid it might not all be a thing of the past. A couple of months ago I bought a new laptop (HP g6, AMD quad-core processor) and in went Linux. Plenty of problems with 11.04, both ubuntu and Mint. Both 11.04s eventually crashed and burned, which has led me to revert back to 10.10 (detailed [here]("http://cyclingmonkey.wordpress.com/2011/09/03/adventures-in-ubuntu-3-grief-anger-salvation/")).
I managed to install everything neatly (sound, wireless, graphics), but it is still cranky in places (for instance, does not like waking up from hibernation and the microphone sound is way worse than it was with Natty).
I never managed to install or run Natty off a LiveCD in this particular box; I have always had to install Maverick and update it - sure sign that Not All Is Well. I look forward to Ocelot solving most of these problems.

That said, Linux sure has come a long way. For instance, the first time I tried ubuntu, in the heady days of Hardy Heron, I never managed to get the sound card to work, never mind the video. It's evolving in the right direction, and I hope the evolution goes on.

---

### Post by sdowney717 on 2011-09-08
I have a USB vbox 3560 which no one has written a device driver in linux.
It picks up over the air hdtv broadcasts

[http://linuxtv.org/wiki/index.php/VBox_Cat's_Eye_USB-A_3560](http://linuxtv.org/wiki/index.php/VBox_Cat's_Eye_USB-A_3560)

---

### Post by BrokenKingpin on 2011-09-08
I would say hardware compatibility is largely a thing of there past. Sure, new devices will be released where we may not have support right away, but they usually get support fairly quickly.

Even the hardware vendors themselves are getting better. I bought a Canon printer and I can get Linux divers directly from their website (in .deb format).

That all be said I find that things that use to work fine will sometimes be broken in the next release. The touchpad on my netbook worked fine in 9.10... but 10.04+ the driver has been broken. It is very frustrating because it has been a known issue for for 3 releases, coming up on 4 and it has not been fixed. It is also not just one specific netbook either, it is effects a lot of netbooks.

---

### Post by forrestcupp on 2011-09-08
> **NightwishFan said:**
> I used Linux for years without an internet connection. Just download a dvd with all the debs/rpms (I bought a boxed OpenSUSE 10.3 DVD). Had all I needed for office work, music work, etc.I guess I should have said Ubuntu. Some distros with a large DVD repository are pretty good for offline use.

> **NightwishFan said:**
> Citation needed.If you count the fact that during installation, Windows 7 connects to their server and downloads their own Microsoft drivers for a lot of hardware, I don't think any rationally minded person would need a citation that shows that Windows 7 works OOTB for more hardware than Linux does. There's no reason to *not* count that when you consider that Ubuntu does the same thing and downloads updates during installation.

People make hardware for Windows, then they work their butts off to get WHQL signed drivers for their hardware. That's just how things are. That doesn't take away from the fact that the Linux devs are doing an awesome job working from the ground up to close the gap.

---

### Post by dpny on 2011-09-08
> **NightwishFan said:**
> Only I do not care enough to troll their forums about it. :)

I'm not trolling: I'm offering my opinion. Apparently that's just a bit too much for you.

Anyway, that's enough bandwidth wasted. We'll see where things stand in two years.

---

### Post by NightwishFan on 2011-09-08
> **dpny said:**
> I'm not trolling: I'm offering my opinion. Apparently that's just a bit too much for you.
No, I just like winning arguments. You can't 'hit me where it hurts'. :P

My honest opinion is hardware support is lacking, but no unreasonably so. It is above the curve where I would not consider recommending or adopting a GNU/Linux system (and that is being conservative).

Special care is needed to ensure you have a good experience, but I had not done so and I have no hardware that functions incorrectly. Luck? Of course, but I believe that a good percentage of hardware is detected if I can play lotto and pick hardware that works great.

---

### Post by MG&amp;TL on 2011-09-09
With a great deal of respect, couldn't you people be out helping to write drivers for dodgy hardware, rather than arguing about it? Just a thought...

---

### Post by NightwishFan on 2011-09-09
> **MG&TL said:**
> With a great deal of respect, couldn't you people be out helping to write drivers for dodgy hardware, rather than arguing about it? Just a thought...

Well for Ubuntu at least it is for end-users (consumers). So I suppose hardware working without needing to be a computer hobbyist is the point of this thread.

I only know python. :-(

---

### Post by Oxwivi on 2011-09-09
> **NightwishFan said:**
> Well for Ubuntu at least it is for end-users (consumers).
While I understand you don't know the necessary knowledge to code drivers, using Ubuntu doesn't mean you can't develop drivers. Kinect drivers were shown to be developed on Ubuntu, for example.

---

### Post by NightwishFan on 2011-09-09
> **Oxwivi said:**
> While I understand you don't know the necessary knowledge to code drivers, using Ubuntu doesn't mean you can't develop drivers. Kinect drivers were shown to be developed on Ubuntu, for example.

You misinterpreted my statement. Ubuntu is a fine developer platform.

I said that users of Ubuntu are more justified to complain about hardware since it is not a hobby os and is a product.

---

### Post by Legendary_Bibo on 2011-09-09
> **MG&TL said:**
> With a great deal of respect, couldn't you people be out helping to write drivers for dodgy hardware, rather than arguing about it? Just a thought...

That doesn't sound fun. Making an app for Windows Phone/Android and for the desktops is a lot more fun though.

---

### Post by NightwishFan on 2011-09-09
If I were a low level C/Assembly programmer I would hack on the cpu and io schedulers and not drivers. I also agree that my talents and fun lie more in interface design.

---

### Post by czig49 on 2011-09-09
ive yet to have luck finding a printer/all in one.  that i can  plug and play. my lexmark printer never would work.  my brother all in one, had drivers but to get the scanner to work  someone finally told me how to script it. have never got the wireless part of the all in one  to function.  hopefully when i get my next printer  i can find some kinda list  somewhere that gives me a company and model # that i can walk in buy,go home plug and play.  thanks for bringin the subject up. printers have been my only hang up  since i started using ubuntu.

---

### Post by NightwishFan on 2011-09-09
All in one printers are generally a recipe for failure. I have a HP printer/scanner that works as of the hplip in Debian Testing. (I have to backport it to stable to use the scanner, otherwise the printer works).

---

### Post by czig49 on 2011-09-09
the printer/all in one  thing   is something that i really hope  the brainy ones here  will make changes to. kinda a basic part of computing  imho.

---

### Post by Oxwivi on 2011-09-09
HP printers generally work - it worked for me, the all-in-one as well.

---

### Post by forrestcupp on 2011-09-09
> **NightwishFan said:**
> My honest opinion is hardware support is lacking, but no unreasonably so. It is above the curve where I would not consider recommending or adopting a GNU/Linux system (and that is being conservative).

Special care is needed to ensure you have a good experience, but I had not done so and I have no hardware that functions incorrectly. Luck? Of course, but I believe that a good percentage of hardware is detected if I can play lotto and pick hardware that works great.I totally agree with you there. I just can't agree that Linux has better hardware support than Windows 7 OOTB. But what you're saying here is right on.

> **MG&TL said:**
> With a great deal of respect, couldn't you people be out helping to write drivers for dodgy hardware, rather than arguing about it? Just a thought...Lol. Lol.

So you think all Linux *users* are hardware level Assembly language programmers who are able to reverse engineer drivers for hardware whose specs haven't been released by their companies? The point of making Linux easier to use is so that the many people who don't know how to program can use it. That means that there are now *a lot* of Linux users who don't know how to program at all, even arguing on these forums. ;)

> **czig49 said:**
> ive yet to have luck finding a printer/all in one.  that i can  plug and play. my lexmark printer never would work.
Lexmark sucks for Linux. In the past, I've had Lexmark all-in-one printers that I was finally able to get to print, but nothing else ever worked.

---

### Post by el_koraco on 2011-09-09
Printing. This is the post-PC era, people, printing is so 2009.

---

### Post by forrestcupp on 2011-09-09
> **el_koraco said:**
> Printing. This is the post-PC era, people, printing is so 2009.

As soon as I get a tablet, my printing is going to go way down. The only thing I'll still have to print will be forms that people have to fill out and sign, only to be scanned back into my computer, and then shred the form.

Everything else, I either just save digital copies, or print to pdf, even all of my tax forms.

---

### Post by Oxwivi on 2011-09-09
> **el_koraco said:**
> Printing. This is the post-PC era, people, printing is so 2009.

Yeah, legal procedures and stuff are so yesterday. Certificates and licenses should be digital in this day and age!

---

### Post by el_koraco on 2011-09-09
> **Oxwivi said:**
> Yeah, legal procedures and stuff are so yesterday. Certificates and licenses should be digital in this day and age!

I refuse the jurisdiction of any court that doesn't have a stack of iPads in the chambers!

---

### Post by forrestcupp on 2011-09-09
> **Oxwivi said:**
> Yeah, legal procedures and stuff are so yesterday. Certificates and licenses should be digital in this day and age!

I actually recently told my wife that I wish they'd come up with a way to get your driver's license on your smart phone. :)

At least you can already scan coupons from a smart phone or tablet.

---

### Post by MG&amp;TL on 2011-09-11
I wouldn't know how to write a driver either. I did say 'help to', which is the whole point of open-source and Ubuntu in my opinion, if you can't code, you file bug reports and experience. You could also classify and pre-process those bugs.

Although I agree it's not a  lot of fun. And it was only a suggestion.

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
**[ugg]("http://www.alluggbootsoutlet.com/")** **[ugg boots]("http://www.alluggbootsoutlet.com/")** **[ugg boots outlet]("http://www.alluggbootsoutlet.com/")** **[ugg outlet]("http://www.alluggbootsoutlet.com/")** **[uggs]("http://www.alluggbootsoutlet.com/all-ugg-c-89.html")** **[ugg boots online]("http://www.alluggbootsoutlet.com/ugg-australia-c-88.html")** **[Kid Sheepskin UGG Boot ]("http://www.alluggbootsoutlet.com/kids-ugg-boots-c-46.html")** **[ugg bailey button triplet boots]("http://www.alluggbootsoutlet.com/ugg-bailey-button-triplet-boots-c-80.html")** **[ugg australia]("http://www.alluggbootsoutlet.com/ugg-australia-c-88.html")** **[Kids UGG Boots]("http://www.alluggbootsoutlet.com/kids-ugg-boots-c-46.html")**

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
. Fill the container with clean water and wash it every day or two. The wildlife attracted to the water will depend on where you place the container. Containers set on the ground usually attract the greatest number of wildlife species, from birds and butterflies to squirrels and toads. Hanging birdbaths or ones on pedestals will be restricted to those creatures that can fly or jump high enough to reach the water, and give birds a chance to escape from neighborhood cats and other predators

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
.

But if you're still thinking of on whether or not you actually do need a laptop to try and do your computer-related higher education work, it is advantageous to take into account the vast capabilities worth mentioning travel-ready devices along with your current needs and capacity operate these.Owning an extremely portable workstation can offer you entertainment, productivity and simplicity of use.Forget with regards to long unpleasant cords and additionally mouse shields

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
**[moncler]("http://www.monclerpage.com/")** **[moncler jackets]("http://www.monclerpage.com/")** **[moncler store]("http://www.monclerpage.com/")** **[moncler jacket sale]("http://www.monclerpage.com/")** **[moncler on sale]("http://www.monclerpage.com/")** **[Moncler Women Bags]("http://www.monclerpage.com/moncler-bags-sale-c-2.html")** **[Moncler Bags stroe]("http://www.monclerpage.com/moncler-bags-sale-c-2.html")** **[Moncler Bags stroe]("http://www.monclerpage.com/moncler-bags-sale-c-2.html")** **[buy Moncler Vest women]("http://www.monclerpage.com/moncler-vest-women-sale-c-10.html")** **[buy Moncler accessories]("http://www.monclerpage.com/moncler-accessories-sale-c-1.html")**

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
.

If you dont want to splash out the full whack for the cost of one of these Bronze furnishings you can purchase a replica. These bronze frog animals are perfect for pools and ponds. Giant-sized bronze frogs are even built as customized fountains inside luxurious gardens. Bronze frogs art pieces, mainly because of their color, connote lavishness wherever it may be placed. Either indoors or outdoors, you will surely marvel at how opulent a bronze frog art design may be

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
**[christian laboutin]("http://www. christianlouboutinforever.com/")** **[christian louboutin boots]("http://www.christianlouboutinforever.com/")** **[christian louboutin sale]("http://www.christianlouboutinforever.com/")** **[christian louboutin shoes]("http://www.christianlouboutinforever.com/")** **[loboutin boots]("http://www.christianlouboutinforever.com/")** **[christian louboutin platform]("http://www.christianlouboutinforever.com/christian-louboutin-platform-c-1182.html")** **[Discount Christian Louboutin Sandals]("http://www.christianlouboutinforever.com/christian-louboutin-sandals-c-1179.html")** **[chistian louboutin online]("http://www.christianlouboutinforever.com/christian-louboutin-replica-c-1304.html")** **[dicount christian louboutin dorsays]("http://www.christianlouboutinforever.com/christian-louboutin-dorsays-c-1194.html")** **[christian louboutin outlet]("http://www.christianlouboutinforever.com/christian-louboutin-outlet-c-1307.html")**

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
.Keep your flight tickets form your jaunts and use 3-d block pop ups to include dimensions.Beads, sequins, lace, buttons, tags and chipboard are are just some of the other choices.The list is endless however recipe for victory is knowing where you can draw the set.The quality and volume of embellishments are maturing rapidly and changing just like fast.Don't obtain overwhelmed, remember that even the straightforward things will characterize the memories that you need to capture and remember for a long time

---

### Post by olagaelli on 2011-10-27
> ** said:**
> 
.

Myth number three, businesses are more likely to hire a person with a traditional bachelor degree
Studies show that businesses and employers show little preference for one over another. Generally, simply having completed college is the qualifying aspect that will get you in the door. After that, your qualifications, experience, and personality will land the job. In many cases, applicants who hold an online bachelor degree will impress employers. In getting this degree, it shows that the person had the initiative and drive to gain the education needed and become more qualified for the career they wish to pursue

---

### Post by sffvba[e0rt on 2011-11-04
Due to the amount of spam this thread has received, I decided to close it.


404

---

