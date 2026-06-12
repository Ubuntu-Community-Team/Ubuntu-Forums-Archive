---
title: "Bluetooth midi controller wont connect"
date: 2012-10-01
forum: Ubuntu Studio
---

### Post by ki3gz on 2012-10-01
i found this sweet app on the android market called blupad, installed it, ran:

  amidi -p virtual -d

and

  sudo modprobe snd-virmidi

in my terminal. but i am having a hard time configuring it from here. in alsa tab there are 5 connections on the left of qjackctl and 7 on the right, i cant seem to figure out how to plug them into each other. i read that virtual midi is like a transport, but i always end up with 2 extra plugs. when i push buttons on the phone there is no activity in patchage. the phone and computer are sync'd via bluetooth alright. i havent slept in 2 days so maybe that is contributing to my frustration, but please can someone help? i want to use my phone as a drumpad and my mpc as a keyboard. its something about a loopback? thanks. -ki3gz

p.s. - please forgive my formatting, i have posted in a forum less than ten times in my life and im 24.. does that make me a loser?:lolflag:

---

### Post by CrocoDuck on 2012-10-02
Hi. I'm trying to get bluepad working... without success (can't install it). Maybe some different solution exist. A thing I found online: [http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/](http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/) . [COLOR=Black]At bottom page you find some program suggested.[/COLOR][URL="http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/"]
[/URL]

---

### Post by CrocoDuck on 2012-10-04
I get anyremote ([http://anyremote.sourceforge.net/index.html](http://anyremote.sourceforge.net/index.html)) working with my Nokia C5-03, Symbian S60. Now I have to configure it to use what I need (Ardour, Hydrogen...). Have a try with it!

---

### Post by ki3gz on 2012-10-05
> **CrocoDuck said:**
> Hi. I'm trying to get bluepad working... without success (can't install it). Maybe some different solution exist. A thing I found online: [http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/](http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/) . [COLOR=Black]At bottom page you find some program suggested.[/COLOR][URL="http://readthisaloud.wordpress.com/2007/08/27/the-ubuntu-way-to-remote-control-your-pc-via-bluetooth-phones/"]
[/URL]


hey sorry that is the wrong application! bluepad is a remote control, blupad is a drumpad emulator. it seems as though the latter has been discontinued, but the app is still on android market. you can find from there. maybe they are related?

---

### Post by CrocoDuck on 2012-10-06
> **ki3gz said:**
> hey sorry that is the wrong application! bluepad is a remote control, blupad is a drumpad emulator. it seems as though the latter has been discontinued, but the app is still on android market. you can find from there. maybe they are related?

OUPS! My eyes didn't noticed the missing e... Making some experiment I found that we could use anyremote to control the program we want... but we have to write a long configuration file by hand... And probably, acting like so, is difficult to use your cellphone as a drumpad. How about the commands you ran:

```
amidi -p virtual -d
```

```
sudo modprobe snd-virmidi
```

Did you noticed some error or bad message? 

I was thinking that maybe _blu_pad is close to working... What you  see in the alsa tab? Open Qjackctl, start jack. Then open Hydrogen (a drum machine). In the alsa tab, connect what seems to be your bluetooth controller to Hydrogen... If it works we should see midi events.

Reposting the output of this (with everything setted up and plugged) could help:

```
amidi -l
```

I'm so sorry to had misunderstood](*,)... I thought you were trying to use blu_e_pad to control some midi sequencer or drum machine... things were actually different...

---

### Post by ki3gz on 2012-10-06
hey first of all i want to thank you for sticking with me through this whole thing, as complicated as it has been getting. here is the results of :

amidi -l```
 
ki3gz@ki3gz-silver:~$ amidi -l
Dir Device    Name
IO  hw:1,0    Virtual Raw MIDI (16 subdevices)
IO  hw:1,1    Virtual Raw MIDI (16 subdevices)
IO  hw:1,2    Virtual Raw MIDI (16 subdevices)
IO  hw:1,3    Virtual Raw MIDI (16 subdevices)
```this is not very informative, but let me try to explain further:
after using 
```

ki3gz@ki3gz-silver:~$ amidi -p virtual -d

```it is only giving me client-129 in my alsa tab, but this is only in the right side window, when i want it on the left. it seems like i can connect a program to it but cannot connect it to a program? i know this is confusing but i dont know how to better explain... i also dont think there is a connection being made to my bluetooth device, not entirely sure what that last line is doing.

---

### Post by CrocoDuck on 2012-10-07
Uhm... I feel as we were just close to properly understand how the machinery works... The bluetooth device, you know, seems like properly recognized, and maybe it talks with your computer through a standard readable client... Can you make a screenshot of the ALSA tab in Qjackctl (or a list of the clients that are listed into it)? Unfortunately I can't find blupad for Symbian, and I don't have a device with Android... So I can't make some experiment in order to try to understand how things works...

---

