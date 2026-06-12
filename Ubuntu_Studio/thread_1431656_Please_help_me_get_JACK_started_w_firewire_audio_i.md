---
title: "Please help me get JACK started w/ firewire audio interface"
date: 2010-03-16
forum: Ubuntu Studio
---

### Post by mirakus on 2010-03-16
Hi.  I'm trying to get an Echo Audiofire 4 audio interface/sound card to work on Ubuntu Studio 9.10.  I made an original attempt with my old install of 8.04 LTS, but after many failures decided to install Studio in the hopes it would magically take care of things for me.  That didn't happen.  ;o)  After days on end of googling with little success, I've decided maybe someone here can help me, based on the kind suggestion from a friend that maybe it was time to get some outside help.  Please forgive my excessive writing; I don't post on forums a whole lot!  Here is some system information:
 

 Ubuntu Studio 9.10  
 Pentium 4 2.97 ghz
 2 GB DDR RAM
 PCI Firewire Expansion card  
 

 Here is the lspci info on the Firewire card:
 01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
 

 My install of Ubuntu Studio was clean (meaning no audio apps were installed, which was strange since I selected to do so), but anyway, I downloaded the code for libffado (2.0.0) and also JACK (0.118 from SVN), and a release of qjackctl (0.3.6).
 

 Here are all of the steps I performed:
 
[LIST=1]
[*]verified driver for firewire card     (libraw1394) was on the system...it was
[*]made an addition to /etc/modules     so raw1394 driver would autoload on boot
[*]changed the udev rules to change     the raw1394 device group ownership to audio
[*]added my user account to the audio     group
[*]built and installed libffado-2.0
[*]built and installed JACK 0.118     from SVN
[*]built and installed qjackctl     (0.3.6)
[/LIST]
 

 Additional details:  
 
