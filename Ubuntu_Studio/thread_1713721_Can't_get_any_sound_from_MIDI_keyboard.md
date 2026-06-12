---
title: "Can't get any sound from MIDI keyboard"
date: 2011-03-24
forum: Ubuntu Studio
---

### Post by accoustika on 2011-03-24
Hello, I'm trying to setup a working MIDI connection on Ubuntu Studio, but I can't seem to figure it out. I want to get sound from my MIDI keyboard through MIDI IN and MIDI OUT on my Steinberg MI4 USB sound card, but it seems that the MIDI signal isn't getting through. On my sound card the MIDI IN LED flashes every time I hit a note but on both JACK and ALSA I get nothing. It seems like my MIDI connection isn't being recognized on Ubuntu, almost as if it's disabled. If so is the case is there any place I can enable it from? I'm almost sure it is a port enabling issue because my audio inputs are working perfectly fine and I know how to connect everything together using JACK control. Any help here would be most appreciated because I really need to make music using my MIDI keyboard.

---

### Post by AutoStatic on 2011-03-24
Hello accoustika, maybe this helps: [http://www.youtube.com/watch?v=kBEzMC35gt8](http://www.youtube.com/watch?v=kBEzMC35gt8)

Best,

Jeremy

---

### Post by KegHead on 2011-03-24
Hi!

Have you unchecked "mute" from system/preferences/sound?

KegHead

---

### Post by accoustika on 2011-03-24
> **KegHead said:**
> Hi!

Have you unchecked "mute" from system/preferences/sound?

KegHead

It's not muted to begin with :/ My issue is not with sound in general, my issue is with MIDI only. Maybe I need to activate or enable my MIDI port from some configuration file, I think this is the issue.

---

### Post by AutoStatic on 2011-03-24
Could you post the output of **amidi -l** with everything connected? And maybe a screenshot of your QjackCtl connections window?

Best,

Jeremy

---

### Post by accoustika on 2011-03-24
> **AutoStatic said:**
> Could you post the output of **amidi -l** with everything connected? And maybe a screenshot of your QjackCtl connections window?

Best,

Jeremy
this is the output of amidi -l

antoine@ubuntwan:~$ amidi -l
Dir Device    Name

and the snapshot of JACK connections in the ALSA tab:

---

### Post by AutoStatic on 2011-03-24
Thanks! The MIDI ports are not being recognized at all apparently. I suspect the MI4 isn't fully class compliant, ie. it doesn't comply to the USB1.1 audio standard that a lot of other manufacturers do respect (Roland/Edirol, most M-Audio USB1 soundcards). But I can't find anything on this card, no technical specs, no manuals, nothing :(

Best,

Jeremy

---

### Post by accoustika on 2011-03-24
> **AutoStatic said:**
> Thanks! The MIDI ports are not being recognized at all apparently. I suspect the MI4 isn't fully class compliant, ie. it doesn't comply to the USB1.1 audio standard that a lot of other manufacturers do respect (Roland/Edirol, most M-Audio USB1 soundcards). But I can't find anything on this card, no technical specs, no manuals, nothing :(

Best,

Jeremy

But that can't be true, on windows I had no problem playing MIDI from the MI4, this sound card is made to be used with MIDI and VSTi so there HAS to be a way I can play MIDI on it on ubuntu! There just HAS to be :(

---

### Post by AutoStatic on 2011-03-24
> **accoustika said:**
> But that can't be true, on windows I had no problem playing MIDI from the MI4, this sound card is made to be used with MIDI and VSTi so there HAS to be a way I can play MIDI on it on ubuntu! There just HAS to be :(Ubuntu != Windows. If it's not class compliant it won't work with Ubuntu and probably never will as Steinberg probably has zero interest in helping out Linux audio driver developers. But I'm only assuming things here. Maybe it does work but I haven't run into reports of people that got MIDI working. What kind of MIDI keyboard do you have? That one doesn't have an USB port by any chance?

Best,

Jeremy

---

### Post by accoustika on 2011-03-24
> **AutoStatic said:**
>  What kind of MIDI keyboard do you have? That one doesn't have an USB port by any chance?


it's a KURZWEIL keyboard, one that doesn't have a USB midi port unfortunately, only standard MIDI IN and MIDI OUT ports :( am I doomed? :P

---

### Post by AutoStatic on 2011-03-25
You could try getting yourself a MIDI to USB cable. Those are fairly cheap and allow you to hook up your Kurzweil to your Ubuntu system.

Best,

Jeremy

---

### Post by zettberlin on 2011-03-25
> **accoustika said:**
> it's a KURZWEIL keyboard, one that doesn't have a USB midi port unfortunately, only standard MIDI IN and MIDI OUT ports :( am I doomed? :P

heads up, you are not :-)

A USB to MIDI adapter-cable is available for est. 10 USD / 8 EUR and should work ootb. And it can be used parallel to your audio-interface.

---

### Post by accoustika on 2011-03-26
Thanks guys for the tip and for your time, I'm gonna get me a MIDI to USB cable as this is my last resort I guess. Blessings!

---

