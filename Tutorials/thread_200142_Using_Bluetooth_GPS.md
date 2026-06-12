---
title: "Using Bluetooth GPS"
date: 2006-06-19
forum: Tutorials
---

### Post by ninocass on 2006-06-19
This how too describes how to get your bluetooth GPS device to work under linux

This is my second how too and parts of the files needed were installed at different times ie the bluetooth a few months ago so if anyone has any problems / suggestions let me know :)

Step 1

install the needed bluetooth files:
```

sudo apt-get install bluez-pin
sudo apt-get install bluez-utils

```

Then edit the main bluetooth config file:
```

sudo gedit /etc/bluetooth/hcid.conf

```

delete everything in the file and replace it with:
```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "Nino's Laptop";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

```

restart the bluetooth services
```

 sudo /etc/init.d/bluez-utils restart

```

and now to test the bluetooth:
```

hcitool scan

```

this should return a list of devices like:
```

        00:16:4E:D7:AE:5F       Nokia N70
        00:12:62:AF:C0:6E       Nino
        00:11:67:80:41:96       BT-GPS

```

Step 2

With the bluetooth we need to create a serial connection between our GPS device and the computer

to do this we first need some information on the device; the MAC code and the serial port.

do a 
```

hcitool scan

```

and take the MAC address of the GPS unit in my case:
        00:16:4E:D7:AE:5F       Nokia N70
        00:12:62:AF:C0:6E       Nino
        00:11:67:80:41:96       BT-GPS

so i want:  **00:11:67:80:41:96**

to get the serial port do
```

sdptool browse 00:11:67:80:41:96

```

which will return 
```

Browsing 00:11:67:80:41:96 ...
Service Name: Bluetooth Serial Port
Service RecHandle: 0x10007
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    **Channel: 1**
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Serial Port" (0x1101)
    Version: 0x0100

```

the channel we want is 1

now create a file in /etc/bluetooth/ called rfcomm

```

sudo gedit /etc/bluetooth/rfcomm.conf

```

adding an entry:
```

rfcomm4 {
        bind yes;
        device < GPS MAC ADDRESS>;
        channel 1;
        comment "Serial Port";
        }

```

to start using the GPS type:
```

rfcomm connect 4

```

if for some reason you get

"Can't create RFCOMM TTY: Address already in use"

do:
```

sudo rfcomm release 4

```

again followed by 
```

rfcomm connect 4

```

that should display:

nino@laptop:~$ rfcomm connect 4
Connected /dev/rfcomm4 to 00:11:67:80:41:96 on channel 1
Press CTRL-C for hangup

any GPS software you are gonna use will make use of the /dev/rfcomm4

Step 3

Now to test the GPS install the GPS utils

```

sudo apt-get install gpsd-clients
sudo apt-get install gpsd

```

the GPSD is the daemon for the GPS reciever so we want to bind the service with the device:

```

gpsd /dev/rfcomm4

```

and finally to see if were getting any information from the GPS device run 

```

xgps

```

[img]http://nino.me.uk/gallery/albums/userpics/10001/desktop1.png[/img]

if you want a tracking program have a looky at gpsdrive

[img]http://nino.me.uk/gallery/albums/userpics/10001/normal_desktop2.png[/img]


Enjoy :D

Nino

---

### Post by mundano on 2006-07-14
I've done everything exactly like the howto, but when i type:

rfcomm connect 4 

I'm getting this error:

ruben-desktop:~$ rfcomm connect 4
syntax error line 3
Can't find a config entry for rfcomm4


Can you help me?

---

### Post by ymod on 2006-08-14
When editing the /etc/bluetooth/rfcomm.conf file you have to make sure you enter the information without the < Brackets >  

this is my rfcomm.conf file

rfcomm4 {
        bind yes;
        device 00:08:1B:12:FA:BB;
        channel 1;
        comment "Serial Port";
        }



Just on a side note, thanks to ninocass for a fantastic HowTo.

---

### Post by frankuzzo on 2006-08-27
Hi, first thanks for the howto.

Following it, I manage to have my gps bt listed while scanning:

```
$> hcitool scan
Scanning ...
00:0D:B5:30:47:C3       BT-GPS-3047C3
```

