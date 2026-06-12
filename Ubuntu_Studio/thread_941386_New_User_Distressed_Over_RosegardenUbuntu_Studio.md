---
title: "New User Distressed Over Rosegarden/Ubuntu Studio"
date: 2008-10-08
forum: Ubuntu Studio
---

### Post by Kaienne on 2008-10-08
So, yeah. I'm a novice electronica artist who used to use FL Studio to make electronica until I got fed up with my current operating system and, at my flatmate's behest, installed Ubuntu. This was a couple months ago. It was only after this that I discovered that FL wasn't fully compatible with Ubuntu, even with Wine; random crashes, no VSTi support, et cetera. I gave Rosegarden a shot, but for some reason couldn't get it to make any sound. It's entirely possible, if not likely, that I am missing one or several steps, but I have only just come from a program that is extremely intuitive.

Having given up on Rosegarden, I looked up "ubuntu sequencing software" online and was eventually led to install Ubuntu Studio on my computer.
Much to my horror, I discovered soon after installation that Ubuntu Studio was not one self-contained programme with various interfaces for different applications, but some *forty-or-so* separate programmes. What's more, certain programmes would not run without 'JACK support'; I don't even know what that is, much less how to enable it.

So, I haven't made any new music in months. I've attempted to get the hang of things a couple times, but to absolutely no avail. Are there any electronica artists out there who may be able to give me a hand on how to work with either of these messes? I don't even know where to start.

---

### Post by thorgal on 2008-10-08
hi, 
you do need jack. Think of jack as the linux "rewire" but in better and more flexible.

Rosegarden can only work with jack, the low latency audio server that can connect many applications together like you would connect devices with cables. Rosegarden need to be connected to jack ports (either your soundcard's output ports or some other sofwtare ports like ardour's track input ports to record the sound you are making). There are many different ways to do so with rosegarden. Either you don't use its audio output ports and rather use the soft synths ports instead (only use rosegarden as the MIDI controller) or use rosegarden's audio output ports.

I suggest you read the very comprehensive rosegarden manual, and before that, install jack and make it run properly on your system (ubuntu studio should make it easy as there are subtle system configurations to take care of).

Good luck.

PS: if that can help, I have a very lame video on youtube where I show rosegarden in action (don't get over excited, it's boring ...)

