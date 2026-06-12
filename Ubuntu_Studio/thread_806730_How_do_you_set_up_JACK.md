---
title: "How do you set up JACK?"
date: 2008-05-25
forum: Ubuntu Studio
---

### Post by christophski on 2008-05-25
There is probably a ridiculously simple answer for this, but *how on earth* do you set up JACK?
I have been trying to do this ever since I switched to Ubuntu (about a year ago), I am a musician and would love to get Rosegarden up and running to see if it will compare to my copy of Cakewalk 9.0 (from 1999 haha).
This there a simple set up guide for JACK?
ALl help is greatly appreciated!

---

### Post by cb951303 on 2008-05-25
*install jack and qjackctl ```
sudo apt-get install jackd qjackctl 
```
*open limits.conf ```
 sudo gedit /etc/security/limits.conf 
```
and add these lines ```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19 
```
*create a group called "audio" and make yourself a member of that group.
*logout and relogin
*run qjackctl and set it up like in the pictures, restart it to get jack running

PS: If you get xruns, try changing "Frames/Period" value.
PS2: There is also a better realtime capable kernel in repos but it's harder to get it work.

---

### Post by christophski on 2008-05-31
Oh wow, thanks!
This does look like it needs some work though, it's not exactly a newbie friendly set up. :s

---

### Post by atomkarinca on 2008-05-31
If you're interested in multimedia production then you can try [Ubuntu Studio]("http://ubuntustudio.org/"). It comes with Jack preinstalled and there are a lot of great softwares in the package. [Here]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy")'s how you can install it in Hardy.

---

### Post by Drunky on 2008-06-01
> **christophski said:**
> There is probably a ridiculously simple answer for this, but *how on earth* do you set up JACK?
I have been trying to do this ever since I switched to Ubuntu (about a year ago), I am a musician and would love to get Rosegarden up and running to see if it will compare to my copy of Cakewalk 9.0 (from 1999 haha).
This there a simple set up guide for JACK?
ALl help is greatly appreciated!

