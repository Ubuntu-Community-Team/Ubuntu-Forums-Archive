---
title: "Jack-Cannot lock down memory area (Cannot allocate memory)"
date: 2010-12-04
forum: Ubuntu Studio
---

### Post by Fardin on 2010-12-04
Hello
I am new to digital audio.
I installed zynaddsubfx, LMMS, Rosegarden, jack control and Qsynth.
During installation, I was asked if I wanted lock down memory.
I did not choose that.
Now every time I open jack, it gives me a message that can not lock memory.
I did uninstall and reinstall everything named above, but this time I was not asked  if I wanted lock down memory.
I read on jack articles that I need to edit /etc/security/limits.conf.
When I tried that I got permission denied
then I tried:
su
and went into root directory
but there I also got permission denied.

How can I change this to lock down the memory in jack?

This is the message that appears when I start jack:

 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]09:42:20.979 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]09:42:21.197 ALSA connection change.[/COLOR]
 [COLOR=#999999]09:42:23.342 Startup script...[/COLOR]
 [COLOR=#990099]09:42:23.343 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]09:42:23.746 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]09:42:23.750 JACK is starting...[/COLOR]
 [COLOR=#990099]09:42:23.751 /usr/bin/jackd -P10 -p128 -t2000 -dalsa -dhw:0 -r44100 -p2048 -n2 -S[/COLOR]
 [COLOR=#999999]09:42:23.766 JACK was started with PID=1972.[/COLOR]
 Cannot create thread 1 Operation not permitted
 Cannot create thread 1 Operation not permitted
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|16bit
 Using ALSA driver ICH4 running on card 0 - Intel ICH5 with AD1980 at irq 17
 configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 AcquireSelfRealTime error
 [COLOR=#999933]09:42:25.835 Server configuration saved to "/home/mao/.jackdrc".[/COLOR]
 [COLOR=#999999]09:42:25.836 Statistics reset.[/COLOR]
 [COLOR=#999999]09:42:25.877 Client activated.[/COLOR]
 [COLOR=#9999cc]09:42:25.930 JACK connection change.[/COLOR]
 [COLOR=#cc9966]09:42:25.942 JACK connection graph change.[/COLOR]
 Cannot lock down memory area (Cannot allocate memory)

---

### Post by madeinfamous on 2010-12-04
allo Fardin,

if jack is still install, just do:

sudo dpkg-reconfigure -p high jackd

it will then ask you again :)


edit: maybe it will not ask, but will created the file,

---

### Post by Fardin on 2010-12-04
> **madeinfamous said:**
> allo Fardin,

if jack is still install, just do:

sudo dpkg-reconfigure -p high jackd

it will then ask you again :)


edit: maybe it will not ask, but will created the file,

I did this"sudo dpkg-reconfigure -p high jackd"
it asked for my password
nothing happened after that
jack seems to be exactly the same?

---

### Post by madeinfamous on 2010-12-04
reallo fardin, 

i see you're in xubuntu, maybe it's a little different,

just wait a little,

someone way better than me will hopefully pass and give a proper answer.

have a nice day

---

### Post by cchhrriiss121212 on 2010-12-04
Try this:
sudo gedit /etc/security/limits.d/audio.conf

Now check you have these two lines present:
@audio   -  rtprio     95
@audio   -  memlock    unlimited

Save and reboot for changes to take effect.

---

### Post by Fardin on 2010-12-04
> **cchhrriiss121212 said:**
> Try this:
sudo gedit /etc/security/limits.d/audio.conf

Now check you have these two lines present:
@audio   -  rtprio     95
@audio   -  memlock    unlimited

Save and reboot for changes to take effect.


after this:
sudo gedit /etc/security/limits.d/audio.conf
I was asked for oassword
after entering password
I got:
sudo: gedit: command not found
??

---

### Post by cchhrriiss121212 on 2010-12-04
Gedit is just a text editor, so replace it with whatever editor Xubuntu comes with or just install gedit then try again.

---

### Post by Pablo_F on 2010-12-04
Wait a bit, it is MUCH easier if you just do:

**sudo dpkg-reconfigure -p high jackd2**

The last "2" is important. Then choose yes, you want to lock down memory and have rtprio scheduling privilege. This will add those lines automatically.

Now, you have to make sure you are in the audio group, so do a:
[B]
sudo adduser mao audio[/B]

supposing that mao is your user name.

Now, you have to reboot. 

Now, check that you have said privileges:

**ulimit -r -l**

Cheers! Pablo

PS: Anyway, it might be useful for you to know how to edit system files as Chris comments. In xfce the default editor is mousepad.

---

### Post by Fardin on 2010-12-07
> **Pablo_F said:**
> Wait a bit, it is MUCH easier if you just do:

**sudo dpkg-reconfigure -p high jackd2**

The last "2" is important. Then choose yes, you want to lock down memory and have rtprio scheduling privilege. This will add those lines automatically.

Now, you have to make sure you are in the audio group, so do a:
[B]
sudo adduser mao audio[/B]

supposing that mao is your user name.

Now, you have to reboot. 

Now, check that you have said privileges:

**ulimit -r -l**

Cheers! Pablo

PS: Anyway, it might be useful for you to know how to edit system files as Chris comments. In xfce the default editor is mousepad.

Thanks
**sudo dpkg-reconfigure -p high jackd2**
worked fine.
after entering
**sudo adduser mao audio**
a message came that mao was already a member of group
after
[B]ulimit -r -L
I got:
[/B]real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

Now when I run jack I get:
p, li { white-space: pre-wrap; } [COLOR=#999999]17:36:51.187 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:36:51.220 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:36:51.299 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]17:36:51.579 ALSA connection change.[/COLOR]
 [COLOR=#66cc99]17:36:51.583 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]17:36:57.594 Startup script...[/COLOR]
 [COLOR=#990099]17:36:57.595 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]17:36:57.999 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]17:36:58.000 JACK is starting...[/COLOR]
 [COLOR=#990099]17:36:58.001 /usr/bin/jackd -p128 -t2000 -dalsa -dhw:0 -r44100 -p2048 -n2 -S[/COLOR]
 [COLOR=#999999]17:36:58.043 JACK was started w[/COLOR]
[COLOR=#999999]
[/COLOR]
[COLOR=#999999]ith PID=1285.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|2048|2|44100|0|0|nomon|swmeter|-|16bit
 Using ALSA driver ICH4 running on card 0 - Intel ICH5 with AD1980 at irq 17
 configuring for 44100Hz, period = 2048 frames (46.4 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]17:37:00.208 Server configuration saved to "/home/mao/.jackdrc".[/COLOR]
 [COLOR=#999999]17:37:00.209 Statistics reset.[/COLOR]
 [COLOR=#999999]17:37:00.248 Client activated.[/COLOR]
 [COLOR=#9999cc]17:37:00.301 JACK connection change.[/COLOR]
 [COLOR=#cc9966]17:37:00.322 JACK connection graph change.[/COLOR]
which is great since it does not give me the last line it used to give me.

However I'm not sure what these mean:
[COLOR=#990099]17:36:57.595 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found

---

### Post by cchhrriiss121212 on 2010-12-08
That is normal, and jack is running correctly.

---

### Post by Fardin on 2010-12-08
Thank you both: Chris & Pablo
:popcorn:

---

