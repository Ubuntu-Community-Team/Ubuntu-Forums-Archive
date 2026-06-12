---
title: "Setting up a FireWire device in 8.10"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by HIFH on 2008-10-31
Hi,

I've installed the linux-rt and linux-headers-rt package (to use nVidia drivers) on a fresh Intrepid install. I'm using my motherboard's sound output, and I'm getting pops and clicks when using the rt kernel, even when nothing is playing. Is it because the rt kernel is only really meant for proper soundcards? I have a Presonus Firebox, but thought this problem should be solved before trying to get the Firebox working.

Cheers

ps. The output of aplay -l is [here](http://paste.ubuntu.com/65749/), and the audio section of lspci is [here](http://paste.ubuntu.com/65750/). Motherboard is a ASRock P4i65G.

---

### Post by HIFH on 2008-11-01
Sorry for the very early bump, but the thread's changed its subject :)

---

### Post by babarosa on 2008-11-01
Hello HIFH,

concerning setting up a firewire device immediately go to [www.ffado.org](www.ffado.org) and join the mailing list respectively read it to get the proper info and best help.

Every time i hear problems with jack (latencies and crackling sound) i give the following advice, please forgive me if you already checked the following suggestions:

I am using Xubuntu, so if you use Ubuntu replace "mousepad" with "gedit":

sudo mousepad etc/security/limits.conf

add to the end of the file:

@yourname - rtprio 89
@yourname - memlock unlimited
@yourname - nice -19

rtprio gives priority to this application with the "weight" of 70 (85 also good value). 700000 is the amount of RAM in Kb you reserve/lock for audio, the value depends of your amount of ram of course.

In the settings menu of qjackctl do NOT set priority value (let the (default)-value).
Start with 64 Frames/Period, 44.1 KHZ and 4 Buffers, then try to reduce values.
Additionally consider to compile jack and qjackctl by yourself.

Example: [http://www.servimg.com/image_preview.php?i=2&u=12842335](http://www.servimg.com/image_preview.php?i=2&u=12842335)

Regards,
Michael

---

### Post by HIFH on 2008-11-01
Thank you very much! Just leaving the system on for a bit after applying those lines to the config file and rebooting, I can't here any pops, clicks or crackles, thanks!

In regards to jack and qjackctl, compiling those shouldn't be a problem as I have compiled plenty before, but as for ffado, I'm a little confused as to what to use; ffado or freebob? I have Presonus Firebox as I said, and it is supported by both drivers, ffado seems to be a newer freebob, but is only in beta, and doesn't appear in synaptic like libfreebob0 does. Which one to use? And if I do compile and use ffado, is using Jack with it similar to freebob? ie. the command to boot the server would be something like

```
jackd -d ffado
```

Cheers!

---

### Post by babarosa on 2008-11-01
HIFH, go to [www.ffado.org](www.ffado.org)

Since a few days there is a repository to get ffado (beta7) without the need to compile if you have ubuntu/xubuntu/kubuntu.

On my system jack and qjackctl's repo-versions work perfectly, compiling new could be necessary if your interface doesn't like these versions.

ffado is a firewire-driver including your firewire interface's mixer-applet, freebob is only a firewire driver. if it works, choose firewire in qjackctl, otherwise use ffado to set the switches on the mixer applet and use freebob in qjackctl.

GO TO FFADO-USER LIST! the programmers directly take care of your questions, they are very helpfuk guys indeed.

Best wishes,
Michael

---

### Post by babarosa on 2008-11-01
HIFH, go to [www.ffado.org](www.ffado.org)

Since a few days there is a repository to get ffado (beta7) without the need to compile if you have ubuntu/xubuntu/kubuntu.

On my system jack and qjackctl's repo-versions work perfectly, compiling new could be necessary if your interface doesn't like these versions.

ffado is a firewire-driver including your firewire interface's mixer-applet, freebob is only a firewire driver. if it works, choose firewire in qjackctl, otherwise use ffado to set the switches on the mixer applet and use freebob in qjackctl.

GO TO FFADO-USER LIST! the programmers directly take care of your questions, they are very helpful guys indeed.

Best wishes,
Michael

---

### Post by ttoine on 2008-11-01
You don't need at all the ffado repository to run your FireBox sound card. I own one and you can launch it just with Qjackctl, just select freebob in the driver list in the setup windows, put "3" in period/buffer, and choose frequency, etc... And it is ok.

Toine

---

### Post by HIFH on 2008-11-02
Fiiinally! She lives!

Blue light, recording through the mono input with a mic, Ardour input lights flickering away, beautiful :D

Thanks very much Babarosa, and too the ffado team of course. My last little query, is can I somehow set up jack/Ardour to have their inputs set to my Firebox, and send all outputs through my soundcard to the connected speakers? I'm waiting on a 3.5mm-1/4"converter so I can't connect the speakers (or headphones) to the Firebox and have ins and outs in one place, but is different devices for ins/outs possible?

---

### Post by babarosa on 2008-11-02
I am glad that you succeded, you will have a lot of fun to explore the possibilities of a linux audio system.

As far as i uderstand your question, i do not believe:
The firebox needs jack running with thefirewire/freebob-driver, but your soundcard needs jack running with alsa.
I don't think that is possible (but once again, ffado team is best - they experiment with everything LOL
Try to open two instances of jack (at least i could do that on my machine).

Work with the patchbay and connect buttons.

Good luck,
Michael

---

### Post by xslimmiejimmiex on 2008-12-24
> **ttoine said:**
> You don't need at all the ffado repository to run your FireBox sound card. I own one and you can launch it just with Qjackctl, just select freebob in the driver list in the setup windows, put "3" in period/buffer, and choose frequency, etc... And it is ok.

Toine

Could you possibly help elaborate? I selected freebob, 3 is in period/buffer, now what should I do?... 
[[IMG]http://img265.imageshack.us/img265/931/31739458ud6.th.png[/IMG]](http://img265.imageshack.us/my.php?image=31739458ud6.png)


When I click connect there is nothing in Audio but my Axiom Audio 61 is in ALSA...

[[IMG]http://img265.imageshack.us/img265/6980/81327668qv9.th.png[/IMG]](http://img265.imageshack.us/my.php?image=81327668qv9.png)

If it try to "Start" I get these error messages...

[[IMG]http://img265.imageshack.us/img265/4136/84515900ms9.th.png[/IMG]](http://img265.imageshack.us/my.php?image=84515900ms9.png)

Thanks in advance.

Also, here's some terminal commands I did:
```

james@james-desktop:~$ lsmod|grep 1394
raw1394                32348  0 
dv1394                 25180  0 
ohci1394               37936  1 dv1394
ieee1394               96324  4 sbp2,raw1394,dv1394,ohci1394

```

```

sudo gedit /etc/udev/rules.d/40-permissions.rules

``` 

and changed
```

KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

```

to 
```

KERNEL=="raw1394",			GROUP="audio"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

```

---

### Post by Stochastic on 2008-12-25
xslimmiejimmiex, it looks like you're having a permissions error trip you up.  Most likely you have almost everything setup right, but don't have an audio group.  To check this, go into System -> Administration -> Users and Groups then click unlock, then click Manage Groups.  In that list check to see if there's a group named audio and if there isn't, add a new group, name it audio, and make sure you're a member of that group (check the tick box beside your name).  Then I'd do a reboot, just to make sure all your settings adjustments have taken effect (though for group edits I don't think its required) and give freebob a go again.

---

### Post by xslimmiejimmiex on 2008-12-25
Ok, blue light is on thanks.

---

### Post by msu3 on 2009-02-19
I got the blue light to come on for my Firebox also, but I get a lot of xruns and this also comes up in messages:

libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

and 

LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 64 (0 / 288 ) (0 / 0 )
subgraph starting at qjackctl timed out (subgraph_wait_fd=12, status = 0, state = Triggered)

Do I absolutely have to be running this in a realtime kernel? For some reason when I load up the realtime kernel at bootup, I can't restart or shutdown without it freezing.

I already changed my permissions and set up an "audio" group and gave myself permission. Any help would be greatly appreciated.
 
Update:

Actually, I finally got rid of the xruns! But for some reason it's only correct when I run jack from the terminal with: 

/usr/bin/jackd -R -dfreebob -r48000 -p1024 -n3 -P -i0

---

