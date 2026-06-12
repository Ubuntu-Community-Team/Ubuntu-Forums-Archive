---
title: "Trouble getting JACK to work in UbuntuStudio 10.04"
date: 2010-06-22
forum: Ubuntu Studio
---

### Post by Smithernz on 2010-06-22
I've recently installed Ubuntu Studio on my mildly aged laptop, and have  been playing about with it, so I am very inexperienced. Sadly, I have had no luck getting JACK to  work. I have read the various 'HowTo's about it, but these haven't  really been much use.

This is what I get when I load up the JACK Audio Connection Kit:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]22:49:07.608 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:49:07.659 Statistics reset.[/COLOR]
 [COLOR=#999999]22:49:07.740 Startup script...[/COLOR]
 [COLOR=#990099]22:49:07.741 artsshell -q terminate[/COLOR]
 [COLOR=#66CC99]22:49:07.746 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:49:08.143 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:49:08.144 JACK is starting...[/COLOR]
 [COLOR=#990099]22:49:08.144 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2 -S[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    563640
 [COLOR=#999999]22:49:08.184 JACK was started with PID=2267.[/COLOR]
 [COLOR=#CCCC99]22:49:08.347 ALSA connection change.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 `default' server already active
 [COLOR=#999999]22:49:08.568 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]22:49:08.568 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:49:08.569 killall jackd[/COLOR]
 [COLOR=#999999]22:49:08.987 Post-shutdown script terminated successfully.[/COLOR]
 [COLOR=#FF0000]22:49:10.353 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I do have Start JACK audio server on application startup checked, which is why I'm guessing it does this at startup as well as when I click Start.

When typing uname -a into the terminal, I get this:

Linux ubuntustudiolaptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Is the "-generic" bad? This is the impression that I get from [https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart](https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart) , where I found the command.

Please help, as I don't know what I'm doing wrong. I can upload a screenshot of my settings if this would help. Also, what are Xruns, as I seem to be getting confusing definitions, and they seem very important.

---

### Post by RaumTrug on 2010-06-22
could you, in a terminal, right after jack refuses to start, try "lsof | grep pcm" to see if some application is already using the soundcard? if it spits something out, close that application & retry. also settingwise, in qjackctl choose for "interface" the soundcard you wish to use (hw:0,0, best use the ">" button next to the interface field) is safest bet in case there's only one...

an x-run is nothing more or less than a situation, where the program (jack, or a prog using it for in/output) fails to supply/read the data to/from the soundcard in time for playback/recording. if that happens, you'll have a click/dropout in the sound, or in worst case (bad prog) the recording/playback will stutter & run slower than expected. happens of course, when the audio progs try to do more work on the cpu than it can do (in time), or with hardware problems (driver not ready in time), which is worse, or when the latency is too low for the system to handle.

edit: "generic" kernel is not bad, it just sometimes cannot handle very low latencies (= delay between reading audio -> processing audio -> output of audio) as stable as the rt ones. also for good midi fiddling (midi-keyboards/controllers) in realtime, a rt kernel is much better, because of its finer clocking resolution.

---

### Post by Smithernz on 2010-06-22
Nope, nothing comes out after  lsof | grep pcm  . I've also changed Interface to hw:0,0 and have tried all the other options there, but have had no success!

---

### Post by RaumTrug on 2010-06-22
oops, my fault, the "default server already running" is not related to the soundcard already in use as it seems :P

what does "ps ax | grep jackd" say? there could be another instance already running in the background, possibly crashed/hung...

---

### Post by bluesscream on 2010-06-22
> 22:49:08.144 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2 -S
You are much more advanced then most beginners. But if you are on a midly aged machine you might not become lucky with above settings. Edit .jackdrc in your home/user directory like this:
'-T -P89 -p512 -t1000 -dalsa -dhw:0 -r44100 -p128 -n3 -Xseq'
p128 is minimum. 
or more user-friendly just set frames/period =>128 and periods/buffers 3 in qjackctl

good luck

---

### Post by Smithernz on 2010-06-23
ps ax | grep jackd  gives me:
1511 pts/0    S+     0:00 grep --color=auto [COLOR=Red]jackd[/COLOR]

I made the changes to .jackdrc, but it still failed. Any more ideas?

Thanks!

---

### Post by luctor on 2010-06-23
Are you running jackd with Jack Control ? (qjackctl)
Then I think editing the .jackdrc doesn't have any effect.
Adjust the settings in the Jack Control app, much easier.
I also think you are better off running the RT kernel and run jack with Real Time priority, you can enable is in Jack Control.

---

### Post by Smithernz on 2010-06-23
I've made the changes in Jack Control, but this has not helped either.

I have Realtime selected, but as I said in my first post, I am not sure whether I am running RT Kernel or not (does what I said in my first post in this thread suggest that in fact I am not running RT Kernel? If I am not, then how do I start it???

---

### Post by Pablo_F on 2010-06-23
Hi, 

/usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2 -S 

Afaik, this implies you are already running jackd with the realtime option. If not, it would be a "-r" in the command.
This doesn't mean you have to run a realtime kernel, although it certainly may help getting lower latencies without x-runs. Try to get jackd running first without the realtime kernel, and then consider installing it. (synaptic, install linux-rt and restart with it in the grub options, if you want to try).

64 frames per period is very low. No wonder jackd doesn't start, unless you have a good souncard and an rt kernel with high audio hardware priority which is not the case right now. Start much less conservative. 1024, for example. buffers per period, 2, or 3. 2 is good on most systems, 3 can help sometimes.

priority default is not a bad choice for starters. 
 
-S option is weird, you only want to force 16 bits when you are limited in disk space and you don't mind capturing with a lower quality even if your card is 24 bit capable. OTOH, if your card is not 24 bit capable I don't think it makes a difference if you choose this option or not. I would uncheck this.

Jack configuration depends a lot on your hardware, as well as on your software system. There is not a universal setup. If you give the outputs of the following informative commands, we will be able to give a better help.

$ uname -r
$ ulimit -r (rtprio limit for the user). 
$ ulimit -a (memlock limit "" "" ""). OK, I see, unlimited.
$ lspci | grep -i audio  (your audio cards, pci)
$ lsusb (you usb devices, in case your audio card is USB)
$ cat /proc/asound/cards (your audio cards, detected by alsa)

Cheers! Pablo

---

### Post by Smithernz on 2010-06-23
uname -r  gave:
2.6.32-22-generic

ulimit -r  gave:
99

ulimit -a  gave:
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 99
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

lspci | grep -i audio  gave:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

lsusb  gave:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

cat /proc/asound/cards  gave:
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC250 at irq 17

I hope this helps!

---

### Post by AutoStatic on 2010-06-23
Thanks for the info. You have an AC'97 onboard card. So you'll probably have to raise your Frames/Period setting way higher like 1024, maybe 512 but don't expect to get it any lower without JACK nagging :(
These old onboard chipsets aren't well suited for realtime audio stuff.

---

### Post by Smithernz on 2010-06-23
I have raised my Frames per period to 1024 and then even to 4096, but it is still not working.

---

### Post by RaumTrug on 2010-06-23
what boggles me is the "`default' server already active" message in the first post. it should normally indicate that a jack server with the server name "default" is already running (I think jackd is designed to run multiple instances, each with its own name...), but the "ps ax | grep jackd" gives no result (other than grep running with that parm)! ...but I'm no command line wiz, maybe that ps command won't list jackd's startet as root?

does jack still fail with that particular message?

now I've seen that the o.p. mentioned the "run jack at startup" option, please try to disable it, reboot & use qjackctl or terminal instead to fire up jack manually. something goes wrong there somehow :(

---

### Post by Pablo_F on 2010-06-23
Oops! I meant "ulimit -l" for the memlock value. a stands for "all", so the info is there, all the same. PAM limits are not the problem here.

I don't see why jack doesn't start with 1024 frames or even more. Anyway, please, give the info on your jack settings when you post. These are reflected in a command line that you can see (from a default user terminal) with:

$ cat .jackdrc

Or else, paste the whole messages window.

Also, please, complete the info with these commands:

$ cat /proc/asound/modules
$ aplay -l


Another question, have you tried with the realtime kernel?

Consider joining #ubuntustudio IRC channel on irc.freenode.net to get help in real time (no pun intended). You can use pidgin or xchat, or even the internet browser, URL:
[http://webchat.freenode.net/](http://webchat.freenode.net/)

EDIT: RaumTrug, I think he refers to the option in the "Others" Tab, so that the jack server starts when you start qjackctl, without the need of pressing the "Start" button. This is for convenience but it doesn't make any difference.

Cheers! Pablo

---

### Post by Pablo_F on 2010-06-23
> what boggles me is the "`default' server already active" message in the first post.

Aham, but maybe the "default server" refers not to jack but to another server? Pulseaudio?

It is weird because qjackctl launches pasuspender.

With that error, what is the output of

$ ps ax | grep pulse
$ ps ax | grep alsa


?

---

### Post by Smithernz on 2010-06-24
Right, sorry for not replying for a little while, GCSEs have required my full attention.

cat .jackdrc gives:
/usr/bin/jackd -p128 -t1000 -dalsa -dhw:0,0 -r44100 -p1024 -n3

cat /proc/asound/modules  gives:
0 snd_intel8x0

aplay -l  gives:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Pablo_F, no, I have not tried running it with RT-kernel. Or at least I don't think I have.

When I press start in qjackctl, I get the following message:
22:43:30.473 Startup script...
22:43:30.474 artsshell -q terminate
sh: artsshell: not found
22:43:30.877 Startup script terminated with exit status=32512.
22:43:30.878 JACK is starting...
22:43:30.878 /usr/bin/jackd -p128 -t1000 -dalsa -dhw:0,0 -r44100 -p4096 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    563640
22:43:30.910 JACK was started with PID=2177.
no message buffer overruns
JACK compiled with System V SHM support.
`default' server already active
22:43:31.219 JACK was stopped with exit status=1.
22:43:31.220 Post-shutdown script...
22:43:31.220 killall jackd
22:43:31.644 Post-shutdown script terminated successfully.
22:43:32.953 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

The System Monitor now tells me that I am running the process jackd, but that it has a "zombie" status. While I'm guessing this isn't as sinister as the name suggests, is it bad?


Finally:

ps ax | grep pulse  gives:
 1471 ?        S<sl   0:04 /usr/bin/pulseaudio --start --log-target=syslog
 1481 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 2211 pts/0    S+     0:00 grep --color=auto pulse

ps ax | grep alsa  gives:
2213 pts/0    S+     0:00 grep --color=auto alsa

Hope this extra info helps!

---

### Post by RaumTrug on 2010-06-24
I've just had some boredom & sparetime and checked the sources of jack 0.118.0 (not the apt-get source "ubuntu version", but the release version from the official jack website due to lack of a running lucid) out of curiosity, it seems this message is indeed related to another jack server with the same "server name" already existant in the system. at least it should be, normally... ;D

I think other programs like alsa servers or pulseaudio can't interfere there.

some technical stuff:

look in jack sources, jackd.c line 728, there a new server is about to be registered, and when return value suggests there's another with the same name, the above error message will be generated & exit.

further in, in shm.c line 410 is the only place where the return value that indicates another jack existing is triggered from the registering function, when in the jack transprocess-sharedmem infothingie there's another server with the same name (in this case "default"), that reacts to being sent signal "0" (probe signal if I understand correctly).

so there must be either another jack server running on the system, or something got really messed up elsewhere (in the jack shm info, for example, or corrupted data somewhere, a jackd process refusing to be killed, another "user" running jack...) :(

smitherenz, could you reboot your pc, and try starting jack again, having made sure you disabled automatic jack startup _everywhere_, and using conservative parameters/settings befor starting it? does it still give the "`default' server already active" msg the first time you try starting then?

if it does, can you try to start jackd with an additional "-n test" parameter (tries to give the new server the name "test", choose any...)?

edit: okie, kill that zombie & try again! :P

---

### Post by Smithernz on 2010-06-24
So here is what I just did:
[LIST]
[*]Rebooted.
[*]Checked the system monitor, and jackd was not running.
[*]Loaded qjackctl, and left the settings as shown in the print screen attachment.
[*]Tried to start JACK and got the normal message:
23:27:11.933 Startup script...
23:27:11.933 artsshell -q terminate
sh: artsshell: not found
23:27:12.336 Startup script terminated with exit status=32512.
23:27:12.337 JACK is starting...
23:27:12.337 /usr/bin/jackd -p128 -t1000 -dalsa -dhw:0,0 -r44100 -p4096 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
23:27:12.361 JACK was started with PID=2022.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    563640
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|4096|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
23:27:13.070 JACK was stopped successfully.
23:27:13.071 Post-shutdown script...
23:27:13.071 killall jackd
23:27:13.073 JACK has crashed.
jackd: no process found
23:27:13.737 Post-shutdown script terminated with exit status=256.
23:27:14.574 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
[/LIST]

So not much luck there. After this there was no sign of the zombie, but when it is here, I am unable to stop the process.

Where do I need to use the -n test??? Do I need to run i from the terminal, and if so, with what?

---

### Post by RaumTrug on 2010-06-24
nah, forget about the "-n servername" test, it could be added to the server path thing I guess, but as you found the "zombie" it's probably more important to get rid of the cause of it instead of creating yet more....maybe you can add "--verbose" to the jackd path to get more info, but I'm not sure if that would work this way ;)

maybe it could run with 2 periods/buffer, and also 512 frames/period, and 48000 sampling rate as a start. mine card crashes with certain settings, too, like 3 periods or too many frames/period. and I remember some hda_intel cards can't really run 44100 but only 48000 stable.

good luck!

---

### Post by VH-BIL on 2010-06-24
> `default' server already active
You might be trying to start a second instance of jack

---

### Post by RaumTrug on 2010-06-25
vh-bil, yep that's what we already found out. in the background there's another jackd that crashed & got "zombified", which is pretty bad, and blocks another jack from being started ;)

smitherenz: you might be able to kill the "zombie" jackd somehow, look here: [http://ubuntuforums.org/showthread.php?t=314592&](http://ubuntuforums.org/showthread.php?t=314592&) for a little discussion on what might do the trick. often not easy, though, I bet you're already pretty tired of rebooting all the time ;)

if you're in bad luck, jack doesn't like your sound card/alsa driver at all, and fixing that would probably be beyond scope of this forum :(

---

### Post by VH-BIL on 2010-06-25
> **RaumTrug said:**
> vh-bil, yep that's what we already found out. in the background there's another jackd that crashed & got "zombified", which is pretty bad, and blocks another jack from being started ;)

smitherenz: you might be able to kill the "zombie" jackd somehow, look here: [http://ubuntuforums.org/showthread.php?t=314592&](http://ubuntuforums.org/showthread.php?t=314592&) for a little discussion on what might do the trick. often not easy, though, I bet you're already pretty tired of rebooting all the time ;)

if you're in bad luck, jack doesn't like your sound card/alsa driver at all, and fixing that would probably be beyond scope of this forum :(

That has happened to me before and I just did a killall on it. if it doesn't work I run the command again. The process will end.

---

### Post by Smithernz on 2010-07-03
Right, sorry for the long delay (again). I've been extreemly busy lately and haven't been able to get to my laptop. I have installed Ubuntu Studio on my PC, as my laptop was just a testing ground, and Jack is working fine I think, so thanks for all the help, but I think I may call it quits and give up on my laptop. It's so old and and I never use it anyway, but thanks very much to everyone who has helped, and I'm sorry again for not persisting!!

---

### Post by RaumTrug on 2010-07-03
nevermind not staying at it, and I wish you lots of fun with the desktop & not too many encounterings with strange bugs anymore!

the "jack has crashed" one is a very generic errormessage, anyways. I think jack just doesn't like what your old soundchip driver is doing somewhere, or the driver is buggy somewhere. maybe as a last thing for my personal interest, if you still got that laptop up with ubuntu, add the "verbose output" (or whatever it is called in english, the option in the lower left corner) option before starting jack on that laptop, and paste the, now more detailed, "messages" info here. "I just wanna see where jack craps out..." ;)

I'm on a desktop where I've had to deactivate a similliar _old_ intel soundchip, because the sound quality was poor as possible, & jack didn't like it too much either. got a compatible pci card & now things roll. if you ever need to get good sound with the laptop, you might consider getting some (linux compatible, do research first & ask in forums) usb or pcmcia soundchip for it. many gadges don't work, and many are flaky.

good luck!

---

### Post by Smithernz on 2010-07-06
Ok, verbose messages gives me this:
12:05:19.947 Startup script...
12:05:19.948 artsshell -q terminate
sh: artsshell: not found
12:05:20.350 Startup script terminated with exit status=32512.
12:05:20.351 JACK is starting...
12:05:20.351 /usr/bin/jackd -v -p128 -t1000 -dalsa -dhw:0,0 -r48000 -p512 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    563640
12:05:20.374 JACK was started with PID=1739.
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x90e5260 fd = -1
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
start poll on 3 fd's
12:05:22.233 JACK was stopped successfully.
12:05:22.234 Post-shutdown script...
12:05:22.235 killall jackd
12:05:22.236 JACK has crashed.
12:05:22.519 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
jackd: no process found
12:05:24.988 Post-shutdown script terminated with exit status=256.

Hopefully that helps. While I would love not to have any more random bugs, I have a feeling that is a bit optimistic. For example, I have just noticed that, intriguingly, my Chromium Web Browser crashes when Jack crashes sometimes, and refuses to work if this is the case. Maybe that's just fluke though...!!!

Thanks very much again!

EDIT: Sorry about double post. Chromium crashed when I clicked Post (Yes, Jack had just crashed too!?!?!). Maybe it is more than fluke...

---

### Post by Smithernz on 2010-07-06
Ok, verbose messages gives me this:

12:05:19.947 Startup script...
12:05:19.948 artsshell -q terminate
sh: artsshell: not found
12:05:20.350 Startup script terminated with exit status=32512.
12:05:20.351 JACK is starting...
12:05:20.351 /usr/bin/jackd -v -p128 -t1000 -dalsa -dhw:0,0 -r48000 -p512 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    563640
12:05:20.374 JACK was started with PID=1739.
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
new client: alsa_pcm, id = 1 type 1 @ 0x90e5260 fd = -1
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
start poll on 3 fd's
12:05:22.233 JACK was stopped successfully.
12:05:22.234 Post-shutdown script...
12:05:22.235 killall jackd
12:05:22.236 JACK has crashed.
12:05:22.519 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
jackd: no process found
12:05:24.988 Post-shutdown script terminated with exit status=256.

Hopefully that helps. While I would love not to have any more random bugs, I have a feeling that is a bit optimistic. For example, I have just noticed that, intriguingly, my Chromium Web Browser crashes when Jack crashes sometimes, and refuses to work if this is the case. Very odd. Maybe I ought to report it!

Thanks very much again!

---

### Post by AutoStatic on 2010-07-06
Try **(default)** in the Interfaces field instead of **hw:0,0**
Or maybe **hw:I82801DBICH4** works too.

---

### Post by Smithernz on 2010-07-06
Nope. Neither worked, and chrome crashed again when Jack did!

---

### Post by AutoStatic on 2010-07-06
Could you try running jackd without having resource intense stuff open like Chrome?

---

### Post by Smithernz on 2010-07-09
I doesn't work even without them running.

---

### Post by JackSchnippes on 2010-07-24
Hi guys[B],
[/B]
I guess this is a quick one, but I can't find my mistake. I installed jackd, qjackctl and linux-rt (from a regular Ubuntu, not Studio), but i get this error:

 p, li { white-space: pre-wrap; }  ```
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
```

jack suggests I edit _/etc/security/limits.conf_, but the ubuntu help pages say at jack installation things will be set up in _/etc/security/limits.d/audio.conf_. The latter looks right to me:

```
# generated by jackd's postinst.
#
# Do not edit this file by hand, use
#
#    dpkg-reconfigure -p high jackd
#
# instead.
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```

BUT as you can see the limits don't apply, although I use the right kernel and I'm in audio group. see for yourselves.
[B]
uname -r:[/B]
2.6.31-11-rt

**ulimit -l:**
64

**ulimit -r:**
0

**groups:**
simon adm dialout cdrom audio video plugdev games users lpadmin sambashare admin nogroup

thanks for any hints! :(

---

### Post by cchhrriiss121212 on 2010-07-24
Try adding the lines to the limits.conf as well and see if that makes a difference. You need to reboot for these changes to take effect.

---

### Post by Pablo_F on 2010-07-24
Hi, 

If you have the relevant lines in /etc/security/limits.d/audio.conf, adding them to /etc/security/limits.conf won't make a difference.

[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html)
says:

>  By default limits are taken from the /etc/security/limits.conf  config file. Then individual *.conf files from the /etc/security/limits.d/  directory are read

Of course, you don't lose anything if you try.

The question:

Are you using SLIM (simple login manager) instead of gdm?

Not long ago I helped a user in #ubuntustudio irc channel who had the same problem. It seems that SLIM does not support PAM (at least by default) and does not load pam_limits.so. More info here:

 [http://meandubuntu.wordpress.com/2008/09/06/xfce-slim-pam-and-jack/](http://meandubuntu.wordpress.com/2008/09/06/xfce-slim-pam-and-jack/)

Cheers! Pablo

---

### Post by crimzon on 2010-07-24
](*,)

I'm having a very similar problem with JACK, and with everything audio related on a fresh Studio 10.04 install. I'll be on the IRC in a bit, but posting here for posterity.

I am getting NO AUDIO OUTPUT after fresh install with Ubuntu Studio. Strangely enough, audio works fine with regular 10.04 Desktop install. Sound device(s) are recognized, I hear an occasional "pop" from my speakers, unrelated to anything I'm doing.

Dear God, this new PC is the most frustrating machine I've ever assembled. ] :frown:

My chipset is AMD 880/850. Is this un-compatible with the studio preempt kernel? I'm so very lost in the Ubuntu Forest. I just want to listen to my music while I get the rest of this machine functional for video editing. Thanks to anyone who can point me in a productive direction.

 ;)

---

### Post by Pablo_F on 2010-07-24
crimzon: If listening to music is the only thing related to music that you need, definitely, forget about jack.
 
In addition, you are better off with a generic kernel even if I don't think that the sound problem is related to the kernel, but anyway you just don't need it. 

The fact is: If jackd (JACK in short) is running, you and everyone else in the world will not have audio from any non-jackified app. And multimedia players are not jackified by default, even in ubuntustudio (although it is easy to do it).

My suggestion is that you install the video editing programs in the ubuntu generic and enjoy your music thanks to the ubuntu's default audio server, pulseaudio.

That said, it could be that you need jack for very specific works. For example ardour + blender is a powerful combination. But hey, start simple. 

Mind you, if you insist on using jack, ask again and we will try to help. But then, please try to be more informative on your description. 

Cheers! Pablo

---

### Post by LuisAugusto on 2010-08-03
> **Pablo_F said:**
> 
The fact is: If jackd (JACK in short) is running, you and everyone else in the world will not have audio from any non-jackified app. And multimedia players are not jackified by default, even in ubuntustudio (although it is easy to do it).


This isn't true anymore, you can make jack work with pulse-audio.

---

### Post by PetteriP on 2010-08-07
Hi, guys

I'm having very similar - if not identical - problem.
Jackd does not start and crashes other applications on the way.

From qjackctl messages:
> 16:46:29.331 Patchbay deactivated.
16:46:29.404 Statistics reset.
16:46:29.541 ALSA connection graph change.
16:46:30.057 ALSA connection change.
16:46:32.174 Startup script...
16:46:32.175 artsshell -q terminate
sh: artsshell: not found
16:46:32.577 Startup script terminated with exit status=32512.
16:46:32.578 JACK is starting...
16:46:32.578 /usr/bin/jackd -P25 -dalsa -dhw:0 -r44100 -p1024 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
16:46:32.600 JACK was started with PID=1973.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    769446
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
16:46:33.272 JACK was stopped successfully.
16:46:33.273 Post-shutdown script...
16:46:33.274 killall jackd
16:46:33.275 JACK has crashed.
jackd: no process found
16:46:33.683 Post-shutdown script terminated with exit status=256.
16:46:34.671 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

uname -r
> 2.6.32-23-generic

ulimit -r
> 99

ulimit -a
> core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 99
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

ulimit -l
> unlimited

cat .jackdrc
> /usr/bin/jackd -P25 -dalsa -dhw:0 -r44100 -p1024 -n2
pee@Wayne:~$ cat /proc/asound/modules
 0 snd_intel8x0
29 thinkpad_acpi

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep -i audio
> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

cat /proc/asound/cards
>  0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 11
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 1RHT71WW-3.04

ps ax | grep pulse
>  1377 ?        S<sl   0:00 /usr/bin/pulseaudio --start --log-target=syslog
 1389 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 2146 pts/0    S+     0:00 grep --color=auto pulse

ps ax | grep alsa
>  2148 pts/0    S+     0:00 grep --color=auto alsa

As you can see the configuration is very similar to Smithrenzs. Only I don't get "'default' server already active"-stuff - which he didn't get either after killing all the zombies. I had some as well earlier, no more though, and still failing to start jackie-boy.

The message window states
> Memory locking is unlimited - this is dangerous. You should probably alter the line:
@audio - memlock unlimited
in your /etc/limits.conf to read:
@audio - memlock 769446
This I already have done, with no apparent effect.
...the file itself actually can be found in /etc/security/limits.conf...

I am planning to use this machine for small-time home studio activity so would be helpful to have Mr. Jack up and running.

---

### Post by t0rment2004 on 2011-03-06
I get this. Running 10.10 on a Lenovo R61i.

15:38:30.710 Patchbay deactivated.
15:38:30.746 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
15:38:30.773 ALSA connection graph change.
15:38:30.980 ALSA connection change.
15:38:34.236 Startup script...
15:38:34.237 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
15:38:34.639 Startup script terminated with exit status=32512.
15:38:34.639 JACK is starting...
15:38:34.640 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
15:38:34.658 JACK was started with PID=3355.
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
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfe100000 irq 45
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
15:38:34.928 JACK was stopped with exit status=255.
15:38:34.929 Post-shutdown script...
15:38:34.930 killall jackd
jackd: no process found
15:38:35.389 Post-shutdown script terminated with exit status=256.
15:38:36.832 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

"lsof | grep pcm" reveals this.

david@ds:~$ lsof | grep pcm
pulseaudi 1821      david  mem       CHR      116,6                7702 /dev/snd/pcmC0D0p
pulseaudi 1821      david   40u      CHR      116,6      0t0       7702 /dev/snd/pcmC0D0p
david@ds:~$ 

I'm sure this is really simple but I'm stupid. :P

---

### Post by Pablo_F on 2011-03-06
Hi, 

You are not stupid :). A posible solution:

In a terminal:

echo "autospawn=no" > ~/.pulse/client.conf

As the "script on server start" in qjackctl's setup, options tab, instead of the useless "artshell -q terminate":

pulseaudio -k

Cheers, Pablo

---

### Post by t0rment2004 on 2011-03-06
Is there something I have to do in the terminal before that?

When I put 'echo "autospawn=no" > ~/.pulse/client.conf' and press enter nothing happens, it just makes another entry line.

---

### Post by sgx on 2011-03-07
> **t0rment2004 said:**
> Is there something I have to do in the terminal before that?

When I put 'echo "autospawn=no" > ~/.pulse/client.conf' and press enter nothing happens, it just makes another entry line.
Hi, most commands that are successful don't generate any output, but
lots of it when the smallest error is typed in :)

I'd love to have a Charley Sheen "duh, WINNER!" sound play, every time
I typed like I made it past 3rd grade :)

---

### Post by sgx on 2011-03-07
> **Pablo_F said:**
> Hi, 

You are not stupid :). A posible solution:

In a terminal:

echo "autospawn=no" > ~/.pulse/client.conf

As the "script on server start" in qjackctl's setup, options tab, instead of the useless "artshell -q terminate":

pulseaudio -k

Cheers, Pablo
Hi, the aqualung music player autoconnects to jackd, its handy to
quickly add a track to an existing song using timemachine to record
your instrument, along with aqualung playing a song, or drumtrack etc

Cheers :)

---

