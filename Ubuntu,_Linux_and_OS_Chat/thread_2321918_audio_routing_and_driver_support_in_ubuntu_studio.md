---
title: "audio routing and driver support in ubuntu studio"
date: 2016-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by patrick119 on 2016-04-25
hello im getting more and more frustrated with windows and not being able to route audio devices the way i want to like you could with older versions, as a result, im thinking about setting up ubuntu  studio .the questions i need to answer  is  will i run into hardware compatibility issues  with my usb audio devices , behringer  guitar link , and xenyx 1204 usb  mixing board, ill later be switching to a tascam  6 channel audio interface  , is the sound quality  any good id like to be able to eventually record at  24bit 44.1 ,as its the standard right now  and can i route my input devices  and output devices the way i want to into different programs and run things like a signal chain i can switch around as needed , thank you  in advance

---

### Post by jejeman on 2016-04-25
Ubuntu Studio is also a Live distro.
Boot up Live DVD/USB, and test everything you need, before install.
I guess Behringer devices will work, they are probably class compliant.

Generally, sound is good on Linux.
Complex routing is also possible, depends on what you need exactly.

---

### Post by patrick119 on 2016-04-26
ill do that later in the week and let you all in detail ,regardless if anyone has any suggestions ill be glad to hear them

---

### Post by Bucky Ball on 2016-04-26
Best just try it. Most USB devices work. Recording in 24bit is not an issue. What you will need to do is take time out to get across the Ubntu audio hardware as, apart from Audacity and VLC if you are going to need to use it, none of it is available in Windows so will be unfamiliar. 

You will also need to familiarise yourself with Jack, if you are going to get that complex, which will allow whatever routing you want (within reason). The default audio sound system, Pulseaudio, has a mixer, Pulseaudio Volume Control, which is very flexible re. routing also and may be all you need.

PS: Be aware that some things may work on a full install that don't work on a 'live' session (Try Ubuntu) and vice versa. Just one of those things and luck of the draw. As mentioned, most USB stuff should work either way. Plug it in when running a live session then open a terminal immediately and put this in:

```
dmesg
```

... then hit return. At the bottom of that output you should get info about the device you just plugged in and, hopefully, info that it has been recognised and configured with driver, if required.

---

### Post by nik.charles on 2016-04-26
hi patrick
I used to love winXP for audio work. The changes that came with win7 started me thinking about moving to Linux. The decider was hearing one of my mates using Ubuntu Studio broadcasting on a 128k radio stream - still can't understand why Linux would sound lots better than windows on such a low bitrate, but I wanted it

As a musician, you will have to deal with a lot of learning to get used to the JACK audio system. But once you get it worked out, the signal routing options are excellent, and so many free tools and effects to play with.

It isn't easy, and may cause as much frustration as using windows in the beginning, but IMHO is well worth the journey

---

