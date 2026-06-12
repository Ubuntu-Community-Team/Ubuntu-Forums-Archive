---
title: "Quantal Startup Disk Creator made defective USB image"
date: 2012-06-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-06-01
"Startup Disk Creator" on 31 May quantal install said it created USB flash O.K. of the 1 June daily i386.iso.

:-o On booting, the cursor was a black X instead of an arrow, there was no top panel, and no launcher.  The Install and Example icons were on the purple splotch background.

Precise "Startup Disk Creator" ran just fine and the USB flash installed O.K. Well, a code 2 on time zone, Colin's got a fix for that, and the usual _usr_lib_gnome-settings-daemon_gnome-settings-daemon.1000.crash which doesn't seem to cause any trouble.

Jerry

---

### Post by ventrical on 2012-06-01
I just finished a zsync about 15 minutes ago.  USB startup disk creator worked ok. Went to boot on another regular testing machine. Got purple screen with Ubuntu keyboard with man in a circle thingy on bottom .. then total black-space - no terminal , mouse .. nothing.

Will try a re-boot .

EDIT: Reboot - black-space.

Will try another machine with ATi (non nvidia).

---

### Post by ventrical on 2012-06-01
I have video with ATi graphics card but got the error:

error occurred while mounting /sys/fs/fuse/connections

and now it is hung at a restart.

will try reboot on that machine.

Edit:

Reboot and then <alt>+F1 gave me manual install screen. Same on nvidia machine but Nvidia gave me black-space when I chose <try ubuntu without installing>!

---

### Post by ventrical on 2012-06-01
Choosing nomodeset it will go as far as allowing you to use Crtl+D and then it hangs :

<mountall start/starting>

---

### Post by ventrical on 2012-06-01
The option to <safely remove > (usb) has gone also so I had to use <eject drive> (USB drive successfully ejected). I wonder if this has nanything to do with this.?

---

### Post by ventrical on 2012-06-01
I copied todays build to an Oneric install (Dell Opti), ran Startup Disk Creator, and got Uncompression Error, System Halted, when I tried to boot on nvidia regular testing machine from USB.

---

### Post by thebestofall007 on 2012-06-01
have you ever tried multisystem to create your startup usb? this awesome bit of software not only will allow you to create your 12.04 startup, but it also allows you to put multiple os's on a thumbdrive (like ubuntu and system rescue utilities together for example) and select them at start using grub2 or grub4dos. it also has supergrub disk and supergrub2 disk. here is the site: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")

---

### Post by ventrical on 2012-06-01
Thanks .

 I'm dealing stricktly with the QQ iso daily builds only here.

---

### Post by jerrylamos on 2012-06-01
> **ventrical said:**
> I'm dealing stricktly with the QQ iso daily builds only here.

Me too, sometimes though I'll use an older ubuntu to do the QQ 12.10 zsync, and the QQ 12.10 startup disk creator is not so good for me.  

I'm usually able to get something or other up on the daily quantal i386.iso's though it may be limping...might run on the netbook but not the notebook which has an external monitor or vice versa and the tower has two hard drives which seems to confuse QQ's ubiquity and grub2 no end.

Alpha 1 is coming, and I'm still waiting for major breakage.

Jerry

---

### Post by pressureman on 2012-06-01
Have any of you tried manually executing 'sync' before removing the USB stick?

---

### Post by jerrylamos on 2012-06-02
> **pressureman said:**
> Have any of you tried manually executing 'sync' before removing the USB stick?

What I do is normal shut down power off. 

If that doesn't do a sync then Ubuntu has a bug.

Another thing I do is create the startup disk, do a normal restart and try the disk out.

If that doesn't do a sync then Ubuntu has a bug.

Of course in any case I wait until ubuntu startup disk creator has said it is finished.

Using the exact same technique, oneiric and precise produce a usable bootable startup USB disk.  quantal startup USB disk has either xorg or desktop or gdm or whatever screwed up.  Since I have a method to produce a startup disk, this is not a showstopper for me.  

Jerry

---

### Post by pressureman on 2012-06-02
Was it working up until a few days ago?

