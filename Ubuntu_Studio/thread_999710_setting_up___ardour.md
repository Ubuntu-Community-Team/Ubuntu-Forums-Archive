---
title: "setting up   ardour"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by robdashu on 2008-12-02
Newbie here.  Trying to get ardour running.  Have alsa, jack, and ardour running on a ThinkPad T43.  Lexicon Omega for hardware interface.
Have accomplished recording, but playback produces no sound.  The visual presentation shows ardour is playing it.
No applications recognize the LEXICON as a new sound card, they all send output to the Thinkpad internal speakers.  If I was in Windows, I would have used the HW Device Manager to try to fix  it.  Is there a parallel utility for system config changes in Ubuntu?/?

I'm hoping there is a simple system parameter that I've missed setting...?

The next issue is how to describe to ardour the mapping between the six physical inputs and two outputs on the hardware, and inputs/outputs that ardour is working with (I have two inputs set up that seem to correspond to mic1 and mic2 inputs on the Lexicon)

rob

---

### Post by robdashu on 2008-12-02
It looks like JACK is my problem.  When I start JACK, it immediately locks up.  The window titlesays:

JACK Audio Connection Kit [(default)] Stopped.

Can Anyone tell me what'swrong?  I tried reinstalling it.  (An old habit from Windows!)  That didn'thelp.

rob

---

### Post by cek on 2008-12-03
> **robdashu said:**
> It looks like JACK is my problem.  When I start JACK, it immediately locks up.  The window titlesays:

JACK Audio Connection Kit [(default)] Stopped.

Can Anyone tell me what'swrong?  I tried reinstalling it.  (An old habit from Windows!)  That didn'thelp.

rob

Are you using qjackctl? (It's a QT frontend for JACK that makes configuration easier)

If so, by default qjackctl starts up, but does NOT start the jack daemon.  To do that, there is a small "play" button at the bottom of the screen that actually starts the jackd service.

---

### Post by robdashu on 2008-12-03
Yes, I'm running Qjackctl.  I've now gotten beyond the lockup problem by changing other settings.  Now Jack say it can't connect:


Could not connect to Jack server as client ...

Postby robdashu on 03.12.2008, 10:32
I can't get Jack to start up successfully so I can use Rosegarden.
Here's what Jack tells me:

jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210472784, from thread -1210472784] (1: Operation not permitted)
cannot create engine
10:15:34.759 JACK was started with PID=10801.
10:15:34.760 JACK was stopped successfully.
10:15:34.761 Post-shutdown script...
10:15:34.761 killall jackd
10:15:34.957 MIDI active patchbay scan...
10:15:34.959 ALSA connection change.
jackd: no process killed
10:15:35.159 MIDI active patchbay scan...
10:15:35.167 Post-shutdown script terminated with exit status=256.
10:15:37.001 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I'm running:
Ubuntu 8.10
Alsa mixer 0.9.7
Qjackctl 0.3.2

on a ThinkPad connected to a Lexicon Omega through a usb port

JACK Settings:
in Connections, under the ALSA tab, I show two Readable Clients and two corresponding Writable Clients:
14:Midi Through
20:Lexicon Omega

However, the detail of Lexicon Omega shows only:
0:Lexicon Omega MIDI 1

(why are all labelled MIDI under the ALSA tab? ALSA is the mechanism for delivering MIDI data?)

I have the Lexicon Omega input connected to the Lexicon Omega output.
In Patchbay, I show two input sockets and two output sockets. I've connected In 1 with Out 1and In 2 with Out 2.

Setup won't let me choose "Interface" - it's set to hw:1; real time is checked.

What am I doing wrong?

robdashu
    HyperGuru
     
    Posts: 1
    Joined: 03.12.2008, 10:05

        * Private message

Top

---

### Post by thorgal on 2008-12-03
it's because you cannot use the realtime, or so it seems judging by the error messages.

Do you have the realtime option on in qjackctl ? if so, try without. If it works, it will give anyway a poorer performance than if you had realtime enabled and working.

---

### Post by robdashu on 2008-12-03
I'm also confused about whether I want to be running PulseAudio.  Several places where you choose devices, there's a choice between PulseAudio or Lexicon Omega.

Also Back-End and Front-End.  It seems like PulseAudio and ANSA manage signals similarly, why use both?  If you use PulseAudio, it seems that it wants to sit between ANSA and Jack.  Am I understanding this correctly?

I understand Jack is just a "connection Manager", hooking up in's and out's, but it gets confusing as to which perspective is being used, and who's acting as server and client!  I guess it would be a lot clearer if the "services" each app provided were clearer!

---

### Post by robdashu on 2008-12-03
Yeah, I noticed that error.  Unchecking realtime in Setup made it run.  I am loading the real-time kernel, though.  I'm afraid it won't perform very well without that capability.

