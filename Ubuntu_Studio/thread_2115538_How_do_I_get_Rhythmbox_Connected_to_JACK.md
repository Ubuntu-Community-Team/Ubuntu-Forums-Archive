---
title: "How do I get Rhythmbox Connected to JACK?"
date: 2013-02-13
forum: Ubuntu Studio
---

### Post by forkenbrock on 2013-02-13
I'm trying to connect Rhythmbox to my USB DAC with JACK.  My goal is to try to get the highest performance 2-channel audio playback that I possibly can and nothing else.  I don't plan to use PulseAudio unless I need to.

So far I have sound coming from the DAC when I do a test in gStreamer.  The Default Output is set to Custom / jackaudiosink and when I press the Test button I see the gStreamer heading open up on the Connections box of JACK in the Audio tab; it's connected on the right side to System > Playback_1 and Playback_2.  The ALSA box says Midi Through Port-0, but it doesn't do anything and I'm not using Midi so I'm assuming I'll disregard that tab.

Patchbay is empty and Qjackctl starts without any errors.

Rhythmbox has music files and they act as if they're playing, but it doesn't produce any sound.


Thanks for your help

---

### Post by forkenbrock on 2013-02-14
I was able to solve this myself after finding some screenshots of Patchbay.

For anyone who's interested, here's what I see.

**Patchbay:**
 On the right, left Socket 1 > Capture 1, which can be added or edited (with a right click).  Type is Audio and Client is System.

On the right,  Input Socket 1 > Playback_1 and Playback_2, which can be added or edited, also select Audio and System.

Save the setup and press the Activate button on the top right.


**Connections - Jack Audio Connection Kit (Audio tab)**
On the right, left Socket 1 > Capture 1, which can be added or edited  (with a right click).  Type is Audio and Client is System.

On the left, Rhytmbox > out_jackaudiosink and out_jackaudiosink.

On the right, System > playback_1 and playback_2

When playing there should be two lines connecting the left and right sections.


Jackctl is started and music playing in Rhythmbox is playing through the DAC.  I would recommend Rhythmbox for its iTunes functionality with filters.  It's a shame there's no Foobar for Linux, because it kills every Linux player.  I am surprised to see Linux players so lacking in configurablility.  The vast majority of players (like Alsaplayer) seem altogether worthless if you have more than about 10 songs in your library.

---

### Post by josephk84 on 2013-02-20
hi,
could you post some screenshots of your patchaby / session setup?
because I can't follow your instructions, even if these are quite easy, i imagine..
cheers

---

### Post by forkenbrock on 2013-03-21
Sorry for the confusion.  I wrote those instructions at 3am, and I wasn't really able to understand them either when I came back.  After some problems that caused me to reinstall everything it took a while to get JACK working again.  It's surprisingly difficult to just get audio playback working.

1. Install the packages: jackd, qjackctl and libjack0

2. Open the file below as root and edit it like in the screensot with the file.  I was getting errors with the server starting until I set the Real Time properties in the .conf file, even when I hadn't checked the RT mode in the settings.  Note, fork is the username (see screenshot), but you can also use @audio if you add users to the Audio group.
/etc/security/limits.conf

3. See the Jack settings in the screenshot.  The Connections box will be blank when JACK isn't started or music isn't playing.  You can't change or set anything in Connections, you will set things up in Patchbay.  See the screenshot for Patchbay as well; it shows the properties settings from the right side and the left is similar (Type is Audio, Client is System and Plug is capture_1).


[ATTACH=CONFIG]240419[/ATTACH]

---

### Post by forkenbrock on 2013-05-29
I didn't show the Ouput Socket in the screenshot, but when you click Add, the window should have the type set as "Audio", the Client as "System" and the Output Socket as "Capture_1.  If you have trouble seeing the settings, try starting JACK and set these while it's running.

You're going to need this link to go with the info above.

[http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html](http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html)

Naturally JACK wasn't working when I tried it in my next setup.  I entered the line below in Setup for Server Path and it started working.  Not sure if it was a coincidence, but it was recommended in the post below.

/usr/bin/jackd -S

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

