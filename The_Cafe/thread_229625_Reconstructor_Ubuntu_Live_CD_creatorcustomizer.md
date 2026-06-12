---
title: "Reconstructor: Ubuntu Live CD creator/customizer"
date: 2006-08-04
forum: The Cafe
---

### Post by UbuWu on 2006-08-04
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

> Reconstructor is a Live CD creator for Ubuntu Linux.

It uses the Ubuntu Linux Live CD as a base, and then allows customization of boot screens (usplash), gnome settings, and software (you can also use the chroot environment to make other changes before creating the live cd).

Reconstructor does not create separate distros.  It keeps the solid Ubuntu foundation, and just allows for customization.  For example, create a custom Live CD with blender, inkscape, etc. included for a friend in graphics, or simply use reconstructor to re-brand your environment (wallpaper, fonts). 

Reconstructor is written in python and is licensed under the GNU General Public License (GPL) 

Works great!

---

### Post by kostkon on 2006-08-04
Wow!! Great project!!

Thanks for the info!

---

### Post by ubuntu_demon on 2006-08-06
Here's a related thread :

easy GUI based custom ubuntu cd creation tool
[http://www.ubuntuforums.org/showthread.php?t=5981](http://www.ubuntuforums.org/showthread.php?t=5981)

---

### Post by ehazlett on 2006-08-06
im glad to see people using it...  it has also been translated to French, Brazilian Portuguese, and is being translated to Basque/Spanish.  i am glad to finally be able to give something back to the ubuntu community... ;)

thanks all...

evan

---

### Post by John.Michael.Kane on 2006-08-06
I tested it, and can say that it does work quiet nicely. though i understand it's still under dev,and might be still rough around the edges. It is still great work.

---

### Post by richbarna on 2006-08-06
> **SD-Plissken said:**
> I tested it, and can say that it does work quiet nicely. though i understand it's still under dev,and might be still rough around the edges. It is still great work.

I have no use for it personally, yet. But I put a post on my blog about it as it looks like a good idea.

I also see that Arnie boy's Automatix-Bleeder is coming along nicely, especially if a newbie has an nvidia or ati card problem but wants all the eye candy.
[http://www.ubuntuforums.org/showthread.php?t=225967&highlight=arnieboy](http://www.ubuntuforums.org/showthread.php?t=225967&highlight=arnieboy)

---

### Post by ubuntu_demon on 2006-08-06
I blogged about this here :

Reconstructor: a Live CD creator for Ubuntu Linux
[http://ubuntudemon.wordpress.com/2006/08/06/reconstructor-a-live-cd-creator-for-ubuntu-linux/](http://ubuntudemon.wordpress.com/2006/08/06/reconstructor-a-live-cd-creator-for-ubuntu-linux/)

---

### Post by John.Michael.Kane on 2006-08-06
richbarna I just wanted to test it to see how it worked. me personaly i use the standard distro. though i can see this being of use for those who may want to make a custom live distro with whatever programs/services they need,and don't need. same holds true for automatrix that has come along ways too, and theres users who may not want to get their hands dirty with the CL yet so these tools may fill this void. most linux/ubuntu users will eventualy have to mess with CL as there maybe something that theres no gui for.

---

### Post by Mathias-K on 2006-08-06
Seems like an absolutely brilliant idea. Subscribed! :)

---

### Post by caldevil on 2006-08-06
When we install through this live cd, do the customizations get installed too?

---

### Post by jc87 on 2006-08-06
Sounds great , i was looking for something like that for a while;) 

Maybe now we start having a bunch of customized Ubuntu isos all over the web , even more freedom of choice:-D

---

### Post by richbarna on 2006-08-06
> **SD-Plissken said:**
> richbarna I just wanted to test it to see how it worked. me personaly i use the standard distro. though i can see this being of use for those who may want to make a custom live distro with whatever programs/services they need,and don't need. same holds true for automatrix that has come along ways too, and theres users who may not want to get their hands dirty with the CL yet so these tools may fill this void. most linux/ubuntu users will eventualy have to mess with CL as there maybe something that theres no gui for.

