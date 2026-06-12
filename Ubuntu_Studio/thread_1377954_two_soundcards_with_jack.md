---
title: "two soundcards with jack"
date: 2010-01-10
forum: Ubuntu Studio
---

### Post by jocampo on 2010-01-10
Two soundcards with jack is that possible? found a similar thread here but was closed and too old.

I have mixxx running on Ubuntu Studio with Jack. I also have an UCA202 audio interface (via usb port) I use it to plug my headphones but I also want to redirect audio via integrated laptop speakers. Only choice I have on mixxx, using Jack is "system"... for both ... mic and playback sound so I get an error and ended with 1 choice only.

How can I use Jack for both, my UCA202 and mixxx itself, has anyone accomplished that before?

I'm running 

jackd version 0.116.1 tmpdir /dev/shm protocol 24
mixxx 1.7
Ubuntu Studio Karmic 64bit (Linux studio 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux)

Thanks in advance,

---

### Post by AutoStatic on 2010-01-11
> **jocampo said:**
> Two soundcards with jack is that possible?You can use two different soundcards as input or output devices as long as they use the same backend (ALSA, FFADO).

> **jocampo said:**
> How can I use Jack for both, my UCA202 and mixxx itself, has anyone accomplished that before?This can't be done with JACK, you have to use plain ALSA. Maybe it can be done with a .asoundrc file but I'm not so familiar with that. The problem is you cannot have two different soundcards as an output device in JACK. But maybe I'm wrong, haven't played around that much with multiple soundcards and JACK.

---

### Post by thorgal on 2010-01-11
something CAN be done with jack. 

Jack1: use alsa_in / alsa_out utilities (jack >= 0.116.x, provided that it was compiled against libsamplerate)

Jack2: use the audioadapter in-process client

I have a couple of threads with details (using jack2). Here is one example:

