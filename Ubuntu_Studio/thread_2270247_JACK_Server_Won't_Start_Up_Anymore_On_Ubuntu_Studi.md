---
title: "JACK Server Won't Start Up Anymore On Ubuntu Studio 14.04 Or 14.10"
date: 2015-03-21
forum: Ubuntu Studio
---

### Post by Sean_Britton on 2015-03-21
Help, I have been using Ubuntu Studio for a couple of months now, and I have always been having problems with Jack starting up all the time. I have re installed Ubuntu Studio multiple times, so Jack could work, but it will work for a few times, and then it will never run again. I am just using the HDA Intel jacks that came built in with my Dell Dimension e310, which comprises of a line-in, line-out, and mic-in on the back, and a headphone jack on the front. Here is my most recent error on QJackCtl:


```
13:05:14.097 Patchbay deactivated.
13:05:14.112 Statistics reset.
13:05:14.179 ALSA connection change.
13:05:14.190 JACK is starting...
13:05:14.191 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
13:05:14.216 ALSA connection graph change.
13:05:14.239 JACK was started with PID=1995.
no message buffer overruns
no message buffer overruns
no message buffer overruns
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
13:05:21.405 Could not connect to JACK server as client. - Overall  operation failed. - Server communication error. Please check the  messages window for more info.
13:05:21.604 JACK is stopping...
JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot read socket fd = 15 err = Success
CheckRes error
JackSocketClientChannel read fail
Cannot create new client
Cannot open qjackctl client
Unknown request 4294967295
CheckSize error size = 0 Size() = 12
CheckRead error
Jack main caught signal 15

```

Any help would be greatly appreciated

---

### Post by marseille2 on 2015-03-23
Oh dear. Reinstalling is pretty drastic. It's probably just a [matter]("https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#.22Cannot_lock_down_memory_area_.28Cannot_allocate_memory.29.22_message_on_startup") of "delete ~/.jackdrc, ~/.config/jack/conf.xml, ~/.config/rncbc.org/QjackCtl.conf. Kill *jackdbus* and restart." 

Take a look at 'Trouble-shooting Jackd' in this [thread]("http://ubuntuforums.org/showthread.php?t=2269785&p=13248150#post13248150") for more.

---

### Post by Sean_Britton on 2015-03-23
Thank you, I will try that soon

---

### Post by Sean_Britton on 2015-03-23
It still doesn't work...
here is the message...

```
 [COLOR=#999999]16:08:10.687 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:08:10.713 Statistics reset.[/COLOR]
 [COLOR=#cccc99]16:08:10.748 ALSA connection change.[/COLOR]
 [COLOR=#999999]16:08:10.838 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]16:08:10.852 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]16:08:48.496 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Mon Mar 23 16:08:23 2015: Starting jack server...
 Mon Mar 23 16:08:23 2015: JACK server starting in realtime mode with priority 10
 Mon Mar 23 16:08:23 2015: self-connect-mode is "Don't restrict self connect requests"
 Mon Mar 23 16:08:23 2015: Acquired audio card Audio0
 Mon Mar 23 16:08:23 2015: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Mon Mar 23 16:08:23 2015: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Mon Mar 23 16:08:23 2015: ALSA: final selected sample format for capture: 32bit integer little-endian
 Mon Mar 23 16:08:23 2015: ALSA: use 2 periods for capture
 Mon Mar 23 16:08:23 2015: ALSA: final selected sample format for playback: 32bit integer little-endian
 Mon Mar 23 16:08:23 2015: ALSA: use 2 periods for playback
 Mon Mar 23 16:08:28 2015: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Mar 23 16:08:28 2015: ERROR: Driver is not running
 Mon Mar 23 16:08:28 2015: ERROR: Cannot open client name = dbusapi
 Mon Mar 23 16:08:28 2015: ERROR: failed to create dbusapi jack client
 Mon Mar 23 16:08:28 2015: ERROR: Unknown request 4294967295
 Mon Mar 23 16:08:28 2015: ERROR: CheckSize error size = 0 Size() = 12
 Mon Mar 23 16:08:28 2015: ERROR: CheckRead error
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#ff0000]16:08:58.241 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot read socket fd = 17 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Mon Mar 23 16:08:58 2015: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Mar 23 16:08:58 2015: ERROR: Driver is not running
 Mon Mar 23 16:08:58 2015: ERROR: Cannot create new client
 Mon Mar 23 16:08:58 2015: ERROR: Unknown request 4294967295
 Mon Mar 23 16:08:58 2015: ERROR: CheckSize error size = 0 Size() = 12
 Mon Mar 23 16:08:58 2015: ERROR: CheckRead error


```