You probably won't believe this SD-Plissken, but I have just installed PClinuxOS and only opened the terminal to see how pretty it was. It is the first non-cli os that I have installed.

Obviously with so much going well, and so little to fix, I am trying very hard to break it at the moment. Still no success.

---

### Post by John.Michael.Kane on 2006-08-06
richbarna you might have point there are distro's out there that allow the user the option to not have to muck about the CL. PClinux does seem to be one of those distro's that is working toward that. though there will always be endusers who will want to use the CL.

---

### Post by d3x7r0 on 2006-08-09
> **caldevil said:**
> When we install through this live cd, do the customizations get installed too?

Now there is something I want to know aswell. It would be great to be able to create a custom cd with everything I need and use it as a quick system restore option :)

---

### Post by John.Michael.Kane on 2006-08-09
d3x7r0 and caldevil the live-cd is giving you a picture of what you get upon install.so the custom stuff should carry over to your install.

---

### Post by ehazlett on 2006-08-12
yes, the customizations get installed to the hard drive when using the installer...  sorry for the late response... ;)

---

### Post by MetalMusicAddict on 2006-09-15
ehazlett. I must thank you a TON! I have been wanting something like this since Warty. I love [nLite]("http://www.nliteos.com/") for windows and Reconstructor lets me work on Ubuntu. Awesome. :)

Would this work on the "Alt" cd? I have many questions. If I post here will you answer or should I email?

---

### Post by punkinside on 2006-09-15
What we really need is something like the mklivecd or whatever command the PCLOS guys have, I dont really know how that works, but I have heavily customized everything there is to customize, and I would like to get my ubuntu just right and then go, ok! in case I FUBAR everything i'll create some iso's that will install my system again...

EDIT: i know there are a few threads about "backup your system" and all but those are bandages to what we should be really doing... a norton ghost type thing but for creating a live CD that could install also. It would be really cool to go around with a live CD of MY ubuntu, not just the same ol' default.

---

### Post by maniacmusician on 2006-09-15
> **punkinside said:**
> What we really need is something like the mklivecd or whatever command the PCLOS guys have, I dont really know how that works, but I have heavily customized everything there is to customize, and I would like to get my ubuntu just right and then go, ok! in case I FUBAR everything i'll create some iso's that will install my system again...

EDIT: i know there are a few threads about "backup your system" and all but those are bandages to what we should be really doing... a norton ghost type thing but for creating a live CD that could install also. It would be really cool to go around with a live CD of MY ubuntu, not just the same ol' default.
that's not very possible...there's a limited amount of space on a CD and "your" ubuntu probably exceeds that by a lot, with all the apps and stuff. maybe if we start doing LiveDVDs, that'll be possible.

PartImage is a program that is sort of norton ghost-like. at least it can be used in that capacity.

---

### Post by punkinside on 2006-09-15
That may be true, but anyhoo theres a bunch of stuff that I dont really use, i normally remove those programs. So MY ubuntu would probably fit in a liveCD so I could just go around with the apps I really need and then all the other stuff I could install afterwards programs in the repos are not a problem, Its things like java and codecs and all the changes ive made in gnome etc. Still a real backup could actually take more cd's thats not a problem many distros have several CD installs

---

### Post by maniacmusician on 2006-09-15
that's true...you can do the multi-cd approach with PartImage. here's a link

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by spockrock on 2006-09-15
This is an amazing tool.  Thank you very much...

---

### Post by PryGuy on 2006-09-16
Amazing!
A DEB package please...:-\"

---

### Post by 3rdalbum on 2006-09-16
Since it's updated so often, I'd prefer a 3rd party repository to a .deb package. But hey, it's so brilliant, I wouldn't even mind looking at their website every day to check when a new version comes out :-)

---

### Post by punkinside on 2006-09-16
> **maniacmusician said:**
> that's true...you can do the multi-cd approach with PartImage. here's a link

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

Thanx! I'd still be nice to make a live CD though :D 

I'm gonna try and look into that PCLOS thingy see what I can find out about it.

---

### Post by spockrock on 2006-09-17
sorry is there a guide to creating a proper pcx file??

