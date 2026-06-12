---
title: "Firewire Audiofire4 on MacBook4.1 Ubuntu 9.10"
date: 2009-11-15
forum: Ubuntu Studio
---

### Post by beauman on 2009-11-15
Hi!

I am having problems with my external sound card.

I installed UbuntuStudioControls on my standard Ubuntu 9.10 installation and followed this [walk thru]("https://help.ubuntu.com/community/FireWire").

Using the parameters suggested in the howto, I tried starting jackd from within qjackctl. But apparently jackd can't be started (sorry for the german output, the call to jackd is in english):

```
20:09:08.041 Steckfeld deaktiviert.
20:09:08.045 Statistik zurückgesetzt.
20:09:08.065 Schaubild der ALSA-Verbindungen geändert.
20:09:08.382 ALSA-Verbindung geändert.
20:09:16.151 Startup script...
20:09:16.152 artsshell -q terminate
sh: artsshell: not found
20:09:16.554 Startup script terminated mit Rückgabewert = 32512.
20:09:16.554 JACK startet...
20:09:16.554 /usr/bin/jackd -dfirewire -dhw:0 -r44100 -p128 -n2
20:09:16.556 JACK wurde mit PID = 3821 gestartet.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
06719919294:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
20:09:16.796 JACK wurde angehalten erfolgreich.
20:09:16.797 Post-shutdown script...
20:09:16.798 killall jackd
jackd: no process found
20:09:17.206 Post-shutdown script terminated mit Rückgabewert = 256.
20:09:18.665 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Overall operation failed. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.
```

I googled a bit the www and [found this thread here]("http://ubuntuforums.org/showthread.php?t=1008723"). I didn't understand everything, but what I understood was, that it is most likely either a version problem of jackd or a missing permission.

When I start ffado-dbus-server, it complains about a firmware version that is not recent enough (at mark 05871420126):

```
xxx@LosBastardos:~$ ffado-dbus-server 
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- www.ffado.org
Version: 1.999.43
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

05871279754:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
05871284556: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
05871291164: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871292417: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871293669: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871294924: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871296182: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871352802: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871354056: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871355233: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871356531: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871357891: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000400, length = 256
05871418387: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05871418462: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 5254 (0x00001486)
05871418496: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 2804 (0x00000AF4)
05871418514: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
05871418538: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire4
05871418553: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
05871418576: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
05871418590: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
05871418706: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05871418727: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 5254 (0x00001486)
05871418751: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 2804 (0x00000AF4)
05871418768: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
05871418789: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire4
05871418804: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
05871418826: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
05871418840: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
05871419156: Debug (devicemanager.cpp)[ 594] discover: driver found for device 0
05871419262: Debug (Configuration.cpp)[ 163] showSetting:   Group: (null)
05871419295: Debug (Configuration.cpp)[ 185] showSetting:     vendorid = 5254 (0x00001486)
05871419311: Debug (Configuration.cpp)[ 185] showSetting:     modelid = 2804 (0x00000AF4)
05871419334: Debug (Configuration.cpp)[ 209] showSetting:     vendorname = Echo
05871419349: Debug (Configuration.cpp)[ 209] showSetting:     modelname = AudioFire4
05871419370: Debug (Configuration.cpp)[ 185] showSetting:     driver = 2 (0x00000002)
05871419385: Debug (Configuration.cpp)[ 209] showSetting:     mixer = AudioFireMixer
05871419406: Debug (Configuration.cpp)[ 185] showSetting:     xmit_max_cycles_early_transmit = 2 (0x00000002)
05871420126: Error (fireworks_device.cpp)[ 175] discoverUsingEFC: Firmware version 4.7 (rev 0) not recent enough. FFADO requires at least version 4.8 (rev 0).
05871420161: Error (devicemanager.cpp)[ 606] discover: could not discover device
05871420235: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
05871420259: Debug (devicemanager.cpp)[1184] showDeviceInfo: ===== Device Manager =====
05871420274: Debug (Element.cpp)[ 121] show: Element DeviceManager
05871420293: Debug (devicemanager.cpp)[1192] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
05871420389:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
05871430529:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
05871430578: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
^C05955884519: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
05955884578: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
05955884592:  (ffado-dbus-server.cpp)[ 339] main:  Stopping...
05956085492:  (ffado-dbus-server.cpp)[ 353] main:  Bye.
05956085527: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns
```

