---
title: "Is Ubuntu too fat?"
date: 2007-05-21
forum: The Cafe
---

### Post by angryfirelord on 2007-05-21
I've noticed on many numerous Linux forums that when Ubuntu comes up in the conversation, they mention that it has become rather bloated.

Unfortunately, I think they're right.

For example, the first linux distro that I got serious about was Ubuntu Dapper. It was speedy, easy to use, and helped me to understand linux better.

Then, Edgy came along. Boot up times were faster, but general usage was slower. However, given the 4 month window it was developed in, I let it go.

Feisty, however, IMHO, wasn't as fast as the Ubuntu devs said it was. Sure, it had all of the shiny new packages, but it was slow. Not suse slow, but slow enough to be annoying. 

Now, I understand that there are people who don't agree with me and I welcome any comments that disagree, but I think Ubuntu needs to focus more on the Debian model of things, which follows the standard Linux model. You don't have to sacrifice usuability, but just don't cram as much stuff in there! Also, I'd like to see more Debian compatability, which would make the Debian devs happy.

For those whom I've offended, I'll probably still be using Ubuntu for a while anyway.

[/rant]

---

### Post by juxtaposed on 2007-05-21
I don't want ubuntu to try and be just like debian (they're both good, but for different things), but I don't know.

I've heard alot about ubuntu loading alot of unneeded modules just in case, which is odd; it should detect which ones are actually needed.

---

### Post by Ziox on 2007-05-21
I've pretty sure that the developers will soon figure out a way to balance speed with features.  In my opinion, they are currently testing out new features that might cause some system slow down.

According to Wikipedia (lol), there might soon be a branch dedicated to explicit bleeding-edge packages, (like debian with one stable branch and one unstable branch).  So hopefully as the features are tested and modified and streamlined, Ubuntu versions will be more balanced, and faster.

P.S.  The installation disc still fits on one disc. :)

---

### Post by Polygon on 2007-05-21
There are reports that ubuntu loads a lot of extra modules and programs to make sure that the distro works for everyone (or most everyone), but for me at least the distro is still as fast (or maybe even faster) then it was in breezy/dapper/edgy. 

Sometimes its just nautilus that is slow, and you can speed this up again by deleting the contents of a few folders. I forget the other ones, but i know if you delete ~/.thumbnails, it can help quite a bit.

---

### Post by Nikron on 2007-05-21
Same with me, Ubuntu feels bloated.  My new primary disto, Arch isn't much faster outside of bootup times(which is like ~12 seconds), but everything is so slimmed down exactly what I need, and it feels good.

---

### Post by Ziox on 2007-05-21
> **Polygon said:**
> There are reports that ubuntu loads a lot of extra modules and programs to make sure that the distro works for everyone (or most everyone), but for me at least the distro is still as fast (or maybe even faster) then it was in breezy/dapper/edgy. 

Sometimes its just nautilus that is slow, and you can speed this up again by deleting the contents of a few folders. I forget the other ones, but i know if you delete ~/.thumbnails, it can help quite a bit.

I do agree that sometimes it is the software that is slowing the system down.  XFCE flies.

---

### Post by CSMatt on 2007-05-21
I'm glad that I'm not the only one to notice this.  It seems that a Feisty installation of Xubuntu using Wubi claims to need  5 GiB of space.  Why does it need that much space?  Even Dapper needed at least 2 GiB, yet it really doesn't seem to actually need that much space.  I've reserved a 10 GiB partition explicitly for Ubuntu (/home is on another partition) which I installed Dapper on.  Two upgrades and a handful of extra packages later, I still haven't even come come close to using half that amount of space.  This is compared to my 20 GiB Windows partition already passing the halfway point despite the minimal amount or programs and all of my personal data being in the /home partition.  This is problematic for me because I want to use Ubuntu on my two desktops which are both low on disk space.  Using Ubutnu on my laptop is not a problem because I could install a dual-boot system right away upon purchase and the lack of existing files and the presence of a 100 GB hard drive made this easy.  My two other computers have been in use for years and either have enormous quantities of data or a small hard disk (the older unit can only hold 10 GB).  I want to create a dual-boot system with Wubi so that I don't have to partition (something that isn't a problem on an almost bare disk) due to the already limited amount of space I have.  However I have found that I cannot do this, and because Wubi doesn't support earlier versions, I can't see if they will leave a smaller footprint.

One of the claims for using GNU/Linux is that it can run on old systems better than most versions of Windows, yet with such a large footprint I find it difficult for Ubuntu to live up to that claim.

---

### Post by angryfirelord on 2007-05-21
> **Ziox said:**
> P.S.  The installation disc still fits on one disc. :)
Ah, that's one thing I really appreciate about Ubuntu. Aside from Knoppix, there's not really that many installable Debian Live CDs, so having it fit onto one disc saves download time.

In terms of slow, it's still acceptable, but the modules thing seems to be the #1 complaint. You can still have Ubuntu load all of the modules at install, detemine which ones are needed, and then deactivate the rest. When someone installs a new piece of hardware, that appropirate module is found and loaded.

Now this is a relatively small complaint. If it weren't for Ubuntu, I'd probably still be sitting on the Windows XP install.

