---
title: "HOWTO: Kernel Compilation for Newbies"
date: 2005-08-14
forum: Tutorials
---

### Post by tseliot on 2005-08-14
This guide is aimed at the newbies who are willing to learn something about kernel compilation or just who need a new kernel for incompatibility issues (e.g. DMA issues). This is a STEP-BY-STEP guide, so don't be afraid of compiling your first kernel, it's a piece of cake.

I want to thank the user luca_linux, who made a great compilation guide, from which I've taken the commands for my guide and thanks to which I learnt how to compile a kernel. I advise you to check it out: [http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation) 

It takes a while (even an hour) to complete the process described below, so make sure you have enough time to spend.

Make sure you have all the repositories: go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  , find the section &#8220;How to add extra repositories?&#8221; and follow the instructions.

BEFORE YOU START

If you have an Nvidia or ATI graphic card and you are using a proprietary driver (i.e. if you have installed the graphic driver before) please do this, otherwise get straight to step 1:

Open Terminal or Konsole and type these commands:

(if you are using GNOME, the graphic interface that comes with Ubuntu)
```
sudo gedit /etc/X11/xorg.conf
```

Otherwise

(if you are using KDE, the graphic interface that comes with Kubuntu)
```
sudo kate /etc/X11/xorg.conf
```

Scroll down the text until you find this section (this is my configuration):

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"[COLOR=Red]ati[/COLOR]"
	BusID		"PCI:1:5:0"
```

Substitute the word in red with &#8220;vesa&#8221;, make it look like this:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"[COLOR=Blue]vesa[/COLOR]"
	BusID		"PCI:1:5:0"
```

Save and exit. Restart the computer and go to the next step. 

When you have the new kernel working you might want to reinstall the proprietary drivers for your graphic card. Have a look at "Hoary 5.04 Customization Tips & Tricks" section of Ubuntu Forum for the instructions.


1)  Open Terminal or Konsole and type these commands (so as to see what kernel you are using)

```
uname -r
```

[COLOR=Magenta]NOTE: if you want to compile a vanilla kernel from kernel.org have a look at the end of the guide.Otherwise proceed with step 2.[/COLOR]

2) Download the Ubuntu kernel sources:
```
sudo apt-get install linux-source
```

NOTE:
If you want to download the sources of kernel 2.6.11 try this otherwise skip it and go to step 3:
Make sure you have all the repositories: go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  , find the section &#8220;How to add extra repositories?&#8221; and follow the instructions.
Then open either Synaptic or Kynaptic, press the &#8220;search&#8221; button and type &#8220;tree&#8221; (and launch the search)
Look for linux-tree-2.6.11 and select it with your mouse, select &#8220;mark for the installation&#8221;, &#8220;mark&#8221;. Then click on the &#8220;Apply&#8221; button and then select &#8220;apply&#8221; again.
Remember that the name of the file (e.g. linux-source-2.6.11.tar.bz2) will be different from the one in my examples. 
i.e. for the 1st command: &#8220;sudo apt-get install linux-tree-2.6.11&#8221;

Apart from this command you will have to put  &#8220;2.6.11&#8221; instead of &#8220;2.6.10&#8221; every time you see it in this HOWTO.
e.g. for this command &#8220;sudo tar --bzip2 -xvf linux-source-2.6.[COLOR=Red]11[/COLOR].tar.bz2&#8221; (instead of &#8220;sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2&#8221;)

3)Open Terminal or Konsole (if it's not open yet) and type these commands:

```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install gcc-3.4  [COLOR="Red"](this is required only for Breezy users)[/COLOR]
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev
```

```
cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
cd /usr/src/linux
```

NOTE: if the computer says "file exists" when you try type this command "sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux", you have to type "sudo rm /usr/src/linux" (this will remove the old link). Now you wont' have this error and the command "sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux" will work.


```
sudo make oldconfig (so as not to compile the entire kernel from scratch)
```

If it makes you any questions just press Enter (so as to select the recommended answer)

```
sudo make menuconfig
```

4)Now you have to use the keyboard to move the cursor over the function or submenu you want and press Enter to select it.

Select the 4th option: Processor type and features

If you have a multiprocessor system you might want to enable "Symmetric multi-processing support" (SMP): select it with your keyboard and press the spacebar to enable it (a "*" will appear beside it). If you don't have it don't enable it.

Select Processor Family and choose the right one (i386 in my case) depending on the output of the command &#8220;uname -r&#8221; you have used before

Press the right arrow and select exit

If you have more than 900MB RAM then you'll definitely need this, otherwise (or if you are using Ubuntu 64 bit) skip this step:  
Scroll down the text until you find &#8220;High Memory Support&#8221;.
Select it.
You'll have three possible choices:
```
Off
4GB (if you have no more than 4GB RAM)
64GB (if you have more than 4GB RAM)
```
Select one of these functions and press enter.
Press the right arrow and select exit
 
The following operation is required if you want to enable DMA directly in your kernel. You might want to try this if none of the methods found in this forum works for you, Otherwise skip it and go to Step 5.
NOTE: if you have old hardware which doesn't support DMA you won't be able to access this hardware with your new kernel. If this happens go straight to Step 8. 

```
Select Device drivers
```

then

```
Select ATA/ATAPI/MFM/RLL support
```

Scroll down the text until you find (and highlight with the keyboard) &#8220;Enable DMA only for disks&#8221; and disable it by pressing N (now the &#8220;*&#8221; beside it should disappear, this means it is not selected any more)

Press the right arrow and select exit

5)Keep on selecting Exit until it asks you whether you want to save you new configuration or not. Answer yes.

Now you are back to the command line, type:

```
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-[COLOR=Red]custom[/COLOR] kernel_image kernel_headers
```

NOTE: you can put whatever you want instead of &#8220;custom&#8221;

e.g. sudo make-kpkg --initrd &#8211;append-to-version=-alberto kernel_image kernel_headers


The system will ask you this question:

&#8220;By default, I assume you know what you are doing, and I
apologize for being so annoying. Should I abort[Ny]?&#8221;

Answer no by either typing N and then pressing Enter, or just by pressing Enter (as N is the recommended answer)

Well now you'll have to wait at least 45min. The process will use 100% of your CPU so try to leave your computer alone, go have a tea or something else just to keep you away from your computer for a while.

6)After the (long) process type this in the command line (Terminal or Konsole)

```
cd /usr/src
ls
```

You'll see a list of the names of the files in the folder as well as the names of your new kernel image and kernel headers; they should look (approximately)like the following:

	kernel-image-2.6.10-custom_10.00.Custom_i386.deb
	kernel-headers-2.6.10-custom_10.00.Custom_i386.deb

Now install them by typing these commands (change the name of the files according to the ones you have seen after the output of the command &#8220;ls&#8221;):

```
sudo dpkg -i kernel-image-2.6.10-custom_10.00.Custom_i386.deb
```

```
sudo dpkg -i kernel-headers-2.6.10-custom_10.00.Custom_i386.deb
```

REMEMBER NOT TO UNINSTALL your previous kernel (just in case anything goes wrong) (i.e. don't do anything else apart from following the instructions)

7)Ok, now it's time to see if they work.

Restart your computer.

Then if you want to see if DMA is active type (in Terminal or Konsole):

```
sudo hdparm -d /dev/hda (to check if your harddisk has DMA enabled)
sudo hdparm -d /dev/cdrom (to check if your cd-reader has DMA enabled)
```

Don't you worry if it gives you an error as output but the performance of your harddisk and cdreader have improved (try to transfer a file from a CD to your harddisk and see if it the system slows down).

If everything is ok, then Congratulations you have compiled your first kernel successfully!

8 )If anything went wrong (I don't know a reason for which it would) you could switch back to your previous kernel: while your computer is booting press "ESC" repeatedly while your computer is booting until GRUB menu appears and you can choose kernel 2.6.10 again (using your keyboard arrows). Once you enter Ubuntu type these commands in order to uninstall the new kernel (remember to put the name of the kernel you have created)

follow this example and put the name of the kernel you have created instead of &#8220;custom&#8221;

```
sudo dpkg -r kernel-image-2.6.10-custom
sudo dpkg -r kernel-headers-2.6.10-custom
```

(in my case, sudo dpkg -r kernel-image-2.6.10-alberto)

NOTE you DON'T have to type the full name of the file .deb which you created

e.g. put &#8220;kernel-image-2.6.10-custom&#8221; instead of &#8220;kernel-image-2.6.10-custom_10.00.Custom_i386.deb&#8221;

And restart your computer.

Enjoy!
---------------------------------------------------------------------------------------------------------------------------------
[COLOR=Magenta]NOTE: HOWTO compile from a vanilla kernel from kernel.org[/COLOR]

If you want to compile from a vanilla kernel from kernel.org something need to be changed in my guide:

Skip[COLOR=Green] point 2[/COLOR]
You have to download it from [www.kernel.org](www.kernel.org) (try the latest stable kernel source)

When you get to [COLOR=Green]Point 3 [/COLOR]of the guide and you get to the following lines you have to modify them in this way:

cd /home/your_username_folder/directory_where_you_put_the_downloaded_kernel (instead of cd /usr/src) (e.g. "cd /home/alberto/download" in my case)
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2 /usr/src (use the name of the file you downloaded)
sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux (use the name of the file you downloaded)
cd /usr/src/linux

Then you can go on with the instructions of Point 3.

And in [COLOR=Green]point 4[/COLOR] (this is the 1st thing to do at the beginning of point 4):

Get to "File Systems".

Select your filesystem (ext3, reiserfs, etc.) with the cursor.( ext3 is the filesystem used by Ubuntu by default, so if you chose automatic partitioning when you installed Ubuntu Hoary then "ext3" is definitely your filesystem)

Then press the spacebar on the desired filesystem (a "*" will appear beside it). (Make sure there's a "*" beside it instead of a "M". In this way the support for you filesystem will be built directly in the kernel instead of being built as a module and you will not get a "kernel panic")

For example:
select "ext3 journalling filesystem support" and press the spacebar (a "*" will appear beside it).

Press the right arrow and select exit.

Then you can go on with the instructions of Point 4.

The rest of the HOWTO is ok.

NOTE: I've always had Ubuntu complaining about errors with ndiswrapper ONLY during the bootstrap when I used a kernel compiled from a vanilla source. Apart from these error messages the kernel worked flawlessly, perhaps it was only my SDcard reader which was not properly detected (I can't test it as I've never used a SDcard).
---------------------------------------------------------------------------------------------------------------------------------

Alberto

---

### Post by ad1138 on 2005-08-14
Bella guida! Good job! :)

Ciao

---

### Post by tseliot on 2005-08-14
Grazie, spero che sia utile ai nuovi arrivati.

Thanks

---

### Post by johannes on 2005-08-14
Nice guide. Thanks!  :)

---

### Post by rodrigocansian on 2005-08-14
Great guide !!

Thanks a lot !

---

### Post by Dolphin on 2005-08-14
[QUOTE=tseliot](if you are using KDE, the graphic interface that comes with Kubuntu)
sudo kate /etc/X11/xorg.conf

Scroll down the text until you find this section (this is my configuration):

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"[COLOR=Red]ati[/COLOR]"
	BusID		"PCI:1:5:0"

Substitute the word in red with “vesa”, make it look like this:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"vesa"
	BusID		"PCI:1:5:0"

Save and exit. Restart the computer and go to the next step. 

[/QUOTE]

Question regarding this.
My driver is listed as "fglrx".  I'm using ATI's 8.14.13 drivers.  Do I still enter 'vesa' ?  What does that mean?  Will I have to reinstall my ATI drivers after recompiling the kernel?

Thanks.

---

### Post by tseliot on 2005-08-14
[QUOTE=Dolphin]Question regarding this.
My driver is listed as "fglrx".  I'm using ATI's 8.14.13 drivers.  Do I still enter 'vesa' ?  What does that mean?  Will I have to reinstall my ATI drivers after recompiling the kernel?

Thanks.[/QUOTE]

Yes you will have to reinstall the driver after booting with the new kernel, I'll edit the guide and make this clear. 

If you put "vesa" you will use a generic driver (without 3d acceleration). If you don't do that, the modules of ATI drivers (which had been compiled for your previous kernel by ATI driver installer, I suppose) won't work with your new kernel and you won't be able to start and use GNOME or KDE because Xserver won't work. I know it because that's the  way it works with nvidia drivers (I have never installed ATI proprietary drivers though)

---

### Post by tseliot on 2005-08-14
However in your case you can also put "ATI" (ATI generic drivers) which also work on the the notebook from which I have written the guide. It's just a temporary thing until you boot with the new kernel and reinstall your graphic driver again.

---

### Post by Copter on 2005-08-14
d0h! thanks a lot tseliot!

i dont have much time now but i will do it for sure tommorow morning. it looks straight and clear enought for me :D. i will write the results.

copter :]

---

### Post by rodrigocansian on 2005-08-14
Uauu, now my Ubuntu is flying

Simple, and Fast !

Thanks again ;)

---

### Post by Dolphin on 2005-08-15
Is there any noteable benefit in going from 2.6.10 to 2.6.11?
If there's not much to gain then I don't think I'll bother until we see an official ubuntu release of the 8.14.13 ATI drivers.  They were a nightmare to install and I don't wanna try again.

---

### Post by luca_linux on 2005-08-15
[QUOTE=tseliot]However in your case you can also put "ATI" (ATI generic drivers) which also work on the the notebook from which I have written the guide. It's just a temporary thing until you boot with the new kernel and reinstall your graphic driver again.[/QUOTE]
 Or put "radeon" if you have an ATI Radeon card.

---

### Post by tseliot on 2005-08-15
[QUOTE=Dolphin]Is there any noteable benefit in going from 2.6.10 to 2.6.11?
If there's not much to gain then I don't think I'll bother until we see an official ubuntu release of the 8.14.13 ATI drivers.  They were a nightmare to install and I don't wanna try again.[/QUOTE]

If your system works fine as it is there's no need to use 2.6.11. If you just want to learn how to compile you could try my guide.

---

### Post by Copter on 2005-08-15
one question: im compiling 2.6.11 and there is also something like linux-patches with 2.6.11 stuff. should i do anything with it?

copter :]

---

### Post by tseliot on 2005-08-15
[QUOTE=Copter]one question: im compiling 2.6.11 and there is also something like linux-patches with 2.6.11 stuff. should i do anything with it?

copter :][/QUOTE]

If you installed linux kernel tree as described in the guide the patches will be applied automatically when you compile. In a nutshell: no, you don't have to do anything, just follow the instructions.

---

### Post by tseliot on 2005-08-15
Copter, why are you compiling kernel 2.6.11 if it didn't work for you before (when you downloaded it)? Why don't you try to compile kernel 2.6.10 instead? It will work for you now if you enable DMA in the kernel.

---

### Post by Copter on 2005-08-15
[QUOTE=tseliot]If you installed linux kernel tree as described in the guide the patches will be applied automatically when you compile. In a nutshell: no, you don't have to do anything, just follow the instructions.[/QUOTE]
 ok, i get it. i just asked because i had some ati driver problems with fglrx and i thought that those patches could be some help. anyway it works leaving driver "ati" in xorg.conf. ive found thread here how to fix it after custom kernel install.

thnaks

---

### Post by gcblig on 2005-08-15
Ya might want to fix the link to the  other how to -double http:// took me to MS

---

### Post by Copter on 2005-08-15
[QUOTE=tseliot]Copter, why are you compiling kernel 2.6.11 if it didn't work for you before (when you downloaded it)? Why don't you try to compile kernel 2.6.10 instead? It will work for you now if you enable DMA in the kernel.[/QUOTE]
 word.

im an idiot. 2.6.11 compilation error
```

drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
```im learning on my own mistakes... doing 2.6.10

copter :]

---

### Post by tseliot on 2005-08-15
[QUOTE=gcblig]Ya might want to fix the link to the  other how to -double http:// took me to MS[/QUOTE]

Thanks, I hadn't noticed. I have fixed it now

---

### Post by abandoned_hussam on 2005-08-15
tseliot, if I compile my own kernel using tarball from kernel.org, will I be able to later install NVIDIA driver from NVIDIA.com ? If yes, how?

---

### Post by tseliot on 2005-08-15
[QUOTE=hussam]tseliot, if I compile my own kernel using tarball from kernel.org, will I be able to later install NVIDIA driver from NVIDIA.com ? If yes, how?[/QUOTE]

In the same way as you do with any other kernel. There are lots of HOWTOs in this section. However if you want me to guide you through the process you'll have to wait because I have to go now.

Bye bye.

---

### Post by tseliot on 2005-08-15
Ok, I'm back, sorry I didn't mean to be rude, but I was such in a hurry. You can use my HOWTO but it is aimed at Ubuntu Breezy users

[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924) 

For this reason you should skip these lines you will find in my HOWTO:

[COLOR=Red]CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

export CC[/COLOR]

These commands are not needed for any of the kernels in Ubuntu Hoary (the current stable version which you installed).

Just follow the HOWTO and they driver will work fine. It's very easy.

I hope this helps you.

---

### Post by c-m on 2005-08-15
can i just ask, i've noticed that in some of the howtos the mention kernel headers. These seem to only be 65mb so can't be the kernel source. what are they? why do i need them or why should i use these rather than downloading the source, which for me would be linux-source-2.6.10.

Thank you. :-)

---

### Post by tseliot on 2005-08-15
[QUOTE=c-m]can i just ask, i've noticed that in some of the howtos the mention kernel headers. These seem to only be 65mb so can't be the kernel source. what are they? why do i need them or why should i use these rather than downloading the source, which for me would be linux-source-2.6.10.

Thank you. :-)[/QUOTE]

Well, I'm not an expert so I don't know exactly what they are. But I know that every kernel has its headers and they are useful to compile modules, this happens for example when you have to install the drivers for your graphic card or when you try to install Vmware (an emulator which allows you to install Windows and other OS in Linux). The source is not needed if you have the headers and their respective kernel installed.

The source is needed in order to compile a new kernel and, thanks to my HOWTO both the kernel image and headers can be created (just follow the instructions).

I hope this makes things a bit clearer for you.

---

### Post by c-m on 2005-08-15
thanks, i've just never seen them on a distro i've used before. 

I don't understand the making kernels in ubuntu, i'm used to doing "make && make modules_install" then coping the image, .config and system.map to /boot. A quick edit of /boot/grub/menu.lst and you are on your way.

Is the way in the howto a better way for ubuntu systems or just a different way of doing the same thing?

---

### Post by tseliot on 2005-08-15
[QUOTE=c-m]thanks, i've just never seen them on a distro i've used before. 

I don't understand the making kernels in ubuntu, i'm used to doing "make && make modules_install" then coping the image, .config and system.map to /boot. A quick edit of /boot/grub/menu.lst and you are on your way.

Is the way in the howto a better way for ubuntu systems or just a different way of doing the same thing?[/QUOTE]

There's no need to edit menu.lst as Grub is updated automatically when you install the kernel. That's the way it works in Ubuntu.

I have compiled kernels only in Ubuntu and I have never used the command "make && make modules_install". I admit my ignorance ;-) . Perhaps luca_linux or other experienced users are able to answer to your questions.

---

### Post by deaderthanyou on 2005-08-16
I don't know if this was a smart thing to do, but I changed a few things around, and guessed on a few things, and installed 2.6.12.5 from kernel.org.  Everything seems to be running fine (although my splashy bootup screen is gone :( )  has anyone else done this?

---

### Post by tseliot on 2005-08-16
[QUOTE=deaderthanyou]I don't know if this was a smart thing to do, but I changed a few things around, and guessed on a few things, and installed 2.6.12.5 from kernel.org.  Everything seems to be running fine (although my splashy bootup screen is gone :( )  has anyone else done this?[/QUOTE]

It's a good thing to play with your kernel (you can learn lots of things) if you know what you're doing. I've never used splashy but I've read somewhere it needs to be supported by the kernel. Can anyone confirm this?