also no matter what I do it seems the my 16 colour indexed 640x400 pngs converted to so's never work.

---

### Post by MetalMusicAddict on 2006-09-17
> **maniacmusician said:**
> that's not very possible...there's a limited amount of space on a CD and "your" ubuntu probably exceeds that by a lot, with all the apps and stuff. maybe if we start doing LiveDVDs, that'll be possible.
If your customized disk exceeds CD size you can use a DVD. Ive just tested this.
> **punkinside said:**
> Thanx! I'd still be nice to make a live CD though :D
You can make one with this. :)


Ive spent the better part of this morning playing with this and its AWESOME!!! Im still learning all the stuff you can do. I have to actually learn the proper commands for gconf so I can set some panel sizes and add things to it. There is a terminal to do stuff like this.

I have a disk so far customized with this so far:
[LIST]
[*]A all black theme. Theme, Icons, Wallpaper and such.
[*]All repos opened up with one for Listen added.
[*]These apps installed: [SIZE="1"](added with apt-get line)[/SIZE]
[/LIST] [SIZE="1"]listen smbfs sysv-rc-conf  nautilus-actions grip lame easytag gimp-data-extras gimp-dcraw gimp-svg xchat bittornado-gui gnome-raw-thumbnailer mail-notification gdesklets linux-image-686 xine-ui gparted acroread acroread-plugins faac f-spot gimp-data-extras lame-extras libdvdnav4 libdvdread3 unrar vlc vlc-plugin-alsa gstreamer0.10-ffmpeg joystick mozilla-thunderbird[/SIZE]
[LIST]
[*]Fully updated with dist-upgrade.
[*]Flash, Java and media codecs.
[*]Other little tweeks.
[/LIST]

The disk has worked great as a live DVD and on install. Definatly use ubuntu-6.06.1-desktop-i386.iso and not 6.06. I kept having problems with installing from the disk. Mainly GRUB.

If you like to tinker this app is TOTALLY for you. Im going to make customized/updated disks for each of my machines. :) Reconstructor also looks to work on 64-bit Ubuntu also. I have yet to test. I also plan on testing this with Xubuntu.

---

### Post by punkinside on 2006-09-17
Dosent this compress anything? A default ubuntu install is, of course, larger than 700 MB. How'd you go about doing all those things?

---

### Post by MetalMusicAddict on 2006-09-17
> **MetalMusicAddict said:**
> The disk has worked great as a live **DVD** and on install.
1.13 gig DVD to be exact.

---

### Post by reluttr on 2006-09-29
so tell me... Is there anyway to run this app through the live cd?

---

### Post by raublekick on 2006-09-29
this looks pretty awesome! any interested in making a version for Kubuntu? you really wouldn't even need to change the front end, just the backend to work with Kubuntu stuff. Don't know how hard it will be, but maybe tonight after work I'll check out the source and see what's up with it.

---

### Post by vilto on 2006-09-30
i have a problem after customizing using reconstructor......

1)some of the icons are not visible like homefolder,terminal caluculator,etc.....
2)when i tried to login as root it says somthing like
   unable to lookup live cd via gethostbyname()
3)login error saying 
   Could not load icon

   Details: Failed to open file         '/usr/share/icons/OSX/scalable/apps/evolution.png': Permission denied

other than this everything looks fine

to note i have changed the live cd user name and password .....did this created the problem??