The recent changes to the source ([https://bazaar.launchpad.net/~usb-creator-hackers/usb-creator/trunk/changes](https://bazaar.launchpad.net/~usb-creator-hackers/usb-creator/trunk/changes)) have mostly been to do with Python 3 support since precise was released, but on May 28 there was a change to how the partition table is handled.

---

### Post by ronacc on 2012-06-02
I'm always pleasantly surprised when startup disk creator actually makes a bootable stick for me , its such a rare occurrence .  Typically my box doesn't even see the stick as a bootable device  , Precise final did make a good one of the 1st quantal live cd to get me started on quantal though .

---

### Post by VMC on 2012-06-02
usb-creator always works, but I use a different approach. Simpler for me.

First and only once I do the following

```
sudo syslinux /dev/sdxx
``` (depending on where the usb stick is)
Then on the root device I create my own syslinux.cfg file,and add the following:
```
DEFAULT live
LABEL live
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
```

From then on I only use 7z to create the needed files.

```
7z x -o/media/quantal quantal-desktop-amd64.iso .disk preseed dists install pool casper
```

On each new ISO I just delete: 
```
.disk preseed dists install pool casper
```

and use 7z again. Never fails.

---

### Post by ventrical on 2012-06-02
> **pressureman said:**
> Was it working up until a few days ago?

The recent changes to the source ([https://bazaar.launchpad.net/~usb-creator-hackers/usb-creator/trunk/changes]("https://bazaar.launchpad.net/%7Eusb-creator-hackers/usb-creator/trunk/changes")) have mostly been to do with Python 3 support since precise was released, but on May 28 there was a change to how the partition table is handled.

 This is the first time I have seen Startup Disk Creator fail. In fact I am not even sure that it is SDC that has the problem. It appears that the process is working just fine.  It seems that the .iso itself may have a problem.  I am going to try again today to zsync that .iso, quantal-desktop-i386.iso.

---

### Post by ventrical on 2012-06-02
After todays' zsync I just get a run with squashfs errors when attempting to boot that newly created USB stick.

---

### Post by ronacc on 2012-06-02
I zsync'd the current ISO and made ( after an epic battle ) a bootable startup usb stick , there are multiple problems not all with startup disk creator , # 1 when SDC is invoked and you try to select an iso if your ISO is on a seperate drive the file requester box creates a drive and mounts it under /media/<size>disk ( note on my sys this came out to 6.3 MB ) for the 744mb ISO . and selects this for the source and then this CANNOT BE CHANGED . I circumvented this by copying the ISO to my /home and rebooting (quiting SDC and restarting it did not help ) , # 2 the resultant usb stick booted to desktop ok but then selecting install ubuntu the installer crashed ( 4 times ) upon exiting from the disk selection window . I suspect the problem with the source selection is a nautilus problem not SDC and the ubiquity crash may be related to partman . also ubiquity now bitches when you do not connect to the internet and when you select an exisitng partition in drive selection window partman insists on trying to resize it even when told not to format it .

---

### Post by ventrical on 2012-06-02
@ronac,

What I did was rename the previous .iso.old zsync file to current (quantal-desktop-i386.iso) then used SDC and subsequently it booted just fine.!!

There is definitely a problem with the builds.

---

### Post by ventrical on 2012-06-02
To prove there is a problem with the builds, I  used a machine that has Quantal installed and used SDC on that machine and used precise-desktop-i386.iso pre-final and it is working excellently on booting my regular machines from USB.

---

### Post by pressureman on 2012-06-02
This is pretty much why I still use the alternate (text mode) installer, since you can always check [http://cdimage.ubuntulinux.org/daily/current/report.html](http://cdimage.ubuntulinux.org/daily/current/report.html) to see if there are potential problems with the image.

You also have a lot more control over the installation process, both before and *during* the installation.

---

### Post by ventrical on 2012-06-02
> **pressureman said:**
> This is pretty much why I still use the alternate (text mode) installer, since you can always check [http://cdimage.ubuntulinux.org/daily/current/report.html](http://cdimage.ubuntulinux.org/daily/current/report.html) to see if there are potential problems with the image.

You also have a lot more control over the installation process, both before and *during* the installation.

Yep .. <Alt+F1>  :)

Thanks for that linklet. I didn't know the .iso could be checked in that way.

---

### Post by mc4man on 2012-06-02
Both yesterdays & todays amd64 iso's work fine, which is no surprise since they haven't changed 
(the .list has changed but not the iso

It's using ubiquity 2.11.3 while it appears that the i386 iso is now using 2.11.4
Maybe your issue is with 2.11.4

(don't see where the other possible new packages from yesterday to today's iso would matter here though can't test all as at least one requires a restart
```
The following packages have been kept back:
  update-manager-core
The following packages will be upgraded:
  apport apport-gtk gir1.2-totem-1.0 gir1.2-ubuntuoneui-3.0 libssl1.0.0 libsysfs2 libtotem0
  libubuntuoneui-3.0-1 libwps-0.2-2 openssl python-apport python-crypto python-problem-report sed
  software-center totem totem-common totem-mozilla totem-plugins ubiquity ubiquity-frontend-gtk
  ubiquity-ubuntu-artwork

```

---

### Post by ronacc on 2012-06-02
> **mc4man said:**
> Both yesterdays & todays amd64 iso's work fine, which is no surprise since they haven't changed 
(the .list has changed but not the iso

It's using ubiquity 2.11.3 while it appears that the i386 iso is now using 2.11.4
Maybe your issue is with 2.11.4


the one that kept crashing ubiquity on me was the current 64 bit desktop iso zsync'd at 10 AM  today Eastern US time .

---

### Post by sammiev on 2012-06-02
Was able to create a boot able USB start disk today but the install failed on update 3/4 of the way through. Well try again in a few days.

---

### Post by mc4man on 2012-06-02
Went ahead & booted to today's i386 iso which contains all the updated packages for what's on the iso.

Definitely a few issues, at least in the live session. The first screen where the 'try me/install' should be was totally corrupted, but got cleaned up by finding the window deco of the above window & dragging around.

The live session worked but had a crash of gnome-settings-daemon, logging out/in & it crashed again
(gives one of those informative pop ups about already being reported, thank you, good bye, you don't need to know..., though if you ask apport nicely it will tell you what the crash was - scr. 1

I don't want a 32 bit install so didn't go further, hopefully an install looks better - screen 2 shows nautilus with huge deco, maybe because text is below icons instead of alongside & menu is in nautilus

---

### Post by ronacc on 2012-06-02
I must have zsync'd at the wrong time , for a check I burned the ISO to a dvd , booted to DT ok but now the installer hangs even earlier , also reports that one of the HD's (sdb) is mounted when it is not .

---

### Post by ronacc on 2012-06-02
checked my iso , zsync says it is up to date .

---

### Post by pressureman on 2012-06-02
> **ronacc said:**
> I must have zsync'd at the wrong time , for a check I burned the ISO to a dvd , booted to DT ok but now the installer hangs even earlier , also reports that one of the HD's (sdb) is mounted when it is not .

The zsync client performs a SHA-1 hash verification after downloading. It's very unlikely you'd get a bad download.

---

### Post by jerrylamos on 2012-06-02
> **pressureman said:**
> The zsync client performs a SHA-1 hash verification after downloading. It's very unlikely you'd get a bad download.
The .iso's in my case (I started this thread) work.

Quantal startup-disk creator (using quantal 2 June i386.iso) from 1 June install worked for a while - desktop was O.K.

Connected wireless.

Started install then wham!  deader than a doorknob.  Desktop disappeared no keys worked couldn't get a cli.  Screen full of all sorts of text stuff I don't understand.  It'd take a hi-res digital picture to capture it all.

Precise startup disk creator using exactly the same .iso everything ran, made the USB flash, booted, install went through, booted & this is quantal from that 2 June .iso. 

Something goes bum on quantal's startup disk creator that does not occur on precise's startup disk creator.  It's so dead I can't gather any ubuntu-bug data.

Not a showstopper to me, just chews up some time seeing if quantal's startup-disk creator is still bad.

Jerry

---

### Post by pressureman on 2012-06-02
> **jerrylamos said:**
> Started install then wham!  deader than a doorknob.  Desktop disappeared no keys worked couldn't get a cli.  Screen full of all sorts of text stuff I don't understand.

You mean a kernel oops or panic? Some examples are shown at [https://en.wikipedia.org/wiki/Linux_kernel_oops](https://en.wikipedia.org/wiki/Linux_kernel_oops)

> **jerrylamos said:**
> Something goes bum on quantal's startup disk creator that does not occur on precise's startup disk creator.  It's so dead I can't gather any ubuntu-bug data.

If usb-creator (or one of its dependencies) is writing bogus data to the USB stick, the results are going to be.... unpredictable. Kinda the same as I'd expect if you dd'ed /dev/urandom to some random offset in the USB stick's partition.

> **jerrylamos said:**
> Not a showstopper to me, just chews up some time seeing if quantal's startup-disk creator is still bad.

You're using a pre-alpha OS to create startup media for a pre-alpha OS. What did you expect? ;-)

---

### Post by ronacc on 2012-06-02
I was just checking to be through , the iso's boot but the installer fails , strangely it fails consistently at the same place every time but it is a different place when I use the startup disk created by SDC or the dvd burned with K3B from the same ISO .

---

### Post by nm_geo on 2012-06-03
I have been testing the Lubuntu amd64 quantal iso with persistent USBs created with precise Startup Disk Creator with no problems.  Made complete installs with 20120601 and 20120602 isos again with only one minor panel volume slider bug. 

After reading this thread, I decide to check out the quantal 12.10 SDC to see if it would create a workable install iso.  Well I admit I thought it would fail, but it installed okay.. Just logged it in the qa-tracker under do something else as I created a partition for the install. 

Crazy, I know.. What flavors of 12.10 were you guys installing?

---

### Post by jerrylamos on 2012-06-03
> **nm_geo said:**
> Crazy, I know.. What flavors of 12.10 were you guys installing?In my case (I started this thread) the normal quantal-desktop-i386.iso from the daily build.  This one's the 2 June version.

What fails for me is "quantal startup disk creator that came with, example the 1 June .iso" in that it says it created a USB startup disk (sic) but which is not able to complete an install.

Precise startup disk creator runs fine.  Creates a quantal USB startup that works. Well, lately anyway.

The .iso's have been working the last few days, just quantal's startup disk creator that doesn't, it creates a USB that starts to do an install then wham desktop disappears, screen is full of text, and nothing works.

I'd like to write a launchpad bug but haven't figured out how since it's a live running in memory and everything disappears on reboot.  Maybe there's something on the persistent part, I haven't looked.

Jerry

---

### Post by sammiev on 2012-06-03
I was testing the June 2 64-bit PC (AMD64) normal from a USB to a dual boot HD.

---

### Post by ronacc on 2012-06-03
I'm using the AMD64 desktop .ISO  , Like jerry the iso boots to dt but when you try to install the installer crashes but in my case (64 bit) just the installer window goes away and dosen't take the desktop with it . I'll try again and see if I can get it to file a bug since the DT stays functional for me .

---

### Post by jerrylamos on 2012-06-03
Being a bit frustrated (!) with quantal's startup disk creator I did a apt-get install of unetbootin.

Hey!  Unetbootin allows me to put the .iso on a partition on the USB stick.  These USB flash memories are getting to be 32 GB at $20 and quantal startup disk creator wants to use the -whole- thing for the startup?

So I've got 2 other partitions on the USB besides today's quantal daily.

BTW, running persistent like I am, I have to remember to wipe out the casper-rw partition when I load in a new .iso.

Now sometime past Ubuntu allowed me to install in a partition on the USB stick, but as far back as I've gone, Maverick, both startup disk creator and brasero (or whatever Maverick is using to write .iso) insist on using the whole USB.

Alpha 1 coming soon?  The daily updates are getting fewer.

Jerry

---

### Post by ronacc on 2012-06-03
I'm not sure that SDC is the problem now , I think partman is screwed up worse than usual . I booted my usb stick and the live session worked fine but when I tried to install ubiquity hung as usual . When I ran ubuntu-bug it insisted that the problem was with my DVD drive , note that I booted off a usb-stick which my bios sees as an HD . I did manage to get a screen shot of ubiquity asking if I wanted to unmount SDB before proceeding ? no hard drives were mounted , it did not mater if I said yes unmount it or no do nothing ubiquity hung shortly there after .

---

### Post by mc4man on 2012-06-04
Here with todays amd64 image it has nothing to do with what ubuntu version made the usb installer. 
When using manual partitioning all versions of ubiquity*_2.11.* will fail on doing the actual partitioning. So while the new partition(s) can be set up in the installer it then exits with nothing done.
No crash, just exits

Tried all .11 versions going back to .11.0 which was where the major changes were made

Was able to install from todays current image by downgrading ubiquity*, (3 packages), to the 2.10.16 versions & installing  python-pyicu
Then the install went as normal
(usb was made on previous 12.10 install

---

### Post by jerrylamos on 2012-06-04
s> **mc4man said:**
> ...When using manual partitioning all versions of ubiquity*_2.11.* will fail on doing the actual partitioning.... 
Glad someone else is testing ubuntu partitioning of the install.

I never use ubiquity's version of partitioning.

I install gparted where I can control what's going on, since even my 40 GB hard drive has multiple partitions various versions of test and tested ubuntu's.  Sure don't want buggy ubiquity messing that up.

Have fun, Jerry

---

### Post by ronacc on 2012-06-04
there really seems to be more than one problem involved here . there is the problem with ubiquity that mc4man notes and there also seems to be a problem with how the images are handled I tried both usb sticks and dvd's ( burned with k3b . I got failures with all of them . Even when I tried the image of precise that I had I had used to install and upgrade at repo opening ( fresh burn using quantal) . when I used my work system (mangy moose still) to make a usbstick of the precise .iso that worked flawlessly . there also seems to be a problem with either partman of udev on the quantal daily's , on booting to the live session it insists that sdb is mounted ( I have 6 hd's in my test box ) when it is not . also as soon as you start SDC it creates a 6.3 mb disk and mounts that as the "source" and you have to "eject" (not unmount"
that before it will let you choose the real .iso .

---

### Post by ventrical on 2012-06-04
Here is what I got after zsyncing about 1/2 hour ago and using SDC to burn an image to USB.

How do I log on ! ? :) lol

[http://www.youtube.com/watch?v=-RgcZlGrBzQ&feature=youtu.be](http://www.youtube.com/watch?v=-RgcZlGrBzQ&feature=youtu.be)

edit: be patient :)

---

### Post by ventrical on 2012-06-04
> **jerrylamos said:**
> Being a bit frustrated (!) with quantal's startup disk creator I did a apt-get install of unetbootin.

Hey!  Unetbootin allows me to put the .iso on a partition on the USB stick.  These USB flash memories are getting to be 32 GB at $20 and quantal startup disk creator wants to use the -whole- thing for the startup?

So I've got 2 other partitions on the USB besides today's quantal daily.

BTW, running persistent like I am, I have to remember to wipe out the casper-rw partition when I load in a new .iso.

Now sometime past Ubuntu allowed me to install in a partition on the USB stick, but as far back as I've gone, Maverick, both startup disk creator and brasero (or whatever Maverick is using to write .iso) insist on using the whole USB.

Alpha 1 coming soon?  The daily updates are getting fewer.

Jerry

  I got unetbootin to install the daliy build  onto a USB in a working and bootable fashion.

Certainly somthing is up with SDC.

---

### Post by VinDSL on 2012-06-04
> **ventrical said:**
> I got unetbootin to install the daliy build  onto a USB in a working and bootable fashion.

Certainly somthing is up with SDC.
Er...

Just used SDC.  Worked fine on my USB drive! I didn't even format it.

Actually, I'm typing this from UbuQQ A1...  ;)

---

### Post by ventrical on 2012-06-05
> **VinDSL said:**
> Er...

Just used SDC.  Worked fine on my USB drive! I didn't even format it.

Actually, I'm typing this from UbuQQ A1...  ;)

Vin,

Did you use SDC while  using an existing  quantal install?

---

### Post by ventrical on 2012-06-05
Here is what I get now while trying to install qqA1.

A blue reversi warty! :)

Oh joy :)

---

### Post by VinDSL on 2012-06-05
> **ventrical said:**
> Vin,

Did you use SDC while using an existing quantal install?
Yes, I used SDC from my existing UbuQQ Pre-Alpha install.

This one...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-5-jun-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-jun-2012-1.png")[/INDENT]

---

### Post by jerrylamos on 2012-06-05
Startup Disk is getting worse and worse.  "Try Ubuntu" bails out with "Bug: unable to handle kernel1 null pointer dereference at 000000f4 - repetitively.

Choosing second item, "Install..." did work with all sorts of screen artifacts.

Also, icon "Home Folder" (nautilus) is getting so bad I can hardly do anything so I installed pcmanfm, no gem but at least it didn't crash for what I had to do.

I had this strange idea if ubuntu development wants people to test new daily builds that installing the builds would be pretty solid.  Wrong...

After a few false starts and fumbling today's 5 June zsync of daily build is up.  A bit strange, wallpaper didn't work on -3D, just the purple splat, but wallpaper does on -2D.

Jerry

---

### Post by novatillasku on 2012-06-05
I tried today with Unetbootin and install crashed also, exactly when slideshow begins.

Change graphic card too, and bug is the same.

---

### Post by ronacc on 2012-06-05
I burned a dvd and it hung on the second install screen . there are obviously several problems right now , They said they would work on the installer this time around so all we can do is keep trying and hope the devs look at this thread , I haven't got ubiquity to file a bug on itself yet .

---

### Post by ventrical on 2012-06-05
> **VinDSL said:**
> Yes, I used SDC from my existing UbuQQ Pre-Alpha install.

This one...

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-5-jun-2012-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-jun-2012-1.png")[/INDENT]


Wow....  just awesome .. those  killer wallpapers ... !! :)  How can you ever get bored ? :) lol..

---

### Post by ventrical on 2012-06-05
> **ronacc said:**
> I burned a dvd and it hung on the second install screen . there are obviously several problems right now , They said they would work on the installer this time around so all we can do is keep trying and hope the devs look at this thread , I haven't got ubiquity to file a bug on itself yet .

Thanks ronacc . Glad to know I am not the only one with  these bad .iso/SDC problems.  It seems there is somthing wrong with ATi and Nvidia right at the outset. Now to try my Intell based  PCs.

---

### Post by ronacc on 2012-06-05
hooray I finally got ubuntu-bug to submit a report , bug # 1009180 .

---

### Post by arpanaut on 2012-06-05
> **novatillasku said:**
> I tried today with Unetbootin and install crashed also, exactly when slideshow begins.

Change graphic card too, and bug is the same.
You might want to look at this bug and "Me Too" if it looks familiar. 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661)
I've had this issue since early last dev. cycle and the only  way I can get a fresh install
is through Alt.iso.  Always crashes just after user info is entered and/or just as slideshow starts...  A real pisser!  

Also reported on the QA bug tracker. Which has become much more easy this cycle, if you have a launchpad account then you just sign in and go to work. No joining team and all that, I like it!

For others in this thread, I've about given up on the SDC as it takes ages and asks to many times for permissions. I still test now and again, but have gone to using the dd method with parameters for most cases, much quicker. Live session works just fine, Ubuquity craps out every time.  One of these days it is going to complete.
Otherwise if it doesn't start working, and they kill the Alt.iso my goose is cooked!

---

### Post by ventrical on 2012-06-05
Here's what I get now.

---

### Post by novatillasku on 2012-06-05
> **arpanaut said:**
> You might want to look at this bug and "Me Too" if it looks familiar. 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661)
I've had this issue since early last dev. cycle and the only  way I can get a fresh install
is through Alt.iso.  Always crashes just after user info is entered and/or just as slideshow starts...  A real pisser!  

Also reported on the QA bug tracker. Which has become much more easy this cycle, if you have a launchpad account then you just sign in and go to work. No joining team and all that, I like it!

For others in this thread, I've about given up on the SDC as it takes ages and asks to many times for permissions. I still test now and again, but have gone to using the dd method with parameters for most cases, much quicker. Live session works just fine, Ubuquity craps out every time.  One of these days it is going to complete.
Otherwise if it doesn't start working, and they kill the Alt.iso my goose is cooked!

Thank's for your help, but i can't see Alternate-CD in daily build.¿Where i can found it?

---

### Post by ventrical on 2012-06-05
> **arpanaut said:**
> You might want to look at this bug and "Me Too" if it looks familiar. 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661)
I've had this issue since early last dev. cycle and the only  way I can get a fresh install
is through Alt.iso.  Always crashes just after user info is entered and/or just as slideshow starts...  A real pisser!  

Also reported on the QA bug tracker. Which has become much more easy this cycle, if you have a launchpad account then you just sign in and go to work. No joining team and all that, I like it!

For others in this thread, I've about given up on the SDC as it takes ages and asks to many times for permissions. I still test now and again, but have gone to using the dd method with parameters for most cases, much quicker. Live session works just fine, Ubuquity craps out every time.  One of these days it is going to complete.
Otherwise if it doesn't start working, and they kill the Alt.iso my goose is cooked!

Done.

---

### Post by ventrical on 2012-06-05
> **ronacc said:**
> hooray I finally got ubuntu-bug to submit a report , bug # 1009180 .


Way to go ronacc!  This one is a thorn in the side. :)

---

### Post by ronacc on 2012-06-05
> **ventrical said:**
> Here's what I get now.

yeah I get that one too sometimes even when I'm installing from a usb-stick :lolflag:

---

### Post by ventrical on 2012-06-05
> **arpanaut said:**
> You might want to look at this bug and "Me Too" if it looks familiar. 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1008661)
I've had this issue since early last dev. cycle and the only  way I can get a fresh install
is through Alt.iso.  Always crashes just after user info is entered and/or just as slideshow starts...  A real pisser!  


 A 'pisser' is an understatement. This one is a pisser-Plus with a captial "P":) I just zsynced the quantal daily and I got this 19:16 at the end of the file rather than Sunday, Monday .. etc.. and it won't show up in the SDC dialog window. For a minute I thought my PCs were all busted, then I thought I was going senile, then I tried it on maveric and could'nt get it  to come up. So I have to go back a re-zsync the little *pisser-Plus* of an .iso :mad:

lol

EDIT:

And a lot of good that did!  NOT!

---

### Post by jerrylamos on 2012-06-05
Latest daily build .iso can't even get a stable "Try Ubuntu...."

I took the second option, "Install..." which was successful on my tower and notebook.  Cripples along with all sorts of bizarre illegible screen artifacts but did complete.

Jerry

---

### Post by ventrical on 2012-06-05
> **jerrylamos said:**
> Latest daily build .iso can't even get a stable "Try Ubuntu...."

I took the second option, "Install..." which was successful on my tower and notebook.  Cripples along with all sorts of bizarre illegible screen artifacts but did complete.

Jerry


Bravo  for sticking it out :)

