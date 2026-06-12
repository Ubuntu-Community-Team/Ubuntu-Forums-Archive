---
title: "Audacity problems"
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by dkfalcone on 2010-05-30
Greetings;
     Not so much of a computer noob as a Linux Gnube. I have a laptop  
 intel pent 4 2.4ghz w/462.3gb mem  running
 ubunto studio upgraded to  
 kernel 2.6.31-10-rt Gnome 2.30.0.
 

 It ran pretty well under openSuse, but I changed to Ubunto in hopes of finding a bit more intuitive interface that I could remotely support for relatives who are having a tough time with windows and virus infected fuzzy puppies attachments.  
     Audacity is a program that ran just fine under openSuse, but under Ubuntu (before and after upgrade) when I go to record, the “track” is grayed out, and at best I can get it to record only a second or two of audio, which shows in the track, then the rest of the track stays gray, and nothing more is recorded. I tried a couple of other audio recording programs, but non of them would record either. I have tried a usb mic (part of a video cam that seems to work ok under skype) and the built in mic.
     System monitor shows that I do max out on processor some times (but not in Audacity), and never seem to run out of memory (gets to about 75%)
 Any ideas?
 Thanks
 

 p.s for what it's worth, GimpShop works fine.

---

### Post by sgx on 2010-05-30
Hi, it may need a change in the device settings 

Edit-->Preferences-->Devices

These settings can change depending on if jackd or other
sound app is already running.

To use the line in of your soundcard with audacity and jackd,

jackd -d alsa -r 44100

prepare to record

start audacity

press record, then press pause


start qjackctl, audacity should be there, but labeled 'portaudio'
(how intuitive is that!)

connect this to the appropriate choice in the opposite pane by selecting
both items and pressing connect on this screen (not the main qjackctl screen) If a line between them exists, its done for you. Now your
line-in is connected to audacity, press the pause button a second time
to begin recording.

Do all the 44100 numbers match in the settings of the apps being used?


If that works, in the Import/Export you can choose to work on a copy of the original,safer, but may need more ram/diskspace. 1 gig free disk space is a lucky minimum when using audacity, more is better.

Hope something helps

---

