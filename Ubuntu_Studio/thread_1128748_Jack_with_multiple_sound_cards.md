---
title: "Jack with multiple sound cards?"
date: 2009-04-17
forum: Ubuntu Studio
---

### Post by OneSeventeen on 2009-04-17
I have Ubuntu 8.10 vanilla with Ubuntu-Studio installed and updated.

I haven't had time to mess with the rt kernel, so I'm still in vanilla kernel.  (nVidia card isn't recognized by rt kernel)

I've got my on-board sound card and a MobilePRE, and I'd like to use my MobilePRE to record and monitor, but I'd like to use my reference monitors to playback.

I know enough to fiddle with Jack connections and route the audio, but I can't figure out how to make Jack server see both my onboard audio and Mobile Pre at the same time.

Any tips?

**EDIT:** My temporary solution is to plug my reference monitors into the line-out of the mobile pre and only turn them up for previewing and editing... I was just hoping for something more graceful, and for the ability to play with multiple audio input and output devices at once.

---

### Post by thorgal on 2009-04-18
you need alsa_in, part of the netjack tools, which are now included in the jack 0.116.x serie.

alsa_in applied to your second sound card will make its inputs visible in the jack graph, under a new jack client. It is really convenient and I can only advise you look into this.

there's also an alsa_out tool, which will make the second sound card's outputs visible as well, so you can expand your physical output possibilities.

The idea of alsa_in and alsa_out were originally derived from netjack, so you could add another PC to the master jack graph via ethernet and alsa_in was used to make this extra PC's soundcard available in the master jack server. All this is working really nicely, I used it in my own studio. It may require that you recompile jack from source, if your version is too old. Can you check your jack version ?

from terminal : jackd --version


Here is an example in my own studio. Since I use jack2 (i.e. jackmp), alsa_in is following a slightly different scheme. So, I have two soundcards: an RME HDSP at hw:1 and an Intel HDA onboard at hw:0. I start jackd like this:

jackd -S -R -P 70 -dalsa -dhw:1 -p1024 -r96000 -n2 -X seq

That's the main jackd server and it runs all the time. Then from a terminal, if I want to bring the intel onboard chip, I do this:
```

jack_load onboard audioadapter

```

"onboard" is the name I want the chip to be called with in the jack graph (you can call it whatever you want of course)
"audioadapter" is a combination of the jack1 alsa_in and alsa_out tools. It is the name of the compiled in-process client library that replaces alsa_in and alsa_out.

So jack2 makes it much easier. The result is this (see image). I started mplayer as an example and connected its outputs to both the RME hdsp (where I have my studio speakers) and the onboard outputs (where I have some cheap speakers). the "audioadapter" will do the necessary resampling so you don't have to worry. When I have both sets of speakers connected to mplayer, I can clearly hear that the RME HDSP is way better at processing the audio!! If I try a very low latency which the HDSP card handles easily, the onboard starts to feel unhappy at processing small buffers so fast ... :lol:    

[ATTACH]110183[/ATTACH]

---

### Post by OneSeventeen on 2009-04-19
Very interesting, I'll have to check this out.  Is there a binary for Ubuntu, or did you compile from source?

I'm using Jackd 0.109.2, which was installed with ubuntustudio-audio on top of Ubuntu 8.10 are alsa_in and alsa_out available for that?

If I can get video working properly, I'm tempted to create a new partition for Ubuntustudio 9.04 when it comes out.

---

### Post by thorgal on 2009-04-19
Hi there,

I compiled jack2 myself, as well as other things for my DAW, because I started to follow some code developments in more details (when I have time, I plan to bring some improvements here and there in some apps like e.g. ardour).

As to a ubuntu package, I have no clue as I am not using ubuntu but debian sid. I had a quick look at packages.ubuntu.com and there does not seem to be an official jack2 (or jackmp or even jackdmp) package. Maybe ubuntu studio has one but it may be too old.

If you are interested in getting the latest jack2, I can help you out but you will have to do some things that you may not be used to, that could "scare" you a little if you are sort of new to linux / unix. It's because jack1 and jack2 cannot coexist together in the same installation. 
Since they provide the same API, jack apps would not tell the difference but if you are heavily relying on keeping your PC tidy regarding official packages, it make break this tidiness. However, it would not be critical at all as things would work. And in any case, you could easily go back to the current state of your installation.

So, what say you ? ;)

---

### Post by bobince on 2009-04-25
I compiled Jack 0.116.1 and copied the alsa_in/alsa_out commands out of the build. Works fine, though there's a nasty click when it realigns the clocks (ie. like an xrun in jack, except that xruns just give me much more acceptable little silences rather than loud clicks). With the default settings I got a *lot* of clicks, but fiddling with the parameters improved it to a pretty-much acceptable level:

    ```
~/.local/bin/alsa_in -j usbmic -d hw:1,0 -c 1 -f 100000 -m 1024
```

