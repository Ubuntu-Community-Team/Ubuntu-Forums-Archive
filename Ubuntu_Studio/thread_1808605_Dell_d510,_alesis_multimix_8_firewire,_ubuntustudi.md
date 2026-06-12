---
title: "Dell d510, alesis multimix 8 firewire, ubuntustudio10.04 not working!"
date: 2011-07-20
forum: Ubuntu Studio
---

### Post by manundi on 2011-07-20
On ardour I get this [IMG]http://dl.dropbox.com/u/17275327/Kuvakaappaus.png[/IMG]

And here are the settings im using:
[IMG]http://dl.dropbox.com/u/17275327/Kuvakaappaus-1.png[/IMG]

Jack cannot work with my multimix: [IMG]http://dl.dropbox.com/u/17275327/Kuvakaappaus-3.png[/IMG]
And here Jack setup: 

[IMG]http://dl.dropbox.com/u/17275327/Kuvakaappaus-2.png[/IMG]

And jack message output as text:

p, li { white-space: pre-wrap; } [COLOR=#999999]21:05:33.322 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:05:33.358 Statistics reset.[/COLOR]
 [COLOR=#66CC99]21:05:33.434 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]21:05:33.636 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:05:39.348 Startup script...[/COLOR]
 [COLOR=#990099]21:05:39.348 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]21:05:39.750 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:05:39.750 JACK is starting...[/COLOR]
 [COLOR=#990099]21:05:39.751 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n3 -i8 -o2[/COLOR]
 [COLOR=#999999]21:05:39.754 JACK was started with PID=2600.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    569550
 jackd: unknown driver 'firewire'
 [COLOR=#999999]21:05:39.789 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]21:05:39.790 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:05:39.791 killall jackd[/COLOR]
 jackd: ei prosesseja
 [COLOR=#999999]21:05:40.199 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:05:41.849 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


Im linux noob but used to music computer hardware.  I tried to disable onboard sounds at bios but d510 bios has  not option for disabling sounds. (im sure about that). I could try to update bios (it will be hard because theres no easy way to do it with ubuntu) but im not sure if onboard sounds are the problem here. So wisemen pls help me!

-Miika, Finland

---

### Post by manundi on 2011-07-20
So i have had deleted jackd wirewire. So i installed it again. now i get this at jack : 
p, li { white-space: pre-wrap; } [COLOR=#999999]21:13:35.843 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:13:35.897 Statistics reset.[/COLOR]
 [COLOR=#66CC99]21:13:35.945 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]21:13:36.148 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:13:44.703 Startup script...[/COLOR]
 [COLOR=#990099]21:13:44.704 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]21:13:45.106 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:13:45.107 JACK is starting...[/COLOR]
 [COLOR=#990099]21:13:45.107 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r44100 -p128 -n3 -i8 -o2[/COLOR]
 [COLOR=#999999]21:13:45.111 JACK was started with PID=2828.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    569550
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 libffado 2.0.0 built Mar 31 2010 14:47:42
 [COLOR=#999933]21:13:47.226 Server configuration saved to "/home/manundi/.jackdrc".[/COLOR]
 [COLOR=#999999]21:13:47.228 Statistics reset.[/COLOR]
 [COLOR=#999999]21:13:47.278 Client activated.[/COLOR]
 [COLOR=#CC9966]21:13:47.297 JACK connection graph change.[/COLOR]
 02192322502: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
 [0m02193207597: [31mError (avc_avdevice.cpp)[  88] probe: Subunit info command failed
 [0mfirewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Resurssi ei tilapÃ¤isesti ole kÃ¤ytettÃ¤vissÃ¤)
 cannot continue execution of the processing graph (Resurssi ei tilapÃ¤isesti ole kÃ¤ytettÃ¤vissÃ¤)
 cannot continue execution of the processing graph (Resurssi ei tilapÃ¤isesti ole kÃ¤ytettÃ¤vissÃ¤)...

---

### Post by Pablo_F on 2011-07-20
Hi, 

According to the ffado site your card is not supported, but I am not an expert so better ask/search there.

Anyway, there are a couple of command line apps that help diagnose the audio firewire devices: ffado-diag and faddo-test from ffado-tools package.

Cheers, Pablo

---

### Post by manundi on 2011-07-20
[http://www.ffado.org/?q=usage/bydevice](http://www.ffado.org/?q=usage/bydevice)

Alesis
 MultiMix Firewire 

  


it is there... yes i might post ffado.com too. Cheers for the tip.
-Miika

---

### Post by manundi on 2011-07-20
[http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)
bah, but your right only 16 channel version reported to work.

---

### Post by manundi on 2011-07-20
[]("http://www.ffado.org/?q=devicesupport/list")_double_

---

