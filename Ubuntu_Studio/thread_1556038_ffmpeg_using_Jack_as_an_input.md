---
title: "ffmpeg using Jack as an input"
date: 2010-08-18
forum: Ubuntu Studio
---

### Post by KoRnholio on 2010-08-18
So I'm trying to make a screencast with audio, working on some Jack applications like Hydrogen and Ardour, and getting the audio output from Jack. At first I tried all of the integrated ones, and just tried to record from a regular app.

xvidcap runs slow and doesn't record any audio, even from regular apps/pulse audio.
Istanbul just crashes when I start to record
gtk-recordMyDesktop records, but doesn't record any audio using pulse audio, and exits when I try to use Jack with it.

So that leaves me with command-line ffmpeg. This is fine with me. Using this command (taken from some other thread on this forum), I can record from regular pulse audio apps just fine...

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

Only problem is, I can't get it to work with Jack.  The ffmpeg documentation says that Jack works, but...

```
ffmpeg -f alsa -ac 2 -i jack -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

gives me the error: "ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM jack
[alsa @ 0x9c33a60]cannot open audio device jack (No such file or directory)
jack: I/O error occurred
Usually that means that input file is truncated and/or corrupted.
"

The ffmpeg documentation further says to switch up the input/output ( [http://ffmpeg.org/ffmpeg-doc.html#SEC24](http://ffmpeg.org/ffmpeg-doc.html#SEC24) ), but that gives me this error: 
"Unknown input or output format: jack"

Any idea how to get ffmpeg to take Jack as an input? I'm on Lucid Lynx Ubuntu Studio, Gnome.

---

### Post by Pablo_F on 2010-08-19
Hi, 

This does not answer the question because I don't know about ffmpeg but I hope it is helpful. 

I use recordmydesktop from the command line, for example:

recordmydesktop -x 300 -y 300 -width 480 -height 272 -fps 15 --use-jack system:capture_1 system:capture_2 -o output.ogv

I use these ports because system:capture_1 and system:capture_2 are always there if jack is running. Afterwards you can launch any jack client and disconnect the system:captures and connect the outputs of, say, hydrogen, to the inputs of rmd, via qjackctl/patchage.

I am using recordmydesktop from Autostatic's PPA in ubuntu karmic, this is, ppa:autostatic/ppa. He did something in rmd in order to play nicely with Jack. There is a thread on it here, IIRC. However, I think this command will work even for the "official" ubuntu version.

Another approach is use "recordmydesktop --no-sound" and use jack_capture (available in ppa:philp5/extra for karmic and lucid) which by default autoconnects to its inputs every audio port that is connected to the system playbacks (i.e., it records what you hear). But then you have to use a video editor to sync video and audio.

BTW, it could be that you have to tell ffmpeg not only use jack, but also the jack audio ports to use, as it is the case with rmd. 

Cheers! Pablo

---

### Post by AutoStatic on 2010-08-19
Well, again recordMyDesktop is broken in 10.04 apparently. I'll upload a fixed Lucid package asap.

---

### Post by KoRnholio on 2010-08-21
> **AutoStatic said:**
> Well, again recordMyDesktop is broken in 10.04 apparently. I'll upload a fixed Lucid package asap.

Yeah, I'm getting this error message using Pablo_F's command:
Error when parsing `-width': libpopt error: -11

I assume this is what you mean. I tried to compile it from source, but the newest SVN is the same one that's in Ubuntu (602). Do you know a version that works? I don't mind compiling it from source

---

### Post by AutoStatic on 2010-08-21
That's a gtk-recordMyDesktop error so you could try grabbing the most recent gtk-recordMyDesktop version. It's not related to the recordMyDesktop backend. Even though that one is broken too... [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188)

So I have to create new packages for both recordMyDesktop and gtk-recordMyDesktop. I'll try to do so after the weekend.

---

