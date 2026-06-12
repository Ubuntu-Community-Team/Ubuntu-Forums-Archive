---
title: "Howto : GfxBoot ( Grub like suse )"
date: 2006-07-04
forum: Tutorials
---

### Post by PingunZ on 2006-07-04
Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one ;) 
Ok, let's start

Download the [grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb")
And the [message.suse ]("http://quasarfreak.googlepages.com/message.suse")

First remove your old grub
```
sudo apt-get remove grub
```

Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```

then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded 
```

Then edit your menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced 
```


Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

-- Howto make you own theme --


```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```

Reboot and enjoy ;)
Thanks to Quasar_freak and kno

here are some themes posted in this thread ;) ( ty :KS  )

Light Green generic theme [message.gobo] | [Link](http://ubuntuforums.org/showpost.php?p=1214274&postcount=12) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288)
Dark Brown (Dapper look) generic theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544)
Medium blue kubuntu theme [message.kubuntu] | [Link](http://ubuntuforums.org/showpost.php?p=1234300&postcount=54) | [Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)
Dark grey ubuntu theme [message.ubugrey] | [Link](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717)
Medium brown ubuntu theme [message.ububrown] | [Link](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657)
Light orange ubuntu theme [message.ubu] | [Link](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852)
Red ubuntu theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852)
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746)
White / Grey Snowish generic theme [message.snow] | [Link](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506)
Linspire-style blue kubuntu theme [message.kubu] | [Link](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390)
Old- Grub style dark blue and light blue [message.kubu] | [Link](http://mitglied.lycos.de/atoth/ubuntuusers/message.napo) | [Screenshot ]("http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo.png")
Light blue / grey Xubuntu theme [message.xubu] | [Link](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350)[/QUOTE]


Grtz PingunZ

---

### Post by bohboh on 2006-07-04
[QUOTE=PingunZ]
Then install it
```
grub-install /dev/X
```

Then do : ```
sudo fdisk -l
```
and if it talks about hda replace X with hda, if it talks about sda ...
[/QUOTE]

Sorry, first thicko question...

Do you mean that we should do "sudo fdisk -l" then with the result of that command do "grub-install /dev/hda" or "grub-install /dev/sda"

If so then your guide suggests to do "grub-install /dev/X" first. Being a newcomer i really down want to mess up my grub installation and so want to be sure. :D

---

### Post by PingunZ on 2006-07-04
yes, if fdisk tells you about sda you should replace the X with sda 
so /dev/sda
same thing for hda
fdisk has nothing to do with grub, its just for you to know if you got sda or hda ;)

Grtz PingunZ

---

### Post by PingunZ on 2006-07-04
Any comments ?

---

### Post by kno on 2006-07-04
Hello,

The command grub-install doesn't work for me, instead I do :
```
grub
> root (hd0,0)
> setup (hd0)
```
Now, it runs very well.

Thanks for this howto.

PS: I use the [theme GoboGrub]("http://dev.gentoo.org/~spyderous/splash/gobo/").

---

### Post by PingunZ on 2006-07-04
Ty kno, I changed it ;)

Grtz PingunZ

---

### Post by bohboh on 2006-07-04
[QUOTE=PingunZ]Ty kno, I changed it ;)

Grtz PingunZ[/QUOTE]

Here is my fdisk -l output:

```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       24791   147926520    f  W95 Ext'd (LBA)
/dev/sda5            6376       12748    51191091    b  W95 FAT32
/dev/sda6           12749       24791    96735366    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9351    75111876   83  Linux
/dev/hdc2            9352        9729     3036285    f  W95 Ext'd (LBA)
/dev/hdc5            9352        9729     3036253+  82  Linux swap / Solaris


```

What is my boot disk?

I tried root (sda1,0) and got an parse number error.

---

### Post by kno on 2006-07-04
[QUOTE=bohboh]Here is my fdisk -l output:

```

...

```

What is my boot disk?

I tried root (sda1,0) and got an parse number error.[/QUOTE]

You should try :
```

sudo grub
grub> find /boot/grub/stage1
 (hd[COLOR="#ff0000"]x[/COLOR],[COLOR="#ff0000"]y[/COLOR])
grub> root (hd[COLOR="#ff0000"]x[/COLOR],[COLOR="#ff0000"]y[/COLOR])
grub> setup (hd[COLOR="#ff0000"]x[/COLOR])
```

---

### Post by d3x7r0 on 2006-07-04
hum... I tried the how to but my grub still looks exactly the same as it did before... did I do something wrong? :-?

---

### Post by bohboh on 2006-07-04
Cool, thanks Kno, that worked. Kind of. Turned out that i needed to run grub as root (sudo).

Problem is that i followed the guide and rebooted, still the old boot menu.

Erm, I:

1. Downloaded the files
2. Uninstalled grub
3. Installed debs
4. Copied file to /boot/grub
5. Added line to menu.lst (added it at the very top, i.e. line 1)
6. Entered the Grub commands
7. Rebooted

Did i miss a step?

---

### Post by tlaloczint on 2006-07-04
Then edit your menu.lst
```
sudo gedit /boot/grub/menu.lst
```
and make it use gfxboot
```
gfxmenu /boot/grub/message.suse
```

ok how do I do that? 

tlaloc@aztlan:~$ gfxmenu /boot/grub/message.suse
bash: gfxmenu: command not found
tlaloc@aztlan:~$

do I missing something here?

---

### Post by kno on 2006-07-04
If it could help someone, herewith my configuration :
[http://rapidsharing.com/download.php?id=87DFE506](http://rapidsharing.com/download.php?id=87DFE506)

---

### Post by scenestar on 2006-07-04
Just copy paste line for line of the quote in a terminal 
It should work for everyone.

> wget [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

wget [http://quasarfreak.googlepages.com/message.suse](http://quasarfreak.googlepages.com/message.suse)

sudo apt-get remove grub

sudo dpkg -i grub-gfxboot_0.97-5_i386.deb

sudo cp message.suse /boot/grub/

sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst

grub-install /dev/hda 


---

### Post by bohboh on 2006-07-04
Tried your message.gobo file, still no joy.

Our files are the same, has the gfxmenu line at the top.

Any ideas?

---

### Post by scenestar on 2006-07-04
[QUOTE=bohboh]Tried your message.gobo file, still no joy.

Our files are the same, has the gfxmenu line at the top.

Any ideas?[/QUOTE]

Did you try with the theme provided in this howto?

If you did EXACTLY as was explained the most logical explanation would be that your theme is corrupted.

---

### Post by bohboh on 2006-07-04
Downloaded both files again and went through the entire guide EXACTLY. 

Still the same. :-?

---

### Post by bohboh on 2006-07-04
One thing, doing

```
sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
```

gave me a permission denied error.

but i can edit it using gedit ok.

---

### Post by scenestar on 2006-07-04
[QUOTE=bohboh]One thing, doing

```
sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
```

gave me a permission denied error.
[/QUOTE]
Ack, just screw sudo
su to root like a real man.

**edit to bohboh**

I found your problem. Instead of :
> grub-install /dev/hda 
try
> grub-install /dev/hdc

---

### Post by bohboh on 2006-07-05
Many thanks, that sorted it. :D

For future reference, Can you explain how, by looking at my fdisk output, you knew it was hdc?

So all i need to do to change themes is to place the message.blah file in /boot/grub and to change the line in menu.lst?

Again, Thanks

---

### Post by kno on 2006-07-05
[QUOTE=bohboh]Many thanks, that sorted it. :D

For future reference, Can you explain how, by looking at my fdisk output, you knew it was hdc?
[/QUOTE]

[QUOTE=bohboh]
   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/hdc1   *           1        9351    75111876   83  Linux[/COLOR]
/dev/hdc2            9352        9729     3036285    f  W95 Ext'd (LBA)
/dev/hdc5            9352        9729     3036253+  82  Linux swap / Solaris
[/QUOTE]
It's hdc because grub is setup on /dev/hdc1 (your 3rd hdd) with Ubuntu
> 
So all i need to do to change themes is to place the message.blah file in /boot/grub and to change the line in menu.lst?

Yes, but I don't find many message.xyz on the net...

---

### Post by bohboh on 2006-07-05
[QUOTE=kno]Yes, but I don't find many message.xyz on the net...[/QUOTE]

Thanks

That was going to be my next question. :D I have had a quick look and cant find any.

Oh well, suppose i could make my own. Do you know of any guides for making your own?

---

### Post by kno on 2006-07-05
[QUOTE=bohboh]Thanks

That was going to be my next question. :D I have had a quick look and cant find any.

Oh well, suppose i could make my own. Do you know of any guides for making your own?[/QUOTE]

sudo apt-get install gfxboot gfxboot-theme-ubuntu

then you'll find  help and examples (to compile ;) ) in :
/usr/share/doc/gfxboot/
/usr/share/gfxboot/themes/

A tutorial :
[http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html]("http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html")

---

### Post by frodon on 2006-07-05
any screenshot of the result ?

---

### Post by bohboh on 2006-07-05
How do i take a screenshot of the boot menu?

---

### Post by fantan on 2006-07-05
Hi,

I did all steps by this how-to but after restart I get an error message like this:

"...I cannot find any graphic file >>message.suse<<..." and I can to go toward by pressing any key, and then I get the ordinary menu.lst to chose a system to boot.

Of course the message.suse graphic file is in the directory /boot/grub and
I ran the command grub-install hd0 without any error message.
 
What to do then?

fantan

---

### Post by kno on 2006-07-05
[QUOTE=bohboh]How do i take a screenshot of the boot menu?[/QUOTE]
eg by using qemu

---

### Post by fantan on 2006-07-05
Hi again,

The error message I get exactly is as follows:

The graphics file message.suse (or message.gobo) is missing, press any key to continue.
By pressing any key, I get the list of my systems according to my menu.lst and I can boot one of the systems.

Why the grub-glx doesn't find the message.suse or the message.gobo graphics file?
Again, these files are in the /boot/grub directory!!! 

What can I do to get the proper screen?

fantan

---

### Post by kno on 2006-07-05
GoboGrubTheme :
[attach]12251[/attach]

SuseTheme :
[ATTACH]12252[/ATTACH]

---

### Post by fantan on 2006-07-05
Hi again, 

Thanks for the screenshots, but I know them very well, because in the past I used SuSE.
My problem is, that I can't get this bootscreen on my computer, although I did all steps exactly as these are written in this how-to.
My grub doesn't find the graphics file message.suse (or message.gobo) in the directory /boot/grub, but both of them are there!!!

What is the problem in my system?

---

### Post by fantan on 2006-07-05
Hi gentlemen,

I figured out what was the problem with my system!
On my HDD I have several partitions and for the boot I have a separate partition, hda1.
This partition is mounted to the /boot directory of the Dapper system.
On this partition there isn't /boot directory, just /grub.
If in the menu.lst file I change the first line from 
"gfxmenu /boot/grub/message.gobo" to "gfxmenu /grub/message.gobo" then grub finds the graphics file message.gobo.
That's all, everithing is fine!
But, there isn't any animation on this screen!!! Although in the SuSE system there is an animation around the Earth picture.

What to do with this?

fantan

---

### Post by bohboh on 2006-07-05
Ok, i have searched and i am going to have to ask. :D

How do you take a screenshot using qemu? My ideas was to create a vmware image, or is that silly? :p

---

### Post by kno on 2006-07-05
[QUOTE=fantan]
...
That's all, everithing is fine!
But, there isn't any animation on this screen!!! Although in the SuSE system there is an animation around the Earth picture.

What to do with this?
[/QUOTE]
Timeout must be greater than 0 in /boot/grub/menu.lst.

---

### Post by kno on 2006-07-05
[QUOTE=bohboh]Ok, i have searched and i am going to have to ask. :D

How do you take a screenshot using qemu? My ideas was to create a vmware image, or is that silly? :p[/QUOTE]
I launch qemu with a grub boot floppy and then I use gnome-sreenshot (Alt+Print Screen).

---

### Post by rejser on 2006-07-05
have been using gfxboot a couple of days now and one things bug me, no mather wich theme I choose i get a popup saying "You have a cool system, but you are about to install a 32-bit applikation on a 64-bit system"
I have amd 64, though ubuntu 32 installed.. anyone know how to make it go away?

---

### Post by bohboh on 2006-07-05
I have managed to create my grub boot floppy using this guide (included menu.lst and device.map with my message file):

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

And then do qemu /dev/fd0

It eventually drops me into the grub console.

How do i get it to display the boot menu?

---

### Post by kno on 2006-07-06
[QUOTE=bohboh]I have managed to create my grub boot floppy using this guide (included menu.lst and device.map with my message file):

[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

And then do qemu /dev/fd0

It eventually drops me into the grub console.

How do i get it to display the boot menu?[/QUOTE]
```
...
cp menu.lst message.suse /media/floppy/boot/grub
umount /media/floppy
qemu -fda /dev/fd0 -boot a
```

---

### Post by kno on 2006-07-06
[QUOTE=rejser]have been using gfxboot a couple of days now and one things bug me, no mather wich theme I choose i get a popup saying "You have a cool system, but you are about to install a 32-bit applikation on a 64-bit system"
I have amd 64, though ubuntu 32 installed.. anyone know how to make it go away?[/QUOTE]
Can you try this :
[ATTACH]12290[/ATTACH]

---

### Post by rejser on 2006-07-06
[QUOTE=kno]Can you try this :
[ATTACH]12290[/ATTACH][/QUOTE]

worked like a charm, mind sharing the source?
did you exclude dia_bits from boot.config? or dia_install?

---

### Post by kno on 2006-07-06
[QUOTE=rejser]worked like a charm, mind sharing the source?
did you exclude dia_bits from boot.config? or dia_install?[/QUOTE]

I comment some lines of common.inc, that's all.
[ATTACH]12295[/ATTACH]

---

### Post by tlaloczint on 2006-07-07
ok I got this what I am doing wrong
 any help please?


root@aztlan:/home/tlaloc# sudo fdisk -l

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1            6203       29053   183550657+   5  Extended
/dev/hdd2   *           1        6202    49817533+  83  Linux
/dev/hdd5            6469       29053   181405949    7  HPFS/NTFS
/dev/hdd6            6203        6468     2136582   82  Linux swap / Solaris

Partition table entries are not in disk order
root@aztlan:/home/tlaloc# grub-install /dev/hdc1
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hdc
(hd1)   /dev/hdd
root@aztlan:/home/tlaloc#

---

### Post by scenestar on 2006-07-07
> ok I got this what I am doing wrong
any help please?


How about you tell us what the hell you were doing in the first place.

---

### Post by frodon on 2006-07-07
please keep civil, this thread has a good spirit

---

### Post by bohboh on 2006-07-07
I got that error also, but like it says. You can ignore it, so i did and it still worked. 

Is it not working for you?

---

### Post by hypnoticstate on 2006-07-07
How about us dual booters on Sata,

My partitions are labelled Sda, Ubuntu root is on
SDA4, XP is on SDA1, suggestions ? or leave well alone.

---

### Post by tlaloczint on 2006-07-07
> **scenestar said:**
> Just copy paste line for line of the quote in a terminal 
It should work for everyone.

this is what I did but nevermind it mess up my grub and I could not boot xp or ubuntu after 5 hours of tring to fix it I gave up so I did a clean install
sorry if I bother asking newbie question not in this tread anymore

---

### Post by art on 2006-07-07
You need to paste the line 
gfxmenu /boot/grub/message
in the menu.lst, somewhere in the beginning, and also do ```
sudo grub
```
and then type root (hd0,0) or whatever
Also, does anyone know how to compile the Ubuntu theme for gfxboot?

---

### Post by gruvsyco on 2006-07-08
> **scenestar said:**
> Just copy paste line for line of the quote in a terminal 
It should work for everyone.
I did this and now when I boot, all I get is a grub cli.

I was able to boot from the Live CD and figure out how to get my Linux partition up but now, I have no real grub config to speak of, other than command line.

---

### Post by nir78 on 2006-07-08
I think it will be great if you'll add a warning asking to save the menu.lst before beginning so things like that: [http://www.ubuntuforums.org/showthread.php?p=1229960]("http://www.ubuntuforums.org/showthread.php?p=1229960")
 will not happen...

Nir

---

### Post by nir78 on 2006-07-08
> **gruvsyco said:**
> I did this and now when I boot, all I get is a grub cli.

I was able to boot from the Live CD and figure out how to get my Linux partition up but now, I have no real grub config to speak of, other than command line.

Is this what happen to you ? [http://www.ubuntuforums.org/showthread.php?p=1229960]("http://www.ubuntuforums.org/showthread.php?p=1229960")

Nir

---

### Post by nickless on 2006-07-08
screenshots? errr...  fotos? :D

---

### Post by gruvsyco on 2006-07-09
> **nir78 said:**
> Is this what happen to you ? [http://www.ubuntuforums.org/showthread.php?p=1229960]("http://www.ubuntuforums.org/showthread.php?p=1229960")

Nir

Yup.  It took me a little research to recover but, it's back and I have a little better understanding of grub.

---

### Post by avender on 2006-07-09
> **kno said:**
> Hello,

The command grub-install doesn't work for me, instead I do :
```
grub
> root (hd0,0)
> setup (hd0)
```
Now, it runs very well.

Thanks for this howto.

PS: I use the [theme GoboGrub]("http://dev.gentoo.org/~spyderous/splash/gobo/").
When I open [http://dev.gentoo.org/~spyderous/splash/gobo/](http://dev.gentoo.org/~spyderous/splash/gobo/)

I'm getting 404 Not found error... :(

---

### Post by mmmichael on 2006-07-09
I know there's a way to compile gfxboot message files, and this aint it.
I borrowed from [http://ubuntuforums.org/showpost.php?p=1049234&postcount=15]("http://ubuntuforums.org/showpost.php?p=1049234&postcount=15")
 and did some editing. I'm sure others can do better but this works for me. If you want you can copy this [ATTACH]12475[/ATTACH] , extract it and sudo cp 
into /boot/grub directory and edit menu.lst accordingly. Just please back up menu.lst first.

---

### Post by sebbe1991 on 2006-07-09
I made a Kubuntu gfxboot :)

[Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)

[ATTACH]12476[/ATTACH]

---

### Post by mmmichael on 2006-07-11
Here's a screenshot taken under qemu

[IMG]http://ubuntuforums.org/images/attach/png.gif[/IMG]

file: [ATTACH]12550[/ATTACH]

---

### Post by adam.tropics on 2006-07-11
> **mmmichael said:**
> Here's a screenshot taken under qemu

[IMG]http://ubuntuforums.org/images/attach/png.gif[/IMG]

file: [ATTACH]12550[/ATTACH]


Nice job, works great

---

### Post by n00b@linux on 2006-07-11
> **mmmichael said:**
> file: [ATTACH]12550[/ATTACH]

Very nice!  I would like to have a go at making my own, but do not know how.  Can you please point me in the direction of how I can do it?  Is it hard to do?

---

### Post by sharperguy on 2006-07-11
> sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lstuhh shouldnt it be >> if you want to append, rather than > which would just overwrite the whole file?

---

### Post by Wipster on 2006-07-11
how do I use qemu to boot, cause I cant seem to work it out from the documentation, cheres.

---

### Post by mmmichael on 2006-07-11
> **n00b@linux said:**
> Very nice!  I would like to have a go at making my own, but do not know how.  Can you please point me in the direction of how I can do it?  Is it hard to do?

I followed the steps here [http://ubuntuforums.org/showpost.php?p=1049234&postcount=15]("http://ubuntuforums.org/showpost.php?p=1049234&postcount=15")
and just changed some of the images from the suse message. 
There is an ubuntu package -see [http://ubuntuforums.org/showpost.php?p=1215764&postcount=22](http://ubuntuforums.org/showpost.php?p=1215764&postcount=22)
but I don't know how to use it.

---

### Post by Footissimo on 2006-07-13
Made a mod of the SuSE GFXBoot theme.  Basically its a mash up of [this SVG icon](http://www.gnome-look.org/content/show.php?content=42245) by Sairitupac Vasquez and [this wallpaper](http://www.gnome-look.org/content/show.php?content=41588) by Paul Beyens.

I know nothing about QEMU, EMU or any flightless birds so I just took a screenie with me mobile.  If some kind person fancies running it through a virtual PC thingy and doing a screenie then that would be much appreciated. (thanks Kno)  There are two problems with it:

1) There is a slight artifact around the ubuntu icon - I've spent hours brushing to minimise JPG artifacts, but there's only so much I can do..it should be barely noticeable now.  Its due to the complexity of the background - if people like this then I'll do another on a plainer background and get the logo 100%

2) The original SuSE theme screws up a little if you scroll down the kernel / OS options - seems to be because that panel needs to be shoved to the left a bit or made into 1024x768 rather than 800x600.  Mine does the same...it doesn't effect functionality or anything, but if I do another, then I'll correct it (it was too late by the time I noticed it on this one).

Installing:

After doing all the GFXBoot palaver, just unzip the theme and copy it to /boot/grub/ then add ```
gfxmenu /boot/grub/message.ubugrey
``` to the top of the /boot/grub/menu.lst file.  Presumably you should remove any other themes you have there (such as message.suse)

---

### Post by mech7 on 2006-07-13
any screenshots ?

---

### Post by Footissimo on 2006-07-13
Another theme, this time based on [this wallpaper](http://www.gnome-look.org/content/show.php?content=32429).  Again, decompress and stick in /boot/grub then change the first line of /boot/grub/menu.lst to ```
gfxmenu /boot/grub/message.ububrown
``` and reboot.

Again, if someone could do a virtual session for the screenie :) (thanks Kno)

---

### Post by Malac on 2006-07-14
Here's my attempt. \\:D/

---

### Post by nimes on 2006-07-17
new gfxboot theme.

---

### Post by kno on 2006-07-17
[#61]("http://ubuntuforums.org/showpost.php?p=1251236&postcount=61")
[ATTACH]12872[/ATTACH]

[#63]("http://ubuntuforums.org/showpost.php?p=1252317&postcount=63")
[ATTACH]12871[/ATTACH]

[#64]("http://ubuntuforums.org/showpost.php?p=1254642&postcount=64")
[ATTACH]12873[/ATTACH]

[#65]("http://ubuntuforums.org/showpost.php?p=1265601&postcount=65")
[ATTACH]12870[/ATTACH]

---

### Post by Footissimo on 2006-07-17
Thank you Kno :)

*looks at QEMU*

---

### Post by nimes on 2006-07-17
thanks Kno

---

### Post by msak007 on 2006-07-17
[LEFT]Thanks for this how-to, it took less than 5 minutes to get everything installed and configured. This one of those "nice to have" features that I missed after switching back from SuSE and previously asked about something like it in the forums, but nobody knew how to do it. It just makes the overall look of the OS much nicer and more integrated. Now I just have to learn how to make my own gfxboot screen. For now I'm using the Kubuntu one that sebbe1991 made and it looks really nice. Thanks again![/LEFT]

---

### Post by BuffaloX on 2006-07-18
With my inferior abilities, I managed to mess my menu.lst :rolleyes:
Got it fixed, and then read the guide more careful...

This is cool, thanx for the howto. :p

---

### Post by Footissimo on 2006-07-18
Another GFXboot theme - this time to go with the blue usplash theme [here](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash) by SilentCacophony.  It's a very basic black background with the glowy logo and lettering from the usplash image.  If anyone likes it, I can do the other colours.

---

### Post by Sandsound on 2006-07-19
This is SO cool :cool: 

Thanks for a great HowTo

---

### Post by Jolly Roger on 2006-07-20
I have been trying to get this tutorial to work for me for a while now. I've done and redone each step of the tutorial many times. The only thing I think that I may be doing wrong is putting the line "gfxmenu /boot/grub/message.blusplash" in the wrong place in my menu.lst file. Here's my file so hopefully someone can help me out:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

gfxmenu /boot/grub/message.blusplash

timeout 20

title		Ubuntu, kernel 2.6.15-26-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by BuffaloX on 2006-07-20
Seems OK
of course you need to have the message.blusplash file in /boot/grub

My menu.lst has a line:

Default 0

Before the timeout line.
I have no idea if this means anything...

---

### Post by Jolly Roger on 2006-07-20
I do have message.blusplash in my /boot/grub directory. Thanks for trying to help. Anyone else got any ideas?

---

### Post by BuffaloX on 2006-07-20
Oh you changed your post..
I have the line
[I]
gfxmenu /boot/grub/message.mysplash[/I]

as the very first line.
then default 0
then timeout 10
...

---

### Post by Jolly Roger on 2006-07-20
Well I did have gfxmenu /boot/grub/message.blusplash as the very first line when I originally posted it. But I moved it to after the commented section to see if it would make the splash work, but it didn't. I editted my post though because that is how my current menu.lst is. Having it as the first line or in it's current position made no difference for me.

---

### Post by BuffaloX on 2006-07-20
Having it as first line works.
So it must be something else.

---

### Post by rogeriovinhal on 2006-07-20
Any amd64 packages for it?
Or the source, so I can do it myself?

Nevermind, just found it here:
[http://kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-7_amd64.deb](http://kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-7_amd64.deb)

---

### Post by Jench on 2006-07-21
Jolly Roger > have you tried with [this]("http://ubuntuforums.org/showpost.php?p=1214303&postcount=13") (thx to scenestar) because it works for me.

And if i'm not wrong it would be : *sudo grub-install /dev/hdc1* for you.
I hope it would help.

---

### Post by PingunZ on 2006-07-22
I updated the guide,
now it uses " find /boot/grub/stage1 " instead of the fdisk thing
I also added the posted messages
Ty very much to all who made a message or helped ppl in this thread ;)

Grtz PingunZ

---

### Post by xXx 0wn3d xXx on 2006-07-23
The Ubuntu Brown theme is amazing. Thanks for writing this tutorial. And to who it may concern, I am back on Ubuntu linux. Hopefully for good.

---

### Post by PingunZ on 2006-07-23
WB xXx 0wn3d xXx and ty very much

Grtz PingunZ

---

### Post by Footissimo on 2006-07-24
One which is a little lighter (and generic)..snowish! :)

This one is a mix-up of the web browser icon from the [Snowish icon set](http://www.gnome-look.org/content/show.php?content=32599) by 'Saki' and the [Snowish-inspirat wallpaper](http://www.gnome-look.org/content/show.php?content=33217) by wuf.  Had to move and add things around a little (and being lighter in colour) so it's not so 'clean' but..oh well.

To install: Install GFXboot. Unzip the message.snow file attached and move it to your /boot/grub directory, then open up /boot/grub/menu.lst and add the following line to the top: ```
gfxmenu /boot/grub/message.snow
```

---

### Post by PingunZ on 2006-07-24
nice footissimo, I added it to the howto ;)

Grtz PingunZ

---

### Post by Footissimo on 2006-07-24
You missed Ubuntu Brown..and called Ubuntu Grey, Brown :cry: 

Anyhoo, I've done another Kubuntu one 's a bit like the other one but a mash up of [this wallpaper](ttp://www.kde-look.org/content/show.php?content=42881) and the official Kubuntu SVG logo.

Unzip, move to /boot/grub and add the following to /boot/grub/menu.lst:
```
gfxmenu /boot/grub/message.kubu
```

---

### Post by PingunZ on 2006-07-24
Added that one too footissimo, nice work ;)

Grtz PingunZ

---

### Post by Footissimo on 2006-07-24
You missed what I said in the last post :(  Just quote then cut and replace the text in your HOWTO below "Here are some themes posted in this thread" and it'll correct and add a couple of links, correct the filenames..and give credit to people who made the themes.

Light Green generic theme [message.gobo] | [Link](http://ubuntuforums.org/showpost.php?p=1214274&postcount=12) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288)
Dark Brown (Dapper look) generic theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544)
Medium blue kubuntu theme [message.kubuntu] | [Link](http://ubuntuforums.org/showpost.php?p=1234300&postcount=54) | [Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)
Dark grey ubuntu theme [message.ubugrey] | [Link](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717)
Medium brown ubuntu theme [message.ububrown] | [Link](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657)
Light orange ubuntu theme [message.ubu] | [Link](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852)
Red ubuntu theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852)
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746)
White / Grey Snowish generic theme [message.snow] | [Link](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506)
Linspire-style blue kubuntu theme [message.kubu] | [Link](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390)

---

### Post by msak007 on 2006-07-24
> **Footissimo said:**
> 
Anyhoo, I've done another Kubuntu one 's a bit like the other one but a mash up of [this wallpaper]("ttp://www.kde-look.org/content/show.php?content=42881") and the official Kubuntu SVG logo.

Unzip, move to /boot/grub and add the following to /boot/grub/menu.lst:
```
gfxmenu /boot/grub/message.kubu
```

Thanks for this, it looks awesome.

---

### Post by DMC_Mandrake on 2006-07-25
How i can change the gfxboot language ? i want to use French.

Thanks

---

### Post by napo on 2006-07-25
I did a gfxboot theme, too.
Here is a screenshot:
[IMG]http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo_thumb.png[/IMG]

And here you can download it:
[http://mitglied.lycos.de/atoth/ubuntuusers/message.napo]("http://mitglied.lycos.de/atoth/ubuntuusers/message.napo")

---

### Post by ltmon on 2006-07-25
I just thought I should post that the newly advised method of installing grub using:
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```
did not work for me.

I had to use the old method of fdisk -l followed by grub-install.  Maybe because I don't have an IDE drive (e.g. my drive is sda1/sda2/sda3)?

Possibly you should add it back to the main instructions as an alternative method for installing.

L.

---

### Post by PingunZ on 2006-07-25
I added the message.napo and also added the links how you told me footissimo ( ty ;) )
ltmon, its weird that youre having that problem.
Are there others with this error ?

---

### Post by DMC_Mandrake on 2006-07-25
How i use the french translation ?

---

### Post by Malac on 2006-07-25
> **PingunZ said:**
> .....ltmon, its weird that youre having that problem.
Are there others with this error ?

Yep me too I recently did a re-install of Ubuntu and this time mucked up the MBR i.e. I installed it on there instead of my /dev/hda2. I re-wrote the MBR with XP fixmbr. And re-did grub from a live disk onto /dev/hda2 after that I couldn't get the find....root....setup method to work. Tried everything and in desperation this morning did grub-install method and it worked. As you can see my system is hdX so I don't think it's sdX related.

It may be worth adding it back in as an alternate if the other method doesn't work as most people wanting to do this might not troll to the end of the posts.

Perhaps my experience might point a more technically savvy person in the direction of what is happening.
Here's the output of fisk -l
```
Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1567    12586896    c  W95 FAT32 (LBA)
/dev/hda2   *        1568        3643    16675470   83  Linux
/dev/hda3            3644        3736      747022+   5  Extended
/dev/hda5            3644        3736      746991   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3961    31816701    c  W95 FAT32 (LBA)
/dev/hdb2            3962       24792   167325007+   f  W95 Ext'd (LBA)
/dev/hdb5            3962        7922    31816701    b  W95 FAT32
/dev/hdb6            7923       11883    31816701    b  W95 FAT32
/dev/hdb7           11884       16060    33551721    b  W95 FAT32
/dev/hdb8           16061       20237    33551721   83  Linux
/dev/hdb9           20238       24792    36588006    7  HPFS/NTFS

```

Hope this helps.

---

### Post by Footissimo on 2006-07-25
> **napo said:**
> I did a gfxboot theme, too.
Here is a screenshot:
[IMG]http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo_thumb.png[/IMG]

And here you can download it:
[http://mitglied.lycos.de/atoth/ubuntuusers/message.napo]("http://mitglied.lycos.de/atoth/ubuntuusers/message.napo")

Nice one!  Thats the first one I've seen that isn't a mash up of the default SuSE theme - would you mind saying how you did it?  I did a larger QEMU screenie for you:

[[IMG]http://img89.imageshack.us/img89/2035/screenshotru1.th.jpg[/IMG]](http://img89.imageshack.us/my.php?image=screenshotru1.jpg)

> I added the message.napo and also added the links how you told me footissimo

No probs - any more I do, I'll add a line so you just have to append :)

---

### Post by Footissimo on 2006-07-25
A Xubuntu theme.  This will be the last one until I can work out how to do a non-SuSE based GFXBoot theme.

This one is a mash-up of Eric Hewitt's SVG icon and JozsefMak's wallpaper from the Xubuntu art page: [https://wiki.ubuntu.com/XubuntuArtwork](https://wiki.ubuntu.com/XubuntuArtwork).  It's a little dull, sorry..but it has rodents! :)

To install - make sure you have GFXBoot installed, then unzip the theme file and put message.xubu in the /boot/grub directory then append the following to the top of /boot/grub/menu.lst:```
gfxmenu /boot/grub/message.xubu
```

For PingunZ

Light blue / grey Xubuntu theme [message.xubu] | [Link](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350)

---

### Post by ltmon on 2006-07-25
Well whilst install GfxBoot I've managed to screw things up royally and nuke my ability to boot Windows.  All of my important files are on Linux, but I do need to boot XP from time to time for work stuff.

Can anyone help me get out of this bind?

When I select it I get a very quick flash of "Loading stage 2" follwed by some "malloc" lines and hex codes.  It all goes by too fast to really see it.

So next I tried to mount my XP (NTFS) partition from Linux, and if failed with errors.  dmesg reports the following:
```

[17179857.324000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179857.324000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179857.324000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179857.324000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.

```

... not encouraging :(

My fdisk -l output:
```

ltmon@clifford:~$ sudo fdisk -l
Password:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        4177     2096482+  82  Linux swap / Solaris
/dev/sda3            4178       12161    64131480   83  Linux

```

Preferably I would like to rescue my Windows partition, but don't mind reinstalling it too much because it's pretty much vanilla and doesn't have anything irreplaceable other than saved games.

I really don't want to reinstall Dapper, as there's a whole lot of work gone into perfecting my setup.

On the plus side, Grub now looks really nice :)

Thanks,

L.

---

### Post by kno on 2006-07-25
> **DMC_Mandrake said:**
> How i can change the gfxboot language ? i want to use French.

Thanks

*Salut *DMC_Mandrake,

You have to replace in makefile (so you need theme source) line ```
DEFAULT_LANG =
``` by ```
DEFAULT_LANG = fr
```
and then compile.

---

### Post by kno on 2006-07-25
> **napo said:**
> I did a gfxboot theme, too.
Here is a screenshot:
[IMG]http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo_thumb.png[/IMG]

And here you can download it:
[http://mitglied.lycos.de/atoth/ubuntuusers/message.napo]("http://mitglied.lycos.de/atoth/ubuntuusers/message.napo")

Very nice !
I would like to take a look at your source...

Thanks

---

### Post by frodon on 2006-07-25
BTW, this guide has been added to the UDSF there :
[http://doc.gwos.org/index.php/GfxBoot](http://doc.gwos.org/index.php/GfxBoot)

Feel free to update the page or add some more theme links.

---

### Post by Footissimo on 2006-07-25
> **ltmon said:**
> Well whilst install GfxBoot I've managed to screw things up royally and nuke my ability to boot Windows.  All of my important files are on Linux, but I do need to boot XP from time to time for work stuff.

Can anyone help me get out of this bind?

When I select it I get a very quick flash of "Loading stage 2" follwed by some "malloc" lines and hex codes.  It all goes by too fast to really see it.

So next I tried to mount my XP (NTFS) partition from Linux, and if failed with errors.  dmesg reports the following:
```

[17179857.324000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179857.324000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179857.324000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179857.324000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.

```

... not encouraging :(

My fdisk -l output:
```

ltmon@clifford:~$ sudo fdisk -l
Password:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        4177     2096482+  82  Linux swap / Solaris
/dev/sda3            4178       12161    64131480   83  Linux

```

Preferably I would like to rescue my Windows partition, but don't mind reinstalling it too much because it's pretty much vanilla and doesn't have anything irreplaceable other than saved games.

I really don't want to reinstall Dapper, as there's a whole lot of work gone into perfecting my setup.

On the plus side, Grub now looks really nice :)

Thanks,

L.

Erm..I'm not the most technical, but couldn't you try reinstalling the Windows bootloader then, once that has done, reinstall grub from a live CD?

[This Wiki entry](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) refers to the latter - not sure about the windows bootloader...can't that be done by just partially going through the windows install (..just seen this: [Google cache link](http://66.249.93.104/search?q=cache:syt0pVVokoAJ:www.linuxforums.org/forum/redhat-fedora-linux-help/50847-removing-fedora-re-installing-windows-xp-boot-loader.html+reinstalling+master+boot+loader+windows&hl=en&gl=uk&ct=clnk&cd=5&client=firefox)

Sorry..not much help :(

---

### Post by ltmon on 2006-07-25
> **Footissimo said:**
> Erm..I'm not the most technical, but couldn't you try reinstalling the Windows bootloader then, once that has done, reinstall grub from a live CD?

[This Wiki entry](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) refers to the latter - not sure about the windows bootloader...can't that be done by just partially going through the windows install (..just seen this: [Google cache link](http://66.249.93.104/search?q=cache:syt0pVVokoAJ:www.linuxforums.org/forum/redhat-fedora-linux-help/50847-removing-fedora-re-installing-windows-xp-boot-loader.html+reinstalling+master+boot+loader+windows&hl=en&gl=uk&ct=clnk&cd=5&client=firefox)

Sorry..not much help :(

Well since posting I have made some progress.  The problem was that I installed Grub on my windows partition rather than my MBR. ](*,) 

I fixed this using the most excellent "testdisk" utility.  It can recover the NTFS partition boot sector by copying it from the backup. Don't use the version in the repositories, as it is old, but download from the testdisk website [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

After doing this it's easiest to reinstall grub before you reboot.  This time I did it properly.

Now I can mount the partition, but it still won't boot.  I think windows needs it's boot record fixed.  To do this I need the Windows XP install CD and to boot into a recovery mode.  Then issue the command "fixmbr" or "fixboot" or something similar.  I'll try this tommorrow.

Cheers,

L.

---

### Post by Footissimo on 2006-07-25
The google cache link shows how to repair the MBR..about 4-5 posts down :)  Though wouldn't surprise me if Windows co-opts Grub.. ho hum.  Good luck! :)

---

### Post by napo on 2006-07-25
> **kno said:**
> Very nice !
I would like to take a look at your source...

Thanks

This is the source: [http://mitglied.lycos.de/atoth/ubuntuusers/gfxboot-theme-napo-0.2.tar.bz2]("http://mitglied.lycos.de/atoth/ubuntuusers/gfxboot-theme-napo-0.2.tar.bz2")

You need this package to compile it: [http://www.barwap.com/morphix/gfxboot_2.5-12.1_i386.deb](http://www.barwap.com/morphix/gfxboot_2.5-12.1_i386.deb)

To change the gfxboot theme you have to edit the files with the inc extension. Here is explained how to do this: [http://mitglied.lycos.de/atoth/ubuntuusers/gfxboot.html]("http://mitglied.lycos.de/atoth/ubuntuusers/gfxboot.html")

This theme is based on the theme from Kanotix. But I did some little modifications.

---

### Post by KStorm on 2006-07-25
I hate to use my first ever post here to gripe, but I could not get it to work.  I downloaded it via kde-look.org to my home directory, unzipped it to /boot/grub/, edited grub (see below) as per instructions, but no change.  Something I'm missing?

Edit: I'll try commenting out "pretty colors" and see what happens.

[I]gfxmenu /boot/grub/message.kubu

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
 color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Kubuntu 6.06 LTS, kernel 2.6.15-26-k7
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Kubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb5 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

title		Kubuntu, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		PCLinuxOS .93 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-oci3.lve root=/dev/hdb1 vga=788 ro noapic nolapic acpi=ht psmouse.proto=imps splash=silent 
initrd		/boot/initrd-2.6.15-oci3.lve.img
savedefault
boot[/I]

---

### Post by Footissimo on 2006-07-25
Sounds obvious, but you didn't mention it...did you install GFXBoot?

---

### Post by PingunZ on 2006-07-26
KStorm, do ```
sudo kate /boot/grub/menu.lst
```
and paste this in it ( just remove everything and paste this ::
```
gfxmenu 	/boot/grub/message.kubu
default 	0
timeout 	15

title Kubuntu 6.06 LTS, kernel 2.6.15-26-k7
root (hd1,4)
kernel /boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb5 vga=791 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-k7
savedefault
boot

title Kubuntu, kernel 2.6.15-26-k7 (recovery mode)
root (hd1,4)
kernel /boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb5 ro single
initrd /boot/initrd.img-2.6.15-26-k7
boot

title Kubuntu, memtest86+
root (hd1,4)
kernel /boot/memtest86+.bin
boot

title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1


title 	Microsoft Windows XP Home Edition
root 	(hd0,1)
savedefault
makeactive
chainloader +1


title 	PCLinuxOS .93 (on /dev/hdb1)
root 	(hd1,0)
kernel /boot/vmlinuz-2.6.15-oci3.lve root=/dev/hdb1 vga=788 ro noapic nolapic acpi=ht psmouse.proto=imps splash=silent
initrd /boot/initrd-2.6.15-oci3.lve.img
savedefault
boot
```

---

### Post by i-mehl on 2006-07-26
hi.

nice howto..
but how can i change the resolution of the monitor.
because the grub-menu is blurred.

---

### Post by PingunZ on 2006-07-26
What do you mean ? the gfxboot image is blurred ?
try another one, but there are lots of limitations. so its normal

Grtz PingunZ

---

### Post by KStorm on 2006-07-26
> **Footissimo said:**
> Sounds obvious, but you didn't mention it...did you install GFXBoot?Yep.

---

### Post by KStorm on 2006-07-26
> **PingunZ said:**
> KStorm, do ```
sudo kate /boot/grub/menu.lst
```
and paste this in it ( just remove everything and paste this ::
<snip>Nothing changed with the GRUB screen, but the subsequent Kubuntu bootup graphics were much smaller (perhaps due to the insertion of the vga=791 argument in the kernel line).

---

### Post by PingunZ on 2006-07-26
Yes, its something I like so I put it in there, erm...
did you install everything without errors ?

Grtz PingunZ

---

### Post by KStorm on 2006-07-27
> **PingunZ said:**
> Yes, its something I like so I put it in there, erm...
did you install everything without errors ?

Grtz PingunZNo issues there.  I'm running the K7 kernel, so that might be an issue.
 [https://launchpad.net/distros/ubuntu/+spec/portable-gfxboot]("https://launchpad.net/distros/ubuntu/+spec/portable-gfxboot")

---

### Post by msak007 on 2006-07-27
> **KStorm said:**
> No issues there.  I'm running the K7 kernel, so that might be an issue.
 [https://launchpad.net/distros/ubuntu/+spec/portable-gfxboot](https://launchpad.net/distros/ubuntu/+spec/portable-gfxboot)

I'm running gfxboot on a k7 kernel with no issues.

---

### Post by PingunZ on 2006-07-27
msak007, your kernel has nothing todo with gfxboot
gfxboot starts before your ubuntu.
But I'm glad it works ;)

---

### Post by i-mehl on 2006-07-27
hi PingunZ.

i change the image, but there is the same :(

---

### Post by gmc on 2006-07-27
Hi Folks,

I must be in need of sleep. I've followed this howto and when I get to running grub, I get the following:

```

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)
 Filesystem type is reiserfs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  18 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

However when I reboot, I just get a simple text menu, no graphical menu when I reboot.

```

gfxmenu /boot/grub/message.suse
default         0
timeout         10

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda6 ro single
initrd          /boot/initrd.img-2.6.15-26-686
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

```

G.

---

### Post by PingunZ on 2006-07-27
So you followed the WHOLE howto on the first page, without errors, your sure you did every step ?

---

### Post by msak007 on 2006-07-27
> **PingunZ said:**
> msak007, your kernel has nothing todo with gfxboot
gfxboot starts before your ubuntu.
But I'm glad it works ;)
 
I know it doesn't, I was just replying to KStorm's post to demonstrate that it's not kernel releated because I'm using the same kernel.

---

### Post by drbmm on 2006-07-27
I too followed the following steps to install GfxBoot:

1. Downloaded the files
2. Uninstalled grub
3. Installed debs
4. Copied file to /boot/grub
5. Added line to menu.lst (added it at the very top, i.e. line 1)
6. Entered the Grub commands
7. Rebooted

Still the text grub page on reboot.

To get the thing to finally work I did the following at step 6:

sudo grub-install /dev/hd*x* #put your drive values in

sudo grub

grub< setup (hd*x*,*y*) #put your values in here

grub< root (hd*x*,*y*) #put your values in

grub< quit

reboot

When I rebooted I got the grub prompt instead of the nice graphical log in screen. At the grub prompt I did the following again:

grub< setup (hd*x*,*y*) #put your values in here

grub< root (hd*x*,*y*) #put your values in

Grub would not allow me to quit so I did a Ctrl-Alt-Del to reboot.

On reboot the nice graphical interface was there.

I have performed the above on two computers to get the program to   work.

---

### Post by domino on 2006-08-01
[earlier post removed]

okay, I had no idea i had access to grub without using a boot disk. So i' back in dapper but without GfxBoot. I'm going to test some thing and see if I can get it to work. In the mean time here is an error:

```
grub> setup (hd1,0)

Error 12: Invalid device requested
```

Those are the correct drive perameters where /boot exists. The MBR is also on IDE hd1,0. I don't understand the error stating that it's an "invalid device".
```
gfxmenu /boot/grub/message.blusplash
#
default		0
#
timeout		10
## ## End Default Options ##

title		Dapper 6.06, kernel 2.6.15-26-686
root		(hd1,0)
kernel		/vmlinuz-2.6.15-26-686 root=/dev/hdc2 ro quiet splash  vga=795
initrd		/initrd.img-2.6.15-26-686
savedefault
boot

title		Microsoft Windows XP / Windows Vista
root		(hd0,0)
savedefault
chainloader	+1

title		Alternative OS
root		(hd0,1)
makeactive
chainloader	+1

#title		Ubuntu, memtest86+
#root		(hd1,0)
#kernel		/memtest86+.bin 
#boot
```

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+   7  HPFS/NTFS
/dev/hda2   *        1913        4998    24788295   af  Unknown

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          18      144553+  83  Linux
/dev/hdc2              19         869     6835657+  83  Linux
/dev/hdc3             870         930      489982+  82  Linux swap / Solaris
/dev/hdc4             931        4998    32676210    f  W95 Ext'd (LBA)
/dev/hdc5             931        2205    10241406   83  Linux
/dev/hdc6            2206        4331    17077063+   7  HPFS/NTFS
/dev/hdc7            4332        4998     5357646    b  W95 FAT32
```

Device map:
```
(hd0)	/dev/hda
(hd1)	/dev/hdc
```

---

### Post by domino on 2006-08-01
Okay i tried a few things but I just cnt get it to work. I think this error on post #122 is the problem. Now on hard boot, grub wouldn't load.

[edit]

solved

---

### Post by doncarlos on 2006-08-03
I do the steps what are in the first post and i dont have graphical grub. I tried many times but dont want to work. I dont know whats the matter.

Pls somebody give an advice to me:(

---

### Post by Malac on 2006-08-03
> **doncarlos said:**
> I do the steps what are in the first post and i dont have graphical grub. I tried many times but dont want to work. I dont know whats the matter.

Pls somebody give an advice to me:(

Have you tried the other method:
```
 sudo grub-install /dev/hdx #put your drive values in
```

---

### Post by domino on 2006-08-03
Why is it on every hard boot, grub deosn't show and goes straight into Windows active partition. but every soft boot, grub shows?

---

### Post by domino on 2006-08-03
Okay, so I get no response to my post from 2 days ago. And obvioussly no one cares to support this thread anymore.

How do i revert back to the original grub configuration. Undoing what was done from the 1st page. This "hack" is not worth all this trouble. You only see grub for less than3 seconds anyway.

---

### Post by kno on 2006-08-04
> **domino said:**
> Okay, so I get no response to my post from 2 days ago. And obvioussly no one cares to support this thread anymore.

How do i revert back to the original grub configuration. Undoing what was done from the 1st page. This "hack" is not worth all this trouble. You only see grub for less than3 seconds anyway.
Try this 3 commands, it should work :
```
sudo apt-get remove grub-gfxboot
sudo apt-get install grub
sudo update-grub
```

---

### Post by domino on 2006-08-04
Yea that worked. Thanks. 

This was my image while I was using the hack. Not perfect, but It was fun while it lasted.

[[IMG]http://img140.imageshack.us/img140/3503/backph4.th.jpg[/IMG]](http://img140.imageshack.us/my.php?image=backph4.jpg)

---

### Post by fornix on 2006-08-04
I am getting a 404 error on the message.suse link. Can someone giv me the message.suse file please.

---

### Post by kno on 2006-08-05
> **fornix said:**
> I am getting a 404 error on the message.suse link. Can someone giv me the message.suse file please.

[ATTACH]13830[/ATTACH]

---

### Post by doncarlos on 2006-08-05
> **Malac said:**
> Have you tried the other method:
```
 sudo grub-install /dev/hdx #put your drive values in
```

```
don @ the_box /home/don]>> sudo grub-install /dev/hda     
cannot find a GRUB device for /boot/grub.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
```

```
don @ the_box /home/don]>> sudo grub-install hd0    
cannot find a GRUB device for /boot/grub.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
```

And when I try a module:
```
 sudo grub-install --modules=default /dev/hda
cannot find a GRUB device for /boot/grub.
grub-setup: error: Cannot guess the root device. Specify the option ``--root-device''.

```
:confused:

---

### Post by kno on 2006-08-05
[QUOTE=doncarlos;1341689]```
don @ the_box /home/don]>> sudo grub-install /dev/hda     
cannot find a GRUB device for /boot/grub.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
```
Could you tried this :
```
sudo grub-install /dev/hd**c**
```
or :
```
sudo grub-install /dev/hd**1**
```

---

### Post by Malac on 2006-08-05
> **doncarlos said:**
> ```
don @ the_box /home/don]>> sudo grub-install /dev/hda     
cannot find a GRUB device for /boot/grub.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
``` 
```
don @ the_box /home/don]>> sudo grub-install hd0    
cannot find a GRUB device for /boot/grub.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly
``` 
And when I try a module:
```
 sudo grub-install --modules=default /dev/hda
cannot find a GRUB device for /boot/grub.
grub-setup: error: Cannot guess the root device. Specify the option ``--root-device''.

``` :confused:

My command reads as follows:
```
sudo grub-install /dev/hda[SIZE=3][COLOR=Red]**2**[/COLOR][/SIZE]
``` As I want my grub on partition 2 of the first hard drive (a) this command works for me.
Try it with the correct partition number for your system;
 i.e.
 /dev/hda1 - First Drive, First Partition
 /dev/hda2 - First Drive, Second Partition
 /dev/hdb1 - Second Drive, First Partition
 /dev/hdb4 - Second Drive, Fourth Partition

So long as this partition is marked active/bootable it should work.

---

### Post by aceracer24 on 2006-08-07
ok I have tried this over and over again with no luck what so ever. First off doing sudo grub gets me a grub prompt but typing in find /boot/grub/stage1 just gives me file not found..... so I tried teh grub-install /dev/hda which game me the same error everyone else got but at teh end said it finished with no errors :shock: but when I rebooted grub spits out that /boot/grub/message.xubu (I picked that one instead of suse since there is no longer a suse link) can't be found...WTF? It's like the partitions don't exist. I've all but given up because even using normal grub and trying to install a bankground gave me much the same error, file can't be read or found. I have been able to get compiz running MUCH easier then getting something as simple as backgrounds for grub to work. ANYONE have any idea what might be the problem? The only thing i can think of is that /boot is on another HDD (hda2) and the rest of the system is on hdb. No clue if that could be the cause of the problem or not.

EDIT: well no reply's, thats always a good sign lol. Anyway, I managed to find my problem. The command grub> Find /boot/grub/stage1 didn't work but after some playing and frustration I found that grub> Find /grub/stage1 did work. I am guessing this has to do with the boot being on a seperate hdd? ANyway all is well in the grub splash world..for me anyway.

---

### Post by delfick on 2006-08-10
just came upon this today...

at first it didn't work
but i kept trying...have no idea what i did..but now it works

so i'm happy :D:D:D:D 
 
so thnx for the tutorial... :D

simple question though....is there a place like gnome-look.org or something like that where i can find other message.xyz files?

thnx

---

### Post by der_kaiser on 2006-08-10
Hello everybody,
I'm working on a customized version of a Live CD based on Ubuntu Dapper.
I'm trying since days to change the picture of gfxboot, but without success...
Gfxboot has almost no documentation, and it's very hard to work on it. As the live cd uses Isolinux instead of Grub as a bootloader, I can't use the Howto in this topic. I've found that the only way to customize the gfxboot picture, is to recompile gfxboot with a PCX picture.
So what I've done, is running make in /usr/share/gfxboot/themes/Ubuntu with my own PCX picture. But I get an error message : 

```
Undefined words: txt_error_title, txt_info_title, txt_change_disk_title, txt_insert_disk, txt_insert_disk3, txt_insert_disk2, txt_load_kernel_title, txt_load_memtest, txt_load_kernel, txt_password_title, txt_password, txt_exit_title, txt_exit_dialog, txt_dvd_warning_title, txt_dvd_warning2, txt_power_off_title, txt_power_off, txt_ok, txt_cancel, txt_reboot, txt_continue, txt_bootoptions, txt_help, txt_harddisk_title, txt_hd_diskdevice, txt_directory, txt_ftp_title, txt_server, txt_user1, txt_http_title, txt_nfs_title, txt_smb_title, txt_domain, txt_user2, txt_other_options, texts
make: *** [bootdir] Erreur 10
```

The only modification I did to the original Makefile is to set the DEFAULT_LANG to fr . 

Can anyone help me on that? Thanks a lot!

---

### Post by denisesballs on 2006-08-13
Ok, you REALLY should add to the first page, if your boot partition is on a seperate partition, that you should do:

```
find /grub/stage1
```

and you should add

```
/grub/message.suse
```

to the menu.lst. A lot of Linux users (especially ones with LVM) have seperate boot partitions.

---

### Post by ophanim on 2006-08-13
I'm having problems getting this to work.  I've followed the directions step by step twice now, but I'm left with the same plain text boot menu that's on by default.

Here's my fdisk -l output if it helps.

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19010   152641597+   7  HPFS/NTFS
/dev/sda3           19011       19452     3550365   db  CP/M / CTOS / ...

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4314    34652173+  83  Linux
/dev/sdb2            4315        4500     1494045    5  Extended
/dev/sdb5            4315        4500     1494013+  82  Linux swap / Solaris

```

Note: When I'm in grub, I'm doing (hd1,0), but my fdisk doesn't show any hda devices.

---

### Post by nathanbriggs on 2006-08-14
Thanks for this solved a problem I had with graphics file not found in grub error stage 2

You wouldn't believe how nice it is not to have to press a key to reboot (sometimes I'ma thousand miles away)

And now I can have eye candy boot splashes too

---

### Post by spockrock on 2006-08-14
this seems weird but I made my own splash, and on my xubuntu box it works perfectly but on my ubuntu box, the gfx menu either crashes or just reboots my computer I have no Idea why.  but if I use one of the ones posted here it works perfectly.   Anyone have any clue as to why that might be??

---

### Post by roe_polak on 2006-08-16
Hi... I couldn't get it working by using the "sudo grub"-command because of my sata drives (I think, I'm noob). Instead I had to log in as root and use "grub-install /dev/sda2". First I tried "sudo grub-install /dev/sda2" but this returned a lot of errors and I didn't dare rebooting. I tried root and it installed with no errors. I really liked this feature in Suse, but I like it even more when it serves Ubuntu...

Again, I should note that I only used this method because of my sata drives. As far as I have understood, the folks with IDE drives can use the guide as is.

To gain root-privileges I entered this in the terminal:

sudo passwd root
(set the password)

Here's my "session" from the terminal:

```
def@maskine:/$ sudo grub-install /dev/sda2
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> root (hd0,1)
 Filesystem type is reiserfs, partition type 0x83
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,1)"...  18 sectors are embedde d.
succeeded
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 (hd0,1) (hd0,1)1+ 18 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2
grub> quit


def@maskine:/$ su
Password:
root@maskine/# grub-install /dev/sda2
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
root@maskine:/#
```

Please tell me if any of my conclussions, especially that one about root (and not sudo), is incorrect. My goal is to help anyone having the same problems, not to throw them into even worse trouble. I'm also sorry if any of this has been noted before in this thread, but since the custom themes showed up, it's like the support-asspect in the thread disappeared.

Oh, and do back up your menu.lst. Justin Case...

---

### Post by human on 2006-08-17
If anyone is still trying to make this work, try the command

```
sudo apt-get install gfxboot
```

as opposed to the file that was in the first post of this thread. 

it worked for me ;)

---

### Post by kno on 2006-08-18
> I couldn't get it working by using the "sudo grub"-command because of my sata drives (I think, I'm noob).
[...]
As far as I have understood, the folks with IDE drives can use the guide as is.
[...]
[-X
> Note that GRUB does not distinguish IDE from SCSI - it simply counts the drive numbers from zero, regardless of their type. Normally, any IDE drive number is less than any SCSI drive number, although that is not true if you change the boot sequence by swapping IDE and SCSI drives in your BIOS.
source : [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")

I've a SATA drive and I only use the commands :
> 
```

sudo grub
grub> find /boot/grub/stage1
 (hd[COLOR="#ff0000"]x[/COLOR],[COLOR="#ff0000"]y[/COLOR])
grub> root (hd[COLOR="#ff0000"]x[/COLOR],[COLOR="#ff0000"]y[/COLOR])
grub> setup (hd[COLOR="#ff0000"]x[/COLOR])
```

---

### Post by Malakia on 2006-08-18
I had tried both ways and I still get that black screen does anybody have any suggestions. I have tried two different messages two.

---

### Post by distroman on 2006-08-20
hmmm, all that did was cook my mbr, I just had to reinstall grub. :(
I can't quit understand how come, but if someone could help me, ill gladly cook grub again. 

I am on duel boot, but since reinstalling grub was fine, I am not sure if that's of any importance.

I used this theme message.blusplash.

```
grub> find /boot/grub/stage1
```
Gave me (hd0,4) so I did -
```
grub> root (hd0,4)
grub> setup (hd0)
```

On reboot I didn't even make it to grub, totally cooked.
Anyone know where I made the mistake?

edit

Seems like there use to be some other instructions.
> **ltmon said:**
> I just thought I should post that the newly advised method of installing grub using:
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```
did not work for me.

I had to use the old method of fdisk -l followed by grub-install.  Maybe because I don't have an IDE drive (e.g. my drive is sda1/sda2/sda3)?

Possibly you should add it back to the main instructions as an alternative method for installing.

L.
Any way it could have anything to do with this?

edit

> As to your problem, post your menu.lst and your fstab and make sure the message.blusplash is in the grub folder and is owned by root with 755 permission. What was the error message when you tried to boot to grub?

This is all I did with the message.bluesplash - 
```
sudo cp message.bluspash /boot/grub/
```

As for an grub error on reboot (from memory), I didn't really get one. It didn't find grub at all, it didn't even say it didn't. I think it was something like - “hd0,0 succeeded”. 
When I try again, ill be sure to note the error.

menu.lst
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

fdisk -l
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6145    49359681    7  HPFS/NTFS
/dev/hda2            6146        9964    30676117+   f  W95 Ext'd (LBA)
/dev/hda5            6146        7178     8297541   83  Linux
/dev/hda6            7179        7318     1124518+  82  Linux swap / Solaris
/dev/hda7            7319        9964    21253963+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2581    20731851    7  HPFS/NTFS
/dev/hdb2            2582        4111    12289725    f  W95 Ext'd (LBA)
/dev/hdb5            2582        4111    12289693+   b  W95 FAT32
```
Thanks

---

### Post by ScottMorris on 2006-08-25
Hi, I have followed the directions many times and it has been unsucessful. below is my menu.lst code, maybe I did something wrong.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
gfxmenu (hd0,1)/boot/grub/message.gobo
splashimage (hd0,1)/home/scott/bootback.xpm.gz

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## ## End Default Options ##

title		Ubuntu 6.06 LTS
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
boot

#title		Debian GNU/Linux, kernel 2.6.15-26-686 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro #single
#initrd		/boot/initrd.img-2.6.15-26-686
#boot

#title		Debian GNU/Linux, kernel memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin 
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I know there is the bootsplash command in there but it is better than looking at black all the time.  I had disabled it to try gfxmenu but it just was the plan black GRUB so I put my boot piture back in.  What could be wrong with it?  I followed the instructions and it turned out nothing.  BTW there is no error messages that come up.

---

### Post by rohankaikini on 2006-08-26
Hi,
I tried to install gfxboot.. as shown in the 1st page of this thread..
everything went well.. as in i got all 'succeeded' messages

But now, all i get on booting is a black screen with a 
'grub>' prompt...
i dont know what to do next... i am unable to boot up my system...
please help

~rohan

---

### Post by Malac on 2006-08-26
> **rohankaikini said:**
> Hi,
I tried to install gfxboot.. as shown in the 1st page of this thread..
everything went well.. as in i got all 'succeeded' messages

But now, all i get on booting is a black screen with a 
'grub>' prompt...
i dont know what to do next... i am unable to boot up my system...
please help

~rohan
Type:
```
 grub> find /boot/grub/stage1
 (hdx,y) [SIZE=2][COLOR=DarkOliveGreen]# this will be the output[/COLOR][/SIZE]
grub> root (hdx,y)
grub> setup (hdx,y)

```see if that works.

---

### Post by rohankaikini on 2006-08-26
> **Malac said:**
> Type:
```
 grub> find /boot/grub/stage1
 (hdx,y) [SIZE=2][COLOR=DarkOliveGreen]# this will be the output[/COLOR][/SIZE]
grub> root (hdx,y)
grub> setup (hdx,y)

```see if that works.
i tried that... 
it says:
> 
grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,2)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

grub>


Thats it... nothing after that... again when i reboot, i get the same prompt..
Is there a way i can check or edit menu.lst file? i think i might have done something wrong there... 

I have taken a backup of that file though.. as mentioned in the method in this thread..

Please tell me what to do...
Thanks a ton for replying..

~rohan

---

### Post by Malac on 2006-08-26
Just to double check this method only works with the gfxboot that is mentioned at the beginning of the thread.

[http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

If you have ANY version of GRUB installed as well you have the wrong gfxboot installed. Check this in synaptic.

```
grub> find /boot/grub/stage1
 (hdx,y) [SIZE=2][COLOR=DarkGreen]# this will be the output[/COLOR][/SIZE]
grub> root (hdx,y)
 Filesystem type is ext2fs, partition type 0x83 [SIZE=2][COLOR=DarkGreen]# this should be the output[/COLOR][/SIZE]
grub> setup (hdx,y)
``` 
and do this also.

```
sudo grub-install /dev/hd[COLOR=Red]A0[/COLOR]
``` Replace the [COLOR=Red]A[/COLOR] with lowercase letter of drive, [COLOR=Red]0[/COLOR] with partition number on that drive.
GRUB to dev conversion.
(hd0) = /dev/hda
(hd1) = /dev/hdb
([COLOR=Red]xxx[/COLOR],0) = /dev/[COLOR=Red]xxx[/COLOR]1
([COLOR=Red]xxx[/COLOR],1) = /dev/[COLOR=Red]xxx[/COLOR]2
([COLOR=Red]xxx[/COLOR],7) = /dev/[COLOR=Red]xxx[/COLOR]8

My other problem I had with this was that I had two GRUB's on my system one on /dev/hdb2 and one in the MBR of the first hard drive /dev/hda. One got updated one didn't. Check that is not the case.

Hope this helps.

---

### Post by Matrixy on 2006-08-26
Hi,
I have read this thread on how to do GfxBoot like in SuSe.
i have amd64 kernel and the deb file is for 386...
how can i install the GfxBoot and make it work instead of GRUB...
i want my menu to have an animation B4 loading Os...
thx for ur help

---

### Post by ciscosurfer on 2006-08-26
[COLOR=Red]***WARNING***[/COLOR]: As with any HOWTO, please take care when modifying your files/system; backup if necessary, and prepare for alternative outcomes. 
The following is what's worked best for me ;).

[B][COLOR=Sienna]_*What works for one, does not work for all!*_[/COLOR]

[/B]If you are still having trouble getting Gfxboot work, try the following steps (modified from [this post]("http://ubuntuforums.org/showpost.php?p=1307510&postcount=121")) that have worked for me:

1. **Start by backing up your current menu.lst so you can revert to it if you want to later**```
sudo cp -pv /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` 2. **Download the files** ([grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb") and [message.suse]("http://quasarfreak.googlepages.com/message.suse") [you can use the files at the bottom of [this UDSF page]("http://doc.gwos.org/index.php/GfxBoot") as well, or the end of the first post of this thread!])
3. **Uninstall grub**```
sudo aptitude remove grub
``` 4. **Install .deb file **'cd' to wherever you downloaded the .deb file, then  issue```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
``` 5. **Copy message.suse file to */boot/grub*** 'cd' to wherever you downloaded the theme file, then issue```
sudo cp message.suse /boot/grub/ ## you can copy any message file over from the bottom of the UDSF page as well
``` 6. **Add line to beginning of */boot/grub/menu.lst* file**```
gfxmenu /boot/grub/message.suse ## modify message.suse to whichever theme you downloaded, message.snowish, for example
``` 7. **Enter the following GRUB commands** (use [COLOR=Red]sudo fdisk -l[/COLOR] to find out where your Ubuntu drive/partition is located...mine happens to be on [COLOR=DarkGreen]sda1[/COLOR], so I use that.) Each line is a separate command:```
sudo grub-install /dev/hd*x* ## put your drive values in...mine happens to be [COLOR=DarkGreen]sda1[/COLOR], so I use that

sudo grub

grub> find /boot/grub/stage1  ## use the output of this to fill in the following values...output will look like this (hd*x,y*) ... mine is (hd1,0)

grub> root (hd*x*,*y*)  ## put your values in here from previous step ... I put in (hd1,0) here including the parentheses

grub> setup (hd*x*,*y*)  ## put your values in here from previous step ... again, I use (hd1,0)

grub> quit

Save all open files, close out, reboot.  I like to use [COLOR=Red]sudo reboot[/COLOR] b/c it's quick...but be sure to save any open file(s) and close out programs before you do this!
```8. [B]Reboot and enjoy your new GRUB modification!

FYI:  [/B]If you have your "Pretty Colors" line enabled (uncommented) or have added your own to your menu.lst file, I have found commenting it out once again, like it is by default on a fresh Ubuntu install, has been helpful...don't know whether this is important or not :wink:

---

### Post by Ahriman on 2006-08-26
Very good. My grub looks awesome now :)
(using Ubuntu Grey)

---

### Post by latebeat on 2006-08-27
> **ltmon said:**
> I just thought I should post that the newly advised method of installing grub using:
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```
did not work for me.

I had to use the old method of fdisk -l followed by grub-install.  Maybe because I don't have an IDE drive (e.g. my drive is sda1/sda2/sda3)?

Possibly you should add it back to the main instructions as an alternative method for installing.

L.


Same thing for me as well, just thought I'd let you know so u could add the second method as well to the howto.


Also I've got a couple of questions..

Does anyone know how to change the resolution of the boot up screen? I'm using a widescreen monitor and 800x600 doesn't look as good. I tried resizing the .jpg image in the message archive to 1680x1050 but it was only shown cropped during boot.

thanks again for the wonderful guide!!

---

### Post by Metroid48 on 2006-08-27
Hi, I typed setup (hd0) by accident (my ubuntu drive is at hd1) and, though GFXboot works fine for Ubuntu, I can't boot windows anymore. BTW, my Ubuntu drive is removable, so that's why I didn't want to install it on my HD.

Also, I'm getting an error 21 for GRUB on the HD.

How do I fix this and uninstall it so that WinXP boots normally?

Thanks,
-Metroid48

---

### Post by ciscosurfer on 2006-08-27
@latebeat
Refer to [post #153]("http://ubuntuforums.org/showpost.php?p=1426798&postcount=153")

And try keeping your questions limited to the title of this thread...post other questions not relating to Gfxboot to another thread to keep this thread consistent.

---

### Post by misaine on 2006-08-27
here is my theme
[http://img182.imageshack.us/img182/2210/terrezo9.th.jpg](http://img182.imageshack.us/img182/2210/terrezo9.th.jpg)
[http://misaine.chez-alice.fr/gfxboot/message.terre](http://misaine.chez-alice.fr/gfxboot/message.terre)
sorry i don't know how to use qemu

---

### Post by Malac on 2006-08-27
> **Metroid48 said:**
> Hi, I typed setup (hd0) by accident (my ubuntu drive is at hd1) and, though GFXboot works fine for Ubuntu, I can't boot windows anymore. BTW, my Ubuntu drive is removable, so that's why I didn't want to install it on my HD.

Also, I'm getting an error 21 for GRUB on the HD.

How do I fix this and uninstall it so that WinXP boots normally?

Thanks,
-Metroid48
Boot to your Windows XP disc and go to recovery console type in fixboot and fixmbr. If you don't know how to get to recovery console do a google search for "XP RECOVERY CONSOLE".

---

### Post by Metroid48 on 2006-08-27
Uh-oh. I have no clue where my XP disk is.

Any free ways to do it?

EDIT: Also, forgot to mention it. I don't have a floppy drive either.

---

### Post by Malac on 2006-08-27
[SIZE=3]Metroid48[/SIZE]
Try this page : [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

XPQUICK files may do the job. If not there are some CD .iso files as you don't have a floppy. You'll probably also need the one with NTLDR and NTDETECT on also, they're on that site if you search.

Or if you can get a Bootable DOS CD with fdisk.exe on it(maybe from a friend or from inside Ubuntu) you could try DOS Command fdisk /mbr. 

From Microsoft.com
>  Fdisk has an undocumented parameter called **/mbr** that causes it to write the master boot record to the hard disk without altering the partition table information.  This only works on the first hard drive but can be dangerous as it can, on rare occassions, make the files that are on the disk unreadable so do it at your own risk.

---

### Post by Metroid48 on 2006-08-27
Well, I found a recovery CD that doesn't require me to have my installation cd.

fixboot works fine, but fixmbr warns that I have a non-standard configuration. It says partitions may become unstable if I proceed.

I have three partitions (1system file thingy, one C:/ drive, and some other system file thingy) and of course the messed up Grub boot loader.

Should I still try fixmbr?

Thanks,
-Metroid48

---

### Post by Metroid48 on 2006-08-27
Hey, so is fixmbr stable enough or could it actually destroy my Windows install?

---

### Post by Malac on 2006-08-28
> **Metroid48 said:**
> Hey, so is fixmbr stable enough or could it actually destroy my Windows install?

Theoretically; Yes, but if you can do a backup of any data you don't want to lose, it may be worth a try.
I, too, had that warning with fixmbr when GRUB installed in my hd0 MBR. I ran the command anyway as I had backups of data and it worked out fine and restored my MBR to Windows XP version.
The GRUB MBR on your first drive could be what it means by "non-standard".

It's ultimately upto you.

---

### Post by latebeat on 2006-08-28
> **ciscosurfer said:**
> @latebeat
Refer to [post #153]("http://ubuntuforums.org/showpost.php?p=1426798&postcount=153")
.

I don't think u read my post at all :)
I solved the problem but had to reboot and reboot and go through 10 pages of this thread until I came up to ltmon's post. It never occured to me doing grub-install /dev/sdx instead of grub, root bla bla, setup bla bla as they are essentially the same thing. Anyway, just thought I'd post my experience as well to help update the howto and save others the trouble I had.

thanks tho

---

### Post by ciscosurfer on 2006-08-28
@latebeat
I'm not sure what you mean.  Your last post (two posts ago) you quoted ltmon and agreed with him/her that the method he lists didn't work for you either.  My method, on the other hand, is a little different than that.  Maybe take a look at it again to verify this.  Either way, glad you solved your problem with whichever way worked for you (no solution is a catch-all solution).

---

### Post by distroman on 2006-08-28
This howto should get added to the first page as an alternative. 
It seems to me that the howto as it is now, don't cover, multiple partitions, dual boot, boot partitions etc. 
> **ciscosurfer said:**
> If you are still having trouble getting Gfxboot work, try the following steps (modified from [this post]("http://ubuntuforums.org/showpost.php?p=1307510&postcount=121")) that have worked for me:

1. **Download the files** ([grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb") and [message.suse]("http://quasarfreak.googlepages.com/message.suse") [you can use the files at the bottom of [this UDSF page]("http://doc.gwos.org/index.php/GfxBoot") as well, or the end of the first post of this thread!])
2. **Uninstall grub**```
sudo aptitude remove grub
``` 3. **Install .deb file **'cd' to wherever you downloaded the .deb file, then  issue```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
``` 4. **Copy message.suse file to */boot/grub*** 'cd' to wherever you downloaded the theme file, then issue```
sudo cp message.suse /boot/grub/ ## you can copy any message file over from the bottom of the UDSF page as well
``` 5. **Add line to beginning of */boot/grub/menu.lst* file**```
gfxmenu /boot/grub/message.suse ## modify message.suse to whichever theme you downloaded, message.snowish, for example
``` 6. **Enter the following GRUB commands** (use [COLOR=Red]sudo fdisk -l[/COLOR] to find out where your Ubuntu drive/partition is located...mine happens to be on [COLOR=DarkGreen]sda1[/COLOR], so I use that.) Each line is a separate command:```
sudo grub-install /dev/hd*x* ## put your drive values in...mine happens to be [COLOR=DarkGreen]sda1[/COLOR], so I use that

sudo grub

grub> find /boot/grub/stage1  ## use the output of this to fill in the following values...output will look like this (hd*x,y*) ... mine is (hd1,0)

grub> root (hd*x*,*y*)  ## put your values in here from previous step ... I put in (hd1,0) here including the parentheses

grub> setup (hd*x*,*y*)  ## put your values in here from previous step ... again, I use (hd1,0)

grub> quit

Save all open files, close out, reboot.  I like to use [COLOR=Red]sudo reboot[/COLOR] b/c it's quick...but be sure to save any open file(s) and close out programs before you do this!
```7. [B]Reboot and enjoy your new GRUB modification!

FYI:  [/B]If you have your "Pretty Colors" line enabled (uncommented) or have added your own to your menu.lst file, I have found commenting it out once again, like it is by default on a fresh Ubuntu install, has been helpful...don't know whether this is important or not :wink:
Perhaps this howto should have some sort of **[COLOR="Red"]warning[/COLOR]** as well, don't these kind of howto's usually have that? 
When I mess with stuff like this, I always backup first. Secondly I have messed up so many MBR's, (because I am really dumb, with stuff like this) that I feel I can fix them with a little luck. However it could be that, not all feel that way. 

During this I managed to both screw up grub and last, but not least windows MBR, I know :D
To my surprise I could fix windows with “fixboot” without messing up grub. I think I know why now, as beside getting a nice picture in grub, I have learned a bit. 

Thank you for this second howto, because I needed a bit more help, then the post it is based on.

---

### Post by distroman on 2006-08-28
> **Metroid48 said:**
> Hey, so is fixmbr stable enough or could it actually destroy my Windows install?
I had to use “fixboot” because I was so clever, that I installed grub on my NTFS partition. If you have done nothing else, then follow this howto, you should not worry about any of these commands.
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
> FIXBOOT
fixboot drive name:
Use this command to write the new Windows boot sector code on the system partition. In the command syntax, drive name is the drive letter where the boot sector will be written. This command fixes damage in the Windows boot sector. This command overrides the default setting, which writes to the system boot partition. The fixboot command is supported only on x86-based computers.

FIXMBR
fixmbr device name
Use this command to repair the MBR of the boot partition. In the command syntax, device name is an optional device name that specifies the device that requires a new MBR. Use this command if a virus has damaged the MBR and Windows cannot start.

Warning This command can damage your partition tables if a virus is present or if a hardware problem exists. If you use this command, you may create inaccessible partitions. We recommend that you run antivirus software before you use this command.

You can obtain the device name from the output of the map command. If you do not specify a device name, the MBR of the boot device is repaired, for example:
fixmbr \device\harddisk2
If the fixmbr command detects an invalid or non-standard partition table signature, fixmbr command prompts you for permission before rewriting the MBR. The fixmbr command is supported only on x86-based computers.
Hope it workes out for you.

---

### Post by cpslim7626 on 2006-08-28
[FONT="Trebuchet MS"][/FONT] i get a grub error sayiing /boot/grub/message.ubugrey is to large

---

### Post by spockrock on 2006-08-28
that happens when you message file is too large, it has to be below 170K i believe.

---

### Post by Matrixy on 2006-08-29
Will GfxBoot work on 64bit amd?
i saw here only i386 version.

---

### Post by lepre on 2006-08-30
> **ciscosurfer said:**
> 6. **Enter the following GRUB commands** (use [COLOR=Red]sudo fdisk -l[/COLOR] to find out where your Ubuntu drive/partition is located...mine happens to be on [COLOR=DarkGreen]sda1[/COLOR], so I use that.) Each line is a separate command:```
sudo grub-install /dev/hd*x* ## put your drive values in...mine happens to be [COLOR=DarkGreen]sda1[/COLOR], so I use that

sudo grub

grub> find /boot/grub/stage1  ## use the output of this to fill in the following values...output will look like this (hd*x,y*) ... mine is (hd1,0)

grub> root (hd*x*,*y*)  ## put your values in here from previous step ... I put in (hd1,0) here including the parentheses

grub> setup (hd*x*,*y*)  ## put your values in here from previous step ... again, I use (hd1,0)

grub> quit

Save all open files, close out, reboot.  I like to use [COLOR=Red]sudo reboot[/COLOR] b/c it's quick...but be sure to save any open file(s) and close out programs before you do this!
```

this fixed!

you should add in the first post that grub-install is necessary!

---

### Post by fishonadish on 2006-09-06
> **cpslim7626 said:**
> [FONT="Trebuchet MS"][/FONT] i get a grub error sayiing /boot/grub/message.ubugrey is to large

Hi,
I'm having trouble getting an acceptable filesize when making a message file.

I've been trying to edit the suse one.
The original message.suse is 125KB, but when I edited the images and archived it I got twice that.

It seems if I extract and then compress the suse one without editing it at all, I get a file of 250KB or so.

I did the following.


> :~/temp$ cpio -i < message.suse
250 blocks
:~/temp$ rm message.suse
:~/temp$ ls . |cpio -o > message.suse
cpio: File message.suse grew, 123392 new bytes not copied
491 blocks

There aren't any other files in the folder to begin with, and I did delete the message.suse before re-archiving (which was my first thought).

Anyone any idea what I'm doing wrong here?
Why is it going from 250 to 491 blocks?

Any help would be greatly appreciated.

Fishonadish


Update: In case anyone else makes this error, the resulting archive did contain a copy of itself, which is why it was double the size.  The solution was to output to another directory (i.e. cpio -0 > /another/dir/message.suse).  Not sure why this happens...anyone able to explain?

Fishonadish

---

### Post by Average Joe on 2006-09-08
Ok. The Gfxboot kind of works for me. But I still have some questions I hope somebody can answer.

1) Why doesn't gfxboot work with the grub that comes with Ubuntu? Gfxboot shows up as a package in Synaptic, saying that it is suitable for grub. But apparently not the default grub. I find that strange. Why the need for an integrated grub/gfxboot package if both grub and gfxboot are available in Synaptic?

2) Is it possible to fully customize the message? I mean not only play around with the images, but also their positions on the screen, and the position where the boot entries are shown. I guess one would need the source code of the message then and compile the message yourself. Where can I get the source code of any message? Or don't I need it?

I hope some wizard knows more about this, and is willing to share some of his infinite wisdom with me, and other forum members of course.

---

### Post by 3rr0r on 2006-09-12
tagged for later reading.

---

### Post by NewbieLearnLinux on 2006-09-13
> **PingunZ said:**
> Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one ;) 
Ok, let's start

Download the [grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb")
And the [message.suse ]("http://quasarfreak.googlepages.com/message.suse")

First remove your old grub
```
sudo apt-get remove grub
```

Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```

then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded 
```

Then edit your menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced 
```


Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

-- Howto make you own theme --


```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```

Reboot and enjoy ;)
Thanks to Quasar_freak and kno

here are some themes posted in this thread ;) ( ty :KS  )

Light Green generic theme [message.gobo] | [Link](http://ubuntuforums.org/showpost.php?p=1214274&postcount=12) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288)
Dark Brown (Dapper look) generic theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544)
Medium blue kubuntu theme [message.kubuntu] | [Link](http://ubuntuforums.org/showpost.php?p=1234300&postcount=54) | [Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)
Dark grey ubuntu theme [message.ubugrey] | [Link](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717)
Medium brown ubuntu theme [message.ububrown] | [Link](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657)
Light orange ubuntu theme [message.ubu] | [Link](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852)
Red ubuntu theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852)
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746)
White / Grey Snowish generic theme [message.snow] | [Link](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506)
Linspire-style blue kubuntu theme [message.kubu] | [Link](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390)
Old- Grub style dark blue and light blue [message.kubu] | [Link](http://mitglied.lycos.de/atoth/ubuntuusers/message.napo) | [Screenshot ]("http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo.png")
Light blue / grey Xubuntu theme [message.xubu] | [Link](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350)


Grtz PingunZ[/QUOTE]

maybe this is a n00b question, but may I use the other "message" files instead of message.suse and just replace the respective phrase in menu.lst ? 
(instead of "How to make own theme" ? )

---

### Post by Average Joe on 2006-09-13
> **NewbieLearnLinux said:**
> Grtz PingunZ

maybe this is a n00b question, but may I use the other "message" files instead of message.suse and just replace the respective phrase in menu.lst ? 
(instead of "How to make own theme" ? )

Of course. That is what they are for.

---

### Post by Najand on 2006-09-14
I did exactly as explained but still have the old non grapgical Grub menu. Did I made a mistake?

---

### Post by NewbieLearnLinux on 2006-09-14
Thank you, it works like a charm! 

But the message.ubu gave me a warning : "You are about to install a 32-bit app on 64-bit machine" or something like that... whilst the others are fine. And the Ubuntu icon of message.ubu is not animated either -_- , though its colors are very eye-candy to me... 


@Najand: what are your steps ? Remember to move/copy the message.xyz to /boot/grub and add the line "gfxmenu /boot/grub/message.xyz" at the top of the file menu.lst (/boot/grub/menu.lst) AFTER installing successfully GFXgrub.

---

### Post by ciscosurfer on 2006-09-14
@Najand,
Try following my post insead of the OP: [http://ubuntuforums.org/showpost.php?p=1426798&postcount=153](http://ubuntuforums.org/showpost.php?p=1426798&postcount=153)_[]("http://ubuntuforums.org/showpost.php?p=1426798&postcount=153")_

---

### Post by Najand on 2006-09-14
Maybe the reason is that I have two Linux Systems with grub on my computer. I saw  your howto , too, ciscosurfer.
Well, didn't find anything wrong with my installation. I am giving up.

---

### Post by silent_scream on 2006-09-20
well, thnx for the how-to.
the images are very nice!

BUT! I also have a prob...
when grub appears, i see the image,
if i select to boot on ubuntu that's ok,
if i choose to boot in windows it takes me back to grub!!

and when i login to ubuntu, it doesn't mount the windows partition!!
any ideas???

it shows a message:

```
silent@MetallicA:~$ sudo mount /dev/sda1 /media/sda1/ -t ntfs -o umask=0222
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

my dmesg | tail : 

```
[17179838.500000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179838.500000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179838.500000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179838.500000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17179864.724000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17179864.724000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17179866.748000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17179866.748000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17179877.628000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17179877.628000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.



```

any ideas?
it's driving me crazy... :(

---

### Post by gabrielmenini on 2006-10-04
I wans't able to get Grub to load the image located at /boot/grub/message.ubugrey

Grub says can't find the file but the file exists in the correct location and have root:root permission....

What am I doing wrong?

T.I.A.

---

### Post by NoWhereMan on 2006-10-04
maybe yoy have to chmod /boot/grub/message.ubugrey ?
but I can't say :)

bye

---

### Post by veloct on 2006-10-06
No matter what I try I can't get it to work. I've tried all suggestions in this thread and nothing.  I get the message that the "message.<filename> is not in /boot/grub" but it's there.  I dunno.

---

### Post by granjerox on 2006-10-11
can I use it in edgy?

---

### Post by granjerox on 2006-10-17
Nobody has tried to install it in edgy?, I had it in dapper and liked so much, but i'm not an expert so I don't dare to do it by myself.

---

### Post by sorcererx84 on 2006-10-17
I have it working in Edgy. No problems so far.

---

### Post by mhueting on 2006-10-17
Ok, now I'm screwed. I just booted my pc with this gfxmenu config, and I just get a grub prompt. No selection whatsoever anymore. Now what should I enter to just boot my pc? To ubuntu?

Thanks a lot, and I'll try to sort this gfxmenu thing out, because it looks so much better than the consolestyle.

---

### Post by Buhmann on 2006-10-28
Hi, I followed the instructions on page 1, but absolute nothing happens. I got no errors and nothing looked wrong, but my grub is still looking like before. Has anyone an idea what to do? (I'm absolutely new to linux so please don't ask too much of me.

[EDIT]
In fact, there was a little problem:
The command "sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst" (posted on the 2nd site of this thread) deleted my entire menu.lst, so i had to use my backup and edit it on my own. But I can't imagine that this could be a reason for grub not to use the gfxboot ...

---

### Post by linuxnewbie946 on 2006-11-08
[B][SIZE="3"]Hi, I am a Kubuntu Edgy user and however hard I try, I cannot make a "valid" theme for gfxboot. Can anyone tell me why? Here are the facts:

I did this.
```
cpio -i < message.new
```
Did NOT edit the pictures, and did this.
```
sudo rm -rf message.new
sudo ls . |cpio -o > message.new
```
And the file ended up larger than the original and is no longer bootable. Why?[/SIZE][/B]

---

### Post by sag47 on 2006-11-15
> **Footissimo said:**
> Another theme, this time based on [this wallpaper](http://www.gnome-look.org/content/show.php?content=32429).  Again, decompress and stick in /boot/grub then change the first line of /boot/grub/menu.lst to ```
gfxmenu /boot/grub/message.ububrown
``` and reboot.

Again, if someone could do a virtual session for the screenie :) (thanks Kno)

Could you please post the full source of your message compiling.  I'm having trouble editing the SuSE boot source.  It keeps getting errors and the message file won't boot right.
Thanks,
SAM

---

### Post by kvonb on 2006-11-20
Took me a while to get it working on Edgy.  This is why:

```
sudo grub

     grub> find /boot/grub/stage1
     (hdx,y) # this will be the output
     grub> root (hdx,y)
     grub> setup (hdx)
```...is wrong, it should be:

```
sudo grub

     grub> find /boot/grub/stage1
     (hdx,y) # this will be the output
     grub> root (hdx,y)
     grub> setup (hdn)
```..where n=a for first hard  disk, b for second, c for third etc'!

So on my system, where I have only 1 hard disk:

```
sudo grub

     grub> find /boot/grub/stage1
     (hd0,4) # this is my output
     grub> root (hd0,4)
     grub> setup (hda)
```You might want to change the original instructions to save a lot of problems.

All I need now is a nice standard theme for Edgy.

Regards,  Kev :)

---

### Post by Malac on 2006-11-20
> **kvonb said:**
> 
All I need now is a nice standard theme for Edgy.

Regards,  Kev :)
You can have mine if you want.
Nothing fancy, just says Ubuntu Edgy 6.10. :)
[ATTACH]19736[/ATTACH]

---

### Post by n3Cre0 on 2006-11-20
After some struggling and like 7 reboots I got it to work. Thnx looks much nicer now

---

### Post by kvonb on 2006-11-20
[Malac]("http://ubuntuforums.org/member.php?u=84076"): Thanks, I tried it but I just get rubbish text in a text box in the top left corner of the screen!  The background picture is there, but nothing else.

---

### Post by Malac on 2006-11-21
> **kvonb said:**
> [Malac]("http://ubuntuforums.org/member.php?u=84076"): Thanks, I tried it but I just get rubbish text in a text box in the top left corner of the screen!  The background picture is there, but nothing else.
Sorry kvonb, I've been playing with mine and uploaded one with the permissions set wrong or something.
I have uploaded one that definitely works on mine to  my previous post with a screenie.
Hope this helps and sorry again.

---

### Post by Footissimo on 2006-11-21
> **sag47 said:**
> Could you please post the full source of your message compiling.  I'm having trouble editing the SuSE boot source.  It keeps getting errors and the message file won't boot right.
Thanks,
SAM

Hi

I didn't edit the source code - just fiddled with the images within the compressed file until I got what I wanted..sorry.  Early in this thread there are links to a couple of people who have though.

---

### Post by Malac on 2006-11-21
Also my ice-cold look one.
:)
[ATTACH]19741[/ATTACH]

---

### Post by kvonb on 2006-11-23
Thanks Malac, that one works well :)

---

### Post by Malac on 2006-11-23
> **kvonb said:**
> Thanks Malac, that one works well :)
You're Most Welcome. :)

---

### Post by OrganicPanda on 2006-11-23
> **kvonb said:**
> 
... snipped ...
```


sudo grub

     grub> find /boot/grub/stage1
     (hd0,4) # this is my output
     grub> root (hd0,4)
     grub> setup (hda)


```

... snipped ...


I'm running edgy and I have tried all the instructions I can find and I'm still seeing the normal grub screen, no errors, nothing atall. I even tried the above suggestion but when in 'sudo grub' if I give it 'setup (hda)' like the example says to It returns an error, I don't know what's wrong here I've followed all instructions without fault and with 3 different message themes. Any suggestions?

---

### Post by zammi on 2006-11-27
> **kvonb said:**
> Took me a while to get it working on Edgy.  This is why:

```
sudo grub

     grub> find /boot/grub/stage1
     (hdx,y) # this will be the output
     grub> root (hdx,y)
     grub> setup (hdx)
```...is wrong, it should be:

```
sudo grub

     grub> find /boot/grub/stage1
     (hdx,y) # this will be the output
     grub> root (hdx,y)
     grub> setup (hdn)
```..where n=a for first hard  disk, b for second, c for third etc'!

So on my system, where I have only 1 hard disk:

```
sudo grub

     grub> find /boot/grub/stage1
     (hd0,4) # this is my output
     grub> root (hd0,4)
     grub> setup (hda)
```You might want to change the original instructions to save a lot of problems.

All I need now is a nice standard theme for Edgy.

Regards,  Kev :)


I'm on edgy but this method is giving me errors. 

Grub setup of the original method on first post working fine but nothing happens at grub screen (Same old black screen). No error though. I've tried 4 theme files so far without success.

---

### Post by zammi on 2006-11-27
At last managed to get this run on my PC. :-)

I think one important step is missing on the howto on first post.

** Once I installed the new grub packages, I had to run:

grub-install /dev/hdb1 (Where my Edgy installation was on hdb1).

Then followed the main thread for rest of the tasks. Everything working fine now.

---

### Post by WishMaster on 2006-12-02
Can anyone provide a WORKING Edgy how-to ?

---

### Post by n3Cre0 on 2006-12-02
I did it on edgy. Works fine

---

### Post by Malac on 2006-12-02
Okay as a couple of people seem to be getting things mixed up. Here are my commands, this works 100% on Edgy with my theme at post # 194.
```
sudo su [SIZE=1](do not sudo grub)[/SIZE]
grub
grub> find /boot/grub/stage1
** (hd0,1)** # this is my output, yours may be different, you may even get multiples if you've lots of versions of linux.
grub> root (**hd0,1)**
grub> setup **(hd0,1)**
grub> quit
```Back at Normal Prompt do this as well.
```
grub-install /dev/hd**a2**
```Okay the bold bits are where people seem to be getting mixed up.
If you already have a Master Boot Record written, say you have Windows on /dev/hda  (hd0) then /dev/hda1 (hd0,1) will **not** overwrite /dev/hda (hd0) therefore you will still get your old boot.
/dev/hda or hd0 without a number after it will write GRUB to the MBR.
With a number after it, grub will write itself to that partition which needs to be active/bootable to work, use the following tables to check you have the right numbers/letters.

**Drives**```
_Grub_  _Dev_
hd0    hda
hd1    hdb
hd2    hdc
........
```                                              **Partitions**```
_Grub_  _Dev_
   ,0      1
   ,1      2
   ,2      3
.................
```Hope this helps.

---

### Post by iGama on 2006-12-02
How to worked with me on Edgy and Dapper.
Thanks

---

### Post by pavel_kbc on 2006-12-03
grub> grub-install /dev/hda 

Error 27: Unrecognized command

grub> grub-install hd0     

Error 27: Unrecognized command

grub> grub-install /dev/dha9

Error 27: Unrecognized command

grub> grub-install /dev/dha2

Error 27: Unrecognized command

grub> grub-install /dev/dha1

Error 27: Unrecognized command

---

### Post by pavel_kbc on 2006-12-03
whatever i am using edgy and its works for me thank you everyone

---

### Post by lepre on 2006-12-03
> **pavel_kbc said:**
> grub> grub-install /dev/hda 

Error 27: Unrecognized command

grub> grub-install hd0     

Error 27: Unrecognized command

grub> grub-install /dev/dha9

Error 27: Unrecognized command

grub> grub-install /dev/dha2

Error 27: Unrecognized command

grub> grub-install /dev/dha1

Error 27: Unrecognized command

if you change the parameters to an Unrecognized command it still remains an Unrecognized command. try setup instead.

---

### Post by Malac on 2006-12-03
> **lepre said:**
> if you change the parameters to an Unrecognized command it still remains an Unrecognized command. try setup instead.
I think he misread my post:
Back at **Normal Prompt** do this as well.
```
grub-install /dev/hd**a2**
```

---

### Post by Sprite1990 on 2006-12-04
Downloaded the file to my desktop, then:


```
dan@DanLinux:~$ sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
dpkg: error processing grub-gfxboot_0.97-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grub-gfxboot_0.97-5_i386.deb
```

](*,)

---

### Post by WishMaster on 2006-12-05
> **Sprite1990 said:**
> Downloaded the file to my desktop, then:

```
dan@DanLinux:~$ sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
dpkg: error processing grub-gfxboot_0.97-5_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grub-gfxboot_0.97-5_i386.deb
```](*,)

The file is on your desktop, 
in your console, you are in your home-folder.

Type first: cd ~/Desktop
then sudo dpkg -i ....
Or just dubble click the file on your desktop. A graphical installer will take over

---

### Post by WishMaster on 2006-12-05
[COLOR=Black]**_Step1:_**
download [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

**_Step2:_**
Download a 'theme'. See the [first post]("http://ubuntuforums.org/showpost.php?p=1212505&postcount=1") for this.

**_Step3:_**
Remove the old GRUB.
Open a terminal and type:[/COLOR]
[COLOR=Blue]    sudo apt-get remove grub

[COLOR=Black]**_Step4:_**
Install gfxboot. Find the downloaded .deb and dubbleclick it. A graphical installer will take over.

**_Step5:_**
We are going to move the 'theme' we just downloaded.
Open a terminal, cd to the folder where you downloaded the theme and type:
   [COLOR=Blue]sudo cp message.suse /boot/grub/ [/COLOR]
[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]Offcourse "message.suse" can be replaced by the one you downloaded

**_Step6:_**
Backup menu.lst and edit the original to use gfxboot.
 [COLOR=Blue]  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
   sudo gedit /boot/grub/menu.lst[/COLOR]
This will open up a textfile. 
Insert a new first line that says:
[COLOR=Blue]   gfxmenu /boot/grub/message.suse [/COLOR]
Once again: the message.suse can be replaced

[B][U]Step7:
[/U][/B][COLOR=Blue]   sudo su
   grub
[/COLOR]Now you are in the "grub-console".
grub> [COLOR=Blue]find /boot/grub/stage1[/COLOR]
 (hd0,1) # this is my output, yours may be different, you may even get multiples if you've lots of versions of linux.
grub> [COLOR=Blue]root (hd0,1)[/COLOR]
grub> [COLOR=Blue]setup (hd0,1)[/COLOR]
grub> [COLOR=Blue]quit

[COLOR=Black]Now we are back in the normal console.
Just 1 more command to go...
take a look at the output. it has the form: (hd[COLOR=Red]**x**[COLOR=Black],[/COLOR]**y**[/COLOR])
_the x: _
0 =a
1 = b
2 = c
....

   [COLOR=Blue]grub-install /dev/hd[COLOR=Red]**xy**[/COLOR][/COLOR]

_An example_: 
*) if your output was (hd0,1) then what you have to type is:[/COLOR][/COLOR][/COLOR][/COLOR]*[COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black] grub-install /dev/hda1[/COLOR][/COLOR][/COLOR][/COLOR]*
[COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]*) [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]if your output was (hd1,6) then what you have to type is:[/COLOR][/COLOR][/COLOR][/COLOR][I][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black] grub-install /dev/hdb6

[/COLOR][/COLOR][/COLOR][/COLOR][/I][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]Get the idea?

**_Step8:_**
reboot and enjoy your gfxboot :)
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by touchlikefire on 2006-12-05
Even though I've followed the initial directions about 4 times, and the modified directions found in the replies another 4 times, I still cannot get gfxboot at the boot screen.  Instead, I'm left with the old grub plaintext boot experience.

I've read through page 16 of this forum, and I haven't come across anything that has helped my problem.  I could be wrong, but from my analysis it seems the problem is with the **menu.lst** configuration.  Since there are a *lot* of us out there with this problem, and I think it would be helpful to devote some time to figuring it out, and then posting the fix once it is solved.

To be clear, the line **gfxmenu /boot/grub/message.wxyz** is what I think is the culprit.  I've placed it all around **menu.lst** and it has had no effect.  But...maybe it's not the problem?  I don't know.  I'm still a novice, so someone please help me.

Here is my **menu.lst**:```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
#default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2f041292-5ad0-4af3-aa8e-4a7af2bac539 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash resume=/dev/hda5

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## ## End Default Options ##

##splashimage=(hd0,0)/grub/splash.xpm.gz
gfxmenu		/boot/grub/message.snow
default		saved
timeout		8

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=UUID=2f041292-5ad0-4af3-aa8e-4a7af2bac539 ro quiet splash resume=/dev/hda5
initrd		/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=UUID=2f041292-5ad0-4af3-aa8e-4a7af2bac539 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```  Oh, and my grub is on hda1, not the MBR.

---

### Post by WishMaster on 2006-12-05
put "*gfxmenu /boot/grub/message.snow*" as the very first line in menu.lst

---

### Post by Malac on 2006-12-05
touchlikefire
As WishMaster says,
```
 gfxmenu        /boot/grub/message.snow
```should be the very first line before the 
```
 # menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
```Then in terminal
```
sudo su 
grub
```At GRUB prompt
```
grub> find /boot/grub/stage1
(hd0,0) # this will be your output.
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```Then back at Terminal prompt :
```
grub-install /dev/hda1
```If this doesn't work then you have overwritten your MBR without realising, in which case you need to switch/recover it.
I see you are running XP on the other partition so run Windows Recovery Console or live with the MBR being GRUB and change the last command to :
```
grub-install /dev/hda
```

---

### Post by touchlikefire on 2006-12-05
Thanks, I got the grub installation portion to proceed without errors; I don't know why I got something different when I tried it myself.

However, when I rebooted I got a grub prompt and nothing else (so I root (hd0,0) and setup (hd0,0) again) and now whenever I reboot I get the message "gfx failed to load image, cannot find /boot/grub/message.snow" even tho I checked and it's in there.

Thoughts?

---

### Post by Malac on 2006-12-06
> **touchlikefire said:**
> Thanks, I got the grub installation portion to proceed without errors; I don't know why I got something different when I tried it myself.

However, when I rebooted I got a grub prompt and nothing else (so I root (hd0,0) and setup (hd0,0) again) and now whenever I reboot I get the message "gfx failed to load image, cannot find /boot/grub/message.snow" even tho I checked and it's in there.

Thoughts?
This may mean the image file is too big for your system or the main file is corrupt.
Try downloading a simple known good file and use that one, like the plain message.suse one, for now until you've got it working.

---

### Post by touchlikefire on 2006-12-08
If you've followed all the steps in this tutorial properly, yet when you reboot your system you receive an error stating "*cannot find image /boot/grub/message.wxyz press any key to continue...*", do this:

Open **/boot/grub/menu.lst** in your favorite text editor and replace the line```
gfxmenu /boot/grub/message.wxyz
``` with ```
gfxmenu **(hdq,p)**/grub/message.wxyz
``` where **message.wxyz** is the name of the image file (eg - message.suse) and **'q'** and **'p'** are the hard drive a partition location, in grub format (eg - (hd0,0) for first hdd, partition 1).

---

### Post by jsteve54302 on 2006-12-08
> **tlaloczint said:**
> Then edit your menu.lst
```
sudo gedit /boot/grub/menu.lst
```and make it use gfxboot
```
gfxmenu /boot/grub/message.suse
```ok how do I do that? 

tlaloc@aztlan:~$ gfxmenu /boot/grub/message.suse
bash: gfxmenu: command not found
tlaloc@aztlan:~$

do I missing something here?

Ok...  don't know why nobody seems to have answered this...  Here goes:

The instructions were, well, a bit vague (technically, you did follow them to the letter :) )
Instead of typing the line starting with "gfxmenu" on the command line, you need type it in the first line of the text editor brought up by the command starting with "sudo gedit" and press enter so that that's the only thing on that line.  Then save and exit. the text editor.  

Oh, and a note to everyone:  If the program you're using doesn't stay in the terminal you launch it from, *please* use gksudo instead of sudo.  Using sudo for the wrong GUI program **can break your system** if it breaks the pipe when it asks for your password (say, when you put '&' at the end of a command to create a new program thread and therefore be able to continue using the terminal).  *Esp.* when messing around with things like boot loader configs...  Thank you...  <edit>For Kubuntu users:  Use kdesu instead of gksudo</edit>

---

### Post by jsteve54302 on 2006-12-09
> **Malac said:**
> 
                                                                           Originally Posted by **touchlikefire**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=1850115#post1850115")                 
                 > [I]Thanks, I got the grub installation portion to proceed without errors; I don't know why I got something different when I tried it myself.

However, when I rebooted I got a grub prompt and nothing else (so I root (hd0,0) and setup (hd0,0) again) and now whenever I reboot I get the message "gfx failed to load image, cannot find /boot/grub/message.snow" even tho I checked and it's in there.

Thoughts?[/I]
                                 
  This may mean the image file is too big for your system or the main file is corrupt.
Try downloading a simple known good file and use that one, like the plain message.suse one, for now until you've got it working.
This may mean the image file is too big for your system or the main file is corrupt.
Try downloading a simple known good file and use that one, like the plain message.suse one, for now until you've got it working.

This may just be the location of your message.wxyz file(s).  Another poster earlier (I believe it was Bohboh) pointed out that, if you're /boot is actually a seperate partition mounted on a /boot directory, rather than a simple directory, you may have to remove /boot from the gfxboot path (i.e., 

```
gfxboot /grub/message.snow
```instead of 
```
gfxboot /boot/grub/snow
```).  This is the case on my system, which has /dev/sdb1 mounted on the /boot directory in /dev/sdb5.  This is because the /boot directory does not actually exist on the boot partition - the boot files are in the / directory, and the grub files in /grub.  Hope this helps :)

---

### Post by jsteve54302 on 2006-12-09
> **Jolly Roger said:**
> I have been trying to get this tutorial to work for me for a while now. I've done and redone each step of the tutorial many times. The only thing I think that I may be doing wrong is putting the line "gfxmenu /boot/grub/message.blusplash" in the wrong place in my menu.lst file. <snip>



Two ideas:
1:  My gfxboot refuses to even look for a message file unless unless the gfxboot line is the very first one in menu.lst (i.e., it goes straight to standard grub with no errors). before any automagic lines/comments.
2:  If grub/gfxboot tells you it can't find the message file, check my last post (post #227, on page#23).

---

### Post by Zeek00 on 2006-12-11
when you type  

```
sudo gedit /boot/grub/menu.lst
```

What should you edit if anything at all?

When I go onto the next step, and type

```
gfxmenu /boot/grub/message.ubugrey
```

I get this error kicked back to me...

```
bash: gfxmenu command not found.
```

---

### Post by Malac on 2006-12-12
@Zeek00
```
sudo gedit /boot/grub/menu.lst
```Then whilst you are in the file menu.lst in gedit insert the line; 
```
 gfxmenu /boot/grub/message.ubugrey
```at the top of that file not in the terminal.

---

### Post by hvdhvd on 2006-12-15
> **silent_scream said:**
> well, thnx for the how-to.
the images are very nice!

BUT! I also have a prob...
when grub appears, i see the image,
if i select to boot on ubuntu that's ok,
if i choose to boot in windows it takes me back to grub!!

and when i login to ubuntu, it doesn't mount the windows partition!!
any ideas???

it shows a message:

```
silent@MetallicA:~$ sudo mount /dev/sda1 /media/sda1/ -t ntfs -o umask=0222
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

my dmesg | tail : 

```
[17179838.500000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179838.500000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179838.500000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179838.500000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17179864.724000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[17179864.724000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[17179866.748000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17179866.748000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17179877.628000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17179877.628000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.



```

any ideas?
it's driving me crazy... :(


i have this exactly problem, what to do?? any help please

---

### Post by Malac on 2006-12-15
> **hvdhvd silent_scream said:**
> i have this exactly problem, what to do?? any help please
Sounds like you've both blown the boot record for sda1. It may help to run fixboot and/or fixmbr from Windows Recovery Console.

---

### Post by hvdhvd on 2006-12-15
> **Malac said:**
> Sounds like you've both blown the boot record for sda1. It may help to run fixboot and/or fixmbr from Windows Recovery Console.

didnt help, couldnt find ntldr etc. so
i got the important data from it with Getdataback and got rid of the M$ at all, now installing ubuntu on the whole disk. thx for trying to help

---

### Post by Ben Sprinkle on 2006-12-15
Cool, it possible to make your own themes from png wallpapers?

---

### Post by ptitpoul on 2006-12-20
I posted on the french Ubuntu forum some tips to modify colors and languages of gfxboot themes : [http://forum.ubuntu-fr.org/viewtopic.php?pid=625301#p625301]("http://forum.ubuntu-fr.org/viewtopic.php?pid=625301#p625301"). I haven't seen these tips on this forum, so if someone find this interesting I (or someone else) can traduce the main thing.

---

### Post by Gurgeh on 2006-12-21
Guys, remember that if you have a SATA HD to run:
 
grub-install [COLOR=red]sd[/COLOR]a (in my case)
 
Had me bloody stumped for ages...

---

### Post by se0siris on 2006-12-29
Is there any way to disable the 64bit check?

I'm running on a 32bit system, but each time GfxBoot loads on boot I get an annoying dialog telling me I'm trying to install 32bit software on a 64bit system. Which I'm not, but the dialog goes away and lets me choose an entry fine if I hit enter.

But I don't *want* to have to hit enter. I'd like to be able to leave my computer start up without hanging around to press buttons to make it boot :-/

---

### Post by Abaddon on 2007-01-05
I usually have my Grub menu hidden by default - with the hiddenmenu option, so unless I hit escape during startup, my computer will automatically load Ubuntu.

Does this work with GFX grub?   ie - press escape to show GRUB then brings up the graphic screen?

This would be very nice.

Cheers,

---

### Post by Rinzwind on 2007-01-07
I did everything in de 1st post plus a
sudo grub-install hd0

Used message.ubugrey

and changed 1 thing extra in the menu:
the text ' (recovery mode)' I changed into ' recovery' so the text isn't cut off.

It all worked 100% perfectly.

Thanks :)

---

### Post by deki999 on 2007-01-27
it's not working for me!!!

---

### Post by Jarn on 2007-01-29
Does the package 'gfxboot' that can be apt-get do this? Or if not, what is that? And removing grub won't be bad, will it? It will keep my menu.lst file and stuff? And where in menu.lst do I put the line for the gfxmenu?

---

### Post by Jarn on 2007-01-30
I followed the instructions, but it didn't seem to work. I still have the normal grub menu. And I did add the gfxmenu line into my menu.lst. Maybe I didn't put it in the right place? I didn't know where to put it so I put it at the very top.

---

### Post by Malac on 2007-01-31
> **Jarn said:**
> I followed the instructions, but it didn't seem to work. I still have the normal grub menu. And I did add the gfxmenu line into my menu.lst. Maybe I didn't put it in the right place? I didn't know where to put it so I put it at the very top.
```
sudo grub
```Then at grub prompt:
```
grub> find /boot/grub/stage1
```copy+paste the results here.

And in normal terminal the results of ```
df
```

---

### Post by Jarn on 2007-01-31
> **Malac said:**
> ```
sudo grub
```Then at grub prompt:
```
grub> find /boot/grub/stage1
```copy+paste the results here.

And in normal terminal the results of ```
df
```

(hd0,2)

And.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             41540528  31222812   8207580  80% /
varrun                  517776       144    517632   1% /var/run
varlock                 517776         4    517772   1% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                  517776         0    517776   0% /dev/shm
lrm                     517776     17580    500196   4% /lib/modules/2.6.17-10-generic/volatile

---

### Post by TrendyDark on 2007-01-31
I've done all the steps listed, but when I reboot I just see the normal Grub screen. . . 

What's going on here?

I thought at first it wasn't working because the file had incorrect permissions, but after chmoding the file to 777, i still have no graphical grub screen.

---

### Post by Malac on 2007-01-31
> **Jarn said:**
> (hd0,2)

And.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             41540528  31222812   8207580  80% /
varrun                  517776       144    517632   1% /var/run
varlock                 517776         4    517772   1% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                  517776         0    517776   0% /dev/shm
lrm                     517776     17580    500196   4% /lib/modules/2.6.17-10-generic/volatile

TRY:
```
sudo grub
```at the grub prompt
```
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit
```Then do the following command as well.
```
 sudo grub-install /dev/hda3
```You may also like to check that /dev/hda3 is bootable/active.
You can use gparted or sudo fdisk -l to find this out.

Also make sure you have a theme file that you know hasn't got too large a graphic in it, etc.

Hope this helps.

---

### Post by haani on 2007-02-01
thanks!! works perfectly fine here also had to do sudo grub-install /dev/sda5 (where sda5 is the name of ur linux active drive)

---

### Post by Jarn on 2007-02-01
> **Malac said:**
> You may also like to check that /dev/hda3 is bootable/active.
You can use gparted or sudo fdisk -l to find this out.What part of the output of sudo fdisk -l tells me if it's bootable? Note, grub is on hda3 and it runs fine. Doesn't that mean it's bootable?

EDIT: Nvmd, after I did "sudo grub-install /dev/hda3" it works. Thanks!

---

### Post by Malac on 2007-02-02
> **Jarn said:**
> What part of the output of sudo fdisk -l tells me if it's bootable?
For future reference here is my output, the * under Boot is next to the bootable partition.
```
[SIZE=1]Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1567    12586896    c  W95 FAT32 (LBA)
/dev/hda2   *****        1568        3587    16225650   83  Linux
/dev/hda3            3588        3736     1196842+   5  Extended
/dev/hda5            3588        3736     1196811   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *****           1        3961    31816701    c  W95 FAT32 (LBA)
/dev/hdb2            3962        5266    10482412+  83  Linux
/dev/hdb3            5267        8138    23069340   83  Linux
/dev/hdb4            8139       24792   133773255    f  W95 Ext'd (LBA)
/dev/hdb5            8139       12315    33551721    b  W95 FAT32
/dev/hdb6           12316       16492    33551721    b  W95 FAT32
/dev/hdb7           16493       20669    33551721    b  W95 FAT32
/dev/hdb8           20670       24585    31455238+   b  W95 FAT32
/dev/hdb9           24586       24792     1662696   82  Linux swap / Solaris[/SIZE]
```

---

### Post by ESPOiG on 2007-02-02
ok this seems to be common, it not working as it should and so... but this is how i did it everytime and everytime it worked fine

> 
1. sudo apt-get remove grub
2. sudo dpkg -i gfxgrub-package.deb #this is the package that you download
3. sudo cp message.suse /boot/grub/message.suse
4. sudo nano /boot/grub/menu.lst
add this line "gfxmenu /boot/grub/message.suse" to the top
5. sudo grub
6. find /boot/grub/stage1
you should get output like this
(hdx,y)
7. quit
8. sudo grub-install /dev/hdx #this is from your output
9. sudo grub
10. root (hdx,y) #from your output


now reboot your computer and it should be there :D, this works for me everytime so i dunno why it would work for you, reply if it dont work for you

ESPOiG

---

### Post by celettu on 2007-02-05
Worked, but this didn't: 

```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

Like many others I had to use grub-install.

---

### Post by Malac on 2007-02-06
> **celettu said:**
> Worked, but this didn't: 

```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```Like many others I had to use grub-install.
This wouldn't work unless your Ubuntu is on the first partition of (hdx).
The setup command should be the same as the root command in this case :
```
grub> setup (hdx**,y**).
```And of course grub to be run using ```
sudo grub
```

---

### Post by ESPOiG on 2007-02-06
just read how i did it and it will work fine :D promise ^ 3 posts up

---

### Post by Nikron on 2007-02-06
Thanks for the howto worked after I used the option

Default 0


and took the rest out 'cept the countdown and gfxmenu

Had to use grub-install too

---

### Post by raul_ on 2007-02-08
Kudos.

Awesome!

---

### Post by raul_ on 2007-02-08
Oops. Double post. Don't know how that happened =\ sorry

---

### Post by Beastboy26 on 2007-02-10
> **WishMaster said:**
> [COLOR=Black]**_Step1:_**
download [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

**_Step2:_**
Download a 'theme'. See the [first post]("http://ubuntuforums.org/showpost.php?p=1212505&postcount=1") for this.

**_Step3:_**
Remove the old GRUB.
Open a terminal and type:[/COLOR]
[COLOR=Blue]    sudo apt-get remove grub

[COLOR=Black]**_Step4:_**
Install gfxboot. Find the downloaded .deb and dubbleclick it. A graphical installer will take over.

**_Step5:_**
We are going to move the 'theme' we just downloaded.
Open a terminal, cd to the folder where you downloaded the theme and type:
   [COLOR=Blue]sudo cp message.suse /boot/grub/ [/COLOR]
[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]Offcourse "message.suse" can be replaced by the one you downloaded

**_Step6:_**
Backup menu.lst and edit the original to use gfxboot.
 [COLOR=Blue]  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
   sudo gedit /boot/grub/menu.lst[/COLOR]
This will open up a textfile. 
Insert a new first line that says:
[COLOR=Blue]   gfxmenu /boot/grub/message.suse [/COLOR]
Once again: the message.suse can be replaced

[B][U]Step7:
[/U][/B][COLOR=Blue]   sudo su
   grub
[/COLOR]Now you are in the "grub-console".
grub> [COLOR=Blue]find /boot/grub/stage1[/COLOR]
 (hd0,1) # this is my output, yours may be different, you may even get multiples if you've lots of versions of linux.
grub> [COLOR=Blue]root (hd0,1)[/COLOR]
grub> [COLOR=Blue]setup (hd0,1)[/COLOR]
grub> [COLOR=Blue]quit

[COLOR=Black]Now we are back in the normal console.
Just 1 more command to go...
take a look at the output. it has the form: (hd[COLOR=Red]**x**[COLOR=Black],[/COLOR]**y**[/COLOR])
_the x: _
0 =a
1 = b
2 = c
....

   [COLOR=Blue]grub-install /dev/hd[COLOR=Red]**xy**[/COLOR][/COLOR]

_An example_: 
*) if your output was (hd0,1) then what you have to type is:[/COLOR][/COLOR][/COLOR][/COLOR]*[COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black] grub-install /dev/hda1[/COLOR][/COLOR][/COLOR][/COLOR]*
[COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]*) [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]if your output was (hd1,6) then what you have to type is:[/COLOR][/COLOR][/COLOR][/COLOR][I][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black] grub-install /dev/hdb6

[/COLOR][/COLOR][/COLOR][/COLOR][/I][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]Get the idea?

**_Step8:_**
reboot and enjoy your gfxboot :)
[/COLOR][/COLOR][/COLOR][/COLOR]

I followed these steps up to the point where you use the command 

grub-install /dev/hda2 #hda2 is what i got from the grub> [COLOR=Blue]find /boot/grub/stage1[/COLOR]

instead i had to use

grub-install /dev/sda

beause i have a serial ATA hdd ??? anyways it worked ... except for one minor inconvenience... when i try to boot into windoze xp , it just loops back to the grub menu.... any ideas?

---

### Post by Malac on 2007-02-11
> **Beastboy26 said:**
> I followed these steps up to the point where you use the command 

grub-install /dev/hda2 #hda2 is what i got from the grub> [COLOR=Blue]find /boot/grub/stage1[/COLOR]

instead i had to use

grub-install /dev/sda

beause i have a serial ATA hdd ??? anyways it worked ... except for one minor inconvenience... when i try to boot into windoze xp , it just loops back to the grub menu.... any ideas?
You should have done ```
grub-install /dev/sda**2**
```You've over-written the Windows boot code. You need to run the fixboot/fixmbr fix from the recovery console.

---

### Post by frying_fish on 2007-02-28
I have recently just tried this gfxboot, I have gotten it to the stage where it is installed and will attempt to load.  But for some unknown reason, no matter what I try and reference the message files as it refuses to load them, saying the file is missing.

Either trying the /boot/grub/message.suse  (for suse message in this case) or (hd0,1)/grub/message.suse (as sugessted earlier in the thread) fails to work,  I still get the "graphics file FOO missing" error

any help is appreciated

---

### Post by rei_t_ex on 2007-03-03
Followed the instructions in the first post verbatim.  When doing:

```
grub> find /boot/grub/stage1
 (hd0,0) # this was returned so I did:
grub> root (hd0,0)
grub> setup (hd0)
```

Everything went without a problem but when I rebooted, I got the same old GRUB.

Read further down the thread and saw bohboh having the same problem.  Trying to follow the resolution ran:

```
sudo fdisk -l
```

and got something along the lines of 

```
   Device    Boot      Start         End      Blocks      Id    System
/dev/sda1     *           1         ****    *******     83    Linux
/dev/sda2               ****       ****    *******      5    Extended
/dev/sda5               ****       ****    *******    82    Linux swap / Solaris
```

Entered GRUB from the terminal again and tried:

```
grub> root (sda,1)

   Error 23: Error while parsing number

grub> root (sda1,0)

   Error 23: Error while parsing number
```

So I figured that this part was fine as per original instructions, and back in the terminal entered:

```
sudo grub-install /dev/sda1
```

It returned a message saying something to the extent of "installation was successful, no errors returned".

Then I rebooted again, only to find 

```
GRUB Loading stage1.5.

GRUB loading. please wait...
```

And the system HANGS!!!

This is my first foray into Linux from the Apple world (I installed Ubuntu on an old laptop about a week ago), so perhaps I have done something very stupid.  Any help would be much appreciated.  I hope that I did not just kill the system completely...


[B]Edit1
----------------------------------[/B]
Booted from my LiveCD, mounted the partition and restored the backed-up menu.lst.  No effect on the problem - system still hangs at boot.


[B]Edit2
----------------------------------[/B]
Booted from LiveCD and restored GRUB as per [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).  Still no luck.

---

### Post by Fabioamd87 on 2007-03-10
hi, is possible to use the theme in the repositories of ubuntu edgy?

how to change for example the suse theme in the ubuntu theme?

---

### Post by kvonb on 2007-03-28
Anyone tried this on Feisty yet?  I'm having a rather odd problem in that Feisty doesn't seem to know what my hard disk is!

Grub reports it as /dev/hda and fdisk thinks it's /dev/sda!

Subsequently I cannot perform a grub-install as each device lists as  "Not found or not a block device."

Very odd :confused:.

---

### Post by Fabioamd87 on 2007-03-28
Feisty can't have it by default? :(

---

### Post by tuxbear on 2007-03-28
Can I get install GfxBoot on a AMD64 ??? All packages they I found are for i386 infrastructure.
It isn't possible to install that with dpkg.

I installed gfxboot with synaptic, but I don't know what's that.:confused:

---

### Post by kvonb on 2007-03-28
> **Fabioamd87 said:**
> Feisty can't have it by default? :(

That would look too nice!  Feisty is nearly the same as Edgy, I expect most of the work is "under the hood" stuff.

It's a bit disappointing so far, well in looks anyway :(.

> **tuxbear said:**
> Can I get install GfxBoot on a AMD64 ??? All packages they I found are for i386 infrastructure.
It isn't possible to install that with dpkg.

-------------------------------------------------------------------------------------------------------------
I installed gfxboot with synaptic, but I don't know what's that.:confused:

I wouldn't think the boot process (at that early stage) would be in 64bit mode.  Maybe try it and see what happens, just make sure you have your Ubuntu CD ready in case of didaster :).

The gfxboot package in synaptic seems to be an editor or creator for the message. files or something.  I installed it then removed it again thinking it was the actual boot loader, but it isn't.

---

### Post by joker806 on 2007-03-28
> **tuxbear said:**
> Can I get install GfxBoot on a AMD64 ??? All packages they I found are for i386 infrastructure.
It isn't possible to install that with dpkg.

I installed gfxboot with synaptic, but I don't know what's that.:confused:

I found [**this**]("http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb"), installed according to first post, but still have the same old black&white grub :( .

---

### Post by el mariachi on 2007-03-28
```
sudo 
grub  grub> find /boot/grub/stage1
 (hdx,y) # this will be the output 
grub> root (hdx,y) 
grub> setup (hdx)
```

after inputing the first command (find) i get this

```
grub> find /boot/grub/stage1

Error 15: File not found

```

is it another stage? Grub shows, at startup, two different Ubuntu versions (different Kernels) a Memtest+ ubuntu and my Windows Xp.

---

### Post by Malac on 2007-03-28
> **el mariachi said:**
> ```
sudo 
grub  grub> find /boot/grub/stage1
 (hdx,y) # this will be the output 
grub> root (hdx,y) 
grub> setup (hdx)
```after inputing the first command (find) i get this

```
grub> find /boot/grub/stage1

Error 15: File not found

```is it another stage? Grub shows, at startup, two different Ubuntu versions (different Kernels) a Memtest+ ubuntu and my Windows Xp.

That happens if you have just run grub without sudo.
The command should be all on one line ```
sudo grub
```then
```
grub> find /boot/grub/stage1
..................
```I also recommend running:```
sudo grub-install /dev/hd-- [SIZE=1][COLOR=SlateGray](replacing your hd numbers for the last two dashes)[/COLOR][/SIZE]
```
Afterwards as well as this only worked on my system if I did both.

---

### Post by Jarn on 2007-03-28
Does the package in the first post still have to be used, or can the gfxboot from the repos be installed?

---

### Post by el mariachi on 2007-03-29
hoe can I know what number is my HD?

---

### Post by Xappe on 2007-03-29
hmm, can I get the automagic list to name the kernels Ubuntu * instead of Debian *?

---

### Post by Malac on 2007-03-29
> **el mariachi said:**
> hoe can I know what number is my HD?
```
df -Th
```
or 
```
sudo fdisk -l
``` that's a lowercase L not a digit 1

---

### Post by chinita96 on 2007-03-30
Help! I am new to ubuntu and i've got it working except now I think I messed up when I tried to install the graphical grub i've seen from the pics.

i followed someone's directions for typing in "sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst" in the terminal and it overwrote my entire menu.lst file. the only thing in it right now is gfxmenu /boot/grub/message.suse and when i restarted, it goes to the grub terminal type screen.

basically it restarts and goes to a black screen with:

grub >

that's it. how do i load into my operating system to get my backup file of menu.lst. i made a backup before i started but i am stuck at grub > and can't get out. i tried "quit" and it didn't do anything. if i totally messed up, how would i go about re-installing everything. seems like everything i type, i can't get out of grub >.

what do i do? can someone help? has anyone else got this problem? i tried searching for it but no luck. also, i'm on a loan computer right now since i screwed up mine. whoops.

any help would be appreciated. thanks.
p.s. how do i get the code to show up in a box like the other replies? (sorry for the idiiot question)

---

### Post by chinita96 on 2007-03-31
i figured it out! thanks to everyone else in the ubuntu community who has already posted about re-installing grub through the livecd. that's what i did. after reading many difference threads on the topic i figured out what i needed to do. i popped in my livecd, mounted the drive and edited my menu.lst file to the backup file i had. that solved the problem! i now have the gfxboot working.

if anyone else has the same problem as me, overwriting your menu.lst file, then do what i did. search for reinstalling grub with livecd and you'll find plenty of info. 

anyways, i just wanted to say problem solved!

---

### Post by Xappe on 2007-03-31
Ah, I fixed the problem with update-grub naming the kernels Debian instead of Ubuntu. Just edit the update-grub script by hand (/sbin/update-grub). Look for the line:

# Title
title="Debian"

and change it to

# Title
title="Ubuntu"

---

### Post by Malac on 2007-03-31
> **Xappe said:**
> Ah, I fixed the problem with update-grub naming the kernels Debian instead of Ubuntu. Just edit the update-grub script by hand (/sbin/update-grub). Look for the line:

# Title
title="Debian"

and change it to

# Title
title="Ubuntu"
Thanks, been annoying me for ages.
In case anyone's on Feisty it's moved to the script in /**usr**/sbin/update-grub .

---

### Post by 5ER on 2007-04-02
what about amd64 grub-gfxboot.deb?

And how to use the gxboot package from repositories

---

### Post by kvonb on 2007-04-02
Hey Malac, did you get gfx-boot working on Feisty?  I failed at the grub-install part, something about /dev/hda being /dev/sda now or something odd!

---

### Post by Malac on 2007-04-02
> **kvonb said:**
> Hey Malac, did you get gfx-boot working on Feisty?  I failed at the grub-install part, something about /dev/hda being /dev/sda now or something odd!
Yeah worked fine for me using /dev/sd-- notation.
In my case grub-install /dev/sda2

---

### Post by kvonb on 2007-04-02
OK, here is my dilemma:

```
kev@kev:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         199     1598436   83  Linux
/dev/sda2   *         200        1729    12289725    7  HPFS/NTFS
/dev/sda3            1730        9729    64260000    5  Extended
/dev/sda5            1730        2875     9205213+  83  Linux
/dev/sda6            2876        9673    54604900   83  Linux
/dev/sda7            9674        9729      449788+  82  Linux swap / Solaris
kev@kev:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
kev@kev:~$ 


```This is my grub output:

 ```
GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

grub> 
```Where do I "grub-install" to?

As far as I understand, hd0,4 is the 4th partition on /dev/hda -or- /dev/hd0, but there is no 4th partition!

I'm extremely confused! :confused:, KEv

---

### Post by Malac on 2007-04-02
> **kvonb said:**
> OK, here is my dilemma:

```
kev@kev:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         199     1598436   83  Linux
/dev/sda2   *         200        1729    12289725    7  HPFS/NTFS
/dev/sda3            1730        9729    64260000    5  Extended
/dev/sda5            1730        2875     9205213+  83  Linux
/dev/sda6            2876        9673    54604900   83  Linux
/dev/sda7            9674        9729      449788+  82  Linux swap / Solaris
kev@kev:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
kev@kev:~$ 


```This is my grub output:

 ```
GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

grub> 
```Where do I "grub-install" to?

As far as I understand, hd0,4 is the 4th partition on /dev/hda -or- /dev/hd0, but there is no 4th partition!

I'm extremely confused! :confused:, KEv
(hd0,4) is the fifth partition grub starts at 0, so in your case that's /dev/sda5

---

### Post by kvonb on 2007-04-03
> Malac: (hd0,4) is the fifth partition grub starts at 0, so in your case that's /dev/sda5

Hmm, this is very odd, this is what I get:

```
kev@kev:~$ sudo grub-install /dev/sda5
Password:
/dev/sda5 does not have any corresponding BIOS drive.
kev@kev:~$ 
```

See this is what I don't get, my drive is IDE **not** SATA or SCSI!  It seems they've changed something in the way drives are used now.  The simple old /dev/hdx system has gone and now we have this dev/sdx system, but it doesn't seem to work on my computer.

I get the same thing when using vmware, my CDROM drive has vanished because it's expecting /dev/hdc and it is now /dev/sdx!

Any ideas?

Thanks, KEv :)

---

### Post by ptitpoul on 2007-04-04
> **5ER said:**
> what about amd64 grub-gfxboot.deb?
There is a recent binary package on sidux.com, 0.97-14, for i386 and amd64 : [http://sidux.com/debian/pool/main/g/grub-gfxboot/]("http://sidux.com/debian/pool/main/g/grub-gfxboot/")

---

### Post by Malac on 2007-04-04
> **kvonb said:**
> Hmm, this is very odd, this is what I get:

```
kev@kev:~$ sudo grub-install /dev/sda5
Password:
/dev/sda5 does not have any corresponding BIOS drive.
kev@kev:~$ 
```See this is what I don't get, my drive is IDE **not** SATA or SCSI!  It seems they've changed something in the way drives are used now.  The simple old /dev/hdx system has gone and now we have this dev/sdx system, but it doesn't seem to work on my computer.

I get the same thing when using vmware, my CDROM drive has vanished because it's expecting /dev/hdc and it is now /dev/sdx!

Any ideas?

Thanks, KEv :)
Try :```
sudo grub-install hd0,4
```
This should still work even if they have been playing around with the standard naming conventions. :)

---

### Post by kvonb on 2007-04-04
Thanks for that Malac, however this is what I get:

```
kev@kev:~$ sudo grub-install hd0,4
Password:
/dev/sda5 does not have any corresponding BIOS drive.
kev@kev:~$ 
```

This is driving me nuts, I can't seem to find a logical sequence in all this!

I installed Feisty from the Beta ISO and have done every update since it came out, hopefully it will be resolved soon.

I have a 60 meg update coming down as I type so maybe there is some hope :).

---

### Post by abraxxas on 2007-04-07
i installed it exactly as ya told in the tutorial on page one.. but my grub is still the same

---

### Post by Malac on 2007-04-07
> **abraxxas said:**
> i installed it exactly as ya told in the tutorial on page one.. but my grub is still the same
Did you also try sudo grub-install hdx,x as well.

---

### Post by abraxxas on 2007-04-07
thx now it works perfectly:lolflag:

---

### Post by kvonb on 2007-04-08
> **Malac said:**
> Did you also try sudo grub-install hdx,x as well.

Hey Malac,

Yeah I tried a heap of combinations but keep getting the same thing.

I started another thread asking about this, so I'll link to that as it seems a bit rude to have 2 on the go :)

[http://ubuntuforums.org/showthread.php?t=401840](http://ubuntuforums.org/showthread.php?t=401840)

If you have the time to have a quick look I would be grateful.

Thanks, KEv :)

---

### Post by patrickfromspain on 2007-04-08
Hi there!

I've made my own gfxboot theme. it's very simple, but I think it fits well into ubuntu. Thanks to Footissimo, as I started the theme basing on the one he made ([http://ubuntuforums.org/showpost.php...&postcount=61)](http://ubuntuforums.org/showpost.php...&postcount=61)).

Bellow I attach a photo I've taken (quite bad quality, but you should get the idea) and the background image.

Hope you like it!

---

### Post by andreyvul on 2007-04-09
If you want to compile grub-gfxboot from source, get the grub-0.97 source, patch, and compile:
```

#Get grub
wget http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97.orig.tar.gz
#Get the gfxboot patch
wget http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11.diff.gz
#Get documentation
wget http://kanotix.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot-doc_0.97-11_all.deb

```
```

#Uninstall old grub
sudo apt-get remove grub
#Unpack grub
tar xvf grub-gfxboot_0.97.orig.tar.gz
#cd to unpacked grub source
cd grub-0.97
#patch grub source for gfxboot support
patch -Np1 < gzip -dc ../grub-gfxboot_0.97-11.diff.gz
#compile
./configure
make
sudo make install

```
Then install grub according to the instructions in the first post

---

### Post by Marktrix on 2007-04-11
> **Footissimo said:**
> Another GFXboot theme - this time to go with the blue usplash theme [here](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash) by SilentCacophony.  It's a very basic black background with the glowy logo and lettering from the usplash image.  If anyone likes it, I can do the other colours.

It does not fit exactly :(

i have to edit menu.lst now ok

---

### Post by Io-Loki on 2007-04-12
Hey guys,

tried to get the gfx-splash to work without success.

I removed grub and installed the grub-gfxboot for amd64. After that i added the gfxmenu line to the menu.lst

```
gfxmenu /grub/message.ububrown
```

Guess this is right, cos grubs installed on an extra partition.
Then i did run the commands in grub.

```
grub> find /grub/stage1
find /grub/stage1
 (hd0,0)
grub> root (hd0,0)
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.

```

Worked fine for me too, but if i restart there's no result.

fstab:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123         608     3903795   82  Linux swap / Solaris
/dev/sda3             609       12161    92799472+   5  Extended
/dev/sda5             609        3647    24410736   83  Linux
/dev/sda6            3648        8510    39062016   83  Linux
/dev/sda7            8511       12161    29326626    b  W95 FAT32

```

I use feisty fawn. Does anybody know what i'm doing wrong? I would be thankful if somebody could help.

Greetz, rijndael

---

### Post by Malac on 2007-04-12
@lo-Loki
```
sudo grub-install hd0
```

---

### Post by Io-Loki on 2007-04-13
hi,

ty malac for your reply. but this doesn't work for me. grub-install output tells me that there's an error in the script file.

```
/usr/sbin/grub-install: 272: Syntax error: redirection unexpected

```

I looked up the file, but there apparently no mistake for me.

rijndael

---

### Post by Malac on 2007-04-13
> **Io-Loki said:**
> hi,

ty malac for your reply. but this doesn't work for me. grub-install output tells me that there's an error in the script file.

```
/usr/sbin/grub-install: 272: Syntax error: redirection unexpected

```I looked up the file, but there apparently no mistake for me.

rijndael
try:
```
sudo grub-install /dev/sda1
``` instead

---

### Post by Io-Loki on 2007-04-13
already tried. same error :(

---

### Post by Malac on 2007-04-13
> **Io-Loki said:**
> already tried. same error :(
Okay first try explicit pointer to gfxfile by inserting (hd0,1)/ after the "gfxmenu " line in menu.lst
Sorry if you have already posted these but post with menu.lst and device.map as attachments.

---

### Post by DeeTee on 2007-04-13
> **roe_polak said:**
> Hi... I couldn't get it working by using the "sudo grub"-command because of my sata drives (I think, I'm noob). Instead I had to log in as root and use "grub-install /dev/sda2". First I tried "sudo grub-install /dev/sda2" but this returned a lot of errors and I didn't dare rebooting. I tried root and it installed with no errors. I really liked this feature in Suse, but I like it even more when it serves Ubuntu...

Again, I should note that I only used this method because of my sata drives. As far as I have understood, the folks with IDE drives can use the guide as is.

To gain root-privileges I entered this in the terminal:

sudo passwd root
(set the password)

Here's my "session" from the terminal:

```
def@maskine:/$ sudo grub-install /dev/sda2
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> root (hd0,1)
 Filesystem type is reiserfs, partition type 0x83
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,1)"...  18 sectors are embedde d.
succeeded
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 (hd0,1) (hd0,1)1+ 18 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2
grub> quit


def@maskine:/$ su
Password:
root@maskine/# grub-install /dev/sda2
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
root@maskine:/#
```

Please tell me if any of my conclussions, especially that one about root (and not sudo), is incorrect. My goal is to help anyone having the same problems, not to throw them into even worse trouble. I'm also sorry if any of this has been noted before in this thread, but since the custom themes showed up, it's like the support-asspect in the thread disappeared.

Oh, and do back up your menu.lst. Justin Case...


The device.map is what did it for me.

Thanks a million.

---

### Post by Io-Loki on 2007-04-14
hi,

i reinstalled feisty in 32-bit architecture, because i had problems getting everything to work and in need a running system.
I tried to install grub-gfxboot again and command

```
sudo grub-install /dev/sda1
```

worked. Don't know what the problem was under amd64.
Thanks for your help. :D 

greetz, rijndael

---

### Post by Ireclan on 2007-04-14
> **PingunZ said:**
> Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one ;) 
Ok, let's start

Download the [grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb")
And the [message.suse ]("http://quasarfreak.googlepages.com/message.suse")

First remove your old grub
```
sudo apt-get remove grub
```Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded 
```Then edit your menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced 
```
Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```-- Howto make you own theme --


```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```Reboot and enjoy ;)
Thanks to Quasar_freak and kno

here are some themes posted in this thread ;) ( ty :KS  )

Light Green generic theme [message.gobo] | [Link]("http://ubuntuforums.org/showpost.php?p=1214274&postcount=12") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288")
Dark Brown (Dapper look) generic theme [message.new] | [Link]("http://ubuntuforums.org/showpost.php?p=1239724&postcount=55") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544")
Medium blue kubuntu theme [message.kubuntu] | [Link]("http://ubuntuforums.org/showpost.php?p=1234300&postcount=54") | [Screenshot]("http://files.upl.silentwhisper.net/upload5/gfxboot.jpg")
Dark grey ubuntu theme [message.ubugrey] | [Link]("http://ubuntuforums.org/showpost.php?p=1251236&postcount=61") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717")
Medium brown ubuntu theme [message.ububrown] | [Link]("http://ubuntuforums.org/showpost.php?p=1252317&postcount=63") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657")
Light orange ubuntu theme [message.ubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1254642&postcount=64") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852")
Red ubuntu theme [message.new] | [Link]("http://ubuntuforums.org/showpost.php?p=1265601&postcount=65") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852")
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link]("http://ubuntuforums.org/showpost.php?p=1272301&postcount=71") | [Screenshot]("http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746")
White / Grey Snowish generic theme [message.snow] | [Link]("http://ubuntuforums.org/showpost.php?p=1292317&postcount=84") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506")
Linspire-style blue kubuntu theme [message.kubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1294120&postcount=86") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390")
Old- Grub style dark blue and light blue [message.kubu] | [Link]("http://mitglied.lycos.de/atoth/ubuntuusers/message.napo") | [Screenshot ]("http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo.png")
Light blue / grey Xubuntu theme [message.xubu] | [Link]("http://ubuntuforums.org/showpost.php?p=1297486&postcount=97") | [Screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350")


Grtz PingunZ[/quote]

I have followed this guide to the letter, yet all I see is the regular text GRUB screen. Am I missing something?

---

### Post by Malac on 2007-04-15
> **Ireclan said:**
> 
I have followed this guide to the letter, yet all I see is the regular text GRUB screen. Am I missing something?
Also try ```
sudo grub-install hdx,x
```Please can the OP put this in the first post as an extra step as this has solved a lot of the people on here's problems and I'm getting fed up typing it in. :)

---

### Post by kvonb on 2007-04-15
> **Malac said:**
> Also try ```
sudo grub-install hdx,x
```Please can the OP put this in the first post as an extra step as this has solved a lot of the people on here's problems and I'm getting fed up typing it in. :)

Hahahah, yeah but I bet you're getting fast at typing it though :D

---

### Post by mrfuzzemz on 2007-04-15
> **Malac said:**
> Also try ```
sudo grub-install hdx,x
```Please can the OP put this in the first post as an extra step as this has solved a lot of the people on here's problems and I'm getting fed up typing it in. :)

I agree that it should be included in original post as I had tried so many different things before and nothing else worked. Thanks.

---

### Post by Jolly Roger on 2007-04-15
I like nimes red grub theme but wanted to make it fit with my green desktop so I changed the background from red to green. I figured he wouldn't mind if I reposted his theme in a green version. 

Credit goes to nimes for making the great grub theme in the first place, I just modified it.

---

### Post by mrfuzzemz on 2007-04-15
I don't know how many of you have gfxboot on a widescreen display, but I thought I might ask if anyone has created a theme for widescreen aspect ratio.  Using the regular themes, one will get stretched images so a proportionately correct squished theme must be made they stretches appropriately when used.  As for the stretching of the text, I don't know what can be done.

---

### Post by pingpongboss on 2007-04-16
I'd like to remind everyone to be VERY VERY careful when choosing what to put for the (hdx,y) or (sdx) when installing grub-gfxboot over grub. You can destroy your windows partition very easily, as I have done :( 

This is what you could potentially end up with if you type in the wrong thing:
[[IMG]http://img352.imageshack.us/img352/3997/screenshotvy4.th.png[/IMG]](http://img352.imageshack.us/my.php?image=screenshotvy4.png)

So if you don't feel like having headaches, then either make absolutely certain that your inputs are correct, or just hold off on grub-gfxboot until more documentation and experimentation comes out for it.

and if anyone feels like helping me with my problem please go here [http://ubuntuforums.org/showthread.php?p=2464478](http://ubuntuforums.org/showthread.php?p=2464478)

---

### Post by Ireclan on 2007-04-17
> **Malac said:**
> Also try ```
sudo grub-install hdx,x
```Please can the OP put this in the first post as an extra step as this has solved a lot of the people on here's problems and I'm getting fed up typing it in. :)

You're QUITE SURE it's "hdx,x" and not "hdx,y"?

---

### Post by Malac on 2007-04-18
> **Ireclan said:**
> You're QUITE SURE it's "hdx,x" and not "hdx,y"?
In this instance both "x" stands for a number but yes any substitution would be permissible as they may be different numerical values. :)

---

### Post by ShirishAg75 on 2007-04-18
interesting thread, would have try sometime. There should be a big place though where all the themes are listed

---

### Post by bootsbradford on 2007-04-20
I've installed GfxBoot with the ubugrey theme and it's all working fine and dandy :KS 

In synaptic, I've installed something called **'gfxboot-theme-ubuntu'**. What does it do? How do I get gfxboot to work with it.

---

### Post by u-foka on 2007-05-01
Hy! I trying to make gfxboot work on a fresh feisty install, but it seems i out of luck :S

I done the steps in the first post without any error, bot when i reboted, i only can see the old grub screen...
I read this thread and try anything without succes... The most interesting thing is this error message: > u-foka@u-foka-laptop:~$ sudo grub-install hd0
/dev/sda1 does not have any corresponding BIOS drive.

I can get it with many grub install parameters, tryed: "hd0" "hd0,0" "/dev/sda" "/dev/sda1"

Anyone some ideas?

---

### Post by patrickfromspain on 2007-05-03
I have the same problem on my laptop.. it's a pitty, and I don't think you'll get gfx-boot to work. I have tried running sudo grub, root (hd0,5) setup (hd0) and it works, but gfx-boot won't work..

I have even tried using gfxmenu (hd0,5)/boot/grub/message.ubuntu instead of /boot/grub..

Nothing works..

---

### Post by Neobuntu on 2007-05-04
Why doesn't this work with Feisty?

---

### Post by 4Play on 2007-05-04
Well, like several other ppl, i followed the guide, and nothing happened, same old lame boot screen. I am running Fiesty Fawn on a Toshiba M45-S351 Satellite Laptop. I have installed and uninstalled glxgrub two times, and tried several message.xyz screens, but nothing happens.

Did anyone on Fiesty get this to work? Will try this on my desktop, which is still running Edgy Eft...will probably work there.

Thanks :)

Update: Did not work on the 6.10 desktop installation, nothing happened, just as with the laptop....very weird. The instructions are way too simple 4 mistakes, I got no error messages whatsoever, everything went smoothly, but the black grub screen remains unaltered. And it seems that other ppl got it working on Fiesty...

any ideas on what might possibly be happening here!? Thanks

---

### Post by Ace2016 on 2007-05-05
Not woring in feisty, followed everything perfectly but it just doesn't work, could it be the deb? could someone post instructions on how to compile it from source?

---

### Post by ayoli on 2007-05-05
i confirm that it does not work in Feisty, what a shame :( 
New instructions and/or adapted package would be appreciated
thx.

---

### Post by mrfuzzemz on 2007-05-05
> **ayoli said:**
> i confirm that it does not work in Feisty, what a shame :( 
New instructions and/or adapted package would be appreciated
thx.

I've had it running in Feisty for a while now without a problem.

Uninstall grub > install this deb > edit the menu.lst > put your message file in the appropriate place > use the grub setup (this is all on the first page).

The part that isn't on the first page that made it work is this (which is posted every so often in this thread):

```
sudo grub-install hdx,y
```

with the numbers for the appropriate partition.

I hope this helps!

---

### Post by ayoli on 2007-05-05
lol, i ve just done that and i was back to post the trick also :)
this:
```
sudo grub-install hdx,y
```
should be added in the first post of this thread.

---

### Post by mrfuzzemz on 2007-05-05
> **ayoli said:**
> lol, i ve just done that and i was back to post the trick also :)
this:
```
sudo grub-install hdx,y
```
should be added in the first post of this thread.

Haha! Excellent! Well I'm glad it worked for you. I don't know if the creator of the thread visits back much as I believe it's been suggested before.  It would certainly clear up a lot of confusion, though.

---

### Post by 4Play on 2007-05-05
Thank you 4 the tip, I thought that "sudo grub-install hdx,y" did the same thing as "root (hdx,y) >> setup (hdx)" 

Thanks very much :)

---

### Post by Ace2016 on 2007-05-05
ace@Linux:~$ sudo grub-install hd0,1
/dev/hda2 does not have any corresponding BIOS drive.
ace@Linux:~$

How do i fix this???

[EDIT]

I solved it, i was using the wrong deb :)

---

### Post by 4Play on 2007-05-05
Erm...got another problem...when I was installing gfxgrub on another PC (amd64, sata drive) all went well except the "grub-install" part:

me@Tornado:~/gfx-grub$ sudo grub-install hd1,2
/usr/sbin/grub-install: 272: Syntax error: redirection unexpected

I get this error no matter what I try, even sudo grub-install --help gives the same redirection error...I have uninstalled gfxgrub (sudo apt-get remove grub-gfxboot) and reinstalled it....to no avail.

I am installing grub on the 3d partition of a SATA drive, since grub sees sata drives as hdX, the syntax is, i believe, correct.

---

### Post by mrfuzzemz on 2007-05-05
Be sure to include the parentheses in the appropriate places.  (hd1,2) for example.  Also be sure that the drive you are trying to set up grub on is found when you do:
```
find /boot/grub/stage1
```

(hd1,2) is the 3rd partition on the *second* hard disk. (hd0,2) is the 3rd partition on the *first* hard disk.

---

### Post by 4Play on 2007-05-05
Thanks 4 the quick reply! 

i believe the grub-install command dosent use the ( ). it's just "grub-install hdx,y"

And yes, i need do install it to the 3d partition of the secont drive (according to grub), 
"find /boot/grub/stage1" yields (hd1,2), and the "root (hd1,2) and setup (hd1) do not return errors.
I've even checked the partitions with "geometry (hd1)" / "geometry (hd0)" and "fdisk -l" It seems the problem is with the grub-install command itself :(

especially because the grub-install command should return something with the "grub-install --help", this is written in the grub-install command usage page of the grub manual, instead i get: 

> me@Tornado:~$ grub-install --help
/usr/sbin/grub-install: 272: Syntax error: redirection unexpected


UPDATE: Problem solved, as I had thought, the problem was the .deb package, I uninstalled it and downloaded the package from another site, it's working fine now :)

---

### Post by kvonb on 2007-05-06
> **4Play said:**
> 

UPDATE: Problem solved, as I had thought, the problem was the .deb package, I uninstalled it and downloaded the package from another site, it's working fine now :)


Can you tell us where you got the fixed package please?

.

---

### Post by u-foka on 2007-05-06
Hy!

I googled for "gfxboot deb" and the first match was an other guide...

I downloaded the deb from there, and it works with grub-install command (it's still missing from the guide)

Sorry :$ the link is [http://doc.gwos.org/index.php/GfxBoot]("http://doc.gwos.org/index.php/GfxBoot")

---

### Post by ayoli on 2007-05-06
it's the same guide posted by the same guy : PingunZ 
so it miss the same line : sudo grub-install hdx,y

---

### Post by u-foka on 2007-05-06
I known that, but the deb on that guide working!
(The one on this post wasn't for me :S)

---

### Post by ayoli on 2007-05-07
that was your first download which failed/corrupted the file, because the deb is the same on the two pages (same link [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb) )

---

### Post by u-foka on 2007-05-07
Hmm... This is interesting... How I can download it corrupted but working?

---

### Post by mrfuzzemz on 2007-05-07
It's the same file in the same exact location.  It just so happened that the first time you downloaded it it was corrupted (due to a blip in your connection or something).  The time you downloaded it and it worked (from the same place, because the link goes to the same file on the same server!) it just so happened to go through normally.

---

### Post by lucasvm on 2007-05-07
Hi there!, it works great for me, but i get a message that says: "Cool computer, but, you are running 32bits in a 64bits" or something like that, i got AMD64 Athlon Dual Core, where can i download a package for my pc?

---

### Post by bootmaker on 2007-05-08
Hello!

I tried to install it on my new feisty .. but i've got that errors:

grub> find /boot/grub/stage1

Error 15: File not found

could someone help me?

Grub works fine, but it can't load the message-file ...

Greetz bOOt

---

### Post by Malac on 2007-05-08
> **bootmaker said:**
> Hello!

I tried to install it on my new feisty .. but i've got that errors:

grub> find /boot/grub/stage1

Error 15: File not found

could someone help me?

Grub works fine, but it can't load the message-file ...

Greetz bOOt
looks like you are just entering "grub" instead of "sudo grub"

---

### Post by Neobuntu on 2007-05-09
With Feisty, I followed all posts and new suggestions and this does not work.

Anyone with feisty have this working?

I'm guessing the package is not compatible.

---

### Post by mrfuzzemz on 2007-05-09
> **Neobuntu said:**
> With Feisty, I followed all posts and new suggestions and this does not work.

Anyone with feisty have this working?

I'm guessing the package is not compatible.

It works just fine in Feisty.  Many people on this thread have reported it working, including myself.  Look a few pages back to see if you can find something that helps.

---

### Post by ayoli on 2007-05-09
> **Neobuntu said:**
> With Feisty, I followed all posts and new suggestions and this does not work.

Anyone with feisty have this working?

I'm guessing the package is not compatible.

works like a charm under feisty with the first post instruction + the missing one:
```
sudo grub-install hdx,y
```

---

### Post by Neobuntu on 2007-05-10
This is a NIGHTMARE!

After 2am in the morn and it still doesn't work. (after days trying)

I've poured over all these pages AGAIN, for new tips and nothing works.

I use Feisty. This box has One drive and Kubuntu is on (hd0,1) AKA hda2.

I've noticed too many people have trashed the first part of their (non-MBR) partitions. (I haven't)

Most people do NOT use grub only in a partition without using the MBR (The Master Boot Record before your "partitions"). So with one drive (and usually all the time also, with more than one) it should be > setup (hd0) for the MBR ONLY! (and "stage Two" goes in your main "root" Linux partition, AKA /boot/grub.) It's the root designation that uses Two numbers. Like "root (hd0,1)" 

There are ERRORS in some of these posts that say (for example) to use hda1 for (hd0,1) and that's wrong. Please check your posts. Also; again, posts with more than one number with "setup (hd0)" will lead people to make mistakes, and write over the first part of an OS! I DON'T KNOW WHY GRUB DOESN'T GIVE A WARNING.

Anyway, somethings amiss here. 

Thank you for reporting success with Feisty, I've having none with gfxboot. 

Is anyone who has specifically upgraded to Feisty (not clean) seen this gfxboot working yet?

I looked at spelling, file placement, syntax, correct directories, using sudo, not using sudo, and nothing works.

Once I get to the new added step of also running "sudo grub-install hd0,1" or "sudo grub-install hd0" I get the same message: > /dev/hda2 does not have any corresponding BIOS drive.

What the heck? I'm using it now AND grub tells me "hd(0,1)".

---

### Post by kvonb on 2007-05-10
It's something to do with the new SATA lib, my guess is that if you didn't do a clean install of Feisty, OR you kept any partitions from a previous installation rather than creating new ones, the lib gets confused.

I have the same errors as you, and I tried about 50 combinations of everything that has been suggested so far.

The confusion comes in the sdx or hdx designation, grub sees one type, and the system sees another, but they are the same thing!

Maybe we can get people to tell us if they created ALL new partitions when installing Feisty, or they kept an old one, and whether it worked or failed.

---

### Post by Malac on 2007-05-10
On Feisty the "missing command" is always:
```
sudo grub-install /dev/[SIZE=3][COLOR=Red]**s**[/COLOR][/SIZE]d[SIZE=3][COLOR=Blue]**x[COLOR=DarkOrchid]y[/COLOR]**[/COLOR][/SIZE]
``` where [SIZE=3][COLOR=Blue]**x **[/COLOR][/SIZE]is "a,b,c, etc." and [SIZE=3][COLOR=Blue]**[COLOR=DarkOrchid]y[/COLOR]**[/COLOR][/SIZE] is "1,2,3, etc." not hd anything regardless of whether it was hd when Edgy was installed.
This applies to fresh Feisty install or upgrade from Edgy.

---

### Post by kvonb on 2007-05-10
```
grub> find /boot/grub/stage1
 (hd0,4)

grub> 
```

```
kev@kev:~$ sudo grub-install /dev/sd0,4
/dev/sd0,4: Not found or not a block device.
kev@kev:~$ sudo grub-install /dev/sd04
/dev/sd04: Not found or not a block device.
kev@kev:~$
```

---

### Post by Malac on 2007-05-10
> **kvonb said:**
> ```
grub> find /boot/grub/stage1
 (hd0,4)

grub> 
``````
kev@kev:~$ sudo grub-install /dev/sd0,4
/dev/sd0,4: Not found or not a block device.
kev@kev:~$ sudo grub-install /dev/sd04
/dev/sd04: Not found or not a block device.
kev@kev:~$
```
No, it should be:```
sudo grub-install /dev/sd**a5**
```
If you get the "no corresponding BIOS drive" message then you are trying to boot from an extended partition and your BIOS doesn't support that.

---

### Post by Marktrix on 2007-05-10
> **Footissimo said:**
> Another GFXboot theme - this time to go with the blue usplash theme [here](http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash) by SilentCacophony.  It's a very basic black background with the glowy logo and lettering from the usplash image.  If anyone likes it, I can do the other colours.

Wonderfull Image thx for that.

---

### Post by Neobuntu on 2007-05-10
> **Malac said:**
> On Feisty the "missing command" is always:
```
sudo grub-install /dev/[SIZE=3][COLOR=Red]**s**[/COLOR][/SIZE]d[SIZE=3][COLOR=Blue]**x[COLOR=DarkOrchid]y[/COLOR]**[/COLOR][/SIZE]
``` where [SIZE=3][COLOR=Blue]**x **[/COLOR][/SIZE]is "a,b,c, etc." and [SIZE=3][COLOR=Blue]**[COLOR=DarkOrchid]y[/COLOR]**[/COLOR][/SIZE] is "1,2,3, etc." not hd anything regardless of whether it was hd when Edgy was installed.
This applies to fresh Feisty install or upgrade from Edgy.

Yields:
> sudo grub-install /dev/sda2
Password:
/dev/sda2: Not found or not a block device. With or without sudo.

---

### Post by Neobuntu on 2007-05-10
also > sudo grub-install hd0,1
/dev/hda2 does not have any corresponding BIOS drive.

---

### Post by Neobuntu on 2007-05-10
and > grub> find /boot/grub/stage1
 (hd0,1) FYI

---

### Post by Neobuntu on 2007-05-10
OK, I even changed fstab to /dev/sda2 rebooted, tried all. Then /dev/hda2 rebooted, tried all and back to the UUID and rebooted and nothing gives a gfxboot graphic.

Does anyone know what the problem is. Again, I have tried all suggestions here.

At least for those of us, where this does not work, I have an easy way to do a grub image here: [http://ubuntuforums.org/showthread.php?t=402971](http://ubuntuforums.org/showthread.php?t=402971)

I understand this is a tack on deb package and not official but it's still wasted way too much time.

In the interest of not driving people away from open software, what the heck is going on here?

---

### Post by Malac on 2007-05-10
@Neobuntu
These are specific instructions for you.

Remove grub, install new .deb then,
```
sudo nano /etc/fstab
```Change the device to /dev/sda2 for your / partition.
Reboot.

In the following code "[COLOR=Gray]grub>[/COLOR]" is the prompt don't type this.

```
sudo grub
[COLOR=Gray]grub>[/COLOR] find /boot/grub/stage1
[SIZE=1][COLOR=Gray] (should give)[/COLOR][/SIZE] (hd0,1)
[COLOR=Gray]grub>[/COLOR] root (hd0,1)
[COLOR=Gray]grub>[/COLOR] setup (hd0,1)
[COLOR=Gray]grub>[/COLOR] quit

sudo grub-install /dev/sda2
```If find /boot.grub/stage1 give just (hd0) (it shouldn't) or (hd0,0)
then change the instructions after the "find" to :
```
[COLOR=Gray]grub>[/COLOR] root (hd0,0)[COLOR=Gray]
grub>[/COLOR] setup (hd0,0)[COLOR=Gray]
grub>[/COLOR] quit

sudo grub-install /dev/sda
```
After all that you could try :
```
sudo update-grub
``` for good measure. :)

If this doesn't work then there is the possibility that the "message" file is corrupt or too large or the entry in the menu.lst is wrong.

Hope this helps.

---

### Post by Neobuntu on 2007-05-10
Thank you so much for trying to help.

I did each and everyone one those exact things already. Really! Including "entry in the menu.lst".

I'm looking for something else to try and I don't think I am the only one.

---

### Post by Neobuntu on 2007-05-11
Can you explain why anyone would use "setup (hd0,1)" or "setup (hd0,1)" (and write stage1) over an installed OS; when they boot GRUB normally from the MBR "setup (hd0)"?

Wouldn't "setup (hd0,1)" or "setup (hd0,1)" write over the first part of my XP /dev/hda1 partition or the first part of my Kubuntu  /dev/hda2 partition causing boot damage??

I went back and did everything again with ("setup (hd0)"); no graphic seen.

---

### Post by Neobuntu on 2007-05-11
No joy.

---

### Post by mrfuzzemz on 2007-05-11
> Can you explain why anyone would use "setup (hd0,1)" or "setup (hd0,1)" (and write stage1) over an installed OS; when they boot GRUB normally from the MBR "setup (hd0)"?

Wouldn't "setup (hd0,1)" or "setup (hd0,1)" write over the first part of my XP /dev/hda1 partition or the first part of my Kubuntu /dev/hda2 partition causing boot damage??


Someone would do that if they were installing grub to the beginning of a partition rather than to the master boot record.  This would make for a slightly more complex boot configuration, but some people do it.

Be sure your menu.lst entry is point to the right file and the file is not corrupt.  You may also want to try 
> sudo grub -install (hd0,1)
with the appropriate partition (where /boot is.)

---

### Post by Neobuntu on 2007-05-11
> **mrfuzzemz said:**
> Someone would do that if they were installing grub to the beginning of a partition rather than to the master oot record.  This would make for a slightly more complex boot configuration, but some people do it.

So you agree that most would NOT have a custom (MBR) menu that goes to a sub-GRUB menu(s) per partition then? Can you say less than 1% perhaps?

Would you also agree that any OS already installed would then be trashed? Thus, anything other than "setup (hd0)" would be done BEFORE an OS install; into that partition(as it would write GRUB stage 1 over the boot sector of the partition and not just the MBR)? Yes, I know "setup (hd1)" could be used for another drive but that's not the point. Trying other than "setup (hd0)" will most likely trash peoples systems.

> Be sure your menu.lst entry is point to the right file and the file is not corrupt.  You may also want to try 

with the appropriate partition (where /boot is.)

You know, I really do appreciate anyone who takes their time to help; in any case. Yet, how many times do I have to indicate that I did that.

I make mistakes and would NEVER assume to be 100% correct or infallible but at this point I believe we have a GFXboot problem.

 I'm asking for help and suggestions; for the benefit of those of us experiencing this no gfxboot graphic. Specifically not being able to do a gfxboot grub-install; on known partition.

How can I say this? I've been assuming it's me and my errors but it doesn't look that way.

I'm also very concerned that many of you guys are trashing your install trying to make this work. 

I'm very curious about the undefined cause of the (no gfxboot graphic, probably due to grub-install failure) problem.

---

### Post by kvonb on 2007-05-11
> **Malac said:**
> No, it should be:```
sudo grub-install /dev/sd**a5**
```

```
kev@kev:~$ sudo grub-install /dev/sda5
Password:
/dev/sda5 does not have any corresponding BIOS drive.
kev@kev:~$ 
```
> If you get the "no corresponding BIOS drive" message then you are trying to boot from an extended partition and your BIOS doesn't support that.Well I have booted from it, and it is working because I am writing this from my unsupported partition, and have been booting from this same partition since Dapper I believe!  Unless I'm actually dead and living a ghost life! :lolflag:

Here is my partition table:

```
kev@kev:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         199     1598436   83  Linux
/dev/sda2   *         200        1729    12289725    7  HPFS/NTFS
/dev/sda3            1730        9729    64260000    5  Extended
/dev/sda5            1730        2875     9205213+  83  Linux
/dev/sda6            2876        9673    54604900   83  Linux
/dev/sda7            9674        9729      449788+  82  Linux swap / Solaris
kev@kev:~$ 
```

---

### Post by Malac on 2007-05-11
> **kvonb said:**
> ```
kev@kev:~$ sudo grub-install /dev/sda5
Password:
/dev/sda5 does not have any corresponding BIOS drive.
kev@kev:~$ 
```Well I have booted from it, and it is working because I am writing this from my unsupported partition, and have been booting from this same partition since Dapper I believe!  Unless I'm actually dead and living a ghost life! :lolflag:

Here is my partition table:

```
kev@kev:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         199     1598436   83  Linux
/dev/sda2   *         200        1729    12289725    7  HPFS/NTFS
/dev/sda3            1730        9729    64260000    5  Extended
/dev/sda5            1730        2875     9205213+  83  Linux
/dev/sda6            2876        9673    54604900   83  Linux
/dev/sda7            9674        9729      449788+  82  Linux swap / Solaris
kev@kev:~$ 
```
No, you are booting from /dev/sda2 that's what the * under Boot means.

---

### Post by ZodiacfreaK on 2007-05-11
gah I am such an idiot, I will try to explain this as best as I can. I have a tri-boot setup, Windows Vista, Mac OS X86, and Ubuntu 7.04 Feisty Fawn. I had grub installed and working perfectly, but then I wanted this graphical boot. Bad idea, I should have just been satisfied with what I had :) but that neever works. So I went through the install steps on either page 30 in this thread, well I got to this part
```

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```
ANd I accidently did the setup on my hd(0,2) partition instead of (0,3)
My 0,2 partition is My Mac OS X86 install. I rebooted. Well nothing changed so  I went back through the steps again and this time put in the correct numbers. Everything worked but when I tried to boot into my Mac OS X partition it stalls about two seconds and then goes back to the GRUB boot screen. What I found out is that I now have GRUB installed on two partitions, I put it on my mac os partition and the other one I think is vista or linux, I dont remember :(. So all I need to do is figure out a way to uninstall GRUB from my mac partition. Can anyone help me with that? If you need any more info just ask!

Basically long story short, if you can tell me how to remove GRUB from a specified partition that would be the way to fix it.

---

### Post by ZodiacfreaK on 2007-05-11
^Edit^ bump

---

### Post by kvonb on 2007-05-12
> **Malac said:**
> No, you are booting from /dev/sda2 that's what the * under Boot means.

OK, so if I did a grub-install to sda2 that would work?

---

### Post by Malac on 2007-05-12
> **kvonb said:**
> OK, so if I did a grub-install to sda2 that would work?
Should do if it were linux yes. not sure what it would do with it being NTFS.
I still can't see how your booting to linux at all if you're saying that GRUB isn't in your MBR. :)
If GRUB is in MBR then "sudo grub-install hd0" should do it.

---

### Post by kvonb on 2007-05-12
> **Malac said:**
> Should do if it were linux yes. not sure what it would do with it being NTFS.
I still can't see how your booting to linux at all if you're saying that GRUB isn't in your MBR. :)
If GRUB is in MBR then "sudo grub-install hd0" should do it.

```
kev@kev:~$ sudo grub-install hd0
Password:
/dev/sda5 does not have any corresponding BIOS drive.

kev@kev:~$ sudo grub-install sda
Format of install_device not recognized.

```

I don't understand either :S

---

### Post by Malac on 2007-05-13
> **kvonb said:**
> ```
kev@kev:~$ sudo grub-install hd0
Password:
/dev/sda5 does not have any corresponding BIOS drive.

kev@kev:~$ sudo grub-install sda
Format of install_device not recognized.

```I don't understand either :S
Looks like you're scuppered. I seem to remember from a previous post you saying the first partition on your disk is corrupt.
You can't boot from an extended partition which is what the "does not have any corresponding BIOS drive" message is indicating.

The only other thing I can suggest is to run through the whole thing again using root (hdo) and setup (hd0) in GRUB and see if that installs it to the MBR successfully then "sudo grub-install hd0" for good measure.

I still can't figure out how you're managing to boot into Ubuntu at all. :)

---

### Post by kvonb on 2007-05-13
> **Malac said:**
> I still can't figure out how you're managing to boot into Ubuntu at all. :)

...that's the magic of Ubuntu baby ;)

---

### Post by Neobuntu on 2007-05-14
No look. We have a real problem here. 

It's not extended partitions, it's probably not our user commands. Myself, kvonb and other are NOT seeing the gfxboot and we have tried all suggested tips (thank you).

People are trashing other OS installs when manually attempting the GRUB setup command with anything other than "setup (hd0) to the MBR. While there is some very advanced uses for this, it HAS to be done BEFORE the OS is installed to said fancy multiboot, multi-menu setup partition. GRUB should warn and it doesn't. Generally, only install GRUB stage 1 into the MBR via "setup (hd0)". 

If you really must set up an advanced mutil-menu system for you multi-booting. I suggest you make up an independent "boot" partition, separate from all others, that holds the GRUB stage 2 (menu.lst etc). This way you don't have to back up or remember which Linux partition that GRUB stage 2 is in. For most people, their only or main Linux install is where GRUB stage 2 is installed (AUTOMATED BY THE INSTALLER) . So really, you might as well just store GRUB stage 2 in your Linux installed partition and if you wipe the whole thing, you can make up a new menu. None of this is critical, writing stage *1* over a partition (other than the MBR) where an existing OS boot sector already exists, IS critical and your best course of action then would be to reinstall (after retrieving anything you can't live without).

We need new direction and explanation about why (with respect that we have double, tripple etc.., checked our attempts) the gfxboot is not working at the grub-install point.

I know that my (stage 2) partition is /dev/hda2 AKA (hd0,1). I've tried /dev/sda and  /dev/sda2 with grub-install as well and NOTHING works. 

We have posted, over and over the output of these trials. GRUB works, why not gfxboot, for us?

---

### Post by Neobuntu on 2007-05-15
I noted that Feisty's GRUB would set menu.lst back to UUIDs when "sudo update-grub" was run so I did the whole shebang again with grub-gfxboot and made sure the "menu.lst" used my /dev/hda2 and I got the exact same results.

No graphic!

Anyone know why gfxboot just does not work?

P.S. BTW, the asterisk on the "sudo fdisk -l" output just means the boot flag, not the partition that one has booted.

---

### Post by kvonb on 2007-05-15
You certainly have a point Neobuntu as this how-to worked perfectly for me (using the exact same hard drive with the same partitions) under Edgy.

It is only since I did a clean install of Feisty BETA, keeping ALL the original partitions and formatting my / partition (/dev/hda5), which Feisty now calls /dev/sda5.

So as far as I can tell, my grub stage 2 is sitting on /dev/sda5, although grub tells me that it is on hd0,4 which doesn't exist!

Now, I'm not 100% sure where my MBR is located.

The thing with my hard disk is that it contains bad sectors at the start of the drive, hence /dev/sda1 is simply an unused partition that I made in order to skip the bad bits, and has nothing on it (I think :confused:).

Now although /dev/sda2 is my active partition (it is NTFS) I don't believe that the MBR is on that partition, as the MBR can be in only one location and that is at the start of the physical disk as I understand it.  PLEASE correct me if I'm wrong on that one!

So to sum up, gfxboot worked under Edgy, but not Feisty!  Why?

---

### Post by mrfuzzemz on 2007-05-15
> So as far as I can tell, my grub stage 2 is sitting on /dev/sda5, although grub tells me that it is on hd0,4 which doesn't exist!

You do realize that hd0,4 and /dev/sda5 are the same exact thing, right?  GRUB just uses a different naming scheme.  hda or sda is hd0, hdb or sdb is hd1.  Partitions go like this: hda1 or sda1 is hd0,0, hdb3 or sdb3 is hd1,2..

GRUB starts counting from 0 rather than 1.

---

### Post by Neobuntu on 2007-05-15
Yes, but why doesn't this work for Feisty?

---

### Post by mrfuzzemz on 2007-05-15
> **Neobuntu said:**
> Yes, but why doesn't this work for Feisty?

Well, uh.  I'm using Feisty right now and gfxboot works perfectly.  Feisty uses UUID as it is more uniquely set.  The partition in the /dev/sda1 format should be commented out just above the UUID in the GRUB menu.lst.

---

### Post by Psicolonia on 2007-05-16
Hi everyone, i've got it up and running. Looks pretty nice but I have a question...

Is your grub quiet? That is, when you boot normal grub you see a "Starting up..." message and then the usplash of ubuntu shows up! In this one this does not happend! I get the entire grub dump. Basically it prints out all the messages of the entry it's booting.

Does this happen to you too? Or it's just me. My menu.lst have the option quiet in all my entries. And this happens in all of them instead the normal "Starting up..."


Can someone help me correct this?

---

### Post by mrfuzzemz on 2007-05-16
> **Psicolonia said:**
> Hi everyone, i've got it up and running. Looks pretty nice but I have a question...

Is your grub quiet? That is, when you boot normal grub you see a "Starting up..." message and then the usplash of ubuntu shows up! In this one this does not happend! I get the entire grub dump. Basically it prints out all the messages of the entry it's booting.

Does this happen to you too? Or it's just me. My menu.lst have the option quiet in all my entries. And this happens in all of them instead the normal "Starting up..."


Can someone help me correct this?

You have quiet as a separate line *and* in the kernel boot line?

---

### Post by Psicolonia on 2007-05-16
here goes :) thanks for the reply!

## ## End Default Options ##

title		Ubuntu
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ace9fa-0a1f-422b-b145-1a240e6f24c0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=74ace9fa-0a1f-422b-b145-1a240e6f24c0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu (memtest86+)
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		----------------------
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1

---

### Post by Neobuntu on 2007-05-16
> **mrfuzzemz said:**
> Well, uh.  I'm using Feisty right now and gfxboot works perfectly.  Feisty uses UUID as it is more uniquely set.  The partition in the /dev/sda1 format should be commented out just above the UUID in the GRUB menu.lst.

I'm aware that some are getting gfxboot to work with Feisty. We are not.

Are you aware that some of us have repeatedly gone over all directions and ideas?

Somethings stopping the graphic. I've tried other graphic files. They are in the correct and designated place. 

root (hd0,1)
setup(hd0)

...seems to work but it does not indicate the graphic file was found like regular GRUB does.

 For you guys with a working Feisty gfxboot, does your install indicate the graphic file was found?

I'm not sure "grub-install" should be needed at all but it yields said errors. "update-grub" only seems to work as with regular GRUB, listing the old grub splash (which I also tested without) and does not fix gfxboot.

What's going on?

---

### Post by Psicolonia on 2007-05-16
i'm a fiesty working fine ;)

here's how i did it (it will sound very wierd)

I tried everything and nothing, so i started dumbly installing on EVERY single partion I've got!

Big mistake! BIG! I tried to boot windows. But windwos partition had a grub! and on that grub if I tried to run windows... I had a grub! I was in a loop. So here's what I did:

Grabbed the WindowsXP boot disc. and ran:

fixmbr
fixboot

both.

Afterwards I ran ubuntu live CD (fiesty) and made grub-install again

everything started to work fine...

Please don't give this a try unless you are crazy but... mine's working...

---

### Post by phansiizwe on 2007-05-17
I think that when you have grub running in the Master Boot record, you need to use the grub-install command to get it working.

I have one SATA harddrive (sda) and had grub installed in the master boot record. Following the steps in the how-to did not give me a graphical grub, but after doing:

```
sudo grub-install /dev/sda
```

everything worked!

---

### Post by Psicolonia on 2007-05-17
basically you have to reinstall grub. otherwise the grub on the mbr is still the old one and does not recognize the graphical line on menu.lst.

But quite honestly i've tried that dozens of times. only when i cleared the mbr and re-install it worked.

On fiesty i wasn't able to get it to run before removing it... but it was just me!

---

### Post by Neobuntu on 2007-05-18
How many people have it working by clearing the MBR first?

---

### Post by u-foka on 2007-05-22
Hy!

Now i find out what was the problem on my feisty computer... It's have an ide hdd, but feisty uses it with a fake scsi driver (/dev/sda), when i try to run "grub-install hd0,0" it's told my: /dev/sda1 does not have any corresponding BIOS drive. But when i loaded feisty with an old 2.6.17 kernel, it's using the generic ide driver for my hdd (/dev/hda), and grub-install work's fine :)

I hope it's can help anybody :)

---

### Post by Neobuntu on 2007-05-22
I tried work-arounds (sda, no UUID, etc) for "2.6.20-15-generic #2 SMP".

Does this mean gfxboot graphic does not work with anyones Fiesty and "2.6.20-15-generic #2 SMP"?

---

### Post by mrfuzzemz on 2007-05-22
The kernel should have nothing to do with it as the kernel is loaded by grub.

---

### Post by fooman on 2007-05-22
running fiesty on my 2nd ide drive (hdb) ...i followed the guide in the first post ,  but could not get it to work.

used the command:

```
sudo grub-install /dev/hdb
```

and hey....IT WORKS !!  :D

thanks

---

### Post by manishk on 2007-05-23
Can anyone please tell me how to get back the old grub (assuming that I have the Feisty Live CD)??

No, I haven't broke my system...I haven't even started installing gfx-grub. I just wanted to make sure I know how to get back before getting my hands dirty!! ;)

---

### Post by mrfuzzemz on 2007-05-23
manishk:
Using the livecd you'll open a terminal and run
> sudo grub
find /boot/grub/stage1
root [whatever it returns above]
setup [whatever drive it says above.  (hd0) for example

Let me know if you have any more questions

---

### Post by Thusitha on 2007-06-02
hello everybody!!
my problem is this ...........
I did everything u hav told to me..........
but @ da booting it says cannot find grafics file...... 
so wat do i do?
is there a proper place in the menu.1st to place that "gfxmenu .............." line.........

thnx.

---

### Post by oGGe on 2007-06-02
Hello people! Thanks for the lovley guide.

But I have a problem. I followed all your steps, but got the same GRUB look as always. So I checked if other ppl got this output, and they had it installed on an other HD. But I have only one HD! What can I do ?

---

### Post by LKRaider on 2007-06-02
your menu.lst is probably wrong:

put the gfxboot onption on the first line of the file
disable password protection if it is enabled (gfxboot won't work with password protection and you'll get the normal grub screen)

see if that fixes it.

---

### Post by oGGe on 2007-06-03
> **LKRaider said:**
> your menu.lst is probably wrong:

put the gfxboot onption on the first line of the file
disable password protection if it is enabled (gfxboot won't work with password protection and you'll get the normal grub screen)

see if that fixes it.

First line now, i have no passwd on. Lets see it it works ^^

---

### Post by oGGe on 2007-06-03
Ok, that didn't work. Ill give you 2 outcomes to find out what i shall do.

Here's 'fdisk -l'
```
Disk /dev/hda: 10,0 GB, 10056130560 byte
255 huvuden, 63 sektorer/spår, 1222 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               1        1161     9325701   83  Linux
/dev/hda2            1162        1222      489982+   5  Utökad
/dev/hda5            1162        1222      489951   82  Linux växling / Solaris
```

And here we go with 'menu.lst'
```
gfxmenu /boot/grub/message.xubu

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)


# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=sv_SE

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.20-16-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.17-11-386
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro quiet splash locale=sv_SE
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=ae9524e5-c83f-4cd8-802d-ad2b73ea519d ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

That's it. Is something wrong ?

---

### Post by phansiizwe on 2007-06-03
> **oGGe said:**
> Hello people! Thanks for the lovley guide.

But I have a problem. I followed all your steps, but got the same GRUB look as always. So I checked if other ppl got this output, and they had it installed on an other HD. But I have only one HD! What can I do ?

If you have GRUB installed in the master boot record, try:

```
sudo grub-install /dev/hda
```

---

### Post by Cyclist on 2007-06-04
I'm a total Newbie, but I think this step is missing at the end:

 sudo grub-install /dev/hda  (or whatever the name of your Ubuntu disk may be: sda, hdc etc.)

I spend hours on it yesterday and didn't get it working, till I ended your instructions with the command in the line above.

Gr, Cyclist

I just see someone else gave the same reply......I found it out myself and it worked for me. NOTE however that your drive may have a different name than hda!

---

### Post by mrfuzzemz on 2007-06-04
> **Cyclist said:**
> I'm a total Newbie, but I think this step is missing at the end:

 sudo grub-install /dev/hda  (or whatever the name of your Ubuntu disk may be: sda, hdc etc.)

I spend hours on it yesterday and didn't get it working, till I ended your instructions with the command in the line above.

Gr, Cyclist

I just see someone else gave the same reply......I found it out myself and it worked for me. NOTE however that your drive may have a different name than hda!

That's absolutely right. We've been saying that for a while, but the starter of the tread has not updated it at all.

---

### Post by Thusitha on 2007-06-04
> **LKRaider said:**
> your menu.lst is probably wrong:

put the gfxboot onption on the first line of the file
disable password protection if it is enabled (gfxboot won't work with password protection and you'll get the normal grub screen)

see if that fixes it.

tired but no success........ always says missing graphic file........ and another thing ...... 
FIND command in the grub shell is not working...... I hav given the right path but it says cannot find the file........

---

### Post by bernerbits on 2007-06-05
Hey,

I seem to be having the same old story. However, I haven't seen my exact symptoms here, it seems to be actually trying to load the graphical grub file but finding it corrupted. For starters, PLEASE don't tell me to "sudo grub-install /dev/sda and it will just work."

That said, I'm running a Dell Inspiron 1501 laptop with an AMD64 processor.

Here's my fdisk -l output:

```
root@delllaptop-ubuntu:/home/dcberner# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11407    81060864    7  HPFS/NTFS
/dev/sda4           11407       14376    23855861    5  Extended
/dev/sda5   *       11407       11414       63595+  83  Linux
/dev/sda6           11415       12720    10490413+  83  Linux
/dev/sda7           12721       12785      522081   83  Linux
/dev/sda8           12786       12916     1052226   82  Linux swap / Solaris
/dev/sda9           12917       13979     8538516   83  Linux
/dev/sda10          13980       14110     1052226   83  Linux
/dev/sda11          14111       14376     2136613+  83  Linux

```

Here's my menu.lst:

```
root@delllaptop-ubuntu:/home/dcberner# cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue
foreground 000000
background ffffff

gfxmenu /grub/message.ubugrey

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=64d033c9-ccac-4a2a-9d75-f781e18614c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Windows Vista
root            (hd0,2)
makeactive
chainloader     +1

title           Debian GNU/Linux, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=64d033c9-ccac-4a2a-9d75-f781e18614c2 ro quiet splash
initrd          /initrd.img-2.6.20-15-generic

title           Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=64d033c9-ccac-4a2a-9d75-f781e18614c2 ro single
initrd          /initrd.img-2.6.20-15-generic

title           Debian GNU/Linux, kernel memtest86+
root            (hd0,4)
kernel          /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


```

Here's the contents of /boot/grub:

```
root@delllaptop-ubuntu:/home/dcberner# ls /boot/grub
default            iso9660_stage1_5  menu.lst.bak     reiserfs_stage1_5
device.map         jfs_stage1_5      message.suse     stage1
e2fs_stage1_5      menu.lst          message.ubugrey  stage2
fat_stage1_5       menu.lst~         message.wide     xfs_stage1_5
installed-version  menu.lst_backup   minix_stage1_5

```

And here's the output of my setup:

```
root@delllaptop-ubuntu:/home/dcberner# grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> find /grub/stage1
find /grub/stage1
 (hd0,4)
grub> root (hd0,4)
root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit

```

So, when I boot up, I get the following message:

```
/grub/message.ubugrey: Invalid file format
```

Then it waits 5 seconds and gives me the standard text GRUB menu. I have tried three themes so far and it's done this for each and every one. A quick glance at the source code confirms that it did indeed FIND the file, but was unable to find a file contained inside it that started with the right magic number (magic number being a standard file format indicator like GIF89a and CAFEBABE).

Anyone run into this particular problem?

---

### Post by kvonb on 2007-06-06
> **bernerbits said:**
> Hey,

when I boot up, I get the following message:

```
/grub/message.ubugrey: Invalid file format
```Then it waits 5 seconds and gives me the standard text GRUB menu. I have tried three themes so far and it's done this for each and every one. A quick glance at the source code confirms that it did indeed FIND the file, but was unable to find a file contained inside it that started with the right magic number (magic number being a standard file format indicator like GIF89a and CAFEBABE).

Anyone run into this particular problem?

Read the following line, note anything wrong?

```
 gfxmenu /grub/message.ubugrey
```

It should be:

```
 gfxmenu /boot/grub/message.ubugrey
```

It's easy to make a mistake, I've done it many many times :(

---

### Post by Robert98374 on 2007-06-11
sorry had to look at an example to figure it out :-)

---

### Post by Neobuntu on 2007-06-11
OK now. Still not working and others here, seem to be having the same frustration.

I realize the details must be followed. No syntax or step can be missed and I know what my drive is called by GRUB and otherwise.

It seems like every time I assert this predicament, someone says "Oh I just fixed it by doing X". I really don't think I have failed to accurately attempt every suggestion (and some of my own).  So this is turning away SOME (not all) of us.

Somethings incompatible.

Perhaps it is the Nvidia card and it's modules I am using?

---

### Post by frying_fish on 2007-06-11
By the time grub is being loaded it isn't even at a stage of looking at graphics card drivers or modules for anything.  It hasn't started an OS, so that won't be the cause.

---

### Post by DizzyTech on 2007-06-11
Is there a repo for this anywhere?

---

### Post by nbayiha on 2007-06-12
Just want to say that i follow the thread and i  get it worked , 
i am using a amd64bit,  and i recommended everyone who want to make it work to be really carefull and to read all the post from the beginning, I know it's too long  but sometimes messing up with Grub can just bring to one solution...... reinstalling and i am sure no one want it. :-p

For those with 64bit  don't forget to had this command ```
sudo grub-install hdx,y
```

Anyway let me resume you what you should do , for those who don't want to read all the post.
actually this should work for everyone, especially for those with 64bit architecture, please go step by step and read carefully

1)  download gfxboot

[http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

2) download the theme you want u can take the one from the first post 
(actually i'm using this one [http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657))
 
[http://ubuntuforums.org/showpost.php?p=1212505&postcount=1](http://ubuntuforums.org/showpost.php?p=1212505&postcount=1)

3)Remove the old Grub 

```
sudo apt-get remove grub
```

4) install the gfx boot from the step one(it's a debian package so there is nothing to say here it is GUI) 

those with  64bit will have to force the architecture cause this deb is for 32bit, so for those with (for example amd64 ) do this in a terminal.

```
 sudo dpkg -i --force-architecture grub-gfxboot_0.97-5_i386.deb
```

just say yes if something is asked.

5) now copy your theme to the grub

```
sudo cp message.suse /boot/grub/ 
```

of course message.suse can be message.xxxxxx for me for example it was message.ububrown
xxx is depending on which theme you are using and like i the beginning we consider using the theme from the first page so it should be message.suse

6) backup you grub file.

```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

7)now edit your menu.ls in the grub, you should be careful about this place cause depending on where u are going to put the line , you theme is going to be seen or  not. actually i put in the first line

```
gksudo gedit /boot/grub/menu.lst
```

this will open a textfile, insert at the beginning this new  line.    _** gfxmenu /boot/grub/message.suse**_ 

save 

8  )  8) now open a terminal
and  write

```
sudo grub
```
u should be now in the grub console and you should be receiving something looking like this  **grub>**
so write this first

```
 find /boot/grub/stage1 
``` press enter
you will have an output looking like this                              **(hdx,y)** of course x, and y represent number in my case they were 0 and 6. anyway remenber those number.

write now this
```
root (hdx,y)
```

and after this
```
setup (hdx)
```

when it says completed hit ctrl+c

9) now this step is actually for those using feisty fawn like me,
 you soul make this at the end

```
sudo grub-install hdx,y
```

and that's it.


I make it as much easier so even someone who don't know a lot about grub loader can make it work(even my Grand Ma) reading this will make it work  ;)  ummmmmmmmmmmmmmm maybe :D

---

### Post by Neobuntu on 2007-06-14
It worked!

T H A N K   Y O U !

---

### Post by rollps on 2007-06-14
worked for me too !!

i had given up any hope to make this thing work again....

i think the important part is to do :
sudo grub-install hdx,y

at the end (it wasn't in the original post)

thanks guys :D

---

### Post by kvonb on 2007-06-14
Anyone know what this means:

```
kev@kev:~$ sudo grub-install hd0,0

GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> root (hd0,0)
 Filesystem type is reiserfs, partition type 0x83
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,0)"...  18 sectors are embedded.
succeeded
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 (hd0,0) (hd0,0)1+18 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2
grub> quit
kev@kev:~$

```...apart from that it is broken :)

OK, I tried this as well and it didn't give any error messages at least:

```
kev@kev:~$ sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
kev@kev:~$   
```

I have yet to reboot and try iy, I'll report back.....

---

### Post by oGGe on 2007-06-14
> **phansiizwe said:**
> If you have GRUB installed in the master boot record, try:

```
sudo grub-install /dev/hda
```


Thank you ^^' That was the missing step. The Grub-terminal stuff didnt rly work ;D

---

### Post by ShareBuntu on 2007-06-17
Works perfectly with the addition of sudo grub-install hdx,y to the original instructions. :D

---

### Post by 4tro on 2007-06-19
maybe this comes in handy

[http://www.kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb](http://www.kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb)

only problem is you'll need to backup your /usr/sbin/update-grub before installing, because there are some differences from debian to ubuntu

to backup
```
sudo cp /usr/sbin/update-grub /usr/sbin/update-grub.old
```to install the package
```
sudo dpkg -i grub-gfxboot_0.97-11_amd64.deb
```after you installed the package, run:
```
sudo cp /usr/sbin/update-grub.old /usr/sbin/update-grub
```these steps just replace the steps about installing the package, nothing else.

---

### Post by msch on 2007-06-20
> **bernerbits said:**
> 

So, when I boot up, I get the following message:

```
/grub/message.ubugrey: Invalid file format
```

Then it waits 5 seconds and gives me the standard text GRUB menu. I have tried three themes so far and it's done this for each and every one. A quick glance at the source code confirms that it did indeed FIND the file, but was unable to find a file contained inside it that started with the right magic number (magic number being a standard file format indicator like GIF89a and CAFEBABE).

Anyone run into this particular problem?

I'm getting the same thing here bernerbits.  This is on a Dell D820 with core2duo running amd64.  Has anyone successfully figured this out?

I've tried 5 different message files, unpacked and repacked assorted ones, nothing seems to work.  Any suggestions would be appreciated!

---

### Post by ESPOiG on 2007-06-21
gfxgrub works in fiesty fine for me

---

### Post by 4tro on 2007-06-21
> **msch said:**
> I'm getting the same thing here bernerbits.  This is on a Dell D820 with core2duo running amd64.  Has anyone successfully figured this out?

I've tried 5 different message files, unpacked and repacked assorted ones, nothing seems to work.  Any suggestions would be appreciated!

i could be mistaken but isn't the standard grub directory /boot/grub/?
dunno if it is related though.

---

### Post by msch on 2007-06-21
> **msch said:**
> I'm getting the same thing here bernerbits.  This is on a Dell D820 with core2duo running amd64.  Has anyone successfully figured this out?

I've tried 5 different message files, unpacked and repacked assorted ones, nothing seems to work.  Any suggestions would be appreciated!

Hello, I've finally figured this out.

It isn't realated to the path name.  The fact that it's reporting invalid file format indicates that it has successfully found the file, but isn't able to process it correctly.  The difference between /boot/grub/message and /grub/message has to do with if you have a seperate boot partition.  I have a seperate boot partition that mounts at /boot.  Thus when looked at indiviudually the pathing on that partition starts with /grub.  

As far as fixing the error, I'm using the sidux amd64 debs mentioned earlier in this thread.  I installed gfxboot-theme-sidux-2006 from the same repo.  You then have to:

```

claudia:~# cd /usr/share/gfxboot-theme-sidux-2006/sidux-2006/
claudia:/usr/share/gfxboot-theme-sidux-2006/sidux-2006# make
claudia:/usr/share/gfxboot-theme-sidux-2006/sidux-2006# cp boot/message /boot/grub/

```

And this gives me a properly formatted message file.  I assume this is a difference in the amd64 debs from sidux vs. the i386 deb using the force-arch.

So to cap, it appears that if you use the  debs mentioned earlier in the thread from 

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

you need to follow the make procedure to get a valid file format for this verision.

---

### Post by 4tro on 2007-06-22
> **msch said:**
> Hello, I've finally figured this out.

It isn't realated to the path name.  The fact that it's reporting invalid file format indicates that it has successfully found the file, but isn't able to process it correctly.  The difference between /boot/grub/message and /grub/message has to do with if you have a seperate boot partition.  I have a seperate boot partition that mounts at /boot.  Thus when looked at indiviudually the pathing on that partition starts with /grub.  

As far as fixing the error, I'm using the sidux amd64 debs mentioned earlier in this thread.  I installed gfxboot-theme-sidux-2006 from the same repo.  You then have to:

```

claudia:~# cd /usr/share/gfxboot-theme-sidux-2006/sidux-2006/
claudia:/usr/share/gfxboot-theme-sidux-2006/sidux-2006# make
claudia:/usr/share/gfxboot-theme-sidux-2006/sidux-2006# cp boot/message /boot/grub/

```And this gives me a properly formatted message file.  I assume this is a difference in the amd64 debs from sidux vs. the i386 deb using the force-arch.

So to cap, it appears that if you use the  debs mentioned earlier in the thread from 

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

you need to follow the make procedure to get a valid file format for this verision.


i pasted a link to amd64 packages a few posts ago. those work perfectly for me.


[http://www.kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb](http://www.kanotix.com/files/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-11_amd64.deb)


have a go at it

somebody should really add these to the howto in the first post.

---

### Post by mrfuzzemz on 2007-06-22
Since no one (the thread starter hasn't) has added to the first post then maybe we should just start a new thread that is complete. Referencing this thread, of course.

---

### Post by 4tro on 2007-06-23
i can start a new one, but i would like to include the complete guide into it.
that way it'll stay readable

i made the new one, posted it for acceptance by the moderators, it will be visible soon i hope.
please comment in the thread if you have ideas or comments on the howto.

or just drop me a pm

*edit*
addendum to this thread on:
[http://ubuntuforums.org/showthread.php?t=481957](http://ubuntuforums.org/showthread.php?t=481957)
mostly useful for people running in 64 bit mode.

---

### Post by kraigory on 2007-07-01
okay, so i feel kindof dumb for asking this, but...

```
kraigory@elihu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8517    68364607+   7  HPFS/NTFS
/dev/sda3            8518       11306    22402642+   5  Extended
/dev/sda4           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda5            8583       11306    21880530   83  Linux
/dev/sda6            8518        8582      522049+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

does this change how I need to configure gfxboot? Since it says sda instead of hda, as implied in the tutorial?

I followed everything closely but still get the same 'ol grub. And, no error messages to tell me whats wrong =/

thanks for any help!

---

### Post by unconcrete on 2007-07-01
I've installed gfxboot by following step-by-step the instructions of the current Howto. At least I thought to have done it correctly but probably not. Actually at the system reboot, [Ubuntu edgy eft - Nvidia Geforce FX5500- Athlon 64 3700+processor] Nothing happens. Only the same black/blue screen with  os choices as used before gfxboot. I've put message.suse in my boot/grub dir without success then I've tried other themes but the problem is the same: gfxboot doesn't work.
This is my current menu.lst.
gfxmenu /boot/grub/message.blusplash
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a6515639-89a1-4753-a488-94309cc1ec80 ro
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
# Splashimage - uncommented since I've installed gfxmenu
# foreground = 0000ff
# background = ffffff
# splashimage=(hd0,5)/boot/grub/splashimages/hpp.xpm.gz

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
...
========endfile=================================================================
This is my partition table:
armonica@persik-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9249    74292561    7  HPFS/NTFS
/dev/sda2            9250       11531    18330165    c  W95 FAT32 (LBA)
/dev/sda4           16145       24321    65681752+   5  Extended
/dev/sda5           16145       16291     1180746   82  Linux swap / Solaris
/dev/sda6           16292       24321    64500943+  83  Linux
armonica@persik-desktop:~$ 
I've seen my linux partition is /dev/sda6 which has been mounted on (hd0,5). I've used these values in the grub environment:
sudo grub
grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hd0,5)
grub> setup (hd0,5)
...I've tried to install other themes but nobody work.Please help.

unconcrete

---

### Post by kraigory on 2007-07-01
^^ i'm in pretty much the same predicament. Any ideas?

---

### Post by Malac on 2007-07-01
@[kraigory]("http://ubuntuforums.org/member.php?u=180363") and [unconcrete]("http://ubuntuforums.org/member.php?u=176792") 					
```
sudo grub-install /dev/sd[COLOR=Red]**xy**[/COLOR]
```Where [COLOR=Red]**x**[/COLOR] is a,b,c,etc. [COLOR=Red]**y **[/COLOR]is 1,2,3,etc.

---

### Post by kraigory on 2007-07-01
```
kraigory@elihu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8517    68364607+   7  HPFS/NTFS
/dev/sda3            8518       11306    22402642+   5  Extended
/dev/sda4           11372       11977     4867695   db  CP/M / CTOS / ...
/dev/sda5            8583       11306    21880530   83  Linux
/dev/sda6            8518        8582      522049+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2048 MB, 2048729600 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992     1999749+   6  FAT16
kraigory@elihu:~$ 

```

> @kraigory and unconcrete
Code:

sudo grub-install /dev/sdxy

Where x is a,b,c,etc. y is 1,2,3,etc.

Which one do I do? sda5 for the linux partition, or sdb1 for the "device boot" ?

---

### Post by unconcrete on 2007-07-02
Ops... I've lost the most important part of the process. 
Now  I've done sudo grub-install sda1 and now gfxboot works correctly. I'll update my little how to.
Thanks a million, kraigory
:)
unconcrete

---

### Post by unconcrete on 2007-07-03
There's another problem now. It happened my ntfs partition was lost as I 've installed grub in my dev/sda1 device. The vfat partion is still visible but i've lost Windos XP. 
How can I recover it?

Thanks in advance
 I know I should not be so hurried to avoid to backup my mbr with dd but I have not done it.  :frown:
unconcrete

Some information...
--------------------------------------------------------CURRENT PARTITIONS------------------------------------------
armonica@persik-desktop:~$ sudo fdisk -l
Password:
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9249    74292561    7  HPFS/NTFS # no more neither visible nor mounted #
/dev/sda2            9250       11531    18330165    c  W95 FAT32 (LBA) #ok
/dev/sda4           16145       24321    65681752+   5  Extended #ok
/dev/sda5           16145       16291     1180746   82  Linux swap / Solaris #ok
/dev/sda6           16292       24321    64500943+  83  Linux #ok

---------------------------------------------------------CURRENT EDGY FSTAB----------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                0  0  
# /dev/sda6
UUID=a6515639-89a1-4753-a488-94309cc1ec80  /              ext3         defaults,errors=remount-ro              0  1  
# /dev/sda1
UUID=E4C0300AC02FE212                      /media/pippo   ntfs         defaults,nls=utf8,umask=0222,gid=46     0  0  
# /dev/sda2
UUID=1006-16B2                             /media/pluto   vfat         defaults,utf8,umask=0000,gid=46         0  0  
# /dev/sda3
# UUID=c0ec6d7e-f4b4-40d5-ab11-a04b99ec3392 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=9206b41a-6f52-477e-8394-bdfadc71329e  none           swap         sw                                      0  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto                             0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto                             0  0  
/dev/sda2                                  /media/pluto   vfat         defaults                                0  0  
/dev/sda1                                  /media/pippo   ntfs         nls=iso8859-1,users,umask=0222,user,ro  0  0  
/dev/sda5                                  /media/sda5    swap         defaults                                0  0  

------------------------------------      MOUNT ERRORS-------------------------------------------------------------
armonica@persik-desktop:~$ sudo mount -a
Password:
mount: special device /dev/disk/by-uuid/E4C0300AC02FE212 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
----------------------------------------------DMSG OUTPUT ----------------------------------------------------------
armonica@persik-desktop:~$ dmesg | tail
[17180099.296000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180099.296000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17180216.748000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180216.748000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180216.748000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180216.748000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17180247.524000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180247.524000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180247.524000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180247.524000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
---------------------------------------------------------------------------------------------------

---

### Post by Malac on 2007-07-03
If you have an XP Install CD insert that and boot from it.
When asked for options choose "Repair Using Recovery Console" from the options. (I am not sure of the exact wording.)

You will be asked which XP you want to log on to  then asked for the administrator password. If you haven't set up a password just press Enter.
When you get to the prompt type:
```
fixboot
```Then
```
fixmbr
```This should restore your XP boot sector and MBR.

If you have no install CD but can access another XP machine then;
Format a floppy
Copy the ntldr, ntdetect.com and boot.ini to it.
Alter the boot.ini on the floppy to point at where your XP partition is.
e.g.```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\Windows 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\Windows="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
```Then boot off the floppy.
This is a handy disk to let you boot XP if anything happens again.

---

### Post by mrfuzzemz on 2007-07-04
If you don't have a windows install CD the free alternative is to download SuperGrub.  You can repair your MBR with grub and even with the windows bootloader.  It's free, it's a small image and it is extremely helpful.

---

### Post by Haama on 2007-07-09
Hi! I've also tried to install the gfxboot. Everything else has gone well except when i run ```
sudo grub
grub> setup (hd0,0)
``` i get ```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```
when i reboot it starts a non-graf grub titled GRUB stage 1.5
how can I make the gfx work?

---

### Post by kvonb on 2007-07-11
> **mrfuzzemz said:**
> If you don't have a windows install CD the free alternative is to download SuperGrub.  You can repair your MBR with grub and even with the windows bootloader.  It's free, it's a small image and it is extremely helpful.

Do you actually understand that super grub disk?

I've tried it several times, it might as well be written entirely in Chinese, it makes no sense to me :/

It asks nonsensical questions then just seems to go around in circles doing unfathomable things and failing miserably!

---

### Post by mrfuzzemz on 2007-07-12
I had no idea what I was doing until I looked at the documentation on the website:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

After browsing through its many menus I became forever indebted to it.

---

### Post by mlock on 2007-07-22
when I try to run command find /boot/grub/stage1 I get a error 15 code : file not found HELP and yes I'm new too linux

---

### Post by 4tro on 2007-07-24
try running any alternatives to that command

find /boot/stage1

find /grub/stage1

the idea is you find where your grub is installed.

---

### Post by kvonb on 2007-07-24
> **mlock said:**
> when I try to run command find /boot/grub/stage1 I get a error 15 code : file not found HELP and yes I'm new too linux

You have to run that command from inside grub.

Open a terminal (menu->accessories) and type:

```
sudo grub

```
then you can type:

```
find /boot/grub/stage1
```

---

### Post by bootsbradford on 2007-07-28
What is the easiest way of removing GfxBoot?

Thanks.

---

### Post by 4tro on 2007-07-29
the easiest way to remove the graphical screen is to remove the entry from your menu.lst.

the slightly more difficult way is to remove the installed gfxboot, reinstalling normal grub and then reinstalling it to your MBR, which are basically the same steps as followed for the how-to

---

### Post by bootsbradford on 2007-07-29
> **4tro said:**
> the easiest way to remove the graphical screen is to remove the entry from your menu.lst.

the slightly more difficult way is to remove the installed gfxboot, reinstalling normal grub and then reinstalling it to your MBR, which are basically the same steps as followed for the how-to

Thanks for the reply.

What is MBR? How do I install normal grub to it?

Thanks in anticipation!

---

### Post by 4tro on 2007-07-30
> **bootsbradford said:**
> Thanks for the reply.

What is MBR? How do I install normal grub to it?

Thanks in anticipation!

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

---

### Post by epgui on 2007-08-05
I've got a 64 bit architecture and gfxboot refuses to install.
Any way to fix that?
```
epgui@epgui:~/Desktop$ sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
dpkg: error processing grub-gfxboot_0.97-5_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 grub-gfxboot_0.97-5_i386.deb
epgui@epgui:~/Desktop$ 

```

edit -
i gave up on x64 and installed i386 version of Ubuntu.
After trying out a combination of solutions i happened to be able to work it out.
Works well now, i'm trying to get a good theme to show up.

---

### Post by mrfuzzemz on 2007-08-05
I have gfxboot wokring fine, but from the package available on this thread.  What is up with the gfxboot package in the ubuntu repositories?  If we could explain how to get that going, it shouldn't depend on the architecture.  Heck, we could start a new thread for it that includes ALL the necessary instructions (such as grub-install).

---

### Post by Ub1476 on 2007-08-05
Hi, I did something wrong any when booting I know end up in the grub command line. Could anyone tell me how to restore all settings, or at least tell me how to get into a *_normal_* command line I need to edit menu.lts)? Thanks in advance.

---

### Post by mrfuzzemz on 2007-08-05
I would say boot up an Ubuntu or Knoppix Live CD and mount your boot or root partitiion (whichever one has menu.lst).  Then you can edit to your hearts content.

---

### Post by Ub1476 on 2007-08-06
Yep fixed it. Edited from /menu/disk/boot/grub

---

### Post by Ub1476 on 2007-08-06
Still nothing changes. I followed the instructions correctly, and got no errors.

Here's my menu.lst if of any help:

```
gfxmenu /boot/grub/message.ubugrey
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by ayoli on 2007-08-06
> **Ub1476 said:**
> Still nothing changes. I followed the instructions correctly, and got no errors.

Here's my menu.lst if of any help:

```
gfxmenu /boot/grub/message.ubugrey
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf4a2202-f314-4e26-83a5-926fb442e101 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

i think you miss a line like this at the begining og your menu.lst:
```
gfxmenu (hd0,1)/boot/grub/message.blusplash
```
replace *message.blusplash* with your theme

---

### Post by TravMan63 on 2007-08-15
Thanks for the 'how to'.

Observations:

It's interesting - grub is uninstalled, yet called on later - I'm guessing that gfxmenu takes over.  Also - running grub as user gives 'command not found', where as sudo or su allows the editing to take place.  (sudo is n/a in Elive...)

On a dual-boot machine (Elive, Ubuntu) - I had two 'boot' folders (actually Ubuntu's boot I placed on separte partition (hda,5) - and is mounted to /boot - so does 'boot folder' exist? , Elive has two partitions (Home and Root - Elive's boot is in it's root partition in /boot/grub/...(hda,14)  - Installed Ubuntu lastly (Elive has it's own message.elive) - which 'destroyed' the gfxmenu (all OS choices were availible in the 'Ubuntu grub' menu.lst).   

If I recall correctly - Elive's installer didn't allow for a choice as to where the /boot partition was.... (how does that work - what's the best way - install all OS's /boot to the same area - Linux's usually play nicely and pick up other OS's - some windows installs do (at least with thier own 'brethern' (have XP and 98 on another machine)

While in Ubuntu,  I did the 'grub (0,x)' (<-syntax is incorrect) - it showed the grub on the Elive install... installed to that - and - got the message.elive to show - just had to copy the menu.lst from the 'ubuntu grub'... 
(that was in Elive - the Elive menu.lst - had just Elive in it...)
(had to mount the 'ubuntu grub' parition - I used gparted to accomplish that)

It was my intent (I did most of this work from the Ubuntu install) - to have the 'ubuntu grub' be used - (edited that menu.lst .... made a symbolic link to the original message.elive, copied the original file - neither worked... changed the directory to /grub/message.elive etc etc etc... didn't work)

In the end - it works - :KS just not the way I had tried to force it (to use the 'ubuntu grub'... :confused: (maybe I needed to do the install to the hda,5 - that seems obvious - but everything else was in place - perhaps by doing that it allows the gfxmenu to actually be active - and I guess that is why it must be installed - in ubuntu - when it existed already in elive...)

Now I'll be working on designing a 'message' or two...
I've seen some tuts/howtos - 

----
oh the joys...  (if it sounds cornfusing - well...IT WAS :lolflag:)
-----

Is there a way to position the text (from the menu.lst)?  
The text goes off screen to the right...
and when it is scrolled - the rightmost becomes garbled...

--------
TM

---

### Post by kvonb on 2007-08-15
Anyone know what this means?

```
kev@kev:~$ sudo grub-install --recheck /dev/sda2
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> root (hd0,1)
 Filesystem type is reiserfs, partition type 0x83
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,1)"...  18 sectors are embedded.
succeeded
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 (hd0,1) (hd0,1)1+18 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2
grub> quit
```

GFXboot will **NOT** take on this damned computer, it works perfectly on my laptop which has the same partition/software setup.

I'm starting to think that the problem is the hard disk controller on this mainboard, it just will not take!

Here is the output of fdisk -l

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       24259   153902700   83  Linux
/dev/sda3           24260       24321      498015   82  Linux swap / Solaris
```

This is a completely new install of both Windows and Linux, fresh partitions too.

:confused:

---

### Post by kvonb on 2007-08-15
Well for some unknown reason it worked this time!!!!

I really don't know what I did differently, but here is what I did:

The message. files in /boot/grub were permissions: 1600744, so I made them 600644 which is the same as the other files in that folder.

Next I opened a terminal and instead of running the command with su, I used a real root prompt:

```
sudo su
```

then ran the command again

```
grub-install /dev/sda2
```

.....and it took!

Maybe it was the small animal I accidentally sacrificed to the god of binary during the reboot!

---

### Post by tapash on 2007-08-18
I want to make my own gfxboot screen. Is there any posibiliy that  i can make my own package. Please reply

---

### Post by 4tro on 2007-08-19
> **tapash said:**
> I want to make my own gfxboot screen. Is there any posibiliy that  i can make my own package. Please reply
have a look at one of the first posts, it's all there ;-)

---

### Post by merlwiz79 on 2007-08-21
Here is one that I made for Linux Mint 3.0.
Click to Enlarge
[[IMG]http://farm2.static.flickr.com/1117/1191230849_e31e6f2c33_m.jpg[/IMG]]("http://farm2.static.flickr.com/1117/1191230849_68d271ee85_o.png")
[http://www.MegaShare.com/260297]("http://www.MegaShare.com/260297")
[http://rapidshare.com/files/50290971/message.mint1.2]("http://rapidshare.com/files/50290971/message.mint1.2")

---

### Post by matiit on 2007-08-22
Hi, 
I cant use any theme from this topic...
I have issue:
Invalid file format.
/place/of/message

---

### Post by merlwiz79 on 2007-08-23
> **matiit said:**
> Hi, 
I cant use any theme from this topic...
I have issue:
Invalid file format.
/place/of/message

Which ones are you using?
Are you putting the right line in menu.lst?
gfxmenu /boot/grub/message.xxxx
replacing xxxx with the name of your file.
Mine is mint1.2 on the previous page.
So it would be```
gfxmenu /boot/grub/message.mint1.2
```

---

### Post by RaZer0r on 2007-09-04
I need some help with this...
I can't get it to work, or I'm missing something, or I'm doing something wrong, but every time i reboot, i get the ordinary grub menu, and not the graphical one....

what I did:
sudo apt-get remove grub2 (as i had that package installed instead of grub)
installed the downloaded package and installed it (dpkg -i package.deb)
downloaded the message.ubugrey and moved it to the /boot/grub/ folder
gfxmenu /boot/grub/message.ubugrey --> this is the first line in my menu.lst
sudo grub

grub> find /boot/grub/stage1
 (hd0,0) # this will be the output
grub> root (hd0,0)
grub> setup (hd0)

and rebooted...

tried the grub-install /dev/sda too... allways the messages never errored whatsoever, always no problem, but never the graphical menu came...

Truely need some help, never had this before, a guide was most of the time clear and understandfull (and this one is too, but what's wrong i'm not sure :)

---

### Post by ayoli on 2007-09-05
> **RaZer0r said:**
> I need some help with this...
I can't get it to work, or I'm missing something, or I'm doing something wrong, but every time i reboot, i get the ordinary grub menu, and not the graphical one....

what I did:
sudo apt-get remove grub2 (as i had that package installed instead of grub)
installed the downloaded package and installed it (dpkg -i package.deb)
downloaded the message.ubugrey and moved it to the /boot/grub/ folder
gfxmenu /boot/grub/message.ubugrey --> this is the first line in my menu.lst
sudo grub

grub> find /boot/grub/stage1
 (hd0,0) # this will be the output
grub> root (hd0,0)
grub> setup (hd0)

and rebooted...

tried the grub-install /dev/sda too... allways the messages never errored whatsoever, always no problem, but never the graphical menu came...

Truely need some help, never had this before, a guide was most of the time clear and understandfull (and this one is too, but what's wrong i'm not sure :)

Did you do that at the end ?
```
sudo grub-install hdx,y
```
In your case it should be 0,0 for x,y (hda, first partition):
sudo grub-install hd0,0

---

### Post by RaZer0r on 2007-09-05
yes I allready did that too, without any results...

---

### Post by Yes on 2007-09-05
I did everything in the first post, plus 

```
sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst

grub-install /dev/hda
```

(Replacing hda with sda, which was what fdisk -l said my hard drive was).  Wen I rebooted, it just gave me the command prompt that you get when you type "sudo grub" in the terminal.  Any reason why this might be?

I should also mention that I'm running a clean install of Feisty (So I don't have any partitions left over from previous installations).

Ok, I just booted from the live CD, and now I can boot into Ubuntu.  Now this is what happens:  I get the same GRUB screen, except at the top it says the GRUB version.  When I chose the operation system, it says stuff like the kernal, root(0,0), initrd (I think that's what it was), and stuff like that.  Then it goes into the normal boot process.  So it seems as though what I've done has changed something, but I still don't have the graphics.  I'm using the message.blusplash, if that matters.

I tried running the sudo grub-install, and I got some errors.  First, I tried 

```
sudo grub-install /dev/hd0
```
(0 was the 'x' value for hd(x,y)).  That gave me the error

```
/dev/hd1: Not found or not a block device.
```
Then I tried using sdb (I'm connected to my network now, so my Ubuntu hard drive is sdb, not sda), and I got this error:

```
/dev/sdb1 does not have any corresponding BIOS drive.
```

Can anyone help me with these errors?

Thanks.

---

### Post by Malac on 2007-09-05
> **Yes said:**
> I did everything in the first post, plus 

```
sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst

grub-install /dev/hda
```(Replacing hda with sda, which was what fdisk -l said my hard drive was).  Wen I rebooted, it just gave me the command prompt that you get when you type "sudo grub" in the terminal.  Any reason why this might be?

I should also mention that I'm running a clean install of Feisty (So I don't have any partitions left over from previous installations).

Ok, I just booted from the live CD, and now I can boot into Ubuntu.  Now this is what happens:  I get the same GRUB screen, except at the top it says the GRUB version.  When I chose the operation system, it says stuff like the kernal, root(0,0), initrd (I think that's what it was), and stuff like that.  Then it goes into the normal boot process.  So it seems as though what I've done has changed something, but I still don't have the graphics.  I'm using the message.blusplash, if that matters.

I tried running the sudo grub-install, and I got some errors.  First, I tried 

```
sudo grub-install /dev/hd0
```(0 was the 'x' value for hd(x,y)).  That gave me the error

```
/dev/hd1: Not found or not a block device.
```Then I tried using sdb (I'm connected to my network now, so my Ubuntu hard drive is sdb, not sda), and I got this error:

```
/dev/sdb1 does not have any corresponding BIOS drive.
```Can anyone help me with these errors?

Thanks.
The last step should be this for you :
```
sudo grub-install hd0,0
```or possibly just:
```
sudo grub-install hd0
```There is no /dev/ if you are using grub notation, which is what this is if it uses numerals.

No corresponding BIOS drive usually means your computer BIOS can't boot off that drive/partition. Sometimes this is just a setting in the BIOS, other times it's hard coded.

Hope this helps

---

### Post by Yes on 2007-09-05
Shouldn't the numbers be the same numbers that I got when from "find /grub/stage1"?  So it would be "sudo grub-install hd1,0" ?

---

### Post by ayoli on 2007-09-05
> **Yes said:**
> Shouldn't the numbers be the same numbers that I got when from "find /grub/stage1"?  So it would be "sudo grub-install hd1,0" ?

yes it should, so yes it would if *find /grub/stage1* outputs *grub> root (hd1,0)*

---

### Post by Malac on 2007-09-05
> **ayoli said:**
> yes it should, so yes it would if *find /grub/stage1* outputs *grub> root (hd1,0)*
Sorry my mistake if that's the output of grub then that's it.

---

### Post by Yes on 2007-09-05
Well, I tried
```
sudo grub-install hd1,0
```

and I got the same
```
/dev/sdb1 does not have any corresponding BIOS drive.
```

error.  Any other ideas?

Thanks.

---

### Post by kvonb on 2007-09-05
> **Yes said:**
> Well, I tried
```
sudo grub-install hd1,0
```and I got the same
```
/dev/sdb1 does not have any corresponding BIOS drive.
```error.  Any other ideas?

Thanks.

Try doing the whole thing again, but use a pure root account instead.

sudo su

.....then go through the whole process again:

```
grub
  grub> find /boot/grub/stage1
     (hdx,y) # this will be the output
  grub> root (hdx,y)
  grub> setup (hdx)
  grub> quit
grub-install /dev/sdb1
```

If you get an error about stage2, run that last command a second time, it worked for me, and I have no clue why!

You should get:

```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'
```.

I'm still of the belief that it's something to do with having old partitions on your drive that were NOT created by the latest version of Ubuntu, ie left over from an earlier install.

Even ones created by the beta version of Feisty gave me problems, but if I wiped the entire drive and created new partitions it worked EVERY time!

The problem seems to stem from when they merged the IDE and SCSI drivers into the same lib (release of Feisty or last few updates to Feisty beta), ie we all of a sudden started calling /dev/hdx, /dev/sdx.

I have gfxboot working on all of my machines now, but I had to trash the partitions and create new ones. ](*,)

---

### Post by Yes on 2007-09-06
Well, for some reason this time the output for 
```
find /grub/stage1
```

was (hd0,0).  Anyways, I tried 
```
grub-install /dev/sdb1
```

, and it gave me the
```
/dev/hd1: Not found or not a block device.
```

error.  I tried 
```
grub-install hd0,0
```

and it said that the installation was completed successively, but when I restarted my computer, nothing had changed with GRUB.  

Also, it's not old partitions left over from previous installations, because I've only installed Ubuntu once on this computer.

Thanks for the help.

---

### Post by kvonb on 2007-09-06
OK, all I can suggest is to make sure that the message.xxxx that you are using (in /boot/grub) is set to be owned by root, group root.

Then have a look at /boot/grub/menu.lst and make sure that hiddenmenu IS commented out, like so:

#hiddenmenu

....and change the time to 10 seconds (not sure if that will make any difference though!)

Oh,and also colours:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color white/blue

Again not sure if it makes a difference, but that is from my menu.lst and it works :)

---

### Post by Yes on 2007-09-06
Yeah, all my settings are the same as yours, and my message.blusplash was owned by root.  Thanks, though.

What does the stuff in /boot/grub/devices.map do?  I switched the numbers, and that didn't seem to do anything at all.

---

### Post by kvonb on 2007-09-07
> **Yes said:**
> Yeah, all my settings are the same as yours, and my message.blusplash was owned by root.  Thanks, though.

What does the stuff in /boot/grub/devices.map do?  I switched the numbers, and that didn't seem to do anything at all.

No idea, but I think that file is created/modified when you do a grub-install.

GFXboot is problematic to say the least, I've had hit and miss success with it over the last year or so, and can't seem to find any rhyme or reason in it's workings :/

Here is EXACTLY what I did if it helps at all:

```
sudo apt-get remove grub
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
sudo cp message.ubugrey /boot/grub/
sudo chown root:root /boot/grub/message.ubugrey
sudo chmod 644 /boot/grub/message.ubugrey
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```....made sure that hiddenmenu was commented out, and 
also added: gfxmenu /boot/grub/message.ubugrey as the very first line.

```
sudo su
 grub
 grub>find /boot/grub/stage1
   (hd0,1)
 grub> root (hd0,1)
 grub> setup (hd0)
 grub> quit

fdisk -l
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/sda2             639        2351    13759672+  83  Linux
/dev/sda3            2352        2432      650632+   5  Extended
/dev/sda5            2352        2432      650601   82  Linux swap / Solaris

grub-install /dev/sda1
```  spat out some error about stage2!
```
 grub-install /dev/sda1
```  spat out:
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

Rebooted and it was there!

I attached a .gz file containing my fstab/device.map/message.ubugrey/menu.lst just in case you can get any useful info from them :)

---

### Post by Yes on 2007-09-07
Could anyone tell me where I want to install Grub (/dev/xxxxx) based on fdisk output?  I really don't want to overwrite my Windows MBR...

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+  83  Linux
/dev/sdb2           19263       19457     1566337+  82  Linux swap / Solaris
/dev/sdb3           18335       19262     7454160   83  Linux
/dev/sdb4              13       18334   147171465   83  Linux

Partition table entries are not in disk order
```

Thanks.

---

### Post by ayoli on 2007-09-07
> **Yes said:**
> Could anyone tell me where I want to install Grub (/dev/xxxxx) based on fdisk output?  I really don't want to overwrite my Windows MBR...

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+  83  Linux
/dev/sdb2           19263       19457     1566337+  82  Linux swap / Solaris
/dev/sdb3           18335       19262     7454160   83  Linux
/dev/sdb4              13       18334   147171465   83  Linux

Partition table entries are not in disk order
```

Thanks.

according to your fdisk output , you should do:
```
grub-install /dev/sda1
```
whath's the output for this ?
```
grub>find /boot/grub/stage1
```

---

### Post by Yes on 2007-09-07
```
grub>find /boot/grub/stage1
```

Gives me "Error 15: File not found".  
```
grub>find /grub/stage1
```

Gives me "hd(1,0)".

```
grub-install /dev/sda1
```
Gives me "/dev/sdb1 does not have any corresponding BIOS drive."

Thanks.

---

### Post by ayoli on 2007-09-07
> **Yes said:**
> ```
grub>find /boot/grub/stage1
```

Gives me "Error 15: File not found".  
```
grub>find /grub/stage1
```

Gives me "hd(1,0)".

```
grub-install /dev/sda1
```
Gives me "/dev/sdb1 does not have any corresponding BIOS drive."

Thanks.
Actually grub have not the same numeration as /dev
hd0 stands for hda or sda
hd1 for hdb or sdb
so in your case that should be (as root, or with sudo) :

```
grub-install hd1,0
```
or
```
grub-install /dev/sdb1
```

---

### Post by Yes on 2007-09-07
Nope, same errors.

---

### Post by Yes on 2007-09-09
Edit:  Success!!!!  I followed everything in [this](http://ubuntuforums.org/showpost.php?p=2827955&postcount=395) post, with a few changes:  Instead of 
```
find /boot/grub/stage1
```
I used
```
find /grub/stage1
```
instead of
```
sudo grub-install hdx,y
```
 I used 
```
sudo grub-install /dev/sda1
```
and instead of adding "gfxmenu /boot/grub/message.xxxx" to menu.lst, I added "gfxmenu /grub/stage1".

Thank you so much to everyone who helped =D .

---

### Post by sirsean1227 on 2007-09-12
well... thanks for having it make no sense..... like the menu.list... what part of it do i edit... i got to there.... had no f****** clue where to put the thing.... thanx for the half *** walk through... i hope i can restart this thing now!!!

---

### Post by 4tro on 2007-09-13
> **sirsean1227 said:**
> well... thanks for having it make no sense..... like the menu.list... what part of it do i edit... i got to there.... had no f****** clue where to put the thing.... thanx for the half *** walk through... i hope i can restart this thing now!!!

maybe you should read more carefully, and don't start yelling and ranting first....

---

### Post by franco07-chaosad on 2007-09-20
Thanks, it's great :)

---

### Post by WishMaster on 2007-09-26
erhm...

Your first 'command' is "[COLOR=DeepSkyBlue]remove grub[/COLOR]"
A few steps later, we need to type "[COLOR=DeepSkyBlue]grub[/COLOR]"
We just removed it??!

---

### Post by jw5801 on 2007-09-26
You remove the default grub and then install a graphical grub. That's what the second step is :p

---

### Post by Yes on 2007-09-26
I would highly suggest using the method laid out in this post: [http://ubuntuforums.org/showpost.php?p=2827955&postcount=395](http://ubuntuforums.org/showpost.php?p=2827955&postcount=395).  The OP's process seems to be missing a key step that gives a lot of people trouble.

---

### Post by ScarfaceIII on 2007-09-26
> **PingunZ said:**
> 
-- Howto make you own theme --


```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```

Reboot and enjoy ;)

Hi! Great How to, thanks. But: I got a question. I can't quite understand the part up here in quotes.  How do I edit your and build one mine? =)

Could you explain a little bit more, for example:
-why do I have to build a new directory if I don't enter it? (cd /home/name/whatever)
-what does the command cpio -i ? I don't know it, could you explain what happens?
- How do I edit pictures? And most of all, WHAT pictures? The output of the command cpio -i is just "250 blocks" and then? thanks, bye

---

### Post by 4tro on 2007-09-27
> **ScarfaceIII said:**
> Hi! Great How to, thanks. But: I got a question. I can't quite understand the part up here in quotes.  How do I edit your and build one mine? =)

Could you explain a little bit more, for example:
-why do I have to build a new directory if I don't enter it? (cd /home/name/whatever)
-what does the command cpio -i ? I don't know it, could you explain what happens?
- How do I edit pictures? And most of all, WHAT pictures? The output of the command cpio -i is just "250 blocks" and then? thanks, bye
you indeed have to enter the directory before you execute the cpio
the cpio command makes and reads a sort of archive of the files, a single file...

let's just say it's somewhat similar to tar... but don't use tar for this :P

---

### Post by WishMaster on 2007-09-27
> **jw5801 said:**
> You remove the default grub and then install a graphical grub. That's what the second step is :p
hmm... I uninstalled "grub" via Synaptic and installed "gfxboot" via Synaptic.

The proposed package here is "grub-gfxboot", I guess it is something different from the "gfxboot" in Synaptic

---

### Post by theff on 2007-09-30
EDIT: nevermind

---

### Post by light-angel on 2007-10-05
i've followed all in the guide you provided but still have no efect. When i boot i get the same ugly screen.

this is What i've done:

First remove your old grub

> 
sudo apt-get remove grub
Then Install the gfxboot-grub



> 
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
then we're going to move the message



> 
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded
Then edit your menu.lst



> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
and make it use gfxboot


> 
gfxmenu /boot/grub/message.suse # the suse can be replaced


Then do : 

> 
sudo grub
grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
-- Howto make you own theme --


Code:
> 
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new


---

### Post by mjpoetic on 2007-10-08
> **light-angel said:**
> i've followed all in the guide you provided but still have no efect. When i boot i get the same ugly screen.

I find the easiest way to use gfxboot is to:

**REMOVE OLD GRUB**
```
sudo apt-get remove grub
```**DOWNLOAD & INSTALL GRUB-GFXBOOT**
```
wget http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb
``````
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```[B]GET THE ANIMATED IMAGE & COPY IT TO YOUR GRUB DIRECTORY
[/B][SIZE=1][COLOR=Gray]***(You can also get some from gnome-look.org or from the bottom of post #1 in this thread)***[/COLOR][/SIZE]
```
wget http://quasarfreak.googlepages.com/message.suse
``````
sudo cp message.suse /boot/grub/
```[B]EDIT YOUR GRUB MENU TO USE THE ANIMATED IMAGE
[SIZE=1][COLOR=Gray](good practice to backup the file first and then edit)[/COLOR][/SIZE]
[/B]```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``````
sudo gedit /boot/grub/menu.lst
```[B]ADD THE FOLLOWING LINE (IN RED) TO THE TOP OF THE FILE SO IT LOOKS LIKE THIS...
[/B]```
[COLOR=Red]**gfxmenu /boot/grub/message.suse**[/COLOR]
[COLOR=Gray]
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.[/COLOR]
```[B]THEN, INSTALL THE BOOT-LOADER
[SIZE=1][COLOR=Gray](this may vary based on your computer)[/COLOR][/SIZE]
[/B]```
sudo grub-install hd0
```[B]
OR 
[/B]```
sudo grub-install /dev/sda
```

:KS:KS:KS
[B]ENJOY!!!  [I]Keep in mind that this is just a template and you can edit it to your liking.  Also, these are general instructions but you may have to edit the lines to fit your computer.

Check out the GRUB editing script called "GrubEd" as it will help with this too:
[http://ubuntuforums.org/showthread.php?t=228104&highlight=Script+for+grub](http://ubuntuforums.org/showthread.php?t=228104&highlight=Script+for+grub)
[/I][/B]

---

### Post by Sonic Reducer on 2007-10-25
i have followed the instructions twice, and i still get the default GRUB setup.

heres some terminal outputs:

Removed GRUB: (keep in mind i did all this three reboots ago, so these terminal commands are in past-tense)
```
ryan@ryan-desktop:~$ sudo apt-get remove grub
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Dpkg'ed grub-gfxboot:
```
ryan@ryan-desktop:~$ sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
(Reading database ... 129013 files and directories currently installed.)
Preparing to replace grub-gfxboot 0.97-5 (using grub-gfxboot_0.97-5_i386.deb) ...
Unpacking replacement grub-gfxboot ...
Setting up grub-gfxboot (0.97-5) ...
```

moving message.blusplash:
```
sudo cp message.suse /boot/grub/
```

Backed up and editing menu.lst:
```
ryan@ryan-desktop:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
ryan@ryan-desktop:~$ sudo gedit /boot/grub/menu.lst
```

here is my menu.lst (note the first line, did i do that right?):
```
gfxmenu /boot/grub/message.blusplash
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cf3dbb90-6e5d-4560-a89a-6b1ebdc01697 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf3dbb90-6e5d-4560-a89a-6b1ebdc01697 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cf3dbb90-6e5d-4560-a89a-6b1ebdc01697 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf3dbb90-6e5d-4560-a89a-6b1ebdc01697 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cf3dbb90-6e5d-4560-a89a-6b1ebdc01697 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

then i sudo GRUB'ed:
```
ryan@ryan-desktop:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
```

```

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> grub> find /boot/grub/stage1 **(NOTE: this was a copy/pasting typo)**

Error 27: Unrecognized command

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
```

i followed all this a third time in order to get the text to copy/paste here, i'm going to reboot again right after i post this. if i don't post again sounding very embarrassed assume it is still not working. thank you for anyone that can help me.

---

### Post by mjpoetic on 2007-10-25
Everything looks fine except for one thing: I see you have **message.blusplash **instead of **message.suse** which you have earlier in the instructions...just make sure that you are using the correct one.

Also, I really recommend using **sudo grub-install** rather than **sudo grub**.  I have never had to use **sudo grub**.  So in your case, just do

```
sudo grub-install hd0
```

then your problem should go away

---

### Post by Sonic Reducer on 2007-10-26
> **mjpoetic said:**
> Everything looks fine except for one thing: I see you have **message.blusplash **instead of **message.suse** which you have earlier in the instructions...just make sure that you are using the correct one.

i want to use the blusplash (which is one of the alternatives listed in the bottom of the first post of this thread)

i did the **sudo grub-install hd0** in the terminal and this came up:
```
ryan@ryan-desktop:~$ sudo grub-install hd0
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
```

so i hope this worked. thank you for the help

---

### Post by mjpoetic on 2007-10-26
Yea it should work.  In fact that message is for you to check if you wanted it to go to that specific boot sector or another.  Without confusing the situation, I think you got what you needed to get done.

---

### Post by Sonic Reducer on 2007-10-26
it looks so freaking cool. thank you PingunZ!

---

### Post by #Reistlehr- on 2007-11-04
anyone know a good tutorial, or the file format that these grubgfx images use?

---

### Post by satsura on 2007-11-09
Hi!
Pls, tell me, how delete bottom text in grub?
[[IMG]http://img223.imageshack.us/img223/1152/102431mv5.th.jpg[/IMG]](http://img223.imageshack.us/my.php?image=102431mv5.jpg)

---

### Post by 4tro on 2007-11-11
> **satsura said:**
> Hi!
Pls, tell me, how delete bottom text in grub?
[[IMG]http://img223.imageshack.us/img223/1152/102431mv5.th.jpg[/IMG]]("http://img223.imageshack.us/my.php?image=102431mv5.jpg")

follow the how to on page 1, what you have here is a standard grub with splashimage, not gfxboot-grub
in gfxboot the text is gone

---

### Post by shinji257 on 2007-11-11
> **PingunZ said:**
> Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```


When I do this I get the message "Error 15: File Not Found".  Why am I getting this error and what can I do to resolve this?  This is a relatively new install.  Grub boots just fine otherwise.

This is a new install of Ubuntu.  I'll try another install inside of a virtual machine and see where it goes with that so I don't mess up the current one badly.  Thanks for any assistance.

P.S. - This is Ubuntu Gutsy 7.10 that I am running.  It is dual booting with Windows XP right now.  I can post the menu.lst if you want.  On that note I might just try a reinstall anyways and see if it corrects it by combining the boot and root partitions together...

EDIT: Nevermind on this.  I reinstalled Ubuntu taking a new partiton layout and now I don't have this issue anymore.  My partition layout was originally as follows

47MB Dell Diag (primary)
200GB Windows XP (primary - active)
100MB /boot (primary)
500MB Mozilla profile space (logical)
29GB / (logical)
1GB swap (logical)

This was done to keep the boot area from getting too big or out of hand.  Now for some reason it doesn't work.  The root was set to (hd0,2) which is correct but grub didn't like it.  So I changed it to this...

47MB Dell Diag (primary)
200GB Windows XP (primary)
29GB / (primary)
500MB Mozilla profile space (logical)
1GB swap (logical)

And now I don't get that error anymore.  I'm going to apply the updates and see what happens from here...

EDIT: I got it working.  The error reappeared as soon as I installed gfxboot but I went ahead and tried to do it anyways.  I reinstalled the boot loader and it works fine now.  I also had backed up the update-grub files from both /sbin and /usr/sbin and then restored it after installing gfxboot.

---

### Post by 4tro on 2007-11-13
> **shinji257 said:**
> When I do this I get the message "Error 15: File Not Found".  Why am I getting this error and what can I do to resolve this?  This is a relatively new install.  Grub boots just fine otherwise.

This is a new install of Ubuntu.  I'll try another install inside of a virtual machine and see where it goes with that so I don't mess up the current one badly.  Thanks for any assistance.

P.S. - This is Ubuntu Gutsy 7.10 that I am running.  It is dual booting with Windows XP right now.  I can post the menu.lst if you want.  On that note I might just try a reinstall anyways and see if it corrects it by combining the boot and root partitions together...

EDIT: Nevermind on this.  I reinstalled Ubuntu taking a new partiton layout and now I don't have this issue anymore.  My partition layout was originally as follows

47MB Dell Diag (primary)
200GB Windows XP (primary - active)
100MB /boot (primary)
500MB Mozilla profile space (logical)
29GB / (logical)
1GB swap (logical)

This was done to keep the boot area from getting too big or out of hand.  Now for some reason it doesn't work.  The root was set to (hd0,2) which is correct but grub didn't like it.  So I changed it to this...

47MB Dell Diag (primary)
200GB Windows XP (primary)
29GB / (primary)
500MB Mozilla profile space (logical)
1GB swap (logical)

And now I don't get that error anymore.  I'm going to apply the updates and see what happens from here...

EDIT: I got it working.  The error reappeared as soon as I installed gfxboot but I went ahead and tried to do it anyways.  I reinstalled the boot loader and it works fine now.  I also had backed up the update-grub files from both /sbin and /usr/sbin and then restored it after installing gfxboot.

the error was that your stage1 wasn't located at /boot/grub/stage1 , but probably at /grub/stage1 on the partition mounted as /boot, there's a difference there

---

### Post by shinji257 on 2007-11-13
> **4tro said:**
> the error was that your stage1 wasn't located at /boot/grub/stage1 , but probably at /grub/stage1 on the partition mounted as /boot, there's a difference there

That was just it.  I had tried that one too.  Both /boot/grub/stage1 and /grub/stage1 produced this error.  Regardless I did get it working and it works great now.  Thanks for the reply though!

---

### Post by lotacus on 2007-11-22
Am I missing something here? I am reading posts that describe commands and such that are not even listed in the tutorial. Is the tutorial incomplete? I find it amazing that there are 49 pages of posts for a small installation of gfxboot, which for the most part doesn't seem to work on a whole lot of systems. mine, being one of them.  Of couerse I do understand that every system, kernel and distros may be different, but seeing as this is posted in the ubuntu forums, i would expect the tutorial somewhat generic. I see nothing about grub or grub2 install/remove etc.. in the tutuorial, perhaps it can be modified to include a little more then what is already there.

my "grub" hd0,5 however when I "find" grub and then do the sudo grub hd0,5 I see some out put of Sda... wierd

---

### Post by Eriksmits596 on 2007-12-03
I have done EXACTLY as I should and tried 3 times but it's still the old menu. What do I do wrong :( Here's my menu.lst 

P.S. I run gutsy

> # gfxmenu /boot/grub/message.new
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e97d6f4c-9a37-465c-bbdf-298d4f0ce66c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e97d6f4c-9a37-465c-bbdf-298d4f0ce66c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e97d6f4c-9a37-465c-bbdf-298d4f0ce66c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by 4tro on 2007-12-04
> **Eriksmits596 said:**
> I have done EXACTLY as I should and tried 3 times but it's still the old menu. What do I do wrong :( Here's my menu.lst 

```
                              
# gfxmenu /boot/grub/message.new
# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
```P.S. I run gutsy

uncomment the                               # gfxmenu /boot/grub/message.new

---

### Post by Eriksmits596 on 2007-12-04
Haha I forgot to do grub-install after:p But now it works!!! Nice

---

### Post by Eriksmits596 on 2007-12-05
Somebody who knoms where I can find this theme?
[IMG]http://www.pro-linux.de/berichte/jpgs/suse10/suse10-boot.jpg[/IMG]

---

### Post by PurposeOfReason on 2007-12-05
I got it to work, but it doesn't take up my full resolution (1280x800) but more is just a centered 800x600. The VGA= options didn't change anything and I even tried resizing the images in the theme.

---

### Post by merlwiz79 on 2007-12-08
Here is a new one I compiled.
[[IMG]http://farm3.static.flickr.com/2094/2097093584_776e7ffe38.jpg[/IMG]]("http://farm3.static.flickr.com/2094/2097093584_78763709de_o.png")
message.red
[http://www.4shared.com/file/31585981/9e6e2573/message.html](http://www.4shared.com/file/31585981/9e6e2573/message.html)
**Source:**
[http://www.4shared.com/file/31936439/693eb95d/gfxboot-theme-example.html]("http://www.4shared.com/file/31936439/693eb95d/gfxboot-theme-example.html")

---

### Post by autocrosser on 2007-12-09
> **Eriksmits596 said:**
> Somebody who knoms where I can find this theme?

I pulled the theme info from the 10.2 install disc--but don't know how to compile it--you might find someone that has 10.2 installed & get the message from them---The file is too big to post--E me if you want the source.....

EDIT: I found the answer on linuxforums.org--- this uses the message.suse that comes with 10.2---

In /boot/message there is a configuration file that controls the randomness of the "walking penguins". However /boot/message is an [archive]("http://www.linuxforums.org/forum/#") and you have to decompress.
Open a terminal and  Code:
 su
cd /boot
cp message message.old
mkdir messagetemp
cd messagetemp
cpio -iv < /boot/message
nano gfxboot.cfg 
Then you should change penguin from -1 to 100
it should look like this Quote:
                                 penguin=100                         
Save and recreate the archive
  Code:
 ls | cpio -ov > /boot/message 
This should be ok. Post if any problems



I have the message & will post it as message.zip

just remove the .zip & do what you need to do to get it in your boot---adapt the instructions above to your use...

EDIT2: message.peng.zip I THINK will work--remove the .zip & insert it--I'll do a reboot with it & report if it works....

EDIT3: gfxboot said that the message is too big--I would guess that it needs to have some of the Suse stuff to work--I'll play with it----

EDIT4: Well--I shrunk the message down to 271k & it still won't work :(  I'll try some more this week--I guess that the GfxBoot Suse uses allows bigger file sizes---

---

### Post by silverdarkness on 2007-12-11
Edit gfxboot themes for widescreen:

1)
extract the files using the commands from pg 1
```

mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
```

2) Open one of the image in gimp. Under image choose scale image and unlock the aspect ratio.

3) You need to shrink the image so when it gets stretched to full screen it looks normal. The new image width is 0.83x the original image width. Calculate the new image width put it in and click scale. Save the image

4) Do the same for any other images.

5) Put the files back in the message file using:
```
sudo ls . |cpio -o > /boot/grub/message.whatever
``` (from pg 1 again)

Thats it. The text will still be elongated but i dont really mind.

---

### Post by merlwiz79 on 2007-12-13
**grub-gfxboot 0.97-11 for Ubuntu i386**
[http://www.gnome-look.org/content/show.php/grub-gfxboot+for+Ubuntu+i386?content=71647]("http://www.gnome-look.org/content/show.php/grub-gfxboot+for+Ubuntu+i386?content=71647")

Can't make amd64 if someone want's I can sent the soucre for the amd64 to make into .debs.

---

### Post by merlwiz79 on 2007-12-13
> **autocrosser said:**
> 
EDIT4: Well--I shrunk the message down to 271k & it still won't work :(  I'll try some more this week--I guess that the GfxBoot Suse uses allows bigger file sizes---Needs to be less than 170 kbs.

---

### Post by autocrosser on 2007-12-13
> **merlwiz79 said:**
> Needs to be less than 170 kbs.

Interesting--the "stock" message that comes with 10.2 is about 370k--any idea about what makes their GFXboot work with larger file sizes?

---

### Post by neoraptor on 2007-12-14
Is it possible to put a 1920x1200 image?

---

### Post by subs on 2007-12-14
cool!!!

---

### Post by merlwiz79 on 2007-12-14
> **neoraptor said:**
> Is it possible to put a 1920x1200 image?
It depends on the back.jpg.
The end file has to be less than 170k so it won't look that good.
Here is the same back.jpg from message.red but resized @ 1920x1200.
[http://www.4shared.com/file/32068519/641202fe/message.html]("http://www.4shared.com/file/32068519/641202fe/message.html")

---

### Post by merlwiz79 on 2007-12-14
I have compiled another one.
It has an Ubuntu version as well.
[http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735]("http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735")
[[IMG]http://farm3.static.flickr.com/2058/2111749660_a6cfa2c15c.jpg[/IMG]]("http://farm3.static.flickr.com/2058/2111749660_64a9125986_o.png")

---

### Post by kryth on 2007-12-15
Okay, I've had it. I admit it, I'm slightly ubuntu retarded and can't get this for the life of me.  Can anymore personalize these parts for me.  I've been trying and trying. And have read the first 20 or so pages and last 5 of this thread. But i'm giving in, and need some help.

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)  


grub-install /dev/hda????

my fdisk -l


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14         673     5295104    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1956       19457   140584815    7  HPFS/NTFS
/dev/sda4             674        1955    10297665    5  Extended
/dev/sda5   *         674        1700     8249346   83  Linux
/dev/sda6            1701        1955     2048256   82  Linux swap / Solaris

find /boot/grub/stage1 returns hd0,4...which seems wrong


give a poor sap a clue?

thanks

---

### Post by kryth on 2007-12-15
Never mind. I finally figured it out.

---

### Post by fooman on 2007-12-16
> **merlwiz79 said:**
> I have compiled another one.
It has an Ubuntu version as well.
[http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735]("http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735")
[[IMG]http://farm3.static.flickr.com/2058/2111749660_a6cfa2c15c.jpg[/IMG]]("http://farm3.static.flickr.com/2058/2111749660_64a9125986_o.png")


sweet!  ....thanks merlwiz.  =D>

---

### Post by merlwiz79 on 2007-12-17
> **fooman said:**
> sweet!  ....thanks merlwiz.  =D>
No problem.
If any one has suggestions for other gfxboot menus, post them here or at the link.

---

### Post by jingo811 on 2007-12-17
OK I'm dyslectic so I can never follow any instructions correctly without doing something wrong in between the steps.  Can somebody point out what exactly I'm doing wrong.
I've tested it on Debian Etch which failed so now I'm finally testing it on Ubuntu Feisty.  Using this kernel version.
```
bill@gates:~$ uname -r
2.6.20-16-generic
```

These are the steps I've done, which doesn't work at all.  Also in case there was something wrong with message.suse I also tried the same procedures with message.ububrown


**1.)**
I downloaded these files which was shown on the first page.
[http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)
[http://quasarfreak.googlepages.com/message.suse](http://quasarfreak.googlepages.com/message.suse)

**2.)**
```
sudo apt-get remove grub
```

**3.)**
Then I navigated to the folder where the gfxboo_0.97*.deb file is located and did this.
```
dpkg -i grub-gfxboot_0.97-5_i386.deb
```

**4.)**
```
cp message.ububrown /boot/grub
```

**5.)**
```
cp /boot/grub/menu.lst menu.lst_backup
```

**6.)**
```
nano /boot/grub/menu.lst
```
And added this to the very top of the menu.lst file:
> 
**gfxmenu /boot/grub/message.ububrown**

# menu.lst - See: grub('8'), info grub, update-grub('8')
#            grub-install('8'), grub-floppy('8'),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
...
...



**7.)**
```
$ sudo grub
```

**8.)**
```
grub> **find /boot/grub/stage1**
 (hd0,1)

grub> **root (hd0,1)**
 Filesystem type is ext2fs, partition type 0x83

grub> **setup (hd0)**
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> **quit**

```

**9.)**
This didn't work!
```
bill@gates:~/src/GfxBoot$ **sudo grub-install /dev/hd0**
[COLOR="Red"]/dev/hd0: Not found or not a block device.[/COLOR]
```

**10.)**
I also navigated to where the file was in /boot/grub and chmodded it.  No difference!
```
sudo chmod 755 message.ububrown 
```

**11.)**
```
$ sudo reboot
```

Nada, zilch, nein, no nothing GRUB remains unmodified :confused: help please.

---

### Post by merlwiz79 on 2007-12-17
It should be **sudo grub-install /dev/hda **or **sudo grub-install /dev/sda**.
Everything else looks fine.

---

### Post by jingo811 on 2007-12-17
Tnx merlwiz79 that solved it for me!  The author of this thread should really put that in the first page tutorial so ppl don't have to read through 50 pages of threads before finding this out.

Next can someone link all the information needed to make your own customized GfxBoot.  Reading this long technical document isn't really my tea of cup.  Nor do I know how to read german.
usr/share/doc/gfxboot/gfxboot.html

> **kno said:**
> sudo apt-get install gfxboot gfxboot-theme-ubuntu

then you'll find  help and examples (to compile ;) ) in :
/usr/share/doc/gfxboot/
/usr/share/gfxboot/themes/

A tutorial :
[http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html]("http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html")

I like visual tutorials.  Until then I guess I'll try swapping the images in the message.suse file the Footissimo way.

---

### Post by CypherHackz on 2007-12-22
> **Footissimo said:**
> Made a mod of the SuSE GFXBoot theme.  Basically its a mash up of [this SVG icon](http://www.gnome-look.org/content/show.php?content=42245) by Sairitupac Vasquez and [this wallpaper](http://www.gnome-look.org/content/show.php?content=41588) by Paul Beyens.

I know nothing about QEMU, EMU or any flightless birds so I just took a screenie with me mobile.  If some kind person fancies running it through a virtual PC thingy and doing a screenie then that would be much appreciated. (thanks Kno)  There are two problems with it:

1) There is a slight artifact around the ubuntu icon - I've spent hours brushing to minimise JPG artifacts, but there's only so much I can do..it should be barely noticeable now.  Its due to the complexity of the background - if people like this then I'll do another on a plainer background and get the logo 100%

2) The original SuSE theme screws up a little if you scroll down the kernel / OS options - seems to be because that panel needs to be shoved to the left a bit or made into 1024x768 rather than 800x600.  Mine does the same...it doesn't effect functionality or anything, but if I do another, then I'll correct it (it was too late by the time I noticed it on this one).

Installing:

After doing all the GFXBoot palaver, just unzip the theme and copy it to /boot/grub/ then add ```
gfxmenu /boot/grub/message.ubugrey
``` to the top of the /boot/grub/menu.lst file.  Presumably you should remove any other themes you have there (such as message.suse)


I really like your image mate. But it displays Ubuntu 6.06 LTS Professional Edition at the bottom. Can you remove that text? Is it possible? :D

-cypher.

---

### Post by CypherHackz on 2007-12-25
i have make my own theme for gfxboot, but the file size is too big. how to reduce it? anyone knows how?

Edit 1:
I think i know why the file size is large. After you package back the theme, try open your message.* with Archive Manager. There you will see file message.* in the package. I tried to delete that file but it doesn't allow me to delete it. So how to delete that file?

Edit 2:
Found out the solution. Create the archive into another directory. So it will not archive it self.

-cypher.

---

### Post by bngguy on 2007-12-25
Hello,
        I was playing around with the gfxmenu message, i created a new one which is 166KB, i remember reading in this forum that it should be less than 170KB, so i edited my menu.lst file to load the new message, and when i rebooted i get a blank screen and it just stays there no menu no nothing, fortunately i have a copy of the LIVE CD, but to edit the menu.lst file i need to be root.

So my question is , how to get root privileges while running the LIVE CD??, is it possible or is there any other way to edit teh menu.lst file to point to a new message while runnning the LIVE CD.

I would really appreciate a response.

Happy Holidays
Av

---

### Post by bngguy on 2007-12-25
Never Mind i figured it out.

> **bngguy said:**
> 
Hello,
        I was playing around with the gfxmenu message, i created a new one which is 166KB, i remember reading in this forum that it should be less than 170KB, so i edited my menu.lst file to load the new message, and when i rebooted i get a blank screen and it just stays there no menu no nothing, fortunately i have a copy of the LIVE CD, but to edit the menu.lst file i need to be root.

So my question is , how to get root privileges while running the LIVE CD??, is it possible or is there any other way to edit teh menu.lst file to point to a new message while runnning the LIVE CD.

I would really appreciate a response.

Happy Holidays
Av

---

### Post by CypherHackz on 2007-12-26
Mind to share how you did it?

-cypher.

---

### Post by Sonic Reducer on 2007-12-27
> **CypherHackz said:**
> i have make my own theme for gfxboot, but the file size is too big. how to reduce it? anyone knows how?

don't put as much crap on it? ;)

you could try saving the image in a lower resolution or quality. it won't look as clean but the same general image will be there, but smaller. try doing as little as possible each time and check the size after you resave it. once you hit the upper limit you'll have the best quality image you can get

---

### Post by CypherHackz on 2007-12-27
i have managed reduce the size. it was because i compile back the message in the same diectory. that is why the file gets bigger. but new problem found, the image does not display properly when boot. the image change into dots like my graphic is broken but it is not.

i think it is because i need to save the image using certain DPI but don't remember what is the DPI to be used for the image. but the size is still remains the same, 800x600.

-cypher.

---

### Post by DuKe2112 on 2007-12-28
So, now I have a nice graphic Grub, but once I choose the kernel the graphics disappear and Grub makes some textoutput, before loading ubuntu.
Also bevore Grub actually starts it displays a message, Grub loading.

Is it possible to disable these message outputs?

What id like to have is a fluent transition from Bootsplash to Gfxboot menu to Ubuntu load screen. (I could life with black screens in between.

---

### Post by merlwiz79 on 2007-12-31
I have made 2 new gfxboot menus with source code.
[http://www.gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720](http://www.gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720)
[IMG]http://www.gnome-look.org/CONTENT/content-pre2/72720-2.png[/IMG]

Has the info of what was changed from last message.red
[http://www.gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668](http://www.gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668)
[IMG]http://www.gnome-look.org/CONTENT/content-pre1/71668-1.png[/IMG]

---

### Post by pavel989 on 2008-01-02
hi I'm having a big issue here.
I've followed the installation directions, grub still works, but i don't get a graphical screen

i think my partition might be messed up but grub install apparently doesn't like it
```
pavel@pavel-desktop:~$ sudo grub-install /dev/hd0
/dev/hd0: Not found or not a block device.
pavel@pavel-desktop:~$ sudo grub-install /dev/hd1
/dev/hd1: Not found or not a block device.

```

---

### Post by erginemr on 2008-01-03
> **pavel989 said:**
> hi I'm having a big issue here.
I've followed the installation directions, grub still works, but i don't get a graphical screen

i think my partition might be messed up but grub install apparently doesn't like it
```
pavel@pavel-desktop:~$ sudo grub-install /dev/hd0
/dev/hd0: Not found or not a block device.
pavel@pavel-desktop:~$ sudo grub-install /dev/hd1
/dev/hd1: Not found or not a block device.

```

Can you please post your "/etc/fstab" file here?

---

### Post by chewearn on 2008-01-03
> **merlwiz79 said:**
> I have made 2 new gfxboot menus with source code.
[http://www.gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720](http://www.gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720)


Has the info of what was changed from last message.red
[http://www.gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668](http://www.gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668)


That's very nice.:popcorn:

Would you mind giving some instructions how to compile the source codes (in the links), thanks.

---

### Post by applegrew on 2008-01-03
This thread is great but is this still applicable for Gusty Gibbon? I need to be sure before I continue. I am really confused about the gfx themes in Gusty's repo, e.g. the gfxboot-theme-suse package. Is the grub of Kubuntu Gusty Gibbon 7.10 already patched for gfx? If not then what these gfx theme packages doing in the repo? Pls, reply I want to get rid of the dull boot screen as soon as I can, but will can't continue unless I settle this doubt of mine.

---

### Post by applegrew on 2008-01-03
Anybody listening?

---

### Post by Sonic Reducer on 2008-01-03
> **applegrew said:**
> Anybody listening?

well it worked for me

---

### Post by pavel989 on 2008-01-03
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=78CB-9F80  /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c212304f-633c-4f1b-ad3e-0f69c3e118d7 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by applegrew on 2008-01-04
> **Sonic Reducer said:**
> well it worked for me
Hi,

Thanks for replying. My actual doubt is grub installed by Gusty has gfx already patched or not?

---

### Post by Morton's Red Stapler on 2008-01-04
ok, i am having a problem creating the new message.whatever, when i run the command ```
sudo ls . |cpio -o > /boot/grub/message.new
``` it gets into the folder, but it is creating another archive, within the archive, so if i name message.new, it creates another inside of it with the same name, and doubls the file size. why???? and how the hell can i fix this?

---

### Post by chewearn on 2008-01-04
> **Morton's Red Stapler said:**
> ok, i am having a problem creating the new message.whatever, when i run the command ```
sudo ls . |cpio -o > /boot/grub/message.new
``` it gets into the folder, but it is creating another archive, within the archive, so if i name message.new, it creates another inside of it with the same name, and doubls the file size. why???? and how the hell can i fix this?

When you extract the archive with:
```
cpio -i < message.old
```
did you delete message.old after that?  Else, when you subsequently run the cpio -o part, the message.old got into message.new

---

### Post by chewearn on 2008-01-04
> **applegrew said:**
> Hi,

Thanks for replying. My actual doubt is grub installed by Gusty has gfx already patched or not?

My guess is no.

But it's easy to confirm; just add line:
gfxmenu /boot/grub/message.suse

to first line of menu.lst; then copy message.suse to /boot/grub/

Skip the other steps to replace grub to gfxboot.  See if you suddenly boot with a graphical menu.

---

### Post by erginemr on 2008-01-04
> **pavel989 said:**
> hi I'm having a big issue here.
I've followed the installation directions, grub still works, but i don't get a graphical screen

i think my partition might be messed up but grub install apparently doesn't like it
```
pavel@pavel-desktop:~$ sudo grub-install /dev/hd0
/dev/hd0: Not found or not a block device.
pavel@pavel-desktop:~$ sudo grub-install /dev/hd1
/dev/hd1: Not found or not a block device.

```

> **pavel989 said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=78CB-9F80  /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c212304f-633c-4f1b-ad3e-0f69c3e118d7 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Apparently, you are trying to re-install grub to /dev/hd0, but you need to install it to /dev/hda instead according to the following thread:

[http://ubuntuforums.org/archive/index.php/t-56668.html](http://ubuntuforums.org/archive/index.php/t-56668.html)

> When installed, Windows will overwrite the MBR with its own information. Some users have experienced that Windows won't even boot after being installed (apparently the MBR can become corrupted when NTLDR is installed on top of Grub).

In any event, the solution is to have Grub write its information to the MBR again, after you have installed Windows (or you can back up the MBR, but that's probably more of an effort).

To make a boot disc (so you can boot Ubuntu after installing Windows), write:
sudo grub-install '(fd0)'
in the terminal (have a formated disc in the floppy drive -- and make sure it works before reinstalling Windows).

When Windows is reinstalled, boot Ubuntu with your boot disc, and then write
sudo grub-install /dev/hda
in the terminal (given your primary master is indeed hda). Everything should now be back to normal.

NB. Things can go wrong, so make backups of your important files before doing anything!

Edit: Forgot the sudo thing ...

But this is irrelevant anyway, as you are trying to install gfxboot, whereas the above technique is proposed to restore the original grub.

---

### Post by erginemr on 2008-01-04
With reference to the following HOWTO:

[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

> Howto : GfxBoot ( Grub like suse )
Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one
Ok, let's start

Download the grub-gfxboot.deb
And the message.suse

First remove your old grub
```
sudo apt-get remove grub
```

Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```

then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded
```

Then edit your menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced
```

```
sudo grub
```

```
grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```


I would recommend you to follow this method mot-à-mot, which was also the one I used, to reinstall gfxboot. Following the above steps, I first uninstalled grub, installed gfxboot, and then, found a nice, sleek GFXBoot menu:

[http://www.gnome-look.org/content/show.php/gulliver+Ubuntu+GFXBoot+Grub+Theme?content=57145](http://www.gnome-look.org/content/show.php/gulliver+Ubuntu+GFXBoot+Grub+Theme?content=57145)

Then follow the above steps in order. I believe your final grub commands should be something like:

```
grub> root (hd0,0)
grub> setup (hd0)
```

because your /etc/fstab file says that your Linux root (ext3) drive is "hda1", your primary (and only) harddisk, which corresponds to (hd0,0). In this respect, your master boot record (MBR) will be (hd0), where grub will be installed.

---

### Post by Morton's Red Stapler on 2008-01-04
> **AstalaVista said:**
> When you extract the archive with:
```
cpio -i < message.old
```
did you delete message.old after that?  Else, when you subsequently run the cpio -o part, the message.old got into message.new

i cd to the folder where i am making th new gfxboot, then i run the command, the only files there are the images, and the text/config files needed to run the boot. the problem is that it is creating the archive, and inside the archive, there is a second archive of the same name.:confused:

---

### Post by Dropknee on 2008-01-06
I follow everything but when I go to this step:

```
sudo grub
```

I got this

dropknee@Drop-Ubuntu-PC:~$ sudo grub
sudo: grub: command not found

Im doing something wrong???

I install the gfxboot from synaptic, is this the same to the package provide by the author of this thread???

Thanks

---

### Post by Dropknee on 2008-01-06
Never mind, I figurate out, I uninstall the gfxboot from synaptic and install the one provided by the author and now all work like a charm.

---

### Post by sigot on 2008-01-07
Hello, I have an 1 problem, all OK, but my grub is still black-white. I think that I dont know where must be gfxmenu ...........messag.suse written to menu.lst. Everything I was installed propertly, but.... I dont know.:confused:

---

### Post by erginemr on 2008-01-07
> **sigot said:**
> Hello, I have an 1 problem, all OK, but my grub is still black-white. I think that I dont know where must be gfxmenu ...........messag.suse written to menu.lst. Everything I was installed propertly, but.... I dont know.:confused:

And you have copied the corresponding message.* file to /boot/grub/ as shown in the attachment??

---

### Post by DuKe2112 on 2008-01-09
Does anyone know how to create themes directly with gfxboot?

Just repacking with cpio gives me a black background with white dots.

---

### Post by Dark Star on 2008-01-17
> gfxmenu /boot/grub/message.suse

Where to add this line /

---

### Post by mrfuzzemz on 2008-01-17
For anyone still trying to get gfxboot working, I would recommend trying out startupmanager instead.  You can use any image as a grub background.

To install:

```
sudo apt-get install startupmanager
```

---

### Post by Dark Star on 2008-01-17
> **mrfuzzemz said:**
> For anyone still trying to get gfxboot working, I would recommend trying out startupmanager instead.  You can use any image as a grub background.

To install:

```
sudo apt-get install startupmanager
```
Thanks but where to add that line ?

---

### Post by mrfuzzemz on 2008-01-17
> **Dark Star said:**
> Thanks but where to add that line ?

Just enter it as a command in a terminal.

---

### Post by Dark Star on 2008-01-17
> **mrfuzzemz said:**
> Just enter it as a command in a terminal.
```
shashwat@shashwat-desktop:~$ sudo gfxmenu /boot/grub/message.blusplash
sudo: gfxmenu: command not found
shashwat@shashwat-desktop:~$ 

```

---

### Post by mrfuzzemz on 2008-01-17
> **Dark Star said:**
> ```
shashwat@shashwat-desktop:~$ sudo gfxmenu /boot/grub/message.blusplash
sudo: gfxmenu: command not found
shashwat@shashwat-desktop:~$ 

```

Umm...  That's not quite what I meant.  The command above (sudo apt-get install startupmanager) is to install Startup Manager.  Then you run it by going to System >> Administration >> Startup Manager.

---

### Post by Dark Star on 2008-01-17
> **mrfuzzemz said:**
> Umm...  That's not quite what I meant.  The command above (sudo apt-get install startupmanager) is to install Startup Manager.  Then you run it by going to System >> Administration >> Startup Manager.
I know that but that doesn't enable gfx boot :x

---

### Post by mrfuzzemz on 2008-01-17
> **Dark Star said:**
> I know that but that doesn't enable gfx boot :x

That's because it isn't gfxboot.  I never said it would enable the package or configuration gfxboot.  It is an alternative.  With startup manager you can create a background image for grub just like is doable with gfxboot.

---

### Post by Dark Star on 2008-01-17
Repeating my question 

> gfxmenu /boot/grub/message.suse

Where to add this line /

---

### Post by mrfuzzemz on 2008-01-17
> **Dark Star said:**
> Repeating my question 



Where to add this line /

That should be added to the top of:

/boot/grub/menu.lst

---

### Post by jw5801 on 2008-01-17
> **Dark Star said:**
> Where to add this line /

You need to add it to the start of the file /boot/grub/menu.lst

Open the file for editing with```
gksu gedit /boot/grub/menu.lst
```then copy and paste into the first line:```
gfxmenu /boot/grub/message.suse
```Then save and exit and continue with the HowTo.

---

### Post by jw5801 on 2008-01-17
> **mrfuzzemz said:**
> That's because it isn't gfxboot.  I never said it would enable the package or configuration gfxboot.  It is an alternative.  With startup manager you can create a background image for grub just like is doable with gfxboot.

Gfxboot is a bit more than *just* a background image. So this isn't really a viable alternative.

---

### Post by Dark Star on 2008-01-18
Done everything but not showing GFX Grub :( What to do now ?

---

### Post by chewearn on 2008-01-18
> **Dark Star said:**
> Done everything but not showing GFX Grub :( What to do now ?

Have you done:
```
sudo grub-install /dev/X
```

Where /dev/X is MBR of your boot disk?

---

### Post by Dark Star on 2008-01-18
Thanks it did the trick :D

---

### Post by DuKe2112 on 2008-01-22
Sine I didn't get an answer I like to ask again:

Does anyone now how to create your own theme with gfxboot?
Although they seem to be cpio archives just repacking doesn't work. The grafiks get messed up.

And secondly, is it possible to disable Grub's textoutput?
At least the quiet option doesn't disable all of them.

---

### Post by pepsi_max2k on 2008-01-23
using gutsy and just gone through the whole guide (uninstall grub, install grub-gfx.., copy message.X to /boot/gurb, edit menu.lst for correct message, grub find root setup) but still have the basic black n white default grub screen.

only things that differed from the guide were find /boot/grub/stage1 spat out:
(hd0,2)
(hd0,4)
which isn't too suprising as partition 5 contains my old ubuntu install with a few grub files so i guess it's just seeing them, anyway....

> root (hd0,2)
 Filesystem type is jfs, partition type 0x83

> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/jfs_stage1_5" exists... yes
 Running "embed /boot/grub/jfs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+18 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


which also looks good, so i don't get why it's not working. do i actually have to use "sudo grub-install /dev/hda"  (hd0)? or any other commands after setup (like "quit")?


**EDIT:** ohh you've gotta love half complete howtos... :(

here's the full, correct and working version for gutsy, no wonder so many are having trouble with the original. after downloading files,

First remove your old grub
```
sudo apt-get remove grub
```

Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```

then we're going to move the message
```
sudo cp message.suse /boot/grub/
```
replace .suse with the .whatever you downloaded.

THE MESSAGE FILE MUST BE OWNED BY ROOT USER/GROUP WITH CORRECT PERMISSIONS
```
sudo chown root:root /boot/grub/message.suse
sudo chmod 644 /boot/grub/message.suse
```
replace .suse with the .whatever you downloaded.

Then edit your menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

and make it use gfxboot, write this as the very first line of the file and save it.
```
gfxmenu /boot/grub/message.suse
```
replace .suse with the .whatever you downloaded.

Then do :
```
sudo grub
 find /boot/grub/stage1

```
it'll print out (hdx,y), so following that type:

```
root (hdx,y)
setup (hdx)
quit
```
if you have multiple (hdx,y) entries, work out which one is your current OS partition and use that (note: grub counts from 0 onwards, eg. hd0,0 is first harddrive, first partition, and it includes extended partitions in it's count).


NOW REBOOT. technically the above should have installed grub correctly, if so then you can stop here. but for whatever reason for quite a few people here it's not, so on we go...


find out your hard drive names:
```
sudo fdisk -l
```
this helps with both the above and below. if you don't know if your OS's partition is on hda, hdb, sda or anything else, then find out using the above.

Install grub to MBR but **CHANGE HDA** to your OS's drive, so if it's on hdb use /dev/hdb:
```
sudo grub-install /dev/hda
```
[COLOR="Red"]**DO NOT**[/COLOR] use any numbering in this, using hda1 will install grub to the first partition not the mbr. if you do this, follow this guide tellingly titled  [Oh crap, I just typed 'grub-install /dev/hda1']("http://www.josephhall.org/grub_install_hda1.html").
you could use grub-install hd0 as with the grub setup command but this is bios dependent and i dunno if you could mess it up by altering bios settings inbetween things (and i don't wanna find out either...).


and that should be it. restart and pray you didn't mess up :popcorn:

more on grub-install at: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

and thanks to kvonb for the tips.

---

### Post by Philio on 2008-01-26
In order to get gfxboot working on my laptop I had to run grub-install as setup (hd0) despite indicating that it had worked had no effect.

I'm now trying to get gfxboot working on my desktop, however I have a dmraid setup, again grub output suggests that it has worked:

```
grub> device (hd0) /dev/mapper/nvidia_dbibefbi
device (hd0) /dev/mapper/nvidia_dbibefbi
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
grub> root (hd0,1)
root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

```

However as with my laptop this had no effect.

Anyone know how to fix this?

---

### Post by Philio on 2008-01-26
I've fixed it, had to copy the /usr/lib/grub/ARCH/* files over to /boot/grub again as I had done the first time round installing Grub.

Noticed as this is a Debian package, not modified by Ubuntu that update-grub creates menu items as 'Debian GNU/Linux' not as 'Ubuntu x.xx'. I fixed this by extracting the Ubuntu grub package and comparing the contents of the two update-grub files, can be fixed by doing the following:

sudo gedit /usr/sbin/update-grub.real

Seach for: title="Debian GNU/`uname -s | sed -e s,GNU/,,g`"
Replace with: title=$(lsb_release --short --description 2>/dev/null) || title="Ubuntu"

---

### Post by leeon182 on 2008-01-31
helow. i am new to ubuntu and i hope you can help me. i want to install bootspalsh, so i followed all the steps written above. i came to the point where it says:

Then do :
Code:

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

i don`t know where to write this.in terminal?in menu.lst that opens up before this action? please help.
tnx

---

### Post by chewearn on 2008-01-31
> **leeon182 said:**
> helow. i am new to ubuntu and i hope you can help me. i want to install bootspalsh, so i followed all the steps written above. i came to the point where it says:

Then do :
Code:

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

i don`t know where to write this.in terminal?in menu.lst that opens up before this action? please help.
tnx

In terminal.

---

### Post by muunleit on 2008-02-08
> **fantan said:**
> I figured out what was the problem with my system!
On my HDD I have several partitions and for the boot I have a separate partition, hda1.
This partition is mounted to the /boot directory of the Dapper system.
On this partition there isn't /boot directory, just /grub.
If in the menu.lst file I change the first line from 
"gfxmenu /boot/grub/message.gobo" to "gfxmenu /grub/message.gobo" then grub finds the graphics file message.gobo....
fantan

Thx, fantan, for this post, it helped me alot (had the same problem)

---

### Post by alison.santiago on 2008-02-22
Has there been an update to the grub-gfxboot package?  I have installed Gutsy and every time I try to update the kernel and the initrdimage file, it fails.  I would have to install the current grub, update and then switch back to grub-gfxboot.  This has become too much of a hassle.  

Any information on this will be greatly appreciated.

Thanks.

---

### Post by ingo on 2008-03-01
Is there a howto for doing your own theme? The instructions in the first post of this thread were a little scant for me...

---

### Post by autocrosser on 2008-03-01
> **alison.santiago said:**
> Has there been an update to the grub-gfxboot package?  I have installed Gutsy and every time I try to update the kernel and the initrdimage file, it fails.  I would have to install the current grub, update and then switch back to grub-gfxboot.  This has become too much of a hassle.  

Any information on this will be greatly appreciated.

Thanks.


The /sbin/update-grub script supplied with GFXBoot is wrong--the first line is #!/bin/sh  -----  it should be  #!/bin/bash

Edit the file in a text editor with root permissions.....and check it with the next kernel update :)

NOTE: I'm still looking for a good tutorial for theme creation--anyone knowing one please PM me...I've got several good ideas waiting!!!!!

---

### Post by ingo on 2008-03-02
The most comprehensive howto I have come across is this 

> #Make a directory test as root:
mkdir /boot/grub/test

# Copy as root /boot/grub/message to /boot/grub/test
cp /boot/grub/message /boot/grub/test

# Change to directory test
cd /boot/grub/test

# Extract the archive 'message'
cpio -i < message  

# Replace the file background.pcx with your own design (you'll probably have to conform to the same format/size/name). In order to get the proper archive move the existing message elsewhere, make a text file "name-list" with all filenames in that directory in it (ls>name-list). Then:

# Copy files named in name-list to the archive
 cpio -o < name-list > message

Reboot.from here 
[http://mepislovers.org/forums/showthread.php?t=1879&highlight=gfxboot](http://mepislovers.org/forums/showthread.php?t=1879&highlight=gfxboot)

---

### Post by tastatur on 2008-03-05
Many thanks to PingunZ  for this useful guide. But after i did every steps in your guide, it shows only "normal"-text Grub Menu.

Thanks to Bohboh, his post is still here. I tried to make 2 steps more and hope.

```
sudo fdisk -l
```
OK, my Ubuntu's partition locates at sda2

also:
```
grub-install /dev/sda
```

Restart and everything is perfect :lolflag:
------
Hope if this post can help someone else :P
@PingunZ: it would very nice if you can check it and correct your first post

---

### Post by Robert2k on 2008-03-29
I only have a question, i have *Ubuntu 7.10 Gutsy Gibbon*, and i want to use graphic grub loader, the package can be installed automatically :confused: or i have to do something previous or during installation :confused:   

Thanks for your answer

---

### Post by spikenick on 2008-04-10
So how would i be able to go about this on hardy heron ubuntu 8.04, i got this to work on gutsy, O and i switched from 32bit ot 64bit

---

### Post by Ubumby on 2008-04-27
I installed GFX boot before fine with 7.04 and 7.10. This time after installation it let me log into ubuntu fine but wouldn't boot into windows. It quickly showed:
root hd0,1
Filesystem Type unknown, partition....
save default
...
...
than it just reverted right back to GFXgrub home screen.
When I tried to boot to windows drive, after I disabled my other drive it just shows the word grub in the top left corner, not letting me do anything. I also tried to use my fix boot disk and selected my windows hard drive but after it was complete nothing helped. It almost has to be that the windows hard drive boot was somehow screwed up when i installed gfxgrub. I then should of just left it alone, but i tried to reinstall ubuntu on my 2nd harddrive again, but this made it worse. It didn't recognize my windows partition after install since it wasn't in the final menu.lst. I tried to use my super grub disk again and fix windows partition and after reboot now I get instead of windows booting, a grub command line.

Grub> (I typed in boot) and it says:
Error 8: kernel must be loaded before booting

Another side note: I'm reinstalled ubuntu 8.04 right now and it cant see either of the two partition on my 1st hard disk. But when I use an ubuntu 7.04 live cd it can see both of them and can read the first partiton: (DellUtility) fat32 (I think), but not the NTFS drive. I gives me an error.

$ sudo fdisk -l
[sudo] password

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

Device Boot Start End Blocks Id System
/dev/sda1 1 4 32098+ de Dell Utility
/dev/sda2 * 5 7294 58556925 7 HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed44c

Device Boot Start End Blocks Id System
/dev/sdb1 1 30119 241930836 83 Linux
/dev/sdb2 30120 30401 2265165 5 Extended
/dev/sdb5 30120 30401 2265133+ 82 Linux swap / Solaris

anyways now when i boot up i get a GRUB loading stage 1.5 then it waits 5 seconds and boots to ubuntu right away. It dosen't show the grub selection screen, so it never recognized my windows after I reinstalled like it should of. Is this a major problem. I don't know how installing gfxgrub could of killed the windows boot so bad.:confused:

---

### Post by ingo on 2008-04-27
ubumby,

I'm sure others can shed more light on this shortened grub explanation, but basically grub ought to be in the mbr (master boot record - the part of the disc that the BIOS addresses). It then opens the partition table and looks for /boot. 

In /boot it opens up /boot/grub/menu.lst - at the bottom of this file you will see listed all the operating systems and entries which you see on the grub screen shortly after booting.

You will find entries for all your systems. 

For **Linux** OSs you have the title, the root partition, the kernel and the initram. There may also be frame buffer or screen mode instructions. 

For **M$** you just see the title and some chainloader instruction (maybe more? I don't know). The chainloader points to the partition only - you may want to google it. Grub then looks for the kernel itself.

Armed with that info you should be able to make some headway:)

---

### Post by mario2409 on 2008-04-27
> **PingunZ said:**
> 
Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```



When I do the first line "find /boot/grub/stage1" I get Error 15: File not found... what am I doing wrong?

---

### Post by Ubumby on 2008-04-27
Thanks for the reply ingo,
    I don't understand how grub or ubuntu can't recognize my windows partition anymore. My /boot/grub/menu.lst doesn't even have windows recognized anymore after I reinstalled ubuntu.

---

### Post by ingo on 2008-04-28
Well, the quick way out here would be to download the [super grub disk]("http://www.supergrubdisk.org/index.php?pid=4") from one of the mirrors listed, burn, boot and let it do its magic - if that does not find your M$ it is because your M$ is not there.

---

### Post by pabl0 on 2008-04-28
> **mario2409 said:**
> When I do the first line "find /boot/grub/stage1" I get Error 15: File not found... what am I doing wrong?

Try with "find /grub/stage1"

---

### Post by hartland08 on 2008-04-28
Alright I just tried the latest super grub disk and tried to fix it. Anyways when I tried, fix boot of windows, it said it succeeded. However I still only get the WORD grub when I reboot snd it won't let me do anything. I also tried to manually fix it and it could see both partitions:

hda1 sda1 00 0s1 fat- windows 
hda2 sda2 01 0s2 NTFS- windows (Not Exact)

whenever I picked one it would read cannot mount selected partition. I'm using a live cd right now and opened gparted. I get a caution sign by my sda2 partition (Not by my sda1), It says Failed to start up volume. Failed to mount: Invalid argument, The device /dev/sda2 doesn't have a valid NTFS!!!:confused: (Is that normal for NTFS drives?)

I don't know how my installation of gfxgrub killed (maybe) this drive:(

---

### Post by adrian15 on 2008-04-29
> **hartland08 said:**
> Alright I just tried the latest super grub disk and tried to fix it. Anyways when I tried, fix boot of windows, it said it succeeded. 

hda1 sda1 00 0s1 fat- windows 
hda2 sda2 01 0s2 NTFS- windows (Not Exact)



**Choose Language & Help -> Boot & Tools -> Boot Partition -> hda2**
Does your Windows boot?

If it boots:
**Choose Language & Help -> Boot & Tools -> Activate Partition -> hda2**
and when rebooting it should boot.

If when running: **Choose Language & Help -> Boot & Tools -> Boot Partition -> hda2** you get GRUB then it means that you have somewhere run a: setup (hd0,1) and your ntfs partition has a severe problem (I am sorry I do not know how to solve it).

adrian15

---

### Post by jw5801 on 2008-04-29
> **adrian15 said:**
> **Choose Language & Help -> Boot & Tools -> Boot Partition -> hda2**
Does your Windows boot?

If it boots:
**Choose Language & Help -> Boot & Tools -> Activate Partition -> hda2**
and when rebooting it should boot.

If when running: **Choose Language & Help -> Boot & Tools -> Boot Partition -> hda2** you get GRUB then it means that you have somewhere run a: setup (hd0,1) and your ntfs partition has a severe problem (I am sorry I do not know how to solve it).

adrian15

You can solve that with a Windows repair disk I believe. I think SGD has the ability to restore the Windows MBR as well.

---

### Post by _Stevie_ on 2008-04-30
i really wonder why ubuntu doesnt use the gfxboot screen from the install cd? it looks much better than that ugly grub screen.

---

### Post by rognas on 2008-05-02
Hi!

A big thankyou for this excellent how-to and the patience for all us n00bs..;-)

---

### Post by jingo811 on 2008-05-02
> **_Stevie_ said:**
> i really wonder why ubuntu doesnt use the gfxboot screen from the install cd? it looks much better than that ugly grub screen.

I don't think you can md5 encrypt GRUB globally or for each specific partition with background graphics on.  Unless there's some programmers who can rewrite how GRUB works maybe coding bootloaders has become a lost art, I don't know.  But without a globally encrypted GRUB your root password is practically useless when someone gets their hand on your PC physically.
But then having encrypted GRUB globally or for each specific partition doesn't make you 100% protected either.  See md5 GRUB encrypt as 30% added armour no more no less :-)

Even my former SUSE instructor told us to turn off the background image for the SUSE distro in order to protect our PC so I'd think that many SUSE users turn back to the darkside of GRUB in the end anyways :-)

---

### Post by ingo on 2008-05-02
Hear, hear!

Well, grub 2 is already an option on Lenny, so don't hold your breath ;)

---

### Post by figos on 2008-05-04
So basicaly I was installing GFX Grub in my laptop and when I came to this step:

> 
The last thing you have to do is to install Grub MBR .

sudo fdisk -l

You will get an output like this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0×0dd6c6bd

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3187 25599546 7 HPFS/NTFS
/dev/sda2 3188 8287 40965750 f W95 Ext’d (LBA)
/dev/sda3 8288 9607 10602900 83 Linux
/dev/sda4 9608 9729 979965 82 Linux swap / Solaris
/dev/sda5 3188 5737 20482843+ 7 HPFS/NTFS
/dev/sda6 5738 8287 20482843+ 7 HPFS/NTFS

Look for the bold Entry and finally install MBR in Filesystem

sudo grub-install /dev/sdaX
Note : Replace sda by hda if it is in fdisk -l output
Instead of grub-installing on my "Linux" partition I was dumb enough to install it in my "sda1-HPFS/NTFS" equivalent which is my Windows Vista partition. So now everytime I boot to that partition a new GFXGrub selection menu logically comes up and I'm stuck in an infinite loop. I checked to see if there was a grub-uninstall equivalent but to no avail. How can I uninstall grub from this partition?

Sorry if this has already been posted but I searched and found nothing.

---

### Post by jingo811 on 2008-05-04
I'm still trying to wrap my brain around how GRUB behaves when multi-boot partitioning doesn't go as abc123....
There seems to be over 10 bad scenarios when GRUB goes wrong and I've only stumbled upon and understood 1,5 of those bad scenarios.

Try out Super Grub Disk it should help you understand and learn how to solve your specific case.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Or you could try and re-install GRUB to your Linux partition and then modify your **/boot/grub/menu.lst** so that it points to your  Vista partition correctly.  My Windows XP partition is in the same position like yours so just study how I made my menu.lst and then you can just modify your own Vista part.  Also note that I'm using **hdx** you should still use **sdx** like before.  Hope it helps.

```
# Which entry should boot by default?
default		0

# Countdown (seconds)
timeout		10

# Menu colors
color dark-gray/black white/red

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#######################################################################################



# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

....
....
....

### END DEBIAN AUTOMAGIC KERNELS LIST




#####################		{ Entry 0 }		###############################
#
# Partition:	/dev/hda5
title		Ubuntu Feisty
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0042284c-4547-41ef-9314-99824cfcf67c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

#####################		{ Entry 1 }		###############################
#
# Partition:	/dev/hda5
title		recovery mode
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0042284c-4547-41ef-9314-99824cfcf67c ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

#####################		{ Entry 2 }		###############################
#
# Partition:	/dev/hda5
#title		memtest86+
#root		(hd0,4)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot





#######################################################################################
title		.....................................................................
root
#######################################################################################



#####################		{ Entry 3 }		###############################
#
# Partition:	/dev/hda6
title		Debian Etch
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/hda6 ro 
initrd		/boot/initrd.img-2.6.18-5-486
savedefault
boot

#####################		{ Entry 4 }		###############################
#
# Partition:	/dev/hda6
title		single-user mode
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.18-5-486 root=/dev/hda6 ro single 
initrd		/boot/initrd.img-2.6.18-5-486
savedefault
boot

#####################		{ Entry 5 }		###############################
#
# Partition:	[COLOR="Red"]/dev/hda1[/COLOR]
title		Windows XP
root		[COLOR="Red"](hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1

#####################		{ Entry 6 }		###############################
#
# Partition:	/dev/hda8
title		openSUSE 10.3
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6E040L0_E118SYPN-part8 vga=0x31a    resume=/dev/sdb2 splash=silent showopts
initrd		/boot/initrd-2.6.22.5-31-default


```

---

### Post by figos on 2008-05-04
Thanks for your help I fixed the problem with the Vista dvd.

---

### Post by _Stevie_ on 2008-05-04
> **jingo811 said:**
> I don't think you can md5 encrypt GRUB globally or for each specific partition with background graphics on.  Unless there's some programmers who can rewrite how GRUB works maybe coding bootloaders has become a lost art, I don't know.  But without a globally encrypted GRUB your root password is practically useless when someone gets their hand on your PC physically.
But then having encrypted GRUB globally or for each specific partition doesn't make you 100% protected either.  See md5 GRUB encrypt as 30% added armour no more no less :-)

Even my former SUSE instructor told us to turn off the background image for the SUSE distro in order to protect our PC so I'd think that many SUSE users turn back to the darkside of GRUB in the end anyways :-)

i didnt know that stuff with md5 and that it is a "security hole".
good to know! ill leave it as ugly as is then and wait for grub 2 :)

---

### Post by jingo811 on 2008-05-05
Make your /boot/grub/menu.lst like this it's much sexier.  Being pretty(gfxboot) and unsecured is not sexy. :)

```
# Menu colors
color dark-gray/black white/red
```

---

### Post by _Stevie_ on 2008-05-06
let me check this........ ;)

---

### Post by Skeet on 2008-05-21
Does this work even if you're not dual booting? When I reboot, it says "Press ESC to enter menu", when I do, just the normal grub appears.

---

### Post by jingo811 on 2008-05-21
Does what work?  Please specify your question.

---

### Post by Skeet on 2008-05-21
GFXBoot. I tried installing it and it just came up with the usual grub menu each time.

---

### Post by jw5801 on 2008-05-21
> **Skeet said:**
> GFXBoot. I tried installing it and it just came up with the usual grub menu each time.

You need to reinstall grub after you install gfxboot. If you read the comments on the first couple of pages this is mentioned.

```
sudo grub-install [your hardrive in (hdX) format]
```

---

### Post by evil_m0nkey on 2008-05-22
Hi, I am pretty much a complete newbie, and i am interested in changing, but i just wanna know,

just in case something messes up, as in the installation of the theme and by my removal of grub, what would happen then??

would i be bale to use my laptop, as i have only one laptop, and cannot afford to NOT live with it.

Thank you in advance :)

---

### Post by jingo811 on 2008-05-22
Doing this in terminal is your **first measure** against future GRUB problems.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup_01
```
Then you should make sure you have a bootable Linux CD handy (**second measure**).  My Debian Etch 4.01 Install CD has always rescued me when I messed up my GRUB.  Somehow my main OS Ubuntu Feisty's LiveCD hasn't worked at all so you should wait for a second opinion before going any further with this business.  If you intend on using Ubuntu LiveCDs for rescueing!

Otherwise you could be sitting there with a crippled laptop for 1-2 weeks.
All your personal data and system files including Windows if you have it will remain unharmed.  GRUB is just a program that manages which of your operating systems to boot.  It doesn't do anything to the files in your partitions except maybe read and write to your /boot/grub files.

So messing up GRUB is not really dangerous I've seen "Error 15 - File not found" around 5 times these past 2 months. :)

---

### Post by focojoaco on 2008-06-16
it worked for me
thanx!

---

### Post by Houli on 2008-06-16
Can someone post the first couple of lines from their menu.lst as an example for me as a working one.

---

### Post by Stefanie on 2008-06-16
there is an ubuntu theme in the repositories: gfxboot-theme-ubuntu . how do you use this theme? i installed the package but there doesn't seem to be a message-file...

---

### Post by mrandersonmd on 2008-06-16
Well I got how to modify the images and create a new message.xxxx, but how can I manage where the text is shown and the color code of the text...

I will thank if anyone can write some tutorial about that. Thanks in advance.

---

### Post by magikasheep on 2008-06-19
i fallowed this, but somehow it came to be that the resolution is wrong or something, and it doesnt show all the background, and the text goes off the screen. does anyone know how to fix this?

---

### Post by obsrv on 2008-06-20
Where do I find grub-gfxboot 64bit package?

---

### Post by jw5801 on 2008-06-20
> **obsrv said:**
> Where do I find grub-gfxboot 64bit package?

Can't remember where I got it from, but it's attached here.

---

### Post by pavel989 on 2008-06-23
i found a few kewl splash's for grub online, starting to mess with this, maybe get around to making my own. but i can't get this to work. my grub menu is just fine, but i followed the steps and its still the old black and white boringness.

also:
pavel@pavel-desktop:~$ sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
pavel@pavel-desktop:~$ su echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

does that matter?

and what could i be doing wrong?

---

### Post by pavel989 on 2008-06-23
> **drbmm said:**
> I too followed the following steps to install GfxBoot:

1. Downloaded the files
2. Uninstalled grub
3. Installed debs
4. Copied file to /boot/grub
5. Added line to menu.lst (added it at the very top, i.e. line 1)
6. Entered the Grub commands
7. Rebooted

Still the text grub page on reboot.

To get the thing to finally work I did the following at step 6:

sudo grub-install /dev/hd*x* #put your drive values in

sudo grub

grub< setup (hd*x*,*y*) #put your values in here

grub< root (hd*x*,*y*) #put your values in

grub< quit

reboot

When I rebooted I got the grub prompt instead of the nice graphical log in screen. At the grub prompt I did the following again:

grub< setup (hd*x*,*y*) #put your values in here

grub< root (hd*x*,*y*) #put your values in

Grub would not allow me to quit so I did a Ctrl-Alt-Del to reboot.

On reboot the nice graphical interface was there.

I have performed the above on two computers to get the program to   work.

TTTTTTTTTTTTTYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY!!!!!!!!!!!!!!!!!!!!!!!!!! using ur method and messing around with it long enough, i got it running.
turns out, i had to use sda instead of hd0 and it grub kept giving me errors after, so i reboot and it worked. however, now as soon as i choose a linux boot, it gives me a little bit of text, idk y, dont really care, but it wasn't there before. 

also, i change boot flags in gparted

so essentially, i have no idea what i did, but i did it with ur help, ty!

---

### Post by jw5801 on 2008-06-23
> **pavel989 said:**
> i found a few kewl splash's for grub online, starting to mess with this, maybe get around to making my own. but i can't get this to work. my grub menu is just fine, but i followed the steps and its still the old black and white boringness.

also:
pavel@pavel-desktop:~$ sudo echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
pavel@pavel-desktop:~$ su echo gfxmenu /boot/grub/message.suse > /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

does that matter?

and what could i be doing wrong?

Try:
```
echo gfxmenu /boot/grub/message.suse | sudo tee -a /boot/grub/menu.lst
```

It's a very good thing you got permission denied for that command, as it would have erased your menu.lst. So you would have had rather severe issues at next boot.

The command it actually wanted was "echo gfxmenu /boot/grub/message.suse >> /boot/grub/menu.lst" as that will append. It won't work with sudo however, you have to actually be root. The reason is that sudo will only give root permissions to the part before the pipe (>, >> or |), so the part of the command that actually needed to be done as root doesn't receive the root permissions.

If you've already added the "gfxmenu" line to /boot/grub/menu.lst then you don't need to do this though, as that's all it does.

---

### Post by pavel989 on 2008-06-23
ooo i get it now. 

Also, are there any really good guides as to how to make a custom theme? like down to the font. i found the instructions with the gxboot-theme--ubuntu package, but it isn't very detailed.

---

### Post by shinji257 on 2008-06-26
> **jw5801 said:**
> Can't remember where I got it from, but it's attached here.

Thanks for the file.  I used it on my 64-bit install and it works great.  It worked once I remembered to type grub-install. :oops:

P.S. - I notice the 64-bit install runs noticeably faster than than the 32-bit one.  All modules loaded too so I don't think anything is missing.  Nothing substantial anyways.

---

### Post by shinji257 on 2008-06-26
> **Philio said:**
> I've fixed it, had to copy the /usr/lib/grub/ARCH/* files over to /boot/grub again as I had done the first time round installing Grub.

Noticed as this is a Debian package, not modified by Ubuntu that update-grub creates menu items as 'Debian GNU/Linux' not as 'Ubuntu x.xx'. I fixed this by extracting the Ubuntu grub package and comparing the contents of the two update-grub files, can be fixed by doing the following:

sudo gedit /usr/sbin/update-grub.real

Seach for: title="Debian GNU/`uname -s | sed -e s,GNU/,,g`"
Replace with: title=$(lsb_release --short --description 2>/dev/null) || title="Ubuntu"

Thanks for the tip.  I also found that update-grub may not run since /bin/sh is symlinked to dash.  Edit the first line of /usr/sbin/update-grub and change #!/bin/sh with #!/bin/bash.  Oh and your line gives something like the following:

Ubuntu 8.04.1, kernel 2.6.24-19-generic

The original from the main grub package doesn't have the ".1" part so I created a slightly modified version of your line.  This one will do it exactly like the old update-grub file formatted it. :)

```

title="$(lsb_release --short --id 2>/dev/null) $(lsb_release --short --release 2>/dev/null)" || title="Ubuntu"

```

Attached are updated versions of update-grub and update-grub.real that mimic the original version.  In this version update-grub will use bash directly and update-grub.real has been updated to use the above line instead of the original one.  Backup the ones you have then extract these into /usr/sbin if you wish to use them and yes they have been tested.

EDIT: I'll mention now that these files were tested for the 0.97-11 version on the amd64 build.  Can't guarantee that it will work fine for newer versions.

---

### Post by Muhammad on 2008-06-27
So what I should be doing is removing Grub and installing gfxboot?

---

### Post by master_kernel on 2008-06-27
> **Muhammad said:**
> So what I should be doing is removing Grub and installing gfxboot?
Yes. Updated packages are here: [http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

---

### Post by shinji257 on 2008-06-29
Did the message file format change between -11 and -29?  In -11 I am able to use the message.suse file on the first post but now it give me an invalid format error with -29.

EDIT: I using the 64-bit version.

---

### Post by rossinio on 2008-06-30
> **shinji257 said:**
> Did the message file format change between -11 and -29?  In -11 I am able to use the message.suse file on the first post but now it give me an invalid format error with -29.

I have the same problem, although I am starting from scratch with -29..

---

### Post by Xgamer on 2008-07-06
I have problem I install gfx boot and do everything as in the tutorial bad the grub says:gfxmenu /boot/grub/message.suse invalid file format
Would you help me with that?thx

---

### Post by shinji257 on 2008-07-06
> **Xgamer said:**
> I have problem I install gfx boot and do everything as in the tutorial bad the grub says:gfxmenu /boot/grub/message.suse invalid file format
Would you help me with that?thx

Are you installing the 32-bit or 64-bit version?  If you are using 32-bit then I'd recommend using the version on the first post (I know it works).  If you are using the 64-bit one then use the copy attached to [this post]("http://ubuntuforums.org/showpost.php?p=5224880&postcount=597").

Both will work.  As mentioned above for some reason -29 changed the image format.

---

### Post by Xgamer on 2008-07-07
I install  64bit version because I run 64bit ubuntu

---

### Post by mb7 on 2008-07-16
Hi,
When I try to install the .deb from the first post it complains about a unmet dependency grub-common which is not available in any repo I have enabled.

any suggestions?

---

### Post by Jan Olieboer on 2008-07-17
Hi,

Well .. it works .. just following the procedure as given. Just one thing. Grub sort of echoes all it's commands to screen. So when it starts, it displays a message, stating that it starts grub stage 1.5, followed by a message that it's going to start gfxboot. Then the graphical boot menu comes up, and after I've made a choice, it nicely echoes all the internal grub commands to screen/terminal, like chainloader +1 .. and what have you.
Can't imagine it's supposed to do that. I tried command 'terminal --no-echo' but that was obviously not it. I also tried different versions of the grub gfxboot, like the 5-version as mentioned in the first post, but also tried an 11 version I found somewhere else. Didn't make a difference. I have seen a post here stating the same issue, but no answer. Does anyone know how to switch of these terminal messages? 

Jan.

---

### Post by sankz on 2008-07-20
The easiest method is available here:
[http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/](http://fasterthanlight.wordpress.com/2008/07/18/beef-up-your-grub-loader/)
and here:
[http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/](http://fasterthanlight.wordpress.com/2008/07/20/create-your-own-grub-splash-image/)

---

### Post by erginemr on 2008-07-20
@sankz,

This refers to Grub splash images, which are 640x480 size, 14 color deep, low quality background pictures, which are applicable to the existing default b/w Grub screen.

But GFXBoot is a completely different system, with backgrounds far more advanced screens with a higher resolution and color depth background and a ticking timer.

[http://www.gnome-look.org/content/show.php/gulliver+Ubuntu+GFXBoot+Grub+Theme?content=57145](http://www.gnome-look.org/content/show.php/gulliver+Ubuntu+GFXBoot+Grub+Theme?content=57145)
[http://www.gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735](http://www.gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735)

---

### Post by DocZayus on 2008-07-21
fdisk -l
returns nothing for me
(unless I have my 1gb sd card in the reader, then it returns the info for the card.)

grub > find /boot/grub/stage1
Error 15: file not found

Now, I've looked and it's there.
Last time I tried anything funny, I hosed my Vista partition.
I really don't want to relive these past 3 days of repartitioning/reformatting/reinstalling.

How else can I find out my ext2 /boot partition's whereabouts?

I manually partitioned it to be:
/boot (100mb - ext2)
/home/vista (100gb - ntfs)
/ (45gb - ext3)
swap (2gb)
/home/share (150gb - fat32)

---

### Post by DocZayus on 2008-07-21
Maybe menu.lst will help:

> gfxmenu /boot/grub/message.suse

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=633fcc98-7e74-4887-ae86-3a0cd7e21001 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=633fcc98-7e74-4887-ae86-3a0cd7e21001 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=633fcc98-7e74-4887-ae86-3a0cd7e21001 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=633fcc98-7e74-4887-ae86-3a0cd7e21001 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=633fcc98-7e74-4887-ae86-3a0cd7e21001 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


---

### Post by DocZayus on 2008-07-21
grub> root (hd0,0)

Error 21: Selected disk does not exist

---

### Post by Les_Caesars on 2008-07-21
I've followed the instructions, have tried other people's solutions, and have a matching menu.lst file, but I'm not having any luck.

Now whenever I boot up, I get an "Invalid file format" error. None of the themes I've thrown at it have seemed to work. I heard somewhere that it had to be patched, and found some opensuse, archlinux, and gentoo-specific patches. Does someone know how we can get some patches for ubuntu, or have any other ideas for the "invalid file format" problem?

---

### Post by Sam Lars on 2008-07-26
FYI, gfxboot is available in the repositories, at least for Hardy...
But the package needed is grub-gfxboot...

---

### Post by Les_Caesars on 2008-07-26
Here we are. I found something that works for me. This should help people with 64-bit.

[http://ubuntuforums.org/showthread.php?t=526605](http://ubuntuforums.org/showthread.php?t=526605)

---

### Post by Sam Lars on 2008-07-29
Thanks for that link.  I installed that, but when I do an update-grub (not related to gfxboot install), I get this error:
```
[: 25: ==: unexpected operator
exec: 25: -a: not found
```
I had to remove grub-gfxboot and install grub again to get the -20 version of the kernel to be set up correctly, because dpkg was running this update-grub as part of its process and failing because of this error.

---

### Post by jw5801 on 2008-07-29
> **Sam Lars said:**
> Thanks for that link.  I installed that, but when I do an update-grub (not related to gfxboot install), I get this error:
```
[: 25: ==: unexpected operator
exec: 25: -a: not found
```
I had to remove grub-gfxboot and install grub again to get the -20 version of the kernel to be set up correctly, because dpkg was running this update-grub as part of its process and failing because of this error.

Open /usr/sbin/update-grub and change the first line from #!/bin/sh to #!/bin/bash.

---

### Post by Les_Caesars on 2008-07-29
Try only following the directions for the first post. Even though you may run 64 bit, use the 32 bit package that he has in the link anyway (that's what I did, it works, and I run 64 bit). Don't overlook the fact that the 64-bit package mentioned in that thread is an older version than the 32-bit one mentioned in the thread. The one in the link is 0.97-5, while the non-working 64-bit one is 0.97-11. A 32-bit grub probably isn't going to affect your whole OS' performance. As long as it works (and doesn't crash), it's as good as any other working solution.

---

### Post by adam_kimber on 2008-08-15
GFX boot is very nice but I seem to have a problem with it. I have a widescreen monitor and all the themes seem to have this split with the countdown on the left and the options on the right. My Countdown is near enough in the middle of the screen with the text going off the screen to the right. 

Is there any way of getting the countdown to sit further left? I might need to edit the message files? 

Second point, is there a way of removing the version number in the list? So all I get is "Ubuntu Linux, Memtest86 and Windows". it would look neater (and the text would not go off the screen ;)

Found a theme that is totally different! [http://www.kde-look.org/content/show.php/Blue+Rays+Gfxboot+Theme?content=75674](http://www.kde-look.org/content/show.php/Blue+Rays+Gfxboot+Theme?content=75674)

---

### Post by Sam Lars on 2008-08-15
You can edit your /boot/grub/menu.lst to change what those titles are.  They're at the bottom.

---

### Post by Sam Lars on 2008-08-26
> **jw5801 said:**
> Open /usr/sbin/update-grub and change the first line from #!/bin/sh to #!/bin/bash.

I did that, but I noticed I'm getting the same error now, whether it says sh or bash.

I followed the advice of Les_Caesars and it works now.  Thanks.

---

### Post by legolas_w on 2008-08-27
I have startupmanager installed and when I tried to remove the grub it shows a message like:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub startupmanager
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1892kB disk space will be freed.

```

should I continue or startup manager do the same job?

Thanks

---

### Post by Malac on 2008-08-27
> **legolas_w said:**
> I have startupmanager installed and when I tried to remove the grub it shows a message like:
 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub startupmanager
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1892kB disk space will be freed.

```
 
should I continue or startup manager do the same job?
 
Thanks
 Continue then install grub-gfxboot deb then ```
sudo apt-get install startupmanager
```
 
Hope this helps.

---

### Post by wesswei on 2008-09-09
I don't know how to send a thanks on this forum, but Thank you for the howto PingunZ! Makes grub look so much more interesting. Looks like Suse knows a little something about linux too! :p

---

### Post by A_Porcupine on 2008-10-19
Hmmm.. i followed that exactaly and it is still not working, i even tried it again and it is still not working.

its just showing the old boot menu :S

the first time i went to remove grub it worked but if i try it now it removes nothing???

i am quite confused

:S

---

### Post by Visible Spirit on 2008-10-27
@merlwiz79,

Thanks for posting this GFXBoot message file! Nicely done good looking graphic. ;)

Visible Spirit

---

### Post by sayantandas on 2008-10-31
Hi, I am using Ubuntu 8.10. I cant get the gfxboot menu working in intrepid. everything installs fine but still the old grub comes up .

---

### Post by Visible Spirit on 2008-10-31
Hi sayantandas,


Don't know anything about Intrepid since I run Hardy 8.04, but throughout this thread the common theme seems to be a step that I don't think was included in the original how-to, considering it was started two years ago.

nbayiha's post: [http://ubuntuforums.org/showpost.php?p=2827955&postcount=395]("http://ubuntuforums.org/showpost.php...&postcount=395") show's the entire install process that seems to have worked for most. The key that worked for me was re-installing grub all said and done as described at the end, if all other procedures were followed.

Back at Normal Prompt do this. (Step #9 above. Ignore the comment referring to Feisty Fawn... worked for me and a few others.)
```
sudo grub-install /dev/hdx,y
```

The option to this is if you have a serial drive vs IDE. In that case it would be...
```
sudo grub-install /dev/sdx,y
```As stated, this step seems to be what's worked for most and was missing in the original how-to. Another post related to this issue was made by Malic here -> [http://ubuntuforums.org/showpost.php?p=1835110&postcount=207]("http://ubuntuforums.org/showpost.php...&postcount=207") .

HTH... ;)


Regards,
Visible Spirit

---

### Post by crowly0 on 2008-11-01
> **sayantandas said:**
> Hi, I am using Ubuntu 8.10. I cant get the gfxboot menu working in intrepid. everything installs fine but still the old grub comes up .
Im running 8.10 x64, and manage to get it working after downloading and compiling gfxboot-theme-suse package. Figured i give it a try after reading [this post](http://ubuntuforums.org/showpost.php?p=5862591&postcount=6) ([thread](http://ubuntuforums.org/showthread.php?t=886281)):
[quote=nicesnake]I've had similar problem with 64 bit gfxboot ( I couldn't `run 32 bit one) Themes provided on sites like gnome-look or kde -look are unusable for me, on boot I had message about invalid file, so I compiled few themes myself (suse, zen from ubuntu repos) and these are working.

And i have grub-gfxboot 0.97-33 from here [http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)


For me it looks like 64bit grub can't read some of 32 bit binary files in not working themes.[/quote]

What i did: 
1) I followed [this guide](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/) (basicly the same as the first post), and instead of the 32bit package, i downloaded/used the 0.97-33_amd64.deb from the link in the quote above. Then just followed the rest of the guide.

2) Installed gfxboot (is this needed?) and gfxboot-theme-suse packages. (Or choose  another theme package)

3) In the terminal go to /usr/share/gfxboot-theme-suse 
a) Compile the theme: (not really sure if both of these are required, im a newbie at compiling stuff)
   i) sudo make
   ii) sudo make install
b) cd install
c) sudo su 
d) ls . |cpio -o > /boot/grub/message.suse

4) Edited /boot/grub/menu.lst and set the gfxmenu parameter as shown in the guide to the newly compiled file.

Heres the working suse theme that i got:

---

### Post by bLaCkMeTaLL on 2008-11-02
Hi crowly0, I have updated Hardy64 to Intrepid64 and tried to apply the changes you suggested, but none worked.
I followed the steps from the linked blog post, doing the steps correctly (unistalling grub - installing grub-gfxboot64 0.97-33, and setting it up); next I tried a gnome-look gfxboot, but it hasn't worked, so I installed through synaptic gfxboot & themes (suse,zen & ubuntu), also trying compiling stuff (suse and zen got compiled correctly but ubuntu given me errors).
I copied the message.suse and the message.zen on the /boot/grub but still it hasn't worked.
I finally tried your attachment and it also hasn't worked too!
WTF?!? :confused:

---

### Post by aniruddha on 2008-11-03
Hi. I am having the same problem as the previous poster. Just bought a new computer (lenovo Ideapad y530, core 2 duo) so I installed Ubuntu 8.10 (64 bit). Everything else worked fine, except for gfxboot. I had a theme from gnome-look which I had been using on my 32 bit Hardy system. Now no themes work. Is it possible to:

a) get themes designed specifically for 64 bit systems from anywhere
b) get some help for recompiling 32 bit themes for 64 bit systems (i tried crowly0's method, but it didnt work). The older cp and then editing pictures method (i forget who first posted it) didn't work as well. 

I miss my old bootloader. Any help would be appreciated.

---

### Post by LnksWolf on 2008-11-06
Why not just use a GFXMenu? I can cope *sigh*. At least a GFXMenu doesn't make my Kubuntu Latty D400's GRUB as ugly as the naked one. :KS

-- LnksWolf --

---

### Post by LnksWolf on 2008-11-06
> **sebbe1991 said:**
> I made a Kubuntu gfxboot :)

[Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)

[ATTACH]12476[/ATTACH]

Thx a lot.:guitar:

---

### Post by Ubumby on 2008-11-06
After a "clean" install of Ubuntu Ibex ....I tried to reinstall gfxboot and of course it didn't work... After investigation my "menu lst" shows my partitions being this(even in my backup file):

title		Ubuntu 8.10, kernel 2.6.27-7-generic
**uuid		8cd0b0d3-9788-431b-855a-aeb932875080**
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8cd0b0d3-9788-431b-855a-aeb932875080 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
**uuid		8cd0b0d3-9788-431b-855a-aeb932875080**
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8cd0b0d3-9788-431b-855a-aeb932875080 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
**uuid		8cd0b0d3-9788-431b-855a-aeb932875080**
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
**root		(hd0,1)**
savedefault
makeactive
chainloader	+1
\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
And heres my fdisk.....Here in lies my question:


[HTML]sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        7294    58556925    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed44c

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       30119   241930836   83  Linux**
/dev/sdb2           30120       30401     2265165    5  Extended
/dev/sdb5           30120       30401     2265133+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008dfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS[/HTML]


................................................................

Can someone please explain why my Linux hard drive lists the partition "as uuid" and shows no root (hdx,x) like my windows drive does......and why is my Linux partition not showing that its boot on my f-disk. Are these related? 

For better understanding I think all this shows that my MBR is on my IDE drive (hd0,1) partition.....Even though grub command now lists...

grub> find /boot/grub/stage1
(hd1,0)

So do I need to install gfxboot on Hd0,1 (MBR?/windows) or Hd1,0 (like the last output suggest).....(sudo grub-install hd0,1)...right?...

---

### Post by ingo on 2008-11-07
You have some reading to do, Ubumby ;)

For UUID - [http://en.wikipedia.org/wiki/Universally_Unique_Identifier](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)

For Grub have a look here - [http://www.gnu.org/software/grub/grub-legacy-faq.en.html](http://www.gnu.org/software/grub/grub-legacy-faq.en.html) - I think no.5 is of particular interest to you.

HTH

---

### Post by Ubumby on 2008-11-07
Ok....I was impatient and screwed up again...My Windows drive is now no longer even readable (mountable) let alone boot able for my comp...ugh....I tried super-grub disk along with windows repair disk (fixboot and fixmbr). I think I have to reinstall windows again. Does anyone know a good recovery program to retrieve files off my hard drive. Or are they lost forever?

---

### Post by ingo on 2008-11-07
Well, I don't know whether knoppix can read ntfs (but I reckon so).  Boot that and see whether you can mount it...

---

### Post by bLaCkMeTaLL on 2008-11-07
:lolflag: poor guy...I's the baptism of fire we all almost had; makes me remember how easy it is to screw things off!

Seems sudo in fact wasn't so "perfect", since today we all use it so lightly! (BUT _still_ IMHO it's one of the greatest killer-apps).

Hey, Ubumby, you may also try UltimateBootCD and see if it helps: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Ubumby on 2008-11-08
hey guys, thanks for the replies....After spending hours of time I can't believe I fixed it....still no Gfxboot though....don't want to try because of the uuid thing yet. Knoppix wouldn't mount it, and Windows repair disk must have pointed all the commands to another drive (e.g. chkdisk output was "The volume appears to contain one or more unrecoverabe problems ---and fixboot wouldn't help)I guess when I ran fixboot it was pointing to my G: drive so by adding "fixboot C:" solved it...All that time for something so simple:D (P.S. Ultimate boot looks awesome by the way)

---

### Post by martinbc on 2008-11-08
I tried, this is what happened:

```

sudo grub

grub> find /boot/grub/stage1

Error 15: File not found

grub>


```


But I have double checked and the file is there...

---

### Post by jw5801 on 2008-11-09
> **martinbc said:**
> I tried, this is what happened:

```

sudo grub

grub> find /boot/grub/stage1

Error 15: File not found

grub>


```


But I have double checked and the file is there...

Do you have a separate boot partition?

---

### Post by martinbc on 2008-11-09
> **jw5801 said:**
> Do you have a separate boot partition?

No I have not.

---

### Post by sneakersupplier on 2008-11-09
I like the shoes: [Nike Air Force 1](http://www.sneakersupplier.com)

---

### Post by samp3ri on 2008-11-10
To all you who are so impatient that they can't do some googling around, [**here**]("http://en.opensuse.org/Gfxboot") is the tutorial: [_http://en.opensuse.org/Gfxboot_]("http://en.opensuse.org/Gfxboot")

I found it pretty good and am currently making a new theme.

---

### Post by Neobuntu on 2008-11-12
Are their any short instructions that work and does this cause problems with the auto kernel upgrades?

---

### Post by a-linan on 2008-11-16
I followed the how-to, but when I restart it does nothing.  I have installed 8.04 Hardy Heron, also tried out with other themes, with the same result... where GFXBoot gets installed?  

** edited **

I found the directory, but still I can't get the grub screen to work, I need heelp!

Thanks for your sugestions

---

### Post by zinc.tw on 2008-11-20
> **martinbc said:**
> I tried, this is what happened:
sudo grub
grub> find /boot/grub/stage1
Error 15: File not found
grub>

But I have double checked and the file is there...

well,well.....
I have the same problem,
and solve it by 3 hours..
finally,
the answers is 
grub-gfxboot_0.97-11_i386.deb or elder is in conflict with ubuntu8.10..
and grub-gfxboot_0.97-**35**_i386.deb is available.

enjoy it!

and then, you may touch the problem "invalid file format!":lolflag:

---

### Post by tstack77 on 2008-11-21
I don't get the lol, zinc!

I got the invalid file format but read nothing of it in this thread...simple fix?

---

### Post by send4m3 on 2008-11-23
hi zinc, i found  out in launch pad gfxboot version is 0.6.10, and you said that older than 0.6.11 can not be installed in intrepid ? have u try it in your system zinc ? Is the step still the same with have been told in forum ?

Please let me know cause i would like to install gfxboot in my PC, is it possible to have beautiful 1280x800 resolution with this gfxboot ? any suggestion theme that fix with intrepid ibex and my resolution screen ? 

please let me know ASAP via my email [email]send4m3@yahoo.com[/email]... thank you...

---

### Post by Quarkrad on 2008-12-01
I'm new to Ubuntu and enter codes in terminal (6to do things) with my fingers crossed all the time.  I tried to have this grub screen (with ubugrey) but messed up and had to re-install.  Having come across this post perhaps my problem was I'm running 8.10.  Any chance of someone who has this working on 8.10 writing up a definitive list of commands for 8.10.  Reading through past threads it gets a little confusing for a newbie on what the correct list of commands are.  There are little changes over many many pages to try and keep up with.

Many thanks.

---

### Post by polymath on 2008-12-04
Hey, can someone post a build of those message.red and message.red2 files from a while back for intrepid?  I'm trying to get them to work but most of the packages i find either look bad, don't work (invalid file format) or don't build because of "Unidentified words: fadein, fade \n make [error 10]"

---

### Post by mhkxio on 2008-12-07
any news about this working on the new ubuntu,intrepid?

---

### Post by Sam Lars on 2008-12-07
I've been using this for a while now, and it's been working fine.  It survived the upgrade to Intrepid.  I'm using the message.blusplash from the first post on 64-bit.

---

### Post by Quarkrad on 2008-12-08
Ok - I've had another go but the more I look into this the more confusing it gets.  Many people say there is a bug(?) in Intrepid that will not allow the grub screen to be changed. As a newbie I think I'm reading messages/posts wrong - this is my problem.  A key clue appears to be:

[B]have the same problem,
and solve it by 3 hours..
finally,
the answers is
grub-gfxboot_0.97-11_i386.deb or elder is in conflict with ubuntu8.10..
and grub-gfxboot_0.97-35_i386.deb is available.

enjoy it!

and then, you may touch the problem "invalid file format!"[/B]

but I'm not sure where (lines of code) this fits in.  message.ubugrey looks really nice (could this not be the default Ubuntu splash screen?) but I am really struggling.  Has anybody got this working on 8.10?  How?

---

### Post by ryukent on 2008-12-08
I got it working in a fresh install of Intrepid.

Problems I got were due to - 
* Old version of grub
* Original tutorial doesn't say to do grub-install
* message file needed to be recompiled

This is what I did

Went to:

[http://www.sidux.com/debian/pool/main/g/grub-gfxboot/](http://www.sidux.com/debian/pool/main/g/grub-gfxboot/)

Downloaded the latest version for my architecture

sudo apt-get remove grub

sudo dpkg -i grub-gfxboot_0.97-35_i386.deb

Note you need to be in the right dir (obviously) and change it to the one for your arch.

sudo gedit /boot/grub/menu.lst

Added: gfxmenu /boot/grub/message.suse

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

Obviously you need to change the X and Ys.

sudo grub-install /dev/sdaX

This was very important. Didn't work without it. Note the X is not the same number as the x or y in the previous section as grub uses different numbers. You need to look up the correct hard disk to use. It should be the one are booting to.

Then installed the gfxboot-theme-suse package from synaptic...

Note: the Ubuntu one didn't work.

cd /usr/share/gfxboot-theme-suse/
sudo make
sudo make install
cd install
sudo su 
ls . |cpio -o > /boot/grub/message.suse

Note: I got errors when compiling the message, but I ignored them and it worked anyway.

This might no work for everyone, but it should give you a newer version than the original deb and also compile the suse message which also didn't work for me from the original. Plus.... remember grub-install

---

### Post by ryukent on 2008-12-09
OK, after a bit of playing around I've realised the compiling part was unnecessary. The message file is basically just a archive with stuff in it. It's easy to update. KDE look site has some others

---

### Post by lowtolerance on 2008-12-10
> **samp3ri said:**
> To all you who are so impatient that they can't do some googling around, [**here**]("http://en.opensuse.org/Gfxboot") is the tutorial: [_http://en.opensuse.org/Gfxboot_]("http://en.opensuse.org/Gfxboot")

I found it pretty good and am currently making a new theme.

Exactly what I've been looking for. Thanks for this!

---

### Post by Glubbdubdribian on 2008-12-30
I followed the steps in the first posts exactly but nothing has changed about grub.. any ideas why this might be?
I've run grub-install and tried version 5 and 36. still no luck
I'm running Ibex 32-bit.

thanks.

---

### Post by Intrepid Ibex on 2008-12-31
> **ryukent said:**
> I got it working in a fresh install of Intrepid.

Problems I got were due to - 
* Old version of grub ....
.... and also compile the suse message which also didn't work for me from the original. Plus.... remember grub-install
Oh no :O!
I did those, but I accidentally selected Windows C: partition at sudo grub: grub> root
and sudo grub-install /dev/sda!

How do I undo those changes ?
- currently I can't boot to Windows (Vista)

ps. I need to fix this as quick as possible:
Thanks forehand for the helpers! Thank you really much!

---

### Post by Intrepid Ibex on 2008-12-31
Bump! Anyone :)?

I did this:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Mounting failed:
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Mounting failed:
mount: you must specify the filesystem type

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ffb046e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   181984319    90992128+   7  HPFS/NTFS
/dev/sda2   *   299162430   312576704     6707137+   7  HPFS/NTFS
/dev/sda3       181984320   221247179    19631430   83  Linux
/dev/sda4       221247180   299162429    38957625    5  Extended
/dev/sda5       221247243   299162429    38957593+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="dcfa8068-b3a8-4645-bfcf-cc8dcffedac8" TYPE="ext3" 
/dev/sda5: UUID="16a57d37-35a7-41b6-bf8f-bc376b65311e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/linuxpro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linuxpro)

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
.................
................
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=dcfa8068-b3a8-4645-bfcf-cc8dcffedac8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=16a57d37-35a7-41b6-bf8f-bc376b65311e /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda3/boot: ==================================

total 24640
drwxr-xr-x  3 root root    4096 2008-12-29 10:26 .
drwxr-xr-x 20 root root    4096 2008-12-29 19:27 ..
-rw-r--r--  1 root root  508385 2008-12-19 19:57 abi-2.6.27-11-generic
-rw-r--r--  1 root root  507665 2008-11-21 01:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91358 2008-12-19 19:57 config-2.6.27-11-generic
-rw-r--r--  1 root root   91364 2008-11-21 01:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-31 21:50 grub
-rw-r--r--  1 root root 8621630 2008-12-24 18:09 initrd.img-2.6.27-11-generic
-rw-r--r--  1 root root 8619552 2008-12-15 14:31 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 23:11 memtest86+.bin
-rw-r--r--  1 root root 1031799 2008-12-19 19:57 System.map-2.6.27-11-generic
-rw-r--r--  1 root root 1029585 2008-11-21 01:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1074 2008-12-19 19:58 vmcoreinfo-2.6.27-11-generic
-rw-r--r--  1 root root    1073 2008-11-21 01:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2248912 2008-12-19 19:57 vmlinuz-2.6.27-11-generic
-rw-r--r--  1 root root 2244304 2008-11-21 01:46 vmlinuz-2.6.27-9-generic

=============================== sda3/boot/grub: ===============================

total 252
drwxr-xr-x 3 root root   4096 2008-12-31 21:50 .
drwxr-xr-x 3 root root   4096 2008-12-29 10:26 ..
-rw-r--r-- 1 root root    197 2008-12-31 21:35 default
-rw-r--r-- 1 root root     15 2008-10-04 23:10 device.map
-rw-r--r-- 1 root root   8108 2008-12-31 21:35 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-31 21:35 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-31 21:35 installed-version
-rw-r--r-- 1 root root   8712 2008-12-31 21:35 jfs_stage1_5
-rw-r--r-- 1 root root   5012 2008-10-04 18:30 menu (copy).lst
-rw-r--r-- 1 root root   5117 2008-12-31 21:50 menu.lst
-rw-r--r-- 1 root root   5143 2008-12-31 21:50 menu.lst~
-rw-r--r-- 1 root root   5259 2008-12-31 21:25 menu.lst.backup
-rw-r--r-- 1 root root   5259 2008-12-31 21:20 menu.lst.backup~
-rw-r--r-- 1 root root   7352 2008-12-31 21:35 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-31 21:35 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-13 14:04 splashimages
-rw-r--r-- 1 root root    512 2008-12-31 21:35 stage1
-rw-r--r-- 1 root root 121460 2008-12-31 21:35 stage2
-rw-r--r-- 1 root root   9556 2008-12-31 21:35 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
/dev/sda2: unknown volume type
```

---

### Post by looi76 on 2009-01-03
Hi, I'm having a problem getting GFX GRUB to work. 

Here is how I installed it:

First I downloaded the files required. I have used grub-gfxboot_0.97-36_amd64.deb since I'm using Ubuntu 8.10 64-bit.
[[IMG]http://img110.imageshack.us/img110/6505/upload01pz8.th.png[/IMG]](http://img110.imageshack.us/my.php?image=upload01pz8.png)

Then I have removed GRUB:
[[IMG]http://img528.imageshack.us/img528/3223/upload02so3.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload02so3.png)

The I have installed GFX GRUB:
[[IMG]http://img528.imageshack.us/img528/9369/upload2nn7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload2nn7.png)

Then I have copied message.suse to /boot/grub:
[[IMG]http://img110.imageshack.us/img110/9762/screenshot3qs9.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot3qs9.png)

Then I have backup /boot/grub/menu.lst and edited it:
[[IMG]http://img528.imageshack.us/img528/3715/screenshot4pb6.th.png[/IMG]  ](http://img528.imageshack.us/my.php?image=screenshot4pb6.png)[[IMG]http://img528.imageshack.us/img528/7362/screenshot5iy4.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot5iy4.png)

Then I have configured grub:
[[IMG]http://img110.imageshack.us/img110/4172/screenshot6yj5.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot6yj5.png)

After I did the following steps, when I switch on my computer nothing has changed to GRUB! Can someone help?

---

### Post by subever on 2009-01-07
I installed the package grub-gfxboot_0.97-36_amd64.deb under ubuntu 8.10 (64bit) i followed all the steps but when i restart i get this message: "gfxmenu /boot/grub/message.suse invalid file format"
anyone figured out this problem.. i already spent hours on different themes.. Help me plz

---

### Post by RJQ on 2009-01-10
Finally I got it working... hopefully this can help some one there with similar situation.

the problem:
I had three os in one hd in my computer kubuntu intrepid and two ubuntu hardy, one of this is my booting system, grub-gfxboot worked well on hardy but it could not see the intrepid partition, installing latest grub-gfxboot let me boot any of my three os but no image no themed menu but the [COLOR="Sienna"]**invalid file format error**[/COLOR]. googling around I read about sidux using different path and that was the answer for me, but instead of changing the files I just change the path in menu.lst...

the solution:
installing the grub-gfxboot from sidux and one of the themes I use gaia, in the theme .deb you can see where this files are going to be placed.
once both .debs were installed I just change the path in the menu.lst like this

[I]gfxboot /boot/message
[/I]
the message is a link to the real file in the same directory (message.hd) an voila! working like a charm also I change the background image for a more suitable look

---

### Post by yzhang12 on 2009-01-11
> **looi76 said:**
> Hi, I'm having a problem getting GFX GRUB to work. 

Here is how I installed it:

First I downloaded the files required. I have used grub-gfxboot_0.97-36_amd64.deb since I'm using Ubuntu 8.10 64-bit.
[[IMG]http://img110.imageshack.us/img110/6505/upload01pz8.th.png[/IMG]](http://img110.imageshack.us/my.php?image=upload01pz8.png)

Then I have removed GRUB:
[[IMG]http://img528.imageshack.us/img528/3223/upload02so3.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload02so3.png)

The I have installed GFX GRUB:
[[IMG]http://img528.imageshack.us/img528/9369/upload2nn7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload2nn7.png)

Then I have copied message.suse to /boot/grub:
[[IMG]http://img110.imageshack.us/img110/9762/screenshot3qs9.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot3qs9.png)

Then I have backup /boot/grub/menu.lst and edited it:
[[IMG]http://img528.imageshack.us/img528/3715/screenshot4pb6.th.png[/IMG]  ](http://img528.imageshack.us/my.php?image=screenshot4pb6.png)[[IMG]http://img528.imageshack.us/img528/7362/screenshot5iy4.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot5iy4.png)

Then I have configured grub:
[[IMG]http://img110.imageshack.us/img110/4172/screenshot6yj5.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot6yj5.png)

After I did the following steps, when I switch on my computer nothing has changed to GRUB! Can someone help?

is hiddenmenu commented out?

---

### Post by Uji-Wu on 2009-01-19
Hé! Whatsup :)

I thought about making my own splash screen with a fat pingoin and a fat butterfly with both a list of instances of linux/windows under them, and with some lighting effect..

Like i'd boot my pc then select the pingoin or butterfly with left and right then up and down to select the instance....


But yet, thats just projects...

Currently, i messed grub by installing a third windows (i was bored to delete windows at each times i had spies) (so i make windows, windows.0 and windows.1 sharing the same program files with some realy non-technical ways:P

I'd like to install gfxboot as it is currently, mayby with a nice sweet beautiful theme as i found elsewere.... But i would have to do it  like from an usb drive or from a lan connection installation or such... I had a friend installing gnome from lan by "dos" (dos is the only name i can find to name what isnt dos) XD

Mayby i could also do that from the live cd... :P Couldnt quite guess how:P

I know that there might be tutorials to install classic grub in many diferant ways.. i even found one meant to be used on ntfs ( [http://www.geocities.com/lode_leroy/grubinstall/](http://www.geocities.com/lode_leroy/grubinstall/) ) But i realy would bounce if i had gfxboot :P


Thanx for any further help :)

---

### Post by Uji-Wu on 2009-01-19
[IMG]http://fc17.deviantart.com/fs40/f/2009/019/1/3/GFXBOOT_grub_idea_by_dijimucks.png[/IMG]

Thats nearly what i had in mind:P

The idea is more to have some arcade alure than realy splitting osses... :P

Even thought.. That'd be cool to be able to change boot order from this menu so if i feel like using fedora for a while i put it on default directly from the boot loader:P :)

---

### Post by Siracide on 2009-01-20
I am just tired of this!... never got it working followed the steps mentioned above since the very beginning...
now looking at the last post that Mr. Penguin or Mrs. Penguin not ofense! OK!...
I did download the gfxboot files and everything he/she mentioned... [WWW.SIDIUX.COM](WWW.SIDIUX.COM) to be exact!... MR/Mrs "RJQ"
Anyways... doing everything that I've seen so far... and by the way, I am using Ubuntu 8.10 Ultimate edition 2.0... which I honestly though it was better than suse... 
I could never have my customize GRUB, after a lot of errors, installs and uninstalls... now finally, ERROR 11: UNRECOGNIZED DEVICE STRING!... #$^%*+!..@.... (^_^) ... SORRY...
But it freaks me out!... LOL...

By the way, any help... thanks for the 670 replies... and for the people that got lucky setting up their GRUB...


:s ... i give up!...

---

### Post by Uji-Wu on 2009-01-20
lol:P

The best way i'd like to learn about installing grub/gfxboot would be to do it via booting... To nearly have grub/gfxboot as an installable exploitation system.... Detecting all instances of installed operation sytems.... I'd even imagine virtualbox to be loadable from this point in standalone without the need of loading neither win or lin. Like..... a setup loadable from an usb key on boot.... (i feel like repeating:P)

The wierdest is that when i installed gfxboot a while ago, and that it didnt work, the grub i reinstalled was generic grub with the blue-white-black screen:P

Mayby a good way of installing gfxboot would be to install OpenSuse aside of ubuntu and windows? Then modifying the skin and all? Or installing suse's boot loader without installing suse totaly? (if there is some way of keeping the loader without endin the setup?)

---

### Post by ov7a on 2009-01-26
Hi! I've everything, but I've got the same error zinc.tw told about:
> and then, you may touch the problem "invalid file format!
Anybody solved that? How can I update message, for example message.blusplash?
P.s. ubuntu 8.10 32bit.

---

### Post by DeltaFee on 2009-01-29
Hi, I followed the instructions and I still can't seem to get it to work

---

### Post by RJQ on 2009-01-30
I see there is some frustration on this set up, I know it because I also did give up for a wile before getting things working again, for me the point in getting this working is that when either my wife or son get into the computer they do not think they just broke it when the classic old grub dialog appears, therefore making the selection more appealing is a must for me.

In the original how to, the gfxboot theme was installed or placed in /boot/grub/ (along with the menu.lst per say) but now at least for me that would not do it, I have to actually install one of the sidux themes (suse ones didn't work) with a .deb file and that placed three files in /boot/ not in /boot/grub/ one of this been just a link to the second installed file the actual message, in menu.lst the file to point with the gfxboot line is /boot/message (this is the link) otherwise pointing to the actual message file will give me an error (this is using gfxboot /boot/messege.hd line in menu.lst) once the theme worked I was able to change the background.

In resume install latest gfxboot (either for hardy or intrepid) as described in the first post > install the message.deb > (check that the files mentioned above exist in /boot/) > change the menu.lst and place in the beginning of it gfxboot /boot/message > experiment with the message.hd to fit your likeness > remember that even one letter wrong and you will get an error.

And of course eye candy without a purpose is just fanciness.

---

### Post by DeltaFee on 2009-01-30
I am still not entirely sure: heres my menu.lst
> 
gfxmenu /boot/messages.blue

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,1)/boot/grub/splashimages/68224-tux_splash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu 8.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
boot

#title		Microsoft XP Pro
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro single
#initrd		/boot/initrd.img-2.6.24-23-generic
#boot

title		Ubuntu 8.04(recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0b224239-ac94-4721-99f8-46a7e4bb2fcc ro single
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by jw5801 on 2009-01-30
> **DeltaFee said:**
> I am still not entirely sure: heres my menu.lst

It should be **message**.blue not messages.blue. Unless you've renamed the file.

---

### Post by DeltaFee on 2009-01-31
heres my /boot directory:
> 
abi-2.6.24-19-generic             initrd.img-2.6.24-23-generic.bak
abi-2.6.24-23-generic             memtest86+.bin
config-2.6.24-19-generic          _messages.blue_
config-2.6.24-23-generic          System.map-2.6.24-19-generic
grub                              System.map-2.6.24-23-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak  vmlinuz-2.6.24-23-generic
initrd.img-2.6.24-23-generic


---

### Post by RJQ on 2009-02-03
> **DeltaFee said:**
> heres my /boot directory:

I do not like to sound "pushy" but why don't give a try to the theme I mention, although it may not work either you do not have any thing to loose, try this [link]("http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/") there just download any theme and install the .deb, that will give a least two files in your /boot/ directory (not just one) the message itself and a link to it, I have no idea why does not work without the link a least for me, if you get it to work then you can replace the theme but live the link along. again suse or ubuntu themes didn't work for me.

---

### Post by DeltaFee on 2009-02-04
> **RJQ said:**
> I do not like to sound "pushy" but why don't give a try to the theme I mention, although it may not work either you do not have any thing to loose, try this [link]("http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/") there just download any theme and install the .deb, that will give a least two files in your /boot/ directory (not just one) the message itself and a link to it, I have no idea why does not work without the link a least for me, if you get it to work then you can replace the theme but live the link along. again suse or ubuntu themes didn't work for me.

I try to install one of your themes, but it gave me an error on sidux. I didn't notice any installer of sidux. This may seem Newbe but am I suppose to compile the source code that you give?

---

### Post by RJQ on 2009-02-04
> **DeltaFee said:**
> I try to install one of your themes, but it gave me an error on sidux. I didn't notice any installer of sidux. This may seem Newbe but am I suppose to compile the source code that you give?

Use the [link]("http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/") I give to you, it is not "my" theme this sidux is a distro (like ubuntu) based on the unstable debian, there download any theme, that is a .deb package ready to install, no compilation need it, just like any other package click on it and it will tell you if a dependency is required, then the installation will happen. after installation you will find the messages files in the /boot/ directory, I have no idea why the error but there is no need of anything else but installing the .deb package. try that first then we can go for the next step if you like so.

---

### Post by DeltaFee on 2009-02-05
I tried installing the chaos theme but I get This is error. 
> 
Error: can't install /boot/message


Not quite sure whats wrong.

---

### Post by Clint000 on 2009-02-15
Hi RJQ,
thanks to your guidance I eventually managed to have a working screen in Intrepid with gfx-boot_0.97-40 (had to install grub-common package as well). 
Could you please explain how you did to change the background image to a customized one? You mentioned it was done by playing with message.hd but I haven´t been able to get it working.

Thanks

---

### Post by UbNewbie on 2009-02-18
> **Clint000 said:**
> Hi RJQ,
thanks to your guidance I eventually managed to have a working screen in Intrepid with gfx-boot_0.97-40 (had to install grub-common package as well). 
Could you please explain how you did to change the background image to a customized one? You mentioned it was done by playing with message.hd but I haven´t been able to get it working.

Thanks

Yes true. I have also mentioned yesterday that you need a new grub-gfxboot version with Intrepid.
But now all other standard message.* from e.g. art-gnome doesn't work at all.
You get error message "invalid file format".

I get manage to install gfxboot-theme-zen and compile it for use. I works fine but I want to change the background etc..
Somebody that can point me to the right direction?
E.G. changing the background, font type, size etc...
It is hardly to find any document regarding the gfxboot theme.....

Any help will be appreciated..

H2T

---

### Post by rmflagg on 2009-02-19
Hi everyone,

   This seems to be a common problem that many people are having with the older gfxboot themes and the newer versions of gfxboot.
   I would *really* like to use some of the older themes with Intrepid.  Can anyone out there(like, maybe the people who MADE the original themes) tell us how to change the themes so that we don't get the "invalid file format" error?  How about some of the folks who made the new themes?  What is the wizardry involved in getting these really nice themes converted?

Thanks,
RM Flagg

---

### Post by traceurST on 2009-02-20
Hi! 
I tried to configure gfxgrub on ubuntu 8.10 following first post, but when I reach grub> find /boot/grub/stage1, it allways returns "Error 15: File not found" 
Please, help me, I don't know what I did wrong...

---

### Post by UbNewbie on 2009-02-20
> **traceurST said:**
> Hi! 
I tried to configure gfxgrub on ubuntu 8.10 following first post, but when I reach grub> find /boot/grub/stage1, it allways returns "Error 15: File not found" 
Please, help me, I don't know what I did wrong...

Hi traceST,

Which version of grub-gfxboot are you using?
You need definitely the version 0.97-40. You can download it from [http://www.sidux.com/debian/pool/main/g/grub-gfxboot/](http://www.sidux.com/debian/pool/main/g/grub-gfxboot/)
Another things that you need to install extra is grub-common from ubuntu repository.

Hope this helps.

Regards,

H2T

---

### Post by RJQ on 2009-02-20
Sorry I was not around, my fault.

to every one, my recommendation is (and for those with 8.10 system is a must) to use the method at the beginning **_but with the latest packages_**, I remember that just for the sake of been "clean" I used the grub-gfxboot, the grub-common and the theme from sidux (rather than using one from here another from there...) and the rest of the story is all ready posted.

Now for changing JUST the background I use a tutorial from the suse website which only knowledge needed was compressing the folder. now I remember that there is several tutorials on how to make your own theme but that is beyond any thing I know for now. You can extract the message contents then play with the picture trying to keep the dimensions and the size about the same then in that folder directory just doing with the terminal a compression "sudo ls . |cpio -o > /boot/message.yours" will do the trick.

I have not a hand any link for those tutorials but I am sure saint google will provide some paths... try suse gfxboot how to, or something like so.

---

### Post by Tom_T on 2009-02-22
> **Uji-Wu said:**
> [IMG]http://fc17.deviantart.com/fs40/f/2009/019/1/3/GFXBOOT_grub_idea_by_dijimucks.png[/IMG]

Thats nearly what i had in mind:P

The idea is more to have some arcade alure than realy splitting osses... :P

Even thought.. That'd be cool to be able to change boot order from this menu so if i feel like using fedora for a while i put it on default directly from the boot loader:P :)

Hi
Only just started reading this thread.. but is that image possible ?

It would make it much easier for the wife and kids if it is !!
If so HOW ?  Thanks :)

---

### Post by wsonar on 2009-02-24
trying to get this to work after doing 

:/boot/grub$ sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.


/boot/grub$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x916e916e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4463    15360000    7  HPFS/NTFS
/dev/sda3            6083        9729    29294527+  83  Linux
/dev/sda4            4464        4866     3237097+   5  Extended
/dev/sda5            4464        4866     3237066   82  Linux swap / Solaris

---

### Post by wsonar on 2009-02-24
Now I boot directly to the grub  SETUP screen.

Everthing was working fine fresh install today of XP, then Vista, Then Ubuntu,

Tested booting to all then tried to install GFXboot thats when I ran into problems

need help getting things back in order and getting gfxboot to work would be greatly appreciated.

Thank you...

---

### Post by wsonar on 2009-02-24
> **PingunZ said:**
> Gfxboot makes grub look nicer but with the same features
In this howto you will install gfxboot and a suse theme for it, soon I'll make an ubuntu one ;) 
Ok, let's start

Download the [grub-gfxboot.deb]("http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb")
And the [message.suse ]("http://quasarfreak.googlepages.com/message.suse")

First remove your old grub
```
sudo apt-get remove grub
```

Then Install the gfxboot-grub
```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
```

then we're going to move the message
```
sudo cp message.suse /boot/grub/ # the suse can be replaced by the one you downloaded 
```

Then edit your menu.lst

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
and make it use gfxboot
```
gfxmenu /boot/grub/message.suse # the suse can be replaced 
```


Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

-- Howto make you own theme --


```
mkdir /home/name/whatever
cpio -i < /boot/grub/message.suse # replace it by the name of you message
edit the pictures
sudo ls . |cpio -o > /boot/grub/message.new
```

Reboot and enjoy ;)
Thanks to Quasar_freak and kno

here are some themes posted in this thread ;) ( ty :KS  )

Light Green generic theme [message.gobo] | [Link](http://ubuntuforums.org/showpost.php?p=1214274&postcount=12) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288)
Dark Brown (Dapper look) generic theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544)
Medium blue kubuntu theme [message.kubuntu] | [Link](http://ubuntuforums.org/showpost.php?p=1234300&postcount=54) | [Screenshot](http://files.upl.silentwhisper.net/upload5/gfxboot.jpg)
Dark grey ubuntu theme [message.ubugrey] | [Link](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717)
Medium brown ubuntu theme [message.ububrown] | [Link](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657)
Light orange ubuntu theme [message.ubu] | [Link](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852)
Red ubuntu theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852)
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746)
White / Grey Snowish generic theme [message.snow] | [Link](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506)
Linspire-style blue kubuntu theme [message.kubu] | [Link](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390)
Old- Grub style dark blue and light blue [message.kubu] | [Link](http://mitglied.lycos.de/atoth/ubuntuusers/message.napo) | [Screenshot ]("http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo.png")
Light blue / grey Xubuntu theme [message.xubu] | [Link](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350)


Grtz PingunZ[/QUOTE]





I try this exactly and at the point I get to grub> find /boot/grub/stage1

get error

grub> find /boot/grub/stage1

Error 15: File not found

grub>

---

### Post by wsonar on 2009-02-24
I don't want to shut down because then I can't boot up any suggestions on how to make this work on 8.10

---

### Post by wsonar on 2009-02-25
I restored my old grub but would like to still figure out why gfx will not work...

---

### Post by traceurST on 2009-02-28
I finally succeded to instal new gfxboot, and common-grub, without any errors, but there is stil old fu**** grub.. I'm using Ubuntu 8.10 Intrepid Ibex, and all new files for gfxboot, except message.something... Can ANYONE please tel me which message. I can use on Intrepid?
Thx

---

### Post by wsonar on 2009-03-02
I got my gfxboot wroking :P

So I ended up just coping over the little data I had to the ntfs part this was a pretty fresh install of all os's it apears it was ext3 after all

I then booted to the  ubuntu 8.04 cd deleted the linux and swap made the sawp 2 gig and the rest for the linux which was ext 3 and primary 


after the install grub was back and  booted into ubuntu 8.04 

before getting any update

I followed the how to for the gfxboot here

[http://abhay-techzone.blogspot.com/2007/10/howto-have-grub-like-suse-on-ubuntu.html](http://abhay-techzone.blogspot.com/2007/10/howto-have-grub-like-suse-on-ubuntu.html)

rebooted and wolla I had my cool themed bootloader 

I tested booting into each os 

I then got all critical security updates

after testing was still good then got recomended updates

---

### Post by wsonar on 2009-03-02
> **traceurST said:**
> I finally succeded to instal new gfxboot, and common-grub, without any errors, but there is stil old fu**** grub.. I'm using Ubuntu 8.10 Intrepid Ibex, and all new files for gfxboot, except message.something... Can ANYONE please tel me which message. I can use on Intrepid?
Thx

you can go here and search for gfxboot and there is about 4 pages of them you can get....not to mention alot of other cool gnome stuff



[http://www.gnome-look.org]("http://www.gnome-look.org")

I like the message.linuxhack

---

### Post by rmflagg on 2009-03-02
Ok...which of the gfxboot themes on gnome-look.org will work under the newest version of gfxboot?

---

### Post by pantelis20 on 2009-03-07
Check this out [http://www.gnome-look.org/content/show.php/Debian+Orange+-+GRUB+gfxboot?content=93581](http://www.gnome-look.org/content/show.php/Debian+Orange+-+GRUB+gfxboot?content=93581)
If you like additional themes then go to [http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/](http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/)
These are deb packages and what they do is that they extract the message.xxx to /boot/.If you like you can right click to the deb packages and select extract here.Then open the extracted folder and do the same to the data.tar.gz and then you will be able to find the message.hd and place it manually to /boot/grub.This stuff worked for me on ubuntu 8.10 and grub gfx grub-gfxboot_0.97-40_amd64.deb package which i downloaded from [http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/](http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/).Warning.Everything worked fine until an update of kernel, then it gave to me error 11.I still cannot figure out what went wrong.After the update of kernel I was not able to boot to my ubuntu desktop since I got error 11.Try at your risk.All the other time it was working perfect.

---

### Post by pantelis20 on 2009-03-08
-----------------------------------------------------------------------------------------

---

### Post by aniruddha on 2009-03-10
Would it be possible to find out:

a) how to create (or edit) our own gfxboot themes? 
b) which of the older themes are compatible with 8.10? 

the opensuse tutorial is a bit unhelpful and the methods in various threads around this forum are rather confusing (to a relatively new ubuntu user). 

thanks.

---

### Post by Gerinych on 2009-03-11
I have GFXboot on a separate partition, and I can't use it to boot Ubuntu. It gives me "Error 2: Bad file or directory type" when it tried to load the kernel. Here's my menu.lst:
```
gfxmenu /boot/grub/message.snow
default saved
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b626a3ea-fa85-4454-9b72-94520b0296a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b626a3ea-fa85-4454-9b72-94520b0296a7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu 8.10
kernel		(hd1,0)/boot/vmlinuz-2.6.27-11-generic root=/dev/sdb1 ro quiet splash vga=795
initrd		(hd1,0)/boot/initrd.img-2.6.27-11-generic
boot

title		Ubuntu 8.10 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b626a3ea-fa85-4454-9b72-94520b0296a7 ro single
initrd		/boot/initrd.img-2.6.27-11-generic
boot

title		Ubuntu 8.10 memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title		Windows Vista Ultimate
root 		(hd0,0)
chainloader 	+1 /vstaldr
savedefault
makeactive

```

---

### Post by pantelis20 on 2009-03-15
About how to edit your own theme you can change the pictures of it and put any picture you want.To do this extract the folder and then replace the picture.The picture should be 800x600.Name it as the original picture of the theme and delete the original one.Then you have to compress the folder with the containing stuff of the theme.To do this open a terminal and type something like cd /home/yourname/Desktop/files (if you have the files needed to the Desktop to the folder files) and then type ls | cpio -ov > message.This command will compress the files needed inside to the /home/yourname/Desktop/files/ with the name message.After that you can rename message to message.xyz if you want and place it manually to the /boot/grub or whatever you may want.If you see black screen then the picture would be not suitable due to depth of colour.Unfortunately I don't know the suitable value of it so you have to test some pictures yourself.If you download a theme from [http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/](http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/gfxboot-theme-sidux/) then another option is to have a theme with some penguins walking.You can do this by extracting the theme and edit the gfxboot.cfg by deleting the line "welcome=0" and editing line penguin=0 to penguin=x where x is the percentage of how often the penguin randomly appear.The penguin=0 is never, the penguin=50 means half of boots likely and the penguin=100 means always.Then you have to compress the folder as previous.If you use the theme with the penguin do not delete or rename any other of stuff even the original picture.The only thing needs to be changed is the gfxboot.cfg.If you don"t know how to find the theme of the link which I give read the second from the bottom post from here [http://ubuntuforums.org/showthread.php?t=208855&highlight=gfx+grub&page=70](http://ubuntuforums.org/showthread.php?t=208855&highlight=gfx+grub&page=70) where I explain how to.

---

### Post by hienfy on 2009-04-03
I followed the steps until 

sudo grub-install hd0
The file /boot/grub/stage1 not read correctly.

Anyone has any ideas? It seems that grub is worknig find, i could do a $find /boot/grub/stage1 . But, when i install the grub-gfxboot package, my grub fails to find stage1 and gives a error 15 File not found.

---

### Post by bmhm on 2009-04-04
> **hienfy said:**
> I followed the steps until 

sudo grub-install hd0
The file /boot/grub/stage1 not read correctly.

Anyone has any ideas? It seems that grub is worknig find, i could do a $find /boot/grub/stage1 . But, when i install the grub-gfxboot package, my grub fails to find stage1 and gives a error 15 File not found.

I got it working by installing **grub-common**.

---

### Post by sirko on 2009-04-04
I'm gettting this error:
```
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> 

grub> grub> find /boot/grub/stage1

Error 27: Unrecognized command

grub>
```
Can anyone help please, I done all steps in first page but still old grub

---

### Post by bmhm on 2009-04-04
> **sirko said:**
> I'm gettting this error:
```
 
grub> grub> find /boot/grub/stage1

Error 27: Unrecognized command

```
Can anyone help please, I done all steps in first page but still old grub

Either you were in a hurry or you shouldn't be changing your grub yet. You pasted the prompt.
If you don't know what you're doing, **DO NOT** just copy-paste commands here. Really. If anything messes up, you cannot boot anymore.


Another issue: Can some1 tell me where to get themes for the NEW version? It's got another message file format.

---

### Post by jw5801 on 2009-04-04
> **sirko said:**
> I'm gettting this error:
```
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> 

grub> grub> find /boot/grub/stage1

Error 27: Unrecognized command

grub>
```
Can anyone help please, I done all steps in first page but still old grub

Ok, 'grub>' is the command prompt you get when you enter the grub shell. 'find /boot/grub/stage1' is the command you want to run at this prompt. You've copied and pasted the 'grub>' in as part of the command, hence the shell can't find the command you gave it.

---

### Post by hienfy on 2009-04-04
What exactly is grub-common? I was fiddling with grub-gfxboot but, somehow installing results in failing to find /boot/grub/stage1 despite it being there. However, when i restore the original grub via sudo apt-get install grub, i'm able to perform find /boot/grub/stage1. 

Hence, does grub-gfxboot works with ubuntu 8.1 or..? It seems like i started with a clean ubuntu install and followed the tutorial completely, but grub-gfxboot just stubbornly dont work.

---

### Post by har02052 on 2009-04-05
I followed the tutorial but I am running into a problem towards the last steps.  if I:

sudo grub

then

find /boot/grub/stage1

but I get a file not found error.

Somebody help me out here.  Thanks

---

### Post by bmhm on 2009-04-05
> **har02052 said:**
> 
find /boot/grub/stage1

but I get a file not found error.

As some1 said before, the tutorial was not written for 8.10 (and not for amd64).
I made it work by installing **grub-common**.
Be sure to install grub-gfxboot version -11, not the more recent -40, or your bootsplashes won't work anymore.

---

### Post by Jordanwb on 2009-04-14
> **PingunZ said:**
> 
Then do : ```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

bash: grub: command not found

I'm running 9.04 amd64 beta

---

### Post by Yathi on 2009-04-19
Bro dont just keep sayin install grub-common. Grub-common was already installed so i removed and installed it again and still it gives me the same thing. 

```
yathi@Zangetsu:~$ sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.

```

---

### Post by Yathi on 2009-04-25
Does anyone see this post now???

---

### Post by markitoxs on 2009-04-26
I did. Thanks for the guide, required a little bit of tweaking but wirked fine.

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111185[/ATTACH]

Hope this helps

---

### Post by camper365 on 2009-05-10
> ```
sudo grub

grub> find /boot/grub/stage1
  (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

```

When I run grub, it can never find /boot/grub/stage1
I have /boot on a separate partition, so I tried /grub/stage1 but it still didn't work.
I did ```
apt-get install grub
``` and it worked just fine.
The problem with that is that it removed gfx-boot.

---

### Post by Kor-Skarn on 2009-05-10
Finally got my gfxboot working on 64-bit system with ext4 root partition. Not much proper info out there. For those who were wondering why the instructions from the Howto don't work on their 64-bit architecture, particularly why they get error "grub> Error 15: file not found" for their "find /boot/grub/stage1" command (even when it's positively there), here's the answer:

GRUB-gfxboot can't read your filesystem, because it doesn't support it. Especially true and confusing for ext4, when it detects the FS as ext2fs (seemingly correctly) with "root (hdx,y)" command, but can't read it (or search in it).

This was valid for versions < -40, so version -11 doesn't work with ext4! Version -40 from sidux works fine though, I tried it with Debian Orange theme from KDE-Look.org.  But maybe recompile for some themes is needed?

(P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)

---

### Post by camper365 on 2009-05-10
That explains my problem. I didn't know that ext4 had anything to do with it.
I thought that ext4 was supposed to be backwards compatible with ext2 and ext3

---

### Post by Malac on 2009-05-11
> **Kor-Skarn said:**
> (P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)
You're Welcome. Glad I could help. :D

---

### Post by Andreas_H on 2009-05-14
@Malac

I tried your message.new, but grub complains it is too large on boot.

Any Ideas?

bye,
Andreas

---

### Post by Malac on 2009-05-14
> **Andreas_H said:**
> @Malac

I tried your message.new, but grub complains it is too large on boot.

Any Ideas?

bye,
Andreas
Did you install the 40 .deb file from sidux.com?
It works fine on my main machine and on a couple of other test machines too (intrepid and jaunty).
And a few people have downloaded it and it works on their machines.
Do you have a separate /boot partition?
Only other thing I can think of is memory but it works on a 512MB machine of mine so unless yours is really low on memory, I don't know. Sorry.

---

### Post by zero7404 on 2009-05-14
> **Kor-Skarn said:**
> Finally got my gfxboot working on 64-bit system with ext4 root partition. Not much proper info out there. For those who were wondering why the instructions from the Howto don't work on their 64-bit architecture, particularly why they get error "grub> Error 15: file not found" for their "find /boot/grub/stage1" command (even when it's positively there), here's the answer:

GRUB-gfxboot can't read your filesystem, because it doesn't support it. Especially true and confusing for ext4, when it detects the FS as ext2fs (seemingly correctly) with "root (hdx,y)" command, but can't read it (or search in it).

This was valid for versions < -40, so version -11 doesn't work with ext4! Version -40 from sidux works fine though, I tried it with Debian Orange theme from KDE-Look.org.  But maybe recompile for some themes is needed?

(P.S. Big thanks to Malac for pointing out the new -40 package from sidux!)

i want to install gfxboot, but i'm running 8.10 x64, can you give some guidance or maybe start a howto on getting gfxboot installed properly on x64 flavors ?

i am confident in doing this without much concern, i've made complete backups using clonezilla (including grub), so if anything goes wrong i can revert in a matter of minutes....

---

### Post by Andreas_H on 2009-05-15
> **Malac said:**
> Did you install the 40 .deb file from sidux.com?
It works fine on my main machine and on a couple of other test machines too (intrepid and jaunty).
And a few people have downloaded it and it works on their machines.
Do you have a separate /boot partition?
Only other thing I can think of is memory but it works on a 512MB machine of mine so unless yours is really low on memory, I don't know. Sorry.

I used the 40 .deb, but forgot to run grub-install afterwards. Now it works, thanks!

---

### Post by nsfnd on 2009-05-15
Thx everyone for your informative posts, i learned alot :)

I have a problem about grub-gfx, whatever file i put after gfxmenu command in menu.lst, grub says "invalid file format". I think im missing something.

I have 32-bit jaunty. Installed on nvidia fakeraid.
My root is ext4 and i have a boot partition which is ext3, my menu.lst looks like "gfxmenu  /grub/message.suse".
Im using -40 version of grub-gfx. 
Any thoughts?

---

### Post by zero7404 on 2009-05-15
> **nsfnd said:**
> Thx everyone for your informative posts, i learned alot :)

I have a problem about grub-gfx, whatever file i put after gfxmenu command in menu.lst, grub says "invalid file format". I think im missing something.

I have 32-bit jaunty. Installed on nvidia fakeraid.
My root is ext4 and i have a boot partition which is ext3, my menu.lst looks like "gfxmenu  /grub/message.suse".
Im using -40 version of grub-gfx. 
Any thoughts?

after looking at numerous howto's, and getting the latest 64-bit deb package for gfxboot (-40 as well), i also have the same issue, invalid file format. i've tried various other message files/themes and it still gives the same message. also tried changing the path from /boot/grub/ to just /grub/, didn't work....

---

### Post by Malac on 2009-05-15
> **nsfnd said:**
> Thx everyone for your informative posts, i learned alot :)

I have a problem about grub-gfx, whatever file i put after gfxmenu command in menu.lst, grub says "invalid file format". I think im missing something.

I have 32-bit jaunty. Installed on nvidia fakeraid.
My root is ext4 and i have a boot partition which is ext3, my menu.lst looks like "gfxmenu  /grub/message.suse".
Im using -40 version of grub-gfx. 
Any thoughts?

> **zero7404 said:**
> after looking at numerous howto's, and getting the latest 64-bit deb package for gfxboot (-40 as well), i also have the same issue, invalid file format. i've tried various other message files/themes and it still gives the same message. also tried changing the path from /boot/grub/ to just /grub/, didn't work....

Did you re-compile the message files on your system?
Also you must run the grub-install command as well or you run the risk of still having the old grub in your mbr or partition.
This could possibly throw up this invalid file format error.

---

### Post by ascendotuum on 2009-05-15
> **Malac said:**
> Did you re-compile the message files on your system?
Also you must run the grub-install command as well or you run the risk of still having the old grub in your mbr or partition.
This could possibly throw up this invalid file format error.

I am also having the same problem as those two, the invalid file format error. I used the -40 version, and did run grub-install at the end.

I'm a linux noob so can you explain what re-compiling the message files means? I'm using the message.ububrown theme that I found on the first page of this thread, and I haven't modified it

oh and I'm running 32-bit jaunty on a dell xps1530, if that makes any difference

---

### Post by nsfnd on 2009-05-15
> **Malac said:**
> Did you re-compile the message files on your system?
Also you must run the grub-install command as well or you run the risk of still having the old grub in your mbr or partition.
This could possibly throw up this invalid file format error.

Thx for the reply.
Until now i thought just installing the grub-gfx and copying message.x to /grub folder was enough to make it work.  

I dunno howto compile the message.

So what i just did was,

> sudo apt-get remove grub (grub package is not installed, so not removed)
Then i reinstalled grub-gfxboot_0.97-40_i386.deb by double clicking on it.
Checked message.suse if it was in the right place. (/boot/grub/message.suse)
sudo grub
device (hd0) /dev/mapper/nvidia_bhiaefdi
find /grub/stage1
 (hd0,0)
root (hd0,0)
setup (hd0)

 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  18 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+18 p (hd0,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

quit

sudo grub-install /dev/mapper/nvidia_bhiaefdi
error: out of disk
error: no signature
error: out of disk
error: no signature
error: out of disk
error: no signature
error: out of disk
error: no signature
error: out of disk
error: no signature
Searching for GRUB installation directory ... found: /boot/grub
error: out of disk
error: no signature
grub-probe: error: no mapping exists for `nvidia_bhiaefdi1'
[: 378: =: unexpected operator

At this point when i tried to boot (with VirtualBox physical disk) it threw me to "grub>" console.

So i had to reinstall the grub back to mbr by "sudo grub" ..
Thats about it ye :)

---

### Post by zero7404 on 2009-05-15
> **Malac said:**
> Did you re-compile the message files on your system?
Also you must run the grub-install command as well or you run the risk of still having the old grub in your mbr or partition.
This could possibly throw up this invalid file format error.

i followed the proceedure in the first post, but also looked at this thread:

[http://ubuntuforums.org/showthread.php?t=481957&highlight=gfxboot](http://ubuntuforums.org/showthread.php?t=481957&highlight=gfxboot)

one of the things i dislike about forums like this one is the 'missing' information from howto's that many ppl use, no admins out there taking a look or checking these howto's to be sure something is not missing, nor are any other posters doing the same. ESPECIALLY when it comes to things like grub.

if i knew i had to re-compile the theme, i would have done it, but no one mentioned this on any other thread i've looked at, this is the first time i am hearing about it. the themes i am looking to use i am getting from GNOME-look.org and even they don't give any specific information on recompiling the theme for use.

and how do i recompile a theme ? when i click on it in nautilus, an extractor shows me some contents - mainly image files and some other stuff.....

UPDATE: i found out how to compile the themes, but only the themes downloaded from synaptic. additionally, the ubuntu theme in synaptic does not compile, it's size is much smaller than the other themes, perhaps it is incomplete.

i found that after downloading the package from synaptic, i need to navigate to the package's folder (/usr/share/gfxboot-theme-xxxx), then:

sudo make
sudo make install
cd install
sudo -s
ls . |cpio -o > /boot/grub/message.xxxx  #### theme file name

the above is per post #634. also note that when i tried this with the ubuntu theme from synaptic, the make command just returned an error and nothing compiled.

when compiling any theme except the ubuntu one, setting up menu.lst, the themes work fine. but those themes aren't what i want. when trying to use the themes from gnome-look art, they don't make sense as to what they are and how i should compile them. simply using the filename message.xxxx in menu.lst and placing the file in /boot/grub/ does not work.

---

### Post by ascendotuum on 2009-05-18
So did anyone find a solution for the "file format invalid" error during boot?

I see alot of threads of people complaining about it, but no one seems to have found a fix for it.

---

### Post by rubioxtu on 2009-05-21
> **ascendotuum said:**
> So did anyone find a solution for the "file format invalid" error during boot?

I see alot of threads of people complaining about it, but no one seems to have found a fix for it.

I haven't tried yet, but I think you have to edit/compile from source
or get a theme compiled with new gfxboot installed (or make your own theme).

Some themes with source included:

[http://gnome-look.org/CONTENT/content-files/76032-gfxboot-theme-ubuntumsk-1280x1024.tar.gz](http://gnome-look.org/CONTENT/content-files/76032-gfxboot-theme-ubuntumsk-1280x1024.tar.gz)
[http://gnome-look.org/CONTENT/content-files/76029-gfxboot-theme-ubuntumsk-1024x768.tar.gz](http://gnome-look.org/CONTENT/content-files/76029-gfxboot-theme-ubuntumsk-1024x768.tar.gz)
[http://gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668](http://gnome-look.org/content/show.php/gfxboot+ubuntu+red+mod?content=71668)
[http://gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720](http://gnome-look.org/content/show.php/GFXBoot+message.blueAqua?content=72720)
[http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735](http://gnome-look.org/content/show.php/GFXBoot+message.Snaiya++?content=71735)

---

### Post by Malac on 2009-05-22
> **ascendotuum said:**
> So did anyone find a solution for the "file format invalid" error during boot?

I see alot of threads of people complaining about it, but no one seems to have found a fix for it.
> **rubioxtu said:**
> I haven't tried yet, but I think you have to edit/compile from source
or get a theme compiled with new gfxboot installed (or make your own theme).

+1 to rubioxtu's suggestion.
I think the message file format changed.
A lot of the themes on gnomelook.org are old format so will have config files missing or bad install files.
The older formats work with versions upto 0.97-11 you probably will need to re-compile themes if you are running the latest 0.97-40 grub-gfxboot.

This can be done for the themes in synaptic as follows:
Navigate to the package's folder (/usr/share/gfxboot-theme-xxxx), then:
```

sudo make
sudo make install
cd install
sudo -s
ls . |cpio -o > /boot/grub/message.xxxx #### theme file name

```
The gfxboot-theme-ubuntu will not work with this method as it is really out of date now.
What I did to create my theme was to copy the /usr/share/gfxboot-theme-zen folder to /usr/share/gfxboot-theme-malac
then edited the files in /usr/share/gfxboot-theme-malac changed pictures, etc.
then used the compile commands in that folder.
This worked fine.

Hope this helps.

---

### Post by piratelv on 2009-05-22
Hi i followed your guide and at first i got nothing, just the standard, then i continued with some solution found on this forum but now i get a grub error 2. And can not boot. I still really want this nice menu but because i need my pc i'm recovering the vista mbr till i can get this to work. So if any one has a solution i would love to try it.

I reinstalled ubuntu 9.04 so i have a fresh system now, i still would like to have this neat boot menu.

---

### Post by mahsom on 2009-06-06
hi

What is Picture information of gfxboot ?
after change picture i recived error Frame_Buffer ; What is this ?
my resolation of monitor is 1440x900 .

---

### Post by hernandito on 2009-06-27
Hello,


I have tried and tried for days and while I made some progress, I have hit a wall. I have Ubuntu 9.04 running on a hard drive. My goal is to install the GRUB bootloader to a USB thumb drive so I can boot several utilities. I have tried many processes, and per Ryukent (a big THANK YOU!!!) post below, I have been able to have gfxboot working from the Ubuntu drive. But the gfxboot does NOT work when booting from USB drive. I get the bootloader, but no graphical menu.

> **ryukent said:**
> I got it working in a fresh install of Intrepid.

Problems I got were due to - 
* Old version of grub
* Original tutorial doesn't say to do grub-install
* message file needed to be recompiled

This is what I did

Went to:

[http://www.sidux.com/debian/pool/main/g/grub-gfxboot/](http://www.sidux.com/debian/pool/main/g/grub-gfxboot/)

Downloaded the latest version for my architecture

sudo apt-get remove grub

sudo dpkg -i grub-gfxboot_0.97-35_i386.deb

Note you need to be in the right dir (obviously) and change it to the one for your arch.

sudo gedit /boot/grub/menu.lst

Added: gfxmenu /boot/grub/message.suse

sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)

Obviously you need to change the X and Ys.

sudo grub-install /dev/sdaX

This was very important. Didn't work without it. Note the X is not the same number as the x or y in the previous section as grub uses different numbers. You need to look up the correct hard disk to use. It should be the one are booting to.



The trouble I believe is in the final step. After doing the find /boot/grub/stage1 I was able to install this step:
    grub> root (hd1,1) 
    grub> setup (hd1)

My trouble was in the last step using the sudo grub-install to get it to the thumb drive. I have tried the following without luck:

    sudo grub-install /dev/sdb1 - tried
    sudo grub-install /dev/sdb2 - tried
    sudo grub-install /dev/sda5 - tried
    sudo grub-install /dev/sda1 - tried

The thumb drive boots, but I don't get the graphic bootloader. All the abobe show an "installation finished" result, but no graphic.

 This is the result of my sudo fdisk -l
> 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007096

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fa005eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391    c  W95 FAT32 (LBA)
/dev/sdb2              14         983     7791525   83  Linux


  I have the message.blue message file loaded in the thumb drive's /boot/grub folder. This is the first line in the /boot/grub/menu.lst on the thumb drive:

  gfxmenu /boot/grub/message.blue

One thing is did, and I don't know if this is the culprit:

   sudo chmod -R 777 /media/TheNameofVolumeUSBDrive

I did this in order to easily copy files to the thumb drive. I did all these operations booted from Ubuntu on the standard hard drive. I am not sure how to reset this to the default, I am a Ubuntu newbie.

Can somebody please help!

Thank you!!
Hernando

---

### Post by hernandito on 2009-06-29
Anyone.....

---

### Post by R3N3GAD3 on 2009-07-05
I managed to get this solution working on ubuntu 9.04 64-bit.

The following site seems to have the most recent downloads for grub-gfxboot. There are also versions for both architectures (i386 and amd64).
[http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/](http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/)

Unfortunately, I wasted a lot of time trying different things to get it to work.

Three of the four gfx samples with source (given in this thread) do not compile in 9.04, and one compiles but craps itself at runtime. The background image is displayed, so I know if I spent some time with it would eventually work.

I found a compiled version that works with 9.04 (and apparently 8.10 as well, but I only tested it on 9.04).
[http://www.gnome-look.org/content/show.php/Ubuntu+Brown+Gfx+Grub+Theme?content=102595](http://www.gnome-look.org/content/show.php/Ubuntu+Brown+Gfx+Grub+Theme?content=102595)

This was a headache. It only took me half a day to get it working, but it was annoying. I wasted a lot of time reading through the hundreds of posts.

Does anyone have the source (or even a binary) for a working gfx sample in 9.04? I would rather not waste my time trying to debug the gfx samples if someone has a working revision.

---

### Post by Elv13 on 2009-07-27
For those who managed to build a new theme, can you make a small step by step guide?

I tried cpio on the (working) theme then cpio in the two subarchive, but I did not work once recompiled.

---

### Post by sfranzyshen on 2009-07-27
> **hernandito said:**
> Anyone.....

> **hernandito said:**
> sudo grub-install /dev/sdb1 - tried

how about just sdb ... not the begining of the partition but rather the mbr ...

sudo grub-install /dev/sdb


If that don't work you may want to checkout the syslinux project ... for booting from USB with gfxboot support.

[http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project]("http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project")

sfranzyshen

---

### Post by lookinggoodson on 2009-08-08
See this link for updated Howto:

[http://ubuntuforums.org/showthread.php?t=1221839&highlight=GfxBoot+Grub+suse+Updated]("http://ubuntuforums.org/showthread.php?t=1221839&highlight=GfxBoot+Grub+suse+Updated")

---

### Post by 600WPMPO on 2009-08-23
When i boot, the message says "invalid file format"

> A lot of the themes on gnomelook.org are old format so will have config files missing or bad install files. The message file format has changed. The older formats work with versions upto 0.97-11 you probably will need to re-compile themes if you are running the latest 0.97-40 grub-gfxboot.

This can be done for the themes in synaptic as follows:
Extract the theme to &#8220;/usr/share/gfxboot-theme-xxxx&#8221; then:

Code:
cd /usr/share/gfxboot-theme-xxxx/
sudo make
sudo make install
cd install
sudo -s
ls . |cpio -o > /boot/grub/message.xxxx #### theme file name

However, even this doesn't work.

Tried the themes gfxboot-theme-blueAqua-ubuntu & gfxboot-theme-ubuntumsk-1280x1024 with the above method, but get the same error at boot : invalid file format

Please help... :confused:

---

### Post by kevinguillorytraining on 2009-10-10
I am facing problem after following your instructions :(. My boot menu disappears and my computer is no more booting :( Should I reinstall OS?

---

### Post by Oneiros90 on 2009-10-25
Hello guys
So... last versions of gfxboot don't support old themes right? Couldn't we just use old gfxboot versions? Is gfxboot 0.97-11 still available on internet? 

Or... where could we find new themes? only on synaptic?

---

### Post by okmijn22 on 2010-01-16
Does this work with the latest version?

---

### Post by ahmad598 on 2010-01-17
hi
there's a problem here: I don't have any menu.lst! instead of that, there is grub.cfg. is it OK?

---

### Post by Chiapo on 2010-01-17
*buntu 9.10 uses the new "GRUB 2" which is quite different from the old GRUB (legacy) in that one does not directly edit the /boot/grub//grub.cfg file (although it's is possible) rather we edit other files in order to configure GRUB appearance & behavior.

GRUB2 how to:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Link to images of my GRUB2 menu:
[http://ubuntuforums.org/showpost.php?p=8466700&postcount=577](http://ubuntuforums.org/showpost.php?p=8466700&postcount=577)

---

### Post by archeryguru2000 on 2010-01-22
> **R3N3GAD3 said:**
> I managed to get this solution working on ubuntu 9.04 64-bit.

The following site seems to have the most recent downloads for grub-gfxboot. There are also versions for both architectures (i386 and amd64).
[http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/](http://ftp-mirror.internap.com/pub/sidux/debian/pool/main/g/grub-gfxboot/)

Unfortunately, I wasted a lot of time trying different things to get it to work.


Thanks alot for the link.  I was finally able to get gfxboot running properly.  However, with the new version (0.97-48), older versions of gfxboot do not work.  I plan on extracting everything and then recompiling them with something like
```
ls . |cpio -o > /path/to/message.whatever
```
to see if that works.

~~archery~~

---

### Post by Malac on 2010-01-23
> **archeryguru2000 said:**
> I plan on extracting everything and then recompiling them with something like
```
ls . |cpio -o > /path/to/message.whatever
```
to see if that works.

~~archery~~I posted a few pages back that this will work with some themes but not others due to some missing files or configuration differences. What I did was find one that did work then extract it to a new folder make any changes to the pictures, wording, etc. and then use that command to "recompile" it.

Hope this helps.

---

### Post by archeryguru2000 on 2010-01-23
Malac, I'm with you.  That's exactly what I plan on doing.  However, I have at least a couple dozen of the old style gfxboot themes (from my Hardy days) that I will have to alter now.  The only problem with that is I'm worried about the placement of text/words/timer-icon/etc.  I wish somebody (much techier than I) would create a gfxboot configuration tool that would allow me (and everyone else) to completely create their own themes.  But I'm sure that's only a matter of time.  Thank God there are OS's like Linux!

~~archery~~

---

### Post by xDoomsdayx on 2010-06-28
Im sorry to ressurect this thread but im in serious need of help, im in the process of making a multiboot usb so naturally i went for the grub4dos (latest version) everything is working nicely but then i found out about gfxmenu so i wanted a cool looking gui, so i got the cpio tool so I can extract the archives and everything but one thing bothers me, why isnt there a gfxboot.cfg file in every gfxmenu archive, im concerned about this because i want to set (for instance) how many entries is shown and i want to hide help, language button and show reboot and poweroff button also on some archives i downloaded the timer is not working although the timeout is set in the menu.lst file. As for the gfxboot.cfg i added a default one to the archives I found which were missing it, repackaged it but there are help and language buttons (F1 F2 shortcuts) as if i didnt specify it in the gfxboot.cfg, it is as if the file is ignored.

Thanks in advance,
xDoomsDayx

---

### Post by xDoomsdayx on 2010-07-05
bumpity

---

### Post by sebas9854 on 2011-07-14
This works on 11.04, right? (also, NEC-C-C-CRO!!

---

### Post by ptitpoul on 2011-08-03
It still works with 11.04.

---

### Post by shin333 on 2011-08-05
Hi all. I'm trying to get gfxboot working but I obviously have no idea what I'm doing. I got grub-gfxboot_0.97-11_amd64.deb and I'm trying to install that but when I did I got the message: 


shin@shin-laptop:/media/Data/Ubuntu Downloads$ sudo dpkg -i grub-gfxboot_0.97-11_amd64.deb
(Reading database ... 172460 files and directories currently installed.)
Unpacking grub-gfxboot (from grub-gfxboot_0.97-11_amd64.deb) ...
dpkg: error processing grub-gfxboot_0.97-11_amd64.deb (--install):
 trying to overwrite '/usr/sbin/grub-install', which is also in package grub-pc 0:1.98-1ubuntu12
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 grub-gfxboot_0.97-11_amd64.deb


I have no idea what any of that means.. any help would be appreciated. Thank you.

P.S. I hate it when I get stuck on the first step lol

---

### Post by ptitpoul on 2011-08-05
Tutorials to install grub-gfxboot are old (2006). Several tools have since changed. Gfxboot is a modification of grub-legacy and I have not seen any new Debian package since 2009 ([_0.97-48_]("http://www.mirrorservice.org/sites/ftp.mepis.org/mepis/pool/main/g/grub-gfxboot/")), although the development seems to be maintained on [_OpenSuse_]("http://en.opensuse.org/Gfxboot").
The archive you're trying to install is in conflict with your current version of grub (grub-pc = grub2). You need to remove grub-pc before. Using gdebi instead dpkg to install a downloaded package may have showed you a more "user-friendly" error... 
When I wrote it worked on Ubuntu 11.04, I should have added "since I installed it three years ago (and I have not modified it ever since)". Now with grub2 being the default boot manager, I don't know if you can downgrade to grub-gfxboot. Given your message, you don't seem to be familiar with Linux, so I suggest you to try [_BURG_]("https://help.ubuntu.com/community/Burg") instead of grub-gfxboot.

---

### Post by roshgorg on 2012-05-27
> **kno said:**
> It's hdc because grub is setup on /dev/hdc1 (your 3rd hdd) with Ubuntu

Yes, but I don't find many message.xyz on the net...

Is it possible to create simple images as backgrounf for that ?

---

