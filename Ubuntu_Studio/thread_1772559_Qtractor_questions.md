---
title: "Qtractor questions"
date: 2011-05-31
forum: Ubuntu Studio
---

### Post by OFobbs on 2011-05-31
Hi, I've been back and forth between Reaper and Mixcraft on windows and 
Qtractor/Ardour LMMS in Ubuntu and I finally think I get it now after about 2 years :). But I have a question about Qtractor, probably nothing too deep for many of you. 
 
I've been trying to get Qtractor to look like the screenshot on the website but haven't figured it out yet. I got to the point of changing the colors on Qtconfig, but have not got it to look like the one on the screenshot. Is there a setting that I need to copy? 
 
Also, in order to get a sound clip to loop, I've been copying and pasting a clip one after another, which becomes a chore after a while. Is there a way to duplicate a clip like in Ardour (press 'D' I think) or in Reaper where you can click and drag a clip to loop it? 
 
Not sure about adding the stand alone instruments, but can I use LMMS instruments in Qtractor rather than use LMMS. I like LMMS but some things like not being able to timestretch a sound clip or a sample track not being able to route to a mixer is a turn off for me. Not a show stopper, but just something I would prefer to be able to do in the application I'm working in. 
 
Thanks for your help in this.
 
 
Omar

---

### Post by sgx on 2011-06-01
The qtractor might be in a window manager that can give its own colors to some apps, or maybe its in a GTK theme, this short topic
mentions a config app to aid using gtk theme colors with Qt apps

[http://www.bodhilinux.com/forums/index.php?/topic/505-qt-apps-are-ugly/](http://www.bodhilinux.com/forums/index.php?/topic/505-qt-apps-are-ugly/)

Reaper works really well in linux, using wine and wineasio, I use it for most of my linux audio projects. There are some discussions at the Reaper forum, as quite a few people enjoy it in their linux.

Cheers

---

### Post by OFobbs on 2011-06-02
> **sgx said:**
> The qtractor might be in a window manager that can give its own colors to some apps, or maybe its in a GTK theme, this short topic
mentions a config app to aid using gtk theme colors with Qt apps
 
[http://www.bodhilinux.com/forums/index.php?/topic/505-qt-apps-are-ugly/](http://www.bodhilinux.com/forums/index.php?/topic/505-qt-apps-are-ugly/)
 
Reaper works really well in linux, using wine and wineasio, I use it for most of my linux audio projects. There are some discussions at the Reaper forum, as quite a few people enjoy it in their linux.
 
Cheers
 
I have Reaper in wine installed. I was also trying to give native linux DAW apps a chance to run and see if I like them better. I'm leaning more towards using Reaper in wine, but I'm also interested in how to get all these linux apps working together in jack.  
 
Do you use anything else besides Reaper for your audio projects?  If so, which ones? 
 
Thanks, 
 
Omar

---

### Post by sgx on 2011-06-03
Hi, I like to record hydrogen drums together with rythm-guitar, or keys, in timemachine, then edit as needed in audacity, and import in to reaper for more parts. If I run low on cpu for some complex fx chain, I will play the track in alsaplayer or aqualung, and record the fx and track in timemachine.

Reapers live rendering also gets a lot of use, as its easy to set high quality settings for complex setups.

Yoshimi gets a lot of use for layered sounds combining sweeps, pads,
and rythmic parts, to get a lot of action for each keypress.

For guitar, I use a Fender Mustang usb amp, into rakarrack, calf plugins, and the nice fx from ComputerMusicMagazine dvd, and Amplitube. Choosing and combining the strengths from each of these is great fun.

I use jp1 from linuxdsp for basic jackd connections, and edit .bash_history to keep alternate jackd commands and long wine command strings readily available. qjackctl can be troublesome, as qt does
not like some windows app GUIs, and xorg fails at the artwork.

Last week, I got the Inovada and MDA lv2 plugins, and some of those are very nice, and should be simple to use in Ardour, which I have
only briefly tested (the beta V3, which I liked) and it is a favorite in many linux recording setups.
Cheers

---

### Post by Pablo_F on 2011-06-03
> Do you use anything else besides Reaper for your audio projects? If so, which ones? 

[www.ardour.org](www.ardour.org)

For qtractor questions, I suggest you ask also in [www.rncbc.org](www.rncbc.org)

---