But than on the following browse commang I get nothing:
```
sdptool browse 00:0D:B5:30:47:C3
Browsing 00:0D:B5:30:47:C3 ...
```

I have usually to enter 0000 to pair on my PDA, is that necessary on linux as well?

Bye!

---

### Post by candyoff on 2006-09-12
It failed in this stage

```
root@ed-laptop:/home/ed# hcitool scan
Scanning ...
        00:0B:0D:xx:04:xx       HOLUX GPSlim236

```

```
root@ed-laptop:/home/ed# sdptool browse 00:0B:0D:xx:04:xx
Failed to connect to SDP server on 00:0B:0D:xx:04:xx: Connection timed out

```

Wondering why?

I have tried "sdptool browse" with my Nokia N70 and tons of info come out. 
Wondering what was the problem. 
And thanks for the guide!

REgards

---

### Post by candyoff on 2006-09-12
solved the problem 
i typed "sdptool browse" for 2 times
it just work!

Regards

---

### Post by cosine7 on 2006-09-14
I can get /dev/rfcomm4 up and running but none of the gps software will read any thing. Do you have to worry about baud rates or does gpsd do all that for you? Other wise i might just have crap reception on my gps. Will xgps, just have nothing if it can not see enought satellites? Any how i'm using a ASUS BT-100 if anyone has had any luck.

---

### Post by Cannaregio on 2006-11-11
Everything seems ok, but, like frankuzzo, I manage to have my gps bt listed while scanning, but then on the following browse command I get nothing. It just says
> sdptool browse 00:02:78:0A:4E:E9
Browsing 00:02:78:0A:4E:E9 ...
and then I'm back to the prompt.

What am I doing wrong?

---

### Post by Cannaregio on 2006-11-26
Turns out now it works, despite the fact that the browsing still does not give any answer from the unit.
For me it works like this

1) sudo hcitool scan (find unit)
2) sudo sdptool browse 00:00:00:00:00:00 (whatever it is)
3) sudo rfcomm release 0 (very important for me)
4) sudo rfcomm connect 0
...connected /dev/rfcomm0 to 00:00:00:00:00:00 (whatever)
...Press CTRL-C for hangup

and then on a separate terminal

5) sudo gpsd /dev/rfcomm0
6) sudo xgps

(of course rfcomm.conf is configured)

---

### Post by dotsi on 2007-02-14
You may try using sdptool **records** instead of browse. It worked for me.

Well, I still get nothing. xgps says "no data arriving".

Has anyone had the same problem and found a solution for it?

EDIT: solved by rebooting the computer

---

### Post by rklauco on 2007-03-25
Great How-to, worked almost smoothly.
Just, before step 3 I had to restart the bluetooth service in order to create the /dev/rfcomm4 device.
Thanks for the effort.

---

### Post by savantelite on 2007-05-03
Is there certain gps units that work better in ubuntu than others. I would like to buy one

---

### Post by REDISISTone.nl on 2007-06-11
Is there someone that got tips on buying a GPS device for ubuntu (feisty)

---

### Post by rklauco on 2007-06-11
Well, I had 3 different and all worked perfectly, without any problem.
1. some Nokia, don't remember exact name, but it is still present on the market
2. MSI StarFinder SF200, have 2 of them, works great
3. i-Tec, but again, no specific device description, I had it only for 3 days, tested and worked even better than the rest.
According my opinion, all the bluetooth devices available on market these days work without any problem using this how-to.

---

### Post by alek66 on 2007-06-17
Is there a way to run first**  rfcomm connect X** before any gps program, automatically?

---

### Post by Cosmofan on 2007-07-16
I'm doing exactly as it's described in the how-to. But I've got the problems on xgps stage - it shows nothing, NO FIX - smth like this. But, when I start gpsdrive without gpsd - everything works clear. I'd like to overcome this. My GPS reciever is BT-338. Could anybody help me?

---

### Post by jamb on 2007-07-18
> **Cosmofan said:**
> I'm doing exactly as it's described in the how-to. But I've got the problems on xgps stage - it shows nothing, NO FIX - smth like this. But, when I start gpsdrive without gpsd - everything works clear. I'd like to overcome this. My GPS reciever is BT-338. Could anybody help me?

