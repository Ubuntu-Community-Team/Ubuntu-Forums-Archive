---
title: "US-122L external sound card recognition problem"
date: 2010-10-09
forum: Ubuntu Studio
---

### Post by stewartnairn on 2010-10-09
I have been going round in circles trying to get my Tascam US-122L to work under Lucid Lynx (with ubuntu studio).

Running  cat /proc/asound/cards gives me

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 16
 1 [U0x46d0x804    ]: USB-Audio - USB Device 0x46d:0x804
                      USB Device 0x46d:0x804 at usb-0000:00:1d.7-4, high speed
 2 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/007)

I think that I need to move the us122l from 2 to 0 but have no idea how to do that.

When I connect up my Edirol UA-20 instead of the US-122L everything works fine. I can choose the UA-20 from the devices that show up in the sound Preferences window. With the US-122L connected it doesn't show up in that window.

Any help appreciated.

Thanks

---

### Post by Pablo_F on 2010-10-09
Hi! What is the output of 

cat /proc/asound/modules
lsmod | grep snd

?

OTOH, just in case, give pavucontrol a go, instead of the gnome sound preferences.

sudo apt-get install pavucontrol

Sound and Video --> Pulseaudio Volume Control

Cheers! Pablo

---

### Post by stewartnairn on 2010-10-09
> **Pablo_F said:**
> Hi! What is the output of 

cat /proc/asound/modules
lsmod | grep snd

?

OTOH, just in case, give pavucontrol a go, instead of the gnome sound preferences.

sudo apt-get install pavucontrol

Sound and Video --> Pulseaudio Volume Control

Cheers! Pablo

cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_usb_us122l

lsmod | grep snd
snd_usb_us122l         12911  0 
snd_hda_codec_realtek   203374  1 
snd_hda_intel          22037  2 
snd_usb_audio          75765  1 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_usb_lib            15801  2 snd_usb_us122l,snd_usb_audio
snd_hwdep               5412  3 snd_usb_us122l,snd_usb_audio,snd_hda_codec
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  21 snd_usb_us122l,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm



I cant see the US-122L using pavucontrol either.

Stewart

---

### Post by Pablo_F on 2010-10-09
It seems a problem with pulseaudio. If there is no more to it than this, don't worry. I suppose you will want to use jack with that card. Try this test: 

First of all, you need that pulseuadio does not autospawn. So you have to:

gedit ~/.pulse/client.conf

And add the line:

autospawn = no

Save and close. Now, kill pulseaudio:

pulseaudio -k

Now look at the ouput of 

aplay -L

