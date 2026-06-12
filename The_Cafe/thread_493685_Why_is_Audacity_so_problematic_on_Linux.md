---
title: "Why is Audacity so problematic on Linux?"
date: 2007-07-06
forum: The Cafe
---

### Post by FuturePilot on 2007-07-06
I don't understand why Audacity is so problematic on Linux. Doing a search here on the forums for Audacity returns tons of threads on people having problems with Audacity. I've tried *everything * to get it working on my laptop and nothing works. If I start it I get that error cannot initialize I/O audio layer. I've tried starting it with the command aoss audacity, but I still can't record anything. On my desktop PC, I'm missing the little Input box that lets you choose different input sources. Again, I've tried everything. I've even compiled the Beta version (which looks very nice by the way with GTK 2 and a lot more features) but still nothing.

*But* on Windows Audacity works perfectly on both computers. Why does Audacity work perfectly in Windows but gives me headaches in Linux? What's the difference?:(

---

### Post by logos34 on 2007-07-06
what about killing ESD and system sounds in System>prefs>sound?  

I can't seem to get it to record at 44 KHz (only 48K)...never figured it out. i'd try the beta version but I can't get it to compile on my edgy (probably wouldn't help anyway).  

yeah it's really slick on windows

---

### Post by FuturePilot on 2007-07-06
Tried that, didn't work:(
When I compiled the Beta it only worked with make install. It failed with checkinstall. Here's a good how to if you're interested
[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/]("http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/")

---

### Post by Polygon on 2007-07-06
Audacity is really weird

for starters, the version in the repos is compiled against gtk1. why cant we update the package so that its compiled against gtk2 so it at least LOOKS a bit better?

second off, half the time i have to run "aoss audacity" or else i dont get any playback... and the other half of the time it seems to work fine if i just do "audacity".

and i no what little input box your talking about. Its also disabled for me, but im thinking its because the linux drivers for my soundcard suck really bad, and it does do anything else besides giving me sound playback. Im supposed to have things like mic input, and "whatUhear" input options (i do in windows) but i guess in linux, the drivers are too immature to allow that for me.

---

### Post by FuturePilot on 2007-07-06
> **Polygon said:**
> Audacity is really weird

for starters, the version in the repos is compiled against gtk1. why cant we update the package so that its compiled against gtk2 so it at least LOOKS a bit better?

second off, half the time i have to run "aoss audacity" or else i dont get any playback... and the other half of the time it seems to work fine if i just do "audacity".

and i no what little input box your talking about. Its also disabled for me, but im thinking its because the linux drivers for my soundcard suck really bad, and it does do anything else besides giving me sound playback. Im supposed to have things like mic input, and "whatUhear" input options (i do in windows) but i guess in linux, the drivers are too immature to allow that for me.

Well at least I'm not the only one. 
Gutsy has the latest Beta version with GTK2.

---

### Post by userundefine on 2007-07-06
I've had the same experience re: Windows/Linux.  Jokosher is maturing rapidly though it's still not up to Audacity's level.  Check it out.

---

### Post by prizrak on 2007-07-06
Hmm, weird. I never had a single issue with Audacity. It's funny I learn about all those things that people have problems with and I never encounter despite doing the same stuff. I must have some kind of ungodly Linux luck or something. I should start distributing little statues of myself to put next to computers :)

---

### Post by Lolicon on 2007-07-06
I used Amarok until I was able to Wine Foobar2000. Why don't you give either of them a shot? I didn't like filehandling on it too much. Amarok is slow and crashes on me, for some reason though.

---

### Post by orange2k on 2007-07-06
> **Lolicon said:**
> I used Amarok until I was able to Wine Foobar2000. Why don't you give either of them a shot? I didn't like filehandling on it too much. Amarok is slow and crashes on me, for some reason though.

How do you edit audio files in Amarok? :rolleyes:

---

### Post by Lolicon on 2007-07-06
I don't. I heard good thing about Ex Falso, and Foobar2000 has mastagging.

---

### Post by prizrak on 2007-07-06
> **Lolicon said:**
> I don't. I heard good thing about Ex Falso, and Foobar2000 has mastagging.

Audacity is an audio editing application not a player. Honest mistake ;)

---