[http://www.backports.ubuntuforums.org/showpost.php?p=7093866&postcount=2](http://www.backports.ubuntuforums.org/showpost.php?p=7093866&postcount=2)

screenshot (from my alsa_in/out post):

[http://ubuntuforums.org/attachment.php?attachmentid=110183&d=1240052591](http://ubuntuforums.org/attachment.php?attachmentid=110183&d=1240052591)

---

### Post by AutoStatic on 2010-01-11
Just installed the alsa_in/alsa_out utilities (ok, I'm using Fedora 12 right now) and the ability to create extra in- and outputs opens up a whole lot of possibilities. Thanks thorgal!

Did a quick test with a C-Sound USB soundstick and the command **alsa_out -j csound -d hw:1 -c 2**, see the attachment.

---

### Post by thorgal on 2010-01-11
you're welcome :)
Note that I never really checked the quality of the resampling in my case (I use 96kHz for my RME system but the onboard can only 48kHz so there was on-the-fly resampling -> overhead varying with resampling quality). However, in case you cannot sinc' both cards via h/w clock, it is a good way to expand for extra monitoring or other purposes.

---

### Post by jocampo on 2010-01-11
THank you both guys!!!

I'll check tonight after work and let you know

---

### Post by jocampo on 2010-01-11
Folks,

I just checked those links from my work (my linux laptop not close) so i got two questions/comments

So, to install from Ubuntu Studio I need to follow these steps:

```

sudo apt-get install alsa_in alsa_out

```

And then, 

```

alsa_out -j csound -d hw:1 -c 2

```


Where "hw:1" is what or which one??? ... my UCA202 or the integrated sound card? also what is the meaning of the "-c 2" flag ... Do i need to run this command before opening mixxx and after starting jack with GUI?

Thanks,

---

### Post by thorgal on 2010-01-11
```

cat /proc/asound/cards

```

will tell you what is what.

-c 2 may mean : 2 channels. Not sure as I am using jack2 with the audioadapter where many of these things are automatic (for what I know).

```

alsa_out --help

# or

alsa_out -h

```

may give you some help.

For the starting order, you can set this up in qjackctl.
I think it is in the Misc tab in the setup window.
You can add this command in the post-startup field.
You can also add a "killall -9 alsa_out" in the pre-shutdown field.

---

### Post by jocampo on 2010-01-11
> **thorgal said:**
> ```

cat /proc/asound/cards

```

will tell you what is what.

-c 2 may mean : 2 channels. Not sure as I am using jack2 with the audioadapter where many of these things are automatic (for what I know).

```

alsa_out --help

# or

alsa_out -h

```

may give you some help.

For the starting order, you can set this up in qjackctl.
I think it is in the Misc tab in the setup window.
You can add this command in the post-startup field.
You can also add a "killall -9 alsa_out" in the pre-shutdown field.

Thanks quick reply Thorgal

So, order should be

1.Install alsa_in/alsa out via apt-get
2.Start Jack
3.Start mixxx

if script is not included on Jack, then

1.Install alsa_in/alsa out via apt-get
2.Start Jack
3.Run that additional line for the 2nd card, from terminal
3.Start mixxx

?

---

### Post by thorgal on 2010-01-11
yes

---

### Post by AutoStatic on 2010-01-11
Unfortunately alsa_in and alsa_out are not available for Ubuntu: [https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/502116](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/502116)

So you have to either install jack2 or find another way, maybe compiling the tools yourself or maybe there's a PPA that has them.

---

### Post by jocampo on 2010-01-11
> **AutoStatic said:**
> Unfortunately alsa_in and alsa_out are not available for Ubuntu: [https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/502116](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/502116)

So you have to either install jack2 or find another way, maybe compiling the tools yourself or maybe there's a PPA that has them.

You are right about that

So, still, if I'm able to install Jack2 and compile, do I need to take an extra step for alsa_in / alsa_out?

---

### Post by thorgal on 2010-01-11
be careful about having home-compiled jack's in your system.

Right now, you probably use the ubuntu-shipped jack1.

Compiling alsa_in and alsa_out (for jack1, I don't think they would work with jack2 at all) requires that you compile the whole jack stuff.

If you already use jack2, then it's another story. But if you plan to switch to jack2, make sure you get version 1.9.4, at least. The problem with the switch would be to remove jack1. jack2 and jack1 CANNOT coexist AT ALL. 

So assuming that you are using jack1, I would recommend you compile alsa_in and alsa_out :

```

sudo apt-get build-dep jackd
sudo apt-get source jackd
sudo apt-get install libsamplerate0-dev

```

(I believe ubuntu forgot to compile jackd against libsamplerate).

then enter the jackd source directory and compile it :
./configure
make

don't install it, just look inside the "tools/.libs" subdirectory (mind the . )

there should be alsa_in and alsa_out. Make sure they are linked correctly, e.g.:

```

ldd ./alsa_in

```

if you have something like "not found" in the list of libs it is linked to, then it will not run.

If it is fine, copy them to where you have jackd installed:

```

sudo cp alsa_in  alsa_out  /usr/bin

```

This whole thing is a bit crude but it should work ;)

---

### Post by jocampo on 2010-01-11
> **thorgal said:**
> be careful about having home-compiled jack's in your system.

Right now, you probably use the ubuntu-shipped jack1.

Compiling alsa_in and alsa_out (for jack1, I don't think they would work with jack2 at all) requires that you compile the whole jack stuff.

If you already use jack2, then it's another story. But if you plan to switch to jack2, make sure you get version 1.9.4, at least. The problem with the switch would be to remove jack1. jack2 and jack1 CANNOT coexist AT ALL. 

So assuming that you are using jack1, I would recommend you compile alsa_in and alsa_out :

```

sudo apt-get build-dep jackd
sudo apt-get source jackd
sudo apt-get install libsamplerate0-dev

```

(I believe ubuntu forgot to compile jackd against libsamplerate).

then enter the jackd source directory and compile it :
./configure
make

don't install it, just look inside the "tools/.libs" subdirectory (mind the . )

there should be alsa_in and alsa_out. Make sure they are linked correctly, e.g.:

```

ldd ./alsa_in

```

if you have something like "not found" in the list of libs it is linked to, then it will not run.

If it is fine, copy them to where you have jackd installed:

```

sudo cp alsa_in  alsa_out  /usr/bin

```

This whole thing is a bit crude but it should work ;)

Too late! lol ... screwed up my system already , hahahaha..

I tried to do that during my lunch hour at home and I think it was a very bad idea. These are the steps I followed

1.Downloaded Jack 1.9
2.Compiled and installed Jack from source (README file said, it was going to upgrade prior version)

So, I started it and looks like everything was running fine but when opening mixxx, I lost "jack" sound api. So .. I reinstalled mixxx from source again and now Jack stop working :-( ...

Before doing 1 and 2 I thought in removing Jack's ubuntu studio version but that action was going to remove a lot of stuff as well, including ardorous I think so I abort that crazy idea.Instead, I decided to download and installed Jack 2.

How can I revert these changes? should I re-install Jack from repositories? mixxx 1.7 looks like is still working but no more "Jack sound api". Like I said before, Jack server/daemon is no longer working.

---

### Post by thorgal on 2010-01-11
> **jocampo said:**
> Too late! lol ... screwed up my system already , hahahaha..

I tried to do that during my lunch hour at home and I think it was a very bad idea. These are the steps I followed

1.Downloaded Jack 1.9
2.Compiled and installed Jack from source (README file said, it was going to upgrade prior version)

So, I started it and looks like everything was running fine but when opening mixxx, I lost "jack" sound api. So .. I reinstalled mixxx from source again and now Jack stop working :-( ...

Before doing 1 and 2 I thought in removing Jack's ubuntu studio version but that action was going to remove a lot of stuff as well, including ardorous I think so I abort that crazy idea.Instead, I decided to download and installed Jack 2.

How can I revert these changes? should I re-install Jack from repositories? mixxx 1.7 looks like is still working but no more "Jack sound api". Like I said before, Jack server/daemon is no longer working.


ouch! it hurts! :lol:


OK, go back to the jack 1.9 source and do this:
```

sudo ./waf uninstall

```

then reinstall the ubuntu package:

```

sudo apt-get install --reinstall libjack0 jackd

```

hopefully, it will take care of the mess :)

---

### Post by RaumTrug on 2010-01-11
I'm using jack2, mainly because of that nice audioadapter (alsa_in/out clickered like hell on my system!!!). only downside is that audioadaptered devices have a little worse sound quality due to resampling (high freqs), so they are best used for extra monitoring ports that don't get recorded...also it seems like they introduce a little extra delay, I think, but maybe I've used the dmix (default) alsa device lat time I've tested ;-P

I've just deleted certain files from jackd, libjack and libjack-dev manually (or jack2 will complain about drivers/modules from jack1), locked those packages with synaptic, and then compiled jack2 & waf installed...not you'll need to "./waf configure --prefix=/usr/" to make it install over the jack1 stuff, or you'll have 2 jacks sitting there, one in /bin/ and one in /usr/bin!!

this link explains a little how to do it that dirty way: 
[http://linuxmusicians.com/viewtopic.php?f=19&t=1010](http://linuxmusicians.com/viewtopic.php?f=19&t=1010)
, but it's not really clean and such, and will get update/upgrade problems probably...

isn't there a ppa for jack2 somewhere that takes care of replacing the old jack packages, without having to uninstall all progs depending on it??? or a way to edit checkinstall .deb's so they replace the old packages? would be cool, feels strange to have a borked up system (at least jack doen't get updated :P)

---

### Post by jocampo on 2010-01-11
> **thorgal said:**
> ouch! it hurts! :lol:


OK, go back to the jack 1.9 source and do this:
```

sudo ./waf uninstall

```

then reinstall the ubuntu package:

```

sudo apt-get install --reinstall libjack0 jackd

```

hopefully, it will take care of the mess :)


Thanks, I had to reboot (don't know why) but fixed the issue ;-) ...

So... before break my system again , lol , let me ask this. I do have Jack1. Can I compile and install the new version on top of this or do I need to take an extra step? If I understood well, these are the steps (in order) that I must follow

```

sudo apt-get build-dep jackd
sudo apt-get source jackd
sudo apt-get install libsamplerate0-dev

```

Then, compile/install jack2

```

sudo ./waf install

```

after that, mixxx should be able to see jack api and I should be able to play with connections and redirect audio to two different sound cards

---

### Post by thorgal on 2010-01-12
no,

don't install jack2 on top of jack1. Just follow what I described:

- keep ubuntu's jack1 (don't even think about anything jack2 at any time)
- get jack1 source via apt-get
- compile it but don't install it
- copy alsa_in and alsa_out to /usr/bin

PS: the lack of alsa_in and alsa_out is a mistake from the ubuntu jack1 packager. AutoStatic provided a link toward the bug report. Hopefully, the ubuntu packager will listen.

---

### Post by AutoStatic on 2010-01-12
> **RaumTrug said:**
> isn't there a ppa for jack2 somewhere that takes care of replacing the old jack packages, without having to uninstall all progs depending on it???Maybe here: [https://launchpad.net/~frasten/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~frasten/+archive/ppa?field.series_filter=karmic)
Isn't Trulan using JACK from that PPA? Maybe he could post his findings. I'm still ok with jack1. I could compile alsa_in and alsa_out though and try packaging them, just set up a Karmic chroot to package stuff. 64bit or 32bit?

---

### Post by eric71 on 2010-01-12
Thorgal,

I'm currently using some packages from the 64 Studio hardy-backports repository where they have Jack2 (1.9.3) available. I'm at work now, so I can't test it, but I am curious about something. In your example you linked to, you start jackd with hw:1 and then hw:0 is brought into the picture with the "jack_load onboard audioadapter" command. Does the audioadapter plugin just automagically connect to the other available card without having to specify the device, like you would have to with alsa_in? If I start jack with qjackctl, telling it to use my onboard hw:0, and I occassionally wish to add a usb mic (hw:1),will a command like "jack_load usbmic audioadapter" do that for me?

---

### Post by thorgal on 2010-01-12
not sure, I haven't used it for a while.

Try this to get some parameter help

```

jack_load audioadapter "-h"

```

---

### Post by jocampo on 2010-01-12
> **thorgal said:**
> no,

don't install jack2 on top of jack1. Just follow what I described:

- keep ubuntu's jack1 (don't even think about anything jack2 at any time)
- get jack1 source via apt-get
- compile it but don't install it
- copy alsa_in and alsa_out to /usr/bin

PS: the lack of alsa_in and alsa_out is a mistake from the ubuntu jack1 packager. AutoStatic provided a link toward the bug report. Hopefully, the ubuntu packager will listen.

Ok sir, I won't :-)

But, having some issues here finding and moving the files you suggested

Ok,

I did this

```
sudo apt-get build-dep jackd
sudo apt-get source jackd
sudo apt-get install libsamplerate0-dev
```

and this is the only Jack folder I can find on my system:

```
jocampo@studio:~/jack-audio-connection-kit-0.116.1$ 
```

That's under my own home directory

Now, running this command

```
ocampo@studio:~/jack-audio-connection-kit-0.116.1$ sudo ./configure make

```
Give me this error
```
jocampo@studio:~/jack-audio-connection-kit-0.116.1$ sudo ./configure make
[sudo] password for jocampo: 
configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash config/config.sub make failed
```

I can't even find tools/.libs directory. What I'm doing wrong, any ideas???


*** EDITED ****
Stupid and nobbie error! I put make as a configure flag! disregard my ridiculous error, but let me try anyway copying alsa_in and alsa_out and see what happen

---

### Post by thorgal on 2010-01-12
hehe, you're a bit too fast ;)

I would like to see the content of the jack-audio-connection-kit directory

Could you post it here ?

About compiling:
You don't have to be root or superuser to configure and compile. sudo is to be used only when installing something in system wide areas (like /usr/bin). So avoid using sudo when calling ./configure because all the files that this action will create will have the superuser bits in their permission, not a very good idea ;)

In general, the compilation sequence is composed of 3 distinct commands:
```

./configure
make
sudo make install

```
in our case, we don't want the last install command. 

OK, first, show me the directory content.

---

### Post by AutoStatic on 2010-01-12
@jocampo, I also have a Karmic 64bit JACK package for you with alsa_in and alsa_out if you're interested. Saves you from compiling stuff, even though it's very instructive :)

[http://linux.autostatic.com/ubuntu/jackd_0.116.1-4autostatic1_amd64.deb](http://linux.autostatic.com/ubuntu/jackd_0.116.1-4autostatic1_amd64.deb)
[http://linux.autostatic.com/ubuntu/libjack0.100.0-0_0.116.1-4autostatic1_all.deb](http://linux.autostatic.com/ubuntu/libjack0.100.0-0_0.116.1-4autostatic1_all.deb)
[http://linux.autostatic.com/ubuntu/libjack0.100.0-dev_0.116.1-4autostatic1_all.deb](http://linux.autostatic.com/ubuntu/libjack0.100.0-dev_0.116.1-4autostatic1_all.deb)
[http://linux.autostatic.com/ubuntu/libjack0_0.116.1-4autostatic1_amd64.deb](http://linux.autostatic.com/ubuntu/libjack0_0.116.1-4autostatic1_amd64.deb)
[http://linux.autostatic.com/ubuntu/libjack-dev_0.116.1-4autostatic1_amd64.deb](http://linux.autostatic.com/ubuntu/libjack-dev_0.116.1-4autostatic1_amd64.deb)

---

### Post by jocampo on 2010-01-12
Thorgal / Autostatic

Thanks for help so far, appreciated!

Here's the content of my directory

```
total 1668
drwxr-xr-x 12 root    root      4096 2010-01-12 07:37 .
drwxr-xr-x 37 jocampo jocampo   4096 2010-01-12 08:34 ..
-rw-r--r--  1 root    root       902 2008-12-15 05:09 acinclude.m4
-rw-r--r--  1 root    root    275002 2008-12-15 05:09 aclocal.m4
-rw-r--r--  1 root    root      2412 2008-12-15 05:09 AUTHORS
drwxr-xr-x  5 root    root      4096 2010-01-12 07:37 config
-rw-r--r--  1 root    root      5070 2010-01-12 07:37 config.h
-rw-r--r--  1 root    root      4662 2008-12-15 05:09 config.h.in
-rw-r--r--  1 root    root     58185 2010-01-12 07:37 config.log
-rwxr-xr-x  1 root    root     39498 2010-01-12 07:37 config.status
-rwxr-xr-x  1 root    root    858938 2008-12-15 05:09 configure
-rw-r--r--  1 root    root     28155 2008-12-15 05:09 configure.ac
-rw-r--r--  1 root    root       271 2008-12-15 05:09 COPYING
-rw-r--r--  1 root    root     17992 2008-12-15 05:09 COPYING.GPL
-rw-r--r--  1 root    root     26518 2008-12-15 05:09 COPYING.LGPL
drwxr-xr-x  4 root    root      4096 2010-01-11 18:03 debian
drwxr-xr-x  3 root    root      4096 2010-01-12 07:39 doc
drwxr-xr-x 12 root    root      4096 2010-01-12 07:37 drivers
drwxr-xr-x  4 root    root      4096 2010-01-12 07:39 example-clients
drwxr-xr-x  2 root    root      4096 2010-01-12 07:37 jack
drwxr-xr-x  4 root    root      4096 2010-01-12 07:38 jackd
-rw-r--r--  1 root    root       289 2010-01-12 07:37 jack.pc
-rw-r--r--  1 root    root       288 2008-12-15 05:09 jack.pc.in
-rw-r--r--  1 root    root      6910 2010-01-12 07:37 jack.spec
-rw-r--r--  1 root    root      6896 2008-12-15 05:09 jack.spec.in
drwxr-xr-x  4 root    root      4096 2010-01-12 07:38 libjack
-rwxr-xr-x  1 root    root    219129 2010-01-12 07:37 libtool
-rw-r--r--  1 root    root     23699 2010-01-12 07:37 Makefile
-rw-r--r--  1 root    root       719 2008-12-15 05:09 Makefile.am
-rw-r--r--  1 root    root     23405 2008-12-15 05:09 Makefile.in
drwxr-xr-x  2 root    root      4096 2010-01-12 07:37 man
-rw-r--r--  1 root    root      1228 2008-12-15 05:09 README
-rw-r--r--  1 root    root        23 2010-01-12 07:37 stamp-h1
-rw-r--r--  1 root    root      4002 2008-12-15 05:09 TODO
drwxr-xr-x  4 root    root      4096 2010-01-12 07:39 tools
```

THat's what I get after compiling Jack, the Ubuntu repository version.

I copied alsa_in alsa_out to /usr/bin already. I tried to start Jack and started, but have no idea how to call or create output for the 2nd card. These are the sound cards I have right now

```
jocampo@studio:~/jack-audio-connection-kit-0.116.1$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 20
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:04.0-1, full s
```

---

### Post by thorgal on 2010-01-12
OK, there's some progress here :)

for the invocation of alsa_out, you need to read AutoStatic's post (something about some csound device). It should be straightforward.

look in [http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack](http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack)
(around bottom of the page)

and

[http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut)


The simplest way is to try (once jackd is started)
```

alsa_out -d hw:1 >& /dev/null

```

(I added the /dev/null thing because of the verbosity of the thing, I remember it was spitting out a lot of screen output).

hw:1 is your USB device and you want to have playback ports for it (thus the use of alsa_out, so you can redirect some audio to your USB headset if I understood correctly).

---

### Post by jocampo on 2010-01-12
> **thorgal said:**
> 
hw:1 is your USB device and you want to have playback ports for it (thus the use of alsa_out, so you can redirect some audio to your USB headset if I understood correctly).

Correct! :-)

hw1 is the UCA202 connected via USB. What I'm trying to do is redirect mixxx sound via integrated laptop speakers but, at same time, be able use my headphones (plugged into the UCA202) to hear master output and mix sounds. In other words, one card for speakers the other one for headphones. I'm able to do that WITHOUT Jack, just using mixxx options for mic and master, but not via "jack api"

At work now, I'll check later, hopefully I will make it work!

---

### Post by jocampo on 2010-01-12
Wohoooo!

Thorgal / AutoStatic, it worked, yeah!

I still need to do some fine tuning to set freq, sampling, etc, but I just started Jack via GUI and then ...

```
alsa_out -d hw:1 >& /dev/null
```

Omitting /dev/null keep putting output to my screen. 

The default command for my Jack (hw0 integrated card) is
```

/usr/bin/jackd -R -m -dalsa -dhw:0 -r44100 -p128 -n3 -P
```

which works on mixxx. I need to study options and commands for alsa_out so I can put 44100, 128 and 3 as parameters.

Thank you guys! Thanks a lot ... ;)

---

### Post by thorgal on 2010-01-13
congratulations :D

---

### Post by eric71 on 2010-01-14
I just wanted to follow up that I have managed to get alsa-in working quite nicely with a USB interface. So thank you to everyone here, especially Thorgal. I've been doing a lot of distro hopping in recent weeks, and this success has been using the Debian Squeeze jackd (0.118+svn3796-1), so I dind't have to do compiling. Despite all of my distro hopping, the best part about Ubuntu has always been the community. 

I hope the request to the Ubuntu packager to include alsa_in and alsa-out in the Ubuntu package isn't ignored. I've been missing the ability to do what something like asio4all allows in windows for a long time, and being able to do something simple like this without arcane modifications to alsa config files to make everything into one big sound card has been a revelation. I know it's not a pro level solution to adding extra inputs/outputs, but it is on par with what I used to do with asio4all in Windows.

One odd problem that I have run into is with Qjackctl. If I have Qjackctl execute the alsa_in command at startup or after startup(from the execute scripts part on the otions tab), Qjackctl locks up. I need to kill it and restart it, but when I do it it shows jack is running and the connections show the alsa_in mic. If I just run the alsa_in command from command line, or with the KDE menu's run dialog, Qjackctl has no problems.

---

### Post by thorgal on 2010-01-14
> **eric71 said:**
> 
One odd problem that I have run into is with Qjackctl. If I have Qjackctl execute the alsa_in command at startup or after startup(from the execute scripts part on the otions tab), Qjackctl locks up. I need to kill it and restart it, but when I do it it shows jack is running and the connections show the alsa_in mic. If I just run the alsa_in command from command line, or with the KDE menu's run dialog, Qjackctl has no problems.

I could try this out on my DAW PC (I always keep jack1_svn ready to be installed for testing). If qjackctl keeps crapping, then it is time to talk to Rui (the dev) :)

Confirmed. 

We need to notify Rui about this. 

PS: by the way, I do not get this crazy amount of screen output any longer when I invoke alsa_in/out. (I use jack1@svn and there must have been a lot of changes to alsa_in/out).

PPS: you guys make sure you use the audio card's name (given by ALSA). In my case, by issuing cat /proc/asound/cards, I see:

```

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe3220000 irq 22
1 [DSP            ]: H-DSP - Hammerfall DSP
                      RME Hammerfall DSP + Multiface at 0xe3000000, irq 22

```

so I use the names between [ ] (so as not to bother with card indexes):

```

jackd -blabla -dalsa -dhw:DSP -blabla

```

```

alsa_out -d hw:Intel

```

---

### Post by eric71 on 2010-01-14
I was meaning to mention the Qjackctl problem in the forum on his homepage today, if I got confirmation it wasn't just me and my mixing of packages. I'm using a Frankenstein moster of Mepis 8.5 beta4 (Lenny based with KDE 4.3.4 added) with the 64 Studio hardy-backports 2.6.31 realtime kernel, and have upgraded jack, qjackctl, and qsynth plus the few assorted dependencies they pulled in to Squeeze. So I couldn't quite be sure it was a real problem or something I created by my distribution mixing.

Thanks for the tip regarding naming of devices. It is very useful - I left my USB mic plugged in and rebooted, and it became hw:0 and my setup was backwards. I think Ubuntustudio prevents this, but in my Debian mishmash, it will be useful to use the names.

Another interesting thing is that the Squeeze jackd package, during installation, asks if you would like to enable realtime access and adds a /etc/security/limits.d config file with appropriate rtprio, nice and memlock settings. It would be cool if Ubuntu's package did that.

---

### Post by eric71 on 2010-01-14
Regarding the Qjackctl freeze: I reported it at Rui's forum and he had an easy solution - "Are you sure you aren't missing an ampersand (&) at the end of the alsa_in or alsa_out command lines ? You need that for any of those commands to run in the background, otherwise QjackCtl just gets stuck indefinitely while waiting for the scripts to terminate."

I haven't had a chance to confirm it yet, but I'm sure it will work. I hadn't appended an "&" to the alsa_in line.

---

### Post by thorgal on 2010-01-14
> **eric71 said:**
> Regarding the Qjackctl freeze: I reported it at Rui's forum and he had an easy solution - "Are you sure you aren't missing an ampersand (&) at the end of the alsa_in or alsa_out command lines ? You need that for any of those commands to run in the background, otherwise QjackCtl just gets stuck indefinitely while waiting for the scripts to terminate."

I haven't had a chance to confirm it yet, but I'm sure it will work. I hadn't appended an "&" to the alsa_in line.


hehe, that's the very first thing I tried after seeing the freeze myself. I did not mention it but the result was: no alsa_out showing up in the graph.


EDIT: retried it again, for the sake of answering in Rui's forum. And it worked this time. The alsa_out client must have blown on me the 1st time I tried it with &
Or maybe I did not tick the check button in the option window :lol:

---

### Post by Frank Carvalho on 2010-04-05
Hi

Found this thread in an attempt to make two M-Audio 2496 cards work together on my AMD64-based machine. I appreciate the ideas here, but it doesn't work for me. I downloaded the source for alsa_in and alsa_out, and compiled both (as well as all the other things in the package. Deployed in /usr/bin, but... both fail to start! I get errors in the initialisation of PCM. It says: 

lt-alsa_out: pcm.c:976: snd_pcm_delay: Assertion `pcm' failed.
Aborted

I looked into the source, and it seems that there is a function to check that the API of ALSA is readable, and apparently it is not. I do not have enough knowledge about ALSAs APIs.
I also notice a directive in the beginning of the C-code that declares that we are using an old ALSA API, before including .h-files for ALSA. So I assume that there is some ironing out there to do before it compiles. 

But I know too little about ALSA to start digging into this, and gave up. Instead I have an alternative suggestion for running multiple sound cards on the same machine. Configure it in ALSA itself, using .asoundrc. Here I found the solution that works for me on my two 2496 cards:

[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

The catch here is that it only works well, if the two cards are clocked by the same clock source. Now that is easy with ICE1712 cards, as they can both master and slave through the S/PDIF I/O, but other cards may need different solutions. However, using this solution, I can get a very large definition of system I/O in JACK that gives access to all I/O of both cards without alsa_in and alsa_out.

/Frank

---

### Post by sgx on 2010-04-05
Thanks for posting that link! If you get a chance, lspci output will
mention the revision number of your soundcards, mine is Rev 02,
curious if yours are newer and working, as I want a backup unit for
good luck, and knowing which revisions work will help ;)
Cheers

---

### Post by Frank Carvalho on 2010-04-05
Consider it done: 

01:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
01:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

It seems that both of mine are rev 02 as well and this works nicely. But the S/PDIF link is very important. Any interference, such as a bad or missing connection, immediately produces nasty clicking sound from the slaved card. It also makes the transport go wild. 

/Frank

---

### Post by sgx on 2010-04-06
Thanks, I'll be watching ebay and the like. ;)

---

### Post by thorgal on 2010-04-06
Hi Frank,

Which system do you have (OS version, kernel version, jack version) ?

alsa_in and alsa_out work perfectly in my system (latest jack2, 1.9.5 svn code, kernel 2.6.32 on a custom debian sid system).

You of course need jack running before you can lauch alsa_in and alsa_out. I think that the names of these apps is misleading. These jack clients have tunable parameters such a resampling quality so you should not get big distorsion due to sample rate mismatch between the cards, at a high quality resampling setting (but it is more CPU demanding, especially at small buffer sizes).

---

### Post by Frank Carvalho on 2010-04-06
> **thorgal said:**
> Hi Frank,

Which system do you have (OS version, kernel version, jack version) ?

alsa_in and alsa_out work perfectly in my system (latest jack2, 1.9.5 svn code, kernel 2.6.32 on a custom debian sid system).

You of course need jack running before you can lauch alsa_in and alsa_out. I think that the names of these apps is misleading. These jack clients have tunable parameters such a resampling quality so you should not get big distorsion due to sample rate mismatch between the cards, at a high quality resampling setting (but it is more CPU demanding, especially at small buffer sizes).

OS: Ubuntu Studio Karmic, AMD64, single core
Kernel: 2.6.31-9-rt
Jack is 0.116.1 - I am not running Jack2.

I know that Jack should be running. Otherwise alsa_in/out will not be able to report itself to the patchbay. But the multi card setup through ALSA works so well now that I want to keep it that way. Otherwise, I've had great success adding netjack to the equation. Starting alsa_netsource seems to works fine.

---

### Post by sonicolonic on 2010-04-14
> **AutoStatic said:**
> @jocampo, I also have a Karmic 64bit JACK package for you with alsa_in and alsa_out if you're interested. Saves you from compiling stuff, even though it's very instructive :)



Man, Jeremy... I should slap you. I just spent all of my free time at home the past couple of days banging my head against the wall and reading posts and code til my eyes bleed, trying to switch to US 9.10, get the HDSP to be recognized, breaking and reinstalling OSes, hacking .asoundrc, and compiling jackd (and/or jackdmp) from scratch.... and NOW I find out you've got a handy little package for this????!?!?!?

Yeah, this experience has been HIGHLY instructional. I think I see the light at the end of the tunnel though. I've got US 9.10 optimized, HDSP is functional, ice1712 is sync'd/slaved to the HDSP, made up alsa_in/alsa_out, put them in their directory, but when invoked it says I don't have permission. 

I had to leave it at that as I was running out the door but I'm hoping it's just a file permission issue. I'm hoping I just have to check the "make executable" box for the scripts and I'll be on my way. Might also be malformed invocation. 

That being said, what am I going to do once it works? Undo it and try to install JACK2... IF that doesn't break the ubuntustudio packge it's in. How do you make sure JACK1 is gone before installing JACK2, and which jackd binary is which so I can delete the one I'm not supposed to use?

I decided after my first 15 hour day working on 64Studio 2.1 last month trying to understand and get both soundcards to work that if I can figure this out in <40 hours, it'll save me the cost and simple connectivity of another Hammerfall card until I really need it, AND re-coup the cost of this older soundcard. 

Thanks guys for all your help!! I'm so close I can almost taste the sound...

~Brian

PS ~ Confucius say: When watching porno in Linux, little package comes in handy.

---

### Post by sonicolonic on 2010-04-14
I got  alsa_in/alsa_out installed on the system, jack 0.116.1, but when I run it I get 

```

sonicolonic@brobriopolis:~$ alsa_in -d hw:2,0
Enhanced3DNow! detected
SSE2 detected
Sample format not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
alsa_in: pcm.c:976: snd_pcm_delay: Assertion `pcm' failed.
Aborted
sonicolonic@brobriopolis:~$ 

```

Does this mean that jack didn't get compiled against libsamplerate? If so, I'm not sure how to do this then because I have that installed and the dev package too.

Ideas?

~Brian

---

### Post by thorgal on 2010-04-15
the problem seems more related to the hardware you try to access.

post the output of
```

cat /proc/asound/cards

```

then we'll have a chance to know what you've got in terms of h/w (hw:2,0 may well be the wrong "device")

---

### Post by sonicolonic on 2010-04-15
2,0 was the right device. I'd followed every how-to and made so many modifications and tweaked code and whatnot it could be anything. I basically spent 18 hours straight working on this and ended up uninstalling jack1 and installing jack2, which worked! 

There's one persistent error I'm getting across both installs which makes me think it's alsa related, or a config file or something, but I've done so much tweaking I have no idea what the last thing I did before the error. Now that I know what works and how to make it work, I might do a fresh install to clear that issue up and know I'm working with a cleaner system.

Here's that persistent error, except that jack seems to run fine. It shows up when I start qjackctl at the top before jackd is even called. 

```
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```Other than that, the ice1712 card has a bug with warbled audio and clicks but that's a whole other problem. Bottomline is I got JACK2 to record 16 tracks and look stable though a bit sluggish (depending on settings) doing so. And all thanks to you guys!!

If you have any ideas on the other two problems I can get you any details you want next time I'm at the studio. 

~Brian

---

### Post by cchhrriiss121212 on 2010-04-16
I had that error when I tried installing jack2, and it is trying to access settings left over from jack1. I solved it clearing out my .config files in  /home, but I would be interested where the settings for jack are stored (I simply deleted everything there).

---

### Post by sonicolonic on 2010-04-16
That's sounds about right. I'll give it a whirl next time I'm in the studio.

So you were concerned about deleting jack2's stored settings when deleting config files?

I think the command line settings from qjackctl are saved in .jackrc in your home folder. I do remember one time there being a discrepency between the file and the settings in jack control, but that might've been before I completely removed jack1 and was changing the settings for jack2.

I've got a couple of leads from the alsa wiki for the ice1712 that I can try sometime. 

You guys know any tricks for reducing cpu load after loading the 2nd soundcard?

~Brian

---

### Post by sonicolonic on 2011-01-03
Update here... I've got an RME Multiface and a Nuendo Audiolink. here.  Finally reinstalled UbuntuStudio 8.04 to get stable realtime  functionality. So far it's been pretty dern stable and low latency. I  installed jack 0.116.x along side whatever jack version comes with  Hardy, and that is working fine. What I find is I still can't get  alsa_in/alsa_out to work with my RME cards. I can add the onboard  soundcard np, but trying to add the other RME card gets me one of these  two errors:

```

sonicolonic@brobri:~$ ./alsa_out -d hw:0
Capture open error: Device or resource busy
lt-alsa_out: pcm.c:976: snd_pcm_delay: Assertion `pcm' failed.
Aborted
sonicolonic@brobri:~$ ./alsa_out -d hw:3
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
lt-alsa_out: pcm.c:976: snd_pcm_delay: Assertion `pcm' failed.
Aborted

```

I'm getting the same error as Frank here.

Here's this too... 
```

sonicolonic@brobri:~$ cat /proc/asound/cards
 0 [DSP            ]: H-DSP - Hammerfall DSP
                      RME Hammerfall DSP + Multiface at 0xfdae0000, irq 21
 1 [Finger         ]: USB-Audio - USB Trigger Finger
                      M-Audio USB Trigger Finger at usb-0000:00:12.1-2, full speed
 2 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 19
 3 [DSP_1          ]: H-DSP - Hammerfall DSP
                      RME Hammerfall DSP + Multiface at 0xfdad0000, irq 22

```

I  want to set the soundcard indexes so they're persistent across reboots,  but seeing as they use the same driver, I'm not sure how to specify  which actual device should be where. Minor detail.

I have been  able to use the second sound card for it's convertors and sync them via  spdif, 4-8 channels of adat lightpipe, seems to work fine. 

Thoughts?

~bb

---

