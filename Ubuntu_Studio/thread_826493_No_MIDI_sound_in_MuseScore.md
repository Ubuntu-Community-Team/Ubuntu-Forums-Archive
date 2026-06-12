---
title: "No MIDI sound in MuseScore"
date: 2008-06-11
forum: Ubuntu Studio
---

### Post by guitarMan666 on 2008-06-11
MuseScore refuses to output sound or even enable the "Play Panel."  While this is not essential, it is extremely useful to ensure that the score I input is the score I want.  I started it from a console to get error messages:

$ mscore
Suspending PulseAudio
Alsa_driver: can't set period size to 1024: Invalid argument
init ALSA audio driver failed
no ALSA audio found
sequencer init failed
Couldn't resolve property: 2

Any help would be greatly appreciated.
Thank you in advance,

---

### Post by Stochastic on 2008-06-12
what settings do you have in Edit -> Preferences -> Audio -> ALSA ?  Also try right after a fresh reboot (just incase something is hanging onto an audio process & not letting other apps play nice).

also could you print the output of ```
apt-cache policy mscore
```

You could also try setting up jack output if you can't get ALSA working right.

---

### Post by guitarMan666 on 2008-06-13
The settings in the preferences dialog are as follows:
Device: default
Sample Rate: 44100
Period Size: 1024
Fragments: 3

I have even tried it after a fresh reboot to no avail.