---

### Post by Copter on 2005-08-16
hi!

got my new kernel (2.6.10). i did everything as you said. when i run my system i get this when hal is being loaded```

[W] hald.d:302 : your kernel does not support capabilities; some features will not be aviable
```everything works fine so i dont care much about it (now).

when i try to set dma on my dvd i get exacly the same thing as before.```

copter@xidge:~$ hdparm -d1 /dev/dvd

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma    =  0 (off)
```i have no idea what to do now to record and use my dvd. ive read all threads on this forum and did all the tricks people posted. nothing seems to work on my computer.

copter :]

---

### Post by tseliot on 2005-08-16
> **Copter]hi!

got my new kernel (2.6.10). i did everything as you said. when i run my system i get this when hal is being loaded```

[W] hald.d:302 : your kernel does not support capabilities said:**
> 


1)Have you tried tranferring some big files from a CD to your harddisk, have you noticed slowdowns? (if not try it)

2) If you noticed slowdowns you can download the latest kernel (2.6.12-4) (from kernel.org) (which is more compatible than 2.6.11 and 2.6.10) and compile it from that source. 

be sure you do this: "sudo rm /usr/src/linux", then you can follow the HOWTO again.

---

### Post by luca_linux on 2005-08-16
**sudo** hdparm...

---

### Post by Copter on 2005-08-16
ok. i will try newer kernel.

ofc sudo hdparm :). unfortunatly it doesnt change anything here.

about speed```

copter@xidge:~$ sudo hdparm -Tt /dev/dvd

/dev/dvd:
 Timing cached reads:   1112 MB in  2.01 seconds = 554.42 MB/sec
 Timing buffered disk reads:    6 MB in  3.38 seconds =   1.77 MB/sec
```the same as before

copter :]

---

### Post by tseliot on 2005-08-16
[QUOTE=Copter]ok. i will try newer kernel.

ofc sudo hdparm :). unfortunatly it doesnt change anything here.

about speed```

copter@xidge:~$ sudo hdparm -Tt /dev/dvd

/dev/dvd:
 Timing cached reads:   1112 MB in  2.01 seconds = 554.42 MB/sec
 Timing buffered disk reads:    6 MB in  3.38 seconds =   1.77 MB/sec
```the same as before

copter :][/QUOTE]

Ok try kernel 2.6.12-4 then.

---

### Post by Copter on 2005-08-16
[QUOTE=tseliot]Ok try kernel 2.6.12-4 then.[/QUOTE]btw. when i was previously setting the architecture i have selected "PIV / Celeron(based on PIV)..." because i have Celeron 2.6GHz (478 pins) based od PIV. generated files looked like that```

kernel-headers-2.6.10-ctr01_10.00.Custom_i386.deb
kernel-image-2.6.10-ctr01_10.00.Custom_i386.deb
```shouldnt they end with i686? also directory usr/src/kernel-headers-2.6.10-ctr01/arch/**i386** was created. is that ok?

(sorry for being such a horrible pain in the ass...)

EDIT: ive found that my architecture is defined _in_ i386 files, so probably everything is ok.

copter :]

---

### Post by tseliot on 2005-08-16
[QUOTE=Copter]btw. when i was previously setting the architecture i have selected "PIV / Celeron(based on PIV)..." because i have Celeron 2.6GHz (478 pins) based od PIV. generated files looked like that```

kernel-headers-2.6.10-ctr01_10.00.Custom_i386.deb
kernel-image-2.6.10-ctr01_10.00.Custom_i386.deb
```shouldnt they end with i686? also directory usr/src/kernel-headers-2.6.10-ctr01/arch/**i386** was created. is that ok?

(sorry for being such a horrible pain in the ass...)

EDIT: ive found that my architecture is defined _in_ i386 files, so probably everything is ok.

copter :][/QUOTE]
I think everything's ok. i386.deb is the extension for 32bit systems. In 64bit systems it would be amd64.deb. Don't you worry, this is the right place to learn (and to ask) something.

---

### Post by cutOff on 2005-08-16
Great and useful howto. Thanks a lot tseliot.

---

### Post by tseliot on 2005-08-16
[QUOTE=cutOff]Great and useful howto. Thanks a lot tseliot.[/QUOTE]
De nada.. Es que esta comunidad es como una grande familia ;-)

---

### Post by Copter on 2005-08-16
ive got the newest stable kernel aviable (released yesterday). here is what ive got also:

- multiple errors during boot```

Aug 16 16:08:12 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
Aug 16 16:08:12 localhost kernel: device-mapper: dm-linear: Device lookup failed
Aug 16 16:08:12 localhost kernel: device-mapper: error adding target to table
```
- some errors with ALSA (i dont know in where the boot log is. cant recall them)
- cant mount ntfs partitions
- and ofc ::```

copter@xidge:~$ sudo hdparm -d 1 /dev/cdrom
Password:

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
copter@xidge:~$ sudo hdparm -d 1 /dev/dvd

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
copter@xidge:~$ sudo hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

copter@xidge:~$ cat /etc/hdparm.conf

# bla bla bla. some commented stuff

/dev/hda {
        dma = on
}
```im really sick and tired of this

this is my second month of linux usage. i did not touch Windows since then. i really really like this OS but there are 2 thing are forceing me to go back to Win

1) < 2mb cd/dvd to hdd transfer rate (i did not pay 100$ for dvd-ram to have this kind of crap). im trying to fix this doing every trick i can find

2) 150 fps at fglxgears with mesa drivers and permanent system hang / freeze with any other drivers using any app that uses gl for 3D. ive read loads of howto's, texts and other info about this. nothing helps.

copter :]

---

### Post by tseliot on 2005-08-16
Dear Copter I understand your frustration. I solved my problems (well, before my motherboard decided to pass away) by installing a Breezy kernel, then compiling a new one (from Breezy kernel tree sources) by using sudo make oldconfig (so as to use Breezy kernel's settings) and tweaking the kernel with menuconfig (only for DMA). However Breezy kernel could be buggy (well, not that buggy).

I did this because Breezy sources have some useful patches which can solve lots of problems (I also had the errors about the device mapper before installing a Breezy kernel).

If you want to try this way you should be aware that the driver of your graphic card will not compile the modules in the traditional way. You will have to follow these steps before launching the installer:

Install Gcc 3.4 in synaptic

Then, in the command line, before launching the installer of the drivers, type:

[COLOR=Red]CC=gcc-3.4 (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

export CC[/COLOR]

Only in this way they will work.

I'm sorry but I can't help with ATI's proprietary driver as I've never tried them. My desktop computer is broken (I hope Compaq is fixing it), my laptop (with an ATI card) has a broken cdreader and a crazy battery. I can't risk to screw it up (I need it for my thesis) so I prefer not to try to install your drivers.

Keep in mind that my computer was highly Linux unfriendly and I had to learn how to make it work properly under Linux. For this reasons I've decided to help newbies because I know how hard it can be with some hardware (on the other hand Ubuntu worked out of the box on my laptop).

A little patience and we'll make things work. ;-)

---

### Post by Steve1961 on 2005-08-16
Great how to.  I've always wondered how to do this

---

### Post by Copter on 2005-08-17
ok, i did it. after all i must admit that it was only my fault. not linux, not ubuntu.

hour ago, before another kernel compilation, i decided to try another thing. on [this](http://www.ubuntuforums.org/showthread.php?t=19519&page=1&pp=10) thread ive found that maybe i need to add my motherboard chipset driver to /etc/modules (thanks goes to **kleeman**). i thought that i was only about via chips...

what i did?```

sudo /etc/modules
```and added there as first thing to load```

atiixp
```thats all. now it works on 2.6.10, 2.6.11 and 2.6.12 kernels. even on Hoary 5.04 default one.

thanks all people here, especially **tseliot** that did not let me down even once. your howto did not solve my problem exacly but it showed me how to compile kernel in general and forced me to read loads of documents about kernel and general linux tweaking / configuration. you are the man! thanks a lot again!!

copter :]

-----------------------------------------------------------------------------------------------------------------------
keywords that can help other Ubuntu / linux users to find this thread and post and solve similar problems on similar mashines

linux problem error hdparm dma dvd cdrom kernel compilation modules
asus pundit-r pundit atiixp chipset motherboard ati ixp RS300 IXP200 P4R8L

---

### Post by tseliot on 2005-08-17
I'm very happy you've solved your problem. And I'm even happier you've learnt lots of things   :)

---

### Post by xodeus on 2005-08-17
[QUOTE=tseliot]
2)sudo apt-get install linux-tree (this will download kernel sources and patches for kernel 2.6.10)

NOTE:
If you want to download the sources of kernel 2.6.11 try this otherwise skip it and go to step 3:
Make sure you have all the repositories: go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  , find the section “How to add extra repositories?” and follow the instructions.
Then open either Synaptic or Kynaptic, press the “search” button and type “tree” (and launch the search)
Look for linux-tree-2.6.11 and select it with your mouse, select “mark for the installation”, “mark”. Then click on the “Apply” button and then select “apply” again.
Remember that the name of the file (e.g. linux-source-2.6.11.tar.bz2) will be different from the one in my examples. 
i.e. for the 1st command: “sudo apt-get install linux-tree-2.6.11”

Apart from this command you will have to put  “2.6.11” instead of “2.6.10” every time you see it in this HOWTO.
e.g. for this command “sudo tar --bzip2 -xvf linux-source-2.6.[COLOR=Red]11[/COLOR].tar.bz2” (instead of “sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2”)
[/QUOTE]
Something is wrong with my installation.
When trying to install the kernel tree nothing happens in /usr/src there's nothing else than "rpm" folder. Why? Please help.

---

### Post by tseliot on 2005-08-17
Have you set all the repositories? if not go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  and follow the instructions,

By the way can you post the error (or whatever the output) you got after installing kernel tree?

---

### Post by Skatox on 2005-08-18
Thanks for the autor of this guide. I was planning to compile my first kernel the same day this post wad posted, and help me a lot. 

For the people who have problems with splashy, is because it must run linux with 1024x768, and when you install the custom kernel, in the grub, he doesn't have the vga=792 option so edit boot/grub/grub.conf file and put vga=792 and the end of the kernel line.



> 
This is mi example:

root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-custom root=/dev/hda5 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.10-custom
savedefault
boot

---

### Post by tseliot on 2005-08-18
[QUOTE=Skatox]Thanks for the autor of this guide. I was planning to compile my first kernel the same day this post wad posted, and help me a lot. 

For the people who have problems with splashy, is because it must run linux with 1024x768, and when you install the custom kernel, in the grub, he doesn't have the vga=792 option so edit boot/grub/grub.conf file and put vga=792 and the end of the kernel line.[/QUOTE]

Thanks for the information.

Is there any other requirement for splashy, I mean something to be enabled during kernel compilation in order to make it work?

---

### Post by Cyberkef on 2005-08-18
Great newbie howto :)

I followed your howto to the letter.

Unfortunately I get an error on number 6...

[QUOTE=tseliot]...

sudo dpkg -i kernel-image-2.6.10-custom_10.00.Custom_i386.deb
sudo dpkg -i kernel-headers-2.6.10-custom_10.00.Custom_i386.deb

...[/QUOTE]

This is what i get (sorry, some words are in dutch, but the important errors are in English, i hope you understand it :))

> cyberkef@CyberTrax2000:/usr/src$ sudo dpkg -i kernel-image-2.6.10-cyberia_10.00.Custom_i386.deb
Password:
Selecteren van voorheen niet geselecteerd pakket kernel-image-2.6.10-cyberia.
(Database inlezen ... 70192 bestanden en mappen geïnstalleerd.)
Uitpakken van kernel-image-2.6.10-cyberia (uit kernel-image-2.6.10-cyberia_10.00.Custom_i386.deb) ...
Instellen van kernel-image-2.6.10-cyberia (10.00.Custom) ...
[B]/usr/sbin/mkinitrd: device /dev/hdc6 is not a block device
Failed to create initrd image.[/B]
dpkg: fout bij afhandelen van kernel-image-2.6.10-cyberia (--install):
 subproces post-installation script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 kernel-image-2.6.10-cyberia

I think it has something to do with the fact i switched some HDDs last month, and /dev/hdc6 is now /dev/hda6 and one variable needs to be updated. But I have no CLUE where & how to change that (i'm a newb :p), can someone help me out here? :)

THX in advance guys :)

---

### Post by tseliot on 2005-08-18
[QUOTE=Cyberkef]Great newbie howto :)

I followed your howto to the letter.

Unfortunately I get an error on number 6...



This is what i get (sorry, some words are in dutch, but the important errors are in English, i hope you understand it :))



I think it has something to do with the fact i switched some HDDs last month, and /dev/hdc6 is now /dev/hda6 and one variable needs to be updated. But I have no CLUE where & how to change that (i'm a newb :p), can someone help me out here? :)

THX in advance guys :)[/QUOTE]

Check your /etc/fstab (and post it) in this way:
Open Terminal or Konsole and type in the command line:

sudo gedit /etc/fstab (or "sudo kate /etc/fstab" if you use KDE)

Make sure no "hdc6" is in the file. If you find it put "hda6" instead of it.

Then do (in the command line)
sudo apt-get update

And try to install the kernel again.

---

### Post by Cyberkef on 2005-08-18
[QUOTE=tseliot]Check your /etc/fstab (and post it) in this way:
Open Terminal or Konsole and type in the command line:

sudo gedit /etc/fstab (or "sudo kate /etc/fstab" if you use KDE)

Make sure no "hdc6" is in the file. If you find it put "hda6" instead of it.

Then do (in the command line)
sudo apt-get update

And try to install the kernel again.[/QUOTE]
Thank you very much!

*edit* Current Uptime:	00:04:38 running Linux 2.6.10-cyberia */edit*

Woohoo!

---

### Post by tseliot on 2005-08-18
You're welcome  :)

---

### Post by Rob2687 on 2005-08-21
Where do you get the linux-tree for 2.6.12?

---

### Post by tseliot on 2005-08-21
[QUOTE=Rob2687]Where do you get the linux-tree for 2.6.12?[/QUOTE]
There's no kernel 2.6.12 (and therefore nor its "tree") in Ubuntu Hoary but there are 2 ways you can get kernel sources you're looking for:

1) [www.kernel.org](www.kernel.org)  at which you can find vanilla kernel sources (without any patch). If you want to use this kernel you might want to look at the NOTE I'm going to add tonight to this HOWTO.

2) Ubuntu Breezy repositories, but it kernels are experimental so they can be buggy sometimes. But on the other hand you can find the kernel "tree" 2.6.12 in there (with all the patches put by Ubuntu developers). Be careful.

---

### Post by tseliot on 2005-08-21
Ok, now my guide has also a mini guide about compiling from a kernel source downloaded from kernel.org. I hope you like it.

The next thing to add is how to compile from Breezy sources although I don't recommend it (even if it worked for me).

---

### Post by liquidfire on 2005-08-22
I'm having some problems updating the kernell whenever i type sudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux
it says "file exists" :? how to solve, how to solve :(?

---

### Post by tseliot on 2005-08-22
[QUOTE=liquidfire]I'm having some problems updating the kernell whenever i type sudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux
it says "file exists" :? how to solve, how to solve :(?[/QUOTE]
This means the link "linux" exists. Perhaps you made it before (for another kernel compilation).

The solution:
Type

sudo rm /usr/src/linux (this will remove the old link)

Then repeat your command:

sudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux

---

### Post by liquidfire on 2005-08-22
[QUOTE=tseliot]This means the link "linux" exists. Perhaps you made it before (for another kernel compilation).

The solution:
Type

sudo rm /usr/src/linux (this will remove the old link)

Then repeat your command:

sudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux[/QUOTE]
I'm having some new problems now (won't they stop ;)) 
When booting to the new kernel it won't load the usb drivers(I think) and my keyboard and mouse seems to stop working  ](*,) So now I still can't enjoy the new kernel :(

---

### Post by tseliot on 2005-08-22
> **liquidfire]I'm having some new problems now (won't they stop  said:**
> (*,) So now I still can't enjoy the new kernel :(
Ok try this then:

1) Install kernel 2.6.11 (choose your architecture:i386, etc.) in Synaptic or Kynaptic (I refer to the kernel itself and not to the sources, which you have probably installed) (put the word "linux" in the search field and you will have a list of all kernels available).

the kernel is called something like "linux-image-2.6.11-i386" (according to your architecture)

2) Restart your computer (the system will boot with the new kernel) and make sure your kernel is 2.6.11:

Open Terminal or Konsole and type "uname -r" (you'll see the name of the kernel you are using)

Make sure you don't have any problems with usb drivers using this kernel.

3)If everything's ok, follow my guide again (do everything as you did before).  

In this way your new compiled kernel will have all the settings of Ubuntu kernel 2.6.11 (thanks to the command "sudo make oldconfig" which has been included in the guide) ( + the details you will set by following the guide) and you should not have any problem with usb drivers.

Tell me if it works

---

### Post by liquidfire on 2005-08-22
[QUOTE=tseliot]Ok try this then:

1) Install kernel 2.6.11 (choose your architecture:i386, etc.) in Synaptic or Kynaptic (I refer to the kernel itself and not to the sources, which you have probably installed) (put the word "linux" in the search field and you will have a list of all kernels available).

the kernel is called something like "linux-image-2.6.11-i386" (according to your architecture)

2) Restart your computer (the system will boot with the new kernel) and make sure your kernel is 2.6.11:

Open Terminal or Konsole and type "uname -r" (you'll see the name of the kernel you are using)

Make sure you don't have any problems with usb drivers using this kernel.

3)If everything's ok, follow my guide again (do everything as you did before).  

In this way your new compiled kernel will have all the settings of Ubuntu kernel 2.6.11 (thanks to the command "sudo make oldconfig" which has been included in the guide) ( + the details you will set by following the guide) and you should not have any problem with usb drivers.

Tell me if it works[/QUOTE]

I need to install the kernel image and kernel headers right ?

---

### Post by tseliot on 2005-08-22
[QUOTE=liquidfire]I need to install the kernel image and kernel headers right ?[/QUOTE]
It won't hurt you  :-P . I think the kernel image is enough though.

---

### Post by c-m on 2005-08-22
[QUOTE=tseliot]It won't hurt you  :-P . I think the kernel image is enough though.[/QUOTE]
 Not a single kernel i have compiled in Ubuntu works. All i get after selecting it in grub is a black screen.

Does ubutu do things differently to other distros, since i've never had a problem with kernels in either gentoo, yoper or vidalinux?

---

### Post by tseliot on 2005-08-22
[QUOTE=c-m]Not a single kernel i have compiled in Ubuntu works. All i get after selecting it in grub is a black screen.

Does ubutu do things differently to other distros, since i've never had a problem with kernels in either gentoo, yoper or vidalinux?[/QUOTE]

I have never tried the distros you have mentioned. By the way have you ever tried to install an Ubuntu kernel (e.g. 2.6.11) in Synaptic or Kynaptic? If yes, did it work or did you get the same problem after grub?

---

### Post by tseliot on 2005-08-22
[QUOTE=c-m]Not a single kernel i have compiled in Ubuntu works. All i get after selecting it in grub is a black screen.

Does ubutu do things differently to other distros, since i've never had a problem with kernels in either gentoo, yoper or vidalinux?[/QUOTE]
Another thing:

1) Have you followed my guide or did you refer to kernel compilation in general in Ubuntu?

2) Can you post both your "/etc/fstab" and your "/boot/grub/menu.lst", please?

---

### Post by c-m on 2005-08-22
[QUOTE=tseliot]Another thing:

1) Have you followed my guide or did you refer to kernel compilation in general in Ubuntu?

2) Can you post both your "/etc/fstab" and your "/boot/grub/menu.lst", please?[/QUOTE]
 ah got it to work your way with the initrd etc... just wouldn't work my way. no biggy. cheers for the howto.

---

### Post by tseliot on 2005-08-22
[QUOTE=c-m]ah got it to work your way with the initrd etc... just wouldn't work my way. no biggy. cheers for the howto.[/QUOTE]
Thanks. I really don't know why kernel compilation only works in this way. Perhaps it's just Ubuntu. I really don't know.

---

### Post by Varox on 2005-08-24
Does anybody knows where i can get the 2.6.11-1-k7 restricted modules?

---

### Post by tseliot on 2005-08-24
[QUOTE=Varox]Does anybody knows where i can get the 2.6.11-1-k7 restricted modules?[/QUOTE]
I guess there aren't any. You have to compile it yourself.

---

### Post by osxus3r on 2005-09-03
it is a great guide indeed, I followed the instructions, everything went ok, but after I choose to load 'Linux' in yaboot it does load the initrd.img ok and then ther is a welcome screen, saying 'welcome to Linux, 2.6.13-custom' and nothing else happens! any ideas?? I would really love to upgrade my kernel because it's been suggested that this is the way to get sound card to work.

---

### Post by tseliot on 2005-09-04
[QUOTE=osxus3r]it is a great guide indeed, I followed the instructions, everything went ok, but after I choose to load 'Linux' in yaboot it does load the initrd.img ok and then ther is a welcome screen, saying 'welcome to Linux, 2.6.13-custom' and nothing else happens! any ideas?? I would really love to upgrade my kernel because it's been suggested that this is the way to get sound card to work.[/QUOTE]
I really don't know yaboot (never had a powerpc).

The only thing I can ask you is: did you read the 2nd part of my guide (at the end)?
It begins with "NOTE: HOWTO compile from a vanilla kernel from kernel.org"

---

### Post by osxus3r on 2005-09-04
[QUOTE=tseliot]I really don't know yaboot (never had a powerpc).

The only thing I can ask you is: did you read the 2nd part of my guide (at the end)?
It begins with "NOTE: HOWTO compile from a vanilla kernel from kernel.org"[/QUOTE]

thanks for reply tseliot, yes I did read that part, maybe it just because I have a mac
 :|

---

### Post by odin on 2005-09-05
Really nice howto but I need to select an option in the library routines menu so I have to compile the kernel from www.kernel.org.That's not a problem because I have done it succesfully several times.

The problem is that I need to build a module outside the kernel and for that I need to select crc functions when I do the "make menuconfig".The thing is that I cannot select one of them(the one in the middle which says "CRC32 options" in kernel 2.6.8).

I'm sure that one is the one I need since I have built the module I need with no errors but a warning saying that the module doesnt have a CRC.I just cant select it neither as a built-in option or as a module.I guess that option depends on others so I'm able to select it but I've tried many conbinations and nothing.

Could anyone help me or guide to find the solution?

What I'm trying to build is seppl-0.4 that you can find in [http://0pointer.de/lennart/projects/seppl](http://0pointer.de/lennart/projects/seppl)

Thank's in advance

---

### Post by mlomker on 2005-09-05
[QUOTE=tseliot]Thanks. I really don't know why kernel compilation only works in this way. Perhaps it's just Ubuntu. I really don't know.[/QUOTE]

You need to use initrd if you do not build your disk controller driver and the file system driver (ext3) into the kernel (cannot be a loadable module).  I'm booting 2.6.13 just fine without initrd.  I just downloaded the kernel source and applied the ck patch set.

---

### Post by osxus3r on 2005-09-06
I am not sure how did you do that because I've tried to build like every possibly fs driver into the kernel not as a module and it still asks for initrd.img

---

### Post by odin on 2005-09-06
[QUOTE=osxus3r]I am not sure how did you do that because I've tried to build like every possibly fs driver into the kernel not as a module and it still asks for initrd.img[/QUOTE]


try to do this:

cd /boot
mkinitrd -o /boot/initrd.img-kernel_version kernel_version

for example,if you are compiling 2.6.8 then would be something like:
mkinitrd -o /boot/initrd.img-2.6.8 2.6.8 

after that just add it in /boot/grub/menu.lst so at the end it looks like this:

title           Debian GNU/Linux, kernel 2.6.8
root            (hd0,0) #this depends on where you have uinstalled it
kernel          /boot/vmlinuz-2.6.8 root=/dev/hda1 ro
initrd          /boot/initrd.img-2.6.8
savedefault
boot
 

You probably have to do this before everything:


apt-get install initrd-tools 


good luck

---

### Post by N'Jal on 2005-09-06
fantastic guide this is the first (sucussesful) kernel i have ever built.

---

### Post by gord on 2005-09-06
i had problems with saa7134 failing during the compalation of 2.6.11 and it seems to be a fairly active bug(?).
```

drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'

```

typing;
sudo gedit /usr/src/linux/.config 

and then disabling the lines that had 'saa7134' in them (change the m to a n) seems to work, allthough if someone wants to come back here and tell me that, that just so happens to be something that you need, please do so ;)

---

### Post by osxus3r on 2005-09-06
[QUOTE=odin]try to do this:

cd /boot
mkinitrd -o /boot/initrd.img-kernel_version kernel_version

for example,if you are compiling 2.6.8 then would be something like:
mkinitrd -o /boot/initrd.img-2.6.8 2.6.8 

after that just add it in /boot/grub/menu.lst so at the end it looks like this:

title           Debian GNU/Linux, kernel 2.6.8
root            (hd0,0) #this depends on where you have uinstalled it
kernel          /boot/vmlinuz-2.6.8 root=/dev/hda1 ro
initrd          /boot/initrd.img-2.6.8
savedefault
boot
 

You probably have to do this before everything:


apt-get install initrd-tools 


good luck[/QUOTE]
 thanks for help odin

I managed to create initrd.img, it loads fine (the image) but then nothing happens! :) it won't continue booting at all after displaying 'welcome to linux-2.6.13-custom'

---

### Post by odin on 2005-09-07
[QUOTE=osxus3r]thanks for help odin

I managed to create initrd.img, it loads fine (the image) but then nothing happens! :) it won't continue booting at all after displaying 'welcome to linux-2.6.13-custom'[/QUOTE]


Ok.I'm sorry,I just saw your previous posts and if we are talking about a Mac I have no idea.I havent even seen many of those  :roll:

---

### Post by GoA on 2005-09-07
I'm using breezy and didnät manage to get kernel working. Allways get some error, few times not even loading kernel, few times filesystem, one time something else and latest time graphics just went into a mess and no error notification. Hope someone makes a new easier how to for breezy and kernel 2.6.13

---

### Post by tseliot on 2005-09-07
[QUOTE=GoA]I'm using breezy and didnät manage to get kernel working. Allways get some error, few times not even loading kernel, few times filesystem, one time something else and latest time graphics just went into a mess and no error notification. Hope someone makes a new easier how to for breezy and kernel 2.6.13[/QUOTE]
kernel 2.6.13 works ok in Hoary. I'll write a new guide when I switch to Breezy.

---

### Post by GoA on 2005-09-07
Thanks. :) If it would be possible, could you also tell which components are essential for ubuntu. Such as; ram-disk, initrd module, ext3 as part of kernel and so on. It's nice that there are lot's of users here who are willing to help us noobs. :)

---

### Post by MichaelM on 2005-09-07
I just compiled my kernel, and now neither my ethernet card nor my wireless card shows up in Networking.  I tried lspci and both were there.  How do I enable them?

---

### Post by tseliot on 2005-09-07
[QUOTE=MichaelM]I just compiled my kernel, and now neither my ethernet card nor my wireless card shows up in Networking.  I tried lspci and both were there.  How do I enable them?[/QUOTE]
Did you follow EVERY step of my guide?
If not step back to your previous working kernel and repeat the process as described in my guide.

---

### Post by MichaelM on 2005-09-07
[QUOTE=tseliot]Did you follow EVERY step of my guide?
If not step back to your previous working kernel and repeat the process as described in my guide.[/QUOTE]
Well, I'm not certain.  I followed steps 1 to 3 exactly, and then I had to work offline, and the guide wasn't cached.  luca_linux's kernel compilation howto was available offline, so that's what I followed for the last few steps.

---

### Post by tseliot on 2005-09-07
[QUOTE=MichaelM]Well, I'm not certain.  I followed steps 1 to 3 exactly, and then I had to work offline, and the guide wasn't cached.  luca_linux's kernel compilation howto was available offline, so that's what I followed for the last few steps.[/QUOTE]
Print the guide (if you need it offline) and follow EVERY step of this guide. Then if you have any problem I can help you.

---

### Post by MichaelM on 2005-09-07
Ok, I'll try it again tomorrow.  Thanks!

---

### Post by MichaelM on 2005-09-08
Well, I just tried it again, and the same thing happened.  It seemed to use the .config that I had made in my last attempt, which may be a problem.  How do I reset the config to the defaults?  Or am I barking up the wrong tree?   :?

---

### Post by mog27 on 2005-09-08
tseliot, can you provide some insight on this kernel issue I can't figure out:

[http://www.ubuntuforums.org/showthread.php?t=62800](http://www.ubuntuforums.org/showthread.php?t=62800)

Thanks.

---

### Post by myha on 2005-09-09
Hi!

Well I'm having a little problem because of my own stupidity... I forgot to change my graphic driver from ati to vesa and now i gat a blank screen on boot...
Is there any way to simply change that or I have to recompile again? It lasted almost 2 hours on my laptop....   :???: 

thanks, Miha

---

### Post by tseliot on 2005-09-09
[QUOTE=MichaelM]Well, I just tried it again, and the same thing happened.  It seemed to use the .config that I had made in my last attempt, which may be a problem.  How do I reset the config to the defaults?  Or am I barking up the wrong tree?   :?[/QUOTE]
boot using kernel 2.6.10 (the one with which Ubuntu comes by default) and repeat the process. Remember to give your new kernel a different name from the ones you did before

---

### Post by tseliot on 2005-09-09
[QUOTE=mog27]tseliot, can you provide some insight on this kernel issue I can't figure out:

[http://www.ubuntuforums.org/showthread.php?t=62800](http://www.ubuntuforums.org/showthread.php?t=62800)

Thanks.[/QUOTE]
Check your thread

---

### Post by tseliot on 2005-09-09
[QUOTE=myha]Hi!

Well I'm having a little problem because of my own stupidity... I forgot to change my graphic driver from ati to vesa and now i gat a blank screen on boot...
Is there any way to simply change that or I have to recompile again? It lasted almost 2 hours on my laptop....   :???: 

thanks, Miha[/QUOTE]
1) I suppose it boots to the command line. If it does:
sudo nano /etc/X11/xorg.conf

set ati to vesa

CTRL+O to overwrite the file
CTRL+X to exit

startx or reboot

2) if instead it doesn't boot at all:
as soon as you turn on your computer after the bios you will see a the word "GRUB" etc. press ESC until it gets you to Grub boot menu and select your previous kernel from the list and press enter.
After you boot in Ubuntu set xorg to vesa. 
and Reboot


In the end you have to install ati drivers again for your new kernel

---

### Post by myha on 2005-09-09
Hi!

Well i decided to compile again... I did everything exactly acc to this how-to and it works great... Except for 1 thing.... When linux boots I dont see anything, I have black screen untill login screen appears.... I cant use virtual consoles either because it shows nothing....   :?  Black screen....

edit: Ok I got it working now, the problem was I edited grub config and added vga=792 and now I removed it and its ok but with smaller resolution... Why 792 isnt working? It works on previous kernel image but not on new one...

Thanks, Miha

---

### Post by tseliot on 2005-09-09
[QUOTE=myha]Hi!

Well i decided to compile again... I did everything exactly acc to this how-to and it works great... Except for 1 thing.... When linux boots I dont see anything, I have black screen untill login screen appears.... I cant use virtual consoles either because it shows nothing....   :?  Black screen....

edit: Ok I got it working now, the problem was I edited grub config and added vga=792 and now I removed it and its ok but with smaller resolution... Why 792 isnt working? It works on previous kernel image but not on new one...

Thanks, Miha[/QUOTE]
A kernel bug? I really don't know.

---

### Post by TakisX on 2005-09-09
I compiled the new 2.6.13 kernel with your How To (very good)

Where i can find more info in order to remove elements from kernel to make it beter ?

When a new kernel is out is there a reason to get it if your hardware works ?

I must compile the nvidia drivers again now ?

---

### Post by tseliot on 2005-09-09
[QUOTE=TakisX]I compiled the new 2.6.13 kernel with your How To (very good)

Where i can find more info in order to remove elements from kernel to make it beter ?

When a new kernel is out is there a reason to get it if your hardware works ?

I must compile the nvidia drivers again now ?[/QUOTE]

1) Google? Really I'm looking for a good (free) guide too

2) No, unless you want to test the new kernel release

3) definitely yes

---

### Post by WiLLiE on 2005-09-10
[QUOTE=myha]Hi!

Well i decided to compile again... I did everything exactly acc to this how-to and it works great... Except for 1 thing.... When linux boots I dont see anything, I have black screen untill login screen appears.... I cant use virtual consoles either because it shows nothing....   :?  Black screen....

edit: Ok I got it working now, the problem was I edited grub config and added vga=792 and now I removed it and its ok but with smaller resolution... Why 792 isnt working? It works on previous kernel image but not on new one...

Thanks, Miha[/QUOTE]
 Yeah, with vga=792 all I get is a black screen at boot. (It seemes that it is continuing as usual b'coz I can hear the drive work. And ctrl+alt+del works.)

If I remove vga=792 I get the normal output, except it's like 640x480. (And Splashy doesn't work.)

How to fix this?

---

### Post by tseliot on 2005-09-11
[QUOTE=WiLLiE]Yeah, with vga=792 all I get is a black screen at boot. (It seemes that it is continuing as usual b'coz I can hear the drive work. And ctrl+alt+del works.)

If I remove vga=792 I get the normal output, except it's like 640x480. (And Splashy doesn't work.)

How to fix this?[/QUOTE]
I admit I've never used splash but I think you could try different resolutions:

put vga=791 for 1024*768 or vga=794 for 1280*1024 to your grub menu.lst

Tell me if it works

---

### Post by greyhound4334 on 2005-09-11
TSeliot,

Thanks for the great guide.  I have 2 questions for you.  I have an AMD64 3200+ processor, but I'm currently running 32-bit ubuntu.  So,

1. You wrote: > If you have more than 900MB RAM then you'll definitely need this, otherwise (or if you are using Ubuntu 64 bit) skip this step:
Scroll down the text until you find “High Memory Support”.
Select it.
You'll have three possible choices:
Off
4GB (if you have no more than 4GB RAM)
64GB (if you have more than 4GB RAM)
Select one of these functions and press enter.
Press the right arrow and select exit 
While running menuconfig and looking at the built-in help, it said "if you have a 32-bit processor AND more than 1GB RAM...".  So I'm a little unsure of which choice to make.  Should I be considered 32-bit (my OS) or 64-bit (my processor)?

2. On a related note, I chose AMD64 as my processor type.  I assume choice only affects kernel optimization, but I was slightly worried/confused over whether that might conflict with the rest of the distro being 32-bit.  Just wanted to double check that choosing "AMD64" was the right move there.

Thanks in advance!

---

### Post by tseliot on 2005-09-12
[QUOTE=greyhound4334]TSeliot,

Thanks for the great guide.  I have 2 questions for you.  I have an AMD64 3200+ processor, but I'm currently running 32-bit ubuntu.  So,

1. You wrote:  
While running menuconfig and looking at the built-in help, it said "if you have a 32-bit processor AND more than 1GB RAM...".  So I'm a little unsure of which choice to make.  Should I be considered 32-bit (my OS) or 64-bit (my processor)?

2. On a related note, I chose AMD64 as my processor type.  I assume choice only affects kernel optimization, but I was slightly worried/confused over whether that might conflict with the rest of the distro being 32-bit.  Just wanted to double check that choosing "AMD64" was the right move there.

Thanks in advance![/QUOTE]
1) You use Ubuntu 32bit so you have to consider it as such (even if your processor is a 64bit one.

2) If you use an AMD64 in a 32bit then you should chose "k7" processor type.

I should add these explanation to the guide. Thanks for making me notice the flaws.

---

### Post by John.Michael.Kane on 2005-09-14
This comand sudo tar --bzip2 -xvf linux-2.6.13.1.tar.bz2 /usr/src gives this error
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

This is the Kernel used linux-2.6.13.1.tar.bz2 and it is saved to the desktop.

Edit: had to use [http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)

---

### Post by tseliot on 2005-09-14
[QUOTE=SD-Plissken]This comand sudo tar --bzip2 -xvf linux-2.6.13.1.tar.bz2 /usr/src gives this error
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

This is the Kernel used linux-2.6.13.1.tar.bz2 and it is saved to the desktop.

Edit: had to use [http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)[/QUOTE]
I've used the same command as the other guide (see point 3 in my guide).

did you launch the command after doing cd /usr/src ?

---

### Post by John.Michael.Kane on 2005-09-14
I did get the guide from the link i posted to work. i will however pass on recompiling the kernel at this time.. Thanks..

---

### Post by 8FootSativa on 2005-09-15
Are the steps the same for using a 2.4 kernel?

If I can use 2.4.31 on Ubuntu I'll have no need for Mepis.  :)

---

### Post by tseliot on 2005-09-15
[QUOTE=8FootSativa]Are the steps the same for using a 2.4 kernel?

If I can use 2.4.31 on Ubuntu I'll have no need for Mepis.  :)[/QUOTE]
Yes, I guess so.

---

### Post by Dooglus on 2005-09-19
[QUOTE=myha]Hi!

edit: Ok I got it working now, the problem was I edited grub config and added vga=792 and now I removed it and its ok but with smaller resolution... Why 792 isnt working? It works on previous kernel image but not on new one...

[/QUOTE]

I have exactly the same problem.  I am using the same config as the pre-built kernel, but when I boot the kernel I compiled the screen is black until the gdm login screen appears.

I use lilo, not grub, and have identical options for both kernels.  I don't mention vga= in there at all, so whatever the default is, it's not working for me.

---

### Post by tseliot on 2005-09-20
[QUOTE=Dooglus]I have exactly the same problem.  I am using the same config as the pre-built kernel, but when I boot the kernel I compiled the screen is black until the gdm login screen appears.

I use lilo, not grub, and have identical options for both kernels.  I don't mention vga= in there at all, so whatever the default is, it's not working for me.[/QUOTE]
Sorry but I've always used GRUB. I'm trying to learn using LILO as I'm running PCLinuxOS now.

BTW try to put vga= some of the numbers I wrote in my post and see if one of them works.

---

### Post by myha on 2005-09-20
Hi!

I need some help here...

I downloaded linux-2.6.13.2.tar.bz2 and extracted it into /usr/src/linux-2.6.13.2  
I then had to go to /usr/src/linux/linux-2.6.13.2/  to do make menuconfig. All went well exept i cant find kernel-image and kernel-headers ... (point 6 in guide)   :???: 

Where are they ??

Thanks, Miha

---

### Post by tseliot on 2005-09-20
[QUOTE=myha]Hi!

I need some help here...

I downloaded linux-2.6.13.2.tar.bz2 and extracted it into /usr/src/linux-2.6.13.2  
I then had to go to /usr/src/linux/linux-2.6.13.2/  to do make menuconfig. All went well exept i cant find kernel-image and kernel-headers ... (point 6 in guide)   :???: 

Where are they ??

Thanks, Miha[/QUOTE]
1) I think you have 2 directories using the same name /usr/src/linux-2.6.13.2/linux-2.6.13.2/

delete both the new folders. When you extract the file try to extract it to /usr/src/ (instead of /usr/src/linux-2.6.13.2) as it will create  linux-2.6.13.2 folder automatically.
Remove the &#8220;linux&#8221; link (the one you made with &#8220;sudo ln -s /usr/src/linux-2.6.13.2 linux&#8221;) and [COLOR=Red]start the guide again[/COLOR] (you will need to compile a new kernel).

2)QUOTE: All went well exept i cant find kernel-image and kernel-headers ... (point 6 in guide)
Make sure you use this command &#8220;sudo make-kpkg --initrd --append-to-version=-custom kernel_image [COLOR=Blue]kernel_headers[/COLOR]&#8221; to compile your kernel&#8221;

As you can see, the words in blue are the ones you need if you want to compile the headers.

And I repeat, please [COLOR=Red]start the guide again[/COLOR].

If you have any othe problems after the process, please post them.

---

### Post by myha on 2005-09-20
Well I tried again the way you wrote and now I got the following error: (please see attachment).

---

### Post by tseliot on 2005-09-20
[QUOTE=myha]Well I tried again the way you wrote and now I got the following error: (please see attachment).[/QUOTE]
Maybe I asked you before but: do you use Ubuntu Hoary or Ubuntu Breezy?

---

### Post by myha on 2005-09-20
Hi!

I'm using hoary... 
Well I managed to compile kernel, the problem was in irda... I removed that and everything is fine now... Well, not everything, but im getting there...  :)

So thank you very much for your time and patience, I think I learned a bit about compiling kernell so you time wasnt quite wasted...   :wink: 

Thank you,
Miha

---

### Post by TakisX on 2005-09-20
here what i get

takisx@nisaki:~/download$ sudo tar --bzip2 -xvf linux-2.6.13.2.tar.bz2  /usr/src 
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

what is wrong ?
i follow your guide to letter

---

### Post by tseliot on 2005-09-20
[QUOTE=TakisX]here what i get

takisx@nisaki:~/download$ sudo tar --bzip2 -xvf linux-2.6.13.2.tar.bz2  /usr/src 
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

what is wrong ?
i follow your guide to letter[/QUOTE]
I admit that I don't know what can cause your problem BUT we can get around the problem.

Open Terminal or Konsole and type:

sudo nautilus (if you use GNOME)

OR 

sudo konqueror (if you use KDE)

Open the zipped file from nautilus or konqueror by clicking on it (it will run ark or some other application) and extract it ([COLOR=Red]DON'T[/COLOR] create any new folder otherwise you will have some double folder like /usr/src/linux-2.6.13.2/linux-2.6.13.2) to /usr/src.

Then you can keep on following my guide.

Tell me if it works

---

### Post by odin on 2005-09-21
[QUOTE=tseliot]I admit that I don't know what can cause your problem BUT we can get around the problem.

Open Terminal or Konsole and type:

sudo nautilus (if you use GNOME)

OR 

sudo konqueror (if you use KDE)

Open the zipped file from nautilus or konqueror by clicking on it (it will run ark or some other application) and extract it ([COLOR=Red]DON'T[/COLOR] create any new folder otherwise you will have some double folder like /usr/src/linux-2.6.13.2/linux-2.6.13.2) to /usr/src.

Then you can keep on following my guide.

Tell me if it works[/QUOTE]


I didnt follow what you were talking about but if you want to untar that and place it in /usr/src then just do:

tar -xvjf linux-xxxx

and then

mv the_directory_created_when_untar /usr/src

hope this helps you.

---

### Post by TakisX on 2005-09-21
Thanks it worked .I unpack and move the file to /usr/src. The line in tseliot howto does not work for me.
How i get the breezy kernel ? I have hoary

---

### Post by tseliot on 2005-09-21
[QUOTE=TakisX]Thanks it worked .I unpack and move the file to /usr/src. The line in tseliot howto does not work for me.
How i get the breezy kernel ? I have hoary[/QUOTE]
If you need breezy kernel tree or something else:

sudo gedit /etc/apt/sources.list

change the word "Hoary" (in the lines) to "Breezy"

save and exit

Open synaptic, reload and download ONLY what you need

Then go back to the file and set everything back to "Hoary" so as not to screw your system up.

---

### Post by odin on 2005-09-21
[QUOTE=tseliot]If you need breezy kernel tree or something else:

sudo gedit /etc/apt/sources.list

change the word "Hoary" (in the lines) to "Breezy"

save and exit

Open synaptic, reload and download ONLY what you need

Then go back to the file and set everything back to "Hoary" so as not to screw your system up.[/QUOTE]

Just asking because I have no idea about it.Is it secure what you say?

I'm confused because some people says that it's not a good idea to mix things from different releases.

---

### Post by tseliot on 2005-09-21
[QUOTE=odin]Just asking because I have no idea about it.Is it secure what you say?

I'm confused because some people says that it's not a good idea to mix things from different releases.[/QUOTE]
If you install ONLY kernel tree (source+patches) it won't break your system. For this reason I recommended to set things back to "Hoary" after you  get the kernel tree. In this way you can compile a new kernel from Breezy sources and you will also need GCC 3.4 ([COLOR=Red]from Hoary repos[/COLOR]). The only "problem" you can have is that you have (if you use nvidia drivers) to make the nvidia installer use GCC 3.4 (I've made a guide about that)

BTW I installed a kernel image and headers from Breezy and I had no problems at all. The problems come when you try to install other things from Breezy repositories because there will be unmet dependencies.

I hope this makes things a bit clearer

---

### Post by cyclister on 2005-09-21
Hey man I really trying here I do not what to do :( I see that your some kind of king at this hehe.Oki I have a shity nvidia vanta 6 card stands in my device manager.
I have breezy if I check in terminal I want hoary hedhog, I have higher recetptions but might missed one step, I think not I can see many more packs now.
And I have gnome and think I want to stay with that.
1 first I want to change to Hoary how to? 
Only change name but Hoary xxxx ?  
I standing in the 
/usr/src$ cd /usr/src/linuxsudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux

And the file do not exist :(
Standing though in /usr/src$
Trying out the next step sudo make menuconfig or xconfig 
In terminal I can read "terminal no rule to create target" I have not an englisch version.And I follow everything bit by bit.
Hey man what to do?

Offtopic
Saying again your the king on compilmation matters, how did you become a master
 in this? 
You are surely a rare guy, take that as a compliment.

---

### Post by tseliot on 2005-09-22
[QUOTE=cyclister]Hey man I really trying here I do not what to do :( I see that your some kind of king at this hehe.Oki I have a shity nvidia vanta 6 card stands in my device manager.
I have breezy if I check in terminal I want hoary hedhog, I have higher recetptions but might missed one step, I think not I can see many more packs now.
And I have gnome and think I want to stay with that.
1 first I want to change to Hoary how to? 
Only change name but Hoary xxxx ?  
I standing in the 
/usr/src$ cd /usr/src/linuxsudo ln -s /usr/src/linux-source-2.6.11 /usr/src/linux

And the file do not exist :(
Standing though in /usr/src$
Trying out the next step sudo make menuconfig or xconfig 
In terminal I can read "terminal no rule to create target" I have not an englisch version.And I follow everything bit by bit.
Hey man what to do?

Offtopic
Saying again your the king on compilmation matters, how did you become a master
 in this? 
You are surely a rare guy, take that as a compliment.[/QUOTE]

Thanks for the compliment but I'm not a "king" of compilation. I had to learn how to compile my kernel because my previous computer was very unfriendly to Linux. I followed Luca_linux's guide in this forum and I thought my experience could be useful to many newbies. Believe me I don't know if you can understand what what kind of problems  I had to face because of hardware incompatibilities. (Fortunately I've bought a new computer that works out of the box with Linux). I don't want any newbie to get as frustrated as I got and for this reason I write my guides. I'm just a common guy who learns fast.

About your problem:

1) delete your linux folder:
sudo rm linux

then

cd /usr/src/

ls (in this way you will see the content of the folder)

See the name of the folder with the linux source (and make sure there is not a double folder, one inside the other, for example /linux-source-2.6.11/linux-source-2.6.11/) and put it when I put the word in red

sudo ln -s /usr/src/[COLOR=Red]linux-source-2.6.11[/COLOR] linux

cd linux

ls

sudo make menuconfig

2) About Hoary: if you want to switch to Hoary (from Breezy) you will have to download a Hoary iso image and install it over Breezy.

---

### Post by cyclister on 2005-09-22
Ok trying doing that part but I now the message command not found apear, this is very strange.
Im gonna do everything all over from the first step, to the last and first do the rm, I did take a good sleep here.So this gonna work tomorrow or so.
I only gonna take that you spelled in red?
Another thing can I have a browser up and going and my firewall when I do this, meaning in other system say windows when you upgrading something you turn off everything.
A little thing here I tried to in put the 2.6.12 kernel first when I saw the compilation, can it be a problem?
When I now trying to do a compilation of 2.6.11 instead.

Ok man how do I know if I have done my lesson and everything is runing on a compilmated kernel?
Now I get this messages: To many levels of symbolic links  :?: 

Btw I think stick with breezy :-P 
Yeah you sure are a quick learner, I guess I gonna get this done after some  ](*,) 
But hey you learned all about it thats cool

---

### Post by tseliot on 2005-09-22
[QUOTE=cyclister]Ok trying doing that part but I now the message command not found apear, this is very strange.
Im gonna do everything all over from the first step, to the last and first do the rm, I did take a good sleep here.So this gonna work tomorrow or so.[/QUOTE]
Yes, I think you'd better start from scratch

[QUOTE=cyclister]I only gonna take that you spelled in red?[/QUOTE]
I don't understand the question. BTW you have to follow the commands (EVERY command) as described in my guide

[QUOTE=cyclister]Another thing can I have a browser up and going and my firewall when I do this, meaning in other system say windows when you upgrading something you turn off everything.[/QUOTE]
You can do whatever you want during the process. However I advise you not to use resource intensive applications such as music or video players, etc. The firewall won't cause you any problem.

[QUOTE=cyclister]A little thing here I tried to in put the 2.6.12 kernel first when I saw the compilation, can it be a problem?
When I now trying to do a compilation of 2.6.11 instead.[/QUOTE]
It's not a problem, you can use any kernel version. Just make sure you extract the tar(or zipped) file properly.

[QUOTE=cyclister]Btw I think stick with breezy :-P 
Yeah you sure are a quick learner, I guess I gonna get this done after some  ](*,) 
But hey you learned all about it thats cool[/QUOTE]
Don't you worry, compiling a new kernel is a breeze after you've managed to do it 1 time  ;-)

---

### Post by cyclister on 2005-09-22
In my usr/src I can see one linux one linux kernel 2.6.11 is I done then?
And I have also a tar "package" 2.6.12 how do I extract that rar or zip?
My "archive handler" didnt achive to extracht it.

My little question is also how do I know I reach the goal when the compilation is done?

---

### Post by tseliot on 2005-09-22
[QUOTE=odin]I didnt follow what you were talking about but if you want to untar that and place it in /usr/src then just do:

tar -xvjf linux-xxxx

and then

sudo mv the_directory_created_when_untar /usr/src

hope this helps you.[/QUOTE]
cyclister: try this method

---

### Post by cyclister on 2005-09-23
A little thing here do I have to restart and do the every first step in this howto evry time?
I guess I am quite long in the compilation, and I have to do every step every 
time or? 
Yesterday I was over to a friend all day, then I ride my bicyckle so darn hard I was all to tired.And some good tv programms and so forth.
But hey now the compilation gonna work, I mean this is a via chipset computer for god sake.So now I gonna pray to the godess of all technical matters technica I invented her to help me get some guide, sometimes her help have come sent from no where thats a promise  ;-) 
I must be stupid I guess many had done the compilation for light years ago :(
With your guidence and all

---

### Post by tseliot on 2005-09-23
[QUOTE=cyclister]A little thing here do I have to restart and do the every first step in this howto evry time?
I guess I am quite long in the compilation, and I have to do every step every 
time or? 
Yesterday I was over to a friend all day, then I ride my bicyckle so darn hard I was all to tired.And some good tv programms and so forth.
But hey now the compilation gonna work, I mean this is a via chipset computer for god sake.So now I gonna pray to the godess of all technical matters technica I invented her to help me get some guide, sometimes her help have come sent from no where thats a promise  ;-) 
I must be stupid I guess many had done the compilation for light years ago :(
With your guidence and all[/QUOTE]
Just to be sure:
1)delete the folder with linux source (sudo rm /usr/src/linux-source-2.6.11 or any other version)

2) delete the link to the kernel (sudo rm //usr/src/linux)

3) and start again using the advices I gave you before.

It's just a matter of copy and paste commands from the guide to the command line. Of course the time of compilation can be 45min long. You can do it  ;-)

---

### Post by cyclister on 2005-09-23
Ok man I have tar the packages I did that but now I cant menu config the thing here, trying out 2 commands. x config or


  :smile: 

I thought linux was a great thing with old grafic cards, hey I do not have any drivers I have look for them but cant score any, not any how does work for this fricking computer.

We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)

Ohh no I have to download a packages again or what should I do?
aaaw crap
When I trying to start with my new kernel I cant I get a black screen with some text on it, but I choose grub and start with my old.I have only done half the complimation due to my menu config problems and such

---

### Post by GoA on 2005-09-24
Has anyone been able to make the kernel in breezy? I treid to follow this guide and one time I got to point where it was loading x but then crashed. :( That was with kernel without any changes. Any of custom made haven't even loaded. :D

---

### Post by tseliot on 2005-09-24
[QUOTE=cyclister]Ok man I have tar the packages I did that but now I cant menu config the thing here, trying out 2 commands. x config or


  :smile: 

I thought linux was a great thing with old grafic cards, hey I do not have any drivers I have look for them but cant score any, not any how does work for this fricking computer.

We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)

Ohh no I have to download a packages again or what should I do?
aaaw crap
When I trying to start with my new kernel I cant I get a black screen with some text on it, but I choose grub and start with my old.I have only done half the complimation due to my menu config problems and such[/QUOTE]

1) Ok, I don't get the problem. But can  you post the results of this actions, please?

cd /usr/src/

ls (and post the results)

cd linux

ls (and post the results)

and if there is another folder inside (like linux source)

cd the_directory_inside

ls (and post the results)

2) In which folder do you do the operation (and get the error) (/usr/src, etc.)?

3) I don't know what your problem is with your graphic card.

---

### Post by thomax on 2005-09-24
After some time of compiling I get this error message :(

> make[1]: Entering directory `/usr/src/linux-source-2.6.11'
  CHK     include/linux/version.h