So I am puzzled. Do I have to update the sound card? 

Version of jackd:

```
jackd --version
jackd version 0.116.1 tmpdir /dev/shm protocol 24
```

I have a bit experience with jack, but I never worked with firewire under linux. By the way, the hardware works fine, if I boot into Mac OS, it works.

Any help appreciated!

---

### Post by mudfly on 2009-11-15
I was having a similar issue as you, so I did a few google searches. One of which brought me to this thread. I noticed nobody answered you and the post was from 6 hours ago, so I thought I would post what I found.

In the end I only had to change the permissions of my firewire interface and I was up and going.

'sudo chmod 777 /dev/raw1394'

Here is the thread that got me running again.

[http://ardour.org/node/3117](http://ardour.org/node/3117)

Good Luck!

---

### Post by beauman on 2009-11-16
Ok, thx, I will try that tonight. Just out of curiosity, do you know what firmware version ffado-dbus-server is talking about?

---

### Post by AutoStatic on 2009-11-16
> **mudfly said:**
> I was having a similar issue as you, so I did a few google searches. One of which brought me to this thread. I noticed nobody answered you and the post was from 6 hours ago, so I thought I would post what I found.

In the end I only had to change the permissions of my firewire interface and I was up and going.

'sudo chmod 777 /dev/raw1394'

Here is the thread that got me running again.

[http://ardour.org/node/3117](http://ardour.org/node/3117)

Good Luck!The UbuntuStudio Controls should take care of this, check Step 3 of the [howto]("https://help.ubuntu.com/community/FireWire"). If ls -al /dev/raw1394 does not match the output mentionned in the howto you could try setting it manually. chmodding will most likely not survive through reboots or updates.

---

### Post by mudfly on 2009-11-16
> **beauman said:**
> Ok, thx, I will try that tonight. Just out of curiosity, do you know what firmware version ffado-dbus-server is talking about?

I am not familiar with that interface, but I did a quick search and it looks to me if you install the 4.8 driver under OSX it will upgrade the firmware on the AudioFire for you.

Check for the driver here, 
[http://www.echoaudio.com/Downloads/Drivers.php](http://www.echoaudio.com/Downloads/Drivers.php)

And make sure to read the readme.

@AutoStatic thanks for the info.

---

### Post by beauman on 2009-11-16
I got it working! Tested it with ardour. Nice!

I indeed had to update the firmware. Also, I had to install a real time kernel. Just for the record:

```
sudo apt-get update
sudo apt-get install linux-rt

``` 

So thanks to mudfly who encouraged me to update. And thx to everybody else!

Some remarks: 
  [LIST]
[*]I had to be root to start jackd with rt-priority. 
[*]Can I use the device without jack? Like a normal sound card?
[*]If I like to chat about music production on ubuntu some day, is this the right place here?
[/LIST]

Regards,
beauman

---

### Post by AutoStatic on 2009-11-16
> **beauman said:**
> I got it working! Tested it with ardour. Nice!

I indeed had to update the firmware. Also, I had to install a real time kernel. Just for the record:

```
sudo apt-get update
sudo apt-get install linux-rt

``` 

So thanks to mudfly who encouraged me to update. And thx to everybody else!

Some remarks: 
  [LIST]
[*]I had to be root to start jackd with rt-priority. 
[*]Can I use the device without jack? Like a normal sound card?
[*]If I like to chat about music production on ubuntu some day, is this the right place here?
[/LIST]

Regards,
beauman

1. [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
This will allow you to use JACK with realtime priority as a normal user

2. No, you need FFADO to be able to use it and FFADO only works with JACK

3. Yup, at least, that's what I think this subforum is intended for :)

---

### Post by kayosiii on 2009-11-16
> 
  [LIST]
[*]Can I use the device without jack? Like a normal sound card?
[/LIST]


You cannot use it without jack... However you can use it as a normal soundcard for most purposes if you can get your desktop apps to use jack.
This is quite difficult currently on ubuntu as a lot of applications that can use jack as an audio output are compiled without that functionality. We are hoping that this desision will be reversed for Lucid Lynx. It is generally easier to set up KDE this way than gnome as phonon (the desktop sound system) runs on top of jack very well.

---

### Post by mudfly on 2009-11-16
Great, good to hear Beauman!

Another forum you might find useful for Linux Pro-Audio is,
[http://www.linuxmusicians.com/](http://www.linuxmusicians.com/)

---

