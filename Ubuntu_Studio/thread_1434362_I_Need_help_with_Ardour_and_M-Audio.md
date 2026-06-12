---
title: "I Need help with Ardour and M-Audio"
date: 2010-03-20
forum: Ubuntu Studio
---

### Post by Hoonakwa on 2010-03-20
Hello,
 Im new to Ardour and I cant seem to get the output to work. The system sounds work fine and I managed to get hydrogen drums to work. I don't know what to set to get ardour to work with the output. The inputs seem to work as I was able to record a guitar track but no matter what I do I cant get the output to play. Any help would be appreciated. I am using M-Audio Fasttrack pro.

---

### Post by raboofje on 2010-03-20
Are you using JACK or ALSA directly?

If you're using ALSA directly, perhaps some other program is blocking the sound output, making it unavailable to Ardour. You'd expect Ardour to show an error message though. Perhap try closing other audio-related applications and restart Ardour?

---

### Post by Capoeira on 2010-03-20
that makes no sense, as the input works it means that the sound-device is connected to jack (ardour only works with jack).

so it has to be something in ardour itself. Is masterout connected to soundcard in? is the master muted? is one track marked to play solo without having audio in it?
Do you have sound in other apps with jack?
do you have sound in other apps without jack?

---

### Post by Hoonakwa on 2010-03-20
OK I might not make much sense as I am pretty new to this. I did not know that you have to use jackctl with ardour. I guess I need to find out how to set up jack to work with M-Audio Fasttrack first.
 In my jack set up the driver is set to alsa. but when I try to set the interface to M-Audio there is no selection for that. My M-Audio is on hdw1 and all I see is hdw0. When I start jack I get an error and this is the message I get.

14:34:59.861 Patchbay deactivated.
14:34:59.877 Statistics reset.
14:34:59.967 ALSA connection graph change.
14:35:00.240 ALSA connection change.
14:35:00.242 ALSA connection graph change.
14:37:32.972 Startup script...
14:37:32.974 artsshell -q terminate
sh: artsshell: not found
14:37:33.381 Startup script terminated with exit status=32512.
14:37:33.383 JACK is starting...
14:37:33.385 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n3
14:37:33.399 JACK was started with PID=2244.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215898864, from thread -1215898864] (1: Operation not permitted)
cannot create engine
14:37:33.717 JACK was stopped successfully.
14:37:33.719 Post-shutdown script...
14:37:33.720 killall jackd
jackd: no process found
14:37:34.163 Post-shutdown script terminated with exit status=256.
14:37:35.658 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

 Maybe you guys could point me to a site that could help me with setting up jack.
Thanks for you help here guys. I really do appreciate the way linux people are will to help the noob, linux challenged people like me. +8-)

---

### Post by rixtr66 on 2010-03-20
do you have an rt kernel?if not untick realtime in your jack settings.
in my setup i use a fast track pro and i have to get the settings in jack right,try this input=fast track pro output usb audio#1,i dont know your settings,so im guessing.maybe if you give me a list of what your jack settings are.
Rick

---

### Post by sgx on 2010-03-22
> **Hoonakwa said:**
> Hello,
 Im new to Ardour and I cant seem to get the output to work. The system sounds work fine and I managed to get hydrogen drums to work. I don't know what to set to get ardour to work with the output. The inputs seem to work as I was able to record a guitar track but no matter what I do I cant get the output to play. Any help would be appreciated. I am using M-Audio Fasttrack pro.

[http://www.linuxjournal.com/article/8354](http://www.linuxjournal.com/article/8354) shows using qjackctl with qsynth

[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76) -this shows patchbay details

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl) -this has several good links up front

[http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s](http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s)

-this is a bounty of useful links on many topics

Cheers

---

### Post by Pablo_F on 2010-03-22
> do you have an rt kernel?if not untick realtime in your jack settings.

The realtime option in jackd has nothing to do with having a rt kernel. What is needed to run jackd with the realtime option is to set some [PAM limits]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_limits.html"). 

Particularly, rtprio is what makes jackd being able to run with the realtime option. It is also important the memlock setting. Take a look at the jackaudio.org FAQS. Instead of memlock unlimited, you can set it to a value of 80%, more or less. For example, with 2 GB of RAM, my /etc/security/limits.conf looks like this:

@audio		-	rtprio		99
@audio		-	memlock		1500000

Of course, my user belongs to the audio group.

To sum up, you need to:

sudo adduser yourloginname audio

sudo yourfavouriteeditor /etc/security/limits.conf

and write the magic lines, if they are not already.

Then restart and check the limits with:

ulimit -l
ulimit -r


That said, in ubuntu lucid the post-installation script of jackd package will write the rtprio and memlock lines in the file:

/etc/security/limits.d/audio.conf

So ubuntu(studio) lucid users won't have to bother with setting PAM limits manually anymore and we will run jackd with the realtime option out of the box.

Running jackd with the realtime option is strongly recommended. If not, jackd will have a very bad performance. 

The realtime kernel may help to get a better performance although I am not sure. Someone can shed some light here, please.

Cheers! Pablo

---

### Post by AutoStatic on 2010-03-22
> **Pablo_F said:**
> That said, the realtime kernel may help to get a better performance although I am not sure. Someone can shed some light here, please.

[quote=FFADO Wiki]The mechanism that provides this delayed execution is called the tasklet API. Hence, bottom halves of interrupt handlers are frequently called "tasklets".

SCHED_FIFO is a scheduling class of real-time enabled kernels. SCHED_FIFO processes can use all available CPU until another SCHED_FIFO process with higher priority needs it, and they take precedence over all other processes on a system. Consequently, a rogue SCHED_FIFO process has the potential to lock up the system.

On a real-time kernel (one that includes the RT patches and has the CONFIG_PREEMPT_RT option enabled), all interrupt handler top halves run SCHED_FIFO, with a priority of 50 by default. To ensure glitch-free audio, it is important that those responsible for audio operation have a higher priority than the others. Moreover, the jackd realtime threads should run at a priority higher than the standard IRQs but lower than the audio-related ones (use the -P option to set it accordingly, or the "Priority" value in qjackctl).[/quote]

Source: [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

So with an RT kernel you can also prioritise interrupt handlers which could improve performance and/or latencies (if I understood the above correctly). On my notebook for exemple I need a RT kernel with the rtirq script otherwise my Firewire soundcard simply won't work.

---

### Post by hudsonryde on 2010-03-24
hey there, I am new to Ubuntu Studio/Jack/Ardour yadda yadda and i cannot get any sound through my fast track pro except through my headphones. which i will assume means i have output from outputs 1&2. but as far as Jack and Ardour are concerned i get nothing, i have done all the steps listed above here(i read similar stories plastered around the interwebz) but i still have nothing... in fact, i cannot get Ardour or Jack to start at all. any help would make me EXTREMELY happy

---

### Post by raboofje on 2010-03-24
> **hudsonryde said:**
> i cannot get Ardour or Jack to start at all

Start a new thread and post the error messages. Start with JACK.

---

### Post by Hoonakwa on 2010-03-24
Wow as a new user of linux im not sure how to do all of that.

---

### Post by Hoonakwa on 2010-03-24
Well Im not sure how but i got it working. It was in the setting of jack. Many thanks to all the wonderful people out there who tried to help me ( a total linux idiot) out.

---