---

### Post by starcraft.man on 2007-05-21
Call me easy going, but I don't mind. I mean raw speed just isn't important to me, and I don't think its really that much of a priority to most people. Ubuntu is stable for me (except the odd crash cuz of Beryl), it is supported well (by this forum), it has plenty of software that suits my needs, it looks and does exactly what I want it to, and it doesn't require any maintenance from me really. All that, makes me a happy camper (as I think it does others). I think I can wait an extra second for it to open firefox or OpenOffice if thats what I have to give up out of my day for a great OS. >.>.

Not to mention, if raw speed is all we want out of an OS, why do we bother with superfluously good looking window managers (gnome, kde, beryl, compiz), we should all just use xfce or a lesser demanding one to shorten all times. Once you start splitting a hair, how fine/far are you willing to spit it?

---

### Post by CSMatt on 2007-05-21
One thing I would like to see is the ability to have a minimalist install where packages that are at the moment necessary (Evolution comes to mind for me, being a Thunderbird user) be completely optional.  Just like you can install stuff into the LiveCD environment and expect it to be copied to the hard disk upon install, I want to see the installer give you the option in some advanced mode to deselect default packages so that they never show up on the disk in the first place.  I realize that this will require a lot of reconfiguring of dependencies, but I don't see why this can't be done.

---

### Post by jerrylamos on 2007-05-21
Out of curiosity, does it help speed to go to System, Administration, Services and un-select things you don't think you'll need?

As far as running speed, CD Live Puppy Linux fits all within memory so once loaded it doesn't have to do any disk accesses.  When you shutdown it gives you options of saving setup, package, files, yata yata on: USB pen drive, a file in XP (yes, NTFS), a file on an installed Linux partition, or even on the rest of the R/W CD/DVD.  The next boot will look for the Pup_save file so boot can be a little slow, but if you used a removable media you can go to another computer and have all your files & setup with you.

Anyway I do applications & internet & photos & LAN file sharing, no games, so this 1.2 GHZ Celeron runs fine for me on this Feisty partly upgraded to Gutsy.

Cheers, Jerry

---

### Post by MetalMusicAddict on 2007-05-21
I, for one, (so far) don't see it. The amount of apps hasn't skyrocketed since Warty. Mostly some switches but for the most part the core app list has remained the same.

---

### Post by Medieval_Creations on 2007-05-21
I too have noticed some slowness.  This isn't entirely the fault of the developers, because the balance of performance vs functionality is difficult and they have little control over 3rd party apps I would imagine..

I agree with andryfielord.  It's not so much the we have to have a screaming machines, I just don't like wasting resources on unneeded services, programs, and the like.  Personally that's one reason I left Winbloze.

I think it's been touched on in an earlier post, but I think would be plus to take a page from the Red Hat / Fedora book in regards to the installer, by giving the user options of what progs we want installed as setup.  I'm always trying to find ways to trim down my install and what is running.  I'm waiting to see how the first release of fluxbuntu does.  I don't need all the eye candy.  I just want a clean, responsive desktop.

---

### Post by justin whitaker on 2007-05-21
I've always felt that Ubuntu needed a little diet, but after using Feisty daily, I understand there is a tradeoff between being accessible and being quick. I could remedy the bloat by doing a server install and going the fluxbox/icewm/low memory route...but Ubuntu is nowhere near as slow on my machine as other leading distributions, particularly the RPM based ones like Mandriva, PCLinuxOS, Fedora, etc. Compared to them, Ubuntu FLIES.

Still, nothing is faster than Arch, except Puppy and DSL. I do not know if I would like to use any of those as my daily desktop.

---

### Post by ThinkBuntu on 2007-05-21
It fits on a single disc...how could it be bloated?

---

### Post by juxtaposed on 2007-05-21
> Not to mention, if raw speed is all we want out of an OS, why do we bother with superfluously good looking window managers (gnome, kde, beryl, compiz), we should all just use xfce or a lesser demanding one to shorten all times.

Most people just don't want unnessecary slowness. There are alot of people who don't like fancy DEs though, and they want even less unnessecary slowness.

---

### Post by justin whitaker on 2007-05-21
> **ThinkBuntu said:**
> It fits on a single disc...how could it be bloated?

Compared to something like....well, let's take Slackware as an example. I can install Slackware with a basic desktop and have a smaller, faster, and more responsive desktop with fewer dependencies....but you lose that plug and play, GUI for almost everything friendliness of Ubuntu. I don't ,mind dipping into the text files now and then, but the trade-off is not really worth it on a daily basis. I'd rather take a slight performance hit for some ease of use.

---

### Post by mrazster on 2007-05-22
Well, I fully agree that Ubuntu feels a little bloated "right out of the box"....but I also think that the balance between speed and usability /compatibility is a very thin line and hard to walk on.
Most distros get either very usable but bloated or very fast but harde to get runing the way you want.

And since Ubuntudevs and Mark are aiming to get Ubuntu more and more desktop ready, I belive it's hard to not make Ubuntu bloated.

Now, there is cure for this. IMHO thoose of us that think there is to much crap "right out of the box", have enough knowledge/expirience to do a slimer/lighter X/K/Ubuntu install.

