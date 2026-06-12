---
title: "Finishing Fixing my Firewire Follies"
date: 2010-05-30
forum: Ubuntu Studio
---

### Post by swedstal on 2010-05-30
I have been working with my new firewire interface (Phonic helix 18 mkII) and thanks to help from the forums, I now have it cooperating with Jack and Ardour. My next hurdle is to get the interface to work with system sounds, such as playing something with VLC or a youtube video. When I go to System -> Preferences -> Sound and click the 'Hardware' tab, the only card displayed is my on board card. I do not understand why the firewire card should not be listed here. Any ideas?

---

### Post by thorgal on 2010-05-31
hi there.
The only way to get sound from firewire is with jack. There is no alternative.

If you want system sounds through your firewire, I suggest you get inspired from my little alsa-2-jack bridge:

[http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge](http://alsa.opensrc.org/index.php/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge)

the trick is to use a virtual ALSA card that is in fact a loopback device. The bridge is using alsa_in and alsa_out to talk to jack. Once you get the bridge working, set your system sound to use the default ALSA device. This will "automagically" redirect the sound to jack.

This trick is very similar to pulseaudio's jack sink and source except that you don't need to involve pulseaudio at all.


EDIT: by the way, there's maybe another alternative. If the system sounds are using gstreamer (which I think is the case in GNOME based environments), you can set the gstreamer-properties to use jack. If you haven't got it installed, you will need the package 'gnome-media' and some of the gstreamer plugin packages.

Look at this link: [http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html](http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html)

There's a paragraph describing how to connect gstreamer to jack. But note that this will only work for apps that use the gstreamer framework, which gnome uses for system sounds I think (I use KDE so I don't really know).

---

### Post by trulan on 2010-05-31
As thorgal said, the only way to get sound out of a firewire device in Ubuntu is through Jack, as the only firewire drivers that exist (Ffado or the old FreeBoB) only communicate with Jack.

You can set VLC to play back directly through Jack if you install the VLC-Jack package (look it up in synaptic), although it seems to not be able to make its own Jack connections for me when I'm using firewire, and I have to manually connect it via Qjackctl or Patchage (which is a pain because as soon as you stop playback the VLC Jack output disappears - so I have to start VLC playing, pause it, make Jack connections, drag the playing bar to the beginning (Don't hit rewind or playback stops, the jack output disappears, and you have to start all over.), and finally, un-pause it and you should get sound.  Like I said, it's a pain.)

I've tried using the Pulse-jack setup in FalkTX's ppa, but I've had limited success with my onboard soundcard and no success whatsoever with firewire.  I have yet to try thorgal's alsa-2-jack bridge, but it sounds like a very good idea, keeping pulse audio out of the mix when using firewire.  Pulse just doesn't seem to play well with Jack/Ffado at this point - or else I don't know what I am doing (which is a very real possibility.)

**Update:**
I was indeed able to get system sounds working through firewire using the jack and pulse packages from falktx's ppa.  And I have some theories about my previous failures, but first,

I wasn't able to get the alsa loopback device working - but I'm using a self-compiled 2.6.33.4-rt20 kernel, which complicates things I am sure.  The only version of alsa-drivers which will compile with my kernel is the latest, which of course does not match the one I have installed.  I'm suspicious that that's my problem.

Anyway, back to Pulse-Jack-Ffado:  I have all the relevant packages upgraded from here:  [https://launchpad.net/~falk-t-j/+archive/lucid]("https://launchpad.net/%7Efalk-t-j/+archive/lucid")
Using this setup, Pulse autmatically calls jackd, using the info in /home/<username>/.jackdrc.  My problem is I'm constantly switching between my onboard card and my firepod, and I usually use Qjackctl to control Jack (which of course suspends pulse audio).  So I had to learn to kill the malfunctioning Jack, restart it from a terminal with the correct command (ah, how gui's make us sloppy...), and restart Pulse Audio.  So far it's been hit or miss, but once it's up and running everything seems to work quite well.

I think the biggest problem is just that it takes a few seconds to start jack with ffado, and by the time it is up and running, Pulse has called it a day.  At least that's how it is on startup - But if I kill jack (killall jackd), restart Jack via terminal (and make sure it is working properly), then restart pulseaudio (pulseaudio -k)(which actually kills it too but it immediately respawns), with a little luck I can do such things as play quadrapassal and have the blips and bleeps come out of my firepod instead of my laptop speakers.

I suspect that if I understood how everything is being automatically called (and in what order), this would all look a lot simpler than it does now.  Sorry for the rambling post - I must have hit '-vvv' instead of '-v' ;)

---

### Post by swedstal on 2010-06-04
Thank you so much trulan and thorgal for your responses. I have been a bit busy so I will see if I can get this running tonight or tomorrow. It does make sense that the only thing firewire communicates to is JACK. I seems that every problem I run into, I am learning more about JACK and the OS in general. The help from this forum makes it a good stage to be in!

---

### Post by mango42 on 2010-06-06
[QUOTE="trulan"]So I had to learn to kill the malfunctioning Jack, restart it from a terminal with the correct command (ah, how gui's make us sloppy...), and restart Pulse Audio.[/QUOTE]

GUI's make humanity in general far more productive in whatever field we're attempting, IMO. In the case of UbuntuStudio and the like, I suppose it depends whether making music or building the tools to make music is the priority ;-)

Ok, I finally admit to having once been a programmer (early '80's but why I am not anymore is another story) and I do realise that, without dedicated tools, coding GUI's can be nearly half the work involved in an application *but* the results, if sufficiently ergonomic, enable more of us to dedicate ourselves to creativity rather than technical detail. Imagine a commandline-only DAW...

I can't...

Now back to trying to get anything to work properly on 64bit Lucid Studio... Without posts like yours, **trulan** and **thorgal**, I wouldn't even attempt it! :popcorn:

---