And, by the way, this in the messages window ow qjackctl...
I don't know how to do it in terminal.;)

---

### Post by marseille2 on 2015-03-23
A couple trouble-shooting questions... Are you starting Jackd with Qjacktl? Is Jackd and/or Jackdbus loading on boot? 

Your messages says Jackd can't connect to **dbus**, so also check to see if that setting is checked-marked in Qjacktl. You may have to go through the the reset procedure, if you change something in Qjacktl and you're running UbuntuStudio Trusty.

You can confirm if Jackd and Jackdbus are running after you first log in with:

```
$ sudo ps aux | grep Jackd
```

```
$ sudo ps aux | grep Jackdbus
```

----
PS: I've seen some a few posts elsewhere that have been complaining about Qjacktl (apparently, KX-Studio uses an improved application that seems to get a lot of praise). So you may want to test and see if it's just that app giving you trouble, by starting Jackd from the command line (after you fix Qjacktl settings, reset, and start fresh with a clean Jackd).

---

### Post by Sean_Britton on 2015-03-23
I checked QJackCtl and DBus is definately checked, so what now?

I also want to thank you for agreeing to help me with this problem, it's something I've been struggling with ever since I first got Ubuntu Studio

---

### Post by marseille2 on 2015-03-24
No problem. I had a hard time getting an explanation that was short, and to the point for years. And every new upgrade always brought another set of challenges, including this one! Usually, it's PulseAudio that creates problems for *me*. And Hopefully, your PA is ok, but if Dbus is checked... it's always good to see if PA is alright. Btw... a quick search of one of your error messages brought up some talk about the exact issue (see [here]("http://linuxmusicians.com/viewtopic.php?f=6&t=11424") and [here]("https://www.mail-archive.com/pulseaudio-discuss@lists.freedesktop.org/msg04913.html")). So you can probably find out if PA is causing a problem by suspending it, then starting Jackd.

