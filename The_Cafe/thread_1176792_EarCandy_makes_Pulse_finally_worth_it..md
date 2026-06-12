---
title: "EarCandy makes Pulse finally worth it."
date: 2009-06-02
forum: The Cafe
---

### Post by Islington on 2009-06-02
[http://webupd8.blogspot.com/2009/05/earcandy-is-smart-pulseaudio-volume.html](http://webupd8.blogspot.com/2009/05/earcandy-is-smart-pulseaudio-volume.html)

so have you guys tried this earcandy program/volume control for pulseaudio? it really makes life easy. It automatically changes your sound depending on the current application using it. For instance if you listen to music and a Skype call comes in, the music will fade out (based on your settings) until it's turned off, and the skype sound will be the only one running. Or if you listen to music and then play a YouTube video, the music will be again turned off and you will only hear the sound of the YouTube video. you can also set up different rules for it.


Finally. a reason to be with pulse.:popcorn:

[A good set of instructions]("http://ubuntuforums.org/showpost.php?p=7390751&postcount=13") to trying out earcandy right from the jaunty repositories. (thanks to monsterstack)

---

### Post by swoll1980 on 2009-06-02
> **Islington said:**
> [http://webupd8.blogspot.com/2009/05/earcandy-is-smart-pulseaudio-volume.html](http://webupd8.blogspot.com/2009/05/earcandy-is-smart-pulseaudio-volume.html)

 the music will fade out (based on your settings) until it's turned off, and the skype sound will be the only one running. Or if you listen to music and then play a YouTube video, the music will be again turned off and you will only hear the sound of the YouTube video.

Finally. a reason to be with pulse.:popcorn:

Isn't this what PA has done all along? Only let you listen to one thing at a time? Sorry I couldn't help myself.

---

### Post by squaregoldfish on 2009-06-02
Wow! Thanks for letting us know about this - I'm definitely going to check it out soon (off on holiday first though!)

Steve.

---

### Post by OutOfReach on 2009-06-02
This looks interesting, about to try it

---

### Post by monsterstack on 2009-06-02
Been using earcandy for a few days now. Pretty cool stuff.

---

### Post by PurposeOfReason on 2009-06-02
Does it work with MPD? I only hear things from MPD and flash videos.

---

### Post by dragos240 on 2009-06-02
> **outofreach said:**
> this looks interesting, about to try it

+1

---

### Post by Islington on 2009-06-02
> **swoll1980 said:**
> Isn't this what PA has done all along? Only let you listen to one thing at a time? Sorry I couldn't help myself.

I had to chuckle damn you/.

---

### Post by Islington on 2009-06-02
> **PurposeOfReason said:**
> Does it work with MPD? I only hear things from MPD and flash videos.

flash will work just fine, mpd you might wish to try. I use gmusicbrowser which uses mpd I think, and that works fine.

---

### Post by OutOfReach on 2009-06-02
Hmm this is a very nice tool, I think I might just keep it :)

---

### Post by albinootje on 2009-06-02
> **Islington said:**
>  It automatically changes your sound depending on the current application using it. For instance if you listen to music and a Skype call comes in, the music will fade out (based on your settings) until it's turned off, and the skype sound will be the only one running. 


Wow, sounds very promising, and those screenshots like nice.
Thanks for sharing!! :)

---

### Post by bxcrx on 2009-06-02
> **swoll1980 said:**
> Isn't this what PA has done all along? Only let you listen to one thing at a time? Sorry I couldn't help myself.


I didn't see anything in PulseAudio's volume mixer (pavucontrol) that allowed me to set specific volume settings per Window event.

---

### Post by monsterstack on 2009-06-02
> **PurposeOfReason said:**
> Does it work with MPD? I only hear things from MPD and flash videos.

Works fine with mpd. It detected my mpd player of choice rather effortlessly. Here are the steps to get the earcandy Jaunty PPA:

```
gksudo gedit /etc/apt/sources.list
```

And paste the following at the bottom of the file:

```

### Ear Candy
deb http://ppa.launchpad.net/flimm/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/flimm/ppa/ubuntu jaunty main
```

Add the keys from the keyserver:

```
gpg --keyserver keyserver.ubuntu.com --recv AC9D76CD6E73CA45
gpg --export --armor AC9D76CD6E73CA45 | sudo apt-key add -
```

Install:

```
sudo apt-get update
sudo apt-get install earcandy
```

You'll find it in the Accessories application menu.

---