make[2]: `arch/i386/kernel/asm-offsets.s' is up to date.
  CC [M]  drivers/media/video/saa7134/saa7134-dvb.o
drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
make[5]: *** [drivers/media/video/saa7134/saa7134-dvb.o] Fout 1
make[4]: *** [drivers/media/video/saa7134] Fout 2
make[3]: *** [drivers/media/video] Fout 2
make[2]: *** [drivers/media] Fout 2
make[1]: *** [drivers] Fout 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.11'
make: *** [stamp-build] Fout 2
thomas@LinuxBox:/usr/src/linux$

---

### Post by tseliot on 2005-09-24
[QUOTE=thomax]After some time of compiling I get this error message :([/QUOTE]
Do you have any dvb card in your computer?

If so, try to remove it from your computer and compile the kernel. If the new kernel works then put the card back into your computer.

---

### Post by cyclister on 2005-09-24
[QUOTE=tseliot]1) Ok, I don't get the problem. But can  you post the results of this actions, please?

cd /usr/src/

ls (and post the results)

cd linux

ls (and post the results)

and if there is another folder inside (like linux source)

cd the_directory_inside

ls (and post the results)

2) In which folder do you do the operation (and get the error) (/usr/src, etc.)?

3) I don't know what your problem is with your graphic card.[/QUOTE]

This is ls result
linux-patches  linux-source-2.6.12  linux-source-2.6.12.tar.bz2
In two colours this one over here is blues ------------ this one is red
The text is in two diffrent colours.

cd the_directory_inside result = The file or the catalouge dosent exist
ls after this is still the same as I posted before.

2) Its in /usr/src everything taking place

3) I do not know wich driver I have or should I take away the "drivers" I cant be able to have any how, I take away them from synaptic.

I can tar but I cant menuconfig my system :(

---

### Post by tseliot on 2005-09-25
[QUOTE=cyclister]This is ls result
linux-patches  linux-source-2.6.12  linux-source-2.6.12.tar.bz2
In two colours this one over here is blues ------------ this one is red
The text is in two diffrent colours.

cd the_directory_inside result = The file or the catalouge dosent exist
ls after this is still the same as I posted before.

2) Its in /usr/src everything taking place

3) I do not know wich driver I have or should I take away the "drivers" I cant be able to have any how, I take away them from synaptic.

I can tar but I cant menuconfig my system :([/QUOTE]
1) You have to create the link to your kernel source (as described in the guide) and you will see the following list:
linux-patches  linux-source-2.6.12  [COLOR=Blue]linux[/COLOR] linux-source-2.6.12.tar.bz2 

2) type:
cd  linux-source-2.6.12
ls
Post the results

---

### Post by cyclister on 2005-09-26
Here I trying out the sudo make oldconfig and get this error.
Unfortanly I have some few other problems to deal with like things, but soon this comilation is done I can sence that :D born optimistic I am

/usr/src/linux-source-2.6.12$ sudo make menuconfig
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] error 127

So this sudo make "config" do not work but soon it will

---

### Post by tseliot on 2005-09-27
[QUOTE=cyclister]Here I trying out the sudo make oldconfig and get this error.
Unfortanly I have some few other problems to deal with like things, but soon this comilation is done I can sence that :D born optimistic I am

/usr/src/linux-source-2.6.12$ sudo make menuconfig
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] error 127

So this sudo make "config" do not work but soon it will[/QUOTE]
Open synaptic/kynaptic and install gcc-3.4 (not only the base package) and then try the compilation again.

---

### Post by cyclister on 2005-09-27
Hi again tseliot
LOL this is both funny and really sad thing going on here.

This sudo make oldconfig/make config does not work at all.
The make: *** Ingen regel f&#246;r att skapa m&#229;let "oldconfig".  Stannar.
In english  *** No rules to create the aim/goal "oldconfig". Stop/end/stay

I can tar do al most everything but not the last little part, mt compilation is like the never ending story ;-)
Until I write again if I succeding in this arreviderci and have a nice afternoon/night if you are in Italy of course, in other way s have a nice day

---

### Post by tseliot on 2005-09-27
[QUOTE=cyclister]Hi again tseliot
LOL this is both funny and really sad thing going on here.

This sudo make oldconfig/make config does not work at all.
The make: *** Ingen regel för att skapa målet "oldconfig".  Stannar.
In english  *** No rules to create the aim/goal "oldconfig". Stop/end/stay

I can tar do al most everything but not the last little part, mt compilation is like the never ending story ;-)
Until I write again if I succeding in this arreviderci and have a nice afternoon/night if you are in Italy of course, in other way s have a nice day[/QUOTE]
I'm sorry :(  the only thing I can suggest is to do this again:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

Buona notte (=good night) to you

---

### Post by cyclister on 2005-09-28
Ok man this really sux, I know its something with my installation i mixed some junk partitions, and so forth.I gonna take away them a little later and make my swap grow a little bit.But hey I think I am a little bit to nub here in this but I promise soon I have a compilated kernel.
I think it can be that things that cause some problems.
Can VIA chipset be a problem here due compilation?
Can this damage my computer in some way, to run with higher receptories and not have done a real compilation of my kernel?

Offtopic and many thanks for sweden, ya
And when I have done my compilation with your gueidings that you really have giving me you put an effort in this, I gonna thank you again.So I thank you for now and when I get on new thoughts and when Im able to raise some energy Im gonna do my system clean and neat, and everything all over, new updated and so forth.In my computer at home get higher receptories, iot might be somthing I did forget their or some junk in the text I didnt do right.Hey in a near future it will work but Im lazy as a dog.I rather eat some candys or cookies with milk, and fart and smile to life as it goes by, and enjoying the stay and art of being dull and bored I think its fun.
But in the other hand I have to train a little wash clean and little, some guy named Per said to me, "Man everything have to have little style" That make a little sense to me, so more of enjoyment and some trainging to make a good balance and after a month you clean a little in your home.
You have really tried man, I have had problems in windows some pall's even didnt heard of, so this aint the first time nothing is like this.Hey I am used to trouble so I have to brawl with my computers but I will always win in the end :D and when Im done I have grown a little in skills :-P
I will go in here and look at the tips you gave me in the future, hope I will see you in IRC/X-chat/Bitch/Or witch client I choose.

As we say in sweden tack och godnatt thx and goodnight
Or Ha en sk&#246;n eftermiddag, Have a nice afternoon :-P

---

### Post by tseliot on 2005-09-28
[QUOTE=cyclister]Can VIA chipset be a problem here due compilation?[/QUOTE]
I think mine is a VIA chipset, so it should work.


[QUOTE=cyclister]Can this damage my computer in some way, to run with higher receptories and not have done a real compilation of my kernel?[/QUOTE]
What do you mean? And (maybe I have asked you before) why do you need to compile a new kernel?

---

### Post by Bomper on 2005-10-05
O. K.

 1.- Reboot

 2.-  

* Starting Hardware absatraction layer...
00:22:08.204 [W] hald.c:301: Your kernel does not support capabilities;
some features will not be available

 ¿capabilities?  ¿some features will not be available?.  ¿¿¿  ¡¡¡  ????

---

### Post by tseliot on 2005-10-05
[QUOTE=Bomper]O. K.
1.- Reboot
2.-  
* Starting Hardware absatraction layer...
00:22:08.204 [W] hald.c:301: Your kernel does not support capabilities;
some features will not be available
¿capabilities?  ¿some features will not be available?.  ¿¿¿  ¡¡¡  ????[/QUOTE]
I don't know what it is, it might be ok though. Does the kernel work?

---

### Post by Bomper on 2005-10-05
> Does the kernel work?

 Yes.  :p 

  I´m sorry.  My English is very bad.

---

### Post by tseliot on 2005-10-05
[QUOTE=Bomper]Yes.  :p 
I´m sorry.  My English is very bad.[/QUOTE]
I remember something similar (I can't recall the exact message) happening to the kernels I compiled some time ago (I'm currently using only the one which comes with Ubuntu by default). Nonetheless they worked flawlessly. This means you don't have to worry about that message. Enjoy your new kernel ;)

---

### Post by Bomper on 2005-10-05
Posible solution?  :-k 

[http://ubuntuforums.org/archive/index.php/t-231.html](http://ubuntuforums.org/archive/index.php/t-231.html)

---

### Post by tseliot on 2005-10-05
[QUOTE=Bomper]Posible solution?  :-k 
[http://ubuntuforums.org/archive/index.php/t-231.html](http://ubuntuforums.org/archive/index.php/t-231.html)[/QUOTE]
I don't know. It might do the trick for you but I can't try it right now because I'm kind of busy. However it doesn't look difficult so why don't you try it yourself? It could be satisfying if you managed to make things work

---

### Post by bored2k on 2005-10-05
Can someone remind me of why I should compile my own Kernel (Breezy here) ?

---

### Post by duminas on 2005-10-06
Strip out drivers and features you don't need (in my case, stripping SCSI, IEEE1394, ISDN, and moving ndiswrapper into the kernel itself, among other things)?

This is to the author of the thread:
Quick question. Why not just CTRL+ALT+Backspace (and the sometimes compulsory *startx*) instead of rebooting the entire PC? Just curious, since the former should restart X (and change the graphics driver), should it not?

---

### Post by tseliot on 2005-10-06
[QUOTE=duminas]Quick question. Why not just CTRL+ALT+Backspace (and the sometimes compulsory *startx*) instead of rebooting the entire PC? Just curious, since the former should restart X (and change the graphics driver), should it not?[/QUOTE]
Because (AFAIK) you have to restart your computer in order to boot using the new kernel.

---

### Post by tseliot on 2005-10-06
[QUOTE=bored2k]Can someone remind me of why I should compile my own Kernel (Breezy here) ?[/QUOTE]
You should do it ONLY if you had problems with hardware recognition (and DMA,etc) or if you were curious to try the latest vanilla kernel.

However I suggest you NOT TO DO IT in BREEZY. Some Breezy users reported kernel panic when they tried to boot using their compiled kernels. I haven't tried Breezy myself yet so I can't support you in case anything goes wrong. I will adapt my guide after Breezy is stable (and according to my free time)

---

### Post by Pablo_Escobar on 2005-10-08
Quick question tseliot if I may :)

By compiling my kernel, instead of using the distro one, and by selecting only the modules I need, will it give my Ubuntu some significant speed boost :confused:

---

### Post by tseliot on 2005-10-08
[QUOTE=Pablo_Escobar]Quick question tseliot if I may :)

By compiling my kernel, instead of using the distro one, and by selecting only the modules I need, will it give my Ubuntu some significant speed boost :confused:[/QUOTE]
Yes I guess so but only if you know how to do it. I think some geek in Gentoo forum can answer you (there are geeks who have found a way to use almost every single drop of power),

---

### Post by merlyn on 2005-10-08
Thanks, this is great. 

I have just compiled my first custom kernel ever and everything is working fine.

The next step is to learn how to fine tune the process and really get this baby singing. :D

I haven't reinstalled the nvidia drivers yet, and it's quite likely that I haven't got the most recent alsa drivers either.

Is is possible to install these into the kernel-source as patches before compiling. If so would you mind pointing me in the right direction.

Thanks heaps once again.

Cheers.

---

### Post by tseliot on 2005-10-08
[QUOTE=merlyn]Thanks, this is great. 

I have just compiled my first custom kernel ever and everything is working fine.

The next step is to learn how to fine tune the process and really get this baby singing. :D

I haven't reinstalled the nvidia drivers yet, and it's quite likely that I haven't got the most recent alsa drivers either.

Is is possible to install these into the kernel-source as patches before compiling. If so would you mind pointing me in the right direction.

Thanks heaps once again.

Cheers.[/QUOTE]
[COLOR="#ff0000"]I suggest you to use my guide to install the nvidia drivers using the nvidia installer (it's MUCH EASIER). you can find the link in my signature[/COLOR]

However if you want to do you it your way you can follow these steps ([COLOR="Red"]I CAN'T ASSURE IT WORKS FOR YOU[/COLOR] but it will do you no harm):

1) You should get the [COLOR="Blue"]"nvidia-kernel-source"[/COLOR] package (you should be able to find 7667 version in Breezy repositories) and the [COLOR="Blue"]"nvidia-glx"[/COLOR] package (of the same version)

2) Extract it to /usr/src (a new "nvidia-kernel" folder will be created) and leave it there.

3) Follow my guide as before BUT you have to change the final command:

sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers [COLOR="Red"]modules_image[/COLOR]

The word in red will make you create an additional package: the nvidia restricted module. You have to install it in the same way you install kernel image and headers or any other .deb package.

4) Then install the nvidia-glx package and enable the nvidia driver from xorg.conf. (as described in the Ubuntu Starter guide)

Have fun!

---

### Post by matthew on 2005-10-12
Just a quick thank you. I had never complied a kernel and wanted to try on a test machine I have just for the experience. Using your howto I compiled both an Ubuntu kernel as well as a vanilla kernel. Thanks for an easy-to-follow guide!

---

### Post by herot on 2005-10-12
hey tselliot you wrote a really great tutorial! thanks. What do i change in it if i just want to REcompile my existing kernel?

i dont really wanna upgrade my kernel i just wanna practice compiling...
i have been doing frequent apt's for two weeks and so far Breezy is working great for me...btw

---

### Post by tseliot on 2005-10-13
[QUOTE=herot]hey tselliot you wrote a really great tutorial! thanks. What do i change in it if i just want to REcompile my existing kernel?

i dont really wanna upgrade my kernel i just wanna practice compiling...
i have been doing frequent apt's for two weeks and so far Breezy is working great for me...btw[/QUOTE]
If you don't want to change anything you have to follow the guide (skipping the dma part). In this way you will make an exact copy of your kernel.

B[COLOR="Red"]TW this guide might not work in Breezy.[/COLOR] I'm downloading Breezy right now, then I will try to adapt all my guides.

---

### Post by matthew on 2005-10-13
[quote=tseliot]B[COLOR=Red]TW this guide might not work in Breezy.[/COLOR] I'm downloading Breezy right now, then I will try to adapt all my guides.[/quote] I'm sure you will want to test it yourself since it is your name on the guide. I used your guide to compile both an Ubuntu kernel and a vanilla kernel in Breezy earlier this week and it worked with no modifications needed.

EDIT: see post below...I remembered a bit later that I did have to make a modification. I had to install gcc-3.4 in order to compile the kernel as it won't yet compile with 4.0. Doh! Sorry for the confusion.

---

### Post by tseliot on 2005-10-13
[QUOTE=matthew]I'm sure you will want to test it yourself since it is your name on the guide. I used your guide to compile both an Ubuntu kernel and a vanilla kernel in Breezy earlier this week and it worked with no modifications needed.[/QUOTE]
Interesting, thanks :)

---

### Post by Alc0h0lic on 2005-10-13
I just tried to recompile the breezy kernel but I run into the following error after doing 'sudo make oldconfig':
```
ivo@s021407:/usr/src/linux$ sudo make oldconfig
Password:
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Fout 127
make: *** [scripts_basic] Fout 2

