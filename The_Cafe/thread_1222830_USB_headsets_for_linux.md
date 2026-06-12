---
title: "USB headsets for linux?"
date: 2009-07-25
forum: The Cafe
---

### Post by Eviltechie on 2009-07-25
I want to go buy the Logitech G35 headset, but I can find hardly any evidence that it works in Linux. One of the logitech blog people commented that there were no plans for linux drivers, and that results were mixed. I managed to find a few forum posts about it here, and they confirmed that they only partly worked. I tried my google foo on usb, headsets, and linux, but I can't come up with anything worthwhile except stuff not working.

Anyone here have good/bad luck with usb headsets in linux?

---

### Post by SunnyRabbiera on 2009-07-25
Well this is why we have receipts

---

### Post by Eviltechie on 2009-07-25
Return it? I do all my gaming in windows. But I would really like to be able to use this for internet radio.

---

### Post by SunnyRabbiera on 2009-07-25
> **Eviltechie said:**
> Return it? I do all my gaming in windows. But I would really like to be able to use this for internet radio.

Well there is not a lot one can do, Linux is last priority for these developers so we have to live with the limitations we encounter.
This is no fault of Ubuntu/ Linux, blame logitech.
Still you can just return the device if it doesnt work.

---

### Post by prshah on 2009-07-25
> **Eviltechie said:**
> 
Anyone here have good/bad luck with usb headsets in linux?

I don't know about headsets, but I did (briefly) have a set of Logitech's USB speakers.

The thing with USB speakers (and probably headsets) is that they are shown as a whole new sound device (Eg., as though you have two sound cards).

This creates no end of confusion, since you need to set all audio devices to this new speaker (in System-Preferences-Sound) everytime you plug it in.

In simple terms it was a pain.

However, I didn't have much time to experiment with it, so I probably could have had it working smoothly with Pulse if I had put in the time.

One point: The USB audio speakers were recognized instantly, and I never had to do any modprobe or driver fiddling. It "just worked".

---

### Post by dlmarti on 2009-07-25
I suggest the turtle beach USB products, I have tested most of them, and they all work flawlessly with Linux.

Turtle Beach is an excellent company, in my opinion.

---

### Post by ssam on 2009-07-25
in general USB sound devices work fine on linux. they will show up as a sound card. all the magical new pulseaudio system should take care of routing audio to the new device.

---

### Post by Eviltechie on 2009-07-25
I went out and bought it. It plugs in fine, the buttons and knobs work, but the microphone and speakers in it don't do anything.

---

### Post by kostkon on 2009-07-25
Try installing the PulseAudio Device Chooser utility. More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by Eviltechie on 2009-07-25
> **kostkon said:**
> Try installing the PulseAudio Device Chooser utility. More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

Hey, it worked!

---

### Post by khelben1979 on 2009-07-28
My Sennheiser have always worked excellent with Linux! And thanks to the inbuilt sound chip the microphone always works without problems as well. It wasn't cheap..

---

### Post by Gizim on 2010-05-12
Had this headset for awhile but would like to switch to Ubuntu 10.04 i got it to play sound with no issues but the "Dolby" part of it does not work. I know in Windows you have to have the app running any luck getting that to work in Ubuntu?

---

