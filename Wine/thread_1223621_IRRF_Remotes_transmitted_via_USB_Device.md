---
title: "IR/RF Remotes transmitted via USB Device"
date: 2009-07-26
forum: Wine
---

### Post by coachnatebean on 2009-07-26
I hope the long post does not discourage others from reading my request for help.  It was meant to trace my steps to solve this problem.

I am currently using WINE 1.1.26 on Ubuntu 9.10

**1st Attempt**
I am trying to install and get operational a program I use in the classroom called [ [COLOR=red]eInstruction-CPS[/COLOR]]("http://www.einstruction.com/products/assessment/cps/index.html") (similar to iClicker).  Students respond to questions during a lesson with a remote, which is then transmitted to the program via USB interface for data desegregation.  Installation of this program required me to install Microsoft Frameworks 2.0 installed BEFORE actually installing eInstruction.  I knew of this from a botched install, and subsequent re-install of Ubuntu 9.10 (wanting to have an absolutely clean platform on which to install the program).  This was done using WineTricks.

Microsoft Frameworks 2.0

[LIST]
[*]$ sudo rm -rf ~/.wine
$ sudo apt-get install cabextract
$ wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
$ sh winetricks corefonts dotnet20
[/LIST]

Thinking I had the necessary support applications installed, I found out I needed to install...
MS Jet 4.0 Service Pack 8

[LIST]
[*]$ ./winetricks jet40
[/LIST]

and MS MDAC 2.8

[LIST]
[*]$ ./winetricks mdac28
[/LIST]

It was only after installing these three components was I able to move forward with the installation process.  The eInstruction program loads correctly and appears to function normally until I try and use the IR or RF remotes.  It reports it can not find the USB device.  

**2nd Attempt**
After looking around on the forums, I followed the advice -[[COLOR=red]HERE[/COLOR]]("http://forum.winehq.org/viewtopic.php?t=4271&highlight=usb+recognized")- and initiated in a terminal...

[LIST]
[*]$ ln -s /dev/ttyUSB0 /dev/ttyS2 
$ ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
[/LIST]

...but, again, was unable to get the program to locate the USB device.

Another search of the forums let me -[[COLOR=red]HERE[/COLOR]]("http://forum.winehq.org/viewtopic.php?t=1131&highlight=usb+recognized")- to consider the possibility of a driver/device mismatch.  From a terminal window I ran...

[LIST]
[*]$ lsusb
[/LIST]

...which returned the following information.

[LIST]
[*]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 028: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/LIST]

Assuming the [[COLOR=red]Future Technology Devices International[/COLOR]]("http://www.ftdichip.com/") (FTDI) driver(s) were not installed I went to their website and found the corresponding drivers for FT232 USB-Serial (UART) IC.

[LIST]
[*][[COLOR=red]D2XX Drivers[/COLOR]]("http://www.ftdichip.com/Drivers/D2XX.htm")
[/LIST]

> READ ME File - Instructions for installing the d2xx shared lib

As Linux distributions vary these instructions are a guide to installation and use.  This setup works with Mandrake 9.2 but may require some investigation on other distributions.  This library has been tested using kernel 2.4.25.  D2XX documentation is available for the Windows dll - some variations may occur between linux and windows implementation. We have endevoured to make the APIs appear the same on both platforms however some issues may slip and we would appreciate that you contact support if you observe this.

D2XX for linux was primarily developed to aid porting windows applications written with D2XX to linux.  Unfortunately the source code for D2XX is not freely available - however if you prefer to have the source and are starting a project from scratch you can try libftdi from Thomas Jarosch.  Details of this library are on the ftdi web site. 

