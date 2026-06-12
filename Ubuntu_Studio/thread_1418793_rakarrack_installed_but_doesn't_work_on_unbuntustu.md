---
title: "rakarrack installed but doesn't work on unbuntustudsio 9.10"
date: 2010-03-01
forum: Ubuntu Studio
---

### Post by manjusri on 2010-03-01
I have installed rakarrack2-cvs_0.4.0-1_i386.deb on my computer but it doesn't work .I have tried to run it as sudo and here is teh message I receivedgerard@ubuntugerard:~$ sudo rakarrack
[sudo] password for gerard: 
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Instruction non permise
gerard@ubuntugerard:~$ 
if somebody can help me great thanks

---

### Post by sgx on 2010-03-01
Hi, you must start everything by the same user, can't have jackd started by you, and an app using jackd started by sudo. Both by you, or both by sudo. If qjackctl is not installed, install it with synaptic, start it, and check the settings to insure the right soundcard is in use. See the Input Device  >  
Output Device  >

Click the  >  and soundcards/chips recognized will be listed, choose which one to use. 

On the Settings panel of qjackctl, if the 'realtime' box has its box ticked, undo that for now, and restart jackd, then start Rakarrack, and the sound source it will need, and connect them in qjackctl.  You must tick the 'FX On' box in the upper left of the Rakarrack gui, make sure your volume is low first time.

I use a preamp with a line-out to connect guitar to Rakarrack, press the qjackctl 'Connect' button, and a 3-tab page opens, the audio tab, has system (input) on the left, and System (output) on the right. So select your guitar line-in on the left, and Rakarrack on the right, and press the 'Connect' button on THIS page, and a line appears between them. Next,
select Rakarrack on the left side, and System (output) on the right side, and press connect again. Now whatever is cabled to your soundcard line in will be affected by Rakarrack, and sent to the soundcard. 

To connect a midi keyboard, use the same process, and also make connections in the Alsa tab, rightmost of the three tabs. So if you
start zynaddsubfx, (again, same user for the entire session) and you have connected midi devices on your computer, they appear in the Alsa tab,
so connect zynaddsubfx on the right, to your souncard midi on the left. You may see Ralarrack already connected there.

If this does not help, post lots of details about your setup, and efforts.
Cheers

---

### Post by manjusri on 2010-03-01
thanks for your quick answer but before I understand it   I think I have to learn about jack on websites like linuxmao:p

---

### Post by transmogrifox on 2010-03-01
Rakarrack help tells you step-by-step how to do this...with pictures too :)
Have a look:
[http://rakarrack.sourceforge.net/help.html](http://rakarrack.sourceforge.net/help.html)

You may learn a lot of other things from Help, as well.  If you want Help that is relevant to your particular version, use the "Help" menu in Rakarrack.  It will give you the version help that was current at the time of the version release, whereas help on the web tracks bleeding-edge development.  The reason I say this is because there are some FX modules shown on the Web Page Help that don't exist in 0.4.2.  These new FX are currently available in the git source tree (active development).  If I didn't mention this, it might cause confusion when you discover your version of Rakarrack doesn't have all the FX shown in help :)

Your problem above is probably that jackd is not yet correctly configured by default.  When you launch Rakarrack without first launching jack, Rakarrack starts jack with your .jackrc default settings.  If you have never configured jack to work properly on your system, then it's just luck if ubuntu happened to make a good guess about what settings will work in your particular setup.
If you ever get to a point in your Ubuntu life where you are comfortable with resolving dependencies and compiling from source, you may find the "bleeding edge" development fun to follow:
[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)

The instructions to build from git assume all dependencies are satisfied on your system.  It's easy to do, but there is a learning curve to ascend before you begin to think it's easy.

---

### Post by transmogrifox on 2010-03-01
FWIW--- here is what tells you about the jack problem.  Basically below tells you what jack is trying to do, then ends with saying it gave an instruction that isn't permitted...this means jackd is probably not configured properly for your system:

> JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Instruction non permise

Install qjackctl and use per the Rakarrack help page.  First configure jack in qjackctl settings, then start jack.  Jack needs to be working before Rakarrack will be useful.

---

### Post by manjusri on 2010-03-03
great thanks for your precious inhormations transmogrifox;I think  they will really help me

---

