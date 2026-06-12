---
title: "Potential User"
date: 2005-04-06
forum: The Cafe
---

### Post by The Producer on 2005-04-06
Hello!

I'm a SuSE 9.2 user at the moment, however, might want to change to a different distro, mainly because I wanted faster upgrades, instead of having to wait until ISO of the new SuSE 9.3 to arrive.

The main things that kept me hooked on SuSE and NLD was YaST....is there something similar to that here in Ubuntu?

Also, I'm going to school for 2D/3D computer animation...and I do my own 3D animations.  I'm a Blender/MAX and soon-to-be Maya user and I want to know how Ubuntu handles these apps (MAX excluded, not available for Linux), and how compatible it is with 3D acceleration in ATI and Nvidia cards, as well as interoperability with Windows2K  and network file sharing. ( A requirement...I use Windows for audio/video editing, Macromedia Flash, and DVD authoring and I need to be able to send my rendered assets over to it)

In SuSE I would constantly be hassled by having to upgrade this or that, or tweak this, or some hardware wouldn't work, and I could never really get any real work done in Linux.  I hope in Ubuntu things are more organized.

Thanks!

EDIT:  BTW, i'm a AMD64 user.

---

### Post by TjaBBe on 2005-04-07
[QUOTE=The Producer]Hello!

I'm a SuSE 9.2 user at the moment, however, might want to change to a different distro, mainly because I wanted faster upgrades, instead of having to wait until ISO of the new SuSE 9.3 to arrive.
[/QUOTE]
First of all, (possibly) welcome to the community!

[QUOTE=The Producer]
The main things that kept me hooked on SuSE and NLD was YaST....is there something similar to that here in Ubuntu?
[/QUOTE]
Second, yes Ubuntu does have a system (called apt), which it inherited from debian linux, to handle packages. It does it's job very well, in fact a lot better then Yast in my opinion! The tool itself is textbased but there is a good GUI interface called Synaptics included in Ubuntu!

[QUOTE=The Producer]
Also, I'm going to school for 2D/3D computer animation...and I do my own 3D animations.  I'm a Blender/MAX and soon-to-be Maya user and I want to know how Ubuntu handles these apps (MAX excluded, not available for Linux), and how compatible it is with 3D acceleration in ATI and Nvidia cards, as well as interoperability with Windows2K  and network file sharing. ( A requirement...I use Windows for audio/video editing, Macromedia Flash, and DVD authoring and I need to be able to send my rendered assets over to it)
[/QUOTE]
I think that whatever programs you used on SuSE should also work on Ubuntu. The difference between distributions is not THAT big, GNU/Linux == GNU/Linux. A distribution's main job is to pack it all together (with slight differences in directory/config organisation and stuff like that), and puts some of it's own programs like apt or Yast in it.
As for windows network sharing, you should just use Samba, like on (in my knowlege) all Linux distributions, to share and mount windows shares.

[QUOTE=The Producer]
In SuSE I would constantly be hassled by having to upgrade this or that, or tweak this, or some hardware wouldn't work, and I could never really get any real work done in Linux.  I hope in Ubuntu things are more organized.
[/QUOTE]
Ubuntu comes with a very good default configuration and should work from scratch on most computers. Ofcourse there always is some tweaking to be done like installing nvidia drivers. But Ubuntu definately minimises this need.

[QUOTE=The Producer]
EDIT:  BTW, i'm a AMD64 user.
[/QUOTE]
Ubuntu comes with AMD64 precompiled packages.

You should definately give it a try, and I hope you will start to love Ubuntu as much as most of us do!

---

### Post by Slapdash on 2005-04-07
Yep, I dont think you will have any problems. Esp, comming from SuSe you will find Ubuntu and Deb packages a breeze.

---

### Post by SquireSCA on 2005-04-07
I came from Suse 9.2 Pro to ubuntu for the same reasons that you are thinking of leaving Suse...  Great distro, but lengthly cycles with a price tag of $90 unless you want to wait even longer for the stripped down free FTP download...

Ubuntu is FAST, and it looks slick.  

However, I personally had trouble getting things to work.  I got DVD playback, but in trying to enable DMA on my drives, I broke the media player.  

I could not get the drivers installed for my 6800GT.  I tried several different ways, nothing worked.

