---
title: "howto run a script when a USB device is pluged in"
date: 2007-07-17
forum: Tutorials
---

### Post by Carlos Santiago on 2007-07-17
This explains how you could run a script made by you (say /usr/local/my_script) when you plug a specific USB device.

1. First run lsusb to identify your device. Example:
$lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID **040a:0576** Kodak Co.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

2. After doing this you know that 
 - the vendor ID of your device is **040a**
 - the product ID of your device is **0576** 

3. Now is time to create your UDEV rule:
```
sudo nano /etc/udev/rules.d/85-my_rule.rules

```
4. And add the text
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", RUN+="/usr/local/my_script"

```
Explanation:
When the **usb_device** product identified as **0576** of vendor **040a** is **add**ed, run **/usr/local/my_script**
Note that '==' and "!=" are comparators, while = and += are assingments

---

### Post by frodon on 2007-07-17
Excelent guide thanks for sharing, will test and spread this, many of my friends were looking for such a thing, it is really usefull to automount you external drives with the good rights and especially if it's a NTFS drives and that you want to mount it with write support.

---

### Post by reclusivemonkey on 2007-07-17
No offence to your excellent guide, but there is a much easier way. Simply make an executable script called autorun in the root drive of your USB flash drive. Then in the "Removable Drives and Media" preferences, make sure you tick the entry to automatically run scripts on plugging them in (sorry I am at work and can't see the exact wording, but it should be obvious which one it is). You're done! I've always wanted to do this, but frankly couldn't be bothered with poking around with udev; this is Ubuntu after all ;-)

---

### Post by Carlos Santiago on 2007-07-17
Reclusivemonkey, seems to me that you didn't notice one small, however very important, thing!
This procedure is generic and works with ANY usb device. For example I use it to configure and start my internet connection when I plug in my UMTS modem.

---

### Post by reclusivemonkey on 2007-07-17
> **Carlos Santiago said:**
> Reclusivemonkey, seems to me that you didn't notice one small, however very important, thing!
This procedure is generic and works with ANY usb device. For example I use it to configure and start my internet connection when I plug in my UMTS modem.

That's very true, please accept my apologies.

But don't you think people will be interested in the USB flash way as well? I am sure plenty of people would like a quick and easy way of running scripts when they plug in their USB drives; especially for syncing.

---

### Post by Carlos Santiago on 2007-07-17
Due to the interest of this subject, I would like to emphasize that udev rules has other very useful features, for example:

**1.** if you had **GROUP="dialout"**, the device will belong to that group. This means that all users in the *dialout* group have special permissions to work with the device.
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", GROUP="dialout"

```

**2.** if you had **SYMLINK+="ladys_camera"**, a *ladys_camera* device will be added to your */dev*.
This could be very usefull if you use several usb devices (as most of us do), because their device (/dev/ttyUSB[0-9]) is set depending on plug order. 
This way */dev/ladys_camera* will always be your lady's camera.
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", SYMLINK+="ladys_camera"

```

**3.** Also notice that udev rules work with all king of devices: usb, serial, pcmcia, ...
 udev rules is a simple and easy way to configure all devices (it can configure, load modules, run scripts, set permissions for all your hardware).

[U]
Final notes:
[/U]
**A.** Each line is a device. If you want to break a line add \ at the end
```
ACTION=="add", SUBSYSTEM=="usb_device", \
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", \
SYMLINK+="ladys_camera"

```

**B.** You can add simultaneous actions in the same line (like group assignment and symbolic link)
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", GROUP="dialout", SYMLINK+="my_modem"
```


**C.** The rules file must be in /etc/udev/rules.d/. Restart udev service (sudo /etc/init.d/udev restart) after changes.

**D.** The rules filename must start with two digits, plus a dash (-), and must end with .rules
 The two digits have a reason. See /etc/udev/rules.d/README

---

### Post by Carlos Santiago on 2007-07-17
There are several ways to skin a cat ... this is just one of them
.... apologies accepted ;-)

---

