---
title: "Could not connect to Jack Server as Client ... etc"
date: 2011-05-10
forum: Ubuntu Studio
---

### Post by jda8818 on 2011-05-10
Hello All:

Fresh new 11.04 Studio Install, which went smoothly.  Up until today I've had some success with Jack, channeling a midi keyboard through ZynAddSubFx out through my built-in sound card (Asus P4C800E motherboard) and just feeling my way around.  Today however, Jack won't start.  The guts of the messaging seems to be:

  ```

  [COLOR=#990099]19:45:54.454 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3 -Xseq[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started


```I must have broken it somehow; my question therefore becomes: How do I reset Jack to it's default values.  This whole install is only a few days old.  

Thanks in advance, and as always any and all comments or suggestions are appreciated!

JA

---

### Post by Sylos on 2011-05-11
Hello.

Do you have Pulse aduio operating? If you do then it maybe that pulse is hogging the soundcard hence jack cannot access it (unless you have already followed one of the work arounds.

Try shutting down any progs that may be using the soundcard (ie non jack media apps and any web browsers that might be using the soundcard) then try the following commands:

```
sudo killall pulseaudio
```

```
sudo alsa force-reload
```

If that works then you might want to investigate some other threads about making jack and pulseaudio play nicely together:

[http://ubuntuforums.org/showthread.php?t=1717272](http://ubuntuforums.org/showthread.php?t=1717272)

Hope that helps

---