### Post by AutoStatic on 2010-08-22
> **KoRnholio said:**
> Any idea how to get ffmpeg to take Jack as an input? I'm on Lucid Lynx Ubuntu Studio, Gnome.You can't with the package from Lucid, it's not compiled with JACK support. I'll see what I can do too here because recordMyDesktop only outputs in a compressed format so the end result on Youtube can get abominable. So I'd like to play around with ffmpeg also.

Edit: apparently ffmpeg can't be compiled with JACK support, it's either dropped or broken. I'll try with the ALSA-JACK plugin, you do need a working .asoundrc file for that.

---

### Post by AutoStatic on 2010-08-22
With the ALSA-JACK plugin it works, but don't expect flawless JACK performance, xruns can happen with this method.

[LIST=1]
[*]Create an .asoundrc file in the root of your home directory with the following contents:
```
pcm.jackplug {
	type plug
	slave { pcm "jack" }
}

pcm.jack {
	type jack
	playback_ports {
		0 alsa_pcm:playback_1
		1 alsa_pcm:playback_2
	}
	capture_ports {
		0 alsa_pcm:capture_1
		1 alsa_pcm:capture_2
	}
}
```
[*]Log out and back in
[*]Start JACK
[*]Start the screencast recording session with the following command:
```
ffmpeg -f alsa -ac 2 -i jackplug -f x11grab -r 30 -s 1440x900 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
[/LIST]

The ffmpeg could be tweaked to your needs of course.

---

### Post by FakeOutdoorsman on 2010-08-22
> **AutoStatic said:**
> Edit: apparently ffmpeg can't be compiled with JACK support, it's either dropped or broken. I'll try with the ALSA-JACK plugin, you do need a working .asoundrc file for that.

I'm fairly JACK ignorant (I used it a few days ago with Ardour2, Hydrogen, ZynAddSubFX, and yoshimi to make a sound clip for a film fest which was fun), but a compiled FFmpeg seems to at least recognize JACK demuxing for me.

1. Install **libjack-dev**
2. Compile FFmpeg: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

```
$ ffmpeg -formats | grep jack
...
 D  jack            JACK Audio Connection Kit
```
^ This is missing in the Lucid FFmpeg.  I'm not sure if this is what you're looking for, and I didn't test any JACK/FFmpeg stuff.

---

### Post by AutoStatic on 2010-08-22
Thanks for the tip! But I prefer packages that I can easily uninstall again. So I'm going to give this PPA a try: [https://launchpad.net/~siretart/+archive/ppa/+packages](https://launchpad.net/~siretart/+archive/ppa/+packages)
Hopefully that one comes with JACK support.

Edit: nope, no libjack-dev in the control file :(

---

### Post by AutoStatic on 2010-08-22
FakeOutdoorsman, followed your guide and now I can enjoy lossless screencasting with JACK:
```
#!/bin/bash

DATE=`date +%Y%m%d`
TIME=`date +%Hh%M`

(sleep 3;qtractor $HOME/Screencasts/Screencast.qtr) &
ffmpeg -f jack -ac 2 -i ffmpeg -f x11grab -r 30 -s 1920x1080 -i :0.0+1920,0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 $HOME/Screencasts/screencast-$DATE-$TIME.mkv
```

Works like a charm and way better quality than recordMyDesktop! Many thanks!

---

### Post by FakeOutdoorsman on 2010-08-23
> **AutoStatic said:**
> ...But I prefer packages that I can easily uninstall again...

You probably noticed this, but the guide I linked to uses *checkinstall* to cleanly install all compiled packages into the package management system.  Removal is as easy as any other package.

> **AutoStatic said:**
> FakeOutdoorsman, followed your guide and now I can enjoy lossless screencasting with JACK:
```
#!/bin/bash

DATE=`date +%Y%m%d`
TIME=`date +%Hh%M`