### Post by Zylar on 2007-12-11
Sorry bout rezzing an older thread, but I'm running into issues.

Ubuntu 7.10 Server

1.   I've created the udev rule in the proper directory (/etc/udev/rules.d/85-my_test.rules), and changed the idVendor, idProduct, and RUN info to reflect my device and script.  When I plug in the device, the script never fires.  Any ideas?  If I run the script manually, it works great.  Also, is the script run as root by udev?

2.  I would actually prefer reclusivemonkeys solution, but 7.10 Server doesn't seem to automount usb devices nor have the 'Removable Drives and Media GUI' for enabling autorun on external drives.  Are there CLI methods of enabling these features?

Thanks for any help,

Edit:

Ok, udev solution fixed now.  Had to change SUBSYSTEM=="usb_device" to SUBSYSTEMS=="usb" and SYSFS to ATTRS.  

On the other solution, both automount & autorun are being handled by 'gnome-volume-manager' I think.  Since this is Server, gnome isn't installed.  I'm going to see if I can find a 'volume-manager'.  Or maybe I could still install the g-v-m on Server...

---

### Post by ktheking on 2007-12-21
Carlos , thank you very much for your post.

This will most certainly help me for building headless systems ,which need an automated backup system ,amongst many other usb plugin items.

I didn't try it yet ,but I'm a big fan of non-"gui restricted" solutions.

They tend to work on any version,and can easely be troubleshooted and customized.

Many thanks again ,

K.
Belgium ...

---

### Post by Carlos Santiago on 2007-12-21
You welcome K.
Note that the comparators must all be TRUE to execute the script.
As Zylar notice the SUBSYSTEM may need to be changed to "usb". You could just remove the SUBSYSTEM comparator. If idVendor and idProduct match, you dont need to verify if it is a USB device.

Also, if SYSFS does not work, try changing to ATTRS. 

Like:
```
ACTION=="add", ATTRS{idVendor}=="040a", ATTRS{idProduct}=="0576", RUN+="/usr/local/my_script"
```

Regards,

CS

---

### Post by ktheking on 2007-12-21
OS : Gusty 7.10 alternate - cli install (command line only)

Just tried it and confirms it works .

But a small (can be solved inside launched script) problem exists :

The script is started several time when device is plugged in ...

This is the line I use :
ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="14cd", ATTRS{idProduct}=="6600", RUN+="/home/tux/usb_script_14cdx_6600.ksh"

I could solve this by working with a tempfile ,and doiing time comparison.
But this is not a clean solution.
Better would be if the script was launched only once ...

Any idea ?

Greetz ,

K.

---

### Post by Carlos Santiago on 2007-12-21
As a first attempt I would try:
ACTION=="add", SUBSYSTEMS=="usb", ATTRS{idVendor}=="14cd", ATTRS{idProduct}=="6600", RUN="/home/tux/usb_script_14cdx_6600.ksh"

---

### Post by ktheking on 2007-12-23
Nope ... that doesn't do the trick.

I'll go for the quick and dirty ...

I've added this to the launched script ,preventing it to start multiple times within a period of 60 seconds ...

Maybe a bit of overkill ,but I might use it for more sensible stuff then mounting a disk.

#!/usr/bin/ksh
sleep 1
cat /tmp/epochtimetesfile.txt | head -1 | while read TIMEBEFORE
 do
  #echo "TIME BEFORE IS=$TIMEBEFORE"
  CURRDATE=`(date +'%Y-%m-%d %H:%M:%S UTC')`
  EPOCHTIME=`(date --date="$CURRDATE" +%s)`
  DIFFTIME=`(echo "$EPOCHTIME-$TIMEBEFORE" | bc)`
  #echo "Difftime=$DIFFTIME"
  if [ "$DIFFTIME" -lt "60" ]
   then
    #echo "START AGAIN , DIFF IS TOO SMALL"
    exit
  fi
 done
