---
title: "wake from suspend issue with GPS and an already running gps client program"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-09
[COLOR="#FF0000"]I solved this with a gotcha, my solution leaves wired LAN  unconfigured after awake from sleep. Of course on boat I have no lan.
If anyone knows why, please let me know[/COLOR].

The downside problem is if you sleep the PC, then wake the PC,  then you have to run a gps program to activate the gps streaming, it is maybe gpsd not running after awaken from sleep?
Who wants to do that! Say your running your gps mapping program, you sleep then awaken, but to use your gps mapping program you have to close it and reopen it, or run xgps after awakening PC from sleep.

Please, I would really like to make this work more effortlessly.
I have a lt-20 gps earthmate with cypress chip which works just fine.

But when you suspend and awaken, the system is no longer getting data from gps into a prior running gps program.

To reproduce, run xgps, watch sattelite data streaming in.
then sleep mode the PC
then awake the PC, xgps is not receiving any data.
close xgps and reopen xgps and it is receiving data.
Any earlier running gps program, such as opencpn, running before the sleep mode will then start working with the gps.

The downside problem is if you sleep, then you have to run a gps program to activate the gps streaming, it is maybe gpsd not running after awaken from sleep?

---

### Post by sdowney717 on 2014-04-09
[http://www.catb.org/gpsd/faq.html#sleep](http://www.catb.org/gpsd/faq.html#sleep)

Can someone help me with this solution?

> Why does my GPS get lost when I sleep/wake my laptop?

This is not a GPSD problem, but a result of the way Linux handles USB serial devices. In a default Linux configuration, USB serial device name do not depend on which physical port you plug the USB/serial adaptor, but on what order you plug devices in: 1st device gets /dev/ttyUSB0, 2nd gets /dev/ttyUSB1, etc....

This collides with what happens during a suspend/resume. If you suspend while gpsd has a device active, it will hold the device open while your laptop is asleep - but, meanwhile, the suspend logic is shutting down hotpluggable devices to be recreated at resume time. On resume, Linux will see that the old device is open and recreate one with a different name, leaving gpsd looking at a bad file descriptor.

There is a solution to this problem: create a stable gps-usb device that is actually a symlink which gets modified by hotplug events, and give gpsd that device when you invoke it. You'll need these replacement udev rules, and the experience required to patch them so the vendor ID in the last one matches your GPS hardware (look in your lsusb output).

---

### Post by sdowney717 on 2014-04-09
here is my lsusb which the solution mentions.

```
boat@boat-MS-7529:~$ lsusb
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1163:0200 DeLorme Publishing, Inc. Earthmate GPS (LT-20, LT-40)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
boat@boat-MS-7529:~$ 
```

---

### Post by QDR06VV9 on 2014-04-09
> **sdowney717 said:**
> here is my lsusb which the solution mentions.

```
boat@boat-MS-7529:~$ lsusb
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1163:0200 DeLorme Publishing, Inc. Earthmate GPS (LT-20, LT-40)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
boat@boat-MS-7529:~$ 
```
Have you done anything yet?
Huum? Maybe related [HERE]("http://ubuntuforums.org/showthread.php?t=1819707")
My Tom Tom used to do that all the time got rid of it.
Also have you tried unpluging and hot-plugin again?

---

### Post by sdowney717 on 2014-04-09
of course unplug - plug works , but not elegant solution.

Consider my situation,
PC is installed in boat in a cabinet.
PC uses a lot of power so very desirable to put it to sleep when not using it
Also very desirable to quickly power up when need to get boat moving.
USB is plugged into mainboard which is in cabinet.
Not easy to get access to the USB off the mainboard, would have to pull out a drawer and squeeze arm in to a small space. all the while boat is moving around on the water, etc...

What I found that works is running xgps after awake from sleep, that will re-enable  opencpn to get data from the gps.
That is not as good as the solution in that link.
**edit --- the  above does not work! although it seemed to I just tried it after letting it sleep for 30 minutes**

I do also have 3 external usb ports I could plug into which have easy acess, but again, not elegant. I can just imagine if boat heaves on a wave, I might break something trying to plug back in, better to just have it work again with less user action needed.

---

### Post by sdowney717 on 2014-04-09
[http://www.linuxfromscratch.org/lfs/view/7.5/chapter07/symlinks.html](http://www.linuxfromscratch.org/lfs/view/7.5/chapter07/symlinks.html)

found some info may help me here.

> 7.5.2. Dealing with duplicate devices

As explained in Section 7.4, “Device and Module Handling on an LFS System”, the order in which devices with the same function appear in /dev is essentially random. E.g., if you have a USB web camera and a TV tuner, sometimes /dev/video0 refers to the camera and /dev/video1 refers to the tuner, and sometimes after a reboot the order changes to the opposite one. For all classes of hardware except sound cards and network cards, this is fixable by creating udev rules for custom persistent symlinks. The case of network cards is covered separately in Section 7.2, “General Network Configuration”, and sound card configuration can be found in BLFS.

For each of your devices that is likely to have this problem (even if the problem doesn't exist in your current Linux distribution), find the corresponding directory under /sys/class or /sys/block. For video devices, this may be /sys/class/video4linux/videoX. Figure out the attributes that identify the device uniquely (usually, vendor and product IDs and/or serial numbers work):

udevadm info -a -p /sys/class/video4linux/video0
Then write rules that create the symlinks, e.g.:

cat > /etc/udev/rules.d/83-duplicate_devs.rules << "EOF"

# Persistent symlinks for webcam and tuner
KERNEL=="video*", ATTRS{idProduct}=="1910", ATTRS{idVendor}=="0d81", \
    SYMLINK+="webcam"
KERNEL=="video*", ATTRS{device}=="0x036f", ATTRS{vendor}=="0x109e", \
    SYMLINK+="tvtuner"

EOF
The result is that /dev/video0 and /dev/video1 devices still refer randomly to the tuner and the web camera (and thus should never be used directly), but there are symlinks /dev/tvtuner and /dev/webcam that always point to the correct device.

---

### Post by sdowney717 on 2014-04-09
looking in /dev/serial I see this delorme device.

Is that the temporary one? ttyusb1 not ttyusb0

Did ttyusb1 get created when it comes out of sleep?

unless someone can help me, I am going to have to hotplug this thing. hotlug might be slow to find satellites again.

---

### Post by sdowney717 on 2014-04-09
ok, I unplugged and replugged and looked at /dev/serial and now it is pointing to ttyusb0

---

### Post by sdowney717 on 2014-04-09
[http://marc.info/?l=gpsd-users&m=126969815425513](http://marc.info/?l=gpsd-users&m=126969815425513)

I see this is already been discussed how the gps is lost including regarding same program opencpn.
And someone has created a little guide and udev rules to try.

What other forum would be more appropriate for this question? I am running Trusty so I posted here originally.

---

### Post by monkeybrain20122 on 2014-04-09
I don't know anything about xgps and never use it. This may be a similar problem: wifi connection is killed on resume from hibernation for some hardware. There is a script to reactivate network that works for me. Maybe you can modify it (I have no idea how) for xgps?
[http://askubuntu.com/questions/348858/wifi-doesnt-work-after-hibernate-but-does-work-after-suspend](http://askubuntu.com/questions/348858/wifi-doesnt-work-after-hibernate-but-does-work-after-suspend)

Edited: it is not clear from you post whether this is specifically a 14.04 problem. Did it work before?

---

### Post by sdowney717 on 2014-04-09
No, dont think it did.
Of course before on earlier ubuntu os's, the pc refused to sleep.:)

I just tried the udev rules.
I modified the file using my usb id's
I called it as shown in the link '70-persistent-usb-gps.rules'

I copied into folder /etc/init.d/

I restarted udev? but gives this error?

```
boat@boat-MS-7529:~$ sudo restart udev /etc/init.d/udev reload
[sudo] password for boat: 
restart: Env must be KEY=VALUE pairs
boat@boat-MS-7529:~$ 
```


boat@boat-MS-7529:~$ xgps
boat@boat-MS-7529:~$ xgps

before sleep a device called gps0 is created when I plug in the usb gps.
```
boat@boat-MS-7529:~$ ls /dev/gps*
/dev/gps0
```

after awake from sleep, a new device gps1 is created, so it still changes the name
```
boat@boat-MS-7529:~$ ls /dev/gps*
/dev/gps1

```

my modded line in the file reads
SUBSYSTEM=="tty", ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK="ttyGPS-lt20"

So I dont have a clue, what to do?

---

### Post by sdowney717 on 2014-04-09
what is really bad about this, unplugging gps then plugging in gps, takes a while to refind the sky!
So your stuck with no gps data having to hotplug after a sleep till the gps can figure out where it is. 

The sleep mode, keeps the green light on the gps, so it is working during sleep mode.

---

### Post by sdowney717 on 2014-04-09
I messed up the directions!
Put file in wrong place
# 1) place this file in /etc/udev/rules.d
# 2) use default config or update with your own vendor:product ID (use "lsusb" to find them)
# 3) reload udev with "/etc/init.d/udev reload"

now it has created the new gps-lt20 

which is good, but the gps is not finding the sky which is unrelated to ubuntu i think

here is screen shot, it shows the symlinked gps lt20 now

---

### Post by sdowney717 on 2014-04-09
yes, it keeps the same name after awaken from sleep now.

gps finally found its location, so will test this.

but I need to point gpsd to this new symbolic link

/dev/ttyGPS-lt20
and not
/dev/ttyusb0

---

### Post by sdowney717 on 2014-04-09
Of course it just got infinitely more complicated. :(
[http://manpages.ubuntu.com/manpages/karmic/man8/gpsd.8.html#contenttoc3](http://manpages.ubuntu.com/manpages/karmic/man8/gpsd.8.html#contenttoc3)

anyone know how to tell the gpsd daemon to look at this new symbolic linked gps?

OR tell the opencpn to look at /dev/ttyGPS-lt20 ?



> GPS DEVICE MANAGEMENT
       gpsd maintains an internal list of GPS devices. If you specify devices
       on the command line, the list is initialized with those pathnames;
       otherwise the list starts empty. Commands to add and remove GPS device
       paths from the daemon´s device list must be written to a local
       Unix-domain socket which will be accessible only to programs running as
       root. This control socket will be located wherever the -F option
       specifies it.

       To point gpsd at a device that may be a GPS, write to the control
       socket a plus sign (´+´) followed by the device name followed by LF or
       CR-LF. Thus, to point the daemon at /dev/foo. send "+/dev/foo\n". To
       tell the daemon that a device has been disconnected and is no longer
       available, send a minus sign (´-´) followed by the device name followed
       by LF or CR-LF. Thus, to remove /dev/foo from the search list. send
       "-/dev/foo\n".

       To send a control string to a specified device, write to the control
       socket a ´!´, followed by the device name, followed by ´=´, followed by
       the control string.

       To send a binary control string to a specified device, write to the
       control socket a ´&´, followed by the device name, followed by ´=´,
       followed by the control string in paired hex digits.

       Your client may await a response, which will be a line beginning with
       either "OK" or "ERROR". An ERROR reponse to an add command means the
       device did not emit data recognizable as GPS packets; an ERROR response
       to a remove command means the specified device was not in gpsd´s device
       list. An ERROR response to a ! command means the daemon did not
       recognize the devicename specified.

       The control socket is intended for use by hotplug scripts and other
       device-discovery services. This control channel is separate from the
       public gpsd service port, and only locally accessible, in order to
       prevent remote denial-of-service and spoofing attacks.

---

### Post by sdowney717 on 2014-04-09
[http://gpsd.berlios.de/faq.html#sleep](http://gpsd.berlios.de/faq.html#sleep)

from the sleep facts for gpsd

> There is a solution to this problem: create a stable gps-usb device that is actually a symlink which gets modified by hotplug events, 

**and give gpsd that device when you invoke it. **

You'll need these replacement udev rules, and the experience required to patch them so the vendor ID in the last one matches your GPS hardware (look in your lsusb output).

I have the first part done.
What about this 
'and give gpsd that device when you invoke it. '
??????
 how is gpsd invoked?
insufficient information to process this request.:

---

### Post by sdowney717 on 2014-04-09
[http://gpsd.berlios.de/bt.html](http://gpsd.berlios.de/bt.html)

mentions you can 
sudo dpkg-reconfigure gpsd

Well I did that. I set it to use
/dev/ttyGPS-lt20

and still it does not work when awakening from sleep.
I honestly thought that would make it work.
So what am i doing wrong?

---

### Post by sdowney717 on 2014-04-09
making progress!
following some troubleshooting instructions.
gpsmon /dev/ttyGPS-lt20 did nothing
[http://gpsd.berlios.de/troubleshooting.html](http://gpsd.berlios.de/troubleshooting.html)

But I did figure out how to stop gpsd
sudo killall gpsd
and remove any sockets gpsd might have left behind, e.g.:
sudo rm /var/run/gpsd.sock

Then I did the dpkg-reconfigure gpsd putting in the symbolic linked gps and 
gpsd is now using that symbolic linked gps, note in xgps window the lt-20 name.
That used to say /dev/ttyUSB0

---

### Post by sdowney717 on 2014-04-09
But still on a sleep then awaken it is not right. 
I do not have to unplug-plug to get it working, I have to restart the program xgps which might be the same thing, it switches from using 
dev/ttyGPS-lt20 to either /dev/ttyUSB0 or /dev/ttytUSB1

If I close xgps and reopen xgps it goes back to using the symbolic linked gps /dev/ttyGPS-lt20

???????????????????

its like something is not internally connected properly.

both these pics show it using the wrong gps  when it awakens.
Any ideas?

It would be dum to have to close then reopen your gps mapping program everytime you awaken from sleep.
But I might have to do that, at least the GPS can stay plugged in and not have to reaquire its location.

---

### Post by sdowney717 on 2014-04-09
I have discovered that If I am running opencpn with gps working
If I sleep then awaken, opencpn has no gps data.

If I startup xgps, then xgps and opencpn get gps data.

SO, it is like after awaken from sleep, gpsd is off not sensing the need to process gps data.
Even if a gps program was running before.
And if you run a new instance of a gps program that needs gps data, then gpsd will start processing and sending gps data.

So I could leave opencpn open, and start up xgps to get gpsd to start working.

Does that sound like a feature or a bug?:p

---

### Post by sdowney717 on 2014-04-10
inexplicably, today when I awoke the PC from sleeping overnight gpsd is apparently not working at all.

Now I find on a reboot gpsd works on the old setting not linking the new symbolic liked gps????
And if I sleep, everything regarding gpsd which worked yesterday is a failure. :(

after a sleep, now xgps cant even find any gps

---

### Post by sdowney717 on 2014-04-10
I purged out gpsd and gpsd-clients (xgps is in there)

I reinstalled and checked it was working on ttyUSB0, it is.
Then did same thing I did yesterday, dpkg-reconfigure gpsd, pointing it to the symbolic linked ttyGPS-lt20, gpsd still shows it using ttyUSB0, so you have to killall gpsd, then reboot, because simply trying gpsd /dev/ttyGPS-lt20 fails to do a thing. 
So this gpsd must be very buggy implementation with ubuntu and only works on a very basic level which is difficult to customize. So I will have to undo everything and just hotplug because nothing works like they say.

 in etc/default is this file which tells gpsd what to do when it starts up I suppose.
```
# Default settings for gpsd.
# Please do not edit this file directly - use `dpkg-reconfigure gpsd' to
# change the options.
START_DAEMON="true"
GPSD_OPTIONS=""
DEVICES="/dev/ttyGPS-lt20"
USBAUTO="true"
GPSD_SOCKET="/var/run/gpsd.sock"
```

There are udev file rules that gpsd uses by default and maybe that is messing up on awaken from sleep. 
Because I think all these guides are from the past and no longer will work today, not being updated to keep up with all the changes.

40-gpsd.rules file contents

```
# udev rules for gpsd
#
# This file is Copyright (c) 2010 by the GPSD project
# BSD terms apply: see the file COPYING in the distribution root for details.
#
# GPSes don't have their own USB device class.  They're serial-over-USB
# devices, so what you see is actually the ID of the serial-over-USB chip.
# Fortunately, just two of these account for over 80% of consumer-grade
# GPS sensors.  The gpsd.hotplug wrapper script will tell a running gpsd
# that it should look at the device that just went active, because it
# might be a GPS.
#
# The following setup works on Debian and Ubuntu - something similar
# will apply on other distributions:
# 
#   /lib/udev/rules.d/25-gpsd.rules
#   /lib/udev/gpsd.hotplug
# 
# Setting the link in /lib/udev/rules.d activates the rule and determines
# when to run it on boot (similar to init.d processing).

SUBSYSTEM!="tty", GOTO="gpsd_rules_end"

# Prolific Technology, Inc. PL2303 Serial Port [linux module: pl2303]
ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# ATEN International Co., Ltd UC-232A Serial Port [linux module: pl2303]
ATTRS{idVendor}=="0557", ATTRS{idProduct}=="2008", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# PS-360 OEM (GPS sold with MS Street and Trips 2005) [linux module: pl2303]
ATTRS{idVendor}=="067b", ATTRS{idProduct}=="aaa0", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# FTDI 8U232AM / FT232 [linux module: ftdi_sio]
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cypress M8/CY7C64013 (Delorme uses these) [linux module: cypress_m8]
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0100", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cypress M8/CY7C64013 (DeLorme LT-40)
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug" 
# Garmin International GPSmap, various models (tested with Garmin GPS 18 USB)  [linux module: garmin_gps]
ATTRS{idVendor}=="091e", ATTRS{idProduct}=="0003", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cygnal Integrated Products, Inc. CP210x Composite Device (Used by Holux m241 and Wintec grays2 wbt-201) [linux module: cp210x]
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cygnal Integrated Products, Inc. [linux module: cp210x]
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea71", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# u-blox AG, u-blox 5 (tested with Navilock NL-402U) [linux module: cdc_acm]
ATTRS{idVendor}=="1546", ATTRS{idProduct}=="01a5", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# u-blox AG, u-blox 6 (tested with GNSS Evaluation Kit TCXO) [linux module: cdc_acm]
ATTRS{idVendor}=="1546", ATTRS{idProduct}=="01a6", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# MediaTek (tested with HOLUX M-1200E) [linux module: cdc_acm]
ATTRS{idVendor}=="0e8d", ATTRS{idProduct}=="3329", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"

ACTION=="remove", RUN+="/lib/udev/gpsd.hotplug"

LABEL="gpsd_rules_end"
```

---

### Post by sdowney717 on 2014-04-10
I wonder if this line
> # Cypress M8/CY7C64013 (DeLorme LT-40)
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug" 

which is same as my usb is causing mischief on awaken, because it is running "/lib/udev/gpsd.hotplug" file?

---

### Post by sdowney717 on 2014-04-10
nope commenting out that line did nothing helpful, i think made it worse.

I completely undid everything including the symbolic link gps rule creating a fixed device called ttyGPS-lt20, because also I noticed sudo reboot or from the menu failed to work anymore.

So it is back to original condition where you must hot unplug-plug in the usb gps device after sleep. sad, anyway I could not figure it out.

So why can the usb mouse work after sleep? But the usb gps can not without unplugging and replugging?

---

### Post by sdowney717 on 2014-04-10
I was also wondering maybe should SYMLINK+="gps%n" be changed to SYMLINK+="ttyGPS-lt20", and keep my symbolic link file 

current line in gpsd.rules that would apply to my usb gps
```
# Cypress M8/CY7C64013 (DeLorme LT-40)
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug" 

```

I also wonder if the web page here is ignorant about the original purpose of this file to create a fixed symbolic link to the gps,
so awaken from sleep, linux will keep the original name of the gps instead of making up a new name.
[http://code.ohloh.net/file?fid=lDt0sGcNXt7xG9dNpT0Iet-IDOo&cid=LF16k5chdPk&s=&fp=293438&mp&projSelected=true#L0](http://code.ohloh.net/file?fid=lDt0sGcNXt7xG9dNpT0Iet-IDOo&cid=LF16k5chdPk&s=&fp=293438&mp&projSelected=true#L0)

says
```
#
# ## This file is obselete, and kept for historical records
# ## only.  It documents alternate ways to use the (then) new
# ## udev facility.
#
# ##  See the file   gpsd.rules   in the source for updated rules
# 

```

---

### Post by sdowney717 on 2014-04-10
back at it, making progress.

I was thinking about /lib/udev/rules.d/gpsd.rules conflicting with the rule file I created  to create a fixed gps name.

So I deleted /lib/udev/rules.d/gpsd.rules
recreated my symbolic link file /etc/udev/rules.d/70-persistent-usb-gps.rules

then 
sudo killall gpsd
sudo dpkg-reconfigure gpsd

point gpsd to use /dev/ttyGPS-lt20

powered off and on and an improvement.
I can start opencpn, sleep, awake, start xgps, and opencpn and xgps are getting data from gpsd
:P

I have a script i can put into suspend that will start xgps after awaken from sleep.

BUT, still, putting the file  /etc/udev/rules.d/70-persistent-usb-gps.rules, prevents sudo reboot from working.

Any thoughts? should 70-persistent-usb-gps.rules, go into /lib/udev/rules.d ?

---

### Post by sdowney717 on 2014-04-10
ok I moved my symbolic gps linked file  70-persistent-usb-gps.rules, into /lib/udev/rules.d 

put this file to start xgps after resume from sleep
```
#!/bin/bash
# put in /etc/pm/sleep.d/xgps_awake_start

USERID=boat
SCRIPT="/usr/bin/xgps"

case "$1" in
  suspend|hibernate)
     ;;
  resume|thaw)
    export DISPLAY=":0"
    export XAUTHORITY="/home/$USERID/.Xauthority"
    su $USERID -c "$SCRIPT"
     ;;
  *) exit $NA
     ;;  
esac
```

And it works!!!!!
I suspend, I awake, xgps loads and gpsd starts sending gps data :P

BUT BUT, doing this kills my LAN leaving it unconfigured.
WHY??
putting this file into either /etc/udev/rules.d/ or /lib/udev/rules.d/ kills my wired LAN so not networking.


Any help would be nice as to why and what to do....
```
# 
# Author: Fulup Ar Foll
# Date:   26-jun-09
# Object: make sure GPS dev (ex: /dev/gps-usb) dont change name on sleep/wakeup
# -----------------------------------------------------------------------------
#
# 1) place this file in /etc/udev/rules.d
# 2) use default config or update with your own vendor:product ID (use "lsusb" to find them)
# 3) reload udev with "/etc/init.d/udev reload"
#
# Device alias can be:
#  (default) - by path  ==> SYMLINK="serial-$env(ID_PATH)"   /dev/gps-pci-0000:00:1d.1-usb-0:1:1.0
#            - static   ==> SYMLINK="gps-usb"                /dev/gps-usb
#            - custom   ==> RUN+="/usr/local/bin/myscript"   /dev/any-thingk-you-want
#
# DEFAULT CONFIG: you can use this file "as it is", you should then see a /dev/gps-pci* 
# that will be created for any of the serial/usb you hot-plug. The name is fixe but
# depend on the USB port you use. As a result the name is fix until you keep the same socket.
#
# -----------------------------------------------------------------------
# check "man 7 udev" for forther syntax. (search for %n)
# -----------------------------------------------------------------------

# Examples
# -----------------------------------------------------------------------
# Your own script:     SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", RUN+="/usr/local/bin/myscript"
# Static device name:  SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", SYMLINK="gps-usb"
# Path dependent name: SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", SYMLINK="gps-$env{ID_PATH}"
# In first case you do what ever you want, script receive the information about context in environement variables
# In second case you name is fixe (ex: /dev/gps-usb) this is working if your usb/serial ID(vendor:product) is unique
# In third case your device name depend on the port it is plugged in.


# ========================================================================================
#                          update YOUR CONFIG here after
# ========================================================================================

# Default rules is applied for any unspecified vendor:product devices
# -----------------------------------------------------------------------------------------
#SUBSYSTEM=="tty", ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK="gps-$env{ID_PATH}"

# Well known device may get a static device name 
# -----------------------------------------------------------------------
SUBSYSTEM=="tty", ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK="ttyGPS-usb"
SUBSYSTEM=="tty", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", SYMLINK="ttyGPS-rt650"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="5740", SYMLINK="ttyGPS-ait2000"
SUBSYSTEM=="tty", ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK="ttyGPS-lt20"

# ************************************************************************************
# WARNING: on Ubuntu version version 13 and more. Standard user does not have acces
#          to dialout group. In order to enable opencpn to access usb devices you
#          should enter following command in a terminal:
#       
#          sudo usermod -a -G dialout $LOGNAME 
#
# ***************************************************************************************
```

---

### Post by sdowney717 on 2014-04-10
I tried a solution from 2009, but that did not work.
my lan driver is r8169
[http://ubuntuforums.org/showthread.php?t=1160802](http://ubuntuforums.org/showthread.php?t=1160802)

so still cant sudo reboot, and after i did this suggestion in the above thread, it will not power off shut down

---

### Post by sdowney717 on 2014-04-10
running 
sudo service network-manger restart 

will bring up networking again.

BUT, I found this gps solution has a time problem.
If you sleep long time, then on awaken, gpsd is not sending any data.
Crazy stuff going on I think!
When was my last post? that is too long. It was one hour.
Hotplugging will bring it up again. so what is going to sleep after an hour and not waking up?

---

### Post by sdowney717 on 2014-04-12
Solution eventually fails inexplicably.
Eventually stops suspending everytime in gnome to a complete failure to suspend.

So I switch to ubuntu unity, and it works again for a while, then fails just like in gnome.
It is doing some kind of checking and I think it eventually hits a threshhold of unexpected configuration and says that is is it, no more going to work for you.

Frankly I dont have a clue. Looking at gpsd.rules that file always runs a linked udev hotplug script which I interupt with my rule/ I tried adding into my rule to run that hotplug rule but no help at all.

---

