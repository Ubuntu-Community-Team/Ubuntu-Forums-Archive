---
title: "MusE can't connect to jack server"
date: 2011-08-24
forum: Ubuntu Studio
---

### Post by HKei on 2011-08-24
I am using Natty Narwhal. After installing the MusE package, I installed jackd1 (removing jackd2 in the process) because with jackd2, MusE would refuse to start up at all (it would just show me this little box telling me that it can't connect to jack and then commit seppuku). Now it does start, but it still can't connect to jack. Though I gotta admit I am new to MusE as well as to jack, so I may very well be doing something very wrong. New as in, I know about either since roughly an hour in which I've been trying to get the two to work together. Basically, all I know about jack is that it's some sort of audio daemon that MusE needs.

jack: 
```
hannes@hannes-laptop:~$ jackd
jackd 0.120.1
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    3037224
jackd 0.120.1
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --no-realtime OR -r ]
             [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
      (the two previous arguments are mutually exclusive. The default is --realtime)
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --no-sanity-checks OR -N ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --replace-registry ]
             [ --silent OR -s ]
             [ --version OR -V ]
             [ --nozombies OR -Z ]
         -d backend [ ... backend args ... ]
             Available backends may include: alsa, dummy, freebob, firewire, net, oss, sun, or portaudio.

       jackd -d backend --help
             to display options for each backend

```MusE
```
hannes@hannes-laptop:~$ muse
Denormal protection enabled.
cannot connect to jack server
cannot create jack client
Trying RTC timer...
fatal error: open /dev/rtc failed: Keine Berechtigung
hint: check if 'rtc' kernel module is loaded, or used by something else
Trying ALSA timer...
AlsaTimer::initTimer(): best available ALSA timer: system timer
got timer = 52
open projectfile: Datei oder Verzeichnis nicht gefunden
starting with default template
  name2route: <alsa_pcm:playback_1> not found
addRoute: invalid dst
  name2route: <alsa_pcm:playback_2> not found
addRoute: invalid dst
Get alsa timer for dummy driver:
AlsaTimer::initTimer(): best available ALSA timer: system timer
AlsaTimer::setTimerTicks(): warning: requested 86 Hz, actual freq is 100 Hz
audio dummy thread _NOT_ running SCHED_FIFO
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 100)
  freq stays at 100 Hz
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
Attempting to auto-start LASH server
lash_dbus_service_connect_handler: Failed to connect to LASH server: The name org.nongnu.LASH was not provided by any .service files
show did you know dialog!!!!

```

---

### Post by HKei on 2011-08-24
Nvm - I actually just reinstalled QJackCtl (I removed it after it seemingly didn't work with jackd1 for some reason), and it actually works just fine now. Well, I wouldn't say fine, but at least it doesn't give me any errors right now.

EDIT: Yeah, saying that it works was maybe a bit exaggerated. Now muse doesn't complain anymore, but in exchange the moment I start jack, no sounds work anymore (no system sounds from Ubuntu, no sounds from flashplayer, nothing). So uh... that's... pretty bad, no? If someone knew how to fix that/how to find out what's wrong and THEN fix that, I would really appreciate that. (Everything goes back to normal only if I stop the server AND exit QJackCtl - pretty weird, I'd have thought stopping the server would be enough).

---

### Post by madeinfamous on 2011-08-24
allo HKei!

so... you can't read and search?

the 10th treads bellow yours...

anyway,

> the moment I start jack, no sounds work anymore (no system sounds from Ubuntu, no sounds from flashplayer, nothing). So uh... that's... pretty bad, no?

everything's fine and work as expected!

just follow this:  [http://ubuntuforums.org/showthread.php?p=11176545#post11176545](http://ubuntuforums.org/showthread.php?p=11176545#post11176545)

have a nice day! 

:)

---

### Post by HKei on 2011-08-24
I searched for the muse thing, and I searched stuff about jack too, but I didn't know anything about PulseAudio. It's not like that kind of information is just shoved into your brain the moment you install Ubuntu :O

Now the sound output works again, but MusE doesn't work anymore...
```
hannes@hannes-laptop:~$ muse
Denormal protection enabled.
SSE2 detected
Trying RTC timer...
fatal error: open /dev/rtc failed: Keine Berechtigung
hint: check if 'rtc' kernel module is loaded, or used by something else
Trying ALSA timer...
AlsaTimer::initTimer(): best available ALSA timer: system timer
got timer = 54
starting with default template
  name2route: <alsa_pcm:playback_1> not found
addRoute: invalid dst
  name2route: <alsa_pcm:playback_2> not found
addRoute: invalid dst
JACK: buffersize changed 1024
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 100)
  freq stays at 100 Hz
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
looping waiting for sequencer thread to start
Attempting to auto-start LASH server
lash_dbus_service_connect_handler: Failed to connect to LASH server: The name org.nongnu.LASH was not provided by any .service files
Speicherzugriffsfehler

```

---

### Post by madeinfamous on 2011-08-24
allo again HKei!

I won't judge you in any way, I was just passing a comment! ;)

welcome to the community!

we all pass by the same road, learning! it's a good thing! 

unfortunately I can't help with Muse! I'm not familiar with it 'cause I dont use it!

someone will pass by and help you, be patient! 

:)

---

