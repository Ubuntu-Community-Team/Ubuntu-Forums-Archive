---
title: "Trouble get qjackctl to work"
date: 2015-03-24
forum: Ubuntu Studio
---

### Post by nathanhurley on 2015-03-24
Hi. I just installed Ubuntu studio 14.04, and am having trouble getting jack to work. I am using a Steinberg MI4 sound card. 
 
I tried running "qjackctl" as sudo, and as user in terminal to no avail. Here is the error I am getting. It gets stuck at "server state" 



17:20:32.945 Patchbay deactivated.
17:20:32.956 Statistics reset.
17:20:32.974 ALSA connection change.
17:20:32.987 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
17:20:32.996 ALSA connection graph change.
(qjackctl:9049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:9049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed


I read to do this command also:

^Cnathan@nathan-ThinkPad-T400:~$ aplay -L | grep CARD
sysdefault:CARD=Intel
front:CARD=Intel,DEV=0
surround40:CARD=Intel,DEV=0
surround41:CARD=Intel,DEV=0
surround50:CARD=Intel,DEV=0
surround51:CARD=Intel,DEV=0
surround71:CARD=Intel,DEV=0
iec958:CARD=Intel,DEV=0
dmix:CARD=Intel,DEV=0
dmix:CARD=Intel,DEV=1
dsnoop:CARD=Intel,DEV=0
dsnoop:CARD=Intel,DEV=1
hw:CARD=Intel,DEV=0
hw:CARD=Intel,DEV=1
plughw:CARD=Intel,DEV=0
plughw:CARD=Intel,DEV=1
sysdefault:CARD=MI4
front:CARD=MI4,DEV=0
surround40:CARD=MI4,DEV=0
surround41:CARD=MI4,DEV=0
surround50:CARD=MI4,DEV=0
surround51:CARD=MI4,DEV=0
surround71:CARD=MI4,DEV=0
iec958:CARD=MI4,DEV=0
dmix:CARD=MI4,DEV=0
dsnoop:CARD=MI4,DEV=0
hw:CARD=MI4,DEV=0
plughw:CARD=MI4,DEV=0



nathan@nathan-ThinkPad-T400:~$ sudo cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k3.13.0-46-lowlatency.

---

### Post by jejeman on 2015-04-04
There is never need to start qjackctl as super user (sudo).

Is your sound card working at all?

---

### Post by nathanhurley on 2015-04-06
Yes. Mi4 is registering in command line, and I can hear system sound through it. 

I am about ready to give up on this. Not much support on linux recording. I really do not like Jack and wish there was a good alternative.

---

### Post by jejeman on 2015-04-07
Don't know what you want to do, but you can record audio without JACK in programs that work with ALSA directly.
Like, Audacity for example.

JACK can go both ways - to be a PITA, and to be best thing in your life..

I'm thinking. Why don't you give a "LIVE" go to AVLinux, see if it works there. It is little more optimized than UStudio.
What kind of sound card is that MI4?

Personaly, I don't run JACK via D-BUS. Try to disable it in Qjackctl settings.
Give us
```
cat .jackdrc
```

---

### Post by nathanhurley on 2015-04-07
Ok I will try all that. I guess I am trying to do multi track recording. I am mainly interested in soft synths. I have a MAC G5, but it's older so I can't get a lot of synths, plus everything is expensive.

My sound card is Steinberg MI4. I had no luck with Ubuntu studio, or KX studio, but I will try AV Linux. 

Here is output:

nathan@nathan-ThinkPad-T400:/$ sudo ls -R | grep jackdrc
ls: cannot open directory ./run/user/1000/gvfs: Permission denied

---

### Post by jejeman on 2015-04-09
Unfortunately I can't think off any program that can do multi track recording and softsynths that is not using JACK. Audacity can do multitrack recording, but it is all much easier with JACK and DAWs as Ardour, MusE and such.

I don't know why did you used that command. File you are looking for is named .jackdrc and is in your $HOME. If there is none there, then nothing.

You have USB card. You should use 3 periods in JACK settings. Anyway, you didn't say which settings did you use? Is JACK working for onboard card?

---

### Post by nathanhurley on 2015-04-13
OK. I will try that 3 periods. I don't think there was anything for jack in my home folder. 

Jack was starting with internal sound card. I didn't try to record because I use guitar cables.

---