libftd2xx uses an unmodified version of libusb ([http://libusb.wiki.sourceforge.net/](http://libusb.wiki.sourceforge.net/)).  Source code for libusb is included in the driver distribution in the libusb-0.1.12 directory.

Installation:
1. unzip and untar the file given to a suitable directory
gunzip libftd2xx0.4.12.tar.gz
tar -xvf libftd2xx0.4.12.tar

2. As root user copy the following files to /usr/local/lib
cp libftd2xx.so.0.4.12 /usr/local/lib

3. Change directory to /usr/local/lib
cd /usr/local/lib

4. make symbolic links to these files using the following commands:
ln -s libftd2xx.so.0.4.12 libftd2xx.so

5. Change directory to /usr/lib
cd /usr/lib

6. make symbolic links to these files using the following commands:
ln -s /usr/local/lib/libftd2xx.so.0.4.12 libftd2xx.so

7. Add the following line to /etc/fstab:
none /proc/bus/usb usbdevfs defaults,devmode=0666 0 0

There have been reports that you may need to use the following command for some distros none /proc/bus/usb usbdevfs defaults,mode=0666 0 0 (use usbfs in 2.6 kernels)

8. Remount all in the fstab file
mount -a

If you have problems with this check with usbview (search on the internet for application or it can be sent to you by ftdi) to check the usb file system is mounted properly.

Other problems will be related to the ftdi_sio driver loading - 

1.you must unload this driver (and usbserial) if it is attached to your device ("rmmod ftdi_sio" and "rmmod usbserial"as root user). 

2.Your PID/VID has not been included in the distribution.A PID of 0x6006 and VID of 0x0403 should work as a temporary workaround.

Known issues:

2.6 kernels require a usb reset to be performed prior to opening a device otherewise subsequent opens will not be successfull.  This can cause a break (if there is a mixture of opened and unopened devices in the system) in communication with any other opened device.

FT_Listdevices and FT_CreateDeviceInfoList will also have this effect.I had no idea what to make of the information in the READ ME file, so I did nothing.

> Other problems will be related to the ftdi_sio driver loading - 

1.you must unload this driver (and usbserial) if it is attached to your device ("rmmod ftdi_sio" and "rmmod usbserial"as root user). 

2.Your PID/VID has not been included in the distribution.A PID of 0x6006 and VID of 0x0403 should work as a temporary workaround.

Known issues:

2.6 kernels require a usb reset to be performed prior to opening a device otherewise subsequent opens will not be successfull.  This can cause a break (if there is a mixture of opened and unopened devices in the system) in communication with any other opened device.

FT_Listdevices and FT_CreateDeviceInfoList will also have this effect.[[COLOR=red]VCP Drivers[/COLOR]]("http://www.ftdichip.com/Drivers/VCP.htm") 
> READ ME File
You may require the sources matching the current kernel to be installed on your system (and built). 

There are many helpfull websites that can assist you with this step and it isnt as daunting as you first think!

Try [http://www.osnews.com/story.php?news_id=2949&page=2](http://www.osnews.com/story.php?news_id=2949&page=2) as a first step if the link is still available.

To install the ftdi_sio driver use the following steps:

1. Create a temporary folder in your linux machine.

2. Extract the files from ftdi_sio.tar.gz file to your temporary folder
"gunzip ftdi_sio.tar.gz"
"tar -xvf ftdi_sio.tar"

3. Build the driver
"make"

4. Plug in your ftdi device

5. Check to see if default driver was loaded
"lsmod" - you will see ftdi_sio if a driver is loaded

6. Remove the default installed driver
"rmmod ftdi_sio"

7. Install the newly built driver
"insmod ftdi_sio.o"

NOTES: 

1.This driver was adapted from the 2.4.32 kernel to support both the 2232C and 232R chip

2.There is no need to follow this procedure if you want 232R chip supprt. The 232BM driver will be sufficient.Changes made to the driver for the 232R chip are purly cosmetic (plug/unplug will appear as a 232R chip in the kernel log).Of particular note for the VCP Drivers was...
> 6. Remove the default installed driver
"rmmod ftdi_sio"  [COLOR=green]<<<This removed the driver I just installed.[/COLOR]

7. Install the newly built driver
"insmod ftdi_sio.o"  [COLOR=green]<<<This file was not found in the package.[/COLOR]...so I repeated the steps and stopped at...
> 5. Check to see if default driver was loaded
"lsmod" - you will see ftdi_sio if a driver is loaded...which it was.

I also had no idea what to make of these additional notes in the READ ME file, so I did nothing.
> 1.This driver was adapted from the 2.4.32 kernel to support both the 2232C and 232R chip.

2.There is no need to follow this procedure if you want 232R chip supprt. The 232BM driver will 
be sufficient.  Changes made to the driver for the 232R chip are purly cosmetic (plug/unplug will appear as a 232R chip in the kernel log).A restart and attempt to load eInstruction yeilded the same result.  The program would load fine, but it was unable to locate the USB device.

**3rd Attempt**
Going back to the forums, something in -[[COLOR=red]THIS[/COLOR]]("http://forum.winehq.org/viewtopic.php?t=1131&highlight=usb+recognized")- post connected my experience with WindowsXP and Ubuntu...maybe something is the registry needs to be added/changed.  The forum post directed me to the Wine Registry Wiki where I searched for information on -[[COLOR=red]PORTS[/COLOR]]("http://wiki.jswindle.com/index.php/Wine_Registry#Ports")-.  

To the Wine Registry I added...

[LIST]
[*][HKEY_LOCAL_MACHINE\hardware\devicemap\serialcomm] 
"COM2"="COM2" 
"COM1"="COM1"
[/LIST]
 
...and to the system.reg file I added...

[LIST]
[*][HARDWARE\\DEVICEMAP\\SERIALCOMM] 1131331688 
"COM1"="COM1" 
"COM2"="COM2"
[/LIST]
 
...and...

[LIST]
[*][Hardware\\Devicemap\\Serialcomm] 1231984861 @="" 
"Serial0"="COM1" 
"Serial1"="COM2" 
"Serial2"="COM3" 
"Serial3"="COM4" 
"Serial4"="COM5" 
“Serial5"="COM6" 
“Serial6"="COM7" 
"Serial7"="COM8" 
"Serial8"="COM9"
[/LIST]
 
FINALLY, that was the addition I needed for the program to recognize the USB device.  BUT the USB device still does not gather the information from the remotes.  Each tweak or change gets me one step closer to using this program in Ubuntu, but I need help with two things...

1.How do I get more than one COM port to be recognized?  In WindowsXP, I have multiple ports to choose from.  In Ubuntu/Wine I only have COM1.

2.How do I get the USB device to recognize and collect the information from the remotes and send the information to the eInstruction-CPS program?

THANK YOU for taking the time to read, and potentially solve, my questions/comments.

---

### Post by Whiffle on 2009-07-26
From the looks of what you've posted, Linux is properly detecting it and loading the driver for the 232 (which is why lsmod is showing the module as loaded).  I'd like to try a couple of things.

First, unplug the device, then plug it back in.  Now, open up a terminal and run "dmesg".  Look at the last 10 lines or so, it may tell you which object in /dev it is getting loaded as, something like /dev/ttyS0.  If it doesn't then we'll do it the hard way.

In the terminal, do "ls /dev/tty*" and look at what shows up.  Now, unplug the device and run the command again, has anything disappeared?  If you plug the device back in, and run the command again, has it reappeared?  If it has, then thats the device you're going to need to get going with wine.

And while you're at it, could you post the output of "ls -l ~/.wine/dosdevices/" (ctrl+shift+c to copy out of the terminal)

---

### Post by coachnatebean on 2009-07-26
Thank you for your quick reply and willingness to help!
> First, unplug the device, then plug it back in. Now, open up a terminal and run "dmesg". Look at the last 10 lines or so, it may tell you which object in /dev it is getting loaded as, something like /dev/ttyS0. If it doesn't then we'll do it the hard way.I believe this is the information you are requesting...I can copy/paste the whole output, but its pretty much the same thing.

[LIST]
[*][347146.152016] usb 5-1: new full speed USB device using uhci_hcd and address 29
[347146.350258] usb 5-1: configuration #1 chosen from 1 choice
[347146.352262] ftdi_sio 5-1:1.0: FTDI USB Serial Device converter detected
[347146.352291] usb 5-1: Detected FT232RL
[347146.352335] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0
[/LIST]


> In the terminal, do "ls /dev/tty*" and look at what shows up.  Now, unplug the device and run the command again, has anything disappeared? If you plug the device back in, and run the command again, has it reappeared? If it has, then thats the device you're going to need to get going with wine.According to your directions the following device is the one we need to get going with wine.

[LIST]
[*]/dev/ttyUSB0
[/LIST]


> ...could you post the output of "ls -l ~/.wine/dosdevices/"
[LIST]
[*]coachnatebean@Discovery-Ubuntu:~$ ls -l ~/.wine/dosdevices/
total 0
lrwxrwxrwx 1 coachnatebean coachnatebean 10 2009-07-15 10:42 c: -> ../drive_c
lrwxrwxrwx 1 coachnatebean coachnatebean  8 2009-07-25 19:00 com1 -> /dev/USB
lrwxrwxrwx 1 coachnatebean coachnatebean 11 2009-07-15 18:59 d: -> /media/disk
lrwxrwxrwx 1 coachnatebean coachnatebean  9 2009-07-15 17:02 d:: -> /dev/sdb1
lrwxrwxrwx 1 coachnatebean coachnatebean  1 2009-07-15 10:42 z: -> /
[/LIST]


Thank you, again, for your help.  In a sick-twisted way, I'm learning a wealth of information about Ubuntu/Wine! :P

---

### Post by Whiffle on 2009-07-26
Oh its the only way to learn ;)

Looks to me like its getting drivers and everything, we just need to get the wine side of it figured out.  Unfortunately, I havn't really done much with wine and serial devices, so this could be a bumpy ride.  

I would try this command again:
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

I just did that with a usb serial converter i have laying around, and was able to make the activity light blink by doing

echo "blah" > ~/.wine/dosdevices/com1 

so I know that part works.  I'll have to look into the wine side of it though.

---

### Post by coachnatebean on 2009-07-26
for purposes of tracking the steps to a solution...

It was not until I stumbled upon the words [COLOR=blue]REVERSE ENGINEERING[/COLOR] that the pieces started coming together.

When I plugged the same device into a WindowsXP unit, I started looking into the Device Manager at different settings.  It further frustrated me that the device was being recognized on COM4, when I could only get Ubuntu to recognize the device on COM1.  

The next logical place for me to look was in the WindowsXP Registry, hoping to compare entries to fill in the missing pieces of the puzzle.  

In the Windows Registry it listed

[LIST]
[*][HKEY_LOCAL_MACHINE\HARDWARE\DEVICEMAP\SERIALCOMM]
"\\Device\\VCP0"="COM4"
[/LIST]

In the Wine Registry it listed

[LIST]
[*][HKEY_LOCAL_MACHINE\HARDWARE\DEVICEMAP\SERIALCOMM]
"COM1"="COM1"
"COM2"="COM2"
"COM3"="COM3"
"COM4"="COM4"
"COM5"="COM5"
[/LIST]


In the Windows Registry it listed

[LIST]
[*][HKEY_CURRENT_USER\Software\eInstruction\CPS4x\Settings\ComPort]
@="4"
[/LIST]

In the Wine Registry it listed

[LIST]
[*][HKEY_CURRENT_USER\Software\eInstruction\CPS4x\Settings\ComPort]
@="1"
[/LIST]

After changing the ComPort to [COLOR=blue]4[/COLOR] and initiating a link via 

[LIST]
[*]ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com4
[/LIST]

I am happy to say the USB receiver and remotes are communicating with each other!  Now all that's left is to "student test" the remotes in the classroom.

I guess all I needed was someone to bounce an idea off of to get to the solution.

THANK YOU!

---

### Post by Fedele on 2010-09-23
Things have changed a bit over the years.  eInstruction CPS now has Linux support.

We just got our remotes working in Karmic and this is how...  We installed InterwritePRS from the file located here:

[http://www.einstruction.com/support_downloads/downloads.html](http://www.einstruction.com/support_downloads/downloads.html)

and modified a file:

sudo gedit /opt/InterWrite_PRS/PRS.ja

to include /dev/ttyUSB0 in -DSERIAL_PORT_LIST like so:

-DSERIAL_PORT_LIST=/dev/ttyUSB0:/dev/ttyS0:/dev/ttyS1:/dev/ttyS2:/dev/ttyS3:/dev/ttyACM0:/dev/ttyACM1:/dev/ttyACM2:/dev/ttyACM3:/dev/usb/acm/0:/dev/usb/acm/1:/dev/usb/acm/2:/dev/usb/acm/3

That's it.  No Wine, No Registry.

---