```
This kinda makes sense since I only have gcc-4.0 installed and not gcc-3.4, do I really need gcc-3.4 to compile the kernel? I thought breezy was supposed to be compiled with gcc-4.0. Anyway let me know if you know of a way to fix this, thanks.

---

### Post by matthew on 2005-10-13
[quote=Alc0h0lic]I just tried to recompile the breezy kernel but I run into the following error after doing 'sudo make oldconfig':
```
ivo@s021407:/usr/src/linux$ sudo make oldconfig
Password:
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Fout 127
make: *** [scripts_basic] Fout 2

``` This kinda makes sense since I only have gcc-4.0 installed and not gcc-3.4, do I really need gcc-3.4 to compile the kernel? I thought breezy was supposed to be compiled with gcc-4.0. Anyway let me know if you know of a way to fix this, thanks.[/quote] 
Oh, man. My bad earlier. I said I used the howto and it worked with Breezy--that was true. I did need to make a modification, though. (I've edited my post above so this fact is known.) I forgot that I needed to install gcc-3.4 to do it. It's in the repos. The thing is almost everything in Breezy is compiled with 4.0, but the kernel still needs 3.4. Better add that to the list of things to install at the beginning of the guide.

---

### Post by tseliot on 2005-10-13
[QUOTE=matthew]Oh, man. My bad earlier. I said I used the howto and it worked with Breezy--that was true. I did need to make a modification, though. (I've edited my post above so this fact is known.) I forgot that I needed to install gcc-3.4 to do it. It's in the repos. The thing is almost everything in Breezy is compiled with 4.0, but the kernel still needs 3.4. Better add that to the list of things to install at the beginning of the guide.[/QUOTE]
You're right, I had to do almost the same thing when adapting my nvidia drivers guide to Breezy.

---

### Post by tseliot on 2005-10-13
[QUOTE=Alc0h0lic]I just tried to recompile the breezy kernel but I run into the following error after doing 'sudo make oldconfig':
```
ivo@s021407:/usr/src/linux$ sudo make oldconfig
Password:
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Fout 127
make: *** [scripts_basic] Fout 2