I have a second 250GB SATA drive that houses all of my files, and I had trouble accessing it, although that appears to be a Gnome issue, as neither Suse 9.2(running Gnome 2.6), FC3 or FC4 could access that drive either.  KDE version of Suse automounted it though.

I went back to Suse, but something was wrong with YAST.  It no longer installed RPM files properly.

In the end, I went back to WinXP Pro, as it does everything I need without issue.  Plus I game a lot, so for gaming, Windows is the winner hands-down...

But I may dual-boot the system with ubuntu and keep hacking away at it.  I am sure that sooner or later I will get it going...

---

### Post by hashimoto on 2005-04-07
Ubuntu is based on Debian and uses apt for package management. And I must say I love apt! It is so easy to use.

Blender is available and I have it installed. Not used it much, just curious so can't comment on its advanced features.

"Conditional" welcome and good luck!

---

### Post by The Producer on 2005-04-07
I'm sold.

This distro (Ubuntu Hoary 5) is the quickest installing Linux i've ever used.  Along with a completely working, and stable GNOME 2.10, and USB Key support that works INSTANTLY... =D>  I just wish it had a better looking bootloader. ;-) 

I've decided to replace SuSE 9.2  However, i'm having some slight problems....

During installation, I was never given, or allowed to create a password for root.  :cry:  , which prevents me from making some edits to FSTAB and other files...

Also, I need the kernel-sources and devel packages from some apps that I might need to compile (mplayer, NVIDIA drivers, ndiswrapper, and others...).  I've read in the Ubuntu help file that there is a DVD ISO available that contains a wider selection of packages not on the standard CD ISO.  Would that contain the kernel-source and other relevant devel packages (for both i386 and AMD64) or would I need to get them from other places? 

Thank you!

---

### Post by Gary Powers on 2005-04-07
Ubuntu uses SUDO.  Which uses your basic user password.  Very simple, very easy, very nice!

Gary

---

### Post by TravisNewman on 2005-04-07
> **The Producer]
During installation, I was never given, or allowed to create a password for root.  :cry:  , which prevents me from making some edits to FSTAB and other files...[/quote]
sudo is your new friend  said:**
> 
Also, I need the kernel-sources and devel packages from some apps that I might need to compile (mplayer, NVIDIA drivers, ndiswrapper, and others...). I've read in the Ubuntu help file that there is a DVD ISO available that contains a wider selection of packages not on the standard CD ISO. Would that contain the kernel-source and other relevant devel packages (for both i386 and AMD64) or would I need to get them from other places? 

Thank you!
synaptic package manager has the nvidia driver (nvidia-glx) and kernel sources, though you'll probably only need the headers. You can also get mplayer as well. I'm way too lazy tonight, but in order to find out how to do all this, use the links in my signature.

---

### Post by The Producer on 2005-04-08
Thank you!

I'm finially up and running!

---

### Post by Slapdash on 2005-04-08
Great stuff!.  And.....?? What do you think?

---

### Post by poofyhairguy on 2005-04-08
[QUOTE=The Producer]
Also, I need the kernel-sources and devel packages from some apps that I might need to compile (mplayer, NVIDIA drivers, ndiswrapper, and others...).  I've read in the Ubuntu help file that there is a DVD ISO available that contains a wider selection of packages not on the standard CD ISO.  Would that contain the kernel-source and other relevant devel packages (for both i386 and AMD64) or would I need to get them from other places? 
[/QUOTE]

The best thing to do is open up your /etc/apt/sources.list file up. (with sudo gedit) Then be sure to pound out the CD source, and pound in the universe.

---

### Post by TjaBBe on 2005-04-08
Good! Glad you have joined us!!

---

### Post by The Producer on 2005-04-08
> Great stuff!. And.....?? What do you think?

It's quick and interfaces well with XP, and looks good...execept for the bootloader (compared to others i've seen).  While i'm loading Ubuntu on my notebook i've been searching around for a way to apply a bootloader theme.   Maybe Ubuntu should create one of it's own.  I think the installater should be skinned too...it'll make it seem more welcoming to the non-technical crowd.  Then maybe I can get my parents and gf on Ubuntu... O:) 

Another plus...the community is well organized and isn't full of mean, closet nerds trying to push their little agendas or whatever upon me...this is the most friendly interaction i've had with a Linux community ever since I started! :-D 

