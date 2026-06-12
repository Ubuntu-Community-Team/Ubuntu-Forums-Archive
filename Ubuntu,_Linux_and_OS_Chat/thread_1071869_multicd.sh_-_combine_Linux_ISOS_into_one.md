---
title: "multicd.sh - combine Linux ISOS into one"
date: 2009-02-16
forum: Ubuntu, Linux and OS Chat
---

### Post by maybeway36 on 2009-02-16
multicd.sh is my script to combine several ISOs into one. It started out supporting DSL, Puppy and GParted, and now supports over 20 Linux distros (wow!) as well as any floppy disk image.
The official webiste, at which new versions can be found, is at [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/).
The old Ubuntu Forums thread was in the Other OS Talk section at [http://ubuntuforums.org/showthread.php?t=718016](http://ubuntuforums.org/showthread.php?t=718016). It was about time for a new thread anyway :)

---

### Post by maybeway36 on 2009-02-20
Version 4.3 (released recently) supports Knoppix (tested with 5.3.1 only, not sure about 6.) Grab it at the website at [http://multicd.tuxfamily.org](http://multicd.tuxfamily.org).

---

### Post by maybeway36 on 2009-02-23
Version 4.4 adds support for Austrumi and GeeXboX, thanks to PsynoKhi0.

---

### Post by FuturePilot on 2009-02-23
This looks awesome. I've been looking for some way to combine multiple tools like the Gparted live CD in one. Definitely going to check this out.

---

### Post by chris200x9 on 2009-02-23
Thank you so much I've been looking for somethin like this but everything else looked so complicate, thanks!

---

### Post by fistfullofroses on 2009-02-23
I was waitin' for you to remake ;)

It's probably good that otherOS was shutdown... we didn't have any new blood there.

---

### Post by Maximus.Psychosis on 2009-02-25
Now, I'm not sure if this where you want ideas errors for your script, but, I'm going to spill them anyways, whats the worse going to happen?... :-P

Here we go:

Brilliant idea, I had a bit if a problem getting gparted 0.3.4 (something with the error of cp: cannot stat `gparted/live': No such file or directory, or if the ISO is already (by the script itself?) mounted it doesn't like it, says something like "Copying Clonezilla..." "umount: clonezilla: not mounted")

Now instead of adding a ton of ISOs in a list, how about making a smart system that looks for a ISO in the directory, mounts it, then searches for a boot system, looks for a name if the ISO (in the boot files?) then adds it. I think even though it may be a hill to climb, but it would be worth it in the end, less mass adding ISOs to you.

The other idea is make a unetbootin plugin, so people can make a bootable USB system with this (or some sort of support, when I've tried it, it didn't work, it may just be me... :-P )
linkies for you: [http://unetbootin.wiki.sourceforge.net/createplugin](http://unetbootin.wiki.sourceforge.net/createplugin)

...and Well Done, keep up the good work!

---

### Post by maybeway36 on 2009-02-25
Lots of distributions store files in different places, which the isolinux.cfg my or may not point to, and some of these files could potenitally conflict. Because of this, it seems like it would be pretty had to write a generic script for any ISO. It could probably be done, it just wouldn't work as often. That said, I might try it sometime; I know UNetbootin does it this way.

---

### Post by Azureskies on 2009-03-19
When I try to run this with slax.iso among the others, it fails with this error message:
> cp: cannot stat `slax/slax': No such file or directory
Is there a way to fix this? Thanks in advance.
EDIT: Was using the wrong iso all along. Was using a slax 5 iso.

---

### Post by Mehall on 2009-03-30
Can we have Crunchbang Linux added?

Lite edition is probably better (it's around 450MB or something) since that leaves room for other distro's.

---

### Post by dragos240 on 2009-03-30
So does your script create a grub list that lists the different distros on bootup?

---

### Post by Mehall on 2009-03-30
> **dragos240 said:**
> So does your script create a grub list that lists the different distros on bootup?



Dunno if it's grub, but there is a boot list.

I can choose:

UBCD
DSL
DSL (to ram)
Puppy
Puppy (not to ram)
Feather
Feather (not to ram)
Feather (console)
Slitaz
Debian Net Install



For some reason the Feather options don't work, but I inly added feather because I had lots of room left, hence asking for Crunchbang ;)

EDIT: That list is probably half innaccurate, but there is certainly a boot-loader with automatically generated entries.

---

### Post by smartboyathome on 2009-03-30
> **Mehall said:**
> Can we have Crunchbang Linux added?

Lite edition is probably better (it's around 450MB or something) since that leaves room for other distro's.

It would fall under "Ubuntu LiveCD". Just rename it (or better yet, create a symlink) to ubuntu.iso.

---

### Post by maybeway36 on 2009-04-05
My script (among other things) generates the isolinux.cfg used for the ISOLINUX boot loader. Using GRUB would be possible, but most Linux CDs use ISOLINUX.

---

### Post by billgoldberg on 2009-04-05
Bookmarked.

Will try it out next weekend.

Could make a great rescue cd (gparted/supergrub,...) and mobile OS (puppy/slitaz, ...).

---

### Post by Mehall on 2009-04-05
> **billgoldberg said:**
> Bookmarked.

Will try it out next weekend.

Could make a great rescue cd (gparted/supergrub,...) and mobile OS (puppy/slitaz, ...).



You can shove UBCD on there too, so it's pretty sweet.

UBCD + gparted or something + slitaz + puppy + dsl + custom rolled Slax still leaves a bit of room :D

---

### Post by stlouisubntu on 2009-04-18
If you please, how does one pass on "arguments" to the script at execution?

I tried sudo ./multicd-4.5.sh -bmv

and the -bmv appear to have been ignored.

I wanted to omit balder freedos, omit memtest, and be verbose.

Would you please add a few examples of using these arguments in your instruction?

Otherwise, great script and ideas.  Thanks so much for sharing this.

Thanks.

---

### Post by Predatorian on 2009-04-20
howdy all, 

i was reading through this, and i found someone asking about grub. i asked the same, and a person named Saikee, was able to point me in a direction. 

my post is:

[HTML]http://www.linuxquestions.org/questions/linux-general-1/having-multiple-distros-on-a-single-flash-stick-719054/[/HTML]

i was able to get 2 out of the 5 distros to boot correctly. the errors i had are listed in the last reply on the thread.

---

### Post by stlouisubntu on 2009-04-21
As a bug report on 4.5, the newest version of Parted Magic
(which is nice as it supports ext4) does not appear to 
work with multicd 4.5 as it will not boot -- unable to 
find -- error and then drops to boot:   prompt.

version pmagic 4.0

Thanks.

---

### Post by sundar_ima on 2009-04-22
i have a problem. I could do every thing as written in the website. But after executing it just created multicd.iso file (1.8mb) inside the folder. How will you write all the mini distro in a disc. All distro combined is around 580mb (FreeNas, Puppy, Slax, Slitaz and Vyatta). For your info all are latest versions.

---

### Post by Mehall on 2009-04-22
Tried to use a multicd.iso with unetbootin. Here's the output (had to run it from a shell, otherwise no output is given, the program just dies)


7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /media/VERBATIM/Media/ISOs/multicd/multicd.iso

Extracting  menus/mboard.cfg

Everything is Ok

Size:       728
Compressed: 672415744
QProcessPrivate::createPipe: Cannot create pipe 0xb3e7dcc: Too many open files
QSocketNotifier: Invalid socket specified
QProcessPrivate::createPipe: Cannot create pipe 0xb3e7d34: Too many open files
QSocketNotifier: Invalid socket specified
QProcessPrivate::createPipe: Cannot create pipe 0xb3e7d4c: Too many open files
QSocketNotifier: Invalid socket specified
QProcessPrivate::createPipe: Cannot create pipe 0xb3e7d64: Too many open files
QSocketNotifier: Invalid socket specified

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_GB.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /media/VERBATIM/Media/ISOs/multicd/multicd.iso

Extracting  menus/main.cfg

Everything is Ok

Size:       779
Compressed: 672415744



Not had problems with any regular ISOs, so it must be to do with multicd.
Care to shed any light, or somehow fix it?

---

### Post by maybeway36 on 2009-04-23
Most live CDs only contain one kernel and initrd, with a small and simple isolinux.cfg. Multicd has a large isolinux.cfg and a lot of different kernels, and this really confuses UNetbootin. So unfortunately, it's not going to work.

---

### Post by maybeway36 on 2009-04-23
> **stlouisubntu said:**
> If you please, how does one pass on "arguments" to the script at execution?

I tried sudo ./multicd-4.5.sh -bmv

and the -bmv appear to have been ignored.

I wanted to omit balder freedos, omit memtest, and be verbose.

Would you please add a few examples of using these arguments in your instruction?

Otherwise, great script and ideas.  Thanks so much for sharing this.

Thanks.

You actually use:
```
sudo ./multicd-4.5.sh b m v
```
This was easier to write code for. ;)

---

### Post by dkoppenh on 2009-05-16
First, I want to say thanks - multicd is an awesome idea; I always hated burning a separate cd for each one of the mini-distros I wanted to play with.

I tried putting RIPLinuX-8.6 on the cd, but they changed the 32-bit kernel name from 'kernel' to 'kernel32'.  Once I made that kernel name change in multicd-4.7.sh, it built the iso.

Also, I got two errors, but it doesn't seem to have affected my particular image:
Writing isolinux.cfg...
./multicd-4.7.sh: line 2356: [: =: unary operator expected
./multicd-4.7.sh: line 2364: [: =: unary operator expected
Building CD image...

On second look, it seems to be because NBISOSLAX and NBISOTC aren't set unless NBISO is, and I wasn't building a NetbootCD.

At any rate, great job on this project!

David

---

### Post by sundar_ima on 2009-05-28
you can make multiple distro on usb too by using multicd.sh and unetbootin (windows). I have checked linux mint, slitaz and slax (for the rest of distro, i do not have iso files). used the latest version 4.7.

**suggestion**
every time i create multiple iso image, your script downloads syslinux and other packages from Internet. Is it possible to add syslinux and other required packages along with iso images and just run the script? what i mean is to run your script in **offline mode**.

---

### Post by dkoppenh on 2009-05-28
> **sundar_ima said:**
> 
**suggestion**
every time i create multiple iso image, your script downloads syslinux and other packages from Internet. Is it possible to add syslinux and other required packages along with iso images and just run the script? what i mean is to run your script in **offline mode**.

The script will include memtest and balder without downloading them, if they're in the same directory as the script.  You can also disable memtest with the m switch and disable balder with the b switch. (see [this]("http://ubuntuforums.org/showthread.php?p=7128441#post7128441") post, above)

Extract [http://www.memtest.org/download/2.11/memtest86+-2.11.bin.gz](http://www.memtest.org/download/2.11/memtest86+-2.11.bin.gz) and name it **memtest**

Put [http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/)**balder10.imz** as-is in the directory.

Unfortunately, it looks like syslinux is downloaded every time.  I have a patched version of the script which will use an existing syslinux-3.80.tar.gz in the script's directory.  I downloaded syslinux from [http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.80.tar.gz](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.80.tar.gz)

I don't have access to my version right now, but will post it later if you're interested.

David

---

### Post by sundar_ima on 2009-05-28
> **dkoppenh said:**
>  I don't have access to my version right now, but will post it later if you're interested.

David

Waiting for your script...;)

---

### Post by dkoppenh on 2009-05-28
Here it is.  I had to gzip it so the forum would let me attach it.

In addition to looking for syslinux-3.80.tar.gz in the script's directory, I fixed the errors mentioned in [my earlier post]("http://ubuntuforums.org/showthread.php?p=7291077#post7291077").

Please let me know how it works out for you.

David

---

### Post by sundar_ima on 2009-05-29
yea i also got those errors. thanks for the script :D

---

### Post by sundar_ima on 2009-05-29
> **maybeway36 said:**
> Most live CDs only contain one kernel and initrd, with a small and simple isolinux.cfg. Multicd has a large isolinux.cfg and a lot of different kernels, and this really confuses UNetbootin. So unfortunately, it's not going to work.

It is working. I have done it from unetbootin windows version. I have added Linux mint, Slax, Puppy and 

Slitaz. Initially Linux mint, Slax and Sltaz worked out of the box and puppy lead to boot Slax. Later on i found 

that path for puppy led to  vmlinuz and initrd.gz of Slax in the syslinux.cfg file. Edited the path from 

**/boot/slax/vmlinuz** to **/vmlinuz** and **/boot/slax/initrd.gz** to **/initrd.gz**. Thats it. Now i have a Mighty, 

Meddium, Mini and Micro Linux on my pendrive with hell lot of space :D

---

### Post by sundar_ima on 2009-05-29
> Please let me know how it works out for you.

**+1**

It is working perfectly. No errors and no downloading. Made one iso image 

by combining following distros / utility 

[B]Slitaz

Puppy

Slax

System Rescue CD

Knoppix

Linux Mint[/B]

Again installed multicd.iso in USB by using unibootin (windows). Works 

flawlessly except puppy which can be rectified by editing syslinux.cfg as 

i mentioned earlier....

---

### Post by maybeway36 on 2009-05-30
Good to know UNetbootin worked. :)

---

### Post by VCSkier on 2009-06-19
Thanks for this script, maybeway36.  It makes my life so much easier.  I did notice a small problem though.

The link in the script to syslinux-3.80 is broken.  Apparently kernel.org has released a newer version, and moved the old one.  I did a simple find/replace on the script to fix it, and it seems to be working now, but it's going to need to be updated.

Thanks again!

---

### Post by VCSkier on 2009-06-19
I think I've found another issue.  I ran the script and made an .iso with the new PartedMagic 4.2, as well as some other utilities.  Unfortunately, the cd will not boot PartedMagic.  The other utilities on the disc work fine...  Maybe was there a change in the structure of the new release that is causing a problem?

I checked the md5 sums, and everything checked out fine...

The output, when I try to boot PartedMagic says something like this:

```
Could not find ramdisk image:  /pmagic/initrd
boot:
```

---

### Post by maybeway36 on 2009-06-21
I released a new version 4.8 to fix both those issues. You can get it from the [home page.](http://multicd.tuxfamily.org)

---

### Post by VCSkier on 2009-06-22
I tried again with 4.8, and the script was able to fetch syslinux fine, but it still won't boot Parted Magic.  Trying to achieves the same results as before.

---

### Post by jefron on 2009-10-08
Thanks for multicd.sh.
I've got 
>                               cp: cannot stat `austrumi/austrumi': No such file or directory                      When i try to compile all iso, with austrumi 1.7.2.

Could you help me to fix this? :)

Thanks

---

### Post by kindofabuzz on 2009-11-11
I keep getting Copying Trinity Rescue Kit... trk.iso: No such file or directory. And then I get no final .iso.

---

### Post by maybeway36 on 2009-11-14
jefron and kindofabuzz - I think those issues have been fixed in the version I'm working on, because I can't reproduce them. I'll be releasing v5.0 final soon (probably within the next few days) so try that when it comes out.

---

### Post by maybeway36 on 2009-11-15
All right, version 5.0 final is out! I can't remember what all I changed, but for sure there's a plugin system now (hence the .tar.gz) and I just added Macpup. If you want it as a single script, there is a combined version also available for download.

---

### Post by Shawnotron on 2009-11-22
I followed the instructions, and when I run the script I get this:

root@shawn-desktop:~/multicd# ./multicd.sh
List of boot options that will be included:
Parted Magic
Puppy Linux
SystemRescueCd
Trinity Rescue Kit
Ultimate Boot CD
Memtest86+
root@shawn-desktop:~/multicd# 

It stops there and doesn't create an .ISO.  What am I doing wrong?

Edit:  I have discovered that the script works fine if I do not include Puppy Linux (this includes MacPuppy).  When I run the script with either of those it creates two files 'puppychooser' and 'puppyresult' and a folder named 'tags'.  Other than that the script fails to finish and no .ISO is created.

---

### Post by maybeway36 on 2009-11-25
Version 5.0.1 fixes the bug. Thanks for reporting it.
Technical explanation: The script tried to use dialog when you had a Puppy variant included, to ask the user which one should be in the CD's root directory (and therefore installable to HD.) Now it will only do so if dialog is installed - if it isn't, the script will put neither of them in the CD's root.

---

### Post by philipcs on 2009-11-27
I have tested with ubuntu 9.10 desktop and remix edition with your script, it works :D

Thanks.

---

### Post by arashiko28 on 2009-12-06
> **maybeway36 said:**
> multicd.sh is my script to combine several ISOs into one. It started out supporting DSL, Puppy and GParted, and now supports over 20 Linux distros (wow!) as well as any floppy disk image.
The official webiste, at which new versions can be found, is at [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/).
The old Ubuntu Forums thread was in the Other OS Talk section at [http://ubuntuforums.org/showthread.php?t=718016](http://ubuntuforums.org/showthread.php?t=718016). It was about time for a new thread anyway :)

In order to record 3 Ubuntu.iso, how do I differentiate them? This are: 9.10-32bits, 9.10-64-bits, 9.10 UNR

All I see is to name them ubuntu.iso

---

### Post by arashiko28 on 2009-12-06
I've done it several times, all I get is a 740kb iso with memtest in it and nothing more. I changed the files names to ubuntu32, ubuntu64 and ubuntunr; I'm dry of ideas...

---

### Post by maybeway36 on 2009-12-07
You have to name the isos "ubuntu.iso" and "ubuntu2.iso". Only two at a time are supported now, but I could probably add a third.

---

### Post by drago_d on 2010-01-14
I tested it with dsl and slax and it works! I have one question? Is it possible to make all this persistent? I tried on Slax and on the next reboot everything was gone.
Thank you very much for the script

---

### Post by The Real Dave on 2010-01-16
Nice one, combine DSL, Clonezilla, PartedMagic, Slitaz and Slax on one disk :) I hate wasting the left over space :D Thank you! :D

---

### Post by maybeway36 on 2010-01-17
> **drago_d said:**
> I tested it with dsl and slax and it works! I have one question? Is it possible to make all this persistent? I tried on Slax and on the next reboot everything was gone.
Thank you very much for the script

On the menu, highlight Slax and press Tab. Add
```
changes=/slax/
```
as a boot option and press ENTER. Come to think of it, this should probably be default.

---

### Post by drago_d on 2010-02-07
thank you ! Yes it would be great if you make it default.Once again thanks :)

---

### Post by maybeway36 on 2010-02-08
I put version 5.1 up on the website. It adds Endian Firewall and CDlinux, fixes a bug that made it so Ubuntu was nameless on the menu, and makes Slax changes default. The .tar.gz version also comes with SYSLINUX so you don't have to download it every time.

---

### Post by tonhou on 2010-02-10
Thanks for your work with this script!

I have just used it to build:

diskcopy
ntpasswd
pmagic
sysrcd
tinycore
ubcd

Here is what happens on startup for all except ubcd:
All have several screens with hexadecimal readout each line followed by:
.ERROR: idle with IF=0
After half a minute of this they all go into normal boot (except diskcopy which drops to command prompt).

Perhaps it is a bad burn, but I am not so sure.

Thanks for any guidance.

Tony

---

### Post by maybeway36 on 2010-02-13
That's happened to me on certain computers. I think it's a problem with SYSLINUX itself. If it still boots, it should be fine.

---

### Post by fontman on 2010-02-14
[SIZE=3][COLOR=Navy][SIZE=2]I was wondering if anyone can point me in the right direction. I'm relatively new to this environment, and have just installed Xubuntu 9.10. I followed the instructions by creating a folder for building the image at /home/fontman/multicd

I renamed the files to:
antix.iso
clonezilla.iso
efw.iso
knoppix.iso
pmagic.iso
sysrcd.iso
ubuntu.iso

When I run *sudo ./multicd*.sh*  I get 
**sudo: unable to execute ./multicd-5.1.sh: No such file or directory**

Are there certain dev tools I need or permissions?

Apologies if this is wrong area to ask...

[/SIZE]     
[/COLOR][/SIZE]

---

### Post by coolcat on 2010-02-21
First right click on that script file and select properties. Go to the permissions tab and make sure the box is checked to allow it to execute.
Next problem may be as follows;
You aren't in the correct directory when you are trying to execute that script.

Open a terminal and type this;

cd ./fontman/multicd

Now type this;

dir

It should show the the script file in that directory listing.
If it does try executing that file with that command..

---

### Post by maf14129 on 2010-02-23
Hi,

I just used multicd.sh 5.1 on a Debian Etch system (mkisofs 9:1.1.2-1) to combine Clonezilla 1.2.3-27, GParted 0.5.1-1, and memtest into one image.

Unfortenately, memtest is the only system I can start.

The Clonezilla entry in the initial boot menu opens the Clonezilla menu. But only the "back to main menu" entry works. Nothing happens if I select any of the others and hit enter or wait for the 30 seconds to tick down.

None of the three GParted entries in menu the seems to trigger anything.

I must be doing something wrong. I'm hoping for your assistance...

---

### Post by Aviendha09 on 2010-02-26
I'm impressed with the concept. I hashed one together and it worked well. I removed Ubuntu and put in Linux mint. As the script runs, I get this error:

cp: cannot stat `linuxmint/drivers': No such file or directory

And the process stops, leaving the linuxmint iso mounted (and unmountable). Hmmmm.

Should I cheat and call Mint Ubuntu?


PS: PCLOS would be nice too!

---

### Post by maybeway36 on 2010-02-27
> **Aviendha09 said:**
> I'm impressed with the concept. I hashed one together and it worked well. I removed Ubuntu and put in Linux mint. As the script runs, I get this error:

cp: cannot stat `linuxmint/drivers': No such file or directory

And the process stops, leaving the linuxmint iso mounted (and unmountable). Hmmmm.

Should I cheat and call Mint Ubuntu?


PS: PCLOS would be nice too!

For the Linux Mint bug, try changing this line:
```
cp -R linuxmint/drivers multicd-working/ #Drivers added by the Mint team

```
with this line:
```
if [ -d linuxmint/drivers ];then cp -R linuxmint/drivers multicd-working/;fi #Drivers added by the Mint team

```
The line is in plugins/linuxmint.sh if you downloaded the .tar.gz, or if you downloaded the single file it's somewhere in there.
And yes, PCLinuxOS would be a good idea. There's a plugin written by PsynoKhi0 for the LXDE version, but I just found a bug in that too, so I'll fix that and then see if it works with regular PCLOS.

---

### Post by chris200x9 on 2010-02-27
can it support multiple architectures? Like arch64 and arch i686? Because that'd be super handy.

---

### Post by maybeway36 on 2010-02-27
It certainly could as far as I know. You would need another plugin .sh to have both a 32-bit and a 64-bit version on the same disc. The hard part is that since they'll probably have the same folder names on both versions, one version has to be renamed and then be modified so it can find itself.
Does anyone know how to have more than one Ubuntu 9.10-based distro on one disc? I thought I had it working with 9.04 but they must have changed something with casper.

---

### Post by Aviendha09 on 2010-03-01
Ah - ha! That clinched it! burning now. Small test in VBox, looks ok. Perfect for school! Discovered Pendrivelinux has a version too. Too bad for wildbill's Billix, it's been superceded!


Uh-ho, Mint is not booting...says
> Could not find ramdisk image: /casper/initrd.gz
boot:



---

### Post by Zirafarafa on 2010-03-10
I had previously done something like this for myself to put multiple distros on a USB drive.

As this script supports more distros than mine, I thought it best just to write a script to convert the generated multicd.iso onto my usb drive.  Details are here

[http://chris.picton.nom.za/?q=node/2](http://chris.picton.nom.za/?q=node/2)

I have also patched the sysrcd and ubcd modules to keep all their files in their own subdirectories of the /boot subdirectory (to keep the USB drive clean), to put the System Rescue CD menu in a submenu by itself, and to add the version string of these to the menu

Finally, I have changed multicd.sh to accept .ima files (like the eb_on_hd.ima file), and Allow spaces in the names of image files: Etherboot Disk.ima to keep the menu looking nice

Let me know what you think of these patches...

Disk Image patch:
```

diff -uNr -x /images/ -x cd2usb.sh multicd.orig/multicd.sh multicd/multicd.sh
--- multicd.orig/multicd.sh    2010-03-07 06:07:43.000000000 +0200
+++ multicd/multicd.sh    2010-03-10 13:07:22.000000000 +0200
@@ -89,11 +89,11 @@
 done
 #END SCAN
 
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
- echo $(echo $i|sed 's/\.im.//')
+for i in *.im[agz]; do
+ echo "$i"|sed 's/\.im.//'
 done
 GAMES=0 #Will be changed if there are games
-for i in $( ls -1 games/*.im[g,z] 2> /dev/null ); do
+for i in games/*.im[agz]; do
  echo Game: $(echo $i|sed 's/\.im.//'|sed 's/games\///')
  GAMES=1
 done
@@ -146,9 +146,9 @@
 
 #The below chunk copies floppy images.
 j="0"
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
+for i in *.im[agz]; do
     echo -n Copying $(echo $i|sed 's/\.im.//')"... "
-    cp $i multicd-working/boot/$j.img
+    cp "$i" multicd-working/boot/$j.img
     if [ $VERBOSE = 1 ];then
         echo "Saved as "$j".img."
     else
@@ -161,7 +161,7 @@
 if [ $GAMES = 1 ];then
     k="0"
     mkdir -p multicd-working/boot/games
-    for i in $( ls -1 games/*.im[g,z] 2> /dev/null ); do
+    for i in games/*.im[agz]; do
         echo -n Copying $(echo $i|sed 's/\.im.//'|sed 's/games\///')"... "
         cp $i multicd-working/boot/games/$k.img
         if [ $VERBOSE = 1 ];then
@@ -249,9 +249,9 @@
 
 #BEGIN DISK IMAGE ENTRY#
 j="0"
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
+for i in *.im[agz]; do
   BASICNAME=$(echo $i|sed 's/\.im.//')
-  echo label $BASICNAME >> multicd-working/boot/isolinux/isolinux.cfg
+  echo label "$BASICNAME" >> multicd-working/boot/isolinux/isolinux.cfg
   echo kernel memdisk >> multicd-working/boot/isolinux/isolinux.cfg
   echo append initrd=/boot/$j.img >> multicd-working/boot/isolinux/isolinux.cfg
   j=$( expr $j + 1 )

```System Rescue CD patch:
```

diff -uNr -x /images/ -x cd2usb.sh multicd.orig/plugins/sysrcd.sh multicd/plugins/sysrcd.sh
--- multicd.orig/plugins/sysrcd.sh    2010-01-03 23:00:02.000000000 +0200
+++ multicd/plugins/sysrcd.sh    2010-03-10 11:05:37.000000000 +0200
@@ -34,37 +34,58 @@
         umount sysrcd
     fi
     mount -o loop sysrcd.iso sysrcd/
-    cp sysrcd/sysrcd.* multicd-working/ #Compressed filesystem
     mkdir multicd-working/boot/sysrcd
+    cp sysrcd/sysrcd.* multicd-working/boot/sysrcd/ #Compressed filesystem
     cp sysrcd/isolinux/altker* multicd-working/boot/sysrcd/ #Kernels
     cp sysrcd/isolinux/rescue* multicd-working/boot/sysrcd/ #Kernels
     cp sysrcd/isolinux/initram.igz multicd-working/boot/sysrcd/initram.igz #Initrd
+    cp sysrcd/version multicd-working/boot/sysrcd/version
     umount sysrcd
     rmdir sysrcd
     fi
 elif [ $1 = writecfg ];then
 if [ -f sysrcd.iso ];then
-cat >> multicd-working/boot/isolinux/isolinux.cfg << "EOF"
+VERSION=$(cat multicd-working/boot/sysrcd/version)
+cat >> multicd-working/boot/isolinux/isolinux.cfg << EOF
+label sysrcd
+menu label ---> ^System Rescue Cd ($VERSION)
+com32 menu.c32
+append sysrcd.cfg
+
+EOF
+
+cat > multicd-working/boot/isolinux/sysrcd.cfg << EOF
+menu title System Rescue CD
+
 label rescuecd0
 menu label ^SystemRescueCd 32-bit
 kernel /boot/sysrcd/rescuecd
-append initrd=/boot/sysrcd/initram.igz
+append initrd=/boot/sysrcd/initram.igz subdir=/boot/sysrcd
+
 label rescuecd1
 menu label SystemRescueCd 64-bit
 kernel /boot/sysrcd/rescue64
-append initrd=/boot/sysrcd/initram.igz
+append initrd=/boot/sysrcd/initram.igz subdir=/boot/sysrcd
+
 label rescuecd2
 menu label SystemRescueCd 32-bit (alternate kernel)
 kernel /boot/sysrcd/altker32
-append initrd=/boot/sysrcd/initram.igz video=ofonly
+append initrd=/boot/sysrcd/initram.igz video=ofonly subdir=/boot/sysrcd
+
 label rescuecd3
 menu label SystemRescueCd 64-bit (alternate kernel)
 kernel /boot/sysrcd/altker64
-append initrd=/boot/sysrcd/initram.igz video=ofonly
+append initrd=/boot/sysrcd/initram.igz video=ofonly subdir=/boot/sysrcd
+
 label rescuecd-rootauto
 menu label SysRCD: rescue installed Linux (root=auto; 32-bit)
 kernel /boot/sysrcd/rescuecd
-append initrd=/boot/sysrcd/initram.igz root=auto
+append initrd=/boot/sysrcd/initram.igz root=auto subdir=/boot/sysrcd
+
+label back
+menu label Back to main menu
+com32 menu.c32
+append isolinux.cfg
 EOF
 fi
 else

```Ultimate Boot CD Patch
```

diff -uNr -x /images/ -x cd2usb.sh multicd.orig/plugins/ubcd.sh multicd/plugins/ubcd.sh
--- multicd.orig/plugins/ubcd.sh    2009-11-29 00:03:14.000000000 +0200
+++ multicd/plugins/ubcd.sh    2010-03-10 11:55:44.000000000 +0200
@@ -46,21 +46,28 @@
             umount ubcd
         fi
         mount -o loop ubcd.iso ubcd/
-        cp -r ubcd/dosapps multicd-working/
-        cp -r ubcd/images multicd-working/
-        cp -r ubcd/menus multicd-working/
-        cp -r ubcd/boot/* multicd-working/boot/ #Some boot files needed for UBCD
+        mkdir -p multicd-working/boot/ubcd/
+        cp -r ubcd/dosapps multicd-working/boot/ubcd/
+        cp -r ubcd/images multicd-working/boot/ubcd/
+        cp -r ubcd/menus multicd-working/boot/ubcd/
+        sed -i 's^/boot/^/boot/ubcd/boot/^g' multicd-working/boot/ubcd/menus/*
+        sed -i 's^/menus/^/boot/ubcd/menus/^g' multicd-working/boot/ubcd/menus/*
+        sed -i 's^/images/^/boot/ubcd/images/^g' multicd-working/boot/ubcd/menus/*
+        cp -r ubcd/boot multicd-working/boot/ubcd/ #Some boot files needed for UBCD
         cp ubcd/isolinux/sbm.cbt multicd-working/boot/isolinux/sbm.cbt #Smart Boot Manager
+        VERSION=$(head -n 1 ubcd/menus/defaults.cfg | awk '{ print $6 }')
+        echo "$VERSION" > multicd-working/boot/ubcd/version
         umount ubcd
         rmdir ubcd
     fi
 elif [ $1 = writecfg ];then
 if [ -f ubcd.iso ];then
-cat >> multicd-working/boot/isolinux/isolinux.cfg << "EOF"
+VERSION=$(cat multicd-working/boot/ubcd/version)
+cat >> multicd-working/boot/isolinux/isolinux.cfg << EOF
 label ubcd
-menu label ^Ultimate Boot CD - Main menu
+menu label ---> ^Ultimate Boot CD ($VERSION) - Main menu
 com32 menu.c32
-append /menus/main.cfg
+append /boot/ubcd/menus/main.cfg
 EOF
 fi
 else

```

---

### Post by Zirafarafa on 2010-03-10
> **Zirafarafa said:**
> Finally, I have changed multicd.sh to accept .ima files (like the eb_on_hd.ima file), and Allow spaces in the names of image files: Etherboot Disk.ima to keep the menu looking nice

Just realized that the patch is not good if disk images/games do not exist - this one is better.  The reason for the change from the $(ls -1 *.im[g,z]) is to support images with spaces in their names

Disk Image patch:
```
diff -uNr -x /images/ -x cd2usb.sh multicd.orig/multicd.sh multicd/multicd.sh
--- multicd.orig/multicd.sh    2010-03-07 06:07:43.000000000 +0200
+++ multicd/multicd.sh    2010-03-10 15:43:55.000000000 +0200
@@ -89,11 +89,13 @@
 done
 #END SCAN
 
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
- echo $(echo $i|sed 's/\.im.//')
+for i in *.im[agz]; do
+ test "$i" = "*.im[agz]" && continue
+ echo "$i"|sed 's/\.im.//'
 done
 GAMES=0 #Will be changed if there are games
-for i in $( ls -1 games/*.im[g,z] 2> /dev/null ); do
+for i in games/*.im[agz]; do
+ test "$i" = "games/*.im[agz]" && continue
  echo Game: $(echo $i|sed 's/\.im.//'|sed 's/games\///')
  GAMES=1
 done
@@ -146,9 +148,10 @@
 
 #The below chunk copies floppy images.
 j="0"
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
+for i in *.im[agz]; do
+    test "$i" = "*.im[agz]" && continue
     echo -n Copying $(echo $i|sed 's/\.im.//')"... "
-    cp $i multicd-working/boot/$j.img
+    cp "$i" multicd-working/boot/$j.img
     if [ $VERBOSE = 1 ];then
         echo "Saved as "$j".img."
     else
@@ -161,7 +164,8 @@
 if [ $GAMES = 1 ];then
     k="0"
     mkdir -p multicd-working/boot/games
-    for i in $( ls -1 games/*.im[g,z] 2> /dev/null ); do
+    for i in games/*.im[agz]; do
+        test "$i" = "games/*.im[agz]" && continue
         echo -n Copying $(echo $i|sed 's/\.im.//'|sed 's/games\///')"... "
         cp $i multicd-working/boot/games/$k.img
         if [ $VERBOSE = 1 ];then
@@ -249,9 +253,10 @@
 
 #BEGIN DISK IMAGE ENTRY#
 j="0"
-for i in $( ls -1 *.im[g,z] 2> /dev/null); do
+for i in *.im[agz]; do
+  test "$i" = "*.im[agz]" && continue
   BASICNAME=$(echo $i|sed 's/\.im.//')
-  echo label $BASICNAME >> multicd-working/boot/isolinux/isolinux.cfg
+  echo label "$BASICNAME" >> multicd-working/boot/isolinux/isolinux.cfg
   echo kernel memdisk >> multicd-working/boot/isolinux/isolinux.cfg
   echo append initrd=/boot/$j.img >> multicd-working/boot/isolinux/isolinux.cfg
   j=$( expr $j + 1 )

```

---

### Post by maybeway36 on 2010-03-10
I think I found another way to handle files with spaces as well as no file at all. Instead of doing
```
for i in $(ls -1 *.im[agz] 2> /dev/null);do
```
I can use
```
(ls -1 *.im[agz] 2> /dev/null | while read i;do
```
I haven't tested your way or mine, because I'm booted into Windows right now :P I'll try it out when I'm in Linux again.
The patches will definitely be useful. Is it OK if I integrate them into the next version?

Also, I can't believe I actually typed this:
```
echo $(echo $i|sed 's/\.im.//')
```
That's like having one guy say something and getting another guy to repeat it when the first guy is right there in front of you.

---

### Post by Zirafarafa on 2010-03-11
> **maybeway36 said:**
> I think I found another way to handle files with spaces as well as no file at all. Instead of doing
```
for i in $(ls -1 *.im[agz] 2> /dev/null);do
```I can use
```
(ls -1 *.im[agz] 2> /dev/null | while read i;do
```
That would work just as well (With the extra '(' removed from the front).

Alternatively, 
```

for i in games/*.im[agz]; do
   test -r "$i" || continue

```will handle missing files as well as those not readable (permissions/broken symlinks/etc)

> **maybeway36 said:**
>  The patches will definitely be useful. Is it OK if I integrate them into the next version?


Please do

---

### Post by Zirafarafa on 2010-03-12
With my goal of being able to put this onto a USB drive, I am trying to get the distros fuly contained within their own /boot directory on the image.  This will keep the USB drive clean, as well as allow similar distros to coexist (mint/ubuntu)

Also, I am trying to use the distros original isolinux.cfg as much as possibe in its own submenu (So that distro upgrades are less likely to affect the script)

Do you think these are useful things to patch in your script?  If so, I will work through the distros I generally use to get them patched as above.

---

### Post by maybeway36 on 2010-03-14
Patches like those would be quite useful. Some distros don't want to stay in their own folder, but having the script extract and edit files in the initrd.gz would be a possibility.
I'm going to try to learn how to use git so I can set up a repository on my tuxfamily site.

---

### Post by sundar_ima on 2010-03-15
When grub2 can be used to boot multiple iso of same distro family (ubuntu, linuxmint...etc) files then why cant you replace syslinux with grub2.

---

### Post by maybeway36 on 2010-03-16
multicd 5.3 lets you use Linux Mint and Ubuntu (and BackTrack and WeakNet Linux) on the same DVD now. The ubuntu2 plugin, which lets you add another Ubuntu 9.10+ image, has also been added. If the script finds ubuntu2.iso and you have "dialog" installed, it will ask you what to call it on the menu.
I also set up a git repository:
```
git clone git://git.tuxfamily.org/gitroot/multicd/multicd.git
```
It's pretty much the same stuff you'll get in the .tar.gz. If I add a new feature but it's not enough to justify releasing it yet, I might push it into here.

---

### Post by Zirafarafa on 2010-03-17
Hi

My patch here for linuxmint (against 5.2) doesn't require initrd editing and allows all files to go into /boot/linuxmint, by using the live-media-path parameter.

No idea yet if this will work for other ubuntu clones.

Also, it modifies and uses the original mint isolinux.cfg in a submenu.

```

--- multicd.orig/plugins/linuxmint.sh    2010-03-11 17:12:16.000000000 +0200
+++ multicd/plugins/linuxmint.sh    2010-03-12 15:38:22.000000000 +0200
@@ -42,25 +42,51 @@
             umount linuxmint
         fi
         mount -o loop linuxmint.iso linuxmint/
-        cp -R linuxmint/casper multicd-working/ #Live system
-        if [ -d linuxmint/drivers ];then cp -R linuxmint/drivers multicd-working/;fi #Drivers added by the Mint team
-        cp -R linuxmint/preseed multicd-working/ #Tells the installer what to install
+        cp -R linuxmint/casper multicd-working/boot/linuxmint #Live system
+        if [ -d linuxmint/drivers ];then cp -R linuxmint/drivers multicd-working/;fi #Drivers added by the Mint team - not working for USB
+        cp -R linuxmint/preseed multicd-working/boot/linuxmint #Tells the installer what to install
         cp -R linuxmint/.disk multicd-working/ #A few more helper files
+        cp -R linuxmint/isolinux/splash.jpg multicd-working/boot/isolinux/linuxmint.jpg #A few more helper files
+        
+        # Fix the isolinux.cfg
+        cp linuxmint/isolinux/isolinux.cfg multicd-working/boot/linuxmint/linuxmint.cfg
+        sed -i 's@file=/cdrom/preseed/@file=/boot/linuxmint/preseed/@g' multicd-working/boot/linuxmint/linuxmint.cfg
+        sed -i 's^initrd=/casper/^live-media-path=/boot/linuxmint initrd=/boot/linuxmint/^g' multicd-working/boot/linuxmint/linuxmint.cfg
+        sed -i 's^kernel /casper/^kernel /boot/linuxmint/^g' multicd-working/boot/linuxmint/linuxmint.cfg
+        sed -i 's^splash.jpg^linuxmint.jpg^g' multicd-working/boot/linuxmint/linuxmint.cfg
+        mv multicd-working/.disk/casper-uuid-generic multicd-working/.disk/casper-uuid-mint
+        
         umount linuxmint
         rmdir linuxmint
     fi
 elif [ $1 = writecfg ];then
 if [ -f linuxmint.iso ] && [ ! -f ubuntu.iso ];then
-cat >> multicd-working/boot/isolinux/isolinux.cfg << "EOF"
-label mint-live
-  menu label ^Try Linux Mint without any change to your computer
-  kernel /casper/vmlinuz
-  append  file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.gz quiet splash --
-label mint-live-install
-  menu label ^Install Linux Mint
-  kernel /casper/vmlinuz
-  append  file=/cdrom/preseed/mint.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
+cat >> multicd-working/boot/isolinux/isolinux.cfg << EOF
+label linuxmint
+menu label ---> Linux ^Mint Menu
+com32 vesamenu.c32
+append /boot/linuxmint/linuxmint.cfg
+
 EOF
+
+cat >> multicd-working/boot/linuxmint/linuxmint.cfg << EOF
+
+label back
+menu label Back to main menu
+com32 menu.c32
+append /boot/isolinux/isolinux.cfg
+
+EOF
+
+#label mint-live
+#  menu label ^Try Linux Mint without any change to your computer
+#  kernel /casper/vmlinuz
+#  append  file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.gz quiet splash --
+#label mint-live-install
+#  menu label ^Install Linux Mint
+#  kernel /casper/vmlinuz
+#  append  file=/cdrom/preseed/mint.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
+#EOF
 fi
 else
     echo "Usage: $0 {scan|copy|writecfg}"

```

---

### Post by Zirafarafa on 2010-03-17
And here is a pentoo plugin...

```

#!/bin/sh
set -e
#Pentoo plugin for multicd.sh
#version 5.1?
#Copyright (c) 2009 maybeway36
#
#Permission is hereby granted, free of charge, to any person obtaining a copy
#of this software and associated documentation files (the "Software"), to deal
#in the Software without restriction, including without limitation the rights
#to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#copies of the Software, and to permit persons to whom the Software is
#furnished to do so, subject to the following conditions:
#
#The above copyright notice and this permission notice shall be included in
#all copies or substantial portions of the Software.
#
#THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#THE SOFTWARE.

# BUGS
# modules directory is not read correctly, as it is searched for in /

if [ $1 = scan ];then
    if [ -f pentoo.iso ];then
        echo "Pentoo Linux"
    fi
elif [ $1 = copy ];then
    if [ -f pentoo.iso ];then
        echo "Copying Pentoo Linux..."
        if [ ! -d pentoo ];then
            mkdir pentoo
        fi
        if grep -q "`pwd`/pentoo" /etc/mtab ; then
            umount pentoo
        fi
        mount -o loop pentoo.iso pentoo/
      mkdir -p multicd-working/boot/pentoo
        cp -R pentoo/{modules,tools,win32,image.squashfs,livecd} multicd-working/boot/pentoo
        cp pentoo/isolinux/{pentoo,isolinux.cfg,pentoo.igz} multicd-working/boot/pentoo
        
        # Fix the isolinux.cfg
        sed -i 's@loop=/image.squashfs@loop=/boot/pentoo/image.squashfs subdir=/boot/pentoo@' multicd-working/boot/pentoo/isolinux.cfg
        sed -i 's@kernel @kernel /boot/pentoo/@' multicd-working/boot/pentoo/isolinux.cfg
        sed -i 's@initrd=@initrd=/boot/pentoo/@' multicd-working/boot/pentoo/isolinux.cfg
        
        umount pentoo
        rmdir pentoo
    fi
elif [ $1 = writecfg ];then
if [ -f pentoo.iso ];then
cat >> multicd-working/boot/isolinux/isolinux.cfg << EOF
label pentoo
menu label ---> ^Pentoo Menu
com32 menu.c32
append /boot/pentoo/isolinux.cfg

EOF

cat >> multicd-working/boot/pentoo/isolinux.cfg << EOF

label back
menu label Back to main menu
com32 menu.c32
append /boot/isolinux/isolinux.cfg

EOF

fi
else
    echo "Usage: $0 {scan|copy|writecfg}"
    echo "Use only from within multicd.sh or a compatible script!"
    echo "Don't use this plugin script on its own!"
fi

```

---

### Post by maybeway36 on 2010-03-17
Zirafarafa: I guess I didn't realize there was a boot option now. I'll test that Mint plugin out, and if it works (it looks like it should) I'll apply that idea to ubuntu2.sh also. Backtrack and WeakNet use an older version of casper that doesn't lave the live-media-path option.
Also, thanks for the pentoo plugin. I'll change the version number to 5.4 (for plugins I use the version at which they were last updated) and put your name on the copyright.

---

### Post by maf14129 on 2010-04-03
Some time ago I reported a problem using multicd.sh which hasn't triggered a reply yet. I hope it's okay to repeat my question? Here it goes:

 > I just used multicd.sh 5.1 on a Debian Etch system (mkisofs 9:1.1.2-1)  to combine Clonezilla 1.2.3-27, GParted 0.5.1-1, and memtest into one  image.

Unfortenately, memtest is the only system I can start.

The Clonezilla entry in the initial boot menu opens the Clonezilla menu.  But only the "back to main menu" entry works. Nothing happens if I  select any of the others and hit enter or wait for the 30 seconds to  tick down.

None of the three GParted entries in menu the seems to trigger anything.May be, someone could point out what I should do differently. Thanks in advance!

---

### Post by maybeway36 on 2010-04-06
Have you tried the newest version yet? I think I might have fixed some bugs in those two plugins.

---

### Post by maf14129 on 2010-04-07
Thanks for your help.

I now used multicd.sh 5.3 to combine clonezilla-live-1.2.4-28-686.iso, gparted-live-0.5.2-1.iso, and ubcd411.iso. It's 2 out of 4 for me, right now:
 - memtest works fine
  - Clonezilla works fine
  - GParted still does not start
  - UBCD starts but runs into a problem during boot and stalls:
```
 - InitDiskBIOS reported 0 sectors/track, assuming 63

Invalid Opcode at F000 9F00 ...
```This is the multicd.sh output:
```
spiro:/pub/linux/multicd/multicd-5.3# ./multicd.sh
List of boot options that will be included:
Clonezilla
GParted Live
Ultimate Boot CD
Memtest86+

Continuing in 3 seconds - press Ctrl+C to cancel
Copying Clonezilla...
Copying GParted Live...
Copying Ultimate Boot CD...
Downloading SYSLINUX...
Unpacking and copying files...
Writing isolinux.cfg...
Building CD image...
Unknown file type (unallocated) multicd-working/.. - ignoring and continuing.
```

---

### Post by Bobhuber on 2010-04-16
> **maybeway36 said:**
> multicd.sh is my script to combine several ISOs into one. It started out supporting DSL, Puppy and GParted, and now supports over 20 Linux distros (wow!) as well as any floppy disk image.
The official webiste, at which new versions can be found, is at [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/).
The old Ubuntu Forums thread was in the Other OS Talk section at [http://ubuntuforums.org/showthread.php?t=718016](http://ubuntuforums.org/showthread.php?t=718016). It was about time for a new thread anyway :)
Fantastic Script !! 
Small problem. I downloaded the most recent Gparted-Live iso (0.5.2-1) and transfered it and Clonezilla.iso (V 1.2.2.31) using your script.Gparted  did nothing when I selected it from the menu after booting into the CD.
Going back to version 0.4.6 of Gparted fixed the problem. 
Thanks and keep up the good work.

---

### Post by arashiko28 on 2010-04-22
I need to create a DVD with the upcoming version of Ubuntu 10.04, 32-bits, 64-bits and Lubuntu. Will it be updated the script to add these?

---

### Post by maybeway36 on 2010-04-24
You can name one ubuntu.iso and another one ubuntu2.iso. It hasn't been tested with 10.04 yet but I would think it would work. I should really add an ubuntu3 plugin; that shouldn't be too hard.
Also install the program "dialog" so you can name each of them when you run the script.

---

### Post by fireballtr on 2010-05-05
Anyone have luck getting 5.4 to work with UNetbootin? Figured I would give this a try and when I try to use unet it will hang at 0% on extracting and copying files (extracting bootloader configuration). After about 10 minutes it simply closes the program.

---

### Post by maybeway36 on 2010-05-17
Honestly, I don't test it with UNetBootin. It used to work. My first instinct would be that some distros have submenus now, but I would think UNetBootin would take that into account.

---

### Post by rudregues on 2010-05-18
DSL is not functioning correctly.
I just can't choose between any boot option by pressing F4, using normal livecd I can choose the display resolution.
The probelm is:
If I don't choose the right display, the screen begin to display a "Not optimum mode, recommended mode 1024x768x24".

It seems like a 'default booter', without boot options.

---

### Post by maf14129 on 2010-05-19
I'm still looking for a solution of the problem I reported [in this earlier post]("http://ubuntuforums.org/showpost.php?p=9087329&postcount=75") regarding multicd.sh 5.3 in combination with  gparted-live-0.5.2-1.iso and ubcd411.iso.

Have you had success including GParted and UBCD? Any suggestions what I should try? Thanks in advance!

---

### Post by maybeway36 on 2010-05-22
@rudregues: Thanks for telling me this. In the next version, DSL will have a submenu. To download multicd with the DSL submenu feature now, use git:
```
git clone git://git.tuxfamily.org/gitroot/multicd/multicd.git
```
EDIT: Okay, the git repo has now been updated with the DSL menu feature.

@maf14129: With multicd.sh version 5.4, both gparted-live-0.5.2-1.iso and ubcd411.iso work perfectly for me when testing them in QEMU. If you still have problems, it might be the computer you're running it on. You can use the original CD images to check.

---

### Post by jerome_bc on 2010-05-26
The script does not work for the new Arch install CD. I'm working on a fix but I'm using the netinstall i386 CD and I doubt any fix I come up with will work with the dual (i386+x86_64) CD.

EDIT

Also there's an extra ']' on line 56 of freedos.sh.

---

### Post by maf14129 on 2010-05-26
> **maybeway36 said:**
> @maf14129: With multicd.sh version 5.4, both gparted-live-0.5.2-1.iso and ubcd411.iso work perfectly for me when testing them in QEMU. If you still have problems, it might be the computer you're running it on. You can use the original CD images to check.

Same result here. I successfully combined und ran clonezilla-live-1.2.4-28-686.iso, gparted-live-0.5.2-9.iso, and ubcd411.iso. Unfortenately, many of the UBCD tools I tested stall when booting FreeDOS. The last two lines are
```
 - InitDiskBIOS reported 0 sectors/trac, assuming 63!

Invalid Opcode at F000 9F00 0246 F601 A003 0E00 0004 6504 0002 1100 00E8 0000 0000
```In the meantime, UBCD has moved to release 5.0 and has [SIZE=2][completely changed its directory structure]("http://www.ultimatebootcd.com/news.html"). The old ubcd.sh plugin does not work anymore. I changed lines like
[/SIZE]```
cp -r ubcd/dosapps multicd-working/boot/ubcd/
``` to ```
cp -r ubcd/ubcd/dosapps multicd-working/boot/ubcd/
```But that's not all. The next error is ```
sed: couldn't edit multicd-working/boot/ubcd/menus/grub4dos: not a regular file
```I did not dare to fool around with the menus, though... Could you possibly update ubcd.sh?

Thanks, maf14129

---

### Post by jerome_bc on 2010-05-30
I fixed the script for the arch install cd and I made a new one for the dual cd. I tested archdual.sh on vbox and 2 machines, and arch.sh on vbox only. Feel free to add them to the repo, modify them or whatever, as per the license.

---

### Post by neoargon on 2010-05-30
Your script is great .I always wished for one like this but there is one problem .The script doesn't detect kubuntu . what to do ?

---

### Post by jerome_bc on 2010-05-30
Rename it to ubuntu.iso. Or ubuntu2.iso if you want to put both Ubuntu and Kubuntu.

---

### Post by neoargon on 2010-05-30
After changing name of Kubuntu to ubuntu2, it works. Bet what if I have to add another ubuntu varient,say xubuntu or lubuntu? Will changing to ubuntu3 or ubuntu4 work ?.

---

### Post by jerome_bc on 2010-05-30
No. As it is the script only works for 2 versions. Honestly though I think it's a waste of space to put multiple variants. I suggest you just put regular Ubuntu and install the desktop you want afterward, i.e.

apt-get install xubuntu-desktop, lubuntu-desktop or kubuntu-desktop

then

apt-get remove ubuntu-desktop

if you want to get rid of gnome. I'm sure there's a way to download the *buntu-desktop packages and their dependencies (the dependencies is the important part) and put them on the CD, so you won't have to redownload them every time, but I'm not too familiar with apt-get as Arch is my main OS. You can look it up in the man page for apt-get.

---

### Post by neoargon on 2010-06-16
Hi 
I created some plugin scripts . they are :
1.kubuntu.sh
2.ubuntu-64-bit.sh
3.kubuntu_64_bit.sh
4.ubuntu_32_bit.sh
5.kubuntu_32_bit.sh

Please merge atleast the kubuntu.sh script to the upstream. Because, most people consider kubuntu as a separate distro. changing name to ubuntu2 is not the best idea since it would be confusing to know which one is kubuntu while booting. It also would not be a good idea if one wish to give a disk with both ubuntu and kubuntu to a friend since the friend won't know which one is kubuntu.

kubuntu and ubuntu 32 and 64 bits are for people who wish to include both 32 and 64 bit versions  of ubuntu

---

### Post by JT9161 on 2010-07-16
(Sorry if I'm bumping a thread that's past it's date)

Is it possible to add support for OPHCrack and is there a method to add it to an existing ISO or modify the script ? I tried just renaming the OPHCrack XP and Vista ISOs to slax1 and slax2 but it did not get added.

---

### Post by maf14129 on 2010-08-22
I just tried to download version 5.6.1 from [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/). Could it be that the packed archiv is an empty file?

---

### Post by maybeway36 on 2010-08-23
It works for me:
[[IMG]http://img651.imageshack.us/img651/6525/83678870.th.png[/IMG]](http://img651.imageshack.us/my.php?image=83678870.png)

---

### Post by Artemis Fowl on 2010-08-23
Sorry for being the newbie here, but sense posting here does not appear to add to your post count, I'll go ahead and ask.
What would be the point?

---

### Post by jerome_bc on 2010-08-23
The link in maybeway36's sig will tell you everything you need to know. Being a newbie is fine but you should [do your homework before asking simple questions.]("http://catb.org/esr/faqs/smart-questions.html")

---

### Post by Artemis Fowl on 2010-08-23
Thanks, Jerome. That will come in handy for the campaign to convert my city to linux I'm going to start someday.

---

### Post by maf14129 on 2010-08-24
> **maybeway36 said:**
> It works for me: ...

Yeah, thanks for checking! Works for me too - now. Must have been a temporary problem.

---

### Post by yogurt06 on 2010-09-02
Maybe someone could shed some light on this for me. When testing a multicd.iso in VirtualBox, I sometimes get an error. I don't remember what it is exactly, and of course I cant replicate it right now :rolleyes:. It says something about "EDD: no DEFAULT or UI..." blah blah blah. If i remember correctly, it gives me an error code 0c00, or 00c0 and a memory address that it supposedly cant read from. Searching for something along the lines of EDD: 0c00 turns up nothing. As soon as I move the file however, it reads just fine. It also works after I burn it (both from the burnt disk, and the .iso).

Also, OPHCrack plugin.

EDIT:

Of course, as soon as I post, I got the error:

```

ISOLINUX 4.02 2010-07-21 ETCD Copyright (C) 1994-2010 H. Peter Anvin et al
EDD: Error 0c00 reading sector 643993
No DEFAULT or UI configuration directive found!
boot: _

```

EDIT2:

Updated ophcrack plugin. Name the XP iso ophxp.iso, and the Vista iso ophvista. If you only have one iso, thats fine too. If you have both, it will build both into one.

*NOTE* I have only tested that it boots, not that it actually works, as I do not have a Windows machine to test it on.

---

### Post by maybeway36 on 2010-09-03
I just posted a new version, 5.7. You'll notice the [website](http://multicd.tuxfamily.org) is brand-new, thanks to someone who contacted me via e-mail. A Spanish translation will be up soon too - this is also not my work ;)
The Slax plugin now works with Slax Remix. I also added support for Damn Vulnerable Linux, Caine, and the Windows 98 SE and Windows Me installation disks. (Can anyone who owns an OEM CD of Windows Me see if it works? I'm not sure if the ISO I used was official or not.)

@yogurt26 - I just saw your problem now, so I haven't been able to look at it yet. But it sounds like it might be some sort of error with your computer. If it works when you move or burn it, maybe try making a new folder for MultiCD and making one from there.

---

### Post by zmi007 on 2010-09-03
I am in trouble with ubuntu_32_bit
My image contains 4 OS versions: kubuntu 32 & 64 bit and the same for ubuntu
Now 3 of them are starting ok,  but ubuntu_32_bit says:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom//boot/ubuntu_32_bit/filesystem.squashfs) on //filesystem.squashfs

Any idea?

P.S And many THANKS for scripts, finally I have got my wanted DVD (with knoppix, systemrescuecd, backtrack, mint and 10 more distros :) )

---

### Post by yogurt06 on 2010-09-04
@maybeway36

I'm not too worried about it, I was just wondering if anyone else had seen it. Also, I have modified my copy of the script. While I doubt that has anything to do with it, it is possible.

On that note, I sent you an email.

> **maybeway36 said:**
> I also added support for Damn Vulnerable Linux, **Caine**, and the Windows 98 SE and Windows Me installation disks.


Maybe I'm crazy, but is this plugin not included? I couldn't find it in the .tar.gz or the git repo, and found no trace of it in the combined version.

And feel free to include the ophcrack script if you wish. However, I may do some more work on it, so that you can include xp and vista on the same iso (if this is possible).

EDIT:

I updated my ophcrack script. Get it from my previous post. It now can use both the XP and Vista versions.

*NOTE* I have only tested that it boots, not that it actually works, as I do not have a Windows machine to test it on.

---

### Post by Thryn on 2010-09-08
When I tried to run it, as described on the website, it gave me the following complaint and then quit:
Copying Kubuntu...
cp: impossible d'évaluer «kubuntu/isolinux/text.cfg»: Aucun fichier ou dossier de ce type

Which in English is probably "cp: impossible to evaluate "kubuntu/isolinux/text.cfg": no file or folder of this type"

This is with the Kubuntu Maverick 64-bit beta. Same thing happens if I change the name of the file to kubuntu_64_bit.iso

I'm pretty sure it's not the iso - I've run the md5sum and it's fine. As it says, however, there is no file at isolinux/text.cfg, but there is one called txt.cfg

What do I do?


EDIT: Tried it without Kubuntu. Now the first file is PCLinuxOS LXDE, and it says:
Copying PCLinuxOS LXDE...
rm: impossible de supprimer «multicd-working/pclosLXDE/isolinux/memtest»: Aucun fichier ou dossier de ce type

translation: rm: impossible to delete "multicd-working/pclosLXDE/isolinux/memtest": no file or folder of this type

Why does it keep complaining about files that don't exist?

---

### Post by yogurt06 on 2010-09-08
These should fix your errors. 

For Kubuntu, the text.cfg was indeed renamed txt.cfg. These scripts check for both, and move whichever one exists. I don't know if this is now standard, or a typo.

For PCLinux, the latest version doesn't seem to contain memtest. So when the script tried to delete it, it couldn't find it. Again, I have no idea if this is now standard.

---

### Post by Thryn on 2010-09-09
> **yogurt06 said:**
> These should fix your errors. 

For Kubuntu, the text.cfg was indeed renamed txt.cfg. These scripts check for both, and move whichever one exists. I don't know if this is now standard, or a typo.

For PCLinux, the latest version doesn't seem to contain memtest. So when the script tried to delete it, it couldn't find it. Again, I have no idea if this is now standard.

Thanks! I now have a working multiDVD!

---

### Post by maybeway36 on 2010-09-11
Thanks, yogurt06. I applied the Kubuntu changes to the ubuntu*.sh scripts also (just in case those are renamed too), and uploaded those, the PCLinuxOS changes, and your ophcrack.sh script to the git repo. I like what you did with Ophcrack and combining its XP/Vista versions.

---

### Post by yogurt06 on 2010-09-11
No problem. You should take a second look at that ophcrack script. Towards the end there are some lines commented out that shouldn't be, and an extra command option that i use for my version of the script that you might want to remove. 

I've also been working on the main script to make the menu it creates in isolinux.cfg a little more friendly, and possibly organize some files a little better. If you would like to see any of it, I can PM you a link to my svn repo.

EDIT:
Caught a potential problem with the Arch Linux plugins. Arch looks for a disk by waiting for a certain label. The plugins seemed to notice this is needed ($ISOLABEL), but it didnt look like it got a label from anywhere. After testing my script, and the latest git repo, this was definitely the case.

To fix it, I put this: 
```

touch tags/cdlabel

echo $CDLABEL > tags/cdlabel
```Somewhere after the cd label is determined, but before the writecfg's are called. Around line 115 would be good. And here are the fixed scripts that accommodate the changes.

---

### Post by zmi007 on 2010-09-14
Is it possible to write plugin for DrWeb Live CD?

[http://www.freedrweb.com/livecd/?lng=en](http://www.freedrweb.com/livecd/?lng=en)
[http://ftp.drweb.com/pub/drweb/livecd/](http://ftp.drweb.com/pub/drweb/livecd/)

---

### Post by maybeway36 on 2010-09-15
I'll look at it. It should be possible, but I can't promise a timeframe.

---

### Post by beew on 2010-09-16
This sounds like Multiboot. Is it a similar idea except they create a usb instead of a CD?

[http://liveusb.info/dotclear/index.php?]("http://liveusb.info/dotclear/index.php?")

---

### Post by maybeway36 on 2010-09-18
Cool, I've never seen that before. It looks like uses a USB drive and has a GUI built with gtkdialog (which maybe I should check into.) My script uses CDs or DVDs, mainly because I have a bunch of those but only one spare USB drive (and it's just 1GB).
Other things that share a similar idea are [UNetbootin](http://unetbootin.sourceforge.net/) and [ULTILEX](http://ultilex.linux-bg.org/).
In other news, v5.8 out:
> #v5.8 - Added Windows 7 recovery disc plugin. Incorporated fixes for Arch Linux plugins. Various bugfixes. Step 1 now run as root again (there were file permission issues) but still checks md5sums first. (September 17, 2010)

---

### Post by borolo on 2010-09-21
Great tool. thanks.

I'm a newbie and I'm getting an error when making the disk. It starts fine and stops during puppy linux:

GParted Live
Parted Magic
Puppy Linux
Slax
SliTaz
SystemRescueCd
Trinity Rescue Kit
Ultimate Boot CD
Ubuntu
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying GParted Live...
Copying Parted Magic...
Copying Puppy...
cp: reading `puppy/lupu-511.sfs': Input/output error

any ideas?

thks

---

### Post by maybeway36 on 2010-09-22
That's an odd error. I tried putting Lucid Puppy 5.11 into the script and it worked fine for me. Usually when I see "Input/output error" in Linux it means it can't read from the disk.

---

### Post by borolo on 2010-09-23
Strange. Perhaps something wrong with the Iso and download again? I tried it on two different pcs. Will do that and let you know.

---

### Post by borolo on 2010-09-23
Ok I downloaded the iso again and it works. thanks. 

Still getting some problems with UBCD, it says that all isolinux files inside the ISO are being used and it skips them.

emilio@emilio-desktop:/mnt/ubt_xp/con nombres cambiados/multicd$ sudo ./multicd*.sh
[sudo] password for emilio: 
GParted Live
Parted Magic
Puppy Linux
SliTaz
SystemRescueCd
Trinity Rescue Kit
Ultimate Boot CD
Windows 7 Recovery Disc (Not open source - do not distribute)
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying GParted Live...
Copying Parted Magic...
Copying Puppy...
Copying SliTaz...
Copying SystemRescueCd...
Copying Trinity Rescue Kit...
Copying Ultimate Boot CD...
Can't remove multicd-working/ubcd/menus/isolinux/main.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/bios.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/cpu.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/defaults.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/main.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/memory.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/others.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/periph.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/system.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/bootmgmt.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/cloning.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/devmgmt.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/diag.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/editing.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/install.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/partmgmt.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/recovery.cfg: Text file busy, skipping file.
Can't remove multicd-working/ubcd/menus/syslinux/hdd/wiping.cfg: Text file busy, skipping file.
Can't remove multicd-working/pmagic/boot/isolinux/isolinux.cfg: Text file busy, skipping file.
Can't remove multicd-working/pmagic/boot/syslinux/syslinux.cfg: Text file busy, skipping file.
Copying Windows 7 Recovery Disc...
Downloading SYSLINUX...
Unpacking and copying files...
Writing isolinux.cfg...
Building CD image...
emilio@emilio-desktop:/mnt/ubt_xp/con nombres cambiados/multicd$

++++++++++++

Another question, once I have the iso created is there a way to boot it from a USB stick?

---

### Post by maybeway36 on 2010-09-27
> **borolo said:**
> Ok I downloaded the iso again and it works. thanks. 

Still getting some problems with UBCD, it says that all isolinux files inside the ISO are being used and it skips them.
No clue what that means. The ISO might still work, though.

> Another question, once I have the iso created is there a way to boot it from a USB stick?

You could try [UNetbootin](http://unetbootin.sourceforge.net/), but I can't guarantee that it will work.

---

### Post by ckenneal on 2010-10-06
Sorry, I am new to the forum. Great program or script you have. I made a disc similar to Borolo;

Lupu Puppy Linux 5.11
RIPlinux
Trinity Rescue Kit
Ultimate Boot CD

I did not copy some of the files from TRK (latest download TRL3.4 build 367, 2 days ago). Don't know the file structure of TRK. It seems to combine TRK into a boot directory, and then loses files. I get a menu and it boots into TRK, but choosing a TRK menu item gives error saying inodes not there, or something lots of them and moves to fast to read. I modified the puppy.sh plugin to read lupu-511 and that worked fine. So do the others. 
What is the language that the script is written in. I want to learn more about the commands. Thanks. Hope you can help.

---

### Post by acbatman54 on 2010-10-06
First off, MultiCD is awesome! Thank you for making this process a lot easier.

I just wanted to make a request. I wish I there was a way to make all of the isolinux.cfg menu options the same, i.e. either they all have submenus or none of them do. I've been bashing my head against my desk trying to get them all lined up. Out of the 7 entries I have on my menu (Local HDD, GParted, Clonezilla, DBAN, NTPASSWD, BackTrack, & Ubuntu), I can usually only get about 5 to work right. Clonezilla and BackTrack are the major pains in my ***. I'm using all of the latest ISO's. Is there a "plugin" repository somewhere that I'm not aware of?

Anyways, thanks again. Hopefully I can Google my way out of this one like I usually do!

P.S. I believe there is an issue with "gparted.sh" as of release multicd-5.8. The gparted-live-0.6.4-1.iso has initrd1.img & vmlinuz1 while the script still refers to them as initrd.img & vmlinuz. Simple to fix on our end but just wanted to put that out there.

---

### Post by maybeway36 on 2010-10-06
> **ckenneal said:**
> I did not copy some of the files from TRK (latest download TRL3.4 build 367, 2 days ago). Don't know the file structure of TRK. It seems to combine TRK into a boot directory, and then loses files.
I just fixed this; it will be in the 5.9 release.
> **ckenneal said:**
> What is the language that the script is written in. I want to learn more about the commands. Thanks. Hope you can help.
It's written in shell scripting, which is basically the Linux version of DOS's batch files (but much more powerful, thanks to programs like sed and awk.)
The [How It Works](http://multicd.tuxfamily.org/#HowItWorks) section (which I'm going to update soon) gives an example of a script and how it works.

> **acbatman54 said:**
> I just wanted to make a request. I wish I there was a way to make all of the isolinux.cfg menu options the same, i.e. either they all have submenus or none of them do.
Some of the plugins, like Clonezilla and Trinity, actually copy the isolinux.cfg from the original ISO and then edit it; that's why they have submenus. I might try making a no-submenu option using sed, though.
> **acbatman54 said:**
> I've been bashing my head against my desk trying to get them all lined up. Out of the 7 entries I have on my menu (Local HDD, GParted, Clonezilla, DBAN, NTPASSWD, BackTrack, & Ubuntu), I can usually only get about 5 to work right. Clonezilla and BackTrack are the major pains in my ***.
What problems are you having with them? GParted I'm going to fix right now like you said, and Clonezilla seems to work (I just tested it.)
> **acbatman54 said:**
> I'm using all of the latest ISO's. Is there a "plugin" repository somewhere that I'm not aware of?
Nope - all the plugins I know of are the ones that come with the script.

---

### Post by ckenneal on 2010-10-06
Thanks for that maybeway36. By the way, this whole concept and work is absolutely great. When do you think the new release (5.9) will be up. Thanks again for the response.

---

### Post by maybeway36 on 2010-10-07
I just put it up last night :) Hopefully TRK and GParted work now, and I didn't break anything.

---

### Post by acbatman54 on 2010-10-07
I'm getting my CD (DVD) close to where I want it to be, minus some backgrounds and help text. I've attached the two .cfg files in my isolinux folder for reference.

I'm still having issues with GParted, Clonezilla, and BackTrack. By the way, Clonezilla and BackTrack do work before I make my changes.

- GParted's menu stuff works but the boot up fails. I've attached a window capture from my VM. It happens on the original multicd.iso as well. Guess it's not being built correctly.

- Clonezilla is, at the moment, still using a separate .cfg file. I hope to change it soon to match the others. But currently, after adding what I thought were minor changes, it no longer boots. It just flashes on the menu page.

- BackTrack is also flashing on the menu page and not booting. I moved it down in the menu by Ubuntu and added a separate menu for it. I don't understand why it's acting up either.

I would appreciate it if someone could take a look and point out the dumb mistakes I'm making. I'm sure it's all minor issues that I'm too blind to see.

Thanks in advance.


Edit 1: *** I'm still using 5.8 as of this post. I'll give 5.9 a try and see if I have better results. ***
Edit 2: *** Using the GParted menu info from 5.9 in my 5.8 isolinux.cfg fixed my GParted issue. Still have Clonezilla and BackTrack issues. ***

---

### Post by acbatman54 on 2010-10-07
Well... I opened up multicd-5.9.tar.gz, did the chmod +x, ran it with sudo, and this is what I got. (I edited the paths and names below for personal sake)

me:~/Downloads/MultiCD_5.9$ sudo ./multicd.sh m v b
[sudo] password for me:
BackTrack
Clonezilla
DBAN
GParted Live

Note: Hiren's BootCD already includes dban.

Note: Hiren's BootCD already includes ntpasswd.
Continuing anyway.

NT Password Editor
Ubuntu

Continuing in 2 seconds - press Ctrl+C to cancel
Copying BackTrack...
Making initrd(s)...67175 blocks
~/Downloads/MultiCD_5.9/plugins/backtrack.sh: 101: cannot create ..//~/Downloads/MultiCD_5.9/multicd-working/boot/backtrack/initrd.gz: Directory nonexistent

And then I'm back to prompt. Is it a permissions problem cause it should be just like my ~/Downloads/MultiCD_5.8 build? 

P.S. I'm using symbolic links for my .iso's, just like I did for my 5.8 build.


Edited: *** I beileve I found the problem. backtrack.sh line45 should be "find . | cpio --create --format='newc' | gzip -c > $WORK/boot/backtrack/$i"   NOT   "find . | cpio --create --format='newc' | gzip -c > ../$WORK/boot/backtrack/$i". Check to see if this is correct. Thanks. ***

---

### Post by ckenneal on 2010-10-08
Sorry maybeway36. I went to download new version, but forgot to refresh the screen, Thanks for the 5.9 upgrade. Haven't tried it yet. Maybe tonight. I read your TODO.txt. Do I need to make those changes in the plugins or will it still run without the changes. I don't know much about script language, but it looks like it will work without me making changes. Thanks again. for the new upgrade.

---

### Post by maybeway36 on 2010-10-08
The stuff in the TODO.txt is just for me to make all the plugins look the same and use some common variables so if I want to change one later, it's easier to do so. The old plugins still work, so you don't have to do anything about that.

---

### Post by melkkoe on 2010-10-08
Hi, new to this forum-thread maybe I post the wrong way.

I would like to try your script but before doing so would like to know whether it is 

*possible to add more than 1 flavor of one distro ?*

Say puppy with so many derivatives.

I[I]f - it is possible do I have to rename them to **puppy1 puppy2** or just [B]puppy puppy puppy ?
[/B]
Does this principle also apply to **multi boot live usb**

Thanks in advance.
[/I]

---

### Post by maybeway36 on 2010-10-08
Right now there are just plugins for Lucid Puppy (puppy.iso) and Macpup (macpup.iso); any other Puppy derivatives would need seperate (but very similar) plugin files, since they use different filenames inside the ISOs.

Ubuntu is an exception to this rule. You can include up to 8 versions of Ubuntu:
```
ubuntu.iso, ubuntu2.iso, ubuntu3.iso, kubuntu.iso, ubuntu_32_bit.iso, ubuntu_64.bit.iso, kubuntu_32_bit.iso, kubuntu_64.bit.iso
```
For ubuntu, ubuntu2, and ubuntu3, you can install "dialog" and then run
```
sudo ./multicd.sh i
```
and it will ask you what to call them on the boot menu.

@acbatman54: Are you editing the .cfg files after the ISO is made? That might be the problem - maybe ISOLINUX is picky. I tried using your .cfg files, but I put them in before "genisoimage" was run, and it seemed to work fine.
In the next version I'll have a feature where you run "./multicd.sh wait" and it gives you a bash prompt before it builds the ISO - that way, you can change things around.

---

### Post by acbatman54 on 2010-10-08
Yeah, I've been ripping out the boot folder from the .iso, tweaking it, then rerunning the genisoimage part of your script. I thought it all seemed a bit weird that it works on the original .iso but doesn't on the remake. I'm going to give your idea a try... stop the build before the .iso, make my changes, then finish the build. Such a good idea... sad that my small brain didn't think of that.

P.S. Did you see my edit above that might be an issue with the backtrack plugin? Where or how would you prefer to receive such findings? Do you have a bug tracker setup somewhere? I would like to help out... ya know, support the open/linux community. :) Thanks.

---

### Post by acbatman54 on 2010-10-09
Well I'll be a baboon's niece! I made my changes in the plugins and  multicd.sh, ran the script, and bam... a near perfect build. Now I just need to  add a part that organizes the entries in number order, referencing the  menu labels, instead of alphabetical order. Who knew isolinux could be  so fickle!?!? Thanks again for the suggestion. Now that I've mostly  mastered my 5.8 build, I'm going to try out 5.9 again. I like where  you're going with the variables, it will make the whole process a lot easier to work with.

I've attached the files ( from MultiCD 5.8  ) that I've changed for others to reference. All of my menu entries are now submenued for a cleaner look. Like I mentioned above, pardon the number scheme until I get it worked out.

---

### Post by acbatman54 on 2010-10-09
And here's my ubuntu.sh and multicd.sh attachments ( MultiCD 5.8 ). Darn 5 attachment limit. This multicd.sh doesn't include the numbering fix. Look forward, hopefully, to an update.

Edited: *** Scratch that process. Maybeway36 was kind enough to leave this note in the multicd.sh that I've pasted over several times without reading. I had a feeling it would be that easy but didn't believe it. 

"##BEGIN ISOLINUX MENU CODE##
#The ISOLINUX menu can be rearranged by renaming your plugin scripts - they are processed in alphabetical order." ***

---

### Post by acbatman54 on 2010-10-09
@melkkoe - Are you talking about different Puppy distros or Puplets? I just had a crazy idea that I might try out using several Puplets on one distro on a MultiCD. I came across this informative forum about someone having issues GRUB'ing several Puplets and it sounds like a nice addition for a MultiCD. Just cause I'm crazy like that!

[http://208.109.22.214/puppy/viewtopic.php?t=46107&sid=f533472518c99ef8b7a34e59c829a3f4](http://208.109.22.214/puppy/viewtopic.php?t=46107&sid=f533472518c99ef8b7a34e59c829a3f4)

Sorry if the link doesn't work, I'm posting from my phone.

---

### Post by waspinator on 2010-10-12
Hi,

I just downloaded 10.10 versions of ubuntu 32bit, ubuntu 64bit, netbook, server 32bit. server 64bit, and lubuntu. I would like to have all these on one dvd. Is there a way with this script? It looks like you can only have one file named "ubuntu.iso"

Thanks

---

### Post by maybeway36 on 2010-10-13
This appears if you mouse over ubuntu.iso on the multicd homepage:
>  Other names supported for Ubuntu and Ubuntu-based ISOs:
ubuntu2.iso, ubuntu3.iso, kubuntu.iso,
ubuntu_32_bit.iso, ubuntu_64_bit.iso,
kubuntu_32_bit.iso, kubuntu_64_bit.iso 
Similar functionality will be added soon for puppy and tinycore.

---

### Post by satyans7 on 2010-10-20
Hi,

I want to get an iso image containing multiple ubuntu iso's. 
e.g., 9.04 32 bit 9.04 64 bit, 10.04 32 bit 10.04 64 bit, 10.10 32 bit, 10.10 64 bit.

when i tried to run multicd.sh, i got multicd.iso of 740Kb size.

Is there any way to do it.

Regards,
Satya

---

### Post by maybeway36 on 2010-10-20
The plugins [ubuntu2.iso, ubuntu3.iso, kubuntu.iso, ubuntu_32_bit.iso, ubuntu_64_bit.iso, kubuntu_32_bit.iso, kubuntu_64_bit.iso] only work for Ubuntu 9.10 or newer. You can include one version of Ubuntu 9.04 if you name it "ubuntu.iso". Then, I suggest naming the 9.10 versions "ubuntu_32_bit.iso" and "ubuntu_64_bit.iso" and the 10.04 versions "kubuntu_32_bit.iso" and "kubuntu_64_bit.iso". The menu will have the wrong names, but they should still work.

---

### Post by raydeejay on 2010-10-23
Here comes a hard one :)

I need (want...) to build a multicd containing Vista and Seven recovery discs, both 32 and 64 bits, besides trk, some desktop distro, and some other things. I suppose the way to go is copy the windows7recovery plugin and fiddle a bit with it, but maybe someone has done it already or knows about their boot sequence and can provide tips/howto/patches?

Thanks to everyone that contributed to multicd.sh, maybe it will be my turn now!

EDIT: It seems that hex editing is needed, and I've only found information for some specific versions of bootmgr. So I'll probably stick to Seven x64 (which is what most new computers come with these days) + tools, and keep the 3 other discs around for when need arises.

---

### Post by debianite on 2010-10-24
Hi,

I'm geting this:

```
~/multicd/plugins/hirens.sh: 71: cannot create tags/hirens.name: Directory nonexistent

```

and the script just stops.

---

### Post by maybeway36 on 2010-10-25
> **debianite said:**
> Hi,

I'm geting this:

```
~/multicd/plugins/hirens.sh: 71: cannot create tags/hirens.name: Directory nonexistent

```

and the script just stops.

In plugins/hiren.sh, change this:
```
head -n 1 hirens/BootCD.txt |sed -e 's/\t//g'>tags/hirens.name
```
into this:
```
head -n 1 hirens/BootCD.txt |sed -e 's/\t//g'>$TAGS/hirens.name
```
Thanks for notifying me about this bug :)

---

### Post by maybeway36 on 2010-11-09
I just released version 6.1. It fixes some bugs, and adds a cool new feature: some ISOs can be automatically linked.
For example, if there is no tinycore.iso in the folder, but there IS a tinycore_3.2.iso, the script will make a symlink pointing from tinycore_3.2.iso to tinycore.iso, and (here's the cool part) it will remember that the version number is 3.2, so that shows up on the MultiCD menu!
This is currently only in place for the distributions that I usually use, but it could certainly be added for others. I simply have to put something above
```
if [ $1 = scan ];then
```
For tinycore, I end up with:
```
if [ $1 = links ];then
	echo "tinycore-current.iso tinycore.iso"
	echo "tinycore_*.iso tinycore.iso"
elif [ $1 = scan ];then
```
Those two "echo" lines get passed to the isoaliases() function in functions.sh, which will make a link $2 pointing to $1 if $1 exists but $2 doesn't.
If you want to clean up these links it makes automatically, run:
```
./multicd.sh cleanlinks
```
This will:
1. remove all symbolic links in the current directory that point to other files in the same directory
2. remove all files ending in ".version"
3. remove all files ending in ".defaultname"
So it might be nice to be careful using cleanlinks, but if you have a separate folder to run MultiCD in it shouldn't be a problem.

---

### Post by maybeway36 on 2010-11-09
I just released version 6.1. It fixes some bugs, and adds a cool new feature: some ISOs can be automatically linked.
For example, if there is no tinycore.iso in the folder, but there IS a tinycore_3.2.iso, the script will make a symlink pointing from tinycore_3.2.iso to tinycore.iso, and (here's the cool part) it will remember that the version number is 3.2, so that shows up on the MultiCD menu!
This is currently only in place for the distributions that I usually use, but it could certainly be added for others. I simply have to put something above
```
if [ $1 = scan ];then
```
For tinycore, I end up with:
```
if [ $1 = links ];then
	echo "tinycore-current.iso tinycore.iso"
	echo "tinycore_*.iso tinycore.iso"
elif [ $1 = scan ];then
```
Those two "echo" lines get passed to the isoaliases() function in functions.sh, which will make a link $2 pointing to $1 if $1 exists but $2 doesn't.
If you want to clean up these links it makes automatically, run:
```
./multicd.sh cleanlinks
```
This will:
1. remove all symbolic links in the current directory that point to other files in the same directory
2. remove all files ending in ".version"
3. remove all files ending in ".defaultname"
So it might be nice to be careful using cleanlinks, but if you have a separate folder to run MultiCD in it shouldn't be a problem.

---

### Post by Aviendha09 on 2010-11-09
Any hope for LMDE ? I tried it as linuxmint.iso and it didn't believe me. thx!

---

### Post by maybeway36 on 2010-11-11
Call it mintdebian.iso instead. There's a separate plugin for LMDE in particular.

---

### Post by dh04000 on 2010-11-11
Kubuntu?
Xubuntu?
Lubuntu?
Elive Ubuntu?


I want to make a ubuntu complete disc. Can I assume that the other *buntu will work with your multicd program?

Also, when is a GUI going to be made?

---

### Post by asteriks on 2010-11-15
Hi, I need advice, I don't know what should I do...
I don't have installed linux at machine, I use public PC, but I started Fedora Live CD and here is my problem at using of multicd script:

```
[root@localhost multicd]# 
[root@localhost multicd]# chmod +x multicd*.sh
[root@localhost multicd]# sudo ./multicd*.sh
Made a link named puppy.iso pointing to lupu-puppy-511.iso (version puppy-511)
Made a link named slax.iso pointing to slax-6.1.2.iso (version 6.1.2)
Made a link named ubuntu_32_bit.iso pointing to ubuntu-10.10-desktop-i386.iso (version 10.10)
Puppy Linux
Slax
Ubuntu (32-bit)
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Puppy...
Copying Slax...
Copying Ubuntu (32-bit)...
Downloading SYSLINUX...
./multicd-6.1.1.sh: line 1598: wget: command not found
You have new mail in /var/spool/mail/root
[root@localhost multicd]# gedit /var/spool/mail/root

[root@localhost multicd]# chmod +x multicd*.sh
[root@localhost multicd]# sudo ./multicd*.sh
Puppy Linux
Slax
Ubuntu (32-bit)
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Puppy...
Copying Slax...
Copying Ubuntu (32-bit)...
Downloading SYSLINUX...
./multicd-6.1.1.sh: line 1598: wget: command not found
[root@localhost multicd]# 

```

here is screenshot of this line 1598 in file: [http://i54.tinypic.com/2qjvy2r.png](http://i54.tinypic.com/2qjvy2r.png) (I don't understand why wget command when I have already downloaded syslinux4.03)
here is screenshot what i have in folder, several linux: [http://i54.tinypic.com/293ttug.png](http://i54.tinypic.com/293ttug.png)

---

### Post by asteriks on 2010-11-15
hm, I installed wget and changed multicd-6.1.1..sh in line 1598, it should be:
wget -qO syslinux.tar.gz [ftp://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.03.tar.gz](ftp://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.03.tar.gz)
but problem is that now SH script recognized only Slax and Ubuntu, nothing else, here is code and screenshot, now I need just advice **how to recognize other distros and not only slax and ubuntu?**
screenshot show you many distros and final multicd.iso file, 876MB: [http://i52.tinypic.com/349e3ow.png](http://i52.tinypic.com/349e3ow.png)
code:
```
[root@localhost multicd]# chmod +x multicd*.sh
[root@localhost multicd]# sudo ./multicd*.sh
Made a link named slax.iso pointing to slax-6.1.2.iso (version 6.1.2)
Made a link named ubuntu_32_bit.iso pointing to ubuntu-10.10-desktop-i386.iso (version 10.10)
Slax
Ubuntu (32-bit)
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Slax...
Copying Ubuntu (32-bit)...
Downloading SYSLINUX...
Unpacking and copying files...
Downloading memtest86+ 4.10 from memtest.org...
Writing isolinux.cfg...
Building CD image...
[root@localhost multicd]# 

```

---

### Post by maybeway36 on 2010-11-18
> **asteriks said:**
> hm, I installed wget and changed multicd-6.1.1..sh in line 1598, it should be:
wget -qO syslinux.tar.gz [ftp://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.03.tar.gz](ftp://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.03.tar.gz)
but problem is that now SH script recognized only Slax and Ubuntu, nothing else, here is code and screenshot, now I need just advice **how to recognize other distros and not only slax and ubuntu?**
screenshot show you many distros and final multicd.iso file, 876MB: [http://i52.tinypic.com/349e3ow.png](http://i52.tinypic.com/349e3ow.png)
code:
```
[root@localhost multicd]# chmod +x multicd*.sh
[root@localhost multicd]# sudo ./multicd*.sh
Made a link named slax.iso pointing to slax-6.1.2.iso (version 6.1.2)
Made a link named ubuntu_32_bit.iso pointing to ubuntu-10.10-desktop-i386.iso (version 10.10)
Slax
Ubuntu (32-bit)
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Slax...
Copying Ubuntu (32-bit)...
Downloading SYSLINUX...
Unpacking and copying files...
Downloading memtest86+ 4.10 from memtest.org...
Writing isolinux.cfg...
Building CD image...
[root@localhost multicd]# 

```

The function for automatically making links (it works with Slax and Ubuntu, among others) is not done yet; also, when a new version comes out it has to be updated. If you want the script to find the other ISO images, name them according to the names I give on [http://multicd.tuxfamily.org](http://multicd.tuxfamily.org), i.e. ubcd.iso, puppy.iso.
Also, the Mandriva and openSUSE live CDs/DVDs are not supported. Hmm... maybe I should add support for those ;)


@dh0400: Other Ubuntu distros should work with this program. You'll have to call them ubuntu.iso, ubuntu2.iso, ubuntu3.iso, and kubuntu.iso.
ubuntu2.iso and ubuntu3.iso will both ask for a distro name to be used on the menu if you run multicd with the "i" option:
```
./multicd.sh i
```
To make ubuntu.iso do this as well, edit plugins/ubuntu.sh (or the single file multicd.sh if you downloaded that) and remove the first "#" from this line:
```
#echo > $TAGS/ubuntu.needsname #Comment out this line and multicd.sh won't ask for a custom name for this ISO
```
so it becomes this:
```
echo > $TAGS/ubuntu.needsname #Comment out this line and multicd.sh won't ask for a custom name for this ISO
```

---

### Post by GO%)$@*1 on 2010-11-20
Just out of curiosity, is this on GitHub or something?

---

### Post by maybeway36 on 2010-11-21
```
git clone git://git.tuxfamily.org/gitroot/multicd/multicd.git

```

---

### Post by GO%)$@*1 on 2010-11-22
> **maybeway36 said:**
> ```
git clone git://git.tuxfamily.org/gitroot/multicd/multicd.git

```
#-oMy bad. I somehow skipped it on the website...
Thanks!

---

### Post by GO%)$@*1 on 2010-11-22
When I run "sudo ./multicd-6.1.1.sh c i v", I get this (at the end):
```
./multicd-6.1.1.sh: line 3461: isohybrid: command not found
```
The ISO seems to be OK, though.

---

### Post by tete245 on 2010-12-02
Congratulations on the program.

I made several attempts to Ubuntu 10.04 and not get an iso that would work with Backtrack, Puppy, the MiniXp of Hirens or graphical configuration correctly LinuxMint. With this version of Ubuntu I have trouble even copy an iso correctly and I use rsync.

Instead I got no problem with archiso-live. I suggest, if possible,  to include archiso-live and zenwalk-live between the supported distros. I think it's a very interesting shell script to cd-lives. 

Many thanks.

PS: Sorry for my english, this text was made with a web translator

---

### Post by maybeway36 on 2010-12-11
A couple days ago I released MultiCD 6.2. It supports archiso-live, AVG, 64-bit fedora and opensuse network installers, and as many Ubuntu distros as you want.

The names you'll have to use for your Ubuntu and Kubuntu isos are different. Instead of ubuntu.iso, ubuntu_32_bit.iso, kubuntu.iso, and so on, you can either:
*name them all [something].ubuntu.iso, or
*name them the original name you downloaded them as (such as ubuntu-10.10-desktop-i386.iso) and the script will detect that too.
Also, make sure to read the upgrade instructions:
> Delete your old plugins folder before extracting the new ones - in particular, these plugins:

    * debian-inst.sh (renamed to debian-mini.sh)
    * fedora.sh (renamed to fedora-boot.sh)
    * kubuntu.sh, kubuntu_32_bit.sh, kubuntu_64_bit.sh (obselete after ubuntu.sh upgrades)
    * mandriva.sh (renamed to mandriva-boot.sh)
    * opensuse.sh (renamed to opensuse-net.sh)
    * ubuntu2.sh, ubuntu3.sh, ubuntu_32_bit.sh, ubuntu_64_bit.sh (obselete after ubuntu.sh upgrades)
    * ubuntu-inst.sh (renamed to ubuntu-mini.sh)

It's also a good idea to run ./multicd.sh cleanlinks before using the new version.

---

### Post by nilarimogard on 2010-12-14
Using the latest version, I get 2 errors:


```
Writing isolinux.cfg...
[: 88: Ubuntu (32-bit): unexpected operator
Building CD image...
isohybrid: Warning: more than 1024 cylinders: 2707
isohybrid: Not all BIOSes will be able to boot this device
isohybrid: multicd.iso: seek error - 6: Invalid argument
andrei@andrei-work:~/multicd$ 
```

Despite the errors, the ISO works.

---

### Post by immux on 2010-12-14
i got an error like this
> Downloading SYSLINUX...
Writing isolinux.cfg...
Building CD image...
./multicd.sh: line 502: isohybrid: command not found
this problem is solved, i've been download the last syslinux and use the isohybrid

but now, i got an error message again like this
> Writing isolinux.cfg...
Building CD image...
isohybrid: multicd.iso: boot loader does not have an isolinux.bin hybrid signature. Note that isolinux-debug.bin does not support hybrid booting

using ubuntu lucid. any suggestion?

---

### Post by thrvers on 2010-12-15
'
is it possible to directly create on USB-disk not just file multicd.iso??? :D 

how to use ubuntu-GUI with apt:dialog as you mention on multicd.tuxfamily.org ??

THX

---

### Post by maybeway36 on 2010-12-15
EDIT: Try version 6.2.1, which I just posted.

> **nilarimogard said:**
> Using the latest version, I get 2 errors:


```
Writing isolinux.cfg...
[: 88: Ubuntu (32-bit): unexpected operator
Building CD image...
isohybrid: Warning: more than 1024 cylinders: 2707
isohybrid: Not all BIOSes will be able to boot this device
isohybrid: multicd.iso: seek error - 6: Invalid argument
andrei@andrei-work:~/multicd$ 
```

Despite the errors, the ISO works.

The isohybrid error seems to appear every time for me as well, but the ISO still works. I'll find a way to keep it from appearing in the next version. The other error I'm looking to fix right now.

> **immux said:**
> i got an error like this

this problem is solved, i've been download the last syslinux and use the isohybrid

but now, i got an error message again like this


using ubuntu lucid. any suggestion?

I've never seen the second error before. The first one shouldn't happen at all - the script should get isohybrid for you automatically, so that's a problem.

> **thrvers said:**
> '
is it possible to directly create on USB-disk not just file multicd.iso??? :D 

how to use ubuntu-GUI with apt:dialog as you mention on multicd.tuxfamily.org ??

THX

To put the file onto a USB stick, you need to use "dd if=multicd.iso of=/dev/something". (Be careful & make sure you don't use the wrong disk.) Having the script use the USB disk directly would require a lot more work.
The "GUI" (which isn't really a GUI) can be activated with:
```
sudo ./multicd.sh i
```
You need to have "dialog" installed.

---

### Post by thrvers on 2010-12-16
'
THX maybeway36 for the answer :D

for now i try use unetbootin to run multicd.iso but fail at initramfs ......
(fail for linuxmint9-dvd-i386, lupu511, LMDE-i386 and only slitaz3.0 work fine)

THX

---

### Post by maybeway36 on 2010-12-16
If UNetbootin doesn't work with multicd.iso, you can write it to the USB drive with:
```
sudo dd if=multicd.iso of=/dev/something
```
Replace /dev/something with the actual USB drive (like /dev/sdb).

---

### Post by Troublegum on 2010-12-16
Could you add support for the **Ubuntu Server Edition**, please?

---

### Post by karmila on 2010-12-26
Hi, please help me...

What is the correct naming for fedora live cd KDE 32bit and opensuse live cd KDE 32bit?

Thank you.

---

### Post by maybeway36 on 2010-12-26
> **Troublegum said:**
> Could you add support for the **Ubuntu Server Edition**, please?

I'll look into it. Should be possible.

> **karmila said:**
> Hi, please help me...

What is the correct naming for fedora live cd KDE 32bit and opensuse live cd KDE 32bit?

Thank you.

The Fedora Live CD isn't supported right now. (I should add that too.) For openSUSE, you could try naming it opensuse-gnome.iso even though it's not GNOME.

---

### Post by A-star on 2010-12-27
Is it possible to include the XBMC live cd?

---

### Post by kuadhual on 2011-01-12
The Debian Installer (for net install cd) only detect 386 version and give up on amd64.

---

### Post by Neudrino on 2011-02-22
**Thanks a lot for the fantastic Program!**

 I was using version 5.5 of your fabulous tool to create a multiboot cd of lot small distros/tools (puppy, gparted, etc.).

 Now I want to make a big DVD with some ?ubuntus. Thereby I encountered some problems with version 6.3. of your program/script.
 
_  First:_
```
kmint-neutrino@Neutrino-PC /media/LinuxIso/MultiCD $ sudo ./multicd.sh
Made a link named i386.ubuntu.iso pointing to ubuntu-10.04.1-desktop-i386.iso (version 10.04.1)
Ubuntu (32-bit) 10.04.1
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Ubuntu (32-bit) 10.04.1...
cat: /tmp/multicd-root/tags/lang: Datei oder Verzeichnis nicht gefunden
[: 101: !=: unexpected operator
[COLOR=Red]Downloading SYSLINUX...
cp: Aufruf von stat für „/usr/bin/isohybrid“ nicht möglich: Datei oder Verzeichnis nicht gefunden[/COLOR]
kmint-neutrino@Neutrino-PC /media/LinuxIso/MultiCD $

```I think this problem has been mentioned somewhere already. I am using the newest syslinux archive (4.03). Even so I am not able to bash-programm, I tried to modify the skript myself a bit...
 I did the following changes in multicd.sh:
 I commented out the part searching in my system for syslinux, so that the script will take the archive in the working directory as first choice.
  ```

echo "Downloading SYSLINUX..."
#if [ -d /usr/lib/syslinux ];then
#    cp /usr/lib/syslinux/isolinux.bin $WORK/boot/isolinux/
#    cp /usr/lib/syslinux/memdisk $WORK/boot/isolinux/
#    cp /usr/lib/syslinux/menu.c32 $WORK/boot/isolinux/
#    cp /usr/lib/syslinux/vesamenu.c32 $WORK/boot/isolinux/
#    cp /usr/lib/syslinux/chain.c32 $WORK/boot/isolinux/
#    cp /usr/bin/isohybrid $TAGS
#elif [ -f syslinux.tar.gz ];then
if [ -f syslinux.tar.gz ];then

```This might be equivalent to changing the order of the scripts searching process for appropriate syslinux.
 This did the trick and I was able to built a working image.
 You might consider to change that in the next version?
 
 Moreover I noticed that your script looked like as it should support the original filename of the downloaded syslinux file (syslinux-4.03.tar.gz), but I had to rename it to syslinux.tar.gz. Otherwise the script generated a new empty syslinux.tar.gz (with no content at all) and threw up the above error.
 
_  Second:_
 ```

kmint-neutrino@Neutrino-PC /media/LinuxIso/MultiCD $ sudo ./multicd.sh
Made a link named i386.ubuntu.iso pointing to ubuntu-10.04.1-desktop-i386.iso (version 10.04.1)
Ubuntu (32-bit) 10.04.1
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Ubuntu (32-bit) 10.04.1...
[COLOR=Red]cat: /tmp/multicd-root/tags/lang: Datei oder Verzeichnis nicht gefunden
[: 101: !=: unexpected operator[/COLOR]
Downloading SYSLINUX...
Unpacking and copying files...
Writing isolinux.cfg...
Building CD image...
Running isohybrid...
kmint-neutrino@Neutrino-PC /media/LinuxIso/MultiCD $

```[Datei oder Verzeichnis nicht gefunden = File or Directory not found]
The problem is, that the Ubuntu submenu in install menu does not has any entries despite „Return to main menu“.
 This Problem occurs with all Ubuntu isos I tried (Mint-,K-,X-,L-,Ubuntu).
 As I mentioned above I am not really able to bash-program and so I have no idea what goes wrong here.
 
 By the way, I also tried to include Lubuntu, which made me add the lines
     ```

echo "lubuntu-*.iso i386.l.ubuntu.iso Lubuntu_(32-bit)"
lubuntu-*.iso            i386.l.ubuntu.iso

```to ubunutu.sh-plugin and isos.txt (respectivly).
 This seems to work, even so I could not check upon this due to the above problem.
 
 Next to Ubuntu Server Edition it might be easy to add Lubuntu to the next version as well.
 
 I would very much appreciate help with the above problems! What might I be doing wrong? How can I check weather I did something wrong? 
 


 P.S.: This is my first entry in any forum at all. So please do not be angry, if I did something wrong or if I am just not smart enough to run the script correctly.

---

### Post by maybeway36 on 2011-02-22
Thanks for the suggestions. I'll implement lubuntu support. (By the way, editing isos.txt isn't necessary - the script never uses it.)
The SYSLINUX isohybrid bug I think is fixed in the git repository, but I also added the link from syslinux-4.03.tar.gz --> syslinux.tar.gz and put the .tar.gz check before the /usr/lib check like you suggested.

From now on, it's best to download the newest git version, from the "Newest (git)" link on the website.

I'll look into the Ubuntu bug soon. I can't remember if I fixed that or not.

---

### Post by Bombenbach on 2011-02-23
Just to give some feedback on this

I'm running Lucid and used the latest multicd-6.3.sh to create a USB flash with some usefull stuff like
latest versions of Clonezilla, Freedos, Knoppix, NT Password Recovery, P-Magic, System Rescude CD, Super Grub 2 and Seagate Seatools.

As far as Seatools are concerned, I've just downloaded the latest ISO of Seatools for DOS, extracted it and took SeaTools.ima. Then, I renamed SeaTools.ima to seatools.img and MultiCD accepted it just fine. 

The first problem concerning MultiCD or better to say my distro version was missing isohybrid. To make MultiCD download a standalone syslinux, I simply edited multicd-6.3.sh changing

```
echo "Downloading SYSLINUX..."
if [ -d /usr/lib/syslinux ];then
```to
```
echo "Downloading SYSLINUX..."
if [ -d /usr/lib/soslinux ];then
```a plain and dirty hack, but whatever. After that I tried to put the multicd.iso on my flash drive using Unetbootin but it would always freeze. I also tried to "dd" the iso file but that didn't work too. Finally I found this:

[http://chris.picton.nom.za/?q=node/2](http://chris.picton.nom.za/?q=node/2)

> 
multicd.sh is a very useful tool to put multiple tools and Linux distributions onto a single iso image: [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Attached is a script which can take this iso and put it on a USB drive (optionally formatting that drive to be bootable)I immediately downloaded the script cd2usb.sh, put it into my MultiCD directory which also contained syslinux.tar.gz (the one that multicd-6.3.sh downloaded from the net) and tried it out but it complained about not being able to found syslinux. The problem is that the author hardcoded the syslinux path to be syslinux-3.84 but the current version happens to be syslinux-4.xx. So I edited the appropriate lines, replacing 

```
  cd2usb-working/syslinux/syslinux-3.84/utils/mkdiskimage -4 $DEVICE 0 64 32
``` by
```
  cd2usb-working/syslinux/syslinux*/utils/mkdiskimage -4 $DEVICE 0 64 32
``` and 
```
  cd2usb-working/syslinux/syslinux-3.84/linux/syslinux "${DEVICE}4"
``` by
```
  cd2usb-working/syslinux/syslinux*/linux/syslinux "${DEVICE}4"
``` This made the script work properly. It actually took quite a long time to prepare the flash drive and to copy my multicd.iso on it (sth. like 10-20 Minutes) but at the end it worked! I tested all the stuff on the usb drive and it all boots well on a real machine! Nice! :guitar:

---

### Post by maybeway36 on 2011-02-24
The bug with SYSLINUX is fixed in version 3.4. It checks for isohybrid before trying to copy it. (It also uses a .tar.gz file is there is one before the installed version.)

---

### Post by Bombenbach on 2011-02-25
Just tested the latest 6.4 version and found some new bugs:

In multicd-6.4.sh

Line 320 
```
if [ $(cat $TAGS/lang) != en ];then
```should be
```
if [ "$(cat $TAGS/lang)" != "en" ];then
```But since $TAGS/lang is defined only in interactive mode, it should better be sth like
```

if [ -f $TAGS/lang ];then
if [ "$(cat $TAGS/lang)" != "en" ];then
...
fi

```Line 1632
```
cp $MNT/ win7recovery/bootmgr $WORK/
```->
```
cp $MNT/win7recovery/bootmgr $WORK/
```Futhermore, "gparted.version" is used when creating bootmenu entry for gparted but is nowhere defined.

Concerning the plugin-version of multicd.sh,
some files like for example ntpasswd.sh or pmagic.sh are missing 
```
. ./functions.sh
```in the 3rd line.

**BTW: Neither Ubuntu 10.10 nor Win7 recovery cd boot properly which is kind of sad** :(

---

### Post by maybeway36 on 2011-02-26
> **Bombenbach said:**
> Just tested the latest 6.4 version and found some new bugs:

In multicd-6.4.sh

Line 320 
```
if [ $(cat $TAGS/lang) != en ];then
```should be
```
if [ "$(cat $TAGS/lang)" != "en" ];then
```But since $TAGS/lang is defined only in interactive mode, it should better be sth like
```

if [ -f $TAGS/lang ];then
if [ "$(cat $TAGS/lang)" != "en" ];then
...
fi

```
I'll do something like this to fix it:
```
f [ -f $TAGS/lang ] && $(cat $TAGS/lang)" != "en" ];then
...
fi
```

> Line 1632
```
cp $MNT/ win7recovery/bootmgr $WORK/
```->
```
cp $MNT/win7recovery/bootmgr $WORK/
```
I'll fix that too.

> Futhermore, "gparted.version" is used when creating bootmenu entry for gparted but is nowhere defined.
gparted.version (and all the other .version files) are created by the isoaliases() function based on the filename of the ISO if it has a version number in it (line 240 of the combined .sh or line 63 of functions.sh).

> Concerning the plugin-version of multicd.sh,
some files like for example ntpasswd.sh or pmagic.sh are missing 
```
. ./functions.sh
```in the 3rd line.

That's OK - those are just old plugins that don't use the shortcuts like "mcdmount" and "umcdmount" I wrote.

> **BTW: Neither Ubuntu 10.10 nor Win7 recovery cd boot properly which is kind of sad** :(
This needs to be fixed. I'm on it ;)

EDIT: Both Ubuntu 10.10 and Windows 7 Recovery are working now that I fixed those two bugs.

---

### Post by Neudrino on 2011-02-27
Thanks a lot for the immediate help! I was not as quick with testing as you were with fixing, but want to give some feedback.

 The ubuntu script works for me (in version 6.04 and git). At least for the images I tried: This are Desktop 10.04 LTS Versions of K-,L-,X-,Ubuntu 32 or 64 bit.
 I did *not* try the newest 10.10 version of any.
 
 Obviously I was wrong, that the second error on display caused the missing of the install menu, because the error is still displayed but everything works fine.
 Only with the Mint-Linux the problem remained, that there were still no boot menu entries. But I was able to solve this myself by comparing the Ubuntu and Mint plugin and adding the line 83 of ubuntu.sh (BASENAME=$...) to the appropriate location in mint-skript.
 
 Finally I was able to build the DVD image and it worked well as far as I could check this with VirtualBox (no 64bit emulation).
 
 Thanks a lot for your help and magnificent program/skript! I can only recommend it and will certainly use it now and than again!

---

### Post by juako on 2011-03-07
Amazing script. I've updated a pentoo plugin posted before for 5.1 to version 6.4, and changed (in the "copy" action) a {} expansion to a for .. in loop, as the expansion was breaking with a stat error, what's strange is this happened only from the script, when i tried manually after the script stopped it worked fine.

```

#!/bin/sh
set -e
. ./functions.sh
#Pentoo plugin for multicd.sh
#version 6.4?
#Copyright (c) 2009 maybeway36
#
#Permission is hereby granted, free of charge, to any person obtaining a copy
#of this software and associated documentation files (the "Software"), to deal
#in the Software without restriction, including without limitation the rights
#to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#copies of the Software, and to permit persons to whom the Software is
#furnished to do so, subject to the following conditions:
#
#The above copyright notice and this permission notice shall be included in
#all copies or substantial portions of the Software.
#
#THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#THE SOFTWARE.

# BUGS
# modules directory is not read correctly, as it is searched for in /
if [ $1 = scan ];then
    if [ -f pentoo.iso ];then
        echo "Pentoo Linux"
    fi
elif [ $1 = copy ];then
    if [ -f pentoo.iso ];then
        echo "Copying Pentoo Linux..."
        mcdmount pentoo

        mkdir -p $WORK/boot/pentoo
        for item in modules tools win32 image.squashfs livecd; do
            cp -r $MNT/pentoo/$item $WORK/boot/pentoo
        done
        for item in pentoo isolinux.cfg pentoo.igz; do
            cp -r $MNT/pentoo/isolinux/$item $WORK/boot/pentoo
        done

        # Fix the isolinux.cfg
        sed -i 's@loop=/image.squashfs@loop=/boot/pentoo/image.squashfs subdir=/boot/pentoo@' $WORK/boot/pentoo/isolinux.cfg
        sed -i 's@kernel @kernel /boot/pentoo/@' $WORK/boot/pentoo/isolinux.cfg
        sed -i 's@initrd=@initrd=/boot/pentoo/@' $WORK/boot/pentoo/isolinux.cfg

        umcdmount pentoo
    fi
elif [ $1 = writecfg ];then
if [ -f pentoo.iso ];then
cat >> $WORK/boot/isolinux/isolinux.cfg << EOF
label pentoo
menu label ---> ^Pentoo Menu
com32 menu.c32
append /boot/pentoo/isolinux.cfg

EOF

cat >> $WORK/boot/pentoo/isolinux.cfg << EOF

label back
menu label Back to main menu
com32 menu.c32
append /boot/isolinux/isolinux.cfg

EOF

fi
else
    echo "Usage: $0 {scan|copy|writecfg}"
    echo "Use only from within multicd.sh or a compatible script!"
    echo "Don't use this plugin script on its own!"
fi

```

I have another multiboot i've made at hand with grub4dos and boots some 20 distros or so, but all are loopback chained to a grub4dos emulated drive. Its structure is as this

/boot
/boot/grub
/boot/grub4dos
/boot/grub4dos/menu/*.lst (submenus)
/iso/*.iso (isos only)
/menu.lst
grldr

I want to integrate these in the multicd iso, is this possible? Can isolinux and grub4dos coexist? If there arent any name clashes for folders or files, they can be chained right?

Anyway i might aswell try to write plugins for the one or two isos that multicd doesn't list as of now and get done. IIUC i can get the same effect with MEMDISK as with grub4dos "map".

After two days of learning all this stuff i'm seeing i'll have to drop the idea of an universal way to boot iso files, and multicd seems great for the "remaster distros" approach, nevertheless I'd like to keep the distros that are capable of booting directly from an iso in a single directory, and remaster the rest with multicd.

Having the isos right there has its advantages, the setup is way easier and they can be easily transferred, burned, etc. I hope some day all isos can be chained directly :(

---

### Post by juako on 2011-03-08
Patches for some errors i had with Ntpasswd, RIPLinux, Pmagic and RIPLinux: 

ntpasswd.sh: 49: mcdmount: not found
pmagic.sh: 94: mcdmount: not found

couldn't find /home/me/data/ware/os/multi/jmulticd/1/riplinux
couldn't find /home/me/data/ware/os/multi/jmulticd/1/ping
the last two popped up in a dialog (i guess at the stage of compiling the iso)

I had errors with doudoulinux (I/O errors, perhaps my iso is bad i'll re-download it)

I also had errors with caine, it couldn't find some windows files it expected in the iso, the version i have here (caine 2) doesn't have those files, maybe it is for a different version?

Ophcrack had trouble too (using both isos), also caused by the script using a seemingly "old" code (not using umcdmount for example), but this is a little bit more complex and anyway i'd like to rewrite this plugin to better handling of xp+vista isos together.

NT Password recovery suite
```

diff -uNr plugins.orig/ntpasswd.sh plugins/ntpasswd.sh
--- plugins.orig/ntpasswd.sh    2010-12-06 22:03:04.000000000 -0300
+++ plugins/ntpasswd.sh 2011-03-08 10:21:04.000000000 -0300
@@ -1,5 +1,6 @@
 #!/bin/sh
 set -e
+. ./functions.sh
 #NT Password Editor plugin for multicd.sh
 #version 6.2
 #Copyright (c) 2010 libertyernie

```

Partimage Is Not Ghost
```

diff -uNr plugins.orig/ping.sh plugins/ping.sh
--- plugins.orig/ping.sh	2010-12-06 18:13:03.000000000 -0300
+++ plugins/ping.sh	2011-03-08 10:57:27.000000000 -0300
@@ -1,5 +1,6 @@
 #!/bin/sh
 set -e
+. ./functions.sh
 #PING plugin for multicd.sh
 #version 5.0
 #Copyright (c) 2009 libertyernie
@@ -28,22 +29,14 @@
 elif [ $1 = copy ];then
 	if [ -f ping.iso ];then
 		echo "Copying PING..."
-		if [ ! -d ping ];then
-			mkdir ping
-		fi
-		if grep -q "`pwd`/ping" /etc/mtab ; then
-			umount ping
-		fi
-		mount -o loop ping.iso ping/
-		mkdir -p multicd-working/boot/ping
-		cp ping/kernel multicd-working/boot/ping/kernel
-		cp ping/initrd.gz multicd-working/boot/ping/initrd.gz
-		umount ping
-		rmdir ping
-	fi
+        mcdmount ping
+        cp $MNT/ping/kernel $WORK/boot/ping
+		cp $MNT/ping/initrd.gz $WORK/boot/ping
+        umcdmount ping
+    fi
 elif [ $1 = writecfg ];then
 if [ -f ping.iso ];then
-cat >> multicd-working/boot/isolinux/isolinux.cfg << "EOF"
+cat >> $WORK/boot/isolinux/isolinux.cfg << "EOF"
 label ping
 menu label ^PING (Partimage Is Not Ghost)
 kernel /boot/ping/kernel

```

Parted Magic
```

diff -uNr plugins.orig/pmagic.sh plugins/pmagic.sh
--- plugins.orig/pmagic.sh	2010-12-28 01:11:39.000000000 -0300
+++ plugins/pmagic.sh	2011-03-08 10:26:55.000000000 -0300
@@ -1,5 +1,6 @@
 #!/bin/sh
 set -e
+. ./functions.sh
 #Parted Magic plugin for multicd.sh
 #version 6.3
 #Copyright (c) 2010 libertyernie

```

RIPLinux
```

diff -uNr plugins.orig/riplinux.sh plugins/riplinux.sh
--- plugins.orig/riplinux.sh	2010-12-06 18:13:03.000000000 -0300
+++ plugins/riplinux.sh	2011-03-08 11:06:59.000000000 -0300
@@ -1,5 +1,6 @@
 #!/bin/sh
 set -e
+. ./functions.sh
 #RIPLinuX plugin for multicd.sh
 #version 5.6.1
 #Copyright (c) 2010 libertyernie
@@ -27,34 +28,26 @@
 	fi
 elif [ $1 = copy ];then
 	if [ -f riplinux.iso ];then
-		if [ ! -d riplinux ];then
-echo "Copying RIP Linux..."
-			mkdir riplinux
-		fi
-		if grep -q "`pwd`/riplinux" /etc/mtab ; then
-			umount riplinux
-		fi
-		mount -o loop riplinux.iso riplinux/
-		mkdir -p multicd-working/boot/riplinux
-		cp -r riplinux/boot/doc multicd-working/boot/ #Documentation
-		cp -r riplinux/boot/grub4dos multicd-working/boot/riplinux/ #GRUB4DOS :)
-		cp riplinux/boot/kernel32 multicd-working/boot/riplinux/kernel32 #32-bit kernel
-		cp riplinux/boot/kernel64 multicd-working/boot/riplinux/kernel64 #64-bit kernel
-		cp riplinux/boot/rootfs.cgz multicd-working/boot/riplinux/rootfs.cgz #Initrd
-		perl -pi -e 's/\/boot\/kernel/\/boot\/riplinux\/kernel/g' multicd-working/boot/riplinux/grub4dos/menu-cd.lst #Fix the menu.lst
-		perl -pi -e 's/\/boot\/rootfs.cgz/\/boot\/riplinux\/rootfs.cgz/g' multicd-working/boot/riplinux/grub4dos/menu-cd.lst #Fix it some more
-		umount riplinux
-		rmdir riplinux
-	fi
+        echo "Copying RIP Linux..."
+        mcdmount riplinux
+        cp -r $MNT/riplinux/boot/doc $WORK/boot/riplinux #Documentation
+		cp -r $MNT/riplinux/boot/grub4dos $WORK/boot/riplinux #GRUB4DOS :)
+		cp $MNT/riplinux/boot/kernel32 $WORK/boot/riplinux #32-bit kernel
+		cp $MNT/riplinux/boot/kernel64 $WORK/boot/riplinux #64-bit kernel
+		cp $MNT/riplinux/boot/rootfs.cgz $WORK/boot/riplinux #Initrd
+		sed -i 's|/boot/kernel|/boot/riplinux/kernel|g' $WORK/boot/riplinux/grub4dos/menu-cd.lst #Fix the menu.lst
+		sed -i 's|/boot/rootfs.cgz|/boot/riplinux/rootfs.cgz|g' $WORK/boot/riplinux/grub4dos/menu-cd.lst #Fix it some more
+        umcdmount riplinux
+    fi
 elif [ $1 = writecfg ];then
 if [ -f riplinux.iso ];then
-cat >> multicd-working/boot/isolinux/isolinux.cfg << "EOF"
+cat >> $WORK/boot/isolinux/isolinux.cfg << "EOF"
 label riplinux
 menu label ^RIPLinuX
 com32 menu.c32
 append riplinux.cfg
 EOF
-cat >> multicd-working/boot/isolinux/riplinux.cfg << "EOF"
+cat >> $WORK/boot/isolinux/riplinux.cfg << "EOF"
 DEFAULT menu.c32
 PROMPT 0
 MENU TITLE RIPLinuX v6.7

```

---

### Post by juako on 2011-03-08
Caine patch for my 2.0 iso

```

diff -uNr plugins.orig/caine.sh plugins/caine.sh
--- plugins.orig/caine.sh	2011-01-08 13:44:25.000000000 -0300
+++ plugins/caine.sh	2011-03-08 12:54:11.000000000 -0300
@@ -23,45 +23,47 @@
 #OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 #THE SOFTWARE.
 if [ $1 = scan ];then
-	if [ -f caine.iso ];then
-		echo "Caine"
-	fi
+    if [ -f caine.iso ];then
+        echo "Caine"
+    fi
 elif [ $1 = copy ];then
-	if [ -f caine.iso ];then
-		echo "Copying Caine..."
-		mcdmount caine
-		cp -R $MNT/caine/casper $WORK/boot/caine #Live system
-		cp $MNT/caine/README.diskdefines multicd-working/
-		mkdir $WORK/CaineFiles
-		cp -R $MNT/caine/{AutoPlay,autorun.exe,autorun.inf,comdlg32.ocx,files,license.txt,page5,preseed,Programs,RegOcx4Vista.bat,rw_common,tabctl32.ocx,vbrun60.exe,WinTaylor.exe} $WORK/CaineFiles
-		umcdmount caine
-		echo -n "Making initrd(s)..."
-		if [ -d $MNT/caine-inittmp ];then rm -r $MNT/caine-inittmp;fi
-		mkdir $MNT/caine-inittmp
-		cd $MNT/caine-inittmp
-		gzip -cd $WORK/boot/caine/initrd.gz | cpio -id
-		perl -pi -e 's/path\/casper/path\/boot\/caine/g' scripts/casper
-		perl -pi -e 's/directory\/casper/directory\/boot\/caine/g' scripts/casper
-		find . | cpio --create --format='newc' | gzip -c > $WORK/boot/caine/initrd.gz
-		cd -
-		rm -r $MNT/caine-inittmp
-		echo " done."
-	fi
+    if [ -f caine.iso ];then
+        echo "Copying Caine..."
+        mcdmount caine
+        cp -R $MNT/caine/casper $WORK/boot/caine #Live system
+        cp $MNT/caine/README.diskdefines multicd-working/
+        mkdir $WORK/CaineFiles
+        for item in AutoPlay autorun.exe autorun.inf comdlg32.ocx files license.txt page5 preseed Programs RegOcx4Vista.bat rw_common tabctl32.ocx vbrun60.exe WinTaylor.exe; do
+            [[ -a $MNT/caine/$item ]] && cp -R $MNT/caine/$item $WORK/CaineFiles
+        done
+        umcdmount caine
+        echo -n "Making initrd(s)..."
+        if [ -d $MNT/caine-inittmp ];then rm -r $MNT/caine-inittmp;fi
+        mkdir $MNT/caine-inittmp
+        cd $MNT/caine-inittmp
+        gzip -cd $WORK/boot/caine/initrd.gz | cpio -id
+        perl -pi -e 's/path\/casper/path\/boot\/caine/g' scripts/casper
+        perl -pi -e 's/directory\/casper/directory\/boot\/caine/g' scripts/casper
+        find . | cpio --create --format='newc' | gzip -c > $WORK/boot/caine/initrd.gz
+        cd -
+        rm -r $MNT/caine-inittmp
+        echo " done."
+    fi
 elif [ $1 = writecfg ];then
-	if [ -f $TAGS/lang ];then
-		LANGCODE=$(cat $TAGS/lang)
-	else
-		LANGCODE=en
-	fi
-	if [ -f caine.iso ];then
-		echo "label caine2
-		kernel /boot/caine/vmlinuz
-		initrd /boot/caine/initrd.gz
-		append live-media-path=/boot/caine ignore_uuid noprompt persistent BOOT_IMAGE=/casper/vmlinuz file=/cdrom/CaineFiles/custom.seed boot=casper -- debian-installer/language=$LANGCODE console-setup/layoutcode=$(cat $TAGS/lang)
-		" >> $WORK/boot/isolinux/isolinux.cfg
-	fi
+    if [ -f $TAGS/lang ];then
+        LANGCODE=$(cat $TAGS/lang)
+    else
+        LANGCODE=en
+    fi
+    if [ -f caine.iso ];then
+        echo "label caine2
+        kernel /boot/caine/vmlinuz
+        initrd /boot/caine/initrd.gz
+        append live-media-path=/boot/caine ignore_uuid noprompt persistent BOOT_IMAGE=/casper/vmlinuz file=/cdrom/CaineFiles/custom.seed boot=casper -- debian-installer/language=$LANGCODE console-setup/layoutcode=$(cat $TAGS/lang)
+        " >> $WORK/boot/isolinux/isolinux.cfg
+    fi
 else
-	echo "Usage: $0 {scan|copy|writecfg}"
-	echo "Use only from within multicd.sh or a compatible script!"
-	echo "Don't use this plugin script on its own!"
+    echo "Usage: $0 {scan|copy|writecfg}"
+    echo "Use only from within multicd.sh or a compatible script!"
+    echo "Don't use this plugin script on its own!"
 fi

```

---

### Post by juako on 2011-03-09
):P anybody here?

Allright i think that putting grub4dos and an /isos dir should be easy, as grub4dos is suppa easy to chainload from isolinux.

What i'm struggling now with is putting multicd.iso in a usb partition and boot it. What i did was copying all the iso contents in the (vfat 32) partition, run syslinux /dev/sdX (the whole usb) and making a copy of every isolinux dir to a syslinux dir, and in those dirs renaming every isolinux.cfg to syslinux.cfg. Wherever isolinux.cfg doesn't exist in a "isolinux" dir, i just copied to a syslinux.cfg file.

Then in every syslinux.cfg i replaced references to isolinux.cfg to syslinux.cfg and references to isolinux folders to syslinux folders.

It booted fine, but at least INSERT doesn't find its filesystem, i wonder why? Mint doesn't seem to boot properly too. I'll test more thorougly both the .iso and the usb in a virtualbox and in my real machine and report back. But...

Please, any clue? any answer????

---

### Post by maybeway36 on 2011-03-09
> **juako said:**
> Amazing script. I've updated a pentoo plugin posted before for 5.1 to version 6.4, and changed (in the "copy" action) a {} expansion to a for .. in loop, as the expansion was breaking with a stat error, what's strange is this happened only from the script, when i tried manually after the script stopped it worked fine.

```

#!/bin/sh
set -e
. ./functions.sh
#Pentoo plugin for multicd.sh
#version 6.4?
#Copyright (c) 2009 maybeway36
#
#Permission is hereby granted, free of charge, to any person obtaining a copy
#of this software and associated documentation files (the "Software"), to deal
#in the Software without restriction, including without limitation the rights
#to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#copies of the Software, and to permit persons to whom the Software is
#furnished to do so, subject to the following conditions:
#
#The above copyright notice and this permission notice shall be included in
#all copies or substantial portions of the Software.
#
#THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#THE SOFTWARE.

# BUGS
# modules directory is not read correctly, as it is searched for in /
if [ $1 = scan ];then
    if [ -f pentoo.iso ];then
        echo "Pentoo Linux"
    fi
elif [ $1 = copy ];then
    if [ -f pentoo.iso ];then
        echo "Copying Pentoo Linux..."
        mcdmount pentoo

        mkdir -p $WORK/boot/pentoo
        for item in modules tools win32 image.squashfs livecd; do
            cp -r $MNT/pentoo/$item $WORK/boot/pentoo
        done
        for item in pentoo isolinux.cfg pentoo.igz; do
            cp -r $MNT/pentoo/isolinux/$item $WORK/boot/pentoo
        done

        # Fix the isolinux.cfg
        sed -i 's@loop=/image.squashfs@loop=/boot/pentoo/image.squashfs subdir=/boot/pentoo@' $WORK/boot/pentoo/isolinux.cfg
        sed -i 's@kernel @kernel /boot/pentoo/@' $WORK/boot/pentoo/isolinux.cfg
        sed -i 's@initrd=@initrd=/boot/pentoo/@' $WORK/boot/pentoo/isolinux.cfg

        umcdmount pentoo
    fi
elif [ $1 = writecfg ];then
if [ -f pentoo.iso ];then
cat >> $WORK/boot/isolinux/isolinux.cfg << EOF
label pentoo
menu label ---> ^Pentoo Menu
com32 menu.c32
append /boot/pentoo/isolinux.cfg

EOF

cat >> $WORK/boot/pentoo/isolinux.cfg << EOF

label back
menu label Back to main menu
com32 menu.c32
append /boot/isolinux/isolinux.cfg

EOF

fi
else
    echo "Usage: $0 {scan|copy|writecfg}"
    echo "Use only from within multicd.sh or a compatible script!"
    echo "Don't use this plugin script on its own!"
fi

```

I have another multiboot i've made at hand with grub4dos and boots some 20 distros or so, but all are loopback chained to a grub4dos emulated drive. Its structure is as this

/boot
/boot/grub
/boot/grub4dos
/boot/grub4dos/menu/*.lst (submenus)
/iso/*.iso (isos only)
/menu.lst
grldr

I want to integrate these in the multicd iso, is this possible? Can isolinux and grub4dos coexist? If there arent any name clashes for folders or files, they can be chained right?

Anyway i might aswell try to write plugins for the one or two isos that multicd doesn't list as of now and get done. IIUC i can get the same effect with MEMDISK as with grub4dos "map".

After two days of learning all this stuff i'm seeing i'll have to drop the idea of an universal way to boot iso files, and multicd seems great for the "remaster distros" approach, nevertheless I'd like to keep the distros that are capable of booting directly from an iso in a single directory, and remaster the rest with multicd.

Having the isos right there has its advantages, the setup is way easier and they can be easily transferred, burned, etc. I hope some day all isos can be chained directly :(

Thanks for the pentoo update.
You can load GRUB4DOS from ISOLINUX. multicd.sh will detect grub.exe and add it as a boot option (it's stored as /boot/grub.exe); then, you can make an "includes" folder and put your menu.lst and the ISOs in there.

> **juako said:**
> ):P anybody here?

Allright i think that putting grub4dos and an /isos dir should be easy, as grub4dos is suppa easy to chainload from isolinux.

What i'm struggling now with is putting multicd.iso in a usb partition and boot it. What i did was copying all the iso contents in the (vfat 32) partition, run syslinux /dev/sdX (the whole usb) and making a copy of every isolinux dir to a syslinux dir, and in those dirs renaming every isolinux.cfg to syslinux.cfg. Wherever isolinux.cfg doesn't exist in a "isolinux" dir, i just copied to a syslinux.cfg file.

Then in every syslinux.cfg i replaced references to isolinux.cfg to syslinux.cfg and references to isolinux folders to syslinux folders.

It booted fine, but at least INSERT doesn't find its filesystem, i wonder why? Mint doesn't seem to boot properly too. I'll test more thorougly both the .iso and the usb in a virtualbox and in my real machine and report back. But...

Please, any clue? any answer????

If you're find with read-only access, you could just "dd" the .iso image to a USB drive (yay isohybrid!) I can't help you with anything more complex - I generally use DVD-Rs.

@juako: You shouldn't have to take away the ./functions.sh call - that's the .sh file that contains the mcdmount and mcdumount functions. If those functions don't work, something odd is going on. I'd also like to keep using the $MNT and $WORK variables, at least for now, in case I want to change them later.
Are there any other changes I need to make that have to do with newer versions of the ISO files?

---

### Post by kuadhual on 2011-03-15
> **juako said:**
> 

Parted Magic
```

diff -uNr multicd-6.4/plugins/pmagic.sh plugins/pmagic.sh
--- multicd-6.4/plugins/pmagic.sh	2011-03-08 10:26:55.156782001 -0300
+++ plugins/pmagic.sh	2010-12-28 01:11:39.000000000 -0300
@@ -1,6 +1,5 @@
 #!/bin/sh
 set -e
-. ./functions.sh
 #Parted Magic plugin for multicd.sh
 #version 6.3
 #Copyright (c) 2010 libertyernie

```


Hi, 
Somehow I think you generate the patch backward. 
I tried 6.4 and multicd-HEAD and try to run it with only parted magic 5.10. This is what I got:

```
sudo ./multicd.sh 
Password: 
md5sum: plugins/caine.sh: No such file or directory


Plugins that are not from the official release: plugins/caine.sh

Make sure you trust every script in the plugins folder - all these scripts will get root access!
Press Ctrl+C to cancel

Parted Magic
Parted Magic
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Parted Magic...
/home/share/iso/multicd/plugins/pmagic.sh: line 35: mcdmount: command not found

```

I re-add function.sh
(some how I have to download memtest manually. Btw, there's a new memtest 4.20)

```
#!/bin/sh
set -e
. ./functions.sh

#Parted Magic plugin for multicd.sh
#version 6.3
................
```

And I can generate the ISO successfully (I haven't test it though)

```

$ sudo ./multicd.sh 
md5sum: plugins/caine.sh: No such file or directory
md5sum: WARNING: 1 listed file could not be read
md5sum: WARNING: 1 computed checksum did NOT match

Plugins that are not from the official release: plugins/caine.sh
plugins/pmagic.sh 
Make sure you trust every script in the plugins folder - all these scripts will get root access!
Press Ctrl+C to cancel

Parted Magic
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Parted Magic...
mount: warning: /tmp/multicd-root/pmagic/ seems to be mounted read-only.
Downloading SYSLINUX...
Copying from installed SYSLINUX files...
Writing isolinux.cfg...
Building CD image...
Running isohybrid...

```


@maybeway36: I think you need to add md5 hash check when downloading memtest. My download failed (memtest size was 0byte) and the script still generate ISO files successfully.

---

### Post by juako on 2011-03-19
@maybeway36
> @juako: You shouldn't have to take away the ./functions.sh call - that's the .sh file that contains the mcdmount and mcdumount functions. If those functions don't work, something odd is going on. I'd also like to keep using the $MNT and $WORK variables, at least for now, in case I want to change them later.

@kuadhual
> 
Hi, 
Somehow I think you generate the patch backward. 
I tried 6.4 and multicd-HEAD and try to run it with only parted magic 5.10. This is what I got:

My mistake, indeed i had got backwards the patches :P, they are corrected now. I tried patching the origs and they work fine this time, thanks for pointing it out.

@maybeway36
> You can load GRUB4DOS from ISOLINUX. multicd.sh will detect grub.exe and add it as a boot option (it's stored as /boot/grub.exe); then, you can make an "includes" folder and put your menu.lst and the ISOs in there.

Totally, it's very easy as you say. I'll post the list of iso's that boot and mount everything correctly from a grub4dos emulated drive, [here's a thread in reboot.pro]("http://reboot.pro/5041/") where many are listed, and i have some others.

---

### Post by iomari on 2011-05-04
Greetings,
first off I would like to say that this tool is awesome. 

Now for my prob:

When trying to use backtrack.iso I keep getting the message:

[COLOR="Blue"]"-> ./multicd.sh

Plugins that are not from the official release:  ./plugins/kubuntu.sh
Make sure you trust every script in the plugins folder - all these scripts will get root access!
Press Ctrl+C to cancel

BackTrack
super_grub_disk_hybrid-1.98s1
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying BackTrack...
mount: warning: /tmp/multicd-root/backtrack/ seems to be mounted read-only.
Making initrd(s)...gzip: multicd-working/boot/backtrack/initrd.gz: No such file or directory
cpio: premature end of archive

-> 
"[/COLOR]

I'm using multicd version 6.5 and backtrack version 4 r2.
any help will be welcome.

Also, how can I transfer this image to a usb drive so I can boot he drive and have the multicd menu but also be able to use the drive as a normal usb drive other than using unetbootin which I can't get to work?

Ibrahim

---

### Post by maybeway36 on 2011-05-04
I don't know how to get USB working, but I'll look into the issue with Backtrack soon.

---

### Post by iomari on 2011-05-06
> **maybeway36 said:**
> I don't know how to get USB working, but I'll look into the issue with Backtrack soon.

Ok, Thanks. I'm impatiently waiting ......... :D

---

### Post by maybeway36 on 2011-05-07
I fixed backtrack; the fix is in the git repo now.
Here's a link:
[http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=blob_plain;f=plugins/backtrack.sh;hb=HEAD](http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=blob_plain;f=plugins/backtrack.sh;hb=HEAD)
Name the file "backtrack.sh" and use it to replace your old one.
I fixed Caine in the same way, but didn't test it yet.

---

### Post by legrostdg on 2011-05-11
Is it possible to use several debian images at the same time?
For example, I'd like to use debian-6.0.1a-amd64-businesscard.iso and debian-6.0.1a-i386-businesscard.iso in the same time multicd.iso...
Is it possible to set the name (which appears in grub) of each iso?
Would it be possible to support grml64 and debian-6.0?

---

### Post by maybeway36 on 2011-05-11
I don't know if you can use multiple Debian images, because they all have the same directory structure. But maybe I'll try it.
To change the name, the easiest thing to do is to go to the plugin's .sh file and find where it is written to the menu (it begins with "menu label"), and change that line.

---

### Post by iomari on 2011-05-12
> **maybeway36 said:**
> I fixed backtrack; the fix is in the git repo now.
Here's a link:
[http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=blob_plain;f=plugins/backtrack.sh;hb=HEAD](http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=blob_plain;f=plugins/backtrack.sh;hb=HEAD)
Name the file "backtrack.sh" and use it to replace your old one.
I fixed Caine in the same way, but didn't test it yet.

Thanks. I now notice that puppy linux shows on y menu but fails to boot. When I look in the iso, I see the puppy folder is not there. I also notice that this only happens when puppy is burned along other supported distros. This problem does nto happen if I try puppy by itself. Is there a fix for this?

I just updated the caine script and now when compiling It stops with the following error:

[COLOR="Blue"]
-> ./multicd.sh
md5sum: WARNING: 3 computed checksums did NOT match

Plugins that are not from the official release: plugins/backtrack.sh
plugins/caine.sh
plugins/pmagic.sh ./plugins/kubuntu.sh
Make sure you trust every script in the plugins folder - all these scripts will get root access!
Press Ctrl+C to cancel

Caine
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Caine...
mount: warning: /tmp/multicd-root/caine/ seems to be mounted read-only.
cp: cannot stat `/tmp/multicd-root/caine/AutoPlay': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/autorun.exe': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/autorun.inf': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/comdlg32.ocx': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/files': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/license.txt': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/page5': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/Programs': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/RegOcx4Vista.bat': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/rw_common': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/tabctl32.ocx': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/vbrun60.exe': No such file or directory
cp: cannot stat `/tmp/multicd-root/caine/WinTaylor.exe': No such file or directory

-> 
[/COLOR]

---

### Post by iomari on 2011-05-12
Maybe I'm missing something on the caine issue I'm having but the line in caine.sh:

[COLOR="Blue"]"cp -R $MNT/caine/{AutoPlay,autorun.exe,autorun.inf,comdlg32.ocx,files,license.txt,page5,preseed,Programs,RegOcx4Vista.bat,rw_common,tabctl32.ocx,vbrun60.exe,WinTaylor.exe} $WORK/CaineFiles"[/COLOR]

keeps failing. When I check the mounted caine.iso, I don't see any of the above files so how can they be copied?

What am I not seeing?

---

### Post by maybeway36 on 2011-05-12
The script hasn't been updated for new versions of caine. Adding another thing on my todo list.
I'm not quite sure what the problem with Puppy is.

EDIT: What version of Puppy are you using? And are you using more than one puppy?

---

### Post by iomari on 2011-05-13
> **maybeway36 said:**
> The script hasn't been updated for new versions of caine. Adding another thing on my todo list.
I'm not quite sure what the problem with Puppy is.

EDIT: What version of Puppy are you using? And are you using more than one puppy?

Thanks for your response. I got caine to work by modifying the caine script. see the attachment. 
Puppy 525.
I also just discovered that weaknet does not boot. I'm using the latest version as of last week of weaknet.

It also seem that pmagic does not boot. When looking at the screen output, it's trying to load pmagic 4 where I have pmagic 6.

Weaknet: "/init: line 3:  can't open /dev/sdb: no medium found:

---

### Post by maybeway36 on 2011-05-13
Thanks for the caine.sh.
I can't figure out the Puppy problem. Could you post the output of "ls" in your folder?
Also, on the CD that has Puppy on the menu but no Puppy folder, are there "vmlinuz" and "initrd.gz" files in the root directory?

---

### Post by iomari on 2011-05-13
> **maybeway36 said:**
> Thanks for the caine.sh.
I can't figure out the Puppy problem. Could you post the output of "ls" in your folder?
Also, on the CD that has Puppy on the menu but no Puppy folder, are there "vmlinuz" and "initrd.gz" files in the root directory?

here is the output of the source files:

[COLOR="Blue"]-> ls -1
Super Grub Legacy.img
Super Grub2.img
caine.iso
changelog.txt
clonezilla.iso
combine.sh
dban.iso
fdfullcd.iso
functions.sh
hirens.iso
i386.k.ubuntu.defaultname
i386.k.ubuntu.iso
i386.k.ubuntu.version
i386.ubuntu.defaultname
i386.ubuntu.iso
i386.ubuntu.version
isos.txt
knoppix.iso
kubuntu-11.04-desktop-i386.iso
memtest
multicd.iso
multicd.sh
ping.iso
plugins
plugins.md5
pmagic.iso
puppy.iso
riplinux.iso
syslinux.tar.gz
trk.iso
ubcd.iso
ubuntu-11.04-desktop-i386.iso[/COLOR]

here is the output of the mounted iso:

[COLOR="Purple"]-> ls -1
CaineFiles
HBCD
KNOPPIX6
README.diskdefines
antivir
boot
fdos
freedos
gem.bat
gemapps
initrd.gz
lupu_525.sfs
pmagic
setup.bat
trk3
ubcd
ubcd-license.txt
vmlinuz[/COLOR]

---

### Post by maybeway36 on 2011-05-14
Thanks! It turned out to be a mistake in the code writing the menu entires - I mistakenly assumed that Puppy always had its own folder. It's fixed now in the git repository version.

---

### Post by iomari on 2011-05-14
> **maybeway36 said:**
> Thanks! It turned out to be a mistake in the code writing the menu entires - I mistakenly assumed that Puppy always had its own folder. It's fixed now in the git repository version.


Cool. Puppy now works, pmagic works, weakerthan works. :-)

The last one still not working is Freedos Full. Reports Invalid Opcode.

---

### Post by dmontaldo on 2011-05-14
Great work!
Can you patch the debian-installer script to support the new version?


~/dev/git/multicd/plugins$ git diff
diff --git a/plugins/debian-install.sh b/plugins/debian-install.sh
index 9decbe3..cf2c5f3 100755
--- a/plugins/debian-install.sh
+++ b/plugins/debian-install.sh
@@ -24,7 +24,7 @@ set -e
-       echo "debian-5*.iso debian-install.iso none"
+       echo "debian-6*.iso debian-install.iso none"

Thanks!

---

### Post by iomari on 2011-05-16
This is awesome. I just did a dcfldd with the iso to my flash and it worked perfectly. No more Cd/DVD's for me. :-)

I didn't notice that the script ran isohybrid at the end until today. Now I 'm going to make a super huge iso with every possible supported distro and tool to my usb HD and see how it comes out.

On a side note. Nothing to do with my revelation above :-), kubuntu and the gnome version (both 11.04) just hangs on the splash screen when loading.

Also, the latest version of geexbox freezes on start menu. works as standalone CD so it's not the iso.

Backtrack 5 not working:

[COLOR="Blue"]-> ./multicd.sh
md5sum: WARNING: 1 computed checksum did NOT match

Plugins that are not from the official release: plugins/netbootcd.sh ./plugins/kubuntu.sh
Make sure you trust every script in the plugins folder - all these scripts will get root access!
Press Ctrl+C to cancel

BackTrack
Endian Firewall
WeakNet Linux
MSDos6.22
Super Grub Legacy
Super Grub2
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying BackTrack...
mount: warning: /tmp/multicd-root/backtrack/ seems to be mounted read-only.
cp: cannot stat `/tmp/multicd-root/backtrack/boot/vmlinuz': No such file or directory

-> [/COLOR]

---

### Post by maybeway36 on 2011-05-17
No new bugfixes to report, but I now have seperate plugins for Debian i386 netinst (debian-install.iso) and Debian amd64 netinst (debian-install64.iso). See if using them both works. I think it might.
[http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=snapshot;h=HEAD;sf=tgz](http://git.tuxfamily.org/?p=gitroot/multicd/multicd.git;a=snapshot;h=HEAD;sf=tgz)

---

### Post by iomari on 2011-05-17
After your last git update, i receive this error when backtrack is not part of the collection:

[COLOR="Blue"]./functions.sh: line 144: multicd-working/boot/backtrack/backtrack.cfg: No such file or directory[/COLOR]

Can you make Endian Firewall a sub menu like you did for backtrack?

Can the full windows 7 DVD be used instead of the recovery? I know it's big but I'm working on my super iso to put on my USB HD.

---

### Post by maybeway36 on 2011-05-18
> **iomari said:**
> After your last git update, i receive this error when backtrack is not part of the collection:

[COLOR="Blue"]./functions.sh: line 144: multicd-working/boot/backtrack/backtrack.cfg: No such file or directory[/COLOR]
Thanks for the tip. I just fixed it.
> Can you make Endian Firewall a sub menu like you did for backtrack?
Sure. I'll do that soon.
> Can the full windows 7 DVD be used instead of the recovery? I know it's big but I'm working on my super iso to put on my USB HD.
I'm not sure. I've never tried it.

---

### Post by iomari on 2011-05-18
Thanks for the speedy reply. :-)

There is still the issue of ubuntu not booting.

---

### Post by Blasphemist on 2011-05-18
> **maybeway36 said:**
> Thanks for the tip. I just fixed it.

Sure. I'll do that soon.

I'm not sure. I've never tried it.

I don't mean to any way be rude but I am in need of creating a usb multi distro installer that includes bootable utilities as well. I've been looking at this [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

Other that the obvious fact that it seems I can reach you here should I need, can you tell me what the benefits are in using your script vs. yumi? Your script and yumi are the best options I've found and I just want to decide on my direction.

---

### Post by maybeway36 on 2011-05-18
You could always use them both :)
YUMI, I think, works with USB but not with a CD/DVD. It uses SYSLINUX to boot the USB drive. Unlike with MultiCD, you could use it and still have your USB drive be writable (MultiCD uses an ISO image with isohybrid, which makes it read-only.)
Also, YUMI is a GUI program for Windows, while MultiCD is a text-mode script that only works on Linux.

---

### Post by iomari on 2011-05-19
Greetings,

If I want to add both the 32 and 64 bit version of win7recovery, can I make a copy of the win7recovery.sh script, rename it and make the necessary changes in the new file?

check the attachments

btw: in case anyone is looking for the win 7 recovery disk: [http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/)

Ok, I tried this and both 32 and 64 have a  "windows failed to start....." error. So I tried the original script and just the 32bit win7recovery.iso and I get the same thing. So the problem seems to be that the default scripts for the default iso don't work. If you can get that to work then I guest my new scripts for both version will work.
Just to confirm, I burned the win7recovery iso directly and it works so the problem is not the iso.

---

### Post by maybeway36 on 2011-05-19
Are you running them in a virtual machine or on a real PC?
I can tell you that your plugins won't work properly, because one will overwrite the other on the multicd being made. Maybe ISO emulation would work here...

---

### Post by iomari on 2011-05-19
> **maybeway36 said:**
> Are you running them in a virtual machine or on a real PC?
I can tell you that your plugins won't work properly, because one will overwrite the other on the multicd being made. Maybe ISO emulation would work here...

understood, but remember that I tried the default script by itself and it still did not work. Btw, I'm not running a virtual machine.

---

### Post by maybeway36 on 2011-05-20
It worked for me (burning the 64-bit Win7 recovery disc to a CD and running it on my PC win Win7), so I'm not quite sure what the problem is...

---

### Post by iomari on 2011-05-21
> **maybeway36 said:**
> It worked for me (burning the 64-bit Win7 recovery disc to a CD and running it on my PC win Win7), so I'm not quite sure what the problem is...

are you saying that it worked through your script or that you burned the recovery disc directly? Because mine works directly. But when I burn it as a multicd, even when it's the only app, it crashes as explained. If yours works as a multicd then I'm confused. I thought it may have been a 32 vs 64 prob but I tried both versions individually. If I could only get this to work, and of course ubuntu/kubuntu, which still freezes at it's graphical initial splash screen, then I'll truly have my "perfect" multi boot CD/DVD/Flash.

---

### Post by maybeway36 on 2011-05-21
Mine does work through MultiCD...
What sort of error do you get when you run it? If there's an error message, take a screenshot and post it here.

---

### Post by iomari on 2011-05-22
> **maybeway36 said:**
> Mine does work through MultiCD...
What sort of error do you get when you run it? If there's an error message, take a screenshot and post it here.

A scream shot may be difficult since there is no OS loaded at that point. I'm not using a VM. But here is what it says:
[COLOR="Blue"]
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert Windows Installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have the disc, contact your system administrator or computer manofacturer for assistance.


File: \Boot\BCD

Status: 0xc0000225

Info: An error occurred while attempting to read the boot configuration data.
[/COLOR]

---

### Post by maybeway36 on 2011-05-22
Sorry, I guess I can't help you, because I don't know what's causing the problem.

---

### Post by iomari on 2011-05-22
> **maybeway36 said:**
> Sorry, I guess I can't help you, because I don't know what's causing the problem.

no prob. I'll keep looking for an answer. thanks for all your previous help.

I forgot, what of the ubuntu problem. Both ubuntu and kubuntu still hang on the boot screen showing the ubuntu logo.

---

### Post by maybeway36 on 2011-05-23
I'll download Ubuntu 11.04 and look into it. Thanks.

---

### Post by iomari on 2011-05-23
> **maybeway36 said:**
> I'll download Ubuntu 11.04 and look into it. Thanks.

Thanks, I'll be waiting

---

### Post by maybeway36 on 2011-05-24
The Ubuntu 11.04 desktop ISO is working for me. Try running it without the "quiet" and "splash" options (you can edit options by pressing Tab on a menu entry) and see what error you get.

---

### Post by iomari on 2011-05-25
> **maybeway36 said:**
> The Ubuntu 11.04 desktop ISO is working for me. Try running it without the "quiet" and "splash" options (you can edit options by pressing Tab on a menu entry) and see what error you get.

Thanks for the git updates. After removing splash and quite, the boot process has no errors until it suddenly stops dead with the last item on screen:

[COLOR="RoyalBlue"]saned disabled: edit /etc/default/saned[/COLOR]

I don't believe saned is the problem but rather whatever should come next is freezing the process. I'll still play around with the boot options and see if it works.

---

### Post by iomari on 2011-06-14
Greetings,
is it possible to add the following app to this collection?

[http://redobackup.org/](http://redobackup.org/)

It has a casper folder and uses isolinux.

Thanks

---

### Post by drdccd on 2011-06-16
Hi .....
thank you very much for this script...i`m now advising my friends & instructor  to switch into linux distro...i wanna to make a DVD-DL with several OS so i can "show-explain=then=>try" the most suitable distro for them.

I`m facing a problem with the following Distro :MINT KATAY 32bit DVD ([link]("http://www.linuxmint.com/edition.php?id=81")).
i added macpup & mint but the script can not detect the linuxmint.iso even i changed the name of the dvd into linuxmint.dvd.

1-what is the problem?
2-would you mind adding Pinguy OS , Zorin OS ,& Fusion linux...these distros are ""out of the box"" ...they include every thing "drivers,codecs,...etc" they are really helpful esp if you are introducing linux to newbie as most of them says.."OS without  codec or tools..programs? don bother go to windows:(".

thank you in advance & thank you ubuntu .

---

### Post by maybeway36 on 2011-06-22
If you name the ISO "linuxmint.iso" then the script should detect it. If you name it anything not ending in .iso, then it won't.
I'll look into those other distros you mentioned. It shouldn't be hard to add them, but I'll have to download them first.

---

### Post by drdccd on 2011-06-22
.

---

### Post by drdccd on 2011-06-22
> **maybeway36 said:**
> If you name the ISO "linuxmint.iso" then the script should detect it
unfortunately it did not detect the iso, i`ll try it with another image.

> **maybeway36 said:**
> 
I'll look into those other distros you mentioned. It shouldn't be hard to add them, but I'll have to download them first.
Thank you very much for your time!!

---

### Post by iomari on 2011-06-23
any luck on:
[http://redobackup.org/](http://redobackup.org/)

:D

---

### Post by iomari on 2011-06-25
thanks for the redo plugin.

sorry but i'm not seeing the redo plugin in the latest git repo.

---

### Post by beew on 2011-06-25
I am not sure what is the point of going through the troubles to make a multiboot live CDs. CDs are slow, noisy, bulky, fragile and can't save settings and burning CD is relatively easy to go wrong. Most netbooks don't even have CD ROMS. IMO CDs are dying technology  going the way of floppies. I sure would not show off Linux to my friends with a live CD because that makes Linux looks so yesterday.

 There is a tutorial for making a multi-boot usb

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

There is also a Ubuntu utility for making multiboot usb  that you can download and install

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Sorry for the spoiling the enthusiasm, I just can't see the point.

---

### Post by iomari on 2011-06-25
> **beew said:**
> I am not sure what is the point of going through the troubles to make a multiboot live CDs. CDs are slow, bulky and can't save settings. IMO it is going the way of floppies.

 There is a tutorial for making a multi-boot usb

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

There is also a Ubuntu utility for making multiboot usb  that you can download and install

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Sorry for the spoiling the enthusiasm, I just can't see the point.

The point that you can't see is that each iso that you make with this tool uses isohybrid which allows you to "burn" it to flash or usb HD. Also, some older systems can't boot from usb.

---

### Post by iomari on 2011-06-26
still waiting for the missing redobackup plugin from the git repo.:lolflag:

---

### Post by drdccd on 2011-06-26
> **beew said:**
> I am not sure what is the point of going through the troubles to make a multiboot live CDs. CDs are slow, noisy, bulky, fragile and can't save settings and burning CD is relatively easy to go wrong. Most netbooks don't even have CD ROMS. IMO CDs are dying technology  going the way of floppies. I sure would not show off Linux to my friends with a live CD because that makes Linux looks so yesterday.

 There is a tutorial for making a multi-boot usb

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

There is also a Ubuntu utility for making multiboot usb  that you can download and install

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Sorry for the spoiling the enthusiasm, I just can't see the point.

what are you saying? Do you wanna  me to sacrifice 4-8 GB drive to save OS? then who told you ""most of Notebook"" did not include DVD?What about old laptop?
We are in new era dude,if you wanna to ""waste" flash thats up to you,& if you wanna to "waste" a DVD,that also up to you,but let me ask you one question: which is cheaper & effective?
you can waste 0.15$ for a DVD then you can archive it, you can also waste 8$ USB then throw it in the desk till the required time,&,what about losing your usb drive in critical time?
----------------------------------------

please maybeway add the following Iso to the supported list, i`ll try to cheat to add it as gparted or other linux in the mean time.
SabayonLinux

---

### Post by maybeway36 on 2011-06-26
This utility makes an ISO image that can also be written onto a USB flash drive with dd. Although the image is read-only when you do it this way, it seems a lot simpler to me than manually copying the files and making a FAT partition bootable, especially if you're going to be updating it a lot. In other words, MultiCD lets you use your USB drive like a CD-RW (but bigger!)

Also, some old computers won't boot from USB. But this is becoming less and less of a problem.

By the way, my other project NetbootCD is bootable from a set of 5 floppies: [http://netbootcd.tuxfamily.org](http://netbootcd.tuxfamily.org) And no, I can't justify that.

---

### Post by maybeway36 on 2011-06-26
> **iomari said:**
> still waiting for the missing redobackup plugin from the git repo.:lolflag:

Fixed :)

---

### Post by drdccd on 2011-06-27
please add zorin,Pinguy,Fusion-linux & Sabayon to the supported iso.:popcorn:
I tried to add zorin as iso files which support live media path kernel parmeter but failed.

thank you very much:D

---

### Post by iomari on 2011-06-27
maybeway36

thanks again.
BTW, I think you need to update your home page with all the new distros you have added recently.

---

### Post by maybeway36 on 2011-06-27
> **drdccd said:**
> please add zorin,Pinguy,Fusion-linux & Sabayon to the supported iso.:popcorn:
I tried to add zorin as iso files which support live media path kernel parmeter but failed.

thank you very much:D

The version in the git repository has Zorin, Pinguy, and Fusion Linux. Sabayon will be next, then I'll release it as version 6.7.

---

### Post by drdccd on 2011-07-01
> **maybeway36 said:**
> The version in the git repository has Zorin, Pinguy, and Fusion Linux. Sabayon will be next, then I'll release it as version 6.7.

people,..multicd.sh6.7 is out...thank you very much for your effort maybeway36.

---

### Post by iomari on 2011-07-01
IS 6.7 the same as the current git?

---

### Post by drdccd on 2011-07-01
yes it`s the same but Sabayon is added.
Unfortunatly sabayon,fusion linux could not be added!!!!! the script could not find the iso!!! this is the printscreen of my desktop:
[IMG]http://ubuntuforums.org/%3Ca%20href=http://img833.imageshack.us/i/screenshotsa.png/%20target=_blank%3E[IMG]http://img833.imageshack.us/img833/2428/screenshotsa.png[/IMG]

[[IMG]http://img833.imageshack.us/img833/2428/screenshotsa.th.png[/IMG]]("http://img833.imageshack.us/i/screenshotsa.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")


[IMG]http://www.freeimagehosting.net/image.php?ef5a63c361.jpg[/IMG]
[IMG]http://imageshack.us/photo/my-images/21/94020200.jpg/[/IMG]
[http://www.freeimagehosting.net/image.php?ef5a63c361.jpg](http://www.freeimagehosting.net/image.php?ef5a63c361.jpg)
[IMG]http://www.freeimagehosting.net/image.php?ef5a63c361.jpg[/IMG]
NB i faced this problem when i tried to add linux mint.
------------------------------------------------------------------------------
UPDATE:
i opened multicd.sh using text editor,copied the name of each iso(fusion & sabayon then renamed the original iso) IT WORKS,,,,,the problem was with the capital letter of the sabayon & fusion as i noticed later>>>
[IMG]http://ubuntuforums.org/%3Ca%20href=http://img823.imageshack.us/i/screenshot1si.png/%20target=_blank%3E[IMG]http://img823.imageshack.us/img823/6451/screenshot1si.th.png[/IMG]

---

### Post by drdccd on 2011-07-02
sabayon gave me this error "using virtual machine vbox"
[IMG][[IMG]http://img843.imageshack.us/img843/6381/errorpk.jpg[/IMG]]("http://imageshack.us/photo/my-images/843/errorpk.jpg/")

i know that virtual machine are not perfect,what do u think?

---

### Post by maybeway36 on 2011-07-04
It is right now. :)

---

### Post by drdccd on 2011-07-06
> **maybeway36 said:**
> It is right now. :)

thank you it works smoothly,i hope that you update your website,
btw...what is your favorite OS?

---

### Post by iomari on 2011-07-06
Yes, I agree. You really should update the website soon. Many new people won't have an idea how many more distros you have added over the past few months.

Great work. You should win an award. :-)

---

### Post by maybeway36 on 2011-07-06
> **drdccd said:**
> thank you it works smoothly,i hope that you update your website,
btw...what is your favorite OS?

I use Windows 7 sometimes and Linux Mint Debian edition sometimes. All the MultiCD work is done on the latter (obviously).

---

### Post by iomari on 2011-07-11
any chance of adding xbmc? :)
[http://mirrors.xbmc.org/releases/live/xbmc-10.1-live.iso](http://mirrors.xbmc.org/releases/live/xbmc-10.1-live.iso)

---

### Post by maybeway36 on 2011-07-13
I'll try adding it next time I work on multicd.

---

### Post by satyanash on 2011-07-27
Hi,
I tried your script with some .iso files, and it works wonderfully well if you know what to do. However i was wondering, that since you do support Arch Linux, will all the other distros built on Arch, like archbang,chakra etc also work ?
If yes, how can i put 2 Arch based distros on a same DVD? since the script renames ArchLinux iso files to arch.iso.?
Thanks in advance.
Satyajeet:)

---

### Post by maybeway36 on 2011-07-27
I'm not sure you would be able to use the same plugin. But I'll download ArchBang and check it out.

---

### Post by imgx64 on 2011-08-01
Is Fedora live CD not supported?

Could it be because of this bug: [https://bugzilla.redhat.com/show_bug.cgi?id=650672](https://bugzilla.redhat.com/show_bug.cgi?id=650672) ?

---

### Post by TheRoach on 2011-08-02
Has the structure of Parted Magic changed? I tried adding it to a multi-cd and instead of starting it, the cd just jumps back to the menu :(

---

### Post by maybeway36 on 2011-08-06
> **imgx64 said:**
> Is Fedora live CD not supported?

Could it be because of this bug: [https://bugzilla.redhat.com/show_bug.cgi?id=650672](https://bugzilla.redhat.com/show_bug.cgi?id=650672) ?

It's not because of the bug; I just haven't gotten around to adding it.

> **TheRoach said:**
> Has the structure of Parted Magic changed? I tried adding it to a multi-cd and instead of starting it, the cd just jumps back to the menu :(

I'm not sure. I'll have to check.

---

### Post by TheRoach on 2011-08-22
Hi,

trying to set up a multiboot-CD to a specific menu order. It says to rename the plug-ins as they are run alphabetically. My problem is: Where do I find the names of the plug-ins so I can rename them? Simply reordering the options when the bootmenu is created doesn't do a thing, neither does reordering the copying-scripts. I tried renaming, but I could only find how to change the kernelname, with the order unchanged.

Help would be greatly appreciated.

The Roach

---

### Post by Inkayacu on 2011-08-28
Hello, and thank you for multicd.sh, I love this script.

I tried making a new iso with Arch, LMDE, and Pinguy, plus PartedMagic.  This gave me an error, but when I took the Arch iso out of the directory, then everything worked, and I successfully tested the generated iso in Virtualbox.

I was attempting to use the x86-64 netinstall image for Arch, this was the terminal output:
```
Copying Arch Linux...
cp: cannot stat `/home/dg/Desktop/multicd-to-usb/multicd/temporary-mountpoints/arch/boot/x86_64/vmlinuz': No such file or directory
```The version of the script I was using is multicd-6.7.sh. Is there any way to make Arch work?

Thanks again!

---

### Post by buttate_la_pasta on 2011-08-30
The latest Arch installer (2011.08.19) uses kernel 3.0 and the kernel is "vmlinuz-linux" not "kernel26" anymore. Besides,  it would be cool to have support for the "dual architectures" netinstall image :)

---

### Post by maybeway36 on 2011-08-31
Arch Linux netboot ISOs work in the git repo version now. (You can name the dual-arch version "archdual.iso" or just keep the default name "archlinux-2011.08.19-netinstall-dual.iso".)

---

### Post by asifnaz on 2011-09-01
i was looking for a similar thing

---

### Post by buttate_la_pasta on 2011-09-01
> **maybeway36 said:**
> arch linux netboot isos work in the git repo version now. (you can name the dual-arch version "archdual.iso" or just keep the default name "archlinux-2011.08.19-netinstall-dual.iso".)


megathanks!!! ^^

---

### Post by buttate_la_pasta on 2011-09-08
It seems something is wrong with Hiren's Boot CD, at least with version 14.1 (I haven't tried older versions). The DOS programs don't work - it seems that no one of them can find the "drive" they are axpecting to use, while miniXP and GParted from the same CD are fine.

---

### Post by maybeway36 on 2011-09-17
Version 6.8 is out, it has lots of bugfixes.

@buttate_la_pasta: I don't have that version of Hiren's, and I probably won't have the time soon to get to supporting it.

---

### Post by maruel on 2011-09-28
> Version 6.8 is out, it has lots of bugfixes.Hi! Found a bug. When making a multicd using partedmagic-6.6-i686.iso (lastest stable release) the boot process fails as pmagic can never be booted. Boot manager just stays looping at automatic boot. The iso works fine on its own.

To reproduce: Download syslinux-4.04.tar.gz and place it inside multicd folder. Rename it as syslinux.tar.gz. Copy partedmagic-6.6.iso to multicd folder and rename it to pmagic.iso. (I also added slitaz and sysrcd just for the sake of trying). Run multicd from terminal. Everything will go fine.

Tested in virtualbox. If I edit the *1. Default settings (Runs from RAM)* entry inside *PartedMagic* boot section to
```
/pmagic/bzImage initrd=/pmagic/initramfs ro
```The distro will boot.
Original line contains the following
```
.com32 linux.c32 /pmagic/bzImage initrd=/pmagic/initramfs edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB
```Can you please fix it?

Thanks :popcorn:

---

### Post by maybeway36 on 2011-10-01
It will be fixed in the newest version on the git repository (once I can upload it). Thanks.

---

### Post by iomari on 2011-10-10
Greetings,

with the latest git source I get the following when i try to compile any iso:

[COLOR="Blue"]-> ./multicd.sh -i
./plugins/centos-boot.sh: line 82: syntax error: unexpected end of file
./plugins/centos-boot.sh: line 82: syntax error: unexpected end of file[/COLOR]
 even if I remove the centos.sh I still get:

[COLOR="Blue"]./multicd.sh -i
./plugins/scientific-boot.sh: line 27: syntax error near unexpected token `elif'
./plugins/scientific-boot.sh: line 27: syntax error near unexpected token `elif'[/COLOR]

So I've reverted back to the previous git compilation. Any suggestions as to why i get these errors?
BTW,opensuse 11.4

---

### Post by asensio on 2011-10-11
iomari,

just edit the file ./plugins/centos-boot.sh adding a "fi" (no quotes) at the end of the file, line 82. Then edit the file ./plugins/scientific-boot.sh (at the end of line 25 there's a typo) change "thne" to "then" (again, no quotes). Hope it helps, cheers :-)

Everybody,
I'm having a problem with TinyCore/MultiCore and multicd-6.8.sh.
Using multicore_3.8.4.iso, the script tries and fails to download SYSLINUX (&#8220;pub/linux/utils/boot/syslinux&#8221;not found)
With MultiCore 4.0.1 (current release) there's no bzImage in .../multicd/temporary-mountpoints/tinycore/boot/
What do I do?

Thanks in advance
**ASENSIO**

---

### Post by iomari on 2011-10-12
Thanks. It worked.

---

### Post by asensio on 2011-10-12
It seems the download URL to Syslinux is down... I changed it in the multicd-6.8.sh file, changed it to (lines 1892 and 1898): [http://mirror.muntinternet.net/pub/linux/boot/syslinux/syslinux-4.04.tar.gz](http://mirror.muntinternet.net/pub/linux/boot/syslinux/syslinux-4.04.tar.gz).

But I keep getting the Tinycore error... could someone help?
Thanks

---

### Post by arashiko28 on 2011-10-13
How can I differentiate Ubuntu 32bits, Ubuntu 64bits from Xubuntu and Lubuntu? Because when I create the CD I end up with 4 files called Ubuntu and once burned turned out to be 4 copies of the same version.

---

### Post by oldfred on 2011-10-13
I use this - [COLOR=DarkRed]uname -m[/COLOR] in Ubuntu, not sure if same in other versions?

if [ $(uname -m) == 'x86_64' ]; then
# 64-bit
apt-get install w64codecs libdvdcss2
else
# 32-bit
apt-get install w32codecs libdvdcss2
fi

---

### Post by arashiko28 on 2011-10-13
OK, that's for 32, 64 bits, but what about he other 2 distros? multicd marks them as Ubuntu, and there is my huge problem. Xubuntu and Lubuntu ends up as Ubuntu.

---

### Post by yotam on 2011-10-14
With the following two ISOs:
  **linuxmint-201109-xfce-dvd-32bit.iso**
  **xubuntu-11.10-desktop-i386.iso**
Here's what I got:

```
$ ./multicd.sh
multicd.sh 6.8
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Linux Mint 201109-xfce-dvd-32bit
Xubuntu (32-bit) 11.10
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Linux Mint 201109-xfce-dvd-32bit...
Copying Xubuntu (32-bit) 11.10...
Unpacking and copying SYSLINUX files...

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```

Am I doing something wrong, or Xubuntu-11.10 is simply not supported?

---

### Post by maybeway36 on 2011-10-20
> **arashiko28 said:**
> OK, that's for 32, 64 bits, but what about he other 2 distros? multicd marks them as Ubuntu, and there is my huge problem. Xubuntu and Lubuntu ends up as Ubuntu.

Use the -i option with multicd, and it should let you give each Ubuntu ISO its own name.

---

### Post by maybeway36 on 2011-10-20
> **yotam said:**
> With the following two ISOs:
  **linuxmint-201109-xfce-dvd-32bit.iso**
  **xubuntu-11.10-desktop-i386.iso**
Here's what I got:

```
$ ./multicd.sh
multicd.sh 6.8
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Linux Mint 201109-xfce-dvd-32bit
Xubuntu (32-bit) 11.10
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Linux Mint 201109-xfce-dvd-32bit...
Copying Xubuntu (32-bit) 11.10...
Unpacking and copying SYSLINUX files...

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```

Am I doing something wrong, or Xubuntu-11.10 is simply not supported?

Looks like the SYSLINUX problem people on the last page were having. Xubuntu should be supported.

---

### Post by tent405 on 2011-12-15
I have found an extremely annoying bug in multicd.
It does not support directories with spaces in their names.

```
/usr/share/multicd/plugins/avg.sh: 8: [: /media/smallstorage/software/operating: unexpected operator
+ mkdir /media/smallstorage/software/operating systems/temporary-mountpoints/avg
mkdir: cannot create directory `/media/smallstorage/software/operating': File exists
mkdir: cannot create directory `systems/temporary-mountpoints/avg': File exists
```

The fix for this is so simple too! Just replace all variables in the scripts surrounded by double quotes and curly brackets. 
I've attached a diff of the main script from the update I made to enable directory spaces. 
The plugins all have to be redone too, ```
sed -i
``` should work for that

---

### Post by iomari on 2012-03-28
greetings,
kaspersky does not move past it's boot menu. If you try to execute any of the menu items, nothing happens. Is there an updated sh file for it?

---

### Post by lkraemer on 2012-04-23
maybeway36,
There are several Hard Drive Diagnostic files that would be nice to add to  multicd.  These are referenced at:
[http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)

Hitachi Drive Fitness Test - Filename dft_416_b00.iso

Maxtor PowerMax Ver 4.23 - Filename PwrMx423En.iso

Seagate  SeaTools for DOS Ver 2.23 - Filename SeaToolsDOS223ALL.iso

Western Digital  Data Lifeguard Diagnostic v5.04f for DOS 
                                  - Filename Diag504fCD.iso
 
Would it be possible for you to add these to Multicd?

I am making a test CD with IMG files of Spinrite 5 & 6 to try out Multicd.

Try as I might, I can make a Multicd.iso, but when I burn the ISO to a CDRW
with Brasero, it doesn't boot.  I've used three different CDRW's.  Beats me.


I downloaded all the multicd files from the git area and they are all owned by root:root.
Should I change them all to larry:larry ????  I've tried as root and as user larry
and the cdrw doesn't boot.  Ideas?

 
Thanks,

lk

---

### Post by xinloiemnham on 2012-04-28
I got this error :
```
multicd.sh 7.0
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Fedora netboot installer
Hiren's BootCD (Not open source - do not distribute)
openSUSE GNOME Live CD
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Fedora netboot installer...

(file-roller:5986): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(file-roller:5986): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(file-roller:5986): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(file-roller:5986): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed

(file-roller:5986): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion `g_type_is_a (gtk_widget_path_get_object_type (path), pspec->owner_type)' failed
cp: cannot stat `/home/quanganh/Desktop/multidvd/temporary-mountpoints/fedora-boot/images': No such file or directory
```
can anyone help me ?
here are list of iso files I put in :
```
hirens.iso
ubuntu.iso
fedora-boot.iso
opensuse-gnome.iso
```

---

### Post by maybeway36 on 2012-04-29
To the last three posters: unfortunately I am unable to duplicate any of the issues you are having, so I won't be able to fix them.
I will look at some of those hard drive tools and see if I can add support for them.

---

### Post by qyot27 on 2012-05-03
Is there some way to support the alternate CD?  Using the latest git (as of 2012-05-03; revision count is 373):
```
$ ./multicd.sh -v
Made a link named ubuntu-alternate.iso pointing to ubuntu-12.04-alternate-i386.iso (version 12.04)
multicd.sh 7.0
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Ubuntu alternate installer
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Ubuntu alternate installer...
cp: cannot stat `/home/qyot27/multicd/temporary-mountpoints/ubuntu-alternate/ubuntu': No such file or directory
```
It also only detects the i386 version of the alternate CD; the amd64 iso isn't detected at all.

I'd like to be able to have all four (i386 and amd64 for both desktop and alternate) on the same disk.  The desktop ones work fine.

---

### Post by maybeway36 on 2012-05-19
ubuntu-12.04-alternate-i386.iso seems to work for me. I updated the script to support xubuntu alternate as well, so try again and see if you get the same error.
By the way, if you have more than one alternate ISO, it only uses one, because there's no way to have more than one on the same disc (without rebuilding the installer.)

---

### Post by qyot27 on 2012-05-20
I'm still getting the same error, even after the fixes.

```
$ ./multicd.sh
Made a link named ubuntu-alternate.iso pointing to ubuntu-12.04-alternate-i386.iso (version 12.04)
Made a link named i386.ubuntu.iso pointing to ubuntu-12.04-desktop-i386.iso (version 12.04)
Made a link named amd64.ubuntu.iso pointing to ubuntu-12.04-desktop-amd64.iso (version 12.04)
multicd.sh 7.0
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Ubuntu alternate installer
Ubuntu (64-bit) 12.04
Ubuntu (32-bit) 12.04
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Ubuntu alternate installer...
cp: cannot stat `/home/qyot27/MultiCD/temporary-mountpoints/ubuntu-alternate/ubuntu': No such file or directory
```

---

### Post by pdlethbridge on 2012-05-27
When you put several iso's on a dvd are they front to back like the music on an lp with a gap betwen the Songs or iso's

---

### Post by lkraemer on 2012-06-01
maybeway36:

I am trying to build a MultiCD, and I want FreeDOS (fdfullcd.iso) included.  I am using multicd-HEAD-604591e.tar.gz

I am getting this error:
> 
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Clonezilla 
FreeDOS
GParted Live
SliTaz
SystemRescueCd
Tiny Core Linux
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Clonezilla ...
Copying FreeDOS...
cp: cannot stat `/home/larry/Downloads/MultiCD/temporary-mountpoints/freedos/isolinux/fdboot.img': No such file or directory
larry@debian:~/Downloads/MultiCD$

The freedos.sh plugin appears to have an error:
```

mkdir "${WORK}"/boot/freedos
		cp -r "${MNT}"/freedos/freedos "${WORK}"/ #Core directory with the packages
		cp "${MNT}"/freedos/setup.bat "${WORK}"/setup.bat #FreeDOS setup
		cp "${MNT}"/freedos/isolinux**/data/**fdboot.img "${WORK}"/boot/freedos/fdboot.img #Initial DOS boot image

```
I added the /data/ to get the path to be where the image is located.

And it appears to build, but I haven't tested yet.  At least the error is gone.

My install of FreeDOS boots properly now!


lk

---

### Post by lkraemer on 2012-06-01
maybeway36,
I saw in a previous posting about the -b switch, which isn't included on
your website or in any documentation I can find.  

Are there other switches that aren't listed/documented?

Will you please update the switches:
> 
-c            : include an MD5 checksum file (md5sum.txt)
 -d            : drop to a shell prompt before building the ISO (debug)
 -m            : don't include Memtest86+
 -i            : offer options like ISOLINUX menu color or copying only certain Slax modules
                 (requires dialog)
 -o [filename] : lets you use another filename for the output instead of multicd.iso
 -t            : run the ISO in QEMU after it is built
 -v            : be more verbose
 -V            : print out the version number
 -w            : put a "press enter to continue" before exiting
 clean         : don't run the multicd.sh script at all - instead, get rid of the symlinks
                 and temporary version files that it makes automatically


lk

---

### Post by lkraemer on 2012-06-01
maybeway36,
I am trying to get Clonezilla (clonezilla-live-1.2.12-60-i686-pae.iso) included on my multicd.iso.

The script creates a Symbolic Link to the clonezilla.iso file, but nothing
is ever inserted in the main menu, even though it is being processed, because it
is listed on the screen.  Am I missing something?

Thanks.

lk

---

### Post by lkraemer on 2012-06-01
maybeway36,
I used the AntiX.sh to create a Mepis.sh for SimplyMEPIS-1.5G_11.0.00_32.iso

You probably want to go through it and clean it up properly,
but it boots Mepis 11.0 and works.

```

#!/bin/sh
set -e
. "${MCDDIR}"/functions.sh
#Mepis Linux plugin for multicd.sh
#version 6.9
#Copyright (c) 2010 Isaac Schemm
#
#Permission is hereby granted, free of charge, to any person obtaining a copy
#of this software and associated documentation files (the "Software"), to deal
#in the Software without restriction, including without limitation the rights
#to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
#copies of the Software, and to permit persons to whom the Software is
#furnished to do so, subject to the following conditions:
#
#The above copyright notice and this permission notice shall be included in
#all copies or substantial portions of the Software.
#
#THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
#AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
#OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
#THE SOFTWARE.
if [ $1 = scan ];then
	if [ -f mepis.iso ];then
		echo "Mepis"
	fi
elif [ $1 = copy ];then
	if [ -f mepis.iso ];then
		echo "Copying Mepis..."
		mcdmount mepis
		cp -r "${MNT}"/mepis/mepis "${WORK}"/ #Everything in Mepis but the kernel and initrd
		mkdir -p "${WORK}"/boot/mepis
		cp "${MNT}"/mepis/boot/vmlinuz "${WORK}"/boot/mepis/vmlinuz #Kernel
		cp "${MNT}"/mepis/boot/initrd.gz "${WORK}"/boot/mepis/initrd.gz #Initrd
		umcdmount mepis
	fi
elif [ $1 = writecfg ];then
if [ -f mepis.iso ];then
echo "label Mepis
menu label ^mepis
com32 menu.c32
append mepis.menu" >> "${WORK}"/boot/isolinux/isolinux.cfg
echo "DEFAULT menu.c32
TIMEOUT 0
PROMPT 0
menu title Mepis Options

label  Mepis-Default
menu label ^Mepis-Default
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init quiet nosplash vga=791 aufs  initrd=/boot/mepis/initrd.gz

label  Mepis-Lite-noNet
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init quiet nosplash vga=791 aufs mean lean initrd=/boot/mepis/initrd.gz

label  Mepis-Vesa
menu label Mepis-Vesa (display problem or virtualbox)
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init vga=normal quiet nosplash drvr=vesa aufs lean initrd=/boot/mepis/initrd.gz

label  Mepis-UltraLite-Vesa
menu label Mepis-UltraLite-Vesa (Fast boot)
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init vga=normal quiet nosplash drvr=vesa aufs lean Xtralean initrd=/boot/mepis/initrd.gz

label  Mepis-Failsafe
menu label Mepis-Failsafe (minimum options, small display)
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init quiet nosplash vga=normal nosound noapic noscsi nodma noapm nousb nopcmcia nofirewire noagp nomce nodhcp nodbus nocpufreq nobluetooth drvr=fbdev aufs res=800x600v initrd=/boot/mepis/initrd.gz

label  Mepis-60Hz
menu label Mepis-60Hz (force monitor to 58-62 Hz)
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init vga=791 quiet nosplash vsync=58-62 aufs initrd=/boot/mepis/initrd.gz

label  Mepis-75Hz
menu label Mepis-75Hz (force monitor to 73-77 Hz)
kernel /boot/mepis/vmlinuz
append SELINUX_INIT=NO init=/etc/init vga=791 quiet nosplash vsync=73-77 aufs initrd=/boot/mepis/initrd.gz

label back
menu label ^Back to main menu
com32 menu.c32
append isolinux.cfg
" > "${WORK}"/boot/isolinux/mepis.menu
fi
else
	echo "Usage: $0 {scan|copy|writecfg}"
	echo "Use only from within multicd.sh or a compatible script!"
	echo "Don't use this plugin script on its own!"
fi

```


Thanks.

lk

---

### Post by lkraemer on 2012-06-01
Maybeway36,
REF: Posting #268
> 
To the last three posters: unfortunately I am unable to duplicate any of the issues you are having, so I won't be able to fix them.
I will look at some of those hard drive tools and see if I can add support for them.


Have you had a chance to look at any of the Hard Drive Diags that boot from a Floppy Image yet?

Thanks.

lk

---

### Post by maybeway36 on 2012-06-06
> **qyot27 said:**
> I'm still getting the same error, even after the fixes.

```
$ ./multicd.sh
Made a link named ubuntu-alternate.iso pointing to ubuntu-12.04-alternate-i386.iso (version 12.04)
Made a link named i386.ubuntu.iso pointing to ubuntu-12.04-desktop-i386.iso (version 12.04)
Made a link named amd64.ubuntu.iso pointing to ubuntu-12.04-desktop-amd64.iso (version 12.04)
multicd.sh 7.0
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Ubuntu alternate installer
Ubuntu (64-bit) 12.04
Ubuntu (32-bit) 12.04
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying Ubuntu alternate installer...
cp: cannot stat `/home/qyot27/MultiCD/temporary-mountpoints/ubuntu-alternate/ubuntu': No such file or directory
```

I changed a line in ubuntu-alternate.sh. Try it now & see if it works.

lkraemer: I'll look into those things soon.

---

### Post by maybeway36 on 2012-06-06
> **lkraemer said:**
> maybeway36,
I saw in a previous posting about the -b switch, which isn't included on
your website or in any documentation I can find.  

Are there other switches that aren't listed/documented?

Will you please update the switches:


lk

I don't think there is a -b switch. Maybe it was a typo?
These are all the switches in multicd.sh:
```
		-c) shift;export MD5=true;;
		-d) shift;export DEBUG=true;;
		-i) shift;export INTERACTIVE=true;;
		-m) shift;export MEMTEST=false;;
		-o) shift;export OUTPUT="$1";shift;;
		-t) shift;export TESTISO=true;shift;;
		-v) shift;export VERBOSE=true;;
		-V) shift;echo $MCDVERSION;exit 0;; #quit program
		-w) shift;export WAIT=true;shift;;
```

> **lkraemer said:**
> Maybeway36,
REF: Posting #268


Have you had a chance to look at any of the Hard Drive Diags that boot from a Floppy Image yet?

Thanks.

lk

Could you give me links to download them?
For the Drive Fitness Test (dft32_v416_b00_install) the floppy version should work with MultiCD. You might have to rename the file so the extension is ".img", not ".IMG".

---

### Post by lkraemer on 2012-06-06
maybeway36,
Here is the information for the Drive Diagnostics.


[http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)

Hitachi Drive Fitness Test - Filename dft_416_b00.iso
[http://www.hitachigst.com/hdd/support/downloads/dft32_v416_b00_install.IMG](http://www.hitachigst.com/hdd/support/downloads/dft32_v416_b00_install.IMG)
[http://www.hitachigst.com/hdd/support/downloads/dft32_v416_b00.iso](http://www.hitachigst.com/hdd/support/downloads/dft32_v416_b00.iso)


Maxtor PowerMax Ver 4.23 - Filename PwrMx423En.iso
[http://www.tacktech.com/download.cfm?file=mirror/maxtor/PwrMxEn.exe](http://www.tacktech.com/download.cfm?file=mirror/maxtor/PwrMxEn.exe)
[http://www.tacktech.com/download.cfm?file=mirror/maxtor/PwrMx423En.iso](http://www.tacktech.com/download.cfm?file=mirror/maxtor/PwrMx423En.iso)


Seagate SeaTools for DOS Ver 2.23 - Filename SeaToolsDOS223ALL.iso
[http://www.seagate.com/support/seatools/seatoold_reg.html](http://www.seagate.com/support/seatools/seatoold_reg.html)
[http://www.seagate.com/support/seatools/seatoold_reg.html](http://www.seagate.com/support/seatools/seatoold_reg.html)


Western Digital Data Lifeguard Diagnostic v5.04f for DOS
- Filename Diag504fCD.iso
[http://support.wdc.com/download/dlg/dlgsetup11_0_dos.zip](http://support.wdc.com/download/dlg/dlgsetup11_0_dos.zip)
[http://support.wdc.com/product/download.asp?groupid=502&sid=2&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=2&lang=en)
[http://support.wdc.com/product/download.asp?groupid=504&sid=30&lang=en](http://support.wdc.com/product/download.asp?groupid=504&sid=30&lang=en)


lk

---

### Post by qyot27 on 2012-06-06
> **maybeway36 said:**
> I changed a line in ubuntu-alternate.sh. Try it now & see if it works.
It seems to have fixed it.  Thanks.

---

### Post by def_mornahan on 2012-06-19
Is it possible to put more than one mini.iso on a CD?  I have aging computers of both amd64 and i386 types that I'd like to put a minimal install on, and I don't think they'll boot from sticks.  I've tried merging mini.iso files with your script and I get:

cp: cannot stat `/home/paulus/applications/MultiCD/temporary-mountpoints/386mini.ubuntu/casper': No such file or directory

I'm happy to peer under the hood and twiddle with the script, but after reading the last 10-15 pages of this thread, I wanted to ask if it's even possible first.

---

### Post by YannBuntu on 2012-06-19
Hello
Just discovered this tool. Is it similar to MultiSystem? (see my signature below)

---

### Post by lkraemer on 2012-06-22
Maybeway36,
I updated to the latest version of MultiCD and tried my Spinrite and Dos Ver 3.3 & 6.22 images again.
The current version appears to work good with Spinrite Versions 5 & 6.  I did find a small problem with
my Spinrite 5 Image and fixed it.  So, in reference to Posting #266, my Spinrite Issues are fixed.

Also I see you included the Mepis Plugin, but you didn't update your Web Page for Supported Distro's
stating that it is also available.

THANKS!

lk

---

### Post by maybeway36 on 2012-07-04
> **def_mornahan said:**
> Is it possible to put more than one mini.iso on a CD?  I have aging computers of both amd64 and i386 types that I'd like to put a minimal install on, and I don't think they'll boot from sticks.  I've tried merging mini.iso files with your script and I get:

cp: cannot stat `/home/paulus/applications/MultiCD/temporary-mountpoints/386mini.ubuntu/casper': No such file or directory

I'm happy to peer under the hood and twiddle with the script, but after reading the last 10-15 pages of this thread, I wanted to ask if it's even possible first.

The script doesn't have a way to use more than one mini.iso (unless it's one for Ubuntu and one for Debian - those are separate.) You can, however, include [NetbootCD](http://netbootcd.tuxfamily.org), or just copy the ubuntu-mini.sh script and make some changes so the files don't overwrite each other.

> **YannBuntu said:**
> Hello
Just discovered this tool. Is it similar to MultiSystem? (see my signature below)

It has a similar concept - a customizable group of distributions on one boot device. So do some other projects (I have links to some of those on the bottom of the MultiCD home page at [http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)).

---

### Post by sinj on 2012-11-05
Hi,

First, great tool!

Just 2 questions.

1. Does ubuntu-12.04-server.iso supported, because DVD iso-s not include this image if i create with other iso-s?

2. If i generate iso DVD with ubuntu 12.04 and ubuntu 12.10 boot menus created without version number like this:
Ubuntu (32-bit)
Ubuntu (32-bit)

although version numbers are visible when creating the iso like this:
Ubuntu (32-bit) 12.10
Ubuntu (32-bit) 12.04

Sorry if already answered...

---

### Post by maybeway36 on 2012-11-13
> **sinj said:**
> 1. Does ubuntu-12.04-server.iso supported, because DVD iso-s not include this image if i create with other iso-s?

I've never tested Ubuntu Server until just now. But it looks like if you name the ISO "ubuntu-alternate.iso", it will work!
(I'll also edit ubuntu-alternate.sh so it can find the regular ISO filename, just like with ubuntu-alternate-12.04-i386.iso, etc.)

> **sinj said:**
> 2. If i generate iso DVD with ubuntu 12.04 and ubuntu 12.10 boot menus created without version number like this:
Ubuntu (32-bit)
Ubuntu (32-bit)

although version numbers are visible when creating the iso like this:
Ubuntu (32-bit) 12.10
Ubuntu (32-bit) 12.04

Sorry if already answered...

That's actually a bug! I'll fix it in the next Git revision.

---

### Post by sinj on 2012-11-28
> **maybeway36 said:**
> I've never tested Ubuntu Server until just now. But it looks like if you name the ISO "ubuntu-alternate.iso", it will work!


OK, but there are lots of "alternate" ubuntu versions. There is lubuntu for example what I also included on my list. (lubuntu-12.04-alternate-i386.iso) I noticed if there is more than one iso -including the "alternate" word- than the multicd.iso wont contain any of it.

I tried to create a multicd.iso from
linux mint
lubuntu
ubuntu-server (renamed ubuntu-alternate) 
ubuntu dekstop

---

### Post by maybeway36 on 2012-12-04
The "alternate" ISO images are the ones that use the text-based installer. ("server" images use that installer as well.) You can only have one of these Ubuntu text-based installers on a single disc, because the files conflict with each other, and I haven't been able to find a way to move them and still make it work.
With the "desktop" ISOS (the live CD installers), it's possible to move the files so they don't conflict; you can have as many of these as you like. I suggest you download the Lubuntu desktop CD (lubuntu-12.*-desktop-i386.iso) and use that instead.

P.S. MultiCD now detects "ubuntu-*-server-i386.iso" and "ubuntu-*-server-amd64.iso", and redirects them to ubuntu-alternate automatically.

---

### Post by sinj on 2012-12-05
> **maybeway36 said:**
> 
P.S. MultiCD now detects "ubuntu-*-server-i386.iso" and "ubuntu-*-server-amd64.iso", and redirects them to ubuntu-alternate automatically.

Thank You, I appreciate your work!

---

### Post by emalyse on 2012-12-11
Hi all - I'm experiencing a syslinux problem after the script downloads syslinux 4.06

Unpacking and copying files...
cp: cannot stat `/tmp/syslinux-*/com32/modules/chain.c32': No such file or directory

If anyone can point me in the right direction It'd be much appreciated.
Best wishes to all.

---

### Post by maybeway36 on 2012-12-17
Whoops! That's a bug in my script - I didn't update the path for 4.06. ((It only affects users who don't have "syslinux.tar.gz" already cached in multicd's folder.) It should be fixed now.

---

### Post by Brizvegan on 2013-01-01
> **emalyse said:**
> Hi all - I'm experiencing a syslinux problem after the script downloads syslinux 4.06

Unpacking and copying files...
cp: cannot stat `/tmp/syslinux-*/com32/modules/chain.c32': No such file or directory


Hi,
I'm having the same problem  ... getting the exact same error.

Edit:
Tried it several times now - with the same result.

Once I tried directly downloading syslinux 4.06 and extracting it to the multicd folder - same result.
After the last failure, I navigated to /tmp/syslinux-*/com32/modules - it is there, but the file **chain.c32** is not there.
I hope this information can help you to provide us with a solution  :)

Brizvegan

---

### Post by emalyse on 2013-01-05
The latest update solved my problem. Many thanks. Had to remember to delete a previous syslinux in /tmp though or I'd get the same problem (in case anyone else is still encountering problems).

---

### Post by Brizvegan on 2013-01-10
[QUOTE=emalyse]The latest update solved my problem. Many thanks. Had to remember to delete a previous syslinux in /tmp though or I'd get the same problem (in case anyone else is still encountering problems). [/QUOTE]

Unfortunately, the latest update with path to syslinux 4.06 hasn't solved my problem.
Also deleted syslinux files in /tmp without success.
Tried again, and got the same error message.

Here is the terminal output of last attempt - maybe someone can spot what is going wrong, or if there is something I'm doing wrong:

d@Mint-13-Cinnamon-laptop ~/multicd/IsaacSchemm-MultiCD-11e1710 $ chmod +x multicd*.sh
d@Mint-13-Cinnamon-laptop ~/multicd/IsaacSchemm-MultiCD-11e1710 $ ./multicd*.sh
Made a link named mint.linuxmint.iso pointing to linuxmint-14-cinnamon-dvd-32bit.iso (version 14-cinnamon-dvd-32bit)
Made a link named 1_mint.linuxmint.iso pointing to linuxmint-14-kde-dvd-32bit.iso (version 14-kde-dvd-32bit)
Made a link named 2_mint.linuxmint.iso pointing to linuxmint-14-mate-dvd-32bit.iso (version 14-mate-dvd-32bit)
Made a link named 3_mint.linuxmint.iso pointing to linuxmint-14-xfce-dvd-32bit.iso (version 14-xfce-dvd-32bit)
multicd.sh 20121217
Extracting ISO images with file-roller; will build multicd.iso; UID 1000.

Linux Mint 14-kde-dvd-32bit
Linux Mint 14-mate-dvd-32bit
Linux Mint 14-xfce-dvd-32bit
Linux Mint 14-cinnamon-dvd-32bit
Memtest86+

Continuing in 2 seconds - press Ctrl+C to cancel
Copying files for each plugin...
Copying Linux Mint...
Copying Linux Mint...
Copying Linux Mint...
Copying Linux Mint...
Downloading SYSLINUX...
--2013-01-11 09:24:14--  [https://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.06.tar.gz](https://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.06.tar.gz)
Resolving [www.kernel.org]("http://www.kernel.org") ([www.kernel.org]("http://www.kernel.org"))... 149.20.4.69, 149.20.20.133
Connecting to [www.kernel.org]("http://www.kernel.org") ([www.kernel.org)|149.20.4.69|:443]("http://www.kernel.org)|149.20.4.69|:443")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6651601 (6.3M) [application/x-gzip]
Saving to: 'syslinux.tar.gz'

100%[============================================================================>] 6,651,601    325K/s   in 22s    

2013-01-11 09:24:41 (299 KB/s) - 'syslinux.tar.gz' saved [6651601/6651601]

Unpacking and copying files...
cp: cannot stat `/tmp/syslinux-*/com32/modules/chain.c32': No such file or directory
d@Mint-13-Cinnamon-laptop ~/multicd/IsaacSchemm-MultiCD-11e1710 $

Any ideas?

---

### Post by Filippop78 on 2013-05-22
Hi, how can I resolve the same problem of Brizvegan?
At the moment I would be fine also manually enter the necessary files in their folders but I don't know what and where to get them.
Thanks

---

### Post by iomari on 2013-08-20
Greetings,
can I modify the win7recovery script to include win8recovery and vistarecovery?

---

### Post by beykex on 2013-09-02
Hello there,
I'm experiencing a small problem with Zorin OS images; basically the script doesn't detect them. I'm trying to burn Zorin OS 7, the latest version of the distro. Why could this be happening?

Thanks for the support and good job with the script, i'll save many DVD's with it.

---

### Post by padmahas on 2014-07-10
Hey maybeway36, first I'd like to thank you for this script. But I have some problem in the installation phase of Ubuntu from multicd.iso as shown here. I successfully created single cd of 4 Ubuntu versions. Ubuntu 12.10, 13.04,14.04(32 bit and 64 bit). Before burning it to dvd I wanted to check whether it is working properly or not so tried installing inside virtualBox. Here it is just blinking but not proceding to installation as shown [here]("http://youtu.be/VXfOML7IHmI").

---

### Post by oldfred on 2014-07-10
@padmahas
I do not use multicd.sh, but 12.10 and 13.04 are not now supported. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Chart does not make it clear but with 10.04 only server version is still supported.

Also you may need boot parameters. What video card do you have. I have to modify my scripts with nomodeset for my nVidia to work. But I just get monitor turning off and system still running if I do not use nomodeset. Other video systems may need other boot parameters.

---

### Post by padmahas on 2014-07-12
Hello @oldfred, I think video card means graphic card you are refering to. But I don't have one. I have inbuilt graphics of 1 GB and its Intel motherboard with i3 processor. Since 12.10 and 13.04 are no longer supported, I'll try with 14.04(32 and 64 bit).

---

### Post by padmahas on 2014-07-15
What is happening here ?
```

root@padmahasa-desktop:/media/padmahasa/Windows1/Multicd# chmod +x multicd.sh
root@padmahasa-desktop:/media/padmahasa/Windows1/Multicd# sudo ./multicd.sh
sudo: ./multicd.sh: command not found
root@padmahasa-desktop:/media/padmahasa/Windows1/Multicd# ./multicd.sh
bash: ./multicd.sh: Permission denied
```

A weak back I could run the script without any problem..

---

