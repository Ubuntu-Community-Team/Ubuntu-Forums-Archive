---
title: "Software for a CarPC"
date: 2006-03-26
forum: The Cafe
---

### Post by zachtib on 2006-03-26
I'm currently working on building a CarPC. After trying out DashPC and being unimpressed, I decided to write my own program.

right now, I'm building the user interface in glade.  First question: Can I use glade to create python code rather than C? I'm not sure which language I'll be writing the final program in yet, though.

This program is basically just a menu to launch the applications.

For firefox, (though im willing to use other browsers, such as epiphany) I want it to start in fullscreen mode (I don't ever want anything to open in a window in this app, the whole interface should be able to be used from a touchscreen LCD) also, I'm looking for an on-screen-keyboard for firefox.  either an extenstion or a separate app.  what would be perfect is if the keyboard would pop up whenever a text field gained focus and leave whenever it lost focus.

I'm also planning on using rhythmbox for music management, and my next question is this:  How should i go about customizing the interface? It (9.3.1) is almost perfect, I just want to add a close button onto the toolbar to make using the touchscreen easier.

Not sure what application to use for the video player.  I was thinking VLC, but i want something that if it touch the screen (aka a click), some controls will show up temporarily.  Totem does this pretty well, and if i could change the 'leave fullscreen' button into an exit button, that interface would be almost exactly what im looking for.

My CarPC will have a wireless card and antenna.  I'm planning on using NetworkManager and working on my own frontend for it (this can be done, correct?)

This is all I can think of for the moment.  If you have any input whatsoever, I would appreciate it. whether is a comment, suggestion, or an anwser to a question i asked.  either post or email me.  my email is my forum username AT gmail.com

I've attached a screenshot of the current user interface.

EDIT: Remembered something:

I'd rather not use gnome, as I want this to be lightweight.  Would these GTK+ widgets still work fine in say, fluxbox? Though I may wind up using gnome 2.14 in the end, im just not sure yet

---

### Post by Kimm on 2006-03-26
Sure, the widgets should still work in fluxbox (you might have to change the theme using gtk-theme-switch2 though). You could try XFCE4 to.

---

### Post by tassoman on 2006-10-04
> **zachtib said:**
> I'm currently working on building a CarPC. After trying out DashPC and being unimpressed, I decided to write my own program.

right now, I'm building the user interface in glade.  First question: Can I use glade to create python code rather than C? I'm not sure which language I'll be writing the final program in yet, though.

This program is basically just a menu to launch the applications.

For firefox, (though im willing to use other browsers, such as epiphany) I want it to start in fullscreen mode (I don't ever want anything to open in a window in this app, the whole interface should be able to be used from a touchscreen LCD) also, I'm looking for an on-screen-keyboard for firefox.  either an extenstion or a separate app.  what would be perfect is if the keyboard would pop up whenever a text field gained focus and leave whenever it lost focus.

I'm also planning on using rhythmbox for music management, and my next question is this:  How should i go about customizing the interface? It (9.3.1) is almost perfect, I just want to add a close button onto the toolbar to make using the touchscreen easier.

Not sure what application to use for the video player.  I was thinking VLC, but i want something that if it touch the screen (aka a click), some controls will show up temporarily.  Totem does this pretty well, and if i could change the 'leave fullscreen' button into an exit button, that interface would be almost exactly what im looking for.

My CarPC will have a wireless card and antenna.  I'm planning on using NetworkManager and working on my own frontend for it (this can be done, correct?)

This is all I can think of for the moment.  If you have any input whatsoever, I would appreciate it. whether is a comment, suggestion, or an anwser to a question i asked.  either post or email me.  my email is my forum username AT gmail.com

I've attached a screenshot of the current user interface.

EDIT: Remembered something:

I'd rather not use gnome, as I want this to be lightweight.  Would these GTK+ widgets still work fine in say, fluxbox? Though I may wind up using gnome 2.14 in the end, im just not sure yet


What's up with this project? I'm interested too at the same thing.

---

### Post by djsroknrol on 2006-10-04
We install systems from carcpu.com at work in our pleasurecrafts. They use XP and all have touchscreens...I've purchaced one for my truck with three screens.

I think I'd rather set up my system with a linux distro as well, but I don't know about support for touchscreens....

---

### Post by zachtib on 2006-10-04
wow, you guys dug up an old topic.  i haven't done any work on it, all that is is a glade file.

maybe i'll work on this someday, maybe not, who knows?

---

### Post by tassoman on 2006-10-04
> **zachtib said:**
> wow, you guys dug up an old topic.  i haven't done any work on it, all that is is a glade file.

maybe i'll work on this someday, maybe not, who knows?

Yea I've found this topic looking for a ubuntu minimal installation to use in a car pc.

I think your idea to create a graphical interface seems good. I was looking also for mythtv and freevo, but theire media center tv home oriented. and not car oriented.

i never used glade, and i dunno where to start from. but if you want we could merge our ideas and work to the project both :-k

---

### Post by basketcase on 2006-10-04
Definitely an old topic, but I've got the parts for my Myth box, so it's time for me to start collecting parts for my carpc..

Had you ever thought about data logging anything on the car (o2's, AFR, boost (if ya got it), etc.)?  that was more the direction I was headed, was I want to be able to tune my EFI system.  

Subscribed...

---

### Post by tassoman on 2006-10-04
> **basketcase said:**
> Definitely an old topic, but I've got the parts for my Myth box, so it's time for me to start collecting parts for my carpc..

Had you ever thought about data logging anything on the car (o2's, AFR, boost (if ya got it), etc.)?  that was more the direction I was headed, was I want to be able to tune my EFI system.  

Subscribed...

there is elm scanner on mp3car.com
[http://store.mp3car.com/ProductDetails.asp?ProductCode=COM%2D013](http://store.mp3car.com/ProductDetails.asp?ProductCode=COM%2D013)

so now r u playing mythtv on your car?

---

### Post by basketcase on 2006-10-04
> **tassoman said:**
> there is elm scanner on mp3car.com
[http://store.mp3car.com/ProductDetails.asp?ProductCode=COM%2D013](http://store.mp3car.com/ProductDetails.asp?ProductCode=COM%2D013)

so now r u playing mythtv on your car?
No...Myth in the house.

Just two projects, I've wanted to do.  Mythtv and CarPC -- separte of each other.

---

### Post by zachtib on 2006-10-04
> **tassoman said:**
> Yea I've found this topic looking for a ubuntu minimal installation to use in a car pc.

I think your idea to create a graphical interface seems good. I was looking also for mythtv and freevo, but theire media center tv home oriented. and not car oriented.

i never used glade, and i dunno where to start from. but if you want we could merge our ideas and work to the project both :-k

I've got my hands full with Deluge and school both, there aren't enough hours in the day for me to take on another project.  But feel free to email me if you want to discuss ideas, etc. for a CarPC.  I'd recommend glade+python to get a quick and easy interface going.  check out [http://www.learningpython.com/](http://www.learningpython.com/) for some good tutorials, a lot of them use python/pygtk/pyglade

---

### Post by Virogenesis on 2006-10-05
have you ever heard of matchbox? Its used on pdas and the nokia 770, might be worth checking out.
Heres the link of some screenshots [http://projects.o-hand.com/matchbox/screenshots.html](http://projects.o-hand.com/matchbox/screenshots.html)
Maybe use a distro like archlinux or something somewhat minimal and load xfce .
As said earlier in the thread.

---

### Post by basketcase on 2006-10-05
Depending on the hardware, I was considering DSL or Ubuntu based on xfce

---

### Post by tassoman on 2006-10-05
> **basketcase said:**
> Depending on the hardware, I was considering DSL or Ubuntu based on xfce

Me too. I was wondering about DSL in a 2GB usb key running xfce. Or ubuntu server runnig xubuntu.

Then something like an handmade gtk interface, or freevo, or mythtv.

My need are not only tv dvd and mp3 but i would add bluetooth sharing with obex server, wifi connection, and GPS navigation.

---

### Post by Virogenesis on 2006-10-05
seen roadster? 
[http://linuxadvocate.org/projects/roadster/](http://linuxadvocate.org/projects/roadster/) 
have a look might be worth using for the gps system.

[http://www.gpsw.co.uk/details/prod1354.html](http://www.gpsw.co.uk/details/prod1354.html)

---

### Post by ZeroXR on 2007-02-26
Anyone working on this still or have ideas on it? I have been doting on the idea of getting a CarPC for my car and a motorized in-dash touch screen for the interface, but I don't want to go with Windows. I have loved my transition over to Linux and would love to have Ubuntu or Xubuntu powering the CarPC.

---

### Post by hotspoons on 2008-01-16
Weird...I found this ancient thread while searching the internet for information of 'Roadster'. I'll chime in, since I run Ubuntu in my car, to let you know what works for me.

The main reason I wanted a computer in my car is to view and log engine/drivetrain health through the ECU. I bought a 2007 Subaru STi last year, and luckily it has a hacked-to-bits ECU that is readable and modifiable by many freeware and open source software solutions. I came across what I thought was the best - Enginuity. It is a Java/Swing application, so it runs 100% in ubuntu with a real JVM (Sun 6 is what I used), plus, with some command-line parameters, you can force it to use GTK widgets, and it can read, log, and modify (but not write - I needed a separate windows partition for that:( ) the ECU data through a [Tactrix]("http://www.tactrix.com/") cable, which is well supported by modern kernels. Something, I don't know what, happened to the project - you can view a debate about the GPL on a car forum (how often does that happen?) here: [http://forums.nasioc.com/forums/showthread.php?p=20731571](http://forums.nasioc.com/forums/showthread.php?p=20731571) .

Anyhow, my current set up consists of an intel i965g micro ATX motherboard (foxconn I think?), a core2-duo @ 1.83, 1 gb of RAM, 120 GB SATA laptop HD, and a ton of stuff hooked up through USB (joystick, touchscreen, DeLorme GPS receiver, bluetooth, soundcard, OBDII cable, etc.). I got a 7" 800x480 touch screen mounted in a custom bezel, and it fits comfortably behind the dash bezel in a double din mounting hole. There is a WRT54G router in the trunk running openWRT linux hooked up as a wireless bridge with the autoAP script at all times, so if I am idle for more than a minute, I usually have the internet.

It has a highly tweaked load of Feisty on it. Mostly, I disabled anything I didn't need, have it boot straight to Gnome with no password (logons don't work well in cars), and I have Beryl (yes, so old, I know) running with a 5 sided cube, a 1 pixel gnome panel, and Roadnav (it sucks, but it works), Banshee, JackRack, and Enginuity running on different faces of the cube at boot, with one free face. I disabled window decoration and fullscreened all applications. I use Jack audio so I can put my car's audio through a million and one plugins with LADSPA (actually, I just use the wideband EQ and mild compression), and everything is using a custom gnome theme I made, based on a Mac OS X theme I found, but colored red to match the instrumentation of the car, and with wider scrollbars. And from engine start to music is about 35 seconds, which is liveable.

I am in the process of creating a new load for the car, using Hardy Alpha and some much improved GPS software (Navit is my favorite so far, but geeks if I zoom out too much), and Exaile for audio (the newer versions can fit in a window that is 800x480, so I am making the switch), as well as all of the newer versions of what I use already, including compiz fusion.

BTW, I use a hacked apart USB PS2-style analog joystick (just the analog parts - I ditched the rest of the JS) to control up/down/left/right, cube spin, and volume in the car, with the two joysticks mounted to a pick guard sitting in an empty spot of my center console (it sounds ugly, but it works out nicely), using qJoyPad to translate joystick movements to keys, but it freaks out after 10 or so minutes, and 'keys' start sticking. I am going to replace this set up with something else, but I haven't figured it out yet.

Happy hacking...

-Rich

---

### Post by zachtib on 2008-01-16
wow, i wasn't expecting this thread to resurface

---

### Post by hotspoons on 2008-01-16
> **zachtib said:**
> wow, i wasn't expecting this thread to resurface

You never do, you never do. Did you ever get anything running in your whip?

---

### Post by blastus on 2008-01-16
> **hotspoons said:**
> Weird...I found this ancient thread while searching the internet for information of 'Roadster'. I'll chime in, since I run Ubuntu in my car, to let you know what works for me.

The main reason I wanted a computer in my car is to view and log engine/drivetrain health through the ECU. I bought a 2007 Subaru STi last year, and luckily it has a hacked-to-bits ECU that is readable and modifiable by many freeware and open source software solutions. I came across what I thought was the best - Enginuity. It is a Java/Swing application, so it runs 100% in ubuntu with a real JVM (Sun 6 is what I used), plus, with some command-line parameters, you can force it to use GTK widgets, and it can read, log, and modify (but not write - I needed a separate windows partition for that:( ) the ECU data through a [Tactrix]("http://www.tactrix.com/") cable, which is well supported by modern kernels. Something, I don't know what, happened to the project - you can view a debate about the GPL on a car forum (how often does that happen?) here: [http://forums.nasioc.com/forums/showthread.php?p=20731571](http://forums.nasioc.com/forums/showthread.php?p=20731571) .

Anyhow, my current set up consists of an intel i965g micro ATX motherboard (foxconn I think?), a core2-duo @ 1.83, 1 gb of RAM, 120 GB SATA laptop HD, and a ton of stuff hooked up through USB (joystick, touchscreen, DeLorme GPS receiver, bluetooth, soundcard, OBDII cable, etc.). I got a 7" 800x480 touch screen mounted in a custom bezel, and it fits comfortably behind the dash bezel in a double din mounting hole. There is a WRT54G router in the trunk running openWRT linux hooked up as a wireless bridge with the autoAP script at all times, so if I am idle for more than a minute, I usually have the internet.

It has a highly tweaked load of Feisty on it. Mostly, I disabled anything I didn't need, have it boot straight to Gnome with no password (logons don't work well in cars), and I have Beryl (yes, so old, I know) running with a 5 sided cube, a 1 pixel gnome panel, and Roadnav (it sucks, but it works), Banshee, JackRack, and Enginuity running on different faces of the cube at boot, with one free face. I disabled window decoration and fullscreened all applications. I use Jack audio so I can put my car's audio through a million and one plugins with LADSPA (actually, I just use the wideband EQ and mild compression), and everything is using a custom gnome theme I made, based on a Mac OS X theme I found, but colored red to match the instrumentation of the car, and with wider scrollbars. And from engine start to music is about 35 seconds, which is liveable.

I am in the process of creating a new load for the car, using Hardy Alpha and some much improved GPS software (Navit is my favorite so far, but geeks if I zoom out too much), and Exaile for audio (the newer versions can fit in a window that is 800x480, so I am making the switch), as well as all of the newer versions of what I use already, including compiz fusion.

BTW, I use a hacked apart USB PS2-style analog joystick (just the analog parts - I ditched the rest of the JS) to control up/down/left/right, cube spin, and volume in the car, with the two joysticks mounted to a pick guard sitting in an empty spot of my center console (it sounds ugly, but it works out nicely), using qJoyPad to translate joystick movements to keys, but it freaks out after 10 or so minutes, and 'keys' start sticking. I am going to replace this set up with something else, but I haven't figured it out yet.

Happy hacking...

-Rich

Cool stuff. Not that I understand a lot of that but cool stuff anyway. I am interested in monitoring my engine's performance, in particular, completing monitors that have been cleared because the PCM has been reset. I have an OBDII programmer but it is very limited. I can also log live data but it is nowhere near sophisticated what you have.

How do I get started?!!!!

---

### Post by hotspoons on 2008-01-16
> **blastus said:**
> Cool stuff. Not that I understand a lot of that but cool stuff anyway. I am interested in monitoring my engine's performance, in particular, completing monitors that have been cleared because the PCM has been reset. I have an OBDII programmer but it is very limited. I can also log live data but it is nowhere near sophisticated what you have.

How do I get started?!!!!

If you have a Subaru, the world is your oyster. View the thread I linked above on NASIOC.com and find a mirror for enginuity, and go to town.

I don't know about any other manufacturers' ECU's that can be read by Linux natively, but there if your OBDII USB cable is supported, and supported fully by the kernel, you can always ' ln -s /dev/ttyUSBx ~/.wine/dosdevices/COM1' and use windows software, which, for the most part, has worked flawlessly with wine.

---

### Post by blastus on 2008-01-16
> **hotspoons said:**
> If you have a Subaru, the world is your oyster. View the thread I linked above on NASIOC.com and find a mirror for enginuity, and go to town.

I don't know about any other manufacturers' ECU's that can be read by Linux natively, but there if your OBDII USB cable is supported, and supported fully by the kernel, you can always ' ln -s /dev/ttyUSBx ~/.wine/dosdevices/COM1' and use windows software, which, for the most part, has worked flawlessly with wine.

I noticed that some of that stuff was just for Subaru. Is your PCM actually modded or is it factory but just programmed? I have a Mustang. I use a Predator to connect to the PCM. I can't connect a laptop directly as there is just an OBD-II port. I don't have an OBD-II USB port. What device and touchscreen do you use?

Edit: Sorry I should have read better, you're using a USB to OBD-II cable right? I didn't know you could get those!

---

### Post by hotspoons on 2008-01-17
> **blastus said:**
> I noticed that some of that stuff was just for Subaru. Is your PCM actually modded or is it factory but just programmed? I have a Mustang. I use a Predator to connect to the PCM. I can't connect a laptop directly as there is just an OBD-II port. I don't have an OBD-II USB port. What device and touchscreen do you use?

Edit: Sorry I should have read better, you're using a USB to OBD-II cable right? I didn't know you could get those!

The screen is a lilliput 629GL: [http://store.mp3car.com/2008_Lilliput_7_VGA_Touchscreen_629GL_70NP_LED_Ba_p/mon-016.htm](http://store.mp3car.com/2008_Lilliput_7_VGA_Touchscreen_629GL_70NP_LED_Ba_p/mon-016.htm)
I bought a CNC bezel mount from a guy who resells them...this is a kit with that monitor, but you can get it separate, and it fits ford, too: [http://store.mp3car.com/Subaru_WRX_bolt_in_kit_with_toushcreen_p/dsh-013.htm](http://store.mp3car.com/Subaru_WRX_bolt_in_kit_with_toushcreen_p/dsh-013.htm)

The USB->OBD-II cable is use is available here: [http://www.tactrix.com/](http://www.tactrix.com/) - I don't know if anything like that is available for Fords, though I would imagine so...though Subaru drivers tend to be nerds, there are a lot less of us than Mustang owners.

The ECU is stock, but with new software (boost, air/fuel, spark, temp/pressure/knock correction, etc.) modified and installed by me. The only mods to the car are a 3" turbo-back exhaust (catless), an intake, and software, but I am probably making 50+ HP over stock to the wheels (300ish at the wheels) with some software and an udder disregard for my NOx emissions.

---

### Post by stalkier on 2008-04-16
> **zachtib said:**
> I'm currently working on building a CarPC. After trying out DashPC and being unimpressed, I decided to write my own program.

right now, I'm building the user interface in glade.  First question: Can I use glade to create python code rather than C? I'm not sure which language I'll be writing the final program in yet, though.

This program is basically just a menu to launch the applications.

For firefox, (though im willing to use other browsers, such as epiphany) I want it to start in fullscreen mode (I don't ever want anything to open in a window in this app, the whole interface should be able to be used from a touchscreen LCD) also, I'm looking for an on-screen-keyboard for firefox.  either an extenstion or a separate app.  what would be perfect is if the keyboard would pop up whenever a text field gained focus and leave whenever it lost focus.

I'm also planning on using rhythmbox for music management, and my next question is this:  How should i go about customizing the interface? It (9.3.1) is almost perfect, I just want to add a close button onto the toolbar to make using the touchscreen easier.

Not sure what application to use for the video player.  I was thinking VLC, but i want something that if it touch the screen (aka a click), some controls will show up temporarily.  Totem does this pretty well, and if i could change the 'leave fullscreen' button into an exit button, that interface would be almost exactly what im looking for.

My CarPC will have a wireless card and antenna.  I'm planning on using NetworkManager and working on my own frontend for it (this can be done, correct?)

This is all I can think of for the moment.  If you have any input whatsoever, I would appreciate it. whether is a comment, suggestion, or an anwser to a question i asked.  either post or email me.  my email is my forum username AT gmail.com

I've attached a screenshot of the current user interface.

EDIT: Remembered something:

I'd rather not use gnome, as I want this to be lightweight.  Would these GTK+ widgets still work fine in say, fluxbox? Though I may wind up using gnome 2.14 in the end, im just not sure yet

Make sure you use a SSD for the hard drive. By using a Solid State Drive you eliminate the wear and tear that a car has on a hard drive's moving parts. A regular HDD can be used but will quickly crash. SSD's are fair in price but are not very large in GB. [www.tigerdirect.com](www.tigerdirect.com) has some good prices as does [www.newegg.com](www.newegg.com). Since you looking into using Linux then you will not have to be over concerned as far as space for the OS and apps. You might have to install a second SSD for the MP3/Video storage. This can be done by installing the SSD into a 2.5" External enclosure and locating a USB 2.0 cord in the dash/glovebox/etc. Just be sure to find one that offers USB power.

Hope this helps.

PS - Don't forget to include a GPS adapter and BlueTooth.

---

### Post by hotspoons on 2008-04-22
> **stalkier said:**
> Make sure you use a SSD for the hard drive. By using a Solid State Drive you eliminate the wear and tear that a car has on a hard drive's moving parts. A regular HDD can be used but will quickly crash. SSD's are fair in price but are not very large in GB. [www.tigerdirect.com](www.tigerdirect.com) has some good prices as does [www.newegg.com](www.newegg.com). Since you looking into using Linux then you will not have to be over concerned as far as space for the OS and apps. You might have to install a second SSD for the MP3/Video storage. This can be done by installing the SSD into a 2.5" External enclosure and locating a USB 2.0 cord in the dash/glovebox/etc. Just be sure to find one that offers USB power.

Hope this helps.

PS - Don't forget to include a GPS adapter and BlueTooth.

Hmmm...I've been going about 9 months on a 2.5" 120GB SATA laptop drive, and don't have a bad sector yet - I was going to get an SSD (probably a CF to IDE unit with a 16GB CF card to keep things reasonably priced) when my hard drive failed, but it hasn't yet. I mounted the drive on a flexible plastic platform, and there is about 1/2" of high density foam underneath of the drive and the platform its mounted on, so it has some suspension.

I reloaded the PC with a very stripped down/customized load of Gentoo; it took about 100 seconds to go from POST to a usable desktop before running Ubuntu 7.04 and Gnome with a couple of applications launching on start up - now it is around 18 seconds to X, and another 10 seconds to a usable desktop (that includes launching Navit [gps/navigation application] and exaile; I set JDash [SSM/OBDII GUI dashboard] to launch 15 seconds later as it was slowing everything else down while booting the java VM). Granted, I am not running a desktop environment, but raw X with Compiz Fusion as my window manager and AWN as a task manager.

GPS is taken care of by some delorme thing an ex-girlfriend gave me, and I have bluetooth, though there are no applications I can find for using the PC as a hands-free speakerphone for linux.

I also have a USB HDTV tuner (I can launch MythTV if I like, but dumb while driving), Tactrix OBDII/SSM cable, part of a dell keyboard (multimedia keys with rotary volume, molded into a fiberglass panel), USB audio plugged into a trunk-mounted amp, and a webcam, not to mention a DD-WRT loaded router with AutoAP script for stealing teh internet. It all works quite well!

---