```
$ pulseaudio -k
```

 or (if PA is stubborn and the above command doesn't work):

```
[COLOR=#333333][FONT=Arial]$ echo autospawn = no > $HOME/.config/pulse/client.conf[/FONT][/COLOR]
```

Then start up Jackd (don't forget that it helps to kill any existing instances of a running Jackd and Jackdbus first ... and you may have to try and kill a stubborn PID twice, like [this]("http://ubuntuforums.org/showthread.php?t=2269785&p=13248391#post13248391")). 

You can try testing your Qjacktl first, but IMO going to the commandline is the best option ... find your sound card's number and start up Jackd (see this [example]("http://ubuntuforums.org/showthread.php?t=2265205&p=13228748#post13228748")).

If it doesn't work based on your current choice of 44.1k sample/32-bit/period 1024 frame ... try lowering the period frames, and *maybe* force 16-bit. BUT if Jackd does work ... then it might be time to check PulseAudio. Personally, I think the AskUbuntu.com site has better info -- or at least, easier to find -- on how to troubleshoot PA, if need be. They seem to have the gurus on there.

---

### Post by Sean_Britton on 2015-03-24
Hi again... I tried everything you told me to try except for the second link you gave me... I don't know how to implement this:
[IMG]file:///home/sean/Desktop/Screenshot%20-%2003242015%20-%2006:27:55%20AM.png[/IMG]

And, hopefully this helps, i also tried the software from kx-studio that you recommended earlier, and the GUI is great! But sadly, JACK still refuses to start. 		 			 				:cry:

---

### Post by marseille2 on 2015-03-24
Oops, the screenshot didn't load. Btw... do you mean you didn't see the thread talking about your error in relation to pulseaudio, and the problems with the modules. A lot of us are having problems with them (mostly jack-sink and jack-source, and a ton of bluetooth questions). Some even choose to turn *off* Dbus, and just run Jackd.

---

### Post by Sean_Britton on 2015-03-24
If you're referring to this link right [here]("https://www.mail-archive.com/pulseaudio-discuss@lists.freedesktop.org/msg04913.html"), I was saying that about midway in there I didn't understand when it said:

- Disabling autospawn and running pulseaudio -vvv  allows jackd to start.

I assumed that that is what they wanted me to do.. I'm an extreme noob with this stuff, sorry

---

### Post by marseille2 on 2015-03-24
No worries. They're just saying [pulseaudio]("http://linux.die.net/man/1/pulseaudio") (PA) has to (temporarily) quit, so Jackd can take control of the sound card (to turn on). You can do that with a script or various commands, such as:

```
 $ pulseaudio -vvv
```

```
 $ pulseaudio -k
```

```
 [COLOR=#333333][FONT=Arial]$ echo autospawn = no > $HOME/.config/pulse/client.conf[/FONT][/COLOR]
```

I went with the last just in case the first two don't work ... to stop PA from 'autospawning.' And you'll know if that's happens ... because if you  **delete **the** .config/pulse folder** (*and[COLOR=#696969] you should, when you reset Jackd, if PA is a constant headache -- see[/COLOR][COLOR=#ff0000] '[Troubleshooting Jackd]("http://ubuntuforums.org/showthread.php?t=2269785&p=13248150#post13248150")'[/COLOR]*) ... it'll just keep creating another folder, and prevent Jackd from taking control of the sound card. 

Since you know the DBUS setting is checked off, but Qjacktl keeps spitting out error messages about DBUS not connecting, like this one:

```
 Mon Mar 23 16:08:28 2015: ERROR: failed to create **dbusapi** jack client
```

it's a clue to check on PA ... since **DBUS** has to be on,* if you're going to use programs that tend to let PA route audio by default*. To do that, **PA modules** jack-sink, and jack-source should be [installed]("http://packages.ubuntu.com/trusty/pulseaudio-module-jack") and have to load.

You can find out if your jack sinks are loaded with [pacmd]("http://ubuntuforums.org/showthread.php?t=2261067") (interactive command line), then typing 'list-sinks'; 'help' for hints on commands to issue; and 'exit' to quit.

```
$ pacmd
>>>
list-sinks
```

You'll know if you can run Jackd and still use PA, if you see something like:

```
driver: <module-jack-sink.c>
```


If the jack sinks aren't loaded, do it at the command line:

```
$ pactl load-module module-jack-sink
```

```
$ pactl load-module module-jack-source
``` 

If it 'fails,' then things get might get more [complex]("http://ubuntuforums.org/showthread.php?t=2269734"). 

Lately, Trusty is giving a lot of problems with the jack sinks (it's thread after thread of frustration). So if the problem is really about PA... then some decide to edit pulse configuration files (/etc/pulse/default.pa and /etc/pulse/daemon.conf) to keep using PA, but others decide to forego PA altogether. The latter can be good to troubleshoot, and see if Jackd works fine. This is done by:


[LIST]
[*]unchecking DBUS (and *I think* ALSA sequencer) 
[*]stopping PA 
[*]then starting Jackd 
[/LIST]

But if the problem is with ALSA (*which is hopefully slim in your case*), then it could be time to look at [bug lists]("http://www.freedesktop.org/wiki/Software/PulseAudio/Backends/ALSA/BrokenDrivers/") and sometimes edit related files.

---

### Post by morizothugo on 2015-03-26
Hi friends :) 
I tried also many time to make Jackd work on my desktop ... For now more than 5 years .... 

My dream is to play my guitar with a very simple Jack in sound in my headphone ... 

Last time i tryed, i learned that pulse-audio was the troublemaker because Ubuntu use an hybrid mix of Pulse audio and Alsa to deliver sound. 
  
Some distros have no problems with Jackd simply because they only use Alsa or another sound server. 

My conclusion is : Ubuntu should have a cleaner sound server, including a basic Jack server so it will be easy for many devellopers to create apps arround it, furthermore that Ubuntu is going mobile and it need to be as light and skillfull as possible ^^ 

Not to devaluate the great coders work done on Ubuntu, but if you think about it quickly, even basic car radio have a jack in plug that i can use to amplify my guitar ^^

I would add that Android have a strong bug with amp apps, there is today  NO guitar amp apps because of the delay bug, would Ubuntu will take this  opportinity to show how good it is on both desktop and mobile ? ;)

To end : Imagine the frustration of the great devellopers from Guitarix, Rakarrack, Lingot or Gxtuner ??? As they can't have there work running on the most famous linux Distros because sound servers ares in conflict and bugged with jackd ?

---