I assume that your Bluetooth GPS is UsGlobalsat. I had a similar problem (still have) with BU-353 (which is USB GPS). I'm using gpsd and monitor the fix with xgps but can not fix position.

May I suggest that you try to post on there support forum. 

[http://www.usglobalsat.com/forum/]("http://www.usglobalsat.com/forum/")

Includes some error logs and as much info you can, since they try to handle all systems...

---

### Post by fdimmling on 2007-10-27
I have problems to get my BT-GPS8 bluetooth GPS receiver to work in Gutsy, steps were
fd@fd-laptop:~$ hcitool scan
Scanning ...
        00:0D:B5:81:FE:6A       BT-GPS8 JENTRO

fd@fd-laptop:~$ sudo sdptool browse 00:0D:B5:81:FE:6A
Browsing 00:0D:B5:81:FE:6A ...
fd@fd-laptop:~$

fd@fd-laptop:~$ sudo sdptool records 00:0D:B5:81:FE:6A
Service Name: GPS OUTPUT
Service RecHandle: 0x10000
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100

fd@fd-laptop:~$ 

[Solution] I made a mistake when copying the MAC address of the GPS device to rfcomm.conf. Now everything works fine.
I am using the hcid.conf from this thread, edited /etc/default/gpsd to make the daemon start at boottime,  and the device is automatically found by gpsdrive. Great!!! 

Friedrich

---

### Post by dysolve on 2007-11-18
i seem to have hit a snag, bluez-pin does not seem to be in the repos anymore and any searching i have done has told me thats its obsolete. when i try spdtool ......... it just tells me that its not available.. that must be part of bluez-pin.. where do i got from here

---

### Post by daller on 2007-11-20
If gpsdrive says "Not enought satelites found!" (translated from danish) - Does that mean that I have a connection to the receiver?

Under "GPS info" it says 0/0

How do I check if the connection is ok?

I got this when running rfcomm:

elav1@elav1-desktop:~$ sudo rfcomm connect 4
Connected /dev/rfcomm4 to 00:0A:3A:1F:C9:C9 on channel 1
Press CTRL-C for hangup

---

### Post by Piffer on 2008-03-26
Hopefully I can find a newer thread or a list of supported GPS devices.

Anyway, if you aren't getting any GPS signal etc, make sure that you're not deep down in a building somewhere, as that will easily prevent the GPS antenna from receiving signals.

---

### Post by f03el on 2008-10-04
My success story :)

I tried this howto to connect my Globalsat BT-359S, and I got to the step where rfcomm has connected and says "Press CTRL-C for hangup". However there was no real connection according to gpsd. Pressing ctrl-c didn't kill the connection (the LED on my BT-dongle continued shining), and just caused rfcomm to hang.

A new try with a fresh (default) hcid.conf didn't help either, but then I started to suspect the line 'passkey "1234";'. Trying to connect my phone to the receiver using that code resulted in hanging the phone, so apparently an incorrect code could hang the connecting unit.

Changing 'security user;' -> 'security none;' did the trick, since my bluetooth device don't want any pin code.

---

### Post by daved2424 on 2009-02-12
Great method, worked fine for me. I am trying to adapt it to work with this tutorial I found [here]("http://tjworld.net/wiki/Linux/Ubuntu/GoogleEarthPlusRealTimeGPS") that allows you to track your position with Google Earth.

The only problem I am finding is configuring the python script to use the bluetooth GPS as the serial port instead of the PCMCIA card that it was written for. Does anyone have any ideas as to how it should be changed to use rfcomm4?

---

### Post by rklauco on 2009-02-12
WOW, I am now playing with McGuider on Ubuntu 8.10, amazing software!!!

---

### Post by Sebjectivist on 2009-05-08
> **rklauco said:**
> WOW, I am now playing with McGuider on Ubuntu 8.10, amazing software!!!

Tell me more please. McGuider is software for windows mobile / symbian no? I'm looking for an offline gps route planner application that works with ubuntu. preferably a native application, but anything will do. I'm busy getting [Navit]("http://www.navit-project.org/") to work. I also found [Polnav]("http://www.polstargps.com/Polstar_Navigation_Software_PolNav.html") as a seemingly suitable - but commercial - solution.. Are these the creme the la creme of linux navigation software?

