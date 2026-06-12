---
title: "Unable to enumerate USB device - Raspberry Pi 4 2gig- Ubuntu Server 20.04"
date: 2020-06-03
forum: Server Platforms
---

### Post by chase.tw on 2020-06-03
I'm new to the forum, if this isn't the correct spot to post this, I'd appreciate being pointed to the correct location.

I recently heard Ubuntu 20.04 was certified for the Raspberry pi 4 so I went ahead and removed the current version of Raspbian (which worked fine, I had no issues) and flashed Ubuntu Server 20.04 with etcher to the SD card. On boot, I get a message:

```
spi-bcm2835 fe204000.spi: could not get clk: -517
usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
usb usb2-port2: unable to enumerate USB device
```

This message repeats a few more times. Nothing is plugged into the USB ports. Eventually, the messages stops, I plug in my keyboard (on any port, they all work), I am able to login, connect to wifi, perform updates. I unplug the keyboard and I then connect to the pi from my laptop via ssh and tmux; everything runs smoothly for a little bit until the ssh session stops responding (can't scroll, type, ctrl-c, ctrl-z, etc.). I go look at the monitor the pi is attached to and the message above is displayed and just repeats; it never stops. I have to unplug and re-plug the pi, and the whole thing starts over. Is it a hardware issue? Can i turn off that USB device so it doesn't try to enumerate it?

---

### Post by LHammonds on 2020-06-03
I assume you downloaded the [ARM version of Ubuntu Server 20.04]("https://ubuntu.com/download/server/arm")?

**EDIT:**

Looking at a few random install guides for RPi seems like they require an unofficial build tailored for the RPi.

[Roadmap for official support for Raspberry Pi 4]("https://ubuntu.com/blog/roadmap-for-official-support-for-the-raspberry-pi-4")

I have not found anything yet that claims Ubuntu is certified for RPi4.  Can you link where this is mentioned?

Raspbian is their official OS but I think they are still in BETA trying to get an finalized version for RPi4

LHammonds

---

### Post by chase.tw on 2020-06-03
Here is the link you requested:

[https://ubuntu.com/blog/ubuntu-20-04-lts-is-certified-for-the-raspberry-pi](https://ubuntu.com/blog/ubuntu-20-04-lts-is-certified-for-the-raspberry-pi)

I’ve also heard this information on 1 or 2 podcasts. But the certification pretty recently happened. Most tutorials online still use 19.10 and like you said, those tutorials require some tweaking.

And no, I got my download from here:

[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

---

