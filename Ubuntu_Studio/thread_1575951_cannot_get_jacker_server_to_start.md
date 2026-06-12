---
title: "cannot get jacker server to start"
date: 2010-09-16
forum: Ubuntu Studio
---

### Post by berean88 on 2010-09-16
hi, i apologize if this is already answered but i couldnt find it anywhere. i am somewhat mew to linux, and obviously to ubuntu studio 10.01 LTS. when i open the jack control and start the server  it error's out with the following text:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]13:03:58.774 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:03:58.821 Statistics reset.[/COLOR]
 [COLOR=#66CC99]13:03:58.856 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]13:03:59.052 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:04:08.336 Startup script...[/COLOR]
 [COLOR=#990099]13:04:08.337 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:04:08.739 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:04:08.739 JACK is starting...[/COLOR]
 [COLOR=#990099]13:04:08.740 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]13:04:08.744 JACK was started with PID=5147.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    763590
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 [COLOR=#999999]13:04:10.457 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]13:04:10.476 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:04:10.477 killall jackd[/COLOR]
 [COLOR=#CC3366]13:04:10.477 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]13:04:10.928 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]13:04:10.974 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

lshw yields the following info for my audio:
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:cfe38000-cfe3bfff

i cant do anything on my system until i quit jack control, then it works fine (other than being able to use jack!) it has never worked for me, i am tring to get it running so i can test out ardour. thank you for any help you can provide.

---

### Post by Pablo_F on 2010-09-16
Can you post the output of

aplay -l

?

---

### Post by berean88 on 2010-09-16
here's the output Pablo_f

shawn@skubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
shawn@skubuntu:~$ 


thanks 4 your help.

---

### Post by Pablo_F on 2010-09-16
I am not sure. Try 48.000 Hz with 2 periods per buffer, if it doesn't work, try 48.000 Hz with 3 periods. 

Oh, wait:
> i cant do anything on my system until i quit jack control, then it works fine (other than being able to use jack!) 

It looks like a RAM problem, probably related to this bug:

[http://pulseaudio.org/ticket/806](http://pulseaudio.org/ticket/806)  

But you seem to have 1 GB RAM, don't you. Anyway, check the output of:

 ls -lah /dev/shm

And, if there are several pulse-sh-xxxxxxx or similar, do a:

rm -f /dev/shm/pulse*

before starting Jack Control

Also, you can check the IRQ numbers. Is your card sharing IRQ number with another device?  

cat /proc/interrupts

What kernel are you running?


Cheers! Pablo

---

### Post by berean88 on 2010-09-16
i deleted the pulse* files, jack runs now, i just need to figure out how to really use it!! i'm not sure what those files are but belieive me, i will save this post! thank you so much!

---

