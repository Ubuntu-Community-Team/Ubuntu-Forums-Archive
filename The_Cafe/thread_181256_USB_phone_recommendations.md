---
title: "USB phone recommendations?"
date: 2006-05-23
forum: The Cafe
---

### Post by banjobacon on 2006-05-23
Can anyone here recommend a USB phone for use with Ekiga, or other VoIP software? I'm looking for something like [this](http://www.amazon.com/gp/product/B000AR8QHC/sr=8-1/qid=1148434927/ref=pd_bbs_1/104-5871821-9314365?%5Fencoding=UTF8). I'm interested in something inexpensive and small, that I can easily bring with me on trips and use with my laptop.

Most of these phones are made to work with Windows and Skype, so it's hard to tell if it'll work on Linux with SIP-based software.

---

### Post by Andrew1234 on 2006-06-09
I would like a USB phone to use on skype, has anyone had sucess with any of the usb phones with Dapper, if so can you let me know the make and model?

---

### Post by sas on 2006-07-31
bump.

anyone got any ideas on the original posters question?

---

### Post by banjobacon on 2006-07-31
> **sas said:**
> bump.

anyone got any ideas on the original posters question?
By the way, the product I intended to link to is not the same one that is now linked to. Maybe Amazon has changed the link around since I posted originally.

I ended up buying something *like* this:
[img]http://ec1.images-amazon.com/images/P/B000B9UWM6.01._AA280_SCLZZZZZZZ_.jpg[/img]

When plugged in, it shows up as an audio device, and works well for the most part. The number pad is useless in Linux, and the volume buttons control the main volume, for some reason. Sound works, though, and that's the important part. I'll be placing my calls through the computer, anyway.

I haven't realy used it much, so I don't remember how the sound quaity was. Probably good enough.

You'll need a USB 2.0 port to use this. With earlier USB ports, the microphone will not work.

And the non-functional buttons work in Windows, if you care about that.

---

### Post by sas on 2006-08-01
sweet, I've seen some like that, that'll do for me. Thanks for following up.

---

### Post by Johnsie on 2006-09-15
I'm looking for one that will actually ring with Ekiga... Anyone found one that does that? I can talk ok on mine but I'd really like it to ring too... At the moment I've got my computer speakers ringing instead but it would be nice to have the dial tones, working buttons and a working ringer like on Windows...

---

### Post by tagra123 on 2006-09-16
PAP2-NA is an external lan phone adapter that is not part of the computer

Not necessarly what you were looking for --  an extra item to carry around but it works just dandy.

Walmart sells a locked version of this adapter (It only works with Vonage) Don't use that one. I purchased mine on ebay. It took a month to arrive but it works just great. Plug in a real phone (it allows for two phones).

Because no computer is needed it doensn't matter what OS you are using -- your phone just works.

---

### Post by ComplexNumber on 2006-09-16
all phones with usb are the same as far as what the OP wants. usb version 2.0 has faster trasnfer speeds and (probably) more capabilities.

---

### Post by Onyros on 2006-09-16
[IMG]http://www.loveno.be/images/product/3d9ff4aea71a55c277d408811ea72127.gif[/IMG] ---> iDream SUP001 USB Phone

I have one of these that I carry around with my laptop, and it works (almost) perfectly in Ubuntu... apart from the key functions on the phone itself (and it does not ring), I always have to dial and pick calls up through software. But it's really inexpensive (I bought it for 15 euros) and does the job more than adequately.

I also have a Cyberphone K at home, better sound quality than the SUP001, but the keys on the phone have no functionality, either. Even so, it was much more expensive (around 35 euros).

---

### Post by DoctorMO on 2006-09-16
We use Cyberphone K's at work and from a developers point of view it looks like this:

USB Device (Phone)
 - USB Audio Device Input (mic)
 - USB audio Device Output (earphone/ring)
 - USB HID (Human Interface Device)

the reason there phones work is because they have standard USB Audio Device nodes, without these the phone wouldn't work at all. I don't believe there are any specific HID drivers for these phones yet and the way you make them ring is by sending a signal to the HID that the phone is ringing.

This is also how you tell when the phone has been picked up and how you set it to load speaker.

So anyone with some spare time and one of these phones, have a play with HID device support :-D it should work just like a usb keyboard (also a HID) or a usb joystick/mouse (also HID) so you could use those as examples.

Or if anyone wants to pay me a large sum of money :-D

---

### Post by oliverb on 2006-09-17
I'd like to apologise in advance for crossposting but I have a very similar problem.

I have a "VoIP keyboard" from A4-tech, it has a "C-media" usb sound adaptor.

The hardware seems to be detected, I can select the adapter as a sound device and I can see it's mixer options, but I cannot get any sound out of it, or record from it. I can set the mixer to feedback and generate a loud whistle.

I've seen some webpages about setting up usb sound but I don't know how much is relevant as one page says to download and compile usbhid and snd-usb-audio. AFAIK those are already present. 

There's also some long config changes, but none really make it clear where they go or what they replace. In short I don't have a clue past finding the device info in device manager.

OOT: Regarding handsets with keys: if the phone device installs as a generic HID then is it just acting as a keyboard but returning higher than normal scancodes, or maybe returning normal keycodes+a combination of shift,control,alt? I ask this because I thought HID devices were limited to keyboards, mice (+trackballs) and joysticks/joypads. Also I notice that Windows XP accepts a keyboard with shortcut buttons without needing a driver, so I figure that there must be a "standard" for keys beyond the normal 102.

---

