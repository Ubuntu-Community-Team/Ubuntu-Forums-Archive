---
title: "Fast Track Ultra:  How to record using all four tracks"
date: 2012-07-25
forum: Ubuntu Studio
---

### Post by DaveBF on 2012-07-25
Hey!  I've tried using my m-audio fast track ultra in a number of fashions.  First, I tried it in regular Ubuntu and after messing about the best I could do is record two separate tracks simultaneously (and who knows about recording over live playback).

Now I'm trying in Ubuntu studio and I seem to be running into the same problem.  It's as if JACK doesn't recognize that the FTU has four audio tracks... In fact, I'm not sure if it sees any audio tracks.  When I look at the situation in patchage it only shows two listings for the FTU, both of which are MIDI inputs.

Basically, I have no idea what I'd doing and I thought I'd ask before I go fiddling about too much with anything important.

NOTE: I currently have Win7, Ubuntu, and Ubuntu Studio installed and in Ubuntu Studio I've done no configuring.

---

### Post by Chiel92 on 2012-07-26
Hey,

I have a fasttrack pro, and i'm also struggling with some similar problems.
For me, JACK doesnt list any fasttrack pro entries in the connections window.
I just managed to get sound from my computer to the fasttrack pro, by selecting the fasttrack pro as default soundcard (and thus default system playback output).
That way, I can also capture sound from the fasttrack via the system capture. But that gives me only 1 track.

Do you have any fasttrack entries listed in JACK->Connections? (Apart from the MIDI ports)

Kind regards

---

### Post by DaveBF on 2012-07-26
The only listing I see in JACK is for the two MIDI ports on the fast track ultra.  It recognizes no audio.  However, in Patchage, FTU tracks 1 and 2 seem to be routed through the Systems capture 1 and capture 2, so I can record two tracks that way.

I suppose I should also note that upon installing the windows drivers in win7 along with ASIO I can record the full four tracks in windows... but who wants to record in windows? ;)

---

### Post by CrocoDuck on 2012-07-26
> **DaveBF said:**
> The only listing I see in JACK is for the two MIDI ports on the fast track ultra.  It recognizes no audio.  However, in Patchage, FTU tracks 1 and 2 seem to be routed through the Systems capture 1 and capture 2, so I can record two tracks that way.

I suppose I should also note that upon installing the windows drivers in win7 along with ASIO I can record the full four tracks in windows... but who wants to record in windows? ;)

Hi. Have a try by setting to 4 the "_I_nput Channels" parameter in Qjackctl.

---

### Post by DaveBF on 2012-07-26
Thanks, CrocoDuck, but I tried that and it didn't seem to change the situation.  It's as if JACK doesn't recognize that the FTU has audio outputs.

Perhaps it's a problem before JACK?  I have the most updated ALSA driver.  Is there any sort of sound card selection process?  I really know nothing about setting one of these up.

---

### Post by CrocoDuck on 2012-07-26
> **DaveBF said:**
> Thanks, CrocoDuck, but I tried that and it didn't seem to change the situation.  It's as if JACK doesn't recognize that the FTU has audio outputs.

Perhaps it's a problem before JACK?  I have the most updated ALSA driver.  Is there any sort of sound card selection process?  I really know nothing about setting one of these up.

Uhm... Repost the output of this:

```
aplay -l
```

---

### Post by DaveBF on 2012-07-26
The FTU is most definitely plugged in :P

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC665 Digital [ALC665 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Ultra [Fast Track Ultra], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by CrocoDuck on 2012-08-06
Hi, so sorry to being able to reply just now (I went on holidays in a place without internet connections...) . It seems that ALSA sees your Fast Track Ultra good. Have a look for  channels and their levels with this: 

```
alsamixer
```Select the Fast Track with the F6 key, move around with right/left arrows and set levels with up/down arrows. Sometimes happens that some soundcard doesn't work good if the internal audio card is enabled. If you can, have a try disabling your HDA intel PCH in your BIOS settings.

---