I abandoned ardour to see if better luck with Rosegarden.  When I startRosegarden, I get an error about system timer resolution:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.

Seems like lack of realtime might be causing this?

---

### Post by thorgal on 2008-12-03
you mean ALSA (not ANSA)

ALSA is the audio layer that talks to the kernel (unless you have a firewire device).

PulseAudio is a user app layer that aims at making all audio related stuff transparent to the user. you fire up a sound app, and it should work in principle. That's the ultimate desktop sound server, or so is its goal. It allows a lot of flexibility and setups (like using different pulseaudio servers on the network, etc).
Jack is a special audio layer, its aim is pro audio work and is tailored to be sample accurate so that jack clients like rosegarden and ardour are synchronized at this level of precision. It also allows very low latency operations. It talks to ALSA or other more h/w oriented audio layers (ffado for firewire, OSS, PortAudio, etc).

So consider jack as sitting at the same layer level as pulseaudio. So in principle they should be quite exclusive. If you use PA, jack will not be happy about it because PA will have a grip on the lower level of your audio system. In fact, PA can be run concurrently to jack but you need to set it up to do so. It's not working out of the box. If you plan on using jack, disable PA.

I think youuse GNOME. I don't know how gnome makes sound devices available, I use KDE. But that should not matter. To disable PA, open a terminal and type 'pulseaudio -k'. Then, to check that it is off, type 'pgrep pulseaudio'. If no number shows up (the process ID), it's off.

The realtime option is only possible if you elevate your user privileges. You can add this in /etc/security/limits.conf (text edit the file):

```

your_user_name - rtprio 99
your_user_name - memlock unlimited
your_user_name - nice -19

```

and log out / log in again.

Beware, that's not the typical way to do so. You should in fact belong to the unix group audio and replace 'your_user_name' by '@audio' (you need the @ for unix groups).

But if you installed a generic ubuntu, it could be that the group audio (with the right level of permissions) has not been created by default. To check this, you can do this in the terminal:

```

grep audio /etc/group

```

It's a quick way to check. I am sure gnome comes with admin tools you can use to set up an audio group. It has to have a group ID like 29 (which very low, close to 0, so with elevated privilege. Your normal user is 1000 by default or 500, depending on which linux system you use).

Once the audio group is created, you must finish by adding yourself in that group (you canuse the same admin tool gnome offers).

Log out and log in again. Check you belong to this audio group by typing in a terminal:

```

id

```

if audio shows up in the list, you're in and can use now the realtime option.

---

### Post by robdashu on 2008-12-03
That looks very promising.  I had tried to look at permissions, but the GUI frontend on "users and groups" doesn't really allow  me to do much (it's mostly greyed out, presumably I don't have permission!  GNOME has seemed pretty good about allowing me to perform sensitive ops if I produce the admin password).  There is no apparent place to specify group membership.  If you could tell me how to do it from command line?

---

### Post by mrufino1 on 2008-12-03
Okay, go to system-administration-users and groups. When the panel pops up, click unlock, enter your system password. Then click your name, manage groups. Add the audio group, then add your name to that group if it was not already there (the group that is). Then you will be in the audio group. Then type the lines that Thorgal posted, using @audio rather than your user name, because you are in the audio group.

After that, experiment with the jack setup panel in qjackctl. The settings that seem to make sense don't always work best! I have an IBM T41, almost the same machine as yours, and I have finally gotten my jack setup fairly decent. The rt kernel with 8.10 seems to have some issues, so you may be better off in the regular kernel for now. If you are able to post a screenshot of your jack setup that may be helpful. I crash if the number of buffers per period is an odd number, but even numbers work fine. Also, verbose output being checked helps mine run better (don't know why- if anyone can explain that would be great!). You should choose alsa as your jack backend. The problem you are having is not ardour- it is your jack setup. Your machine recognized the lexicon obviously, since it sees the midi from it, so once you have jack talking correctly to it all should work. 

I am still fairly new at this but I asked a ton of questions and learned a lot, on here and on the ardour IRC, so keep at it. I'm still tweaking and getting things 100% but I recorded 3 hours at church last week using a phonic firewire 24 mkII and my t41, and it got better as I worked on the jack setup throughout the day (was not a critical recording, I was doing it sepcifically to get linux audio working for me). The second service recorded with only 4 xruns, none of which happened during recording, all happened while opening the programs I needed. Anyway, hope I can help you solve your issue because it helps me too!

---

### Post by Areia on 2008-12-05
Go to --> [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by markbuntu on 2008-12-11
Here are some links for setting up jack and ardour and rosegarden etc


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)


You can use pulseaudio and jack together. Directions are here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by markbuntu on 2008-12-12
I also just found this excellent guide to getting started with ardour:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

---