The out put of apt-cahce:
mscore:
  Installed: 0.9.1d+dfsg-0ubuntu4
  Candidate: 0.9.1d+dfsg-0ubuntu4
  Version table:
 *** 0.9.1d+dfsg-0ubuntu4 0
        500 [http://ftp.usf.edu](http://ftp.usf.edu) hardy/universe Packages
        100 /var/lib/dpkg/status

---

### Post by Stochastic on 2008-06-13
Strange those are nearly the exact same settings I have, and I have no playback issues.  The only thing I have different is the sample rate (mine is set to 48000), though that doesn't seem to be your sticking point according to the error.  Maybe try specifying the hardware directly - instead of "default" use "hw:0,0".  Are you running UbuntuStudio or just vanilla Ubuntu?  Can you play midi files anywhere on your system?  Also, could you post the output of ```
mscore -d
```

Lastly, try starting jackd via ```
jackd -d alsa
``` (post the results) then open MuseScore, go to the sound settings, turn jack mode on, and alsa off, restart MuseScore, then try playing a file.

---

### Post by guitarMan666 on 2008-06-14
MIDI output in Rosegarden works fine thru timidity.  My computer is a repurposed business PC so sound facilities are limited until I can afford a better card with a HW synth on it.  It's kinda a special case as far as the OS goes.  It's running a "patched" version of Ubuntu Studio.  I used Ship-It to get a "vanilla" Ubuntu CD-ROM then, installed the ubuntustudio packages (all of them) to make it Ubuntu Studio.
Here is the requested output:
$ mscore -d
Suspending PulseAudio
locale file not found for locale <en_US>
midi devices found
global share: </usr/share/mscore-0.9>
Alsa_driver: can't set period size to 1024: Invalid argument
init ALSA audio driver failed
no ALSA audio found
sequencer init failed
Couldn't resolve property: 2
Failure to resume: Invalid argument
--------------------------------------
Attempting to run jackd yields:
$ jackd -d alsa
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
-----------------------------------
Finally here is the output from mscore after changing from default to hw:0,0 (I don't know if that's my soundcard though, I'm gonna have to hunt that down):
$ mscore
Suspending PulseAudio
Alsa_driver: Cannot open PCM device hw:0,0 for playback.
init ALSA audio driver failed
no ALSA audio found
sequencer init failed
Couldn't resolve property: 2
Got SIGINT, exiting.

Thanks for all your time by the way.

---

### Post by Stochastic on 2008-06-15
Hmm, were all of those error messages obtained directly after a fresh boot (no firefox sessions, mp3 listens, etc...)?  It looks like alsa may not be configured properly in your system or that some other process is hogging it as a resource.  Possibly post the list of processes running on your machine (after a fresh reboot, just to narrow things down) - this can be found in the Gnome System Monitor.  The next step would be to go into System -> Administration -> Synaptic Package Manager then do a search for ALSA, and all boxes that are green should be right-clicked, then "mark for re-installation", then apply changes.

---

### Post by guitarMan666 on 2008-06-15
No, none of those errors were after a fresh boot.  I created a list of processes (attached as a LONG text file) that run after a fresh boot.  I used ps -A rather than system monitor because I wanted to ensure a complete, perfectly copied list.  The problem doesn't seem to be affected by a fresh boot.  I am re-installing the ALSA packages as I post this reply and will edit when I am finished to post the results.

EDIT: Success!  Reinstalling the packages seems to have made all the difference.

---

### Post by apos on 2008-11-15
Hi Eric,
this is an older thread, but NOT SOLVED for me (and others).
There is filed a new [Bug #292391]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/292391") for Ubuntu Intrepid describing this problem.

**@guitarMan666**
Some questions remain from your last posting:

> EDIT: Success! Reinstalling the packages seems to have made all the difference. 
[LIST]
[*]Which packages (in detail) did you reinistall.
[*]Did you disable pulseaudio otherways?
[*]Did you do your process list after the reinstall or before?
[*]Did you do your process list as normal user or root?
[/LIST]
Knowing this would be very helpful solving the problem.
Greets Axel

---

### Post by ideebe on 2008-11-15
Idee jewelry wholesale,supply,necklace supply, earrings supply,ring supply, hangs falls supply, jewelry wholesale,925 silver jewelry wholesale,gem,makeup,hairdressing[img]http://www.ideewomen.com/cn/uploads/1.jpg[/img]http://www.ideejewelry.com/

---

### Post by guitarMan666 on 2008-12-23
Hello, I no longer remember what specific pacakages I reinstalled but here is the procedure I followed:

In Synaptic, do a search for alsa.
Look for the installed packages (they are marked with a GREEN box next to them).
Go through each one and mark it for "reinstallation"

To your remainging questions:
* No, I did NOT disable PulseAudio in any other way.
* My process list was created as a normal user (the -A flag makes it irrelavent as to whether I was root or not...I think)
* My process list was created BEFORE reinstalling.

Also, on a seperate note, this problem returned after my update to Intrepid.
I have unmarked the thread because the solution here did NOT work in Intrepid.

---

### Post by babarosa on 2008-12-23
Hi folks,

if you want to have the most latest version (at the moment it is muse score 0.9.4) and maybe solve your problems this way, add to your software sources the lines
**deb [http://ppa.launchpad.net/mscore-ubuntu/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/ubuntu) hardy main**
and
**deb-src [http://ppa.launchpad.net/mscore-ubuntu/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/ubuntu) hardy main**
then
**sudo apt-get update**
then either search for "mscore" in synaptic or do a
**sudo apt-get install mscore**

You did copy Soundfont FluidR3_GM.sf2 to usr/share/sounds/sf2, did you?
I use it on Xubuntu 8.04.1 and it works very well.

Happy scoring, merry christmasing and happy new yearing to all linux users all over the world from hallein, the small city in austria where "Silent night, holy night" was composed ):P

---

### Post by guitarMan666 on 2008-12-28
I didn't copy anything anywhere.  I was under the impression that it would put it where it needs to go.

I'll also try this latest version, assuming they have a repo for Intrepid.

---

### Post by babarosa on 2008-12-29
Guitarman,

muse score needs a soundfont to play the midi data as sound.
Search for "FluidR3_GM.sf2" and download it.
If you have ubuntu, type "sudo nautilus" into the terminal (in Xubuntu "sudo thunar") and enter your password, now copy this soundfont to the path I mentioned. If the sf2-folder doesn't exist, generate it.

Regards, Michael

P.S. I use hardy but assume the above mentioned repo works fine with intrepid. Please let us know.
The recent most version I recommend already gives you a hint at installation that it could not find a soundfont including a link where to download it.

---