Simply just do a server/cli install then add whatever packages you want/need thru apt. and there you go....you`ll have an OS with only the packages off your choice...it less recourse hungry and takes less place on hdd. And as for boot time...there are loads of howtows out there to tweak your boot.

I consider my self very much a noob...and I recently did it with "xubuntu". Just did a CLI install and went a head with installing *xorg, xfce4, synaptic e.t.c* ...and when enterng my X I keppt installing whatever packages I needed to get everything running.
I can virtualy feel the difference. Takes a bitt longer to set it up..but you get it the way you want.

---

### Post by zgornel on 2007-05-22
> **justin whitaker said:**
> Compared to something like....well, let's take Slackware as an example. I can install Slackware with a basic desktop and have a smaller, faster, and more responsive desktop with fewer dependencies....but you lose that plug and play, GUI for almost everything friendliness of Ubuntu. I don't ,mind dipping into the text files now and then, but the trade-off is not really worth it on a daily basis. I'd rather take a slight performance hit for some ease of use.

I have to agree. The days when everything had to be done manually are long gone and I hope they will never return.
I do not know what this bloatness complaint is about, it's like people are using 4 gb drives. Furthermore, the amount of software installed does not necesairly affect the system performance (unless you're installing daemons like crazy). One way of dealing with the 'bloatness' is to manually uninstall what is not needed. Personally, I'd make a 10 GB distro so I won't have to install anything again.

---

### Post by MOS95B on 2007-05-22
This being my first real Ubuntu install (I dual booted a previous version for a little while, but didn't keep it long) I can't compare it to "before".  But I think my Thinkpad R51 is pretty quick "out of the box".

I've gone in several times to remove unnecessary programs (the phone program, etc), but every time I do, I find something else cool to install.  So, even after bloating it myself, my machine still runs a lot quicker than it did with Windows.

So, I think the Dev's have done a good job of ensuring functionality and fluff in this install.  But, adding one step, similar to the Windows Custom Install, might not hurt.  I personally don't need or want all the chat, VoIP, etc.  But they aren't hurting anything either.

---

### Post by angryfirelord on 2007-05-22
I tried the server install, but that still doesn't allow you to customize packages. Maybe in the server or alternate cd, there could be a package selection like in Debian's netinst. I would keep the desktop installer the way it is because most people who 1st try Ubuntu are unfamiliar with the environment.

Ubuntu is still an excellent distro and I will keep recommending it to people who want to try linux. :)

---

### Post by PatrickMay16 on 2007-05-22
"angryfirelord", I agree with you. Ubuntu is becoming very bloated. On my laptop, Edgy used almost 200MB of RAM just sitting at the gnome desktop after booting and logging in. Really crazy. After some tweaking I got it down to 135MB RAM, but that's still a lot more than Dapper used.

---

### Post by ThinkBuntu on 2007-05-22
I believe that, from the Linux perspective, it may be bloated. If I'm steering clear of "bloat," the heaviest distribution I'll install is Zenwalk, and to really build my system from the ground-up, I'll use the Arch Base, which is a superb implementation of Linux basics.

But Ubuntu isn't competing for those who like to build their system from the ground-up. That's what Slackware, Gentoo, Arch, and Debian net-install are for. Ubuntu competes with the likes of Fedora, openSUSE, Sabayon, Mandriva, PCLOS, Windows, and Mac OS. By these standards, it's far from bloated. And I don't necessarily mean that as a compliment.

When I install OS X, I immediately have a full-featured music player, photo app, movie app, and a whole bunch of other useful stuff. Now, I'm not much of a video editor, I only use iPhoto to organize pictures (before I used Linux as my main computer), so a lot of this IS bloat to me. But for many users, this is a draw.

Give me OpenOffice and GIMP over 300MB iPhoto and who-knows-how-large iMovie/iDVD any day.

---

### Post by jrusso2 on 2007-05-22
Do I look fat in this distro?

I have been hearing about Linux getting bloated since 1996 When I started.

---

### Post by Rashid584 on 2007-05-22
I've been trying Sidux for the last couple of days...I never thought ubuntu was bloated before but after using sidux, it definitely feels it!

The problem is...I don't think I'd use sidux as a production machine...its very nice. Mad quick and has some nice touches, but I just didn't find it as stable as (K)ubuntu...and the main gripe I had...the fonts. Sorry, but they are absolutely hideous...I tried different anti alias settings in kcontrol but nothing was as nice as Kubuntu. Sidux fonts are horrible and that alone is enough for me to not use it :p (I switched from suse to ubuntu because of messed up fonts...back in days of 9.2 :p)

Its annoying because I'll be sticking with Ubuntu/Kubuntu because of its stability and polish (rather than "easy to use desktop" because I'm comfortable with a console and text files, though things like restricted drivers manager are very cool)..

...hmm, maybe I'll do an alternate kdecore install sometime...gotta find a nice tutorial for that.

-Rashid

---

### Post by Anthem on 2007-05-22
OpenOffice has always been a hog.  MS Office 2003 is much leaner and quicker than a standard OO.o install.  I know everybody hates Microsoft, but that doesn't change the fact that OO.o is pretty slow in most cases.

---

### Post by ThinkBuntu on 2007-05-22
> **Rashid584 said:**
> I've been trying Sidux for the last couple of days...I never thought ubuntu was bloated before but after using sidux, it definitely feels it!

The problem is...I don't think I'd use sidux as a production machine...its very nice. Mad quick and has some nice touches, but I just didn't find it as stable as (K)ubuntu...and the main gripe I had...the fonts. Sorry, but they are absolutely hideous...I tried different anti alias settings in kcontrol but nothing was as nice as Kubuntu. Sidux fonts are horrible and that alone is enough for me to not use it :p (I switched from suse to ubuntu because of messed up fonts...back in days of 9.2 :p)

Its annoying because I'll be sticking with Ubuntu/Kubuntu because of its stability and polish (rather than "easy to use desktop" because I'm comfortable with a console and text files, though things like restricted drivers manager are very cool)..

...hmm, maybe I'll do an alternate kdecore install sometime...gotta find a nice tutorial for that.

-Rashid
For a light install with nice-looking fonts, use an Arch base and use KDEmod. Very nice! I used it for a week, but came back to Ubuntu because I'm too lazy (or, mor accurately, I prefer to spend my time actually doing work, not to say that Arch is anywhere near Gentoo. It just takes a little time to get the right fit).

---

### Post by loathsome on 2007-05-22
Ubuntu isn't bloated at all.

Even though it was bloated, it's so easy to uninstall / configure everything to suit exactly your needs.

---

### Post by Rashid584 on 2007-05-22
> **ThinkBuntu said:**
> For a light install with nice-looking fonts, use an Arch base and use KDEmod. Very nice! I used it for a week, but came back to Ubuntu because I'm too lazy (or, mor accurately, I prefer to spend my time actually doing work, not to say that Arch is anywhere near Gentoo. It just takes a little time to get the right fit).

I'm considering that...

What I wanna know though is whats responsible for the awful fonts in sidux, and the nice ones in kubuntu...and kdemod for that matter. Is it some sort of package, library, setting, or what? Something to do with the kernel even??

I dunno...but I wanna find out :D

-Rashid

---

### Post by ThinkBuntu on 2007-05-22
> **loathsome said:**
> Ubuntu isn't bloated at all.

Even though it was bloated, it's so easy to uninstall / configure everything to suit exactly your needs.
I've found uninstalling to be a bit difficult, myself. Why, for example, does "ubuntu-desktop" depend on something as trivial as "ubuntu-sounds"? I ran into this when trying to swap the Ubuntu Studio sounds for the plain Ubuntu ones yesterday.

---

### Post by Medieval_Creations on 2007-05-22
> **ThinkBuntu said:**
> I've found uninstalling to be a bit difficult, myself. Why, for example, does "ubuntu-desktop" depend on something as trivial as "ubuntu-sounds"? I ran into this when trying to swap the Ubuntu Studio sounds for the plain Ubuntu ones yesterday.

I've run into similar problems and the reverse.  Where even doing a custom install from the alternative CD for some reason some things are overlooked when programs are installed.  An example, I did a command line install, installed xorg, fluxbox, alsa & synaptic.  When I opened synaptic none of the icons were there (the checkboxs marking for installation).  This was a minor, but just little things like that, make it frustrating.

I still plan on sticking with Ubuntu.  It's is by far one of the best distro's out there right now.  I would just like to see an option as to what services/applications are installed at setup.

---

### Post by Rashid584 on 2007-05-22
> **Rashid584 said:**
> I'm considering that...

What I wanna know though is whats responsible for the awful fonts in sidux, and the nice ones in kubuntu...and kdemod for that matter. Is it some sort of package, library, setting, or what? Something to do with the kernel even??

I dunno...but I wanna find out :D

-Rashid

Just in case anyone else using sidux is interested...I found a really cool fix for the font issue in sidux (thanks for members in the great #sidux irc channel :D)

See [http://techpatterns.com/forums/about736.html](http://techpatterns.com/forums/about736.html)

Just skip most of the first steps until it asks you for fix-font, then select that, let it to its ting, then restart kde :D

-Rashid

---

### Post by diskotek on 2007-05-22
> **Polygon said:**
> Sometimes its just nautilus that is slow, and you can speed this up again by deleting the contents of a few folders. I forget the other ones, but i know if you delete ~/.thumbnails, it can help quite a bit.

how we can delete items in nautilus.. for wxample, when i right clicked i saw few apps. that they are not existing anymore.

---

### Post by Enverex on 2007-05-22
I think you're kinda missing the point. Ubuntu IS fat, that's the point. It's Debian with EVERYTHING thrown in to try and make Linux easier to use for the "Average person". If you remove all the fat from Ubuntu you're just left with Debian.

---

### Post by angryfirelord on 2007-05-22
Ok, so we seem to be in agreement that things can be removed. My question to you all is, what should be removed? (besides unnecessary packages) I've never unloaded any modules and as Medieval_Creations stated, removing ubuntu-desktop does cause issues.

---

### Post by Enverex on 2007-05-22
> **angryfirelord said:**
> Ok, so we seem to be in agreement that things can be removed. My question to you all is, what should be removed? (besides unnecessary packages) I've never unloaded any modules and as Medieval_Creations stated, removing ubuntu-desktop does cause issues.

Seriously, if you intend to do this then just switch to Debian.

---

### Post by cotcot on 2007-05-22
Depends on the hardware.
I have gentoo 64 bit and feisty 32 bit on the same box with an amd64x2. Sure there is a big difference in speed but not on an annoying level. 

I am awaiting the time that 64 bit is default.

---

### Post by Rhox on 2007-05-22
The only simple (and by simple I mean like dee dee dee) thing you could do is uninstall runtime libraries.

---

### Post by macogw on 2007-05-22
Yes, it's bloated.  Why is it that when I try to uninstall the bluetooth stuff (bluez-utils) it wants to remove ubuntu-desktop?  That shouldn't be a dependency!  It can "suggest" but it shouldn't be required in order for me to keep the meta-package (which you do kinda need to upgrade correctly).   I don't have bluetooth on my computer.  Why should I need that?  And Ubuntu installs ALL video drivers by default.  ALL OF THEM!  Again, WHY?  I don't need all this:
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-cyrix
xserver-xorg-video-dummy (wtf is the point of a "display driver that doesn't display anything"?)
xserver-xorg-video-glint
xserver-xorg-video-i128
xserver-xorg-video-i740
xserver-xorg-video-imstt
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-newport
xserver-xorg-video-nsc
xserver-xorg-video-nv
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-tga
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-vesa
xserver-xorg-video-vga
xserver-xorg-video-via
xserver-xorg-video-voodoo

Probably also don't need xserver-xorg-video-vmware since this isn't running inside a VM (though idk maybe it needs it to run other stuff inside a VM....kinda doubt it though).

Why doesn't the installer ONLY install what your hardware needs?  I don't have 30 video cards.  I have one.  It uses xserver-xorg-video-i810, and that's it.  Why are the rest even installed when that hardware isn't present?  The installer needs to get smarter.  It should detect what hardware you have and only run that.

Also, given the problems people have had with nm-applet/network-manager, why not have that only install when you have a wireless card that actually works with it?

Why is VNC software part of a default install?  NTP isn't in by default.  You click "okay, download and install it" when you first tell the clock to sync with time servers.  Why can't VNC be like that?  The first time you tell it you want to have remote desktop available, it should prompt you and offer to install VNC stuff.  

Desktop effects installed by default is fine.  However, you should be able to remove it without removing ubuntu-desktop.

There's a lot of stuff that shouldn't be in by default but should have prompts to install if you try to activate it (like the VNC stuff) the way NTP support and codecs act.  There's a lot of stuff that shouldn't install unless your system requires it (30 spare video drivers, bluetooth, wireless, probably more).

---

### Post by macogw on 2007-05-22
> **Enverex said:**
> I think you're kinda missing the point. Ubuntu IS fat, that's the point. It's Debian with EVERYTHING thrown in to try and make Linux easier to use for the "Average person". If you remove all the fat from Ubuntu you're just left with Debian.

Not really.  Ubuntu can make it easier without being fat.  It doesn't need to install stuff to run hardware you don't have.  It can leave some stuff not-installed and then prompt if you try to activate it.  It doesn't need to be FAT though.

---

### Post by Rhox on 2007-05-22
> **macogw said:**
> Why doesn't the installer ONLY install what your hardware needs?

So you don't waste time downloading or deleting stuff. Also so you don't need an internet connection.
edit: nvm

---

### Post by Rhox on 2007-05-22
> **macogw said:**
> (which you do kinda need to upgrade correctly)

You should be able to upgrade just fine without it.

---

### Post by macogw on 2007-05-22
> **Rhox said:**
> So you don't waste time downloading or deleting stuff. Also so you don't need an internet connection.
edit: nvm

If your hardware doesn't need all those spare drivers, why would you waste time downloading them?  There'd be no point because you don't need them.  Instead I waste time deleting them.

About upgrades:
> It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
You're not supposed to do a Dapper-->Edgy or a Edgy-->Feisty thing without it.  The distro upgrading instructions include making sure ubuntu-desktop is installed.

---

### Post by Rhox on 2007-05-22
> **macogw said:**
>  Instead I waste time deleting them.
Why?

> **macogw said:**
> 
About upgrades:
You're not supposed to do a Dapper-->Edgy or a Edgy-->Feisty thing without it.  The distro upgrading instructions include making sure ubuntu-desktop is installed.

It just installs _____-desktop. You don't really need it.

---

### Post by urukrama on 2007-05-22
> **angryfirelord said:**
> removing ubuntu-desktop does cause issues.

Really? I've never had any trouble with removing it. It is just a meta-package and can easily be removed.
I've even installed xubuntu-desktop and later removed the meta-package, keeping most of the other packages that make up xubuntu. If you don't plan on upgrading every new release you're fine.

---

### Post by juxtaposed on 2007-05-22
> (though idk maybe it needs it to run other stuff inside a VM....kinda doubt it though).

It isn't for running other things in vmware:

X.Org X server -- VMware display driver
This package provides the driver for VMware client sessions, i.e. if Linux
is running inside a VMware session.

Anyway, each one from that long list is like 45-300KB, so it's small. But still :P

---

### Post by zgornel on 2007-05-23
> **Anthem said:**
> OpenOffice has always been a hog.  MS Office 2003 is much leaner and quicker than a standard OO.o install.  I know everybody hates Microsoft, but that doesn't change the fact that OO.o is pretty slow in most cases. Unfortunately, very very true.

---

### Post by angryfirelord on 2007-05-23
> **jerrylamos said:**
> Out of curiosity, does it help speed to go to System, Administration, Services and un-select things you don't think you'll need?
Tried it last night and that seems to have helped out a bit. I disabled bluetooth, cupsys, hplip, one other thing, and that seems to have made it more snappy (I think it was hplip because the system froze for a few seconds as if it were unloading something big).

---

### Post by Medieval_Creations on 2007-05-23
> **angryfirelord said:**
> Tried it last night and that seems to have helped out a bit. I disabled bluetooth, cupsys, hplip, one other thing, and that seems to have made it more snappy (I think it was hplip because the system froze for a few seconds as if it were unloading something big).

I already had gone in an disabled the services that I didn't need (i have to leave hplip, since I have an HP OfficeJet).  It does make it boot a little quicker, but the responsiveness from the desktop is where I'm looking to improve it.

I downloaded the testing versions for Debian and LinuxMint last night.  I plan on testing Mint out this weekend.

---

### Post by angryfirelord on 2007-05-23
I also have the nvidia-glx-new package as well, which I've noticed tends to speed things up a bit.

Seems like whatever I disabled made it snappier. However, my machine isn't that old:

AMD Sempron 3400+ @ 2GHZ
G.Skill DDR400 1GB
Nvidia GeForce 6200 AGP 128MB

---

### Post by plb on 2007-05-23
Yes, imho it has become very bloated and slow compared to what it once was. When debian etch came out I tried it and gnome ran a lot faster, not to mention it is a lot more stable.

---

### Post by Rhox on 2007-05-23
I may just be crazy but I think ubuntu has all ways had about the same amount of software by default.

---

### Post by CSMatt on 2007-05-24
> **Anthem said:**
> OpenOffice has always been a hog.  MS Office 2003 is much leaner and quicker than a standard OO.o install.  I know everybody hates Microsoft, but that doesn't change the fact that OO.o is pretty slow in most cases.
I think it's Java that's mostly to blame for this.  Java may make porting easier, but the fact that no operating system supports it natively (except maybe Solaris, but I'm not sure) could account for a performance hit.  I've honestly never seen a Java application or applet that *wasn't* slow, and I think the fact that a runtime environment is needed on all platforms may be causing or escalating this problem.

Of course, I could be wrong.

---

### Post by loathsome on 2007-05-24
> **CSMatt said:**
> I think it's Java that's mostly to blame for this.  Java may make porting easier, but the fact that no operating system supports it natively (except maybe Solaris, but I'm not sure) could account for a performance hit.  I've honestly never seen a Java application or applet that *wasn't* slow, and I think the fact that a runtime environment is needed on all platforms may be causing or escalating this problem.

Of course, I could be wrong.

How does it matter anyway? I just cold started OO on my C2D (that's UNDERCLOCKED atm @ 800MHz), and it took about 7 seconds to start up the word processor. When it was up, it stayed up - stable, fast and responsive. Ms' Office is fast but it's not that stable + it's only for Windows **plus** it's ******* expensive.

OpenOffice beats Office in so many ways :)

edit; I just tried launching Spreadsheet while running @ 1.6GHz, and it took like .. two seconds?

---

### Post by Enverex on 2007-05-24
> **loathsome said:**
> How does it matter anyway? I just cold started OO on my C2D (that's UNDERCLOCKED atm @ 800MHz), and it took about 7 seconds to start up the word processor. When it was up, it stayed up - stable, fast and responsive. Ms' Office is fast but it's not that stable + it's only for Windows **plus** it's ******* expensive.

OpenOffice beats Office in so many ways :)

edit; I just tried launching Spreadsheet while running @ 1.6GHz, and it took like .. two seconds?

I'm gonna call BS on your numbers. On my machine (Athlon64 X2 3800+, 2GB RAM, 76MB/s HD) it took 21 seconds to open OO Writer with no other apps using CPU time.

---

### Post by ThinkBuntu on 2007-05-24
> **Enverex said:**
> I'm gonna call BS on your numbers. On my machine (Athlon64 X2 3800+, 2GB RAM, 76MB/s HD) it took 21 seconds to open OO Writer with no other apps using CPU time.
**OpenOffice times I've experienced**
Specs: 1.6GHz, 1.5GB RAM, 5400rpm HD, ATI card
* *All times in seconds*
* *These are in fresh sessions, i.e. no cache involved.*
Ubuntu: 5
Debian: 2-3
Arch: 2-3
Sabayon: 7
Zenwalk: **<1**
openSUSE: 4
PCLinuxOS: 4

---

### Post by Enverex on 2007-05-24
Those machines would have to have OO pre-loaded as there's no way it could load that fast, especially the <1 one.

---

### Post by Rashid584 on 2007-05-24
> **Enverex said:**
> I'm gonna call BS on your numbers. On my machine (Athlon64 X2 3800+, 2GB RAM, 76MB/s HD) it took 21 seconds to open OO Writer with no other apps using CPU time.

I kinda agree...I have a P4 256MB RAM and it takes on average about ~17 seconds to load, and when it does it causes multi tasking to be extremely painful

I dunno how thinkbuntu got his openoffice to be so fast...I think he used oooqs or something

-Rashid

---

### Post by brim4brim on 2007-05-24
> **Enverex said:**
> Those machines would have to have OO pre-loaded as there's no way it could load that fast, especially the <1 one.

Yeah I have to agree.  I've never had OO load that fast unless it was preloaded.

It usually takes about 10 seconds on Ubuntu and longer on windows unless it is preloaded.

---

### Post by ThinkBuntu on 2007-05-24
> **Enverex said:**
> Those machines would have to have OO pre-loaded as there's no way it could load that fast, especially the <1 one.
I can guarantee that my times are accurate. Why would I lie? And I know what I'm doing (I wouldn't be tricked by a Quickstarter. I don't like quickstarters anyway..they hog RAM). If you want speed, use Zenwalk. It's really amazing for that, while being quite robust and stable.

---

### Post by loathsome on 2007-05-24
> **Enverex said:**
> I'm gonna call BS on your numbers. On my machine (Athlon64 X2 3800+, 2GB RAM, 76MB/s HD) it took 21 seconds to open OO Writer with no other apps using CPU time.

Well, I have no reason at all to lie, so .. 

That's the truth.

---

### Post by CSMatt on 2007-05-24
OpenOffice.org loads in 9 seconds for me.

I think the other reason it takes so long is because you are loading all installed parts of the suite at once, while Microsoft Office is made up of distinct programs that can run independently from one another.

---

### Post by loathsome on 2007-05-24
OpenOffice took 20 seconds to load at my desktop computer, whic is a lot faster than my laptop. Hmm .. It seems like it depends on something.

lol, every time I see this thread  title I always think it's "Is Ubuntu too fast", haha. It's fast, but nothing is **too** fast! ;)

---

### Post by n0dl on 2007-05-24
I think any distro is as big, small or, bloated or minimalistic as you want it to be. If you dont want a bloated ubuntu then do a server install then just get what you need and/or get apps through compiling source and zomg-optimize it with compile time options. At the risk of sounding like an old foggy *nix admin, the only real difference between the distros is the package managers used (this includes how repos are managed release cycles etc), governing body, and a couple of kernel patches. Even then, theres not much of a difference. Linux distros, despite what enthusiast might say, are not different OSes, hence things such as memory management, processor time and other system process should not necessarily matter, unless the source code of the program was modified to work more specifically with a patched kernel . An LFS machine running with the most bleeding edge build of Beryl a couple of games, a movie on mplayer plus a buttload of unused libraries and rarely used apps is obviously more bloated than a bare bone, only CLI ubuntu server install.
Make what you will of my rant

---

### Post by enlightenment now on 2007-05-24
Ubuntu is too *phat*, not too fat.

---

### Post by CSMatt on 2007-05-24
> **loathsome said:**
> lol, every time I see this thread  title I always think it's "Is Ubuntu too fast", haha. It's fast, but nothing is **too** fast! ;)

Wrong.  There *is* such a speed as "too fast," especially when it comes to games.  Have you ever played an old game on a new computer only to find out that the program was written without some kind of speed cap because the programmers couldn't fathom something like the beast you have now ever being used with their program?

---

### Post by hakimaki on 2007-05-24
I have noticed my feisty install has had the computer running a bit slower, especially when downloading multiple files in comparison to my edgy install.  However I take into account that everything has worked for me out of the box, no configuration needed from my end at all.  I figure if I wanted it to run that so much faster, i'd beef up the computer like I needed to when I was a windoze user.  An extra couple of seconds in waiting time aint worth the hardware upgrade costs in my eyes.

---

### Post by angryfirelord on 2007-05-24
> **CSMatt said:**
> Wrong.  There *is* such a speed as "too fast," especially when it comes to games.  Have you ever played an old game on a new computer only to find out that the program was written without some kind of speed cap because the programmers couldn't fathom something like the beast you have now ever being used with their program?
haha your for loops go from 0 to 60 in .000000000000001 seconds. :D

---

### Post by Egils on 2007-05-25
I have noticed that Ubuntu Studio seems to be quite a bit faster than my regular Fiesty install, but then again I have bloated the regular install myself, and Ubuntu Studio has also been stripped of some of the software that normally comes with Ubuntu. Still, it could be an interesting alternative for people looking for a leaner Ubuntu install right out of the box. Just a shame that there is no 64-bit version yet.

And I decided to test out Fedora a little while ago. While I gave up on it as soon as I had to confront the awful yum system, the option of being able to pick the software you want to install during the installation process was interesting. This could easily be incorporated into the Ubuntu install as some kind of 'advanced option'.

---

### Post by jerrylamos on 2007-05-25
> **angryfirelord said:**
> I've noticed on many numerous Linux forums that when Ubuntu comes up in the conversation, they mention that it has become rather bloated.

Unfortunately, I think they're right.

[/rant]

You Bet!  I just did an update that included absolutely endless megabytes of true type fonts for languages I never heard of and can't even imagine what country they are.

All due respect for the people of those languages, at age 72 I'm never in my lifetime going to read, write, or speak Gascon or Occitan or Xhosa and I watched in horror as megabyte after megabyte got downloaded using up internet and using up space on my hard drive.

As far as I can tell, they went into Open Office but I'm not sure where these endless megabytes got stored?

How do I remove ttf fonts for languages I'll never use?

Thanks, Jerry

---

### Post by Rashid584 on 2007-05-25
Jerry, do the following from a terminal:

```
dpkg -l | grep ttf
```

Now do

```
sudo aptitude remove ttf-name ttf-name2 ttf-name3
```

Replaces name, name2, name3, etc etc with the names that come up from the previous command. This should hopefully get rid of those that installed recently...however if they are dependencies it may try to kill openoffice too.

Not a bad idea, if you ask me :D

lemme know how it goes

-Rashid

---

### Post by loathsome on 2007-05-26
That's weird, I don't have any of those fonts @ Feisty .. I have like 40 different(?) fonts or so.

---

### Post by punong_bisyonaryo on 2007-05-27
For my two cents worth, I used dapper on my home file server/azureus server. And i can connect to it through SSH and VNC from anywhere. It's a P3 500, used to work tolerably before in Dapper. Now with Feisty, it's really sluggish with azureus. And even connecting thru vnc through LAN is slow! Plus wireless issues with my laptop, i'm considering going back to edgy. If things don't improve, well it's either I stay at edgy forever or i'll find another distro. In short, to developers, WAKE UP. You're turning Ubuntu to another Vista -- overbloated software that doesn't deliver much improvements anyway.:mad:

---

### Post by Rashid584 on 2007-05-27
I don't see why you should go back to feisty forever...dapper is an LTS and believe it or not, is actually the most used version of Ubuntu. Its still perfectly reasonable and perfectly normal to still use dapper...until the next LTS is released.

-Rashid

---

### Post by roadrocket13 on 2007-06-07
YES! 

Ubuntu is bloated as hell, but i still like it

---

### Post by init1 on 2007-06-07
> **angryfirelord said:**
> I've noticed on many numerous Linux forums that when Ubuntu comes up in the conversation, they mention that it has become rather bloated.

Unfortunately, I think they're right.

For example, the first linux distro that I got serious about was Ubuntu Dapper. It was speedy, easy to use, and helped me to understand linux better.

Then, Edgy came along. Boot up times were faster, but general usage was slower. However, given the 4 month window it was developed in, I let it go.

Feisty, however, IMHO, wasn't as fast as the Ubuntu devs said it was. Sure, it had all of the shiny new packages, but it was slow. Not suse slow, but slow enough to be annoying. 

Now, I understand that there are people who don't agree with me and I welcome any comments that disagree, but I think Ubuntu needs to focus more on the Debian model of things, which follows the standard Linux model. You don't have to sacrifice usuability, but just don't cram as much stuff in there! Also, I'd like to see more Debian compatability, which would make the Debian devs happy.

For those whom I've offended, I'll probably still be using Ubuntu for a while anyway.

[/rant]
Ubuntu <700mb != bloated. The apps on the CD are very useful. Smaller versions (like fluxbuntu) can be made to de-bloat it.

---

### Post by forrestcupp on 2007-06-07
What's the difference between bloat and features?  I like having lots of features.  A computer that can't do anything is worthless.  I like being able to do a lot with my computer.

---

### Post by Rashid584 on 2007-06-07
alternate install + kde core here...much faster :D

Not quite as fast as sidux though...but has a nicer feel, and is more stable (and nice to use i.e. gives less problems)

The line between bloat and features is very fine...for me, at least, bloat is features that I will never use, or will use so rarely there's no point in having them slowing the rest of my usage time down.

I perform a few set tasks so for me a slim install works fine...web browsing, MSN, mp3s/oggs, videos, torrents, pdf viewing, image processing, console, beryl, file managing, and occasional bluetoothing between phone. 

-Rashid

---

### Post by FFighter on 2007-06-07
Well, I stayed solely with Ubuntu for about 15 days and while I enjoyed both in terms of fun and learning, I had to step back to XP after the poor performance of key features of the Web Developer Toolbar FireFox add-on (the ruler and page magnifier - both which were almost unusable due to poor rendering performance). I wish I could make a complete switch to GNU/Linux (Ubuntu) but unfortunately I don't have the time (time is money) to spend searching for fixes right now and had to go back to my XP workstation. XP is rock solid here and I get work done on it fast and without any glitches, so, unfortunately, at least currently, this is my best option.

---

### Post by angryfirelord on 2007-06-08
Well, after experimenting with other distros, I have confirmed that 1) Disabling hplip does speed it up and 2) I may have been exaggerating a little bit out of frustration. Ubuntu does have some speed compared to openSuSE, Fedora, MEPIS, Mandriva, etc (except for Debian and PCLOS, which seem to be faster). So now I'm happy with Ubuntu again.

Also, bloatness (if that's even a word) doesn't relate to the # of packages installed, it's how responsive the system is.

---