and run the speaker test, as explained here:
[http://alsa.opensrc.org/index.php/Speaker-test](http://alsa.opensrc.org/index.php/Speaker-test)

If in doubt, show the output of aplay -L  

Assuming that the problem is pulseadio, and not the alsa driver, 
you can try a higher level test with jack. jack is another audio server, Use it for recording audio at low latency and enjoying the best linux music audio apps.  

So you start Jack Control, with the alsa driver. In the interface field write down the name of your device:

hw:US122L

Start the server. Try playing some music with audacious with the jack output plugin or another jack-friendly audio player like aqualung (sudo apt-get install aqualung).

If jack does not start, copy here the message window.

To come back to the "normal" gnome sound server, start pulseadio again: 

pulseaudio --start


Cheers! Pablo

---

### Post by stewartnairn on 2010-10-09
> **Pablo_F said:**
> It seems a problem with pulseaudio. If there is no more to it than this, don't worry. I suppose you will want to use jack with that card. Try this test: 

First of all, you need that pulseuadio does not autospawn. So you have to:

gedit ~/.pulse/client.conf

And add the line:

autospawn = no

Save and close. Now, kill pulseaudio:

pulseaudio -k

Now look at the ouput of 

aplay -L

and run the speaker test, as explained here:
[http://alsa.opensrc.org/index.php/Speaker-test](http://alsa.opensrc.org/index.php/Speaker-test)

If in doubt, show the output of aplay -L  

Assuming that the problem is pulseadio, and not the alsa driver, 
you can try a higher level test with jack. jack is another audio server, Use it for recording audio at low latency and enjoying the best linux music audio apps.  

So you start Jack Control, with the alsa driver. In the interface field write down the name of your device:

hw:US122L

Start the server. Try playing some music with audacious with the jack output plugin or another jack-friendly audio player like aqualung (sudo apt-get install aqualung).

If jack does not start, copy here the message window.

To come back to the "normal" gnome sound server, start pulseadio again: 

pulseaudio --start


Cheers! Pablo

Thanks for your help so far Pablo, but I am not out of the woods yet.

I followed your instructions down to the speaker test. My output from aplay -L is...

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers


I am guessing that I should see some reference to US122L in there.

I didn't do the speaker test on the ALC662, which I presume is the built in sound card since I have no speakers attached to it - I normally have sound from USB to Edirol UA20 to HiFi. Happy to find speakers to plug into built in sound card if it is of diagnostic value. Just thought the fact that the US122L was not showing up was more of a problem.

Keen to do whatever you suggest.

---

### Post by Pablo_F on 2010-10-10
Weird. I am not sure why it doesn't appear. Testing the onboard is useless. Does it appear in 

lsusb 

and

aplay -l

?

---

### Post by stewartnairn on 2010-10-10
> **Pablo_F said:**
> Weird. I am not sure why it doesn't appear. Testing the onboard is useless. Does it appear in 

lsusb 

and

aplay -l

?

Looks to be a usb issue.

To simplify things I unpluged all usb stuff except the reciever for my remote keyboard. With the US122L plugged in (and it's usb light on)lsusb gives me...


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0644:800e TEAC Corp. 
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Replacing the US122L with the UA20 gives...

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0582:0025 Roland Corp. EDIROL UA-20
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

with the UA20 pluged in aplay -L gives...

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA20 [UA-20], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

which looks (and plays) fine. I imagine the fact that lsusb doesn't report the US122L when it is plugged in explains why aplay -L gives ...

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The frustrating thing (well one of them anyway) is that the US122L works fine under windows).

Stewart



which looks

---

### Post by Pablo_F on 2010-10-10
Have you tried in different USB sockets?

Let's hope Autostatic see this and lends you a hand. I am not an expert on USB. A bad controller or something? Ah by the way, try installing the alsa-firmware package.

You can always ask in the alsa user mailing list or in the linux audio user mailing list where the most knowledgeable people in this field (including the driver developers) are reading.

Cheers! Pablo

---

### Post by AutoStatic on 2010-10-10
> **stewartnairn said:**
> Bus 001 Device 007: ID 0644:800e TEAC Corp.That's the US122L.

And all the other commands report the US122L being recognized, the proper kernel module gets loaded and ALSA sees it also. So only **aplay -l** doesn't show it.

I think aplay -l doesn't show it because you probably still need to create a custom *.asoundrc* file as pointed out here: [http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030201](http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030201)

Normally, you put such a *.asoundrc* file in your home directory. So could you give that a try and report back?

---

### Post by Pablo_F on 2010-10-10
Oh, I did not try very hard, did I? I missed that. Thank you Jeremy!

Anyway, I can't see any alsa-plugins-usbstream or related package in ubuntu but the .asoundrc hack is also mentioned here:
[http://wiki.briata.org/doku.php](http://wiki.briata.org/doku.php)

(skip everything up to step 3, it is outdated and probably not necessary anymore)

So hopefully, just this command:

wget -c [http://pub.briata.org/us-122l/.asoundrc](http://pub.briata.org/us-122l/.asoundrc) ~/.asoundrc

(I checked and it is the same file as the one suggested in the fedora site).

and writing down the right interface entry in the setup of qjackctl should allow you to have your TASCAM up and running through the jack audio server.

Cheers! Pablo

---

### Post by stewartnairn on 2010-10-10
Thanks guys you have been wonderful. Got the  .asoundrc file, and the right settings in jack. A lot of footering about plugging, unplugging, logging in and out, rebooting. The Us122L seemed to come and go. Seems to be some issue re US122L not being seen after a reboot, but unplugging it then plugging it in again sorts it. Eventually  opened up Rythmbox, clicked on a radio station and got beautiful music through the speakers. Wonderful. Clicked on an mp3 and got a quick blast of Tom Jones. Opened a movie - sounded great. 

Each time I opened an app I saw it appear in the Jack connections screen and saw the connection lines.

Now, I know I could be pushing my luck here, and I clearly have a lot to learn about Jack and sound in linux, but...when I opened a browser, both chrome and firefox, nothing popped up on the Jack connections page and no sound from the browsers. Will research this myself tomorrow but if you were able to point me in the right direction, that would be wonderful.

Thanks again for everything.

---

### Post by AutoStatic on 2010-10-11
Cool that it works!
But.... You don't need JACK to be able to use your card. In fact, you're actually using JACK for the wrong purpose. JACK is a 'prosumer' low-latency sound daemon while the apps you want to use are all 'consumer' apps that are not so picky about latency. That's the territory of PulseAudio. The US122L doesn't work with PulseAudio?

---

### Post by Pablo_F on 2010-10-11
In addition to Autostatic' comment, I would like to say that there are different approaches to solve this issue, depending on your needs and your workflow.

Some prefer to have one soundcard for general purpose audio and another one for music production.

Some prefer to have different user accounts using the same card, one for general purpose audio and another one for music production. 

Some prefer to "jackify it all", including the flash player, to use one card with jack in all situations, even if jack is overkilling for general purpose audio.

Some prefer to use other tricks, like the alsa-jack sink (if not using pulseaudio) or the pulse-jack sink, so that you can connect pulseaudio to jack via patchage or qjackctl connections.

But we still don't know if your card works with pulseaudio (the ubuntu's default audio system that you control with sound preferences or pavucontrol) or not.

Cheers! Pablo

---

### Post by OFobbs on 2010-10-11
> **stewartnairn said:**
> Thanks guys you have been wonderful. Got the .asoundrc file, and the right settings in jack. A lot of footering about plugging, unplugging, logging in and out, rebooting. The Us122L seemed to come and go. Seems to be some issue re US122L not being seen after a reboot, but unplugging it then plugging it in again sorts it. Eventually opened up Rythmbox, clicked on a radio station and got beautiful music through the speakers. Wonderful. Clicked on an mp3 and got a quick blast of Tom Jones. Opened a movie - sounded great. 
 
Each time I opened an app I saw it appear in the Jack connections screen and saw the connection lines.
 
Now, I know I could be pushing my luck here, and I clearly have a lot to learn about Jack and sound in linux, but...when I opened a browser, both chrome and firefox, nothing popped up on the Jack connections page and no sound from the browsers. Will research this myself tomorrow but if you were able to point me in the right direction, that would be wonderful.
 
Thanks again for everything.
 
 
Could you post a screenshot of your JACK settings.  I've been trying to get it working and JACK sees the 122L, but I think I may have the wrong settings.
 
Thanks, 
 
Omar

---