[LIST]
[*]Performed standard build of     libffado &#8211; got the warnings about pyqt being missing and therefore     mixer would not be built
[*]Built JACK with only firewire     support, disabled OSS and freebob support (for some reason, alsa was     not automatically enabled which I thought it would be, but I didn't     think I would be using it for this device)
[/LIST]
 

 Loaded modules:
 lsmod | grep 1394 
 ohci1394               30308  0  
 raw1394                25692  0  
 ieee1394               87284  2 ohci1394,raw1394
 

 If I run ffado-test ListDevices, my device is recongized:
 ~$ ffado-test ListDevices 
 ----------------------------------------------- 
 FFADO test and diagnostic utility 
 Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org") 
 Version: 2.0.0 
 (C) 2008, Daniel Wagner, Pieter Palmers 
 This program comes with ABSOLUTELY NO WARRANTY. 
 ----------------------------------------------- 
  
 === 1394 PORT 0 === 
   Node id  GUID                  VendorId     ModelId   Vendor - Model 
    0       0x000000000000034f  0x00000000  0x00000000   Linux - ohci1394  -  
    1       0x00148602c9969982  0x00001486  0x00000AF4   Echo Digital Audio - AudioFire4 
 no message buffer overruns 
 

 When I attempted to run jackd, I got errors.  Based on the messages, I added these lines to /etc/security/limits.conf:
 @audio          -       rtprio          100 
 @audio          -       nice            -10
 

 Running JACK from the command line:
  jackd -r -d firewire 
 jackd 0.118.3 
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others. 
 jackd comes with ABSOLUTELY NO WARRANTY 
 This is free software, and you are welcome to redistribute it 
 under certain conditions; see the file COPYING for details 
  
 no message buffer overruns 
 JACK compiled with System V SHM support. 
 loading driver .. 
 libffado 2.0.0 built Mar 16 2010 19:59:58 
 firewire ERR: Error creating FFADO streaming device 
 cannot load driver module firewire 
 no message buffer overruns 
 

 Here is the JACK output with only jackd -d firewire:
 john@jstudio:/etc/security$ jackd -d firewire 
 jackd 0.118.3 
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others. 
 jackd comes with ABSOLUTELY NO WARRANTY 
 This is free software, and you are welcome to redistribute it 
 under certain conditions; see the file COPYING for details 
  
 no message buffer overruns 
 JACK compiled with System V SHM support. 
 cannot lock down memory for jackd (Cannot allocate memory) 
 loading driver .. 
 JACK: unable to mlock() port buffers: Cannot allocate memory 
 JACK: unable to mlock() port buffers: Cannot allocate memory 
 libffado 2.0.0 built Mar 16 2010 19:59:58 
 firewire ERR: Error creating FFADO streaming device 
 cannot load driver module firewire 
 no message buffer overruns 
 

 Here are the results when running JACK from qjackctl, with every setting on the left unchecked except for verbose messages:  
 jackd 0.118.3
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 getting driver descriptor from /usr/local/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/local/lib/jack/jack_net.so
 getting driver descriptor from /usr/local/lib/jack/jack_firewire.so
 [COLOR=#999999]21:40:24.452 JACK was started with PID=24595.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 server `default' registered
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 start poll on 3 fd's
 loading driver ..
 new client: firewire_pcm, id = 1 type 1 @ 0x9538230 fd = -1
 new buffer size 1024
 resizing port buffer segment for type 0, one buffer = 4096 bytes
 resizing port buffer segment for type 1, one buffer = 4096 bytes
 libffado 2.0.0 built Mar 16 2010 19:59:58
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 starting server engine shutdown
 freeing shared port segments
 server thread back from poll
 stopping server thread
 last xrun delay: 0.000 usecs
 max delay reported by backend: 0.000 usecs
 freeing engine shared memory
 max usecs: 0.000, engine deleted
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 no message buffer overruns
 [COLOR=#999999]21:40:24.695 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]21:40:24.695 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:40:24.697 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]21:40:25.108 Post-shutdown script terminated with exit status=256.[/COLOR]
 

 To conclude, I think I have a couple of problems here, but the main issue is that I have no other way to interact with my audio device (that I'm aware of), and I would like to get it working.  Although these error messages are pretty informative, I don't know quite what to make of them at this point.  I've noticed that firewire audio information for linux is pretty sparse around the www, with the exception of a lot of really common problems which I thought I had gotten past.  Thanks for taking the time to read this, and if anyone could provide me with any pointers on this situation, I would be greatly appreciative!  Thanks again!

---

### Post by fedexnman on 2010-03-16
only thing i can tell you to do is google ubuntu studio prep, follow those steps closely, there is also a link for firewire devices on that page, i have a echo audifire4 and have now problems after following these steps.

---

### Post by mirakus on 2010-03-16
After looking at this thread ([http://ubuntuforums.org/showthread.php?t=1327537&highlight=audiofire4](http://ubuntuforums.org/showthread.php?t=1327537&highlight=audiofire4)), I think that the firmware may be at least a part of my issue.  

Here is my output from ffado-dbus-server:
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 2.0.0
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

 Discovering devices...
18393882897: Error (fireworks_device.cpp)[ 175] discoverUsingEFC: Firmware version 3.0 (rev 512) not recent enough. FFADO requires at least version 4.8 (rev 0).
18393882927: Error (devicemanager.cpp)[ 606] discover: could not discover device

I'm going to try updating the firmware on the device and see if that helps...sadly, I don't have a Windows or Mac computer around, which apparently seems the only way to update the firmware!  I'm going to keep looking into though, and will post back here with the results.  Thanks!

---

### Post by fedexnman on 2010-03-17
you maybe able to ship it to echo, or borrow a friends pc or mac to update it , i have windows and a macbook, so maybe thats why i had such good luck;)  there is also a ffado mixer app too, did you download that ?

---

### Post by mirakus on 2010-03-17
Okay...after swapping my new firewire expansion card and Audiofire onto a Windows machine, doing the operation, and putting everything back on this system, JACK is starting!  I may run into other issues, but that was definitely the cause of my FFADO errors.  

If it's of any help to anyone dealing with something like this in the future, run ffado-dbus-server, which is the little app which notified me of my firmware being outdated.  

As far as ffado-mixer goes, I would prefer to build it myself, but for whatever reason, I didn't seem to have the dependencies during the install, and after installing several py-qt packages, I still couldn't get it to build.  If I use the one from the repo's, it will force me to also download a separate ffado lib, which might conflict with my built one.  I'm going to keep messing around and see if I can get it built myself.  

Strangely enough, with all the info on the net about firewire audio on Linux, there wasn't much mentioning of the possibility of the sound card firmware not being current with FFADO.  I'm thinking about writing a tutorial for people struggling with learning to do this.  Hopefully my long, initial post will help someone else, even though the problem was simpler than I thought.  

Thanks everyone!

---

### Post by fedexnman on 2010-03-17
glad you got it working !! i love my echo audiofire4. enjoy man:guitar:

---