This is on Jaunty where the native Jack version matches the above, but the alsa_ commands are for some obscure reason not included. I don't know if it would also work on Intrepid, whose Jack predates the NetJack alsa_ commands being integrated.

---

### Post by thorgal on 2009-04-26
alsa_in and alsa_out need libsamplerate0 (and -dev) to be compiled and run. If the packaged libjack or jackd has been compiled without this dependency, then these tools will not be part of the package. That's at least my suspicion.

I just checked jackd source code:

in the directory tools, Makefile.am contains

```

if HAVE_SAMPLERATE
if HAVE_ALSA
NETJACK_TOOLS += alsa_in alsa_out
endif
dist-check-samplerate:
else
dist-check-samplerate:

```

So it does depends at least on libsamplerate and alsa.

---

### Post by bobince on 2009-04-26
> **thorgal said:**
> So it does depends at least on libsamplerate and alsa.

Indeed. Both of those are already dependencies of ubuntu-desktop, though, so it would seem reasonable to depend Jack on them.

---

### Post by thorgal on 2009-04-26
that's right. It's more an issue on the packager's side. If he/she did not have these dependencies installed, then jack would compile without them. One has to check how the packaging took place. There must be some configuration / compilation log for each package available in the repos. If you could have a look at the jackd packaging log files, you could see the root cause of the issue.

---

### Post by JDPP on 2009-07-01
Hi 
I tried 
jack_load onboard audioadapter
But I got 
could not load audioadapdter, status = 0x 1

I googled this message but nothing...
I'm on a 64studio distrib (basicly gnome / ubuntu jaunty) with 0.71 version on jackdmp.
Jack is lauched with input and outpu set on hw:1
as you, I want to load the on board sound (on an MSI U100).

any idea ?

---

### Post by thorgal on 2009-07-02
hi JDPP,
jackmp 0.71 is way too old. You will have to check out the source code and compile it. No other choice ATM I think.

---

### Post by JDPP on 2009-07-02
ok, so either I have to do the things you describe as :   "If you are interested in getting the latest jack2, I can help you out but you will have to do some things that you may not be used to, that could "scare" you a little if you are sort of new to linux / unix."  for jack one or jack two ....  ;)  Thanks for your help !

---