#echo "TIME BEFORE IS=$TIMEBEFORE"
#Current full epoch date/time =
CURRDATE=`(date +'%Y-%m-%d %H:%M:%S UTC')`
#echo "$CURRDATE"
EPOCHTIME=`(date --date="$CURRDATE" +%s)`
#echo "New epoch time is entered"
echo "$EPOCHTIME" > /tmp/epochtimetesfile.txt
#date --date='1970-01-01 00:01:10 UTC' +%s
#echo "MOUNTING DRIVE"
wall /home/tux/test.txt


Thanks for the usefull guide on udev stuff ...

Kind regards,

K.

---

### Post by Superwallah on 2007-12-24
Hello everybody,

I would like to RUN an init process from /etc/init.d everytime the USB disk is plugged in.
I found out that you can't hand over parameters like the "start" or "stop" for the /etc/init.d script.
Hence, the only way is to set up a one line shell script.



Best regards,

Superwallah

---

### Post by Gina on 2008-01-16
Having 3 USB memory sticks and never knowing which is which, I think this thread should be very useful.  I'll have a play around and see how I get on.  Thanks everyone :):)

---

### Post by arron on 2008-01-21
I got this running my script (i know it does, echo test >> /home/arron/testfile.txt lets me know).

I want the script to run a gui program for the logged in user, but it doesn't run.  I assumed it was a x screen permission thing, since it runs the script as root, so i tried

```
su arron -c /bin/mygui
```

but still no luck.  do i need something else special for it to run?  I even tested with gedit with no luck.

---

### Post by Reech.out on 2008-10-17
Hi,

This seemed like an appropriate place to post this question...

I recently bought a netbook with 2 SD cardreaders.
And I can't get them to work completely automatically.
 
I Need to run 2 commands/scripts before they get detected automatically.
# Jmb38x_d3e.sh (which apparently loads the kernel modules for my card reader)
# setpci -d 197b:2381 AE=47 (which, I assume makes, sure the SD cards are recognized so they will automount)

I've put these commands in a little shell script and added it to runlevels 2 trough 5.

However the setpci command fails during startup and also if I try it manually right after booting.
It returns the error: "Warning: No devices selected for `AE=47`"

After inserting an SD card I can run the setpci command without error, and any SD card inserted afterwards automounts.

I think I need a way to fake an SD card that is inserted during boot, so I can add it to my shell script between de jmb38... and the setpci...
How would I go about this?

---

### Post by flameup on 2008-10-17
> I recently bought a netbook with 2 SD cardreaders.
And I can't get them to work completely automatically.
As far as I know all should come with software to autorun... 
What about yours? 
At least there are must be drivers

---

### Post by Reech.out on 2008-10-17
I followed [this]("https://help.ubuntu.com/community/AspireOne") howto.

here's the specific part:```
CARD READER:

    *

      (NOTE: This section needs to be improved. It seems that card reader is not truly "Fully functional") 

According to DebianAcerOne the following command enables the card reader:

setpci -d 197b:2381 AE=47

The card reader works fine now.

    * it might help to suspend/resume
    * a static entry for the device /dev/mmcblk01p in /etc/fstab might help
    * powersaving can be done with the jmb38x_d3e.sh script - 

wget http://petaramesh.org/public/arc/projects/AcerOne_Ubuntu/jmb38x_d3e.sh
sudo chmod 754 jmb38x_d3e.sh
sudo mv jmb38x_d3e.sh /usr/local/sbin/

To recognize cards every time.

sudo gedit /usr/local/sbin/jmb38x_d3e.sh

Add the following to line 11

modprobe pciehp pciehp_force=1

