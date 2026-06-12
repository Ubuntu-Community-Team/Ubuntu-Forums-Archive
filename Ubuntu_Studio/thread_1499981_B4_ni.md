---
title: "B4 ni"
date: 2010-06-02
forum: Ubuntu Studio
---

### Post by andres.varela on 2010-06-02
Hi, I recently started using ubuntu and as a musician (piano and organ player), was wondering if this software, native instruments B4, which is something like a Hammond organ emulator, it's Linux compatible. There's also a newer version B4 II, but looking around I was not able to find any information regarding this issue. 
Does anybody know?
Thanks,

Andres

---

### Post by zettberlin on 2010-06-02
> **andres.varela said:**
> was wondering if this software, native instruments B4, which is something like a Hammond organ emulator, it's Linux compatible.

No, not really compatible.
Many NI-Programs run via an emulation-software called WINE though. For audio-use you can try to install Wine-ASIO also, wich allows WINE-Software like NIs Guitar rig to run with better Latency and connected to the audio-server jackd.

There are many capable software-organs natively written for Linux:

Bristol has a B3-Module

Horgand is a big organ, so is Aeolus (both are more like classical organs)

CALF Organ is a software synthesizer with drawbars on its interface and presets like "jimmy" ;-)

For your piano-playing there is the commercial pro-grade modeling-software pianoteq. Not for free but runs natively under Linux and offers very good quality.

---

### Post by AutoStatic on 2010-06-02
[AZR-3]("http://ll-plugins.nongnu.org/azr3/") is a good alternative too which is in [falkTX's PPA]("https://launchpad.net/~falk-t-j/+archive/lucid/"). And then there's [Beatrix]("http://people.dsv.su.se/~fk/beatrix_home.html") but I never tried that one.

---

### Post by sgx on 2010-06-02
> **andres.varela said:**
> Hi, I recently started using ubuntu and as a musician (piano and organ player), was wondering if this software, native instruments B4, which is something like a Hammond organ emulator, it's Linux compatible. There's also a newer version B4 II, but looking around I was not able to find any information regarding this issue. 
Does anybody know?
Thanks,

Andres
Hi, it should work if you install wine, wineasio, jackd, qjackctl, and Reaper (step by step guide below)
I have several NI demos and the Service Center installed.

Use synaptic to install wine, wineasio, and qjackctl. 

In the qjackctl setup page, on the right side

Input device  >
Output device  >

click the > widgets and choose your soundcard from the list that appears

run the commands

wineprefixcreate

winecfg  (choose alsa for audio in the gui that opens) 

regsvr32 wineasio.dll

wine will now have created

/home/username/.wine/drive_c/Program Files

make the needed folders to install vst plugins in this location:

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

copy the B4 installer to
/home/user and run the simple wine command

If the file is:  Battery 2 Demo Setup.exe

its name must be changed first 

wine Battery*2*Demo*Setup.exe  or
wine Battery\ 2\ Demo\ Setup.exe  

(Note the 2 ways spaces can be changed, choose one, a wine command necessity)


Use the default installer locations of windows plugins,
(dongles, pace, and ilok plugins won't work, most others will.)

Install Reaper, ( [http://www.reaper.fm/download.php](http://www.reaper.fm/download.php) )
in /home/username. 

Install it with

wine reaper352-install.exe

start jackd with   jackd -d alsa -r 44100
start qjackctl by menu, or by name in a terminal.
Start Reaper with

wine reaper/reaper.exe

In reaper, choose wineasio  from Options-->Preferences-->Device

Enable your midi keyboard from Options-->Preferences-->MIDI Devices

for VST, Options-->Preferences-->VST  choose the location B4 is installed
in for Reaper to scan it. Click rescan.

should be ready to go. right-click in the blank space beneath the reaper menus/icons, and choose 'Insert virtual instrument on new track'.
The track and B4 gui should appear

-------------------------------------------------------------------------

(in the synaptic metapackages folder, in the list on the left side of its gui, there will be a Ubuntu Studio package, to install many other nice apps) 
Cheers

---

### Post by andres.varela on 2010-06-03
Thanks for taking the time and helping me out, and thanks for the info.
Ill try something out...
cheers!

---

### Post by sgx on 2010-06-03
> **andres.varela said:**
> Thanks for taking the time and helping me out, and thanks for the info.
Ill try something out...
cheers!
just to be sure, phrases like

/home/user or /home/username 

you would insert your chosen ubuntu username,

/home/andres

whatever it may be.
Since all linux have a /usr folder by default, I don't want to confuse.

Cheers :)

---

### Post by Xmat on 2010-08-24
Just to add to the very good step-by-step guide by sgx: you don't actually need Reaper to run B4 II. You can run it as a standalone VST. (You'll, of course, need jack, wineasio and wine).

---

