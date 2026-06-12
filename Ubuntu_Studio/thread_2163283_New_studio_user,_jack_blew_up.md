---
title: "New studio user, jack blew up"
date: 2013-07-17
forum: Ubuntu Studio
---

### Post by mashaffer on 2013-07-17
[COLOR=#000000]Hi, last night I installed Ubuntu Studio on my macbookpro4,1 with plans to use it with jOrgan virtual organ software. Last night I was able to start jack normally with Qjackctl (although jorgan didn't recognize that it was available). To day I allowed the system to do automatic updates (167 or so of them) and I also played around a little bit with keyboard settings (it started i-bus or something like that in the process).

Now jack is blown up and can't start jackd. I have been using pasuspender all alnong both when it was working and now. I checked this resouce

[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack)

and tried the [/COLOR][COLOR=#000000]**killall -9 jackdbus** command to no avail. Any ideas? Monitor output from QjackCTL follows.

mike [/COLOR][COLOR=#999999]

Statistics reset.[/COLOR]

 [COLOR=#cccc99]19:03:27.984 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:03:28.528 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]19:03:28.537 ALSA connection graph change.[/COLOR]
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]19:03:32.518 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Wed Jul 17 19:03:32 2013: Starting jack server...
 Wed Jul 17 19:03:32 2013: JACK server starting in realtime mode with priority 10
 Wed Jul 17 19:03:32 2013: Acquired audio card Audio0
 Wed Jul 17 19:03:32 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: Cannot initialize driver[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: Failed to open server[0m
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Wed Jul 17 19:03:34 2013: Saving settings to "/home/mike/.config/jack/conf.xml" ...
 [COLOR=#ff0000]19:14:06.039 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by mjhouska on 2013-07-17
How sad that we keep seeing posts like this. I'm not a jack guru, but as a jack-Ubuntu user I feel your pain my friend. I need to s tart writing down the jack fixes I learn from these forums. I use PC version though.


> **mashaffer said:**
> [COLOR=#000000]Hi, last night I installed Ubuntu Studio on my macbookpro4,1 with plans to use it with jOrgan virtual organ software. Last night I was able to start jack normally with Qjackctl (although jorgan didn't recognize that it was available). To day I allowed the system to do automatic updates (167 or so of them) and I also played around a little bit with keyboard settings (it started i-bus or something like that in the process).

Now jack is blown up and can't start jackd. I have been using pasuspender all alnong both when it was working and now. I checked this resouce

[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack)

and tried the [/COLOR][COLOR=#000000]**killall -9 jackdbus** command to no avail. Any ideas? Monitor output from QjackCTL follows.

mike [/COLOR][COLOR=#999999]

Statistics reset.[/COLOR]

 [COLOR=#cccc99]19:03:27.984 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:03:28.528 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]19:03:28.537 ALSA connection graph change.[/COLOR]
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]19:03:32.518 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Wed Jul 17 19:03:32 2013: Starting jack server...
 Wed Jul 17 19:03:32 2013: JACK server starting in realtime mode with priority 10
 Wed Jul 17 19:03:32 2013: Acquired audio card Audio0
 Wed Jul 17 19:03:32 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: Cannot initialize driver[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Wed Jul 17 19:03:32 2013: [1m[31mERROR: Failed to open server[0m
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Wed Jul 17 19:03:34 2013: Saving settings to "/home/mike/.config/jack/conf.xml" ...
 [COLOR=#ff0000]19:14:06.039 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2108): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by mjhouska on 2013-07-17
There will also be people claiming super low latencies with minimal xruns. Don't listen to them. They are full of ****. Whatever settings get jack running on your system is the optimal setting. They will try to convince you otherwise.

---

### Post by mjhouska on 2013-07-17
Don't get me wrong jack is a very powerful and useful too when it's working properly.

---

### Post by su:bhatta on 2013-07-19
Try the settings on this page & revert:
[https://help.ubuntu.com/community/Ub....Starting_Jack]("https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro#UbuntuStudio.2BAC8-ProAudioIntro.2BAC8-1204.Starting_Jack").

---

### Post by mashaffer on 2013-07-19
I am not sure what you mean by revert but I set up as close to that as fits with my setup, rebooted,  and had same results. Attached are the last setings I tried. If it matters both jackd and jackd2 are installed. Is it possible that the system updates installed a new jack or jackctl that is not compatible (say wrong bit size)?

installed jack pkgs...

mike@mike-MacBookPro:~$ dpkg -l | grep jack
ii  dssi-host-jack                        1.1.1~dfsg0-1                        amd64        Example of DSSI host
ii  jack-capture                          0.9.70-1                             amd64        program for recording soundfiles with jack
ii  jack-rack                             1.4.8~rc1-1ubuntu1                   amd64        LADSPA effects "rack" for JACK
ii  jackd                                 5                                    all          JACK Audio Connection Kit (default server package)
ii  jackd2                                1.9.9.5+20130127git15950eb1-1        amd64        JACK Audio Connection Kit (server and example clients)
ii  jackd2-firewire                       1.9.9.5+20130127git15950eb1-1        amd64        JACK Audio Connection Kit (FFADO and FreeBoB backends)
ii  libjack-jackd2-0:amd64                1.9.9.5+20130127git15950eb1-1        amd64        JACK Audio Connection Kit (libraries)
ii  libjack-jackd2-0:i386                 1.9.9.5+20130127git15950eb1-1        i386         JACK Audio Connection Kit (libraries)
ii  pulseaudio-module-jack                1:3.0-0ubuntu6                       amd64        jackd modules for PulseAudio sound server
ii  qjackctl                              0.3.9-2                              amd64        User interface for controlling the JACK sound server
ii  zita-ajbridge                         0.2.2-1                              amd64        alsa to jack bridge
ii  zynjacku                              6-4                                  amd64        JACK based host for LV2 synths and LV2 plugins

mike

---

### Post by mashaffer on 2013-07-19
Not sure how to mark this [Solved] but it is. It turned out to be uber simple. The audio device was not listed in the drop down menu in the setting. By pressing the arrow to the right of the field I got a complete list of devices and was able to select the right one (HW:1). Starts fine now.

Many thanks for the help.

mike

---

### Post by su:bhatta on 2013-07-20
See, thats why i provided that link...I am pretty new to Ubuntu Studio too... but i found out if you did everything mentioned on that page & played with your settings a bit then generally jack starts to behave himself ;)

So mark the thread as solved:
Go to post#1 and 'Edit" it...
2)once on 'Edit' page hit 'Advanced'...
From 'Advanced' page, you can change the 'Prefix' to 'Solved'

Glad to be of help...
Enjoy your Ubuntu Studio !

---

### Post by su:bhatta on 2013-07-20
If any thing with JAck gets on your nerves, please visit Jack Trac and read it up:

[http://trac.jackaudio.org/](http://trac.jackaudio.org/)

Just out of curiosity, no offence, what audio work do you want to do with U'Studio?
There is a great accompaniment application i found out, LinuxBand... You can have a look at it, if you want some midi accompaniment ...
[http://linuxband.org/](http://linuxband.org/)

---

### Post by mashaffer on 2013-07-20
Thank you Bhatta (BTW: Is that pronounced with soft "a" sound i.e. baa taa?),

Oddly enough it took someone on the jOrgan user community ([http://jorgan.999862.n4.nabble.com/jOrgan-User-f999863.html](http://jorgan.999862.n4.nabble.com/jOrgan-User-f999863.html)) pointing out the arrows for me to get it. Sometimes I can be a little dense. Thank you for the Jack Trac link. That looks very useful.

What I am doing is putting together an organ based on the jOrgan Virtual Organ Software ([http://sourceforge.net/apps/mediawiki/jorgan/index.php?title=Introduction](http://sourceforge.net/apps/mediawiki/jorgan/index.php?title=Introduction)) which takes input from midi devices like the Galanti Praeludium II organ console that I plan to use. It then provides a user interface to create an organ and uses a backend like fluidsynth to produce audio output. Lots of dispositions are available free of charge. Everything from small chamber organs to huge English Cathedral, American Classic, or Theater organs. There is even a Hammond B3 or two out there. A few excellent examples are here ([http://sourceforge.net/apps/mediawiki/jorgan/index.php?title=Stratman_Virtual_Instruments](http://sourceforge.net/apps/mediawiki/jorgan/index.php?title=Stratman_Virtual_Instruments)).

Even though it has midi record/playback capability its primary purpose is as a live instrument.

Some examples of JO in action.

[http://www.youtube.com/watch?v=IxTpYZT4B9E](http://www.youtube.com/watch?v=IxTpYZT4B9E) A nice Silberman disposition. Tres' Baroque
[http://www.youtube.com/watch?v=ZAdcbrwtYbY&feature=c4-overview&list=UULzx2N3WgoaRb7BmI9sC_9Q](http://www.youtube.com/watch?v=ZAdcbrwtYbY&feature=c4-overview&list=UULzx2N3WgoaRb7BmI9sC_9Q) Lots of good examples using different dispositions on this channel.

If you search youtube for "hauptwerk" you will find recordings of a similar commercial product. Many of those recordings are of better quality, probably in part due to the fact that those who can afford hundreds of dollars for software have better recording and audio equipment than those who need to use freeware but JO can sound excellent. :)

mike

---

### Post by mashaffer on 2013-07-20
I managed to create an mp3 of a midi performance included with Paul Stratman's English Cathedral Organ. The midi file using the built in midi player/recorder controls jOrgan to the point of pulling stops, playing keyboard and pedal notes, and operating swell pedals. The audio output is the same as if you played it on the instrument directly. I used jack to connect the jOrgan output directly into Audacity to create the mp3.

The mp3 is 3.3MB in size. I don't see a way to upload it here but if you are interested in listening to it we can arrange for me to send it via. email.

mike

---

