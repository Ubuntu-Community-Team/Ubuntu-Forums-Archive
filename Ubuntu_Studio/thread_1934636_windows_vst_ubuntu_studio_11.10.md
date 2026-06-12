---
title: "windows vst ubuntu studio 11.10"
date: 2012-03-02
forum: Ubuntu Studio
---

### Post by filtermonk on 2012-03-02
hello,

i have some windows vst plugins which i would like to keep... i wanted to install dssi-vst, but i have seen that the dssi-vst seems to be already part of the ubuntu studio 11.10 standard installation...

so i searched further and tried to figure out more about the VST_Path and so on... i did come along jack-dssi-host dssi-vst.so:plugin.dll

but i get error messages...

can somebody please give me a walktrough to get my favorite windows vst plugins to work, because i realy need them

thanks for any help

regards 

Mark

---

### Post by sgx on 2012-03-02
Hi, I would recommend wine, wineasio, festige, (from a Falk PPA)
and Reaper (installed in your user directory)and a windows version
of Energy XT2.5 as a good backup, available on CM Magazine DvDs,
or with any Behringer hardware purchase.

[http://www.reaper.fm/](http://www.reaper.fm/)

[https://launchpad.net/~falk-t-j/+archive/festige](https://launchpad.net/~falk-t-j/+archive/festige)

91% of non-dongled plugins should work in Reaper, 63% in Festige.
Reaper offers full DAW features, and is fast/efficient/stable for
basic multi-track recording in linux.

You'll want a full windows path:

/home/you/.wine/drive_c/Program Files/Steinberg/VstPlugins

google and download these .dll files to 

/home/you/.wine/drive_c/windows/system32 folder if they are not there

gdiplus
mfc42
mfc71
msvcp60
msvcp71
msvcr71
msvcr80
mscvsc60
msvcp90
msvcr90

In /etc/profile.d folder, I have these files,
dssi-vst.sh  vst.sh and lv2.sh

# Set DSSI_VST_PATH for Bash shell
if [ -n "\$DSSI_VST_VST_PATH" ]; then
   export DSSI_VST_VST_PATH="/usr/local/lib/vst"
fi

# Set VST_PATH for Bash shell
if [ -n "\$VST_PATH" ]; then
   # Set VST_PATH for Bash shell
   export "VST_PATH=/usr/lib/vst"
fi

# Set LV2_PATH for Bash shell
if [ -n "\$LV2_PATH" ]; then
   # Set VST_PATH for Bash shell
   export "LV2_PATH=/usr/lib/lv2"
fi

calf, invada, and mda are fine lv2 plugin collections. :popcorn:

---

### Post by filtermonk on 2012-03-12
i am using renoise...

i please still need assistance to get the Windows VST Plugins to work with ubuntu studio 11.10

---

### Post by filtermonk on 2012-06-17
the installation of reaper is not an option for me...

currently i am using 12.04 and also renoise... i can install renoise win32 with wine and use vst plugins tough...

i can remember, about 5 years ago i used openSuse and there i have compiled the dssi-vst wrapper which worked very well... i also found FST as a solution...

maybe there is someone who can guide me through to get my vst working with dssi wrapper in ubuntu 12.04

---

### Post by Precipitous on 2012-06-17
I run a few Windows vst plugins (synths, effects, etc) in Ubuntu by running [SAVIHost]("http://www.hermannseib.com/english/savihost.htm") in Wine/Wineasio. It is a simple vst host with a very small footprint and best of all it works with Jack.

The basic process is:

[LIST=1]
[*]Install Wine.
[*]Install Wineasio.
[*]Register Wineasio by running *regsvr32 wineasio.dll* in a terminal
[*]Download the desired version of SAVIHost from [http://www.hermannseib.com/english/savihost.htm](http://www.hermannseib.com/english/savihost.htm)
[*]Copy the savihost.exe file downloaded in step 4 to the folder where the Windows vst plugin resides, then rename it to the name of the Windows vst .dll file. For example if your Windows vst is named Zebra2.dll you would rename savihost.exe to Zebra2.exe.
[*]Repeat step 5 for any Windows vst plugins you wish to use.
[*]Use Winetricks to install msvcrt.dll and mfc42.dll (you can do this by installing the Visual C++ 6 Runtimes and Foundation Classes.
[*]Setup Wine to use alsa (this is done differently in different versions of Wine, so you may need to do some research).
[*]To run a Windows vst plugin navigate to the folder where it resides and run the SAVIHost .exe file created in step 5.
[*]When SAVIHost opens go to the Devices menu and set the MIDI Input to your MIDI controller and the Wave Output Device to Wineasio.
[*]The Windows vst plugin should now be ready to use and should show up in Jack the same as any other audio source.
[/LIST]
Let me know if you run into any difficulties and I will be glad to offer further assistance...

---

### Post by drfreq on 2012-06-17
i have read your instructions and i will think about it...

do you know something about FST?

[http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)

---

### Post by Precipitous on 2012-06-18
> **drfreq said:**
> i have read your instructions and i will think about it...

do you know something about FST?

[http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)
I am sorry, but I do not have any first-hand experience with FST...

---

### Post by Precipitous on 2012-06-18
> **drfreq said:**
> i have read your instructions and i will think about it...

do you know something about FST?

[http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)
I am sorry but I do not have any first-hand experience with FST...

---

### Post by sgx on 2012-06-18
fst will work, if your wine/wineasio are installed right,
quite a few plugins will work, but stick to ones with in-built
preset handling. Try U-he, Native Instruments, IK Multimedia
and Cakewalk instruments, quite a few will work.

Excellent free instruments with their own
preset interface include Synth1, Oatmeal, and from U-he,
TyrellN6, Bazille, Zebralette and TripleCheese.

Old Computer Music Magazine dvd often had Wusikstation3, and
a huge soundset. ZebraCM is on every dvd, and also CMFuzz for
distortion/compression, and Sanford Phaser is one of the best
in class.
A back-issue with z3ta 1.5 is a great purchase, z3ta is a fine
synth, and multi-fx processor,using the fx .dll

Most of the free ampsims/fx work with fst
[www.guitarampmodeling.com](www.guitarampmodeling.com)

A lot of great Reaktor 'user library' ensembles run in the 30 minute demo, and they all should use the 'snaps' preset scheme. A deep  parallel universe of creative and free instruments ;)

---

