---
title: "Not fun"
date: 2007-06-28
forum: Testimonials &amp; Experiences
---

### Post by oohal on 2007-06-28
In short, my experience with feisty was a pain.

The problems began with the livecd, after booting into GNOME I noticed two things:
1. For some strange reason ubuntu decided not to use DHCP to get an address for my ethernet card, but had a usb1 and wlan0 marked as active interfaces (according to ifconfig) even though I don't have a USB network device or a wireless card.
2. The default screen refresh rate in X was 60Hz, which makes my eyes bleed (This is might just be an X issue).

After dropping to a console and fixing these, I started up the installer only to have it hang while trying to partition the hard drive. After rebooting (and fixing the above issues again) then trying to partition and create the filesystems manually, I ran into a brick wall when mke2fs (ext2/3 filesystem creation tool) told me the filesystem was mounted, dispite the fact there was no FS to mount. At this point gave up on feisty and used a debian livecd to partition the drive. After this the install went fine.

Booting in to my new feisty install (X was fine, seems the installer copied my edited xorg.conf from the livecd, yay for that) and fixing the network (same problem as with the livecd), I tried to get the binary nvidia driver up and running, but the Restricted Drivers manager didn't seem to want to cooperate, so I edited xorg.conf manually and loaded the kernel module only to have X crash on me because the installer had neglected to install the Xorg driver, dispite the fact it installed the kernel model. After reverting to the "nv" driver and restarting X, the Restricted Drivers manager decided to start cooperating and installed the Xorg driver for me.

With all that sorted, it was just a matter of waiting for updates to download (all 68 of them) then installing some software to make my new install useful to me (irc client, gcc, etc) and fixing the network issue permanantly.

All up, it was about 3 hours of screwing around trying to get various things to work. I can't see why it was an issue at all since i've had Dapper and Kubuntu Edgy run flawlessly in the past (except for that broken X update ;)).

-oohal

---

### Post by weblordpepe on 2007-06-28
Holy cow what a nightmare. My Fiesty install was no where near that rough.
Glad you got it sorted though. 
I do agree about the updates thing - there should be like a monthly archive of debs or something you can download along with Ubuntu. Like a monthly service pack or something. In between new OS releases.

---

### Post by wolfen69 on 2007-06-28
it's wierd, some people have the best possible experience when installing (me included) and for others it can be a pain. go figure. at least you got it sorted. you can always go back to edgy if feisty gives you fits.

---

### Post by weblordpepe on 2007-06-29
<windows-troll> HaH sEE IWNDOWS IS SO MEUCH BETTER COZ IN LIMUCKS U HAVE ALL THESE PROBLMS WITH STUFF
</windows-troll>

At least when poo hits the fan with Linux, it is an open system and you can get assistance. There's been many times when XP/2K/98 hit the fan and I was using the command line. It was a nightmare  having to just fumble about aimlessly.

---

### Post by DjBones on 2007-06-29
you're workin with the wrong distro buddy,
if you wanted an easy install you'll have to head over to those gentoo people ;)

---

### Post by weblordpepe on 2007-06-29
I heard Gentoo was real good but you gotta spend ages installing stuff after the OS is installed.

---

### Post by jbaerbock on 2007-07-08
Well you are working with the right distro just not the right version. Give Linux Mint a try. They have a sexy start menu and have some programs pre-installed to help you with your problems. They have Envy which auto installs any ATI or Nvidia drivers you need (run it twice if it does not work first time). Then it has a GUI version of ndiswrapper so you can get a windows wireless driver up in no time. Plus it has all the codecs and DvD playback issues fixed (come loaded so everything works). Most of the time remmember that there are GUI programs that can help you better than if you did it via console. Envy for Graphics drivers, Ndiswrapper GUI's (a few versions out there) for wireless drivers, and I'm sure you can find many other things too. Sorry if this is all a repeat for you.

It took me a few installs to get everything figured out too but since I'm a computer Geek it was more fun than frustration. I now have WinXP/Linux dual boot. Use Linux for everything, but use windows for the more 3D intensive games and ones that only run in windoze.

---

### Post by 3rdalbum on 2007-07-11
You probably should've tried the Alternate CD - it uses the Debian installer, which is much more stable than Ubuntu's live CD installer (Ubiquity).

But hey, I'm sure you'll enjoy your Debian system.

---

### Post by jbaerbock on 2007-07-11
That's ok I got sick of Linux constantly breaking on me (all distros) and I like 3d intense games too much and Linux doesnt like my ATI card much plus WoW isnt supported there. So I am back to winXP, maybe go with a Mac someday or see in the future if Linux makes headway.

---

### Post by 3rdalbum on 2007-07-12
> **jbaerbock said:**
> That's ok I got sick of Linux constantly breaking on me (all distros) and I like 3d intense games too much and Linux doesnt like my ATI card much plus WoW isnt supported there. So I am back to winXP, maybe go with a Mac someday or see in the future if Linux makes headway.

If you like intense 3D games, you won't have much joy with the Mac I'm afraid. Linux is constantly blazing trails, so keep a partition set aside for Ubuntu. Disk space is cheap.

---

### Post by mr_biggie on 2007-07-12
i dont like mint linux. i find their start menu depressing and a little bloated, and envey just doesnt work for me at all. now ubuntu ultimate is a whole different ball game, its ubuntu made pretty, try it i like it

---

### Post by jbaerbock on 2007-07-12
I still have a place in my heart for Linux and always will. I look forward to the day Linux has good game emulation software and good drivers for my graphics card. And I have tried Cedega without luck.

---

### Post by jbaerbock on 2007-07-12
Looks to me like ultimate added some packages, a custom repo, and some pretty themes and that is about it. Mint has all the java, flash etc... plus if you do not like the slab menu like I do, it is simple to remove it and put in the normal Gnome Menu.

---

### Post by ageilers on 2007-07-12
What WOW not supported? My brother-in-laws are over at my house everyday hogging my PC because of WOW on Wine. Nvidia card helps.

Sorry to hear you had so much problems with installing. I have had little problems with installing/using Ubuntu. Those problems I have had, my firiends here at the forums have been very helpful with  (and Google). I definately won't argue over the price. ;)

---

### Post by weblordpepe on 2007-07-12
Yeah I just recently gave an Ubuntu 7.04 disc to my work colleague to try cos he was nosey. He asked if I would be on MSN that night to give him a hand. All I did was tell him that 'Gaim' was the program that you use to connect to MSN.

And what do ya know- a dude with no linux experience at all popped up on my MSN list saying 'hey guess what im in linux!'

After a bit of a walk in the park, he said 'im sold!'. I said well the cost is the icing on tha cake: $0

---