[http://www.youtube.com/watch?v=Ys1s3Dk5sGo](http://www.youtube.com/watch?v=Ys1s3Dk5sGo)

---

### Post by Kaienne on 2008-10-08
Jack is a separate programme entirely [from U. Studio]?

---

### Post by thorgal on 2008-10-08
yes it is.
The packages are something like 
- jackd
- libjackxxx

and then, there are a few utilities like
- qjackctl : GUI to configure and run jackd (the jack audio server daemon)
- some jack tools that may not come with the jackd package but that are optional

The current version should be 0.109.2 or so.
Install these packages and try to run qjackctl. There must be some info describing all this in this forum.

---

### Post by Kaienne on 2008-10-08
Thank you.

---

### Post by eric71 on 2008-10-08
You should also look into trying LMMS, which should be more similar to FL than Rosegarden. Should be in the standard ubuntu repository. Or you can get the latest developmental version at:

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

edit: a slightly more up to date stable version than that in the Hardy repositories is available through getdeb.net

[http://www.getdeb.net/app/Linux+MultiMedia+Studio](http://www.getdeb.net/app/Linux+MultiMedia+Studio)

---

### Post by markbuntu on 2008-10-09
You need to read these:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

---

### Post by bolex100 on 2008-10-10
I'm just about to install Rose garden.  My add/remove shows Jack Control, JackEQ, and jack rack.  Do I need all of them?  For any that I DO install, would I need to start them manually before I run Rose Garden?

I have been using Lmms.  Its like FL studio but there is less control.  Also I can use FL with Cubase which has one great advantage.  You can time delay an entire track by 200mS, which replicates playing in front or behind the beat.  Lmms cant do that.  I don't know about Rose garden.

This whole subject of audio software needs a pinned guide to cover installing and connecting.  :guitar:

---

### Post by roaldz on 2008-10-11
> **bolex100 said:**
> I'm just about to install Rose garden.  My add/remove shows Jack Control, JackEQ, and jack rack.  Do I need all of them?  For any that I DO install, would I need to start them manually before I run Rose Garden?

I have been using Lmms.  Its like FL studio but there is less control.  Also I can use FL with Cubase which has one great advantage.  You can time delay an entire track by 200mS, which replicates playing in front or behind the beat.  Lmms cant do that.  I don't know about Rose garden.

This whole subject of audio software needs a pinned guide to cover installing and connecting.  :guitar:
I think you can use a ladspa plugin on a track in LMMS to delay it. 
There is sooo much possible with jack-enabled linux audio software/plugins, you have no idea:)

There are guides, you just need to look for it, it won´t show up when you think about it.

---

### Post by markbuntu on 2008-10-11
Jackrack has all the effects and makes them very easy to use in the jack/connection box.

---

### Post by robeast on 2008-10-11
Hey, check out the first link in my sig, it goes over all the basics of JACK, Rosegarden and a couple other useful apps that you will probably be using soon. You need to commit a good chunk of time and patience to learning audio in Linux because, instead of learning one program that does everything, you need to learn four or five programs at the same time which all do different things. I think once you get the hang of it you will find this approach much more flexible, but the first few weeks are hard. :x

---

### Post by paron on 2009-01-19
Far, far too late for this user, but here's how I got Rosegarden working in Ubuntu Studio 8.10. 

Ubuntu Studio apparently installs and autostarts TiMidity++ as a MIDI synth. I added the soundfonts to the TiMidity CFG file (see below), and then fiddled RoseGarden's "Studio -- Manage MIDI Devices" dialog and set everything to one of TiMidity's ports.

**How to add soundfonts to TiMidity:** I used "Fluid Release 3" by Frank Wen. I don't know what that means, but I appreciate it being available. I just googled for it (fluid soundfonts R3), downloaded, and unzipped to /usr/share/sounds/sf2 

In Ubuntu Studio, you can find TiMidity's cfg file in: /etc/timidity/timidity.cfg. You have to start gedit from a terminal like: "sudo gedit" or it won't save. (Gedit won't tell you why, either -- goes on about "wrong directory" or some such).

I just stuck the line, "soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2" on the end of the .cfg file. 

OK, that worked, and I didn't find it anywhere else, although I'm sure it's out there. ( EDIT: found some at [http://www.rosegardenmusic.com/wiki/setting_up_the_fluidr3_gm.sf2_for_timidity](http://www.rosegardenmusic.com/wiki/setting_up_the_fluidr3_gm.sf2_for_timidity) )I'm also sure there are easier ways, because I frankly don't know what the heck I am doing. 

I just got lucky, but I'll bet there are lots of people here who can explain what I did -- to me, for starters! Anyway, it worked.

---

### Post by Senior Ah Me on 2010-03-19
Been running UbuntuStudio for a while now. I'm working on kicking the Microsoftheaded habit....I'm getting there! I've been running UbuntuStudio Hardy, and have an image of that DAW safely archived in case this UbuntuStudio Jaunty install doesn't quite measure up. 
While I don't mind Rosegarden et al, my focus has been on Reaper and EnergyXT2, both running in Wine.
Little irritating bugs like the audio suddenly cutting out in Rosegarden sends me scurrying back to more reliable and familiar wine applications.
Besides...Jack is cool and all, but I'm used to native VST/i support, and there's no substitute for being able to save your whole project, synths, samplers and all with one click.
Anyway....this Jaunty install is coming along, inspired mostly by the dual monitor support for my video card...one of my final reasons for doing projects in WinDohs. Unfortunately, and seemingly without any discernable pattern, UbuntuStudio will decide to mirror my 2 monitors instead of extending them. I've managed to isolate a file that will restore my original layout if I copy it in root...but this has been a major annoyance. 
So while it might be sacriligeous to the Linux purists, my advice is Reaper and/or EnergyXT2 in wine. Any Linux audio app can still be jacked into either sequencer, giving you the best of both worlds.

You might notice the two "Waves" plugins. I got DirectX9 going yesterday! Awesomeness!!!

[IMG]http://photos-c.ak.fbcdn.net/hphotos-ak-snc3/hs469.snc3/25760_103757852989555_100000660211055_100090_7299478_n.jpg[/IMG]

---

