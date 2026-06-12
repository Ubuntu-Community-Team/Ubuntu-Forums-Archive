---
title: "Howto: Get Your External Syquest Drive Working In Ubuntu"
date: 2008-05-20
forum: Tutorials
---

### Post by Bungo Pony on 2008-05-20
This is my first howto! Give me a round of applause =D>

Before I go on, I'd just like to say that Google is really your friend, and there's two sources that I got information from. I will share them here:

[http://cyberelk.net/tim/parport/parport.html](http://cyberelk.net/tim/parport/parport.html)
[http://ubuntuforums.org/showthread.php?t=77900](http://ubuntuforums.org/showthread.php?t=77900)

From these two sources and some tinkering, you should be able to get almost any external parallel drive working in Ubuntu!

Also, this Howto is made for Ubuntu 8.04 Hardy Heron. So let's get started!

==========================================================

First, you need to write a script to get the parallel drivers loaded up. This should work with all Syquest drives.

Open up gedit (either type in gedit in a terminal, or click Applications -> Accessories -> Text Editor)

copy and paste the following into the text file:
```
# Start here...

# modprobe parport # Already maybe loaded
# modprobe parport_pc # Already maybe loaded

modprobe paride

#
# The following 2 steps are not necessary on Breezy...
# mkdir /lib/modules/$(LINUX_VERSION)/misc
# cp /lib/modules/$(LINUX_VERSION)/kernel/drivers/block/paride/epat.o /lib/modules/2.4.20-20.8/misc/epat.o

echo "Inserting the necessary modules..."
modprobe epat # Sparq Protocol
modprobe pd # Sparq Driver

dmesg | grep paride
# Look for: "paride: epat registered as protocol 0"

# modprobe pd drive0=0x378,1 drive1=0x3bc,1 # Example syntax
# To support such a wide range of devices PARIDE, the parallel port IDE subsystem, is actually structured in three parts.
# There is a base paride module which provides a registry and some common methods for accessing the parallel ports. 
# The second component is a set of high-level drivers for each of the different type of supported device:
# pd IDE disk
# pcd ATAPI CD-ROM
# pf ATAPI disk
# pt ATAPI tape
# pg ATAPI generic devices

# The pg driver exists mainly to support parallel port ATAPI CD-R and CD-RW devices. 

#
# Run the commands below from a script 
# ================================================== ==================
echo "Running commandsmou..."
test `whoami` = 'root' || echo "You must be root to execute the commands."
cdrecord -scanbus > /dev/null
if ! (pidof kerneld || test -f "/proc/sys/kernel/modprobe"); then
echo "Neither kerneld nor kmod are running to automatically load modules".
fi
report_no_autoload() {
echo "Ensure the module $1 is loaded automatically next time."
}
if test ! -f "/proc/scsi/scsi"; then
report_no_autoload scsi_mod && modprobe scsi_mod
fi
if ! grep "^........ sg_" /proc/ksyms > /dev/null; then
report_no_autoload sg && modprobe sg
fi
if ! grep "^........ sr_" /proc/ksyms > /dev/null; then
report_no_autoload sr_mod && modprobe sr_mod
fi
if ! grep "^........ loop_" /proc/ksyms > /dev/null; then
report_no_autoload loop && insmod loop
fi
if ! grep iso9660 /proc/filesystems > /dev/null; then
report_no_autoload iso9660 && modprobe iso9660
fi
echo "The following is only needed for IDE/ATAPI CD-writers."
if ! grep ide-scsi /proc/ide/drivers > /dev/null; then
report_no_autoload ide-scsi && modprobe ide-scsi
fi
# ================================================== ==============

# Now check if it is recognized:
# cdrecord -scanbus

# Mount to an appropriate location after placing a CD in the drive
mkdir /media/Sparq
mount -t vfat /dev/pda1 /media/Sparq
ls -al /media/Sparq # Works !

```

Save it under a name you like. I personally chose the name "Paride" (which is the name of the parallel port IDE subsystem)

Next, you need to make the file executable. Open up a terminal and type (or copy + paste) the following:

```
chmod +x paride
```

Now, you can run the script by typing in the following in a terminal

```
sudo ./paride
```

and you should see the directory of your Syquest drive!

*Note: you only need to run the script once per session. You can alternately mount and unmount the drive my typing the following:

Mount:
```
sudo mount /dev/pda1
```

Unmount:
```
sudo umount /dev/pda1
```


If you see something in my Howto that could use improvement, please share!

Good luck, and have fun with your Syquest drive!

---

### Post by lfmiller on 2009-01-10
Hi, Thanks worked great, but I personally got a lot of error messages when the script ran, but the drive mounted and worked. - On a side note, in your orignal post you said it works under 8.04 - It also works under 8.10 - that is what I am running. Thanks again, LeRoy, KD8BXP

---

### Post by DocEsq on 2009-03-29
This did not work for me.

When I attempted to run the script *sudo ./paride* I got the message "Loading Modules".  This message never changed and I my system froze causing me to use the reset button.

I also noticed that there did not appear to be any Syquest directory and that there was no */pda1*  in */dev*

Doc

---

### Post by afrodeity on 2012-10-05
```
FATAL: Module ide_scsi

```
I am running 12.04, apparently ubuntu linux no longer has this module, any ideas?

---

### Post by ColfaxLinix on 2013-04-16
*April 2013*

Since google "ubuntu syquest" gets you here, I thought I'd post what worked for me. Under Ubuntu 12.04 LTS my computer also locks up as described by others. Something goes very wrong when try to install kernel module pd.ko.

The following is not a fix for Ubuntu. This is a work-around to get files off the parallel drive ezflyer disks and saved elsewhere.

Computer: Dell Dimension 2400 w Intel Pentium 4 CPU 2.53GHz (32 bit)

Procedure:

- Create a live CD of Ubuntu 8.04.4 (from 2008, the year of the above HOWTO). I used **ubuntu-8.04.4-desktop-i386.iso**.

- Attach the ezflyer to the parallel port, power it up, and insert a disk.

- Boot the Ubuntu live CD.

- When Ubunbu has fully loaded open a Terminal window.

- Become 'root' and create a mounting point for the ezflyer:
> **sudo su**
> **mkdir /media/ez**  (<- any directory name will do)

- Install the kernel modules necessary to handle the ezflyer:
> **modprobe paride**
>** modprobe epat**
> **modprobe pd**

- mount the ezflyer:
> **mount /dev/pda1 /media/ez**

- The ezflyer should now be 'good to go'. Verify with:
>  **echo I am Here > /media/ez/test.txt; cat /media/ez/test.txt**

Note: This scheme occasionally freezes in the same way as under 12.04 LTS. In this case I suspect I have flaky drive since it doesn't always eject properly.

Good luck!

---