(sleep 3;qtractor $HOME/Screencasts/Screencast.qtr) &
ffmpeg -f jack -ac 2 -i ffmpeg -f x11grab -r 30 -s 1920x1080 -i :0.0+1920,0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 $HOME/Screencasts/screencast-$DATE-$TIME.mkv
```

Works like a charm and way better quality than recordMyDesktop! Many thanks!

Good to hear!  I think I'll add **libjack-dev** as a dependency to the guide.

---

### Post by AutoStatic on 2010-08-24
> **FakeOutdoorsman said:**
> You probably noticed this, but the guide I linked to uses *checkinstall* to cleanly install all compiled packages into the package management system.  Removal is as easy as any other package.Yes, I've seen it.

> **FakeOutdoorsman said:**
> Good to hear!  I think I'll add **libjack-dev** as a dependency to the guide.I get the feeling after an evening of screencasting that FFmpeg has difficulties keeping up on the audio side. I can't use FFmpeg with a latency below 20ms (FYI, I can run recordMyDesktop < 3ms) otherwise it produces a lot of xruns on the FFmpeg side (JACK doesn't complain though). Also I have the feeling that audio lags, it's not in sync.
So I'm going to try FFmpeg together with jack_capture and mux it afterwards. Any suggestions on editing? Editor (I'm currently using OpenShot)? What format to render it to?

---

### Post by KoRnholio on 2010-08-24
> **FakeOutdoorsman said:**
> I'm fairly JACK ignorant (I used it a few days ago with Ardour2, Hydrogen, ZynAddSubFX, and yoshimi to make a sound clip for a film fest which was fun), but a compiled FFmpeg seems to at least recognize JACK demuxing for me.

1. Install **libjack-dev**
2. Compile FFmpeg: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

```
$ ffmpeg -formats | grep jack
...
 D  jack            JACK Audio Connection Kit
```
^ This is missing in the Lucid FFmpeg.  I'm not sure if this is what you're looking for, and I didn't test any JACK/FFmpeg stuff.

Thanks, this is pretty much exactly what I was looking for. I'll try it out tonight.

---

### Post by AutoStatic on 2010-08-28
With jack_capture I can do screencapturing at low latencies. So that's solved. But I'm running into a new issue: the quality of the video really degraded after I uploaded it to YouTube. I've posted about it [here]("http://ubuntuforums.org/showpost.php?p=9776487&postcount=61"). Any help would be much appreciated, thanks :)

---

### Post by stinkeye on 2010-08-29
> **AutoStatic said:**
> FakeOutdoorsman, followed your guide and now I can enjoy lossless screencasting with JACK:
```
#!/bin/bash

DATE=`date +%Y%m%d`
TIME=`date +%Hh%M`