Your's is the first success story, I think.

---

### Post by sammiev on 2012-06-05
WoWser! Someone did a daily install. :guitar:

---

### Post by pressureman on 2012-06-05
> **novatillasku said:**
> Thank's for your help, but i can't see Alternate-CD in daily build.¿Where i can found it?

[http://cdimage.ubuntulinux.org/daily/](http://cdimage.ubuntulinux.org/daily/)

Try the one in "current" first - check the report.html in the directory to see if any packages were uninstallable. If there are no failures in report.html, you're pretty much guaranteed of a successful install.

If report.html lists any uninstallable packages **for your platform**, try one of the previous days' builds.

---

### Post by jerrylamos on 2012-06-06
> **pressureman said:**
> [http://cdimage.ubuntulinux.org/daily/](http://cdimage.ubuntulinux.org/daily/)

Try the one in "current" first - check the report.html in the directory to see if any packages were uninstallable. If there are no failures in report.html, you're pretty much guaranteed of a successful install.

If report.html lists any uninstallable packages **for your platform**, try one of the previous days' builds.
I looked in [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/) which is where I do my zsync's to, and did not see any "report.html".  I looked in the parent directory [http://cdimage.ubuntu.com/cdimage/daily-live](http://cdimage.ubuntu.com/cdimage/daily-live) and didn't see any "report.html" either.

Curious, if [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/) has un-installable packages why aren't there any warnings?

Frankly, it's not that there are defective packages, it's install itself that doesn't work - perhaps "ubiquity" is the un-installable package you're referring to?  Is "startup-disk creator" an uninstallable package?

As an "ordinary user" I use 3 test pc's, a wide screen notebook, a netbook, and a tower sometimes the latest zsync with Quantal startup-disk creator will install on one but not the others, sometimes it fails on all three.  Chews up a lot of time.  The wide screen notebook has an external monitor and the systems settings "Displays" crashes, segfault I think, - what is the name of the systems settings displays package?  Bug# 1007588.

Better luck with precise or oneiric or lucid startup-disk creator, or even the very primitive (!) dd which is quite particular about the format of the pen drive.  I do apt-get install of gparted and then use that to format the whole pen drive at F32.  Of course wastes a whole 4 GB (or 16 GB or 32 GB) pen drive on a 750 mb image.  Unetbootin (apt-get install) will allow putting the image into a suitably sized partition however that's not testing any ubuntu startup disk code.

Jerry

---

### Post by jerrylamos on 2012-06-06
> **pressureman said:**
> [http://cdimage.ubuntulinux.org/daily/](http://cdimage.ubuntulinux.org/daily/)

Try the one in "current" first - check the report.html in the directory to see if any packages were uninstallable. If there are no failures in report.html, you're pretty much guaranteed of a successful install.

If report.html lists any uninstallable packages **for your platform**, try one of the previous days' builds.

Typical failure with cd image daily live current ...i386.iso "Try ubuntu...." which on booting up gets "Bug: unable to handle linux1 null pointer dereference at 000000f4" and is unable to complete never gets to desktop.

Jerry

---

### Post by ventrical on 2012-06-06
I get a seamless install using unetbootin.

There seems to be something across the board with the new alpha build and Startup Disk Creator across the board because  I tried to use SDC on different releases back as far as Maveric with the same .iso (I am typing from now - qqalpha1) and there is no way it will install. Unetbootin saves the day. Is this perhaps a trend towards obsoleteling SDC?

---

### Post by novatillasku on 2012-06-06
> **pressureman said:**
> [http://cdimage.ubuntulinux.org/daily/](http://cdimage.ubuntulinux.org/daily/)

Try the one in "current" first - check the report.html in the directory to see if any packages were uninstallable. If there are no failures in report.html, you're pretty much guaranteed of a successful install.

If report.html lists any uninstallable packages **for your platform**, try one of the previous days' builds.

I install Quantal with Alternate iso.Wauuuu!!.
Thank you very much ;-p

---

### Post by pressureman on 2012-06-06
> **jerrylamos said:**
> I looked in [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/) which is where I do my zsync's to, and did not see any "report.html".  I looked in the parent directory [http://cdimage.ubuntu.com/cdimage/daily-live](http://cdimage.ubuntu.com/cdimage/daily-live) and didn't see any "report.html" either.

daily, not daily-live. Read the URL carefully.

[http://cdimage.ubuntulinux.org/daily/](http://cdimage.ubuntulinux.org/daily/)

---

### Post by ventrical on 2012-06-06
Most recent build works great now with SDC on a Quantal system. I used the "Somthing Else" option and it was a seamless install.

---

### Post by jerrylamos on 2012-06-06
6 June quantal startup disk creator on 6 June i386.iso on 2 GB USB flash:
"Try Ubuntu...." on 3.3 GHz tower with ATI radeon xpress 200 got
"Bug: unable to handle linux1 null pointer dereference at 000000f4"
then screen went to garbage, dead in the water, wouldn't do a thing.  Power off.

Re-boot then "Install Ubuntu...."
All kinds of screen artifacts and garbage fonts, was able to navigate through install which completed successfully.  Booted up running now.

On my netbook, "Try Ubuntu..." worked as intended.

On my wide screen notebook with external monitor, got usual bug #1007588 where Display Apply fails.  I'm stuck with 1024x768 on a 1280x1024 screen.  Apply won't even turn off the laptop display so I do that with keyboard.  Of course, Ubuntu boots with MAX BRIGHT on the notebook and I'm really not interested in burning it out.

Anyway, ignoring the lousy screen, install worked as intended provided I used the 2nd choice "Install Ubuntu...".

So, one fail on "Try Ubuntu.." two successes, and three successes on install.

Jerry

---

### Post by jerrylamos on 2012-06-06
"nomodeset" did enable the 3.3 GHz with ATI radeon xpress 200 to boot "Try Ubuntu...." successfully.

I first ran across the "nomodeset" workaround on Ubuntu Intrepid seems like years ago on a long ago discarded Intel graphics tower.  Obviously ubuntu development hasn't been able to fix that yet.  I suppose there might have been something in ".xession-errors" or "Xorg.0.log" but no way to tell since when "modeset" failed absolutely nothing worked. 

I've seen some explanations on why Ubuntu Development is dedicated to using "modeset" on the install disk even though failures persist.  I really don't think it's worth the risk, but since I'm just a user my opinion doesn't matter.

Jerry

---

### Post by sammiev on 2012-06-06
> **jerrylamos said:**
> "nomodeset" did enable the 3.3 GHz with ATI radeon xpress 200 to boot "Try Ubuntu...." successfully.

I first ran across the "nomodeset" workaround on Ubuntu Intrepid seems like years ago on a long ago discarded Intel graphics tower.  Obviously ubuntu development hasn't been able to fix that yet.  I suppose there might have been something in ".xession-errors" or "Xorg.0.log" but no way to tell since when "modeset" failed absolutely nothing worked. 

I've seen some explanations on why Ubuntu Development is dedicated to using "modeset" on the install disk even though failures persist.  I really don't think it's worth the risk, but since I'm just a user my opinion doesn't matter.

Jerry

Thanks for the info Jerry.

---

### Post by ronacc on 2012-06-06
quantal does not like my hardware ! today SDC wouldn't make a usb stick that my box would recognize as bootable . Up to today atleast I could get to the live desktop although the installer would hang . I installed precise release and the first quantal live cd no problem with sdc but since then no joy even when I burn a dvd the installer hangs . today I tried the alternate burned to a dvd , that got a little further but barfed its cookies right after the partitioner started during detecting drives .

---

### Post by twipley on 2012-09-24
> **jerrylamos said:**
> Quantal Startup Disk Creator made defective USB image
Sorry to revive such an old thread. I also was recently affected by this issue.

Has it been resolved? I would not wish to be stuck after installing Beta 2, if anything goes wrong, without the ability to recreate another stick.

Cheers!
twipley

---

### Post by cariboo on 2012-09-24
Until Quantal is released, we advise that you keep a working stable release, and install Quantal to a separate partition, for just the type of issue you are talking about.

---