This Ubuntu Help page is, well, helpful :)
[HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration")

Make sure your sample rate matches the on-board audio...some are at 48K and some are 44.1K.

To help reduce xruns, I would first increase Frames/Period and then increase Periods per Buffer.

I hope this helps.

Regards.

---

### Post by pittmantechno on 2009-05-03
Thaaaaank you I was having a hard time getting decent performance - your instruction has set me on my way - weeee time for techno thanks again

---

### Post by bobince on 2009-05-04
> **christophski said:**
> This does look like it needs some work though, it's not exactly a newbie friendly set up. :s

Well the basic setup with qjackctl is easy enough; it's only the realtime feature that needs a bit of messing about, and you can certainly live without that if you just want to get it working. For me, even without realtime jack is still much lower-latency than anything I'm used to from Windows.

(Perhaps jack ought to default to no-realtime to make it easier to get running the first time.)

---

### Post by Khufucius on 2009-10-29
Thank you, this was really helpful.

-Khufucius

---

### Post by curran on 2009-12-02
*create a group called "audio" and make yourself a member of that group.

...years of toil ensued, avoidable if the original post had said...

#create a group called "audio"
sudo groupadd audio
#make yourself a member of that group
sudo usermod -a -G audio yourusernamehere

Thanks for the tips, eventually I got Jack working!

---

### Post by hellocatfood on 2010-01-04
I tried those settings and still couldn't get jack to work. It stops almost a second after I start it.

Any help is welcome

---

### Post by AutoStatic on 2010-01-04
Hello hellocatfood, it stops, but with what kind of warning/error message? And what soundcard do you use? And what are your current JACK settings?

---

### Post by hellocatfood on 2010-01-04
How do I check what soundcard I have? My laptop model is in my signature

Here's the terminal output:

```
21:23:50.677 Patchbay deactivated.
21:23:50.724 Statistics reset.
21:23:50.804 ALSA connection graph change.
21:23:51.010 ALSA connection change.
21:23:56.151 Startup script...
21:23:56.151 artsshell -q terminate
sh: artsshell: not found
21:23:56.553 Startup script terminated with exit status=32512.
21:23:56.553 JACK is starting...
21:23:56.554 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -m
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216915776, from thread -1216915776] (1: Operation not permitted)
cannot create engine
21:23:56.572 JACK was started with PID=7757.
21:23:56.599 JACK was stopped successfully.
21:23:56.599 Post-shutdown script...
21:23:56.599 killall jackd
jackd: no process found
21:23:57.009 Post-shutdown script terminated with exit status=256.
21:23:58.664 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

And my settings are attached in a screenshot

---

### Post by AutoStatic on 2010-01-04
Untick the 'Realtime' option and you're good to go.

---

### Post by hellocatfood on 2010-01-04
Thank you so much! I can't believe it's really that simple to get Jack up and running. 

I'm guessing that this isn't running it in an environemtn. Out of interest, would I experience any performance issues by running it this way?

---

### Post by AutoStatic on 2010-01-07
The chance that you'll run in occasional xrun will be a bit bigger. But I don't think you'll run in really big performance issues.

---

### Post by gandalf0777 on 2010-01-07
I tried it too and my jack is also stopped after approx. 1 second. In my messages I have:

```


the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
 cannot load driver module alsa

```

I will let you know when I solve the problem.

---

### Post by thorgal on 2010-01-07
try this in a terminal

```

fuser -v /dev/snd/pcmC0*

```

and you'll see what's having a grip on your hw:0

---

### Post by il-luzhin on 2010-04-13
Hey folks, 

To get my Delta 44 sound card working I had to uninstall pulseaudio.  So now the obvious is occuring.  When I start up JACK all my audio dies.  Firefox, VLC, Amarok, nothing will play audio.  When I stop the JACK server it all comes back.  Any idea of a work around?

Thanks

---

### Post by Pablo_F on 2010-04-13
> To get my Delta 44 sound card working I had to uninstall pulseaudio. So now the obvious is occuring. When I start up JACK all my audio dies. Firefox, VLC, Amarok, nothing will play audio. When I stop the JACK server it all comes back. Any idea of a work around?

I think this is because of a bug in pulseaudio that can be fixed. I am not sure though and I have not looked into it.

I rather recommend you get all of your audio through jack. Note that Jack only will take care of its clients and many media players are not so by default so you will hear nothing if you don't tell them: Do jack, please!! 

Here is a guide on how to "jackify" several popular media players, including VLC, amarok and the flash player (youtube, vimeo, myspace, etc):

[http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

As a side note, afaik in ubuntu lucid, some of these tricks will get easier (no need to add motin's PPA for Amarok, mixxx... because Jack will be included in main, if I am not wrong)

Cheers! Pablo

---

### Post by Bionbrains on 2010-04-13
I've recently jumped into the world of linux for recording purposes and gained a bit of knowledge but am now stuck with jack. The configuration process has been my biggest problem along with linking it up with ardour but specifically jack. My sound card and midi along with ubuntu studio version include..
M-Audio Delta 2496
    4 ins, 4 outs
    Envy24T chipset
    using ICE1712 driver    
ubuntu studio 9.10-64 bit
Any help would be appreciated. If needed I can provide more information..

---

### Post by AutoStatic on 2010-04-14
> **il-luzhin said:**
> When I start up JACK all my audio dies.  Firefox, VLC, Amarok, nothing will play audio.  When I stop the JACK server it all comes back.  Any idea of a work around?Create two accounts. One for browsing, office apps, watching videos etc with PulseAudio enabled and one for music production with PulseAudio disabled.
PulseAudio is for consumer audio and JACK for pro audio in short. You can't run Firefox and Windows Media Player through ASIO either.

---

### Post by AutoStatic on 2010-04-14
> **Pablo_F said:**
> I think this is because of a bug in pulseaudio that can be fixed. I am not sure though and I have not looked into it.It's not a bug. If you uninstall PulseAudio then you have to run everything through ALSA. As soon as JACK starts up it takes over ALSA so no other app can use that backend anymore.
PulseAudio and Delta cards could have issues together, I'd look on Launchpad, there's a huge bugreport on it: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

> **Pablo_F said:**
> As a side note, afaik in ubuntu lucid, some of these tricks will get easier (no need to add motin's PPA for Amarok, mixxx... because Jack will be included in main, if I am not wrong)That's right. Jack will be back in main for Lucid: [https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/510481](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/510481)

---

### Post by AutoStatic on 2010-04-14
> **Bionbrains said:**
> I've recently jumped into the world of linux for recording purposes and gained a bit of knowledge but am now stuck with jack. The configuration process has been my biggest problem along with linking it up with ardour but specifically jack. My sound card and midi along with ubuntu studio version include..
M-Audio Delta 2496
    4 ins, 4 outs
    Envy24T chipset
    using ICE1712 driver    
ubuntu studio 9.10-64 bit
Any help would be appreciated. If needed I can provide more information..Hello Bionbrains, where are you stuck with JACK? Does it start up or not? Could you post the outcome of the following terminal commands:
[LIST]
[*]**aplay -l**
[*]**arecord -l**
[*]**cat ~/.jackdrc**
[*]**uname -a**
[*]**tail /etc/security/limits.conf**
[/LIST]
Thanks!

---

### Post by cub on 2010-04-16
I suppose I could continue in this thread instead of starting a new one.

I've been running Ubuntu Studio 9.10 with real time kernel on an old Toshiba laptop. With this I use a Edirol UA-25EX sound card and it has been working great. Only issue was that my laptop was too old and weak to handle mixing. So I bought myself a new laptop, a Sony VAIO.

Now, I installed the Vaio the exact same way as the Toshiba. I have the exact same settings on JACK and the UA-25EX card, but on the Sony JACK just won't run.

I've read that to get the internal sound card in this Vaio model running one needs to download another alsa adn do some tweaking. But I figure since I'm not trying to use the internal card but the USB one this shouldn't matter..? It's the same Ubuntu version, same sound card and same settings on both card and JACK. I have checked that I'm running the RT kernel as well. The UA-25EX is hw:1.

Why does it run on the old laptop and not the new one?

The Message from JACK:
```
19:03:04.779 Patchbay deactivated.
19:03:04.780 Statistics reset.
19:03:04.859 ALSA connection graph change.
19:03:05.056 ALSA connection change.
19:04:28.473 Startup script...
19:04:28.474 artsshell -q terminate
sh: artsshell: not found
19:04:28.875 Startup script terminated with exit status=32512.
19:04:28.875 JACK is starting...
19:04:28.875 /usr/bin/jackd -R -m -dalsa -dhw:1 -r48000 -p128 -n2
19:04:28.877 JACK was started with PID=8838.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|128|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
19:04:28.924 JACK was stopped successfully.
19:04:28.924 Post-shutdown script...
19:04:28.929 killall jackd
jackd: no process found
19:04:29.339 Post-shutdown script terminated with exit status=256.
19:04:30.970 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

And my JACK settings are attached as well. I can run JACK with UA-25EX when I set the card to not use the advanced driver (which is preferred and used for my recordings on the old laptop) and 44100 kHz (but all my recordings are done in 48000 kHz). Any ideas?

---

### Post by AutoStatic on 2010-04-16
> **cub said:**
> I have the exact same settings on JACK and the UA-25EX card, but on the Sony JACK just won't run.

> **cub said:**
> I can run JACK with UA-25EX when I set the card to not use the advanced driver (which is preferred and used for my recordings on the old laptop) and 44100 kHz (but all my recordings are done in 48000 kHz).Does JACK run or not, it's a bit confusing :)

---

### Post by Bionbrains on 2010-04-16
> **AutoStatic said:**
> Hello Bionbrains, where are you stuck with JACK? Does it start up or not? Could you post the outcome of the following terminal commands:
[LIST]
[*]**aplay -l**
[*]**arecord -l**
[*]**cat ~/.jackdrc**
[*]**uname -a**
[*]**tail /etc/security/limits.conf**
[/LIST]
Thanks!

Thanks for responding AutoStatic. Heres what came up..

_aplay -l_ - card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

_arecord -l_ - card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889 Analog [ALC889 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

_cat ~/.jackdrc_ - /usr/bin/jackd -R -dalsa -dhw:0 -r22050 -p64 -n2 -m -Xraw

_uname -a_ - Linux ubuntu-DAW 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux

_tail /etc/security/limits.conf_ - #@student        -       maxlogins       4

@audio          -       rtprio          99

# End of file
@audio - rtprio 99
@audio - memlock unlimited
@audio - memlock unlimited
@audio - rtprio 99
@audio - memlock unlimited

Jack does does work. I'm also pretty sure the server is recognized as well. It's just a question of how it all fits together. Any ideas?

Thanks AutoStatic.

---

### Post by AutoStatic on 2010-04-17
> **Bionbrains said:**
> Thanks for responding AutoStatic. Heres what came up..Thanks!

> **Bionbrains said:**
> _cat ~/.jackdrc_ - /usr/bin/jackd -R -dalsa -dhw:0 -r22050 -p64 -n2 -m -Xrawhw:0 is your onboard card. What you could do is open QjackCtl and enter the value *hw:M44* manually in the Interfaces field of the QjackCtl Setup window. Also try a Sample Rate of 44100 or 48000 Khz.

> **Bionbrains said:**
> _tail /etc/security/limits.conf_ - #@student        -       maxlogins       4

@audio          -       rtprio          99

# End of file
@audio - rtprio 99
@audio - memlock unlimited
@audio - memlock unlimited
@audio - rtprio 99
@audio - memlock unlimitedIf you delete all the double lines it would look a lot more clarifying.

---

### Post by Bionbrains on 2010-04-17
> **AutoStatic said:**
> Thanks!

hw:0 is your onboard card. What you could do is open QjackCtl and enter the value *hw:M44* manually in the Interfaces field of the QjackCtl Setup window. Also try a Sample Rate of 44100 or 48000 Khz.

If you delete all the double lines it would look a lot more clarifying.

It was a bit messy. Sorry about that. I did what you suggested so now I'm just trying to configure the outputs/inputs for jack in order to get something to be recognized in ardour. Nothing yet but I feel many more hours of fooling around is on it's way. There is still something I'm not seeing. Any more suggestions?

 Thanks for your time.

---

### Post by AutoStatic on 2010-04-18
Can't help you with Ardour, I don't use it. But maybe the manual could help you: [http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/)

---

### Post by Bionbrains on 2010-04-18
> **AutoStatic said:**
> Can't help you with Ardour, I don't use it. But maybe the manual could help you: [http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/)

Thanks.

---

### Post by cub on 2010-04-19
> I have the exact same settings on JACK and the UA-25EX card, but on the Sony JACK just won't run.
--------------------------------------------
I can run JACK with UA-25EX when I set the card to not use the advanced driver (which is preferred and used for my recordings on the old laptop) and 44100 kHz (but all my recordings are done in 48000 kHz).
> **AutoStatic said:**
> Does JACK run or not, it's a bit confusing :)
Yes...and no. ;)

When using the same settings as my old laptop: Advanced Driver and sample rate 48000 and all the same settings in JACK = it won't run on the Sony laptop.

When using the "normal" driver and sample rate 44.1, it do run on the Sony.

However, all my recordings done on the old laptop are done in sample rate 48000 and with the advanced driver. I see no reason why I should settle for less with a 6 years newer laptop.

---

### Post by AutoStatic on 2010-04-19
> **cub said:**
> YHowever, all my recordings done on the old laptop are done in sample rate 48000 and with the advanced driver. I see no reason why I should settle for less with a 6 years newer laptop.Thanks for the info! It should work. Jack issues a warning:
```
DRIVER NT: could not start driver
cannot start driver
```

I think this is because your Edirol shares a port with another USB device. Could you post the out put of **lsusb** with the Edirol attached?

---

### Post by markbuntu on 2010-04-19
FYI Here is some links for jack and ardour and rosegarden etc and setting them up and using them. Some of them are a little dated but still mostly relevant and helpful.

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

If you would like to use jack and pulseaudio together so you can sample youtube clips or amarok streams directly into ardour etc the pulse-jack modules for this will be available with Lucid Lynx.

The pulse-jack modules and the alsa-jack libs have been excluded from previous Ubuntu releases due to some drm issues that kept jack out of the /main repository but all that has been resolved for Lucid. These modules will not be installed or loaded automatically so you will have to do that yourself.

If you are using a previous version of Ubuntu and would like to use the pulse-jack modules you will need to build and install them yourself from the appropriate pulseaudio source code and then add a small script to run at jack startup. It has worked for me and many others with every ubuntu since hardy and there are a bunch of threads around here about how to do it so please do not start new ones if you can help it. 

I know there are a lot of studio purists who are entirely against the whole idea of combining pulseaudio and jack but there are also a lot of people who want it so they can do stuff with it.

best regards,
mark

---

### Post by cub on 2010-04-19
> **AutoStatic said:**
> Thanks for the info! It should work. Jack issues a warning:
```
DRIVER NT: could not start driver
cannot start driver
```

I think this is because your Edirol shares a port with another USB device. Could you post the out put of **lsusb** with the Edirol attached?
```
Bus 002 Device 007: ID 0582:00e6 Roland Corp. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I have three USB ports on the laptop and I have tried all three with the same result and JACK messages.

---

### Post by cub on 2010-04-20
Now I'm confused. I checked the wiki ( [http://alsa.opensrc.org/index.php/Edirol_UA-25EX](http://alsa.opensrc.org/index.php/Edirol_UA-25EX) ) on the Edirol UA-25EX card and tried this:

```
Testing sound output

Test the card output. This command plays a woman voice on 2 channels ("Front Right", "Front Left"):

speaker-test -c2 -D plughw:UA25EX -twav

Playing sound

In the following example, Advance button is set to ON, and sample rate is 48 Khz. Do not forget to cold/hot reboot whenever you change settings.

To play a sound:

aplay -D plughw:UA25EX foo.wav

```
And it plays beautifully into my headphones...which are connected into my UA-25EX card. Now, how can that be? So it kind of works even when set on Advance Driver and 48 kHz. Just not together with JACK.

[edit] More strangeness. I set up Audacity to record with UA-25EX card in 48000 Hz and 24 bit. No problem! Both records and plays without issues.

---

### Post by AutoStatic on 2010-04-21
aplay, speakertest and Audacity use plain Alsa, but I reckon with a pretty high latency. JACK uses ALSA too, but when using it with lower latencies you could run into issues similar to yours.
You have only two USB buses but the Edirol is sitting on its own on a bus, so that couldn't be the issue. I think it's maybe the device with the ID 8087:0020 (Intel USB 2.0 rate matching hub). Apparently that device loads the xhci kernel module. Could you check with **lsmod** ? And if the xhci module is loaded could you try unload it with **sudo modprobe -r xhci** and try JACK again with the Edirol in Advanced mode?

---

### Post by cub on 2010-04-21
> **AutoStatic said:**
> aplay, speakertest and Audacity use plain Alsa, but I reckon with a pretty high latency. JACK uses ALSA too, but when using it with lower latencies you could run into issues similar to yours.
You have only two USB buses but the Edirol is sitting on its own on a bus, so that couldn't be the issue. I think it's maybe the device with the ID 8087:0020 (Intel USB 2.0 rate matching hub). Apparently that device loads the xhci kernel module. Could you check with **lsmod** ? And if the xhci module is loaded could you try unload it with **sudo modprobe -r xhci** and try JACK again with the Edirol in Advanced mode?
I couldn't find anything on xhci from the lsmod. The closest thing was as below:
```
lsmod| grep hci
sdhci_pci               7188  0 
sdhci                  17656  1 sdhci_pci
led_class               4088  2 ath9k,sdhci
```

I tried the **sudo modprobe -r xhci** anyway but no change when trying to start JACK.

---

### Post by cub on 2010-04-23
Are we out of ideas?

I'm seriously considering going back to Windows 7 which was pre-installed on the Vaio. It feels like a major failure but reverting to 16 bit and 44.1 kHz after I spent over €100 on new equipment (to improve my recording quality!) also seem stupid. After all my research it seems I bought the wrong laptop after all. :(

---

### Post by Pablo_F on 2010-04-23
Bionbrains said:
> I'm just trying to configure the outputs/inputs for jack in order to get something to be recognized in ardour

It is the other way. When you start jack, you will see the system (audio card) connections only because there are no software clients running yet. Make sure you see your card's inputs and outputs (maybe you will see more outputs than analog ones you actually have because the card may have an internal mixer whose outputs are exposed by the alsa driver).

When you start ardour, some new ports will appear in the connection window. If you add tracks/buses, their input and/or output ports will appear too.
 
This does not mean you need to make the connection in that window. You can also use ardour to route the signals (more easily), in the Mixer or in the track/bus inspector. Or you can also use patchage. 

See jack as a server waiting for clients like ardour and others. Its first and must-have client is the soundcard. If all is fine with it, all will be fine with any well programmed "jackified" audio app.

Cheers! Pablo

---

### Post by Pablo_F on 2010-04-23
Hi cub, 

Some questions/ideas

1. Unmark "no memory lock"

2. what are the output of "free" and "ulimit -l"?

3. htop also may help to find the problem:

F2 -> Display options -> Unmark hide kernel threads
F6 -> Sort by PRI

Try to identify the irq number of the USB port your card is using.
Check with 

cat /proc/interrupts

And maybe, raise the priority with

sudo chrt -f -p 82 PID

where PID is the process ID number of the irq (left column). 

Also, give jack priority 70 (in the jack setup).

4. There is a diagnosis script in 
[http://www.linuxmusicians.com/viewtopic.php?f=27&t=452](http://www.linuxmusicians.com/viewtopic.php?f=27&t=452)

5. Have you tried with another distro, AV Linux maybe?




Cheers! Pablo

---

### Post by cub on 2010-04-23
> **Pablo_F said:**
> Hi cub, 

Some questions/ideas

Unmark memory lock

1. what are the output of "free" and "ulimit -l"?

2. There is a diagnosis script in 
[http://www.linuxmusicians.com/viewtopic.php?f=27&t=452](http://www.linuxmusicians.com/viewtopic.php?f=27&t=452)

3. htop also may help to find the problem
F2 -> Display options -> Unmark hide kernel threads
F6 -> Sort by PRI

Try to identify the irq number of the USB port your card is using.
Check with 

cat /proc/interrupts

And maybe, raise the priority with

sudo chrt -f -p 82 PID

where PID is the process ID number of the irq (left column). 

4. Have you tried with another distro, AV Linux maybe?

Cheers! Pablo
I unmarked the memory lock after watching a jack tutorial on youbtube. :)

And then:
1.
```
jimmy@jimmy-vaio:~$ free
             total       used       free     shared    buffers     cached
Mem:       3909556     662468    3247088          0      46112     165588
-/+ buffers/cache:     450768    3458788
Swap:      7815612          0    7815612
jimmy@jimmy-vaio:~$ ulimit -l
unlimited
```
2. Will read more when I get home from work.

3. I couldn't get much useful information from **htop** but will take a closer look this evening as well.

```
jimmy@jimmy-vaio:~$ cat /proc/interrupts 
            CPU0       CPU1       CPU2       CPU3       
   0:        134          0          0          0   IO-APIC-edge      timer
   1:       1650          6       1582          6   IO-APIC-edge      i8042
   8:          0          0          0          1   IO-APIC-edge      rtc0
   9:        479         92        485         94   IO-APIC-fasteoi   acpi
  12:         34       7841         37       7838   IO-APIC-edge      i8042
  16:         69       4049         69       4165   IO-APIC-fasteoi   ehci_hcd:usb1, ath
  17:         29         22         34         20   IO-APIC-fasteoi   mmc0, HDA Intel
  19:          0          0          0          0   IO-APIC-fasteoi   mmc1
  22:        309         94        315         93   IO-APIC-fasteoi   HDA Intel
  23:         19        358         12        362   IO-APIC-fasteoi   ehci_hcd:usb2
  24:          2          0          0          0  HPET_MSI-edge      hpet2
  25:          0          0          0          0  HPET_MSI-edge      hpet3
  26:          0          0          0          0  HPET_MSI-edge      hpet4
  27:          0          0          0          0  HPET_MSI-edge      hpet5
  34:       6450        790       6450        787   PCI-MSI-edge      ahci
  35:       1304      25382       1318      25317   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
 NMI:          0          0          0          0   Non-maskable interrupts
 LOC:     637209     636040     633552     633924   Local timer interrupts
 SPU:          0          0          0          0   Spurious interrupts
 CNT:          0          0          0          0   Performance counter interrupts
 PND:          0          0          0          0   Performance pending work
 RES:       1043       7158       1130       7665   Rescheduling interrupts
 CAL:        666        678        628        142   Function call interrupts
 TLB:        657        645       1255        862   TLB shootdowns
 TRM:          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0   Threshold APIC interrupts
 MCE:          0          0          0          0   Machine check exceptions
 MCP:          4          4          4          4   Machine check polls
 ERR:          0
 MIS:          0
```

4. Today I downloaded both AV Linux and 64 Studio to try out.

---

### Post by AutoStatic on 2010-04-23
@cub, could you post the output of **lsusb -vvv** ?

---

### Post by cub on 2010-04-23
> **AutoStatic said:**
> @cub, could you post the output of **lsusb -vvv** ?
It created quite a long list of information so I attached it as a txt-file.

Off topic: My friends are amazed I'm still trying to get this done. "But you already have a legal Windows 7 license?!?!".
I, on the other hand, am still amazed people I don't know still is sacrificing their time to try to solve my problem..for free! My friends will never understand why we do it..:D

---

### Post by Pablo_F on 2010-04-23
Before anything else, 

I have just read this thread in the ardour forum by a UA-25EX user (mihai007)
[http://www.ardour.org/node/3481#comment-20942](http://www.ardour.org/node/3481#comment-20942)

¿Could it be that you just have to replug the usb port?

---

### Post by cub on 2010-04-23
> **Pablo_F said:**
> Before anything else, 

I have just read this thread in the ardour forum by a UA-25EX user (mihai007)
[http://www.ardour.org/node/3481#comment-20942](http://www.ardour.org/node/3481#comment-20942)

¿Could it be that you just have to replug the usb port?
Unfortunately not. I have tried booting the pc with the card plugged in, connected it after I have logged in, disconnected and connected while logged in....still no change.

This evening I also tried the AV Linux live cd and got the same error messages from JACK. I tried to do an installation of both AV Linux and 64 Studio 3 Beta but they both failed during installation so right now I'm restoring Windows..:/

---

### Post by AutoStatic on 2010-04-23
Thanks cub for the lsusb output. It doesn't reveal anything though. I suspect it's the USB ports on your motherboard, not that their faulty but I get the feeling that those ports don't allow big data streams. Maybe it's an option to get yourself a USB expansion card, those are fairly cheap, and try the Edirol on those ports.
And Pablo_F, if you enable or disable the Advanced setting then you have to replug the cable, that's right, that's also the case with my UA-25 (the predecessor of the UA-25EX).

---

### Post by cub on 2010-04-23
> **AutoStatic said:**
> I suspect it's the USB ports on your motherboard, not that their faulty but I get the feeling that those ports don't allow big data streams. Maybe it's an option to get yourself a USB expansion card, those are fairly cheap, and try the Edirol on those ports.
You mean to get like a pc-card with usb-ports on it? [http://www.dustinhome.se/pd_5010334610.aspx](http://www.dustinhome.se/pd_5010334610.aspx)
because..well...there is no such openings to plug into my precious Sony Vaio. :(

I sure picked the wrong laptop for Ubuntu Studio, that's for sure...

---

### Post by AutoStatic on 2010-04-24
Ouch, forgot that it's about a notebook, sorry for that. I think you have to dig a little deeper into what kind of USB ports your Vaio has. Could you post the outcome of **lspci -vvv** ? That's also  pretty big text file so you'll probably need to attach it. I'd really like to know what USB controller chipset is in the Vaio.

---

### Post by cub on 2010-04-24
> **AutoStatic said:**
> Ouch, forgot that it's about a notebook, sorry for that. I think you have to dig a little deeper into what kind of USB ports your Vaio has. Could you post the outcome of **lspci -vvv** ? That's also  pretty big text file so you'll probably need to attach it. I'd really like to know what USB controller chipset is in the Vaio.
I'm on deep water now so I just attached the output. I looked through the file but it means nothing to me..:P

---

### Post by AutoStatic on 2010-04-24
Thanks! Unfortunately, your system is just a bit too new: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532021](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532021)

So that's probably why JACK won't run properly with your card in Advanced mode. Maybe Lucid Lynx 10.04 fixes some issues or you could try a newer kernel from the Ubuntu kernel PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/)

That's a brand new 2.6.34 kernel that should have better support for your notebook. You only need the kernel image ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/linux-image-2.6.34-020634rc2-generic_2.6.34-020634rc2_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/linux-image-2.6.34-020634rc2-generic_2.6.34-020634rc2_amd64.deb)), download it and double-click it. This opens gdebi, a package installer. You can safely install it even though it might seem pretty hefty, installing a different kernel. After restarting you should be able to select this kernel in your Grub2 boot menu. Boot with this kernel and hopefully the card works better now. If you have issues with the kernel (graphics or network not working etc.), reboot, select your old kernel (2.6.31) and when booted open Synaptic, search for 'linux-image' and uninstall the 2.6.34 kernel again.

---

### Post by cub on 2010-04-24
Hmm I don't remember which kernel was on the 10.04 Beta2 I tried out. I'll try the .34 kernel on my 9.10 in the meantime.

[edit]That was quick. My laptop didn't boot with the 2.6.34 rc2 kernel. Though I did pick [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/linux-image-2.6.34-020634rc2-generic_2.6.34-020634rc2_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc2-karmic/linux-image-2.6.34-020634rc2-generic_2.6.34-020634rc2_i386.deb) since I run 32 bit Ubuntu. I suppose that was the right kernel?

---

### Post by AutoStatic on 2010-04-24
Yes, if you're running a 32bits Ubuntu then you need the i386 kernel (I think you're depriving yourself by running a 32bits OS on your notebook though). But it didn't boot? Any idea where it got stuck? 10.04 has kernel 2.6.32.

---

### Post by cub on 2010-04-26
Yes, I installed the 32-bit version to get the exact same setup as my old laptop to try to narrow down possible sources of error. When 10.04 goes live I'll use the 64-bit version.

The kernel fail is in the bootup and the last line produced say **kernel_thread_helper** and some numbers.

---

### Post by cub on 2010-04-26
I just tried out the 2.6.33 kernel. Funny thing, it refused to show my mouse pointer. The mouse worked but I could see the pointer. After fiddling around I got JACK up, tried out my settings of Advanced Driver and 48 kHz. JACK shut down with the same messages as with the 9.10 standard and RT kernel. I suppose I'll wait for the 2.6.34 to be released and try again then.

---

### Post by jorrieboy on 2010-05-02
I have a question:

Is it possible to run JACK on a netbook (samsung nc-10), and if so, how?

I want to use it for connecting my electric guitar to the microphone plug on my netbook, and then use the rakarrack real time guitar effects, like this:

[http://www.youtube.com/watch?v=4m0EBl19Ue8](http://www.youtube.com/watch?v=4m0EBl19Ue8)

---

### Post by AutoStatic on 2010-05-03
Hello jorrieboy, that's possible: [http://www.youtube.com/watch?v=l15-17oCbOQ](http://www.youtube.com/watch?v=l15-17oCbOQ)

That's Rakarrack running on my netbook which has similar specs as the Samsung. But you do need a pre-amp for your guitar, you can't just plug it into the mic input. As for JACK, it won't run happily unless you use a lightweight Desktop Environment (like LXDE, XFCE or in my case IceWM). And using your onboard card isn't the best option either.

---

### Post by lien_meat on 2010-05-12
@cb951303: thank you so much for the info you gave!  I would have never figured out how to get jack working without your help.  I've tried before and fail, but your instructions worked without a hitch.  Just wanted to let you know it means a lot to someone.

---

### Post by cub on 2010-05-14
[deleted flame]

---

### Post by Grone1985 on 2010-07-04
> **AutoStatic said:**
> Create two accounts. One for browsing, office apps, watching videos etc with PulseAudio enabled and one for music production with PulseAudio disabled.
PulseAudio is for consumer audio and JACK for pro audio in short. You can't run Firefox and Windows Media Player through ASIO either.

Hi AutoStatic, how do I disable PA on the second account? Thanks!

---

### Post by AutoStatic on 2010-07-05
Hello Grone1985,

[LIST]
[*]Create the file *~/.pulse/client.conf* with one single line: *autospawn = no*
[*]Add a new Startup Application: System - Preferences - Startup Applications
[*]Click Add, Name could be something like Kill PulseAudio and the command should be **pulseaudio -k**
[/LIST]

---

### Post by Grone1985 on 2010-07-05
> **AutoStatic said:**
> Hello Grone1985,

[LIST]
[*]Create the file *~/.pulse/client.conf* with one single line: *autospawn = no*
[*]Add a new Startup Application: System - Preferences - Startup Applications
[*]Click Add, Name could be something like Kill PulseAudio and the command should be **pulseaudio -k**
[/LIST]

Worked like a charm. Thanks!

---

### Post by Turner Herman on 2010-12-17
hey guys, i got jack to work last night but today when i went to open it i got this message saying it wont connect? and now anymore when i open the jack audio connection it goes dormant and wont let me click anything? im somewhat new to ubuntu so if anybody could help me out i'd really appreciate it

---

### Post by Turner Herman on 2010-12-17
p, li { white-space: pre-wrap; } [COLOR=#999999]07:10:16.635 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]07:10:16.637 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]07:10:16.735 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]07:10:16.950 ALSA connection change.[/COLOR]
 [COLOR=#66CC99]07:10:16.951 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]07:10:29.117 ALSA connection change.[/COLOR]
 [COLOR=#999999]07:13:16.290 Startup script...[/COLOR]
 [COLOR=#990099]07:13:16.292 artsshell -q terminate[/COLOR]
 Cannot open qjackctl client
 sh: artsshell: not found
 [COLOR=#999999]07:13:16.711 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]07:13:16.711 JACK is starting...[/COLOR]
 [COLOR=#990099]07:13:16.712 /usr/bin/jackd -r -u -dalsa -dhw:0 -r44100 -p1024 -n2 -P -s -m -S -H -M[/COLOR]
 Cannot create thread 1 Operation not permitted
 [COLOR=#999999]07:13:16.739 JACK was started with PID=1790.[/COLOR]
 Cannot create thread 1 Operation not permitted
 `default' server already active
 Failed to start server
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]07:13:16.788 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]07:13:16.789 Post-shutdown script...[/COLOR]
 [COLOR=#990099]07:13:16.790 killall jackd[/COLOR]
 [COLOR=#999999]07:13:17.233 Post-shutdown script terminated successfully.[/COLOR]
 [COLOR=#FF0000]07:13:18.889 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#FF0000]07:13:26.436 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket

---

### Post by AutoStatic on 2010-12-17
Try disabling Unlock Memory, Soft Mode, Monitor, Force 16bit, H/W Monitor and H/W Meter in QjackCtl (JACK Control).

---

### Post by Pablo_F on 2010-12-17
And enable realtime mode.  You might need to:

sudo dpkg-reconfigure -p high jackd2

And allow users who belong to the audio group rtprio and memlock privileges (just say yes). Then add your user to the audio group by typing in a terminal:

sudo adduser your_user_name audio

And reboot the computer. Then, run jack with realtime mode enabled. The other options in the left column are not very useful afaik.

Cheers, Pablo

---

### Post by christophski on 2010-12-19
@Turner Herman

I find the first thing to do is ALWAYS to make sure you have the right interface selected. Sometimes the devices get numbered in a different order by mistake, especially if you have an external sound card which has to be switched on.

---

### Post by Pablo_F on 2010-12-19
> I find the first thing to do is ALWAYS to make sure you have the right interface selected. Sometimes the devices get numbered in a different order...

You should specify your cards by name, not by number, in the jack setup. Problem solved.

---

### Post by youWho on 2011-02-11
Can somebody please help??!
Audio output in general works fine. That is, I can play files with sweep for example and basically any other app I've tried. The problem is that although Jack runs, as far as I know just fine, there's no audio output. If for example I play something in Ardour I can see activity on the meters, but no matter what I try I get no sound.

---

### Post by Pablo_F on 2011-02-11
> Can somebody please help??!  --> [http://ubuntuforums.org/showthread.php?t=1686041](http://ubuntuforums.org/showthread.php?t=1686041)

---

### Post by youWho on 2011-02-12
> **Pablo_F said:**
> --> [http://ubuntuforums.org/showthread.php?t=1686041](http://ubuntuforums.org/showthread.php?t=1686041)

Well, the problem I was having is solved. By the way sorry  if it was inappropriate to post that question here. I wasn't sure. Anyway I started a  new thread instead. If  it helps anybody to know, the things I did that fixed it are listed there.

---

### Post by Richieisinuse on 2011-02-16
Thank you very much! This was very helpful. Install and setup seemed to take. I'm going to try and see if it worked now.

---

