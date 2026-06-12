---
title: "Ubuntu-Studio 9.10 and Firewire - a sad tale..."
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by sjelly on 2009-11-25
I have been trying to get my Echo Audio Firewire 12 working with Ubuntu Studio for about 4-months, firstly with 9.04 and recently with 9.10.

I downloaded 9.10 about a week ago and made a fresh install of the 32-bit variant. During the installation I was only able to install the base system - I could select the applications packages (Audio, Video, etc) but the installation would then fail. Was this because I didn't have a internet connection at the time? I don't know. I was able to install the audio option by selecting the ubuntustudio-audio package in Synaptic Package Manager.

I then did the 5 basic steps outlined at the Ubuntu documentation "FireWire Audio in Ubuntu Studio" page ([https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)). Things seemed to be going just fine. 

I made the following checks and got the following results:

1. sjelly@ubuntu-studio:~$ cat /etc/issue
    Ubuntu 9.10 \n \1

2. sjelly@ubuntu-studio:~$ uname -a
     Linux ubuntu 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux

3. As instructed by a kindly soul on Ubunt-Studio users mailing list I did
     sjelly@ubuntu-studio:~$ sudo chmod 777 /dev/raw1394

4. sjelly@ubuntu-studio:~$ ls -al /dev/raw1394
     crwxrwxrwx 1 root video 171, 0 2009-11-22 16:38 /dev/raw1394

5. sjelly@ubuntu-studio:~$ ffado-test ListDevices
     -----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 1.999.43
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
   Node id  GUID                  VendorId     ModelId   Vendor - Model
    0       0       0x0014860968bc006a  0x00001486  0x00000AF4   Echo Digital Audio - AudioFire12

Finally I came to start qjackctl and this is what I got:

21:28:44.769 Patchbay deactivated.
21:28:44.773 Statistics reset.
21:28:44.823 ALSA connection graph change.
21:28:45.020 ALSA connection change.
21:28:48.791 Startup script...
21:28:48.792 artsshell -q terminate
sh: artsshell: not found
21:28:49.195 Startup script terminated with exit status=32512.
21:28:49.195 JACK is starting...
21:28:49.196 /usr/bin/jackd -R -P70 -t1000 -dfirewire -dhw:0 -r44100 -p128 -n2 -i12 -o12
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
21:28:49.215 JACK was started with PID=2848.
loading driver ..
01024651260:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
21:28:49.533 JACK was stopped successfully.
21:28:49.534 Post-shutdown script...
21:28:49.534 killall jackd
jackd: no process found
21:28:49.946 Post-shutdown script terminated with exit status=256.
21:28:51.232 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I can't figure out how to get beyond this error. It's killing me. I'm no Linux guru, but I can follow instructions. What am I doing wrong? It's got to the point where I'd consider paying someone to help me get this to work!

---

### Post by AutoStatic on 2009-11-25
> **sjelly said:**
> 3. As instructed by a kindly soul on Ubunt-Studio users mailing list I did
     sjelly@ubuntu-studio:~$ sudo chmod 777 /dev/raw1394Hello sjelly, this is not persistent through reboots and can be fixed by following step 3 from the FireWire help page: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

> **sjelly said:**
> 21:28:49.196 /usr/bin/jackd -R -P70 -t1000 -dfirewire -dhw:0 -r44100 -p128 -n2 -i12 -o12Why did you change the Timeout default? And maybe you could try another samplerate instead of 44100 Hz.

> **sjelly said:**
> I can't figure out how to get beyond this error. It's killing me. I'm no Linux guru, but I can follow instructions. What am I doing wrong? It's got to the point where I'd consider paying someone to help me get this to work!Your device seems to be supported so we must get it to work :)

---

### Post by sjelly on 2009-11-25
OK, with reference to step 3, it has to be said the instructions are not at all clear for a novice, like myself; specifically, how do I "unload and reload /dev/raw1394". What are the commands to do this?

---

### Post by trulan on 2009-11-25
I was wondering that myself.  (I wrote the how-to but did not put that line there.)  The only way I know of is to reboot.

---

### Post by ku4b on 2009-11-25
The first thing I would try is going to setup in qjackctl and in the options tab turn off
artsshell (near the top).  That said, I am trying to get jack and ffado working here also.
I have not been able to get some firewire hardware to behave yet.

---

### Post by AutoStatic on 2009-11-26
> **trulan said:**
> I was wondering that myself.  (I wrote the how-to but did not put that line there.)  The only way I know of is to reboot.

Unload: **sudo modprobe -r raw1394**
Load: **sudo modprobe raw1394**

---

### Post by bluesscream on 2009-11-26
My private checklist when jackd/ffado will not run at all:
0. run ffadomixer. If it shows the gliders goto 4.
1. Run ubuntustudio-controls with all options defaults marked
2. control files manually: /lib/udev/rules.d/50(or an other number)-udev-default-rules: is there a line 'KERNEL=="raw1394",		GROUP="video"' (mostly near the end of the file)?
ls -l  /dev/raw1394 should be like 'crw-rw---- 1 root video 171, 0 2009-11-26 09:56 /dev/raw1394. reboot
3. has user rights for audio and video? (system/administration/users and groups/myuser/properties/user rights). In earlier versions this was done by adding user to groups. If ffadomixer still shows no device goto 10.a.
4. make sure /etc/security/limits.conf contains a line '@audio - rtprio 99'
5. does jackd run with alsa? with rt unmarked? with low performance settings? Explicitely the internal soundchip selected? if not at all goto 10 b
6. reset fw device, make sure the same samplerate is selected as in qjackctl. 
7. try lower priorities in jack i.E. default(=10)
8. Is cpu frequency set to full speed - 'userspace max' or 'perfomance' for each core?
9. Have a look into system-monitor-applet - are there zombie-processes of jackd or other stopped programmes?
10. If it's still not running, completely remove a. ffado b. jackd,  with all configurations, consult the howtos and install them new.

---

