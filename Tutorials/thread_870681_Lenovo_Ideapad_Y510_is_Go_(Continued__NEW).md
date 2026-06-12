---
title: "Lenovo Ideapad Y510 is Go (Continued / NEW)"
date: 2008-07-26
forum: Tutorials
---

### Post by HunterThomson on 2008-07-26
This is a Thread to continue the "Lenovo Ideapad Y510 is GO by wyth" do to the fact that the thread is now "Read Only"

[http://ubuntuforums.org/showthread.php?t=687663](http://ubuntuforums.org/showthread.php?t=687663)


I am happy to see that both Google and Ubuntuforums are showing this thread is search results. The fact that wyth's thread was so good was a major reson I got this laptop. I didn't want to see the tread die. I hope this tread takes over were wyth's thead ended. Whith all the GUN community spirit & development. Keeping all the fixes & info related to the Lenovo Ideapad in one place.

Keep up the good work everyone:)
[COLOR="Red"]
[SIZE="6"]bwsmith7  Found a fix for the Webcam Upside down problem !!![/SIZE][/COLOR] check below for the fix.

---

### Post by HunterThomson on 2008-07-26
**_[COLOR="Red"]How To get the Webcam To work "right side up"[/COLOR]_**

**(This is only a problem with some laptops. try it first. If the image is upside down. then do this.)**

**[COLOR="Blue"]bwsmith7[/COLOR]** **Found a fix for this YA!**


Well Just follow this link and do what it says to do. 
On page 55 of this tread bwsmith7 said this worked for him.

[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)






**_How to get the sound working_**

[U][B]Copy of wyth's post on Page 15 of this thread
[/B][/U]

[http://ubuntuforums.org/showthread.php?t=870681&page=15](http://ubuntuforums.org/showthread.php?t=870681&page=15)

Okay, I'm just basically reposting what is already on this Ubuntu help page and on the previous Lenovo Ideapad Y510 is GO page, but with some new tweaks. This guide is using the 1.0.18rc3 ALSA drivers, but this will/should work for other drivers.

First, you need to make sure you have the right stuff installed:

Code:

```
  sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

Next get the latest ALSA drivers; they'll be downloaded to wherever your default downloads go, but you're going to move them to a new directory. For this case, I'll use the Desktop.


    * alsa-driver
    * alsa-lib
    * alsa-utils

[COLOR="Blue"]**_[U]From here..._[/U]**[/COLOR]
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Next step is to create a /usr/src/alsa directory for the files and copy the tar.bz2 files to that directory; you may have this directory of you've rolled your own drivers in the past:

Code:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/Desktop/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```
    * Compile and install alsa-driver

Code:

```
cd alsa-driver* 
sudo ./configure --with-card-options=hda-codec-realtek,hda-codec-analog,hda-codec-sigmatel,hda-codec-via,hda-codec-atihdmi,hda-codec-conexant,hda-codec-cmedia,hda-codec-si3054,hda-generic
sudo make
sudo make install
```

    * Compile and install alsa-lib

Code:

```
cd ../alsa-lib* 
sudo ./configure 
sudo make 
sudo make install

```
    * Compile and install alsa-utils

Code:

```
cd ../alsa-utils* 
sudo ./configure 
sudo make 
sudo make install
```

Next find out what sound card you're using:

Code:

```
cat /proc/asound/card0/codec#* | grep Codec
```
The Y510 uses RealTek ALC888, so look for that. (This may be different if you have a newer version of the Y510 with some different hardware.)

Next you can check the ALSA-Configuration for specifics on the sound card. I found it at
Code:

```
/usr/src/alsa/alsa-driver*/alsa-kernel/Documentation/ALSA-Configuration.txt
```

Look for the section titled ALC883/888. There are many possible options, and some work better than others.

    &#8227; 3stack-6ch
    &#8227; 3stack-6ch-intel
    &#8227; lenovo-101e (Lenovo 101E)
    &#8227; lenovo-nb0763 ( Lenovo NB0763)
    &#8227; lenovo-ms7195-dig (Lenovo MS7195)
    &#8227; lenovo-sky (Lenovo Sky)
    &#8227; auto (Gets the information from BIOS)

Next to tell alsa-base what to do:
Code:

```
sudo nano /etc/modprobe.d/alsa-base
```

at the end of that file, add:
Code:

```
  options snd-hda-intel model=MODEL
```

For model=MODEL, use one of the options from above, such as:

    &#8227; options snd-hda-intel model=lenovo-sky

I found model=lenovo-sky worked beautifully and then you will have no problem with the speakers muteing with you plug in headphones.

You will want to reboot now...

```
sudo reboot
```

Then you will want to set up the default sound settings by doing this...

Open a shell and swich to the root user:

```
sudo su
```

Then set the sound up to the way you would like it at startup:
(Hint, make sure headphone is NOT muted, Frount to 100%, Surround 100%, Center 100%, LFE 100%, Side 100%, and I like to have Master set to 50% at startup.)

(Hint, use the arow keys and the "Esc" key to exit)

```
alsamixer
```

After exiting the Alsamixer, run this command to save your sound settings:

```
alsactl store
```

Then reboot:

```
reboot
```

Reboot and see if it's working. In the past, kernel updates did not break this. The surround sound features are present, the system sounds work, and the headphones automatically mute all speakers when plugged in.

_____________________________________________________________________________________



**_How to get the sound working in Arch Linux_**

In the shell:

pacman -S alsa-oss alsa-utils alsa-lib

Then add this line to the end of /etc/modprobe.conf

```
sudo nano /etc/modprobe.conf
```

```
options snd-hda-intel model=lenovo-sky
```

reboot or restart the alsa daemon

```
sudo reboot
```

Then you will want to set up the default sound settings by doing this...

Open a shell and swich to the root user:

```
sudo su
```

Then set the sound up to the way you would like it at startup:
(Hint, make sure headphone is NOT muted, Frount to 100%, Surround 100%, Center 100%, LFE 100%, Side 100%, and I like to have Master set to 50% at startup.)

(Hint, use the arow keys and the "Esc" key to exit)

```
alsamixer
```

After exiting the Alsamixer, run this command to save your sound settings:

```
alsactl store
```

Reboot and all well be working:)

---

### Post by HunterThomson on 2008-07-26
**_Lenovo Ideapad Y510 is Go Summary, Linux Compatibility List_**

I will update this and add new sections as needed. All Page #'s are in reference to wyth's thread found here;
 
[http://ubuntuforums.org/showthread.php?t=687663](http://ubuntuforums.org/showthread.php?t=687663)

**_Web cam_**= mite be upside down.... bwsmith7 fond a **[COLOR="Red"]FIX[/COLOR]** ! check it out on this web site.
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)


**_Backlight_**= Fixed in 2.6.28 Kernel
> **_Backlight_**= YA, Big Thanks to chrismulderza . He fixed the backlight by fixing errors in the DSDT (( a file which is part of the BIOS and tells the ACPI module in the Kernel what kind of hardware the computer is made out of and how to use it i.e. backlight and what is up/down and max bright and all that stuff)) 

You can find his fix on page 21 of this thread. 
[http://ubuntuforums.org/showthread.php?t=870681&page=21](http://ubuntuforums.org/showthread.php?t=870681&page=21)


**_HDD Load_Cycal_Count_**= Page 16-17...Install Laptop-mode-tools and set the powersaveing setting to 254 on AC and Bat... Read up on Laptop-mode-tools there are a lot of options.

**_Sound_**= All better now Big Thanks to Wyth. For Pwning up this problem form the git go. He has now come up with some new driver compolation flags to build the alsa driver better. He also spent the time to go though the new ALSA relece to find a new Module for our laptop "lenovo-sky" head phones mute now and sound is better.

**_Hibernation_**= Works again now in Ubuntu 8.10

**_Suspend to ram_**= Works again now in Ubuntu 8.10

**_BIOS Update_** 
[COLOR="Red"]New BIOS out 06CN33WW.ROM so this is out of date untill we get more feed back[/COLOR]

The newest BIOS vertion that works well is ***31.ROM

. Page=3-4 Of "This Thread". There is a "CRITICAL BIOS UPDATE" for all the Ideapad laptops. Lenovo only lets you download a .exe for Vi$ta. You mite want to do that before you install Linux. However you can update the BIOS in Linux look at P20 for the links and stuff. I Flashed my BIOS from my 1GB USB dirve. You can see my HOW TO below. I have also writen a description of what the BIOS is on page=3 Of "This" thread.

To make things really EZ, I have writen a script to make a USB Thumb Dirve that you can use to flash your BIOS. It works vary well. It takes all the guess work and effort out of flashing your BIOS. You can find it on page=4 of this thread
[http://ubuntuforums.org/showthread.php?p=5552537#post5552537](http://ubuntuforums.org/showthread.php?p=5552537#post5552537)

_**CD/DVD**_ Just Works... No problems at all. THE Y710 with the BlueRay drive dosn't work right now. But I have hope we will fix it at some point.

_**Multi Card Reader**_ Well the SD cards work I have not tried MMC or MS.....

_**VGA Port**_ Just Works... No problems at all.

_**S-Video Port**_ I don't konw.... PM me if you know.

_**RJ-45 Ethernet Port**_ Just Works...No problems at all.

**_FireWire_** Just Works... No problems at all.

**_Bluetooth_** Just Works... May need to use something other then NetworkManager.

**_WiFi_** Just Works... No problems at all. Got to love intel's OpenSource commitment.

_**Media Buttons**_ Just Works in Ubuntu. Or in archlinux I justed maped them in VLC an my Mediaplayer.

**_Fn Keys_** Just Works...

---

### Post by HunterThomson on 2008-07-26
[COLOR="RoyalBlue"][B]
MY info quite probably could be out of date. I don't own this laptop anymore and My post were talking about the First model of this laptop. As you can see in the pic's in the first post. The NEW Y510 you probably have doesn't look like this. However, the hardware is probably close to the same. Heck probably all Lenovo hardware is close to the same.
====================================================
++++++++++++++++++++++++++++++++++++++++++++++++++++
====================================================
[/B][/COLOR]


**_Lenovo Ideapad Y510 Flash BIOS "HOW TO"_**

[COLOR="Red"]New BIOS 06CN33WW.ROM[/COLOR]

_**NOTE: If this all looks vary confusing and/or you don't want to wast 30-40min's doing all of this then just run the script I wrote on page=4 of this thread :)**_

Bash Script >>>>>>>>>>>>>
[http://ubuntuforums.org/showthread.php?t=870681&page=4](http://ubuntuforums.org/showthread.php?t=870681&page=4)


This is what I did. I take no resposability if your compuer turns into a coster. If your BIOS gets messed up or if ANYTHING goses wrong with the BIOS Flashing your computer with not even start, it will be worthless!!!!! You should read more about it if this is new to you.

You can also check out this link for more info and options

[http://ubuntuforums.org/showthread.php?t=694513](http://ubuntuforums.org/showthread.php?t=694513)

_Downloaded the .ROM file posted by me_
 
[http://ubuntuforums.org/attachment.php?attachmentid=98752&d=1231117384](http://ubuntuforums.org/attachment.php?attachmentid=98752&d=1231117384)

_Save it to your home folder and unpack it with this comand_

```
cd ~
tar xvf 06CN31WW.bios.update.tar.gz
```

_Then put a USB thumb dirve in your box and used gparted to format it to FAT32_

_Then install "mbr"_

in Ubuntu= 
```
sudo apt-get install mbr
```

In Archlinux= You have to get it from Aur. I just edited the PKGBUILD file to read ARCH='x86_64' insted of ARCH='i686'.

_To write boot sector on the thumb drive I issued the following command.. Make sure to change the /dev/sdX as needed_

```
sudo install-mbr --enable A1 --partition 1  --force --timeout 0  /dev/sdX
```

((
**_Replace the "sdx"_** in /dev with the corect device. On my box it was "/dev/sdb1". You can find out what it is by mounting the the USB thumb drive and using the  df  comand. Look for the drive that has the same size as the thumb drive or look for the new one. d

df output with thumb drive mounted

ilesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             20807216   3951644  15806932  20% /
none                   1025920         0   1025920   0% /dev/shm
/dev/sda1               132221     16147    109247  13% /boot
/dev/sda4            220285256  68871332 140312208  33% /home
/dev/sdb1              1002056    198852    803204  20% /media/disk
))

You will need image of a bootable Floppy...(I don't think you really need to do this step because you are not booting into the USB drive... But it is your BIOS so don't mess around)

The file here [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz) contains bootable image of a basic (OEM) Freedos floppy disk, this version does not contain himem.sys so it is suitable for flashing bios. I have extracted it into home directory using Ark but you can use anything you like 
_Or just type in command_

```
cd ~
gunzip FDOEM.144.gz

```
(I have put "cd ~" to make sure that your terminal is located in the user's home folder, I also assume that you have saved the file in the home folder).

_Create new folder in your home folder, either from GUI or by issuing the following command_

```
cd ~
mkdir fdoem144
```

_Then mount the image FDOEM.144 into the folder you have created above by issuing following commands_

```
cd ~
modprobe loop
sudo mount -o loop FDOEM.144 fdoem144
```

Now you can just use dolphin/GNOME Konqueror/KDE. Open a few windows for /fdoem144, the usb sick (just click on the desktop icon), and the BIOS .ROM file. Drag and drop all the files from ~/fdoem144 and the .ROM file to the USB thumb drive. 

_Or you can just run these 2 comands in the shell ;)_ (( LOOK, These commands copy the files to the "Mount Point" where the thumb drive is mounted you can find the corect mount point with the df command))

```
cp ~/fdoem144/* /media/disk
cp ~/06CN29WW.ROM /media/disk
```

_Now clean up the junk_

```
sudo sync
sudo unmount ~/fdoem144
rmdir ~/fdoem144
rm ~/06CN31WW.ROM
rm ~/06CN31WW.bios.update.tar.gz
```

Then reboot with the USB thumb drive in and hit F2 when the "Lenovo Logo" BIOS POST screen appears to enter the CMOS. Go over to BOOT tab and go down to HardDrive (Not Boot Order) then select the USB Thumb Drive as the 1st hard drve. Then F10 and yes to save changes. Then when the Lenovo BIOS POST Screen appers on reboot hit F4 to enter the BIOS FLASHING program. The USB Thumb Drive will be seen as the C: drive. Select the .ROM file in the list on the Right of the screen and start the BIOS FLASH. (NOTE: Your hart may stop beating... This is normal) Pray to any God you know of and your computer should restart just like normal. Hit F2 and the BIOS will now stay it is 06CN29WW. You will need to set the boot order to the way you like it and other things if you need to because they have been changed to the default.

Thanks To wyth :) For the .ROM file. That takes a big pain in the *** step out of it:)

Well, for some reson I am haveing problems compressing the new .ROM fiel. but you can just use wine to extract it.in the meen time

---

### Post by Yellow Pasque on 2008-07-26
I have a script that installs ALSA 1.0.17 [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you folks find a certain model= keyword works better than others, let me know so I can add it to the list (in the thread linked above).

---

### Post by brandn on 2008-07-26
did the bios update improve performance or fix any problems?  i don't really want to mess with my bios unless it's gonna solve something.

---

### Post by HunterThomson on 2008-07-26
> **brandn said:**
> did the bios update improve performance or fix any problems?  i don't really want to mess with my bios unless it's gonna solve something.

I didn't see anything change other then the BIOS #. However, the update fixes a problem with the way the BIOS handels your RAM. "I" don't think it dose anything other then that. That is a "critical" update. If your BIOS is making mistakes with RAM then that would be a hard problem to trubleshoot. You don't want BIOS to be making any mistakes with RAM that is a critical part of you computer and could cause problems with almost any part of operation. I was not haveing any problems before but I thought it was a good idea to do the BIOS Flash. The choice is up to you.

---

### Post by HunterThomson on 2008-07-27
**_Back Light FIX for the Lenovo Ideapad Y510_**
[B][U]
This is all a quote form "chrismulderza" on page 21 of this thread. 
[/U][/B]

Thanks too

Good News Everyone!

I have a correctly working backlight on my Ideapad Y510! ...

This has been achieved by using a custom DSDT, and nothing else, no fiddling with ACPI or HAL or anything like that.

After days of trawling and scrolling through the original DSDT I finally figured out that the Lenovo emedded controller seems to be expecting some specific input values, and that there seemed to be a slight mistake in the "Package" of values returned by the _BCL AML method. Additionally ACPI as bundled with Ubuntu and the Kernel at the moment, expects the values to be in the correct order, i.e. <value when on AC>, <value when on Battery>, val0, val1, val2 ...etc the most important thing to note is that ACPI at the moment does not appear to sort the values, and assumes that they are from lowest to highest. In the case of the Ideapad they seem to have been reversed.

I have attached the DSDT.dsl in BZIP2 format to this post for those who want to give this a go.

You will obviously need the Intel ASL compiler:

Code:

```
sudo apt-get install iasl
```

To compile the DSDT just run:

Code:

```
iasl DSDT.dsl
```

Once it's compiled put it into the initramfs-tools directory under /etc:

Code:

```
sudo cp DSDT.aml /etc/initramfs-tools/
```

You might need to install the initramfs-tools package

Code:

```
sudo apt-get install initramfs-tools
```

and then finally regenerate the initrd image

Code:

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
```

reboot the machine and then give it a go...

Please test this and let me know if anyone is experiencing any other difficulties...

Cheers all!

---

### Post by wyth on 2008-07-28
Just a quick thanks to HunterThomson for keeping this thread going, and for the fantastic BIOS update instructions.  I wish I had those instructions months ago when I flashed my BIOS -- I felt like I was cliff-diving at the time, and couldn't see the bottom.

---

### Post by winnibob on 2008-07-29
Hello guys,

First, I want to thank wyth and HunterThomson, and everyone who posted on wyth's thread. I bought my Y510 on february and I run Ubuntu on it since then, and thanks to you, it rocks!

Here are the issues I noticed, and perhaps sometimes some pieces of solution...

**Suspend/Hibernate :**
In the beginning, I couldn't hibernate at all, every time I tried to wake it up, Ubuntu was just booting normally, as if it has just been powered off.
Suspend to ram was doing well 9 times on 10, and when it was buggy, it woke up with a full black screen, and I was unable to recover the system even with Ctrl+Alt+F2 : nothing happened.
I found this way to solve the hibernate problem :
first of all, the size of the swap must be two times greater than size of the ram (or at least one and a half, but two is secure)
after that, the command "s2disk" from uswsusp package worked fine for me to hibernate ( I use it twice a day since 2 weeks without one reboot).

I didn't find a solution to make suspend to ram more stable on my laptop, but the bug seems to be related to the nvidia graphics card. There are some things I had no time to try on this web page :
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

**Sound card :**
The sound works fine for me, with the HowTo given on wyth's thread. I just had to compile alsa drivers one time, and had no problem with kernel updates at all (unless gnome sound control is no longer linked to alsa mixer). I can report that *model=lenovo-ms7195-dig* and *model=3stack-6ch-dig* work both fine.
I have the same problem as everyone for the sound not muting on every channel when plugging headphones, but it seems that it can be solved with a script with *model=lenovo-ms7195-dig*. There's also something I didn't try for this on post #97 of wyth's thread.
An other thing I saw is that the channels are not correctly mapped on the speakers, as I can hear when I run
```
$ speaker-test -Dplug:surround51 -c6 -twav
```
wyth : in the post #198 of your thread, you were asking for a way to restart alsa, and this way seems to work, hope it can help :
```
sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...     [ OK ] 
 * Setting up ALSA...        [ OK ]
```

**Webcam :**
Worked out of the box, no upside-down problem. I just tried it with cheese, I was unable to make it work with aMSN and I didn't try with Skype.

**Network :**
Everything fine. Wired, Wireless and Bluetooth worked out of the box. Some people reported problems with NetworkManager and suggested to use an other soft, but no compatibility problems.

**Screen problems :**
Seems this is the big deal. Same problems as yours. An interesting fact is that I had quite the same problems under Win****XP (eg reverted keys and dimness problems) and the BIOS update solved it for this OS, but not for Ubuntu. Anyway, I just had an eye on the problem of the screen not being as bright as it can, and here is what i found : 
the file that directly controls screen brightness is /proc/acpi/video/VGA/LCDD/brightness, and you can change the value in it whenever you want, with this command :
```
sudo echo x > /proc/acpi/video/VGA/LCDD/brightness
```
where **x** is the value you want. AFAIK, our screen supports x between 0 and 10, after some experiments.
The problem is that the value in this file never get higher than 8, because the file /sys/devices/virtual/backlight/acpi_video0/max_brightness contains "8". AFAIK, this value is read from the hardware while booting, and for some reason, the system can't read the right value ( 10 ) and uses the default value ( 8 ) instead.
So I put this command in my /etc/rc.local :```
sudo echo 10 > /proc/acpi/video/VGA/LCDD/brightness
``` and made it executable, and now I have a brighter screen at startup. But when I try to change brightness with the Fn keys, the brightness file comes back to its original config (eg max=8 ). I think it happens because the system checks each time the value in /sys/devices/virtual/backlight/acpi_video0/max_brightness. I tried to modify this value but I was not able to do it.

**Miscellaneous :**
All the Fn keys seem to work, but the "sensitive" keys don't. It may be a hardware problem because it was malfunctioning under Win***.
SD card reader works perfectly.
FireWire works also perfectly (at least for external HDD).
VGA output works great on LCD and projector, some issues on CRT (couldn't set resolution over 800x600). I didn't try S-video output.

**Other Stuff :**
I'm interested in my laptop's power consumption, because if I can reduce it, I will increase its battery-life, make it more cool, and pollute less, so everyone wins :) . So I tried many things with the help of [lesswatts.org]("http://www.lesswatts.org"), powertop, cpufreq, and some threads about undervolting. My Y510 is now consuming around 22W instead of 35W before, and my CPU is around 53°C instead of 65°C, without any performance loss. So if anyone is interested, just ask and I'll tell you what I did.

---

### Post by evets25 on 2008-07-29
On another thread, ([here]("http://ubuntuforums.org/showthread.php?p=5483403#post5483403")) there is someone having the same problem as us on a different laptop, in regards to the webcam image being upside down. Apparently, the fix for this is to add a parameter to the driver when the module is loaded, like so: 
```
modprobe xxxx_driver_name_xxx invert=1

```
...but neither I nor the origonal poster know how to do that in such a way that it happens automagically at boot. This is progress at least.

---

### Post by HunterThomson on 2008-07-30
> **evets25 said:**
> On another thread, ([here]("http://ubuntuforums.org/showthread.php?p=5483403#post5483403")) there is someone having the same problem as us on a different laptop, in regards to the webcam image being upside down. Apparently, the fix for this is to add a parameter to the driver when the module is loaded, like so: 
```
modprobe xxxx_driver_name_xxx invert=1

```
...but neither I nor the origonal poster know how to do that in such a way that it happens automagically at boot. This is progress at least.

Hum..... Well the script could look like this...

#!/bin/bash

modprobe xxxx_driver_name_xxx invert=1

In KDE there is a Autostart folder, I don't know about Gnome I bet there is. The other way of makeing it run at startup is puting it in your startup daemons. I have that "alsascript" run at startup by puting it in my daemons. I have my script to turn the brightness up in my Autostart folder in KDE because KDE starting is what turns down the brightness.

((
NOTE, when I first installed Archlinux I had no problems with brightness... I installed Xorg and had no problems with brightness using only Xorg. I installed KDEbase and then I started haveing the prblems with the screen not as bright as it could be and diming at start.
))

((
Also, Now after the BIOS update. I put in the Ubuntu7.10 Live CD and the screen will not get as bright as it did. I press the Fn+up/down. The GUI brightness bar on the screen go's 10 steps but after the 6th step it dosn't get any brighter.... I guess when I Flashed the BIOS with the brightness at that level it thought that that was as bright as the screen could get and now will not get any brighter nomader what the programming... I will do more looking into this I mite be wrong. I would sugjest that you put in a Ubuntu7.10 Livecd to turn the brightness up all the way. Then reboot and do the BIOS Flash.... Just to make sure.
))

Anyway back to the web cam fix.... To put it in the daemons you need to... I don't know terditional Linux setup... But in BSD an Archlinux you put the script in /etc/rc.d folder and then add the name to the deamons array in /etc/rc.conf... Dose any one know what folder you list stuff to start in normal Linux??? 

If that dosn't work i.e. Gnome starting is what is messing it up. Then you have to put it in the Autostart folder..... Owe hay I found a grate Wiki on the Gentoo sight here is a link...

[http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

If you need root privleges to use Modeprobe then you have to give your user the ability to exicute the "webcamscript" with no password. You do this by adding this line to the sudoers file (to edit the sudoers file just type... sudo visudo) 

# Same thing without a password
# %groupname        ALL=(ALL) NOPASSWD: ALL
username ALL=(root) NOPASSWD: path/to/script/webcamscript

Then you have to write at new script to put into the auto start folder...

#!/bin/bash

sudo webcamscript


Check out how I did my Backlight bright on startup Workaround and I guess in is EZ to do it in Gnome to so you don't have to turn it up by hand every time you strat your computer:)...

[http://ubuntuforums.org/showthread.php?t=687663&highlight=lenovo+ideapad&page=19](http://ubuntuforums.org/showthread.php?t=687663&highlight=lenovo+ideapad&page=19)

---

### Post by HunterThomson on 2008-07-30
DO NOT USE KDE4 !!!!!!!!!!!

It looks like it will be cool in like 3 more Years.... Mybe KDE5 will work???

--------------------------

Well, OpenBox IS all it is cracked up to be:) Way better then KDE4. I think I even like it better then KDE3.5.9:)

---

### Post by evets25 on 2008-07-30
> **HunterThomson said:**
> Hum..... Well the script could look like this...

#!/bin/bash

modprobe xxxx_driver_name_xxx invert=1

In KDE there is a Autostart folder, I don't know about Gnome I bet there is. The other way of makeing it run at startup is puting it in your startup daemons. I have that "alsascript" run at startup by puting it in my daemons. I have my script to turn the brightness up in my Autostart folder in KDE because KDE starting is what turns down the brightness.


Well, this isn't something you want done when the user logs in, this needs to happen at the point when the driver is initially loaded, which is rather early in the boot process, and certainly long before X starts and GDM pops up. 

I know how to make a program start on log in, but this is on a whole different level; this is happening when the driver is initially loaded as a module in to the kernel.

EDIT: Also, the proper way to allow the user to run such a script would be to simply have gnome/kde's autostart run "sudo /path/to/webcamscript" (as opposed to just running the script without sudo) instead of editing sudoers to allow a user to run that particular script... that way, the whole process that the script creates is elevated to root privilges (which is okay because it's loading a *kernel module*, not just running some random program). Otherwise, the script might still fail because even if that particular user is allowed to run the script without sudo, modprobe still needs root access to actually work. However, you are thinking along the right lines.

---

### Post by winnibob on 2008-07-30
I found this after typing *dmesg* in the command line :
```
[   42.152568] usbcore: registered new interface driver hci_usb
[   42.375623] Linux video capture interface: v2.00
[   42.485825] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (046d:09b6)
[   42.488790] usbcore: registered new interface driver uvcvideo
[   42.488800] USB Video Class driver (v0.1.0)

```and this after typing *lsmod | grep uvc* :
```
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
```So I think the driver module is _uvcvideo_, and since I spent much time trying to make this webcam work with some softwares, now I'm sure it is a _v4l2_ compatible webcam.

I checked uvcvideo parameters in */sys/modules/uvcvideo/* but I could only find one : *trace*, which seems to be a verbose option.

I also found these configuration lines in */etc/modprobe.d/options* file :
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2
```but I don't think it is related to the upside-down problem.

Oh, and I should hae mentioned that everything works fine for me : no upside-down or other problems. It works at least with cheese, luvcview, vlc and amsn.

---

### Post by winnibob on 2008-07-30
**Solution for the webcam :**

Someone wrote a patch for upside-down image problem from UVC webcam. You'll find a howto to install it on this page :

[http://ubuntuforums.org/showthread.php?t=838210]("http://ubuntuforums.org/showthread.php?t=838210")

I found it on this thread :
[http://ubuntuforums.org/showthread.php?t=561433]("http://ubuntuforums.org/showthread.php?t=561433")

---

### Post by wyth on 2008-07-30
> **winnibob said:**
> **Suspend/Hibernate :**
In the beginning, I couldn't hibernate at all, every time I tried to wake it up, Ubuntu was just booting normally, as if it has just been powered off.
Suspend to ram was doing well 9 times on 10, and when it was buggy, it woke up with a full black screen, and I was unable to recover the system even with Ctrl+Alt+F2 : nothing happened.

For what it's worth, the latest kernel (2.6.24-20) has a suspend issue, and there are bugs filed against it.  I just found this out yesterday; not sure if I still have the bugs (sorry, teaching summer classes, running between rooms right now).  

You may want to try 2.6.24-19; people report that going back to that kernel solved the suspend issue.

To get that, either edit grub by commenting out the 2.6.24-20 entries (in /boot/grub/menu.lst), or just press escape, I believe, at boot so you can enter the grub options and choose a different kernel.

By the way, the 2.6.24-20 kernel also has some wireless issues I'm messing with.  This isn't specific to our hardware.  The problem is wireless is showing it's on when you boot, but doesn't automagically connect to networks it once did, often asking for passwords over and over again.

The quick fix: If you're experiencing this problem, note that the wireless light doesn't actually turn on, even though the wireless switch on the front of the machine is set to "on."  If you switch that switch to "off" and back to "on," it connects again.

I thought I had a fix and posted it [here]("http://ubuntuforums.org/showthread.php?t=859486"), but so far that fix has only worked for me once.

---

### Post by HunterThomson on 2008-07-30
> **evets25 said:**
> Well, this isn't something you want done when the user logs in, this needs to happen at the point when the driver is initially loaded, which is rather early in the boot process, and certainly long before X starts and GDM pops up. 

I know how to make a program start on log in, but this is on a whole different level; this is happening when the driver is initially loaded as a module in to the kernel.

EDIT: Also, the proper way to allow the user to run such a script would be to simply have gnome/kde's autostart run "sudo /path/to/webcamscript" (as opposed to just running the script without sudo) instead of editing sudoers to allow a user to run that particular script... that way, the whole process that the script creates is elevated to root privilges (which is okay because it's loading a *kernel module*, not just running some random program). Otherwise, the script might still fail because even if that particular user is allowed to run the script without sudo, modprobe still needs root access to actually work. However, you are thinking along the right lines.

I didn't think you were right but WOW you are. I just typed... nano brightscript and then added a # and it let me save it. So, I moved it to root's /bin to see if that would lock editing of the file but no it didn't. I moved it back to /usr/bin. Then I adden visudo to the end of it and when I ran brightscript it opened the sudoers file as ROOT!!!! WOW that is not cool..... 

I thought it only let me run the program but the fact that it was in a restricted folder would stop the editing of the script so it was not a secruity risk.

I guess I could use AppArmer to set it up like that.

---

### Post by winnibob on 2008-07-31
> Originally Posted by **wyth**
For what it's worth, the latest kernel (2.6.24-20) has a suspend issue, and there are bugs filed against it. I just found this out yesterday; not sure if I still have the bugs (sorry, teaching summer classes, running between rooms right now).

You may want to try 2.6.24-19; people report that going back to that kernel solved the suspend issue.

Actually, I'm using 2.6.24-19 kernel. 2.6.24-20 is not yet installed on my machine, maybe because I didn't activate hardy-proposed repository.
Anyway, I had these problems with suspend to ram on all kernels since 2.6.24-16.

About your networking problem, I experienced the same with 2.6.24-16 and 2.6.24-17, and it seemed the problem was in nm-applet. Many people reported that these strange behaviours while connecting disappeared after suppressing NetworkManager for an other soft.

---

### Post by JSuresh on 2008-07-31
I'm using Ubuntu 7.10 32-bit version, 

Sound: same issues, haven't tried to fix yet
Brightness: worked out of the box

The problem I'm having is with the webcam.  Neither Skype nor Cheese can even find the webcam.  Has anyone else run into this?  :confused:

---

### Post by winnibob on 2008-07-31
> Originally Posted by **JSuresh** :
The problem I'm having is with the webcam. Neither Skype nor Cheese can even find the webcam. Has anyone else run into this?
You should try the first things in post #15 (i.e. dmesg and lsmod) to find out if your problem is related to the driver.

---

### Post by wyth on 2008-07-31
> **winnibob said:**
> Actually, I'm using 2.6.24-19 kernel. 2.6.24-20 is not yet installed on my machine, maybe because I didn't activate hardy-proposed repository.
Anyway, I had these problems with suspend to ram on all kernels since 2.6.24-16.

About your networking problem, I experienced the same with 2.6.24-16 and 2.6.24-17, and it seemed the problem was in nm-applet. Many people reported that these strange behaviours while connecting disappeared after suppressing NetworkManager for an other soft.

winnibob, maybe enabling hardy-proposed and keeping at the 2.6.24-19 kernel would take care of those issues for you.  I went back to 2.6.24-19 last night and did some tests -- all the networking and suspend/hibernate issues were solved.  (In fact I'm not even sure what 2.6.24-20 was supposed to improve.)

Just a thought.

---

### Post by winnibob on 2008-07-31
> **wyth said:**
> winnibob, maybe enabling hardy-proposed and keeping at the 2.6.24-19 kernel would take care of those issues for you.  I went back to 2.6.24-19 last night and did some tests -- all the networking and suspend/hibernate issues were solved.  (In fact I'm not even sure what 2.6.24-20 was supposed to improve.)

Just a thought.
Oh, you're right. I think the last full test I did for suspend/hibernate was with kernel 2.6.24-18, and since I used to hibernate with uswsusp. I did some quick test a few minutes ago and everything seems to be allright. Suspend and hibernate both works fine from the "Quit" menu, even with no updates from hardy-proposed repsitory.

Thank you for pointing this.

---

### Post by evets25 on 2008-07-31
> **winnibob said:**
> **Solution for the webcam :**

Someone wrote a patch for upside-down image problem from UVC webcam. You'll find a howto to install it on this page :

[http://ubuntuforums.org/showthread.php?t=838210]("http://ubuntuforums.org/showthread.php?t=838210")

I found it on this thread :
[http://ubuntuforums.org/showthread.php?t=561433]("http://ubuntuforums.org/showthread.php?t=561433")

Ok, so I tried the patch(s) given in the guide, and was eventually able to compile and install the patched kernel module, which made me happy at first, but when I tried to actually use the webcam (I.e.: I opened up cheese), it completely froze the system. It's the kind of behavior I would expect if I loaded a driver for the wrong device, but I don't know. The webcam isn't that important to me (I never use it), so I don't really care about getting it to work again.

---

### Post by JSuresh on 2008-08-01
Just wanted to update setting up 32 bit Gutsy:

Hard Disk Load Cycle Error:  I was in fact getting this error which was overworking my harddrive.  I found a working fix here:
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=2](http://ubuntuforums.org/showpost.php?p=5031046&postcount=2)

Sound: Thanks a bunch for everyone's help here, wyth's instructions work perfectly.  Make sure to add the "options snd-hda-intel model=lenovo-ms7195-dig" line to the end of /etc/modprobe.d/alsa-base
Then open volume control (right click the speaker icon), go to preferences, and enable center, surround, and LFE.

The sound worked immediately but then I was having troubles with sound on reboot.  What worked for me, as pointed out earlier in the thread was to run alsamixer (just type alsamixer in the command line) and move to the right until you get to channels, change this to 6ch.  Now the sound is beautiful.

I do NOT have the problem where LFE and center are muted on reboot, however I am having the issue where these channels are not muted by plugging in headphones.  However a script could probably fix this (does anyone have one?  I'm still a nub), but really it's not a big deal to just mute the two channels and enjoy the sound :guitar:

I was originally apprehensive about moving from a windows power user to being a ubuntu newbie but with all this support I'm really enjoying the new  awesomeness of my ideapad.  Thanks a lot :KS

---

### Post by wyth on 2008-08-03
Just wanted to report  on my roll-back to the 2.6.24-19 kernel, which has taken care of the suspend/hibernate kernel panic, the wireless connection issues, and now I just learned it took care of another issue I was having -- the screen dimming every time I played a video.   

Something's screwy with 2.6.24-20.

---

### Post by HunterThomson on 2008-08-04
> **wyth said:**
> Just wanted to report  on my roll-back to the 2.6.24-19 kernel, which has taken care of the suspend/hibernate kernel panic, the wireless connection issues, and now I just learned it took care of another issue I was having -- the screen dimming every time I played a video.   

Something's screwy with 2.6.24-20.

Ya, see this is why I keep going back and forth on the "Is the backligh a Kernel problem?" I am running a genaric 2.26.25-ARCH kernel. I have said before that it dims on VLC boot but not all the way and only the first time. I would not be suprized if a lot of these settings could be fixed by changing setting in a custom Kernel build.

Note.. On my angry move from KDE I pased through Gnome2 and it didn't dim my backlight on boot. I didn't stay there long enugh to do some more tests.

ALSO, I booted into Ubuntu7.10 live CD and the max bright setting in there is 15 NOT 10. So, this makes sents if the Brightness bar in KDE was reporting max bright at 67%. 8/15 is 67% 8/10 is 80%..... So, this talk about how it should be 10 is wrong it "should be" 15.

Note: Off topic but OpenBox kicks*** :)

Note: If you are using a intel X3100 graficx card and don't want to mess everything up by running Compiz but still want to have the 3D desktop effects when changing desktops youcan use 3ddesktop

Ubuntu
sudo apget 3ddesktop
Archlinux
sudo pacman -S 3ddesktop

---

### Post by azteca_04 on 2008-08-08
Hi, thanks for all the help you guys have provide here, its helped me with my lenovo y510, and its awsome, ok well my question is about the bios update, i updated the bios via vista de own on the lenovo web page, so i dont need to update for my ubuntu partition right? once i updated it will remaind that no matter what SO i ran, or how many times i format right? thanks for all the help wyth and HunterTompson

---

### Post by HunterThomson on 2008-08-08
_**BIOS and CMOS What They Are**_
**_What Flashing the BIOS Is_**

> **azteca_04 said:**
> Hi, thanks for all the help you guys have provide here, its helped me with my lenovo y510, and its awsome, ok well my question is about the bios update, i updated the bios via vista de own on the lenovo web page, so i dont need to update for my ubuntu partition right? once i updated it will remaind that no matter what SO i ran, or how many times i format right? thanks for all the help wyth and HunterTompson

Yes, This that is corect. You do not have to flash your BIOS agin. The BIOS is not on the HDD it is on the System ROM chip.

On your motherboard there are two small chips that are needed to start your computer. They are cald the system ROM "Read only memory" and CMOS "Complementary metal-oxide semiconductor". The system ROM is the special memory chip that stores the BIOS "basic input/output system" programs. The BIOS is the collective name for the hundreds of tiny porgrams that tell your computer everything from what the time is to what kind of computer it is and the CMOS setup utility. The CMOS setup utility is the porgram that is running when you hit the F2 at the POST screen. The CMOS memory chip containes saved information that you selected in the CMOS setup  utility such as the boot order. 

When you turn on the power to your computer there is a wire that is connected to your CPU cald "power good wire". This tells your CPU to wake up. It then talks to the ROM and runs the BIOS programs to find out what hardware is connected to the PC and runs self diognostic tests. This is cald the POST "Power on self test". The POST will also look for Bootable drives in the order spesifid by the CMOS settings i.e. the GRUB bootloader on the Harddrive. If all go's well it will then give control of the coputer over to the GRUB bootloader wich will intern give control over to the OS that you choose. 

The BIOS programs will be coppyed over to the RAM "Random acess memory" to preform basic tasks. One of these programs controls and maps the RAM. This is the program that had a Bug in it in the older vertion the the BIOS on all of the Lenovo Ideapad laptops. So, that is why it was taged a "Critical Update". It mite have updated other things but that is the only one Lenovo said was updated.

In the beginning the only way to change any of the BIOS programs was to change the ROM chip itself. But then there was the advent of CMOS wich alowd to save some settings in a safe way. The CMOS is volital though it requiers voltige to retain memory. To give it this voltige there is a CMOS battery. If your clock starts to loose time or every time you start you computer the CMOS setup utility settings are back to the defalt settings your CMOS battery is dead and needs to me changed. BUT now there is new system ROM cips that use Flash memory. They are cald FlashBIOS chips or FlashROM-BIOS chips. These chips can be written to inorter to update hardware compatability or fix Bugs. Changeing the BIOS programs on a FlashROM chip is cald "Flashing the BIOS".

Now that you know that the BIOS programs on the system ROM chip are the cridical software needed to start you compuer you should also know that if something gose wrong wile Flashing the BIOS your compuer will not turn on. So, when you flash your BIOS make sure you know what you are doing and DO NOT INTERUPT THE FLASHING PROSSESS.

Dring the POST if the compuer will not start and only Beeps at you or prints an error coad on the screen. Then the POST has dettected an error with one or more componets of the hardware. The error codes are some what standerdized such as 100-199 are motherboard errors, 200-299 are keyboard errors, 300-399 are RAM errors. You can find a list of the error coads (beeps and #'s) on the computer makers web sight or on the Mother board makers web sight.

---

### Post by pbouf on 2008-08-09
> **evets25 said:**
> Ok, so I tried the patch(s) given in the guide, and was eventually able to compile and install the patched kernel module, which made me happy at first, but when I tried to actually use the webcam (I.e.: I opened up cheese), it completely froze the system. It's the kind of behavior I would expect if I loaded a driver for the wrong device, but I don't know. The webcam isn't that important to me (I never use it), so I don't really care about getting it to work again.
I get the exact same thing. I would like to get the webcam working; hopefully someone can figure it out.

---

### Post by HunterThomson on 2008-08-09
_**Script to make a USB Thumb Drive to Flash your BIOS with**_


**ubf2 v2.0.0**
-New BIOS 
-rm the MBR
-Should come executable
**usbbiosflasher v1.0.1**
-Changed some little stuff....
**usbbiosflasher v1.0.0**


This script makes this task as EZ as 1,2,3...

You should still read through the description on page=1 of this thread just for the hell of it. There are also a few "notes" there that are not here. If you don't know what the BIOS is then read through my post on page=3 of this thread.

Thanks one more time to wyth for posting the .ROM file :) That makes life way more simple.

```
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. 
# This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
#
# If you have anyideas send be a PM on ubuntufourms.org  my user name is HunterThomson 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drives come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#
#
#

echo "Interactive Shell Script to Make a USB Thumb Drive \for Flashing BIOS On a Lenovo Ideapad Y510"
echo "You will need to have the USB Memory stick formated FAT32 and give it a BOOT flag with a program like gpartted"


# The next comand will make a directory to put needed files into. Note this file and everything init will be owned by root.
mkdir ~/usbbiosfiles
if [ $? != 0 ] ; then
    #failed
    echo "Could not \make directory usbbiosfiles"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    exit 1
else
    echo "Made directory usbbiosfiles... OK"
fi

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles
if [ $? != 0 ] ; then
    echo "Could not Change to the usbbiosfiles directory"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Changing to the usbbiosfiles directory... OK"
fi


wget  "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"
if [ $? != 0 ] ; then
    echo "Could not Download FreeDOS"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Download of FreeDOS... OK"
fi

wget "http://ubuntuforums.org/attachment.php?attachmentid=84991&d=1221204455"
if [ $? != 0 ] ; then
    echo "Could not Downlad the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Download of the BIOS.ROM \file... OK"
fi

# The next comand will name the .ROM file to the right name.
mv ~/usbbiosfiles/attachment.php?attachmentid=84991\&d=1221204455 ~/usbbiosfiles/06CN31WW.ROM.tar.gz
if [ $? != 0 ] ; then
    echo "Could not rename the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Renameing of the BIOS.ROM \file... OK"
fi

echo ""

# The next two comands set the variables. DEVX for the path i.e. /dev/xxx and MOUNTX for the mount point i.e. /media/xxx
verify="n"
while [ "$verify" != y ]
do
    echo "You will need to know the Mount Point and the dev Path. You will also need to \make sure the File System \type is vFAT, FAT16 or FAT32." 
    echo ""
    echo "With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug \in the USB Thumb Drive and run the comand df -T one \more time. The new device listed is the USB Thumb Drive. Note the Mount Point and The dev Path and the File system Type i.e. vFAT... If the File System \type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to \make sure. In any \case delete all files and directorys on the USB drive before you go any ferther with this program."
    echo ""
    printf "Enter the dev path the USB Thumb Drive is at?"
    read DEVX
    echo ""
    echo "Are you sure $DEVX is the dev path of the USB Thumb Drive... y or n?"
    read verify
done 

echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "What is the Mount Point of the USB Thumb Drive?"
    read MOUNTX
    echo ""
    echo "Are you sure $MOUNTX is the Mount Point of the USB Drive... y or n?"
    read verify
done 

echo ""

tar xvf ~/usbbiosfiles/*.tar
if [ $? != 0 ] ; then
    echo "Could not unpack BIOS.ROM file"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unpacking BIOS.ROM file... OK"
fi

gunzip ~/usbbiosfiles/FDOEM.144.gz
if [ $? != 0 ] ; then
    echo "Could not unpack FreeDOS files"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unpacking FreeDOS files... OK"
fi

mkdir ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not make directory fdoem144 in usbbiosfiles directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Made directory fdoem144 in direcoty usbbiosfiles... OK"
    echo ""
    echo "Going to \sleep \for 5secs"
fi

modprobe loop && sleep 5
if [ $? != 0 ] ; then
    echo "Could not \modprobe loop"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Modprobeing loop... OK"
fi

mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not \mount FreeDOS on the fdoem144 directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Mounting FreeDOS on the fdoem144 directory... OK"
fi

cp ~/usbbiosfiles/fdoem144/* $MOUNTX
if [ $? != 0 ] ; then
    echo "Could not copy FreeDOS files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Copying FreeDOS files to $MOUNTX... OK"
fi

cp ~/usbbiosfiles/*.ROM $MOUNTX
if [ $? != 0 ] ; then
    echo "Could not copy BIOS.ROM files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Copying BIOS.ROM files to $MOUNTX... OK"
fi

sync
if [ $? != 0 ] ; then
    echo "Could not run the syncing command"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Runing the syncing command... OK"
fi

umount ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not unmount FreeDOS"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unmounting of FreeDOS... OK"
fi

verify="n"
while [ "$verify" != y ]
do
    printf "Do you see any errors... yes or no?"
    read AN2
    echo ""
    printf "You answered... $AN2 to errors. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN2" == "yes" ]
then
    echo "Prosses Check Repoted... Error"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Success"
    echo "I did a lot of error checking too and didnt find anything"
    echo ""
    echo "Go get a pen and paper to write down these instructions"

printf "Then hit the Enter to continue"
read WAIT
echo "#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS on a Lenovo Ideapad Y510. 
# This script needs to me owned and run as ROOT with the "sudo command"
# i.e.  sudo usbbiosflasher
#
# If you have anyideas send be a PM on ubuntufourms.org  my user name is HunterThomson 
# Name/Rename this script usbbiosflasher and save it to the ~/home directory.
# Then run the command-  chown root:root usbbiosflasher
# Then run the command-  chmod 755 usbbiosflasher
# Then copy the script to the directory /usr/bin.
# Run this comand to do that- sudo cp ~/usbbiosflasher /usr/bin  
#
# You also must have the program "mbr" installed
# You can install the mbr program by running this comand in the shell on Ubuntu
# sudo apt-get install mbr
# In Arch Linux you have to get it from Aur
#
# First you will need to know a few things...
#
# You will also need to know the Mount Point i.e. /media/disk and the /dev path i.e. /dev/sdb1.
# You can find these by using the df -T comand. 
# Run   df -T  in the shell. Then plug in the USB Thumb Drive and run the  df -T  comand agin.
# The new listing is the USB Thumb Dirve.
# Also check to make sure the File System tipe is vFAT or FAT16 or FAT32. 
# If it is not use gparted to format it to FAT32.
# I am farly certen that all USB Thumb drives come formated with FAT file system out of the BOX.
# You may want to fromat it anyway just to make sure.
#
#
#
#

echo "Interactive Shell Script to Make a USB Thumb Drive \for Flashing BIOS On a Lenovo Ideapad Y510"

# The next comand will make a directory to put needed files into. Note this file and everything init will be owned by root.
mkdir ~/usbbiosfiles
if [ $? != 0 ] ; then
    #failed
    echo "Could not \make directory usbbiosfiles"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    exit 1
else
    echo "Made directory usbbiosfiles... OK"
fi

# The next two comands will get the FreeDOS file and the .ROM file.
cd ~/usbbiosfiles
if [ $? != 0 ] ; then
    echo "Could not Change to the usbbiosfiles directory"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Changing to the usbbiosfiles directory... OK"
fi


wget  "http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz"
if [ $? != 0 ] ; then
    echo "Could not Download FreeDOS"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Download of FreeDOS... OK"
fi

wget "http://ubuntuforums.org/attachment.php?attachmentid=84991&d=1221204455"
if [ $? != 0 ] ; then
    echo "Could not Downlad the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Download of the BIOS.ROM \file... OK"
fi

# The next comand will name the .ROM file to the right name.
mv ~/usbbiosfiles/attachment.php?attachmentid=84991\&d=1221204455 ~/usbbiosfiles/06CN31WW.ROM.tar.gz
if [ $? != 0 ] ; then
    echo "Could not rename the BIOS.ROM \file"
    echo "look above \for \info"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Renameing of the BIOS.ROM \file... OK"
fi

echo ""

# The next two comands set the variables. DEVX for the path i.e. /dev/xxx and MOUNTX for the mount point i.e. /media/xxx
verify="n"
while [ "$verify" != y ]
do
    echo "You will need to know the Mount Point and the dev Path. You will also need to \make sure the File System \type is vFAT, FAT16 or FAT32." 
    echo ""
    echo "With the USB Thumb Drive unpluged, Open another shell and run the comand  df -T  Then plug \in the USB Thumb Drive and run the comand df -T one \more time. The new device listed is the USB Thumb Drive. Note the Mount Point and The dev Path and the File system Type i.e. vFAT... If the File System \type is not vFAT, FAT16 or FAT32 you will need to fromat it with gparted. You may want to format the USB Thumb Drive anyway just to \make sure. In any \case delete all files and directorys on the USB drive before you go any ferther with this program."
    echo ""
    printf "Enter the dev path the USB Thumb Drive is at?"
    read DEVX
    echo ""
    echo "Are you sure $DEVX is the dev path of the USB Thumb Drive... y or n?"
    read verify
done 

echo ""

verify="n"
while [ "$verify" != y ]
do
    printf "What is the Mount Point of the USB Thumb Drive?"
    read MOUNTX
    echo ""
    echo "Are you sure $MOUNTX is the Mount Point of the USB Drive... y or n?"
    read verify
done 

echo ""

tar xvf ~/usbbiosfiles/*.tar
if [ $? != 0 ] ; then
    echo "Could not unpack BIOS.ROM file"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unpacking BIOS.ROM file... OK"
fi

gunzip ~/usbbiosfiles/FDOEM.144.gz
if [ $? != 0 ] ; then
    echo "Could not unpack FreeDOS files"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unpacking FreeDOS files... OK"
fi

mkdir ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not make directory fdoem144 in usbbiosfiles directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Made directory fdoem144 in direcoty usbbiosfiles... OK"
    echo ""
    echo "Going to \sleep \for 5secs"
fi

modprobe loop && sleep 5
if [ $? != 0 ] ; then
    echo "Could not \modprobe loop"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Modprobeing loop... OK"
fi

mount -o loop ~/usbbiosfiles/FDOEM.144 ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not \mount FreeDOS on the fdoem144 directory"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Mounting FreeDOS on the fdoem144 directory... OK"
fi

cp ~/usbbiosfiles/fdoem144/* $MOUNTX
if [ $? != 0 ] ; then
    echo "Could not copy FreeDOS files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Copying FreeDOS files to $MOUNTX... OK"
fi

cp ~/usbbiosfiles/*.ROM $MOUNTX
if [ $? != 0 ] ; then
    echo "Could not copy BIOS.ROM files to $MOUNTX"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Copying BIOS.ROM files to $MOUNTX... OK"
fi

sync
if [ $? != 0 ] ; then
    echo "Could not run the syncing command"
    echo "look above \for \info"
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this scrip agin"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    rm -r ~/usbbiosfiles
    exit
else
    echo "Runing the syncing command... OK"
fi

umount ~/usbbiosfiles/fdoem144
if [ $? != 0 ] ; then
    echo "Could not unmount FreeDOS"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Unmounting of FreeDOS... OK"
fi

verify="n"
while [ "$verify" != y ]
do
    printf "Do you see any errors... yes or no?"
    read AN2
    echo ""
    printf "You answered... $AN2 to errors. Is this correct... y or n?"
    read verify
done

echo ""

if [ "$AN2" == "yes" ]
then
    echo "Prosses Check Repoted... Error"
    echo "Look above for errors or problems reported and fix the problem"
    echo ""
    echo "removeing directory usbbiosfiles..." 
    echo ""
    echo "Reformat the USB Stick to FAT32 with gparted"
    echo "Fix the problem and run this script agin"
    rm -r ~/usbbiosfiles
    exit
else
    echo "Success"
    echo "I did a lot of error checking too and didnt find anything"
    echo ""
    echo "Go get a pen and paper to write down these instructions"

printf "Then hit the Enter to continue"
read WAIT
echo """

```

---

### Post by azteca_04 on 2008-08-10
thanks HunterTompson for the explanation and the new info,

i have another problem with my ubuntu 8.04 sometimes when i start it and try to play song, it will never happen only after i reboot, and same happen with my webcam, sometimes it can't find it, and when it does is upside-down,if you have any suggestions it will be great thanks again

---

### Post by HunterThomson on 2008-08-10
> **azteca_04 said:**
> thanks HunterTompson for the explanation and the new info,

i have another problem with my ubuntu 8.04 sometimes when i start it and try to play song, it will never happen only after i reboot, and same happen with my webcam, sometimes it can't find it, and when it does is upside-down,if you have any suggestions it will be great thanks again

Hum... My guess is that the drivers are getting jumbled up and triping over eachother at startup.... 

In archlinux this would be a ez thing to fix or prove that it is not the problem because archlinux uses a rc.conf file to control what starts at startup and in what order.... I don't know how to do that on Ubuntu or a normal Linux system. If someone knows let me know. 

How did you get the sound working.... did you install new alsa-Stuff (you didn't have to) Did you just add...

```
options snd-hda-intel model=lenovo-ms7195-dig
```

too the end of this file...

```
/etc/modprobe.d/alsa-base
```

If all you did was add that try....

```
sudo apt-get --reinstall alsa-utils alsa-lib alsa-driver
```

You mite have to add the driver option the the end of the alsa-base file agin too...

I am just taking crazy shots in the dark.... Maybe waite for someone to give you better advice... 

If you are felling adventurous you could try a new distro... Linux Mint would be a good move... It is based on Ubuntu and uses the same package repositorys. I have herd many good things about it. Ubuntu was the first Linux disro I used (well I spent my first week on Fedora wich is just horable) It was farly simple to learn and I liked it. However, as soon as it swiched to 8.04 I started to dig out... "To me" 8.04 is a pile of buggy junk..."To ME"..."Some people Love it".... I know for sure if you download Ubuntu 7.10 and install that you will not have anyproblems "At All". Well other then using an out of date Gnome but that is not realy a problem. Arch Linux is the Best Disto Ever :) "If You Ask Me". However, you will have to use the Shell to do stuff. Installing mite scare you a bit... You would be best to wate untill you play around a bit more and find out what programs you like to use and how things are set up.

P.S. SO... you updated your BIOS before you moved to Linux :) What is your Backlight like????

---

### Post by azteca_04 on 2008-08-10
hi thanks for the replya, well i installed the alsa drivers like it was mentioned in the previous thread i did everything that it said in there, and for me i think ubuntu is right for me, so i think im going to play some more with these one but i going to reinstall everything and hope to get it right

---

### Post by azteca_04 on 2008-08-10
> **HunterThomson said:**
> 

P.S. SO... you updated your BIOS before you moved to Linux :) What is your Backlight like????

i forgot to answer this, same problem like most of them, if i go up is less brightess, and if a go down its brighter and at start up is not that bright

---

### Post by HunterThomson on 2008-08-10
> **azteca_04 said:**
> hi thanks for the replya, well i installed the alsa drivers like it was mentioned in the previous thread i did everything that it said in there, and for me i think ubuntu is right for me, so i think im going to play some more with these one but i going to reinstall everything and hope to get it right

Hope that works :) 
Ya, Ubuntu is good :) It is not the most populare bcause it sucks... I just don't like it. 

-------------------------------

I was thinking "klibc" mite be causing the problem with teh backlight. I'm looking into it. If you know I am wrong pleas save me some time.

---

### Post by Morpheun on 2008-08-11
Hey HunterThomson, I don't want to completely derail this thread but, I'm working on installing Arch on a seperate partition from Ubuntu, I am rather experienced with Arch, but I'm having trouble getting a working xorg.conf for this computer, did you generate one with hwd or write your own? If you did anything special in making it I'd like to know. 

Thanks in advance.

---

### Post by chargersfan420 on 2008-08-12
Hey everyone, I've been silently watching this thread, but now i need a little bit of advice...

I've got a Y710 (Specs here: [http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3523911](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3523911) ) with a triple boot Vista/XP/Ubuntu 8.04.  I'm new to Ubuntu and so far i like it alot.  However, i have a couple of problems with my installation.

Firstly, the optical drive is not recognized at all by Ubuntu only.  When i installed XP i had to switch the ACHI in the BIOS to "Compatibility" mode in order to boot the installation disc and i think that might have something to do with it, but i put it back to enhanced recently with no noticable changes.  If i turn ACPI off on startup, the drive works, but many other things don't.  Googling suggests modifications to /etc/fstab, but no suggestions have solved this issue.

Second, sound issues.  I can't get more than the front speakers only, and i've tried everything suggested in the page 2 area of the old thread.  I have done the BIOS update with the Vista drive (not sure if that was sound related).  I also notice the only setting that VirtualBox was able to pass sound through was PulseAudio, but it is a little bit static-y.  I'm not sure if this is useful...

A friend told me that i'm running 64bit edition... is there a way to check?  If that's what i have, i didn't mean to, which leads to a couple of questions:
1.  Is it easy to change over to a 32bit edition?  The only file i really care about is my VirtualBox, which is stored on a separate partition.  I can back up the rest if wiping the Ubuntu partition is required.
2.  Will i get better battery life from the 32bit edition?  I'm only getting about an hour and 20 minutes tops... is this comparable to the Y510 users? (typically running Virtualbox all the time)
3.  Any other suggestions of things to try before downgrading to 32bit?  Any other pros and cons between 32bit and 64bit?

Thanks for listening.

P.S. for the record, webcam works without issue, brightness works without issue (all 10 levels), only basic hotkeys worked out of the box (volume, mute, etc)

---

### Post by evets25 on 2008-08-12
As far as 64-bit goes, I don't really see much of an advantage in using it right now. I used 64-bit Ubuntu for a while, and I encountered a lot of problems with it that I wouldn't normally be getting with 32-bit, such as a 64-bit version of flash player being non-existent, certain hardware drivers missing or not working, and programs not being native 64-bit. One benefit of 64-bit is that it allows more than 4Gb of ram natively, but that's not an issue unless you actually have more than 4Gb of ram. Supposedly, there's an advantage of speed for some programs, but I know from experience that some programs that are 32-bit ONLY (such as the Linux version of the orginal Unreal Tournament) will actually run slightly *slower* on a 64-bit OS, because the 32-bit environment or whatever has to be emulated. 

So basically, until almost all programs and drivers have 64-bit versions that are equal to or greater than their 32-bit versions, IMHO there is no advantage.

---

### Post by Morpheun on 2008-08-12
post the output of 

cat /etc/fstab

and

ls /dev/cd

However with the amount of problems you're having (none of which seem typical of my ubuntu install) You should install the 32bit version as a fresh install. 

Download it here, burn it to a CD and install. The version for "Standard Personal Computers" is the 32bit.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by chargersfan420 on 2008-08-12
results of    cat /etc/fstab:
```

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2 none swap sw  0       0
# /dev/sdc0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0     /media/cdrom0   auto user,noauto,exec,utf8 0       0
/dev/scd0     /media/cdrom4   auto user,noauto,exec,utf8 0       0

/dev/sda1       /mnt/vista	auto	defaults	0	0
/dev/sda5	/mnt/xp		auto	defaults	0	0
/dev/sda6	/mnt/music	auto	defaults	0	0

```

As you can see, i commented out lines and tried a few options... wasn't sure if it was scd0 or sdc0... lol.   Also tried cdrom4 because a cdrom0 folder exists, but there's never anything there... i thought by trying for cdrom4, i could see if the directory exists faster than opening cdrom0.

results for:   ls /dev/cd
```
$ ls /dev/cd
ls: cannot access /dev/cd: No such file or directory

```

I think i will probably switch over to 32bit, but i'm in no hurry, so if anyone wants to take a shot at this problem, i'm happy to help the community resolve issues.

---

### Post by Morpheun on 2008-08-12
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Try using that, thats currently the cd entry in mine. I find it weird that ubuntu doesn't use /dev/cdrom or /dev/cdrw for it though, you might want to try those if it still isn't working.

Also the /media/cdrom0 folder should exist already, messing with it can potentially cause problems.

---

### Post by chargersfan420 on 2008-08-12
Thank you for your assistance, Morpheun.

This is one of the suggestions i found when googling the problem earlier.  I didn't try it since switching the ACHI back to enhanced mode, and i just tried it now with no joy.

Although i don't know what i'm talking about, it seems to me that the problem lies beyond /etc/fstab.  There are no entries in /dev that even remotely resemble an optical drive.  Folders in /dev include:
bus, disk, dri, fd, input, net, pts, shm, snd, usb.
It seems to me that the mount command just relocates devices and filesystems shown as folders... wouldn't the folder have to exist (in /dev) for it to get mounted (elsewhere)?

a couple other things i have noticed:

1.  after booting, i found this in dmesg:
[   62.101979] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Most google results to "e2fsck" are at least 4 years old...

2.  While going through the instructions on page 2 to get the sound working, i found this in the alsa-base installation notes:
Searching for GRUB installation directory ... found: /boot/grub 
Cannot determine root device.  Assuming /dev/hda1 
This error is probably caused by an invalid /etc/fstab 

At this point it might also be important to mention that GRUB failed to set up my triple-boot correctly.  It found one of my two Windows drives, named it Vista, but in actuality, it found the XP one.  Now i have the Vista bootloader booting into GRUB when I select Ubuntu.  I have learned that most OS's get their basic hardware information from the bootloader, so perhaps this could also be a cause of the issues...?

---

### Post by HunterThomson on 2008-08-13
> **Morpheun said:**
> Hey HunterThomson, I don't want to completely derail this thread but, I'm working on installing Arch on a seperate partition from Ubuntu, I am rather experienced with Arch, but I'm having trouble getting a working xorg.conf for this computer, did you generate one with hwd or write your own? If you did anything special in making it I'd like to know. 

Thanks in advance.

I don't realy remember if I did anything specal to make Xorg work. I did install a new driver for the intel X3100 grafix card....

Atached is my xorg.conf

---

### Post by HunterThomson on 2008-08-13
> **chargersfan420 said:**
> Thank you for your assistance, Morpheun.

This is one of the suggestions i found when googling the problem earlier.  I didn't try it since switching the ACHI back to enhanced mode, and i just tried it now with no joy.

Although i don't know what i'm talking about, it seems to me that the problem lies beyond /etc/fstab.  There are no entries in /dev that even remotely resemble an optical drive.  Folders in /dev include:
bus, disk, dri, fd, input, net, pts, shm, snd, usb.
It seems to me that the mount command just relocates devices and filesystems shown as folders... wouldn't the folder have to exist (in /dev) for it to get mounted (elsewhere)?

a couple other things i have noticed:

1.  after booting, i found this in dmesg:
[   62.101979] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Most google results to "e2fsck" are at least 4 years old...

2.  While going through the instructions on page 2 to get the sound working, i found this in the alsa-base installation notes:
Searching for GRUB installation directory ... found: /boot/grub 
Cannot determine root device.  Assuming /dev/hda1 
This error is probably caused by an invalid /etc/fstab 

At this point it might also be important to mention that GRUB failed to set up my triple-boot correctly.  It found one of my two Windows drives, named it Vista, but in actuality, it found the XP one.  Now i have the Vista bootloader booting into GRUB when I select Ubuntu.  I have learned that most OS's get their basic hardware information from the bootloader, so perhaps this could also be a cause of the issues...?

Run the alsascript and I also attached my "install-script" script. So, just install the 'install-script' script.

open in a text editor like gedit and 'Save As' alsascript ((Cut off the ".txt")) and save it to the home directory.

Then in the shell...

```
sudo chown root:root ~/instal-script
sudo chmod 755 ~/install-script
sudo mv ~/install-script /usr/bin
```

Then to install scripts all you have to do is. Put it in the home directory. Then in the shell...

```
sudo install-script
```

That will make installing script a lot faster.

After you do that make sure you have...

```
options snd-hda-intel model=lenovo-ms7195-dig
```

At the end of this file...

```
/etc/modprobe.d/alsa-base
```

Restart the computer and type alsascript in the shell. Sound should work now.

The "e2fsck" (ext2 File System Check) will check your ext2/ext3 file system for errors and corect them. This should be done auto at boot after a certen # of mount cycals. But you can do it your self. It can not be run on a mounted file system. So, boot up into a Live CD and run this comand...Replase "XXX" with what it should be for the partiton you want to check.

```
e2fsck -fp /dev/XXX
```

also see

```
man e2fsck
```


As for the...

> found: /boot/grub 
Cannot determine root device.  Assuming /dev/hda1

Well, is /dev/hda1 the corect location? Also, I am going to edit the Ubuntu Sould instructions. You don't have to install alsa. That was for Ubutnu7.10...Ubuntu8.04 alredy has the newest ALSA or at leest new enough.

As for the Vista problem... look about I am sure you are not the first one to have it. Make a new thread for that one.

---

### Post by chargersfan420 on 2008-08-13
Thank you for the script, but unfortunately, it didn't help... yet.  It looks like it can be of use if we can get to the root of the problem.

I have attached a screenshot from both device manager and the volume control panel.  Unfortunately, i was unable to take a screenshot when i go to File - Change Devices, so i will list off my entries here:
* 0: HDA Intel (Alsa Mixer)
  1: HDA ATI HDMI (Alsa Mixer)
  2: Realtek ALC888 (OSS Mixer)
  3: Playback: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
  4: Capture: Monitor source of ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
  5: Capture: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
0 is the regular control panel (from the screenshot).  The only thing that seems to work (output-wise) is the Front speaker control, PCM and Master, which all do the same thing. 
1 only lets me flip a switch on IEC958, i'm assuming its for HDMI, which i don't have a use for just yet.
2 is a stripped down version of the regular control panel, and nothing here works except for (master) "volume".
3, 4, and 5 give me a master volume level only.

I am just curious if all of this should be here or perhaps i have conflicting drivers...?  Also, does Device Manager look normal in the screenshot?

I have a few ideas on the optical drive, and will report findings later.

---

### Post by HunterThomson on 2008-08-13
> **chargersfan420 said:**
> Thank you for the script, but unfortunately, it didn't help... yet.  It looks like it can be of use if we can get to the root of the problem.

I have attached a screenshot from both device manager and the volume control panel.  Unfortunately, i was unable to take a screenshot when i go to File - Change Devices, so i will list off my entries here:
* 0: HDA Intel (Alsa Mixer)
  1: HDA ATI HDMI (Alsa Mixer)
  2: Realtek ALC888 (OSS Mixer)
  3: Playback: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
  4: Capture: Monitor source of ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
  5: Capture: ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer)
0 is the regular control panel (from the screenshot).  The only thing that seems to work (output-wise) is the Front speaker control, PCM and Master, which all do the same thing. 
1 only lets me flip a switch on IEC958, i'm assuming its for HDMI, which i don't have a use for just yet.
2 is a stripped down version of the regular control panel, and nothing here works except for (master) "volume".
3, 4, and 5 give me a master volume level only.

I am just curious if all of this should be here or perhaps i have conflicting drivers...?  Also, does Device Manager look normal in the screenshot?

I have a few ideas on the optical drive, and will report findings later.

Well the alsascript should have set the "ch"(chanels) to "ch6" (6 chanels). Check it anyway in the "Options tab".

---

### Post by evets25 on 2008-08-13
> **Morpheun said:**
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Try using that, thats currently the cd entry in mine. I find it weird that ubuntu doesn't use /dev/cdrom or /dev/cdrw for it though, you might want to try those if it still isn't working.

Also the /media/cdrom0 folder should exist already, messing with it can potentially cause problems.

FYI, the /dev/cdrom and /dev/cdrw devices are just symlinks to whatever the actual cdrom device is, in this case /dev/scd0. These are usually generated automagically, since some programs use the symlinks rather than figuring out what the CD device is.

---

### Post by chargersfan420 on 2008-08-13
@ HunterThomson - confirmed, the volume control is set to 6ch.  Still no joy :(

---

### Post by chargersfan420 on 2008-08-13
@ HunterThomson - I didn't notice you edited your post with the sound script... i played around with it a bit, noticing a " symbol was missing early on.  It seemed to do what it was designed for... but no change to the status.

> **HunterThomson said:**
> 

Well, is /dev/hda1 the corect location?

Actually, no, i don't think it is... my hard drives are picked up as sda and sdb instead of hda / hdb.  I think this also relates to my optical drive problem...

My root drive is sdb6... i see in /boot/grub/menu.lst i have this:
root      (hd1,5)
Is this the source of that error?

---

### Post by HunterThomson on 2008-08-14
> **chargersfan420 said:**
> @ HunterThomson - I didn't notice you edited your post with the sound script... i played around with it a bit, noticing a " symbol was missing early on.  It seemed to do what it was designed for... but no change to the status.



Actually, no, i don't think it is... my hard drives are picked up as sda and sdb instead of hda / hdb.  I think this also relates to my optical drive problem...

My root drive is sdb6... i see in /boot/grub/menu.lst i have this:
root      (hd1,5)
Is this the source of that error?


Aaa Yes...evets25 is right I knew I forgot to say something.... /dev/cdrom should be there and empty... It is just a link...

Anyway.... The Linux Kernel names your harddrive/Optical/USB.... It seems like evrything as part of a SCSI .... However, Grub and stuff calls your harddrive "hda". Anyway, if GRUB didn't have the corect location of stuff would cause it not too boot into Linux. So, I would not wory about that. Now, I am sure BIOS is what is telling your OS what hardware the coumputer is made out of not GRUB. I mite be wrong about that. I don't know how Boot loaders work. It would make sents that in order for a boot loader to Load a OS one of it's jobs would be to tell the OS what hardware the computer is made out of. But to go back on myself agin this is still the job of BIOS so I don't know why GRUB would have to do it to...

I do know that Vi$ta if giving Linux hell because of it's bootloader. Seeing as how you are having so many problems... I would say... Can you do with out Vista? Do you realy need Vista? What can Vista do that XP can't?....

In any case what I am getting at is that if I were you I would just reinstall Ubuntu. You should not be having all of these problems. When I first swiched to Linux that was my fall back plan and it worked out well for me :) saved me a lot of truble and time. I must have reinstalled like 20 times :lolflag:

How dose Ubuntu run on the live cd? What would be Ideal would be to install the ISO on a USB Thumb Drive. Then boot into Ubuntu from the UBD drive. That way you could test the CDrom. 

Also, duble check the /etc/modprobe.d/alsa-base and make sure you spelled everything right... just one . and it is all over. Also, I know for a fact that if you only put (options snd-hda-intel) and not the (model=lenovo-ms7195-dig) part in there it will show the LEF and all that but they will not work. So, if it is not a "ch2/ch6" problem it sounds like a problem with that. Also, I put that info in "/etc/modprobe.conf" not "/etc/modprobe.d/alsa-base" But I think you have to put it in that if you installed the ALSA stuff yourself.... Or it mite be a Ubuntu thing or it mite be something you would want to try...

Anyway, to wrap it up.... Your best bet is to dich Vista, Keep XP (if you want) and Reinstall Ubuntu form scrach. 

P.S. Don't be scared to use the 64bit. I don't understand why somany people say it dosn't work??? It works grate no problems. Also, people say "Owe ya well most programs are not written for 64 so it dosn't even madder"... Well that is not true at all. That's just silly every program on my box is 64 bit. The only program that I can think of is Skype and you can still install the 32bit. I am sure programing can get way super Kool'r codeing for 64bit but it is still better then 32bit.

---

### Post by chargersfan420 on 2008-08-14
Okay, I've done quite a bit of reading and I have discovered a few more details.

First, i think you're right, and blaming GRUB was grasping at straws.  I don't think it's the Vista bootloader either...  The reason i kept Vista was because it's the only officially supported OS for the machine.  The only use i've had for it was installing the vista bootloader, verifying what my speakers are capable of, and reading DVD's / BlueRay discs (haven't tried yet but the optical drive is capable).  Hence the reason i'd like to get the issues resolved.

The Live CD works fine for me, and the optical drive was used to install Ubuntu, so i know it should work.  I also found that i could start Ubuntu with ACPI=off and the drive would work, but many other things don't (such as the power manager gauge, general system instability, etc).  Since it's a laptop, booting from a flash drive doesn't sound very efficient.

I have learned that linux has a long history of compatibility problems with ATA, more specifically Parallel ATA (which to my limited understanding means an IDE drive that is controlled by a SATA controller... something like that).  Some (ThinkPad specific) info i found here: [http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)
One thing mentioned there that had me thinking was this sentence:
"You must also make sure that the IDE driver (ide-generic) does not grab the devices before ata_piix. "
Sounds logical to me but i have no idea how i would go about that.  Perhaps my IDE module is causing problems?  I'm not even sure i need it.

Within hours of my first post, another Y710 user PM'd me to say he has the exact same issues.  We compared notes, and i discovered this:
Things we have in common:
- Ubuntu 8.04
- Lenovo Y710
- using GRUB 

Things we don't have in common:
- I'm on 64 bit, he's on 32 bit (so i think downgrading won't help anymore)
- I'm using Vista bootloader to boot GRUB.  It seems to me that this is not the problem then.
- I have the model with the T9300 processor in it, and his is a T8100.

I have also found a couple of contacts at Lenovo through their forums.  One said he'd get back to me with the differences in sound hardware between the Y510 and the Y710, and the other is a Linux guy so i'm trying to see if he can help...

---

### Post by chargersfan420 on 2008-08-15
Hey everyone,

I have an update on my sound problem.  Yes, i feel like an idiot.  I realized that the front of the laptop has a bass on/off switch, which was set to off.  I made the same stupid mistake with the wireless switch when i first got the machine.  By the way, i can't think of a single reason why the wireless switch would be useful... anyone?

Anyway, the sound is still a problem though.  I'm getting the two rear channels come out of the subwoofer.  The "surround" volume control still does nothing, and when i type:

speaker-test -Dplug:surround51 -c6 -twav

I get "rear left" and "rear right" both come out of the subwoofer, and the "center" and "LFE" channels don't make any noise at all.  The center and LFE channels in the volume control panel both change the volume of the channels being sent to the subwoofer.

Does anyone know how to fix this?

I'm still having problems with the optical drive... new idea - ditch ACPI and try out APM... any thoughts on this?  (if the optical drive works with ACPI=off, then can it be the cause of the problem?)

---

### Post by wyth on 2008-08-15
Just a quick update -- 

There was a kernel upgrade from 2.6.24-20-generic to 2.6.24-21-generic today.

The same problems remain: 

* Wireless doesn't turn on at boot
* Suspend fails with kernel panic

The 2.6.24-19-generic kernel does still work fine.  I haven't tried the non-generic kernels, nor have I filed any bugs yet.  Has anyone else?

---

### Post by HunterThomson on 2008-08-15
> **wyth said:**
> Just a quick update -- 

There was a kernel upgrade from 2.6.24-20-generic to 2.6.24-21-generic today.

The same problems remain: 

* Wireless doesn't turn on at boot
* Suspend fails with kernel panic

The 2.6.24-19-generic kernel does still work fine.  I haven't tried the non-generic kernels, nor have I filed any bugs yet.  Has anyone else?

Ya, no I have not filed any bugs... Wait I did add the lenovo ideapad y510 to the list of laptops that had backlight problems.... Like 4 month ago... And I think it was for a Kerenl problem.. Yes that is the bug I added too... That is why I was talking "Kernel Problem" from the git go. However, Now I am thinking it is maybe a problem with the way the Kernel and DE work together....

---

### Post by HunterThomson on 2008-08-15
> **chargersfan420 said:**
> Hey everyone,

I have an update on my sound problem.  Yes, i feel like an idiot.  I realized that the front of the laptop has a bass on/off switch, which was set to off.  I made the same stupid mistake with the wireless switch when i first got the machine.  By the way, i can't think of a single reason why the wireless switch would be useful... anyone?

Anyway, the sound is still a problem though.  I'm getting the two rear channels come out of the subwoofer.  The "surround" volume control still does nothing, and when i type:

speaker-test -Dplug:surround51 -c6 -twav

I get "rear left" and "rear right" both come out of the subwoofer, and the "center" and "LFE" channels don't make any noise at all.  The center and LFE channels in the volume control panel both change the volume of the channels being sent to the subwoofer.

Does anyone know how to fix this?

I'm still having problems with the optical drive... new idea - ditch ACPI and try out APM... any thoughts on this?  (if the optical drive works with ACPI=off, then can it be the cause of the problem?)

Good work :) By the end of this you will know quite abit about how Linux starts up :)

As for the sound.... Try other "model=" in the /etc/modprobe.d/alsa-base.
such as...

```
                             model=lenovo-101e
options snd-hda-intel...     model=lenovo-nb0763
                             model=lenovo-ms7195-dig

```

Or really anyof these...
```
ALC883/888 
 
          MODEL        DESCRIPTION   

	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  haier-w66	Haier W66
	  6stack-hp	HP machines with 6stack (Nettle boards)
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  auto		auto-config reading BIOS (default)

```


Also, It just skimmed through it but it seems you can set up what volume controle dose what.... look though this...

```
/usr/src/alsa/alsa-driver*/alsa-kernel/Documentation/ALSA-Configuration.txt
```

As for the ACPI.... Hum... Ya, I don't know much about that.... Yet.... I'll read up on it for my own sake. But, ya if you found an alternitive to it... Hell try it out... I think it mite also solve the backlight problem too....

Just a little FYI...

Parallel port means that the data is sent in "parrallel" across the bus like this...

1 | 0 | 0-> ----
0 | 1 | 1-> ----
0 | 1 | 0-> ----
0 | 0 | 0-> ----   CPU
1 | 1 | 1-> ----
0 | 1 | 0-> ----

As you can see the each bit is set parallel across the "bus"(the lines on the printed mother board) to the CPU. This requiers a lot of error checking because if all the 1's & 0's don't arive at the same time then it has to fide out wich one didn't get there on time and yada yada... This makes it vary slow...

Seral means that the data is sent one 0 or 1 one at a time down one line of the buss to the cpu and the line next to it sends data one 0 or 1 one at a time back to the device... Like a two lane highway... The two bus lines next to it can be used as anuther two lane highway. Like this...

010010100101001->
010010101010110<-
010010101010111->   CPU
010101001010101<-

This is way faster then parallel because there is like no need for error checking at all.

AND
Bit rate is the # of lanes it can use.

---

### Post by HunterThomson on 2008-08-15
Hey chargersfan420 thank you for turing me on to ACPI...

I have found some intresting info...

I beleve there is a high probability the backlight problem and your cdrom problem have to do with a buggy DSDT. I am going to recompile my DSDT and fix any errors I find and report back. (However, I am haveing problems so this may take some time...)

Just one tid bit to turn you on...

> If you like me have a reliability issue and have to boot with the noacpi flag and don’t have /proc/acpi/dsdt populated there is an another solution. If you are going to make a dualboot and got Windows available you could use this method.

    * Download windows binaries of iasl.exe by follow the link from [http://www.acpi.info](http://www.acpi.info)
    * Use start menu Run and type cmd
    * type

      path_to_iasl\iasl -d

Hopefully you ended up with a fully readable dsdt.dsl file that you could move into your Gentoo install. 


I am checking out this wiki right now...

[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

also check out...

[http://www.lesswatts.org/projects/acpi/overridingDSDT.php](http://www.lesswatts.org/projects/acpi/overridingDSDT.php)

---

### Post by HunterThomson on 2008-08-16
From what I read they put workarounds in the Linux Kernel for DSDT bugs... So, maybe one of these workarounds got messed up or taken out in the newer Linux Kernel and that is why rolling back the Kernel starts to fix some porblems...

I am really thinking this DSDT thing makes all the peces of the puzle fit to gether.... I can't see how this would not be the cause of the problems.

Problems it is extremly likely to be causeing...

Backlight...
Suspend....
Hibernation....
for sure your CDrom chargersfan420... 

OK... I was stupid... Well the documetation I was reading was unclear...
Anyway, I have now dissasembled and reasembled the DSDT.dat file with ASL... And guess what.... The Micosoft compiler is junk and mised some errors.... The Open Sorce intel compiler I used found and error and 12 wornings... I am going to play with it I'lll be back to tell you how it turns out....

```
DSDT.dsl 13624:                 Name (_T_0, Zero)
Error    4081 -     Use of reserved word ^  (_T_0)

ASL Input:  DSDT.dsl - 13995 lines, 402087 bytes, 6667 keywords
Compilation complete. 1 Errors, 12 Warnings, 0 Remarks, 36 Optimizations

```

_Read this for more info..._
[http://lwn.net/Articles/237085/](http://lwn.net/Articles/237085/)

---

### Post by HunterThomson on 2008-08-16
> **wyth said:**
> Just a quick update -- 

There was a kernel upgrade from 2.6.24-20-generic to 2.6.24-21-generic today.

The same problems remain: 

* Wireless doesn't turn on at boot
* Suspend fails with kernel panic

The 2.6.24-19-generic kernel does still work fine.  I haven't tried the non-generic kernels, nor have I filed any bugs yet.  Has anyone else?

FYI Arch Linux is on Kernel 2.6.26 .... So, don't get your hopes up

The wireles turn on at boot is a good job for a bash script....

#!/bin/bash
ifconfig wlan0 up


--------------------------------------
---------------------------------------

Have any of you with camara problems seen this...

[http://consumersupport.lenovo.com/lenovo/hints/2414/1414.html](http://consumersupport.lenovo.com/lenovo/hints/2414/1414.html)

It will not help but it is intoresting

---

### Post by HunterThomson on 2008-08-17
> "It seems unfortunate if we do this work and get our
partners to do the work and the result is that Linux works great without
having to do the work" (Bill Gates on Making ACPI Not Work with Linux,
[http://www.osnews.com/story.php/17689/B](http://www.osnews.com/story.php/17689/B) &#8230; n-Makin...)

For Sure... This is our problem With Suspend...With Hibernation... With backlight.

if you look at Page 3 of this thread you can read my discription of how BIOS works. Well, I tell you that some parts of the BIOS are loaded into RAM and used by the OS to know what hardware it has... The DSDT and ECDT do that.. BOTH of them are buggy... The DSDT has one fullon Error's and 12 wornings (wich are errors too) the ECDT has 2 full on Error's.

> The ACPI Specification defines the requirements for the DSDT (and everything else, for that matter) pretty explicitly. Intel's ASL compiler, iasl, used to compile the DSDT to AML from ASL, will throw errors and warnings if the underlying ASL is buggy. Unfortunately, Microsoft's ASL compiler allows many of these errors and warnings to sneak by. As a result, many OEMs write buggy DSDTs, and it turns out that Windows is very forgiving of bugs in the DSDT that get by Microsoft's compiler (not surprisingly).

What this means is that a DSDT that does not conform to the ACPI specification will work under Windows, even though it shouldn't. However, when you try to use it in Linux, where the ACPI developers expect that the DSDT is written to comply with the standard (and the Intel ASL compiler), the buggy sections of the DSDT are unsupported. If you have a buggy DSDT, ACPI may not be aware that certain devices exist. Or, if it is aware, it may not support all of their capabilites. If you have either of these symptoms (missing or incompletely supported functionality in /proc/acpi), then the cause may be a buggy DSDT. 

I am almost done fixing my DSDT.... I still have 2 warnings in my DSDT... I am running my fised DSDT now and still have the same Backlight problem... Hopefuly after I fix these two things it will be fixed. I be the Suspend and Hibernation are fixed now but I don't have any program installed to Suspend or Hibernate... I also don't have a big enugh Swap Partition to Hibernate... i.e. I have 2GB of ram and only 1GB of Swap. I will edit this post with new info. If I conferm any fixes to anything I will start a new reply...

```
DSDT.dsl  4620:                 Method (OGCD, 0, NotSerialized)
Warning  1086 -                            ^ Not all control paths return a value (OGCD)

DSDT.dsl  4673:                 Method (OGCA, 0, NotSerialized)
Warning  1086 -                            ^ Not all control paths return a value (OGCA)

ASL Input:  DSDT.dsl - 13987 lines, 401852 bytes, 6662 keywords
AML Output: DSDT.aml - 50055 bytes 1470 named objects 5192 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 36 Optimizations

```

Anyway, My advice to you is git cracking on fixing your DSDT. Each laptop with difrent hardware will be different. Even if you have the same hardware it is safer to just fix your own....

[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

We are lucky though :) At lest Lenovo was thinking of Linux. This is not common at all!
```

        Else
        {
            If (MCTH (_OS, "Microsoft Windows NT"))
            {
                Store (0x04, OSVR)
            }
            Else
            {
                If (MCTH (_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x02, OSVR)
                }

                If (MCTH (_OS, "Linux"))
                {
                    Store (0x03, OSVR)
                }
            }
        }

        Return (OSVR)
    }
```
Note: It dosn't through any errors but dosn't it look like there sould be an Else between Windows ME and Linux?...

------------------------------------
------------------------------------
Well, I still have not fix the two errors left in the DSDT and no errors in the ECDT. However, there is no in your face tags that point to them causeing backlight errors.... But, I am still sre that the DSDT and/or ACPI are the cause of the Backlight problems and for sure suspend/ Hibernation problems(Bcause that is what DSDT and ACPI do). There is however one more way to fix this problem. There is a program that I can use to compare the last known working Kernel to then next Kernel that has the problem.. It will then tell me exacetly what the error is... SO, what is the last working kernel?? Ubuntu 7.10... what was the last kernel it used? Each Kernel has is't own ACPI.

---

### Post by wyth on 2008-08-18
I'm *pretty sure* the kernel for 7.10 was 2.6.22 -- and I'm not certain of any sub-versions.  There must be some documentation of that stuff.  But at least in my case, I had 7.10 running just dandy, and that was off 2.6.22.

You're doing a hell of a detective job here.  I should be working, but I may just start poking around my DSDT.

**EDIT:**

For kicks, here's my recompiled dsdt file -- 12 warnings, 1 error, 36 optimizations:

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  4620:                 Method (OGCD, 0, NotSerialized)
Warning  1086 -                            ^ Not all control paths return a value (OGCD)

dsdt.dsl  4673:                 Method (OGCA, 0, NotSerialized)
Warning  1086 -                            ^ Not all control paths return a value (OGCA)

dsdt.dsl  6784:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6798:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6813:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6828:             Acquire (MUTE, 0x0FFF)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6842:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6857:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  6872:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  9508:                     And (CTRL, 0x1E)
Warning  1104 -                             ^ Result is not used, operator has no effect

dsdt.dsl 12982:             Name (_VPC, 0x00040000)
Warning  1097 -                      ^ Unknown reserved name (_VPC)

dsdt.dsl 12993:             Method (_CFG, 0, NotSerialized)
Warning  1097 -  Unknown reserved name ^  (_CFG)

dsdt.dsl 13624:                 Name (_T_0, Zero)
Error    4081 -     Use of reserved word ^  (_T_0)

ASL Input:  dsdt.dsl - 13995 lines, 402087 bytes, 6667 keywords
Compilation complete. 1 Errors, 12 Warnings, 0 Remarks, 36 Optimizations

```The [Gentoo How-To]("http://forums.gentoo.org/viewtopic.php?t=122145") has a [link to a page for a DSDT repository]("http://acpi.sourceforge.net/dsdt/view.php") that has fixed dsdt files for certain models (IdeaPads aren't there).  But apparently, [http://acpi.sourceforge.net](http://acpi.sourceforge.net) is outdated, and we're supposed to go to [http://www.lesswatts.org/](http://www.lesswatts.org/) -- and I'm guessing either [http://www.lesswatts.org/projects/acpi/](http://www.lesswatts.org/projects/acpi/) or [http://www.lesswatts.org/projects/acpi/overridingDSDT.php](http://www.lesswatts.org/projects/acpi/overridingDSDT.php).  But I don't find any DSDT repositories there.

[B]EDIT:
[/B]
From what I can gather so far, all that's needed for the Name (_T_0, Zero) error is to change _T_0 to anything else?  Did anyone else come across that (and try it)?

---

### Post by chargersfan420 on 2008-08-19
I'm having similar results here on the Y710.  When i first recompiled, i had 2 errors, 8 warnings and 859 optimizations (why so many more than you guys? lol)

I've managed to whittle it down to 1 error, 6 warnings, or 0 errors, 7 warnings.  Have a peek at mine:
```
$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   382:         And (Local0, 0x42)
Warning  1104 -                   ^ Result is not used, operator has no effect

dsdt.dsl  4579:                         Method (HKDS, 1, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (HKDS)

dsdt.dsl  5125:                             Name (_VPC, 0x00050440)
Warning  1097 -                Unknown reserved name ^  (_VPC)

dsdt.dsl  5134:                             Method (_CFG, 0, NotSerialized)
Warning  1097 -                  Unknown reserved name ^  (_CFG)

dsdt.dsl  5150:                             Method (VPCR, 1, Serialized)
Warning  1086 -   Not all control paths return a value ^  (VPCR)

dsdt.dsl  5175:                                         Name (_TX0, 0x00)
Warning  1097 -                            Unknown reserved name ^  (_TX0)

dsdt.dsl  5402:                             Method (_CFG, 0, NotSerialized)
Warning  1097 -                  Unknown reserved name ^  (_CFG)

ASL Input:  dsdt.dsl - 7600 lines, 273589 bytes, 3049 keywords
AML Output: dsdt.aml - 28531 bytes 730 named objects 2319 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 0 Remarks, 859 Optimizations

```

I have tried changing _T_0 to a bunch of different things, and either i get the 'use of reserved word' error like you, or 'unknown reserved name' like shown above with my _TX0 attempt.

I also have the _VPC error like you do, and i found only one line in my DSDT that mentions it:
Name (_VPC, 0x00050440)
I found i could suppress the error by commenting out the line, but i don't know if that's a good idea because i don't know what it does.  The only thing googling could tell me about VPC is it's short for virtual pc...?

I can't seem to boot with the DSDT i've modified either... not sure what i'm doing wrong.  I recompiled, and copied dsdt.aml to /boot, and set up a NEW grub option like this (by copying current grub entry, commenting out initrd, and replacing it with my custom DSDT):
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic NEW DSDT TESTING
root		(hd1,5)
kernel		/boot/initrd.img-2.6.24-19-generic root=UUID=a843a703-0690-44c7-bf2d-385d09c9c5f9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
initrd		/boot/dsdt.aml
quiet
```

When i try to boot with that, i get:

[   1212.703524] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)

I tried a couple of things, and the number used to be [30.xxxxx]... where did i go wrong?

---

### Post by HunterThomson on 2008-08-19
Hello wyth :) Thankyou for joing the party :) I thought I was all alown on this one.

Ya, there is not vary much "Good" documentation on this stuff.

One good thing, I was wrong. I was just playing it safe so I didn't mess up anyone's computer. Anyone useing the same BIOS as me can use my DSDT :) So, I have attached it for you. Pleas try it out and test suspend and hibernation. There are still two errors left but I think I know how to fix them.... Reverse engineering is a real pain in the ***. I also can not find any documentation on AML code so I don't know what anything meens without just reading the 3,000+ lines of code and deduce the answer. I'll get back to you with that...

Yes, your wright all you have to do for the _T_S is change it to T_S... Realy you could change it to anything like BoB or MSSUCKS. But I just changed it to T_S. All of the Mute's just had to be changed to Mute, 0xFFFF. I just deleted the whole 1104 stucture... If it has no effect then who needs it. I serched the code for the retrun value and it is not used anyware.... This is also what someels did when he got this warning. I don't remember what I did with the  1097's I think I just changed them from _VPC to VPC. It seems that you can't have a Under_score at the start of name. 

Anyway, you don't have to do any of that you just have to download my DSDT.aml... gunzip it and do this....

Put it in a direcotry (I made a DSDT directory to play around in the ~home directory is fine though).

mkinitcpio is built into the Archlinux Kernel but I don't know about Ubuntu.

So type this

```
sudo apt-get install mkinitcpio
```

Then you have to put it in this directory....  I think maybe the Arch dev's set it all up a nice way maby if you just install it or Ubuntu didn't make the file system all prity like Arch you mite have to make your own directory on the /root-partition/direcotry... You can read up on it.... Or type... locate initcpio and look to see if any thing pops up((That is what I did and then read the kernel hook code and it told me where to put the DSDT.aml file)) 

Well in Archlinux I had to rename the DSDT.aml file to custom.dsdt and put it in... /lip/initcpio... I did it all with this one line wile in the directory contaning the DSDT.aml file... ((Did you know the mv or cp comand is also the comad to rename files... such as... mv ~/bob.txt ~/bob420.txt))

```
cp DSDT.aml  /lib/initcpio/custom.dsdt
```

Then I added the hook... dsdt to the file... /etc/mkinitcpio.conf. If you do this you don't even have to rebuild the kernel... I don't think.. You can try it and then read the dmeseg log to see if it loaded it... Or you can just compile a new Kerel RAM disk to Boot into and add it to the GRUB menu. To do that do this next wile in the directory contaning the DSDT.aml file NOT the Renamed file.

```
mkinitcpio -g /boot/kernel26-dsdt-custom.img
```

Then enter the grub menu list...

```
sudo nano /boot/grub/menu.lst
```

Add this after the menu entry that is alredy in there...
(NOTE: You see the root=???? put the corect /dev location in there for your root partition) ((NOTE:NOTE: You know it is probaly better to advize you to just look at the menu entry that is alredy in there and just copy the root=/dev/??? and the root (hd???) from there so you don't get it wrong))

```

# Gonzo Custom DSDT Kernel
title Gonzo Custom DSDT Kernel
root (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26-dsdt-custom.img

```

Then reboot... enter the grub menu list selection and select the Gonzo Kernel. 

I will get the other two wornings fixed this weekend. I will also start to try out other Kernels. Once I find out what the problem is in the newer kernel I will send it off the to the real Kernel dev's. I will also try to pach the Kernel myself.... Should just be some cut and past... we'll see....

---

### Post by chargersfan420 on 2008-08-19
Is that a Gentoo-specific command?

bash: mkinitcpio: command not found

Edit:  perhaps Gentoo is not the right word.. Archlinux?  I've been staring at that Gentoo help page too long.

P.S. Please forgive the noob status.

---

### Post by HunterThomson on 2008-08-19
[B][COLOR="Blue"]Hay wyth you updated your BIOS... If you boot into the Ubuntu 7.10 try turning down the brightness and then back up agin... Dose it stop getting any brighter after about the 60% mark on the bar???
[/COLOR][/B]

FYI for everyone that is useing a diffrent BIOS vertion or a Y710 i.e. anuther BIOS. This is how I am finding out how to fix the DSDT. 

I google for the error code. like so...


Warning  1086

OR..

Warning  1086 DSDT

Then I normaly find a Bugzilla email log...With the ansor. The Bugzilla mailling list is the proper place to be if you whant to fix your DSDT. Or play with the Kernel. However, I would advize saving everyone some time and hassel and just try googleing first and fixing as much as you can "In a Safe manner". Ya, just comenting out lines of code is not a good idea... I did remove some code but it was not being used. However, on the same note all this mite be a big wast of time. Not all of the code is used anyway. Some of it is OS dependent code i.e. if your not running windows vista then the code is not used or yadayada.... But probaly it is.... And the reverbe of that note is that you can also use ACPI flags to lie to the BIOS and tell it that it is any OS you wan't. 

Anyway, this all can get Extremly indepth. Just google for the error or worning + the #. If you have any questions that you can't fide the ansor too, you can ask here and I probaly have the solution. Lets make working DSDT.aml file for all the Ideapad laptops and BIOS's :) and I will write a HOW TO and post it here.... Hell I will write a Bash script to install them:)

I wish I could just find a book on how to code in AML. Or a IDE for AML or a tex editor with the syntax.... If I could code in AML there are some super kool things I could do.

I am thinking now that at lest the backlight problem is a real bug in the ACPI code in the Kernel. I also think there is a bug in the new BIOS I installed.... Arg... Even if I boot into the Ubuntu 7.10 cd The backlight stops getting any brighter after the 60% mark....Arg... I am going to edit the BIOS posts and worn agist upgrading the BIOS untill we know more about the problem...

((Also, someone that has a Y510 and has not updated the BIOS i.e. you are using BIOS vertion ?????26 not ?????29. Pleas post your DSDT.dat or .dsl. So, I can see if ther is any change to it)) 

(( Also, I have come to find out that there is a BIOS vertion ?????30 that can not be downloaded from the lenovo web site but is on some Y510 notebooks and I have a link to it.... I am to scared to try it though...))

---

### Post by HunterThomson on 2008-08-19
> **chargersfan420 said:**
> Is that a Gentoo-specific command?

bash: mkinitcpio: command not found

Edit:  perhaps Gentoo is not the right word.. Archlinux?  I've been staring at that Gentoo help page too long.

P.S. Please forgive the noob status.

Thank you too for helping out. Lets make a bug free DSDT for the Y710 :)

Nope... you just need to intall it


sudo apt-get mkinitcpio

There are no disto spicific commands. There are disto spicific filesystiem structures though. Such as, Archlinux used the BSD stile rc.conf rc.d files...

Also, DO NOT just coment out thouse lines in the DSDT !

---

### Post by wyth on 2008-08-19
> **HunterThomson said:**
> **[COLOR=blue]Hay wyth you updated your BIOS... If you boot into the Ubuntu 7.10 try turning down the brightness and then back up agin... Dose it stop getting any brighter after about the 60% mark on the bar???[/COLOR]**
 
I updated my BIOS (2.6.24-21-generic), but I'm on 8.04.  I don't even think 7.10 will take 2.6.24-21-generic, although I'm not sure.  Tell you what: I have an empty partition I keep on my Y510 to toy with, and I'll install 7.10 there and see what's up. (Actually, would it be just as easy to do this in a virtual machine?)
 
Yeah, I'm trying to follow along here and fix what I can. I just finished teaching a summer session and have a load of work before I start teaching in the fall, but I'm following along.

---

### Post by chargersfan420 on 2008-08-19
Your suggestion to:
sudo apt-get mkinitcpio

Resulted in:
E: Invalid operation mkinitcpio

However, i think i have it working... I downloaded a script from this page ([http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)) and used it to incorporate my DSDT.aml into a file i created by typing

mkinitrd -o initrd-test-file.img

I think i understand basic concepts somewhat, but this is mostly over my head.

Then i went back to my GRUB test entry, and changed the initrd entry to point to my initrd-test-file.img (after incorporating DSDT.aml into it using the script) and it actually booted this time.  It also says there that to test out if you actually booted with the new DSDT, try:

dmesg | grep DSDT

To which i get:
```
$ dmesg | grep "DSDT"
[    0.000000] ACPI: DSDT 7FED8420, 77A6 (r2 LENOVO CB-01     6040000 MSFT  2000001)
[   24.661565] ACPI: Looking for DSDT in initramfs... successfully read 28531 bytes from /DSDT.aml.
[   24.661581] ACPI: Table DSDT replaced by host OS
[   24.661583] ACPI: DSDT 00000000, 6F73 (r2 LENOVO CB-01     6040000 INTL 20061109)
[   24.661586] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"<6>Using local APIC timer interrupts.
[   25.062428] ACPI: EC: Look up EC in DSDT

```

That looks good to me, i think it's working now :)  Although i notice that it says it read from /DSDT.aml... Do you think that's part of the img, or it is pretending that /boot is the root fs?  I don't have a DSDT.aml in / (probably irrelevant anyway).

However, still no CD drive :(  I also noticed before that i was wrong about the SD card reader, it's not working.  I had to plug in a USB style one to read cards (which works fine).

I still have all of those errors in my previous post, but at least now i know that i can boot with the new DSDT.

So, suppose i correct one of those errors and it makes my CD drive work properly in Ubuntu... If I took such findings over to the Lenovo forums, do you think it would incline them to fix their buggy DSDT?  Or would that be like waiting for hell to freeze over, as suggested in (i think) the Gentoo article?

---

### Post by wyth on 2008-08-19
Update:

I've installed 7.10 in a virtual machine, and the latest kernel on that is **2.6.22-15-generic**.  I *believe* that one worked fine.  I'm going to go ahead and install it on my spare partition in a while and see what's up.

**Edit:**

7.10 with the 2.6.22-15-generic kernel has backlight wireless working on startup.  Need to check suspend/hibernate -- can't right now.  If it all works, should I post the dsdt file here?

---

### Post by chargersfan420 on 2008-08-20
Sounds like it would be worth comparing to the 8.04... 

But perhaps i don't understand this fully.  The DSDT is provided by the BIOS, right?  Why would the version of Ubuntu make a difference if any OS is being fed garbage code?  Is it because they have already put workarounds into the kernel, like Windows did?  

And if that's true, couldn't they write some code to attempt to fix the DSDT and save its own copy?

---

### Post by wyth on 2008-08-20
Yeah, that's what I'm not clear on.  I'm waiting for HunterThompson's response on this.  But 7.10 uses a different kernel, and that may have something to do with it.

But suspend and hibernate work on 7.10, although when it resumes, wireless is off and the screen is at its dimmest.  Turn the kill-switch off and back on, and wireless snaps back up.

As far as the backlight goes, there are nine settings, the fn-arrow keys work correctly, and the top is much brighter, I believe, than on 8.04.  However, the top three are all the same; so it's really only about seven settings.  

So I'll leave this my spare partition, and whatever files are needed for comparison, I'll post.

---

### Post by HunterThomson on 2008-08-20
> **wyth said:**
> Update:

I've installed 7.10 in a virtual machine, and the latest kernel on that is **2.6.22-15-generic**.  I *believe* that one worked fine.  I'm going to go ahead and install it on my spare partition in a while and see what's up.

**Edit:**

7.10 with the 2.6.22-15-generic kernel has backlight wireless working on startup.  Need to check suspend/hibernate -- can't right now.  If it all works, should I post the dsdt file here?

7.10 with the 2.6.22-15-generic kernel has backlight wireless working on startup.  Need to check suspend/hibernate -- can't right now.  If it all works, should I post the dsdt file here?[/QUOTE]


Hum... The backlight "did" go to full brightness, Really got brighter 10 times.... Well, I will wait untill I know for sure that it is not causeing anyproblems before I take down the "[COLOR="Red"]Do not update BIOS[/COLOR]" warning. I am haveing problems. I mite try and flash my BIOS agin. Maybe something whent wrong when I did it before. What I realy want to do is download that *****30 BIOS. It is for a Y510. Kind of risky to do that though. If it dosn't work... Ya, I am going to stick with the ***29 :)

Thankyou, Wile there is certanly problems with the DSDT file in the BIOS. It dose seem that it is a problem with the ACPI in the newer Kernel is the problem. But, we should still run a bug free DSDT as a first step in finding/fixing the problem. I will start on the 2.6.22 kernel and then move up one by one untill things are messed up :) 

Chargersfan420 the DSDT fixing mite fix the Optical dirve for you. I will go through the list of errors you posted this weekend. I just don't have time on the weekdays.

P.S. I missed a cridical step in the loading of the cutome DSDT at boot time.... 

initcpio is a Kernel moduel.. The Archlinux Kernel has it built in by defult. I don't know about Ubuntu. However all you have to do is install it.

Then you will have to add the... dsdt    hook in.... /etc/mkinitcpio.conf

---

### Post by HunterThomson on 2008-08-20
Owe hey, The BIOS is not a part of the OS i.e. linux. It is on the system ROM cip. So, no you don't need to edit you DSDT agin if you install a new OS. Only if you install a new BIOS AKA Flasy your BIOS. 

Normaly, at boot time parts of the BIOS programs are loaded into the RAM to be use by the OS to tell it what hardware the computer is made out of and what that hard ware can do. One of these things that is loaded into the RAM is the DSDT. You can't change that fact in Wincrap but Linux is alsom so you can install a Kernel modual wich will have the linux Kernel look for a new DSDT file a directory in on the /boot direcotry. If it finds it the Kernel will load that DSDT file into the RAM and get rid of the one that it is supose to load that is one of the BIOS files stored on the system ROM.

I guess the DSDT and a few other files in the BIOS on the system ROM are the ACPI.

Now The OS kernel has a part of the Kernel that interpits the ACPI files on the BIOS and uses them to do stuff like suspend to RAM and Suspend to Disk AKA Hibernation. Also, how much power can be given to the Backlight and what hardware keys are on the keyboard. So, ether the ACPI files like the DSDT OR the ACPI inturpeting part of the OS Kernel can be causing the problem.... OR even higher level things. But seing as how the problems we are haveing are not disto spisific and the onely comon thered is the Kernel and the BIOS/DSDT-File.... It seems not to be higher level stuff like Xorg or the Desktop Envierment.

---

### Post by HunterThomson on 2008-08-20
Owe hay, I am vary tired after work. I work 10hr days.... I can't waite untill I get my A+ certification so I can play on computers all day but those tests cost a bit of $.

sudo apt-get install mkinitcpio

.... I am also not + that it is in the Ubuntu repo's but I bet it is.

Owe, hay good work chargersfan420 that is how you can have the Kernel module initcpio load a cusome DSDT.aml file insted of the one it is supose to from the BIOS on the system ROM chip. That is also how you can make sure it is loading he DSDT file you want it to load and not the one from the BIOS on the System ROM chip.... it did load it. I just open the dmesage log in gedit and serch for the word "custom".

And Yes the Linux Kernel ACPI moduel dose have a few things in it to deal with bugy DSDT files in the BIOS. There also a new ACPI for each Kernel so the new one mite just be buggy ( I think it is). However, auto debuging and rewriteing of file is beond it's capability. So ya, that could have changed in newer Kernel. And ya using a older kernel is what using the old Ubuntu 7.10 is all about it is just kind of a fail safe way to do it. And I wanted wyth to test if he had the same problems with it that I was haveing with 7.10 because we both have the BIOS update.

---

### Post by chargersfan420 on 2008-08-20
> **HunterThomson said:**
> 
Chargersfan420 the DSDT fixing mite fix the Optical dirve for you. I will go through the list of errors you posted this weekend. I just don't have time on the weekdays.


Thank you very much, I would greatly appreciate the help.

I found a couple of good links about this stuff here:
[http://www.acpi.info/]("http://www.acpi.info/")
[http://developer.intel.com/technology/iapc/acpi/]("http://developer.intel.com/technology/iapc/acpi/")

I notice when i compile my dsdt.dsl file, i see this right at the top of the error list:
Supports ACPI Specification Revision 3.0a

So i have been reviewing the 3.0a documentation.  The odd thing is that most of the errors I'm having have no relation to any of the things in that 627 page document... there are lots of similarities, such as PNP0C(XX) numbers, and _(XXX) variables... but the ones I have in my error list such as _VPC and HDKS just don't appear on the documentation anywhere.

The one error i have corrected was something like "*pnp0c14" <- string must be alphanumeric only.  Taking a quick scan of the DSDT.dsl i notice there were lots of pnp0cxx numbers, so i figured the * shouldn't be there.  Then i notice the documentation has lots of listings for pnp0c0(x) devices and pnp0c2(x) devices, but nothing for pnp0c14... that's odd.  I have a feeling it might have something to do with the lid.  I don't ever recall telling Ubuntu to do NOTHING when i close my lid, but that's what happens, and that's just how i want it.  Is this a default behavior?  (Actually, the screen goes black like a screensaver, but it doesn't power off the monitor)

Perhaps the different kernels are established to work with a different ACPI specification revision.  I haven't searched through any other versions of the documents yet... this stuff is starting to burn out my brain and waste most of my free time.  Just thought i'd toss a few ideas out there.

---

### Post by HunterThomson on 2008-08-21
Thankyou chargersfan420 for the links. That is just what I was looking for:)

The PnP stuff is for Plug n' Play devices such as PnP/PCI cards like a sound card. The lid swich is actually cald LID something like LIDX. The LCD screen is cald LCDD. When it is seting up stuff the a old school monitory (a CRT cathode-ray tube) it is cauld CRT something like CRTX.

I checked what I did to fix the errors and this is what I did to fix my errors.

changed all the... _T_S to... T_S

Changed all the mute stuff such as this... MUTE, 0x03E8 to... MUTE, 0xFFFF

I just deleted the whole strcture for both of the 1097 warnnings ...Unknown reserved name ^  (_CFG)... Because ya your right if it is not used in the 3.0a then it dosn't need to be in there.

Agin, we should fix the DSDT but I am thinking that it is going to take more then that to solve our problems. Kind of a Da' statement do to the fact that it worked befor and the BIOS didn't change the OS did so it is a problem with the OS or more spicificly the ACPI implimentation in the Linux Kernel. 


Chargersfan420 you can move into the directory where the DSDT."dsl" file is and then gzip it by just typing gzip DSDT.dsl.... Then post it and I will fix it. I alredy know how to do it so hell why spend your time. Well, you can do it if you want to learn more stuff. That is why I am doing all of this. The backlight is not really all that big of a deal. It is bright enugh. If I didn't know better I would not even know there was anything wrong ;)

As for posting about this on the Lenovo forums. It is a good idea. However, I think we whould wait untill we have bugless DSDT file to post over there. We should have them by this the end of the weekend. We should post then with a request to Lenovo to start compileing there DSDT file with the Open Sorce intel Compiler. That way we will no longer have this problem. I don't really see why they don't do it anyway. Lenovo now owns IBM. IBM dose a lot for Open Sorce and Linux. Hell you can buy a Y510 with Linux pre-loaded. I would also like to request that they start to post BIOS.DAT files not just the EXE file. It is just a pain in the *** and there is no need for it. The idea pad has the BIOS flashing program build into the CMOS utility.

I did email Lenovo a nice well written letter to that effect 5days ago... No responce. I am not vary happy about that. They could have just said "Thankyou for likeing our product and sujesting it to your friends. But, we don't care what you think."

Hay could someone that has not upgraded there BIOS post there DSDT file. For testing/fixing.

Also could someone that has not upgraded there BIOS pleas boot into a Ubuntu 7.10 Live CD and test out the backlight. See if all 10 steps of the brightness really make it brighter 10 times. I just want to make srue.

---

### Post by chargersfan420 on 2008-08-21
Hmm, the plot thickens.

I decided i would try installing Ubuntu 7.10 on one of my two spare partitions.  Since i'm at home now, I'll have to use another OS to burn a disc.  Sigh.

What the heck.  Let's try booting with ACPI off... Earlier i set up /etc/fstab to try to force mounting the drive (in vain)... even with ACPI off i still see "/dev/scd0 device does not exist" during startup, even though the drive still works (under IDE i think).  When i hit eject on the drive, it blinks and the HDD light blinks at the same time... it thinks about it, until i jam the button furiously and it finally pops open.  It makes a burnout noise, as if the CD was spinning the whole time and it rubbed along something when i finally got the lid open.  Okay, sure, not the first time i have seen it do this.  But it works fine in my other OS's...

So next i try out XP.  During the splash screen, i get a half-second flash of some blue screen of death, followed by instant reboot.  I have no idea what the BSOD says.  I get the same results 4 more times.  Never tried safe mode, some other time perhaps.  I'm on a mission here.

Vista loads without trouble, seemingly faster than before.  Unfortunately, there's no preloaded ISO burning software.  The only free one i know of gets quickly downloaded before it informs me that there's a 300 MB limit on ISO burning during the trial version.  This of course is why open source is desirable.  I pay for the equipment, it should do its job, right?  Not only that, but the optical drive again refuses to open, which of course ends in the same burnout pattern.  Weird, i swear it worked fine before... sorta.

I'm at a total loss as to why the XP drive is toast.

I also PM'd a Lenovo guy from the forum... i sent him the Gentoo help link and asked him if my Y710 is ACPI Spec 3.0a compliant.  I'll see if i get a response.

Attached is my dsdt.aml.

By the way, i just got a Y510 shipped to the office... I have no plans of putting Ubuntu on it, because it's for another employee... bu i'm in no hurry to get it configured for the guy... I'm thinking i could probably obtain a fresh copy of the DSDT if i use a live CD and a flash drive... wouldn't have to touch the HDD...

---

### Post by chargersfan420 on 2008-08-21
Whoops.  I suppose you wanted the .dsl, not the .aml.  Here ya go.

EDIT: I suppose i should also mention the two fixes i put in there already.

As i stated earlier, i found pnp0c14 originally as *pnp0c14, and another one said "(something) doesn't return (something) on all paths, so i added in "Return (0x00)" somewhere, but now i forget where.  

Note to self: keep better records of what was changed... haha

---

### Post by HunterThomson on 2008-08-22
First off, Ya send me the DSDT from the new Y510. It would be Best if you get it from with in Windows. Folow these directions...

> * Download windows binaries of iasl.exe by follow the link from [http://www.acpi.info](http://www.acpi.info)
* Use start menu Run and type cmd
* type

path_to_iasl\iasl -d

Hopefully you ended up with a fully readable dsdt.dsl file that you could move into your Gentoo install.

That seems to be missing a step.... but hay try it for me just like that. Also, it dosn't realy mader what form the DSDT is in .aml .dsl .dat whatever.

Also, could you hit the F2 at boot up and check to see the BIOS vertion on it for me. I would like to know.

I'll go ahead and fix your DSDT tomarow and post it. 

Um... A grinding, slideing, scraping, nose.... That dosn't sound good... I hope everything is ok.... 

Also, did you know that you can eject your optical drive by typing this comand at in the shell...
```

sudo eject /media/cdrom

OR.. if there is a dvd in there

sudo eject /media/dvd
```

Also, here is a free iso burning program for windows :guitar:

---

### Post by Sonyadora on 2008-08-24
I just purchased an ideapad y150 and I love it!  I was hoping that someone here could help me figure out how to get the dial up modem working though.  I'm new to Linux and I think I might have screwed something up fiddling around.

I followed the dial up modem instructions on ubuntu's support pages and ran scanModem.  The results: 

> --------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008
 scanModem update of:  2008_08_19

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 5986:0200 Bison 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	17aa:3d96	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 23:        348        351   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   30.510152] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   30.510188] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: 
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-02: ALC883 Analog : ALC883 Analog : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfeaf8000 irq 23

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x17aa3d7d
Revision Id: 0x100700
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573055

The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for Upgrading snd-hda-intel and its dependent driver set are at:
[http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         344728  3 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=17aa:3d96
IRQ=23
HDA=8086:284b
SOFT=8086:284b.HDA
CHIP=0x10573055
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  17aa:3d96 
    Softmodem codec or chipset from diagnostics: 0x10573055
                               from    Archives: 
                        The HDA card softmodem chip is 0x10573055
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd


This was quite an overwhelming amount of information for me, but it seemed like I should be using ALSA drivers so I followed the instructions here: [https://help.ubuntu.com/community/DialupModemHowto/AlsaModem](https://help.ubuntu.com/community/DialupModemHowto/AlsaModem) and installed the slmodem-daemon and slmodem-source packages using synaptic. and ran sudo /etc/init.d/sl-modem-daemon restart and got this output:

Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... snd_atiixp_modem.
FATAL: Module ungrab_winmodem not found
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

Well, that made me think I needed to follow the instructions  here: [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink)

At the first step to compile the driver things seemed to be working out, but failed halfway through.  The log file looks like this:

>  dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.24-19-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.24-19-generic/g ;s/#KVERS#/2.6.24-19-generic/g ; s/_KVERS_/2.6.24-19-generic/g ; s/##KDREV##/2.6.24-19.36/g ; s/#KDREV#/2.6.24-19.36/g ; s/_KDREV_/2.6.24-19.36/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_clean -k
dh_installdirs lib/modules/2.6.24-19-generic/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux KVERS=2.6.24-19-generic
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc -I/usr/src/linux/include -o kernel-ver kernel-ver.c
kernel-ver.c: In function ‘main’:
kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this function)
kernel-ver.c:11: error: (Each undeclared identifier is reported only once
kernel-ver.c:11: error: for each function it appears in.)
make[2]: *** [kernel-ver] Error 1
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/sl-modem'
make: *** [kdist_build] Error 2

Clearly, I'm in way over my head, since I don't understand just what all the commands were meant to do anyway, I'm not able to make sense of where they went wrong.  Any guidance would be appreciated.

---

### Post by HunterThomson on 2008-08-24
Well, unforchanatly this is not the best thread for this question. If you started a new thread then anyone could come across your question and help you out. However, if you post in this thread then you are limited to only people with Lenovo ideapad's. I would highly sugjest you start a new thread in the newbee section or the network section. 

Before I would start with all of this. Make sure all the setting in the PPP program your using are corecct. If they are then try a new PPP program to make the conection. Listen if you can hear the modem make nose. If the modem is makeing noise then it is not a ALSA (Sound problem). I would also check to make sure that the "Caller" volume bar is not muted in the ALSAmixer (The sound applet thing). You mite what to get the ALSA working first the instrucitons are on page one of this thread.

Here is a web page that shows how to set up sevral difrent PPP programs.
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by Sonyadora on 2008-08-24
> **HunterThomson said:**
> Well, unforchanatly this is not the best thread for this question.  However, if you post in this thread then you are limited to only people with Lenovo ideapad's. 

That was the idea.  I've cross posted in networking, but I wanted to get the attention of people with similar hardware to see if they have also had problems (I'm guessing not, since I haven't seen much talk of dial up skimming the two threads about this model laptop but it couldn't hurt).

> 
Before I would start with all of this. Make sure all the setting in the PPP program your using are corecct. If they are then try a new PPP program to make the conection. Listen if you can hear the modem make nose. If the modem is makeing noise then it is not a ALSA (Sound problem). I would also check to make sure that the "Caller" volume bar is not muted in the ALSAmixer (The sound applet thing. You mite what to get the ALSA working first the instrucitons are on page one of this thread.


The settings are correct in the PPP programs I've been using as far as I can tell.  I've tried the Smartlink dialer, GnomePPP, and using wvdial from the command line.  None are able to detect the modem.  It does not make any noise.  The ALSA is working, at least for music purposes, including muting with headphones, I worked through upgrading it and smoothing out the quirks using this thread before I started working on the modem issue.

---

### Post by chargersfan420 on 2008-08-25
@ Sonyadora - it seems like an appropriate place to me, but what do i know, i'm a newbie too.

I don't know much about dial up systems (do people really still use those?), but i was a little curious if booting with ACPI=off might solve your issue.  For some reason, it temporarily fixes my optical drive... sort of.

---

### Post by HunterThomson on 2008-08-25
Owe ya, this is a fine place to post :) If you have a lenovo Ideapad you can post whatever you want here :)

I was just saying you mite find more help if you also started a new thead.

I don't think anyone has tried to use the modem before on these laptops. Maybe you need to intall a driver for it??? I think Ubuntu like installs every drive in the world on the system though... I just don't know.

--------------------

chargersfan420.... Sory for not going through you dsdt file yet.. I caused some problems for myself.... I had the stupid though of "Hum... Why don't I try a reinstall of Archlinux" ..... Nightmare situation..... I'll get to work on it as soon as I can. Archlinux takes for ****ing ever to install and setup.....

---

### Post by Sonyadora on 2008-08-25
I live in a rural area.  Dial up and satellite are the only options, and satellite is too expensive.  I'm using the wireless at my workplace right now.  I love this laptop, and I don't want to get rid of it, but I also don't want to go back to Windows.  I think I will just post this directly to the linmodems ML if no one here has tried to get the modem working on the ideapad.

I'm also curious to see if people have gotten S-Video working? I haven't tried it yet, but I see a few posts from people asking about it, which is a concern to me as I was hoping to be able to hook it up to the tv to show pictures and whatnot.

For some reason I can't get the player to play dvd movies either, although I can burn cds and read data disks just fine.  I opened totem from the terminal and got the following:

> ** (totem:9404): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***

libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).

(totem:9404): GStreamer-CRITICAL **: 
Trying to dispose element test_dvdsrc, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


If anyone knows what the issue is here, please let me know.  Don't let me be condemned to Vista!  :)

---

### Post by gep642 on 2008-08-25
Concerning the Y710:

As it turns out, a better choice than:
```
options snd-hda-intel model=lenovo-nb0763
```

in the /etc/modprobe.d/alsa-base file is:

```
options snd-hda-intel model=6stack-dell
```

It's not a perfect solution, but, when set on 8 channel mode, all of the speakers work. The front channels correspond to the front speakers, the side channels correspond to the speakers near the LCD and both center channels (center and LFE) are through the sub woofer. I suppose it would be ideal to have the correct channels mapped to the correct speakers, but I haven't had a chance to look into how that would be done.

---

### Post by chargersfan420 on 2008-08-26
Confirmed, that fixes sound for the Y710.  It sounds beautiful, better than Vista.

Optical drive still a problem.  I have found several bug reports that sound a lot like my problem:
[BUG#8196]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8196")
[BUG#21860]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/21860")
There are others, but these seem the most relevant.  8196 suggests some workarounds in building a custom kernel to make sure that the ide-generic module gets loaded early, but i am not really sure how to do this.  21860 suggests at the very end that the problem still persists in Hardy but was no problem in Gutsy.  It appears that this problem has been fixed several times over the life of Ubuntu and it keeps recurring.  Definitely looks like a kernel issue... fixing the DSDT may help, but i think we would also have to look at the SSDT...?

I will try installing Gutsy on a spare partition tonight and see if that makes a difference.

```
npeirson@npeirson-laptop:~$ lsmod | grep ata
pata_acpi               9856  0 
ata_generic             9988  0 
ata_piix               24196  5 
libata                176432  3 pata_acpi,ata_generic,ata_piix
scsi_mod              178488  4 sbp2,sg,sd_mod,libata

```
```
npeirson@npeirson-laptop:~$ lsmod | grep ide
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
video                  23444  0 
output                  5632  1 video
usbcore               169904  6 uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
ide_cd                 35488  0 
cdrom                  41512  1 ide_cd
ide_generic             2560  0 [permanent]
ide_core              136600  2 ide_cd,ide_generic

```
```
npeirson@npeirson-laptop:~$ ls -al /proc/ide
total 0
dr-xr-xr-x   2 root root 0 2008-08-26 11:52 .
dr-xr-xr-x 145 root root 0 2008-08-26 04:31 ..
-r--r--r--   1 root root 0 2008-08-26 11:52 drivers

```
```
dmesg
...
[   46.944375] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   46.944379] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   46.944696] Probing IDE interface ide0...
[   47.510285] Probing IDE interface ide1...
[   48.086313] fuse init (API version 7.9)
[   48.097485] ACPI: SSDT 7FED733D, 02ED (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[   48.097648] ACPI: SSDT 7FED6CCE, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
...
```

---

### Post by wyth on 2008-08-26
Sonyadora,

I can't help you with the S-Video, but you should probably look at these pages:

DVD: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Dial-Up: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by chargersfan420 on 2008-08-28
Gutsy was no different.  Still no optical drive. :(

I am positive this is because my two HDD's are SATA and the optical drive is not.  I actually removed it just to see how it was connected... I'm not sure what type of plug that is.  Found something on Google that looks just like it... it's the bottom piece in this picture:
[http://tbn0.google.com/images?q=tbn:B9KYen8-ywYqkM:http://www.ultradrives.com/images/adapter_jae-to-40pin-bare2.JPG]("http://tbn0.google.com/images?q=tbn:B9KYen8-ywYqkM:http://www.ultradrives.com/images/adapter_jae-to-40pin-bare2.JPG")

Is that called ATAPI?

Any suggestions how I can get the attention of the Linux ACPI programmers?  It appears no one here can help me... :(  (thanks for trying HunterThomson, but after reading those bug reports, i don't think a fully corrected DSDT will solve this issue)

---

### Post by HunterThomson on 2008-09-01
[U][B]Y710 Fix DSDT.aml File for your use
[/B][/U]

Chargersfan420..... here is your bug free DSDT.... Well there are still 2 warnings that I can't fix.. 

As a side note... There is a lot of refrence to Linux or "LINX". In the 710 DSDT. It seems to be grouped with older vertions of windows... You mite want to try setting a ACPI flag to tell the DSDT that your running WidowsXP, See what happens.


```

dsdt.dsl  4579:                         Method (HKDS, 1, NotSerialized)
Warning  1086 -                                    ^ Not all control paths return a value (HKDS)

dsdt.dsl  5150:                             Method (VPCR, 1, Serialized)
Warning  1086 -   Not all control paths return a value ^  (VPCR)

ASL Input:  dsdt.dsl - 7600 lines, 273573 bytes, 3049 keywords
AML Output: dsdt.aml - 28531 bytes 730 named objects 2319 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 859 Optimizations

```


P.S. GVIM is the ****! I highly sugjest useing it :guitar: Way more Syntax and stuff then Gedit or Kate. It works vary well for codeing.

---

### Post by HunterThomson on 2008-09-06
Chargersfan420,

Have you tried to change your SATA controler back to "ACHI" in CMOS Setup Utility? Your Optical drive is most likely connected to a SATA port. In your first post you said that you changed it to "Compatibility" for XP. I read someware ells that the person had to set their SATA controler to Compatability for Windows and back to ACHI for Linux. This sounds like something you would have tried alredy but if you have not do it. It sounds like this is the most likely of the unlikely solutions.

edit: Well if it is not on SATA try it anyway. Also the SSDT is error free on the Y510.

---

### Post by Sonyadora on 2008-09-06
> **wyth said:**
> Sonyadora,

I can't help you with the S-Video, but you should probably look at these pages:

DVD: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Dial-Up: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I had already looked at those, they weren't much help.  It turned out my problem with the optical drive was related to the BIOS settings.  I had to change from "Compatibility" to "ACHI" (I'd initially changed it when my first attempt at installing Feisty failed to see if that would help.  It didn't, I installed Hardy and never changed it back).  Since then, everything's been groovy.

The nice folks at linmodems.org have been helping me with the dial up modem.  We've got the OS talking to the modem, but it still won't dial out. Still haven't tried the S-Video.

---

### Post by HunterThomson on 2008-09-07
> **Sonyadora said:**
> I had already looked at those, they weren't much help.  It turned out my problem with the optical drive was related to the BIOS settings.  I had to change from "Compatibility" to "ACHI" (I'd initially changed it when my first attempt at installing Feisty failed to see if that would help.  It didn't, I installed Hardy and never changed it back).  Since then, everything's been groovy.

The nice folks at linmodems.org have been helping me with the dial up modem.  We've got the OS talking to the modem, but it still won't dial out. Still haven't tried the S-Video.

Right on,
Please report back with info on the modem.

---

### Post by jacobleonardking on 2008-09-07
> **evets25 said:**
> Ok, so I tried the patch(s) given in the guide, and was eventually able to compile and install the patched kernel module, which made me happy at first, but when I tried to actually use the webcam (I.e.: I opened up cheese), it completely froze the system. It's the kind of behavior I would expect if I loaded a driver for the wrong device, but I don't know. The webcam isn't that important to me (I never use it), so I don't really care about getting it to work again.

I did the same.

I got so sick of trying software fixes to the upside-down camera, that I made a hardware fix. I took my leatherman and pried off the shiny sheet covering the monitor.

Suddenly, I realized this solved another problem: the annoying glossy (reflective) screen.

Then, I cut off a piece of the plastic above the monitor surrounding the webcam, removed the circuit board with the camera on it, turned it around and replaced it (to the right of where it was previously, since the cable didn't have any slack).

Viola, right-side-up image. Works in cheese & skype, and presumably any other program. 15 minute hardware fix for what had been an unsuccessful 4+ hours of various attempted software fixes.

---

### Post by HunterThomson on 2008-09-07
> **jacobleonardking said:**
> I did the same.

I got so sick of trying software fixes to the upside-down camera, that I made a hardware fix. I took my leatherman and pried off the shiny sheet covering the monitor.

Suddenly, I realized this solved another problem: the annoying glossy (reflective) screen.

Then, I cut off a piece of the plastic above the monitor surrounding the webcam, removed the circuit board with the camera on it, turned it around and replaced it (to the right of where it was previously, since the cable didn't have any slack).

Viola, right-side-up image. Works in cheese & skype, and presumably any other program. 15 minute hardware fix for what had been an unsuccessful 4+ hours of various attempted software fixes.

=D> You have got some Balls !

You'd never find me taking apart my laptop and cuting parts off.
Good job though. Could you post a Pic?

---

### Post by Cheesecycle on 2008-09-08
Is anyone still having problems getting the subwoofer to work?  I have followed the instructions posted by wyth, and other than the subwoofer, the audio is excellent.  I tried all three options listed in the configuration file with no luck.  There were no problems during the setup, but I still have no LFE option in the volume controls.  I have the HDA intel alsa mixer selected.

---

### Post by jacobleonardking on 2008-09-08
As per request:
[ATTACH]84635[/ATTACH]

---

### Post by HunterThomson on 2008-09-09
> **Cheesecycle said:**
> Is anyone still having problems getting the subwoofer to work?  I have followed the instructions posted by wyth, and other than the subwoofer, the audio is excellent.  I tried all three options listed in the configuration file with no luck.  There were no problems during the setup, but I still have no LFE option in the volume controls.  I have the HDA intel alsa mixer selected.

Hum... do you have a Y510, Y710, or U???

Do you get the new center, suround, ..................

You know what I think is going on. I did this when I first got this laptop... You just need to go into prefrences and check all the "NEW" boxes there to enable the "NEW" volume controle bar's. You have to do that in "Gnome ALSAmixer". To check really fast to see if that is all just open up a shell and run this comand to open up the ALSA mixer in there. The 'NEW' volume control bar's apear on there owne in the shell alsamixer...

```
alsamixer
```

Don't forget to change the Chanels to "ch6" from "ch2". Also I mute the CD because is makes a high piched ringing sound. I use this option and is works vary well for me. 

options snd-hda-intel model=lenovo-ms7195-dig

---

### Post by HunterThomson on 2008-09-09
> **jacobleonardking said:**
> As per request:
[ATTACH]84635[/ATTACH]
WOW that is hard core. Looks cool though. Thanks for the Pic :)

---

### Post by Cheesecycle on 2008-09-09
HunterThomson:
I have the y510.  I do not have center or surround options.  Initially the audio was very quiet and after following the instructions in wyth's post, the max volume increased to an acceptable level.  Upon closer inspection, the center channel (above the keyboard) is not working.  Gnome ALSAmixer does not show any more options.  Everything is enabled.  Also, I do no see anywhere to select ch6/ch2.  I am currently using options snd-hda-intel model=lenovo-ms7195-dig as well.

---

### Post by HunterThomson on 2008-09-09
Hum...

Did you open a terminal aka comandline and check out the alamixer in there? That one is strate forword... No click this, then click that, bull. GUI's look cool but they make simle things complicated. (My thoughts on the subject. Use what you want)

The # of chanels ch2/ch4/ch6 is under the Options tab.

With all of that said.... And after you have checked out the alsamixer in the shell.... Your problem would be in the selections of the options in the /etc/modprobe.d/alsa-base file. Check spelling, syntax i.e. do you have a empty line at the end of the configuration file. Is there a "dot" where there should not be.. Is there not one where there should be?(well I guess there are no dot's so that was a bad example)

If all else fails you could also try adding options snd-hda-intel model=lenovo-ms7195-dig to the end of this file.

> /etc/modprobe.conf

Then reboot.


You mite want to take the "option" out of the /etc/modprobe.d/alsa-base file before you reboot with the "option" at the end of the /etc/modprobe.conf file.

---

### Post by Cheesecycle on 2008-09-09
I checked out the alsamixer in the terminal as well, but I dont see anything new there.  The options tab only has two options, both containing to microphones.  This is with everything enabled in preferences.

I dont see any typos in the alsa-base file, everything looks correct.

There is no /etc/modprobe.conf ...  

Thanks for helping out.

---

### Post by HunterThomson on 2008-09-10
> **Cheesecycle said:**
> I checked out the alsamixer in the terminal as well, but I dont see anything new there.  The options tab only has two options, both containing to microphones.  This is with everything enabled in preferences.

I dont see any typos in the alsa-base file, everything looks correct.

There is no /etc/modprobe.conf ...  

Thanks for helping out.

It must be something little.... Did you install the new alsa stuff yourself? Or did you just add the options to /etc/modprobe.d/alsa-base. If the latter then maybe you need to install new alsa-libs.

This is a software configuration problem not a hardware problem, not bug.

Could you attach a copy of this file..

```
/usr/src/alsa/alsa-driver-1.0.16/alsa-kernel/Documentation/ALSA-Configuration.txt
```

If the file is not there then use the locate comad to find it...

```
locate ALSA-Configuration.txt
```

Wyth do you have any ideas.

---

### Post by Cheesecycle on 2008-09-10
I installed it myself.  Two separate times now.

Should I be using alsa version 1.0.16?  I am using 1.0.17 now.

The ALSA-configuration.txt file was too big, so I split it up into 5 parts.

---

### Post by wyth on 2008-09-10
[This is really disappointing]("http://www.desktoplinux.com/news/NS8639308872.html?kc=rss").

Lenovo has been building up to sell machines with Suse Linux pre-installed.  They've now decided to drop all Linux support.

For the most part, I think the IdeaPads are perfectly situated to become fantastic Linux machines.  They're *this close* to having everything in place; they just need a little tightening up with their hardware specs.  

But if they've decided to just head in the opposite direction all together, I think this IdeaPad will be the last Lenovo computer I purchase.

---

### Post by chargersfan420 on 2008-09-10
After spending a lot of time on my issues, i've turned to other things, but i still haven't given up.

@ HunterThomson - Thank you very much for the new DSDT.  I have tried booting with it, but i don't notice anything different.  Is there anything specific i can try to notice a difference?

Still no optical drive - and yes, i have tried with the SATA controller mode set to AHCI instead of Compatibility, also with no difference.  I'm thinking a combination of fixes might be required to make this work (such as new DSDT + AHCI (nope), perhaps downgrading to 32-bit + new DSDT + AHCI...?)

I finally got a reply from the Linux guy @ Lenovo (this morning), he says he's been busy but he is still willing to help - will keep you posted.

@ HunterThomson - did you still want a fresh DSDT from the new Y510?  I am just getting around to taking it out of the box now.  BIOS version is 06CN30WW.

I have another minor problem, and i realize that this is probably not the most appropriate place to post it, but maybe one of you knows something i don't and can help.

My webcam worked just fine in Ubuntu, but after going through some steps [here]("http://www.uluga.ubuntuforums.org/showthread.php?t=770745"), i made some changes to the USB configurations in order to allow passthrough of USB devices to VirtualBox.  For the most part, it worked as intended, i can now use USB flash drives with Virtual-XP, and XP recognizes my webcam, but the webcam no longer works at all for either OS.  Cheese just shows a TV test pattern with static in the bottom corner, and XP tells me that the device is in use by another application or user.  Any ideas here?  How can i "reboot" the webcam, or check if it really is in use?

EDIT - and yes, i tried using the webcam in XP without using Cheese first, and i tried using Cheese without even starting up Virtualbox.

---

### Post by H4ck54w on 2008-09-10
06CN31WW dropped yesterday [Here]("http://consumersupport.lenovo.com/lenovo/drivers/2412/2993.html")
Have been Ubuntu only for about 4 months now but not brave enough to go this big yet (fear of bricking) anybody else done it yet?

---

### Post by wyth on 2008-09-11
I'll look into flashing the bios later this weekend, but in the meantime, HunterThompson has a good bios flashing guide [here]("http://ubuntuforums.org/showpost.php?p=5461070&postcount=4").

---

### Post by H4ck54w on 2008-09-11
Well no luck for me, went through HunterThompson's from step 1 three times and kept getting Disk I/O error when selecting C: at the BIOS loader screen, what may have caused it is I extracted the .exe through WINE so I don't know if it corruped the BIOS file or not, but you would think if that was it I wouldn't have a Disk I/O error, I would have a different result. I wonder if I could make a bootable CD and do it that way???

Edit:OK I got it.
I may have had a bad flash drive. I booted to LiveCD, partitioned 512MB of my HDD to FAT32 with Gparted just coppied all the files that resulted from HunterThompson's directions (sans old BIOS file added new BIOS file) Don't know if all files were necessary or not, but did it anyway. I haven't noticed anything better/worse/otherwise yet, but I do know that it doesn't fix the camera invert/upside down.

---

### Post by HunterThomson on 2008-09-12
> **H4ck54w said:**
> Well no luck for me, went through HunterThompson's from step 1 three times and kept getting Disk I/O error when selecting C: at the BIOS loader screen, what may have caused it is I extracted the .exe through WINE so I don't know if it corruped the BIOS file or not, but you would think if that was it I wouldn't have a Disk I/O error, I would have a different result. I wonder if I could make a bootable CD and do it that way???

Edit:OK I got it.
I may have had a bad flash drive. I booted to LiveCD, partitioned 512MB of my HDD to FAT32 with Gparted just coppied all the files that resulted from HunterThompson's directions (sans old BIOS file added new BIOS file) Don't know if all files were necessary or not, but did it anyway. I haven't noticed anything better/worse/otherwise yet, but I do know that it doesn't fix the camera invert/upside down.


I am editing the USB bios script thing but I am having the same problem. You also think it is the flash dirve. The HDD partition worked is sounds like...? I'll try that.

I have also posted the ***29.ROM and the new ***31.ROM files with the BIOS flashing HOW TO.

---

### Post by H4ck54w on 2008-09-12
> **HunterThomson said:**
>  You also think it is the flash dirve. The HDD partition worked is sounds like...? I'll try that.

Yeah, cause every time after I formated the flash drive to FAT32, then went through the steps, afterwards it would say Unknown partition, it wouldn't stay FAT32

Yes HDD partition works flawlessly.

---

### Post by HunterThomson on 2008-09-13
Well I just did it by formating the USB drive fat32 with a boot flag. Then copied over the freedos files and the .rom file.

---

### Post by H4ck54w on 2008-09-13
I tried that once as well, except I didn't add a boot flag. #-o

Well looks like people have a couple different options now.
Thanks.

---

### Post by azteca_04 on 2008-09-13
Hey, guys, its the flashing of the bios its solving any problems (backlight, webcam)?

a have another problem i hope you can help me, everytime i start my lap(y510 ubuntu 8.04 32 bits) and go to the internet then my videos music wont play, or if a play firt my music or video, internet video like youtube wont work, i did the how to for the sound on the thread, any ideas what could it be, thanks guys

---

### Post by arixavier on 2008-09-14
Hello, I got the Y710 and everything works well with 8.04 with the exception of the CD/DVD rom not showing at all, have anyone found a solution to this problem? Also should I use the default Vesa driver or is there a better one to use (ATI 2600)

 

Appreciate it reply specially about the DVD rom issue.

---

### Post by wyth on 2008-09-15
I haven't had a chance to update the BIOS -- has anyone else?  Any news on that?

EDIT

By the way, I have the ROM file extracted out of the new BIOS update -- it's attached.

---

### Post by HunterThomson on 2008-09-16
Thankyou wyth for posting the ROM file. I was having problems. Now I will tie that into the bios script.

As for the New BIOS fixing anything.... Not that I can tell...

As for the CD/DVD rom on the Y710.... That sucks... Do you have the BlueRay drive like Chargersfan420??? That is kind of a biggy problem.... If this is a problem with all Y710's or the BlueRay drives... I would start to download loads of Linux Distro's untill I found one that worked out of the box. Start with Linux Mint. Mint is the same as Ubuntu exept it works better. Then I really don't know....

About the ATI 2600 driver... Ya there is a better driver. I don't know what it is though. Google "ATI 2600 driver Ubuntu" and read up then start a new thread for that one. I think you have your choce between Open Sorce and Closed Sorce.

The internet sound video problem.... Is is a sound problem or a video problem? Or both? If it is just a sound problem there is a program that is in charge of alowing you to paly sound form mutiple sorces at once. I can't recall the name right now. But that program should have been installed by default in Ubuntu....

---

### Post by jpflanigan on 2008-09-16
Back to the whole LCD brightness bug...

I tried this (once!) and got some interesting results:
1. Add video to /etc/modprobe.d/blacklist
2. After booting video would be "locked" on highest brightness
3. Typing "sudo modprobe video" appeared to reenable the fn-up/down functionality

(You would think this would get to the same endpoint...)

Then the buttons worked in the proper way (FN-up=brighter FN-down=dimmer) and applications like VirtualBox seemed to leave it alone.:guitar:

Any volunteers to give this a try and let me know what happens?

PS - As a disclaimer this was my last ditch effort before hitting the hay last night, so I haven't repeated this yet.

Update 9/16 4pm:  I have a Y510 with the on-board Intel video, Ubuntu 8.04 32-bit.  Some of the board suggestions have been tried, so some gnome-powermanager settings have been toyed with etc... I'll repeat tonight.

---

### Post by wyth on 2008-09-16
For sound with internet video:

I had this problem on my desktop, but not my laptop.  The difference: My laptop was using ALSA, and my desktop Pulse.  This was a problem with Flash 9 as far as I can tell.  I recently installed the Flash 10 release candidate, and that took care of everything.

I followed the instructions [from this link on Tombuntu]("http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/").  Note that the .deb file installs over the same places Flash 9 is, so if you installed Flash via aptitude/synaptic (i.e. normally), then no worries.  If you manually installed it, then you'll have to remove that stuff first.  

Also note: You'll most likely need to remove libflashsupport if you have that installed.  That's needed for Flash 9, but seemingly not for Flash 10.

Imonna try that screen brightness trick now.

**EDIT**

Tried jpflanigan's modprobe tick, and had the same results as before -- fn+up and fn+down are still reversed, and starting something like VirtualBox still dimmed the screen.  Question to jpflanigan: What's your specs?  Video card, Y510 or Y710, etc.?

---

### Post by winnibob on 2008-09-16
> **jpflanigan said:**
> Back to the whole LCD brightness bug...

I tried this (once!) and got some interesting results:
1. Add video to /etc/modprobe.d/blacklist
2. After booting type "sudo modprobe video"

(You would think this would get to the same endpoint...)

Then the buttons worked in the proper way (FN-up=brighter FN-down=dimmer) and applications like VirtualBox seemed to leave it alone.:guitar:

I just tried it with no result.
After blacklisting the video module, my screen was brighter than usual (like 10 instead of 8 in /proc/acpi/VGA/LCDD/brightness), but I was unable to modify the brightness with the FN-up and FN-down keys.
After the "modprobe video", I was still unable to change it this way.

---

### Post by jpflanigan on 2008-09-16
Well I tried it again on a fresh reboot and it performed as described:

1 - with "video" module blacklisted it booted up at full brightness and the fn-keys did nothing.

2 - did a "modprobe video" from the root console and fn keys worked 6 levels of brightness in the correct direction.

It could be this action in combination with the 27-odd ideas I tried from this board and others (gotta luv Linux!)...

Prior to this change it seemed that the brightness would work but was being over-ridden by software.  Hitting the fn-up would cause the screen to flash bright then go dim, the flash would be the "right" brightness, then it would be immediately changed to the wrong brightness.  Somehow this eliminates the 2nd change.

Now I have to find a way to add this to the end of the boot-up routine so it works automatically.

---

### Post by azteca_04 on 2008-09-16
> **HunterThomson said:**
> 

The internet sound video problem.... Is is a sound problem or a video problem? Or both? If it is just a sound problem there is a program that is in charge of alowing you to paly sound form mutiple sorces at once. I can't recall the name right now. But that program should have been installed by default in Ubuntu....

if i play first a video that a have on my lap then the sound on youtube wont play, video ok, but if i play youtube first then my videos on laptop wont work, the video nor sound work

if you can help me please, i hate that i can only play onething and having to reboot if i want the other, thanks

---

### Post by wyth on 2008-09-17
Based on HunterThompson's [bios flashing script post here]("http://ubuntuforums.org/showpost.php?p=5552537&postcount=31"), it seems the new bios makes the screen dimming worse.  Is this the case?  Has anyone tried the new bios?

**EDIT**

I'm impatient and went ahead and updated my BIOS.  So far it started up fine, and I don't really notice anything in particular that's different.  The screen dimming is still backwards, it still dims when I start VLC or Avidemux, and I screwed up my camera a while back so I don't know if that's working better or not.  

But if anyone is interested in a little more user-friendly way to update the BIOS, this worked for me.

_Gear_

[LIST]
[*] gparted live CD or live Ubuntu cd
[*]the rom of the bios update
[LIST]
[*]You can get this from a Windows installation; the .exe is an archive, and the .rom is inside.  You can try cabextract to get the .rom (available in the repositories), or if you have Windows/Virtual Windows installed, you can just run the .exe and nab the .rom that way.
[/LIST]
 
[/LIST]
_Steps_

[LIST]
[*]Boot into live cd
[*]With gparted, create a small partition and format it as fat32
[LIST]
[*]If you have a small root partition, this will be easy and not very time consuming
[/LIST]
 
[*]Boot back into linux
[*]Drop the .rom into the fat32 partition
[*]Restart
[*]Hit F2 to get into the BIOS
[*]Go to Advanced and then to the EasyFlash
[*]You'll see a C drive -- that's your new fat32 partition, and the .rom will show up
[*]Flash away, and reboot into your new BIOS
[*]You can boot back into gparted and nix that partition, or just unmount it and keep it from loading at boot if you want.  I made mine tiny and keep it around for just these sorts of occasions.
[/LIST]

---

### Post by wyth on 2008-09-17
azteca, I replied to your question a page ago, [here]("http://ubuntuforums.org/showpost.php?p=5799911&postcount=119").  See if that helps.

---

### Post by azteca_04 on 2008-09-18
> **wyth said:**
> 

I followed the instructions [from this link on Tombuntu]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5799279").  Note that the .deb file installs over the same places Flash 9 is, so if you installed Flash via aptitude/synaptic (i.e. normally), then no worries.  If you manually installed it, then you'll have to remove that stuff first.  



Hi thanks Wyth for the reply the link you mentioned doesnt work it takes me to write a coment, but i thing the proble could be with the alsa drive dont you, because if i play first the youtube it works but my music wont, but if you send me the link ill sure try it thanks again, and sorry for bugging you

---

### Post by wyth on 2008-09-18
Sorry -- I pasted the wrong link before.  It's fixed now, and [here's the correct link for Flash 10]("http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/").

I can't say for certain if you have your alsa set up correctly, but what you're describing is consistent with some errors people were having with Flash 9 -- sound would work one way, but then not on any web site with Flash like YouTube, etc.  So trying Flash 10 couldn't hurt, and it may fix your problem.  Just be sure to not have libflashsupport installed if you go with 10.

---

### Post by azteca_04 on 2008-09-18
> **wyth said:**
>  So trying Flash 10 couldn't hurt, and it may fix your problem.  Just be sure to not have libflashsupport installed if you go with 10.

Thanks for the reply, ill try the link and upgratin to flash 10, but how can i check if libflashsupport is install, i don't remember installing it my self, but to make sure, if theres a way to check, thanks

---

### Post by wyth on 2008-09-18
If you didn't install libflashsupport, you're probably okay (and it's probably why you're having problems now).  You can search for it in synaptic -- if it's installed. remove it.  If it's not installed, don't worry about it.

For Flash 9, libflashsupport helped take care of a number of sound and crashing issues.

If you haven't seen it yet, you should probably look at the [Restricted Formats info]("https://help.ubuntu.com/community/RestrictedFormats") and the help page on [Multimedia Applications]("https://help.ubuntu.com/community/MultimediaApplications").

---

### Post by azteca_04 on 2008-09-19
Hey Wyth, thanks for the help, but i check and it wasn't install so i went and got the flash 10 and install it like it said on the link you put but no luck, maybe im doing something wrong? if you can help me please, thanks

---

### Post by azteca_04 on 2008-09-20
Hey guys, has anyone else experince the same, only to get one thing working not both at the same time, i still thing its a problem with the audio drivers because video its ok just the audio that wont play, so if anyone had the same problems please tell me have you did it, thanks

---

### Post by wyth on 2008-09-20
> **azteca_04 said:**
> Hey Wyth, thanks for the help, but i check and it wasn't install so i went and got the flash 10 and install it like it said on the link you put but no luck, maybe im doing something wrong? if you can help me please, thanks

You'll have to give a bit more information:

[LIST]
[*]What procedure did you actually go through?  Did you just install the Flash 10 deb?
[*]Under System > Preferences > Sound, what devices are set as the default?
[*]What are the specs on your machine?  Is this a Y510 or Y710?  What sound card and video card do you have?  That all makes a difference on what advice people can offer.
[/LIST]

---

### Post by HunterThomson on 2008-09-21
Hum... azteca_04, Ya I just tried out all the flash aplicatons i.e. Gnash-gk, swfdec-mozila, Adoby 9, and now I am using Adoby 10 on my x86_64. I use to use Gnash before I reinstalled Arch. Now gnash will notwork. Anyway, Ya it seems Adoby9 did have sound problems that were fixed by a lib*. In any case it dose sound like it could be a flash problem... Hum you know I did have a similer problem when I installed xmms. It installed some progrme to manage the sound. When I turned it on it would cause the same problem you are talking about So, I just turned it off. However, xmms still gives me problems when I try to pay to sound form two sorces at once. Something to the effect of 'the sound resorce is alredy in use'.

Just kind of rambling but I hope it gave you some ideas. Have you started a thread in the genoral help or audio/video section yet? I bet you will get a lot more help if you do that.

---

### Post by azteca_04 on 2008-09-21
> **wyth said:**
> You'll have to give a bit more information:

[LIST]
[*]What procedure did you actually go through?  Did you just install the Flash 10 deb?

after checking if i had the libflashsupport on synoptic, and i did it have, i downloaded the .deb flash 10 and install it like it said on the web and reboot and nothing
> 
[*]Under System > Preferences > Sound, what devices are set as the default?
My sound defaults are on the atachmente below
> 
[*]What are the specs on your machine?  Is this a Y510 or Y710?  What sound card and video card do you have?  That all makes a difference on what advice people can offer.

i have the Y510 Procesador: Intel Pentium Dual Core CPU T2370 @ 1.73 GHz
Memory: 2.0 Gb
Kernel: 2.6.24.19-generic GNOME 2.22.3 Ubuntu 8.04

Video:  Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Audio:  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

thanks for the post and replying thanks

---

### Post by azteca_04 on 2008-09-21
Hey HunterThomson thanks for the reply yeah it looks like mozilla its having troble with the flash it also happen in xp but i really dond care for it on xp, but what its weird is that in ubuntu it would play with no problems as long as i dont use any sound or video from my laptop like movies music or stuff like that it would work but then i will not be able to play any of that stuff onless i reboot, dont no what is the problem, thanks for helpin and for any help you can give me, 

and thanks to wyth that is helping an anybodoy that can helping

---

### Post by Gruu on 2008-09-21
I'm having some problems with my (Ideapad Y510) laptop booting up rather slowly. The little bar will go from side to side:

```

[---|||-----]
[-----|||---]
[-------|||-] <-- hangs here

```

Then when it fills up:

```

[|----------]
[||---------]
[|||--------] <-- hangs here, too

```

And hangs there for quite a while. *Most* boots are like this.

Every so often, during bootup the system asks me to do a routine disk check. When this happens, and if I skip the check, my laptop boots up a whole lot faster. How can I fix this?

Thanks!

---

### Post by HunterThomson on 2008-09-21
> **Gruu said:**
> I'm having some problems with my (Ideapad Y510) laptop booting up rather slowly. The little bar will go from side to side:

```

[---|||-----]
[-----|||---]
[-------|||-] <-- hangs here

```

Then when it fills up:

```

[|----------]
[||---------]
[|||--------] <-- hangs here, too

```

And hangs there for quite a while. *Most* boots are like this.

Every so often, during bootup the system asks me to do a routine disk check. When this happens, and if I skip the check, my laptop boots up a whole lot faster. How can I fix this?

Thanks!

Well, It vary well could be that this is normal behaviour. 

This is one thing that I realy like about Archlinux. When it boots up it prints evrything on the screen that it is doing. So, when something is takeing long or thoughing an error you can see what is going on.

The slow boot could be a few things. One, that could be the point when it is setting up a network connection. It mite be a error of some sort so when it is trying to do something agin and agin but it dosn't work. It could just be a sleep comand at some point to let things settle down.

You can check /var/log/dmesg.log for errors at bootup. Or other logs.

You do what to do the routine disk check. It checks the partition for errors.

====================================
DSDT

It seem that after you get a Kernal update the new Kernel compiles in the DSDT thing so you don't have to do it or use the old Kernal you compiled.

---

### Post by wyth on 2008-09-30
> **jacobleonardking said:**
> As per request:
[ATTACH]84635[/ATTACH]

I'm really curious about this.  Is it just a glossy sheet affixed over a normal screen?  Does it leave any adhesive  remnants or anything?  Does it bend/warp the frame around the screen?  How does it look without the gloss, and is the gloss replaceable once you remove it?

---

### Post by ethan__ on 2008-09-30
After adding 
```
options snd-hda-intel model=lenovo-ms7195-dig 
```
to /etc/modprobe.d/alsa then 
```
emerge alsa
``` 
was able to get my speakers working in gentoo :]

---

### Post by wyth on 2008-10-01
If anyone is having a kill switch issue with wireless on boot, I've filed [bug #275026 on launchpad]("https://bugs.launchpad.net/ubuntu/+bug/275026"); please go there and add to it.

Things you'll need to include:


[LIST]
[*]Run ```
uname -r
``` in the terminal to get your kernel number.  This problem is related to 2.6.24-20 and 2.6.24-21, both generic and i386 (as far as I know).
[/LIST]


[LIST]
[*]In the terminal, run ```
dmesg > dmesg.log
``` after a fresh boot.  The dmesg.log will be in your home directory; attach it to the bug report.
[/LIST]


[LIST]
[*] In the terminal, run ```
sudo lspci -vvnn > lspci-vvnn.log
```  Like above, the lspci-vvnn.log will be in your home directory; attach it to the bug report.
[/LIST]

---

### Post by chargersfan420 on 2008-10-06
A suggestion has come up in the Ideapad forum on the Lenovo site to fix the CD/DVD issue with Y710's and Linux.  The suggestion is to use LILO instead of GRUB.

[http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=2557&view=by_date_ascending&page=3]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=2557&view=by_date_ascending&page=3")
[http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=3581]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=3581")

It failed to work for someone... they say that LILO must be located on the MBR.  So, my question is this - Since i have two HDD's, with the Vista bootloader in the MBR of HDD-a (booting to GRUB in the root partition, which happens to be the primary partition of HDD-b), can i install LILO to the MBR of HDD-b and go into the BIOS and change the boot order of the hard drives?  I'm hoping i can use this to test LILO and if it fails, i can just switch the boot order back to normal and not mess anything up.

If this seems reasonable, I will give it a shot.  If i have to reinstall Ubuntu, it wouldn't be the end of the world (with Intrepid coming up, a fresh install might be a good thing), but i really don't want to mess with my Vista / XP partitions.  

Anyone want to toss in their two cents on this idea?

---

### Post by wyth on 2008-10-10
Anyone upgraded to the beta of 8.10?  I'm just curious how it runs on these machines, but I've just moved and not had internet access to download anything to test.

---

### Post by ziptiespec on 2008-10-22
I had 8.10b installed for about an hour on my brand new Y510 (1.6Ghz/Intel video).  The brightness issue was present, though the button functionality was "circular" - you could keep hitting + or - and the screen would cycle from dimmest to brightest endlessly.  Wireless didn't work out of the box.  I didn't test the camera or anything else.  I just installed 8.04 over 8.10b and am working on the brightness issue, and getting the card reader to work.

---

### Post by HunterThomson on 2008-10-25
helo everyone... been awile. My life has been taken over by Eternallands a MMORPG.


Chargersfan420. I have not used lilo before. If you were switching to grub then I could tell you that it would not be a problem you would just have to install grub on the MBR of the second harddrive and just edit the grub.config file. I am sure the same is true with lilo. You will have to uninstall grub then install lilo on the MBR of the HHD that you have ubuntu on. You can infact change the boot order of the hhd's. I chage that inorder to boot into backtrack on USB. Read up on lilo.

You should not have to mess with win at all. Hell just take out the win HHD and put in only one HHD then instll linux on that but use Lilo insted of grub. ((I don't know if ubuntu give you a option anymore)) Make sure you chose "Install Lilo to MBR". Then once you know lilo works you can go through the hassle of setting it up on your tri-boot system. 

As for ubntntu 8.10. WOW we realy need to get in touch with some devs. This backlight thing is just not cool at all. I am running Kernal 2.6.27-ARCH. The problem with filing the bug is what the hell is broken???? Kernl? ACPI? Xorg? Video driver? Where do we post ??? The problem is cross distro....

---

### Post by wyth on 2008-10-26
Okay, so here's some 8.10 RC info.

I had started a long post about what worked and what didn't.  Overall, it's great -- in general, better than 8.04.  The screen brightness works better (except it cycles, as noted above), suspend/hibernate work, wifi, etc.  But the sound problem is still there.  

Here's what I don't get: I have the live CD in right now, and not only does the brightness work correctly -- meaning it stops when it reaches full brightness and doesn't start over -- but the sound works.  It's not surround sound, but it works.  It seems to be working with Pulse.  But this is only on the live CD, not on the install.

Which makes me wonder if there's a way to get the correct settings of the live CD and just tweak the install, and voila, you have a flawless system.  I'm just not sure where to begin looking here.

---

### Post by wyth on 2008-10-27
Okay, so I have 8.10 RC installed, with pretty fantastic results.  

I did a clean install of the 8.10 Release Candidate recently, and things look great on the Lenovo Y510 IdeaPad -- better than 8.04.

Here's what I did:

[LIST]
[*]Downloaded the regular desktop .iso
[*]Made a list of all the apps and other things I use that I'll need to download again
[*]Made a backup of my sources.list file in my /home directory for all my extra repositories
[*]Checked my partitions -- I keep my /home directory in a separate partition.  That's just a good idea, I think, because you don't have to spend much time keeping the look/feel/settings preferences consistent between upgrades.  Hardly any time at all, actually
[LIST]
[*]And when you install programs you once had, you won't need to adjust all the settings or anything.  For instance, I have way too many podcast feeds in Amarok; I can wipe out my root partition and do a clean install, install Amarok again, and it'll pick up my previous config settings in my /home directory, and it's like nothing ever changed
[/LIST]
[*]Manually partitioned everything to format the root (/) partition and use the pre-existing /home directory (don't format that)
[/LIST]
 
Here's what I got:

[LIST]
[*]Wireless fires right up with the new 2.6.27 kernel
[*]The backlight is working again.  However, it doesn't stop when you reach the top level of brightness -- it cycles through.  (I think this was mentioned)
[*]The webcam is working almost correctly; the picture is good, but still upside down
[*]Suspend and Hibernate WORK -- woo-hoo!
[*]Sound didn't work out of the box.  I didn't want to compile ALSA again (eventually had to, see next post), but I did get it to work
[LIST]
[*]I installed linux-headers-lbm, linux-backports-modules-intrepid-generic, medibuntu, ubuntu-restricted-extras, all that.
[*]I set /etc/modules.d/alsa-base to options
[*]ALSA didn't work on reboot; I was stuck with the two channels.  Went into System - Preferences - Sound and switched the default to OSS.  Changed the default in Amarok, in VLC, etc. to OSS.  Whadaya know, the subwoofer is working, the sound is rich, and everything seemed great.  This didn't last; headphones wouldn't turn off any sound when under OSS
[/LIST]
 
[/LIST]
So the sound is the big issue.  Other than that, it's a slick system -- snappier, clean, and wait'll ya hear what's up with the sound now.  Like I said, I didn't want to compile the drivers for ALSA again if I could help it.  However, after three days of getting nothing done but messing with sound possibilities, I gave it.  But I found something very interesting -- [this bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/223407/") suggests that the alsa-modules need to be compiled with the following options: ```
--with-card-options=hda-codec-realtek,hda-codec-analog,hda-codec-sigmatel,hda-codec-via,hda-codec-atihdmi,hda-codec-conexant,hda-codec-cmedia,hda-codec-si3054,hda-generic
```.  My sound card is a Realtek ALC888, and this was new to me.


So I gave in and compiled the latest ALSA drivers, 1.0.18rc3.  However, I included that --with-card-options when configuring the driver, and I also found a new model to add to the end of /etc/modprobe.d/alsa-base -- lenovo-sky.


Now I'm no expert, so I don't know for sure if it was the --with-card-options or the lenovo-sky or both, but not only do I have my 6 channel sound, but:

[LIST]
[*]All the nifty little system sounds work again -- the drums and greeting at boot, etc.  Those were gone when I compiled my own drivers in 8.04
[*]All the surround sound elements automatically mute when headphones are plugged in -- no need to mute
[*]Note: in System-Preferences-Sessions, I have PulseAudio Session Management ticked **OFF**.  I had it set like that from before -- I'm not certain yet if it makes a difference or not.  It certainly doesn't hurt.
[/LIST]
I'm not sure why this stuff can't be included in a default install, especially since the live CD seems to work (but lacks the surround sound).  But if you're willing to compile the ALSA drivers again, 8.10 is looking like it could be the best version of Ubuntu yet for the Lenovo Ideapads.

I'll post an updated ALSA compile guide next.

---

### Post by wyth on 2008-10-27
Okay, I'm just basically reposting what is already on [this Ubuntu help page]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and on the previous [Lenovo Ideapad Y510 is GO page]("http://ubuntuforums.org/showpost.php?p=4329171&postcount=14"), but with some new tweaks. This guide is using the 1.0.18rc3 ALSA drivers, but this will/should work for other drivers.

First, you need to make sure you have the right stuff installed:
     
```
  sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r` 
```Next get the latest ALSA drivers; they'll be downloaded to wherever your default downloads go, but you're going to move them to a new directory.  For this case, I'll use the Desktop.

[LIST]
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/")
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/")
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/")
[/LIST]
Next step is to create a /usr/src/alsa directory for the files and copy the tar.bz2 files to that directory; you may have this directory of you've rolled your own drivers in the past:

 ```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/Desktop/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2 
```
[LIST]
[*] Compile and install alsa-driver
[/LIST]
       ```
cd alsa-driver* 
sudo ./configure --with-card-options=hda-codec-realtek,hda-codec-analog,hda-codec-sigmatel,hda-codec-via,hda-codec-atihdmi,hda-codec-conexant,hda-codec-cmedia,hda-codec-si3054,hda-generic
sudo make
sudo make install 
```
[LIST]
[*] Compile and install alsa-lib
[/LIST]
      ```
cd ../alsa-lib* 
sudo ./configure 
sudo make 
sudo make install 
```
[LIST]
[*] Compile and install alsa-utils
[/LIST]
      ```
cd ../alsa-utils* 
sudo ./configure 
sudo make 
sudo make install 
```Next find out what sound card you're using:

```
  cat /proc/asound/card0/codec#* | grep Codec 
```The Y510 uses RealTek ALC888, so look for that.   (This may be different if you have a newer version of the Y510 with some different hardware.)

Next you can check the ALSA-Configuration for specifics on the sound card. I found it at 
```
  /usr/src/alsa/alsa-driver*/alsa-kernel/Documentation/ALSA-Configuration.txt 
```Look for the section titled ALC883/888.  There are many possible options, and some work better than others.[INDENT]&#8227; 3stack-6ch
&#8227; 3stack-6ch-intel 
&#8227; lenovo-101e (Lenovo 101E)
&#8227; lenovo-nb0763 (   Lenovo NB0763)
&#8227; lenovo-ms7195-dig (Lenovo MS7195)
&#8227; lenovo-sky (Lenovo Sky)
&#8227; auto (Gets the information from BIOS)
[/INDENT]Next to tell alsa-base what to do:
```
  sudo nano /etc/modprobe.d/alsa-base 
```at the end of that file, add:
```
  options snd-hda-intel model=MODEL 
```For model=MODEL, use one of the options from above, such as:[INDENT]&#8227; options snd-hda-intel model=lenovo-sky
[/INDENT]I found model=lenovo-sky worked beautifully.
Reboot and see if it's working. In the past, kernel updates did not break this.  The surround sound features are present, the system sounds work, and the headphones automatically mute all speakers when plugged in.

---

### Post by JSuresh on 2008-10-30
With the newly compiled ALSA drivers for Intrepid, do you have to mute/turn on each speaker separately as we've had to so far?  If not, I'll probably stick with Gutsy..

---

### Post by wyth on 2008-10-30
Nope -- set your settings once, and it sticks. No need to constantly reset things.

Note: PulseAudio Session Manager *will try* to take over the sound settings and that will mess with them.  Just go to System - Preferences - Sessions and untick it (using ALSA, you don't need it anyhow).

And you can turn on all the surround sound features, plug in headphones, and they automatically mute -- no need to manually mute them.

---

### Post by wyth on 2008-10-30
**UPDATE:**
There was a kernel upgrade today, and it required compiling the drivers again.  No big deal; just use the terminal, get into that /usr/src/alsa directory, repeat the above steps, reboot, and you have your beautiful sound back.

---

### Post by chargersfan420 on 2008-10-31
Hey everyone, it's been a little while for me too.

@HunterThomson - Thank you for the response.  I've actually been through a couple of nightmare situations since my last post.

First, my Ubuntu drive flooded.  It turns out that Virtualbox was the culprit.  Long ago i had moved my VDI file to a different partition to avoid this error, but what i didn't realize was that i had taken a few snapshots that were saved to the Ubuntu drive, and they were getting bigger.  Virtualbox doesn't let you re-locate snapshot files, which i was very displeased to find out... Some googling revealed it is a "low priority feature request" at this point.

So, the only way to fix my problem and keep my virtualbox was to resize my partition.  After doing this, Ubuntu was unbootable, and it turns out that somehow my partitions got re-numbered.  I managed to get this going again with a lot of messing around.  My boot process looks horrible now.

I also noticed that Firefox 3 was eating up quite a bit of RAM and i wanted Virtualbox to have more too, so i upgraded from 2 GB to 4 GB.  Once i did this, Ubuntu wouldn't boot at all.  I get the screen that says:
Kernel alive.  Direct mapping tables up to 14000000 @ 8000-e000
I could have that wrong, i'm just typing it from memory... but Ubuntu would hang right there.  I also notice with the RAM upgrade, the numbers changed... it used to be 1000000 (give or take a few zeros) and 8000-d000.

I checked the obvious solutions already - Vista and XP boot fine, i can boot from CD just fine, and i ran Memtest for 9 hours and passed 4 times.  I'm completely baffled.

So, i decided i'm going to give up on Hardy and try out Intrepid (assuming a fresh install will fix this 4 GB = no boot problem).  I have 100 spare GB to work with, and i'm looking for a little advice now...
- Can i re-use the home folder of Hardy when I set up Intrepid?
- Anyone have a suggestion of how big i should make my / partition, and how big my /home partition should be?  It would probably be good to store all virtualbox related files in the /home partition so i can cleanly install newer versions to their own partitions and not lose anything...

---

### Post by wyth on 2008-10-31
Hey howdy,

You can re-use your /home folder *if and only if* your /home folder is on its own partition.  You can make a partition, copy the directory over there, then do a clean install and choose it for your /home directory (just don't format it).  You can make that partition pretty big; my root partition is only about 4 gigs, and my /home partition is about 200 gigs.

I had the Sun version of VirtualBox, which was pretty slick.  My virtual machines/.di files are in my /home directory.  However, I ran into an issue on the upgrade -- I think it was because I ran the cruft remover in Intrepid, and it nixed any .debs I installed independently.  So I just installed the ose version in the repository, and whadaya know, it automatically found my previous machine/.vdi, and everything is working great.  In fact, the ose version feels lighter and faster than the previous one.  Might want to install vboxgtk and the virtualbox-ose-guest-utils.

---

### Post by chargersfan420 on 2008-10-31
Thank you for the quick reply, Wyth.

Two questions for you:
1.  Any reason why you went from Sun XVM to OSE?  I switched from OSE to XVM in order to gain USB support in my virtual machine.  I like to backup my code files to flash drive, and I would like my webcam to work in my virtual machine as well, but I couldn't get it going before.  If I connected it to the virtual machine, XP would just tell me that the camera device was in use and couldn't be opened...

2.  Are there any good reasons to make separate partitions for the other options in the installer (/boot, /tmp, /usr, /var, /srv, /opt, /usr/local)?  I'm assuming that they will all go into the / partition if i don't...

---

### Post by wyth on 2008-10-31
Y'know, I didn't even think about the usb issue, but I just tried something and got around it.  Here's what I did:

Before opening up a virtual machine, I added /media/usb to my shared folders in the Vbox settings.  (That's where my usb key shows up on my machine.)  Fired up the virtual machine, and then added this code at the command line:
```
net use Z: \\vboxsvr\usb
```That added a persistent link in my XP shared network directories.  If I didn't have my usb key in, it spit an error.  When I plugged in my key and tried the link, it worked every time.  So with that, usb problem solved.

As far as making partitions for other directories, I don't know of any good reason to make extras -- all those directories you ask about will appear in the /root partition, and the OS will just look to the other partition for your /home partition as if it were in your /root partition.  I think some people put /boot on its own partition, but I've never needed to and am not clear on the specifics.

Hope this helps.

---

### Post by chargersfan420 on 2008-10-31
Thank you Wyth.  I think i may have tried that earlier, but i didn't set up the mount points correctly.  Just out of curiosity, are you able to suppress that error message when the USB key is not plugged in?  I haven't decided if i will go back to OSE or use XVM again...

Attention all Y710 Ubuntu users:  The optical drive is alive!!!  Some reports i have heard blame GRUB and state that using LILO solves the problem.  I can confirm that this is true.  It's so nice to have my optical drive working after many months of frustration.  I haven't found any side effects yet, as my Intrepid install is fresh and there is much to be configured.

And yes, i was able to install LILO to the MBR of sdb (or hard drive 2).  The Vista bootloader still exists on the MBR of sda (hard drive 1).  If LILO can successfully boot into Vista and XP, then sdb will be my primary boot device in the BIOS, and i can just use the vista bootloader if something goes wrong... we'll see how that works out.

One odd thing that i noticed... Intrepid won't let you specify using LILO, it's pretty much locked down to GRUB.  I couldn't change this (but i refused to try the text-based installation method - I'd much rather deal with GUI's)... but once intrepid was installed, "sudo apt-get install lilo" reveals that lilo is part of the default installation.  Why would they default install LILO but not let you use it?

---

### Post by wyth on 2008-10-31
> **chargersfan420 said:**
> Just out of curiosity, are you able to suppress that error message when the USB key is not plugged in?

Not to worry -- it only spits the error if the key isn't plugged in and you click on the folder.  The folder will always be there in the Network shares, but if the key isn't plugged in and you clicked on the folder, *then* it'll spit the error.  (But you wouldn't be clicking on it anyway if the key wasn't plugged in.)

So the only difference is that the Network share always shows up, instead of only when the key is plugged in.  It's a slight difference, and yes there are some other features the Sun version has that I haven't used and don't miss, but for running a virtual machine of XP, it's dandy.

---

### Post by denisesballs on 2008-11-01
Has anyone else been running Intrepid? I've noticed very poor video performance. Full screen flash is terrible and actually blinks and pauses, and vmware performance is also terrible. This is with the linux-server kernel. Everything works great on Hardy with the same setup.

---

### Post by wyth on 2008-11-02
Yes, running intrepid.  No, have none of those problems.  Make sure you have medibuntu enabled, and get the right flash packages (Flash 10 has been out for some time now). I don't use vmware, I use virtuabox, and it's fantastic.

---

### Post by denisesballs on 2008-11-03
> **wyth said:**
> Yes, running intrepid.  No, have none of those problems.  Make sure you have medibuntu enabled, and get the right flash packages (Flash 10 has been out for some time now). I don't use vmware, I use virtuabox, and it's fantastic.

Been on Flash 10, and VMware is not the problem. It has to be something with either the new Server kernel (which I'm only using because I have 4gb RAM) or something with the latest Intel driver.

---

### Post by chargersfan420 on 2008-11-04
Alright.  I'm now on my 3rd install of Intrepid.  I learned a few things:
1.  It's a really bad idea to copy your entire home folder of your old partition to your brand new /home partition as root while in your new install.  This causes many permissions errors, among other annoyances.
2.  Simply reinstalling your / partition and trying to use this messed up /home partition won't help either.

I've got the tri-boot going quite well now.  On my 3rd install, I set up a small partition for /boot and stashed LILO there.  Since LILO crashed on my second try, my plan is this:  Use the Vista bootloader (on MBR of sda) to chainboot LILO (just have to point it to / partition - it finds the /boot partition).  If anything fails, i believe GRUB is still installed to the MBR of sdb, so i can just boot from the other hard drive and fix up LILO.  I didn't allow LILO to touch the MBR, so i'm pretty sure GRUB is still there, but i don't want to try it in case it somehow messes up LILO.  We'll save that one for emergencies.

I notice LILO boots slower, but shuts down much faster than GRUB.  Also, the LILO install fresh from the CD was broken - it keeps asking for a bmp file that doesn't exist, but it seems to work just fine if you edit /etc/lilo.conf to just "text" mode instead of "bmp".

I also went through Wyth's Y510 instructions for getting the sound to work.  It seems his instructions work just as well for the Y710, but... i notice lenovo-sky as a model option works well, and makes use of the "surround" channel for subwoofer, and "center" and "LFE" now do nothing... but it seemed quieter to me, so i tried the old Y710 suggestion of 6stack-dell and to me it sounds louder for sure.  Be sure to set it to 8 channel, in which case surround does nothing and center and LFE both control the subwoofer.  Anyone with a Y510 want to try this and see if it works better?

Brightness isn't circular; instead when you turn brightness up, it seems to jump up two levels and then back down one... and the opposite logic for turning brightness down.  Weird, but not annoying enough for me to do anything about it.  Brightness jumps down a few levels on battery power, but all levels are still available.

Webcam (with cheese) isn't working out of the box... i'm still playing with it.

---

### Post by HunterThomson on 2008-11-05
Well I am back to Ubuntu and liking it. I resized my swap partition then when trying to make it mount on boot I somehow messed up the whole HHD. Not even Gparted on a live cd could read anything. I didn't fell like spending the next month installing Archlinux and after installing Xubuntu on 4 of my friends computers I have come to find two things. One, getting niddy griddy with Linux is a lot of fun though time consuming. Two, at then end of the day you just want your computer to work with out a bunch of hassle. So, back to friendly Ubuntu it is.

Really, what took me ~4hrs to install and setup in Xubuntu (xorg, Xfce, video driver, flash, java, laptop-mode-tools, locals, volume button, clock, logfiles....) Would have taken me 30+ hrs with Archlinux.

And I am glad to report that 8.10 is Good. 

Wireless is up on boot :)
Sound stays where you set it :) And Sound sounds better.
Headphones Mute the speakers :)
Back light "Seems like" it is brighter. Mine dose that thing chargersfan420 was talking about but hay it seems brighter for real. When I first booted into the live CD it thought the screen was full bright for sure.

---

### Post by wyth on 2008-11-07
So a kernel update later and my VirtualBox-ose version broke.

However, I found this -- there is a repository with a key for the Sun version.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

And it works fine.

**EDIT**

ProductiveLinux has [this post about getting USB support in VirtualBox under Ibex]("http://productivelinux.com/2008/11/09/how-to-get-usb-working-in-virtual-box-on-ubuntu-intrepid-ibex/"), and there's also [this thread]("http://pennsylvania.ubuntuforums.com/showthread.php?t=946268"):

```
#Make USB Work in Sun VirtualBox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Remounting didn't do it for me, but I found I was no longer part of the vboxusers group -- be sure you're part of that.

---

### Post by chargersfan420 on 2008-11-13
Hmm, it appears my sound issues aren't over yet.

Audio works when i have Autodetect in Sound Preferences (after a reboot only, and it even makes the Ubuntu startup sounds choppy), and when i select ALSA (although when i press the Test button, the first second is a skip). No other options here give me sound.

With ALSA selected, Totem sometimes plays music, and sometimes claims to be playing but no sound comes out. With Autodetect, Totem plays sound normally. With either option, the visualization is horribly choppy, and makes a strobe light effect. Repositioning the window doesn't move the visualization pane for a couple of seconds, and the visualization pane will overlap other windows, even if they are on top of Totem.

Any media player i use in VirtualBox (WinXP) will cause the sound to skip exactly every 5 seconds. This also includes using flash to watch youtube videos. I've tried all of the sound options for VirtualBox and they all give the same result.

I have also recompiled ALSA a few times by following Wyth's instructions (post 146), which i realize is not the exact same model...

EDIT: Also tried switching model back to lenovo-sky but it didn't make any difference.

It seems to me that I must be missing a package, or a package is malfunctioning, or maybe there's a couple of conflicting ones... All i know for sure is that I have no idea what to try next. Any help would be greatly appreciated!

---

### Post by wyth on 2008-11-13
chargersfan, in the terminal try
```
alsamixer -Dhw
```and tell us what card and chip it's using (it'll say at the top).  Since you have a different model, you may have some different specs.

---

### Post by chargersfan420 on 2008-11-13
Thanks for the quick reply, Wyth.

It says:
Card: HDA Intel
Chip: Realtek ALC888

I believe you had the same listed in your instructions.

:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Motorola Si3054

The post before your instructions, you said this:
"I installed linux-headers-lbm, linux-backports-modules-intrepid-generic, medibuntu, ubuntu-restricted-extras, all that."
Is it possible I'm missing one of these common modules... perhaps not one of the 4 mentioned?
Oh, and i couldn't find medibuntu...

---

### Post by wyth on 2008-11-13
Yep, those are the same specs I have.  But here's a couple things that may help:

The latest kernel is 2.6.27-8-generic.  I haven't compiled ALSA for that yet, but I ran into an issue with that kernel, NetworkManager, and everything locking up.

One thing I had to do was remove linux-backports-modules-intrepid-generic and all its attendent packages.  So I purged that, then ran ```
sudo apt-get autoremove
``` and cleaned out the unnecessary stuff.  That may help, and possibly trying the 2.6.27-7-generic kernel again.

Oh -- to get Medibuntu, you need to add a repository. More info is [here]("http://medibuntu.org/").  Short version:

Add the following to your sources.list:
```

deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
deb-src http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
```
Then run an apt-get update, which might spit something negative, but you need to do it so you can then run ```
sudo apt-get install medibuntu-keyring
``` and then run another update.  Then you should have the Medibuntu repository in place.


I wish I knew enough about this stuff, but I'm just not clear on the generic kernel -- is it supposed to automatically choose the best specs for a system, or would we be better off with the 386 kernel, or one of the other many kernels in the repository?  

Another thing I wish I knew more about was the difference between all the different brews of Java.  My Firefox 3.0.3 is now spiking my cpu up past 90%, and from what  understand it has something to do with Java.  Only I don't know what to replace.

---

### Post by chrismulderza on 2008-11-17
Good day all,

I have been using the Lenovo Ideapad Y510 since April of this year (2008), and have been following this thread since then. (My Y510 never even started the supplied Vista O.S. :) ) First of all thanks to wyth and HunterThomson for their relentless testing, and input ... I've recently upgraded to Intrepid (8.10) and had many of the same issues, especially with sound. 

I've managed to fix the majority using the vanilla kernel 2.6.27-7-generic, and compiling alsa 1.0.18rc3 drivers. Using the model=lenovo-sky switch in alsa-base in /etc/modprobe.d .. 

Anyways so that's my feedback on the laptop.. why I'm actually posting, is to gauge the interest and support from folks here on this forum for a patch to the current alsa-driver-1.0.18rc3 source tree, and if anyone would be interested in helping out with testing? 

I'm by no means a regular driver developer, but I've looked through the source code, and think I'll be able to hack through it enough to create a model named "lenovo-y510" that would at least initially map all the volume controls properly.. ;)

So if anyone's interested, I've got some free time coming up in a week or so, and will start "hacking away" at the driver sources, hopefully to post a patch on this forum soon! ... 

Cheers!

---

### Post by wyth on 2008-11-17
If you get something working, I'd give it a try.

---

### Post by em4g.3ht on 2008-11-17
Hi everyone, I have been reading this forum for a while now, and have just about every issue solved, except for the webcam

I am not the best gnu/linux user but I try:)

anyway I was wondering, what driver is our y510 webcam using because there is a very extensive driver update for 8.10 here:

[http://ubuntuforums.org/showthread.php?t=966398&highlight=%2Fvar](http://ubuntuforums.org/showthread.php?t=966398&highlight=%2Fvar)

-i dunno if this will help anyone or not, I just really want my webcam to work.

---

### Post by wyth on 2008-11-17
Man, I don't know... I had to remove the backports because it killed NetworkManager in the past two kernels (it wouldn't pick up any wireless, like the kill switch was permanently on).  Personally, I don't use my camera nearly as much as I use NetworkManager.

But I have something else to talk about -- stay tuned for the next post.

---

### Post by wyth on 2008-11-17
So lately, with kernel 2.6.27-8-generic, I've been getting some hard freezes.  There are bugs galore filed out there about this sort of thing; everything freezes up with a nice hard lock, and the wireless and caps lock lights flash.  I think this may have something to do with wireless, but I'm not sure, and it doesn't seem like anyone is paying all that much attention to the issue yet, save for those who have the problem.  

However, removing everything that has to do with pulseaudio may help if you're having this issue.  ```
sudo apt-get purge pulseaudio pulseaudio-utils pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 gstreamer0.10-pulseaudio
``` etc.  That should get most of it out, but there will be some extra stuff in there; a simple ```
sudo apt-get autoremove
``` should help with that.

Let me just say that my hard freezes are happening almost exclusively on my university's open network (since the new NetworkManager doesn't work with their secured network anymore).  I'm just sayin'...

---

### Post by em4g.3ht on 2008-11-18
that interesting, I have been experiencing, the same freezes, with blinking lights and everything. I thought it had to do with my /var being full (i guess there was a bug, but it's fixed now). Ever since I cleaned up my /var i haven't had the problem.

the only other time I have had this (still before I fixed the /var issue) was when I loaded steam up. I thought it might have been a wine server error.

It would be nice to get to the bottom of this one...if you don't want to work on the webcam issues :lolflag:

---

### Post by wyth on 2008-11-18
I'm almost positive the freezing is a NetworkManager issue, although it seems some have experienced the problem with compiz ([as this bug shows]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/293200")).  

After I removed pulseaudio, everything was fine on my WPA2 network at home; suspended and came out numerous times, and ran all night without issue.  As soon as I connected to the insecure network at my university, it hard froze within two minutes.

---

### Post by em4g.3ht on 2008-11-18
does it do the samething if you connect via ethernet?

---

### Post by wyth on 2008-11-18
I rarely connect via ethernet, but no, I haven't noticed the freezes when I'm jacked in, and it never happens to my desktop at home (which is always jacked in).

---

### Post by em4g.3ht on 2008-11-18
hmm I have herd of a bug from the intel wireless driver, but I am not sure it causes the same symtoms. They supposedly have a fix for whatever it is on the way (I believe)

---

### Post by chrismulderza on 2008-11-19
Hey folks,

Just been tracking the wireless freeze issue here on the forum for the last day or so ... I've had the same sort of wireless issues, especially when trying to connect to an "open" network provided by certain Cisco Aironet AP's as found in larger wifi deployments :( ... I eventually solved the problem by reverting back to the ipw3945 driver, instead of the iwl3945 as packaged with the kernel/ubuntu from 8.04. This forum post [here]("http://forums.debian.net/viewtopic.php?t=29245") details on how to replace the driver, however this does introduce some issues with hibernate/suspend operations depending on your configuration.. YMMV .. 

Hope this is of some help to someone ... 

Cheers!

---

### Post by HunterThomson on 2008-11-20
I just got a D-link DI604 gateway router and a Linksys WAP11 for $20 on craigslist.org:) I flashed the WAP11 v2.2 with 2.61 D-link 900AP+ firmware, which is nice D-link to D-link. This also adds DHCP 802.1x, antenna throttle, 22M, Repeater Mode and Multi-point Bridge Mode. Wanting Linksys WRT54G to use DD-WRT. I have been turning my wlan on/off, 11M 1M 54M, changing modes... all no problems at all. My built in wlan is super powerful. I turn on wireshark and see AP's a block away an around the corner. I use it for sniffing and I inject with a WUSB54GC.

Have any of you tried WiFi-radar? That mite work.

By the way, my web cam dose not work in Xubuntu 8.10... but i have never used it once or wanted to use it. So, I don't care. Just FYI. Also, I have never been given the option to upgrade to 2.6.27-8, still on -7.

Also, fellow intel graphics card users. Xfce has a window compositor that can make all windows even videos transparent and add shadow effects with no problem with the intel driver i.e. compiz. You can also use 3DDesktop to give you a cubed desktop effect when changing workspaces. This desktop effects set-up will also run on slow PCs no problem. I don't see any difference in ram or CPU with window compositor on/off.

---

### Post by em4g.3ht on 2008-11-20
I was think about re partitioning my hard drive, so that I could add a Fat32 partition (for bios) and also 3 more partitions for maybe a gentoo or an arch distro (i'm feeling adventurous)

I know you can't have more than 4 primary partitions and here's what I have now
```

/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        3326    12064815   83  Linux
/dev/sda3            3327        3630     2441880   82  Linux swap / Solaris
/dev/sda4            3631       30401   215038057+  83  Linux

```
if someone could do a quick walk through of how to make extended partitions (even in gnome partitioner), so that i could boot in to both OS's.

I was just going to go for it, but I thought I would ask before bricking (or force my self to re-install) the one computer that i have.

---

### Post by chargersfan420 on 2008-11-20
I read somewhere that Linux names partitions sda1,2,3,4 for primary and 5+ for extended... that's why it sometimes skips straight to 5, depending on your setup (much like mine was)...

So if that's the case, you might already have 4 primaries...

---

### Post by em4g.3ht on 2008-11-20
yes this is the case, I was wondering if there is anything to watch out for when setting up extended partitions. For example, do they behave diffrently? Is there something special I need to do to add them?

---

### Post by chargersfan420 on 2008-11-20
I'm sorry i can't offer expert advice (because I'm no expert), but i have also heard that if you're using LILO, you have to have your / drive installed on a primary...

I'm only using LILO because i'm on a Y710, and the optical drive doesn't work at all with GRUB.

If this doesn't concern you, i think it's fairly straightforward if you have empty space to work with... but if you're resizing, then proceed with caution!  The last time i resized a partition, GRUB renamed all of my partitions and Hardy became unbootable....  Granted it may have been repairable, but i had to put Intrepid on a primary for LILO anyway...

---

### Post by em4g.3ht on 2008-11-20
eek, this makes me worried, I have already resized once (which took 4 hours). I'm not sure if I should risk it now.

however the only thing I need to do is snip some space off the end. So it should be fine right?!

---

### Post by HunterThomson on 2008-11-21
Never resize or mess with partition table. Tecnecly you can but be prepared to loss it all, For Real. 

That said I have done a lot of partitoning. This is what I would do... I'll explain down below>>>

sda1  1GB FAT23
-----------------------------
sda2  extended
-----------------------------
sda5  10GB   /"RooT"   Ubuntu......................
sda6  10GB   /"RooT"   Archlinux...................
sda7  10GB    /"RooT"   FreeBSD.....................
sda8  5GB    /home     Ubuntu .....................
sda9  5GB    /home     Archlinux................... All ext3... swap is swap
sda10 5GB   /usr      FreeBSD.....................
sda11 2GB    /var      Ubuntu......................
sda12 2GB    /var      Archlinux...................
sda13 2GB    /var      FreeBSD.....................
sda14 3GB    SWAP..................................
sda15 198GB-------ext3----Files-&-Midia............

Install Archlinux first. And don't install grub. This way the Ubuntu installer should find Arch.

Then install Ubuntu and make sure Grub is installing to the MBR. I think it dose automatically. Ubuntu should find Archlinux and add it to the Grub menu. But you mite have to do it with a text editor. 


USE Archlinux it is the best and BSD would be cool to have:)

---

### Post by em4g.3ht on 2008-11-21
Thank you this is exactly what I was looking for!! I should have some time to do it this weekend!

one question though, how are BSD's in comparision to arch or ubuntu? like preformance, complexity and support?

I have always been a little scared to take the plung into BSD's and Arch was a challege, but fun so I was just wondering if it is worth it.

---

### Post by Gruu on 2008-11-22
please delete this message; it is obsolete (all problems were fixed after restarting x)

---

### Post by wyth on 2008-11-23
Gruu, if you run into any more problems with your wireless, make sure you don't have any backports installed, and try the 2.6.27-7-generic kernel.  

The 2.6.27-8-generic was causing my machine to kernel panic into a hard freeze.  Apparently this is due to the wireless, and backports is supposed to take care of that, but the backports right now breaks the wireless (at least on my machine).  You can install them, but no networks will show, and you can't modprobe the module.

---

### Post by HunterThomson on 2008-11-23
> **em4g.3ht said:**
> Thank you this is exactly what I was looking for!! I should have some time to do it this weekend!

one question though, how are BSD's in comparison to arch or ubuntu? like preformance, complexity and support?

I have always been a little scared to take the plung into BSD's and Arch was a challege, but fun so I was just wondering if it is worth it.

I don't really know a whole lot about BSD but I think I can answer you question to a satisfactory degree. Performance is suppose to be better. The BSD Kernel is suppose to be better then Linux. As for Complexity, I'd say it is just like any other Unix copy like Linux or MacOS. BSD uses .rc files to control everything that happens at startup i.e. daemons, modules....That makes BSD way simpler to control. Archlinux uses the .rc stuff. BSD names the HHD partitions really strange names which seems to cause problems. I read hardware support in BSD is always a step behind Linux.

---

### Post by em4g.3ht on 2008-11-23
thanks hunter, I think I will have to check this stuff out for myself ;)

I SOLVED (kinda) the issue with the web cam!

firstly check this thread out:

[http://ubuntuforums.org/showthread.php?t=966398&highlight=%2Fvar]("http://ubuntuforums.org/showthread.php?t=966398&highlight=%2Fvar")

*don't install backports kernel, because I herd it can break the wireless, and lead to hard freezes. It didn't for me, but it also didn't solve anything.

if that doesn't get you up and running, and you have a lenovo y510 here's what I did:

firstly if you have cheese insalled uninstall it:   sudo apt-get remove cheese

then clean apt cache:   sudo apt-get clean

then re-install cheese:   sudo apt-get install cheese

open cheese (here's where it never worked for me, always froze) it should detect your camera after linuxdragons instructions, now go to preferences and change the resolution to 960x720. Now make sure to shut off your camera before exiting cheese (Fn+esc). After exiting you can turn you camera back on and go back into cheese, and you should see yourself. Make sure to turn you camera off BEFORE closing cheese each time (also remeber to turn it on before entering cheese ;))

you also have to exit everytime you want to change an effect or cheese will freeze. Probably best to shut your camera off before changing effect.

*I have no idea why this works, and I am sure there is someone out there that knows a better way, but if you have the urge to impress your friends with awesome webcam pics, this should work until someone better and/or smarter solves this bug.

by the way, ekiga softphone worked with no tinkering after fallow linuxdragon's instructions.

---

### Post by chargersfan420 on 2008-11-25
Okay, I've been messing around, and I think i have got more specifics on some of my difficulties...

@ em4g.3ht - I tried your webcam "fix" on my Y710, and it worked the way you describe, which is better than nothing at all... 
@ everyone - however, the choppy visualization problems i spoke of earlier (in totem) seem to also be affecting Cheese.  I'm guessing this isn't a codec problem anymore... But still no idea where to look.

I have also found that the skips every 5 seconds in any Virtualbox - XP media players isn't limited to media players at all.  Virtualbox itself skips every 5 seconds... it used to be that the virtualbox process would eat one of my two cpu's all the time, and then drop down to 10 percent usage for one second (exactly every 5 seconds)... I just installed the latest version (2.0.6, xVM), which appeared to come out yesterday.  I have also upgraded my guest additions (which i notice some strange things happen if you don't update your guest additions when you install a new version of virtualbox).  The skipping doesn't start right away anymore, but is unstoppable when it does... it also no longer eats 100% of one cpu when operating normally..

I have also tried purging PulseAudio, as per Wyth's instructions, which didn't help at all.  Yesterday i found generic instructions to configure PulseAudio [here]("http://ubuntuforums.org/showthread.php?t=789578"), which also explains why it is a good idea to have PulseAudio - for example, Wyth, if you've still got it purged, can you play sound from two different applications at the same time?

Since configuring PulseAudio and reinstalling Virtualbox more than once, i notice my virtualbox skips have occurred less frequently, but i still don't know why.  If it keeps up, i'm going to create a brand new virtual machine - maybe since i started this one on 1.5.6, that's why it's buggy...

The webcam still won't work in XP - it still recognizes when i "plug it in" to the VM, but it still continues to say that the device is in use.  I notice it takes a minute to initialize with Cheese after following em4g.3ht's instructions... perhaps XP is too impatient?

Cheese doesn't give me the option to use 960x720 resolution.  I put it on 640x480, which sadly is the closest thing.

I also have a brand new Y710 here that i'm installing Ubuntu on for a coworker... 
- There seems to be no problem with virtualbox so far.  
- Just finished with the webcam instructions.  It's working, but it also is having the visualization choppiness problem - cheese and totem.  Can't explain why, but the choppiness is far less of a problem to this machine... but it still does weird things, like show the visualization on top of active windows, or not moving it when i relocate the window...

Sorry if i sound like i'm rambling... i just want this damn thing to work!

---

### Post by chargersfan420 on 2008-11-25
Update:

I ditched the proprietary video driver that seems to be the only (easy) way to get 3D effects working on a fresh install.  
System - Administration - Hardware Drivers  -- deactivate proprietary driver

And then, i went to this website:
[http://ati.amd.com/support/driver.HTML]("http://ati.amd.com/support/driver.HTML")
and i grabbed the correct driver for my video card.  I don't know about you Y510 people, but my Y710 has an ATI Radeon HD 2600.  There is also a link to a PDF with instructions on that page.  Remember to run that last command line in terminal when you're finished with the GUI and before you reboot!

I'm happy to say that the graphics / 3D acceleration looks much better than it did with the initial proprietary driver.  I haven't encountered any choppiness when using compiz effects, which happened occasionally before.  It also installed a Linux version of Catalyst Control Center, which is full of some very nice advanced graphics options...

... unfortunately, it didn't solve the visualization problem.  Since then I reinstalled cheese and still no joy!  Are there any other Y710 users out there that are having visualization problems in Totem & Cheese and possibly others, or is it just me?

Perhaps i should try more programs that use some sort of visualization...?

---

### Post by wyth on 2008-11-27
> **chargersfan420 said:**
> I have also tried purging PulseAudio, as per Wyth's instructions, which didn't help at all.  Yesterday i found generic instructions to configure PulseAudio [here]("http://ubuntuforums.org/showthread.php?t=789578"), which also explains why it is a good idea to have PulseAudio - for example, Wyth, if you've still got it purged, can you play sound from two different applications at the same time?

I still have it purges, and I only have ALSA compiled for the 2.6.27-7-generic kernel (it's the most stable for me).  I can report that I *can indeed* hear two apps at once.  I just streamed music via Banshee and opened a movie in Totem, and it sounded like I was in a train station.

---

### Post by wyth on 2008-11-27
Okay, so I had a bit of a breakthrough today.

**The Problem**
For some time now, I've been getting some random lock-ups; kernel panic with a hard freeze I could only end with a hard reset.  This had something to do with the wireless card, iwl3945 -- it really didn't like one of the networks at my university, and whenever I got on that network, it crushed my system.

I read in a number of places that in order to fix this, one needed to install linux-backports-modules-intrepid.  Okay, why not.  That introduced the other problem; the hard freezes may have stopped, but it broke wireless.  No networks could be seen, and the module couldn't be modprobed.  Of course it fixed the problem -- how can the wireless card bring down the system if it's broke?  Removing the backports fixed the wireless, but left the freeze problem.

**The Fix**
After some more research, I found some references to "proposed" as a possible culprit, although I couldn't find enough to tell me what they meant.  So I experimented.  I commented out the proposed repositories in my sources.list and did all the updates and autocleans.  

The first thing I noticed was that the 2.6.27-10-generic kernel was no longer available, but the 2.6.27-9-generic was (before it seemed to skip 2.6.27-9-generic).  I added the 2.6.27-9-generic kernel, made sure I had the backports installed, the headers, restricted modules, all that stuff, and rebooted.  

AND WIRELESS WAS THERE.  AND IT WAS GOOD.

So far no freezes (although it's a U.S. holiday and I'm not on my university's network), wireless is working fine, and everything seems happy.

So if you're having any hardware woes, consider commenting out the intrepid-proposed lines, re-installing some things, and it may solve some of your issues.

---

### Post by b0yd07 on 2008-12-04
1. Does anyone here have a 'popping' noise come from the speakers on shutdown/suspend? Sounds like a little power surge hitting my speakers. It's not loud but it's definitely annoying.
These guys seem to have the same problem with no answer: [HERE](http://ph.ubuntuforums.com/showthread.php?t=934399)

2. Also, anyone else have green artefacts appear at the top of the screen when initially shutting down? They appear for a split second right after the desktop disappears. Again, just an annoyance.

3. The wireless card turns on no matter what. I have the switch turned off but the purple light still lights up and my laptop still detects a signal. I can slide it on and then back off again to turn the light off, but it still insists on running.

I think that's it. Everything else works wonderfully thanks to you guys and this enormous thread.

Please help me out if you know how to sort these issues out! :D Thanks in advance for any help.

---

### Post by chargersfan420 on 2008-12-04
Good news for any Y710 users - i have now officially solved all of my problems... I think.

I determined that the poor visualization was the result of using the repository supplied driver for my graphics card.  Turning off "extra" visual effects in the Appearance menu managed to fix it, but it disables compiz, avant, and other things.  So, clearly not a solution.

I downloaded the driver from the ati/amd website and followed instructions to compile it, which knocked out xorg.  I was only able to boot into a text-only mode.  After several hours of getting the old video driver back, only to have the new one crash again and again was simply too frustrating.  I also experimented with the 2.6.27-3-rt kernel, (and i'm using 64-bit), which probably only made matters worse.

So, i took the plunge and decided to go back to Hardy Heron, and everything is working great!  Visualization is back to normal, virtualbox doesn't skip every 5 seconds anymore, and the webcam worked out of the box.  I didn't even have to recompile ALSA, i simply edited alsa-base and inserted the line of code for model name.  I'm going to stick with the 2.6.24-22-generic kernel now, because i have no complaints at all anymore.

I was mocking Linux's "It just plain works" motto before, but now i see that it can, in fact, just plain work.  Setting up /home on its own partition saved me countless hours of reconfiguring stuff, so i believe it should be a must with every linux installation.

Since i had a second Y710 here to attempt installation on, i believe that the graphics driver problem will affect all Y710 users - perhaps until ATI / AMD does something about it, but i wouldn't count on that any time soon.  I don't know what caused the virtualbox skips, and i haven't used the newer Y710 long enough to see if it was a common problem... but starting tonight, i'm downgrading it to Hardy also.  If anyone out there with a Y710 running Intrepid got their video to work properly, please say so.

Another weird problem i had on Intrepid is that whenever i booted via LILO, with a CD (Blu Ray?) in the drive, i would get alsa segfaults in dmesg.  These are also gone in Hardy.

After being through several installations of Ubuntu now, i think i can put together an installation guide for the Y710, if anyone is interested.... let me know.

The next thing to try is to see if i can get Blu Ray working...

---

### Post by chrismulderza on 2008-12-11
Good day all!

Anyone had anymore progress on the backlight issue and the DSDT? 

Thanks

---

### Post by wyth on 2008-12-12
> **chrismulderza said:**
> Good day all!

Anyone had anymore progress on the backlight issue and the DSDT? 

Thanks


I haven't, but  noticed something last night.  My wife logged in on my laptop under a guest session, and it seemed like the backlight worked just as it should.  I just don't get this problem -- it works fine in a guest session and on the live CD, but not on a full install?

---

### Post by chrismulderza on 2008-12-17
> **wyth said:**
> I haven't, but  noticed something last night.  My wife logged in on my laptop under a guest session, and it seemed like the backlight worked just as it should.  I just don't get this problem -- it works fine in a guest session and on the live CD, but not on a full install?
Hey wyth,

I was curious to check this out, so I tried logging with a guest session on my laptop, but got different results. The backlight control "appears" to be working correct on my laptop when using the hotkeys i.e. fn+up & fn+down. It starts the popup bar in the middle, then if you set it brighter the bar goes to full, and then you can still make the screen go brighter. If you go in the opposite direction it dims until you get half way, and then goes brighter again. Adding the brightness applet to the taskbar when logged in as guest, still only works in reverse.  Go figure ... :P

Anyways I've been doing some trawling across the web, researching this issue, as well is trying to figure out how the DSDT and ISL and AML work, and have come across some interesting bits... 

According to the kernel bug list ([Here]("http://bugzilla.kernel.org/show_bug.cgi?id=12037")) there was an issue with ACPI returning the brightness values returned from the _BCL DSDT method "as is", meaning that it seems Lenovo programmed the DSDT in reversed order, and hence ACPI "reverses" them. The bug has apparantly been fixed in the kernel, so it might just take some time before it makes it down into an Ubuntu update. What's interesting to note, is that the Thinkpad SL300's and SL500's apparently also make use of the same or rather similiar BIOS and EC as the Ideapad's.

I am going to try a fix similiar to what is mentioned in bug 12037 and see if I can get any better results, will keep you folks posted.

What would also be useful is to get some information regarding the make and model of the Ideapad's embedded controller, so that we can modify the DSDT to be more "Linux friendly" ... anyone have any good connections at Lenovo? perhaps they can point us to a reference manual etc. ??? ;) While looking through the DSDT I've noticed that there seems to be a lot of Windows V!sta specific function calls in the DSDT, especially in the case of the backlight control method(s) _BCM etc.. 

Anyways that's it for now.. 

PS. Making some progress on a patch to the ALSA drivers as well for the Ideapad, hope to have it compiling by the weekend .. :P .. 

Cheers all!

---

### Post by chrismulderza on 2008-12-17
Oops that post went in twice for some reason

---

### Post by HunterThomson on 2008-12-21
Well Good work evryone :)

As for the green artifacts on the screen at bootup and shutdown.... I have install ubuntu on two computers that that happens too. I just don't wory about it. I am sure it is fine.

Yes Linux is stable as hell if you use the older versions of programs that the programmers have had time to tweak and fix up. The new stuff is always a little less stable but the choice is up to you. That is the nice thing about Linux.

Nice work on the DSDT back-light stuff. I really want that fixed. And it just pi**es me off that it use to work but now no. 
You seem to be on to some good stuff. If you can code in AML then we should be able to get it to work.

Also, have you tried to set a ACPI flag to tell the BIOS that you are using VISTA and see if that works. Should enable all that Vista only code. But I forgot how to set the flag. I'm sure it is in the man pages.

Owe, I also set up a guest account and I don't think that it made any difference for me.

---

### Post by chrismulderza on 2008-12-22
Hey HunterThomson,

Just a quick update.

I have tried setting the ACPI flag to Vista with:

```
acpi_osi="Windows 2006"
```

Did not seem to make any difference. I'm assuming that the VISTA ACPI drivers have the ability to call some proprietary methods in the DSDT. Also just fixing up the package that gets returned by the _BCL method in the DSDT does not seem to fix the reversed backlight problem... :( ... The upside is that it does seem to make the brightness control "smoother", because of the additional steps. 

From some extensive googling, it seems that the problem may be more complex, and that it could be somewhere between HAL and the kernel ACPI.. I'm going to try and patch to the latest ACPI release, which should have some fixes included and see... 

I'm starting to get comfortable with the AML code stuff, but it damn difficult without having the Emedded Controller reference, which I'm still looking for... :( .. There's alot of other good stuff that can be done with a proper DSDT, especially around fan control, power management and the THERMAL ZONE stuff ... although I have not spent too much time looking into it, as I have been sidetracked by the ALSA patch I'm trying to get done for these laptops. There's another piece of opensource code that has very little documentation ... :P ... 

On a side note, researching the ALSA drivers and the likes, I've found a fairly good sound setup, using pulse audio daemon at the centre of it all. I know some folks complained about it, but I'm starting to think that it's rather good, and has some really good potential. When I have some more time available, I'll start putting together a howto document for that as well... 

Cheers all!

---

### Post by chrismulderza on 2008-12-22
Good News Everyone!

I have a correctly working backlight on my Ideapad Y510! ... 

This has been achieved by using a custom DSDT, and nothing else, no fiddling with ACPI or HAL or anything like that.

After days of trawling and scrolling through the original DSDT I finally figured out that the Lenovo emedded controller seems to be expecting some specific input values, and that there seemed to be a slight mistake in the "Package" of values returned by the _BCL AML method. Additionally ACPI as bundled with Ubuntu and the Kernel at the moment, expects the values to be in the correct order, i.e. <value when on AC>, <value when on Battery>, val0, val1, val2 ...etc the most important thing to note is that ACPI at the moment does not appear to sort the values, and assumes that they are from lowest to highest. In the case of the Ideapad they seem to have been reversed.

I have attached the DSDT.dsl in BZIP2 format to this post for those who want to give this a go. 

You will obviously need the Intel ASL compiler:

```
sudo apt-get install iasl
```

To compile the DSDT just run:

```
iasl DSDT.dsl
```

Once it's compiled put it into the initramfs-tools directory under /etc:

```
sudo cp DSDT.aml /etc/initramfs-tools/
```

You might need to install the initramfs-tools package

```
sudo apt-get install initramfs-tools
```

and then finally regenerate the initrd image

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
```

reboot the machine and then give it a go... :P

Please test this and let me know if anyone is experiencing any other difficulties... 

Cheers all!

---

### Post by winnibob on 2008-12-22
> **chrismulderza said:**
> Good News Everyone!

I have a correctly working backlight on my Ideapad Y510! ...

Thanks a lot! This is awesome!!!
To me, it was the only thing that didn't work perfectly under Ubuntu, and now it does!

I tried it, it took me 2 minutes (with restarting!) and now it's perfect.

---

### Post by chrismulderza on 2008-12-23
> **winnibob said:**
> Thanks a lot! This is awesome!!!
To me, it was the only thing that didn't work perfectly under Ubuntu, and now it does!

I tried it, it took me 2 minutes (with restarting!) and now it's perfect.

You're welcome winnibob!

Just a note to the other users that may be of interest:

The DSDT.dsl will work with BIOS versions 06CN29W, 06CN30W and 06CN31W, as there was no change in the original DSDT that shipped with these BIOS versions. 

Have fun!

Cheers all!

---

### Post by HunterThomson on 2008-12-23
:guitar:     chrismulderza     :guitar:

YOU ARE THE MAN !!!! WOOOOOOOOOOOHHHHHHOOOOOOOOOOOOO !!!

I gave you two stars. One for the hard work and one for the Success.


Dude I knew it had to be the DSDT :) Thank you so much for taking that baton the rest of the way.

Have you sent it off to Lenovo So they can include it in the next BIOS update. Hell they should release a update right now, just for this fix. This is a huge big deal. That back light stuff really really got on my nerves. How can I tell people Linux is so good and my back light doesn't even work right.  

You also need to start a thread on the Lenovo forums too. 


This is just so alsom I can't even .... wow. THANK YOU.


P.S. Sents you are so good with this stuff now have you thought about working on a DSDT for the Y710. They are having a lot of problems and they all sound like a clear cut case of a bad DSDT.

---

### Post by talktorishav on 2008-12-23
A simple solution I found if the brightness is reversed.
[http://techspalace.blogspot.com/2008/12/brightness-reversed.html](http://techspalace.blogspot.com/2008/12/brightness-reversed.html)

---

### Post by chrismulderza on 2008-12-24
**@HunterThomson**

Thanks for the kudo's mate. Truth be told, the backlight was getting on my nerves too! :D

I'll post this onto the Lenovo forums in the new year, I'm off on holiday today, and will only be back the 5th of Jan 2009 Woohoo! ... \\:D/

I think it's been a collaborative effort on this stuff from everyone, even just the folks giving us some feedback on quirks in this thread :cool:

I'll be happy to look at the DSDT for the Y710 as well, not that I have access to one, but if it uses the same mobo I'm sure we can try and find some solution. So any Y710 users out there, please post the following to this thread:

The running generic DSDT

```
sudo cat /proc/acpi/dsdt > DSDT.bin
```

The output of lspci

```
sudo lspci -vvnn > lspci.txt
```

and the output of dmidecode

```
sudo dmidecode > dmidecode.txt
```

I suspect that they might be using the same mobo's but if not, then these bits will help me to "hack" :P some solution... 

My next challenge is to get the sound system working 100%. It does not seem too difficult, and at least I have gotten my hands on the Intel HDA spec, and the Realtek ALC888 codec spec, and some developer info from the ALSA site.

I have broken it down into the following requirements:

1 - 5.1 Surround (6 Channel Mode) should work (i.e Front, Rear, Center, LFE) when using built in speakers

2 - Speakers to be muted when plugging in headphones and switch to 2 Channel Mode)

3 - Should detect presence of a SPDIF connection in the headphone jack

4 - When using SPDIF, 8 Channel mode to be activated (i.e. Front, Rear, Center, LFE, Side)

5 - Switch capture source from internal mic to ecternal mic when jack detected in microphone input.

6 - (Optional) and if possible, ability to toggle headphone jack between headphone and line-out. (According to the ALC888 codec spec this should be possible, so that when connecting the Ideapad to a Hi-Fi Stereo system we don't introduce distortion on the output.)

7 - (Optional) and if possible, ability to toggle microphone in jack to produce output for "Rear line-out" (Should also be possible according to the ALC888 codec spec)


So this sounds ambitious, but I believe things should work correctly, 100% correctly at that. :P ... 

To everyone who has made some superb contributions to this thread, I wish you all a very Merry Christmas, and Happy New Year!.. ):P

Cheers all!

---

### Post by HunterThomson on 2008-12-25
Owe Ya, this whole thread and everyone here is awesome. And I get the feeling that there are a whole lot of people that read this thread and don't post. 12,000 hits so far and it has not been up all that long few months. We should start our own web site.... na, Ubuntu is the place.

Chargersfan420 was telling me about it and posted his DSDT.aml on page 8.

[http://ubuntuforums.org/showthread.php?t=870681&page=8](http://ubuntuforums.org/showthread.php?t=870681&page=8)

You know learning how to code AML is really cool. Your getting into some really low level stuff. It would be cool to learn how to code firmware for like routers and wifi cards and stuff.

Mary Christmas and a Happy New year everyone ):P

---

### Post by wyth on 2008-12-26
chrismulderza, yes that does sound ambitious, and I can't wait to see the results.  The backlight seems to be working perfectly, even after the latest kernel update.  (I re-enabled the proposed repository, to see if some Network Manager issues have been resolved, and I got a kernel update out of it.)

What you're saying about ALSA, at least on my rig, pretty much all works whenever I recompile it.  I can' speak to the SPDIF or other optional issues you brought up -- just never had the opportunity.  What I'm curious about is if there are new hardware configurations being shipped with this machine (at least the Y510) that changes the scenario somewhat. I know new video cards are being shipped, and I don't know if any other new components are out there.  But that could change someone's needed configuration to get sound fully working.  

I don't know if this is possible, and I really rather doubt it, but I wonder if there is some sort of way to compile ALSA once and make that "sticky" through the kernel upgrades, so I wouldn't have to recompile ever couple of weeks.  It's fine for me, but for others who are getting used to this stuff, it may be more pleasant to show them how they need to do something once to fix it, rather than having to fix it time and again, which gives it the sense of being perpetually broken.

Also looking forward to the post on pulseaudio. On my desktop I have no issues with it, except for I sometimes need to give it a kick in the pants after coming out of suspend.  I just haven't had time to work with it, so I'm not sure of it's uses at this point, aside from getting in the way of sound on my laptop.

(By the way, since ALSA is in the repositories, why can't it just work out of the box?  The current version in the repository is later than what was being downloaded and compiled by some of us last year, yet the extra features that make the sound worthwhile just don't work unless you download the same software and compile it yourself.  I'm just curious why that might be, and if there's a way around it.)

---

### Post by wyth on 2008-12-26
By the way, I know they've been talking about the screen brightness, etc. at the Lenovo thread for Ubuntu [here]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=802&view=by_date_ascending&page=1"), and I'm sure they'd love to see what you (chrismulderza) have done.

---

### Post by lun on 2008-12-27
Where do you put the dsdt.dsl?

```
nick@schwieterman:~$ iasl DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Error    4067 - Could not open file "DSDT.dsl" (No such file or directory)

```

I have it on my desktop now.

---

### Post by shinzou7 on 2008-12-27
@chrismulderza

would you be able to look at the DSDT for the Y530?  The brightness controls are reversed on this laptop as well, but everything else works great.

webcam, wireless, sound, battery monitor, flash card reader, function keys, and soft keys work great.

thanks for all your efforts on this topic.  It has been very enlightening to read this post and the tech involved in making all this stuff work.

---

### Post by talktorishav on 2008-12-28
> **chrismulderza said:**
> Good News Everyone!

I have a correctly working backlight on my Ideapad Y510! ... 

This has been achieved by using a custom DSDT, and nothing else, no fiddling with ACPI or HAL or anything like that.

After days of trawling and scrolling through the original DSDT I finally figured out that the Lenovo emedded controller seems to be expecting some specific input values, and that there seemed to be a slight mistake in the "Package" of values returned by the _BCL AML method. Additionally ACPI as bundled with Ubuntu and the Kernel at the moment, expects the values to be in the correct order, i.e. <value when on AC>, <value when on Battery>, val0, val1, val2 ...etc the most important thing to note is that ACPI at the moment does not appear to sort the values, and assumes that they are from lowest to highest. In the case of the Ideapad they seem to have been reversed.

I have attached the DSDT.dsl in BZIP2 format to this post for those who want to give this a go. 

You will obviously need the Intel ASL compiler:

```
sudo apt-get install iasl
```

To compile the DSDT just run:

```
iasl DSDT.dsl
```

Once it's compiled put it into the initramfs-tools directory under /etc:

```
sudo cp DSDT.aml /etc/initramfs-tools/
```

You might need to install the initramfs-tools package

```
sudo apt-get install initramfs-tools
```

and then finally regenerate the initrd image

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
```

reboot the machine and then give it a go... :P

Please test this and let me know if anyone is experiencing any other difficulties... 

Cheers all!


Is this the solution for reversed brightness?

---

### Post by wyth on 2008-12-28
> **lun said:**
> Where do you put the dsdt.dsl?

```
nick@schwieterman:~$ iasl DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Error    4067 - Could not open file "DSDT.dsl" (No such file or directory)

```I have it on my desktop now.


In the terminal, just be sure to cd into the directory you have it (Desktop) before you run the commands.  If you're in /home/[YOUR NAME] and tell the machine to run a command on a file that's in a different directory, it'll fuss at you.

---

### Post by lun on 2008-12-28
I regenerated the initrd.img with DSDT.aml and restarted and it broke my install.  This is my fault for getting involved with something that i was not completely clear on.  I think it failed because i have not yet updated the BIOS.  I tried to fix the kernel by booting into the second kernel in grub, but i messed that one up as well. :oops:

So now i am running from the live cd and am not too sure what i can do from there.  If anyone can tell me how to regenerate initrd.img in my first kernel without DSDT.aml, that would be greatly appreciated.

nick

I tried to update BIOS with the usbbiosflasher from hunterthomson, but i have to be root in order to run it:(.

---

### Post by shinzou7 on 2008-12-28
@lun

I had a similar issue and just put the kernel image back to what came with the default install.

try this:

sudo dpkg-reconfigure linux-image-2.6.27-9-generic

if that isn't your kernel version, just replace it with the one you have installed.

---

### Post by lun on 2008-12-28
That would do it, but the problem is is that i cannot boot into that kernel at all to reconfigure it.  When i try to boot into it it loads a little bit and then stops.  The only access i have to the files on my install is through live cd, and i cannot reconfigure the kernel through there (unless there is something i do not know).  I can see everything on my harddrive, but i cannot add or remove from it, nor run root commands to change it (obviously).

I reinstalled.

---

### Post by HunterThomson on 2009-01-01
> **lun said:**
> That would do it, but the problem is is that i cannot boot into that kernel at all to reconfigure it.  When i try to boot into it it loads a little bit and then stops.  The only access i have to the files on my install is through live cd, and i cannot reconfigure the kernel through there (unless there is something i do not know).  I can see everything on my harddrive, but i cannot add or remove from it, nor run root commands to change it (obviously).

I reinstalled.

Yes you do have to be root to run my script to make the BIOS-USB. 

sudo usbbiosflasher


MAKE SURE YOU READ THE QUESTIONS I ASK !!! READ ALL THE STUFF THAT POPS UP. IT TELLS YOU WHAT TO DO. YOU DON'T WANT TO FORMAT YOUR HHD ON ANTECEDENT.


You did not do this if you are getting a messaged that is telling you it didn't find the dsdt.

> ```
sudo cp DSDT.aml /etc/initramfs-tools/
```


===========================================
As for your Kernel.... You know there is a way to do it :)

I don't know step by step but if you google you could find it. 

What you need to do is boot into a Live CD then you can change to the root directory of your harddrive (( chroot  maybe)). This way your kernel will be from the Live CD but the root file system will be the one on your harddive. Then you can build a new kernel. Read this in the Debian instructions to "Install from a running Linux OS."

There is also a command to build a new normal Kerenel. Just a copy of the one you have. Then you boot into that and mess with that kernel. If it messed up then you can just boot into your first Kernel you have not changed.

---

### Post by HunterThomson on 2009-01-01
Good fun>>>>

Two days ago, late at night, I wanted to clear my SD card. So I opened the shell and typed


```
DO NOT RUN THIS COMMAND

sudo rm -r * /media/disk

DO NOT RUN THIS COMMAND
```

As you can see this deleted every file on my computer..... That sucked. 
Fresh install now......

Moral of the story,,,, Respect the Sudo.

---

### Post by sourcecode on 2009-01-03
Thnx to everyone on this thread !! I finally got all the issues fixed , though the webcam upside down prblm still exists , but I don't use the cam much.

Now I am ready to go around and flaunt my Y510 + Hardy combo :)

thnx
Source

---

### Post by sourcecode on 2009-01-03
> **HunterThomson said:**
> 
Note: If you are using a intel X3100 graficx card and don't want to mess everything up by running Compiz but still want to have the 3D desktop effects when changing desktops youcan use 3ddesktop

Ubuntu
sudo apget 3ddesktop
Archlinux
sudo pacman -S 3ddesktop

HunterThomson ,are u sure the 3ddesktop pack exists for ubuntu ? I get the msg

E: Couldn't find package 3ddesktop

when I run sudo apt-get install  3ddesktop


I've got compiz on my desktop with Gutsy . Want the same effects on my lappy with Hardy too. But don't want to get messed with the intel x3100 card 

thnx
Source

---

### Post by wyth on 2009-01-03
> **sourcecode said:**
> Thnx to everyone on this thread !! I finally got all the issues fixed , though the webcam upside down prblm still exists , but I don't use the cam much.

I know one person on here just opened up the screen case and physically turned the camera upside-down.  I don't use it enough to go that far, but it's a solution.

---

### Post by HunterThomson on 2009-01-04
Elow Sourcecode and mpc350.

Sourcecode. Ya your right there is to 3ddesktop in the Ubuntu repositorys. However here is a a link to all the .deb packages of 3ddesktop.

[http://debian.cs.binghamton.edu/debian/pool/main/3/3ddesktop/](http://debian.cs.binghamton.edu/debian/pool/main/3/3ddesktop/)

It works vary well just read the man page. You can even set a picture in the backgrownd. Also, the Xfce composit manager uses like no CPU/RAM and couses no problems with the X3100. It will make widows and menus and stuff transparent and also add shadows. I think you have to run Xfce to use it though.

++++++++++++++++++++++++++++++++++++

mpc350 

quote from PM.....

> I followed your info on getting the subwoofer to work with my ideapad y530, and it worked great until I rebooted; then no sub. Tried everything, including the other suggested lenovo drivers. They did not work either, but when I reconfigured for the first one [options snd-hda-intel model=lenovo-ms7195-dig] that I tried, it worked great again until reboot, then no sub. As a side note, the volume control is affecting the "Front" speakers on the gnome volume control and not "Master". You know, in case you are looking for more things to troubleshoot

I had the same problem for like two weeks..... I gave up... Then I found out all i needed to do was set the channel to 6 (( default is 2)) I still don't understand why it works after the first reboot and then it swiches back to 2 channel. But that was the problem and is probly yours too.

Just open up the volume manager and then click on the third tab. You will find the "ch" setting. Change it to "6" and you should be good to go. If you have problems finding the volume setting you can use the shell alsamixer. Just arrow over and you will see the channel setting. set it and press "Esc" to exit. 


YOU KNOW......???  Did you use the instructions on page one?? or the ones on page 15 ?

[http://ubuntuforums.org/showthread.php?t=870681&page=15](http://ubuntuforums.org/showthread.php?t=870681&page=15)

Use the new instructions from wrth. And use the lenovo-sky module, it's default setting is 6 channel. Also, make sure you install the newest alsa stuff the  1.0.18rc3

---

### Post by HunterThomson on 2009-01-04
Aloha everyone,

Well, I must say we are what Open Source I all about :)

Sound works :)
Backlight problem Fixed :)

I have updated the page one. I have also posted the DSDT fix on page one now.

++++++++++++++

But new problem I am having and wondering if it is just me. 

It seems that after i have started using the new DSDT my Sound is now all the way down on boot agin. I don't remember having this problem untill I set up the DSDT stuff. 

I can not really remember when this started happening. Maybe it was just an update that did it....

So, I am the only one ?
Do you think it is the DSDT or the ALSA ? 

Maybe I will try to build a new kernel then do the DSDT thing FIRST then do the ALSA thing. Maybe when the ALSA compiles it gets some of its cues from the DSDT and so now that I am using a changed DSDT the alsa isn't set up right for it ???

Just my guess.. What do you think?

---

### Post by wyth on 2009-01-04
I'm not sure if I mentioned this before, but each time there's a kernel upgrade, you need to recompile ALSA to get sound back.

Thought I'd throw that in, just in case.

---

### Post by mpc350 on 2009-01-04
What threw me about getting 6 channel sound was that that third tab in the gnome volume control was absent.  I had to go to preferences> enable channel mode.  Then the tab appeared.  Now all is right with the world.  --Actually, I would love to figure out how to keep Rhythmbox from rescanning all of my music and re-warning me about import errors with my DRM'ed music every time I launch.  That takes about 2 minutes and is a resource hog.

Thanks for your help

---

### Post by wyth on 2009-01-05
Oh, man, that Rhythmbox quirk is a big reason I stopped using it.  

I sort of like Banshee, but it lacks functionality that Amarok provides, and at least on my laptop, runs the cpu into the ground at times (mono?).  

Amarok does the job fairly nicely, but likes to crash at weird times, is clunky, and not nice to look at in Gnome, but it's the most functional one (for me, who downloads way too many podcasts and streams audio).  

I've been holding out some hope for Exaile.  In fact [I filed a bug report]("https://bugs.launchpad.net/exaile/+bug/276025") that basically lays out what I would love to see in a good Gnome music app that handles podcasts.  This was well-received by the developers (who urged me to file the bug report), and it was confirmed just the other day.  Development is slow on Exaile, as their team is basically one guy, but there is promise.

---

### Post by HunterThomson on 2009-01-06
Ya never used Rhythmbox sounds honorable. Armrok is nice to use but it is a resorce hog on slow hardware. XMMS is fast and looks good but the whole file system thing is kind of a pain. I don't really listen to music to much though. I watch moves and scifi when I am not hacking away.

The graphical ALSA mixer was the cause of trubble for me and a few other people as well. They didn't make the layout all that intuitive. Took me like two weeks to find the channel thing. I just use the alsamixer in the shell and tell people to use that one.

---

### Post by Gruu on 2009-01-10
I have a y510, but my webcam doesn't work. Here's the relevant portion of dmesg:
```

[   22.819055] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   23.817186] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
[   23.817197] uvcvideo: Failed to initialize the device (-5).
[   23.817371] usbcore: registered new interface driver uvcvideo
[   23.817379] USB Video Class driver (v0.1.0)

```

As polluxx mentioned forever ago (in the _[old thread]("http://ubuntuforums.org/showthread.php?p=5075504")_), my model should be supported, but it doesn't seem to work at all (cheese doesn't detect any camera). I've had this laptop for a while (the first installation was feisty), and I've just been upgrading as time goes on. Any suggestions?

Thanks in advance for any help :)

EDIT: I forgot to mention that the camera works fine when I *shudder* boot into vista, so it's not a hardware thing (at least I'm pretty sure it isn't ;)).

And just in case, here's the entire dmesg output from booting up just a few minutes ago:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7b0000 (usable)
[    0.000000]  BIOS-e820: 000000007f7b0000 - 000000007f7be000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f7be000 - 000000007f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7f7b0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782d000 - 37fefdbe
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F81F0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7F7B0100, 007C (r1 LENOVO CB-01    12000726 MSFT       97)
[    0.000000] ACPI: FACP 7F7B0290, 00F4 (r3 LENOVO CB-01    12000726 MSFT       97)
[    0.000000] ACPI: DSDT 7F7B0640, C3A6 (r1 LENOVO CB-01           1 INTL 20051117)
[    0.000000] ACPI: FACS 7F7BE000, 0040
[    0.000000] ACPI: APIC 7F7B0390, 005C (r1 LENOVO OEMAPIC  12000726 MSFT       97)
[    0.000000] ACPI: MCFG 7F7B03F0, 003C (r1 LENOVO OEMMCFG  12000726 MSFT       97)
[    0.000000] ACPI: SLIC 7F7B0430, 0176 (r1 LENOVO CB-01    12000726 MSFT       97)
[    0.000000] ACPI: BOOT 7F7B05B0, 0028 (r1 LENOVO OEMBOOT  12000726 MSFT       97)
[    0.000000] ACPI: ECDT 7F7B05E0, 0054 (r1 LENOVO OEMECDT  12000726 MSFT       97)
[    0.000000] ACPI: OEMB 7F7BE040, 0060 (r1 LENOVO AMI_OEM  12000726 MSFT       97)
[    0.000000] ACPI: HPET 7F7BC9F0, 0038 (r1 LENOVO OEMHPET  12000726 MSFT       97)
[    0.000000] ACPI: GSCI 7F7BE0A0, 2024 (r1 LENOVO GMCHSCI  12000726 MSFT       97)
[    0.000000] ACPI: ATKG 7F7C02D0, 8024 (r1 A_M_I_  OEMATKG  5000702 MSFT       97)
[    0.000000] ACPI: SSDT 7F7C8DD0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003782d000 - 0037fefdbe]          RAMDISK ==> [003782d000 - 0037fefdbe]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007f7b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f7b0
[    0.000000] On node 0 totalpages: 522063
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 290210 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517473
[    0.000000] Kernel command line: root=UUID=338cb035-bb13-41f6-8f5a-6f38dbd9064e ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1595.978 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2055244k/2088640k available (2572k kernel code, 32136k reserved, 1160k data, 424k init, 1171136k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.95 BogoMIPS (lpj=6383912)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.020009] ACPI: Core revision 20080609
[    0.027337] ACPI: Checking initramfs for custom DSDT
[    0.876330] ENABLING IO-APIC IRQs
[    0.876565] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.918992] CPU0: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[    0.920031] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3192.02 BogoMIPS (lpj=6384052)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    1.004663] CPU1: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz stepping 0d
[    1.004699] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    1.008071] Brought up 2 CPUs
[    1.008078] Total of 2 processors activated (6383.98 BogoMIPS).
[    1.008118] CPU0 attaching sched-domain:
[    1.008124]  domain 0: span 0-1 level MC
[    1.008131]   groups: 0 1
[    1.008144] CPU1 attaching sched-domain:
[    1.008150]  domain 0: span 0-1 level MC
[    1.008156]   groups: 1 0
[    1.008309] net_namespace: 840 bytes
[    1.008309] Booting paravirtualized kernel on bare hardware
[    1.008619] Time: 17:18:07  Date: 01/10/09
[    1.008678] NET: Registered protocol family 16
[    1.008718] EISA bus registered
[    1.008718] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.008718] ACPI: bus type pci registered
[    1.008718] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    1.008718] PCI: Not using MMCONFIG.
[    1.008718] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    1.008718] PCI: Using configuration type 1 for base access
[    1.018155] ACPI: EC: EC description table is found, configuring boot EC
[    1.016064] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.065749] ACPI: Interpreter enabled
[    1.065758] ACPI: (supports S0 S1 S3 S4 S5)
[    1.065810] ACPI: Using IOAPIC for interrupt routing
[    1.066177] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    1.076180] PCI: MCFG area at c0000000 reserved in ACPI motherboard resources
[    1.076186] PCI: Using MMCONFIG for extended config space
[    1.100608] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    1.100615] ACPI: EC: driver started in interrupt mode
[    1.100735] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.100735] PCI: 0000:00:02.0 reg 10 64bit mmio: [feb00000, febfffff]
[    1.100735] PCI: 0000:00:02.0 reg 18 32bit mmio: [e0000000, efffffff]
[    1.100735] PCI: 0000:00:02.0 reg 20 io port: [ec00, ec07]
[    1.100735] PCI: 0000:00:02.1 reg 10 64bit mmio: [fe900000, fe9fffff]
[    1.100735] PCI: 0000:00:1a.0 reg 20 io port: [e000, e01f]
[    1.100735] PCI: 0000:00:1a.1 reg 20 io port: [dc00, dc1f]
[    1.104077] PCI: 0000:00:1a.7 reg 10 32bit mmio: [feaff400, feaff7ff]
[    1.104172] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.104184] pci 0000:00:1a.7: PME# disabled
[    1.104263] PCI: 0000:00:1b.0 reg 10 64bit mmio: [feaf8000, feafbfff]
[    1.104352] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.104362] pci 0000:00:1b.0: PME# disabled
[    1.104480] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.104490] pci 0000:00:1c.0: PME# disabled
[    1.104607] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.104618] pci 0000:00:1c.1: PME# disabled
[    1.104735] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.104745] pci 0000:00:1c.2: PME# disabled
[    1.104861] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.104871] pci 0000:00:1c.3: PME# disabled
[    1.104988] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.104998] pci 0000:00:1c.4: PME# disabled
[    1.105080] PCI: 0000:00:1d.0 reg 20 io port: [d880, d89f]
[    1.105186] PCI: 0000:00:1d.1 reg 20 io port: [d800, d81f]
[    1.105291] PCI: 0000:00:1d.2 reg 20 io port: [d480, d49f]
[    1.105405] PCI: 0000:00:1d.7 reg 10 32bit mmio: [feaff000, feaff3ff]
[    1.105500] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.105510] pci 0000:00:1d.7: PME# disabled
[    1.105757] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    1.105767] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    1.105816] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    1.105831] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    1.105846] PCI: 0000:00:1f.1 reg 18 io port: [8f0, 8f7]
[    1.105861] PCI: 0000:00:1f.1 reg 1c io port: [8f8, 8fb]
[    1.105876] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
[    1.106000] PCI: 0000:00:1f.2 reg 10 io port: [e880, e887]
[    1.106015] PCI: 0000:00:1f.2 reg 14 io port: [e800, e803]
[    1.106029] PCI: 0000:00:1f.2 reg 18 io port: [e480, e487]
[    1.106045] PCI: 0000:00:1f.2 reg 1c io port: [e400, e403]
[    1.106059] PCI: 0000:00:1f.2 reg 20 io port: [e080, e09f]
[    1.106074] PCI: 0000:00:1f.2 reg 24 32bit mmio: [feaff800, feafffff]
[    1.106129] pci 0000:00:1f.2: PME# supported from D3hot
[    1.106139] pci 0000:00:1f.2: PME# disabled
[    1.106478] PCI: 0000:02:00.0 reg 10 32bit mmio: [fdcff000, fdcfffff]
[    1.106725] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.106743] pci 0000:02:00.0: PME# disabled
[    1.106835] PCI: bridge 0000:00:1c.1 32bit mmio: [fdc00000, fdcfffff]
[    1.107015] PCI: 0000:03:00.0 reg 10 64bit mmio: [fddf0000, fddfffff]
[    1.107117] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    1.107129] pci 0000:03:00.0: PME# disabled
[    1.107221] PCI: bridge 0000:00:1c.2 32bit mmio: [fdd00000, fddfffff]
[    1.107445] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    1.107455] PCI: bridge 0000:00:1c.4 32bit mmio: [fde00000, fe5fffff]
[    1.107471] PCI: bridge 0000:00:1c.4 64bit mmio pref: [dbb00000, ddafffff]
[    1.107552] PCI: 0000:07:03.0 reg 10 32bit mmio: [fe6ff800, fe6fffff]
[    1.107641] pci 0000:07:03.0: PME# supported from D0 D3hot D3cold
[    1.107651] pci 0000:07:03.0: PME# disabled
[    1.107713] PCI: 0000:07:03.1 reg 10 32bit mmio: [fe6ff400, fe6ff4ff]
[    1.107802] pci 0000:07:03.1: supports D1
[    1.107806] pci 0000:07:03.1: supports D2
[    1.107811] pci 0000:07:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.107821] pci 0000:07:03.1: PME# disabled
[    1.107881] PCI: 0000:07:03.2 reg 10 32bit mmio: [fe6ff000, fe6ff0ff]
[    1.107971] pci 0000:07:03.2: supports D1
[    1.107976] pci 0000:07:03.2: supports D2
[    1.107980] pci 0000:07:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.107990] pci 0000:07:03.2: PME# disabled
[    1.108064] PCI: 0000:07:03.3 reg 10 32bit mmio: [fe6fec00, fe6fecff]
[    1.108154] pci 0000:07:03.3: supports D1
[    1.108158] pci 0000:07:03.3: supports D2
[    1.108163] pci 0000:07:03.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.108173] pci 0000:07:03.3: PME# disabled
[    1.108233] PCI: 0000:07:03.4 reg 10 32bit mmio: [fe6fe800, fe6fe8ff]
[    1.108322] pci 0000:07:03.4: supports D1
[    1.108326] pci 0000:07:03.4: supports D2
[    1.108331] pci 0000:07:03.4: PME# supported from D0 D1 D2 D3hot D3cold
[    1.108341] pci 0000:07:03.4: PME# disabled
[    1.108432] pci 0000:00:1e.0: transparent bridge
[    1.108447] PCI: bridge 0000:00:1e.0 32bit mmio: [fe600000, fe6fffff]
[    1.108524] bus 00 -> node 0
[    1.108547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.109352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.109775] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.110215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.110645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.111064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.111535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    1.128717] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    1.129056] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    1.129594] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    1.132482] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    1.133021] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[    1.133550] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    1.134088] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    1.134627] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    1.141001] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - 19, should be 59 [20080609]
[    1.141031] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.141061] pnp: PnP ACPI init
[    1.141061] ACPI: bus type pnp registered
[    1.149490] pnp: PnP ACPI: found 13 devices
[    1.149496] ACPI: ACPI bus type pnp unregistered
[    1.149504] PnPBIOS: Disabled by ACPI PNP
[    1.149544] PCI: Using ACPI for IRQ routing
[    1.156052] NET: Registered protocol family 8
[    1.156059] NET: Registered protocol family 20
[    1.156097] NetLabel: Initializing
[    1.156097] NetLabel:  domain hash size = 128
[    1.156097] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.156112] NetLabel:  unlabeled traffic allowed by default
[    1.156126] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.156139] hpet0: 3 64-bit timers, 14318180 Hz
[    1.158318] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.158326]    actual entries 65620
[    1.158506] AppArmor: AppArmor Filesystem Enabled
[    1.158547] ACPI: RTC can wake from S4
[    1.160047] Switched to high resolution mode on CPU 0
[    1.160732] Switched to high resolution mode on CPU 1
[    1.164058] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.164089] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.164097] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.164104] system 00:08: ioport range 0x400-0x41f has been reserved
[    1.164111] system 00:08: ioport range 0x500-0x53f has been reserved
[    1.164119] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.164128] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.164135] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    1.164143] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.164151] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.164168] system 00:0a: ioport range 0x250-0x253 has been reserved
[    1.164176] system 00:0a: ioport range 0x256-0x25f has been reserved
[    1.164183] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.164191] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.164206] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[    1.164221] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    1.164228] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    1.164236] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    1.164244] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
[    1.200236] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    1.200243] pci 0000:00:1c.0:   IO window: disabled
[    1.200255] pci 0000:00:1c.0:   MEM window: disabled
[    1.200266] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.200280] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    1.200286] pci 0000:00:1c.1:   IO window: disabled
[    1.200298] pci 0000:00:1c.1:   MEM window: 0xfdc00000-0xfdcfffff
[    1.200308] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.200323] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    1.200328] pci 0000:00:1c.2:   IO window: disabled
[    1.200340] pci 0000:00:1c.2:   MEM window: 0xfdd00000-0xfddfffff
[    1.200350] pci 0000:00:1c.2:   PREFETCH window: disabled
[    1.200364] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    1.200369] pci 0000:00:1c.3:   IO window: disabled
[    1.200380] pci 0000:00:1c.3:   MEM window: disabled
[    1.200390] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.200404] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
[    1.200412] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    1.200424] pci 0000:00:1c.4:   MEM window: 0xfde00000-0xfe5fffff
[    1.200435] pci 0000:00:1c.4:   PREFETCH window: 0x000000dbb00000-0x000000ddafffff
[    1.200451] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    1.200456] pci 0000:00:1e.0:   IO window: disabled
[    1.200468] pci 0000:00:1e.0:   MEM window: 0xfe600000-0xfe6fffff
[    1.200478] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.200512] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.200524] pci 0000:00:1c.0: setting latency timer to 64
[    1.200544] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.200554] pci 0000:00:1c.1: setting latency timer to 64
[    1.200574] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.200584] pci 0000:00:1c.2: setting latency timer to 64
[    1.200603] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.200614] pci 0000:00:1c.3: setting latency timer to 64
[    1.200631] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.200641] pci 0000:00:1c.4: setting latency timer to 64
[    1.200658] pci 0000:00:1e.0: setting latency timer to 64
[    1.200667] bus: 00 index 0 io port: [0, ffff]
[    1.200672] bus: 00 index 1 mmio: [0, ffffffff]
[    1.200677] bus: 01 index 0 mmio: [0, 0]
[    1.200681] bus: 01 index 1 mmio: [0, 0]
[    1.200686] bus: 01 index 2 mmio: [0, 0]
[    1.200691] bus: 01 index 3 mmio: [0, 0]
[    1.200696] bus: 02 index 0 mmio: [0, 0]
[    1.200701] bus: 02 index 1 mmio: [fdc00000, fdcfffff]
[    1.200706] bus: 02 index 2 mmio: [0, 0]
[    1.200711] bus: 02 index 3 mmio: [0, 0]
[    1.200716] bus: 03 index 0 mmio: [0, 0]
[    1.200721] bus: 03 index 1 mmio: [fdd00000, fddfffff]
[    1.200726] bus: 03 index 2 mmio: [0, 0]
[    1.200730] bus: 03 index 3 mmio: [0, 0]
[    1.200735] bus: 04 index 0 mmio: [0, 0]
[    1.200740] bus: 04 index 1 mmio: [0, 0]
[    1.200744] bus: 04 index 2 mmio: [0, 0]
[    1.200749] bus: 04 index 3 mmio: [0, 0]
[    1.200754] bus: 05 index 0 io port: [c000, cfff]
[    1.200759] bus: 05 index 1 mmio: [fde00000, fe5fffff]
[    1.200765] bus: 05 index 2 mmio: [dbb00000, ddafffff]
[    1.200770] bus: 05 index 3 mmio: [0, 0]
[    1.200775] bus: 07 index 0 mmio: [0, 0]
[    1.200780] bus: 07 index 1 mmio: [fe600000, fe6fffff]
[    1.200785] bus: 07 index 2 mmio: [0, 0]
[    1.200790] bus: 07 index 3 io port: [0, ffff]
[    1.200795] bus: 07 index 4 mmio: [0, ffffffff]
[    1.200814] NET: Registered protocol family 2
[    1.212118] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.212647] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.213321] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.213772] TCP: Hash tables configured (established 131072 bind 65536)
[    1.213781] TCP reno registered
[    1.220194] NET: Registered protocol family 1
[    1.220451] checking if image is initramfs... it is
[    2.920617] Freeing initrd memory: 7947k freed
[    2.921208] Simple Boot Flag at 0x52 set to 0x1
[    2.923055] audit: initializing netlink socket (disabled)
[    2.923096] type=2000 audit(1231607887.920:1): initialized
[    2.937714] highmem bounce pool size: 64 pages
[    2.937728] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.943374] VFS: Disk quotas dquot_6.5.1
[    2.943598] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.943848] msgmni has been set to 1743
[    2.944144] io scheduler noop registered
[    2.944152] io scheduler anticipatory registered
[    2.944158] io scheduler deadline registered
[    2.944186] io scheduler cfq registered (default)
[    2.944213] pci 0000:00:02.0: Boot video device
[    3.075969] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.076053] pcieport-driver 0000:00:1c.0: found MSI capability
[    3.076135] pci_express 0000:00:1c.0:pcie00: allocate port service
[    3.076235] pci_express 0000:00:1c.0:pcie02: allocate port service
[    3.076330] pci_express 0000:00:1c.0:pcie03: allocate port service
[    3.076549] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.076630] pcieport-driver 0000:00:1c.1: found MSI capability
[    3.076710] pci_express 0000:00:1c.1:pcie00: allocate port service
[    3.076807] pci_express 0000:00:1c.1:pcie02: allocate port service
[    3.076903] pci_express 0000:00:1c.1:pcie03: allocate port service
[    3.077128] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    3.077209] pcieport-driver 0000:00:1c.2: found MSI capability
[    3.077289] pci_express 0000:00:1c.2:pcie00: allocate port service
[    3.077383] pci_express 0000:00:1c.2:pcie02: allocate port service
[    3.077478] pci_express 0000:00:1c.2:pcie03: allocate port service
[    3.077689] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    3.077770] pcieport-driver 0000:00:1c.3: found MSI capability
[    3.077849] pci_express 0000:00:1c.3:pcie00: allocate port service
[    3.077947] pci_express 0000:00:1c.3:pcie02: allocate port service
[    3.078043] pci_express 0000:00:1c.3:pcie03: allocate port service
[    3.078254] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    3.078335] pcieport-driver 0000:00:1c.4: found MSI capability
[    3.078415] pci_express 0000:00:1c.4:pcie00: allocate port service
[    3.078513] pci_express 0000:00:1c.4:pcie02: allocate port service
[    3.078607] pci_express 0000:00:1c.4:pcie03: allocate port service
[    3.079401] isapnp: Scanning for PnP cards...
[    3.434064] isapnp: No Plug & Play device found
[    3.514839] hpet_resources: 0xfed00000 is busy
[    3.515070] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.520608] brd: module loaded
[    3.520768] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.521082] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.525085] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.526455] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.526468] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.526475] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.526482] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.526488] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.527361] mice: PS/2 mouse device common for all mice
[    3.527682] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.527728] rtc0: alarms up to one month, y3k, hpet irqs
[    3.528058] EISA: Probing bus 0 at eisa.0
[    3.528116] EISA: Detected 0 cards.
[    3.528123] cpuidle: using governor ladder
[    3.528130] cpuidle: using governor menu
[    3.529373] TCP cubic registered
[    3.529428] Using IPI No-Shortcut mode
[    3.529876] registered taskstats version 1
[    3.530179]   Magic number: 9:792:339
[    3.530208] tty ttyze: hash matches
[    3.530328] acpi ACPI0007:01: hash matches
[    3.530386] rtc_cmos 00:03: setting system clock to 2009-01-10 17:18:10 UTC (1231607890)
[    3.530394] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.530399] EDD information not available.
[    3.530764] Freeing unused kernel memory: 424k freed
[    3.530855] Write protecting the kernel text: 2576k
[    3.530920] Write protecting the kernel read-only data: 936k
[    3.569083] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.902159] fuse init (API version 7.9)
[    3.973104] ACPI: SSDT 7F7C83D0, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    3.974605] ACPI: SSDT 7F7C86B0, 0712 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    3.977403] Monitor-Mwait will be used to enter C-1 state
[    3.977411] Monitor-Mwait will be used to enter C-2 state
[    3.977418] Monitor-Mwait will be used to enter C-3 state
[    3.988419] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.988558] processor ACPI0007:00: registered as cooling_device0
[    3.988569] ACPI: Processor [P001] (supports 8 throttling states)
[    3.989398] ACPI: SSDT 7F7C8300, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    3.990811] ACPI: SSDT 7F7C8620, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    3.996023] Marking TSC unstable due to TSC halts in idle
[    4.034302] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    4.034460] processor ACPI0007:01: registered as cooling_device1
[    4.034471] ACPI: Processor [P002] (supports 8 throttling states)
[    4.061330] thermal LNXTHERM:01: registered as thermal_zone0
[    4.063826] ACPI: Thermal Zone [THRM] (35 C)
[    4.389886] usbcore: registered new interface driver usbfs
[    4.389939] usbcore: registered new interface driver hub
[    4.390043] usbcore: registered new device driver usb
[    4.395091] USB Universal Host Controller Interface driver v3.0
[    4.395173] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.395190] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.395198] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.395282] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.395343] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    4.395597] usb usb1: configuration #1 chosen from 1 choice
[    4.395667] hub 1-0:1.0: USB hub found
[    4.395682] hub 1-0:1.0: 2 ports detected
[    4.600441] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.600460] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.600469] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.600527] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    4.600584] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    4.600809] usb usb2: configuration #1 chosen from 1 choice
[    4.600875] hub 2-0:1.0: USB hub found
[    4.600891] hub 2-0:1.0: 2 ports detected
[    4.704501] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.704521] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.704529] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.704596] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.704656] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    4.704870] usb usb3: configuration #1 chosen from 1 choice
[    4.704935] hub 3-0:1.0: USB hub found
[    4.704950] hub 3-0:1.0: 2 ports detected
[    4.712110] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    4.809152] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.809172] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.809181] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.809244] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    4.809303] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    4.809529] usb usb4: configuration #1 chosen from 1 choice
[    4.809594] hub 4-0:1.0: USB hub found
[    4.809610] hub 4-0:1.0: 2 ports detected
[    4.879654] usb 1-1: configuration #1 chosen from 1 choice
[    4.912462] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.912481] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.912489] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.912547] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    4.912604] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    4.912815] usb usb5: configuration #1 chosen from 1 choice
[    4.912879] hub 5-0:1.0: USB hub found
[    4.912894] hub 5-0:1.0: 2 ports detected
[    5.106134] No dock devices found.
[    5.120642] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.120671] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.120679] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.120741] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    5.124665] ehci_hcd 0000:00:1a.7: debug port 1
[    5.124679] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.124695] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaff400
[    5.179944] SCSI subsystem initialized
[    5.223615] libata version 3.00 loaded.
[    5.238407] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    5.248061] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.248330] usb usb6: configuration #1 chosen from 1 choice
[    5.248399] hub 6-0:1.0: USB hub found
[    5.248420] hub 6-0:1.0: 4 ports detected
[    5.415717] usb 5-2: not running at top speed; connect to a high speed hub
[    5.459386] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.459414] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.459423] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.459500] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    5.463443] ehci_hcd 0000:00:1d.7: debug port 1
[    5.463457] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.463475] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaff000
[    5.476075] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.476361] usb usb7: configuration #1 chosen from 1 choice
[    5.476439] hub 7-0:1.0: USB hub found
[    5.476455] hub 7-0:1.0: 6 ports detected
[    5.479559] usb 5-2: unable to read config index 0 descriptor/all
[    5.479570] usb 5-2: can't read configurations, error -71
[    5.536102] hub 5-0:1.0: unable to enumerate USB device on port 2
[    5.536152] usb 1-1: USB disconnect, address 2
[    5.685182] tg3.c:v3.94 (August 14, 2008)
[    5.685250] tg3 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.685269] tg3 0000:03:00.0: setting latency timer to 64
[    5.685673] ahci 0000:00:1f.2: version 3.0
[    5.685701] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    5.685878] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.685887] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    5.685898] ahci 0000:00:1f.2: setting latency timer to 64
[    5.687030] scsi0 : ahci
[    5.687280] scsi1 : ahci
[    5.687449] scsi2 : ahci
[    5.687812] ata1: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 218
[    5.687820] ata2: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 218
[    5.687828] ata3: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaffa00 irq 218
[    5.776130] usb 6-1: new high speed USB device using ehci_hcd and address 2
[    5.910615] usb 6-1: configuration #1 chosen from 1 choice
[    6.004099] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.006712] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.006949] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.006957] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.008402] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    6.008410] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.011225] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    6.011462] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    6.011470] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.012469] ata1.00: configured for UDMA/133
[    6.020076] usb 7-6: new high speed USB device using ehci_hcd and address 2
[    6.221624] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1e:8c:c1:2b:c8
[    6.221635] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    6.221642] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    6.221735] ohci1394 0000:07:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.274558] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fe6ff800-fe6fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.348092] ata2: SATA link down (SStatus 0 SControl 300)
[    6.457423] usb 7-6: configuration #1 chosen from 1 choice
[    6.498203] usbcore: registered new interface driver libusual
[    6.523723] Initializing USB Mass Storage driver...
[    6.523936] scsi3 : SCSI emulation for USB Mass Storage devices
[    6.537150] usbcore: registered new interface driver usb-storage
[    6.537160] USB Mass Storage support registered.
[    6.537834] usb-storage: device found at 2
[    6.537839] usb-storage: waiting for device to settle before scanning
[    6.684152] ata3: SATA link down (SStatus 0 SControl 300)
[    6.700369] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    6.700680] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.700797] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.700856] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    6.700885] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    6.709640] ata_piix 0000:00:1f.1: version 2.12
[    6.709663] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.709747] ata_piix 0000:00:1f.1: setting latency timer to 64
[    6.713434] scsi4 : ata_piix
[    6.713888] scsi5 : ata_piix
[    6.715791] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.715800] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.752465] Driver 'sd' needs updating - please use bus_type methods
[    6.752691] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.752740] sd 0:0:0:0: [sda] Write Protect is off
[    6.752746] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.752829] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.753027] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.753076] sd 0:0:0:0: [sda] Write Protect is off
[    6.753082] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.753163] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.753172]  sda:<6>ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, EV02, max UDMA/33
[    6.892535] ata4.00: configured for UDMA/33
[    6.892670] ata5: port disabled. ignoring.
[    6.896345] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  EV02 PQ: 0 ANSI: 5
[    6.896984] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    6.940960] Driver 'sr' needs updating - please use bus_type methods
[    7.001104] Clocksource tsc unstable (delta = -323309190 ns)
[    7.135518]  sda1 sda2 sda3 sda4
[    7.153990] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.178537] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.178548] Uniform CD-ROM driver Revision: 3.20
[    7.178774] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.553567] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000103b8cc]
[    7.591726] PM: Starting manual resume from disk
[    7.591736] PM: Resume from partition 8:4
[    7.591741] PM: Checking hibernation image.
[    7.592017] PM: Resume from disk failed.
[    7.651843] kjournald starting.  Commit interval 5 seconds
[    7.651872] EXT3-fs: mounted filesystem with ordered data mode.
[   11.536506] usb-storage: device scan complete
[   11.537143] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   11.537734] scsi 3:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   11.539349] sd 3:0:0:0: [sdb] 3999377 512-byte hardware sectors (2048 MB)
[   11.539970] sd 3:0:0:0: [sdb] Write Protect is off
[   11.539978] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   11.539984] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   11.542073] sd 3:0:0:0: [sdb] 3999377 512-byte hardware sectors (2048 MB)
[   11.542696] sd 3:0:0:0: [sdb] Write Protect is off
[   11.542702] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   11.542708] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   11.542718]  sdb: sdb1
[   11.544470] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   11.544654] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   11.547323] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   11.547483] sr 3:0:0:1: Attached scsi CD-ROM sr1
[   11.547630] sr 3:0:0:1: Attached scsi generic sg3 type 5
[   17.947955] udevd version 124 started
[   18.741637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.801298] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.908659] Linux agpgart interface v0.103
[   19.035355] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   19.036012] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   19.057887] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   19.375724] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.401062] ACPI: Power Button (FF) [PWRF]
[   19.401426] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   19.417055] ACPI: Sleep Button (CM) [SLPB]
[   19.417271] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   19.420028] ACPI: Lid Switch [LID]
[   19.544682] asus-laptop: Asus Laptop Support version 0.42
[   19.552251] asus-laptop: BSTS called, 0xc8c8 returned
[   19.552426] asus-laptop:   SPEEDY model detected
[   20.068622] ACPI: AC Adapter [AC0] (off-line)
[   20.213386] ACPI: Battery Slot [BAT0] (battery present)
[   20.263941] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   20.263950] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   20.264110] iwl3945 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.264131] iwl3945 0000:02:00.0: setting latency timer to 64
[   20.264162] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   20.517114] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.534208] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.590126] acpi device:07: registered as cooling_device2
[   20.590599] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[   20.617067] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.617166] proc_dir_entry 'video/VGA' already registered
[   20.617175] Pid: 2793, comm: modprobe Not tainted 2.6.27-9-generic #1
[   20.617182]  [<c037c4b6>] ? printk+0x1d/0x1f
[   20.617199]  [<c01f3eb2>] proc_register+0x1a2/0x1d0
[   20.617210]  [<c01f40c8>] proc_mkdir_mode+0x38/0x50
[   20.617219]  [<c01f40f4>] proc_mkdir+0x14/0x20
[   20.617228]  [<f8c0bd04>] acpi_video_bus_add_fs+0x29/0x163 [video]
[   20.617255]  [<f8c0cda6>] acpi_video_bus_add+0xd2/0x298 [video]
[   20.617268]  [<c0290a06>] acpi_device_probe+0x47/0x89
[   20.617280]  [<c02c3cb9>] really_probe+0x59/0x190
[   20.617289]  [<c028fd65>] ? acpi_match_device_ids+0x51/0x75
[   20.617302]  [<c02c3e33>] driver_probe_device+0x43/0x60
[   20.617310]  [<c02c3ec9>] __driver_attach+0x79/0x80
[   20.617320]  [<c02c3593>] bus_for_each_dev+0x53/0x80
[   20.617329]  [<c0290958>] ? acpi_device_remove+0x0/0x67
[   20.617339]  [<c02c3b6e>] driver_attach+0x1e/0x20
[   20.617347]  [<c02c3e50>] ? __driver_attach+0x0/0x80
[   20.617357]  [<c02c2f37>] bus_add_driver+0x1b7/0x230
[   20.617366]  [<c0290958>] ? acpi_device_remove+0x0/0x67
[   20.617375]  [<c02c409e>] driver_register+0x6e/0x150
[   20.617384]  [<f8860000>] ? acpi_video_init+0x0/0x56 [video]
[   20.617397]  [<c01f40c8>] ? proc_mkdir_mode+0x38/0x50
[   20.617407]  [<f8860000>] ? acpi_video_init+0x0/0x56 [video]
[   20.617418]  [<c0290cfe>] acpi_bus_register_driver+0x3f/0x41
[   20.617427]  [<f8860037>] acpi_video_init+0x37/0x56 [video]
[   20.617436]  [<c0101120>] _stext+0x30/0x160
[   20.617444]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[   20.617458]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[   20.617472]  [<c015c208>] sys_init_module+0x88/0x1b0
[   20.617482]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[   20.617492]  =======================
[   20.622811] acpi device:22: registered as cooling_device3
[   20.623279] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/input/input6
[   20.649066] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.792640] iwl3945 0000:02:00.0: PCI INT A disabled
[   21.418738] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.418791] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.450968] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   21.469313] iTCO_vendor_support: vendor-support=0
[   21.493555] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   21.493823] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
[   21.494043] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.552872] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   21.737804] ricoh-mmc: Ricoh MMC Controller disabling driver
[   21.737811] ricoh-mmc: Copyright(c) Philip Langdale
[   21.737888] ricoh-mmc: Ricoh MMC controller found at 0000:07:03.2 [1180:0843] (rev 12)
[   21.737931] ricoh-mmc: Controller is now disabled.
[   21.839008] sdhci: Secure Digital Host Controller Interface driver
[   21.839016] sdhci: Copyright(c) Pierre Ossman
[   21.875461] sdhci-pci 0000:07:03.1: SDHCI controller found [1180:0822] (rev 22)
[   21.875492] sdhci-pci 0000:07:03.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   21.876522] sdhci-pci 0000:07:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.878668] mmc0: SDHCI controller on PCI [0000:07:03.1] using DMA
[   22.641083] Linux video capture interface: v2.00
[   22.733494] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa580b1, caps: 0xa04713/0x200000
[   22.774515] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   22.819055] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   23.817186] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
[   23.817197] uvcvideo: Failed to initialize the device (-5).
[   23.817371] usbcore: registered new interface driver uvcvideo
[   23.817379] USB Video Class driver (v0.1.0)
[   24.131983] udev: renamed network interface wlan0 to eth1
[   25.680984] lp: driver loaded but no devices found
[   26.160601] Adding 4000176k swap on /dev/sda4.  Priority:-1 extents:1 across:4000176k
[   26.207323] EXT3 FS on sda3, internal journal
[   27.433513] type=1505 audit(1231625914.010:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4365
[   27.844581] type=1505 audit(1231625914.418:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4370
[   27.844977] type=1505 audit(1231625914.418:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4370
[   28.106560] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.361743] ACPI: WMI: Mapper loaded
[   30.850684] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   31.128110] NET: Registered protocol family 10
[   31.130150] lo: Disabled Privacy Extensions
[   31.676302] apm: BIOS not found.
[   31.867647] ppdev: user-space parallel port driver
[   32.396554] type=1503 audit(1231625918.974:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/etc/krb5.conf.debathena" pid=5189 profile="/usr/sbin/cupsd"
[   35.395033] Bluetooth: Core ver 2.13
[   35.396562] NET: Registered protocol family 31
[   35.396575] Bluetooth: HCI device and connection manager initialized
[   35.396582] Bluetooth: HCI socket layer initialized
[   35.452414] Bluetooth: L2CAP ver 2.11
[   35.452428] Bluetooth: L2CAP socket layer initialized
[   35.489257] Bluetooth: SCO (Voice Link) ver 0.6
[   35.489274] Bluetooth: SCO socket layer initialized
[   35.529923] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.529939] Bluetooth: BNEP filters: protocol multicast
[   35.588689] Bluetooth: RFCOMM socket layer initialized
[   35.588719] Bluetooth: RFCOMM TTY layer initialized
[   35.588725] Bluetooth: RFCOMM ver 1.10
[   35.607281] Bridge firewalling registered
[   35.609098] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   35.876338] openafs: module license 'http://www.openafs.org/dl/license10.html' taints kernel.
[   35.972747] Starting AFS cache scan...found 843 non-empty cache files (10%).
[   40.858113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.877229] iwl3945 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   40.877402] iwl3945 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   40.878498] firmware: requesting iwlwifi-3945-1.ucode
[   40.879504] [drm] Initialized drm 1.1.0 20060810
[   40.887057] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   40.887075] pci 0000:00:02.0: setting latency timer to 64
[   40.887309] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.036776] Registered led device: iwl-phy0:radio
[   41.037868] Registered led device: iwl-phy0:assoc
[   41.038870] Registered led device: iwl-phy0:RX
[   41.039829] Registered led device: iwl-phy0:TX
[   41.054227] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   41.100887] NET: Registered protocol family 17
[   43.900704] eth1: authenticate with AP 00:30:ab:29:11:6d
[   43.902557] eth1: authenticated
[   43.902572] eth1: associate with AP 00:30:ab:29:11:6d
[   43.910890] eth1: RX AssocResp from 00:30:ab:29:11:6d (capab=0x421 status=0 aid=2)
[   43.910906] eth1: associated
[   43.912645] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   43.918283] eth1: disassociating by local choice (reason=3)
[   54.464101] eth1: no IPv6 routers present
[   66.262173] eth1: deauthenticated
[   66.262824] eth1: authenticate with AP 00:30:ab:29:11:6d
[   66.266281] eth1: authenticated
[   66.266304] eth1: associate with AP 00:30:ab:29:11:6d
[   66.272293] eth1: RX ReassocResp from 00:30:ab:29:11:6d (capab=0x421 status=0 aid=2)
[   66.272309] eth1: associated
[   66.274818] eth1: disassociating by local choice (reason=3)
[   88.341151] CPU0 attaching NULL sched-domain.
[   88.341171] CPU1 attaching NULL sched-domain.
[   88.344205] CPU0 attaching sched-domain:
[   88.344215]  domain 0: span 0-1 level MC
[   88.344222]   groups: 0 1
[   88.344234]   domain 1: span 0-1 level CPU
[   88.344240]    groups: 0-1
[   88.344251] CPU1 attaching sched-domain:
[   88.344256]  domain 0: span 0-1 level MC
[   88.344262]   groups: 1 0
[   88.344271]   domain 1: span 0-1 level CPU
[   88.344278]    groups: 0-1
[   96.166053] eth1: deauthenticated
[   96.166916] eth1: authenticate with AP 00:30:ab:29:11:6d
[   96.169350] eth1: authenticated
[   96.169370] eth1: associate with AP 00:30:ab:29:11:6d
[   96.174233] eth1: RX ReassocResp from 00:30:ab:29:11:6d (capab=0x421 status=0 aid=2)
[   96.174244] eth1: associated
[   96.174928] eth1: disassociating by local choice (reason=3)
[  128.691982] eth1: authenticate with AP 00:30:ab:29:11:6d
[  128.693721] eth1: authenticated
[  128.693734] eth1: associate with AP 00:30:ab:29:11:6d
[  128.696547] eth1: RX AssocResp from 00:30:ab:29:11:6d (capab=0x421 status=0 aid=2)
[  128.696558] eth1: associated
[  128.697611] eth1: disassociating by local choice (reason=3)
[  136.303854] eth1: deauthenticated
[  136.310667] eth1: authenticate with AP 00:23:12:f8:b8:57
[  136.314070] eth1: authenticate with AP 00:23:12:f8:b8:57
[  136.315962] eth1: authenticated
[  136.315979] eth1: associate with AP 00:23:12:f8:b8:57
[  136.322489] eth1: RX AssocResp from 00:23:12:f8:b8:57 (capab=0x431 status=0 aid=1)
[  136.322503] eth1: associated
[  136.516017] padlock: VIA PadLock not detected.

```

---

### Post by wyth on 2009-01-11
Anybody notice that after the last couple kernel updates, the backlight fix doesn't work anymore?

---

### Post by HunterThomson on 2009-01-12
> **wyth said:**
> Anybody notice that after the last couple kernel updates, the backlight fix doesn't work anymore?


My backlight is still good. Though I would like it if there is a way to have the DSDT tell the ACPI kernel module that it can give the backlight more power.

I am reinstalling the ALSA stuff because is is starting muted for me now.

Edit- I reinstalled ALSA stuff and still (Master at 81%, Front 81%, CD 81%, The rest are un-muted but vol all the way down on boot)

---

### Post by wyth on 2009-01-12
Huh.  I can't change my backlight settings anymore.  Wonder where that came from.

---

### Post by HunterThomson on 2009-01-14
> **wyth said:**
> Huh.  I can't change my backlight settings anymore.  Wonder where that came from.

Well, just to bubble check.. do you still have the file DSDT.aml in /etc/initramfs-tools/  ?? 

I don't think that helped you but hay sometimes I forget little things like that. 

Other then that.... There should be no reason your back-light should have stopped working.

---

### Post by wyth on 2009-01-14
Yep, the DSDT.aml file is in the right place.  I *think* this occurred somewhere amongst a slew of recent kernel updates.  I have a backlight, I just can't change the settings (via keyboard or panel app). 

I *can* change the backlight with the Fn-arrow keys as it's booting up (before I get to the login screen).  So when I'm in, say, a class lecture, I can turn it on and make it dim before I get to the desktop, and keep my battery all class.  If I don't, however, I'm taking my chances.

---

### Post by HunterThomson on 2009-01-14
> **wyth said:**
> Yep, the DSDT.aml file is in the right place.  I *think* this occurred somewhere amongst a slew of recent kernel updates.  I have a backlight, I just can't change the settings (via keyboard or panel app). 

I *can* change the backlight with the Fn-arrow keys as it's booting up (before I get to the login screen).  So when I'm in, say, a class lecture, I can turn it on and make it dim before I get to the desktop, and keep my battery all class.  If I don't, however, I'm taking my chances.


Hey, I have was on the forums last night and it seems a whole bunch of laptops backlights stopped working. All there backlight adjustment keys and even the backlight applet will not work. I saw someones update log and there on kernel 2.6.27-11. I am still on 2.6.27-9. 

To day there is one update.... It is "acpi-support" ... Hum... I don't think I am going to do that one. If someone already has let us know if it is messing things up.

---

### Post by nmfralich on 2009-01-15
So I'm seeing that this webcam issue has been going on for multiple years now.  I've just gone through the entirety of this post and found no solution.  As far as mine is concerned, it does not show up in skype or cheese and a printout of dmesg gives the following:

[   26.140833] Linux video capture interface: v2.00
[   26.369165] uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
[   26.630605] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   27.365244] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
[   27.365254] uvcvideo: Failed to initialize the device (-5).
[   27.365315] usbcore: registered new interface driver uvcvideo


It would be wonderful if someone might have any new insight into this problem and I would greatly appreciate any help!

---

### Post by wyth on 2009-01-15
So I accepted today's updates, including the acpi-support update, and all the backlight issues are cleared up.  I never even tried the previous kernel, and was about to restart and try it when I got the updates.

As far as the camera goes, yeah, that's just an ongoing problem.  I did get it to work a while back, but never well.  There is a thread somewhere out there that explains how to get a camera working on a macbook, and the process is basically the same.  In my case, the image was never very good -- very degraded, so it looked *cool* in a way, but was never *good,* and it was always upside-down (easily fixed in Cheese).  Since I only ever used the camera twice to hold my beagle up to it and test the video record, I never really thought about it again.  It's one of those things I never think about except to check on when a new version comes out.

---

### Post by chargersfan420 on 2009-01-30
Hey guys, long time no post.

Good to see that you Y510 users solved your brightness problem.  I never really had a problem with brightness, but i noticed one lately.

I was running on battery power, and i needed all the time i could get out of it, so i did a few things to help preserve battery power.  I turned the brightness all the way down, i turned off the wireless and bass switches on the front of the unit, and i turned off virtualbox.

I noticed that after a minute of sitting idle, the screen usually would dim to a lower brightness setting, but on the lowest setting, it can't do this... however, after moving the mouse, it jumps back to a medium brightness setting, causing me to have to turn it all the way down again.

Does anyone else have this problem too?  I'm not too concerned about fixing it, since the situation is pretty rare...

Also, was anyone looking for a copy of the DSDT from the Y710?

What also has me a bit upset is the Y710 is discontinued... I don't think the Y510 is yet, but it probably will be soon.  The Yx30 line is beginning to take over, and the Yx50 line is coming soon.

What really pisses me off about Lenovo is that here in Canada, they only sell ONE model with a 17" screen and a number pad, and it is the ThinkPad W700... but at $5000, you'd really have to want one.  Damn you Lenovo for making the Y730 but not selling it in Canada!

---

### Post by chrismulderza on 2009-02-02
Hey all, been a while since I posted here, my Y510 dev work has been put on hold due to work... (not all bad, been fiddling with OpenSolaris on the Y510 a bit ... quite impressive ... :D )

@chargersfan420

That behavior you described in your post is gnome-power manager trying to conserver batter power, by dimming the backlight, and then restoring it when the session is not idle. 

You can tweak the settings by editing the gnome-power-manager gconf registry keys

From a terminal type
```
gconf-editor
```

Then expand "apps" 
Scroll down to "gnome-power-manager"
Expand the "gnome-power-manager" node
Click on "backlight"
You can tweak the behavior from here.
Most likely you'd want to untick "idle_dim_battery"

Hope this helps somewhat.

Cheers folks!

---

### Post by eipxen on 2009-02-13
I believe my friend has one of these (looks just like it, seems to fit the time she bought it) and she put ubuntu on it after a windows infection necessitated a reformat.  Her computer will get very hot and shut itself off, but will remain silent, so it seems most likely that her fans are simply not working, or at least not hard enough.  Can anyone help me?  Thanks!

---

### Post by winnibob on 2009-02-13
> **eipxen said:**
> Her computer will get very hot and shut itself off, but will remain silent, so it seems most likely that her fans are simply not working, or at least not hard enough.  Can anyone help me?  Thanks!

Perhaps you should try what is explained on [this topic]("http://ubuntuforums.org/showthread.php?t=786402"). It helped me reducing the temp of my cpu from 70 to 50°C.

---

### Post by morphgt on 2009-02-13
it works :guitar: 
lenovo y530 :P

---

### Post by wyth on 2009-02-13
> **morphgt said:**
> it works :guitar: 
lenovo y530 :P

What works?

---

### Post by GoogleGuy on 2009-02-15
Hey guys, just bought a Y510-KA and found this thread. Great info al around.

I didn't read all the way through yet, so I'm sorry if this info already came up... But here's something new, hopefully...

Regarding brightness:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301524)
[https://bugzilla.redhat.com/show_bug.cgi?id=470465](https://bugzilla.redhat.com/show_bug.cgi?id=470465)

Here's a patch (haven't tried yet):
[https://bugzilla.redhat.com/attachment.cgi?id=323670](https://bugzilla.redhat.com/attachment.cgi?id=323670)


Regarding flipped UVC camera:

1. [http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) + 4 different patches

2. [http://ubuntuforums.org/showthread.php?t=561433&page=2](http://ubuntuforums.org/showthread.php?t=561433&page=2) (someone suggests trying "echo 1 >/sys/class/video4linux/video0/vflip", can'ttry it right now, posting from a different machine)

Hope this helps someone.

---

### Post by wyth on 2009-02-17
Some of you may have a problem with a hot machine that's always ramping up the fan.  Here's something I recently came across that will drop the running temp of your machine by possibly 10 degrees Celsius. 

You need to add the following modules into /etc/modules.  You can do this at the command line or in your favorite text editor, but be sure to do it as root. Add the following to the bottom of the list of modules that are already there (see the proviso at the bottom of the post):[INDENT] battery
ac
thermal
processor
acpi-cpufeq
cpufreq-userspace
p4_clockmod
[/INDENT]The next time you start your machine, these modules will be loaded at boot, and they go a looooong way to controlling the possible thrashing your machine may undergo.  

I was consistently at around 61 degrees and the fan was almost always on.  I was looking into undervolting the machine, but that never worked.  When I added these modules, even with 31 tabs open in Firefox (I'm researching/writing), I'm resting comfortably at around 47 degrees Celsius, and even when it jumps up after some heavy multimedia use, it drops fairly quickly.

For those who want a little more fine-tuned control over their CPU, you can add the CPU Frequency Scaling Monitor and a few other things to help you monitor your specs via applets (little apps that run in a panel).
```
sudo apt-get install hddtem lm-sensors sensors-applet computertemp
```This installs the necessary applets to start checking things out.  

[LIST]
[*]**Computer Temperature Monitor**: Gives you the temp of the CPU and disks
[*]**Sensors Applet**: Like the above, but a little more detailed (it gives me my GPU temp on my desktop machine)
[*]**CPU Frequency Scaling Monitor**: Allows you to change the frequency of your CPU's.  I've added that twice and monitor both cores at once, just for tests.
[/LIST]
However, you need to do one more step to enable the CPU Frequency Scaling Monitor's full range power:
```
sudo dpkg-reconfigure gnome-applets
```This will bring up an ncurses dialog asking if you want to install the frequency monitor with the SUID set.  Choose OK, and when it asks "Install cpufreq-selector with SUID root?" choose "Yes."  (You'll need logout and log back in to get it running with the options.)

Now, if you want to change the frequency of the CPU to make it run at a higher or lower frequency (depending on what kind of power you want/need), you can change that through the CPU Frequency Scaling Monitor applet to the panel.  You can either choose governors or a set frequency.  Ondemand seems like a good choice -- it increases and lowers the frequency as needed.  Performance is obvious, Powersave is obvious, and I'm not quite clear on the difference between Ondemand and Conservative; I think Conservative does about the same thing, but slower.  

[B]_PROVISO_
[/B]I'm not completely clear on the p4_clockmod module.  I searched for quite a while and came up black with good info.  Lots of people recommend it, but I don't know if it is necessary or conflicts with anything or even loads if it isn't necessary.  It does something other than managing the frequency; as I understand it, it manages the rate that frequency changes, no the frequency itself.  If someone else knows, please post.

---

### Post by wyth on 2009-02-17
> **GoogleGuy said:**
> Hey guys, just bought a Y510-KA and found this thread. Great info al around.

I didn't read all the way through yet, so I'm sorry if this info already came up... But here's something new, hopefully...

Regarding brightness:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301524)
[https://bugzilla.redhat.com/show_bug.cgi?id=470465](https://bugzilla.redhat.com/show_bug.cgi?id=470465)

Here's a patch (haven't tried yet):
[https://bugzilla.redhat.com/attachment.cgi?id=323670](https://bugzilla.redhat.com/attachment.cgi?id=323670)


Regarding flipped UVC camera:

1. [http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) + 4 different patches

2. [http://ubuntuforums.org/showthread.php?t=561433&page=2](http://ubuntuforums.org/showthread.php?t=561433&page=2) (someone suggests trying "echo 1 >/sys/class/video4linux/video0/vflip", can'ttry it right now, posting from a different machine)

Hope this helps someone.

Heya,

I think the brightness issue has been fixed -- it's not an issue for me, anyway.  As for the camera, mine works via two steps:

[LIST]
[*]Add uvcvideo to /etc/modules (need to edit the /etc/modules file as root)
[*]In Cheese under Effects, just choose the flip effect.
[/LIST]

---

### Post by GoogleGuy on 2009-02-20
Hi Wyth,

you're right, brightness has been fixed in 2.6.28+ kernels.

Camera is still flipped, yeah you can flip it back in Cheese, but what about Skype?

Also, does any of you guys got the Infra Red controller to work? If so, which module do I need?

Thanks.

---

### Post by talktorishav on 2009-02-21
I am using Jaunty Jacalope Alpha version and Yes the brightness issue is fixed.

2.6.28-8

[techspalace.blogspot.com]("techspalace.blogspot.com")

---

### Post by ruivilela on 2009-02-24
Hi
I have a Linux Gentoo 2.6.27 in a Lenovo Ideapad Y530.

Some issues that i have after reading this topic.

1. ALSA seems resolved for next Kernel. or 2.6.29.

2. Orange keys work and don't work. In Ubuntu 8.10 LiveCD they work without glitches. 

Most of the time that keys don't work. Sometimes work after tap them a lot of times. They work 'perfectly' after a few minutes without using laptop (...)

I see sometimes this in dmesg (random appearance) when i try to use them... not always the same output...
```

CE: hpet increasing min_delta_ns to 15000 nsec
CE: hpet increasing min_delta_ns to 22500 nsec
CE: hpet increasing min_delta_ns to 33750 nsec
CE: hpet increasing min_delta_ns to 50624 nsec

```
This PLAY orange keys produce the same code as the FN+(F9..F12) keys (this works). And they respond when i use the '#showkey' command. But in 'xev' not really or sometimes. Anyway I have them mapped in .Xmodmap and later configured in Xfce4 shortcuts to control 'exaile'. Anyway why they work well in Ubuntu? What kernel config needs?

3. I can not play AUDIO CD. I use dcd for this, and also cdplay. And they don't work in this laptop. I can read/record cdr. I can extract audio CD tracks using cdparanoia. Some one has this problem. It gives a lot IO errors from kernel. It works in Windoze

lshw:
```

*-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: S801
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc


```

4. I have problem with brightness. This keys have the same problem as the orange soft keys. But they always work, Fn+up give always second lowest bright and Fn+down gives always the lowest bright. Solution? Kernel 2.6.29-rc5 does not solve the problem.


Regards
Rui

---

### Post by mylh on 2009-02-24
I also have Y530 and currently don't know hot to makw its mirophones work properly though sound in general works ok... any suggesions?
Thanks.

---

### Post by ruivilela on 2009-02-24
I usually open alsamixer in a shell. Depends which model you configured anyway. 

alsamixer in shell/terminal (in Gnome maybe you also have similar mixer)

Make sure that in playback mode, your mic and front mic are mutted (press M to change state to Mute 'MM').

press tab to go to capture mode. If you want to test your integrated micro:

Change input source to "front mic" (up key)
Capture only from input source (space and raise volume)
If you want raise volume of front mic boost.

Try your favorite recorder.

---

### Post by mylh on 2009-02-24
Thanks! I managed to record sound in audacity with default settings after selected front mic as input source and make front mic boost to max level.

And in skype you have to select HDA Intel (hw:Intel,0) as sound in.

---

### Post by ruivilela on 2009-02-24
I use default settings and they work, I advise you to not let skype to change your mic volume, or at least try first.

---

### Post by GoogleGuy on 2009-02-27
**Here's how to -- finally! -- solve Video Camera being upside down.**

...or at least how I did it 5 minutes ago.

1. Get code from an earlier version of uvcvideo git, already patched:

# mkdir ~/src
# cd ~/src
# git clone git://github.com/dfu/linux-uvc_flip.git

you'll now have a local git repo called "linux-uvc_flip".

2. cd to this dir and type "make" to compile. If it complains about "too many arguments in some function... blah-blah", do this:

(a) find the file called uvc_v4l2.c in the git repo you just created.
(b) replace these 2 lines:

```
if ((ret = v4l_compat_translate_ioctl(inode, file, cmd, arg,
uvc_v4l2_do_ioctl)) == -ENOIOCTLCMD)
```

with this (I made it one line, doesn't matter):

```
if ((ret = v4l_compat_translate_ioctl(file, cmd, arg, uvc_v4l2_do_ioctl)) == -ENOIOCTLCMD)
```

3. type "make" to compile, and it'll compile fine.

4. backup your current driver by finding the file called "uvcvideo.ko" in /lib/modules/blah-blah and moving it to uvcvideo.ko.orig.


Here's where your current drive is at right now:
# find /lib -type f -name 'uvcvideo.ko'

5. cd back to the local git repo and type "sudo rmmod uvcvideo && sudo make install" to unload the old driver and install the new driver.

6. enjoy (tested with latest Skype and Cheese 2.22.3, work great so far)!

(btw, in Vista Home Premium that came with this laptop, the camera image is not upside down, but mirrored instead -- left is right, and right is left)


Cheers!

---

### Post by HunterThomson on 2009-02-27
Hi everybody

Seems that has been a lot of work being done. Good work GoogleGuy for fixing the camera. Mine has always worked fine but I am sure there are a lot of people who will be vary pleased. As for the back light it was solved for the Y510 by re-writing some of the DSDT. Glad to here the new Kernel fixes that. I will be happy to see if it works for me and then I don't have to use the mod-DSDT.

Speaking of the new Kernel.... I am on kernel 2.6.27-11 What is everyone ells on? My fried brought his computer over for me to fix up and he is on a much latter Kernel. I think I need to change the repo I have first in the list. Then again it is nice waiting to get things after the bugs have been fixed.

---

### Post by nmfralich on 2009-03-03
Well I can only speak for myself, but the recent attempt to fix the webcam has come up short for me.  I tried it once and I'll try it again to be sure, but more importantly I had another idea.  Perhaps this is a little too naive, but would it not be possible to mimic the approach Cheese uses when it flips the image when you select flip under effects? Just a thought...

---

### Post by mylh on 2009-03-03
Hi all

I didn't have enough time to be happy with my new lenovo y530 after fixing sound as it is not works properly again.

After a couple of updates and software installations something strange happened to my soundcard. Now it is detected as having realtec ACL1200 codec instead of ACL888.

Does anybody expierienced such problem? How to make it become ACL888 again. I tried to completly remove custom compiled sound drivers, reinstalled it from ubuntu repository. It is helped and soundcards detected as ACL888 again. But if I then compile and install new alsa drivers as before,it is detected as ACL1200 again. Any ideas?

Any help will be appreciated. Thanks.

---

### Post by kulit494 on 2009-03-03
Greeting all!

I am very happy for this thread. I recently (12 hours ago) wiped Vista from my Y510 and installed Fedora 10 (yes I know this is an Ubuntu forum, but there was no where else for me to go). Everything is running smoothly so far, but I have hit a few snags. Oh, and I have read the previous posts and still need help.

- My mic does not work. I mainly would like to use it for skype and the previous suggestions have not worked (i.e. setting sound in to (hdel:intel, 0).
- I was just hoping for a little clarification on the compiz issue. Does it work? with or without hacks? I saw some posts on it, but still came out unclear.
- Lastly the webcam. I know that this is the ongoing struggle. I am happy to see GoogleGuy's post, and will try it shortly.

Thanks for any info you can give. This thread has been a lifesaver. I now need to try and solve the speaker/subwoofer issue. Thanks again!

---

### Post by myagaa on 2009-03-09
Hi. Tnx for solving problems.
  I have some problems about media buttons. I installed ubuntu 8.10. Yesterday my laptops' media buttons were working good. But it's not working properly today. When i press volume up button it's not controlling my sound card. It's controlling my Microphone(volume up). When i press volume down button it's controlling Microphone(Volume down). And when i press mute button it's muting my microphone. How to fix these problems. I didn't install any programs and drivers...
 I configured alsa-base driver by options snd-hda-intel model=lenovo-ms7195-dig. 
  Sound is good but i cann't control volume :( 
 plz gimme advice.

etc. 
Lenovo Y510 2.1 GHz
4GB RAM
OS: Ubuntu 8.10
   tnx

---

### Post by nmfralich on 2009-03-09
I would like to second myagaa's woes and hopefully add to the urgency people feel to solve this problem...also, webcam anyone, now registering in 8.10, but still upside down

---

### Post by winnibob on 2009-03-09
@kulit494
> **kulit494 said:**
> - I was just hoping for a little clarification on the compiz issue. Does it work? with or without hacks? I saw some posts on it, but still came out unclear.
I experienced a few problems (i.e. compiz random crashes) on older ubuntu versions (7.10 and 8.04) but it is really stable since I use kernell 2.6.27 with Xorg and Nvidia driver versions officially supported in Ubuntu 8.10 (i.e. Xorg v.1.5.2 and Nvidia driver v.177.82).

Edit : I forgot to mention that this behaviour is the one I experienced **without hacks**.

---

### Post by winnibob on 2009-03-09
@myagaa
> **myagaa said:**
> I have some problems about media buttons. I installed ubuntu 8.10. Yesterday my laptops' media buttons were working good. But it's not working properly today. When i press volume up button it's not controlling my sound card. It's controlling my Microphone(volume up). When i press volume down button it's controlling Microphone(Volume down). And when i press mute button it's muting my microphone. How to fix these problems. I didn't install any programs and drivers...
 I configured alsa-base driver by options snd-hda-intel model=lenovo-ms7195-dig. 
  Sound is good but i cann't control volume :( 
 plz gimme advice.


I had this problem once and I solved it by right-clicking on the speaker icon in the system tray and selecting "Settings" (I don't know if it really is "settings because my system is in french, so it is written "Préférences". Anyway, it's the third line). In the box that appears, you should select the peripheral "HDA Intel (Alsa Mixer)" if it's not already done, and select below the channel you want to control with the media buttons for this peripheral (Main Volume if you want to control the output of Alsa Mixer).

I think this is how it works. It solved the problem for me. I hope it could help you.

---

### Post by myagaa on 2009-03-09
Tnx for reply winnibob.
  I tried by your settings. But i had still problems...
 In the Preference - HDA(Intel Mixer) - Master is selected. :(

---

### Post by mylh on 2009-03-10
Myagaa, winnibob said right. You just have to select what chanel is controlled by volume control applet. In KDE you can do this somewhere in settings of volume control. I don't remember exactly where, but it quite obvious, try to right-click its icon.

---

### Post by myagaa on 2009-03-10
Yeah i tried... But still problem continues...
there don't have any choice. I can choose 
Select the device track control. And there: Master, PCM, FRORNT, FRONT MIC.... and Close button :(
  I choice Master. Problem is same :(
  grub :(

---

### Post by HunterThomson on 2009-03-11
Well, I swiched back to Archlinux and loveing it. It realy is faster.

Also, Archlinux as you know is a rolling disto and so I am using the newest kernel 2.6.28 and Yes the backlight thing is fixed in it. I have no problem with the backlight at all. There is no need to use the custom DSDT. So, to all you people using the 530 and stuff your backlight mite work whith the new 2.6.28 kernel.

---

### Post by mylh on 2009-03-11
good news :)))

By the way, anybody managed to make MemoryStick cards work with builtin cardreader?

---

### Post by winnibob on 2009-03-11
@myagaa

If you want to have a bit more configuration options, you should try System->Settings->Sound (or something like that).

There are some things that are differents between our two configurations.
First, I don't use lenovo-ms7195-dig but lenovo-sky model (which seems to work very well) in my /etc/modprobe.d/alsa-base
Second, I compiled myself the latest alsa version, following the tutorial in post #2 of this thread (because of few problems I don't precisely remember).
There may also be differences in our use of ESD/OSS/ALSA, but I don't think that your problem is related to this.

I suggest you try lenovo-sky model, and read alsa mixer documentation if it has no effect.

Good luck!

Edit : I'm using Gnome desktop, so my advice could be unhelping if you're using KDE.

@nmfralich

You seemed to have the same problem. Is it solved for you ?

---

### Post by wyth on 2009-03-11
Hey winnibob -- 

A long time back you wrote about how you were able to get your machine to use less power.  

I'm interested in what you did.  I've been through lesswatts.org, and have made a number of adjustments, and attempted undervolting (failed).  

Powertop does offer some useful tips, but the problem is you have to keep powertop running to keep the altered settings in place, and it's constantly telling me to shut down USB, which I need for my mouse.  But things like adjusting the SATA for min_power and adjusting the wireless via powertop worked well.  I'd love to find a way to make those permanent.

---

### Post by myagaa on 2009-03-12
Hello Everybody. 
I installed New ubuntu :p and now everything is fine :)
  I use lenovo-sky driver.
 Before i used:
options snd-hda-intel model=lenovo-ms7195-dig
  When i use lenovo-ms7195-dig, and plugin headphone it's not good working... :) 
  Lenovo sky is very good :) tnx

---

### Post by mylh on 2009-03-12
> **myagaa said:**
> 
  Lenovo sky is very good :) tnx

My subwoofer finally started to work as I use this option. Thank you very much!!!

---

### Post by winnibob on 2009-03-13
Hi wyth,

A few tips for you :

> **wyth said:**
> I've been through lesswatts.org, and have made a number of adjustments, and attempted undervolting (failed).

There is a really good thread about undervolting for notebooks [here]("http://ubuntuforums.org/showthread.php?t=786402"), in case you have not already read it. 

> **wyth said:**
> Powertop does offer some useful tips, but the problem is you have to keep powertop running to keep the altered settings in place, and it's constantly telling me to shut down USB, which I need for my mouse.  But things like adjusting the SATA for min_power and adjusting the wireless via powertop worked well.  I'd love to find a way to make those permanent.

When powertop gives you a tip, you can either press the key that is told to apply it or copy and paste the given command line in a terminal : it has the same effect, but it doesn't end when you shut down Powertop. To make these changes permanent, you just have to copy these command lines in your /etc/rc.local , before the exit line. So these commands will be executed with root permissions on each boot.

Good luck.

---

### Post by myagaa on 2009-03-15
Hello. I have some question.
  Do u use NOVO button (Power management button) for ubuntu 8.10? :)

---

### Post by winnibob on 2009-03-16
Hi everyone,

Since I installed Ubuntu on my Y510, I have had several problems making the multicard reader work.

At the beginning it was working perfectly, and after a kernel update it was unusable, this was fixed in the next kernel release, and after I regularly had multicard reader problems again with kernel updates.

So I post here a deb of Ricoh driver, which seems to manage the multicard reader very well.

Cheers

Edit : This driver solves problems with SD cards, not sure for other types...

---

### Post by wyth on 2009-03-16
> **myagaa said:**
> Hello. I have some question.
  Do u use NOVO button (Power management button) for ubuntu 8.10? :)

Actually I've never touched it.  As far as I recall, it was a trigger to install a backup installation of Vista.  I imagine it could be configured to work with a backup of Ubuntu, but I've not toyed with it.

---

### Post by wyth on 2009-03-16
> **winnibob said:**
> Hi wyth,

A few tips for you :


Okay, going through the power-saving tips:

Yep, I've been through that undervolting page backwards and forwards.  The script always came up with funky numbers for me, and I didn't get very far.  

As far as powertop goes there are three suggestions that I'd like to make permanent -- one for iwl3945 power level, one for sata power level, and one to disable hal from polling the cd-rom.  These three come up every time I run powertop, and they've never caused a problem for me. 

So here's what my /etc/rc.local looks like:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 5 > /sys/bus/pci/drivers/iwl3945/0000:02:00.0/power_level 
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
hal-disable-polling --device /dev/cdrom
exit 0
```

But on reboot, none of those powertop suggested changes took, and it was back to normal.  This is the issue I've been running into.  It's one of two things that have been bugging me lately:

[LIST=1]
[*]It should be possible to make power-saving changes permanent, and
[*]It should be possible to add a line in the command to start a program via Alacarte to make a program **Always On Top** or **Always on Visible Workspace** automatic.  (I know there is something through devilspie, but installing an application to do something Metacity already does seems needlessly redundant.)
[/LIST]

---

### Post by winnibob on 2009-03-17
Hi Wyth,

Let's see what's wrong, and what we can do, because the things I told you are apparently working fine on my system.

**About undervoting :**

What is really your problem with this ?
If it's related to the undervolting test script going down to multiplier zero without making your system freeze, I had the same problem and this is totally normal.
For other problems, you may find help on the undervolting thread.

**About powertop tips :**

It's strange that your added lines in rc.local are unefficient, because it works for me.

Here is the end of my rc.local :

```
# By default this script does nothing.

# set cpus voltage to min supported
echo "12:19 10:19 8:19 6:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
echo "12:19 10:19 8:19 6:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
# increase writing interval of modified pages from 5sec to 15sec
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
# disable hald polling on cdrom
hal-disable-polling --device /dev/cdrom
# wifi powersaving state
echo 5 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level

exit 0
```And while my system is running, i get this :

```
cat < /sys/devices/system/cpu/cpu1/cpufreq/phc_controls
12:19 10:19 8:19 6:19 
cat < /proc/sys/vm/dirty_writeback_centisecs
1500
cat < /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level
5 (Timeout 25ms, Period 1000ms)
```So it seems to work, but even if the cdrom polling line works (tested on my system), powertop always tells me something about it (I think it always does because it has no way to check it).

I removed the sata power level line because the /sys/class/scsi_host/host0/link_power_management_policy file doesn't exist any more on my system and it made my rc.local exit without executing the last commands.

AFAIK, when a command cannot be executed, the rc.local exits before the end, and each time I had a problem in my rc.local it was related to this. And of course, make sure your rc.local is executed at startup.

Hope it helps.

Edit : I didn't understand what you want to do with "make a program Always On Top or Always on Visible Workspace automatic" ?

---

### Post by nmfralich on 2009-03-17
ok, perhaps a very naive question, but how do I check to see that rc.local is being loaded?

---

### Post by wyth on 2009-03-17
(nmfralich, I'm feeling pretty naive too -- just haven't had time to tear into things)

winnibob -- the Always On Top and Always on Visible Workspace are options you get when you right-click the top of any window.  (See the attached screenshot)

[LIST]
[*]Choosing Always On Top makes that window/application always appear on top of every other window. This can be useful for all sorts of things, especially if you're researching and/or writing and need to look at one or two things while writing on a third document.
[*]Choosing Always on Visible Workspace makes that window sticky on every workspace.  So for instance, I have three workspaces.  When I'm writing, I'll have a set of research and info open in one workspace, and a different set open in a second, and maybe some time waster on the third.  I'll set the document, Banshee, and maybe Pidgin to Always on Visible Workspace, and no matter what workspace I switch to, those applications are always visible.
[/LIST]
I love those options and use them nearly every time I'm at my machine.  But there are certain applications that I just always set to the same setting, and I didn't see a way to make those settings persistent and permanent.  I thought there must be some sort of hidden switch you could add the the exec in the menu, but I just couldn't find it.

However, I figured it out today.  If you run Compiz and have ccsm installed (the big CompizConfig Settings Manager), you can accomplish this with the Window Rules plugin.  For instance, to make an application always visible on every workspace, add it to the Sticky section in Matches.  To add it, you can use the tool to grab an application, or type class=foobar in the dialog.  To add more than one, separate them by a pipe.  So for instance, 
```

class=banshee-1 | class=Pidgin | class=gnome-terminal

```would make Banshee, Pidgin, and the terminal visible on all workspaces all the time.  Compiz takes care of it.  (But metacity should.)

It was a while ago when I tried to undervolt my machine, and I didn't have any of the regular problems.  If I recall correctly, I ran the script, it finished, and it never really gave me any parameters.  It's supposed to crash the system a few times and find the limits, but that never happened.  So I just never got the data I needed to work the undervolt.  I don't know if it's all that necessary, but my problem was working at my university's library; they blast the heat back in the carrells in the stacks, and that makes the desktop very warm.  Put a laptop that already runs warm on top of that, and my machine was getting toasty.  I was hoping undervolting would generate less heat in the machine and spare some potential damage.  

I'm not sure why my rc.local isn't being called at boot, but it doesn't seem to be.  Using sysvconfig, I see that a few modules aren't set to run at boot, and maybe one of those are needed to let rc.local do its thing.  I don't know enough about these modules, but the ones that caught my eye were:

[LIST]
[*]bootmisc.sh
[*]glibc.sh
[*]module-init-tools
[*]procps
[*]x11-common
[/LIST]
Again, I'm not too sure about any of that, but I know my rc.local file isn't passing the commands I added to it on boot.

---

### Post by myagaa on 2009-03-17
Ok. I usually use CPU performance panel.(added in panel)
  Do u use TV card how to use?

---

### Post by wyth on 2009-03-17
> **myagaa said:**
> Ok. I usually use CPU performance panel.(added in panel)
  Do u use TV card how to use?

If you're referring to ways of lowering power usage with the CPU performance panel, yep, I've used that.  Undervolting is a way of pushing that tweak, and with powertop there are all sorts of other little tricks you can enact to make a laptop use even less power.

Can't say I use a TV card.  I don't even think one comes in the Y510, does it?

---

### Post by cerfbennet on 2009-03-18
**New sound issues**

First, thanks to everyone who has been contributing to this thread (I just found the continuation).

I wanted to try out lenovo-sky, so I thought I would update alsa-driver, alsa-lib, and alsa-utils. The latest version as of January is 1.0.19.

A couple of changes from Wyth's directions:
* the package xmlto is required
* the models are listed in a separate file ../alsa-kernel/Documentation/HD-Models.txt

I set the model to lenovo-sky and rebooted, but I am only getting sound out of the speakers near the back. I am going to try to debug this/try some other models and then I'll provide more information.

Question: should the ouput of ```
cat /proc/asound/version
``` return the same version number as alsa-driver, lib, utils?? I get 1.0.17...

**Update:** OK, I was dumb. I forgot to run make install for alsa-driver. Everything is working great now.

---

### Post by winnibob on 2009-03-19
Hi guys,

**About the rc.local execution :**

> **wyth said:**
> I'm not sure why my rc.local isn't being called at boot, but it doesn't seem to be.  Using sysvconfig, I see that a few modules aren't set to run at boot, and maybe one of those are needed to let rc.local do its thing.  

Again, I'm not too sure about any of that, but I know my rc.local file isn't passing the commands I added to it on boot.

This is not a module problem at all.

First, make sure it is executable by typing in a shell :
```
sudo chmod +x /etc/rc.local
```
To test tour rc.local execution, you can just add this line **fist** in it
```
mkdir /temp/my_rc.local_dir
```
and see if it worked after a reboot (remember to delete it after testing).

If not, it's because there is no link to it at startup. So you'll have to play with your shell a bit.
**Remember that the following manipulations could damage your os or break its security if thy're not done well. Do not try this if you don't know what you are doing. I will not be responsible for any problem.** 
First, check which runlevel you are running typing "runlevel" in your shell. It will tell you "N X", where **X** is a number between 0 and 6 (usually 2).
Second, make sure you have the script /etc/init.d/rc.local, which is made to execute your /etc/rc.local securely when it exists, and make sure it is executable.
Finally, create a link to it in the good runlevel (if there is not already one, of course) :
```
sudo ln -s /etc/init.d/rc.local /etc/rc**X**.d/S99rc.local
```
Then everything should be fine and your rc.local will be the last script executed at startup (because of the S99).

**@ wyth -- about undervolting**

> **wyth said:**
> It was a while ago when I tried to undervolt my machine, and I didn't have any of the regular problems.  If I recall correctly, I ran the script, it finished, and it never really gave me any parameters.  It's supposed to crash the system a few times and find the limits, but that never happened.  So I just never got the data I needed to work the undervolt.

Ok, it seems to be the same issue I had and that I described in my previous post, and as I said, it is totally normal. It is due to hardware limitations of the processor (mine is T2330) that prevent your motherboard to undervolt your processor below multiplier 19. So even if your software tells your hardware to lower the voltage under multiplier 19, your mobo will stay at this minimum voltage. While your software doesn't see that, it will "think" your CPU voltage went to multiplier 0 without crashing, what is obviously wrong. So the software can't tell you what is your CPU's limitations, because it can't see any.

To be sure, you can easily test this, setting your CPU freq to minimum (less risky) and adjusting the corresponding multiplier in /sys/devices/system/cpu/cpu0/cpufreq/phc_controls (and /sys/devices/system/cpu/cpu1/cpufreq/phc_controls if you have a dual core). With [read_msr]("http://www.linux-phc.org/viewtopic.php?f=13&t=13") or [msrinfo]("https://www.dedigentoo.org/bdz/linux-phc/") (the second has my preference, more clear and reliable), you'll be able to see which multiplier the system is asking for and which multiplier your CPU is really running with.
With these tools and BurnMMX, you should be able to run manually the tests that are automated in the script for each frequency (remember to run one BurnMMX process for each core).

For information, I run the lowest voltage (multiplier 19) for all frequencies since many month and never had a problem.

Bye

---

### Post by nmfralich on 2009-03-19
I also saw rc.local in the list of items when I ran sysvconfig in the terminal.  It may be as simple as checking the box there to get it to run at startup

---

### Post by winnibob on 2009-03-19
I don't know, I don't have it, so I don't use it.

---

### Post by droid8622 on 2009-03-19
I m sorry if i have missed the answer - but my ```
Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```
is always ON after restart - i need to turn switcher on and off - to turn off wireless...Somebody have the same issue?? Tested with 8.10 and 9.04 alpha 6 - the same

---

### Post by GoogleGuy on 2009-03-20
> **droid8622 said:**
> I m sorry if i have missed the answer - but my ```
Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```
is always ON after restart - i need to turn switcher on and off - to turn off wireless...Somebody have the same issue?? Tested with 8.10 and 9.04 alpha 6 - the same

I just spend 15 minutes researching this, as it's been bothering me too.

The culprit: asus-acpi module (which is loaded at bootup)

How to work around it: add "echo 0 > /sys/devices/platform/asus-laptop/wlan" to your rc.local before the "exit 0" line. No quotes, of course.

How to fix it permanently: Not sure, fix the source of asus-acpi? Fix the DSDT? both mention WLED, but this kernel ACPI stuff is mostly above my head.

Hope this helps.

---

### Post by nmfralich on 2009-03-21
> **winnibob said:**
> @myagaa

If you want to have a bit more configuration options, you should try System->Settings->Sound (or something like that).

There are some things that are differents between our two configurations.
First, I don't use lenovo-ms7195-dig but lenovo-sky model (which seems to work very well) in my /etc/modprobe.d/alsa-base
Second, I compiled myself the latest alsa version, following the tutorial in post #2 of this thread (because of few problems I don't precisely remember).
There may also be differences in our use of ESD/OSS/ALSA, but I don't think that your problem is related to this.

I suggest you try lenovo-sky model, and read alsa mixer documentation if it has no effect.

Good luck!

Edit : I'm using Gnome desktop, so my advice could be unhelping if you're using KDE.

@nmfralich

You seemed to have the same problem. Is it solved for you ?

Thanks for the advice, for me it was as simple as System->Preferences->Sound 'Default Mixer Tracks:HDA Intel (alsa mixer):Master'

---

### Post by wyth on 2009-03-23
Sheesh -- been way too busy, haven't been able to respond.

Here's what I can tell you so far:

I'm less concerned about undervolting right now.  I actually need to use my laptop for some video and audio this semester, and need the power.

But as far as those wake-ups and the rc.local, I did the test, and rc.local made the temp file like it should.  However, when I check /sys/class/scsi_host/host0/link_power_management_policy and /sys/bus/pci/drivers/iwl3945//0000:02:00.0/power_level, those always remain at their normal full level.

I'm thinking about moving to Jaunty soon, with a scorched earth clean install, and that may make a difference.

---

### Post by winnibob on 2009-03-24
Hi wyth,

> **wyth said:**
> I'm less concerned about undervolting right now.  I actually need to use my laptop for some video and audio this semester, and need the power.Undervolting is not underclocking! It is just lowering the voltage of your CPU to the minimum it can run with. It makes it produce less heat without reducing the perfs.

> **wyth said:**
> But as far as those wake-ups and the rc.local, I did the test, and rc.local made the temp file like it should. However, when I check /sys/class/scsi_host/host0/link_power_management_policy and /sys/bus/pci/drivers/iwl3945//0000:02:00.0/power_level, those always remain at their normal full level.I don't know what your problem could be, as it works fine for me.

Good luck with Jaunty, I'll try the final release next month.

---

### Post by wyth on 2009-03-24
> **winnibob said:**
> Undervolting is not underclocking! It is just lowering the voltage of your CPU to the minimum it can run with. It makes it produce less heat without reducing the perfs.

Well, either way I've been too busy to really deal with it right now, and have been relying on my desktop more.  As for the rc.local thing, I've even gone in as root (sudo su) and hand edited the files powertop suggests to change, and they've never stayed changed.  That one has me stumped.

---

### Post by chargersfan420 on 2009-03-24
Hey everyone.  It's been a while.

@ Wyth

Before you do a "scorched earth" install to Jaunty, consider learning from my past mistake.  For some reason, ATI is slow at putting out drivers suitable for the newest versions of Ubuntu.  I'm still on 8.04, because when i tried to upgrade to 8.10 back in November, compiz was pretty much unworkable.  I've been thinking there must be something useable now, but i am not sure if i want to upgrade.  The idea of LTS in 8.04 is appealing, but it is depriving me of newer kernels... (i'm stuck on 2.6.24-23-generic).  I suppose it all depends on how much time you want to invest on being current.

Although all this might be moot being on the Y710... It's got an ATI Radeon HD 2600.  Not sure about Y510s, or the availability of drivers.

@ anyone interested in the card reader

Not sure if this is helpful (being on older kernel listed above), but I found that the first few times i inserted a card into the slot, nothing.  Without doing any tweaks, i found it actually started working after removing the card and plugging it back in a few times.  One time it was even mounted "read only".  Can't explain that one, but it's been fairly reliable since.  (Using SDHC Micro w/adapter)

@ anyone

This might be a bit of a noob question, but is there a "dmesg" equivalent for shutdown?  I see some weird errors when i shut down, something about wireless, and this was consistent on both GRUB and LILO... but the weird thing is wireless seems to work fine, no complaints.

While catching up on the thread, i also saw someone mention something about making use of the NOVO button.  There's a [[COLOR="Blue"]tutorial posted to the lenovo forum[/COLOR]]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=4467&query.id=94220#M4467") that explains how to insert an image into the boot service partition.  It could come in handy if you were trying to set up Ubuntu for a friend (especially if you make the /home folder a separate partition), but if you're always on the newest kernel available, it might not be very useful.  I don't know how well or even IF it will work with linux, it's a pretty long thread, and i didn't get through it... but it might help someone.

---

### Post by JSuresh on 2009-03-26
This is a bit off-topic but have you Y510 guys had any hinge problems with the right hinge (behind the sound control buttons)?  Mine just broke for the second time (sent it in for repairs the first time), and on the lenovo forums it seems this might be a design flaw.

---

### Post by GoogleGuy on 2009-03-27
> **JSuresh said:**
> This is a bit off-topic but have you Y510 guys had any hinge problems with the right hinge (behind the sound control buttons)?  Mine just broke for the second time (sent it in for repairs the first time), and on the lenovo forums it seems this might be a design flaw.

I've seen this problem in the forums, I hear Lenovo recognizes this as a design flaw and fixes this for free. AFAIK, the problem's been addressed in recent Y510 models.

Can you tell me how old the laptop was when the hinge broke?

---

### Post by JSuresh on 2009-03-27
> **GoogleGuy said:**
> 
Can you tell me how old the laptop was when the hinge broke?

The hinge first broke last August, and it broke again a week or so ago.  I'm sending it in again, I hope they fix it for good this time and don't wipe ubuntu off of the machine :rolleyes:

---

### Post by wyth on 2009-03-28
> **chargersfan420 said:**
> Hey everyone.  It's been a while.

@ Wyth

Before you do a "scorched earth" install to Jaunty, consider learning from my past mistake.

Oh yeah, I'm aware of the possible dangers (been at this for a five years now).  The /home directories are on their own partitions and backed up.  Besides, there's no way around it; I want to try Ext4, and that means formating the hard drive.  But I'm waiting for the stable release and the time to do it all.

But my machine is one of the first iterations, before they got all shmancy and put nVidia and ATI cards in them; I have one of those basic GM965/GL960 graphics chips that can't run OpenGL very well (Google Earth is a horror show, and Sauerbraten just doesn't happen).

---

### Post by HunterThomson on 2009-04-02
Well I got the media keys to work in Archlinux. It turns out I was thinking the wrong way. I was trying to set hot keys system wide which I can't do. But all I had to do was set them in VLC and Quodibet(A dependency light clone of Rythembox) And Quodibet just worked.

I use the SD card reader all the time with no problems. In fact I use it as my /home partition for the most part. I have a 8GB SD that I have set in /etc/fstab too mount at boot. This is because I just got a small SSD and nedded the extra space.

I also got 4GB of CAS4 ram wich seems to help a lot with games on my intel GPU.

Ya, I got a 30GB Vertex OCZ SSD drive. It works no problem. Crazy fast. 250MB/s read and 155MB/s wright. I will never regret it :) No more head park, drive spin down/up, Cycal count stuff. It will keep my data now and latter, never brake.

Chargersfan420, It sounds to me you are ready to move on to a more advanced Linux distro. I don't see how it could get much better then archlinux. Rolling disto so no big swiches messing things up. Not as many packages avalabe but enugh. And buinding from AUR is almost better then the packages are built from source on your proccesor and are keept up to date by that package manager. It takes way longer to set up but if you do you can be sure to have a system that is alwas up to date and stable. Ubuntu is just far to genaric to be good. You don't have any controle as to what gets installed as dependencies and you don't realy no what you have installed because you didn't set it up. So, if an ubuntu box is not workign wright it is much harder to find the real cause. Just my thought. If your stuck on 8.04 do to upgrade hell you would love Arch linux.

Also, the log your looking for for shut down... well the everything log should do. I bet you it is just failling to bring down the wierless interface. This is not a problem just a bug in network manager. But if you can not find the log you need then you can always press "ctrl+s" to stop the shutdown so you can read the error. Then press "ctrl+w" to continu with the shut down. You can use thoughs hot keys to stop start anything that is running in a shell.

---

### Post by GoogleGuy on 2009-04-07
> **JSuresh said:**
> The hinge first broke last August, and it broke again a week or so ago.  I'm sending it in again, I hope they fix it for good this time and don't wipe ubuntu off of the machine :rolleyes:

Good luck, I hope they fix it for good too!

My right hinge creaks sometimes and is a little tight :mad:. Was yours creaking before it broke?

GoogleGuy

---

### Post by chargersfan420 on 2009-04-08
Thanks for the suggestion, HunterThomson.  I will consider Arch when i eventually make a move... i find my biggest problem is that there is only one person i know of in the whole world with my same laptop, and using Ubuntu on it... this is something i will consider with my next purchase.

My newest biggest problem is now the battery.

Wyth's recent posts on improving battery life had me checking some things out.  I installed powertop and found that my laptop likes to eat around 30+ watts on battery power.  My most common cause for interrupts to sleep mode are Virtualbox, which is somewhat understandable... but i can't seem to get more than 2.5 ms in a C3 state, even with Vbox turned off.  From what i understand, increasing my average time in C3 will have the greatest impact on battery life, although i have no idea how to do this.

What is even more concerning is what i see when i run this command:
```
~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         56160 mWh
last full capacity:      21290 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 1060 mWh
design capacity low:     742 mWh
capacity granularity 1:  318 mWh
capacity granularity 2:  20230 mWh
model number:            LTY-TS0A0A
serial number:            1191
battery type:            LION
OEM info:                SANYO


```
I used to boot and see a quick message flash across the screen, but it never hung around long enough for me to read it... well, it does now, and it says that my battery is only charging to 39% of its capacity.  A few days ago, it was 46%, and it seems to be dropping quickly for some unknown reason.  (last full capacity was 24000 mWh about a week ago, now only 21290 mWh).  At this rate, I won't have a functional battery at all in 2 months, and a useless one before then.  I haven't found anything in Ubuntu capable of battery regeneration.  I booted into Vista hoping to find a pre-installed app that could regenerate the battery like the Thinkpads have, but there was nothing.  What is up with that?  Is it because Thinkpads use something other than Lithium Ion batteries?

I was getting only about an hour out of the battery since i purchased the laptop (almost a year ago), regardless of whether or not i was using Ubuntu or XP (which the ACPI driver failed to install for), but now i'm down to maybe 45 minutes tops... I have never spent more than 20 minutes in Vista, so theoretically it would make better use of the battery... but who wants to use Vista?

I would greatly appreciate any suggestions anyone might have here...

---

### Post by GeorgeVita on 2009-04-08
Hi **chargersfan420**,

> **chargersfan420 said:**
> ... At this rate, I won't have a functional battery at all in 2 months, and a useless one before then.  I haven't found anything in Ubuntu capable of battery regeneration.
...
I was getting only about an hour out of the battery since i purchased the laptop (almost a year ago), regardless of whether or not i was using Ubuntu or XP (which the ACPI driver failed to install for)..., but now i'm down to maybe 45 minutes tops...

My opinion (from h/w side) is that ACPI or O.S. can extend the life expectancy of the battery by consuming less power resulting to less charges (charge/recharge cycles). This can be done with idle/sleep/lower clocks for CPU and peripherals. Most manufacturers control the charge of the battery via special circuitry or BIOS.
A careful reading of a technical specification for Li-Ion batteries (or even OLED displays) gives an idea for the designed life cycle of the final product (laptop, mobile phone etc.). Most consumers recycle the product without changing a consumable part (battery).

Specifically for Li-Ion batteries I found [http://www.buchmann.ca/Article5-Page1.asp](http://www.buchmann.ca/Article5-Page1.asp) (a small part can be found below)

> 
A typical life of a lithium-ion is 300-500 discharge/charge cycles or about three years from time of manufacturing. The loss of battery capacity occurs gradually and often without the knowledge of the user. Although fully charged, the battery eventually regresses to a point where it may hold less than half of its original capacity. The function of the battery analyzer is to identify these weak batteries and "weed' them out.


Regards,
George

---

### Post by ReuseablePlastix on 2009-04-11
Thanks everyone for your work on this, I've really enjoyed the reading... I've made some good progress as a new linux and ubuntu user however I've got two hang-ups that I'd really like some assistance on: sound and sleep/hibernation.

Here's what I'm working on:
Lenovo Ideapad Y530 (4051-2YU), Intel Core 2 Duo P8400 2.26Ghz, NVIDIA GeForce 9500M G, 4GB RAM, Intel WiFi Link 5100, Ubuntu 8.10 x64

SOUND -
I got the sound working quite well aside from the built in mics (saw some posts that I never got to try).  Just yesterday however, Ubuntu quit recognizing my sound card.  I believe the issue came after the latest update.  The message I receive is as follows:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I did some other light reading to try to troubleshoot and here are some results:

results for aplay -l
```
aplay: device_list:215: no soundcards found...
```

results for lspci -v | less
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Device 3a0d
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d3d00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel
```

SLEEP/HIBERNATION:
It just doesn't work - I get a black screen with a blinking cursor. I can't ctl+alt+F2 out of it I"m not sure where to go from there so I have to do a hard reset. I'm not sure if it's a swap issue or if it's an Nvidia thing.  I get a little lost in the conversation between chargersfan and HunterThompson about ACPI and DSDT, so I'm not really sure if I'm in the same boat or not.


Any assistance would be appreciated.
Thanks.

---

### Post by HunterThomson on 2009-04-12
As for the Mic. Mine work. I have to set them to "Front Mic".

Also, I alwas had a problem with my sound not being set the way I like it at start up i.e. most things mutted and stuff. But, I found the answer in the Archlinux Beginners Guide. (note, I edited it a bit so it makes scents out of context)

>   Saving the Sound Settings

First set the alsamixer to the setting you would like on startup. Then,
Exit your normal user shell (enter the root shell "sudo su") and run /usr/bin/alsactl as root

```
alsactl store
```

This will create '/etc/asound.state', saving the alsamixer settings

ReuseablePlastix, as for your now not working sound. I am sure there is a simple way to fix it by just editing some files. However, I don't know them or feel line walking through it with you. So, my sugjestion is to go thorugh the ALSA driver install written by wyth. I coppied it to the first page of this thread. If you do all that is there in order it should solve your problem. I think your 530 uses the same audio as the 510 so try the "lenovo-sky" module.... well close enugh. Mine is.....

> Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller

As for the suspend and resume... We were messing with the DSDT was to solve a backlight problem but ya the suspend/hibernate is a part of ACPI. The reson it dosn't work is Lenovo falt for compileing the BIOS files used in ACPI with Micro$oft's compiler. Suprize suprize MicroShaft's compiler is not standards compliant and it is proprietary. There is no way to know what kind of code is coming out of their compiler unless your Micro$aft. So, in the end ACPI works vary well for Windows becaus Mico$aft knows what code is comeing out of there compiler. But everyone els looks stupid because they are wrighting the BSD kernel and the Linux kernel and UNIX.... based on the ACPI code being standards compliant but the code is not. So, Linux and everyone have to add patches to the ACPI Kernel module for the messed up M$ code as it comes. This is one of the clearist cut casses to show how Miro$oft is bad for the consumer and use unfare business practises. This was also part of the Supreem cort case aginst M$ for monopoly... The case M$ lost but then weaselled out of the punishment of, spliting IE into it's own Compay, by integrating IE into Windows.

On the Same note, if you didn't know, Windows IE also is not standards compliant so MicroSoft was trying to prevert websight code so web sights would only display corectly in Windows IE. This is why Novel droped Netscape started the Mozila project and came out with FireFox. Novel makes there realy money in the Server market. If Micro$aft were to have that hold on the Web they could have pushed everyone ells out of buisness because they would have preverted the code so much that the WWW would only work on MicroCrap Software.

This was working too. IN the early to mid 90's a lot of web dev's were getting lazy and only coding web pages to work on IE. As a resolt a notable part of the web was IE only at the time.

MicroSoft is a vary dangerous compay in terms of development and consumer choice. Use Open Sorce whenever you can.

---

### Post by HunterThomson on 2009-04-12
move along

---

### Post by chargersfan420 on 2009-04-12
Good day everyone!

@ GeorgeVita - Thanks for the great info and the quick response.  Unfortunately, there was nothing in the BIOS about the battery.  No tuning controls, no regenerator, nothing. That was a little disappointing.  I believe my battery is getting a bit old, but there was something about the combination of the 2.6.24-23-generic kernel + Sun xVM Virtualbox 2.1.2 that was killing it faster than it should. 

However, I have made the jump to Jaunty 9.04 Beta (64 bit), and I have lots of good news.  Before i get to that though, I should probably say...

@ HunterThomson - Sorry, man, but I don't think I'm ready for Arch just yet.  I was reading up on it, and I must say I like the concept of minimalist, building from the ground up (especially to get a good understanding of the way things work under the hood), but here are my reasons for not going there yet:
1.  I'm really busy right now - I just don't have the time.
2.  For now, I'd rather be an advanced beginner on Ubuntu than a beginning advanced user on another distro... if that makes any sense.
3.  I wanted to confirm that my upgrade hell situation was caused by the kernel I was stuck on.  I've never run powertop before that kernel, and I wanted to see its output on the newest kernel and see how it looked.

Okay, as for my results for Jaunty:
- Sound didn't work out of the box (front speakers only), but I didn't have to recompile alsa.  All I had to do was "sudo gedit /etc/modprobe.d/alsa-base.conf" (note the .conf as suggested by autocomplete) and add "options snd-hda-intel model=6stack-dell" (model works great for Y710's).
- Webcam worked out of the box!
- Card reader didn't work on the first try, but just like last time, all i had to do was unplug the card and plug it back in, and it works fine.
- Virtualbox came out with version 2.2.0, which seems to be working great so far.  Slightly fewer core interrupts than I was previously experiencing.
- ATI Drivers were a little tricky to get in, but are working great for things like compiz.  This was the problem I had when I went to 8.10 on release day, and it's nice to see the Ubuntu developers recognized this was a major issue for some and did something about it.
- Powertop has battery consumption around 8 watts lower (when doing not much), which to me seems to confirm my thesis that 2.6.24-23-generic was messing things up.  I also noticed that my cpu scaling governer was set to "ondemand" on both the old kernel and this one (2.6.28-11-generic), but on this one, I'm not stuck in a P-state of 2.51 GHz all the time.  The old kernel had me switching the governor to "conservative" or "powersave", but it doesn't seem to be necessary anymore.
- System boots much faster, especially using LILO, which is still necessary on a Y710 if you want to use your optical drive.
- Pulseaudio seems to be working without messing with configuration.  I can play music through Virtualbox and still get system sounds (such as a music preview when I hover my mouse over an MP3 in nautilus)

Battery capacity has stabilized at about 37% of its original capacity, and is no longer dropping quickly.  I get 30 - 45 minutes, depending on what is running.  At the moment I have lots running, have been on battery power for 25 minutes, and i supposedly have 11 more to go.  I'm going to get a new battery on order.

So far, my only issue is that some of powertop's suggestions don't seem to do anything anymore.  It used to say something like "press B to turn off bluetooth", and had the command "hciconfig hci0 down; rmmod hci_usb", but it doesn't suggest this anymore (and as it turns out, the appropriate module to remove is "btusb" anyway, which I inserted into /etc/modprobe.d/blacklist as "blacklist btusb".  It also needs to be disabled from System - Administration - Services and System - Preferences - Bluetooth).  Powertop keeps suggesting that I enable USB suspend, but the command doesn't do anything.  It suggests this for 3 devices:  Logitech mouse (umm, kinda need that), Webcam, and Bluetooth (which I have taken care of above). 

If anyone else is considering making the jump, let me know if you have any questions, or if I may have overlooked something...

---

### Post by HunterThomson on 2009-04-12
Chargersfan420 I think that if you made an /etc/fstab entre that mite solve your SD card problems.

Make sure you have the file /mnt/fl...

```
sudo mkdir /mnt/fl
```

try adding this line to /etc/fstab...

```
/dev/mmcblk0p1     /mnt/fl vfat user,noatime,umask=000     0      0
```

Here is a coppy of my /etc/fstab...

```
#
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0
tmpfs                  /tmp          tmpfs     noatime,mode=1777   0      0
tmpfs                  /var/tmp      tmpfs     noatime,mode=1777   0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
/dev/sr0                /mnt/disk  iso9660 ro,user,noauto,unhide          0      0
/dev/mmcblk0p1          /mnt/sd   vfat    user,noatime,umask=000          0      0
/dev/sdb1               /mnt/usb  vfat    user,noauto,noatime,umask=000   0      0
/dev/sdb2               /mnt/usb2 vfat    user,noauto,noatime,umask=000   0      0

UUID=f62caae4-6c9b-4abc-bc1b-6d2222a85895 / ext3 noatime,commit=120  0 1
```

---

### Post by PhilMize on 2009-04-15
Hey guys I've skimmed through this thread quite a bit for other things but is there any news on getting the built in mic to work with skype? Right now the reason I have been using windows over ubuntu is because of skype... I need it, love it, and and addicted to it...lol :lolflag:

---

### Post by HunterThomson on 2009-04-20
> **PhilMize said:**
> Hey guys I've skimmed through this thread quite a bit for other things but is there any news on getting the built in mic to work with skype? Right now the reason I have been using windows over ubuntu is because of skype... I need it, love it, and and addicted to it...lol :lolflag:

Do you have a Y510 ? Mine works fine in Skype. I have go in to the ALSA-Mixer and set both the mic's to "Frount Mic". I think I set someing in skype too... But it should work use frount mic setting in alsa and then go form there. You'l find a setting that works.

You should try a SIP phone though, it's Open Source. Skype uses it's own proprietary code that has been shown to pose a security risk. Also, Skype has rolled over to the US goverment and rout all your calls throught NSA computers and give up any and all info to whoever asks for it. Useing non-standard compliant software in the VOIP world poses the same threat to free thought and quality product as with any other field of software development.

[http://www.voip-info.org/wiki-Open+Source+VOIP+Software](http://www.voip-info.org/wiki-Open+Source+VOIP+Software)

""I love the computer world my anarchist beliefs can be argued soundly here.""

---

### Post by PhilMize on 2009-04-22
um... i personally dont care about the government listening in on my calls lol

and i played with the alsa mixer a bit but its confusing as heck... i cant figure out how to get to like more advanced settings... all i can do is raise vlume levels...lol


yes i have a y510

---

### Post by PhilMize on 2009-04-23
K so first off thanx again hunter for your help with the alsa drivers...


Upgraded to Jaunty like 30min ago and im having issues with getting compiz to work. When I go too the appearance tab under preferences and set the effects to extra it says "searching for available drivers", the screen flashes and then a window pops up saying "desktop effects could not be enabled" and the screen flashes a second time.

I have no idea where to go to enable compiz? I have it installed and I can play with the Compiz Config settings manager but I cant get the effects to show up.

Can some body point me in the right direction? If I go back in the tutorial and try the trouble shooting made for 8.10 will that work? Soo lost...


BTW everything else is working just the same before i upgraded except for the whole graphics issue...

---

### Post by HunterThomson on 2009-04-24
> **PhilMize said:**
> K so first off thanx again hunter for your help with the alsa drivers...


Upgraded to Jaunty like 30min ago and im having issues with getting compiz to work. When I go too the appearance tab under preferences and set the effects to extra it says "searching for available drivers", the screen flashes and then a window pops up saying "desktop effects could not be enabled" and the screen flashes a second time.

I have no idea where to go to enable compiz? I have it installed and I can play with the Compiz Config settings manager but I cant get the effects to show up.

Can some body point me in the right direction? If I go back in the tutorial and try the trouble shooting made for 8.10 will that work? Soo lost...


BTW everything else is working just the same before i upgraded except for the whole graphics issue...

Compiz alwas gives me a headache. I am happy to say that it now works with the intel chipset no problem i.e. no VLC problem. (or at lest did on my laptop with 8.10) It seemed to me that using the appearance tab under preferences (the one you get from right clicking the Gnome Desktop) Messed things up. I found it was better to use the "Compiz Icon" wich is it's own application you can find in the "Add Remove" application. Try uninstalling compiz, Then delete the config file wich can be found in your home folder... Something like /home/user/.compiz or like /home/user/.config/compiz .. maybe /home/user/.gnome/compiz.... Anyway get rid of that then install compiz then the settings manager then "Compiz Icon". Use the "Compiz Icon" to turn it on/off. 

What you are describing sounds just like what use to happen to me way back in 7.10 when it didn't work with the intel driver. If you have a ATI or Nividia card then make sure you have the drivers installed for that card. Ubuntu should have given you a pop-up after install telling you there are proprietary drivers avalabel for install.

But, you mite get more help starting a new thread. I don't know that much about compiz. Like I said it gives me a headache and I don't use it. I used it for a cuple weeks then got over it. I like to keep my system clean and slim. Compiz works wonders when you show your laptop to a Windos user though ;) Then go on to talk about how Linux is far faster/secure/FREE.

---

### Post by wyth on 2009-04-24
There is a known bug with Intel graphics cards.  A fix is in the works, but it won't be ready for a little while, so there are some work-arounds.  This may be the problem (can't tell, haven't upgraded yet).

See the [release notes on the problem here]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards"), and [this thread]("http://ubuntuforums.org/showthread.php?t=1130582") for some more tweaks.

---

### Post by PhilMize on 2009-04-24
K so I tried un-installing compiz and the config file and reinstalled. I can open the compiz setting manager just fine and edit all the settings but without the effects being enabled under the appearance setting none of the compiz effects are used. So unless theres another method of enabling the effects other then system>preferences>appearance>visual effects, I don't know what to do aboot getting this to work. I'll start another thread I guess, but I'm thinking this is more of an issue with the y510 cause my buddy went jaunty and his compiz works dandy... I did get the option when I finished installing to use the proprietary drivers and everything is up too date. It's so early in the release though, I'll just wait it out till somebody figures it out.:guitar:

---

### Post by PhilMize on 2009-04-24
I got it to work!!! It was totally random too!:guitar::lolflag:

K so after uninstalling compiz and deleting the config file I reinstalled Compiz and also installed the compiz icon. If you go to the appearance tab and try to enable the effects through that, its going to give an error message. If you Turn on the compiz icon so it shows up in the task-bar and right click on it, go to compiz options and make sure you have both Loose Binding and Indirect Rendering checked. You should see a the screen flash. If you upgraded to 9.04 like I did all your old compiz settings should reappear.

---

### Post by myagaa on 2009-04-24
Hello everyone. I have been installed Ubuntu 9.04 Jaunty. 
  But sound card have some problem. I configured alsa driver by:::
 options snd-hda-intel model=lenovo-ms7195-dig
Sound is good working. But if i plug-in headset Speaker working together...
  How to solve? plz help me

---

### Post by chargersfan420 on 2009-04-24
@ HunterThomson - Thanks for the suggestion with fstab.  It's really not necessary tho, because it's not the first time that i plug in the card with each boot, it was the first time PERIOD.  So it's not really an issue.

@ PhilMize - I was going to suggest trying System - Administration - Hardware Drivers.  This is where i have to enable the proprietary fglrx driver for my Y710 (and i have to do this and reboot before i can enable "extra" visual effects in appearance)... but if you got it working, good.

Speaking of the proprietary driver, i did something stupid the other day.  I was playing around with settings, and for some stupid reason, i decided to invert my display (so it was upside down).  This crashed my proprietary driver, and eventually my whole system.  I could only get an inch of artifacts across the top of the screen, and i was unable to fix it from command lines... i reinstalled and re-used my /home partition, but the problem was still there.  I learned my lesson that day not to push the proprietary driver to the limits...

Anyway, on to more important stuff.  I've been keeping an eye on my battery charge levels and also have been tinkering with my DSDT lately, and i noticed a couple of odd things.  Just because we cleared up all of the error messages from compiling it with the Intel compiler doesn't mean it is fixed.  For example, i found in the ACPI specs that the fan is supposed to have a plug n play ID of PNP0C0B, and typically be listed as _AC1 or FAN0 or something like that.  It seems that there is no such listing in my DSDT for my fan.  I have never seen it run in Ubuntu, and i am not sure if it ever runs in Vista, either.  The only time i hear the fan spin is when i first power on the machine.

The other thing is that the battery will only charge to 99% every time.  I use Conky (which uses ACPI battery information) and it always reports the battery as "charging xx%" until it hits 99%, and then it switches to "unknown 99%".  The results from:
cat /proc/acpi/battery/BAT0/state      and
cat /proc/acpi/battery/BAT0/info
always show the charge stalling out and wavering at different levels of "present rate" and the "last full capacity" goes down just a little bit every time i switch to battery power and then back to AC power.  I think there might be something wrong with the DSDT in that it doesn't seem to fully charge the battery properly... or is this somewhat normal...?

Also, in Conky i turned on the "acpifan" variable, but it returns "no fans?".  /proc/acpi/fan/ does exist, but it is an empty folder.

So, I put forth these questions to Y510 users:
- does your fan ever run in Ubuntu?
- if you do a search of your DSDT, do you see any results for PNP0C0B?
- does your battery get back to its "last full capacity" after a recharge or does it stop short?
- if any of you are using Conky, do you see a value for the variable "acpifan", or a "battery" value of 100% ever?

Also, just fyi, i found some good info on DSDT fixing in the following links.  Nothing too specific or comprehensive, just a couple of people that managed to repair theirs on other laptops.  For example, one link says that _T_0 and other _T_(x) numbers will work properly if you simply remove the first underscore (_T_0 becomes T_0) and this seemed to work for me too.  Here are some links:
[[COLOR="Blue"]http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt-2.html[/COLOR]]("http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt-2.html") 
[[COLOR="Blue"]http://www.openlaptops.org/index.php?topic=195.0[/COLOR]]("http://www.openlaptops.org/index.php?topic=195.0")
Crap, there was another good one i found i didn't bookmark.  Anyone new to DSDT fixing, here is the best how-to i have found:
[[COLOR="Blue"]https://help.ubuntu.com/community/ACPIBattery[/COLOR]]("https://help.ubuntu.com/community/ACPIBattery")

---

### Post by chargersfan420 on 2009-04-24
oh, and

@ myagaa - if you go into your Volume Control menu, you can mute your speaker channels and just get sound to the headphones.  I use the model=6stack-dell (for my Y710) and i notice the "surround" channel (on the 8-ch mode) will control the volume of my headphones.

I think many, many pages ago someone had written a script to mute the speakers automatically when headphones are plugged in, but i actually like it better the way it is.

---

### Post by HunterThomson on 2009-04-25
PhilMize: I don't meen to sound rude but I just have to say...
"Thats what I told you, Use the "Compiz Icon" not the settings manager to turn on/off compiz." I am sorry I just had to say that. It was just hurting my brain. 

Also, the Compiz Intel thing is fixed right now. There is no need for work arounds. It works with video and games and all. But, I would still turn it off befor playing a game so you don't wast CPU/GPU time. (Keep in mind that all that stuff you have running on your desktop Stays running when you pay a game and stuff.)

Chargersfan420: My battery is reading "unknown 95%" in conky right now. If I discharge it to say below 90 then charge it with the laptop OFF it will charge to 100% but then drop down to say 95 after using it for a bit on AC. I think it is a cuple things. First, I bet it lets it get discharged a bit before it charges it back up to 100 to save on charg/discharge cycals. Second, I also think that my battery is just getting old and can no longer hold a full charge.

My fan directory is empty too. However, my fan works. Wach the temp if it gets above say 55-60C and the fan still is not turning on then you do have a poblem. If you ask me though I bet your fan is working just fine. It could just be under normal use your laptop stays cool enugh so the fan has no nee to turn on. But, put it under hevy load wach the temp and see if the fan turn on.

As for DSDT/BIOS in genoral, All computers BIOS are buggy as all hell. This is do to a few resons.

1. Most comptuer makers use the non standards compliant microshaft compiler. Bla bla you know.

2. There are like only two companys that make BIOS so they do a crappy job do to the lack of compition. Same as the case with micro$oft and there fisher price quality toy thing OS and software.

3. They simply do not care if your computer works right. It costs them more money to bring the BIOS out of alfa quality.

You can and arguably should recomplile your DSDT with the standards compliant Intel compiler and fix the errors that the M$ compiler delibritly dosen't flag. (such as starting a varable name with and "_" you can never start a varable name with and "_" in AML) But I have read it is best to leave the DSDT alown unless your trying to fix a problem.

With that said there are lots of cool things you can do with BIOS hacking. I read one guy wrighting some code so he can make use of the harddrive's excelerometer in aplications. Lots of cool stuff... The BIOS is the hardware level OS after all.

There is also an Open Source BIOS project called "CoreBoot". It is built on the Linux Kernel and mind blowingly cool ! They only have written BIOS for a slect few motherboards but there good borads. You sould read up on it. It is plugin based so you can 'Roll your own BIOS'. Way freeking cool. You can have it give you a BusyBox Shell on the hardware level in less then 4 sec's!!! Customized BIOS for Linux and all kinds of cool stuff. Dude for real, the next time I buy a motherboard I will make sure it is one they support. Realy if you don't see the potental in this you have to read up on it. I have trubble sleeping after thinking about it :lolflag:

[http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)

---

### Post by myagaa on 2009-04-25
> **chargersfan420 said:**
> oh, and

@ myagaa - if you go into your Volume Control menu, you can mute your speaker channels and just get sound to the headphones.  I use the model=6stack-dell (for my Y710) and i notice the "surround" channel (on the 8-ch mode) will control the volume of my headphones.

I think many, many pages ago someone had written a script to mute the speakers automatically when headphones are plugged in, but i actually like it better the way it is.
  tnx for reply.
 i checked headphone. If i plug-in headset speakers are off. Surround and Center speaker working... Left and right's speakers are off...

---

### Post by PhilMize on 2009-04-25
> **HunterThomson said:**
> PhilMize: I don't meen to sound rude but I just have to say...
"Thats what I told you, Use the "Compiz Icon" not the settings manager to turn on/off compiz." I am sorry I just had to say that. It was just hurting my brain. 


lol its cool yea that was my bad... Though I've been having a slight issue with compiz not showing the menus correctly. 

Example:
[IMG]http://farm4.static.flickr.com/3311/3472986245_9b04888a3c.jpg?v=0[/IMG]
It sits like that and doesnt show up at all.

---

### Post by JSuresh on 2009-04-25
Are the only problems with 9.04 on the Y510 compiz and sound?  Are brightness, webcam, card reader working out of the box?

---

### Post by PhilMize on 2009-04-25
> **JSuresh said:**
> Are the only problems with 9.04 on the Y510 compiz and sound?  Are brightness, webcam, card reader working out of the box?

well out of the box sound still is crappy just follow the guide in this thread and use the sky lenovo driver and the sound will be working fine.

webcam is upsidedown still

microphone works but u gotta play around with the settings some

card reader works

brightness isnt backwards for me works just fine

and yes 9.04 boots from grub dual boot menu to login menu in 17sec

---

### Post by wyth on 2009-04-25
**Compiz**
Okay, so the Intel chip that comes with many Y510's is blacklisted by compiz.  On top of the fixes/pages noted above, you could try 
```
 mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` That didn't do it for me, but the following has gotten compiz up and running on boot:

[LIST]
[*]in /etc/X11/xorg.conf, added the following under Section "Device"
[/LIST]
```
    Option         "EXAOptimizeMigration" "true"
    Option         "MigrationHeuristic" "greedy"
```
[LIST]
[*]In System > Preferences > Start Applications, under the Startup Programs tab,
[LIST]
[*]Add a new entry
[*]Name: Name it Compiz or Bloody Mad Groundhogs whatever you like
[*]Command: compiz --replace
[*]Comment: Set compiz to start on boot, Bael is NOT an Anatolian God, or whatever you like
[*]Save
[/LIST]
 
[/LIST]
When you reboot, compiz --replace will automatically run when you log in, and compiz will work again.  It adds a little time to your boot, but  so it goes.

Intel is working on a new version of the driver, I guess.  You can try using it if you're adventurous; instead of the EXAOptimizeMigration and MigrationHeuristic options in /etc/X11/xorg.conf, add
```
    Option         "AccelMethod" "UXA"
```There are reports of instability with UXA, and I guess suspend doesn't yet work for some, but I've not tried that.   I only played with UXA for a short while, and didn't notice any particular difference, but I hadn't yet had compiz fixed, so I wasn't looking for those sorts of things.

Some report UXA is a lot nicer on their cpu's.  Right now, with EXA, I'm floating between a 3%-12% cpu hit. 

There are also some launchpad ppa's for backported and bleeding-edge Intel drivers.  The X Updates are labled stable, although I haven't tried them yet.

[LIST]
[*][X Updates: The stable backported drivers]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")
[*][Xorg Crack Pushers: The bleeding edge drivers]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa") (not necessarily stable)
[/LIST]
*EDIT: I added the X Updates ppa and booted again WITHOUT compiz added to the Start Applications -- compiz didn't start.  So the drivers may work better, but it seems compiz in Start Applications is still necessary.*
[B]

Sound[/B]
I don't really know what to say about this, because later versions of the Y510 came with different guts -- different sound cards different gfx cards, etc.  All I can say is that for the first time ever, it updated/upgraded and my ALSA sound worked with the surround and everything right out of the gate.

---

### Post by HunterThomson on 2009-04-26
PhilMize: Aw yes I forgot to mention that... If you use the lenovo-sky module that will solve your headphone/speaker-mute problem. I am glad you solve the problem.

I don't know about the menu problems. That's why compiz gives me a headake. There are all these little problems and junk. I spent hr's tuning it and still little problems here and there. If you go into the "compiz settings manager" and into advanced there are is a "Work around" thing if I remember right. There are all kinds of settings scattered all over the place that mite fix the problem ( like the "Compiz Icon" thing). I can't justify spending my time on compiz when all it realy dose is slow my system and mess things up. But, it dose look cool... to each his own.

chargersfan420: About the fstab entry for your SD-card... Did you try it? Adding an fstab entries solves a lot of mount problems it is not just for automounting at boot. I realy think it will solve your problem. I think it will make it easyer for the system to find the drive on the first pass.

Like with me, The first few times I installed Archlinux I had problems even getting a CD to mount. I would have to add a lot of lines of code to Xorg config files inorder to get it to work. This is the proper way of setting it up to mount CD's, SD cards and USB sticks. However, it is a real pain and a bit of work. Now all I do is add entries to /etc/fstab. Then all is well no errors and no Xorg.confg editting. I also set user permitions for any media that is in that location i.e. cdrom and set automount or not.

Wyth: Realy, Compiz works fine with my intel X3100 ? I have to use the "Compiz Icon" to tun it on though. If I use the "Gnome setting manager" it messes things up. I was useing Ubuntu 8.10 when I was using compiz. I didn't have to do anything just out of the box. And yes compiz didn't work in 7.10. I don't think I tried it in 8.04. In 7.10 I could get it to work with some editing but it would mess up my video's in VLC and would mess up games. In 8.10 it just worked so I thought it must have been fixed. I never would have found out but I installed Ubuntu on a friends laptop with and Intel GPU. He had me fix a problem he was having and I noticed that he had Compiz running just fine.

---

### Post by Sapfeer on 2009-04-26
Hello there

Recently I've installed Ubuntu 8.10 on my Y510 and I faced with some issues: after login brightness is reset to minimal value and I have to increase it to comfort level and WiFi indicator always showing that WiFi is On even if it turned Off... Is there a way to solve such problems?..

---

### Post by BlueCanary9999 on 2009-04-26
My sound at maximum volume is low.  Is this a problem with the speakers, or is one of my settings off?  Sorry if this is a nooby question, but will the same fixes mentioned earlier for the Y510 working with my Y530?  I'm using Jaunty, btw.

---

### Post by HunterThomson on 2009-04-27
Sapfeer: Well the brightness problem is fixed in the new Linux Kernel. You will have to install 9.04 so you are using the new Kernel.

As for the wifi light and I don't think the swich works ether... I just don't care. It is a problem with the BIOS not the DSDT file but.. anuther one that I can remember the name to that maps the hardware keys. No one has fixed the problem that I know of.

BlueCanary9999: Ya you have 4 speakers and a sub, Right? Then yes you have to do the alsa sound set up on page one of this thread. Though I should edit it becaus we don't have to install the newest ALSA stuff. That is relic code form Ubuntu 7.10 days. The default vertion of ALSA that comes with new vertions of Ubuntu have the sound modules we need. You just have to do this...

Edit the alsa-base file:

```
sudo nano /etc/modprobe.d/alsa-base
```

Add this line to the bottom of it:

```
options snd-hda-intel model=MODEL
```

Or mabe that file is created when you install alsa form source. You mite have to add that like to this file:

```
sudo nano /etc/modprobe.conf
```

___All of that mite just confuse you or I mite just be wrong. If so then just folow the guide on the first page of this thread. However, you still need to do the following....

((Edit: I edit'ed the Alsa setup guide on the first page of this tread to enclude these steps but I just feel like leaving them here too))

Then you will want to set up the default sound settings by doing this...

Open a shell and swich to the root user:

```
sudo su
```

Then set the sound up to the way you would like it at startup:
(Hint, make sure headphone is NOT muted, Frount to 100%, Surround 100%, Center 100%, LFE 100%, Side 100%, and I like to have Master set to 50% at startup.)

(Hint, use the arow keys and the "Esc" key to exit)

```
alsamixer
```

After exiting the Alsamixer, run this command to save your sound settings:

```
alsactl store
```

Then reboot:

```
reboot
```

---

### Post by chargersfan420 on 2009-04-27
@ Sapfeer / HunterThomson

I can't be much assistance here, but i can confirm that the wireless switch on the front of the Y710's has functioned properly since 8.04 (possibly earlier, this is the earliest Ubuntu i have tried on the Y710).  I still see occasional error messages pointing to wireless ("iwlagn") when shutting down, but i have no complaints with its operation...

@ BlueCanary9999 / HunterThomson

BlueCanary, one thing you should check for is that sound is coming out of ALL of your speakers.  This is probably a model setting issue.  HunterThomson is partially right - in Jaunty, it seems that they're setting a more strict standard on naming configuration files with the .conf extension.  So, before jaunty, it was
/etc/modprobe.d/alsa-base
and now it is:
/etc/modprobe.d/alsa-base.conf
And also, if you're new to Ubuntu, for simplicity, use gedit instead of nano, it's just easier to edit text documents in a text document editor instead of a terminal program.  

So, in conclusion, type:
```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```
(also, use tab to auto-complete, and to verify the file exists - it's how i found the .conf extension)
Add this line to the bottom of the file:
```
options snd-hda-intel model=MODEL
```
Where MODEL = lenovo-sky (for Y510's) or 6stack-dell (for Y710's) (there are other options, see earlier posts)
And then reboot and go into volume control, set channel mode to 6-channel (for Y510's) or 8-channel (for Y710's), and unmute the appropriate channels (Center, Surround, LFE, Side, Front, Master) and you sound should be good...

I find it nice to leave the Side and Front channels a little lower in order to get more bass out of full volume too, but that's just me.

@ Wyth / HunterThomson / anyone, really

I'd like to get a copy of a DSDT.dsl (COMPLETELY UNMODIFIED) from a Y510 owner, just so i can compare it to my original DSDT from my Y710.  I'm going to print it out and compare entire code blocks and see what we do and don't have in common.  For example, say you guys can't use your wireless switch, but i can.  Maybe i have a block of code for that that you guys don't.  Maybe i can't use my fan but you guys can... i think you see what i'm getting at... It's probably the most similar laptop out there to what i have, so a thorough comparison might be helpful... or interesting...

---

### Post by BlueCanary9999 on 2009-04-27
Thank you, you two... but I think I messed up somewhere.  I followed chargersfan's instructions to add the options model line to /etc/modprobe.d/alsa-base.conf.  Originally I went with lenovo-sky even tho I have a Y530, not Y510.  After rebooting, the sound worked.  Unable to fnd the channel mode in Volume Control (my only options are Device and sliders), I switched to HunterThomson's instructions and fiddled with alsamixer.  But I didn't see any vertical bars for Surround, Center, LFE, or Side, so I reset the bars to where I think they were originally and stopped....  Back to chargersfan's instructions, I started trying different models, going by this list:
> &#8227; 3stack-6ch
&#8227; 3stack-6ch-intel
&#8227; lenovo-101e (Lenovo 101E)
&#8227; lenovo-nb0763 ( Lenovo NB0763)
&#8227; lenovo-ms7195-dig (Lenovo MS7195)
&#8227; lenovo-sky (Lenovo Sky)
&#8227; auto (Gets the information from BIOS)
None of them work, including lenovo-sky now....  The speakers crackle instead of playing music or whatever.  The same happens if I omit this line.  Maybe I reset the alsamixer vertical bars wrong?  Here's how they're set now:
[http://img54.imageshack.us/img54/6092/alsamixer.png](http://img54.imageshack.us/img54/6092/alsamixer.png)
Are those levels correct?  Or did is something else messed up?  Sorry about this....

Btw, where do I set channel mode in Volume Control?

---

### Post by chargersfan420 on 2009-04-27
@ BlueCanary9999

For the channel mode, try this:
1.  Go to the Volume Control panel.  Make sure the device selected is "HDA Intel (Alsa mixer)"
2.  At the bottom, next to the "Close" button, there should be a "Preferences" button.  Click on it.
3.  Checking off these preferences will add more controls to your Volume Control panel.  If you're like me, you want to see ALL of the options, so check off everything.
4.  Once this is done, you should notice that the sliders are on a "playback" tab.  I also have the following other tabs:  Recording, Switches, Options, Sound Theme.  Click on the "Options" tab.
5.  There should be a "Channel Mode" selection on this "Options" tab.  With lenovo-sky, you should be able to choose between 4ch and 6ch, and with 6stack-dell, between 6ch and 8ch.

Does this help?

Edit:  Sorry, should have been paying more attention.  If the original lenovo-sky doesn't work anymore, you might need to recompile alsa, following the instructions at the beginning of this thread :(   I'm not well versed in the alsamixer controls, so it might be fixable, i just don't know what to tell you...

Another Edit:  Sorry, i REALLY should have been paying attention.  I think you might need to set the PCM volume in alsamixer to full to get any sound... Muting the PCM channel on mine does the same thing as muting the master volume.

---

### Post by wyth on 2009-04-27
> **HunterThomson said:**
> Wyth: Realy, Compiz works fine with my intel X3100 ? I have to use the "Compiz Icon" to tun it on though. If I use the "Gnome setting manager" it messes things up. I was useing Ubuntu 8.10 when I was using compiz. I didn't have to do anything just out of the box. And yes compiz didn't work in 7.10. I don't think I tried it in 8.04. In 7.10 I could get it to work with some editing but it would mess up my video's in VLC and would mess up games. In 8.10 it just worked so I thought it must have been fixed. I never would have found out but I installed Ubuntu on a friends laptop with and Intel GPU. He had me fix a problem he was having and I noticed that he had Compiz running just fine.

The X3100 *is supposed* to work out of the box, but not yet -- with the next kernel.  Using Compiz Fusion will override the Visual Effects issue, as will the other stuff mentioned.  It's just because Compiz has this and a few other Intel chips blacklisted until Intel gets the driver stabilized and out (UXA).  

For whatever reason, I've found that adding the little compiz --replace at startup took care of having to fire up Compiz Fusion, although it adds a few seconds to getting to desktop.  (Running compiz --replace basically does what reloading the desktop manager does in Compiz Fusion.)  

I've noticed Firefox is a little natty with the current Jaunty kernel, but everything is a little smoother and faster with the other kernels.  I'm still messing with it a bit.

---

### Post by meatlover on 2009-04-27
I have a Lenovo Ideapad Y530 model 2PU.  I have managed to get everything working, except for suspending/resuming.

Relevant information about my computer

Graphics Card: Nvidia Geforce 9300M
3gb ddr3 ram
Partition with windows vista
Nvidia driver from the Nvidia website
Compiz Running
Ubuntu 9.04 32bit

When I suspend to ram, my computer suspends quickly and turns the screen off, then in less than a second, it resumes into a blank screen with a blinking cursor.  All keys are locked and no combination works, including the alt + sysrq + r etc. keys.  I checked pm-suspend log and it says it is working correctly:



```
Initial commandline parameters: 
Mon Apr 27 17:43:08 PDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux computer-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nvidia               7236444  45 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
arc4                    9856  2 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                    10752  2 
uvcvideo               63240  0 
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
compat_ioctl32          9344  1 uvcvideo
soundcore              15200  1 snd
psmouse                61972  0 
sdhci_pci              15232  0 
mac80211              217208  2 iwlagn,iwlcore
pcspkr                 10496  0 
serio_raw              13316  0 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
video                  25360  0 
asus_laptop            24440  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
sdhci                  23940  1 sdhci_pci
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
led_class              12036  2 iwlcore,asus_laptop
cfg80211               38032  3 iwlagn,iwlcore,mac80211
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       2546444    1595692     950752          0     787744     328480
-/+ buffers/cache:     479468    2066976
Swap:      7462152          0    7462152
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Mon Apr 27 17:43:09 PDT 2009: performing suspend

```

Everything seems to be normal in the Syslog at the exact time I call suspend:

```
27 17:43:08 computer-laptop anacron[6361]: Anacron 2.3 started on 2009-04-27
Apr 27 17:43:08 computer-laptop anacron[6361]: Normal exit (0 jobs run)
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  Sleeping... 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): now unmanaged 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): cleaning up... 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): taking down device. 
Apr 27 17:43:08 computer-laptop avahi-daemon[4252]: Withdrawing address record for fe80::224:8cff:fe6f:3496 on eth0.
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): now unmanaged 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5056 
Apr 27 17:43:09 computer-laptop kernel: [ 4106.673141] wlan0: disassociating by local choice (reason=3)
Apr 27 17:43:09 computer-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Withdrawing address record for 192.168.1.101 on wlan0.
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  (wlan0): cleaning up... 
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  (wlan0): taking down device. 
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Withdrawing address record for fe80::222:faff:fe48:f8ce on wlan0.
Apr 27 17:43:09 computer-laptop postfix/master[3954]: reload configuration /etc/postfix
```

However, I believe it may be Nvidia related based on the following messages in the syslog (immediately after hard reboot):

```
27 17:52:04 computer-laptop kernel: [   59.816120] Corrupted low memory at c000fcf4 (fcf4 phys) = 83840000
Apr 27 17:52:04 computer-laptop kernel: [   59.816125] Corrupted low memory at c000fcf8 (fcf8 phys) = 0010000a
Apr 27 17:52:04 computer-laptop kernel: [   59.816132] ------------[ cut here ]------------
Apr 27 17:52:04 computer-laptop kernel: [   59.816135] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
Apr 27 17:52:04 computer-laptop kernel: [   59.816137] Memory corruption detected in low memory
Apr 27 17:52:04 computer-laptop kernel: [   59.816139] Modules linked in: nvidia(P) binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn iwlcore snd_seq uvcvideo snd_timer snd_seq_device compat_ioctl32 mac80211 psmouse intel_agp sdhci_pci snd soundcore videodev serio_raw agpgart iTCO_wdt ricoh_mmc video sdhci pcspkr asus_laptop snd_page_alloc v4l1_compat cfg80211 iTCO_vendor_support output led_class ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
Apr 27 17:52:04 computer-laptop kernel: [   59.816198] Pid: 0, comm: swapper Tainted: P           2.6.28-11-generic #42-Ubuntu
Apr 27 17:52:04 computer-laptop kernel: [   59.816200] Call Trace:
Apr 27 17:52:04 computer-laptop kernel: [   59.816204]  [<c0139ab0>] warn_slowpath+0x60/0x80
Apr 27 17:52:04 computer-laptop kernel: [   59.816208]  [<c013a2f9>] ? release_console_sem+0x1c9/0x200
Apr 27 17:52:04 computer-laptop kernel: [   59.816213]  [<c015aee3>] ? tick_dev_program_event+0x33/0xc0
Apr 27 17:52:04 computer-laptop kernel: [   59.816216]  [<c0500ac6>] ? printk+0x18/0x1a
Apr 27 17:52:04 computer-laptop kernel: [   59.816219]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816223]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816226]  [<c0143b00>] run_timer_softirq+0x130/0x200
Apr 27 17:52:04 computer-laptop kernel: [   59.816229]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816232]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816236]  [<c013f197>] __do_softirq+0x97/0x170
Apr 27 17:52:04 computer-laptop kernel: [   59.816239]  [<c0106f30>] ? timer_interrupt+0x30/0x80
Apr 27 17:52:04 computer-laptop kernel: [   59.816242]  [<c013f2cd>] do_softirq+0x5d/0x60
Apr 27 17:52:04 computer-laptop kernel: [   59.816244]  [<c013f445>] irq_exit+0x55/0x90
Apr 27 17:52:04 computer-laptop kernel: [   59.816247]  [<c0106853>] do_IRQ+0x83/0xa0
Apr 27 17:52:04 computer-laptop kernel: [   59.816250]  [<c01051f3>] common_interrupt+0x23/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816253]  [<c0319417>] ? acpi_idle_enter_bm+0x269/0x2b8
Apr 27 17:52:04 computer-laptop kernel: [   59.816257]  [<c040f4df>] cpuidle_idle_call+0x6f/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816260]  [<c010285d>] cpu_idle+0x6d/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816263]  [<c04f110e>] rest_init+0x4e/0x60
Apr 27 17:52:04 computer-laptop kernel: [   59.816265] ---[ end trace 512babe2d9f27f83 ]---
```


As a side issue, any idea what the memory corruption is?  I've seen this on other Y530 Ideapad's but the issue was never resolved.

---

### Post by HunterThomson on 2009-04-28
[SIZE="3"]Wow[/SIZE] what a that was scarry !

I was concerned about problem with lowmem coruption in the Y530. So I went to the lenovo sight to see what the newest BIOS is for the Y530. But, sents I have a Y510 I just checked up on the Y510 first. There is a new BIOS for the Y510 it is 06CN33WW.ROM but there is no BIOS upgrade for the Y530.

Now to the scarry part. I upgraded to the new 06CN33WW.ROM from 06CN31WW.ROM. Then when I rebooted the screen whent dim as soon as ACPI loaded :( I even jumped the gun and stared posting up here not to upgrad to the new BIOS do to it bringing back the backlight problem. However, I just rebooted agin and the backlight stayed bright so I think all is well.

It seems like Lenovo got smart or maybe they were listening to us Linux useres. Now are posting .ROM files insted of .EXE files. So, Up grading the BIOS is a snap. Just download the .ROM file and put it on a USB Stick. Then reboot > Enter the CMOS Setup by hiting "F2" at the POST > go to the "Boot" tab > then Hard Drive solection and move the USB stick to the first Harddrive posisiton > then find the tab with the IDE settings and you will see a "Easy Flash Utility" Option > arow down to the "Easy Flash Utility" and hit the Enter Key > Then in the flash program arow down to the C: drive and hit the Enter Key > Then you should see the 06CN33WW.ROM file pop up in the big box to the right > then hit start flash.

((TIP: I downloaded the .ROM file two times and saved one copy to one USB stick and the other coppy to a second USB sick. That way if anyting gos wrong I have a difrent coppy))

So, Far so good but I have not checked for things in the Log files yet but the backlight is fine and I have 8 steps of brightness. My WiFi swich now turns the blue LED on/off ((for some crazy reson xev is not working for me so I don't know if it is now maped or not))


[http://consumersupport.lenovo.com/en/DriversDownloads/drivers_show_1044.html](http://consumersupport.lenovo.com/en/DriversDownloads/drivers_show_1044.html)

---

### Post by HunterThomson on 2009-04-28
BlueCanary9999: From the looks of it your Y530 has the same chipset as my Y510 "Realtec ALC888". So, you should do the same as all the Y510 users do for sound. I sugjest the lenovo-sky it defaults to 6-channels and has no problem with the headphones. 

Also, form the looks of it ether you added...

```
options snd-hda-intel model=lenovo-sky
```

To the /etc/modprobe.d/alsa-base.conf with a typo or you Ubuntu users realy do still have to install the ALSA stuff form source.

Make sure you have it all typed in correctly ((Just cut and past)) and make sure you have one empty line at the end of the file.

You will know the model is set correcty if you have the Suround, Center, LEF,... stuff there in the terminal alsamixer ((The one you have pictured)) Keep useing the terminal alsamixer and NOT the Gnome ALSA mixer untill all is well. It will show all the avalabe options. The Gnome ALSA mixer will not show them untill you tell it too as chargersfan420 has said. The Gnome one is a pain in the ***.

Yes chargersfan420 is right your sound is crappy becaus sound is only comming out of the two speakers by the monitor as you have it right now. That is why it is so quiet.

Ya, feel free to edit the /etc/modprobe.d/alsa-base.conf file with "gedit" if you like.

If you check/fix the /etc/modprobe.d/alsa-base.conf file and you still don't have the Suraound, Center, LEF,... stuff in then ALSA mixer then go to page-1 of this thread and follow the instructions word for word(( Just Cut & Past)) but you can skip the step to see all the avalable options for the "modle" just use the lenovo-sky one.

You should have no problem but if you do just report back here. We will help you no problem :)

Meatlover: Well I can tell you right now the suspend problem is a problem with ACPI which is caused by a problem with the BIOS file DSDT. 

I supose anything is posable but I don't think that the problem is related to your video driver. If that was the case then you would have problems like... "When your computer comes out of suspend you get artifacts on the screen or some other strange video problem".

Suspending to RAM is a common come and go problem with all laptops. This is agin do to computer manufacturers using the non-standards compliant M$ compiler. Just bill shafting us with his MicroShaft agin. 

There are several things that could solve your problem. Like recompileing the DSDT with the Intel AML compiler and fixing all the errors it finds. If that dosn't do it ((& it probaly will not maybe don't even mess with it)) there are a few other programs that will put your computer into Suspend and have a fair chance of working. Try googleing to see how other people on other laptops have fixed this problem.

Like...

```
"suspend" "fixed" sight:ubuntuforums.org
```

As for the lowmen corruption :|

That is a problem you should keep and eye on. See what you have to do to see that error. Like dose it show 'Every' Boot? If it dose happen every boot then it is agin a problem with the BIOS ](*,)
I would keep an eye on it do some reboots and see what you have to do to get the corruption.

However, At the end of the day your computer works, Right? Well then we are just over analyzing the problem. Wate for a BIOS update and see what happens. You will also want to head on over to the Lenovo forums or email lenovo and inform them of the problem. This is 90% doubt free that it is a BIOS problem. The BIOS maps the memory NOT Linux so if there is corruption......
Well come to think of it you could just have bad RAM. Try running Memtest86 from the Ubuntu Live CD. Heck this could also be caused by a bad Power suply or dirty electricity.


FYI- I am not that smart or knolageable. I just talk alot.

---

### Post by chargersfan420 on 2009-04-28
@ HunterThomson / anyone

My request in a recent post for an UNMODIFIED copy of a DSDT from a Y510 may have been overlooked because i tucked it into the bottom of a post.  HunterThomson, can you help me out here?  It would also be cool if i could get a pre-BIOS upgrade copy and a post-BIOS upgrade copy, if you still have a copy of the old one...  I wouldn't mind looking at a copy of one from a Y530 or a Y730 if anyone is willing to donate one...

@ meatlover

I would suspect the issue lies somewhere between your graphics driver and your BIOS / DSDT table.  When i stated earlier that i crashed my system after flipping the display upside down, i realized later that i was playing with hibernate / suspend shortly before doing that and it may have had something to do with it.  I also modified my DSDT to allow Linux to use Vista's settings, and one thing i noticed with this is that the BIOS screen will now say "System Resuming", when i resume from hibernate... it throws me into the bootloader shortly afterwards, and then goes through a somewhat normal boot process, throwing a few errors in dmesg output, showing some artifacts on the screen, and then returning to my desktop with my programs still open.

Here is the dmesg output i see while hibernating and resuming from hibernate:
```
[ 2146.745115] mmc0: Controller never released inhibit bit(s).
[ 2146.755114] mmc0: Reset 0x2 never completed.
[ 2146.948007] mmc0: Reset 0x4 never completed.
[ 2146.954104] mmc0: Controller never released inhibit bit(s).
[ 2146.964102] mmc0: Reset 0x2 never completed.
[ 2146.964102] mmc0: Reset 0x4 never completed.
[ 2147.162917] mmc0: Reset 0x1 never completed.

```
the first 3 lines are repeated 11 times, followed by the "Reset 0x1" line at the very end.  No idea what the problem is here, but apparently the mmc0 is my card reader.  And no, Hunter, I didn't add it to fstab.  I keep the card reader slot filled with a SD to Micro-SD adapter, and the only card i use with it is the one in my Blackberry, for putting music on my phone.  I've only used the card reader maybe 5 or 6 times, it's not a regularly used feature of the laptop.

The last time i tried suspend, the machine just hung and i had to kill it.  I could see hibernate being a useful feature, but i don't think i'd have much use for suspend.

I could be wrong about this, but i think that it may not hibernate at all without the "vista modification" of the DSDT, or at the very least, the patching of the errors in it... I could try the original DSDT and see if i can hibernate...

EDIT: @ meatlover
Brain not fully functioning this morning.  I had a look at your logs, and i don't know if you can blame your graphics driver.  I've been quick to blame mine a few times (for being an ATI - it seems to me that nVidia is more Linux-friendly), but it seems to me that it's more likely a BIOS / DSDT problem.

I think that the DSDT may be coded incorrectly for the release / resuming of the graphics driver with mine, and possibly yours too.  However, i should state for the record that i am no expert... but i would like to learn more about DSDT coding.

Oh, and while i'm at it, @ HunterThomson - thank you very much for the link to CoreBoot.  Haven't had time to check it out, but it sounds awesome, and when i eventually build my super-computer desktop, i will be making sure to buy a mobo with an excellent BIOS for Linux functionality.

---

### Post by chargersfan420 on 2009-04-28
Here's another odd thing:
Before hibernating, i see an entry in Powertop that says:
<interrupt> : fglrx[0]@PCI:1:0:0     

This shows up exactly 60 times per second, every single time.  To me it makes sense, because the monitor refresh rate is 60 Hz.

After hibernating, this entry is completely missing.  Monitor is working, but not registering interrupts with powertop???

I guess this leads me to 3 (rhetorical?) questions:
1.  Should it be there to begin with?
2.  Why is it gone?
3.  Am i going to crash my graphics driver with the next boot, kind of like i did last time?  hahaha...

Anyone else using powertop see such an entry?  And also see it disappear after resuming from hibernate?

---

### Post by HunterThomson on 2009-04-29
[SIZE="3"][COLOR="Blue"]How To Help Chargersfan420 with his BIOS hacking[/COLOR][/SIZE]

All you have to do is run this one line of code > compress > then attach the file to your next post.

```
sudo cat /proc/acpi/dsdt > dsdt.aml
```


To compress, just go into the Gnome grafical filemanager and right click it then select compress.

It's that easy so pleas help:guitar:

---

### Post by HunterThomson on 2009-04-29
[SIZE="3"][COLOR="Blue"]Suspend/Hibernate Video Driver Test[/COLOR][/SIZE]

Set you laptop to go into suspend in like 2 min's so you don't have to wait

Then logout of Gnome

Then hold Ctrl+Alt and press F2 and login. 
((For some really anoing reason Ubuntu has problems swiching to a diff vertural terminal so you may have to press it two or three times. FYI I never have this problem with any other distro... See in Arch back and forth to F2,... F5 and back to F7 no problem at all))

Then run:

```
ps aux
```

Find the "gdm" in the list ((I think it mite be /usr/bin/gdm)). Once found, you will want to find it's pid# ((pid# = Prosses ID Number)) this is the first # to the right of the prosseses owner's name.

Then kill it with this command ((PID = the real PID#)):

```
sudo kill PID
```

Make sure it is killed by running "ps aux" agin. 
If it is still running then run this command:

```
sudo kill -9 PID
```

Now Xorg is no longer running and your Video Driver is no longer in use.
So, wait untill it goes to suspend and see if you still have the same problem.

---

### Post by HunterThomson on 2009-04-29
Chargersfan420: Ya your right ATI Linux drivers are not good. Nvdia are good. Intel is ultra suportive of Open Source and they make the video driver for Linux Open Source. 

I love Intel:guitar:

Also, how are you useing the Vista DSDT settings? You do know there is a setting in Linux so you can tell Linux to Lie to the BIOS and say it is any OS you want. You don't have to edit the DSDT to do that.

Also, if you google for this you will find alredy posted DSDT files and work that has alredy been done. You will want to find the guy that fixed the DSDT for the Y510 backlight problem. He realy was on a role. He found the AML Code book and posted a link to it in this thread. He even fixed the DSDT after I gave up on. At the time started to think I made a big fool of myself claming the backlight problem could be fixed by editing the DSDT. But, He proved me right :) Big thanks. I had to do 50+ hr's of reading to even know about DSDT and then deduce the conclution the problem was the DSDT BIOS file. I am vary proud of myself for that one but now I know a hell of a lot about BIOS/the boot proccess/ACPI.

```
"dsdt" "Lenovo Ideapad Y510 is Go (Continued / NEW)" site:ubuntuforums.org
```

---

### Post by meatlover on 2009-04-29
Hey Guys,

Thanks for all the suggestions.  I totally forgot to check this post so I tried some new things that didn't help.  I posted a bug at launchpad.  Please check that out here:

[https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873).

I don't think it is my graphics card any more because I have a completely fresh install.  The link has attached dmesg from pm_trace, and syslog during boot, etc.

Also, my bios is from 2/25/09, so it's pretty new.  I think I will post on lenovo forums to let them know that the bios is kind of broken.

---

### Post by wyth on 2009-04-30
Here's my dsdt.aml

---

### Post by PhilMize on 2009-04-30
Anyone know how to get the front mic working? I've got alsamixer all set, sound works perfect just cant get my Mic to work with Skype. I've tried all the options on the list none of them work.I'm not good enough to know how to do any workarounds for this... So can any of you genius's help?:confused:

---

### Post by HunterThomson on 2009-05-01
> **PhilMize said:**
> Anyone know how to get the front mic working? I've got alsamixer all set, sound works perfect just cant get my Mic to work with Skype. I've tried all the options on the list none of them work.I'm not good enough to know how to do any workarounds for this... So can any of you genius's help?:confused:

Ok so you have set your mic settings in ALSAmixer to "front mic" and it still is not working in skype. Well, next try to install, if there is not one alredy, a basic recording application. Try to get the mic to work with that first. Then you will know if it is just a skype setting or a mic/ALSA setting. Skype adds a variable.

I think your mic is probaly the same as mine. I got mine to work in Skype. However, I thought the mic would work realy well do to having two but as it turns out it sounds like crap. The mic's are to sensitive and haveing two as it turns out is a bad thing. Even if you talk into one mic for clearer reseption the other mic pics up abeyant noise. Though I think you can remedy the problem by setting one mic to a none working setting. I never tried it though. 

(( I didn't read about its proprietary codec until after I paid for a year))

Insted I bought this supper cool WiFi phone. It works vary well don't pay any attention to what people have said about it on forums. They just don't understand that VOIP requires good wifi connection. 

[http://accessories.us.dell.com/sna/prohttp://reviews.dell.com/2341/A1287991/reviews.htmductdetail.aspx?c=us&l=en&sku=A1287991](http://accessories.us.dell.com/sna/prohttp://reviews.dell.com/2341/A1287991/reviews.htmductdetail.aspx?c=us&l=en&sku=A1287991)

And it dubbles as a super low-key WiFi network scout. It will tell you all networks in range, their strength, and what encryption. You can also easy walk around with a the cell phone looking thing and locate exactly where the router is without looking like a cracker.

But there are way better, by leaps and bounds, SIP phones.](*,)

---

### Post by PhilMize on 2009-05-01
> **HunterThomson said:**
> Ok so you have set your mic settings in ALSAmixer to "front mic" and it still is not working in skype. Well, next try to install, if there is not one alredy, a basic recording application. Try to get the mic to work with that first. Then you will know if it is just a skype setting or a mic/ALSA setting. Skype adds a variable.

I think your mic is probaly the same as mine. I got mine to work in Skype. However, I thought the mic would work really well do to having two but as it turns out it sounds like crap. The mic's are to sensitive and haveing two as it turns out is a bad thing. Even if you talk into one mic for clearer reseption the other mic pics up abeyant noise. Though I think you can remedy the problem by setting one mic to a none working setting. I never tried it though. 

(( I didn't read about its proprietary codec until after I paid for a year))

Insted I bought this supper cool WiFi phone. It works vary well don't pay any attention to what people have said about it on forums. They just don't understand that VOIP requires good wifi connection. 

[http://accessories.us.dell.com/sna/prohttp://reviews.dell.com/2341/A1287991/reviews.htmductdetail.aspx?c=us&l=en&sku=A1287991](http://accessories.us.dell.com/sna/prohttp://reviews.dell.com/2341/A1287991/reviews.htmductdetail.aspx?c=us&l=en&sku=A1287991)

And it dubbles as a super low-key WiFi network scout. It will tell you all networks in range, their strength, and what encryption. You can also easy walk around with a the cell phone looking thing and locate exactly where the router is without looking like a cracker.

But there are way better, by leaps and bounds, SIP phones.](*,)

I'll try what you suggested... O and the link you listed is bad. I did purchase a cheap philips usb phone for like $30 that I use on my work machine. It worked fine out of the box, I run intrepid at work. So we shall see. BTW voip is amazing all the haters don't know what their saying...lol :guitar:


Update:

So I tried it out with sound recorder and could get the headset mic to pick up my voice, but then I unplugged the headset and tried all the different options for capture devices and none of them could pick up my voice. So it's not just skype I'm having the issue with.

---

### Post by chargersfan420 on 2009-05-01
Good day everyone,

I've got a lot of work to do with this DSDT stuff, but i thought i would take a minute to point out something interesting...

HunterThomson, Wyth, are either of you still having brightness issues?  I take it these are original, unmodified DSDTs.  Are you guys booting custom ones now?  Hunter, is this the DSDT from after the BIOS update?

I found a method called _BCL, which according to the specs is for establishing a list of brightness control levels.

HunterThomson's _BCL method looks like this:
```
                        Method (_BCL, 0, NotSerialized)
                        {
                            Return (Package (0x0B)
                            {
                                0x0A, 
                                0x09, 
                                0x08, 
                                0x07, 
                                0x06, 
                                0x05, 
                                0x04, 
                                0x03, 
                                0x02, 
                                One, 
                                Zero
                            })
                        }

```

Here is Wyth's:
```
Method (_BCL, 0, NotSerialized)
                        {
                            Return (Package (0x0C)
                            {
                                0x0A, 
                                One, 
                                One, 
                                0x02, 
                                0x03, 
                                0x04, 
                                0x05, 
                                0x06, 
                                0x07, 
                                0x08, 
                                0x09, 
                                0x0A
                            })
                        }

```
I think i read somewhere that using "One" and "Zero" were acceptable substitutes for "0x01" and "0x00".  It just seems weird to me that they were listed backwards... I'm guessing the reverse brightness issue was caused by this, and if Hunter did provide a DSDT from the new BIOS, perhaps that is the issue that was addressed...

Although it is also possible that the OS is smart enough to realize what order they should be in for normal operation...

And now, something completely different - My _BCL:
```
Method (_BCL, 0, NotSerialized)
                        {
                            Return (BCLP)
                        }

```
BCLP shows up in a number of different places in my document.  I think the relevant initialization of the levels is from this section:
```
    Name (\BCLP, Package (0x0D)
    {
        0x64, 
        0x3C, 
        0x14, 
        0x1C, 
        0x24, 
        0x2C, 
        0x34, 
        0x3C, 
        0x44, 
        0x4C, 
        0x54, 
        0x5C, 
        0x64
    })

```
In Jaunty, lowering the brightness works normally, but raising it tends to make it jump up two levels of brightness really fast, and then back down one, producing a quick flash.  A bit odd, but not annoying or anything - but then again, maybe i'm just crazy and i just think it's doing that... it all happens so fast.

It seems to me that both myself and Wyth could have "circular" brightness, where when you hit the highest level of brightness and try to keep going brighter, it will switch to the lowest level and start going up again, because our initialization of the levels both start and end with the same number... This was the case for me on Hardy for a while, but not anymore...

Another weird thing i noticed is that both of your DSDTs are ~ 248 pages if i were to print it in this format, and mine is only 137 pages... which sure makes me scratch my head, considering my DSDT compiling supposedly produced "857 optimizations", and you guys were somewhere around 1/10th of that, if i remember correctly...

---

### Post by HunterThomson on 2009-05-01
chargersfan420: Ya sorry I should have told you. The DSDT I posted is form the new BIOS 06CN33WW. I bet Wyth's is from the 06CN31WW BIOS.

Nether the 06CN31WW nore 06CN31WW need the custom DSDT with the new Kernel 2.6.28

The problem that made the backlight dim on boot/VLC/Game and the backwards brightness controll and the brightness to jump up a cupple stepps then back down one then up 2 then down one. ((like your discribing with your laptop)) Was caused by the DSDT sending the brightness levels to the Kernel in a random order when the Kernel was expecting the info to be sent in order. So ya, I guess now in kernel 2.6.28 ACPI implementation the programers have added some code to order then info comeing from the BIOS and that is why there is no longer the need for the custom DSDT.((Just to be clear the DSDT was modified to send the backlight info to the Kernel in order))

Sents the DSDT is not in anyway closed from view I see no reason why Lenovo would not send you a coppy of the DSDT with the programers notes. What is makeing this hard is that you have to reverse engineer the DSDT. Just imagine if it was full of comments telling you execetly what each block of code did. . . Wouldn't that be a dream come true :) You can already get the source code with progamers notes for the ACPI kernel module.

-------------------------------

I have just sent a ESC+ request to IBM/Lenovo for the DSDT BIOS file with programmers notes for the Y510/Y710. I will let you know when I get a response. If they blow off my request as I expect I will call them.

---

### Post by meatlover on 2009-05-01
Hey Guys, 

I've looked into re-compiling my dsdt file, however, I didn't not have any errors.  I did have 11 warnings though, and I've been able to resolve most of them.  I have 2 errors left that I'm not sure how to fix.

My dsdt.aml file is attached, and here are the warnings I'm getting.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdtMINE.dsl  1350:                             Or (IPSC, PARM)
Warning  1105 -                                        ^ Result is not used, operator has no effect

dsdtMINE.dsl 15209:                     And (CTRL, 0x1E)
Warning  1105 -                                 ^ Result is not used, operator has no effect

ASL Input:  dsdtMINE.dsl - 15514 lines, 475296 bytes, 7518 keywords
AML Output: dsdtMINE.aml - 56145 bytes, 1644 named objects, 5874 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 2297 Optimizations
```


Any ideas?  Do these errors really matter?

---

### Post by HunterThomson on 2009-05-01
cool now we have the DSDT:

Y510 BIOS 06cn31ww
Y510 BIOS 06cn33ww

Y530 BIOS (only one)

Y710 BIOS (unknown)

I Just got a call from IBM. The guy said Lenovo handels all the Ideapad stuff so he gave me a # for them. Calling now. . .

meatlover: Well I think that in warning's about not used stuff can just be left alown.

---

### Post by HunterThomson on 2009-05-02
OK well I called Lenovo. The guy said no. Then I explained I alredy have the DSDT and that it is not closed in anyway I just need the notes. Then asked if there was a corporate address I could make a written request too. He then asked his boss agin and he said his boss is going to Email corporate for me and would send me a coppy of the Email he sent so I could see it. ((I hope he recorded my email address corecctly.. I have the funny felling he didn't)) He also told me they have never gotten a request like that before. I told him we are fixing it alredy but it would be way easyer if we had the programers notes. Good times good times :lolflag:

To not add to the confution . . . wait a second I don't think I ever told him what laptop I needed it for..Arg, darn he and I got lost in the fog of unexpected questions and forgot to exchange all the info needed.

------------------------------

OK request submitted. I called back and got the same office((thank god)) They got my compleet info. They are requesting the BIOS file DSDT with the programers notes for the Y510/Y710/Y530 for me. They repeted back to me my email and it's correct now. She said they will contact me through Email when they get more info. I will try my best to convince them to send me the files after they respond saying no. I hope I can just sign a non-disclosure agreement or convince them to release the files under the GPL.

---

### Post by chargersfan420 on 2009-05-02
Thanks for the DSDT, meatlover.  One weird thing is that when i compile your DSDT, it says only 38 optimizations... Perhaps the compiler is smart enough to check its compiled code against your system hardware... but if that's true, what would it check against? after all, it IS the BIOS info... Just a thought.

As for your errors, I'll see if anything interesting comes up in the specs.  The problem with this is that sometimes they don't name their variables according to the spec, so notes would be nice, like HunterThomson says.  There are some notes in the tables like this:
```
Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0062,             // Range Minimum
                            0x0062,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0066,             // Range Minimum
                            0x0066,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                    })
```
But there isn't much, and sometimes variables like _CRS might not even show up in the spec at all (in this case they do), because they named them whatever they wanted.

HunterThomson, nice work!  It may not go anywhere, but it doesn't hurt to try.

---

### Post by meatlover on 2009-05-02
@Hunter:

How would I install this new DSDT?

---

### Post by chargersfan420 on 2009-05-02
@ meatlover

It's actually easier than some websites with instructions make it sound.  I followed the instructions here ([COLOR="Navy"][https://help.ubuntu.com/community/ACPIBattery]("https://help.ubuntu.com/community/ACPIBattery")[/COLOR]) but i'll give you the version specific rundown:

If you're using grub, first go into /boot/grub/menu.lst (sudo gedit /boot/grub/menu.lst) and make a copy of the entry you're using.  Change the name of one of them to say "Original" or "Backup" or something.  

Then go to the files that your entries point to (/vmlinuz-something and /initrd-something) and make backup copies of these just in case.  (I even made a 3rd copy in grub and pointed to these backups just to be sure, but this may be a little crazy)

Then copy your newly compiled DSDT.aml into /etc/mkinitramfs/DSDT.aml (sudo cp (wherever your new DSDT is) /etc/mkinitramfs/DSDT.aml)
Notes on this step:
- you will require the package initramfs-tools if you don't already have it
- you MUST capitalize DSDT and include the extension .aml

and generate a new initrd by typing:
mkinitramfs -o (name of your new initrd-img file here)

Point your new grub entry to this new initrd file and name it "testing" or "custom" or whatever.  Then save and close it.

there might be some sort of command to update grub, i can't remember right now because i'm still stuck on LILO (and getting sick of it because it takes forever).  Maybe check on that and then reboot and try out your new entry.

If it doesn't boot, then select your backup entry.
*** Disclaimer - there's a chance you could mess stuff up and not be able to boot, and i won't take any responsibility for this.  Just be freaking careful! ***

To check to see if it worked, after rebooting, type:
```
$ dmesg | grep DSDT
[    0.000000] ACPI: DSDT BFED8420, 77A6 (r2 LENOVO CB-01     6040000 MSFT  2000001)
[    0.005577] ACPI: Checking initramfs for custom DSDT
[    0.249174] ACPI: Found DSDT in DSDT.aml.
[    0.249235] ACPI: Override [DSDT-CB-01   ], this is unsafe: tainting kernel
[    0.249293] ACPI: Table DSDT replaced by host OS
[    0.249434] ACPI: DSDT 00000000, 6EE1 (r2 LENOVO CB-01     6040000 INTL 20081204)
[    0.249585] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"
[    0.400650] ACPI: EC: Look up EC in DSDT

```

---

### Post by HunterThomson on 2009-05-02
you don't have to backup or update grub.

There is no chance of makeing your compuer unbootable becaus you don't change the kernel ram disk your using, you make a new one.

Just put the DSDT file in that place and move the new Kernel Ram disk you compiled to the same folder as the other kernel ram disk files. Then make the new entery in grub and point it to the new kernel ram disk.

Ya, I will be suprized if they just hand me the code. However, it is not realy all that usefull for anything other then there Ideapad laptops so there is no real risk for them. I think the problem will be the licensing of there intellectual property rights, legal red tape.

---

### Post by meatlover on 2009-05-02
Tried to use the new dsdt file, but nothing changed!  I'm not sure what to do about my suspend/resume errors.

---

### Post by HunterThomson on 2009-05-02
> **meatlover said:**
> Tried to use the new dsdt file, but nothing changed!  I'm not sure what to do about my suspend/resume errors.

chech dmesg log and make sure the words DSDT.aml Found is in there.

Then ya I didn't think it would fix the problem. But it is still good to have a non-buggy one. In depth editing is needed I am sure. Did you try the other programs to put your laptop into suspend? The first link that shows up with that google search I posted will explain how to install it. It works for a lot of laptops when the default ubuntu suspend program dosn't.

---

### Post by meatlover on 2009-05-02
Yeah, 

I checked dmesg and it had all of that listed.  What suspend program is this?  I've tried uswsusp before, and it did not work.  I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873)

---

### Post by HunterThomson on 2009-05-02
> **meatlover said:**
> Yeah, 

I checked dmesg and it had all of that listed.  What suspend program is this?  I've tried uswsusp before, and it did not work.  I filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873)

darn that's the one.

Well now this thread is the first in the list if you google for

"suspend" "fixed" sight:ubuntuforums.org


did you try it with the force flag

```
sudo s2ram --force
```

---

### Post by meatlover on 2009-05-02
Yes I tried all the options on the OpenSuse tutorial.

---

### Post by HunterThomson on 2009-05-02
> **meatlover said:**
> Yes I tried all the options on the OpenSuse tutorial.

Darn well your only options I know of then are fix the DSDT or try older Kernel's.

---

### Post by meatlover on 2009-05-02
Have you read anything about SSDT and ECDT files?

---

### Post by meatlover on 2009-05-02
Hey Hunter, 

Are you aware of how I can revert back to my old dsdt?

---

### Post by HunterThomson on 2009-05-02
> **meatlover said:**
> Hey Hunter, 

Are you aware of how I can revert back to my old dsdt?

you should have made a new kernel ram disk and a new entry in your grub menu file. so you should just select the origonal grub entry.

ya one of maps the function keys.

---

### Post by meatlover on 2009-05-02
I actually followed another post before you posted your method, which is located here:

[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Is there still another way to do it?

---

### Post by HunterThomson on 2009-05-02
> **meatlover said:**
> I actually followed another post before you posted your method, which is located here:

[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Is there still another way to do it?

Hum well chargersfan420 was wright you do need to back up your files I guess. 

There is realy no need to use the old kernel ram disk. The only thing you changed was told it to look in that direcotry for a DSDT.aml file. So, If you simply rename it Custom-DSDT.aml. It will nolonger load. Then it will be simple to just rename it back to DSDT.aml when you want to use it agin. Youu should use it even though it didn't solve the suspend problem.

---

### Post by meatlover on 2009-05-02
Also, 

I'm still getting these low memory corruption errors which I mentioned in an earlier post, although memtest has found no errors with my ram.  But now I've realized something odd, dmidecode thinks I have ddr2 (towards the end and it is in bold):

```
dmidecode

# dmidecode 2.9
SMBIOS 2.4 present.
47 structures occupying 1571 bytes.
Table at 0x9DCA9018.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Lenovo
	Version: 10CN41WW
	Release Date: 02/25/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 4.41

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Lenovo
	Product Name: INVALID
	Version: Lenovo IdeaPad Y5306
	Wake-up Type: Power Switch
	SKU Number: Lenovo SKU
	Family: Lenovo Family

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Lenovo
	Product Name: INVALID
	Version: 10CN41WW
	Serial Number: AB00214013
	Asset Tag: Lenovo Assert TAG
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Lenovo
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: Lenovo
	Type: Notebook
	Lock: Not Present
	Version: 10CN41WW
	Serial Number: INVALID
	Asset Tag: Lenovo Assert TAG
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Pentium M
	Manufacturer: Intel            
	ID: 76 06 01 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 23, Stepping 6
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GH 
	Voltage: 3.3 V 2.9 V
	External Clock: 1066 MHz
	Max Speed: 4000 MHz
	Current Speed: 1865 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: None
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: None
	System Type: <OUT OF SPEC>
	Associativity: <OUT OF SPEC>

Handle 0x0007, DMI type 126, 19 bytes
Inactive

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: TV Out
	External Connector Type: Mini Centronics Type-14
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2A
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2B
	Internal Connector Type: None
	External Reference Designator: Video
	External Connector Type: DB-15 female
	Port Type: Video Port

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB3
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: LAN
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB4
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB5
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9A1 - TPM HDR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9C1 - PCIE DOCKING CONN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2B3 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6C2 - EXT HDMI
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3C1 - GMCH FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1D1 - ITP
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 9, 13 bytes
System Slot Information
	Designation: J6B2
	Type: x16 PCI Express
	Current Usage: In Use
	Length: Long
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x001A, DMI type 9, 13 bytes
System Slot Information
	Designation: J6B1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x001B, DMI type 9, 13 bytes
System Slot Information
	Designation: J6D1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 2
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x001C, DMI type 9, 13 bytes
System Slot Information
	Designation: J7B1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 3
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x001D, DMI type 9, 13 bytes
System Slot Information
	Designation: J8B4
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 4
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x001E, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description:    To Be Filled By O.E.M.

Handle 0x001F, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Disabled
	Description: To Be Filled By O.E.M.

Handle 0x0020, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.

Handle 0x0021, DMI type 12, 5 bytes
System Configuration Options
	Option 1: To Be Filled By O.E.M.

Handle 0x0022, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

[B]Handle 0x0023, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: No Error
	Number Of Devices: 2

Handle 0x0024, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0025, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 3 GB
	Physical Array Handle: 0x0023
	Partition Width: 0

Handle 0x0026, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0023
	Error Information Handle: 0x0027
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x0027, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0028, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0026
	Memory Array Mapped Address Handle: 0x0025
	Partition Row Position: 1

Handle 0x0029, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0023
	Error Information Handle: 0x002A
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1[/B]

Handle 0x002A, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x002B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0029
	Memory Array Mapped Address Handle: 0x0025
	Partition Row Position: 1

Handle 0x002C, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x002E, DMI type 133, 5 bytes
OEM-specific Type
	Header and Data:
		85 05 2E 00 01
	Strings:
		KHOIHGIUCCHHII

Handle 0x002D, DMI type 127, 4 bytes
End Of Table




```

---

### Post by interfect on 2009-05-02
Hello,
I'm having a brightness issue on a Y530 running 9.04, so I figured this might be the place to post. I can set the LCD brightness from the command line and through the brightness slider panel applet fine, but the keys to change it seem mis-mapped. Brightness up (function+up arrow) toggles between dim and slightly less dim, and brightness down (function+down arrow) sets the brightness to zero. The keys don't send real keycodes--they fire ACPI events. The scripts that catch the events fake key presses on certain keycodes, but those are not what is changing the brightness--I can change the codes in the files or fake the same codes manually and see no change. I suspect the BIOS or a kernel module is catching these key presses and misbehaving. Would the hacked DSDT above fix this issue? Is it safe to try it?

The little software brightness meter comes up when this is happening--not very BIOS-y. Is there something in the default desktop setup that could be causing this?

EDIT: The machine also seems to be incapable of powering itself down under Ubuntu. Am I missing some critical module?

---

### Post by HunterThomson on 2009-05-02
> **interfect said:**
> Hello,
I'm having a brightness issue on a Y530 running 9.04, so I figured this might be the place to post. I can set the LCD brightness from the command line and through the brightness slider panel applet fine, but the keys to change it seem mis-mapped. Brightness up (function+up arrow) toggles between dim and slightly less dim, and brightness down (function+down arrow) sets the brightness to zero. The keys don't send real keycodes--they fire ACPI events. The scripts that catch the events fake key presses on certain keycodes, but those are not what is changing the brightness--I can change the codes in the files or fake the same codes manually and see no change. I suspect the BIOS or a kernel module is catching these key presses and misbehaving. Would the hacked DSDT above fix this issue? Is it safe to try it?

The little software brightness meter comes up when this is happening--not very BIOS-y. Is there something in the default desktop setup that could be causing this?

EDIT: The machine also seems to be incapable of powering itself down under Ubuntu. Am I missing some critical module?

Just to be clear after the BIOS truns over control to the OS Kernel the BIOS dosn't do anything. However, the Kernel uses some of the info the BIOS give it to control the computer hardware i.e. the DSDT, Memory map and so on. So, it is alwas a BIOS/OS combo problem.

Well if you can just set the brightness with a command you know why not just wright a script and map it to any key you would like.

Also, there is only a DSDT for the Y510 with BIOS 06CN31WW that has the section dealing with the backlight modified so it sends the info to the Kernel in order. There is no midified DSDT for anyother laptop yet. Also, this DSDT is now out of date for the new Y510 BIOS 06CN33WW and it is not needed for new Ubuntu or more correctly Kernel 2.6.28. So in short, no do not use that DSDT file.

meatlover: Hum that sucks. Ya I'll look around but I don't know of anyway of solving these Memory problems other then indepth rewrighting of the DSDT and/or Kernel or trying Old kernels.

Hopefully Lenovo sends me the source code with all the comments and hopfully the programer wrote good commments. If so we will be able to get these laptops singing.

--------------------------------------

Or try the new Kernel. My Arch Linux just updated to Kernel 2.6.29.2-1 
Ubuntu is on 2.6.28 and will be for the next 6 months.

---

### Post by chargersfan420 on 2009-05-05
@ meatlover

In both HunterThomson's and Wyth's DSDT files, line 11 has this:
```
*     Revision         0x01 **** ACPI 1.0, no 64-bit math support
```

Mine says this:
```
*     Revision         0x02
```

What does yours say?  Are you running a 64-bit version?

I know that 32/64 bit goes a long way in how your RAM is used, so I thought this may be a factor.

Another thought:  I'm not sure if the revision number is a direct relation to the ACPI specification revision... if that's the case, then perhaps i should stop looking at the 3.0a spec.

@ interfect

I'd suggest installing the iasl package, extracting your DSDT and attempting to compile it.  You can find instructions on how to do this a few pages back in this thread.  I wouldn't worry too much about booting with a custom one just yet, but i'd like to see it if you're willing to share, and if you want to post your error list, be my guest.  There may be something specific regarding brightness in there.

@ HunterThomson

Are you getting anywhere with Lenovo Support?

---

### Post by meatlover on 2009-05-05
@Chargersfan420:

My dsdt says:

 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x0000DB51 (56145)
 *     Revision         0x01 **** ACPI 1.0, no 64-bit math support
 *     Checksum         0x37
 *     OEM ID           "LENOVO"
 *     OEM Table ID     "CB-01   "
 *     OEM Revision     0x00000223 (547)
 *     Compiler ID      "INTL"
 *     Compiler Version 0x20081204 (537399812)
 */

I have 32 bit.  Are you running 64?

---

### Post by chargersfan420 on 2009-05-05
@ meatlover

Yes, i am using 64-bit.  I'm using it because i upgraded to 4 GB and i am usually running VirtualBox, so i wanted to make use of all 4 GB.  I'm not entirely sure if it is worth it, though, because in 8.04 i couldn't use Adobe Flash Player at all, and i can now, but it causes a process called npviewer.bin to eat around 10% of my CPU and cause ~ 120 interrupts per second to the CPU.  I'm not sure if this happens anyway with 32 bit or not... Perhaps it's required to use flash player, or maybe it is the process that converts it from 64-bit to 32-bit (or vice versa).

I don't know what else to tell you about your memory issues.  That is really strange.  Maybe ACPI 1.0 and DDR3 don't jive in terms of power saving.

I checked my dmidecode and it appears i was correct - the "Revision" in the DSDT table refers to the revision of the ACPI spec.  It's odd that the Y510 and Y530 are on 1.0 spec and the Y710 is on 2.0 spec, and the latest spec level (to my knowledge) is 3.0a.

---

### Post by meatlover on 2009-05-05
Whats also weird is that I'm getting memory corruption errors, however, memtest says my memory is fine.  Check these two bug reports which I contributed to.

[https://bugs.launchpad.net/ubuntu/+bug/368873](https://bugs.launchpad.net/ubuntu/+bug/368873)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894)

---

### Post by chargersfan420 on 2009-05-05
With regards to that second link, it sounds like you found the right line to get into to log your complaint.

I had an issue with my RAM when i upgraded from 2 GB to 4.  Hardy wouldn't boot with the new RAM.  All of my other OS's worked fine, and memtest confirmed that the new RAM was good.  But Hardy still wouldn't boot.  It wouldn't even say why, it'd just freeze.  I reinstalled fresh with the new RAM and was on my way...

---

### Post by HunterThomson on 2009-05-05
Nope no reply about the DSDT from Lenovo. I never got that email he said he would send me. I can only assume they just blue me off.

...........

Mother **** thouse **** ***IT
I have only had this laptop for 13 mounth just long enugh so it is not under warranty !

The right hindge just broke in a vary bad way :evil:

This is bull. As far as I am conserned this is a mission critical laptop. I can not do with out it for even a day. 

JSuresh: What was the total time from mailing it to them and getting it back?

I am thinking now. My plain of action is to buy a new laptop. THEN send this in to be fixed then sell this laptop when I get it back.

---

### Post by HunterThomson on 2009-05-06
Arg, I think i am going to get a Thinkpad R500 direct from Lenovo.
That will put me under $800 that I realy don't have. And on top of that it is DDR3 ram so the 4Gig Cas4 DDR2 ram I "Just" got I will have to sell.
On the pluss side I am getting the WSXGA+ (1680 x 1050) screen :) But I will have no DVD burnner because they say it will add 4 freaking weeks to shipping date.
It seems like ThinkPad laptops are still being made by IBM and the Ideapad's are made strictly by Lenovo.

I am going to demand that someone gives me back my $150+ for the Wincrap I will not even boot once. The first boot will be with a Archlinux install CD.

+++++++++++++++++++++++++++++++++++++

Man I am pissed. I got this laptop becaus I thought it would never brake. I thought that they made sold laptops. Boy was I wrong.

I don't think I am going to buy a Thinkpad. They are infact made by Lenovo.

I am thinking of buying a Samsung. Anyone have any knolage of Samsung laptops? I don't realy associate Samsung with PC's but it is ether them or MSI. Anyone know anything about MSI laptop quality?

Here are the two I am thinking about...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834131026](http://www.newegg.com/Product/Product.aspx?Item=N82E16834131026)

and

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834152105](http://www.newegg.com/Product/Product.aspx?Item=N82E16834152105)

======================

Arg, all laptops suck. Samsung and MSI suck. I realy don't want to by a China Lenovo Thinkpad. Boy O' boy I wish IBM didn't sell the Thinkpad to Lenovo. It would be no question hands down Thinkpad. I guess I trust Mac but they are super crazy over priced and I would just install Archlinux on it. I am not paying $1,000 for a 13" and to get a 15.4 I would have to pay $2,000+. This sucks.

Well maybe dell. I have set up a lot of them and they all impressed me with quality. Still working after 5+years and still running like new no broken hinges or any bull like that.
++++++++++++++++++++++++++++++++++++++++++++

Ya I think Dell it is. I think I'll go and drop some $1,500 on ether a Dell Precision NSeries or Dell Latitude. They are the quality I am looking for. Real Enterprize class laptop.

It seems as though all personal laptops like MSI, Lenovo, Samsung, ASUS... are all cheap crap. Sure the spec's look good but the build quality is junk. What good is it to have a super fast CPU and nice GPU if the keyboard or hige or speakers brake in a year? I don't ever play games so all I need is realy high dots per inch screen and super good build quality.

---

### Post by HunterThomson on 2009-05-06
[COLOR="Red"][SIZE="3"]FIY[/SIZE][/COLOR]: Lenovo will not even try to fix your laptop if your warranty is up. AND they will not sell you extended warranty if your laptop is more then 30 days out of warranty.


SO, there is no hope of fixing my laptop.

If you have a Y510 Sell Now wile it still works !

[COLOR="DarkOrange"][SIZE="3"]Keep in mind I have extremly high expectations !
Forums reviews alwas make things sound way worse then thay are ![/SIZE][/COLOR]

---

### Post by wyth on 2009-05-07
When I got this laptop, it was an emergency situation, and I got an incredible deal on it.  I thought since the ThinkPads had such good reputations running linux, it was a generally safe bet.  But I saw a slow retreat in Lenovo's support for linux not long after getting the machine, and then there was that crazy article by one of their heads about how linux had no future (hint: he sits in on a lot of Microsoft meetings).

This is unfortunate, because IBM has invested a lot of work in unix and linux.  Since letting their hardware division go to Lenovo, that support is dissipating, and from what I've seen on the Lenovo forum, the one guy they had answering some linux questions just isn't around.  

I haven't had the physical trouble others have had, but I'm generally hyper-careful with any electronics (oldest of three brothers, all of us wrestlers, stuff got broke, and I developed the careful habit).  That said, one of the best things about this machine was the deal I got on it.  Overall, it's a mixed bag, otherwise this thread wouldn't have to exist.  

I decided a while back, when it's time for a new laptop, I'll be looking elsewhere as well.

---

### Post by wyth on 2009-05-07
> **HunterThomson said:**
> 
Ya I think Dell it is. I think I'll go and drop some $1,500 on ether a Dell Precision NSeries or Dell Latitude. They are the quality I am looking for. Real Enterprize class laptop.

It seems as though all personal laptops like MSI, Lenovo, Samsung, ASUS... are all cheap crap. Sure the spec's look good but the build quality is junk. What good is it to have a super fast CPU and nice GPU if the keyboard or hige or speakers brake in a year? I don't ever play games so all I need is realy high dots per inch screen and super good build quality.

You *might* want to look at some of the HP enterprise laptops or System76.  I don't know enough about them now, but my brother has been looking at them.  The HP's are aluminum and built a little tougher than the home models, and I've seen nothing but praise for System76.

I'm also running a Dell desktop (Inspiron 530, ordered with Ubuntu), and it's been problem-free for three years, save for one motherboard glitch.  But that wasn't the computer's fault -- I wasn't home, and our power turned on and off about 17 times in two hours, more the next day, and that can fry a motherboard.  It was still under warranty, and Dell was out to replace it in two days.  The repairman said he sees that same problem all the time.  

So if you're power is cutting on you, unplug your machine.

---

### Post by HunterThomson on 2009-05-07
I was vary angry when I wrote all that stuff. I have calmed down a bit now. However, I think I will leave it up to show an experience some people mite have with Lenovo.

As far as Lenovo droping Linux. I remeber you saying that before. It seems your right they are droping suport. Dell on the other hand is increasing support for Linux. Mr. Dell has been reported as saying he uses Ubuntu on his laptop. So, quite the opposite of Lenovo. Also, Dell warranty is 3 years Lenovo is 1 year. I have read a lot of problems starting to pop up in the Thinkpad laptops now that Lenovo bought them. It seems like Lenovo quite effectively bought the customer base form IBM and now are droping quality slowly, like a fish in a pot of bolling water.

System76 hum never heard of it but sounds good. I'll look into it thank you for the sugjestions. HP is in direct compitition with Dell in the buisness class laptop's. Which leads me to beleave they are about the same good quality. The difrance with 'me' is that I have seen good Dell laptops but have never seen much HP. Better to go with the devil you know but System76 sounds worth looking into. If I don't find one with Sysem76 I think I am going to get an all Magnesium Alloy case Dell latitude E6500 that has it's hinge made from a sold peace of machined aluminum and a UltraSharp™ Wide WXGA+ (1440x900) LED Display

---

### Post by JSuresh on 2009-05-07
[QUOTE=HunterThomson]JSuresh: What was the total time from mailing it to them and getting it back?[/QUOTE]

The first time I sent it in, the return time was about 2 weeks.  Sorry to hear about your hinge breaking as well :(

---

### Post by wyth on 2009-05-07
For what it's worth, [System76]("http://system76.com/index.php") just reported a [crazy increase in profits, like 60%, in one quarter]("http://www.workswithu.com/2009/04/15/system76-ubuntu-pc-makers-revenue-up-61-percent/").  And that's in a recession.  They're not a huge company, but they get all kinds of praise for their hardware, make machines specifically designed to run Linux well (Ubuntu), and I've seen some of their staff responding on the System76 page here.  If such a specialized company is seeing that kind of profit increase, it says something about the company and their products.  You might want to [browse their page here]("http://ubuntuforums.org/forumdisplay.php?f=341") to see what people say about the machines.  (I'm sure Arch would run on them as well.)

Their machines are a little more expensive, and I'd like to use one for a while before I dropped cash on it, but I'm considering their Starling netbook as a gift.

(Can also bump up to a 3 year warranty on them)

---

### Post by HunterThomson on 2009-05-07
> **wyth said:**
> For what it's worth, [System76]("http://system76.com/index.php") just reported a [crazy increase in profits, like 60%, in one quarter]("http://www.workswithu.com/2009/04/15/system76-ubuntu-pc-makers-revenue-up-61-percent/").  And that's in a recession.  They're not a huge company, but they get all kinds of praise for their hardware, make machines specifically designed to run Linux well (Ubuntu), and I've seen some of their staff responding on the System76 page here.  If such a specialized company is seeing that kind of profit increase, it says something about the company and their products.  You might want to [browse their page here]("http://ubuntuforums.org/forumdisplay.php?f=341") to see what people say about the machines.  (I'm sure Arch would run on them as well.)

Their machines are a little more expensive, and I'd like to use one for a while before I dropped cash on it, but I'm considering their Starling netbook as a gift.

(Can also bump up to a 3 year warranty on them)

Ya I was just looking at System76. I too am sure with out a dout any linux distro would work the same. I'd just see how they set up Ubuntu.

Boy I would really love to buy one from them just to support them but the laptops just are not quite there for me. I like my laptop to be 'all' black simple square design. Just like how the Y510 looks. Also, a metal case is a must have this time around. The Latitude E6500 meets all the spec's I'm looking for. Well all exept the bigy 'no windows tax.'

It seems though that if I spend 5-10hr's on the phone Dell will give me ~$50 back for my unused windows licence. Here is a good link to someone that did just that.

[http://www.linux.com/articles/59381](http://www.linux.com/articles/59381)

---

### Post by HunterThomson on 2009-05-07
[SIZE="3"][COLOR="Blue"]Some things that "Mite" extend the life of your Y510 right hinge.[/COLOR][/SIZE]

1: Never hold the laptop closed with the hinge side down in your hand. Always hold it tuchpad side in your hand.

2: There are two screws on the bottom of the laptop by the hinges. If you loosen them just a bit so the lid opens and closes easyer this mite help quite a bit.

3: Oil the hinges. However, try loosenig the screws first once it is oiled there is no going back. If you over tighten the hige screws to compensate it would be worse overall. Your choice of oil I would guess WD40 just be carefull not to gunk up your laptop. Oil is non-poler so ther is no chance of shorting out anything. You may even want to open up the laptop to do the oiling but I bet you can get some in there with out doing that.

Keep in mind there is Zero warning. All I did was open it up nice an easy nice and slow and keeping in mind I heard the right hing could brake. All of a sudden it looked like someone took a hammer to the corner of my laptop with wire bundels sticking out and all.

---

### Post by chargersfan420 on 2009-05-07
I stay away from the forum for two days and look what happens.  All hell breaks loose.

In regards to Lenovo turning to ****, i agree.  The Ubuntu support is just not here, I'm editing poorly coded bios tables to make things work (which seriously makes me think every time something goes wrong, do i blame lenovo or do i blame the ubuntu people?  How can i expect Ubuntu to work if the bios is giving it crummy specs?).  And the thing that really gets me is that i'm an IT Administrator, i make purchasing decisions for a company with lots of computers, and i keep needing to buy more laptops, and they won't even offer anything in Canada with my only two requirements (a 17" screen and a number pad) for less than $3,000 even though i CLEARLY know they make them (Y730's).  Effing ridiculous.  I bought a toshiba satellite for one of our execs last week.  And i was really hoping to avoid a whole different array of brands deployed in the company.  It just makes troubleshooting tougher.

About the toshiba satellite, it seems really nice, but there were two things that bugged me:  the lid didn't seem to close very nice (not seamless at all), and the enter key was narrow and occupied 2 rows, with a / key where the left half of enter used to be, so i was constantly hitting / by mistake.  That would drive me nuts.

The only thing i've heard about Dell is that they make poor quality personal PC's but very awesome business machines.  This was a while ago, and I must say i'll be taking a closer look at them the next time my company needs a computer.

Oh, and HunterThomson, if you buy a Mac, i will personally come to Hawaii just to kick you in the ***.  I'm as anti-Mac as they come.  

It's also really funny how much negativity was flying around in here while i was swearing at my machine for crashing again.  I was using the 9.04 release candidate (64-bit) and i noticed about 4 times in the last 3 weeks that fsck would fail on boot and make me do it manually.  The first two times it was no big deal.  The 3rd time somehow my Desktop folder got deleted (losing 1 file in the process), and everything in my home folder was now on my desktop.  This was also very easily fixed but I shouldn't have ignored the warnings...

The 4th time took FOREVER to get through all the errors.  Most of the time i held down Enter because i had no idea what it was asking, i just assumed that if i did what it suggested i would be able to boot.  It easily took an hour including a few reboots, and when i finally got back in, my virtual machine's latest snapshot was toast.  I lost all of my code projects from the last 3 weeks. :(

Then graphics started glitching, so i rebooted again, a few times, and it wouldn't mount /dev.  Time for a reinstall.

This time i'm on 32-bit and i have a few findings:
- power saving is slightly better, and the cpu's average sleep time is easily doubled
- npviewer.bin is a power-hogging wrapper for adobe Flash player conversion between 32 bit and 64 bit systems.  totally not necessary on 32 bit.
- without the custom DSDT, i can't hibernate without my screen locking up.  more on this below
- powertop now says this when i first start it:
```
Your CPU supports the following C-states : C1 C2 C3 C4 C5 C6 
Your BIOS reports the following C-states : C1 C2 C6 

```
(looks like more DSDT work to do)

Bottom line, don't use 64-bit if you don't have to.  Especially in a laptop.  If you're running lots of vm's and need lots of RAM, then sure, but ~3.25 GB of RAM and 1 VM on 32 bit will be just fine.

I think i figured out what is happening with the graphics though.  When i use the proprietary driver, powertop shows fglrx interrupting the cpu at 60 Hz.  After returning from hibernate (with custom DSDT), these interrupts no longer register with the cpu and graphics runs smoothly.  I think both the cpu and the gpu are running the display at the same time, or maybe just the cpu is doing it, and then, somehow after hibernating, the gpu starts doing all the work like it is supposed to.  Anyone have any suggestions what i can do about this?

(perhaps not, if everyone is ditching for Dell...)

EDIT: Since this install is so fresh, I'm tempted to try to bend it to see how far i can go before it breaks.  I'm going to try Wyth's suggestion for UXA or whatever it was called.
EDIT: Wait, Wyth, you said that's for Intel?  Does that mean it doesn't apply to me and my ATI Radeon HD2600?

---

### Post by HunterThomson on 2009-05-07
LOL, chargerfan420 . . . Ya, things have gotten realy crazy over here :P
Even after I "hopefully" sell this laptop, I'll still check this thread and help out where I can.

You should have said your in IT before. I would have not talked to you like a noob but I guess it is good for everyone ells that is not in IT. I am not in IT but am shooting for it. I plan on going to Honolulu comunity collage and get a AS in CENT+CCNA+RHCE. They teach LINUX !!! I'll take Unix systems administration I/II with LINUX. TCP/IP with LINUX, computer science with JAVA. I am learing Python right now and there is Jython so I will not lose any time learning a language I will never use and both are cross platform. All the other schools in Hawaii only teach Wincrap and VB.

Good work on the DSDT I am impressed :o It soulds like your realy getting someware. You got hibernation to work that is way cool. To bad that Lenovo probaly will not even think about useing your work in there next BIOS. Worth a shot sending it to them thogh.

That sucks your getting all though problems with 64bit. I have never used 32bit linux. 64bit was also a reason I swiched to Linux the Y510 dosn't have 64bit drivers for wincrap. But Windows is still noob to 64bit even though Linux has suported 64bit for years and years. But I hear there is not realy that much real life difreance.

Boy, it is tough finding a good laptop to run Linux. I think I am going to pass on Dell after all. The E6500 is getting a lot of bad revews form users but good ones form Mag edditor's. I listen the "users" more. The users are saying the E6500 still fells crappy even though it has a medal case. The speakers suck and the keyboard flexes. There is also some problem that will not let 64bit Vista work, which mite be a sign of a bigger problem. I think it is all do to the same problem I have with the Ideapad Y510, It's a new model. I bet the Y710's and Y530's are better. Hopefully, Dell and Lenovo learned from there mistakes on these laptops.

Now, I am thinking HP EliteBook 8530w Mobile Workstation. I can get it with,15.4 WSXGA+ anti-glare 1680 x 1050. Reviews are even better for this one. Zero keyboard flex and way crazy strong case, hard plastic and strong magnesium alloy inner shell with aluminum outer shell. Still 3year warranty and Onsite repair. We'r talking ~$1,500 though. You realy do have to pay big bucks to get a nice laptop. I meen you could make the argument, "Why not just buy a new $500 laptop every year for the next three years?" But, I would respond saying "15.4 WSXGA+ 1680x1050".

[http://www.notebookreview.com/default.asp?newsID=4631](http://www.notebookreview.com/default.asp?newsID=4631)
And check out this crazy asain guy droping the laptop from head hight.
[http://www.youtube.com/watch?gl=AU&hl=en-GB&v=H5cKuO8ojAU](http://www.youtube.com/watch?gl=AU&hl=en-GB&v=H5cKuO8ojAU)

---

### Post by HunterThomson on 2009-05-07
> **chargersfan420 said:**
> 
Oh, and HunterThomson, if you buy a Mac, i will personally come to Hawaii just to kick you in the ***.  I'm as anti-Mac as they come.  


Ya, I am vary anti-Mac too. I hate Steve Jobs as much as I hate Bill Gates. Something about Mac alwas rubbed me the worng way. All the media blitz stuff realy turns me off. I also don't like the non-Tec Mac people. They think thier so smart for getting a Mac, "No viruses". Du, the only OS that has viruses is Wincrap. They never know the history of MacOS ether, "It's BSD guys." Mac is also the deffinition of non-standard compliant. You can't ever get away form MacOS. You use to not even be able to buy any compuer parts unless they were "Aple ram or Aple harddrive". Even still you can not upgrade the "Firmware" with out MacOS installed. Booting form a Live CD is a nightmare on a Mac. All the MacOS application's are even more of a rip off then Wincrap ones. Silly little application's to partiton the harddrive cost $200. The list go's on and on. I'll never buy a Mac but they are well built.

P.S. I added a disclamer to my ranting and raving.

---

### Post by PhilMize on 2009-05-08
Hey Hunter, I'm looking at ditching this Lenovo as well. I was looking into the Dell xps studio 13. I've seen nothing but great reviews and I even got to play with a display model at best buy. You can pick them up for around $900 if you are good. I can get the midrange model through my Dell rep at work for $850. Only issue i have with it is 1 dedicated usb 2.0 port and 3 display ports!(hdmi, s video, and vga) Though the ESATA port on it also acts as a usb 2.0 port. The 16' model Would be a better buy I think due to more usb slots and blueray drive, but I want something small for work I'm sick of carrying around a 15' to do inventory.

---

### Post by HunterThomson on 2009-05-08
PhilMize: Ya I hear good things about XPS too. They are what most people are buying from dell right now. There Laditued E's are giving people problems and the Persison M's are over priced. But, the XPS's are doing vary well. $850 is a killer deal for that quality of laptop. Owe also, you can use a USB Hub if on the One port. Up to 127 devices, including the hub devices, may be connected to a single host controller (wikipedia.org) but real life only like maybe 10'ish.

I should have gotten one of thoughs probaly.
I just felt like going nuts and geting some crazy rugged laptop.

I have just paied for and HP elitebook 8530w Moble Workstation and got a good deal on insight.com. I only paid (before shipping and tax) $1,272.15 but my address is all mested up out here in the jungle so I bet I'll have to call them on monday and mabey spend more on shipping. As of now the form said the total is $1,382.37. So, ya I am paying a Crazy amount of money on my laptop but a lot cheaper for it then anyware ells. At HP.com it would have been something like $1,649.00. I will also have a few Linux problems. The backlight controls will not work and it has a  NVIDIA Quadro FX 770M which is only suported by the most recent proprietary driver, a real pain to set up. HP elitebooks are supose to have a bad overheating problem. I can live with that if I can throgh this thing on the ground and have it still work :P

[COLOR="Red"]HOLY CRAP ![/COLOR] I am so lucky insight.com forced me to use the po box insted of the physical address that I have registerd with my Credit card company. They are reporting "Contact Sales Rep(1)" next to "Credit Status:". I'l call and cancel the order. I just found the same laptop on compusa.com for ! $850 ! with shipping !. Ya it comes with all the same stuff exept it has the P8400 2.26Ghz and just the plain DVD-Rom and 5400rpm HHD insted of 7200rpm. On the pluss side it has the ATI Mobitilty FireGL V5700 which has a way better driver for Linux. The optical drive is a removeable bay so I can just buy the DVD-+RW drive for like $200 or just get an external for like $50. I save $531.32! WOW way better deal ! I am so glad my credit card didn't go through with insight.com. Though I bet I could have canceled the order anyway before they shiped it but this is way easyer. I hope compusa.com takes the money from my card before insight.com even has a chance to try agin. That way there is no way they can get any money form me, it will not be there :P

Here is the run down of the spec's I find relivant:
compusa.com model: (KS054UT)
tigerdirect.com has (KS054UT) for the same price buy form them.

insite.com modle: (KS049UT)
    
MIL-STD 810F Military Standard:guitar:

Intel core 2 P8400 2.26Ghz '45nm'
cd-rom/DVD-ROM
15.4  1680 x 1050 ( WSXGA+ )
3 year parts&laber + 3 year on-site repair
Blue tooth Class-2 + Intel 5300 wifi
Intel Centrino-2 platform
1-DDIM DDR2-800 2Gb RAM 'or my' 4GB cas4 DDR2-667
160GB 5400RPM 'or my' OCZ Vertex 30GB SSD
3G fax could get 3G internet stuff (but my credit score is '-10')
SD 'all that' card reader
ATI Mobitilty FireGL V5700 256MB VDDR3

I did calm down about Lenovo and checked out there Thinkpad's. I must say that if I was an IT guy needing to get a corprate laptops, on a buget, the Thinkpad is still the way to go. The new Lenovo one's don't have the nice IBM screens. Lenovo just downgraded the keyboard to cheap flexable keyboard's and the power supply is messed up. However, they are the cheapest and most configurable business laptop's between the big three, Dell, HP, Lenovo. Other then what is mentioned they should still be the same as the IBM Thinkpads. Lenovo phone suport was good to me too. They at lest patronize me and said they would email corporate about getting the DSDT's. I forgot to mention even though I was past the grace period they did offer to let me pay $120 for one more year warranty. I didn't have the money on my card to buy it though and I don't want to invest anuther $120 in this.

Also, a quick Linux note:

HP will give you FreeDOS
___HP will suport SUSE Linux on there elitebook but You install it.
___Everything on the elitebook is supose to work with Open SUSE
___Also, HP owned the UNIX source code at one point and made HP-UX
Dell will give you Red Hat Linux or FreeDOS
Lenovo will only give you Wincrap

FreeDOS seems to be the there vertion of a WhiteBOX. That way they can still have an OS they can provide suport too. As far as 'Realy' getting RadHat or FreeDOS. . . Well It's not going to happen. The only way your going to get that is if you buy your laptop direct form the manufacturer. None of the re-sellers sell laptops with FreeDOS or RedHat. Unfortunately this is artificially decreasing Linux sales by orders of magnitude.

To _End_ this _extremely off topic_ post, off topic in terms of this being a Lenovo Ideapad Y510 thread and not my personal place to rant and rave....
The compusa.com $850 order went thourgh and is Shiped. So, happy I saved $531.32 by not getting parts I don't need.

P.S. I have got to stop wrighting long post's after 10PM

---

### Post by HunterThomson on 2009-05-10
Chargersfan420: This mite intrest you. I have been reading up on the HP elitebook BIOS. I have found it uses what is caled "Extensible Firmware Interface (EFI) Boot Manager" developed by Intel. It alows you to wright applications that operate in between the hardware firmware and the OS. Vary much like but more customizable then the Coreboot modules. It is a BIOS that is on a block device like your HHD. The HP implementation uses a FAT32 primary partition to store the EFI. A lot of the HP application seem kind of dumb but there is a lot of power in EFI and it lets you run you own non-signed EFI applications. One of the cool EFI applications is a EFI level Shell with scripting capabilities. They speek of a security risk useing EFI do to it being on a FAT32 partition (FAT32 has no user file permitions). However, with a *nix implementation you could add a /etc/fstab entry for the EFI partition and set the user permitions for it to 000 (odd though if you set user permitions in fstab to "000" it is read by Archlinux as "777" and viceversa. So, you realy want it to be set to 777 in fstab) . Someone with physical access could still boot up a Live CD and load some realy powerfull malicious application. Still, it would protect you form someone that had gained 'user' level access on your box remotely. 

Here is a link to the HP white paper if you would like to read more:

[http://www.docs.hp.com/en/rx1600_OpMaint/ch05s01.html](http://www.docs.hp.com/en/rx1600_OpMaint/ch05s01.html)

Also there is UEFI wich is a OS & platform independent compatability layer. It Abstracts the platform from OS & Decouples development. This UEFI can also boot Linux so it could be used to take the place of the GRUB/Lilo boot loader and add far more capabilitys.

Here is a link to the Intel web page which explains it.

[http://software.intel.com/en-us/articles/uefi-architecture-and-technical-overview/](http://software.intel.com/en-us/articles/uefi-architecture-and-technical-overview/)

---

### Post by meatlover on 2009-05-11
So I have noticed a few things:

I have ubuntu 9.04 and ubuntu 8.04 installed on an hp dv5000 with an ati graphics card.  Suspend works fine on this machine when 8.04 is installed, and when 9.04 is installed, it hangs just like my ideapad.  I decided to check out lshal, to see if there were any differences:

on 8.04:

```

lshal | grep can_suspend
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.can_suspend_to_disk = true  (bool)
  power_management.can_suspend_to_ram = true  (bool)

```

on 9.04:

```
lshal | grep can_suspend
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)

```

I'm not sure why the last two lines are missing. My ideapad has the same two lines missing. So, I downloaded a copy of ubuntu 8.04 and put the live cd in my ideapad. The two lines were there.  I decided to try to suspend, (I'm not sure if this is supposed to work with live cd), and this time I got a message on a black screen, 

"Withdrawing address record for fe80::222:faff:fe48:f8ce on wlan0."

instead of the blinking cursor.  I was forced to do a hard reboot still, but it is interesting that I was able to get a message which will not show up on my ideapad.  Does this look like a problem with network manager, or avahi-daemon?  The following is taken out of my syslog file, at precisely the time my computer began to suspend from 9.04 just a few minutes ago:

```
May 11 19:54:11 computer-laptop anacron[4623]: Anacron 2.3 started on 2009-05-11
May 11 19:54:11 computer-laptop anacron[4623]: Normal exit (0 jobs run)
May 11 19:54:11 computer-laptop NetworkManager: <info>  Sleeping... 
May 11 19:54:11 computer-laptop NetworkManager: <info>  (eth0): now unmanaged 
May 11 19:54:11 computer-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
May 11 19:54:11 computer-laptop NetworkManager: <info>  (eth0): cleaning up... 
May 11 19:54:11 computer-laptop NetworkManager: <info>  (eth0): taking down device. 
May 11 19:54:12 computer-laptop NetworkManager: <info>  (wlan0): now unmanaged 
May 11 19:54:12 computer-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
May 11 19:54:12 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
May 11 19:54:12 computer-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3619 
May 11 19:54:12 computer-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
May 11 19:54:12 computer-laptop avahi-daemon[2929]: Withdrawing address record for 192.168.1.101 on wlan0.
May 11 19:54:12 computer-laptop avahi-daemon[2929]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
May 11 19:54:12 computer-laptop NetworkManager: <info>  (wlan0): cleaning up... 
May 11 19:54:12 computer-laptop NetworkManager: <info>  (wlan0): taking down device. 
May 11 19:54:12 computer-laptop avahi-daemon[2929]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 11 19:54:12 computer-laptop avahi-daemon[2929]: Withdrawing address record for fe80::222:faff:fe48:f8ce on wlan0.
May 11 19:55:18 computer-laptop syslogd 1.5.0#5ubuntu3: restart
```

It looks like the last thing is does is withdraw my address, and then hang there for a few seconds before I hit the power button.

I think the computer might think that it CAN'T suspend, since those entries aren't in HAL.  Any ideas?

---

### Post by HunterThomson on 2009-05-12
Hum, it dose seem like you would need tha hal entries to susped but somthing mite have changed with that so it dosn't need to be there.
I have also heard of NetworkManager making suspend not work.

The only way to know for sure would be to stop the networkmanager and avahi deamon. In Archlinux the daemons are in /etc/rc.d/xxxx how ever in Ubuntu I think it is /etc/modprob.d/xxxx. Look for the one that ends in ".d" in /etc. Look in /etc and see what the networkmanager daemon is called. You would stop it by giving it the stop command like this.

```
sudo /etc/modprobe.d/networkmanager stop
sudo /etc/modprobe.d/avahi-daemon stop
```

If that dosn't work....
I just did a "locate hal" and found my hal.conf file here 
/etc/dbus-1/system.d/hal.conf

It looks simple enugh. I'd maby find a vertion of Ubuntu that dose suspend and compare the conf files. Maybe even just copy the working one over (make back up though) and see if that works. If you have a problem booting with the coppied hal.conf you and alwas boot up a live CD and change it back.

---

### Post by meatlover on 2009-05-12
Tried both of your suggestions, still seeing the same problem.  Do you know how to add those options (e.g. can_suspend_to_ram) to hal?

---

### Post by HunterThomson on 2009-05-12
> **meatlover said:**
> Tried both of your suggestions, still seeing the same problem.  Do you know how to add those options (e.g. can_suspend_to_ram) to hal?

I know you add it to your hal.conf file but I don't know exactly what you type in. You'll have to look at I guess the 8.04 hal.conf file.

Note: On HP and Open Source.
It seems HP also helps out a lot with Linux and Open Source. I feel good suporting them. 
They also have an Linux hotline: 1-888-HP-Linux

Quote form:
[http://h20219.www2.hp.com/enterprise/cache/599999-0-0-0-121.html](http://h20219.www2.hp.com/enterprise/cache/599999-0-0-0-121.html)

"""
HP does a lot more than talk about open source&#8212;we're a solutions provider, active user, and a longstanding supporter of the community that drives it. Today, more than 2,500 developers across the company are focused on Linux and open source projects. Over 6,500 service professionals worldwide are involved in the implementation and support of Linux and open source projects. And HP has over 200 shipping products with embedded open source software.
"""

---

### Post by chargersfan420 on 2009-05-13
This morning when I got to work, I had a follow-up email from Lenovo asking me to rate their service (from the battery replacement).  I wasn't very nice, and I'm sure my concerns will once again fall on deaf ears.  Still, it was fun.

@ HunterThomson - I've heard of EFI - it is the process that Mac uses to boot.  It's also one of the main reasons that OSX doesn't run on a PC, but i found a company making a chip called the EFI-X, which connects to a USB dongle on a mobo and becomes a bootable drive to emulate EFI.  It is only compatible on a list of motherboards. Not sure how useful it could be to a Linux application... [[COLOR="Blue"]www.efi-x.com[/COLOR]]("http://www.efi-x.com")

What i wasn't aware of is whether or not anyone can set up a small partition for EFI and try to use it themselves on any device... and those links you sent me don't seem to talk about it, unless i was looking in the wrong places...

---

### Post by HunterThomson on 2009-05-13
Ya chargersfan420 stick it to them :) Tell them to support Linux and make laptops that don't brake in a year AND to write BIOS's that are not completely full of bug's.

Chargersfan420: Ewu, ya I was not vary clear was I. No, you can not use EFI on just any board. All of the HP elitebook's have EFI that you can turn on/off if you like. I brought it up to you just becaus your hacking the BIOS right now so I thought if you had not heard of it you mite find it interesting but no you can not use it unless you get a laptop or motherboard that has EFI capabilities. Ya, didn't know mac used it at first but after googleing a bit I have found that Mac is what there talking about 70% of the time, which sucks. I plan on playing aroud with EFI on my new elitebook. But, it is kind of hard to find out what will work and what will not do to Mac crap poping up all the time. I don't realy know if Mac EFI works the same and HP EFI so I have to assume it dosn't. I read a "2007" post saying that ATI drivers will not work with EFI+Linux. I hope that is not the case. I guess I will not realy know untill I try it.

I started a thread about useing EFI with Linux on an HP elitebook...
[http://ubuntuforums.org/showthread.php?t=1157586](http://ubuntuforums.org/showthread.php?t=1157586)

I hope I get it working. Then I can post a "how to" on it and maybe that will get the thread rolling, 20 views no posts.

Boy O' boy, check it out Post# "392" we are realy getting up there. When we get to post 420 you have to take it :P Maybe a litte ASCII art would be in order. I wonder what people think when they see this thread keep poping up to the top of the list. I use to keep clicking "new posts" and help the people I could. I bet a lot of other people do the same thing.

---

### Post by PhilMize on 2009-05-14
Soooo I'm not exactly sure what I did but for some reason my speakers are quieter. I could be going def. Anyways, most of the sound comes from the top speakers and the sub-woofer isn't working any more. I had the alsa drivers configured perfectly and it sounded same as it would on a windows machine. But now its alot weaker sounding.

Is there a way to reload everything back to default? And randomly my front mics are working with skype.

Looks like I'm missing some things if I rem correctly...
[IMG]http://farm3.static.flickr.com/2048/3532077271_8e6e734356_o.png[/IMG]

---

### Post by HunterThomson on 2009-05-15
hum it looks like you got a Kernel update and you need to redo it all. Normaly that dosn't happen though....

---------
But WOW want to talk about crappy BIOS my new laptop will not even see a my drive if it has any extened paritions. They have to be all Primary. I spent 14hr's just trying to get my new laptop to boot yesterday and today.

---

### Post by Zekses on 2009-05-15
About right hinge and warranty - I`ve contacted our local (Russia) Lenovo service center and they told me there`s no problem even if warranty expires... Anyway, mine still has 1 more year...

---

### Post by PhilMize on 2009-05-15
> **HunterThomson said:**
> hum it looks like you got a Kernel update and you need to redo it all. Normaly that dosn't happen though....


O JOY! ](*,)](*,)](*,):lol::lol:\\:D/

---

### Post by PhilMize on 2009-05-15
> **HunterThomson said:**
> **_How to get the sound working_**
Code:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/Desktop/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```


I've just been having one of those days, the problem im having is in the past and Can't remember what I was doing wrong and how I fixed it. This is the error I keep getting:
```

Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

phil@phil-laptop:~$ sudo mkdir -p /phil/src/alsa
phil@phil-laptop:~$ cd /phil/src/alsa
phil@phil-laptop:/phil/src/alsa$ sudo cp ~/Desktop/alsa* .
cp: omitting directory `/home/phil/Desktop/alsa-driver-1.0.20'
cp: omitting directory `/home/phil/Desktop/alsa-lib-1.0.20'
cp: omitting directory `/home/phil/Desktop/alsa-utils-1.0.20'
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2

```

alsa driver, lib, and util are all extracted to my desktop. And I thought what I did before was change the usr to phil, my user account name.

---

### Post by wyth on 2009-05-17
Don't know if this will help (I'm having no sound problems), but there is a launchpad ppa for the latest ALSA that may help.  It's maintained by one of the Canonical staff that works on accessibility issues.  The launchpad page is [here]("https://launchpad.net/%7Ethemuso"), and the ppa is located [here]("https://launchpad.net/%7Ethemuso/+archive/ppa").  The necessary stuff to add to your /etc/apt/sources.list file is below, but don't forget to [add the key]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x0B47F0A6B88A1AA8").

## Alsa
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main #ALSA
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main #ALSA

---

### Post by HunterThomson on 2009-05-17
> **Zekses said:**
> About right hinge and warranty - I`ve contacted our local (Russia) Lenovo service center and they told me there`s no problem even if warranty expires... Anyway, mine still has 1 more year...

That's cool that is not what they told me. All good then I would not worry about it if I were you then.

---

### Post by HunterThomson on 2009-05-17
> **PhilMize said:**
> I've just been having one of those days, the problem im having is in the past and Can't remember what I was doing wrong and how I fixed it. This is the error I keep getting:
```

Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

phil@phil-laptop:~$ sudo mkdir -p /phil/src/alsa
phil@phil-laptop:~$ cd /phil/src/alsa
phil@phil-laptop:/phil/src/alsa$ sudo cp ~/Desktop/alsa* .
cp: omitting directory `/home/phil/Desktop/alsa-driver-1.0.20'
cp: omitting directory `/home/phil/Desktop/alsa-lib-1.0.20'
cp: omitting directory `/home/phil/Desktop/alsa-utils-1.0.20'
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
phil@phil-laptop:/phil/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2

```

alsa driver, lib, and util are all extracted to my desktop. And I thought what I did before was change the usr to phil, my user account name.

Try doing the "apt-get clean" or that command may be wrong but look up the man page for someing that sounds like it.

That is why I hate Ubuntu. The system just assumes your a idot and will not let you do anything if it thinks your worng. But almost all the time the system is wrong.

"But almost all the time the system is wrong." Boy how true that statement is....

---

### Post by HunterThomson on 2009-05-17
Note,

NEVER  BUY ATI !!!!! 

My new laptop is STILL NOT WORKING !!!! I got it on wensday and spent every waking second on it. ~8am->1am everyday.

---

### Post by PhilMize on 2009-05-17
> **HunterThomson said:**
> Note,

NEVER  BUY ATI !!!!! 

My new laptop is STILL NOT WORKING !!!! I got it on wensday and spent every waking second on it. ~8am->1am everyday.

noted... whad you end up getting?

---

### Post by HunterThomson on 2009-05-18
> **PhilMize said:**
> noted... whad you end up getting?

The hp elitebook 8530w it is a MobileWorkstation so it has a strange grafics card Mobiliy FireGL 5700 which is realy a Radeon HD3650.

I am stuck using Ubuntu I cant use it in archlinux do to the ATI. Arg

---

### Post by PhilMize on 2009-05-18
> **HunterThomson said:**
> The hp elitebook 8530w it is a MobileWorkstation so it has a strange grafics card Mobiliy FireGL 5700 which is realy a Radeon HD3650.

I am stuck using Ubuntu I cant use it in archlinux do to the ATI. Arg

Not to be a douche, but i never buy hp for reasons liek that... 

I'm thinking of getting the dell studio xps 13'... I'm assuming there will be good support for it on accounta it's dell... Now I just got to convince my boss that my lenovo is broken and the company needs to get me a new one... maybe its time i go back to windows... tehehe ;)

---

### Post by HunterThomson on 2009-05-19
> **PhilMize said:**
> Not to be a douche, but i never buy hp for reasons liek that... 

I'm thinking of getting the dell studio xps 13'... I'm assuming there will be good support for it on accounta it's dell... Now I just got to convince my boss that my lenovo is broken and the company needs to get me a new one... maybe its time i go back to windows... tehehe ;)

I would have been fine it I got the nvidia card... Well the BIOS didn't even see my SSD if I had even one logical partition. That took me two days to figure out. Then came the ATI problem so I can only use Redhat or Debian based Linux (even then the ATI catalyst is VARY sketchy). Then came the problem with Ubuntu all bugged out with the Intel 5300 wireless card. Now I am using #!Crungbang Linux. It is OK....

Didn't you just get your laptop? I don't know maybe you should just keep it.
Or just start opening and closing it until it brakes... Just a thought.

Trust me, I had to install Vista on this ideapad so I can sell it and boy it is not easier at all. Just a different set of problems. At lest with Linux you can fix the problems. What you want is "Arch Linux" boy as long as you don't have ATI it is hands down the best distro. NO problems at all. It just dose what you tell it, no more no less.

---

### Post by archer6 on 2009-05-21
> **HunterThomson said:**
> [COLOR="Red"][SIZE="3"]FIY[/SIZE][/COLOR]: Lenovo will not even try to fix your laptop if your warranty is up. AND they will not sell you extended warranty if your laptop is more then 30 days out of warranty. SO, there is no hope of fixing my laptop.
[COLOR="Red"]**NOT TRUE!**[/COLOR] Lenovo is very customer oriented and _WILL_ sell you an extended warranty if yours has expired. I know I just got a warranty for mine and it's warranty had expired 68 days ago. Within the United States, call 1-800-656-6291 and a trained service representative will assist you with your warranty upgrade.

> **HunterThomson said:**
> As far as Lenovo droping Linux. I remeber you saying that before. It seems your right they are droping suport.
[COLOR="Red"]**NOT TRUE!**[/COLOR] Lenovo is _INCREASING_support for Linux. Before you post information that is _wrong_ please get your facts straight. 

Cheers...

---

### Post by HunterThomson on 2009-05-21
> **archer6 said:**
> [COLOR="Red"]**NOT TRUE!**[/COLOR] Lenovo is very customer oriented and _WILL_ sell you an extended warranty if yours has expired. I know I just got a warranty for mine and it's warranty had expired 68 days ago. Within the United States, call 1-800-656-6291 and a trained service representative will assist you with your warranty upgrade.


[COLOR="Red"]**NOT TRUE!**[/COLOR] Lenovo is _INCREASING_support for Linux. Before you post information that is _wrong_ please get your facts straight. 

Cheers...

Right on, Glad to here you had a different experience.

Though, You can not buy a Thinkpad with Linux like you could before. They only offer Windows. HP and Dell offer Linux or at lest Linux support as the case is with HP. They will not sell you SUSE Linux installed on there elitebook but they do give tec support for SUSE Linux.

Also, the CEO was quoted as saying that Linux has no future.

Also, it is the Official policy of Lenovo not to sell you extended warranty if your warranty is out of date or past the "grace period". I don't know how long the grace period is but I just assumed it was 30days scents when I called 40 latter it was out of the grace period.

---

### Post by wyth on 2009-05-22
Uh huh.  Okay archer6, I'll show you my facts if you show me yours.

The following are from or about [Lenovo’s Worldwide Competitive Analyst, Matt Kohut]("http://lenovoblogs.com/insidethebox/?page_id=20").  This is the guy who meets with vendors, the press, and Microsoft, and helps determine the market direction that Lenovo will head in.

[LIST]
[*][Linux on Netbooks is Doomed]("http://tech.blorge.com/Structure:%20/2009/04/21/lenovo-analyst-linux-on-netbooks-is-doomed/") (April 21, 2009):
[LIST]
[*]"Linux is going to remain a niche market."
[*]“You have to know how to decompile codes and upload data, stuff that the average person, well, they just want a computer." (My wife asked what that means; she's used Linux for three years and has never decompiled code or uploaded data.)
[*]Here's Kohut saying what Linux needs to do to catch up with Windows: “Linux needs to get to the point where if you want to plug something in, Linux loads the driver and it just works."
[*]“I’ve played around with Linux enough to know that there are some that are better at this than others. But, there are some that are just plain difficult.”
[*]“From a vendor perspective, Linux is very hard to support because there are so many different versions out there: do we have Fedora, do we have SUSE, do we have Turbo Linux?"
[*]“So, until Linux gets to the point where it is easy, it’s not going to succeed on netbooks and I’ve not seen the Linux community make a serious effort to get to that point."
[*]“I think that some of them even like the fact that it is a little difficult and that it isn’t accessible to the average user."
[*]“Linux in netbooks and notebooks I don’t think is ever going to happen.”
[/LIST]
 
[/LIST]

[LIST]
[*][Lenovo on the Future of the Netbook]("http://tech.blorge.com/Structure:%20/2009/05/09/lenovo-on-the-future-of-the-netbook/") (May 9, 2009):
[LIST]
[*]Says Linux is too hard, and Lenovo will be pushing Windows 7 on netbooks, even though he admits Windows 7 will not have a true netbook version.
[/LIST]
 
[/LIST]
Carla Schroder looks into Kohut's pronouncements at *Linux Today *in her April 21, 2009 article [This is Why Lenovo Sucks at Linux]("http://blog.linuxtoday.com/blog/2009/04/this-is-why-len.html").  She finds [this gem on Kohut's Lenovo blog from September, 2007]("http://lenovoblogs.com/insidethebox/?p=97") that starts with "Why on earth would you want to run Linux on a mobile PC?", then snarkily predicts he'll be insulted by those childish Linux users, and then lays out a string of complaints about Linux that might have made sense 5 years ago.  He clearly has all kinds of respect for the community and the product.

Schroder also points out places in Kohut's blog where he discusses Lenovo changing and adapting it's hardware to accommodate shortcomings in Windows 7, while he's telling his audience how great Windows 7 is.  

[LIST]
[*][In a February 26, 2009 blog post]("http://lenovoblogs.com/insidethebox/?p=201"), Kohut starts by telling his audience "You're going to want Windows 7. It’s that good."  In the next paragraph, he notes that Lenovo is developing its own tools to overcome some of Windows 7's incapabilities, like printing to your office computer when you're on your home network.  Lenovo had to develop a tool to make sure Windows 7 doesn't do that.
[/LIST]
 
[LIST]
[*]In that same post, she also finds this gem from Kohut: "Yet, our dilemma is clear – at what point does Windows offer “good enough” functionality that we should abandon our own tools and focus on something else?"  Check that again; he's talking smack about Linux, pushing Windows like its Viagra, and in the same breath, admits Windows doesn't offer "good enough" functionality.
[/LIST]
So -- did you catch all that?  Linux is far too hard for anyone to use, yet Lenovo is spending cash to develop technology that will pick up the slack on known Windows shortcomings.  Schroder puts it best when she says this is the tail wagging the dog.

But I have a hard time believing a company would willingly invest that much time and cash to fix something they admit has flaws unless the OS they're developing tools for already made a deal with them, and there's little choice.  Reading his attitude toward Linux sounds like he's had a few lunches with Balmer -- and that's his job (to have lunch with Balmer and people like him).   It sounds like Lenovo, at least when it comes to netbooks, had determined their position long before they took a look at either technology's strengths and weaknesses, and are now justifying that choice.

Besides, if Linux was as bad has he suggests, he wouldn't need to tear into it in his blog or in interviews.  It would be self-evident.  If Windows 7 was that good, he wouldn't need to sneak in the bits about them creating tools to fix its flaws while selling it like some carnival barker.  The tools wouldn't be necessary.

Yet he does tear into Linux, and crows about how Lenovo is diving head-long into the Windows 7 space.  That suggests to me that they're trying to poison the well; they've already got a deal with Microsoft, feel threatened by Linux (rightfully or not), and need to spread as much bad news about their perceived competition ahead of time in the hopes of guaranteeing a few more sales.

This is the last Lenovo I'll buy.  I may sell it to my brother, but somehow I feel like that'd be unethical.

By the way, [Dell just featured the Inspiron Mini 10v running Ubuntu, Ubuntu Netbook Remix, and Android]("http://www.electronista.com/articles/09/05/20/dell.mini.10v.android.demo/").  I think that's three more distros than Kohut and Lenovo could handle.

-------------------------------------

The Access Connections baffles me.  On three laptops running multiple distros, I've never had a problem going from my office at school to my apartment, and the computer decided to print to my office printer rather than the home printer.

On that line about too many distributions from a vendor perspective: I'm not sure he realizes that the underlying structure is pretty much the same on any distribution, it's the package manager and desktop environment a vendor would need to worry about -- and there are about two of each to choose from, RPM or DEB, and Gnome or KDE. Or maybe he does realize it and is just talking crap, but then the examples he gives -- Fedora, Suse and Turbo Linux -- are all RPM-based distros.  Besides, look at what Dell does; offer basic support for Ubuntu, and for the heavier stuff, contract out to Canonical.  It's not like Lenovo couldn't contract all that complex support out to Novell or Red Hat.

I'd really like to know what he means by "I've played around with Linux enough to know."  Is that day-in, day-out steady use for your standard OS?  How many days -- a week?  Month?  A few years?  Or was it a few minutes before he just shut it off, said "I've seen enough," and got ready for a meeting in Redmond?

---

### Post by archer6 on 2009-05-22
**Please understand that I am _not_ being critical of you, as I respect your thoughts and opinions.**

I've simply asked that you do not post false and misleading information. I do not blame you, as after all it is others that have mislead you. 
 
> **HunterThomson said:**
> You can not buy a Thinkpad with Linux like you could before. They only offer Windows.
**Your statement above is FALSE. **

The company I run is currently using 52 brand new (one month old) ThinkPads supplied to us by Lenovo with SLED10 Suse Linux. These replaced the prior Linux ThinkPads that were supplied by Lenovo. In fact I'm writing this post from my corporate Suse Linux ThinkPad at this very moment. 

[COLOR="red"]The model is: ThinkPad 7733-3BU pre-loaded with SLED10 Linux[/COLOR]

We have deployed ThinkPads with Linux preloaded for over five years. 
> **HunterThomson said:**
> Also, the CEO was quoted as saying that Linux has no future. 
Let's remember the politics surrounding the relationship with Microsoft. Just like any politician a CEO is going to say whatever it is that is appropriate for the audience they are speaking to. 
> **HunterThomson said:**
> It is the Official policy of Lenovo not to sell you extended warranty if your warranty is out of date or past the "grace period".FIY: Lenovo will not even try to fix your laptop if your warranty is up. AND they will not sell you extended warranty if your laptop is more then 30 days out of warranty. SO, there is no hope of fixing my laptop.
**Your statement above is FALSE.**

[COLOR="Red"]**Lenovo's Official Policy** is to sell Laptops with full warranty coverage, and offer extended warranties for those machines. Even if the machine is out of warranty you may still buy an extended warranty.[/COLOR]

[COLOR="Red"]Lenovo **WILL** fix your laptop if you do your part.[/COLOR] And what might that be? Purchase an extended warranty since you allowed yours to lapse and now expect them to work it. I gave an example in my earlier post where mine was out of warranty for over two months and they happily sold me extended coverage. At this point, since it's obvious that no one is choosing to believe the facts I've stated and no one has made any effort to find the information on the web site I will make it even easier for you to confirm that I am indeed correct. 

Lenovo is a huge international company and operates in professional manner. Are they perfect? NO. Does everyone in their company know every policy? NO. Do they make mistakes? Yes. Therefore by simply speaking with one person who tells you no, is rather meaningless. It's unfortunate but as consumers today we must be assertive and in some cases make more than one attempt to get something done. 

Lenovo is so serious about providing great service they have not one but two warranty departments. They have the in warranty department, and the post warranty department. Why this is news to you is something that I cannot understand. Personally I have over 20 ThinkPads and each time I've called there has been no trouble either extending the warranty on and in-warranty machine, or an out-of-warranty machine. Here are the web links to prove it. 

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=UPGD-WARNTY](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=UPGD-WARNTY)

[http://www.pc.ibm.com/us/accessories/services/thinkplus.html](http://www.pc.ibm.com/us/accessories/services/thinkplus.html)

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=TPAD-WSU](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=TPAD-WSU)

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=TPAD-PWMA](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=TPAD-PWMA)


I'm sure you will feel better now to know that you can have Lenovo repair your machine. 

They do great work and offer fast turnaround times. I had a hard drive die on one of my personal ThinkPads after it was 3 years old, they replaced it with a new hard drive and returned it to me in just 48 hours. 

It is my pleasure to provide the factual information for those who have ThinkPads, IdeaPads, and other Lenovo notebooks, such as the 3000, and Value Lines. 

Cheers...:D

---

### Post by archer6 on 2009-05-22
> **wyth said:**
> Uh huh.  Okay archer6, I'll show you my facts if you show me yours.
The gentleman you reference is but one individual in the upper management team of Lenovo. Being an international company, they have a huge challenge meeting peoples expectations and navigating the treacherous waters of global commerce. The business of mobile computing is a highly charged, very political arena in which they must operate. The gorilla in the room is Microsoft and Lenovo is like Dell land the others, they must watch how they manage the dialog that surrounds various press releases, corporate meetings, public speaking engagements, and responses to the press. Everyone has an agenda. So often times what are perceived as "facts" as you cite here, is really nothing more than the speech of the moment. For some real time facts and feedback from a corporate perspective, backed by actual experience, I refer you to my previous post. 

[http://ubuntuforums.org/showthread.php?p=7328736#post7328736](http://ubuntuforums.org/showthread.php?p=7328736#post7328736)

Cheers...

---

### Post by PhilMize on 2009-05-22
> **HunterThomson said:**
> 
Didn't you just get your laptop? I don't know maybe you should just keep it.
Or just start opening and closing it until it brakes... Just a thought.

Nah I'v had it a little over a year... lol and funny you say that! the hinge is starting to go!

---

### Post by HunterThomson on 2009-05-22
> **PhilMize said:**
> Nah I'v had it a little over a year... lol and funny you say that! the hinge is starting to go!

Owe ya making that "click" as it closes... That is the only warning you get. But, it is not really a warning because mine made a "click" for months. Then one day "SNAP" and it was broke.

My new elitebook has a hinge that is tested to open and close 20,000 times. That is about 10 times a day for 10 years :)

---

### Post by HunterThomson on 2009-05-22
PhilMize: If I were you ( I guess you know I am going to say this) I would get the laptop I got. If you don't mind using Ubuntu then you can get the same one I got for $800 on tigerdirect. However, your better off paing more and getting one with the nVidia card for ~$1,100. Pretty much everything works out of the box with ubuntu.

also the differences between the 8530p personal computer and the 8530w MobileWorkstation is really the warranty. The workstation has standard 3year P/L + 3year OnSite repare. The Personal Comptuer dosn't have the OnSite. With the WorkStation you can replace any non sealed part Like CPU, Grafics card, RAM, HHD without voiding warranty. I don't think you can do that with the PC. OWE an the PC has a different Mother Board that can't be upgraded to as nice of a CPU as my WorkStation can.
 
Here is the thread I started for it.

[http://ubuntuforums.org/showthread.php?t=1166667](http://ubuntuforums.org/showthread.php?t=1166667)

---

### Post by wyth on 2009-05-23
> **archer6 said:**
> The gentleman you reference is but one individual in the upper management team of Lenovo. Being an international company, they have a huge challenge meeting peoples expectations and navigating the treacherous waters of global commerce. The business of mobile computing is a highly charged, very political arena in which they must operate. The gorilla in the room is Microsoft and Lenovo is like Dell land the others, they must watch how they manage the dialog that surrounds various press releases, corporate meetings, public speaking engagements, and responses to the press. Everyone has an agenda. So often times what are perceived as "facts" as you cite here, is really nothing more than the speech of the moment. For some real time facts and feedback from a corporate perspective, backed by actual experience, I refer you to my previous post. 
Cheers...

I fail to see how your statements qualify as contradictory evidence for Lenovo increasing their Linux support.  

First, long before Lenovo had the ThinkPad line, the ThinkPads supported enterprise SLED and Red Hat. When Lenovo bought this hardware division from IBM, that came with it; it would be bad business to just drop support for all those users (probably like your company).  So that support was grandfathered in, and it's specialized.  But that's not what's in question here, since we're all home end-users, getting machines one at a time, and not buying a gross of specialized machines for a business.

Second, the "being political" line doesn't wash.  You say they are like Dell and the others and have to manage the dialog.  Have you looked at Dell and the others lately?  Dell, HP, MSI, and the mighty little System76 are all offering Linux options to home users (which is partly why I added the [link]("http://www.electronista.com/articles/09/05/20/dell.mini.10v.android.demo/") to Dell showing three distros on their Mini 10v).  Granted, every hardware manufacturer seems to have that proviso on their web pages that they "recommend Windows Vista" -- it's like the tag on a mattress.  But that doesn't stop those companies from either offering Linux options, supporting those options, and they don't insult the community with misinformation.  

Besides, from a Linux perspective, how is it anything *but* impolitic to repeatedly say that Linux has no future and Lenovo will only be supporting Windows 7 on future netbooks and notebooks?  Do you think Kohut's just winking behind his back?  That's some political strategy, because if I hear a spokesperson say over and over again that he wants to slash the very thing I use for work, I don't support that outfit.  If they're trying to grow their Linux user base, Kohut has a funny way of doing it.  If he truly thinks Linux is that bad and is working to make sure their end-user customers can't easily get it on their machines, all that requires is a brief boiler plate statement on the site, not slams.

Third, if you're certain they're increasing their Linux support, show some proof here.  Don't just tell us you have the facts, *show us*.  Go to their web page, and find us one Linux offering for end users, *not* enterprise deployments. I could save you some time; I went to the page and searched before I wrote my earlier piece -- because, y'know, you were all about the facts.  All that comes up is support pages for enterprise deployments.

I offered a number of quotes from one of the more prominent public faces of Lenovo for the average user.  Not only do those quotes show that they racing away from Linux support, but Kohut also decided that Linux is too hard for average users, and that Windows 7 is all unicorns and candy floss and all Lenovo users will love it.  He said this while admitting that they're investing time and money to develop tools to take care of Windows 7 shortcomings, shortcomings that don't exist on Linux, or if they did, would most likely not require the company to build its own tools, because the community often steps up.  

Since those are an official spokesperson's statements on the record, placed in the press and on their official sight, that stands as factual evidence.  Check their support forums; there have been only seven threads tagged Linux in all of 2009, and some of those were started in 2009. Combine that with the lack of Linux offerings for the end user on the site, and it adds up to Lenovo not interested in supporting linux beyond the enterprise element that came with the IBM sale.  (I'd like to see if that support has increased or decreased since the IBM deal.)

Yes, his statements are political -- politically, it seems Lenovo is already in Microsoft's back pocket whether they want to be or not, at least for end users.  I imagine it came down to some deal done a year ago or so when the markets started to contract; Lenovo started looking around, and Microsoft offered them some stability if they went with only Microsoft products -- *for end user*s.  I remember there was a lot of talk about Linux on some of their ultra-light notebooks, but that just fizzled. 

So: I'm not as worried about the warranty and all that; those things can be haggled out if need be.  But please don't tell use we're spreading lies, or don't have our facts straight, and presume to tell us you do have your facts straight, when you don't actually provide factual evidence and ignore the evidence presented to you.  (Look up "special pleading.")  

If you can find us a page on Lenovo's customer site that offers Linux options -- for the *end user*, not the enterprise-- then we'll stand corrected.

---

### Post by HunterThomson on 2009-05-23
Boy, somehow I just totally missed all this lenovo linux talk until now.

Though, like I thought form the start, Wyth would be much better at handling this talk. As archer6's quote form me was just a reply to Wyth.

Any how, calm down archer6. I never thought anyone would take what I say at 11PM on the Internet as FACT. I believe people are smart enough to think for themselves. I also added a disclaimer to my posts saying in short I am pissed so look into it if you care but don't just act because some pissed off guy on a forum was talking smack ;) 

I am sorry that when I called the guy on the phone told me that they didn't sell warranty to a computer after the warranty was up for a certain amount of time. That sounded kind of normal to me... though it still pissed me off.

As for them not selling Linux on a Thinkpad. Ya, I am sure if you call and want 30 they will be happy to make $30,000 and put Linux on your thinkpads rather then you go to Dell. What I was talking about is you can go to Dell's website and HP's web site and get 1 laptop with Linux installed or get a HP and then install SUSE linux on it and call up HP tec support and get support. When I go to Lenovo's web site I can't find a Thinkpad with Linux. Though if you get the X series you can get Freedos. But you can not get freedoss on the vary common R or T series. If you buy a Thinkpad T or R searies your helping MicroShaft sew Linux developers and increasing there sales #'s.

Dell is vary vary Linux supportive. If you don't know how to build a desktop computer you can have Dell build you one and get any one you like with Freedos or Linux. They have Linux pre installed laptops on there web site. Mr. Dell him self uses Ubuntu Linux on his laptop. That is not propaganda that is really Linux support. HP spends money on OpenSource projects like ELILO and they even have a Linux support line 
1-888-HP-LINUX. 

[http://h20341.www2.hp.com/enterprise/cache/309906-0-0-0-121.html](http://h20341.www2.hp.com/enterprise/cache/309906-0-0-0-121.html)

[http://linux.dell.com/](http://linux.dell.com/)

Come on you don't need me to give you facts all you need is google. Dell and HP are totality Linux supportive and Lenovo is not. The reason why this pisses me and Wyth off is that IBM is one of the Kings of Linux. I think I even remember them paying for Lawyers to fight MicroShaft in bull crap law suites brought up by M$ only to drain $ from the Linux development and instil fear into the harts of Corporations that are thinking about switching to Linux. So now the top Linux Laptop "Thinkpad" is owned by some company whose Linux support is questionable at best and down right anti-Linux at worst.

Lenovo only has bad Linux press or it is really a "IBM" web site.

Just google...

HP Linux support
Dell Linux support
Lenovo Linux support

I keep talking about HP, Dell, and Lenovo because they seem to me to be the top corporate Laptop manufactures. And, I think that it is just dumb to buy a desktop computer... Just build your own. And, as for servers IBM still makes the servers and Dell and HP sell there servers with Linux. Also, come on, if your building a server you have to have your hands tied by management or just not care about security+performance to run Wincrap on them. And, I put security+performance because you can sacrifice performance in a Wincrap box by running all kinds of applications monitors and virus protection in order to make up for core security flaws in Wincrap's (total lack of a) security model.

---

### Post by PhilMize on 2009-05-23
> **HunterThomson said:**
> PhilMize: If I were you ( I guess you know I am going to say this) I would get the laptop I got. If you don't mind using Ubuntu then you can get the same one I got for $800 on tigerdirect. However, your better off paing more and getting one with the nVidia card for ~$1,100. Pretty much everything works out of the box with ubuntu.

also the differences between the 8530p personal computer and the 8530w MobileWorkstation is really the warranty. The workstation has standard 3year P/L + 3year OnSite repare. The Personal Comptuer dosn't have the OnSite. With the WorkStation you can replace any non sealed part Like CPU, Grafics card, RAM, HHD without voiding warranty. I don't think you can do that with the PC. OWE an the PC has a different Mother Board that can't be upgraded to as nice of a CPU as my WorkStation can.
 
Here is the thread I started for it.

[http://ubuntuforums.org/showthread.php?t=1166667](http://ubuntuforums.org/showthread.php?t=1166667)

Hurm... I'll look into it... I don't know though I just have this wall in my head that won't let me buy an HP. I've had such bad luck with them in the past... Plus I can get the Dell for $900. nedfovbhw9t42h0jv95jgowenbowr no n!!! Decisions! Decisions!

---

### Post by wyth on 2009-05-23
> **PhilMize said:**
> Hurm... I'll look into it... I don't know though I just have this wall in my head that won't let me buy an HP. I've had such bad luck with them in the past... Plus I can get the Dell for $900. nedfovbhw9t42h0jv95jgowenbowr no n!!! Decisions! Decisions!

Phil, I saw this yesterday, a Cyber Cynic article from Computer World.  I don't know if this is the sort of thing you're looking for, but it's at least interesting:

[A+ for Dell's new Ubuntu netbook]("http://blogs.computerworld.com/a_for_dells_new_ubuntu_linux_netbook")

I don't know if this is the sort of thing you're looking for; I've just had feelers out for these sorts of stories for my brother.  But he's reviewing the [Dell Latitude 2100-n]("http://http://www.dell.com/content/products/productdetails.aspx/laptop-latitude-2100?c=us&cs=RC956904&l=en&s=hied"), which can't be ordered with either Ubuntu or Windows.  He's using Ubuntu 8.10 (Steven Vaughn-Nichols writes almost exclusively about Linux), and he says it ran like a charm -- no problems whatsoever.  It found all his networks, connected flawlessly, and just worked.  

Some of the nicer bits: This is a netbook, with a 10.1' LED display.  But it's much more expandable than some others:

[LIST]
[*]Starts with 512MB's of SO-DIMM RAM, but can be expanded up to 2GB
[*]Hard drive options: Comes with a 16GB solid state drive, can go up from there to the hunky SATA drives.
[*]1.68GHz Intel Atom N270 chip
[*]Intel 950 GMA gfx
[/LIST]
I just saw this one for the first time last night, and it's designed for education.  It looks like the main market is elementary/middle/high school, but the review doesn't seem to find any market-specific issues that caused him any trouble.  Some of those education-space specifics:

[LIST]
[*]Rubberized covering; reviewer said it felt very rugged
[*]Optional touch screen
[*]A network monitor light on the back side of the cover, to let the teacher know when a student is surfing the web (as a teacher, I'd love that)
[*]Anti-microbial keyboard
[/LIST]
The whole thing starts at around $370 for a basic model.  ([Customize it here]("http://www.dell.com/content/topics/reftopic.aspx/pub/products/latit_kat?c=us&cs=RC956904&l=en&s=hied&%7Esection=latitude-2100").)  They note you can get it with Windows, but that's $30 more, and if you want MS Office, they recommend upgrading from a solid state drive to at least an 80GB SATA drive.  So if you want the Ubuntu option and can do your officework on the cloud, that could save weight/money and add speed. ([Ubuntu One]("https://ubuntuone.com/") would be a good tie-in to a netbook like this.)

---

### Post by HunterThomson on 2009-05-23
Ya, as you were talking about how you want a light laptop for inventory I was thinking you mite like a netbook too. However, you don't get the power. What would be best is to have a nice laptop and a cheap netbook and a server at home streaming video and music while downloading torrents for you.

Also, I am not saying don't go for Dell. They would be a grate company to support(really, far more Linux supportive then HP...). I also think you will get good quality from them. To be honest my new laptop has one dead pixel but it is in the bottom left and the high rez screen makes the one pixel vary vary small, speck of dust.

Funny you have a mental block about HP. I had a mental block about Dell. I got a really nice HP ipaq a long time ago and always though they had good stuff after that. When I was growing up my computer buddy always hatted Dell.

My problem with Dell laptops right now is, I can't afford their mobile-workstations so the only one I would want would be a latitude E6500. The problems with the latitude Exx00 are endless at this point. The optical drive firmware is all messed up so it dosen't work in windows or Linux, the speakers are suppose to suck... Owe ya and the Ethernet is not suppose to work with Linux to well. 

But if your looking at a XPS then it is a totally different story. I think I am only going to buy Enterprise class laptops form now on. Maybe, only Mobile-Workstations from now on....

---

### Post by PhilMize on 2009-05-24
I saw the Latitude 2100-n on lifehacker and really thought it was cool. I am going to see if I can check it out in person. And ya know i thought about it. I really don't use my laptop for alot of heavy tasks. So a netbook is an option. See what I don't understand is, why are the "business orientated" laptops from dell more expensive then their personal laptops which are better specced?

---

### Post by HunterThomson on 2009-05-25
I think the price is higher on Business class laptop's because the warranty on business laptops is far better most of the time. 

Like I was saying about my elitebook. I can change out RAM, HHD CPU and all that without voiding warranty. I can't even find a "Void Warranty" sticker anywhere and I have even popped off the keyboard and looked at the CPU and GPU and stuff. 

That is the other thing about businesses laptops. You can actual change out parts. The keyboard just pops right out the fan/heat sink you can take out. It is all modular and removable stuff "FRU's". OR, if your not upgrading. The next day OnSite service benefits form this too. If your keyboard is DOA they just have a guy come to your business or house and pop a new one in, in like 10 sec's. No need to mail your laptop to Dell or HP for a week and a half.

Business laptops are generality more upgradeable then PC's. They also have stronger build quality. Like my elitebook and the Latitude E both meet MIL-STD 801 Military standards for rugedness.

So, the differences in business class laptop's and like a XPS is not the GPU or CPU or RAM... They are all the same really. It is all the little things that are better. Like not having a "Void Warranty" sticker on your RAM stick.

I think this is worth paying a one or two or even $500 more for. 
But hay that is me.

---

### Post by nmfralich on 2009-05-26
If I may, I'd like to interrupt this discussion briefly to revisit the webcam issue, which is still upside down on my computer.  I haven't had time recently to do much about it, but I did find this interesting post and was hoping somebody might be able to take a look and see if it sheds any light on the problem.  The initial HOWTO is for a different computer, but the comment is based on the Y510.  The only difference for me was that I used udevadm instead of udevinfo, because for some reason I didn't have that and couldn't install it.  Anyway, I'd really appreciate somebody taking a look, thnx!

nmfralich

[http://onlyubuntu.blogspot.com/2008/12/how-to-fix-upside-down-webcam-image-in.html]("http://onlyubuntu.blogspot.com/2008/12/how-to-fix-upside-down-webcam-image-in.html")

---

### Post by wyth on 2009-05-26
> **nmfralich said:**
> If I may, I'd like to interrupt this discussion briefly to revisit the webcam issue

I might look into that later.  I always ignored it in the past because I had little use for the web cam, but now I do.

One thing I also saw a while back (possibly in this thread) is someone who just dismantled the screen, manually flipped the camera around, and put things back -- no more upside-down camera.  But that takes a little mechanical aptitude and bravery, and I haven't looked into how the screen is put together.  

Given the other mechanical issues people have had, I'm also a little hesitant to risk loosening something that won't go back into place; right now, I'm having no mechanical issues with my Y510.

---

### Post by HunterThomson on 2009-05-27
> **nmfralich said:**
> If I may, I'd like to interrupt this discussion briefly to revisit the webcam issue, which is still upside down on my computer.  I haven't had time recently to do much about it, but I did find this interesting post and was hoping somebody might be able to take a look and see if it sheds any light on the problem.  The initial HOWTO is for a different computer, but the comment is based on the Y510.  The only difference for me was that I used udevadm instead of udevinfo, because for some reason I didn't have that and couldn't install it.  Anyway, I'd really appreciate somebody taking a look, thnx!

nmfralich

[http://onlyubuntu.blogspot.com/2008/12/how-to-fix-upside-down-webcam-image-in.html]("http://onlyubuntu.blogspot.com/2008/12/how-to-fix-upside-down-webcam-image-in.html")

_Owe, Any time we get off topic like this, feel free to jump in with something that we should really be talking about ):P_

Well I looked at that link and I must say it shows real promise. I meen hell I see no reason it should not work. What your doing it just saying to the computer... 
"Hey I don't care why you have some problem with portraying the webcam up right.. what ever. Just flip it, OK."


OK, I did some reading.
You still have all these commands...
lsusb
modinfo
udevadm info

It seems the udevinfo command has been depreciated. This command should do the same thing.

```
udevadm info --query=all --name=/dev/video0 --attribute-walk
```

I don't really think you need to do this because the command up above lists all the attributes. But hay why not.

```
modinfo "Driver name lenovo web cam or something I think"
```
(with out the... "")

Then look to make sure the "vflip" or something that looks like it is there. If vflip is there then you can test to make sure it works by doing this.

```
sudo modprobe -r DriverName
sudo modprobe DriverName vflip=1

```
If in the "udevadm info bla bla command it showed the "vflip=1" then change the above command to "vflip=0" instead.

Now fire up cheese or whatever and see if it worked. If it did, you can make the change stick by running this command.

```
echo "options DriverName vflip=1" | sudo tee -a /etc/modprobe.d/options
```

If the command above dosen't work i.e. on reboot you open up cheese and the camera is upside down agin. Then the above command didn't work. I don't really know what it is doing anyway. I meen I know it is making a new file /etc/modprobe.d/options but I have never done stuff like this like that before. I always just add the line of code to the /etc/modprobe.conf file. Maybe the /etc/modprobe.d/options has meed depreciated. Or if that dosen't work you can just make a little script and set it to run at boot time.

I need to dig through my documents to find out how to make a script run at boot with root privileges on a traditional Linux system i.e. not ArchLinux's BSD rc stile. So, just try that strange /etc/modprobe.d/options thing and if it dosn't work I'll look and find out how to set a scrip to run with root privileges at boot time.

---

### Post by chargersfan420 on 2009-05-27
My apologies for rumbling off-topic again, but here's my two cents.

Lenovo called me two days after i filled out my customer (dis-)satisfaction survey.  The guy on the other end of the phone call was also a Canadian, who completely agreed with me on my points (much less selection in Canada, Linux support is terrible, etc).  He told me he would pass along my complaints to his superiors (and also admitted he didn't think it would go anywhere).  He even said he "hates it too" when Lenovo makes models (like the Y730) and NOT offer them in Canada... we're right freaking here, why the hell not?

This is one of the main problems with Lenovo - they treat their customers differently based on location.  In some places (eg. Hawaii) they maybe don't want to offer to extend your warranty.  I bet they won't for me just because they don't want to have to keep spare parts for this and similar models in Canada.  That's why they discontinued the Y710 up here sooner than the states, and why they won't offer Y730's up here.

At one point in the call he asked me "So, basically your issue with Lenovo here is in the product itself and not the service given during the battery replacement?"  To which i said yes, but i strongly feel that this service request wouldn't have been necessary if i didn't have issues with the product itself.  Seems to me that their customer satisfaction department is only concerned with making sure the customer service department is doing their jobs - not if actual customers are happy with Lenovo.

Oh, and @ PhilMize
Hunter is mostly right - business laptops are all about the warranty.  You get a longer term with quicker shipping, and some companies also supposedly encrypt hard drives to protect against theft in business machines.  I didn't buy that last one when the sales guy pitched it to me, thinking if someone really wants to read this hard drive, they'll find a way... all in all i didn't see the value in it when buying for a medium sized business without a huge tech budget and end users with very basic requirements, but in personal gear you may feel a bit different.  Think of it as your insurance policy on the machine.

Oh, and I missed post 420!  Damn!

Ok, back to on-topic:

Sorry i can't be much help with the webcam.  This one was a bit troublesome but seemed to have fixed itself.  There must be a better way than opening the case though.

I've also noticed that ALSA seems to work better than ever.  Pulseaudio started doing weird things like locking up Virtualbox every time i shut down, and no longer serving totem, so i turfed it, and for the first time ever ALSA seems to play sounds from multiple programs at once.

---

### Post by nmfralich on 2009-05-27
@ HunterThompson

Thanks for the speedy response and the help.  Unfortunately I've yet to find the attribute vflip on my system.  Below is the output of udevadm:

!!!!@!!!!-laptop:~$ udevadm info --query=all --name=/dev/video0 --attribute-walk

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="Lenovo Easy Camera"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0':
    KERNELS=="2-6:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{modalias}=="usb:v5986p0200d0004dcEFdsc02dp01ic0Eisc01ip00"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"
    ATTRS{interface}=="Lenovo Easy Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-6':
    KERNELS=="2-6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="12"
    ATTRS{idVendor}=="5986"
    ATTRS{idProduct}=="0200"
    ATTRS{bcdDevice}=="0004"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{product}=="Lenovo Easy Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="32"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.28-11-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x17aa"
    ATTRS{subsystem_device}=="0x3d88"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d00002836sv000017AAsd00003D88bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

And having found no other suitable driver than uvcvideo, I put that into modinfo and got the following:

!!!!@!!!!-laptop:~$ modinfo uvcvideo
filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
version:        v0.1.0
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@skynet.be>
srcversion:     F6FE641F5413EC1A6EA9193
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v064EpA115d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0303d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0300d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0203d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0202d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0200d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0141d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0105d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0104d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0102d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0101d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0100d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v1C4Fp3000d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d00*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d01[0-1]*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d012[0-6]dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A33d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp8A31d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v090CpB371d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05E3p0505d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v05ACp8501d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v045Ep0723d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v041Ep4057d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v0402p5606d*dc*dsc*dp*ic0Eisc01ip00*
depends:        videodev,v4l1-compat,compat_ioctl32
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           quirks:Forced device quirks (uint)
parm:           trace:Trace level bitmask (uint)


Any advise you might have on what I've done wrong/not done at all to find the vflip attribute would be greatly appreciated.

Thnx

---

### Post by nmfralich on 2009-05-27
I've done a little more sniffing around and wanted to add that I neither have a /etc/modprobe.conf file or a /etc/modprobe.d/option file.  Not sure what that means, just thought I'd toss a little more info into the mix.

---

### Post by wyth on 2009-05-27
I think -- *think* -- that the vflip is a feature that just isn't available for those cameras, nor have I seen any success installing a driver with that feature that also gets the camera to work (and I think kernel updates would mean changing the driver again).  

But that's all info I found a long time back when I first tried to mess with the camera.

---

### Post by PhilMize on 2009-05-27
I just bought the new dell latitude 2100n with all the available bells n' whistles...
I'll update this with my first impressions when i get it.


Dell Latitude 2100 N-series - New!
Latitude 2100n, Ubuntu Linux version 8.10 $569.00
Processor: Intel® Atom® Processor N270, 1.0GB int memory, Chalkboard Black
Additional Memory: 1.0GB, DDR2-800 SDRAM
Internal Keyboard: Internal English keyboard with Anti-microbial protection
Graphics: Intel® Graphics Media Accelerator 950
Primary Storage: 16GB Mobility Solid State Drive
LCDs: Chalkboard Black 10.1inch WSVGA Touchscreen LED Display with camera
Operating System: Ubuntu Linux version 8.10
Bluetooth: Dell Wireless® 365 Bluetooth Module
AC Adapter: 65W A/C Adapter (3-pin)
Wireless LAN (802.11): Intel® WiFi Link 5300 802.11a/g/n Mini Card
Primary Battery: 6 Cell Primary Battery
Hardware Support Services: 1 Year Limited Warranty and 1 Year

Subtotal: $569.00
Shipping and Handling: $19.99
Sales Tax: $36.83
Total Amount: $625.82

---

### Post by HunterThomson on 2009-05-28
nmfralich: Well it seems like the driver is uvcvideo. I found this thread and it seems they fixed it with a patched driver. Here on page 11. Kind of cryptic but it looks like it mite work.

[http://ubuntuforums.org/showthread.php?t=838210&page=11](http://ubuntuforums.org/showthread.php?t=838210&page=11)

PhilMize: I see you have already found your support thread :) I saw your post. One thing about this laptop you should tell your new friends is that you have the same intel wireless card I do "Intel 5300." Ubuntu 9.04 dosen't play nice with the driver. You can serf the web but any download like up-dates... get badly corrupted and the corruption will brake the Debian Aptitude package manager. I have yet to find a fix. It seems it is just a problem with Kernel 2.6.28. Ubuntu 8.10 with Kernel 2.6.27 it works fine and in Archlinux on Kernel 2.6.29 it works fine. So, [COLOR="Red"]DO NOT UPGRADE TO 9.04[/COLOR] If you guys find a fix let me know. Right now I am forced to use my Linksys WUSB54GC with my hacking "Packet Injection Capable :) " driver. Intel also just released a new driver for this card like one week ago so that mite fix it too.

Other then that it looks like a grate laptop. And kudos for supporting Linux market share. That is the only thing "$$$" that will bring more Linux support from hardware manufactures.

---

### Post by HunterThomson on 2009-05-28
I may have found a way to get the Intel WiFi 5300 to work.

Well I was reading the bug report in launchpad and on 05/23/2009 it seems this guy installed the backports modual and it worked for him.


> I enabled Pre-released updates in the software sources application. Then I installed the package linux-backports- modules-jaunty. The wifi problem seems to have been solved. And I haven't experienced any side effects. I have now disabled the Pre-released updates and hope that all goes well. Maybe this will help others. But I'm just a user trying some stuff and no linux expert so this is all at your own risk.
This also solved another unrelated wifi issue my parents were experiencing.

I think one of two things could have been the reason this worked for him.

1> The backport driver really did the job.

2> He enabled the Pre-released updates... SO, he is now on the new Ubuntu Kernel 2.6.28-12. We are on 2.6.28-11.

I'll try just installing the new Kernel 2.6.28-12 and see if that works first. If that doesn't work, then I'll go back to 2.6.28-11 and install the backports. If that doesn't work then I'll install the new Kernel 2.6.28-12 and the backports and if I get to this point I sure hope it works.

I'll mess with it tomorrow though, because it installs a new Kernel. I don't want to deal with the ATI crap tonight.

---

### Post by HunterThomson on 2009-05-28
Owe I found how to make a script to run at boot time with root privileges.


Put the script in /etc/init.d like so...

```
sudo mv blabla.sh /etc/init.d/blabla.sh
```

Make it executable

```
sudo chmod uog+x /etc/init.d/blabla.sh
```

Make it run at bootup

```
sudo update-rc.d blabla.sh defaults
```

---

### Post by HunterThomson on 2009-05-28
YES :guitar:

I FIXED the WIFI Problem with intel WiFi 5300 driver :D

I'll put the "How To" on the support thread for my laptop in the first post with all the other "How To"'s
Here...

[http://ubuntuforums.org/showthread.php?t=1166667](http://ubuntuforums.org/showthread.php?t=1166667)

OK the how to is in there.

I am happy to say we got EVERYTHING working on the HP elitebook 8530w w/ ATI FireGL v5700. Well all but the fingerprint reader but from what I understand there just is not a Linux driver for the "AuthenTec with 08ff:2810"

Also, Ya my buisness laptop dose have BIOS level Full disk Encription. However, I don't use it. If I want to encript something TrueCrypt is a better option I think.

BUT, the thing with that Full Disk Encryption is this. If your /root partition is not encrypted someone can just boot up a LiveCD and then mount your /root partition and change the Root password. Then boot back up and now they have Root on your box. If your disk is encrypted they can't do that.

---

### Post by PhilMize on 2009-05-29
LOL! Boy hunter youve been a busy little bee! haha and dont worry just because i got a new laptop doesnt mean im ditching my hinge broken lenovo... ive got some plans for it HE HE HE...

and also i wouldnt dare go to 9.04... im just going to wait till 9.10 comes out... 9.04 was effed up on this lenovo and another hp i use and a few desktops all the same problem with video drivers soo im just gunna wait it out...

grats though on figuring the driver out!

---

### Post by wyth on 2009-05-29
Hey Phil, do you know how soon your Latitude is arriving?  I know some people who are interested in them, and I'd love to get your response before I recommend them.

By the way, I'm still on the Lenovo boards, and responded to a recent post asking the community what we'd like to see in the new notebooks.  I basically gave a short version of what went down here last week with a link to my argument.  Two of the Lenovo employees responded back, cordially, and another Linux user piped in his disappointment.  Interesting...

[Here's a link]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=10965#M10965"); I have yet to respond -- been too busy.

---

### Post by HunterThomson on 2009-05-30
> **PhilMize said:**
> LOL! Boy hunter youve been a busy little bee! haha and dont worry just because i got a new laptop doesnt mean im ditching my hinge broken lenovo... ive got some plans for it HE HE HE...

and also i wouldnt dare go to 9.04... im just going to wait till 9.10 comes out... 9.04 was effed up on this lenovo and another hp i use and a few desktops all the same problem with video drivers soo im just gunna wait it out...

grats though on figuring the driver out!

Yes I have :) I started a kick *** support thread though haven't I? Just taking what we have here and spreading it around. Well I guess we are slacking on the web cam though....

Ya, it kind of seems like all the x.04's suck and the x.10's are stable.

WAY off topic but I just got my first e-cigarette today and it is amazing! :) I am never smoking a real cigarette ever again. This is way better. Satisfies my addiction to nicotine and my habit of chilling out and thinking while having a smoke. If you know anyone that smokes I would highly suggest you tell them to get a DES801 form dietsmokes.com and some liquidXpress Mr. Bean e-liquid. Also, tell them about e-cigarette-forum.com

---

### Post by PhilMize on 2009-06-01
> **wyth said:**
> Hey Phil, do you know how soon your Latitude is arriving?  I know some people who are interested in them, and I'd love to get your response before I recommend them.

By the way, I'm still on the Lenovo boards, and responded to a recent post asking the community what we'd like to see in the new notebooks.  I basically gave a short version of what went down here last week with a link to my argument.  Two of the Lenovo employees responded back, cordially, and another Linux user piped in his disappointment.  Interesting...

[Here's a link]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=10965#M10965"); I have yet to respond -- been too busy.

Should be in either today or tomorrow... *checks tracking number*

not supposed to be in till the 24th... :( they say its "being assembled" but I think its the same thing as the Australian's where they have too wait a whole 2 weeks...

---

### Post by HunterThomson on 2009-06-01
> **PhilMize said:**
> Should be in either today or tomorrow... *checks tracking number*

not supposed to be in till the 24th... :( they say its "being assembled" but I think its the same thing as the Australian's where they have too wait a whole 2 weeks...

Ya you have to wait for fing ever. Dell clams to build every laptop to order. They clam to not stock anything. I would hope that means they will never send you a laptop with a dead pixel or some other defect.

---

### Post by wyth on 2009-06-02
If it's any consolation, my Dell Inspiron 530 has run basically flawlessly for about 3 years now.  So if they're keeping low overhead and building to order, they did a fine job with my machine.

e-cigarettes?

---

### Post by HunterThomson on 2009-06-02
> **wyth said:**
> If it's any consolation, my Dell Inspiron 530 has run basically flawlessly for about 3 years now.  So if they're keeping low overhead and building to order, they did a fine job with my machine.

e-cigarettes?

Ya, Dell is a good company to buy form. Worth the wait.

Ya man, e-cigarettes or "personal vaporisers" as they are staring to call them now for legal reasons. They vaporise a liquid with nicotine and flavouring. I am loving it. Though scratch the DES801, one with a "manual" button is better like a Dura-C or Janty Kissbox or the new Janty stick.

---

### Post by mjsolis on 2009-06-02
Hi all, 

I'm reading on the thread that the brightness problem is resolved in 9.04, but I still have it.  My biggest issue is how it dims when booting up.  I may be wrong, but I think this slows down my bootup time.  Does anyone else know about 9.04 continuing to have this problem for some people?  My apology if this question was already asked.  If so, I couldn't find it.  

Thanks for any responses.

---

### Post by PhilMize on 2009-06-02
mj when did you buy your y510?

sounds like you just need to update the bios...

---

### Post by wyth on 2009-06-02
mj has a y530 -- mj, I just sent you a message.  Philmize is right, it may need a bios update; I didn't put that in my message.  Let me see if I can dig up the thread on doing that.  It's not difficult.

---

### Post by mjsolis on 2009-06-02
Phil & Wyth: Can't say thanks enough for your responses. I do have a Y530, which I forgot to mention on my post...I bought it last February. 

Wyth: Thank you for your time looking that info up.   What a help!  BTW, I do have a clean install of 9.04.

---

### Post by HunterThomson on 2009-06-02
> **mjsolis said:**
> Phil & Wyth: Can't say thanks enough for your responses. I do have a Y530, which I forgot to mention on my post...I bought it last February. 

Wyth: Thank you for your time looking that info up.   What a help!  BTW, I do have a clean install of 9.04.

Hum, you know I looked up the Y530 just a month or so ago and I there was know BIOS up date for the Y530. I tried to look just now and didn't find one.

So, the BIOS update while the first thing to check is not and option. Though the BIOS is the problem....

How about this, dose your screen dim when you start a game or VLC or anything like that or is it just boot-up?

If it is just boot up I can write a script that you can have run at boot to set the brightness for you.

---

### Post by wyth on 2009-06-02
mj, [here's an old page about updating the BIOS on these machines]("http://ubuntuforums.org/showthread.php?p=5808814&highlight=bios+update#post5808814").  You'll need a live CD to make a tiny little fat32 partition space.  Then boot back into Ubuntu and drop your ROM there.  Then restart and go into your BIOS settings, and run the upgrade from its own software, pointing to that ROM.  

I've kept a sliver of space left over since; makes updating the BIOS a snap.  I just wipe it when I'm done, so it doesn't keep showing up on my desktop, and format it when I need to do the update.

By the way, one simple trick I did in the past was turn the brightness up as soon as the machine began to boot.  Sometimes that would stick, sometimes not.

---

### Post by mjsolis on 2009-06-03
Alright fellas...Both of you are just too cool. :cool: 

I have the reverse brightness, but the dimming at startup is my only issue right now. (I've been using the brightness applet added to the panel instead of the Fn & arrow keys that get stuck between extremely dark and almost black)

Videos are working fine, though I'm using gstreamer. But I just decided to try VLC and also see if there's a dimness problem there and I'll get back to your suggestions.   But first, should I uninstall gstreamer before trying VLC?  I believe I read about some possible conflicts there.   

Thanks again to both of you guys.  I've been floundering a lot with Ubuntu, so I feel very lucky.

---

### Post by PhilMize on 2009-06-03
> **mjsolis said:**
> Alright fellas...Both of you are just too cool. :cool: 

I have the reverse brightness, but the dimming at startup is my only issue right now. (I've been using the brightness applet added to the panel instead of the Fn & arrow keys that get stuck between extremely dark and almost black)

Videos are working fine, though I'm using gstreamer. But I just decided to try VLC and also see if there's a dimness problem there and I'll get back to your suggestions.   But first, should I uninstall gstreamer before trying VLC?  I believe I read about some possible conflicts there.   

Thanks again to both of you guys.  I've been floundering a lot with Ubuntu, so I feel very lucky.



HEY! >_> I wanna be cool...

LOL 

You can always just virtualize a copy of windows and do the bios update through there... on windows lenovo does everything for you through a step by step process to update your bios... just make sure when it says to restart you restart your host machine not just the virtual one... My buddy said he did this and it worked... though I have not done it myself so don't take my word on it...

[See Walkthrough]("http://consumersupport.lenovo.com/en/HintsandTips/hints_show_1231913189017.html") (note this is for y510 I couldn't find an update for y530)

---

### Post by wyth on 2009-06-03
> **mjsolis said:**
>  But first, should I uninstall gstreamer before trying VLC? I believe I read about some possible conflicts there.

No need to uninstall Gstreamer; it won't conflict. But know that there's one known bug in the current VLC, so the video pops out in its own window. It's been there for some time, and there was a way to turn it off, but that only worked on some configurations, so they turned that feature completley off on the current version (0.9.9a). It won't hurt anything; your video is just in a popped-out window.

It's a bug that's hung around for a number of versions, and they have it fixed, but it required a complete rewrite of some of the code, and that rewritten version won't be available until 1.0.

Also, if you're just getting going, here's a few things to check out:

[The Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty") is a community-made wiki with tips/explanations about what you can add/do.

The [Medibuntu]("http://medibuntu.org/") repository will allow you to add all kinds of codecs and software easily that might otherwise be a hassle. Medibuntu's page links back to [an official Ubuntu help page]("https://help.ubuntu.com/community/Medibuntu") that shows how to add the repository


*(Tip: You can copy and paste text into the terminal. Copy the text, and to get it into the terminal, use shift-insert or Edit > Paste.)*

First code to automatically add it to your sources.list:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```Second code to add the GPG key: 
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```Also, in System > Administration > Synaptic > Settings > Repositories (or System > Administration > Software Sources, same thing), there are some choices to make. If some piece of software isn't working, you may want to try to latest upstream version.  

MANDATORY CAUTION: This could lead to downloading something that doesn't quite work or occasionally crashes.  Personally, I've set my systems to get all the latest for the past three years, and have had no disasters, but it's always worth mentioning the warning.  You may also get an updated piece of software that takes care of a problem.

Anyway, in that Repositories box, two tabs you'll want to hit immediately are "Ubuntu Software" and "Updates." Under Ubuntu Software, make sure to tick on [COLOR=DarkSlateGray]**main**[/COLOR], [COLOR=DarkSlateGray]**universe**[/COLOR], [COLOR=DarkSlateGray]**restricted**[/COLOR], and [COLOR=DarkSlateGray]**multiverse**[/COLOR].  In Updates, make sure [COLOR=DarkSlateGray]**security**[/COLOR], [COLOR=DarkSlateGray]**updates**[/COLOR], [COLOR=DarkSlateGray]**proposed**[/COLOR] and [COLOR=DarkSlateGray]**backports**[/COLOR] are ticked on.  (See attached pics.)

Last thing: Many developers and developer teams have gotten their own personal repositories into Launchpad.net in what's called PPA's (personal package archives).  They're fantastic, they're safe, and they require a key to actually add the repository to your sources.list and download/install the software.  I have a lot of these added -- some for software in development that I want to try, some for drivers and the like that work better with my hardware.  Here's one that may help with hardware -- the [Ubuntu-X Team]("https://launchpad.net/%7Eubuntu-x-swat").  They work on packaging the latest stable versions of xserver-xorg, nvidia, and fglrx.  Here's their [PPA page]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") -- it shows the lines to add to your sources.list, and links to the GPG key.  (See attached pic.)

Two ways to add the sources of a PPA:

[LIST=1]
[*]In System > Administration > Synaptic > Settings > Repositories (or System > Administration > Software Sources), click on the Third-Party Software tab.  Click on Add (see pic) and then add the first line from the PPA page that looks like the following (see pic): ```
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
``` Then do the same with the line that looks like ```
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
```
[*]As root, use your favorite editor to edit your /etc/apt/sources.list file.  (*It has to be your favorite editor -- if its your second favorite, wild marmets will eat kitties.*) You can do this in the terminal with vi, vim, nano, or with an app like gedit.  I like nano and gedit; they're simple.  So the code would be something like ```
gksu gedit /etc/apt/sources.list
``` That will bring up the text page.  At the bottom, add something like ```
## X Updates
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X Updates
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X Updates
```
[/LIST]
I generally take the second option, because that way I can keep my sources.list completely organized and commented, so I know what each PPA is for.  Sometimes you'll get a PPA that's just someone's name, so you can't tell what software it's for; that's what adding the ## X Updates at the beginning and the #X Updates at the end of each line helps with.  Plus, when you add #X Updates after each line, you'll see just that in your Synaptic/Software Sources, "X Updates" instead of the entire line of code.

Last step: Add the keys so you can authenticate to the Launchpad PPA.  On the PPA page below the source lines, you'll see something that says > This repository is signed with           [             1024R/AF1CDFA9]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9&op=index") OpenPGP key.           [Follow these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")           for installing packages from this PPA.  Again, there are a few ways to add the key.

[LIST]
[*]If you click on the string of numbers, you'll first go to a "Search results page" with a long string of numbers at the top, and a couple links below. If you click on the link that says > 1024R/[AF1CDFA9]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9") it'll take you to the [Ubuntu keyserver page]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x3B22AB97AF1CDFA9") page that shows the following:
[/LIST]
> 
**Public Key Server -- Get ``0x3b22ab97af1cdfa9 ''**

 -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXVCiwEEANKBDbiSLOJOouub/S97iDifYCVW1b0KONg7XkFYiFos+bMBzzZyGGo90k1h
hCxcseLvqCKPL7dG0RzPRKMo7mvM68yyqi2ljw0ZYC9cVf0YzgKRTohVhihelpwZ+sBRGNYk
OCu+u0Dr+EdVI3u5RNOxAELrbd4vYaS+2cCOfzmLABEBAAG0GkxhdW5jaHBhZCBQUEEgZm9y
IFVidW50dS1YiLYEEwECACAFAkl1QosCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRA7
IquXrxzfqY4HBACIQEFhl59ZkuIhTD3pmCQgfkhpcg0RVdB6Xwhu3QDJvmlWmrs+cofNMzyA
7SwdjD9ARvhGbqHwub+T7oGiHlmFyodGypUZ4i/fdHsZYpsf34MwgYxhyNyOPY/jNImUE/yw
kSI+kV5esWURH4j0jYfkaergFqCpDnsSkxuIvdjH2Q==
=bkAa
-----END PGP PUBLIC KEY BLOCK-----[INDENT]Copy that into a text file, save it, and in the Synaptic Repositories/Software Sources, Authentication Tab, click "Import Key File" and grab that text file.  Key imported.

[/INDENT]
[LIST]
[*]Quick and command-liney way: Open the terminal and add this code: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 
```  Then go back to the PPA page and look at that line that says > This repository is signed with           [             1024R/AF1CDFA9]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9&op=index") OpenPGP key.           [Follow these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")           for installing packages from this PPA.[/quote]  What you need is the string after the slash -- AF1CDFA9.  That goes at the end of the string of code you just added in the terminal.  So:  ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
```  Done.  Key imported.
[/LIST]
I actually keep that string of code in a Gnote/Tomboy Note for easy access; just make sure you have a space between the string of code and the key number itself.

Last question: You have an nvidia cart, right?  Did you run System > Administration > Hardware Drivers and install nvidia-settings?

---

### Post by HunterThomson on 2009-06-03
Ok, here is a script that should set the brightness to max when it is run.

just follow the little howto I have a page or so back to make a script run at boot time with root privileges.

Note: try running this command in the terminal to make sure it will work fist.

```
sudo echo 10 > /proc/acpi/video/VGA/LCDD/brightness
```

---

### Post by HunterThomson on 2009-06-04
For all us 64bis users. I alredy knew we had a native 64bit adobe flash player beacaus Archlinux uses it. However, Ubuntu doesn't. Here is how you install it in Ubuntu.

Download it form here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

2. Unpackage it:
cd
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

3. Create a plugin directory in your $HOME (instead of a system directory):
mkdir -p .mozilla/plugins

4. Move the file to the plugin directory:
mv libflashplayer.so .mozilla/plugins

5. Restart firefox. Go to ```
about:plugins
``` to see if it’s enabled

---

### Post by wyth on 2009-06-04
Ha!  I just did this two days ago -- re-installed as 64 bit on my desktop.  

Tell me, any particular reason for making a plugins folder in /home rather than using /usr/lib/mozilla/plugins?

---

### Post by HunterThomson on 2009-06-04
> **wyth said:**
> Ha!  I just did this two days ago -- re-installed as 64 bit on my desktop.  

Tell me, any particular reason for making a plugins folder in /home rather than using /usr/lib/mozilla/plugins?

Well, the how to I found explicitly said NOT to put it into that directory. It is Alfa so mabe it has some bug that will not let it work in there. Also, even though it is Alfa it works WAY better then the 32bit one.

It still baffles me why some people think that 64bit Linux is problematic. I have NEVER had a problem with 64bit. 
64bit Wincrap is a pile of **** though but hay wincrap is a pile of **** anyway.

As for VLC, hum I didn't know that how it defaults to the two window mode was a bug. I always liked that mode better anyway. That way I can minimize the player thing and keep the movie playing in it's own window with, nice & clean.

---

### Post by wyth on 2009-06-05
I dropped the file in /usr/lib/mozilla/plugins, and don't *think* it's causing any trouble, but honestly I'm not sure -- had one issue with sound, and the iGoogle pages aren't showing half the feeds, but that seems to be a feed issue.  Where'd you get your instructions?  I should check the adobe page.

(Seems like recently 1/3 of the rss feeds out there added a digit or something; most feedburner feeds went from *feeds.feedburner* to *feeds2.feedburner*, but most links still point back to *feeds.feedburner*. -- even on big sites, like CNet.  It's broken a lot of podcast feeds for me.)

As far as the VLC bug, making the window pop out was always a feature, but you just can't turn it off for now -- not until version 1.0.

---

### Post by HunterThomson on 2009-06-05
> **wyth said:**
> I dropped the file in /usr/lib/mozilla/plugins, and don't *think* it's causing any trouble, but honestly I'm not sure -- had one issue with sound, and the iGoogle pages aren't showing half the feeds, but that seems to be a feed issue.  Where'd you get your instructions?  I should check the adobe page.

(Seems like recently 1/3 of the rss feeds out there added a digit or something; most feedburner feeds went from *feeds.feedburner* to *feeds2.feedburner*, but most links still point back to *feeds.feedburner*. -- even on big sites, like CNet.  It's broken a lot of podcast feeds for me.)

As far as the VLC bug, making the window pop out was always a feature, but you just can't turn it off for now -- not until version 1.0.

Hum ok, (about the VLC)

Well it seems the 64bit didn't fix the problem for me with Flash. Still better then useing the 32bit though. While trying to get some error output I did notice that when firefox starts flash it said something like droping root privileges. I don't know though. I just cut and pasted the how to I found here so that is all there is to read form it. I would just put it in ~/.mozilla/pulgins if I were you though.

Here is a link to the thread I started about my flash problem.
Problem: Works fine then Wham! CPU at 100% and video stutters then keeps playing but no sound.

[http://ubuntuforums.org/showthread.php?t=1178961](http://ubuntuforums.org/showthread.php?t=1178961)

---

### Post by mjsolis on 2009-06-05
Sorry for the delay guys...

Phil: You are declared cool! :cool:  Just kidding...You're already cool...I thought about virtualizing Windows but I heard it was too slow...(?)   

Wyth & Hunter:  Thanks to both of you for your input.  Talk about going the extra mile...I haven't been able to get this kind of help in my area even though I've paid for it. It seems they either didn't have this much knowledge or just couldn't (or wouldn't) take the time.  

The BIOS is now current and I do have the Nvidia driver installed, but neither affect the dim screen at bootup. 

Hunter: I'd like to get some clarification on running the script...I cut and pasted that command to try it first and got "no such file or directory."  I bet I'm missing something simple.  Thanks for your response.

---

### Post by HunterThomson on 2009-06-05
Hum yes you will need to find the file. In Linux "Everything is a file" even the current setting of your back-light is mearly a # in a file.

Start to look for that file in /proc Then if there is a /acpi go into that, Then /video then /VGA then, LCDD .... Your looking for a file caled brightness or something like it. The file will contain only one number like
8

Once you found it 

echo 10 > /Path/To/File

"echo" just prints what ever string you put after it like 10
">" will put the output of the command before it into the file after it
so, echo 10 > /path/to/file
Will "Overwrite" the file /path/to/file with the string "10"
10 will then be the level of brightness of your backlight.

---

### Post by HunterThomson on 2009-06-06
nevermind flash is still borken..... ****

---

### Post by mjsolis on 2009-06-07
Done Hunter...But this is what I got after I clicked on the "brightness" file:  

"The file /proc/acpi/video/VGA1/LCDD/brightness changed on disk"
I don't fully understand what I'm doing (yet),  so I decided to try a few things...With the message above, it also asks “Do you want to reload the file?”  I then clicked “reload” and the brightness file comes back blank.   I tried it again but instead of  “reload,” clicked cancel... “echo 10 > /Path/To/File” remained, so I clicked save and got this:  “Could not save the file /proc/acpi/vidoe/vga1/lcdd/brightness....You do not have permissions necessary to save the file.  Please check that you typed the location correctly and try again.”    

Again,  I bet the answer is really simple...Just disregard if this is taking too much of your time.  

Regards

---

### Post by HunterThomson on 2009-06-08
There is not?
 /proc/acpi/video/[COLOR="Blue"]VGA[/COLOR]/LCDD/brightness

Only?
/proc/acpi/video/[COLOR="Blue"]VGA1[/COLOR]/LCDD/brightness


You don't want to change the file in a text editor. Just do...
```
sudo echo 10 > /proc/acpi/video/VGA1/LCDD/brightness
```

Or maybe 10 is not an exceptiable value... So, just to make sure it is working. Set the brightness to max any way you can noramly. Then try this...

```
sudo echo 0 > /proc/acpi/video/VGA1/LCDD/brightness
```

or

```
sudo echo 2 > /proc/acpi/video/VGA1/LCDD/brightness
```

If one of thougs dose dim the brightness of your screen then just keep incrementing up the valu untill you find the max value. It mite be 8..

```
sudo echo 8 > /proc/acpi/video/VGA1/LCDD/brightness
```

Once you have found what works then just edit the script I wrote or write your own and folow the instructions I posted to make it run at boot time.

It mite not work running at boot time with the instructions I wrote because it mite get changed back to dim when X starts. If that is the case there are a few other ways of doing it. But just find a command that works first.

---

### Post by HunterThomson on 2009-06-08
Nice I got my ATI card to work in Archlinux.
I am soo happy. Never did get the flash problem fixed in Ubuntu but now I will never have to deal with random stuff braking ever agin. 

I LOVE Aarchlinux :guitar:

Here are a cupple screen shots.

---

### Post by mjsolis on 2009-06-10
Right Hunter...There's only a "VGA1" file and no "VGA."  I input the commands and got  "permission denied" on each one.  BTW: Congrats on your archlinux experience.

---

### Post by HunterThomson on 2009-06-11
> **mjsolis said:**
> Right Hunter...There's only a "VGA1" file and no "VGA."  I input the commands and got  "permission denied" on each one.  BTW: Congrats on your archlinux experience.

You got "permission denied" while using sudo? Well... some filesystem stuff must have gotten changed in Ubuntu. Boy thats all I can tell you. Look for a shell command that can set the bightness for you. If you found some bash application that would work too. Then just have it run at boot. It will not fix the problem but is a nice workaround.

Ya, I am soo happy I am back on Archlinux. You should realy give it a shoot. It is just like Gentoo with half the work. Rolling distro and bleading edge and stable as a rock. They also focus on x86_64 not mainly x686 with a 64bit option.

Edit: Well if you got permition denied with sudo. Try swiching to root "sudo su" then run the command. The script will run as root so if it works so would the script.

---

### Post by santhinen on 2009-06-12
Hey guys.. I see that the thread is long and many could fix the problem... But i still have some issues
1- Audio: I could fix the problem of headphones and also the subwoofer is working fine...but when i use the volume up and down i get some high pitch screeching sound...i donno why...

---

### Post by wyth on 2009-06-12
> **santhinen said:**
> Hey guys.. I see that the thread is long and many could fix the problem... But i still have some issues
1- Audio: I could fix the problem of headphones and also the subwoofer is working fine...but when i use the volume up and down i get some high pitch screeching sound...i donno why...

Check in the Volume Control if you have a Mic ticked on or too loud.

Right-click on the Volume app in the panel, and choose "Open Volume Control."  That'll show you what's enabled, at what level, and what isn't enabled.

---

### Post by mjsolis on 2009-06-14
Thanks Hunter...I'll try it "sudo su"  BTW, I think I'll stick with Ubuntu for a while...Wyth wrote a long post for beginners recently and I'm now learning in 5th gear.  But what kind of support does Archlinux have? Maybe I'll check it out in the future.  Depends on the pros and cons I guess.    

I'm also glad you guys have covered the sound issues...I haven't even started on that, but I'm lucky it's all outlined here.

---

### Post by HunterThomson on 2009-06-14
> **mjsolis said:**
> Thanks Hunter...I'll try it "sudo su"  BTW, I think I'll stick with Ubuntu for a while...Wyth wrote a long post for beginners recently and I'm now learning in 5th gear.  But what kind of support does Archlinux have? Maybe I'll check it out in the future.  Depends on the pros and cons I guess.    

I'm also glad you guys have covered the sound issues...I haven't even started on that, but I'm lucky it's all outlined here.

Ya that mite work mite not. It mite be that the permitions of the file do not alow it to be wirtten to. Check the permitions of the file like this

```
ls -l /proc/acpi/video/VGA1/LCDD
```

If it is listed as rw-r--r-- then root can read and wirght to it, anyone in the file owners group can read fromit and everyone ells can r.
If it is --------- then you can't do anything.

```
rwx    rwx     rwx
^       ^       ^
Owner   Group   Everyone ells
```


You can set the permitions to rw-r--r-- by doing this

```
sudo chmod 644 /proc/acpi/video/VGA1/LCDD/brightness
```

In that chmod the #'s equle the permitinos like this
1= exicute
2= wright
4= read

and any combonation are just by adding the #'s like this
1+2=3 Exicute and Writht
4+2=6 Read and wright
4+2+1=7 Read and Wright and Exicute
..... and so on...

---

### Post by PhilMize on 2009-06-15
On a side note...


I installed Fedora 11 on my y510 while I wait for my new 2100 to come in, and well everything pretty much works out of the box. I only had to get the sub woofer working and the web cam is still upside down. But the Mic issue I was having is gone and any other issues I have yet to run into. Man if I was still planning on using my Lenovo after I get the Dell I might of never came back to Ubuntu. :(


The 24th can't come fast enough! :D

---

### Post by HunterThomson on 2009-06-15
> **PhilMize said:**
> On a side note...


I installed Fedora 11 on my y510 while I wait for my new 2100 to come in, and well everything pretty much works out of the box. I only had to get the sub woofer working and the web cam is still upside down. But the Mic issue I was having is gone and any other issues I have yet to run into. Man if I was still planning on using my Lenovo after I get the Dell I might of never came back to Ubuntu. :(


The 24th can't come fast enough! :D

That's cool. Fedora was the first Linux distro I tried but it didn't last more then a few days with me. I didn't like the SElinux stuff. Maybe now that I know a little I mite like it better. However, I am never going to use any bloated distro agin now that I got a tast of Arch.

You ever try any other sound module's? I used lenovo-sky and that didn't have the mic problem but the 3stack-6ch did.

Today is a happy day. I got this external HHD case a while back and it didn't work with my ideapad. However, my new laptop's BIOS sees it and even lets me boot from it. My new laptop also has a eSATA port and so dose this HHD case so I am stoked. Full speed from the HHD and no CPU hit :)

---

### Post by PhilMize on 2009-06-17
> **HunterThomson said:**
> That's cool. Fedora was the first Linux distro I tried but it didn't last more then a few days with me. I didn't like the SElinux stuff. Maybe now that I know a little I mite like it better. However, I am never going to use any bloated distro agin now that I got a tast of Arch.

You ever try any other sound module's? I used lenovo-sky and that didn't have the mic problem but the 3stack-6ch did.

Today is a happy day. I got this external HHD case a while back and it didn't work with my ideapad. However, my new laptop's BIOS sees it and even lets me boot from it. My new laptop also has a eSATA port and so dose this HHD case so I am stoked. Full speed from the HHD and no CPU hit :)

Lenovo-Sky was the one i was using in the first place. :(

It's w/e though I'm so ready for my new netboook. I opened up the Y510 yesterday to check out the hinge issue and a bunch of broken plastic and metal fell out. :-| Though it got me thinking of ways to splice the lcd screen ribbon and create some sort of molded box to house the laptop. Or I was thinking about mounting the lcd screen in a picture frame of sorts and hiding the rest of the laptop mounted under my desk. I want to do something cool with it, So anybody have any ideas? Maybe something like [this]("http://www.instructables.com/id/EWQUH9EV7EEP2871V1/").

BTW was looking at the newer Y series laptops at tiger direct the other day at it seems like Lenovo is pushing more for looks now then quality. At least with their commercial models. The one was like aaaa I think Y550? Anyways, after my hinge issue, I'm looking at this newer Y550 and all I could help but think is "this **** looks easier to brake then the Y510!" I could be wrong though, just me rambling,

---

### Post by wyth on 2009-06-17
No idea if this will help or not, but I came across this tip recently.

If for some reason your Y510 is using Pulse, here's a way to make sure it's picking up all speakers:

As root, head to /etc/pulse/daemon.conf, and look for the line that says ```
; default-sample-channels = 2
```Remove that comment and change the line to read ```
default-sample-channels = 6
```(You might even try 5.1 -- not sure.)

I can't say if that'll help or not, because ALSA works fine for me, but it's a shot in the dark until the new machine arrives.

---

### Post by PhilMize on 2009-06-18
WTF!!!!

I just got an email from Dell saying my new 2100n has been delayed to ship on the 1st of July... It was supposed to come in ion the 24th... Effing rediculas... I've already been waiting like 3 weeks... UGH!

---

### Post by BlueCanary9999 on 2009-06-19
Sorry this response is soooooo late.  I've been constantly busy for the last two months, but now I'm free to work on my computer.  :D  My problem is about the speakers, btw.

(So... going way back to like... page 34....)

> **HunterThomson said:**
> BlueCanary9999: From the looks of it your Y530 has the same chipset as my Y510 "Realtec ALC888". So, you should do the same as all the Y510 users do for sound. I sugjest the lenovo-sky it defaults to 6-channels and has no problem with the headphones. 

Also, form the looks of it ether you added...

```
options snd-hda-intel model=lenovo-sky
```

To the /etc/modprobe.d/alsa-base.conf with a typo or you Ubuntu users realy do still have to install the ALSA stuff form source.

Make sure you have it all typed in correctly ((Just cut and past)) and make sure you have one empty line at the end of the file.

You will know the model is set correcty if you have the Suround, Center, LEF,... stuff there in the terminal alsamixer ((The one you have pictured)) Keep useing the terminal alsamixer and NOT the Gnome ALSA mixer untill all is well. It will show all the avalabe options. The Gnome ALSA mixer will not show them untill you tell it too as chargersfan420 has said. The Gnome one is a pain in the ***.

Yes chargersfan420 is right your sound is crappy becaus sound is only comming out of the two speakers by the monitor as you have it right now. That is why it is so quiet.

Ya, feel free to edit the /etc/modprobe.d/alsa-base.conf file with "gedit" if you like.

If you check/fix the /etc/modprobe.d/alsa-base.conf file and you still don't have the Suraound, Center, LEF,... stuff in then ALSA mixer then go to page-1 of this thread and follow the instructions word for word(( Just Cut & Past)) but you can skip the step to see all the avalable options for the "modle" just use the lenovo-sky one.

You should have no problem but if you do just report back here. We will help you no problem :)

Checking everything in Preferences and maximizing the PCM volume fixed the crackling.  :D  It's also louder than it used to be.  But in the Options tab in Volume Control, I only have two drop-down lists, both of which are called "Input Source" and my options for each are Mic or Front Mic.  No channel mode.  After adding "options snd-hda-intel model=lenovo-sky" to "/etc/modprobe.d/alsa-base.conf" again doesn't seem to change anything.  There are also no Surround, LEF, etc. options in the terminal alsamixer.  I copied and pasted it verbatim tho, and there is one blank line at the end of the "/etc/modprobe.d/alsa-base.conf".

So I started following the instructions on page 1 on "How to get the sound working".  Everything works fine until I get to "* Compile and install alsa-lib".  At "sudo ./configure ", the terminal starts checking things, but then it says:

```
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
```

So where do I get a "sufficiently new version of libasound"?  I tried apt-get and it didn't work.  I checked Synaptic and it says I have libasound2 and libasound2-plugins, but not libasound2-dev or libasound2-doc.  I just reinstalled libasound2 and the same error appears.  What should I do?

Thanks for the help so far, btw!

---

### Post by HunterThomson on 2009-06-20
BlueCanary9999: Download the newest dirvers, libs, and utils from here...
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

The new drivers are 1.0.20. Ubuntu must be on 1.0.16

Use the HowTo on the first page of this thread for the install instructions.

edit:Boy I never put the link in the instrutions on the first page of this thread to get the newest alsa stuff... Boy, sorry. And from reading it it didn't even seem oveous that you needed to get the new ones.

---

### Post by BlueCanary9999 on 2009-06-20
Right, those are the ones I got and tried installing.  What do you mean by "Ubuntu must be on 1.0.16" tho?

---

### Post by HunterThomson on 2009-06-20
> **BlueCanary9999 said:**
> Right, those are the ones I got and tried installing.  What do you mean by "Ubuntu must be on 1.0.16" tho?

I figured that you must have the 1.0.16 ALSA driver/libs/utils sents it was asking for them.

I guess you need to reinstall the libs.

----------------
Fun times with my newly working eSATA external HHD
Becaus it is bootable. I now have FreeBSD and OpenSolaris fully installed
Like so...

```
160GB Fuji 5400RPM Hard Drive (via 3.0GB/s eSATA)
/dev/sdb1 -- Primary -- 30GB -- FreeBSD
/dev/sdb2 -- Primary -- 30GB -- OpenSolaris
/dev/sdb3 -- Primary -- 1GB -- HP_TOOLS (EFI boot files)
/dev/sdb4 -- Extended -- 88GB
/dev/sdb5 -- 2GB -- Linux-Swap
/dev/sdb6 -- 86GB ext3 -- DATA (backup of /documents /mnt/sd/etc /pictures /music /wallpaper + Videos and stuff)

30GB OCZ Vertex MLC SSD
/dev/sda1 -- Primary -- 29.8GB -- Archlinux

SDHC 8GB SanDisk (SD card)
/documents
/web
/etc
/pictures
/music
/wallpaper
```

---

### Post by michaelzap on 2009-06-21
This really is an amazingly helpful thread!

I just got a new Y530 and almost everything worked right out of the box with 64-bit Jaunty. I didn't have sound from all of my speakers, but adding "options snd-hda-intel model=lenovo-sky to /etc/ion keys don't wormodprobe.d/alsa-base.conf fixed that easily enough. The only other thing that I haven't fixed yet is the backlight (I get some flickers and the function keys don't work properly).

What is the proper way to fix the backlight in 64-bit Jaunty?

I also installed with no swap partition but now I'm confused by the fact that my laptop doesn't seem to want to suspend (which I would've thought would work) but does hibernate (which I would've thought impossible with no swap)...

---

### Post by HunterThomson on 2009-06-22
> **michaelzap said:**
> This really is an amazingly helpful thread!

I just got a new Y530 and almost everything worked right out of the box with 64-bit Jaunty. I didn't have sound from all of my speakers, but adding "options snd-hda-intel model=lenovo-sky to /etc/ion keys don't wormodprobe.d/alsa-base.conf fixed that easily enough. The only other thing that I haven't fixed yet is the backlight (I get some flickers and the function keys don't work properly).

What is the proper way to fix the backlight in 64-bit Jaunty?

I also installed with no swap partition but now I'm confused by the fact that my laptop doesn't seem to want to suspend (which I would've thought would work) but does hibernate (which I would've thought impossible with no swap)...

Ya strange... Hibernate is "Suspend to disk" and Suspend is "Suspend to ram"... Maybe they got switched around somehow?

Well, we have never fixed the backlight for the Y530. The Y510 had that problem and was fixed partly by me dedusing that the BIOS is the problem but mostly by ??? patching the DSDT BIOS file. However, the Y510 backlight works out of the box as of Kernel 2.6.28.
This is the best bet for the Y530 owners. Fix the DSDT.

What do you meen by you "get some flickers"? Is it dim on boot?

------------------------
I dumped the FreeBSD and now am using OpenBSD becuas FreeBSD dosn't support my WiFi card.

After, setting up OpenSolarus and Free/Open*BSD Here is what I think...

OpenSolarus has the best file System. ZFS !:) way cool :) I wish Linux had real support for it but they may change the license so it can be used with GNU. Other then that.... BSD has everything OpenSolarus has exept More. Also, the OpenSolarus Pachage manger SUCKS as far as I can tell. Total pain in the *** to use. OpenSolarus is slow too boot.

OpenBSD, Ya I can see that it is laid out better then Linux. Supose to be way more secure, faster and more stable. Vary much like setting up Arch Linux. Way nice package manager ... "As good as" Archlinux's pacman. And OpenBSD's repositorys are set up nice too but a tad more dependency-bloated then Archlinux's repo's. I would use OpenBSD over Archlinux if it supported my ATI card with the Catalyst or will when the OpenSource radeonhd driver gets better.

In then end, Linux is best for your Workstation and OpenBSD is best for your old hardware and/or Server. The problem with *BSD is that they only support hardware that is 2+years old. OpenSolarus supports all of it exept I have to use the open radeonhd driver. OpenSolarus would be a VARY VARY good OS for a Server becuas of it's ZFS filesystem. However, you can use ZFS with *BSD.... So, I'll stay with Linux untill the radeonhd driver has good 3D support then I'm off to OpenBSD.

---

### Post by michaelzap on 2009-06-22
> **HunterThomson said:**
> Well, we have never fixed the backlight for the Y530. The Y510 had that problem and was fixed partly by me dedusing that the BIOS is the problem but mostly by ??? patching the DSDT BIOS file. However, the Y510 backlight works out of the box as of Kernel 2.6.28.
This is the best bet for the Y530 owners. Fix the DSDT.

What do you meen by you "get some flickers"? Is it dim on boot?


I'll try editing the DSDT tomorrow.
 
What I mean is that the backlight goes momentarily darker every once in a while. It's frequent enough to be annoying. Plus the function brightness keys don't work (if I use either of them, the backlight ims and won't brighten up again).

Other than that the screen is beautiful and everything works just fine.

---

### Post by BlueCanary9999 on 2009-06-22
Well, I reinstalled the ALSA stuff and continued with the instructions and... IT WORKS PERFECTLY!  Thank you so much!  I can now listen to Chopin in full glory.  :D

Okay, so now for two more questions, which might be linked.  The first is about shutting down.  Sometimes it works, sometimes it doesn't.  Right now it isn't working.  It'll go through the shut down process and then at what I assume is the final stage, it displays a blank screen and hangs.  To shut it down I have to hold the power button.  I have no clue what the problem is.  Is this a problem with the Y530 and Linux?  What would I do?

The second question is about hibernating, which doesn't work fully.  In the same sense as shutting down, it will hang mid-process.  It says:
```
[  686.529325] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  686.529327] ata1: irq_stat 0x00400040, connection status changed
[  686.694577] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  686.694670] ata2: irq_stat 0x40000001
_
```
The cursor at the last line blinks pretty rapidly.  Then it stalls, doesn't react to any keys or buttons, and to turn it off I have to hold the power button.  On turning it back on it says "Waking up.  Please wait...", returns to the code above for a short while, and then gets to a log-in screen.  It then boots as if it correctly hibernated, with windows still open.

On the second try, the same thing happened but the code was this:
```
[  864.171188] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  864.171190] ata1: irq_stat 0x00400040, connection status changed
[  864.372830] ata2: irq_stat 0x40000001
_
```
When I turn it on it goes through the same process but the code it shows for a short while is more like the first set of code I posted, but the numbers on the left began with 864, like the second set of code I posted.  But then it disabled my visual settings, making me reset them.

Anyhow, I dunno what the problem is or how to fix it, being quite a Linux noob.  What do I do?

---

### Post by HunterThomson on 2009-06-23
Nice glad you got the sound working :)

Boy I have no clue how to solve your back-light problems other then write that script.

michaelzap: your backlight problem really would bug me. Maybe try an older Ubuntu like 8.10. I think that mite solve your problem. It seems the *.04's are all buggy and the *.10's are sold.

Your power-off problem is a problem with Ubuntu not your computer.

As for hibernation, I don't know. Do you have a swap partition at lest as big as your RAM? Probably just more ACPI problems caused by bugs in the DSDT.

---

### Post by HunterThomson on 2009-06-23
> **PhilMize said:**
> WTF!!!!

I just got an email from Dell saying my new 2100n has been delayed to ship on the 1st of July... It was supposed to come in ion the 24th... Effing rediculas... I've already been waiting like 3 weeks... UGH!

That was my fear about buying form Dell. 
When I order something I want it now. I'll pay what ever it takes to get it fast. I'd be going nuts if I had to wait for my new laptop.

Sorry to hear but hay lets just hope it is spotless and everything works :)
If you call and complain they will give you free stuff. The same thing happed to a friend of mine and they gave her a really nice laptop case for free. Just keep on the phone and don't let them hang up on you until you they offer you something.

---

### Post by mylh on 2009-06-23
Hi all!

Yesterday I sucessfully connected my Y530 to my HD TV through HDMI. I got 2 modes in what a laptop can connect to TV
1) When I get a copy of what I see on th laptop screen
2) When only TV works
The only issue is that desktop on TV screen was cropped though I was able to scroll it with mouse.

So are there any ideas of how to configure TV as a second independent display and to specify 1920 x 1080 resolution?

---

### Post by PhilMize on 2009-06-23
> **mylh said:**
> Hi all!

Yesterday I sucessfully connected my Y530 to my HD TV through HDMI. I got 2 modes in what a laptop can connect to TV
1) When I get a copy of what I see on th laptop screen
2) When only TV works
The only issue is that desktop on TV screen was cropped though I was able to scroll it with mouse.

So are there any ideas of how to configure TV as a second independent display and to specify 1920 x 1080 resolution?


Lol its about time we got back too lenovo and the y510. 

I'm assuming your running 8.10? 9.04? If you haven't already, install compiz and enable desktop effects. Open up your compiz control panel and there should be a tab for dual monitors. Are you trying to get identical screens? Or an extended desktop? and whats the brand of tv?

---

### Post by HunterThomson on 2009-06-23
> **mylh said:**
> Hi all!

Yesterday I sucessfully connected my Y530 to my HD TV through HDMI. I got 2 modes in what a laptop can connect to TV
1) When I get a copy of what I see on th laptop screen
2) When only TV works
The only issue is that desktop on TV screen was cropped though I was able to scroll it with mouse.

So are there any ideas of how to configure TV as a second independent display and to specify 1920 x 1080 resolution?

PhilMize is right. I know the ATI Catalyst Control Center has a duel monitor setup and I bet nVidia blob dose too.

The sure fire way to get what ever settings you like (i.e. extended monitor, or have one resolution setting for your laptop and a difrent setup for the TV) can be done by specifying what you like in your /etc/X11/xorg.conf file. If you google for "duel Monitor" "xorg.conf" I am sure you will find some to copy. Also, reading through the Archlinux and Gentoo WiKi's on setting up Xserver will help you out too.

**_How to set up xorg.conf_**
[http://wiki.archlinux.org/index.php/Xorg.conf](http://wiki.archlinux.org/index.php/Xorg.conf)

---

### Post by mylh on 2009-06-24
Thank you, guys :) I'll try your solutions though actually I don't like the idea of installing compiz - regular KDE is enough for me in terms of visual effects.

---

### Post by akarun on 2009-06-24
> **Temüjin said:**
> I have a script that installs ALSA 1.0.17 [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you folks find a certain model= keyword works better than others, let me know so I can add it to the list (in the thread linked above).

Not sure if you got the answer already..
model=6stack-dell works with alsa right out of the box. The headphones work and mute the speakers and 5.1 works.

Got it from here: [http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html](http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html)

My mic still doesn't work with skype :(
If anyone can get it working too, then lenovo y530(y510) has really no reason for me to switch to windows.

Also what is the status of suspend/hibernate? Doesn't work for me

Cheers,
Arun

---

### Post by HunterThomson on 2009-06-25
I got my mic working Skype on my Y510

If I remember correctly, ((I mean I know what I am about to tell you is correct but there may have been a setting in Skype that I had to change too)) You have to change both mic's in ALSAminxer to "Front Mic" don't have it set to the default "Mic".

So do that, set the alsamixer to "Front Mic" and then try all the Skype mic settings one by one.

______________________

Also, I just had a problem after upgrading to the new 2.6.30-ARCH kernel in Archlinux. I had to run this command a root to fix it.

>Enter root 
```
su -
```

>Then close all apps and stop the alsa deamon
```
/etc/modprobe.d/alsa stop
```
<<((I mite be wrong about the location of the daemon in Ubuntu))>>

>Then run this configuration application

```
alsaconf
```

I just chose all the defaults.

---

### Post by PhilMize on 2009-06-26
sooo... Dell delayed it again... this time to the 9th...ugh

---

### Post by HunterThomson on 2009-06-26
> **PhilMize said:**
> sooo... Dell delayed it again... this time to the 9th...ugh

I'd call and get some free stuff that is crazy !

---

### Post by josesilva on 2009-06-27
Has anyone gotten sound to work correctly with an Ideapad Y430? I have tried following all the instructions (newer alsa, different models, etc) given here and in the older thread but when I plug in my headphone, the front speakers get muted, but not the subwoofer. Also, my audio properties dialog only shows Master, PCM, Docking Mic, External Mic, and Internal Mic for Playback. I do NOT see LFE, Center and all those options that other members have mentioned. 

Ideapad Y430 has the following soundcard:
==> /proc/asound/card0/codec#1 <==
Codec: Nvidia ID 3

==> /proc/asound/card0/codec#2 <==
Codec: Conexant CX20561 (Hermosa)

Alsa, altough the subwoofer "works," it works like another speaker and does not provide bass sound. Everything else works on this laptop (haven't tested SD/MMC/etc, HDMI, Modem, firewire)

Any ideas?

---

### Post by HunterThomson on 2009-06-29
> **josesilva said:**
> Has anyone gotten sound to work correctly with an Ideapad Y430? I have tried following all the instructions (newer alsa, different models, etc) given here and in the older thread but when I plug in my headphone, the front speakers get muted, but not the subwoofer. Also, my audio properties dialog only shows Master, PCM, Docking Mic, External Mic, and Internal Mic for Playback. I do NOT see LFE, Center and all those options that other members have mentioned. 

Ideapad Y430 has the following soundcard:
==> /proc/asound/card0/codec#1 <==
Codec: Nvidia ID 3

==> /proc/asound/card0/codec#2 <==
Codec: Conexant CX20561 (Hermosa)

Alsa, altough the subwoofer "works," it works like another speaker and does not provide bass sound. Everything else works on this laptop (haven't tested SD/MMC/etc, HDMI, Modem, firewire)

Any ideas?


Check out this file and look for your sound card or close enough.
Then try out the modules it has for it.

```
gedit /usr/src/alsa/alsa-driver*/alsa-kernel/Documentation/ALSA-Configuration.txt
```


I am fairly sure you can restart ALSA with this command

```
sudo /etc/init.d/alsa restart
```

--------------------------------------------------------------------------

You could also try alsaconf

enter root

```
su -
```

Then run this just take all the defaults unless you know it is wrong

```
alsaconf
```

---

### Post by PhilMize on 2009-07-02
Dell just delayed my order again too the 17th... I called about it and they said don't expect it till Aug. I just canceled my order and bought the Dell Studio XPS 13' w/ 8.10...They said the part that was on backorder was the 16gb ssd. So for future reference don't get it with the ssd till Dell gets their act together!

---

### Post by HunterThomson on 2009-07-02
> **PhilMize said:**
> Dell just delayed my order again too the 17th... I called about it and they said don't expect it till Aug. I just canceled my order and bought the Dell Studio XPS 13' w/ 8.10...They said the part that was on backorder was the 16gb ssd. So for future reference don't get it with the ssd till Dell gets their act together!

They should have told you that sooner.

Your better off not getting the Dell SSD. When I read you got that I was like :-? I wish he didn't get that. You have to be really picky when you go SSD shopping. The non-brand-new ones have many many problems that make them not worth having.

Really, the only SSD you would want to get is a OCZ Vertex MLC or SLC. The OCZ Vertex MLC is Faster and way, way cheaper then the Intel SLC SSD that gets so much publicity. OCZ's customer support is "Unbelievably Good." The Vertex supports TRIM. The Vertex has flash-able Firmware that they keep releasing new versions of. They keep adding more and more features to the SSD's and tweaking them for speed and performance. At this point the Firmware for the OCZ Vertex is a tweaked out work of art.

Don't be fouled by GSkill with there SSD that has the same controller chip as the Vertex. It is no comparison to the speed and sold coding of the Vertex.

The Vertex is so fast it was crashing old SATA Controllers! Speeds with new firmware are ~250MB/s Read ~210MB/s Wright

---

### Post by chargersfan420 on 2009-07-03
Hey guys, it's been a while.

I did something stupid, and now i need help...

My wireless was working fine, but i noticed sometimes it would "skip" a bit... say i was downloading something, it would come in at 130 K/s, and then jump down to half of that, and then back up, and down, etc.  

I thought maybe i'd give ndisgtk a try, but it didn't work.  It claimed to install the driver, but couldn't find the hardware.  I might have been able to fix it but i decided i didn't want to use ndis-whatever, so I didn't spend much time on it.

Now I'd like to go back to the way it was, but I can't seem to figure out how.  I have no wireless at all now, wlan0 does not exist, and i found drivers at intellinuxwireless.org but installing them did nothing.  (this machine has an Intel Pro/Wireless 4965 agn card in it)

Other things i've tried include rolling back to kernel 2.6.28-11-generic (from -13-generic), reinstalling kernel headers, restricted modules, backports... nothing seems to have helped.  Any ideas?

---

### Post by HunterThomson on 2009-07-03
> **chargersfan420 said:**
> Hey guys, it's been a while.

I did something stupid, and now i need help...

My wireless was working fine, but i noticed sometimes it would "skip" a bit... say i was downloading something, it would come in at 130 K/s, and then jump down to half of that, and then back up, and down, etc.  

I thought maybe i'd give ndisgtk a try, but it didn't work.  It claimed to install the driver, but couldn't find the hardware.  I might have been able to fix it but i decided i didn't want to use ndis-whatever, so I didn't spend much time on it.

Now I'd like to go back to the way it was, but I can't seem to figure out how.  I have no wireless at all now, wlan0 does not exist, and i found drivers at intellinuxwireless.org but installing them did nothing.  (this machine has an Intel Pro/Wireless 4965 agn card in it)

Other things i've tried include rolling back to kernel 2.6.28-11-generic (from -13-generic), reinstalling kernel headers, restricted modules, backports... nothing seems to have helped.  Any ideas?

First get rid of the any other drivers that you installed or blacklist them or whatever. You could try just re-installing the Linux driver. It's in the repo "iwl4965".

Then 

sudo modprobe wlan0

sudo ifconfig wlan0 up

---

### Post by HunterThomson on 2009-07-04
> **PhilMize said:**
> Dell just delayed my order again too the 17th... I called about it and they said don't expect it till Aug. I just canceled my order and bought the Dell Studio XPS 13' w/ 8.10...They said the part that was on backorder was the 16gb ssd. So for future reference don't get it with the ssd till Dell gets their act together!

Hum, The Dell Mini 10v sounds cool. It fully supports Mac OS out of the box. I'd like to have that just to see how much better Linux is then MacOS. Na, I would just like to learn my way around MacOS a bit. I guess once you install all the BSD and GNU and Linux compatibility it's like real *nix system.

I like the look of the Dell Studio XPS 13. You will also have a nice processor and graphics card too. I think your better off with the XPS you got. Lets just hope you get it by then end of the year ;)

---

### Post by chargersfan420 on 2009-07-04
> **HunterThomson said:**
> First get rid of the any other drivers that you installed or blacklist them or whatever. You could try just re-installing the Linux driver. It's in the repo "iwl4965".

Then 

sudo modprobe wlan0

sudo ifconfig wlan0 up

Thanks Hunter, but the plot thickens... I can't find iwl4965 in the repo's... am I missing a source or something?  There's an iw package, but nothing else that starts with iw.  There's no firmware-iw* either.

Also, earlier today i physically removed and reinstalled the card itself, not sure if that should affect anything here...

UPDATE:  On one hand, I can't use wireless in XP or Vista anymore... that's weird.  On the other hand, i managed to get wlan0 back by sudo modprobe iwl4965, but it doesn't do anything, and doesn't survive a reboot.  I can't help but think a module is blacklisted somewhere but i can't find it.

XP and Vista both behave like they know i have a wireless card, they know they have good drivers, but they think the switch on the front is set to off, no matter which way it's set.

Tempted to try a live CD and see what happens...

UPDATE:  Tried a live CD, and i get the same behavior as i do in Windows.  The card is there, the drivers are present, but wireless networking is disabled, no matter which way the switch is set.  The switch turns bluetooth on and off on the live CD, which is normal, but doesn't happen in regular ubuntu because i blacklisted bluetooth.

Fortunately for me, my roommate had a 50 foot Cat5e cable, but this is getting really annoying.

---

### Post by HunterThomson on 2009-07-05
> **chargersfan420 said:**
> Thanks Hunter, but the plot thickens... I can't find iwl4965 in the repo's... am I missing a source or something?  There's an iw package, but nothing else that starts with iw.  There's no firmware-iw* either.

Also, earlier today i physically removed and reinstalled the card itself, not sure if that should affect anything here...

UPDATE:  On one hand, I can't use wireless in XP or Vista anymore... that's weird.  On the other hand, i managed to get wlan0 back by sudo modprobe iwl4965, but it doesn't do anything, and doesn't survive a reboot.  I can't help but think a module is blacklisted somewhere but i can't find it.

XP and Vista both behave like they know i have a wireless card, they know they have good drivers, but they think the switch on the front is set to off, no matter which way it's set.

Tempted to try a live CD and see what happens...

UPDATE:  Tried a live CD, and i get the same behavior as i do in Windows.  The card is there, the drivers are present, but wireless networking is disabled, no matter which way the switch is set.  The switch turns bluetooth on and off on the live CD, which is normal, but doesn't happen in regular ubuntu because i blacklisted bluetooth.

Fortunately for me, my roommate had a 50 foot Cat5e cable, but this is getting really annoying.

Did the problem get worse after you took the card out?
Sometimes, just reseting the CMOS can solve strange problems like that. I mean as simple as just selecting reset in the CMOS setup but if you can find the little battery to pull out then do that.

Ya, I got a 100' Cat5e I will never regret buying it :D

All the blacklisted modules in should be in /etc/modprobe.d/blacklist file.
I don't know the names of some of these drivers in Ubuntu but it sounds like it should be working now. It should at lest work in the LiveCD.

---

### Post by chargersfan420 on 2009-07-05
> **HunterThomson said:**
> Did the problem get worse after you took the card out?
Yes, i think that was a big mistake.  I remember reading about a problem on the Lenovo forum where removing the wireless card was the only solution.  I'm not saying that i had the same problem... i just thought it might help.
> **HunterThomson said:**
> 
Sometimes, just reseting the CMOS can solve strange problems like that. I mean as simple as just selecting reset in the CMOS setup but if you can find the little battery to pull out then do that.
Couldn't find the battery.  The BIOS has no CMOS related options.

Anyway, i have it working now, but not quite perfect.  In Vista, i tried Fn-F5, which kicked the interface back into gear.  After doing that, in Ubuntu i found i could use the card again after typing "sudo modprobe iwlagn", but this won't survive a reboot.  Sorry if my knowledge of dealing with modules is limited, but how can I make this change permanent?

---

### Post by PhilMize on 2009-07-06
Oops! LOL over the 4th of July weekend my Lenovo's screen finally cracked off! Funny though, it still works! I'm thinking I have a new platform to stream content off now! woot!

---

### Post by HunterThomson on 2009-07-06
> **chargersfan420 said:**
> Yes, i think that was a big mistake.  I remember reading about a problem on the Lenovo forum where removing the wireless card was the only solution.  I'm not saying that i had the same problem... i just thought it might help.

Couldn't find the battery.  The BIOS has no CMOS related options.

Anyway, i have it working now, but not quite perfect.  In Vista, i tried Fn-F5, which kicked the interface back into gear.  After doing that, in Ubuntu i found i could use the card again after typing "sudo modprobe iwlagn", but this won't survive a reboot.  Sorry if my knowledge of dealing with modules is limited, but how can I make this change permanent?

```
gksudo gedit /etc/modules 
```

Then add the name of the module to the bottom of the file, should work.

The CMOS (Complementary metal–oxide–semiconductor) set-up is that screen you get to by hitting F2. CMOS stores the options you select like boot order and is on volatile memory. The BIOS is the OS on that ROM chip. Ya, most people call it BIOS settings but really they are settings in CMOS.

---

### Post by chargersfan420 on 2009-07-09
Thank you, HunterThomson!

On to a new can of worms.  I have upgraded to Virtualbox 3.0.0, and it's time to migrate to a new virtual machine, since i made a huge mess of snapshots.  (My new plan - NO MORE SNAPSHOTS!  If i want a backup, i'll just copy the damn image file.  But even better than that, i'll save everything elsewhere anyway)

Anyway, it occurs to me that VT-x is disabled by default in the BIOS, and it's not a changeable option.  I'm pretty sure my T9300 is capable, but not positive on the chipset.

Then i found this post: [http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=12068&query.id=14879#M12068]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=12068&query.id=14879#M12068") 
It's entitled "Does the Y series have a crippled BIOS?"

And this post: [http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&message.id=12353&query.id=14879#M12353]("http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&message.id=12353&query.id=14879#M12353")
In this post, a guy explains how to fix the problem on a Lenovo 3000 V100, by changing a flag on a BIOS table and writing it to NVRAM.  It also has two links to two different apps that will check if VT-x is enabled.  One involved booting a CD, the other one i didn't look at.

My questions are... can we figure out how to do this on our Y series models?  Is it worth the trouble?  ... and does anyone else care enough to try it?

---

### Post by HunterThomson on 2009-07-13
> **chargersfan420 said:**
> Thank you, HunterThomson!

On to a new can of worms.  I have upgraded to Virtualbox 3.0.0, and it's time to migrate to a new virtual machine, since i made a huge mess of snapshots.  (My new plan - NO MORE SNAPSHOTS!  If i want a backup, i'll just copy the damn image file.  But even better than that, i'll save everything elsewhere anyway)

Anyway, it occurs to me that VT-x is disabled by default in the BIOS, and it's not a changeable option.  I'm pretty sure my T9300 is capable, but not positive on the chipset.

Then i found this post: [http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=12068&query.id=14879#M12068]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=12068&query.id=14879#M12068") 
It's entitled "Does the Y series have a crippled BIOS?"

And this post: [http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&message.id=12353&query.id=14879#M12353]("http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&message.id=12353&query.id=14879#M12353")
In this post, a guy explains how to fix the problem on a Lenovo 3000 V100, by changing a flag on a BIOS table and writing it to NVRAM.  It also has two links to two different apps that will check if VT-x is enabled.  One involved booting a CD, the other one i didn't look at.

My questions are... can we figure out how to do this on our Y series models?  Is it worth the trouble?  ... and does anyone else care enough to try it?

Well, the snapshots are smaller. I would guess/hope there done 'log-structured file systems' style only backing up files that have changed.

Ya, it has VT
[http://processorfinder.intel.com/details.aspx?sSpec=SLAQG](http://processorfinder.intel.com/details.aspx?sSpec=SLAQG)

My laptop had a T5550 which doesn't have VT-x so no option in the BIOS for it. Would be better to have it. My new laptop has the VT-x option in the BIOS.

---

### Post by vonmars on 2009-07-19
Has anyone figured out how to get the microphone working on their Y510, and if so can you post step-by-step instructions or point me to ones that already exist?  My sound is working beautifully.  I just need my microphone to work.

Thanks!

---

### Post by HunterThomson on 2009-07-20
> **vonmars said:**
> Has anyone figured out how to get the microphone working on their Y510, and if so can you post step-by-step instructions or point me to ones that already exist?  My sound is working beautifully.  I just need my microphone to work.

Thanks!

you need to open the ALSAmixer and find where it has the mic options. You need to set both mic's to "Front mic".

---

### Post by vonmars on 2009-07-20
> **HunterThomson said:**
> you need to open the ALSAmixer and find where it has the mic options. You need to set both mic's to "Front mic".
I have tried just about every combination I can imagine in the Alsa mixer.  I have three sliders relating to microphone.  Plain old microphone, front microphone and mic boost.  Microphone seems to do nothing.  I have it set to front mic.  When I raise the mic boost slider it produces some pretty irritating feedback, but when I test the audio recording the mic is still not working.  Any other ideas?  Thanks for your help.

---

### Post by HunterThomson on 2009-07-21
> **vonmars said:**
> I have tried just about every combination I can imagine in the Alsa mixer.  I have three sliders relating to microphone.  Plain old microphone, front microphone and mic boost.  Microphone seems to do nothing.  I have it set to front mic.  When I raise the mic boost slider it produces some pretty irritating feedback, but when I test the audio recording the mic is still not working.  Any other ideas?  Thanks for your help.

Sorry I should have been more specific.

It is not a slider that needs changing though ya unmute it and stuff I guess. No need to have Mic Boost all the way up or anything. Just Mic and Front Mic.

What needs to be changed to Front Mic is in another 'tab' in the Gnome GUI ALSAmiser. It will give you two dropdown list to select  mic , front mic or mic boost.

If you open a terninal and run...

```
alsamixer
```

it will open up a terminal GUI app. In there you hit the tab button and look at the top left it has...

Card: balbal
Chip: blabla
[COLOR="Blue"]**View: Playback  Capture  All**[/COLOR]
Item: blabla

When you hit tab it will change the "View" option. Ether tab until it is on "ALL" or "Capture". 

Then use the arrow keys to move over to the "input" one and use the UP,Down arrow to set them to "Front Mic".

After you have the "Input" set to "Front mic" in the ALSAmixer. You only need to mess around with the setting in the application to get it to work.

---

### Post by vonmars on 2009-07-24
Thanks.

I will give this a try tonight!  :D

---

### Post by vonmars on 2009-07-24
> **vonmars said:**
> Thanks.

I will give this a try tonight!  :D

It worked!!  You Rule!  My Y510 is fully functional.  WOO HOO!!!!

---

### Post by HunterThomson on 2009-07-25
> **vonmars said:**
> It worked!!  You Rule!  My Y510 is fully functional.  WOO HOO!!!!

That is fantastic :)

---

### Post by abartylla on 2009-08-17
Hey guys I'm going to be installing 9.04 onto my friends Y510 since Vista crapped out on him. I am curious what kind of problems I will run into and what should I take care of first? From what I have read I mainly need to fix backlight, sound, and mic off the bat. Is there anything else or any suggestion/recommendations that you can make for a clean install of ubuntu 9.04 on to a y510?

---

### Post by abartylla on 2009-08-20
I just got done with the alsa setup as noted on the first page of this forum. Everything that should be set to 100 in alsa is set to 100 and the sound sounds weak even when maxed out. Maybe its just me

Nevermind it was the PCM

---

### Post by wyth on 2009-08-20
I've been well out of this loop for some time (rebuilding some of my machine), but I decided to try the 2.6.30 kernel.

After making sure the Master, PCM, Front, Surround, Center, and LFE sound levels were all cranked to 11, then pulling back from there, the sound works great -- and that was the only thing.

The reason I went with the 2.6.30 kernel was to disable IPv6 system-wide.  In the current kernel, IPv6 is enabled automatically, and it can't be turned off without recompiling the kernel.  I didn't feel like recompiling, and I wanted the speed boost afforded by turning off IPv6, so 2.6.30 kernel, here we come.

If you're interested in trying it out (and it may solve a few other hardware issues for some), here's what to do (borrowed from the** [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showpost.php?p=7104256&postcount=1")**).

In your terminal, run the following commands, depending on the system you're using (32 bit or 64 bit):

**i386 users:**
     ```
$ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb")
$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb 
```**amd64 users:**
     ```
$ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb")
$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb 
```Once installed, you'll need to restart.  Then adjust your sound as mentioned above.  There should be no no need to compile ALSA (I haven't had to in two versions), and the backlight and other issues aren't problems for me.

---

### Post by abartylla on 2009-08-21
Thanks wyth that really simplified my sound issues and the backlight was not a problem for me either. I've spent the past hour crawling through 3 different forums trying to figure out this upside down webcam thing. Is there anyone out there that can give a summary of or the fix to this issue I still do not understand how to fix this.

---

### Post by HunterThomson on 2009-08-23
> **abartylla said:**
> Thanks wyth that really simplified my sound issues and the backlight was not a problem for me either. I've spent the past hour crawling through 3 different forums trying to figure out this upside down webcam thing. Is there anyone out there that can give a summary of or the fix to this issue I still do not understand how to fix this.

Nope sorry if the application dosn't have the option to rotate the picture back upright then there is no way to fix it. As far as I remember onone ever fixed it.. well apart from taking apart the laptop.

---

### Post by onemyndseye on 2009-08-24
Hi guys,

  Just got a stellar deal on one of these laptops and have been digging through this thread the last 4-5 days..

I see the webcam issue was never worked around...  Wyth's seem to better than mine which just renders a black screen. Anyone ever find a solution for the non-working App Launch, Dolby, and EQ touch buttons? Keytouch was a utter fail for me... so I starting looking a little deeper.

Using acpi_listen I learned that App Launch doesnt have an event. No event in xev either..  The Dolby buttons AND the EQ buttons all return a event.  Notice I said *A* event...

All of these keys return the acpi code: hotkey ATKD 000000b3 xxxxxxxxxx

Without separate events I am not sure how to proceed, however I have worked up a solution to toggling Surround On/Off

Create these files -

/etc/acpi/events/lenovo-touch-surround
```

# /etc/acpi/events/lenovo-touch-surround

event=hotkey (ATKD) 000000b3
action=/etc/acpi/lenovo-touch-surround.sh


```


/etc/acpi/lenovo-touch-surround.sh
```

#!/bin/bash
# Script to handle ACPI button press to toggle surround on/off
#

# Source in ACPI functions
. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs


ICON=/usr/share/icons/gnome/32x32/devices/audio-card.png
OSD="$(which notify-send)"

getXconsole;
if [ x"$XAUTHORITY" != x"" ]; then
  xhost +local:root
  VALUE="$(amixer cget numid=4 |egrep -v "type|name" |sed '{s|values=|| ; s| : || ; s|,| | }' | awk '{print $1}')"
  if [ "$VALUE" = "on" ]; then
    [ -n "$OSD" ] && notify-send --icon=$ICON "Surround Sound" "Off"
    amixer cset numid=8 0
    amixer cset numid=7 0
    amixer cset numid=4 0
  else
    [ -n "$OSD" ] && notify-send --icon=$ICON "Surround Sound" "On"
    amixer cset numid=8 1
    amixer cset numid=7 1
    amixer cset numid=4 1
  fi
  xhost -local:root
fi

```

then:
```

sudo /etc/init.d/acpid restart

```

This creates an acpi event for the button press and runs the script in /etc/acpi/ which in turn sends a notify event and toggles on/off the following mixer controls: LFE, Center, Surround

Because the same acpi event is returned by the EQ buttons as well pressing any of the following buttons will toggle your surround: Dolby, EQ Jazz, EQ Pop, EQ Dance, EQ Classical, EQ Normal.

Not a perfect solution but it works for me.  Tested throughly on a up-to-date Jaunty system.


Hope this helps,
-onemyndseye

---

### Post by HunterThomson on 2009-08-25
onemyndseye: That looks like some cools stuff. I have no idea how to set it up with out it giving distinct codes though.

---

### Post by onemyndseye on 2009-08-25
Hunter T,

Yeah...  cant really proceed with the rest of the buttons without a ACPI or ACPI module patch Im guessing..  and thats abit beyond my realm

But this little solution works well if you are mostly concerned with the Surround button (as I was)..  I have found myself using it like a Attenuation switch...  for time when I wish to reduce the sound volume for a moment without completely muting the sound or messing with your volume level...  then at the touch of a button things return to normal. ;) This action script could be changed to a more accurate example of an Attn button easily enough.  Reducing Master Output to ~25% then back to your previous setting at next press.

I'll do some looking around and see if I can locate the piece of code that is responsible for the events and try to get some Idea of how feasible it is to apply a patch...  Looking at the list of modules thats loaded now I guess asus_laptop would be a decent place to start.

I will report that I moved to the 2.6.30-5 kernel and the NVIDIA driver 185.18.36 /w libvdpau with no issues at all on a Jaunty system as posted earlier in this thread. Note that for nvidia users the upgrade to 185+ is required or dkms will fail to build it.

Found here:
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

-and-

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/)

---

### Post by HunterThomson on 2009-08-27
> **onemyndseye said:**
> Hunter T,

Yeah...  cant really proceed with the rest of the buttons without a ACPI or ACPI module patch Im guessing..  and thats abit beyond my realm

But this little solution works well if you are mostly concerned with the Surround button (as I was)..  I have found myself using it like a Attenuation switch...  for time when I wish to reduce the sound volume for a moment without completely muting the sound or messing with your volume level...  then at the touch of a button things return to normal. ;) This action script could be changed to a more accurate example of an Attn button easily enough.  Reducing Master Output to ~25% then back to your previous setting at next press.

I'll do some looking around and see if I can locate the piece of code that is responsible for the events and try to get some Idea of how feasible it is to apply a patch...  Looking at the list of modules thats loaded now I guess asus_laptop would be a decent place to start.

I will report that I moved to the 2.6.30-5 kernel and the NVIDIA driver 185.18.36 /w libvdpau with no issues at all on a Jaunty system as posted earlier in this thread. Note that for nvidia users the upgrade to 185+ is required or dkms will fail to build it.

Found here:
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/)

-and-

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/)

The hot key table is a BIOS file. It is not the DSDT it is I think the ESDT ??? One of thoughs. You could look at it and see if there is a way to change it to make it do what you want. It's not hard to edit code it is only hard to wright an application form the ground up.

---

### Post by onemyndseye on 2009-08-27
haha... very true ;)   Im not much of a programmer but I'll hack something to pieces from time to time ;)

i.e.  I just modded the network-manager-openvpn package to included the sorely missing --float option.

If this is somehting that interest you, you may check it out here (Thread to come):

[http://dl.getdropbox.com/u/1397571/network-manager-openvpn_0.7.1%7E20090213%2Bbzr14-0ubuntu1%7Eonemyndseye1.diff.gz](http://dl.getdropbox.com/u/1397571/network-manager-openvpn_0.7.1%7E20090213%2Bbzr14-0ubuntu1%7Eonemyndseye1.diff.gz)

[http://dl.getdropbox.com/u/1397571/network-manager-openvpn_0.7.1%7E20090213%2Bbzr14-0ubuntu1%7Eonemyndseye1_i386.deb](http://dl.getdropbox.com/u/1397571/network-manager-openvpn_0.7.1%7E20090213%2Bbzr14-0ubuntu1%7Eonemyndseye1_i386.deb)


Based on the version in the PPA right now ([https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa))

---

### Post by chargersfan420 on 2009-08-30
Thanks to Wyth for the great info.  I've now moved to 2.6.30 as well.

For anyone else with a Y710 (am i the only one out there?) or with an ATI Radeon HD2600, if you're going to try this you should download the newest ATI drivers before you switch.  9.7 won't work on 2.6.30, so having 9.8 downloaded and ready to install once you boot into 2.6.30 will make for a smoother transition.

Wyth was totally right, though.  Ethernet / wireless is much faster with IPv6 disabled.  I can't seem to kill it when booting with LILO though - it seems that kernel command switches are handled differently (or not at all?)  

I notice I still can't hibernate, because I'm now back to my vanilla DSDT.  After mucking around with it, i found this thread:
[[COLOR="Blue"]Custom DSDT patch removed since 2.6.30[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1247168")

I'd like to try out onemyndseye's suggestions for the media buttons, but acpi_listen isn't returning anything when i press them, so I'm thinking I best get the fixed DSDT working first... 

If I can get that going, I'd like to use the dolby button to toggle all of my speakers on / off, because they still don't mute when I plug in headphones, and there are times where i want external speakers + laptop speakers all going at once.  Lol, is this a silly idea?  Did you guys find a simpler way?

---

### Post by HunterThomson on 2009-08-31
> **chargersfan420 said:**
> Thanks to Wyth for the great info.  I've now moved to 2.6.30 as well.

For anyone else with a Y710 (am i the only one out there?) or with an ATI Radeon HD2600, if you're going to try this you should download the newest ATI drivers before you switch.  9.7 won't work on 2.6.30, so having 9.8 downloaded and ready to install once you boot into 2.6.30 will make for a smoother transition.

Wyth was totally right, though.  Ethernet / wireless is much faster with IPv6 disabled.  I can't seem to kill it when booting with LILO though - it seems that kernel command switches are handled differently (or not at all?)  

I notice I still can't hibernate, because I'm now back to my vanilla DSDT.  After mucking around with it, i found this thread:
[[COLOR="Blue"]Custom DSDT patch removed since 2.6.30[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1247168")

I'd like to try out onemyndseye's suggestions for the media buttons, but acpi_listen isn't returning anything when i press them, so I'm thinking I best get the fixed DSDT working first... 

If I can get that going, I'd like to use the dolby button to toggle all of my speakers on / off, because they still don't mute when I plug in headphones, and there are times where i want external speakers + laptop speakers all going at once.  Lol, is this a silly idea?  Did you guys find a simpler way?

Boy I am glad that DSDT Kernel Patch was still in when I needed it. Sucks that it's excluded and may not work at all anymore.

---

### Post by onemyndseye on 2009-09-01
Well,

Im still poking around abit with this...    Looks like the needed tables are either in FADT or XSDT but Im having trouble making sense of it. On a positive note, if this could be made to work it could be coupled with the great pulse HOWTO thread [Here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=789578") to actually provide EQ presets as in Vista

---

### Post by chargersfan420 on 2009-09-04
> **onemyndseye said:**
> Well,

Im still poking around abit with this...    Looks like the needed tables are either in FADT or XSDT but Im having trouble making sense of it. On a positive note, if this could be made to work it could be coupled with the great pulse HOWTO thread [Here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=789578") to actually provide EQ presets as in Vista

A HUGE HUGE HUGE thank you to onmyndseye for this last post.  After reading up on the link you provided, I decided to give PulseAudio another try, which led me to try once again to accomplishing something I've always dreamed of and wasted time on for years:  running MediaMonkey in wine.  For once I finally have it working!

(for those not familiar with MediaMonkey, it's only the best media program ever, IMHO)

Anyway, I went a step further and found an Amarok script that successfully made use of my Play/Pause, Stop, Previous, Next buttons with Amarok, so i tweaked it a little bit to launch a small console app in Wine that would manipulate MediaMonkey.  The script looks useful enough to make these buttons do whatever you want them to, if you're up to hacking it.
Original Amarok script was found [here]("http://www.kde-apps.org/content/show.php?content=103448").
My hacked version is attached.  All the credit in the world to Chris Brown for creating the script, but no fault of his if my hacked copy doesn't work for you.  I mostly just took out Amarok-related stuff, because I don't know anything about python.

In the middle of the file, you'll see this:
```
for mmk in mmkeys:
        	if mmk == "Play":
			print "playPause"
			os.system("wine 'C:\mmscripts\mmh.exe' /playpause")
		elif mmk == "Pause":
			print "pause"
			os.system("wine 'C:\mmscripts\mmh.exe' /playpause")
		elif mmk == "Stop":
			print "stop"
			os.system("wine 'C:\mmscripts\mmh.exe' /stop")
		elif mmk == "Next":
			print "next track"
			os.system("wine 'C:\mmscripts\mmh.exe' /next")
		elif mmk == "Previous":
			print "previous track"
			os.system("wine 'C:\mmscripts\mmh.exe' /prev")
```
Just replace the contents of the quotes to launch the command of your choice.  The Amarok script used dcop to pass a command to Amarok.  If you want to use MediaMonkey with wine like I am, you'll also need the Windows script i made (mmh.exe).  I'll post it if anyone asks for it, but it's not the most polished script I've ever written.

I also tried to put "print mmk" just after the For statement, but it wouldn't print any additional output for the other buttons.  So far we have 5 working (including mute), and 7 more to go.

I also noticed that when using the command "xev", i can return output on all of the working buttons so far, but it reports the same thing with all of them:
```
FocusOut event, serial 32, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 32, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

System - Preferences - Keyboard Shortcuts allows you to set these hotkeys, which is how the script recognizes them, but careful, because i can't seem to put one back that i accidentally took out.  You'll notice there's a lot of XF86 stuff in here?

My next thought is using a program like KeyTouch, we might be able to specify a compatibility with a different keyboard, something in the XF86 spec, and perhaps more buttons might be recognized...?

EDIT:  Attached mmh.exe (in mmh.zip) for Mediamonkey / Wine users.  More details on how to use it can be found here:
[http://www.mediamonkey.com/forum/viewtopic.php?f=2&t=42432&p=221247#p221247]("http://www.mediamonkey.com/forum/viewtopic.php?f=2&t=42432&p=221247#p221247")

---

### Post by onemyndseye on 2009-09-09
Yeah... same issue here. The Dolby button and all EQ buttons report the same event :/ Only the novo button and the quick launch key are completely dead...

Keytouch didnt work at all for me..  couldnt get anything out of it although it is possible to create a keyboard file for it.

Even if you did get it to work it basicially just listens to the acpi calls so you would still be stuck with 6 buttons that all do the same thing...  unless we can find a way to update the acpi tables...   still digging for info on this but its slow going.

does MediaMonkey support DAAP? (Itunes shares).  I have a Open-DAAP server running on my MythTV machine at home that I connect to with rhythmbox to access my music..  This coupled with OpenVPN means I have instant access to my MP3s (120gig worth) from anywhere in the world with a internet connection..   sooooooooo   damn nice :)

Its interesting that xev is showing an event for you..  mine doesnt for ANY of the soft touch keys...  though the media controls work perfectly  lol

---

### Post by onemyndseye on 2009-09-09
I like this too (messing with acpi events):

I prefere for my audio to be turned off when I close the lid..  speakers too muffled by the lid anyway so Id rather have it mute..  if the lid is close my attention is not on it.. and it saves power on battery mode...

/etc/acpi/events/lenovo-extra-lidbtn
```

# /etc/acpi/events/lidbtn
# Extra event called when the user closes or opens the lid for lenovo laptops to
# mute/unmute the sound

event=button[ /]lid
action=/etc/acpi/lenovo-extra-lid.sh


```


/etc/acpi/lenovo-extra-lid.sh
```

#!/bin/bash
# Script to handle ACPI lid close to mute sound
#

# Source in ACPI functions
. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs


getXconsole;
if [ x"$XAUTHORITY" != x"" ]; then
  VALUE="$(amixer cget $(amixer controls |grep "Master" |grep "Switch" |sed '{s|,| |g}'|awk '{print $1}') |egrep -v "type|name" |sed '{s|values=|| ; s| : ||$
  if [ "$VALUE" = "on" ]; then
    amixer cset $(amixer controls |grep "Master" |grep "Switch" |sed '{s|,| |g}'|awk '{print $1}') 0
  else
    amixer cset $(amixer controls |grep "Master" |grep "Switch" |sed '{s|,| |g}'|awk '{print $1}') 1
  fi
fi

```


Same script should work on nearly any laptop that has a correctly working lid switch and a Master Playback toggle switch in alsa controls...   everyone wont like this but I thought Id share.

---

### Post by JSuresh on 2009-09-22
Hey guys, so my old 65 watt y510 power cord died so I am thinking of buying a new one from lenovo, this one is 90 watts though.  Will the higher watts kill my computer, or is it safe? :confused:

---

### Post by winnibob on 2009-09-23
> **JSuresh said:**
> Hey guys, so my old 65 watt y510 power cord died so I am thinking of buying a new one from lenovo, this one is 90 watts though.  Will the higher watts kill my computer, or is it safe? :confused:

It is safe, since your computer will only consume the power it needs, i.e. your power supply can't make your computer consume more power than it needs and kill it. 90 watts is just the maximum your power supply can give to your computer, and if you try to get more it may die, but less is ok.

To give you an idea, when you use your Y510 normally, without charging the battery, it consumes 25 to 35 watts, but when the battery is charging, it may consume up to 65 watts.

So there is not any problem about using a 90 watts power supply, but it may be bigger and more expensive.

---

### Post by wyth on 2009-09-29
Just a note:

My power cord recently died as well.  I had a back-up targus one with multiple connectors from way back -- it works fine and it's less expensive.

---

### Post by spandanj on 2009-10-05
How do I get my microphone to work with programs in ubuntu 9.04. I know the front mic is working b/c when I turn it on I can hear noise, and myself speaking. However, sound recorder and skype can't actually use the mic ...

So how do I set it up?

Here is my /etc/modprobe.d/alsa-base.conf

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2 

---

### Post by winnibob on 2009-10-12
Hi guys, has anyone had problems with usb really slow transfer rate (especially for pen drives) since we use 2.6.28.x kernel?

I saw that many people around the web has this problem with debian-based distros, and no one could find out how to resolve it. That's why I'm asking this to you : to see if that may be a hardware compatibility problem instead of a configuration one.

Thanks for telling.

---

### Post by onemyndseye on 2009-10-29
Further tinkerings with the sound system:


I setup alsa and OpenAL for surround sound support and maped my speakers correctly.  I havnt looked into how to accomplish this with Pulse yet but the issue was (as Im sure some of you have seen) that the speakers were abit mixed up in terms of directional when using the surround51 pcm.

This laptop has 5 speakers total: [Shown here]("http://i38.tinypic.com/5vvuox.jpg")

They represent the following channels:
1   -  Front Left 
2   -  Front Right
3   -  Rear Left
4   -  Rear Right  
5   -  LFE/Subwolfer (Bottom of laptop)

I should note at this point that im using the following snd-hda-intel module config each of the commented modules worked wth slightly different results.  Sky was the closest.
```

onemyndseye@onemyndsmobile:~$ cat /etc/modprobe.d/hda-intel.conf 
# 3stack-6ch
# 3stack-6ch-intel
# lenovo-ms7195-dig (Lenovo MS7195)
# lenovo-sky (Lenovo Sky)


options snd-hda-intel model=lenovo-sky

```


Then I needed a proper speaker map to get "5.1 surround".

The default surround device (pcm surround51) had my  channels alittle mixed up. The Front and Rear was reversed and any call to Center rear was handled by the LFE only. For example in Quake4, a enemy shooting at you from behind would only sound in the LFE. eewww.

so I remaped as follows.  The syntax I learned for this maping is:
ttable.MAP_CHAN.REAL_CHAN  GAIN

MAP_CHAN = Represented channel 
REAL_CHAN = Actual channel as identified by alsa
GAIN  =  Gain/Volume at a fraction (1 = 100%)


My ~/.asoundrc
```

pcm.!default {
	type plug
	slave.pcm "lenovo_surround"
	slave.channels 6
	route_policy duplicate
}


pcm.lenovo_surround {
        type route
        slave.pcm surround51
        slave.channels 6

        # Front  with 50% volume LFE for both channels
        ttable.0.2 0.7	## Front Left		(Speaker 1)
        ttable.1.3 0.7	## Front Right		(Speaker 2)
        ttable.0.5 0.5	## Touch sub		(Speaker 5)
        ttable.1.5 0.5	## Touch sub		(Speaker 5)

        # Rear with 50% volume LFE for both channels
        ttable.2.0 1.0	## Rear Left		(Speaker 3)
        ttable.3.1 1.0	## Rear Right		(Speaker 4)
        ttable.2.5 0.5	## Touch Sub		(Speaker 5)    
        ttable.3.5 0.5	## Touch Sub 		(Speaker 5)   

        # Center (Spkr1+Spkr2) with 50% volume LFE  
        ttable.4.2 0.5	## Center Left		(Speaker 1)
        ttable.4.3 0.5	## Center Right		(Speaker 2)
        ttable.4.5 0.5	## Touch Sub		(Speaker 5)  
              
        # Center Rear  (Spkr3+Spkr4) with 50% volume LFE
        ttable.5.0 0.5	## Center Rear Left	(Speaker 3)
	ttable.5.1 0.5	## Center Rear Right	(Speaker 4)
	ttable.5.5 0.5	## Touch Sub		(Speaker 5)
}

```


The OpenAL config: ~/.alsoftrc
```


format = AL_FORMAT_51CHN16

refresh = 6144
#sources = 256
stereodup = True
drivers = alsa

##
## ALSA backend stuff
##
[alsa]

device = lenovo_surround  # Call my virtually maped device
#periods = 0
mmap = true

```



Still playing with the volume levels abit to get that "just right mix" but I've tested this with [Regnum Online]("http://www.regnumonlinegame.com/") and Quake4 with satisfying results.  I dont expect this exact example to work for anyone else or do I truely believe it to be a 100% correct (for instance: the gains in most channels are too high.  i.e.  Center Rear should total to 1) example of mixing 5.1 surround, but it gave me the results I was looking for and hopefully will save someone the trouble of figuring this crap out  lol.

---

### Post by JSuresh on 2009-10-30
So I'm *excited* but also scared.  Has anyone tried 9.10 for the y510 yet?  :popcorn: 

I'm still on Gutsy =O

---

### Post by michaelzap on 2009-10-30
I have a Y530 and I did a clean install of Karmic x64 last night. So far it's a vast improvement over Jaunty. Pulseaudio seems to work properly, the Intel video driver now works well with the new kernel (no flickering or tearing), and overall it feels fast and smooth.

I did have a few freezes last night as I was installing apps, however, so we'll see how that goes over the next few days.

---

### Post by commonplace on 2009-11-01
> **michaelzap said:**
> I have a Y530 and I did a clean install of Karmic x64 last night. So far it's a vast improvement over Jaunty. Pulseaudio seems to work properly, the Intel video driver now works well with the new kernel (no flickering or tearing), and overall it feels fast and smooth.

I did have a few freezes last night as I was installing apps, however, so we'll see how that goes over the next few days.

I also have a Y530 and did Karmix x64 and it was terrrrriiiibble. No sound at all, and it completely locked up frequently.

I'm tempted to give it yet another go, but... ugh. It seems to be a problem with the kernel and all the new distros use the kernel, which would explain why none of the new distros (I tried the latest betas/release candidates of openSUSE, Mandriva, and of course the final release of Ubuntu 9.10) worked on this laptop.

Has anyone else had success in getting 9.10 to work on the IdeaPad Y530? And by success, I mean, working sound and no lockups?

/Kevin

---

### Post by michaelzap on 2009-11-01
> **commonplace said:**
> I also have a Y530 and did Karmix x64 and it was terrrrriiiibble. No sound at all, and it completely locked up frequently.

I'm tempted to give it yet another go, but... ugh. It seems to be a problem with the kernel and all the new distros use the kernel, which would explain why none of the new distros (I tried the latest betas/release candidates of openSUSE, Mandriva, and of course the final release of Ubuntu 9.10) worked on this laptop.

Has anyone else had success in getting 9.10 to work on the IdeaPad Y530? And by success, I mean, working sound and no lockups?

/Kevin

I should have come back here and corrected my previous post. I had a brief Karmic honeymoon, but after that things went sour. I'm still having pretty serious stability issues, which you can read about here:
[http://ubuntuforums.org/showthread.php?p=8215338#post8215338](http://ubuntuforums.org/showthread.php?p=8215338#post8215338)

Removing the proprietary modem driver in System -> Hardware Drivers got my sound to work reliably, although only in stereo.

Right now I'm seeing what happens if I turn off Compiz, although I'm not convinced that it's related to the crashing I've had.

---

### Post by commonplace on 2009-11-01
Just posted this in another thread:

Alright, here's something weird (at least, to me): I wiped out everything and installed **K**ubuntu 9.10 -- and it works great. Sound works. No freezes. No kernel errors. No speed issues. Everything is great.

I don't understand why this is, unless my issues were specific to GNOME...?? That doesn't really make sense to me, but it's the only explanation I have at the moment. I mean, this is the same kernel... so it's not the kernel, apparently.

I prefer KDE over GNOME but I'm going to stick with this for awhile and adapt -- it's better than having an unusable GNOME-based system (Ubuntu).

/Kevin

---

### Post by chargersfan420 on 2009-11-04
Call me crazy, but I like to run the disc checking program on install CD's at least 3 times before i use it to install.  I've had discs that passed only on the first try, and I figure using it after a failure is asking for trouble.

I plan to do a clean install over the weekend.  Usually i wait until downloading updates won't be too difficult on the Ubuntu server side, but i temporarily have my hands on a spare hard drive, and it seems like a good opportunity to try it.  For some reason I have had problems with every x.10 version on this laptop, so I'm scared too.

There is some incentive for Y710 users (or others with ATI HD series graphics adapters) to move to the 2.6.32 kernel early (or wait until it is deployed stable in 10.04), as apparently you won't have to use proprietary drivers anymore.  I think I'll be setting aside a small chunk of hard drive space to try this out on a test install.

There's also hope that GRUB2 will finally recognize my optical drive once again and i can finally ditch LILO.

---

### Post by JSuresh on 2009-11-08
I've heard early updaters to 9.10 have been having more headache than normal.  I'll probably wait until Christmas break to upgrade..

---

### Post by chargersfan420 on 2009-11-08
I can confirm headaches.  Firefox is broken, continually dropping my sessions without warning.  The flash plugin is the suspected culprit, but I don't know for sure what's wrong.  It comes with 3.5.2 by default, but some threads I found say 3.5.4 is just as bad.

Webpages seem to take forever to load now, and this doesn't seem to be firefox-specific either.  I decided to take Konqueror for a spin, and it took its time too... maybe a driver problem?

I also decided to try out Evolution and it crashed on me a couple of times too.

Good thing i can just plug in my other HDD with 9.04 on it!

Also tried to move to 2.6.32 but i can't seem to find a precompiled version, so I'm going to wait on that one.

---

### Post by michaelzap on 2009-11-08
> **chargersfan420 said:**
> Also tried to move to 2.6.32 but i can't seem to find a precompiled version, so I'm going to wait on that one.

The latest Release Candidate (2.6.32-rc6) can be found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

It made my Y530 stop crashing constantly with Karmic.

---

### Post by Sapfeer on 2009-11-27
I have a problem with sound... After some time I can't hear anything but fizz from out dynamics or headphones... Is there a way to work it out?..

---

### Post by bwsmith7 on 2009-12-03
I'm a completely new Ubuntu user (and not all that computer-literate), so apologies in advance if I am missing something completely obvious :)

I am running Ubuntu 9.1, and my webcam (Lenovo Easy Camera) is appearing upside down.  Ubuntu does detect and recognize my webcam - I can use it in Skype and Cheese - but in each instance it is upside down. I've searched through the help forums but can't seem to find a solution. Any assistance would be greatly appreciated! Thanks,

-Brent

---

### Post by HunterThomson on 2009-12-06
> **bwsmith7 said:**
> I'm a completely new Ubuntu user (and not all that computer-literate), so apologies in advance if I am missing something completely obvious :)

I am running Ubuntu 9.1, and my webcam (Lenovo Easy Camera) is appearing upside down.  Ubuntu does detect and recognize my webcam - I can use it in Skype and Cheese - but in each instance it is upside down. I've searched through the help forums but can't seem to find a solution. Any assistance would be greatly appreciated! Thanks,

-Brent

Aloha, 

It's been a long time sens I posted here.

Hum, unless someone has found a fix for this.... I think it is still an unsolvable problem. However, I know cheese has an option to flip the image but I am sure you want it for Skype.

Hum though. I don't think it is upside down to the person receiving the video of you.... Or is it?

----------

Don't let this drive you away from Linux though. I know you will love Linux and never want to go back to Windows after a month or so... You know after you learn how to do the things you like to do with your computer.

Also, I think and the 4 friends I have moved to Linux think Ubuntu is a much easyer OS to use for people that are not Geeks.

The reason is that Windows is a VARY high maintenance OS.
i.e. with windows you have to manage Viruses, Spy-ware, Ad-ware, Disk Fragmentation, File-system Corruption, OS crashing.... You also have to dig through ripoff software to find an application that dose what you need and this is made harder because you don't know the software sucks until after you already payed for it. Owe, also the Windows Kernel corrupts drivers. This is why Wireless, Printers, bla bla, Just stop working randomly in Windows and you need to reboot or even reinstall the driver.

With Ubuntu .. Ya it is work to learn a new OS. However, in just a month or so that will be over for the most part. You also have forums like these full of people looking to help others.....

After that, Ubuntu is a Zero maintenance OS. No Viruses, Spy-ware, Ad-ware. The Disk NEVER gets Fragmented with the ext file-system. Drivers never get corrupted. And All the Software is Free and you don't have to hunt anywhere on the web for it. It is all in the software repository.

============================

Try these Vary Cool Audo and Video Apps :)

**LMMS** - This is just like FrutyLoops aka FLstudio for Windows. It even handles standards such as SoundFont2, VST(i), LADSPA, GUS Patches, and MIDI

**Kdenlive** - This is for Video editing. Heck you could use this to flip videos you made with your web cam

_Avidemux_ - This is for Video editing but not as useful as Kdenlive.

---

### Post by bwsmith7 on 2009-12-06
Thanks for the reply HunterThomson.  I do like Ubuntu a lot, better than Windows Vista or Windows 7, and would love to keep it as my primary OS.  It's doing a lot of things really well, and although the learning curve is a bit steep at first, overall I am happy with the system :-) 

That said, I really need a fix for the webcam.  It is upside down to me and to the person receiving it.  I am currently teaching overseas, and the main way I stay in contact with family back home is through video chat.  Do you think that if I bought a cheap external webcam, it would be usable?

---

### Post by HunterThomson on 2009-12-06
> **bwsmith7 said:**
> Thanks for the reply HunterThomson.  I do like Ubuntu a lot, better than Windows Vista or Windows 7, and would love to keep it as my primary OS.  It's doing a lot of things really well, and although the learning curve is a bit steep at first, overall I am happy with the system :-) 

That said, I really need a fix for the webcam.  It is upside down to me and to the person receiving it.  I am currently teaching overseas, and the main way I stay in contact with family back home is through video chat.  Do you think that if I bought a cheap external webcam, it would be usable?

Owe that sucks. 


**EDIT: Check out the link in my next post**
""""
But, Ya for sure an external webcam should be just fine. Do google it though like...

webcam model ubuntu
webcam model site:ubuntuforums.org

Just to be sure.
""""

The reason no one has been able to fix the internal one is that no one knows what the problem is exactly. Some Ideapads have a problem and some don't even the same model. Most likely it is a bug in the BIOS. You can find my ranting an raving about BIOS's in this thread. The short and sweet of it is that all the BIOS problems are form Microsoft being a one evil company.

-------------

I am hunting for one for you. I'll post when I find one I would buy.

---

### Post by HunterThomson on 2009-12-06
OK cool I found a nice list of them here

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

I hope I saved you a headache.
Maybe get a slightly better webcam then the internal one to help justify buying it.

Pleas let us know if you need anymore help.

Aloha :D

---

### Post by bwsmith7 on 2009-12-06
Thanks for your suggestion, but it's working now! I followed the instructions on this page: [http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

 It took me a bit to understand how to add repositories, and after I did that the packages still weren't showing up in the package manager so I had to use the terminal... I was just copying and pasting somewhat at random (probably not the smartest method), but somehow something changed and now it works, so I'm happy. I wish I could copy the terminal output but I've closed it already. Anyway hope that fixes things for anyone else who may be having problems!

---

### Post by HunterThomson on 2009-12-06
> **bwsmith7 said:**
> Thanks for your suggestion, but it's working now! I followed the instructions on this page: [http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

 It took me a bit to understand how to add repositories, and after I did that the packages still weren't showing up in the package manager so I had to use the terminal... I was just copying and pasting somewhat at random (probably not the smartest method), but somehow something changed and now it works, so I'm happy. I wish I could copy the terminal output but I've closed it already. Anyway hope that fixes things for anyone else who may be having problems!

WOW !!!!!

I'll add that to the first post in this Thread.

Thanks for letting us know :KS

---

### Post by HunterThomson on 2009-12-06
OK bwsmith7

I added your fix to the top of the second post of this thread and gave you credit for finding the solution.

Boy we have been looking for a fix for this for like 2 years now.

Good Job !

**This makes you one of the most important contributers to this thread ever !**

---

### Post by onemyndseye on 2009-12-18
I can confirm this working on x64....  sort of.

Great find none-the-less


My issue:

` LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese ` doesnt work at all.   cheese never gets video from the cam and eventually hangs. However running cheese normally now shows that the cam is right-side-up

` LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype ' returns:
```


ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


```

Images are still upside-down in skype...  bummer.  Could be because I am still in Jaunty

---

### Post by HunterThomson on 2009-12-20
> **onemyndseye said:**
> I can confirm this working on x64....  sort of.

Great find none-the-less


My issue:

` LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese ` doesnt work at all.   cheese never gets video from the cam and eventually hangs. However running cheese normally now shows that the cam is right-side-up

` LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype ' returns:
```


ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


```

Images are still upside-down in skype...  bummer.  Could be because I am still in Jaunty

Hum, Ya, I would try on the newest version of Ubuntu. It will have new versions of that stuff that is braking. Then report back. I hope it dose work, and work for x86_64.

---

### Post by BlueCanary9999 on 2009-12-21
I'm having problems with sound in Karmic.  I'm running 9.10 64bit on a Lenovo Y530.  I was able to get sound working on all speakers in Jaunty by following the sound guide in the second post, but not all worked in Karmic.  So I followed the same guide, and nothing works, because I'm unable to access ALSAmixer.  See [here]("http://ubuntuforums.org/showthread.php?p=8532940#post8532940") for more info.  But I feel like I'm taking the wrong approach.  What should I do?

Thanks in advance!

---

### Post by michaelzap on 2009-12-21
> **BlueCanary9999 said:**
> I'm having problems with sound in Karmic.  I'm running 9.10 64bit on a Lenovo Y530...
I've got the same rig and I now have surround sound working in 64-bit Karmic. Take a look at [my thread on all my Karmic problems]("http://ubuntuforums.org/showthread.php?t=1309718"), especially post #17. It may also have been important that I'm running the Lucid kernel (which is mentioned earlier in that thread).

One minor issue that I still have is that if I mute the sound using the (PulseAudio) volume control, I have to use alsamixer to turn up the volume on my front speakers and subwoofer again. But that's not difficult to do, so I'm not really complaining. Hopefully this info helps you also.

---

### Post by BlueCanary9999 on 2009-12-21
> **michaelzap said:**
> I've got the same rig and I now have surround sound working in 64-bit Karmic. Take a look at [my thread on all my Karmic problems]("http://ubuntuforums.org/showthread.php?t=1309718"), especially post #17. It may also have been important that I'm running the Lucid kernel (which is mentioned earlier in that thread).

One minor issue that I still have is that if I mute the sound using the (PulseAudio) volume control, I have to use alsamixer to turn up the volume on my front speakers and subwoofer again. But that's not difficult to do, so I'm not really complaining. Hopefully this info helps you also.

I've done that, but I'm unable to get to ALSAmixer.  :/  Thanks for your help tho!

---

### Post by michaelzap on 2009-12-21
> **BlueCanary9999 said:**
> I've done that, but I'm unable to get to ALSAmixer.  :/  Thanks for your help tho!

I thought from your other thread that you could now run alsamixer but you don't have all the options you should have in there.

Do you see your sound card in the volume control applet? You're running the Lucid mainstream kernel? I also installed linux-backports-modules-alsa-karmic as suggested [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html"), and I don't know if that helped.

---

### Post by BlueCanary9999 on 2009-12-22
> **michaelzap said:**
> I thought from your other thread that you could now run alsamixer but you don't have all the options you should have in there.

Do you see your sound card in the volume control applet? You're running the Lucid mainstream kernel? I also installed linux-backports-modules-alsa-karmic as suggested [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html"), and I don't know if that helped.

I had ALSAmixer, and then it disappeared.

Anyhow, I tried linux-backports-etc. and it didn't work.  Then I tried the new kernel, rebooted, and IT WORKS!!!  THANK YOU SO MUCH!
I have some questions about RC kernels tho.  How often should I update them to non-RC kernels, if at all?  Also, should I update them to the next RC when it comes out?  Right now I'm running 2-6-32-RC8, I think.

In other news, I have the same GNOME-Do problem sometimes, but I haven't found a fix.  :/

---

### Post by michaelzap on 2009-12-22
> **BlueCanary9999 said:**
> I had ALSAmixer, and then it disappeared.

Anyhow, I tried linux-backports-etc. and it didn't work.  Then I tried the new kernel, rebooted, and IT WORKS!!!  THANK YOU SO MUCH!
I have some questions about RC kernels tho.  How often should I update them to non-RC kernels, if at all?  Also, should I update them to the next RC when it comes out?  Right now I'm running 2-6-32-RC8, I think.

In other news, I have the same GNOME-Do problem sometimes, but I haven't found a fix.  :/

Cool beans. Glad the new kernel is working for you. I am running the final (non-RC) version of 2.6.32, which is available from the mainline download page I linked to in my post. I think it's fine to just keep running that until the final version of 2.6.33 comes out. You can always try a newer version and see how it goes. They're easy to remove using Synaptic if they don't work well for you, and you can always reboot using the older kernel by choosing it from the Grub menu.

I find that Gnome Do is fine as long as I wait a few seconds after all of my Gnome panels have appeared before trying to use it (the problem seems to be that I'm trying to run it before it's finished starting up).

---

### Post by onemyndseye on 2009-12-23
Using a fresh isntall of Karmic x64.. still no dice :(

```

onemyndseye@onemyndsmobile:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


```

Cam is infact oriented correctly in cheese tho (without preloading)

---

### Post by onemyndseye on 2010-02-01
> **onemyndseye said:**
> Using a fresh isntall of Karmic x64.. still no dice :(

```

onemyndseye@onemyndsmobile:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


```

Cam is infact oriented correctly in cheese tho (without preloading)

Its been a busy month for me so I havnt had much time to look into this but I can now confirm this 100% working on 64bit Karmic.

The issue for 64bit users is that skype is NOT a 64bit app therefore you cannot preload a 64bit lib... 

```

onemyndseye@onemyndsmobile:~$ file /usr/bin/skype
/usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped

```

```

onemyndseye@onemyndsmobile:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Notice the path :)..  is a easy fix. Simply preload the 32bit lib:
```

onemyndseye@onemyndsmobile:~$ locate v4l1compat.so
/usr/lib/libv4l/v4l1compat.so
/usr/lib32/libv4l/v4l1compat.so


```

```

onemyndseye@onemyndsmobile:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

and all works perfectly :)   Thanks for a great find!!!

---

### Post by wysong on 2010-02-05
Just to let everyone know.. I found two fixes.

The first is the sound issue (i.e. 5.1 surround sound) with ubuntu 9.10 I'm not sure if it works in 9.04 yet. Someone will need to try it and let us know.

The second is the upside down web cam.

#1 GETTING 5.1 SOUND TO WORK
###############################################################

Default installation of Ubuntu doesn't recognises all four speaker. There are few fix going on the Internet. There is one problem with those fixes, i.e. headphone doesn't mute the speakers. So you have to manually mute and un-mute the speaker while using the headphone.

However I have found one fix, that recognises all four speaker and one sub-woofer, mutes and un-mutes them while using headphone, and produces 5.1 surround sound.

Open /etc/modprobe.d/alsa-base.conf for editing. (you need root access)
add the following line at the end

```
options snd_hda_intel model=6stack-dell
```

save and reboot.

If your in 9.10 it should work just turn up your speakers and test with this command.

```
speaker-test -Dplug:surround51 -c6 -twav
```

Now if your in 9.04, you might need to go to Audio Preferences and select "6ch" under the options tab. Then test with the above code.



#2 GETTING THE WEBCAM ORIENTATION CORRECTED
#################################################################

This second fix I actually found from a guy named Hans de Goede.
Basically he pushed the fixes for those specific webcam models that were mounted upside down into the libv4l, a video library for Linux that handles various devices. He did that by asking people having problems for two files that could help him make the needed changes into his library.

Hans works for Red Hat, he built the packages for Fedora and the only way you could have installed the library in Ubuntu was to remove every trace of the default libv4l and then recompile and reinstall it from his sources. But apparently somebody took care to build the packages for Ubuntu too. Just add the sources for your release and then take care to install / update the libv4l-0 package.

You can follow these steps in order to do so:

```
echo -e "\n# libv4l PPA\ndeb http://ppa.launchpad.net/libv4l/ppa/ubuntu `lsb_release -c | awk '{print $2}'` main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C3FFB4AA
sudo apt-get update
sudo apt-get install libv4l-0
```

Now, whenever you want to run one of the applications that use your webcam you should launch them using a command like

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so application_name
```

Or better yet… Make a general wrapper for all webcam applications similar to the one above:
```

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $1
exit 0

```
Save the script in ~/bin/webcamWrapper.sh, (You might not have ~/bin, if not just make one or you can just store this file where ever, just make sure you point to it.) make it executable with command
```

sudo chmod +x webcamWrapper.sh

```
And then for each application that needs the library loaded in its menu entry, for the command field, write something like

```

/path/to/webcamWrapper.sh application_name

```

for example if I want to run skype it would be

```

/path/to/webcamWrapper.sh skype

```

And there you go, you now have the sound working great and the video is now right side up!

---

### Post by talktorishav on 2010-02-06
I found the fix for sound here,
[http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html](http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html)

The sound comes from all speakers and mute/unmute on headphone works too.

---

### Post by onemyndseye on 2010-02-08
Here is a revised version of the wrapper script to suit 64bit users.

This version makes an attempt at detecting if the specified command is 32 or 64 bit and preloads the correct lib and passes any parameters.
```

#!/bin/bash


BIN_PATH=$(which $1)
if [ -f "$BIN_PATH" ]; then
  shift 1
  ARCH=$(file "$BIN_PATH"  |awk '{print $3}' |sed '{s/-bit//}')
  if [ "$ARCH" = "32" ]; then
    # 32 bit Binary detected
    echo "Loading webcam fix for 32bit application: $BIN_PATH"
    LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so $BIN_PATH "${@}"
  else
    # 64 bit Binary detected
    # Will always assume 64bit if arch isnt detected.
    echo "Loading webcam fix for 64bit application: $BIN_PATH"
    LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so $BIN_PATH "${@}"
  fi
else
  # File not found
  echo "File: $1 not found!"
  exit 1
fi


```

---

### Post by treesurf on 2010-02-09
Anyone had any luck getting the subwoofer to work on the Y550?  Exhaustive internet searching has brought me no luck yet. :(

---

### Post by onemyndseye on 2010-02-09
> **treesurf said:**
> Anyone had any luck getting the subwoofer to work on the Y550?  Exhaustive internet searching has brought me no luck yet. :(

I dont know anything about that model but I suspect your fix can be found in playing with the hda-intel module options:

example:
```

options snd_hda_intel model=6stack-dell

```

---

### Post by treesurf on 2010-02-09
I've already tried at least a dozen different model options with no luck. :(

By the way, how can I restart ALSA without rebooting?  It sucks to reboot every time I want to try a new setting.

---

### Post by onemyndseye on 2010-02-10
> **treesurf said:**
> I've already tried at least a dozen different model options with no luck. :(

By the way, how can I restart ALSA without rebooting?  It sucks to reboot every time I want to try a new setting.


Sometimes its possible to to unload the module and reload but often you will find that the module is in use and cannot be unloaded, therefore a reboot is needed.

Try: 
```

sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel

```

Other module options to try:
```

model=lenovo-sky
model=6stack-dig
model=lenovo-ms7195-dig

```

What is the output of:
```

lspci |grep Audio

```


Here is a simple script to help you compare your audio device to the available options:
~/alsa-models.sh
```

#!/bin/bash

## Changed this if needed
EDITOR=gedit

mkdir ~/tmp-alsa-info
cd ~/tmp-alsa-info
wget -q http://www.alsa-project.org/alsa-info.sh -O ./alsa-info.sh
chmod +x ./alsa-info.sh
./alsa-info.sh --no-upload --output ./alsa-info.txt
cat  /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz  |gunzip >./HD-Audio-Models.txt
$EDITOR ./alsa-info.txt ./HD-Audio-Models.txt
cd ~
sleep 2
rm -rfd ~/tmp-alsa-info

```

Other useful soundcard info:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
```

cat /proc/asound/card0/pcm0c/info


```

---

### Post by treesurf on 2010-02-10
onemyndseye,  thanks for the advice.  I did learn a bit more based on it.  The sound codec I have is the Realtek ALC272.  I've tried pretty much all of the module options related to this codec with no luck, including the ones you suggested.  I think at this point the only way to get the subwoofer working would be to figure out the pin configuration for the speaker wiring on this laptop.  Unfortunately, that's beyond my capabilities, so I'll just let it go for now and hope that someone figures it out in a future release of ALSA and adds a new module for this laptop model.

---

### Post by onemyndseye on 2010-02-11
does the sub show in alsamixer?

---

### Post by treesurf on 2010-02-11
No, the sub does not show in alsamixer.  A couple of the hda models I tried did show an LFE (low frequency effects) channel in alsamixer, but still there was no sound from the sub even with those channels turned to max.  Additionally those models had other problems, such as headphones not working, so they weren't of much use.  Of the few other models that have all other audio hardware working, there is no channel shown for the sub.

---

### Post by onemyndseye on 2010-02-15
> **treesurf said:**
> No, the sub does not show in alsamixer.  A couple of the hda models I tried did show an LFE (low frequency effects) channel in alsamixer, but still there was no sound from the sub even with those channels turned to max.  Additionally those models had other problems, such as headphones not working, so they weren't of much use.  Of the few other models that have all other audio hardware working, there is no channel shown for the sub.


Hrmmm  shame about the other problems.  Its possible that with some mapping you could get sound from your sub.  But getting alsamixer to show it is the 1st step.


I use these mapings in ~/.asoundrc
```


# Default PulseAudio
pcm.!default {
	type pulse
}


pcm.lenovo_stereo {
       hint {
              show on
               description "Lenovo Stereo Device"
       }

       type plug
       slave.pcm "hw:0"
       slave.channels 2
       route_policy duplicate
}

pcm.lenovo_surround {
       hint {
              show on
              description "Lenovo Surround Device"
       }
        type route
        slave.pcm "surround51"
        slave.channels 6

        # Front
        ttable.0.2 0.75	## Front Left
        ttable.1.3 0.75	## Front Right

        # Color Front channels with rear speakers and sub
        ttable.0.0 0.25 ## Rear Left
        ttable.1.1 0.25 ## Rear Right
        ttable.0.5 1.0	## Touch sub
        ttable.1.5 1.0	## Touch sub


        # Rear
        ttable.2.0 1.0  ## Rear Left
        ttable.3.1 1.0	## Rear Right

        # Color Rear channels with with fronts and sub
        ttable.2.2 0.25	## Front Left
        ttable.3.3 0.25	## Front Right
        ttable.2.5 1.0	## Touch Sub      
        ttable.3.5 1.0	## Touch Sub      

        # Center
        ttable.4.2 0.5	## Center Left
        ttable.4.3 0.5	## Center Right
        ttable.4.5 1.0	## Touch Sub        
              
        # Center Rear
        ttable.5.0 1.0	## Center Rear Left
	ttable.5.1 1.0	## Center Rear Right
	ttable.5.5 1.0	## Touch Sub
}


```

---

### Post by PhilMize on 2010-02-16
Hey thread, it's been some time since I've used my y510. What's new?:o

---

### Post by treesurf on 2010-02-16
> **onemyndseye said:**
> Hrmmm  shame about the other problems.  Its possible that with some mapping you could get sound from your sub.  But getting alsamixer to show it is the 1st step.





Thanks for that.  At this point, mapping is a bit beyond me,though, so I'll just leave it as is and hope for better results from the next ALSA release.

---

### Post by onemyndseye on 2010-03-09
I am happy to report that all seems well with the upcoming release of Lucid.  Nice improvement to boot time (its about 15-20sec from grub to desktop for me).  Performance seems on par.  Pulse/Alsa seems abit more sane so far.


```

onemyndseye@onemyndsmobile:~$ uname -a ; echo "" ; cat /etc/lsb-release
Linux onemyndsmobile 2.6.33-linux-phc+onemyndseye #1 SMP PREEMPT Thu Mar 4 23:14:37 CST 2010 x86_64 GNU/Linux

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"


```

I am using a custom kernel based on 2.6.33 from the mainline ppa..  recompiled for Linux-PHC support and RT Kernel.  In other words a nice responsive realtime kernel with undervolting support:

/usr/local/bin/showvolts.sh
```

#!/bin/bash

for VID in $(cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids); do
  TMP="$(($VID * 16 + 700))mV"
  CURRENT_TRUE_VOLTS="$CURRENT_TRUE_VOLTS $TMP"
done

for VID in $(cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids); do
  TMP="$(($VID * 16 + 700))mV"
  DEFAULT_TRUE_VOLTS="$DEFAULT_TRUE_VOLTS $TMP"
done

THERMAL="$(cat /proc/acpi/thermal_zone/THRM/temperature |awk '{print $2}') C"

echo  ""
echo "Current voltages: $CURRENT_TRUE_VOLTS ("VIDS: $(cat /sys/devices/system/cpu/cpu0/cpufreq/phc_vids)")"
echo ""
echo "Default voltages: $DEFAULT_TRUE_VOLTS ("VIDS: $(cat /sys/devices/system/cpu/cpu0/cpufreq/phc_default_vids)")"
echo ""
echo "Current temperature:  $THERMAL  "
echo ""

```

~$ showvolts.sh
```


Current voltages:  1052mV 828mV 780mV (VIDS: 22 8 5 )

Default voltages:  1388mV 1164mV 1004mV (VIDS: 43 29 19 )

Current temperature:  48 C  


```

There is a bug in Plymouth currently so I would recommend that if anyone wants to take the plunge into Lucid that they purge the Plymouth packages until that issue is resolved.

Other than that..  enjoy being Lucid :)

---

### Post by onemyndseye on 2010-03-17
I forgot to note that the webcam is working perfectly in Lucid without the use of the 3rd party PPA.   However it does still require preloading v4l1compat.so

---

### Post by commonplace on 2010-03-20
I have the Lenovo IdeaPad Y530 and have always used this thread to solve my issues (mostly related to sound). I installed the new Lucid (10.04) beta and everything is great. Got all my speakers and mic working with no problem, etc. Buuuuut my built-in webcam doesn't work at all. I open Cheese and it just sits there and nothing happens; no video at all. Same with Skype.

I'm not sure how to troubleshoot this. Any ideas?

/Kevin

EDIT: NEVER MIND! It works now. I didn't realize you could enable/disable the camera with a hotkey. Not sure how or why it was disabled, but I guess it was. I did Fn+Esc and that seemed to have done the trick. Video works great in Cheese, Skype, etc. now. Sorry for the false alarm! (Although on top of my surprise at finding out about that hotkey, I was more surprised that the hotkey worked in Linux -- I know I always have to boot into Windows to enable my BlueTooth (Fn+F5). Glad it worked/works, though!

---

### Post by JSuresh on 2010-04-30
Has anyone tried the Lucid LTS on the Y510?  I've got the weekend to try a clean install :)

---

### Post by commonplace on 2010-04-30
> **JSuresh said:**
> Has anyone tried the Lucid LTS on the Y510?  I've got the weekend to try a clean install :)

I'm on the Y530, and it works great, aside from my usual lack of suspend/resume (which I have yet to ever work successfully in any distro on this laptop).

Hopefully someone else will chime in with a Y510 and say the same. :)

/Kevin

---

### Post by michaelzap on 2010-04-30
> **JSuresh said:**
> Has anyone tried the Lucid LTS on the Y510?  I've got the weekend to try a clean install :)

I've been running Lucid on a Y530 with Intel video since the first beta release, and it works much better on this machine than Karmic did. Suspend and hibernate still don't work properly, however. Everything else works very well.

---

### Post by winnibob on 2010-05-01
> **JSuresh said:**
> Has anyone tried the Lucid LTS on the Y510?  I've got the weekend to try a clean install :)

I have upgraded to Lucid yesterday on my Y510, and had a few problems with flash video playback in firefox, notification area in the deskbar and boot with grub and plymouth. But it seems that everything was related to the upgrade from Karmic, so there should be no problems with a clean install.

Anyway, everything is working fine now after few fixes, but I wonder if I should make a clean install because I only did upgrades since 8.04 and 10.04 doesn't help a lot with my catastrophic boot time (1,30').

---

### Post by nmfralich on 2010-05-31
I would also like to offer an option for those having sound/headphone/subwoofer problems in Lucid.  Conventional wisdom has told us (if you're a real forum snooper) to fill in the "model=" parameter as model=lenovo nb0763; however, I was browsing an [COLOR="Blue"][ArchLinux forum]("http://bbs.archlinux.org/viewtopic.php?id=95506")[/COLOR] and one user recommended using 

options snd-hda-intel model=auto

for /etc/modprobe.d/alsa-base.conf

I mention this only because using model=lenovo nb0763 was giving me subwoofer support but not headphones and with it disabled giving me the opposite and only giving me internal mic support with it disabled, but by using model=auto I have everything at the same time!!!

Just something to try...

---

### Post by innerwolf on 2010-09-28
There was another suggestion about the 4.1 sound system with a sub-woofer (Dolby Home Theater), here [http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html]("http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html")

Looks like it is working :)

options snd-hda-intel model=6stack-dell

---

### Post by michaelzap on 2010-10-16
> **innerwolf said:**
> There was another suggestion about the 4.1 sound system with a sub-woofer (Dolby Home Theater), here [http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html]("http://techspalace.blogspot.com/2009/01/lenovo-y510-surround-sound-in-ubuntu.html")

Looks like it is working :)

options snd-hda-intel model=6stack-dell

That worked for me in 10.04, but sadly it is not working in 10.10 x64 (I get no sound at all when I add this option).

---

### Post by commonplace on 2010-10-16
> **michaelzap said:**
> That worked for me in 10.04, but sadly it is not working in 10.10 x64 (I get no sound at all when I add this option).

Same here. Anyone have a fix?

/Kevin

---

### Post by wyth on 2010-10-18
Although I really don't want to, I'm about to recompile alsa again. Back the in the 7.* and 8.* days, alsa had to be recompiled in order to get surround sound. That seemed to be taken care of in Intrepid, Jaunty and Lucid, but it looks like we're back to the hack factory.

Question: I did a clean install of Maverick. Has anyone done a regular upgrade and *not* experienced this sound problem?

(I wrote instructions for how to recompile alsa a long time back; if anyone's interested, the link to the forum post is [here]("http://ubuntuforums.org/showpost.php?p=6041731&postcount=146").)

---

### Post by michaelzap on 2010-10-18
> **wyth said:**
> Question: I did a clean install of Maverick. Has anyone done a regular upgrade and *not* experienced this sound problem?

I did a regular upgrade (Lucid x64 -> Maverick x64), and surround sound no longer works for me. First time I've ever done an upgrade, and except for this issue it went really well. I'll be doing a clean install later on, as usual (after debugging the sound problems).

---

### Post by commonplace on 2010-10-18
> **wyth said:**
> Although I really don't want to, I'm about to recompile alsa again.

Definitely report back your findings! If that fixes it, I'll do the same, but I'll let you be the guinea pig. :)  It's the only problem I have with 10.10 but it's pretty bad. Without the surround sound, the volume is so quiet even when it's turned on the way up.

/Kevin

---

### Post by commonplace on 2010-10-18
I was a clean installation, as was wyth, but michaelzap was an upgrade. So no correlation there, it would seem.

What about 32-bit versus 64-bit? I'm x64 and michaelzap is, too -- wyth, are you running 32-bit or 64? Is there anyone that has this WORKING?

/Kevin

---

### Post by wyth on 2010-10-19
Okay, I got alsa working with 5.1 surround, and didn't have to recompile. This may have been the providence of a lucky apt-get update break, but nevertheless, here's what's working on my machine:

**Seven Steps:** ubuntu audio dev team ppa, linux-alsa-driver-modules-2.6.35-22-generic, options snd-hda-intel model=6stack-dell, reboot, alsamixer, sudo alsactl store

**Step One:** Add the [ubuntu audio dev team ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa); they're running the latest alsa drivers, and if you get any help from the officios on Launchpad or elsewhere, they'll ask you to do that anyway.

**Step Two:** Once the ppa is added, install the new linux-alsa-driver-modules-2.6.35-22-generic (or whatever floats your kernel's boat)

**Step Three:** As sudo (root), edit /etc/modprobe.d/alsa-base.conf and make sure the only snd-hda-intel option enabled is ```
options snd-hda-intel model=6stack-dell
``` 

That was the only one that worked for me. In the past, lenovo-sky was brilliant, but now only the dell one works... for a lenovo. 

**Step Four:** Reboot your machine to get the new alsa module kick-started

**Step Five:** Open a terminal and and bring up ```
alsamixer
```
Check the levels -- you'll want to make sure Master, PCM, Front, Surround, Center, LFE, and Side are up.

**Step Six:** Close alsamixer (just hit esc) and store the settings: ```
sudo alsactl store
```

That should do it -- at least it worked in my case. The one difference between now and about eight hours before I wrote this is there was an update to that linux-alsa-driver-modules. 

I'm not positive if that's what did it or what, so if you want to play mad computer scientist and experiment, you could try doing all this *without* adding that ubuntu audio dev team ppa.

---

### Post by michaelzap on 2010-10-20
> **wyth said:**
> That should do it -- at least it worked in my case. The one difference between now and about eight hours before I wrote this is there was an update to that linux-alsa-driver-modules. 

I'm not positive if that's what did it or what, so if you want to play mad computer scientist and experiment, you could try doing all this *without* adding that ubuntu audio dev team ppa.

OK so I'm trying your steps on my Y530 (10.10x64 Gnome). First I tried just adding the 6stack-dell option to alsa-base.conf and rebooting (on the theory that perhaps the kernel update yesterday resolved the issue). No dice. Then I added the ubuntu audio dev team ppa, installed linux-alsa-driver-modules-2.6.35-22-generic, and rebooted. Set and saved settings in alsamixer. Still no dice (no sound at all with the 6stack-dell option).

Right now I'm installing a ton of updates, including a lot of PulseAudio packages from the ubuntu audio dev team ppa. So when that's done, I'll restart again and see if it works. It may be necessary to install all of the dev audio packages.

---

### Post by michaelzap on 2010-10-20
> **michaelzap said:**
> OK so I'm trying your steps on my Y530 (10.10x64 Gnome). First I tried just adding the 6stack-dell option to alsa-base.conf and rebooting (on the theory that perhaps the kernel update yesterday resolved the issue). No dice. Then I added the ubuntu audio dev team ppa, installed linux-alsa-driver-modules-2.6.35-22-generic, and rebooted. Set and saved settings in alsamixer. Still no dice (no sound at all with the 6stack-dell option).

Right now I'm installing a ton of updates, including a lot of PulseAudio packages from the ubuntu audio dev team ppa. So when that's done, I'll restart again and see if it works. It may be necessary to install all of the dev audio packages.

Rats. So no it still doesn't work after the updates and a reboot. No sound at all if the 6stack-dell option is in alsa-base.conf.

Anyone else tried this, and if so did it work for you?

---

### Post by wyth on 2010-10-21
> **michaelzap said:**
> Rats. So no it still doesn't work after the updates and a reboot. No sound at all if the 6stack-dell option is in alsa-base.conf.

Anyone else tried this, and if so did it work for you?

I'm using a Y510, so there may be some hardware differences I can't account for. 

When you bring up alsamixer in a terminal, what options are there?

---

### Post by michaelzap on 2010-10-21
> **wyth said:**
> I'm using a Y510, so there may be some hardware differences I can't account for. 

When you bring up alsamixer in a terminal, what options are there?

The Y510 and Y530 are very similar beasts, so I'm betting on some sort of software issue. When I bring up alsamixer I see all of the channels I ought to and it is identifying my card as it did in Lucid. But I get no sound...

---

### Post by onemyndseye on 2010-10-23
very strange...  Ive had no difference in sound behavior since Lucid.   I was an upgrade to Maverick.

---

### Post by michaelzap on 2010-10-23
> **onemyndseye said:**
> very strange...  Ive had no difference in sound behavior since Lucid.   I was an upgrade to Maverick.

What model hardware are you running? What system (Gnome? 64-bit?)? If it works for you, that gives me hope that I can make it work for me, too.

---

### Post by commonplace on 2010-10-24
> **michaelzap said:**
> Rats. So no it still doesn't work after the updates and a reboot. No sound at all if the 6stack-dell option is in alsa-base.conf.

Anyone else tried this, and if so did it work for you?

I tried it and had the exact same results as you: no sound at all. Still hoping someone comes up with a fix or workaround!

/Kevin

---

### Post by onemyndseye on 2010-10-25
Y510 64bit ...  using the lenovo-sky option.   Also I am KDE but as of 10.10 KDE moved to Pulseaudio as well so shouldnt be a huge difference there.

Michael,
 Your getting no sound at all or surround channels are not being mapped proper?

---

### Post by michaelzap on 2010-10-25
> **onemyndseye said:**
> Y510 64bit ...  using the lenovo-sky option.   Also I am KDE but as of 10.10 KDE moved to Pulseaudio as well so shouldnt be a huge difference there.

Michael,
 Your getting no sound at all or surround channels are not being mapped proper?

So that's two people with Y510s and working surround sound, so maybe it is more of a Y530 problem.

I can get (low-volume) stereo sound only if I include no custom option in my alsa config file. If I add lenovo-sky or 6stack-dell and reboot, alsamixer sees all the proper channels and I can choose 4.0, 5.0, or 5.1 sound in Sound Preferences, but no matter what I choose (including analog stereo), I hear nothing. I also tried installing the latest Realtek drivers from their site (they were updated this month), but that made no difference.

What do you Y510 folks see when you run this command?
```
cat /proc/asound/card0/codec#* | grep Codec
```

I get:
```
Codec: Realtek ALC888
Codec: Intel Cantiga HDMI

```

---

### Post by commonplace on 2010-10-28
> **michaelzap said:**
> So that's two people with Y510s and working surround sound, so maybe it is more of a Y530 problem.

I can get (low-volume) stereo sound only if I include no custom option in my alsa config file. If I add lenovo-sky or 6stack-dell and reboot, alsamixer sees all the proper channels and I can choose 4.0, 5.0, or 5.1 sound in Sound Preferences, but no matter what I choose (including analog stereo), I hear nothing.

Just wanted to chime in and parrot what you said. Y530 here, and my results are exactly like you said. Low-volume stereo sound if I have no options on the config file; anything else results in no sound whatsoever.

Considering trying Linux Mint 10, which I did once a long time ago when I had a different sound issue. Even though it was based off of the same problematic version of Ubuntu at the time, switching to Mint fixed the issue. I'm wondering if it might not work again. I just don't feel like re-doing my system... so I'm still holding out hope for a fix. :)

Maybe it really is a Y510 vs. Y530 thing right now, though, which would make me lose some hope.

/Kevin

---

### Post by gauravmohile on 2010-10-30
Switched back to 2.6.32 kernel and audio works fine again.

---

### Post by michaelzap on 2010-10-30
> **gauravmohile said:**
> Switched back to 2.6.32 kernel and audio works fine again.

I don't have time to try this right now (busy churning out several projects and can't be futzing with my system), but people might try installing the latest mainline kernel instead of the default one:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

This resolved audio issues for me on this machine back when I was using Karmic, since some mod that was in the default kernel was causing the problem then.

---

### Post by commonplace on 2010-11-20
> **michaelzap said:**
> I don't have time to try this right now (busy churning out several projects and can't be futzing with my system), but people might try installing the latest mainline kernel instead of the default one:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

This resolved audio issues for me on this machine back when I was using Karmic, since some mod that was in the default kernel was causing the problem then.

I installed the latest one, which as of this writing is 2.6.37-rc2. No difference. No sound options in alsa-conf equals very low volume from two speakers; changing it to either lenovo-sky or 6stack-dell means seeing the 5.1 configuration but having no sound at all.

Highly frustrating. I really don't want to switch distros -- and I mean I really, REALLY don't want to -- but this sound issue is recurring and very frustrating.

Anyone else found any solutions?

/Kevin

---

### Post by commonplace on 2010-11-29
No one has gotten this to work? Gah, it's driving me crazy. Does anyone know if Linux Mint 10 has the same issue? Presumably it's kernel-related, but when I had this same issue with a previous version of Ubuntu, Mint wasn't affected. Any ideas? (If not, I guess I'll give it a try and report back.)

/Kevin

---

### Post by michaelzap on 2010-11-29
> **commonplace said:**
> Does anyone know if Linux Mint 10 has the same issue? Presumably it's kernel-related, but when I had this same issue with a previous version of Ubuntu, Mint wasn't affected. Any ideas? (If not, I guess I'll give it a try and report back.)

Don't bother. Mint 10 has the same issue. I'm running that on my Y530 now and it behaves exactly the same.

---

### Post by commonplace on 2010-11-29
> **michaelzap said:**
> Don't bother. Mint 10 has the same issue. I'm running that on my Y530 now and it behaves exactly the same.

Dang. :(  Well, thanks for saving me from wasting a lot of time! I just can't believe this is so difficult. I guess the issue is that it doesn't really affect that many people (in the grand scheme of things), so no one really cares.

/Kevin

---

### Post by michaelzap on 2010-11-29
> **commonplace said:**
> Dang. :(  Well, thanks for saving me from wasting a lot of time! I just can't believe this is so difficult. I guess the issue is that it doesn't really affect that many people (in the grand scheme of things), so no one really cares.

It is kind of frustrating. I've always had trouble with Linux on this laptop (first the Intel video, then the surround audio, and I still can't put it to sleep or hibernate it). It doesn't seem to be particularly unique or outdated hardware, so I really don't understand why the new kernels can't deal with it.

---

### Post by commonplace on 2010-11-29
Alright, just ended up installing the 2.6.33.7 kernel, which is apparently the most current kernel that doesn't break our sound.

The kernel is here: [http://bit.ly/gM1WaC](http://bit.ly/gM1WaC)

In my case, for 64-bit Ubuntu, I downloaded both of the files whose names end with "amd64.deb" along with the headers file that ends with "all.deb" (not the source one) into a single folder. Then, from the terminal, I did a dpkg -iG *.deb from within that folder to install all three .deb files. Rebooted and selected the kernel from the list, and now I have full sound again.

Pretty sad that I had to do this, but I guess now I'll just hope that a future kernel re-fixes the issue.

/Kevin

---

### Post by michaelzap on 2010-11-29
> **commonplace said:**
> Pretty sad that I had to do this, but I guess now I'll just hope that a future kernel re-fixes the issue.

Good to know where to find that, but I don't need surround sound so much that I'd downgrade the kernel to get it. That's a mainline kernel, so it might actually be a mod to the later kernels (not the kernel itself) that caused the issue. That would be a hopeful sign (I think), and might mean that Debian with the current kernel doesn't have this issue.

---

### Post by Benalene on 2010-12-17
I am having the same problem in Arch Linux, just fyi. I have tried lenovo-sky, 6stack, 6stack-dell, and with all three, I get all surround sound options in alsamixer, but no sound. If I don't specify any model, I get really crappy sound.

---

### Post by mylh on 2010-12-17
Be sure to check in alsamixer that your sound shanels are unmuted.

---

### Post by commonplace on 2010-12-17
> **Benalene said:**
> I am having the same problem in Arch Linux, just fyi. I have tried lenovo-sky, 6stack, 6stack-dell, and with all three, I get all surround sound options in alsamixer, but no sound. If I don't specify any model, I get really crappy sound.

Well, that's bad news. Good to know, though, so thanks for letting us all know. That would tend to point toward the kernel itself, I'd think -- unrelated to Ubuntu's customized kernels. UGH.

/Kevin

---

### Post by commonplace on 2011-01-25
Well, it's been over a month, so I thought I'd bump this and see if anyone has found any resolution or workaround. Anyone? Anyone? :)  I seriously love this laptop but the lack of Linux support for it definitely stinks!

/Kevin

---

### Post by michaelzap on 2011-01-27
I've been very busy over the last month, so the only thing I've done to test this further is to install LMDE on my Y530 and see if the speakers work properly in it. They don't. If they don't work in Debian or Arch, I'd bet that any distro with a recent kernel will have this regression.

---

### Post by ktullanux on 2011-02-06
Hello guys! My keyboard is broken, and i want to transfer the Fn key on another key!
Please, run xev in a terminal emulator, and press Fn, and copy the output here.  Thank you ;)

---

### Post by commonplace on 2011-02-07
> **ktullanux said:**
> Hello guys! My keyboard is broken, and i want to transfer the Fn key on another key!
Please, run xev in a terminal emulator, and press Fn, and copy the output here.  Thank you ;)

If no one has done this by the time I get home from work tonight, I'll be happy to do this for you! I'll check back from home (where my laptop is) and if no one else has done this already, I'll let you know the output.

/Kevin

---

### Post by commonplace on 2011-02-07
> **ktullanux said:**
> Hello guys! My keyboard is broken, and i want to transfer the Fn key on another key!
Please, run xev in a terminal emulator, and press Fn, and copy the output here.  Thank you ;)

Okay, I did that and it didn't return anything at all. I tried a bunch of other keys and the Fn key was the only one that literally did nothing at all. Sorry. Let me know if you want me to try anything else!

/Kevin

---

### Post by kyleaudio on 2011-02-12
ok, i think i need some help, i am new to linux, i just installed ubuntu 10.10 for the first time yesterday, had some issues with the dual boot, but i got that figured out with some help. so now i'm trying to get the sound working, i had sound, but it wasnt very good sound, only two speakers and no subwoofer, the microphones are not recognized either. the speakers did turn off when headphones are plugged tho.

i found this thread and decided to follow the instructions in post 2. first thing, when i entered

  sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`



i got "sudo: aptitude: command not found" but i continued (not sure if it was good idea to continue, but i did anyways), i downloaded the most recent alsa driver lib and utils files (1.0.24) and put them on the desktop as suggested. everything seemed to go well until i installed the utils file, and type "sudo ./configure" it runs through some text and at the end the last line says "configure: error: required curses helper header not found" and sudo make and sudo make install dont work.

now i have no sound and i dont know what to do... can you guys help me out?

thanks, kyle.

---

### Post by commonplace on 2011-03-31
Any Y530 users tried the 11.04 (Natty) beta yet? Does it fix our sound issues? I'm doubtful, but I'll be trying soon. Whether it helps or not, I'll still be upgrading, but I'm curious if anyone else has tried and what their experience has been. I SO miss having surround sound -- and loud sound, period -- working.

/Kevin

---

### Post by mylh on 2011-04-01
I'm surprised that there are users still having problems with sound on Y530. I have Y530 and there are no any sound problems at all. You just need to tweak config file of alsa and all sound devices including subwoofer work perfectly. Two years ago you also had to recompile alsa-driver and utils, but with new versions of thesese tools in ppa you don't have to. Unfortunately my notebook is to with me right now, so I can't tell what is the config param exaxtly but I found it in this thread so try to read from the beginning.

One more thing. My Y530 is broken - display hinge breaked down in metal crumbs though it just 2 years old. But all electronic parts still work. So be careful with it.

p.s. I've bought Dell Vostro V130 and kubuntu runs smoothly on it.

---

### Post by commonplace on 2011-04-01
> **mylh said:**
> I'm surprised that there are users still having problems with sound on Y530. I have Y530 and there are no any sound problems at all. You just need to tweak config file of alsa and all sound devices including subwoofer work perfectly. Two years ago you also had to recompile alsa-driver and utils, but with new versions of thesese tools in ppa you don't have to. Unfortunately my notebook is to with me right now, so I can't tell what is the config param exaxtly but I found it in this thread so try to read from the beginning.

I've read this thread top to bottom and have been subscribed to it since I got this laptop well over a year ago. I had the sound fixed at one point but newer kernels broke it. I am not the only one having issues still.

If you have a fix, please share! I'm not the only one who would benefit from this and be extremely grateful.

Where I (and others) stand is this: with any recent kernel in Ubuntu 10.10, we only get two-channel audio and it is very quiet even with all volume controls maxed out. If we put any of the parameters into the alsa file (lenovo-sky, etc.), we lose ALL audio completely.

/Kevin

---

### Post by mylh on 2011-04-01
Ok, please wait a couple of hours till I get back home. I'll post my config. I really don't have any issues with sound even when install new kernels. All 5 channels of sound system work and the sound is so loud that I can listen to music from another room.

---

### Post by commonplace on 2011-04-01
> **mylh said:**
> Ok, please wait a couple of hours till I get back home. I'll post my config. I really don't have any issues with sound even when install new kernels. All 5 channels of sound system work and the sound is so loud that I can listen to music from another room.

Awesome!! (And this had better not be an April Fool's joke! :D)

/Kevin

---

### Post by mylh on 2011-04-01
so, i've just checked my config file and there is just this option

options snd-hda-intel model=lenovo-sky

I also checked that las time i complied the driver one year ago. Since then everything works fine even when kernel is upgraded

---

### Post by commonplace on 2011-04-01
> **mylh said:**
> so, i've just checked my config file and there is just this option

options snd-hda-intel model=lenovo-sky

I also checked that las time i complied the driver one year ago. Since then everything works fine even when kernel is upgraded

Appreciate it! If I set that lenovo-sky option, I get no sound at all. But I have NOT compiled the ALSA driver at all -- it was believed that that was no longer necessary in this version of Ubuntu (at least, according to this thread).

When I re-do my laptop with the new Ubuntu 11.04, which I will probably do soon (with the beta), I'll go ahead and compile ALSA from scratch and see what happens.

/Kevin

---

### Post by mylh on 2011-04-02
Also remembered, check that all channels are unmuted, run alsamixer in console.

---

### Post by CitricAcid on 2011-05-02
Hello everyone.
I use Ubuntu 11.04
As always after Ubuntu reinstallation I have compiled ALSA. That made my sound dead. So I have uninstalled compiled version and reinstalled kernel. Sound came back to me ;)

The only thing I did is that I set the lenovo-sky for model option.
The other thing is to choose proper amount of channels in sound settings dialog window. That's it. No compilation necessary.

I have only one issue. My subwoofer does not produce any sound. So let's say I have 4.0 sound system instead 4.1 (which I have chosen in the config window).

Regards,
CitricAcid

EDIT:
I set sound system to 5.1 and all speakers are talking to me :D

---

### Post by commonplace on 2011-05-02
Did a clean install of 11.04 on my Y530, and the sound works perfectly out of the box for me!

Unfortunately, I experience frequent lockups when running in the default Unity mode, so I've resorted to falling back to classic. I would assume that is video-related, but I really don't know. Hopefully after some updates it'll be resolved, but I won't hold my breath. At least I'm able to run in "classic" mode (regular old Gnome) with full sound and no issues that I've noticed. :)

/Kevin

---

### Post by wyth on 2011-05-04
Just wanted to report that with 11.04 on the Y510, adding this at the end of /etc/modprobe.d/alsa-base.conf works for sound:

```
options snd-hda-intel model=lenovo-sky
```

One idiot move I've made since maybe Hardy is writing *module* instead of *model*, and it takes me ten minutes to figure out what I did. So maybe double-check the syntax if it's not working.

---

### Post by CitricAcid on 2011-05-05
Well...
I have been so happy lately about my sound working...
Now I have a problem with headphones. I hear the sound in them. But when I play some game with 3d sound (Shadowgrounds) I cannot hear some of the sounds: many speeches, sounds behind me etc.

Does anybody know how to make my headphones to work as stereo device?
3D for my speakers in Y530 is ok. But not for headphones.

Regards

---

### Post by BlueCanary9999 on 2011-05-24
Just recently installed Natty on the Y530.  Everything is smooth, but sound wasn't working perfectly for me.  As far as I could tell, only the back speakers, at the bottom of the screen, were working.  From my previous experiences, this is usual for a fresh install of Ubuntu on the Y530.

So, as usual, I followed the guide on the first page of this thread to get all the speakers working.  But I came across the same problem I had previously: when I go to adjust things in alsamixer, it won't load.  The console spits out
```
cannot open mixer: No such file or directory
```
I know it's installed tho.  Entering "which alsamixer" into the terminal returns "/usr/bin/alsamixer".  Calling alsamixer with the full path doesn't change anything tho.

alsamixergui returns another error message:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
And gnome-alsamixer also doen't work.  It's just a blank window.

I had this problem with a previous upgrade, and posted the question in this thread and in [another thread](http://ubuntuforums.org/showthread.php?p=8532940).  But the solution I used then--installing some Karmic backport modules--doesn't seem to be applicable for Natty.  (Or is it? I'm quite a noob...)

So I'm not sure what to do.  Googling this problem hasn't given me any leads.  And at the moment, I have no sound, because all the speakers are muted until I can access alsamixer.  Help would be much appreciated.  Thanks in advance!

[EDIT]
Alright, it's fixed, somehow. I just reinstalled Natty and now it works. And as far as I can tell (my ears aren't very sensitive), all the speakers work. :O

---

### Post by BlueCanary9999 on 2011-05-30
Hey Citric Acid, how did you get your sound to work?  Same for other Y530ers.

[EDIT]
Alright, it's fixed, somehow.  I just reinstalled Natty and now it works.  And as far as I can tell (my ears aren't very sensitive), all the speakers work.  :O

---

### Post by BlackGrizzly on 2013-04-29
Hello! Who use Ubuntu 13.04 &#1086;&#1085; Lenovo Y510?

---

### Post by wyth on 2013-04-30
I'm using 13.04 on my Y510. For the most part it's working, except I'm having a problem with the launcher autohiding -- it leaves a blank space on the left side of the screen, and that blank space also blanks out any open windows (see this pic [https://launchpadlibrarian.net/138667774/unity.launcher.problem.png](https://launchpadlibrarian.net/138667774/unity.launcher.problem.png)).

I think I'd also recommend a clean install. I had been doing in-place upgrades, and my system was becoming unusable (the touchpad had completely conked out in 12.04). I upgraded via the software manager, still had issues, and then did an upgrade off the live disk where I re-installed the system but kept my home (it's an option), and that cleared up a lot of problems (including the touchpad).

For what it's worth, there's a bug report on the autohide issue, and it looks like it might be a Lenovo thing. [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1078075](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1078075)

---

### Post by BlackGrizzly on 2013-04-30
Sound works fine? I can't set it up...
"options snd-hda-intel model=lenovo-sky" is set
if I use 4.1 work only the front speakers and a subwoofer

---

### Post by wyth on 2013-05-01
Y'know, I didn't even think of the sound, which is strange because I wrote the guide on how to get sound working on these machines.

Sound wasn't a problem when I was having the other problems, but since I reinstalled the system files, any previous flags in alsa-base.conf have been removed, yet my sound seems to be working fine. All options are there -- 4.0, 4.1, 5.0, 4.1, analog stereo. They all work, but the front left/front right on 4.1 and 5.1 are pretty quiet. It's not something I've really noticed or been concerned about before (usually on headphones).

Reinstalling the system makes me a bit nervous because a few iterations ago, I tried that and was locked out of my encrypted home partition; despite using the same username and password, I lost it, and that was a problem. But this time around it wasn't an issue, and the system is running much cleaner and more functionally than before. So if you're willing to risk it, maybe try the system reinstall off a live disk. If not, back up what you need in /home, then just try a clean install. (If you boot off the live disk, test it out first and see if the sound works fine there; if it does, it should work fine when cleanly installed.)

---

