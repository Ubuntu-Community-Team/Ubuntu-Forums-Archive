---
title: "PulseAudio + M-Audio 10/10 = no sound on UStudio 10.04"
date: 2010-08-19
forum: Ubuntu Studio
---

### Post by Tarrasque on 2010-08-19
Hello.

I came back after a while to my UbuntuStudio box.

On my box I had 8.04. I'm no expert, but I managed to start JACK, use various apps and make music with it.

The soundcard is a M-Audio 10/10, plus there's the onboard one.

Now I installed UbuntuStudio 10.04 on another partition, and I prooceeded to try it.

Unfortunately, JACK refuses to start. QJACK Control freezes when I click start and the GUI becomes blank. System Monitor reports jackd as "zombie".

I tried back the US 8.04 installation and it still works, so It's not a soundcard problem.

So, I switched to US 10.04 and tried to listen to some file with Audacity. I then discovered that audio in Lucid is handled by this "PortAudio" thing.

I don't know anything about it, but playing with the "Device Manager" (not in front of the box now, don't remember well, anyway the application that starts the applet in the panel) i managed to see entries for what seems to be the 2 correct sound cards.

Audacity meters moved, the soundcard meters in PulseAudio moved, nevertheless, the meters of Envy24 did not, and I could not hear anything.

Can anybody help me?

THX

---

### Post by Pablo_F on 2010-08-19
1. You will know already but just in case, Envy24control is the very first thing to setup properly or check. It gives access to the hardware mixer and converters' levels. Normally you don't use this app almost never but you must take a look at it or tweak in these first steps. Use the manual of the card. It is similar here but pay attention to the analog volume tab.

2. Pulseaudio doesn't sound with that card out of the box, afaik. Try the work around in this bug report, comment number #30:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