---

### Post by rklauco on 2009-05-11
> **Sebjectivist said:**
> Tell me more please. McGuider is software for windows mobile / symbian no? I'm looking for an offline gps route planner application that works with ubuntu. preferably a native application, but anything will do. I'm busy getting [Navit]("http://www.navit-project.org/") to work. I also found [Polnav]("http://www.polstargps.com/Polstar_Navigation_Software_PolNav.html") as a seemingly suitable - but commercial - solution.. Are these the creme the la creme of linux navigation software?
McGuider (originaly Sygic Drive, [http://www.sygic.com](http://www.sygic.com)) is for lots of the platforms. Thanks to their modular code the app can be simply ported to various OSes - as far as I know, they have version for Symbian, Symbian UIQ, Symbian touchscreen, Windows mobile, Windows Mobile PRO, Windows CE and iPhone.
Unofficialy they do have the Linux version (runs pretty fast also on the slowest eeePC with eeebuntu on it). Unfortunately, they only sell the Linux version to OEM distributors and minimum amount is 1000 licenses :-(
The app is great, response is pretty fast, easy to operate and the map coverage is excelent.
Sorry I can't give you better answer. But I can try to provide some screenshots if wanted.

---

### Post by Keith_Beef on 2009-06-06
Great, Nino. Thanks for putting this together.

It took a few tries, and it isn't 100% reliable for me, but it seems right...
The hcitool scan step sometimes works, sometimes doesn't... I've not figured out why. The GPS puck is right next to the computer I'm using, and so is my phone. Sometimes neither device shows up, sometimes only the phone, sometimes both the phone and the puck. 

When it works, here's what I see.

```
$ hcitool scan
Scanning ...
	00:11:22:33:44:55	Nokia 5800
	00:11:22:33:44:66	TeleNav GPS
```

Browing never works:
```
$ sdptool browse 00:11:22:33:44:66
Browsing 00:11:22:33:44:66 ...
```

Showing the records can sometimes work... there is a loooong pause between showing the base offset and the prompt coming back.
```

$ sdptool records 00:11:22:33:44:66
Service Name: BT-GPS COM Port
Service RecHandle: 0x10000
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100

```


I made the entry in rfcomm4 as you described.

```
rfcomm4 {
        bind yes;
        device 00:11:22:33:44:66;
        channel 1;
        comment "Serial Port";
        }
```

I start gpsd and create the rfcomm device.
```
$ rfcomm connect 4
Connected /dev/rfcomm4 to 00:11:22:33:44:66 on channel 1
Press CTRL-C for hangup
```



The I can start xpsd and gpsdrive. Yippee!

K.

---

### Post by Thalarse on 2009-06-25
Unfortunately this doesn't seem to work for me. :(

The gps receiver shows up on hcitool scan as "00:0A:3A:25:7E:BD BT GPS" 
But when I do the sdptool browser I get "Browsing 00:0A:3A:25:7E:BD ..." And that's it. 

I fudged the rfcomm4 thing and "rfcomm connect 4" claims to connect. But "gpsd /dev/rfcomm4" gives me no output. Is it supposed to confirm the command or something? Then trying xgps I get a status of "unknown", and other gps programs don't find the device either. 

The gps receiver connects to the phone without a fuss, and the phone responds to sdptool browse with a whole bunch of info. 

I think I've got the wrong channel, perhaps, but I'm not sure. I don't know how to get the info out of the bluetooth receiver any other way.

---

### Post by Blackworm on 2009-07-07
I think that your problem is that the gpsd daemon doesn's starts on startup. Open the gpsd config file with:

```
sudo gedit /etc/default/gpsd
```

then modify the file like this:

```
START_DAEMON="yes"
DAEMON_OPTS=""
DEVICES=""
USBAUTO="false"
```

save and reboot. After you successfully connect your GPS with rfcomm connect 4, type:

```
sudo gpsd /dev/rfcomm4
```

and that's it. Start xgps to verify your antenna. Don't forget to release the rfcomm4 device when you turn off your GPS, or next time it will return a "device or resource busy" error.;)

---

### Post by Glitch0r on 2009-07-09
> **Blackworm said:**
> I think that your problem is that the gpsd daemon doesn's starts on startup. Open the gpsd config file with:

```
sudo gedit /etc/default/gpsd
```

then modify the file like this:

```
START_DAEMON="yes"
DAEMON_OPTS=""
DEVICES=""
USBAUTO="false"
```

save and reboot. After you successfully connect your GPS with rfcomm connect 4, type:

```
sudo gpsd /dev/rfcomm4
```

and that's it. Start xgps to verify your antenna. Don't forget to release the rfcomm4 device when you turn off your GPS, or next time it will return a "device or resource busy" error.;)
Thanx a million ... this got it to work for me ...

---

### Post by lotus49 on 2009-11-08
I have two problems with this plus one annoyance.

Firstly, this does work for me but I have to run the

$ rfcomm connect 0 

command, then kill it with ^C and then run it again.  It never works the first time and always works the second time.  Any suggestions?

However, running gpsd automatically fills up my logs with crap if the gps receiver is off.  After about three hours I have >3GB of gpsd warnings in two separate log files.  Considering that my laptop has a tiny 8GB SSD, this is a serious problem so I have to start gpsd manually.

Is there some way of starting all this automatically (this is the annoyance) so that the rfcomm connect command and then gpsd are run when the gps receiver is on and in range?

---

### Post by Whigu on 2010-02-24
> **Thalarse said:**
> Unfortunately this doesn't seem to work for me. :(

The gps receiver shows up on hcitool scan as "00:0A:3A:25:7E:BD BT GPS" 
But when I do the sdptool browser I get "Browsing 00:0A:3A:25:7E:BD ..." And that's it. 


Try:
sdptool browse --l2cap 00:11:22:33:44:55

That worked with my GPS when sdptool browser gave that same what you said.

> 
I think I've got the wrong channel, perhaps, but I'm not sure. I don't know how to get the info out of the bluetooth receiver any other way.

Check what that sdptool browse -l2cap says and try that channel.

I had problems with backtrack linux and nokia bluetooth gps and I wrote short "tutorial" about that: [http://www.petrilopia.net/wordpress/software/nokia-ld-3w-bluetooth-gps-on-backtrack-linux/](http://www.petrilopia.net/wordpress/software/nokia-ld-3w-bluetooth-gps-on-backtrack-linux/) maybe it helps you?

---

### Post by Gorlist on 2010-05-01
resurrecting a bit of old thread here - strange problem, blue tooth gps dongle is connected and working fine, xgps and gpspipe -r both receive data and function. However im finding no other program seems to want to work, specificly GmapCatcher and gpsdrive... Both appear to indicate the gps is unavailable but I can't find any further information on it.

This is how im currently starting the gps:

```
sudo service gpsd stop
sudo rfcomm connect 4
sudo gpsd -D 5 -nN /dev/rfcomm4
```

Followed all of the normal guides, the only thing I can seem to remember is in 9.10 having a similar problem (now running 10.04), and perhaps todo with permissions. Other than that im at a loss.

---

### Post by Ixtao on 2010-05-07
I followed the instructions in this guide but didn't get data from the gps although connection was established. xgps reported "gpsd stopped sending data" after a while.

When I made the connection with the commands Gorlist describes it works with both xgps and Navit!

---

### Post by shrauf on 2010-05-22
Hi! Thanks for the great howto!
I got stuck at a late step:
```
rfcomm connect 4
```did not work (permission denied), but
```
sudo rfcomm connect 4
```did work.
So I used the latter plus this. (Idea from [https://answers.launchpad.net/ubuntu/+source/bluez/+question/70933](https://answers.launchpad.net/ubuntu/+source/bluez/+question/70933))
```
 chown me:me /dev/rfcomm4
```No error here.
```
gpsd /dev/rfcomm4
```The command seems to complete without any error.

However, xgps displays nothing; gpsdrive says "no gps".
Any ideas?

---

### Post by Davez69gto on 2010-07-01
I think i'm beating a goat w/ an old stone or horse with a stick or however you say it but I figured I would give it a try.  

So I went through many different tutorials to setup all my bluetooth stuff.  Well I have a connection now.

With: ```
sudo cat /etc/rfcomm4
``` I get stuff like 
```
$GPGGA,224017.000,3859.6387,N,07655.5266,W,2,04,5.8,16.5,M,-33.5,M,0.8,0000*71
$GPRMC,224017.000,A,3859.6387,N,07655.5266,W,0.00,114.17,010710,,,D*75
$GPVTG,114.17,T,,M,0.00,N,0.0,K,D*0A
$GPGGA,224018.000,3859.6388,N,07655.5254,W,2,04,5.8,15.8,M,-33.5,M,0.8,0000*7E
$GPRMC,224018.000,A,3859.6388,N,07655.5254,W,0.00,114.17,010710,,,D*74
$GPVTG,114.17,T,,M,0.00,N,0.0,K,D*0A
$GPGGA,224019.000,3859.6389,N,07655.5249,W,2,04,5.8,15.4,M,-33.5,M,0.8,0000*7E
$GPRMC,224019.000,A,3859.6389,N,07655.5249,W,0.00,114.17,010710,,,D*78
$GPVTG,114.17,T,,M,0.00,N,0.0,K,D*0A
$GPGGA,224020.000,3859.6391,N,07655.5241,W,2,04,5.8,14.8,M,-33.5,M,1.8,0000*79
$GPGSA,A,3,07,13,11,08,,,,,,,,,7.9,5.8,5.4*3D
$GPGSV,3,1,11,07,79,213,36,19,53,047,,08,52,311,26,11,43,165,23*76
$GPGSV,3,2,11,28,30,292,19,03,23,053,22,13,12,201,30,06,11,052,17*72
$GPGSV,3,3,11,24,10,039,18,17,06,231,21,48,21,243,34*43
$GPRMC,224020.000,A,3859.6391,N,07655.5241,W,0.00,114.17,010710,,,D*73
$GPVTG,114.17,T,,M,0.00,N,0.0,K,D*0A
$GPGGA,224021.000,3859.6392,N,07655.5233,W,2,04,5.8,14.3,M,-33.5,M,2.8,0000*76
$GPRMC,224021.000,A,3859.6392,N,07655.5233,W,0.00,114.17,010710,,,D*74
$GPVTG,114.17,T,,M,0.00,N,0.0,K,D*0A

```
 
So i'm obviously getting data in but none of the programs can read it (xgps, tangogps...)

I'm hoping I missed something simple.  Anyone have any ideas?

---

### Post by gvoima on 2010-07-01
This is correct raw gps (NMEA) data that all gps-units receive. So search for a program to parse that.

i.e. all programs use this through their own or a 3rd party api.

Use keyword NMEA in the ubuntu software center. I don't have any gps-units to test atm. :|

---

### Post by mmaacc11 on 2010-07-31
Hi. I'm new to forum and Ubuntu. I went to all the steps from this howto. Many thanks for that.
At the end I got some mess coming form the GPS. xgps tells that it's connected at 4800bps. I'm sure that my GSpace GS-R238 works at 38400. How to make rfcomm connect at correct speed?
M.

---

### Post by mmaacc11 on 2010-08-01
I think I got it!
Something has happened to GPS itself. I did factory reset on it and it works fine now.
Thx.

---

### Post by mattbrook on 2010-08-01
Ok. This is the solution I have for Ubuntu 10.04 LTS through VMWare Fusion 2.0.7 on a MacBook Pro with a Globalsat BT-338 bluetooth unit.

*Download bluez-utils, gpsd and gpsd-clients*

sudo apt-get install bluez-utils
sudo apt-get install gpsd-clients
sudo apt-get install gpsd

*Then*

sudo gedit /etc/bluetooth/hcid.conf

*This is what my hcid.conf looks like. Paste it in and save it*

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluepin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "My Laptop Ubuntu";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

*Save it. I then rebooted as the init.d restart command didn't work*

*Turn the GPS unit on*

hcitool scan

*Note the MAC address of the bluetooth unit*

sdptool search SP

*Note the channel number*

sudo gedit /etc/bluetooth/rfcomm.conf

*Paste the following at the end of the file, and save the file.*

rfcomm4 {
        bind yes;
        device < GPS MAC ADDRESS>;
        channel <CHANNEL NUMBER>;
        comment "Serial Port";
        }

*I then found that to connect reliably switch the order of gpsd and rfcomm commands worked*

sudo gpsd -b /dev/rfcomm4
sudo rfcomm bind rfcomm4

*Then run cgps or xgps or whatever you have to look at the GPS data*

*To disconnect*

sudo killall gpsd
sudo rfcomm release 4

*To reconnect*

sudo gpsd -b /dev/rfcomm4
sudo rfcomm bind rfcomm4

***And that only took about 18 hours of pissing about and I've had to type it in twice because this forum timed out my login the first time. So I hope someone finds it useful.***

**PS. Thanks to NinoCass for the bulk of my solution.**

---

### Post by mattbrook on 2010-08-01
*Here's a sample shell script to start the GPS system once you've done all the other stuff*

#!/bin/bash

echo "Setting up gpsd..."
sudo gpsd -b /dev/rfcomm4
wait
echo "Done."

echo "Connecting to GPS unit..."
sudo rfcomm bind rfcomm4
wait
echo "Done."

*And the one to stop it again*

#!/bin/bash

echo "Stopping gpsd..."
sudo killall gpsd
wait
echo "Done."

echo "Disconnecting GPS unit..."
sudo rfcomm release 4
wait
echo "Done."

---

### Post by mattbrook on 2010-08-04
Getting GPSDrive to work in 10.04

The version in Synaptic Package Manager didn't pick up the GPS.

This one does.

[http://download.osgeo.org/livedvd/data/gpsdrive/lucid/]("http://download.osgeo.org/livedvd/data/gpsdrive/lucid/")

Thanks.

---

### Post by miocappo on 2010-08-07
I'am using ubuntu 10.04. I can't download and install "bluez-pin". Is there another solution?

Regards

---

### Post by mattbrook on 2010-08-07
> **miocappo said:**
> I'am using ubuntu 10.04. I can't download and install "bluez-pin". Is there another solution?

Regards
I'm not sure, my GPS unit defaults to '0000' as the pin, I never get asked for one.
I couldn't find bluez-pin either so didn't install it.

Might be worth trying to use the bluetooth GUI. There should be a bluetooth symbol in the toolbar at the top of the screen.

Otherwise in hcid.conf, if you look at it, it looks like you can try to set an option to get it to ask for a pin. 'security user' I'd try that.

---

### Post by miocappo on 2010-08-08
> **mattbrook said:**
> I'm not sure, my GPS unit defaults to '0000' as the pin, I never get asked for one.
I couldn't find bluez-pin either so didn't install it.

Might be worth trying to use the bluetooth GUI. There should be a bluetooth symbol in the toolbar at the top of the screen.

Otherwise in hcid.conf, if you look at it, it looks like you can try to set an option to get it to ask for a pin. 'security user' I'd try that.

ok, Now it works perfect!

Thanks!

---

### Post by sv8bur on 2010-12-16
Hi all

I am using Kubuntu 10.04 and my bluetooth GPS is 'Clip-On BT GPS'
After  giving the command 'sdptool browse'
I got this 'Browsing 00:11:A5:C0:53:35 ...' and nothing else
and
After giving the command rfcomm connect 4
I got this 'Can't open RFCOMM device: Permission denied'
Why
Thank you very much

---

### Post by Fitch on 2012-01-19
Is this thread still being watched?

I've perused and done everything over the 5 pages and everything seems to work except the last part.
All I get when I run gpsd is:

{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/rfcomm4","activated":1326983699.84,"native":0,"bps":115200,"parity":"N","stopbits":1,"cycle":1.00}]}

over and over again.

---

### Post by ttakacs on 2012-02-12
> **Fitch said:**
> Is this thread still being watched?

I've perused and done everything over the 5 pages and everything seems to work except the last part.
All I get when I run gpsd is:

{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/rfcomm4","activated":1326983699.84,"native":0,"bps":115200,"parity":"N","stopbits":1,"cycle":1.00}]}

over and over again.

What worked for me was setting up gpsd to start as a daemon by running (as root) *dpkg-reconfigure gpsd*. Starting gpsd by giving the command *gpsd /dev/rfcomm4* in the root terminal was not working for me.

(Ubuntu 10.04. My BT receiver is Holux M-1200.)

---