here is the screenshot
[[IMG]http://img89.imageshack.us/img89/6889/vijpf6.th.jpg[/IMG]](http://img89.imageshack.us/my.php?image=vijpf6.jpg)

---

### Post by luisbg on 2007-06-29
Awesome project!

What would be very cool is that it also added all the system configurations... /etc/modules, kernel used, xorg.conf, /etc/rc.local, etc...

This would be very useful for those of us using laptops. Since after making a clean install we have to spend a while (sometimes even days) to get everything working, configurated to perfection. All hardware supported, all our little tweaks, power consumption to it's minimum, etc...

my two cents,
luis

---

### Post by bobbocanfly on 2007-07-02
Wow! Reconstructor is *amazing*. This is one of the things i like most about Linux/OpenSource. YOu can do pretty much what you want to Ubuntu, make it look dead good by default, while still having the solid Ubuntu base. Plus its free and legal.

Cant wait to make some new LiveCDs in this

---

### Post by smartboyathome on 2007-07-02
I use UCK (Ubuntu Customization Kit). It is not only more straight forward, but (to me) has a better interface (and doesn't have all the flaws of Reconstructor).

---

### Post by rsambuca on 2007-07-17
I really don't know too much about this, but I have a couple of questions:

1. Will Reconstruction work on 64-bit ubuntu?

2.  If it does, could it be used to create a 64-bit ubuntu iso with the 32-bit firefox automatically installed (possibly with java/flash)?

---

### Post by smartboyathome on 2007-07-17
1. I think it can, but you would have to install it as a 32 bit application
2. You would have to wget, configure, and install it all through the terminal.

---

### Post by Azriphale on 2007-10-06
I have been trying for hours to remaster the Ubuntu Live disc, and after looking for more instructions on how to do so, came across your tool. And finally I have a working live CD! Thanks for a great and easy to use tool!

---

### Post by darkmaster on 2007-10-16
Unfortunately, this doesn't work well with the Ubuntu Gtusy Gibbon Live CD.
There's no apparent way to set username and password of the Live but I need to do it. How could I solve my problem? How can I change username and password, so that after login I can still use ubiquity and the likes?

---

### Post by zahris on 2008-04-08
i'm currently remastering Ubuntu 7.10 using Reconstructor 2.7..

evertything works great.. but after the instalation the ubiquity packages are still installed, unlike normal ubuntu instalation. i can still access the installer in System > Administrations > Install

is there anyone know how the packages can be automaticaly uninstalled after the instalation to the harddrive?

when i use the normal ubuntu live-cd for instalation, i see that. packages such as  ubiquity and gparted is already uninstalled.

can anybody help me?
thanx

---

### Post by capink on 2008-04-08
> **zahris said:**
> i'm currently remastering Ubuntu 7.10 using Reconstructor 2.7..

evertything works great.. but after the instalation the ubiquity packages are still installed, unlike normal ubuntu instalation. i can still access the installer in System > Administrations > Install

is there anyone know how the packages can be automaticaly uninstalled after the instalation to the harddrive?

when i use the normal ubuntu live-cd for instalation, i see that. packages such as  ubiquity and gparted is already uninstalled.

can anybody help me?
thanx


The live cd tree contains two files: /casper/filesystem.manifest & /casper/filesystem.manifest-desktop. The first file contains a list of all packages installed in the live cd filesystem (including casper, ubiquity, ....). The second contains the same list of packages minus those you would like to uninstall after the instalation to the harddrive.

Ubiquity compares the two files and decides what packages to remove. So make sure the any package you want to remove is not included in /casper/filesystem.manifest-desktop.

---

### Post by zahris on 2008-04-09
> **capink said:**
> The live cd tree contains two files: /casper/filesystem.manifest & /casper/filesystem.manifest-desktop. The first file contains a list of all packages installed in the live cd filesystem (including casper, ubiquity, ....). The second contains the same list of packages minus those you would like to uninstall after the instalation to the harddrive.

Ubiquity compares the two files and decides what packages to remove. So make sure the any package you want to remove is not included in /casper/filesystem.manifest-desktop.

okay thanks... i'll try it

:)

---

### Post by darkmaster on 2008-09-23
> **capink said:**
> The live cd tree contains two files: /casper/filesystem.manifest & /casper/filesystem.manifest-desktop. The first file contains a list of all packages installed in the live cd filesystem (including casper, ubiquity, ....). The second contains the same list of packages minus those you would like to uninstall after the instalation to the harddrive.

Ubiquity compares the two files and decides what packages to remove. So make sure the any package you want to remove is not included in /casper/filesystem.manifest-desktop.

Unlickily, I'm not able of having this tip working.... I tested it in Hardy now for exampel with my OpenGEU... I still have this issue, see here:
[https://bugs.launchpad.net/bugs/273382](https://bugs.launchpad.net/bugs/273382)

---

