---
title: "Ubuntu studio apps? from a newbie"
date: 2011-04-01
forum: Ubuntu Studio
---

### Post by eevilscotsman on 2011-04-01
Hi, just installed Ubuntu Studio 10.10 from live cd on a usb- looks great, and all works perfectly - however - it takes up roughly 1.7gb and as part of that, i also chose to install the editing suite during the setup - which was pretty time consuming. I was hoping studio came with inbuilt production suite for audio editing however the apps menu looks pretty vacant- ie. under sound & video, I only have a sound recorder under audio production tab, brasero, movie player and 2 pulse audio choices, device chooser and volume.

My question is - what's taking up the 1.7gb install? - I'd have been as well just installing normal ubuntu at 700mb - it's only an issue as i'm running on a 4gb usb. Thanks for any advice

---

### Post by zettberlin on 2011-04-01
> **eevilscotsman said:**
> Hi, just installed Ubuntu Studio 10.10 from live cd on a usb- looks great, and all works perfectly - however - it takes up roughly 1.7gb and as part of that, i also chose to install the editing suite during the setup - which was pretty time consuming. I was hoping studio came with inbuilt production suite for audio editing however the apps menu looks pretty vacant- ie. under sound & video, I only have a sound recorder under audio production tab, brasero, movie player and 2 pulse audio choices, device chooser and volume.

Maybe the menu is not updated correctly.

You can find the apps that *should* be installed with Ubuntu Studio easily like this:

open a terminal

type the name of the application and enter, some examples:

qjackctl

(you need this one, start it, set up Jack and start Jack before anything else)

ardour2

HD-recording/editing/arranging suite

rosegarden

MIDI-Sequencer



> **eevilscotsman said:**
> 
My question is - what's taking up the 1.7gb install? - I'd have been as well just installing normal ubuntu at 700mb - it's only an issue as i'm running on a 4gb usb. Thanks for any advice

1.7 Gig is not that much for a complete Linux plus audio-production tools.

---

### Post by Precipitous on 2011-04-01
> **eevilscotsman said:**
> Hi, just installed Ubuntu Studio 10.10 from live cd on a usb- looks great, and all works perfectly - however - it takes up roughly 1.7gb and as part of that, i also chose to install the editing suite during the setup - which was pretty time consuming. I was hoping studio came with inbuilt production suite for audio editing however the apps menu looks pretty vacant- ie. under sound & video, I only have a sound recorder under audio production tab, brasero, movie player and 2 pulse audio choices, device chooser and volume.
Most of the applications you are looking for are available by going to the Sound & Video menu, then to the Audio Productions sub-menu. The first level of Sound & Video is pretty barren by default, but the Audio Production section houses some great applications.

---

### Post by eevilscotsman on 2011-04-03
cheers for the advice, I know that 4gb aint a lot for audio production suites etc but I'm just road testing the whole system on an old laptop with no screen or internal hdd seeing how well it all functions - after testing just about every linux distro out there! Matter of interest, my audio productions sub menu is empty too asides jack and my newly installed ardour - what great apps had you in mind preciptous?
many thanks
matt

---

### Post by riffey#4 on 2011-04-03
Not much of a help, because I only started using Ubuntu Studio a few weeks ago, but I have some 30+ applications in the Audio Production menu, and I'm pretty sure most of them came with Ubuntu Studio.

You said you installed Ubuntu Studio on a laptop with internal HDD?
Aren't you just running it from the live disk? Maybe that's the difference. 

Some of my entries are: 
Aconectgui
Aeolus
Ardour
Audacity
BEAST
Bitmeter
Calf Plugin pack
Echo mixer
Freebirth
Genpo
GNU Denemo
Gtick
Hydrogen and so on...

---

### Post by eevilscotsman on 2011-04-03
Thanks for the hints - I dowloaded the ubuntustudio install cd, which cannot be run in live mode - only install - which i installed on my broken dell laptop - ie. I dropped it and the screen broke and internal hard now fails. I've whipped off the screen and now run it on an external monitor and instead of buying a new hard drive, i installed ubuntu on a 4gb usb flash drive. Although the ubuntustudio installation iso is twice the size of the normal ubuntu- I had no apps to use in the sound/vid menu so have to do it manually. That said, I'm impressed at how fast and smoothly everything is working and am definately considering using it as my permanent operating system on my " real " laptop

---

### Post by jejeman on 2011-04-03
> Hi, just installed Ubuntu Studio 10.10 from live cd
Ubuntu studio does not have live cd. Only alternate install cd.
> My question is - what's taking up the 1.7gb install? - I'd have been as well just installing normal ubuntu at 700mb - it's only an issue as i'm running on a 4gb usb. 
1.7GB is the dvd install image. If you have only 1.7GB occupied space than you didnt install ubuntu studio apps.
I have ubuntu studio 10.10 instaled on 8GB usb flash drive, and it occupied at start 4GB with all aplications from dvd (audio, video, graphics), after adding some more programms that I need it has only 1GB free. So 4GB usb drive is really thight, almost insufficient.

---