### Post by Islington on 2009-06-03
> **bxcrx said:**
> I didn't see anything in PulseAudio's volume mixer (pavucontrol) that allowed me to set specific volume settings per Window event.

it was a stupid joke, PA only lets you hear one thing before crashing har har.

good write up, can I link it in the top post?

---

### Post by monsterstack on 2009-06-03
> **Islington said:**
> it was a stupid joke, PA only lets you hear one thing before crashing har har.

good write up, can I link it in the top post?

Who me? Go right ahead.

---

### Post by swoll1980 on 2009-06-03
> **Islington said:**
> it was a stupid joke, PA only lets you hear one thing before crashing har har.


Actually no. The joke was a reference to the problem that some users have with PA only allowing them access to one audio stream at a time. For example if you were listening to music, and started a game, the game would steal the audio until you exited it. Wine is another one that steals the audio if I remember right.

---

### Post by monsterstack on 2009-06-03
> **swoll1980 said:**
> Actually no. The joke was a reference to the problem that some users have with PA only allowing them access to one audio stream at a time. For example if you were listening to music, and started a game, the game would steal the audio until you exited it. Wine is another one that steals the audio if I remember right.

That was my experience too till I followed one of thems pulseaudio guides floating around the Howto section. But then I've followed the upgrade path and apparently some of the problems are due to mouldy old ALSA configuration settings not being purged by updating. My girlfriend did a clean install of Jaunty and she didn't have the same issues.

---

### Post by swoll1980 on 2009-06-03
> **monsterstack said:**
> That was my experience too till I followed one of thems pulseaudio guides floating around the Howto section. But then I've followed the upgrade path and apparently some of the problems are due to mouldy old ALSA configuration settings not being purged by updating. My girlfriend did a clean install of Jaunty and she didn't have the same issues.

I've never had an issue with it. I know it was a pretty common problem though.

---

### Post by Mr. Picklesworth on 2009-06-03
Hooray! I was waiting for this day to come :)

(I still want volume control in window title bars, though. Hurry up and reinvent the wheel, Metacity!)

---

### Post by Islington on 2009-06-03
> **Mr. Picklesworth said:**
> Hooray! I was waiting for this day to come :)

(I still want volume control in window title bars, though. Hurry up and reinvent the wheel, Metacity!)

:popcorn: where in the world did you see metacity may have vol. control in in window title bar?

---

### Post by bluebyt on 2009-06-03
The deb cannot work on intrepid :(

Error: Dependency is not satisfiable: python-central?

---

### Post by Islington on 2009-06-03
> **bluebyt said:**
> The deb cannot work on intrepid :(

Error: Dependency is not satisfiable: python-central?

could you not just build it?

---

### Post by bluebyt on 2009-07-06
> **Islington said:**
> could you not just build it?

I tried but I get this error:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ear_candy/ear_candy.py", line 35, in <module>
    from pulseaudio.PulseAudio import PulseAudio 
  File "/usr/lib/python2.5/site-packages/ear_candy/pulseaudio/PulseAudio.py", line 17, in <module>
    from lib_pulseaudio import *
  File "/usr/lib/python2.5/site-packages/ear_candy/pulseaudio/lib_pulseaudio.py", line 1914, in <module>
    pa_stream_set_monitor_stream = _lib.pa_stream_set_monitor_stream
  File "/usr/lib/python2.5/ctypes/__init__.py", line 361, in __getattr__
    func = self.__getitem__(name)
  File "/usr/lib/python2.5/ctypes/__init__.py", line 366, in __getitem__
    func = self._FuncPtr((name_or_ordinal, self))
AttributeError: /usr/lib/libpulse.so.0: undefined symbol: pa_stream_set_monitor_stream

---

### Post by dragos240 on 2009-07-06
Holy crap! I know that song!!!!!!! It's by inoue joe, closer.

---

### Post by SKLP on 2009-07-06
Just tested it! pretty cool app

---

### Post by nielsek on 2009-07-06
me likes

---

### Post by _exn_ on 2009-08-24
Anybody gets it work with 8.04 ?!

---

### Post by speedwell68 on 2009-08-24
> **bluebyt said:**
> The deb cannot work on intrepid :(

Error: Dependency is not satisfiable: python-central?

[http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html](http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html)

---

### Post by calrogman on 2009-08-24
Necromancy!

Zombie thread!

Run!

---

### Post by bluebyt on 2009-08-24
> **speedwell68 said:**
> [http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html](http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html)

Thanks speedwell68 but doesn't seem to work. I get this error, even though I had installed the repisotory. 

sudo apt-get install earcandy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package earcandy

---