(sleep 3;qtractor $HOME/Screencasts/Screencast.qtr) &
ffmpeg -f jack -ac 2 -i ffmpeg -f x11grab -r 30 -s 1920x1080 -i :0.0+1920,0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 $HOME/Screencasts/screencast-$DATE-$TIME.mkv
```

Works like a charm and way better quality than recordMyDesktop! Many thanks!
If you want to automatically grab your screen resolution you could use xwininfo.
eg
```
ffmpeg -f jack -ac 2 -i ffmpeg -f x11grab -r 30 -s [COLOR="Magenta"]$(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0[/COLOR] -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 $HOME/Screencasts/screencast-$DATE-$TIME.mkv
```

---

### Post by AutoStatic on 2010-08-30
Hello stinkeye, thanks, but I want to capture my right screen (I have two 24" screens), so I don't need the resolution to be grabbed automatically.

---

### Post by user1220 on 2010-10-20
Hi,

Thank you for that hint with the libjack-dev package, this helped me a lot.

I noticed that if you install the **jackd** dummy package on Ubuntu 10.10, it installs, among others the package **jackd2** as well. However, if you install **libjack-dev** then, **jackd2** is removed and **jackd1** is installed instead.

Too keep jackd2 installed and have ffmpeg support for jack at the same time, i found out that you can install **libjack-jackd2-dev** instead of **libjack-dev**.

So for ffmpeg to support the jack input, it seems
[LIST]
[*]you need to install **libjack-dev** if you use **jackd1**.
[*]you need to install **libjack-jackd2-dev** if you use **jackd2**.
[/LIST]

I don't really know the difference between jackd1 and jackd2, but jackd2 seems like the better option since the jackd dummy package installs jackd2.

---

### Post by nickleus on 2010-10-30
i only want to record audio from the system out and save it as a flac file. what's the ffmpeg command to do this while running jack?
i looked at the jackaudio docs and it didnt make sense to me. (i was going to copy the example here, but the JA docs page is timing out right now)

---

### Post by Pablo_F on 2010-10-31
> i only want to record audio from the system out and save it as a flac file. what's the ffmpeg command to do this while running jack?

For this task, I suggest you use jack_capture. It does exactly what you want. By default, jack_capture autoconnects to its input ports all the ports that are connected to the system: playbacks. As a result, it captures what you are hearing through the speakers. It records to mp3, ogg, flac and wav.

It has an intuitive gui that you can invoke with "jack_capture_gui2". 

Or just run the command: 

**jack_capture -f flac**

For more info, see:

jack_capture --help


Cheers! Pablo

---

### Post by AutoStatic on 2010-10-31
Maybe the tutorial I recently added to the linuxaudio.org Wiki could be helpful too.

[http://wiki.linuxaudio.org/wiki/screencasttutorial](http://wiki.linuxaudio.org/wiki/screencasttutorial)

Best,

Jeremy

---

### Post by nickleus on 2010-10-31
> **Pablo_F said:**
> 
Or just run the command: 
**jack_capture -f flac**

that would be nice if there was a jack_capture program in 10.10 =) where'd it go? =)

EDIT: i found the src here: [http://archive.notam02.no/arkiv/src/](http://archive.notam02.no/arkiv/src/)
that program should be in the repos =)

---

### Post by nickleus on 2010-10-31
> **AutoStatic said:**
> Maybe the tutorial I recently added to the linuxaudio.org Wiki could be helpful too.

[http://wiki.linuxaudio.org/wiki/screencasttutorial](http://wiki.linuxaudio.org/wiki/screencasttutorial)

Best,

Jeremy
thanks jeremy, i found the link to the jack_capture src on your page =)

---

### Post by Pablo_F on 2010-10-31
> that would be nice if there was a jack_capture program in 10.10 =) where'd it go? =)

No idea, I have been using the packages from Philip Johnsson's PPA for karmic and lucid but he has not built it for maverick yet. I am sure he will include it if someone asks him. Jack_capture is so cool and simple. I agree, it is a pity that it is not included in the official repos. 

Cheers! Pablo

---

### Post by nickleus on 2010-11-01
> **Pablo_F said:**
> Jack_capture is so cool and simple. I agree, it is a pity that it is not included in the official repos.
i totally agree, it is a cool little app

---

### Post by wachin on 2013-03-29
Working fine for my this on my laptop Dell Inspiron 1750, but with this variants:

Code:

```

pcm.jackplug { 
	type plug 
	slave { pcm "jack" } 
} 

pcm.jack { 
	type jack 
	playback_ports { 
		0 system:playback_1 
		1 system:playback_2 
	} 
	capture_ports { 
		0 system:capture_1 
		1 system:capture_2 
	} 
} 

```

See this:

[img]https://dl.dropbox.com/u/83295394/Jack%20Connections/Asoundrc%20file.png[/img]


Explication: You can see it in the message Jack Control (QjackCtl) (you clic on buttom). Example on my Delll Inspiron:
 
```

Fri Mar 29 11:29:01 2013: Starting jack server...
Fri Mar 29 11:29:01 2013: JACK server starting in realtime mode with priority 10
Fri Mar 29 11:29:01 2013: control device hw:0
Fri Mar 29 11:29:01 2013: control device hw:0
Fri Mar 29 11:29:01 2013: Acquired audio card Audio0
Fri Mar 29 11:29:01 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Fri Mar 29 11:29:01 2013: control device hw:0
Fri Mar 29 11:29:01 2013: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Fri Mar 29 11:29:01 2013: ALSA: final selected sample format for capture: 32bit integer little-endian
Fri Mar 29 11:29:01 2013: ALSA: use 2 periods for capture
Fri Mar 29 11:29:01 2013: ALSA: final selected sample format for playback: 32bit integer little-endian
Fri Mar 29 11:29:01 2013: ALSA: use 2 periods for playback
Fri Mar 29 11:29:01 2013: graph reorder: new port 'system:capture_1'
Fri Mar 29 11:29:01 2013: New client 'system' with PID 0
Fri Mar 29 11:29:01 2013: graph reorder: new port 'system:capture_2'
Fri Mar 29 11:29:01 2013: graph reorder: new port 'systemlayback_1'
Fri Mar 29 11:29:01 2013: graph reorder: new port 'systemlayback_2'

```

See this:

[img]https://dl.dropbox.com/u/83295394/Jack%20Connections/Jack%20Control%20Message.png[/img]

Is you will see, it Shows:

```

 'system:capture_1'
 'system:capture_2'
 'system:playback_1'
 'system:playback_2'

```

This is important, because if you do not choose the correct port that are using your computer that does not work.

Finally I put this in my terminal:
```
 
ffmpeg -f alsa -i jackplug -f x11grab -r 25 -s 1024x768 -i :0.0 -sameq output3.mkv

```

This variant work fine for my, Is great

The only bad thing is that it has maybe 0.2 seconds of delay voice regarding the video, but it is only taking into account and when you make a tutorial wait a little to move the cursor to where you're going to explain. 

[highlight]
STERO MIX
[/highlight]

also if you want to record a song in the same time, you can do with Audacious, go in Audio Preferences and putting out Jack,

See this:

[img]https://dl.dropbox.com/u/83295394/Jack%20Connections/Audacious%20to%20Jack%20Output.png[/img]

and then, on Jack Control, in Connections connecting dragging:

audacious-jack_6464_000

to (create a bridge):

alsa-jack.jackC.7966.0

(Note: This number jackC.79660 can variate)

and have the mixture between your voice and the song being played.

See this images:

[img]https://dl.dropbox.com/u/83295394/Jack%20Connections/Jack%20Connections%2C%20audacious%20to%20jackplug%201.png[/img]

[img]https://dl.dropbox.com/u/83295394/Jack%20Connections/Jack%20Connections%2C%20audacious%20to%20jackplug%202.png[/img]

Note: The plugin  "alsa-jack.jackC.7966.0" wich is: "pcm.jackplug" on de Code from Autostatic's only appear on Jack Control Connections when you press ENTER on Terminal with this:
```

ffmpeg -f alsa -i jackplug -f x11grab -r 25 -s 1024x768 -i :0.0 -sameq output3.mkv

```
(You can change output3 to whatever name except .mkv)

Thanks

AutoStatic's, You Are The Best, without you no one would know how to do this.

---

### Post by FakeOutdoorsman on 2013-03-29
Your post is hard to read: differentiating commands and outputs from your post text can be done with the [[code]](ubuntuforums.org/misc.php?do=bbcode#code) tag.

---

### Post by wachin on 2013-04-13
Hi, also published a post on how to make Stereo Mix with RecordMyDesktop and Jack

[http://ubuntuforums.org/showthread.php?t=986966&page=4&p=12601501#post12601501]("http://ubuntuforums.org/showthread.php?t=986966&page=4&p=12601501#post12601501")

[http://ubuntuforums.org/showthread.php?t=2057191&p=12601494#post12601494]("http://ubuntuforums.org/showthread.php?t=2057191&p=12601494#post12601494")

at the end of the page

---

### Post by wildmanne39 on 2013-04-13
Thread closed. Please do not post in old threads.

---