```
This kinda makes sense since I only have gcc-4.0 installed and not gcc-3.4, do I really need gcc-3.4 to compile the kernel? I thought breezy was supposed to be compiled with gcc-4.0. Anyway let me know if you know of a way to fix this, thanks.[/QUOTE]
Open Terminal or Konsole and type:

sudo apt-get install gcc-3.4

Then try the compilation again.

[COLOR="Red"]But I think the repositories are down at the moment[/COLOR]

---

### Post by herot on 2005-10-14
tselliot

when i do:

```
apt-get install linux-k7
```

it doesn't recompile the kernel does it??
doesn't it just give me a new kernel version with all my old settings?

---

### Post by tseliot on 2005-10-14
[QUOTE=herot]tselliot

when i do:

```
apt-get install linux-k7
```

it doesn't recompile the kernel does it??
doesn't it just give me a new kernel version with all my old settings?[/QUOTE]
It installs a new kernel with the default settings of Ubuntu kernels (which can be your old settings too if you are currently using an Ubuntu kernel). 

In other words if you are using the kernel which comes with Ubuntu you will have the same settings when you install any other kernel from ubuntu repositories (like "linux-k7" kernel)

---

### Post by TiMBuS on 2005-10-14
Because I need to compile kernel modules for my modem, I kinda find it difficult to update through repositories...

Can you give me a link to a .deb package for gcc-3.4? That would be very appreciated. Thanks!

---

### Post by tseliot on 2005-10-15
[QUOTE=TiMBuS]Because I need to compile kernel modules for my modem, I kinda find it difficult to update through repositories...

Can you give me a link to a .deb package for gcc-3.4? That would be very appreciated. Thanks![/QUOTE]
Get to this link:
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/")

and download the following files according to your architecture (i386, k7,etc.)

gcc-3.4-base_3.4.4-6ubuntu8_your_architecture.deb
gcc-3.4_3.4.4-6ubuntu8_your_architecture.deb

---

### Post by Juippisi on 2005-10-16
Firstly: Thanks for the howto.

Secondly: Sight... having some problems ;-). I have readed every post in this thread and found nothing so far.

Ok, so I have tried to compile 2.6.13.4 and 2.6.13-ck8 (downloaded from the internet, extracted and so on) but neither of them worked. They compiled well, but on the boot both said something like "kernel: device-mapper: dm-linear: Device lookup failed" (Copter had the same problem) and neither of them mounted my hdb partitions. Still hda has DMA enabled, so it can't be that.

Yes, both booted so I could use my Linux, but all my important files are on hdb1 partition so I can't do anything reasonable with it.

Dmesg doesn't say much that why they won't mount so I'm pretty confused with this problem. Not to mention that I haven't had similar problem ever with other distributions. 

I have enabled ext3 and reiserfs supoorts to the kernel (hdb's are ext3, root is reiserfs).

So, No 'll just have to use this default-kernel which is slow compared to -ck what I have get used to use :-(.

I'm using Kubuntu 5.10, if that tells something to you. And no, I'm not changing my (K)Ubuntu away so easily, there has to be some answer for this. Do I miss some principal support from kernel which I don't know about? Hope that you guys know better ;-).

---

### Post by TiMBuS on 2005-10-16
[QUOTE=tseliot]Get to this link:
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/")

and download the following files according to your architecture (i386, k7,etc.)

gcc-3.4-base_3.4.4-6ubuntu8_your_architecture.deb
gcc-3.4_3.4.4-6ubuntu8_your_architecture.deb[/QUOTE]

Thank you very much! That helped me out alot!

---

### Post by tseliot on 2005-10-16
[QUOTE=Juippisi]Firstly: Thanks for the howto.

Secondly: Sight... having some problems ;-). I have readed every post in this thread and found nothing so far.

Ok, so I have tried to compile 2.6.13.4 and 2.6.13-ck8 (downloaded from the internet, extracted and so on) but neither of them worked. They compiled well, but on the boot both said something like "kernel: device-mapper: dm-linear: Device lookup failed" (Copter had the same problem) and neither of them mounted my hdb partitions. Still hda has DMA enabled, so it can't be that.

Yes, both booted so I could use my Linux, but all my important files are on hdb1 partition so I can't do anything reasonable with it.

Dmesg doesn't say much that why they won't mount so I'm pretty confused with this problem. Not to mention that I haven't had similar problem ever with other distributions. 

I have enabled ext3 and reiserfs supoorts to the kernel (hdb's are ext3, root is reiserfs).

So, No 'll just have to use this default-kernel which is slow compared to -ck what I have get used to use :-(.

I'm using Kubuntu 5.10, if that tells something to you. And no, I'm not changing my (K)Ubuntu away so easily, there has to be some answer for this. Do I miss some principal support from kernel which I don't know about? Hope that you guys know better ;-).[/QUOTE]
I suggest you to install Kubuntu Breezy. Perhaps you won't have to recompile your kernel and BTW it's great.

---

### Post by TiMBuS on 2005-10-17
ooh, one more thing. I don't normally compile my kernel (got real sick of doing it after gentoo...) but I gave it a shot. THe process seems.. different to that of gentoo. Anyways it's all good till I type:
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

the errors I get are:

(with kpkg-clean)
make[4]: *** No rule to make target `arch/um/scripts/Makefile.rules'.  Stop.
make[3]: *** [fs/hostfs] Error 2
make[2]: *** [_clean_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: [real_stamp_clean] Error 2 (ignored)

followed by

(with kpkg --initrd...)
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [stamp-build] Error 2

Weird. Anything I missed?
Don't stress over it though, I'm not fully interested making my own kernel just yet.. Just wondering whats wrong.

---

### Post by tseliot on 2005-10-17
[QUOTE=TiMBuS]ooh, one more thing. I don't normally compile my kernel (got real sick of doing it after gentoo...) but I gave it a shot. THe process seems.. different to that of gentoo. Anyways it's all good till I type:
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

the errors I get are:

(with kpkg-clean)
make[4]: *** No rule to make target `arch/um/scripts/Makefile.rules'.  Stop.
make[3]: *** [fs/hostfs] Error 2
make[2]: *** [_clean_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: [real_stamp_clean] Error 2 (ignored)

followed by

(with kpkg --initrd...)
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [stamp-build] Error 2

Weird. Anything I missed?
Don't stress over it though, I'm not fully interested making my own kernel just yet.. Just wondering whats wrong.[/QUOTE]

Open Synaptic/kynaptic and install: 

"build-essential"
"linux-kernel-headers"
"linux-headers-386"

---

### Post by TiMBuS on 2005-10-17
aaaah
linux-headers-386 wasn't installed. Didn't think it nessisary

TY!

---

### Post by Juippisi on 2005-10-18
[QUOTE=tseliot]I suggest you to install Kubuntu Breezy. Perhaps you won't have to recompile your kernel and BTW it's great.[/QUOTE]

Yes, I'm running now on Kubuntu Breezy (as I said). But, I'm missing the prefetch swap feature that -ck patch provides :-(.

Ok, this isn't slow or laggy (2.6.12-9-686) so it's not like I couldn't use this. I think that soon I'll forget the whole -ck because this is good enough :-P.

But, I'll keep on trying, when I have interest of compiling kernels again.

---

### Post by Mave^ on 2005-10-18
Tseliot i have a few questions and think you or somebody else could answer them for me. First of all i would like to thank you for the howto, i followed it and compiled a kernel succesfully. But, i forgot something. In the xorg.conf i didn't change the driver to vesa, i own a nvidia card so i realised that this applies to any videocard. Do i have to compile the kernel again and do i have to set it to vesa?

This was the first time i ever compiled a kernel, i've worked alot with Debian machines actually my server is one but i always used the standard precompiled kernel that ships with Debian. Usually those kernels including Ubuntu work well but they have alot of drivers and stuff in it that i never use so i want to get rid of that. At first i like to integrate ext3 FS into the kernel but with the "sudo make oldconfig" command al those things are loaded as modules. Do i have to compile from scratch for those options?

Like most users i only use the ext3 FS so all other filesystems may be left out except for floppy en CD/DVD, the same thing goes for a lot of drivers. I have a AMD64 processor but i prefer 32 bit because a lot of programs are 32 bit, i don't like to mess with 32 bit packages in a 64 bit environment. Because i have an Nforce motherboard i would like to install the drivers from nvidia, same thing for my Geforce card. 

Can i still use the nvidia-glx package after compiling a custom kernel or do i have to use the driver from nvidia? For the nvidia drivers the kernel source is needed, i think that's not a problem because everything is there can you acknowledge that for me? Thanks in advance. :)

---

### Post by tseliot on 2005-10-18
[QUOTE=Mave^]In the xorg.conf i didn't change the driver to vesa, i own a nvidia card so i realised that this applies to any videocard. Do i have to compile the kernel again and do i have to set it to vesa?[/QUOTE]
No, I suggested to set it to vesa because if you boot in a new kernel while using nvidia (or ati) proprietary drivers (not the "nv" or "ati" which comes with Ubuntu and which are opensource drivers) the xserver (and the GUI) doesn't start because it can't find the modules of the drivers. In that case you can still edit your xorg.conf (sudo nano /etx/X11/xorg.conf) and set the driver to vesa in order to access the GUI. Then you have to compile the prorietary drivers (if you need 3d acceleration) (I've written a guide about that). In conclusion: no, you don't have to compile your kernel again.

[QUOTE=Mave^]Usually those kernels including Ubuntu work well but they have alot of drivers and stuff in it that i never use so i want to get rid of that. At first i like to integrate ext3 FS into the kernel but with the "sudo make oldconfig" command al those things are loaded as modules. Do i have to compile from scratch for those options?[/QUOTE]
If you want to build the support for ext3 into your kernel you have to recompile it (and use menuconfig after oldconfig, as described in the guide). 

[QUOTE=Mave^]Can i still use the nvidia-glx package after compiling a custom kernel or do i have to use the driver from nvidia? For the nvidia drivers the kernel source is needed, i think that's not a problem because everything is there can you acknowledge that for me? Thanks in advance. :)[/QUOTE]
You won't be able to use the "nvidia-glx package" but you can use the nvidia installer (select the ones for your NFORCE or GEFORCE chipset). I suggest you to follow my guide (look at my signature).

---

### Post by Mave^ on 2005-10-18
[quote=tseliot]No, I suggested to set it to vesa because if you boot in a new kernel while using nvidia (or ati) proprietary drivers (not the "nv" or "ati" which comes with Ubuntu and which are opensource drivers) the xserver (and the GUI) doesn't start because it can't find the modules of the drivers. In that case you can still edit your xorg.conf (sudo nano /etx/X11/xorg.conf) and set the driver to vesa in order to access the GUI. Then you have to compile the prorietary drivers (if you need 3d acceleration) (I've written a guide about that). In conclusion: no, you don't have to compile your kernel again.
[/quote]
Ok thanks, i will edit my xorg.conf before installing the kernel and it will work.
> 
If you want to build the support for ext3 into your kernel you have to recompile it (and use menuconfig after oldconfig, as described in the guide). 

I missed that part, i will check that out.
> 
You won't be able to use the "nvidia-glx package" but you can use the nvidia installer (select the ones for your NFORCE or GEFORCE chipset). I suggest you to follow my guide (look at my signature).
Yes sir, i will follow your guide :cool:

---

### Post by cltrujil on 2005-10-19
[QUOTE=Copter]word.

im an idiot. 2.6.11 compilation error
```

drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
```im learning on my own mistakes... doing 2.6.10

copter :][/QUOTE]

Hello, I have the same error in the same part, I would like to know if anyone could help me, I was trying this kernel because I have had thousand of problems with the ati driver of my video card(ATI 9550), I followed another howto about it in other section of this page, but nothing has worked, finally I decided to compile a new kernel, and it was ok untill I arrived at this point, I got the same error, I was compiling 2.6.11 and I have 2.6.10, anyone who can help me please, thanks in advance.

---

### Post by tseliot on 2005-10-19
[QUOTE=cltrujil]Hello, I have the same error in the same part, I would like to know if anyone could help me, I was trying this kernel because I have had thousand of problems with the ati driver of my video card(ATI 9550), I followed another howto about it in other section of this page, but nothing has worked, finally I decided to compile a new kernel, and it was ok untill I arrived at this point, I got the same error, I was compiling 2.6.11 and I have 2.6.10, anyone who can help me please, thanks in advance.[/QUOTE]
I don't know how to help you but I think you might try Ubuntu Breezy, it has better kernels.

---

### Post by anonOmus on 2005-10-20
Will this howto only allow one to compilt the i386 kernel, i followed your steps and it seems to be the case. how would one go about compiling the 686 kernel?

---

### Post by tseliot on 2005-10-20
> **anonOmus]Will this howto only allow one to compilt the i386 kernel, i followed your steps and it seems to be the case. how would one go about compiling the 686 kernel?[/QUOTE]

Read the guide more carefully:

[QUOTE=]4)Now you have to use the keyboard to move the cursor over the function or submenu you want and press Enter to select it.

[COLOR="Red"]Select the 4th option: Processor type and features

If you have a multiprocessor system you might want to enable "Symmetric multi-processing support" (SMP): select it with your keyboard and press the spacebar to enable it (a "*" will appear beside it). If you don't have it don't enable it.

Select Processor Family and choose the right one (i386 in my case) depending on the output of the command &#8220 said:**
> 

Press the right arrow and select exit

---

### Post by anonOmus on 2005-10-20
silly me sorry

---

### Post by ivalladt on 2005-10-20
[QUOTE=SD-Plissken]This comand sudo tar --bzip2 -xvf linux-2.6.13.1.tar.bz2 /usr/src gives this error
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

This is the Kernel used linux-2.6.13.1.tar.bz2 and it is saved to the desktop.
[/QUOTE]

You better cd to /usr/src and sudo tar xvfj /path/to/linux-2.6.13.1.tar.bz2 from there.

Better if you add your common user to the src group so you don't need to become root for uncompressing sources and compiling them.

---

### Post by jimchristopher on 2006-01-03
nevermind... i reloaded.

---

### Post by Samuro on 2006-02-08
ok, i tried this and it worked like a charm with one exception:
my wireless does not get recognized anymore.

i've already tried what happens if i take no drivers out of the (wireless) network section, but its always the same = lan works, wireless adapter is not recognized. its an intel pro wireless 2915ABG on a acer travelmate 8104

thanks in advance for all hints & tipps

---

### Post by tseliot on 2006-02-19
[QUOTE=Samuro]ok, i tried this and it worked like a charm with one exception:
my wireless does not get recognized anymore.

i've already tried what happens if i take no drivers out of the (wireless) network section, but its always the same = lan works, wireless adapter is not recognized. its an intel pro wireless 2915ABG on a acer travelmate 8104

thanks in advance for all hints & tipps[/QUOTE]
I think that happens because the driver to use your wireless connection is included in the restricted modules (but you don't have any as you recompiled your kernel).

I guess the driver you need is madwifi. You can compile it in the following way:
sudo apt-get install module-assistant
sudo module-assistant

Then a menu will show up:
select "SELECT"
select ipw2200 and press the spacebar to enable it (a cross will appear beside it)
Then press Enter and follow the instructions.

The module should be compiled and your wifi card will work

---

### Post by ifwntrends on 2006-03-06
for the make-kpkg steps i get a command not found error, is that a kubuntu specific thing? i tried replacing with dpkg, no luck.

---

### Post by heimo on 2006-03-06
[quote=ifwntrends]for the make-kpkg steps i get a command not found error, is that a kubuntu specific thing? i tried replacing with dpkg, no luck.[/quote]
make sure you have kernel-package installed:
```
sudo apt-get install kernel-package
```

---

### Post by commodore on 2006-03-06
I can't have over 900mb with 64 bit Ubuntu :(?

---

### Post by ifwntrends on 2006-03-07
[QUOTE=heimo]make sure you have kernel-package installed:
```
sudo apt-get install kernel-package
```[/QUOTE]

thanks, i was just reading through before i got started and didn't recognize those commands

---

### Post by bb002 on 2006-03-10
Nice guide. My vanilla kernel is compiling as I type. I noticed a mistake in your vanilla kernel instructions, though.

the line ```
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2 /usr/src
```
should be ```
sudo tar -xvjf linux-source-2.6.10.tar.bz2 -C /usr/src
```

Well the "--bzip2 -xvf" is valid and can be left alone, I just happen to be to lazy to type that. :)
However, the "-C" that must be added before "/usr/src" otherwise "tar" tries to extract "/usr/src" from the bzip archive and fails.

---

### Post by valde on 2006-04-09
Just compiled the newest vanilla kernel ( [http://www.kernel.org/](http://www.kernel.org/) )
kernel-headers-2.6.16.2-custom_10.00.Custom_i386.deb 
kernel-image-2.6.16.2-custom_10.00.Custom_i386.deb

Everything worked fine and the new kernel loads faster.

sudo hdparm -d /dev/hda 
/dev/hda:
 using_dma    =  1 (on)

sudo hdparm -d /dev/cdrom
/dev/cdrom:
 using_dma    =  1 (on)

I love it!

---

### Post by tseliot on 2006-04-12
[QUOTE=commodore]I can't have over 900mb with 64 bit Ubuntu :(?[/QUOTE]
Of course you can. Install linux-image-686 or linux-image-k7 (according to yuor CPU) and reboot

---

### Post by japplex on 2006-04-13
Being easter i thought I would try to do my first kernel upgrade following this guide.

My xorg.conf is as follows
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

When I change it to:
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

and I restarted the PC, it went through the normal boot process then the monitor went into sleep mode and nothing would bring it back to life. 

Why is this so and what should I do to get an active PC so that I can upgrade the kernel.
Thanks.

---

### Post by techneck on 2006-04-17
Try this:

Put that "Device Section" back the way that it was.
Instead, add your own Vesa "Device Secton" for the vesa driver.
Like so,

Section "Device"
Identifier "Generic Vesa Graphics Driver"
Driver "vesa"
EndSection

And then, under the "Screen Section" comment out this line, like so:
#        Device          "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
and put in this one:
        Device          "Generic Vesa Graphics Driver"
Or whatever "Identifier" you feel like naming your Vesa "Device Section"

Any time you need to switch back and forth, just comment/uncomment the appropriate lines under the "Screen Section"

This may or may not fix your problem. The only real difference here from what you've already (effectively) done would be taking out the line:
BusID "PCI:1:0:0"

But, the point is, you don't want to mess up your NVIDIA driver section, and you don't need to. You can have multiple sections. What matters is each "Screen Section". Again, you can have multiple Sections for Screens. X is simply told which "Screen Section" to go with. And each Screen Section will only have one Identifier listed for each of the other sections.

~Tim

---

### Post by Justbill on 2006-04-18
So far so good!

I have the linux-2.6.16.7 kernel installed using this how to and it is working **GREAT!** Next..............the GeForce.

Talk to you at the other thread

Thanks again tseliot, these howto's are excellent, and a life saver!

Justbill

---

### Post by Justbill on 2006-04-18
Well, going to have to give this another try. The new kernel would only allow me to log in, and not the other three users in the house. So I had to start booting the old kernel again............if at first you don't succed...........try, try, try, try, try, try, try, try, try, try, try, try, try ,try, try, try, try, try, try, try, try, try, again!

Justbill

---

### Post by tseliot on 2006-04-19
[QUOTE=Justbill]Well, going to have to give this another try. The new kernel would only allow me to log in, and not the other three users in the house. So I had to start booting the old kernel again............if at first you don't succed...........try, try, try, try, try, try, try, try, try, try, try, try, try ,try, try, try, try, try, try, try, try, try, again!

Justbill[/QUOTE]
You're using Dapper. This guide is for Hoary.

The guide for Breezy should be good for you. 
[HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

Remeber NOT to "export CC".

---

### Post by Justbill on 2006-04-20
Well, still no luck.

I followed the "Breezy" how to and I have the same problem, my other users cannot log in.

I tried using linux-2.6.16.9.tar.bz2 from the vanilla kernels link, and when it installed it came up as 2.6.16.[COLOR="Red"]7[/COLOR]-custom. So I am not sure what I have done wrong here, I guess I'll give it another try later

Bill

---

### Post by krotaz on 2006-04-27
tseliot: great how to man. It really helped me a lot. 

But I've a little problem. I want to install the DRI drivers for my intel 830 chipset, and when it tries to compile it sends an error

"ERROR: kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on what went
wrotng"

The question here is. How do I install those kernel modules???

Hope you can help me-
Thanks!!

---

### Post by idea on 2006-04-27
Good idea!Kisses Ida

---

### Post by idea on 2006-04-27
Great guide!Bravo Alberto!Ida:p

---

### Post by krotaz on 2006-04-27
Well, I look at the dri.log file to see what's going on and I found this.


[B]make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/r300_cmdbuf.c r300_cmdbuf.c
+ ln -s ../shared-core/r300_reg.h r300_reg.h
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
+ ln -s ../shared-core/nv_drv.h nv_drv.h
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.12-krotaz/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
make[2]: *** No hay ninguna regla para construir el objetivo `card/i915-20060403-linux.i386/drm/linux-core'.  Alto.
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2
[/B]

Dont understand whats going on.

Plz help me.

---

### Post by tseliot on 2006-04-27
[QUOTE=idea]Great guide!Bravo Alberto!Ida:p[/QUOTE]
Grazie :D

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]tseliot: great how to man. It really helped me a lot. 

But I've a little problem. I want to install the DRI drivers for my intel 830 chipset, and when it tries to compile it sends an error

"ERROR: kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on what went
wrotng"

The question here is. How do I install those kernel modules???

Hope you can help me-
Thanks!![/QUOTE]
Ok, since I am an Nvidia user and I've never had an Intel card, could you explain me what you did (step by step)?

---

### Post by krotaz on 2006-04-28
well I used this guide

[http://www.frikis.org/staticpages/index.php/aceleracion-dri](http://www.frikis.org/staticpages/index.php/aceleracion-dri)

It's in spanish, don't know if you understand it but in few words says that I've to download the driver for my intel 830M chipset wichis supported by the driver provided by DRI in the i915 snapshot.

Then I put

sudo ./install.sh

1.-

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : i915
Description    : Intel i915 Driver
Architecture   :
Build Date     : 20060403
Kernel Module  : i915

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.

2.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will need to copy the DRI Xorg driver modules to
your Xorg directories.

The script will use the following Xorg directories:

Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

If this is correct press ENTER, press C to change or CTRL-C to exit.

3.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.12-krotaz
Module Directory : /lib/modules/2.6.12-krotaz

If this is correct press ENTER, press C to change or CTRL-C to exit.

4.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.

5.-

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

krotaz@calzonzin:~/software/video card/i915-20060403-linux.i386$


those are the 5 screens that the driver install show.

The DRI.log file is the one I posted before

Thanks

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]well I used this guide

[http://www.frikis.org/staticpages/index.php/aceleracion-dri](http://www.frikis.org/staticpages/index.php/aceleracion-dri)

It's in spanish, don't know if you understand it but in few words says that I've to download the driver for my intel 830M chipset wichis supported by the driver provided by DRI in the i915 snapshot.

Then I put

sudo ./install.sh

1.-

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : i915
Description    : Intel i915 Driver
Architecture   :
Build Date     : 20060403
Kernel Module  : i915

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.

2.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will need to copy the DRI Xorg driver modules to
your Xorg directories.

The script will use the following Xorg directories:

Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

If this is correct press ENTER, press C to change or CTRL-C to exit.

3.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.12-krotaz
Module Directory : /lib/modules/2.6.12-krotaz

If this is correct press ENTER, press C to change or CTRL-C to exit.

4.-
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.

5.-

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

krotaz@calzonzin:~/software/video card/i915-20060403-linux.i386$


those are the 5 screens that the driver install show.

The DRI.log file is the one I posted before

Thanks[/QUOTE]
Yo también hablo español como soy estudiante de lenguas extranjeras ;) 

Try to boot in the default Ubuntu kernel (select it in the grub menu) and run the script.

And tell me how it goes.

---

### Post by krotaz on 2006-04-28
q bueno q tambien hables español, pero dime en q idioma te acomodas mas para en ese escribir, de momento voy a asumir q prefieres en ingles 

Ok. I changed the kernel and try the script

after all the questions the same error. and also to check dri.log

the dri.log changed this time for this

Makefile: 173: *** Cannot find a kernel config file

Now I'm back to the other kernel because my wireless card is compiled for my new kernel

any other idea???

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]q bueno q tambien hables español, pero dime en q idioma te acomodas mas para en ese escribir, de momento voy a asumir q prefieres en ingles 

Ok. I changed the kernel and try the script

after all the questions the same error. and also to check dri.log

the dri.log changed this time for this

Makefile: 173: *** Cannot find a kernel config file

Now I'm back to the other kernel because my wireless card is compiled for my new kernel

any other idea???[/QUOTE]
Sí, mejor que hablemos en inglés, así que los demás nos entiendan.

Ok, you're back to your new kernel.
Try this:
```
cd /usr/src/linux-source*
```
Make a backup of the config file
```
sudo cp .config .tentativo
```
```
sudo make oldconfig
```

And try the script again

---

### Post by krotaz on 2006-04-28
I've done what you asked me to and the same error and suggestion to check the dri.log

the dri.log has the same message that in the first time

-------------------------------------

make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.12-krotaz/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
make[2]: *** No hay ninguna regla para construir el objetivo `card/i915-20060403-linux.i386/drm/linux-core'.  Alto.
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2
-------
](*,)

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]I've done what you asked me to and the same error and suggestion to check the dri.log

the dri.log has the same message that in the first time

-------------------------------------

make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.12-krotaz/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
make[2]: *** No hay ninguna regla para construir el objetivo `card/i915-20060403-linux.i386/drm/linux-core'.  Alto.
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/krotaz/software/video card/i915-20060403-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2
-------
](*,)[/QUOTE]
Restore the backup 
```
cd /usr/src/linux-source*
```
```
sudo cp .tentativo .config
```

1) can you post the output of:
cd /usr/src
ls
2) It looks like it works in Ubuntu Dapper without compiling (at least that's what I've read, I'm not sure though)

---

### Post by krotaz on 2006-04-28
```
krotaz@calzonzin:/usr/src/linux-source-2.6.12$ cd /usr/src/
krotaz@calzonzin:/usr/src$ ls
kernel-headers-2.6.12-krotaz                        linux-patches
kernel-headers-2.6.12-krotaz_10.00.Custom_i386.deb  linux-source-2.6.12
kernel-image-2.6.12-krotaz_10.00.Custom_i386.deb    linux-source-2.6.12.tar.bz2
linux

```

thats the output

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]```
krotaz@calzonzin:/usr/src/linux-source-2.6.12$ cd /usr/src/
krotaz@calzonzin:/usr/src$ ls
kernel-headers-2.6.12-krotaz                        linux-patches
kernel-headers-2.6.12-krotaz_10.00.Custom_i386.deb  linux-source-2.6.12
kernel-image-2.6.12-krotaz_10.00.Custom_i386.deb    linux-source-2.6.12.tar.bz2
linux

```

thats the output[/QUOTE]
Try this guide:
[http://www.ubuntuforums.org/showthread.php?t=75393&highlight=intel]("http://www.ubuntuforums.org/showthread.php?t=75393&highlight=intel")

That guide is for Savage cards therefore you need to replace this line:
```
wget http://dri.freedesktop.org/snapshots/archive/savage-20051125-linux.i386.tar.bz2
```

with this:
```
wget http://dri.freedesktop.org/snapshots/archive/i915-20060307-linux.i386.tar.bz2
```

---

### Post by krotaz on 2006-04-28
nop, still the same error and the same dri.log file.

I tryed the guide you told me and used the newest common and i915 but no luck.

](*,)

---

### Post by idea on 2006-04-28
[QUOTE=tseliot]Grazie :D[/QUOTE]
Prego!:p your friend Ida.

---

### Post by tseliot on 2006-04-28
[QUOTE=krotaz]nop, still the same error and the same dri.log file.

I tryed the guide you told me and used the newest common and i915 but no luck.

](*,)[/QUOTE]
Sorry pal I'm short of ideas. I think you might want to try Ubuntu Dapper as soon as it's released (as it should work as expected).

---

### Post by tseliot on 2006-04-28
[QUOTE=idea]Prego!:p your friend Ida.[/QUOTE]
Faccio il riduttivo e ti saluto. Ciao.

---

### Post by idea on 2006-04-28
](*,) Non te la prendere, scherzavo! kisses.See you soon.

---