After reboot cards are recognized. 
```

But SD cards would only be recognized when one was inserted @ boot time.

After a lot of asking around I've  gotten at the situation described  above...
Any help is welcome...
I tough it would be a solvable by echoing something to a device or process but so far, no luck.

---

### Post by Green_Star on 2008-10-27
> **arron said:**
> I got this running my script (i know it does, echo test >> /home/arron/testfile.txt lets me know).

I want the script to run a gui program for the logged in user, but it doesn't run.  I assumed it was a x screen permission thing, since it runs the script as root, so i tried

```
su arron -c /bin/mygui
```

but still no luck.  do i need something else special for it to run?  I even tested with gedit with no luck.


If some one can solve this problem, that would be great for me.

I have usb sony walkman NW-E00x, to use this usb mp3 player, sony provided a software to load songs into device(we can not just copy and paste the songs), unfortunately that software works only in windows. Luckly some one developed a application in java so that I use that software copied into my usb and use in in my Ubuntu machine. 
[http://sourceforge.net/project/showfiles.php?group_id=174319](http://sourceforge.net/project/showfiles.php?group_id=174319)

So I want that software automatically loaded/open when I plug in the usb. Because it is gui application, I am not succeeded. Same problem like DISPLAY was not configured.

I tried changing my shell to root account and tried to run that application manually with my user name. 

> sudo -u myusername /media/WALKMAN/walkman.sh

I get those DISPLAY variable errors. Anyone has any workaround?

---

### Post by techflat on 2009-02-22
Green_Star

I know it's an old post, but, were you able to solve this problem?

If not, I'm thinking you cannot run your script since it's not run inside the window manager. I'm guessing there's a way to run it so it's executed in gnome (if that's what your running).

Cheers

---

### Post by everthonvaladao on 2009-03-19
> **techflat said:**
> Green_Star

I know it's an old post, but, were you able to solve this problem?

If not, I'm thinking you cannot run your script since it's not run inside the window manager. I'm guessing there's a way to run it so it's executed in gnome (if that's what your running).

Cheers

I found the answer by adapting [[COLOR="Blue"]the script from this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=994233&highlight=udev+rule+gui"), ending with something like this:

```

#!/bin/bash
set -x 
xhost local:MYUSERNAME
export DISPLAY=:0.0

su MYUSERNAME -c '/usr/local/bin/my_script args1 arg2 etc'

## (Optional) Put a notification-icon into the system tray
#/usr/bin/zenity --notification --window-icon=/usr/share/pixmaps/gnome-irc.png --text="the USB stuff was connected!"

```

It succesfully run some GUI app! :-)

---

### Post by Roanoke on 2009-03-21
This doesn't work at all for me.
```

ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="040d", SYSFS{idProduct}=="6204", RUN+="/usr/share/scripts/backup.sh"

```

---

### Post by kevdog on 2009-03-22
roanake, please review the name conventions requred for your script.

---

### Post by Roanoke on 2009-03-22
The numbers and the dash are only required for the rules file. This line is inside the rules file, which is named 85-myrule.rules.

---

### Post by unutbu on 2009-03-22
It would be nice to know if (A) the script is being run, but quitting early, or (B) the script in never getting run at all.

If we are in case (A), then we can stop fiddling with the udev rule and concentrate on the script.

If (B), then we need to work on the udev rule.

To find out if we are in case (A) or (B), perhaps try this: Edit your script by adding this line:
```

env > /tmp/env.out

```

Unplug and then plug in the drive. See if you get a file called /tmp/env.out.

If you see /tmp/env.out, then we are in case (A). In this case, please post your script.

If you do not see /tmp/env.out, then we are in case (B). In this case, please post the output of lsusb.

---

### Post by Roanoke on 2009-03-22
The file didn't appear in /tmp, so here's lsusb's output.
```

**Bus 005 Device 016: ID 040d:6204 VIA Technologies, Inc. **
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by unutbu on 2009-03-22
Try removing SUBSYSTEM=="usb_device":
```

ACTION=="add", SYSFS{idVendor}=="040d", SYSFS{idProduct}=="6204", RUN+="/usr/share/scripts/backup.sh"

```
Also make sure that /usr/share/scripts/backup.sh is executable:
```

sudo chmod 755 /usr/share/scripts/backup.sh 
```

Unplug and plug in the device once more. Check for /tmp/env.out.
If you don't see /tmp/env.out, run
```

for dev in $(ls /sys/bus/usb/devices); do udevinfo -ap /sys/bus/usb/devices/$dev; done > udevinfo.txt

awk 'BEGIN { RS=""; FS="n"; PATTERN="040d" } { if ( $0 ~ PATTERN ) print $0; }' udevinfo.txt > 040d.txt
```