3. As for the jack problem, it is strange. See if the thread below can help (comment #4). If not, please, post the content of that file, preferably in pastebin.com

[http://ubuntuforums.org/showthread.php?t=1530294](http://ubuntuforums.org/showthread.php?t=1530294)

Cheers! Pablo

---

### Post by Tarrasque on 2010-08-20
Thank you for the answer!!

> **Pablo_F said:**
> 1. You will know already but just in case, Envy24control is the very first thing to setup properly or check. It gives access to the hardware mixer and converters' levels. Normally you don't use this app almost never but you must take a look at it or tweak in these first steps. Use the manual of the card. It is similar here but pay attention to the analog volume tab.

Yes, turning up to max all controls in Envy24control is the first thing I've learned to do!! :D :D

Then after I'm sure everything's ok, I tune the levels until I'm ok. :)


> **Pablo_F said:**
> 2. Pulseaudio doesn't sound with that card out of the box, afaik. Try the work around in this bug report, comment number #30:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

OK, I'll try the fix as soon as I can. Just in case, since I'll be using the box mostly to make music, and so I'll use JACK all the time, can I just disable/uninstall PortAudio in some way?

> **Pablo_F said:**
> 3. As for the jack problem, it is strange. See if the thread below can help (comment #4). If not, please, post the content of that file, preferably in pastebin.com

[http://ubuntuforums.org/showthread.php?t=1530294](http://ubuntuforums.org/showthread.php?t=1530294)

Reading around the docs in the site, I noticed I haven't installed the realtime kernel yet. Could this be an issue? I remember that in 8.04 if I tried to start JACK with the realtime option and I was using the generic kernel, I got an error message, but it didn't hang up...

> **Pablo_F said:**
> Cheers! Pablo

Thank you again very much for the quick and kind answer!!

---

### Post by Pablo_F on 2010-08-20
> ...and so I'll use JACK all the time, can I just disable/uninstall PortAudio in some way?

I assume you mean pulseaudio. When you launch Jack Control pulseaudio suspends, and this should be enough. However, if you want to disable it, you should edit/create a:

 ~/.pulse/client.conf

and add the following line:

autospawn = no

This way you can safely kill pulseaudio with:

pulseaudio -k

which you can add as a startup aplication, in System -> Preferences or put it in qjackctl as a script on startup in the options tab of the setup.

> Reading around the docs in the site, I noticed I haven't installed the realtime kernel yet. Could this be an issue?

First thing to do is properly set the rtprio and memlock limits for the user and of course, start jack with the realtime option. This doesn't imply that you need a linux-rt. 

If you want very low latencies, the rt kernel and a well configured rtirq-init script can do wonders, but anyway, I don't think this is related to the problem you have. 

Can you please copy here or in pastebin.com the qjackctl conf file? 

You are welcome! Pablo

---

### Post by Tarrasque on 2010-08-26
> **Pablo_F said:**
> I assume you mean pulseaudio.

You're absolutely right!!!


I applied the patch you linked and PulseAudio seems to work perfectly.

Tonight I'll try again with JACK.

Thank you very much for yur help!!!!

---

### Post by Tarrasque on 2010-08-29
Unfortunately, JACK still refuses to start.

This is the configuration file. I hope you can help.

```
[Splitter]
AudioConnectView\sizes=220, 72, 220
MidiConnectView\sizes=34, 20, 34
AlsaConnectView\sizes=34, 20, 34
PatchbayView\sizes=34, 20, 34

[Settings]
Server=/usr/bin/jackd
Realtime=true
SoftMode=false
Monitor=false
Shorts=false
NoMemLock=false
UnlockMem=false
HWMon=true
HWMeter=true
IgnoreHW=false
Priority=0
Frames=2048
SampleRate=44100
Periods=2
WordLength=16
Wait=21333
Chan=0
Driver=alsa
Interface=
Audio=0
Dither=0
Timeout=500
InDevice=hw:1
OutDevice=hw:1
InChannels=0
OutChannels=0
InLatency=0
OutLatency=0
StartDelay=2
Verbose=false
PortMax=256
MidiDriver=none

[Geometry]
qjackctlConnectionsForm\x=5
qjackctlConnectionsForm\y=47
qjackctlConnectionsForm\width=544
qjackctlConnectionsForm\height=277
qjackctlConnectionsForm\visible=true
qjackctlMessagesForm\x=1084
qjackctlMessagesForm\y=265
qjackctlMessagesForm\width=511
qjackctlMessagesForm\height=905
qjackctlMessagesForm\visible=true
qjackctlStatusForm\x=35
qjackctlStatusForm\y=420
qjackctlStatusForm\width=378
qjackctlStatusForm\height=234
qjackctlStatusForm\visible=true
qjackctlPatchbayForm\x=0
qjackctlPatchbayForm\y=0
qjackctlPatchbayForm\width=720
qjackctlPatchbayForm\height=353
qjackctlPatchbayForm\visible=false
qjackctlMainForm\x=453
qjackctlMainForm\y=1013
qjackctlMainForm\width=453
qjackctlMainForm\height=100
qjackctlMainForm\visible=true

[History]
ServerComboBox\Item1=/usr/bin/jackd
ServerComboBox\Item2=jackd
ServerComboBox\Item3=jackdmp
ServerComboBox\Item4=jackstart
ServerComboBox\Item5=jackd-realtime
InterfaceComboBox\Item1=(default)
InterfaceComboBox\Item2=hw:0
InterfaceComboBox\Item3=plughw:0
InterfaceComboBox\Item4=/dev/audio
InterfaceComboBox\Item5=/dev/dsp
InDeviceComboBox\Item1=hw:1
InDeviceComboBox\Item2=(default)
InDeviceComboBox\Item3=hw:0
InDeviceComboBox\Item4="hw:1,0"
InDeviceComboBox\Item5=plughw:0
InDeviceComboBox\Item6=/dev/audio
OutDeviceComboBox\Item1=hw:1
OutDeviceComboBox\Item2=(default)
OutDeviceComboBox\Item3=hw:0
OutDeviceComboBox\Item4="hw:1,0"
OutDeviceComboBox\Item5=plughw:0
OutDeviceComboBox\Item6=/dev/audio
StartupScriptShellComboBox\Item1=artsshell -q terminate
PostShutdownScriptShellComboBox\Item1=killall jackd
XrunRegexComboBox\Item1=xrun of at least ([0-9|\\.]+) msecs
MessagesLogPathComboBox\Item1=qjackctl.log
ServerConfigNameComboBox\Item1=.jackdrc
InDeviceComboBox\Item7=/dev/dsp
OutDeviceComboBox\Item7=/dev/dsp

[Program]
Version=0.3.4

[Presets]
DefPreset=(default)

[Options]
StartJack=false
StartupScript=false
StartupScriptShell=artsshell -q terminate
PostStartupScript=false
PostStartupScriptShell=
ShutdownScript=false
ShutdownScriptShell=
PostShutdownScript=true
PostShutdownScriptShell=killall jackd
StdoutCapture=true
XrunRegex=xrun of at least ([0-9|\\.]+) msecs
XrunIgnoreFirst=false
ActivePatchbay=false
ActivePatchbayPath=
MessagesLog=false
MessagesLogPath=qjackctl.log
BezierLines=false
TimeDisplay=0
TimeFormat=0
MessagesFont="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
MessagesLimit=true
MessagesLimitLines=1000
DisplayFont1="DejaVu Sans,12,-1,5,75,0,0,0,0,0"
DisplayFont2="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
DisplayEffect=true
DisplayBlink=true
JackClientPortAlias=0
ConnectionsIconSize=0
ConnectionsFont="DejaVu Sans,8,-1,5,50,0,0,0,0,0"
QueryClose=true
KeepOnTop=false
SystemTray=false
StartMinimized=false
DelayedSetup=false
ServerConfig=true
ServerConfigName=.jackdrc
ServerConfigTemp=false
QueryShutdown=true
AlsaSeqEnabled=true
AliasesEnabled=false
AliasesEditing=false
LeftButtons=true
RightButtons=true
TransportButtons=true
TextLabels=true
BaseFontSize=0

[Defaults]
PatchbayPath=
```

Thank you in advance.

---

### Post by Pablo_F on 2010-08-30
Hi, 

Please, can you give the terminal output of the following informative commands?

```
cat /proc/asound/cards
```

```
cat ~/.jackdrc
```

Does qjackctl freeze? 
If not, what is the content of the Messages window?

Cheers! Pablo

---

### Post by Tarrasque on 2010-08-31
Here they are:

```
root@tron:/home/tarrasque# cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1980 at irq 17
 1 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xb800, irq 21
```

```
root@tron:/home/tarrasque# cat /home/tarrasque/.jackdrc
/usr/bin/jackd -dalsa -r44100 -p2048 -n2 -D -Chw:1 -Phw:1 -H -M

```


No, QJackCtl doesn't seem to freeze anymore. After some minutes it's irresponsive it gives the following messages, and I can quit it without leaving zombie processes around.

```
07:37:18.798 Patchbay deactivated.
07:37:19.034 Statistics reset.
07:37:19.457 ALSA connection graph change.
07:37:23.032 ALSA connection change.
07:38:19.817 JACK is starting...
07:38:19.834 /usr/bin/jackd -dalsa -r44100 -p2048 -n2 -D -Chw:1 -Phw:1 -H -M
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    379158
07:38:19.928 JACK was started with PID=8087.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|2048|2|44100|0|0|hwmon|hwmeter|-|32bit
control device hw:1
07:38:51.208 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
07:39:48.301 JACK was stopped successfully.
07:39:48.585 Post-shutdown script...
07:39:48.586 killall jackd
07:39:48.587 JACK has crashed.
jackd: no process found
07:40:01.828 Post-shutdown script terminated with exit status=256.
```

Thank you very much again!!!

---

### Post by Pablo_F on 2010-08-31
Hi, 

Do you have 512 MB of RAM? What is the output of 

free

? You might be suffering from this bug:

[https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/491329](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/491329)

In addition to killing pulseaudio (once permanently avoided autospawning, see above), you will have to:

rm -f /dev/shm/pulse*

before starting jackd. (Check at any moment with:

ls /dev/shm

). You don't want any pulse-shm-xxxxxxxxxx there while jackd is running.

Other hints and observations:

- Try to get more RAM

- If you don't intend to use the onboard card, disable it in the BIOS.

- You don't need to select playback and capture devices in qjackctl. I strongly recommend you write "hw:M1010LT" in the interface field, and choose "(default)" in the input and output devices. 

- Disable HW monitoring and metering. They do nothing useful. See:

[http://lalists.stanford.edu/lau/2010/08/0497.html](http://lalists.stanford.edu/lau/2010/08/0497.html)

If needed, use envy24control.

- If you are going to do HW monitoring, (use the patchbay/router in envy24control), you don't need a low value of frames per period. Even so, 2048 seems very high to me. I woould go for default 1024. If you are going to do software monitoring, choose 256 or lower. If you experience xruns, there are several things you can tweak, but that is another story.

HTH, Pablo

---

### Post by Tarrasque on 2010-08-31
Yes, in facts I have 512 MB of RAM.

The box I'm using is an old one. I am basically checking up the compability of the soundcard with the latest release of UbuntuStudio before upgrading.

Hopefully, I'll get a new motherboard in a short while. Anyway, I was able to do some real time recording with UbuntuSTudio 8.04, when with Win XP I was barely able to boot the machine. :)

So, to recap I'm going to:

- disable autospawning in the .conf file

- stop pulsesudio and delete any pulse* file

```
pulseaudio -k
rm -f /dev/shm/pulse*
```

before starting JACK, is it right?

I'm going to try it as soon as I can. Thank you verymuch again. You've been very helpful.

---

### Post by Pablo_F on 2010-08-31
Yes, that is right. Let's see if it works. You are welcome!
Pablo

---

