---
title: "USB audio interface"
date: 2011-05-14
forum: Ubuntu Studio
---

### Post by Icebear on 2011-05-14
Hi

I been recording with Ubuntu studio and a friend saw it and was impressed with it.

He also wants to do some recording also. I have a firewire (1394) audio interface but he only has usb.

So what would be a good usb audio interface withmaybe two inputs.

Does the Roland UA-25EX work now with ubuntu. I see in some older versions of Linux it had problems.

---

### Post by Pablo_F on 2011-05-14
Hi, 

Check the usb controller first. Ask him for the terminal output of:

lspci |grep -i usb

Cheers, Pablo

---

### Post by barisurum on 2011-05-14
Any class compliant usb 1x interface would play well with linux and Roland UA-25EX is one of them AFAIK. If you want good preamps for less though I can recommend presonus audiobox usb. Its 2 combo in, 2 out + stereo phones out, 24bit 48khz, has midi in + out, doesn't have spdif as the only drawback. I use one and the XMAX preamps on these devices give excellent value for the price. I've tried a few other devices from other producers but I never got the full, rich and fat sound presonus preamps give. Presonus is also known to prefer class compliant firewire-usb devices which automatically makes them linux friendly.

---

### Post by xwindowsfan on 2011-05-14
I would like to suggest the Yahmaha Audiogram 6. it has two main inputs which can be mic or 1/4" as well as two line inputs.

its small and inexpensive. in my case running ubuntu studio 10.10 it was plug and play no drivers necessary. it will show as a device under jack as USBCodec. it does connect via USB but also has two line outs.

it has level, compression and gain knobs for the main inputs. as well as a +48v mic phantom power button for ch1.

one tip I got I like to pass on was run your guitar cable through a direct box and then the mic output to the mic input of the recording device. i use a guitar with active pickups successfully with this unit and setup 

the Audiogram is solid and well be built and snarls and growls when you want it to.

---

### Post by Icebear on 2011-05-15
Thank you for your help.

A local shop in our town has the presonus audiobox so I will recommend that to my friend.:popcorn:

---