Then post 040d.txt.

---

### Post by Roanoke on 2009-03-22
Thank you, that worked :)

---

### Post by techflat on 2009-04-08
> **everthonvaladao said:**
> I found the answer by adapting [[COLOR="Blue"]the script from this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=994233&highlight=udev+rule+gui"), ending with something like this:

```

#!/bin/bash
set -x 
xhost local:MYUSERNAME
export DISPLAY=:0.0

su MYUSERNAME -c '/usr/local/bin/my_script args1 arg2 etc'

## (Optional) Put a notification-icon into the system tray
#/usr/bin/zenity --notification --window-icon=/usr/share/pixmaps/gnome-irc.png --text="the USB stuff was connected!"

```

It succesfully run some GUI app! :-)

Nice. Just a question, what does the xhost local:MYUSERNAME do?

---

### Post by mihaicj on 2009-05-07
It just doesn't work for me. I tried ```
cat /etc/udev/rules.d/85-my_backup.rules
ACTION=="add", ATTRS{idVendor}=="1058", ATTRS{idProduct}=="0704", RUN+="..."
```

And nothing happens. Anyone have some ideas?

---

### Post by map84 on 2009-08-13
> **Carlos Santiago said:**
> Reclusivemonkey, seems to me that you didn't notice one small, however very important, thing!
This procedure is generic and works with ANY usb device. For example I use it to configure and start my internet connection when I plug in my UMTS modem.

is this also working with a pcmcia-umts-card?
Could you provide me with your internet-connection-script, please?
Thank you!

---

### Post by wtstommy on 2009-12-04
I am trying to follow this guide to run a automatic backup script when mounting my Android phone. Here is my udev rule:

ACTION=="add", KERNEL=="sd?1", SYSFS{serial}=="040363260701200E", RUN+="/usr/local/bin/backupDroid.sh"

It sort of works. It runs the script. But it waits for the script to finish running BEFORE it mounts the device, which of course is not really helpful. Ideas?

---

### Post by Carlos Santiago on 2009-12-04
wtstommy, like I said in post [#6]("http://ubuntuforums.org/showpost.php?p=3033983&postcount=6") add the SYMLINK to your rule. Something like
```
ACTION=="add", KERNEL=="sd?1", SYSFS{serial}=="040363260701200E", RUN+="/usr/local/bin/backupDroid.sh",SYMLINK+="android_phone"

```
When you plug it, your device should be accessible in /dev/android_phone.

Then you should be able to mount it with:
```
sudo mkdir /mnt/android
sudo mount /dev/android_phone /mnt/android

```
The directory that will be the mount point of your device (in this case /mnt/android), you only need to create once.

If you need to define the file system, try:
```

sudo mount -t vfat /dev/android_phone /mnt/android

```

If the mount works, add the mount line in the beginning of your script.

---

### Post by wtstommy on 2009-12-04
I found the answer to my question. You have to "detach" the executed script. I found out how to do that here: [http://ubuntuforums.org/showthread.php?t=1098089](http://ubuntuforums.org/showthread.php?t=1098089)

---

### Post by restart on 2009-12-13
Just tried to write the same rule for my SD Card reader when I plug the **correct** SD card into it.

```
ACTION=="add", BUS=="pci", ATTRS{idVendor}=="fc30", ATTRS{idProduct}=="3da9", RUN+="/home/pechenie/.bin/photobackup.py"
```

Why pci? Coz:

```
# lspci | grep SD
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Also, idVendor:idProduct got from automouting folder:
```
/media/FC30-3DA9/
```

And finally:
```

# fdisk -l
Disk /dev/mmcblk0: 3999 MB, 3999268864 bytes
82 heads, 17 sectors/track, 5603 cylinders
Units = cylinders of 1394 * 512 = 713728 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               6        5604     3901440    b  W95 FAT32

```

Any suggestions?

---

### Post by tanoloco on 2010-03-17
hi to all!