### Post by tseliot on 2006-04-28
[QUOTE=idea]](*,) Non te la prendere, scherzavo! kisses.See you soon.[/QUOTE]
No offence taken ;) . See ya.

---

### Post by hellmet on 2006-05-07
do i have to download linux-source-2.6.11.tar.bz2 for this.??
Or is it included in the other packages you mentioned,
coz its  a  huge 35 MB file..

---

### Post by tseliot on 2006-05-07
[QUOTE=hellemt]do i have to download linux-source-2.6.11.tar.bz2 for this.??
Or is it included in the other packages you mentioned,
coz its  a  huge 35 MB file..[/QUOTE]
Yes, if you need to compile kernel 2.6.11 you need the source code (linux-source-2.6.11.tar.bz2)

---

### Post by tizzef on 2006-06-11
Thanks for this howto very educational :)

---

### Post by mooshie on 2006-06-13
Wow, great tutorial. I was doing things the old way (installing bzImage myself, creating an entry in menu.lst, etc) until I read this. Thanks for the liberation!

---

### Post by ububug on 2006-06-25
Ok, after i type in the command 'sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers", it does it's thing for a  while and then i get an error:

Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2

What is wrong? And is this enough information for anyone to determine a problem? If  not, let me know what else you need. BTW, just to let u know, i am a newbie at this.

---

### Post by TisTatos on 2006-08-21
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_header

This doesnt work for me... first of all it says -g is a invalid option and also that -a is an invalid option.. why is that?

---

### Post by emmanuelepig on 2006-08-29
hello,

thanks for the nice guide. did you ever try it on a macintosh ? i have an ibook G4 with ubuntu 6, when i boot on the new kernel, it goes into panic because it does not recognize the root partition. any ideas ?

                                     thank you
                                           emmanuele

---

### Post by Quintin Riis on 2006-10-19
Original Poster, re: changing xorg.conf: "restart the computer"

wtf?  This isn't Windows.  Ctrl+Alt+Bksp || sudo /etc/init.d/gdm restart

---

### Post by tseliot on 2006-10-20
> **Quintin Riis said:**
> Original Poster, re: changing xorg.conf: "restart the computer"

wtf?  This isn't Windows.  Ctrl+Alt+Bksp || sudo /etc/init.d/gdm restart

I know... but sometimes only a reboot does the trick.

---

### Post by starscalling on 2006-12-29
@tesliot awesome guide
i downgraded to breezy as im running a crap machine and i have disk access problems and softfreezes with edgy and i figured wth downgrade past dapper while i'm at it :P
currently conpiling 2.6.19.1 onto breezy :D i'm interested to see if i can get it working... using vanilla instruction set ^_~

---

### Post by NattyFido on 2007-02-12
Great guide.

But there is no mention of initrd.img! I tried compiling a new kernel and everything went well until I re-booted and got a 'Kernel panic' error.
What is initrd, does that need to be re-compiled as well and where can I get it?

---

### Post by Floppyjoe on 2007-02-12
Great Guide!

I compiled a 2.6.20 version kernel. My ethernet adapter and wireless adapter with ndiswrapper do not work with it. Is there something needed to get these working again. I tried to install ndiswrapper from the install disk but it still shows as following after ndiswrapper -v :
```
utils Error: no version specified!
driver modinfo: could not find module ndiswrapper
```
Further research revealed that the repository versions of ndiswrapper don't work with custom kernels.

Edit: Ok I installed the newest version of ndiswrapper so now wireless works but I still have the problem with the ethernet connection not working. Any suggestions?

regards,
Floppyjoe

---

### Post by grkravi on 2007-04-18
I too have this problem...i first upgraded my edgy kernel to stable  2.6.20.6 and then tried 2.6.20.7 from kernel.org and couldn surf.
My firewall firestarter keeps blocking my net connections but even if i quit the firewall, i am not able to surf.
I am able to ping my ip, localhost, gateway and even google (by enabling it id firewall) though.
Seems to be enhanced security feature in the new kernel.

---

### Post by lotacus on 2007-04-25
"Scroll down the text until you find (and highlight with the keyboard) “Enable DMA only for disks” and disable it by pressing N (now the “*” beside it should disappear, this means it is not selected any more)"


Why would you want to disable DMA for disks? I thought the purpose of DMA is to improve the disks  performance?

I type in the command: sudo hdparm -d /dev/sda (note SDA because the drive I use is SATA)
and the output shows: /dev/sda:

it doesn't tell me if it's on or off.

---

### Post by Super_6_4 on 2007-04-27
Thanks for rescuing me from compilation hell!! I'd been looking all day for some type of guide that actually worked. I actually used the procedure for Feisty - but it still seemed to work. GREAT TUTORIAL!!

---

### Post by Dinchamion on 2007-06-23
Excellent guide, thank you! :KS

It still amazes me how easy can stuff be in Ubuntu.

Edit: ok, I have a problem. :/

>   AS      arch/x86_64/lib/putuser.o
  AS      arch/x86_64/lib/rwlock.o
  AS      arch/x86_64/lib/thunk.o
  CC      arch/x86_64/lib/usercopy.o
  AR      arch/x86_64/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
dnsdomainname: Unknown host
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
ubuntu/built-in.o:(.bss+0x10588): multiple definition of `debug'
arch/x86_64/kernel/built-in.o:(.kprobes.text+0x3d0): first defined here
ld: Warning: size of symbol `debug' changed from 333 in arch/x86_64/kernel/built-in.o to 4 in ubuntu/built-in.o
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