### Post by JDPP on 2009-07-03
In reference to [http://ubuntuforums.org/showthread.php?t=1128748](http://ubuntuforums.org/showthread.php?t=1128748) thread.

I checked the version in the apt directory, it says :
```
Package: jackd
Priority: optional
Section: sound
Installed-Size: 176
Maintainer: Nedko Arnaudov <nedko@arnaudov.name>
Architecture: i386
Source: jack-audio-connection-kit
Version: 1.8+0.71-0.64studio2~jaunty1
Provides: jack-server
Depends: libjackserver0 (= 1.8+0.71-0.64studio2~jaunty1), libjackserver-bin (= 1.8+0.71-0.64studio2~jaunty1)
Conflicts: jackdmp
Filename: pool/main/j/jack-audio-connection-kit/jackd_1.8+0.71-0.64studio2~jaunty1_i386.deb
Size: 29378
MD5Sum: 30aa0fd4db032b3911ba540b6e5c126b
```Is it too old to ?
As I said in the thread, I have the jack_load command with "could not load audioadapdter, status = 0x 1" error when I try it...

Do you think I should try to compile the last available source code of Jack2 ?
If so, do I have to uninstall jackd packages first, then
> **JDPP said:**
> something like : ```
cd /home/Desktop/
wget http://jackaudio.org/downloads/jack-audio-connection-kit-0.116.2.tar.gz
tar xzfv jack-audio-connection-kit-0.116.2.tar.gz
cd jack-audio-connection-kit-0.116.2
./configure
make

``` 
then
```
make install
```?
with [http://www.grame.fr/~letz/jack-1.9.2.tar.bz2]("http://www.grame.fr/%7Eletz/jack-1.9.2.tar.bz2") as source ?


My config is :
MSI Wind U100 netbook with Transmission (distrib from 64 studio) and also Ubuntu Studio Jaunty.

What I wan't to acheive :
Use IDJC with two outs...
In the first one I'd like to listen the main (what is to be streamed) and in the second one headphones for pre-listening.
I have a Zoom H4 Usb plugged (for input and pre listening), and the onboard audio soundcard (in wich I'd like to have an out working to check the stream)...

I'll probably try an Maudio Fast Track Pro as audio device, hoping that JAck will see the 4 outs of the M-Audio so that I won't need to begin going away from the distro and compiling myself....

---

### Post by JDPP on 2009-07-12
I'll have to try, only two outs recognised with fast track...

---

### Post by sonicolonic on 2010-04-15
I got this far using JACK2 from a ppa for karmic, and got jack_load to do the same... only add 2 I/Os to the connect window. Here's what I was thinking. My soundcards are indexed like so:

options snd_hda_intel index=0
options snd_hdsp index=1
options snd_ice1712 index=2

Since jack_load only added 2 I was thinking maybe it automagically picked the next lowest soundcard in the index and didn't know to choose hw:2, so I changed my /etc/modprobe.d/alsa-base.conf  to put the hdsp on 0 and ice1712 on 1, onboard on 2, and am now getting these errors:

First (after a fresh reboot, or sometimes after restarting alsa):

could not load audioadapter, status = 0x 1

Continued attempts produce this:

Could not read result type = 29
could not load audioadapter, status = 0x7fff

and kill jackd. 

I've searched and am not coming up with much, but if I revert the indexes and it goes away, maybe that'll be a lead.

~Brian

---

### Post by sonicolonic on 2010-04-15
Switched the indexes back like I said and I'm getting 2 additional channels in and out. Just tested it and it's definitely playing back on my onboard sound card. I'm going to play with indexes some more.

It'd be nice if I could fix this before sunrise.

~Brian

---

### Post by sonicolonic on 2010-04-15
SUCCESS!!!!!!!!!:guitar:

Not sure if changing the indexes did anything but I got it to work by using the -i option.

my jack settings are 

jackd -dalsa -dhw:2,0 -r96000 -p512 -n2 -i14 -o14

and once it's running I run

jack_load -i "-d hw:1 -i12 -o10" seasound audioadapter

So I'm specifying which soundcard to use and how many channels are available. Did a simple test in Ardour and the system is pretty sluggish but it seems to get the job done with no xruns. I'm happy... I'll take it as a win. Sound quality on playback of previously recorded material was a little sketchy, I'm starting to think the converters are gonna hold their own against the HDSP. I upped the buffer to 1024 which helped, but over that it gets bogged down again. 

Any thoughts or input as far as further tuning goes? I won't need to use this often, but it'll be nice to have... as long as this ice1712 card isn't converting garbage into the DAW, but that's a whole other set of tests. Also, I still get the:

 p, li { white-space: pre-wrap; }  Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

error, but jackd runs anyways. EEP! I just looked at all the scary messages from jack_load/audioadapter... I'm gonna pretend I didn't see that... unless y'all have something to say on the subject.

THANK YOU!!!!!! Thank you guys so much for all of your help and for taking the time to read my posts and every other post you read and respond to and for actually giving a shirt about this software and this community. This is what it's all about. I know about 100x more about my system than I did a month ago when I got into this mess with this new computer. I'm buying you guys beers!!!

~Brian

PS ~ @ 48khz, system is much happier... so either I start running @ 48khz, or I trade in my dual core for a faster quad.

---

### Post by bobince on 2010-05-02
I thought I'd give Jack2 a go before flattening a system for Lucid. I've got a USB mic (hw:1) I use in combinaion with an onboard sound card (hw:0), and I'd like to avoid the occasional xruns of running &#8216;system&#8217; across two devices.

So I'm testing Jack 1.9.6~svn3959-1~frasten0 mainly for audioadapter, as I've never managed to get alsa_in/out to work reliably (the amount of clicking can be reduced with choice of buffer params, but could never be eliminated).

```
$ jack_load -i "-dhw:1,0 -C -i1"
could not load audioadapter, status = 0x 1
```This unhelpful message is elaborated on in the qjackctl Messages window:

```
../linux/alsa/JackAlsaAdapter.h:220, alsa error -2 : No such file or directory
```Looking at JackAlsaAdapter in SCM ([http://trac.jackaudio.org/browser/jack2/trunk/jackmp/linux/alsa/JackAlsaAdapter.h](http://trac.jackaudio.org/browser/jack2/trunk/jackmp/linux/alsa/JackAlsaAdapter.h)) it appears to be attempting to open the device for both capture and playback regardless of whether the -C or -P flags are used. The attempt to open a microphone for playback would seem doomed to failure. Is this deliberate? What's going on here?

(Any further attempts to jack_load fail with the same status, but with &#8220;alsa error -16 : Device or resource busy&#8221; in the messages, until jackd is restarted.)

Running the main JACK as capture-only off hw1, and then using audioadapter to run the playback on hw0 (allowing it to open the unused capture device on hw0) fares no better, rapidly filling the message log with:

```
../linux/alsa/JackAlsaAdapter.h:371, reading samples : Broken pipe(-32)
JackResampler::Read : producer too slow, missing frames = 1024
JackResampler::Write : consumer too slow, skip frames = 1024
JackResampler::Write : consumer too slow, skip frames = 1024
JackResampler::Read : producer too slow, missing frames = 1024
JackResampler::Write : consumer too slow, skip frames = 1024
JackResampler::Write : consumer too slow, skip frames = 1024
```Any ideas?

---

