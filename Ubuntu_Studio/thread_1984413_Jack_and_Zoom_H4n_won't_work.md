---
title: "Jack and Zoom H4n won't work"
date: 2012-05-21
forum: Ubuntu Studio
---

### Post by finnvreten on 2012-05-21
Hi,
I'm a relative noob to Ubuntu and a complete noob to Ubuntu Studio. I installed an assortment of audio-related programs on my 11.04 (natty) as per one of the instructions I found on help.ubuntu.com. Jack and Ardour start right out-of-the-box with the laptop sound card. Then I tried the Zoom H4n and Jack simply won't have it. I set device to hw 1,0 (USB audio). I also tried setting it to hw 1 (h4). But that won't work either.

I don't really know how to do this stuff, so any help would be greatly appreciated. I really hope I've made something stupid, which is easy to fix :)

(messages at startup of QjackCtl)
 p, li { white-space: pre-wrap; }  [COLOR=#999999]00:46:34.445 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]00:46:34.446 Statistics reset.[/COLOR]
 [COLOR=#cccc99]00:46:34.549 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = Filen eller katalogen finns inte (ie "There is no such file or folder")
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]00:46:34.588 ALSA connection graph change.[/COLOR]
 [COLOR=#999999](after I press "Start")
[/COLOR]
[COLOR=#999999]00:46:38.145 JACK is starting...[/COLOR]
 [COLOR=#990099]00:46:38.145 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:1,0 -r44100 -p128 -n2 -S[/COLOR]
 Cannot connect to server socket err = Filen eller katalogen finns inte
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]00:46:38.202 JACK was started with PID=5272.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:1
 control device hw:1
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1,0|hw:1,0|128|2|44100|0|0|nomon|swmeter|-|16bit
 control device hw:1
 Using ALSA driver USB-Audio running on card 1 - ZOOM Corporation H4 at usb-0000:00:1d.7-3.2, full speed
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 2 periods for playback
 ALSA: could not start playback (Broken pipe)
 Cannot start driver
 JackServer::Start() failed with -1
 control device hw:1
 Released audio card Audio1
 audio_reservation_finish
 control device hw:1
 Failed to start server
 [COLOR=#999999]00:46:38.420 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]00:46:40.289 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = Filen eller katalogen finns inte
 Cannot connect to server socket
 jack server is not running or cannot be started


Thanks,
-Carl

---

### Post by CrocoDuck on 2012-05-31
Hi. Have a look here: [http://ardour.org/node/2964](http://ardour.org/node/2964) . Just out of curiosity, post the output of: 

```
cat /proc/asound/modules
```

with your sound devices plugged.

---

### Post by finnvreten on 2012-05-31
Cheers CrocoDuck
Thanks for helping!
I will check the link and see if I get any wiser :)
In the mean time, the output is:

0_snd_hda_intel
1 snd_usb_audio

-Carl

---

### Post by CrocoDuck on 2012-06-01
Can you set something in the "Interface" option in qjackctl? If you simply installed some cool packages on 11.04 please check if your user is in the audio group:

```
grep audio /etc/group
```

If you see your user name here you are ok. If not:

```
useradd -G audio yourusername
```

You should do the last operation logged as root. I recommend to log with su:

```
su
```

If you didn't set a root password is better to set it:

```
sudo passwd root
```

You can also view all the groups that hosts your user with:

```
id yourusername
```

check if you see the word "audio" in these output to be sure your user was successfully added.

---

### Post by jejeman on 2012-06-01
No need for root password, just use sudo.
Also simpler command to see to which groups you belong is
```
groups
```

---

### Post by finnvreten on 2012-06-01
Dear cool people :)

Thanks for the help! Greatly appreciated!

BTW: I was already added to the audio group. 

While  searching the web for ideas I stumbled across someone saying that  sometimes you get these problems after installing ubuntu studio elements  on a standard ubuntu OS. So I DL:ed the Live DVD of Ubuntu Studio  12.04. Tried it from the DVD - and the H4n worked like a charm!

I installed a fresh Ubuntu Studio  and I'm guessing it will work nicely. If not I'll be back with more (other) questions!

Be cool!
-Carl

---

