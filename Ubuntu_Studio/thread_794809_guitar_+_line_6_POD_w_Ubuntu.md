---
title: "guitar + line 6 POD w/ Ubuntu"
date: 2008-05-15
forum: Ubuntu Studio
---

### Post by RottenBananas on 2008-05-15
Hey everyone,
   So I play guitar :guitar: and have a line6 pod and wanna use ubuntu to record. I looked around and saw that audacity would work alright.

I only have a laptop, with an intel soundcard that I can use...

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

Questions I Have:
Do I need to buy another sound card? 

Can I have that card sit outside the laptop externally? 

How can I hook up the guitar to the computer?(I have 3 jack slots, 2      
for headphones and 1 for the mic)

How can all this work with the pod?

Is Audacity the way to go?

Thanks 
-Bananas

---

### Post by warbread on 2008-05-15
If you don't care about quality, you should be to plug into your laptop from the direct out on the Pod to the mic in on your computer.  Just tell Audacity to record from your line-in and it should work.  Note that with this method, you won't be able to hear what you're recording as you're playing it UNLESS you use a 1/4" -> 1/8" jack adapter.  This is your cheapest option.  

If you want good quality recordings and low-latency real time monitoring, you'll need to spend money on a new sound card and then get Jack to work.  I'm not going to bother explaining any of that unless that's the path you want to take, though.

---

### Post by RottenBananas on 2008-05-15
Hey thanks for the reply,
   Quality is somewhat important...it cant sound terrible. So if i buy i card, since i have a laptop can i have it sit outside when i want to record? How much $$ are we talkin?

---

### Post by warbread on 2008-05-16
Well, first thing is first.  Here's what I suggest starting out with:

- Get a 1/4" male to 1/8" female adapter.  Plug this into the "Amp out" jack on your POD.
- Get a 1/4" patch cable and plug it into the female end of the adapter.  Plug the other end into your laptop.
- Get your headphones (I assume you have some) and plug those into the headphone jack of your POD (**not** your computer).
- Go into Audacity and record something.

That should cost you next to nothing.  In fact, you may know people who have an adapter and cable already, so it would cost you nothing.  Recording like this will give you an idea of where you want to go next.  Don't expect anywhere near professional quality, but it will sound a helluva lot better than a tape deck.  Plugging your headphones into your POD will let you hear what your playing, which is important because without additional hardware/software configurations, you can't do monitoring on your computer.  

If  you want to go the USB soundcard route, it's not looking cheap.  A cursory glance at Musiciansfriend.com and a quick check on google for Linux compatibility shows us starting at [$99.]("http://www.musiciansfriend.com/product/Lexicon-Alpha-USB-Audio-Interface?sku=245507")
I suggest you don't go for a Line 6 usb interface as they're reported to not work.   Also with this, you will need to install and configure Jack and the real time kernel.  I don't want to make it seem like it's difficult, but it is intimidating to newcomers as there are lots of options and for many, lots of new concepts to learn.  I've learned in a matter of months without a guide, so with me and the other knowledgeable people here, you'd be fine.

Check out your current options before moving on, though.  It could save you a lot of headaches later on.

---

### Post by RottenBananas on 2008-05-16
god i LOVE these forums, You guys are so helpful.

Thanks a ton for your input warbread. Ill go get those cables and give it a shot to see how it turns out. 

Thanks again!
-Bananas

---

### Post by RottenBananas on 2008-05-17
So I went over to radio shack and picked up the 1/4 to 1/8 adapter. The guy said the patch cable can only go into the male end of the adapter? Dunno...anyway I came back home and gave it a shot..

-I plugged my guitar into the input of my pod
-I plugged a guitar cable into the output of the pod (this would normally go into the amp) and the other end of that cable i plugged into the adapter i just bought.
-Then i plugged the 1/8" part into the mic jack of my laptop
-And stuck headphones into the pod

Opened up audacity and hit record but nothing plays back...i just get a straight line goin across so its not pickin anything up.

I tried changing the devices in audio preferences and made sure my input source was the mic but nothing happened

In audacity the Audio I/O tab has recording set to the oss...if i try the alsa one it gives me an error saying it cant open the device

What should i try next? Am i doing something wrong?

---

### Post by RottenBananas on 2008-05-19
Also the pod does have a usb interface. Can it work through usb? I tried pluggin it in to give it a shot in audacity but a usb device never shows up in Audio I/O

---

### Post by thorgal on 2008-05-19
if the ALSA option ended up with a complain that your h/w is busy, it means that something is having a grip on your h/w. Could be the windows manager audio daemon (GNOME used to use esd, KDE used artsd and the newer ubuntu version uses pulseaudio). Whatever it is, you can check by examining the processes running in the background. From a terminal, run this : ps xa
look in the list if esd or artsd or pulseaudio is running.

You can disable the guilty daemon by either killing it (kill -9 process-id-of-the-daemon) or if it's artsd or esd, turn it off through the control center of your desktop. If it is pulseaudio, you can type : pulseaudio -k

Then try audacity again. Make sure that all levels are turned up in alsamixer (run it in a terminal as well, it's a curses-based app).

---

### Post by warbread on 2008-05-20
> **RottenBananas said:**
> So I went over to radio shack and picked up the 1/4 to 1/8 adapter. The guy said the patch cable can only go into the male end of the adapter? Dunno...anyway I came back home and gave it a shot..

-I plugged my guitar into the input of my pod
-I plugged a guitar cable into the output of the pod (this would normally go into the amp) and the other end of that cable i plugged into the adapter i just bought.
-Then i plugged the 1/8" part into the mic jack of my laptop
-And stuck headphones into the pod

Opened up audacity and hit record but nothing plays back...i just get a straight line goin across so its not pickin anything up.

I tried changing the devices in audio preferences and made sure my input source was the mic but nothing happened

In audacity the Audio I/O tab has recording set to the oss...if i try the alsa one it gives me an error saying it cant open the device

What should i try next? Am i doing something wrong?

I'm pretty sure you did good.  Have you tried all of the input options available?

---