Sound is great (5.1 SB Live!...I haven't tested 5.1 playback....yet), video and 3D acceleration is great,  my network works great...and without me having to type "modprobe ndiswrapper" everytime I log in.
USB Keys work instantly, unlike in some other distros...I don't know if it's GNOME/KDE or just the kernel.  Everything was loaded perfectly and properly the first time around in the quickest installation of any OS that i've seen to date.

(My systems:
AMD Athlon 2400+XP
256MD RAM
Nvidia GeForceFX 5200 128MB
17in CRT Monitor
5.1 SB Live! 
CDRW
DVD-+RW
Dlink Wireless Adapter

AMD Athlon 64 3400
512MB RAM
ATI Radeon 9600 64MB
15.4 inch Widescreen LCD
CDRW/DVDRW
6 in 1 Media Card Reader
Firewire 1394
)
The only quirks are icon theme loading problems, problems with installing my printer (Lexmark Z23...would work if I could install the official Lexmark Linux drivers for Lexmark Foomatic Kit.  It gives an error during installation about error in opening RPM files....) and there isn't a good CD/DVD burning application.  I wish K3B would be ported to GNOME.

Over all, this is the best distro i've used, and i'm relatively new to Linux (been involved for about 9 months).  I don't ever intend on getting rid of Windows, mostly because of some apps that I really like (Adobe, Vegas, Particle Illusion, Encore, WMEncoder, etc, etc), and because I don't experience any of the nasty problems that everyone else claim to have.  I thought like everyone else that NLD could possibly one day replace MS as the basic user's desktop...but my mind has been changed....

Once my notebook is running with Ubuntu, i'll be able to get to work enjoying 3D rendering on a 64bit OS!

---

### Post by lordofkhemenu on 2005-04-08
[QUOTE=The Producer]I'm sold.

This distro (Ubuntu Hoary 5) is the quickest installing Linux i've ever used. Along with a completely working, and stable GNOME 2.10, and USB Key support that works INSTANTLY... =D> I just wish it had a better looking bootloader. ;-) 

I've decided to replace SuSE 9.2  However, i'm having some slight problems....

During installation, I was never given, or allowed to create a password for root.  :cry:  , which prevents me from making some edits to FSTAB and other files...

Also, I need the kernel-sources and devel packages from some apps that I might need to compile (mplayer, NVIDIA drivers, ndiswrapper, and others...). I've read in the Ubuntu help file that there is a DVD ISO available that contains a wider selection of packages not on the standard CD ISO. Would that contain the kernel-source and other relevant devel packages (for both i386 and AMD64) or would I need to get them from other places? 

Thank you![/QUOTE]
If you REALLY want an enabled root account w/ password, do the expert/advanced install option. I did that the first time around. 
But after dealing with the frenzied prompting and mind numbing options options presented (I *understood* it, but reminded myself I didnt want to *deal* with it anymore), decided just to go with the flow when I did my final hoary full install (something like hoary array 3 or 4, can't recall)...been using hoary happily ever since, SUDO/no root and all.
Somewhere in the Wiki, I saw instructions on how to make a perty boot splash instead of the fugly text-only.

---

### Post by UbuWu on 2005-04-09
[QUOTE=The Producer]It's quick and interfaces well with XP, and looks good...execept for the bootloader (compared to others i've seen).  While i'm loading Ubuntu on my notebook i've been searching around for a way to apply a bootloader theme.   Maybe Ubuntu should create one of it's own.  I think the installater should be skinned too...it'll make it seem more welcoming to the non-technical crowd.  Then maybe I can get my parents and gf on Ubuntu... O:) 
[/QUOTE]

A graphical installer and a graphical bootsplash (usplash) are plannen for the next version which you will have to wait for for 6 more months...

[QUOTE=The Producer]
The only quirks are icon theme loading problems, problems with installing my printer (Lexmark Z23...would work if I could install the official Lexmark Linux drivers for Lexmark Foomatic Kit.  It gives an error during installation about error in opening RPM files....) and there isn't a good CD/DVD burning application.  I wish K3B would be ported to GNOME.[/QUOTE]

Have you tried gnomebaker yet?

---

### Post by The Producer on 2005-04-09
Excellent...this is exactly what I invisoned!  Thanks!

Everything is just fine now...except for some problems in Blender on Ubuntu 64-bit...
(this Blender version is 32bit ATM...)
./blender
./blender: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

That file is present..in /usr/lib.  It points to libSDL-1.2.so.0.7.1.

Is this where the libSDL-1.2.so.0 file should be?

---