first of all thanks to Carlos for this great guide :)

I would like to run a script on mounting .. anything :)
For testing purpose I've created a simple entry for my /etc/udev/rules.d/85-my_rule.rules
```

ACTION=="add", RUN+="/usr/bin/touch /home/testcrypt.txt"
```and it works great whenever a usb device is mounted, but unluckly it doesn't work
for me when I mount a partition on  an internal hard drive already connected.

I would like it to run on gnome/karmic using the gui: the user must click on Places > partition_name
and it must mount the partition and run the script automatically without anyhing to do manually.

Hope I've been clear: I'm not english mother tongue :)

Any help would be appreciated.

---

### Post by AndyDeGroo on 2010-03-19
> **tanoloco said:**
> 
I would like to run a script on mounting .. anything :)
For testing purpose I've created a simple entry for my /etc/udev/rules.d/85-my_rule.rules
```

ACTION=="add", RUN+="/usr/bin/touch /home/testcrypt.txt"
```and it works great whenever a usb device is mounted, but unluckly it doesn't work
for me when I mount a partition on  an internal hard drive already connected.

I would like it to run on gnome/karmic using the gui: the user must click on Places > partition_name
and it must mount the partition and run the script automatically without anyhing to do manually.


You may get more information about what's going on by running:
```
udevadm monitor -p
```and mounting your drive while udev monitoring runs

and if that's not enough You can try setting higher udev logging level:
```
sudo udevadm control --log-priority=info
```and after that mount/unmount your device and check syslog

---

### Post by kiddykoff on 2011-02-17
> **unutbu said:**
> Try removing SUBSYSTEM=="usb_device":
```

ACTION=="add", SYSFS{idVendor}=="040d", SYSFS{idProduct}=="6204", RUN+="/usr/share/scripts/backup.sh"

```
Also make sure that /usr/share/scripts/backup.sh is executable:
```

sudo chmod 755 /usr/share/scripts/backup.sh 
```

Unplug and plug in the device once more. Check for /tmp/env.out.
If you don't see /tmp/env.out, run
```

for dev in $(ls /sys/bus/usb/devices); do udevinfo -ap /sys/bus/usb/devices/$dev; done > udevinfo.txt

awk 'BEGIN { RS=""; FS="n"; PATTERN="040d" } { if ( $0 ~ PATTERN ) print $0; }' udevinfo.txt > 040d.txt
```

Then post 040d.txt.

I'm having a problem with my script not launching. I tried putting in those commands suggested, but the problem is there is no udevinfo command. What package is it a part of? The replacement is udevadm. However just replacing the command does not work. Can someone tell me what is going on here? I'm trying my best.

---

### Post by elianthony on 2011-05-05
I couldn't get this to work on Ubuntu 10.04. I tried the different versions brought out in the thread, and I get nothing. Anyone using it on 10.04?

---

### Post by jarazz on 2011-09-11
Hello Everyone
I have big problem with a simply script. I need automatic copy all files from USB pendrive to my folder in HDD, every time when I will plug USB device.
I used rule :

ACTION=="add", KERNEL=="sd?", SUBSYSTEM=="usb", RUN+="/home/art/bin/copy.sh"

and (first) script copy.sh

#!/bin/sh
mountdir="/media/`blkid /dev/sd? | awk {'print $2'} | sed -e 's/LABEL=//' -e 's/"//g'`"
dstdir="/home/art/Wideo/"
mkdir -p $dstdir
cp -r $mountdir $dstdir
chmod -R 777 $dstdir

(second)

#!/bin/sh 
find /media/ -name "*[mpg|avi|mov|mp4]" -exec cp {} /home/art/Wideo \; chmod -R 777 /home/art/Wideo

Unfortunetly both of scripts works when I run them from file, but not working when i plug my USB device. 
I have Ubuntu 11.04
Any suggestions?

---

### Post by tumutanzi on 2011-09-15
what kind of USB device?

---

### Post by jarazz on 2011-09-17
> **tumutanzi said:**
> what kind of USB device?
Pendrive

---