I tried everything I could possibly think of (even completely disabling every bit in the kernel that said "debug", just for trying), but now I'm clueless. As you can see, I'm using 64 bit architecture, Feisty and 2.6.20 kernel. I followed every step of the guide, and of course the unique modifications to my system. What I'm gonna try now is copying the old config file and compiling from that - however, in case that won't work (I suspect it won't) can I get some advice about where to go?

---

### Post by ChaiTan on 2007-06-28
I upgraded my kernel from 2.6.17-10 to 2.6.21.5
using edgy eft
the kernel compiled fine
rebooted the computer and after choosing the new kernel option, ubuntu got stuck at the loading screen
while loading ubuntu with the new kernel in recovery mode 
the loading stops at
[some no.] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
why does it get stuck??

---

### Post by sacater on 2007-07-08
hey, I have been told to include everything into the kernel, (*) and not as modules (M) as it runs faster, is that true?

---

### Post by benkong2 on 2007-08-23
This is a great guide. However I had a problem with missing /li/modules/firmware for the custom kernel and it would not boot. What did I do wrong. The exact error is
modprobe FATAL Could not load /lib/modules/2.6.22.4benjamin/modules.dep. No such file or directory. And it just hangs there

---

### Post by waxyfresh on 2007-09-11
sudo apt-get install linux-tree
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-tree

all repos enabled and a fresh list from source-o-matic.

also im useing a ati radeom 200m and it wont let me boot under vesa any ideas?

---

### Post by vixensjlin on 2007-09-20
I followed the howto and successfully compile my working kernel.  However, when I want to install nVidia driver, the restricted driver manager report:"You need to install the package linux-restricted-modules-2.6.22.6-jack for this program to work"and refused to install nVidia driver, .  Could anybody tell me how to do this?  Thanks a lot!


#/usr/src$ ls -F
linux@
linux-headers-2.6.22-10/
linux-headers-2.6.22-10-generic/
linux-headers-2.6.22-11/
linux-headers-2.6.22-11-generic/
linux-headers-2.6.22.6-jack/
linux-headers-2.6.22.6-jack_2.6.22.6-jack-10.00.Custom_i386.deb
linux-image-2.6.22.6-jack_2.6.22.6-jack-10.00.Custom_i386.deb
linux-source-2.6.22-11/
linux-source-2.6.22.tar.bz2

#/lib/modules$ ls -F
2.6.22-10-generic/
2.6.22-11-generic/
2.6.22.6-jack/

---

### Post by TuxWarrior on 2007-09-24
my /etc/X11/xorg.conf has this::

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

i.e i am using Intel on-board graphics card
so, do i still change this i810 to vesa ??

Also, i have just 256 MB RAM, so do i need to enable high memory support ?

i am also confused about the DMA setup, shud i enable/disable it ??

---

### Post by abhi.datt on 2007-10-01
Thanks, excellent howto. 
Just to add a bit. For those of who want to support  multi processor and dual core processors (like xeon) based systems , please also select the Processor type & features > Processor family > Core2 /newer Xeon
from the options in menuconfig. (besides of course selecting the 64GB memory support, if your sytem  has something like 6GB or ++

---

### Post by master_kernel on 2007-10-01
> **TuxWarrior said:**
> my /etc/X11/xorg.conf has this::

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

i.e i am using Intel on-board graphics card
so, do i still change this i810 to vesa ??

Also, i have just 256 MB RAM, so do i need to enable high memory support ?

i am also confused about the DMA setup, shud i enable/disable it ??

You don't have to change it to vesa, you don't need high memory support, and you should leave DMA at the default.

---

### Post by Yarbo on 2007-10-23
I am new to Ubuntu, but i've decided to try and compile my own vanilla kernel from kernel.org.  I am using gutsy gibbon while doing this, and everything works fun until I run the following:

```
ln -s /usr/src/linux-source-2.6.10 /usr/src/linux
cd /usr/src/linux
```

It seems to work, and if I use 'dir' it shows linux as being there, but when I try to "cd /usr/src/linux" I get:  bash: cd: linux: No such file or directory.


I am not sure why.

---

### Post by eyemou on 2007-10-23
Just a quick question - before I compile a new kernel, I was wondering: is there was an easy way to see how the current, stock (K)Ubuntu kernel was set-up (what modules, etc.)?

That would be both interesting and potentially useful.

*Edit: Oops. I think I answered my own question - it looks as if you can view your present configuration when performing configuration of the new kernel, if I'm reading this correctly: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)*

---

### Post by HarkTheSoundofTHV on 2007-12-02
i'm no expert. i've been dabbling in this compiling for a few days but what you reference is the config file your kernel is currently operating on. While if your current istallation works then your config file will reflect this but also includes unneded components, like amatuer radio modules.

---

### Post by Roddles on 2007-12-23
> **waxyfresh said:**
> sudo apt-get install linux-tree
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-tree

all repos enabled and a fresh list from source-o-matic.

also im useing a ati radeom 200m and it wont let me boot under vesa any ideas?

I have exactly the same problem.  Cant find linux-tree.

Is there another package that replaces this now?

Any assistance would be greatly appreciated

Cheers

Rod.


Just an update - I did some googling and found that the linux-tree package is now the linux-source-(version) package.

So there is no linux-tree anymore.

[http://ubuntuforums.org/archive/index.php/t-499015.html](http://ubuntuforums.org/archive/index.php/t-499015.html)

Cheers

Rod.

---

### Post by ewomer on 2008-01-26
i have a problem i get these errors with the vanilla kernel from kernel.org
i dont know if this is a real issue or not but im just worried ill get a broken system because of this. is there any way to fix this



ubuntu:~/src/linux-2.6.24-git$ make xconfig  
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  CHECK   qt
  HOSTCC  scripts/kconfig/conf.o
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
/usr/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
scripts/kconfig/qconf arch/x86/Kconfig
#
# using defaults found in /boot/config-2.6.24-5-generic
#
/boot/config-2.6.24-5-generic:34:warning: trying to assign nonexistent symbol ACPI_CUSTOM_DSDT_INITRD
/boot/config-2.6.24-5-generic:431:warning: trying to assign nonexistent symbol CRYPTO_ABLKCIPHER
/boot/config-2.6.24-5-generic:795:warning: symbol value 'm' invalid for FB_VESA
/boot/config-2.6.24-5-generic:967:warning: trying to assign nonexistent symbol HW_RANDOM_VIRTIO
/boot/config-2.6.24-5-generic:1031:warning: trying to assign nonexistent symbol IDEPCI_SHARE_IRQ
/boot/config-2.6.24-5-generic:1513:warning: trying to assign nonexistent symbol MSS
/boot/config-2.6.24-5-generic:2002:warning: trying to assign nonexistent symbol PM_DISABLE_CONSOLE
/boot/config-2.6.24-5-generic:2244:warning: trying to assign nonexistent symbol SECURITY_APPARMOR
/boot/config-2.6.24-5-generic:2245:warning: trying to assign nonexistent symbol SECURITY_APPARMOR_BOOTPARAM_VALUE
/boot/config-2.6.24-5-generic:2246:warning: trying to assign nonexistent symbol SECURITY_APPARMOR_DISABLE
/boot/config-2.6.24-5-generic:2949:warning: trying to assign nonexistent symbol VIDEO_PVRUSB2_24XXX
/boot/config-2.6.24-5-generic:2950:warning: trying to assign nonexistent symbol VIDEO_PVRUSB2_29XXX
/boot/config-2.6.24-5-generic:2964:warning: trying to assign nonexistent symbol VIDEO_SAA7134_OSS
/boot/config-2.6.24-5-generic:3007:warning: trying to assign nonexistent symbol VIRTIO_PCI
/boot/config-2.6.24-5-generic:3049:warning: trying to assign nonexistent symbol WRAPPER_PRINT
/boot/config-2.6.24-5-generic:3129:warning: trying to assign nonexistent symbol PREEMPT_BKL
/boot/config-2.6.24-5-generic:3133:warning: trying to assign nonexistent symbol VERSION_SIGNATURE
/boot/config-2.6.24-5-generic:34:warning: trying to assign nonexistent symbol ACPI_CUSTOM_DSDT_INITRD
/boot/config-2.6.24-5-generic:431:warning: trying to assign nonexistent symbol CRYPTO_ABLKCIPHER
/boot/config-2.6.24-5-generic:795:warning: symbol value 'm' invalid for FB_VESA
/boot/config-2.6.24-5-generic:967:warning: trying to assign nonexistent symbol HW_RANDOM_VIRTIO
/boot/config-2.6.24-5-generic:1031:warning: trying to assign nonexistent symbol IDEPCI_SHARE_IRQ
/boot/config-2.6.24-5-generic:1513:warning: trying to assign nonexistent symbol MSS
/boot/config-2.6.24-5-generic:2002:warning: trying to assign nonexistent symbol PM_DISABLE_CONSOLE
/boot/config-2.6.24-5-generic:2244:warning: trying to assign nonexistent symbol SECURITY_APPARMOR
/boot/config-2.6.24-5-generic:2245:warning: trying to assign nonexistent symbol SECURITY_APPARMOR_BOOTPARAM_VALUE
/boot/config-2.6.24-5-generic:2246:warning: trying to assign nonexistent symbol SECURITY_APPARMOR_DISABLE
/boot/config-2.6.24-5-generic:2949:warning: trying to assign nonexistent symbol VIDEO_PVRUSB2_24XXX
/boot/config-2.6.24-5-generic:2950:warning: trying to assign nonexistent symbol VIDEO_PVRUSB2_29XXX
/boot/config-2.6.24-5-generic:2964:warning: trying to assign nonexistent symbol VIDEO_SAA7134_OSS
/boot/config-2.6.24-5-generic:3007:warning: trying to assign nonexistent symbol VIRTIO_PCI
/boot/config-2.6.24-5-generic:3049:warning: trying to assign nonexistent symbol WRAPPER_PRINT
/boot/config-2.6.24-5-generic:3129:warning: trying to assign nonexistent symbol PREEMPT_BKL
/boot/config-2.6.24-5-generic:3133:warning: trying to assign nonexistent symbol VERSION_SIGNATURE
#
# configuration written to .config
#

---

### Post by fabiopaolini on 2008-02-21
Please, when I try to compile a kernel following the  procedure 
of the "How to kernel compilation ..."  there are the error message:

"dpkg-parsechangelog: error: format /usr/lib/dpkg/parsechangelog/debian unknown"

after I press the command: "make-kpkg clean" 

And after the command:

"make-kpkg --initrd –append-to-version=-alberto kernel_image kernel_headers"

The files .deb don't appear in "/usr/src"
Someone could help me?
Thanks.

---

### Post by JonNicc on 2008-02-25
Thank you very much for this post, tseliot! With your info & the info from luca_linux, you were right! It was a piece of cake...with your help! Now, my Gutsy has the most up-to-date kernel, and flies like a Concorde @ 4,000 meters! Have a double shot cappuccino, amico. You and luca-linux both deserve one. I'll donate the cost of 'em to Ubuntu.

---

### Post by NEKOKONEKO on 2008-06-15
It says Kunde inte hitta paketet linux-tree in english can't find package linux tree. What shuld i do ?

---

### Post by tseliot on 2008-07-21
> **NEKOKONEKO said:**
> It says Kunde inte hitta paketet linux-tree in english can't find package linux tree. What shuld i do ?

try with linux-source.

---

### Post by Angus77 on 2008-07-28
Since moving to Hardy, in my /etc/X11/xorg.conf I have:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

I have and ATI Radeon X1300 video card running with the proprietary drivers.  Should I leave this as it is or should I add the stuff about the "vesa" driver?

Nice guide, btw.  I'm compiling the kernel right now (and so may be answering my own question!)

---

### Post by Angus77 on 2008-07-28
It appears that it's okay to leave it as is.  I'm running my freshly-compiled kernel right now!

---

### Post by &gt;.3 on 2008-08-12
I accidentally closed the terminal while compiling. Do i really have to start all over again?

Apologies for the absolute newbness.

---

### Post by nick_h on 2008-08-12
> Do i really have to start all over again?
Not from the very beginning.  You will need to re-run the command that you cancelled.

---

### Post by eeeandrew on 2008-09-23
Hi all, I realise this is an older thread now but I was hoping someone would be able to answer a nagging question I have about compiling a kernel.

Why would you do it?

No disrespect to all the hard work that went into this tutorial but I seem to have missed the point. In what situation would it be better to create your own kernel rather than download one that people have spent months developing?

Any info would be appreciated, thanks,
Andrew

PS. I bet your all doing this: ](*,) now

---

### Post by DagMan on 2008-09-24
Primarily just in the event that there was hardware support in a newer kernel, for something that doesn't work with the current kernel.

Other reasons might be to apply a patch that you think might give you a performance increase or again, for unsupported hardware.
 
Some people also want to select kernel options that are specific to their processor as the generic kernel is one size to fit all and they feel it might be faster to have something specifically selected at compile time.

The other reason I can think of would be to remove hardware support for things that aren't being used.  The Ubuntu kernel tries to autodetect hardware and for the most part just load the parts that are needed and it does a very good job at it, but cutting down to nothing more than what you need can reduce your boot time.  It might free up a little memory as well but I'm really not sure about that, maybe not.  

It is good to know how to apply a patch and compile a kernel for when you do need it.

---

### Post by go_beep_yourself on 2008-10-13
Does anybody have benchmark results or know how to make benchmarks in Ubuntu to compare the performance difference of a stock Ubuntu kernel with a custom configured kernel?

---

### Post by Werderx on 2008-11-11
Hey tseliot,
   Newb here.  I replaced what i had in my xorg.conf file with mesa (it use to be fglrx), and then rebooted my computer.... which failed.  It took me about 2 hours of trying to remember commands to get it fixed in recovery mode.  Luckily I wrote down what it said before I changed it to mesa.  I see that the user NEKOKONEKO had this same issue and changed it to ati instead of mesa which seemed to work... I'm getting ready to try that again now that i have my computer back up. LOL

Anyways, can you add that part into the guide so others done make the same mistake i did?... or maybe it's there and i dont see it.. hehe as i said, newb here. :)

BTW, i'm running ATI Radeon HD 3650.  

I also saw someone else say that they put "radeon" and it works as well.

Well.. here goes nothing... again. Lol :p

PS: DING 1!!!!! :D

---

### Post by Werderx on 2008-11-11
OK so that didn't work..

I changed the xorg.conf file to say ati with no luck.  I then tried radeon and nothing.

Currently it says:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"

I could have sworn that "Identifier" use to say ATI somthing or other.
I also have another file called xorg.conf~.  So just in case i changed both of them to say the same stuff, but nothing... 

i'll try and do this without editing the file and see what happens... tomorrow hehe

---

### Post by masaki on 2008-11-11
Hi all!

I'm trying to build the kernel 2.6.27 to lighten it for use Ubuntu on my ThinkPad x20 laptop (PIII, 320Mb RAM). Now it's working a bit slow...

I've read lots of howtos, and that's the way I could succesfully compile the sources from kernel.org:

```
cd /usr/src
tar -jxvf linux-source-2.6.27.tar.bz2
cd linux-source.2.6.27
make menuconfig
make-kpkg clean
make-kpkg --initrd --revision=x20 kernel_image
```

Everything is good, but I have a pcmcia WiFi adapter that runs only with ndiswrapper, which disappears in compiled kernel ('module not found' when I'm doing modprobe ndiswrapper).

Then I've tried to config and build kernel source from Ubuntu repos, but it won't compile anyway.
For now it looks so:

```
  LD      arch/x86/vdso/built-in.o
  LD      vmlinux.o
ubuntu/built-in.o:(.bss+0x2ec): multiple definition of `debug'
arch/x86/kernel/built-in.o:(.kprobes.text+0x78): first defined here
ld: Warning: size of symbol `debug' changed from 76 in arch/x86/kernel/built-in.o to 4 in ubuntu/built-in.o
make[1]: *** [vmlinux.o] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [debian/stamp-build-kernel] Error 2

```

So, what can I do with this?

---

### Post by Werderx on 2008-11-16
Ok... So When i finally got the kernel to compile, I ran out of room on the /usr partition LOL. ahhhh the insanity.

I got a white screen when i tried to run gparted  v. 0.3.9-4, so i just reformatted. :/  No real biggie since I'm not putting anything of importance on my linux HDD until I'm close to being a guru lol.  This time when I reformatted, I made the /usr partition 70 gigs (another lesson learned) hehe.

Between this forum and another one at [http://ubuntuforums.org/showthread.php?t=311158&highlight=patch-2.6.27.5.bz2]("http://ubuntuforums.org/showthread.php?t=311158&highlight=patch-2.6.27.5.bz2"), I was able to get my kernel updated from 2.6.24 to 2.6.27... However, after rebooting, I got a white screen and no sound. LOL 

So I'm back to 2.6.24.  I'll just chill with what I have after a week of wrestling with this. LOL
I learned a lot though and this guide was great! Thanks again!:)

---

### Post by newbee70 on 2008-11-23
What am I doing wrong here.

I am trying to compile 2.6.27.7 and am running into fun results.


3)Open Terminal or Konsole (if it's not open yet) and type these commands:

Code:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package

<<<<<do I need this in step 3 and if so what do I put here the bz2 filename>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


NOTE: HOWTO compile from a vanilla kernel from kernel.org

If you want to compile from a vanilla kernel from kernel.org something need to be changed in my guide:

Skip point 2
You have to download it from [www.kernel.org](www.kernel.org) (try the latest stable kernel source)

When you get to Point 3 of the guide and you get to the following lines you have to modify them in this way:

cd /home/your_username_folder/directory_where_you_put_the_downloaded_kernel (instead of cd /usr/src) (e.g. "cd /home/alberto/download" in my case)
sudo tar --bzip2 -xvf linux-source-2.6.10.tar.bz2 /usr/src (use the name of the file you downloaded)
sudo ln -s /usr/src/linux-source-2.6.10 /usr/src/linux (use the name of the file you downloaded)
cd /usr/src/linux


<<<<<<<<<<<<<<<<And what is causing me this headache?>>>>>>>>>>>>>>>>

ghost@topper:~/Desktop/1$ ls   directory where I stored the download
linux-2.6.27.7.tar.bz2         the download does exist there
ghost@topper:~/Desktop/1$ cd /usr/src  checked that directory exists
ghost@topper:/usr/src$ cd ~
ghost@topper:~$ cd Desktop/1   moved back to directory
ghost@topper:~/Desktop/1$ sudo tar --bzip2 -xvf linux-2.6.27.7.tar.bz2 /usr/src linux-2.6.27.7.tar.bz2

it took about 2 minutes before it came back with this information

tar: /usr/src: Not found in archive
tar: linux-2.6.27.7.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
ghost@topper:~/Desktop/1$ 


any and all help will be appreciated... and yes I am a Nooob 2.

---

### Post by DagMan on 2008-11-24
[B]sudo tar -xvf linux-2.6.27.7.tar.bz2 -C /usr/src 

[/B]
You don't need to add --bzip2 with tar anymore whlinux-source-2.6.27en its data coming from a file.  If it had that type of compression coming over a network or another stream then it would be needed

the -C switch says to unpack it into a specific directory, in this case /usr/src which I assume you want.  You'd want to then
**cd /usr/src**

And I think the next part is in the guide...
[B]rm linux
ln -s linux-source-2.6.27 linux[/B]
except in the above line you'de substitute linux-source-2.6.27 for whatever the name of the source is.  If you got it from ubuntu then it would be linux-source-2.6.27 but from kernel.org or elsewhere it might be differant.
It should be clearer, if you get this far, where to pick back up from the guide.

If you don't want to build in /usr/src then you can specify another location after the **-C** switch in the first line, but it's the recommended place.




> **masaki said:**
> Hi all!

I'm trying to build the kernel 2.6.27 to lighten it for use Ubuntu on my ThinkPad x20 laptop (PIII, 320Mb RAM). Now it's working a bit slow...

I've read lots of howtos, and that's the way I could succesfully compile the sources from kernel.org:

```
cd /usr/src
tar -jxvf linux-source-2.6.27.tar.bz2
cd linux-source.2.6.27
make menuconfig
make-kpkg clean
make-kpkg --initrd --revision=x20 kernel_image
```

Everything is good, but I have a pcmcia WiFi adapter that runs only with ndiswrapper, which disappears in compiled kernel ('module not found' when I'm doing modprobe ndiswrapper).

Then I've tried to config and build kernel source from Ubuntu repos, but it won't compile anyway.
For now it looks so:

```
  LD      arch/x86/vdso/built-in.o
  LD      vmlinux.o
ubuntu/built-in.o:(.bss+0x2ec): multiple definition of `debug'
arch/x86/kernel/built-in.o:(.kprobes.text+0x78): first defined here
ld: Warning: size of symbol `debug' changed from 76 in arch/x86/kernel/built-in.o to 4 in ubuntu/built-in.o
make[1]: *** [vmlinux.o] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [debian/stamp-build-kernel] Error 2

```

So, what can I do with this?
If your problem is that you build and still aren't getting ndiswrapper, then it needs to be enabled in menuconfig.  I don't know where its located.
If your problem is that you've enabled it but your build is stopping in that error, then from the looks of the error, try going down into, at menuconfig, the kernel hacking section and turning off kernel debugging.  Look at the help within menuconfig for the things that are enabled in the kernel hacking section.  I can't be any more specific, but there are a couple of things that aren't needed in there, I've already disabled them and don't have a referance to look at but the help section should point the way.

Whenever I try to build a really small kernel, I plug in as many devices as I can, connect to the internet, start up my prefered firewall... do everything that will load modules that I might need after a compile, then run this script [http://lkml.indiana.edu/hypermail/linux/kernel/0503.1/1248.html](http://lkml.indiana.edu/hypermail/linux/kernel/0503.1/1248.html) and direct the output to .config
I end up having to recompile to enable things that were stripped out and I didn't think about before compiling, but on the positive side I'm not removing unwanted modules.

---

### Post by newbee70 on 2008-11-28
[QUOTE=DagMan;6241301][B]sudo tar -xvf linux-2.6.27.7.tar.bz2 -C /usr/src 

[/B]
You don't need to add --bzip2 with tar anymore whlinux-source-2.6.27en its data coming from a file.  If it had that type of compression coming over a network or another stream then it would be needed

the -C switch says to unpack it into a specific directory, in this case /usr/src which I assume you want.  You'd want to then
**cd /usr/src**

And I think the next part is in the guide...
[B]rm linux
ln -s linux-source-2.6.27 linux[/B]
except in the above line you'de substitute linux-source-2.6.27 for whatever the name of the source is.  If you got it from ubuntu then it would be linux-source-2.6.27 but from kernel.org or elsewhere it might be differant.
It should be clearer, if you get this far, where to pick back up from the guide.

If you don't want to build in /usr/src then you can specify another location after the **-C** switch in the first line, but it's the recommended place.


If this was for me thanks it got me through that part, now I have a problem with make oldconfig that I have to research.

so you'll probably hear me pulling my hair out for a few days.

**But again thank's for the assist.**   :)

---

### Post by RoundSparrow on 2008-11-30
I'm trying to build kernel on recently updated Ubuntu 8.10.

I get this problem:

```

# sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for linux-ubuntu-modules-2.6.27-9-generic

```

Any ideas?d

---

### Post by DagMan on 2008-12-02
It doesn't look like linux-ubuntu-modules are still part of the repos. I think they're all in the section where it says Ubuntu patches or something like that when you're in menuconfg.  If you have a device that is no longer supported on a custom build of the 2.6.27 kernel and you got the kernel from ubuntu software sources and not kernel.org or elsewhere, then you're probably looking to build the ubuntu-backport-modules or possibly there's a particular package that needs to be reinstalled so the kernel module is rebuilt for the kernel you built.

What's the hardware device that you need support for btw?

---

### Post by connexion2503 on 2008-12-04
I'm using Ubuntu 8.1 and trying to compile kernel 2.6.18 for a study reason. I use 'make xconfig' to make the configuration. However I don't know which processor family that Intel Core 2 Duo belongs to. Thus I chose Intel Pentium 4 family. When I compiled kernel with this configuration, I got this problem:
> make[1]: Entering directory `/usr/src/linux-2.6.18'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/mod/sumversion.o
scripts/mod/sumversion.c: In function ‘get_src_version’:
scripts/mod/sumversion.c:384: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/mod/sumversion.c:384: error: (Each undeclared identifier is reported only once
scripts/mod/sumversion.c:384: error: for each function it appears in.)
scripts/mod/sumversion.c:384: warning: unused variable ‘filelist’
make[3]: *** [scripts/mod/sumversion.o] Error 1
make[2]: *** [scripts/mod] Error 2
make[1]: *** [scripts] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [debian/stamp-build-kernel] Error 2

Did I have a mistake in configuration? If not what is the reason?

---

### Post by FerociousTwig on 2008-12-30
Yeah I'm having some wireless card issues with my new kernel too, trying to work em out though. I'll post more info/details if I can't figure it out soon.

Thanks for the great guide.

---

### Post by cb34 on 2009-01-11
hi, really great guide, but i need some help please.

i want to recompile my kernel and remove all the cpu thermal control, and acpi and anything to do with that.

i run a prescott chip, and it is naturally very hot, i have the uguru Abit board, and i have full control of the temps and fans from there, it is totally normal for my chip to run at 70-75 under heavy load, and if it blows up, hehe, i dont really care, ive had this chip for soo long, so the issue is, i have these thermal warnings in my kern and sys logs and i dont even think my cpu supports thermal/frequency throttling and i dont want the kernel to control any aspect of this. it's causing me many shutdowns, when the kernel thinks its a dangerous temp, and i know it is not.

also, when it tries to throttle the cpu, i read the reason it crashes my system is because either my cpu doesn't support it, or the way in which it tries to send the workload to the other cpu for a second.. but its HT, not real core2 duo.. and the system jams.. or when trying to cut the power by half to the chip, it can't, and jams the system.. my motherboard has a seperate uGuru chip on it that controls all that stuff.. anywayz..

i downloaded the source from the repo, untared it, and i tried to use the program -make xconfig-, and i do find thermal stuff(did a search for thermal, found what i think it is i need to change), my question is, i untick those few thermal things, then save the config. then what.

how do i recompile my current kernel with that new config.

also.. when i open the linux source with make-xconfig, are all the settings i see my current settings, or am i looking at a fresh config and i need to set EVERYTHING properly in the kernel??
hope you know what i mean.

Thanks for any help.. i really need to get rid of these thermal modules in the kernel.

and i found all these thermal modules lookin at lsmod, modprobe -r them, but the thermal warnings are still there, and tried acpi=off(but then nvidia driver wouldn't load up, even after reinstalling the nvidia module), and during the nvidia reinstall, with the thermal modules unloaded, i still got the thermal warnings, so it is inside the kernel that i need to tweak..

sorry for the long winded post, just wanted to try and get all the details on what im tryin to do out., and what i've tried so far.

and i definitely do want to disable the thermal stuff in the kernel, i know what im doing in that respect.

Thank you.

edit-> just to show the warning im talkin about.. that eventually lock my machine...

CPU1: Temperature above threshold, cpu clock throttled (total events = 1820)
CPU0: Temperature above threshold, cpu clock throttled (total events = 1820)

and i'm pretty sure it's the thermal control module/s in the kernel that's crashing my machine, and not the high temp itself.. i mean..  there's no high temp condition that needs to be addressed if that's what you're thinking, that's just how my p4prescott runs, and how it alwayz ran.

---

### Post by aklilom on 2009-02-26
Thanks a lot! a nice guide.

---

### Post by itsjareds on 2009-07-23
Thanks! Worked great for me to enable CONFIG_MODULE_FORCE_UNLOAD. I did reach this error, however, when installing the linux-image package, and I used the fix from [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795") to work around it:

```
sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common
```

All went smoothly after that.

Quick question: What files are OK to clean up after I've finished compiling? I still have 4.5GB of /usr/src/linux-source-* and 3 .deb packages, and I'd like to remove them. I also assume that it's ok to remove the link /usr/src/linux?

---

### Post by Mickeysofine1972 on 2009-08-07
Hi

Does this work for Intel based video too?

Mike

---

### Post by vishwaba on 2009-10-07
UBUNTU 8.10 default kernel comes with symbol versioning enabled. I want to disable kernel symbol version and build standard kernel. Anybody know how to disable kernel symbol versioning ?

---

### Post by kevinguillorytraining on 2009-10-07
Nice guide. Thanks for posting

---

### Post by kevinguillorytraining on 2009-10-10
Good Job. Thanks for a nice tutorial

---

### Post by SuperMetroid on 2009-11-02
I followed this guide, but when I went to install the kernel, I got a dkpg-related error:

Command:
```

$ sudo dpkg -i linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb

```Response:
```

Selecting previously deselected package linux-headers-2.6.31.4-xxxx.
(Reading database ... 201129 files and directories currently installed.)
Unpacking linux-headers-2.6.31.4-xxxx (from linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb) ...

Setting up linux-headers-2.6.31.4-xxxx (2.6.31.4-xxxx-10.00.Custom) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

```Command #2:
```

$ sudo dpkg -i linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb

```Response:
```

(Reading database ... 212420 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31.4-xxxx 2.6.31.4-xxxx-10.00.Custom (using linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.31.4-xxxx ...
Setting up linux-headers-2.6.31.4-xxxx (2.6.31.4-xxxx-10.00.Custom) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

```I think it's a bug, but I don't understand how to fix it.

Here is a page mentioning fixes (though I don't understand how to use this to my advantage): 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/403316](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/403316)

Can anyone help?

---

### Post by timhalo on 2009-11-22
@SuperMetroid, I got the "'--print-architecture' instead." message as well. Don't remember what else the printout said but I remember that line. I just went ahead and booted to the new kernel anyways. No problems so far. But then I only need it for 1 specific task.

@All, I read this entire thread and my problem is solved....so Thanks. I think I got back 400 megs of ram.

So now my question is....can I safely remove all this inside /usr/src/?:
linux -> /usr/src/linux-source-2.6.31/
linux-headers-2.6.31-14/
linux-headers-2.6.31-14-generic/
linux-headers-2.6.31.4-custom20091121/
linux-headers-2.6.31.4-custom20091121_2.6.31.4-custom20091121-10.00.Custom_amd64.deb
linux-image-2.6.31.4-custom20091121_2.6.31.4-custom20091121-10.00.Custom_amd64.deb
linux-source-2.6.31/
linux-source-2.6.31.tar.bz2

But, if I should want to compile another kernel, I can keep the link and linux-source-2.6.31/ or should I get rid of all, and just untar the source again?

Thanks.

---

### Post by Wulfeous on 2010-03-28
> **SuperMetroid said:**
> I followed this guide, but when I went to install the kernel, I got a dkpg-related error:

Command:
```

$ sudo dpkg -i linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb

```Response:
```

Selecting previously deselected package linux-headers-2.6.31.4-xxxx.
(Reading database ... 201129 files and directories currently installed.)
Unpacking linux-headers-2.6.31.4-xxxx (from linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb) ...

Setting up linux-headers-2.6.31.4-xxxx (2.6.31.4-xxxx-10.00.Custom) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

```Command #2:
```

$ sudo dpkg -i linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb

```Response:
```

(Reading database ... 212420 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31.4-xxxx 2.6.31.4-xxxx-10.00.Custom (using linux-headers-2.6.31.4-xxxx_2.6.31.4-xxxx-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.31.4-xxxx ...
Setting up linux-headers-2.6.31.4-xxxx (2.6.31.4-xxxx-10.00.Custom) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

```I think it's a bug, but I don't understand how to fix it.

Here is a page mentioning fixes (though I don't understand how to use this to my advantage): 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/403316](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/403316)

Can anyone help?

Wish I could find an answer to this :(
I have no idea where to change --print-installation-architecture to --print-architecture

---

### Post by Mark_in_Hollywood on 2010-05-22
Quoted material in RED color.

From page 1 of this HOWTO I read:

[COLOR="Red"]Scroll down the text until you find this section (this is my configuration):

Code:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
Substitute the word in red with “vesa”, make it look like this:
Code:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"vesa"
	BusID		"PCI:1:5:0"[/COLOR]

my xorg.conf (LUCID LYNX) reads:

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

every word in this xorg.conf is NOT in color. Do I have to change the line:

Driver "nvidia" to "vesa" like yours? 

I know it would be asking a week's work, but could you write an updated HOWTO on this subject?

---

### Post by new_bember on 2010-05-23
main thing is that after installing new kernel (vanilla kernel)* your proprietary drivers will unable to start.. so you just prevent yourself from unstarted X. If you`re useing 10.04 then seems right option to change `nvidia` in your xorg.conf to `nouveau` or to `vesa`.

As for me, my nvidia-current driver works after rebuilding current kernel version.

---

### Post by godspeedmav on 2010-08-02
if i were to compile the kernel and apply a patch to it, how should i do it?
this is the *.txt file of the patch that i've to apply to Linux 2.6.35-rc6
i've gotten to the no.6 step as in the guide:

> 6)After the (long) process type this in the command line (Terminal or Konsole)

 	Code:
 	cd /usr/src ls 
You'll see a list of the names of the files in the folder as well  as the names of your new kernel image and kernel headers; they should  look (approximately)like the following:

	kernel-image-2.6.10-custom_10.00.Custom_i386.deb
	kernel-headers-2.6.10-custom_10.00.Custom_i386.deb

could you please guide me?
thanks in advance.

---

### Post by ChaVinee on 2011-06-08
Hey,
the whole process went fine till

kernel-image-2.6.10-custom_10.00.Custom_i386.deb
kernel-headers-2.6.10-custom_10.00.Custom_i386.deb

these files were not build in the /usr/src folder as you suggested they would. 

Help me,....what should I do next?

---

### Post by emperorpsf on 2012-04-03
This is works but... dont create initrd and i have kernel panic ;)
I must manually create initrd by command
```
sudo update-initramfs -c -k 3.3.1
```
and after this operation i run
```
sudo update-grub
```
and now new kernel work ok.

---

### Post by BStrizzy on 2013-03-04
can someone please explain what kernel compilation is? I am interested in looking at the source of ubuntu (kernel) but now sure what the comopilation part is. 

check out my thread [http://ubuntuforums.org/showthread.php?t=2122292](http://ubuntuforums.org/showthread.php?t=2122292)

---