### Post by a12ctic on 2007-07-06
Accualy, the only problems that I have ever had with audicity happened on windows. Coincidence?

---

### Post by picpak on 2007-07-06
I can't remember the last time I got the cannot initialize I/O audio layer error. It just disappeared on its own. But lately I've had to stop running it with aoss because of how buggy it gets. It runs a lot smoother when I run it normally.

This is Audacity 1.3.3 beta, by the way.

---

### Post by stmiller on 2007-07-06
> **logos34 said:**
> what about killing ESD and system sounds in System>prefs>sound?  

I can't seem to get it to record at 44 KHz (only 48K)...never figured it out. i'd try the beta version but I can't get it to compile on my edgy (probably wouldn't help anyway).  

yeah it's really slick on windows

Do you have a VIA chipset? Recent VIA chipsets actually are made to operate at 48Khz, and will only do so with the current driver in Linux. A pain in the ***, I know. I've got the same thing on my AMD box. Check out this page, short summary is at very bottom:

[http://www.baudline.com/solutions/full_duplex/via8235/index.html](http://www.baudline.com/solutions/full_duplex/via8235/index.html)

---

### Post by FuturePilot on 2007-07-06
I'm thinking it's because of the current sound drivers in Linux. They're not that mature right now, but hopefully they'll get better.

---

### Post by forrestcupp on 2007-07-06
> **FuturePilot said:**
> I don't understand why Audacity is so problematic on Linux. Doing a search here on the forums for Audacity returns tons of threads on people having problems with Audacity. I've tried *everything * to get it working on my laptop and nothing works. If I start it I get that error cannot initialize I/O audio layer. I've tried starting it with the command aoss audacity, but I still can't record anything. On my desktop PC, I'm missing the little Input box that lets you choose different input sources. Again, I've tried everything. I've even compiled the Beta version (which looks very nice by the way with GTK 2 and a lot more features) but still nothing.

*But* on Windows Audacity works perfectly on both computers. Why does Audacity work perfectly in Windows but gives me headaches in Linux? What's the difference?:(

It's because Linux and Windows work differently, so Audacity works differently in Linux and Windows.  In Windows, you can only have one recording source.  In Linux, you can record from multiple sources.  What you need to do is just unmute/turn up the volume of the input you want to use, and turn down the volume sliders of the inputs you don't want to use.  You do this with alsamixer, or the Gnome GUI mixer if you're using Gnome.  Audacity in Linux will automatically record from whatever inputs you have turned up in the system.  You don't adjust anything in Audacity.  That is why it's different in Linux than it is in Windows.

About the error, try to go to Edit->Preferences.  In the Audio I/O tab, try resetting the Playback device and the Recording device.  Try setting them to the ALSA entry that says (hw:0,0).  Maybe that will help.

---

### Post by a12ctic on 2007-07-06
> **FuturePilot said:**
> I'm thinking it's because of the current sound drivers in Linux. They're not that mature right now, but hopefully they'll get better.

The sound drivers in linux are amazing on lower end cards. My AC97 cards always work and sound quite a bit better with alsa than they do in windows.

---

### Post by logos34 on 2007-07-06
> **a12ctic said:**
> The sound drivers in linux are amazing on lower end cards. My AC97 cards always work and sound quite a bit better with alsa than they do in windows.

Hard to believe.

---

### Post by mridkash on 2007-07-11
There are no buttons and menus appearing in audacity. Looks like there is no text on the buttons, every thing is blank.

I installed audacity as a part of Ubuntu studio, which was upgraded from ubuntu 7.04.

I've tried reinstalling the package audacity but no respite.

Help!

---

### Post by Gina on 2008-06-14
I can't get Audacity to record from Line In whatever I try! (Except the dreaded Windoze - in which it works beautifully!)  Unmpteen different versions of Ubuntu and all sorts.  Line In accepts audio to play on the speakers via Line Out and Audacity plays back audio files alright - it just won't record.  This applies to 3 computers too - of varying ages and different sound systems.  I've started a thread about this in the Multimedia & Video forum.

---

### Post by bufsabre666 on 2008-06-14
i use the one from getdeb, works just as good if not better than the one for windows on my computer

---

### Post by zmjjmz on 2008-06-14
Audacity works fine for me (admittedly, I haven't tested recording), but the rest of this thread is kind of old :/

---

