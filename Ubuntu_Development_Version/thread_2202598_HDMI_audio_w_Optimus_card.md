---
title: "HDMI audio w/ Optimus card"
date: 2014-01-30
forum: Ubuntu Development Version
---

### Post by Amorget on 2014-01-30
Hi,
I installed Truty on my new laptop as it was said it had better Optimus support.  It does.  Immensily.  With 13.10 when I plugged in the HDMI it would cause X to crash when booting.  Now with 14.04 I was able to do a basically vanilla install and it everything has worked without issue (including hooking the HDMI to a TV/AVR), except the HDMI audio.

In "Sound" HDMI is not listed as an option.  However, aplay -l does:

```
amorget@AmorgetLP:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: VT1802 Digital [VT1802 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Anyone have any ideas as to why it wouldn't be displaying the HDMI as an option in Sound, yet it shows in aplay?

Video cards are a Nvidia 765M and an Intel 4600 (on a i7-4700MQ).  Laptop is a Sager NP7355 to be exact.

Thanks,
Douglas

---

### Post by squakie on 2014-01-30
ooopppsss - accidentally posted before finishing - text removed.

---

### Post by squakie on 2014-01-30
I don't have those videos options, but I do know that with AMD it requires putting "radeon.audio=1" in the boot line.  Perhaps there is a similar option on the nVidia?  I found one thread that said you need to be using a driver version of at least 325.xxx with that video - I don't know what you have or if that would help your audio or not.

---

### Post by squakie on 2014-01-30
I found these threads - the first looks promising:

[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

[URL="https://devtalk.nvidia.com/default/topic/609790/no-hdmi-sound-w-optimus-in-linux/"]https://devtalk.nvidia.com/default/topic/609790/no-hdmi-sound-w-optimus-in-linux/

[/URL]

---

### Post by P-I H on 2014-01-30
The attached files show what you get with System Settings/Sound and PulseAudio Volume Control.
Try to select device with PulseAudio Volume Control.

---

### Post by Amorget on 2014-01-30
P-I H - The HDMI isn't listed there.  I only have the Speakers and the S/PDIF.

---

### Post by Amorget on 2014-01-30
> **squakie said:**
> I found these threads - the first looks promising:

[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

[URL="https://devtalk.nvidia.com/default/topic/609790/no-hdmi-sound-w-optimus-in-linux/"]https://devtalk.nvidia.com/default/topic/609790/no-hdmi-sound-w-optimus-in-linux/

[/URL]

Thanks for the links.  The first is what I originally attempted to get HDMI working but in the end did not work, which caused me to try 14.04.  That link also said that sound was not working over HDMI.  The second link I had not found and is an interested read. Doesn't look promising, though...

---

### Post by squakie on 2014-01-30
I'll keep looking and see if anything turns up - if so, and if this thread is still open, I'll post back.

Sorry I couldn't be of more help.

---

### Post by Amorget on 2014-01-30
I appreciate the help!  It's not the end of the world if it doesn't work.  Was hoping this was kind of the same deal as getting the S/PDIF working where it just had to be unmuted.

---

### Post by cariboo on 2014-01-30
Just out of curiosity, does the HDMI audio output show up in alsamixer, when you choose the correct sound card?

---

### Post by Amorget on 2014-01-30
If I am looking at it correctly, yes.  

Alsa Mixer:
[ATTACH=CONFIG]249956[/ATTACH]

Sound Control:
[ATTACH=CONFIG]249957[/ATTACH]

There are 2 sound cards listed in alsamixer  (0) HDA Intel HDMI and (1) HDA Intel PCH  It looks like default is set to the HDMI one.

---

### Post by squakie on 2014-01-30
It is just showing the card is an hdmi card - your outputs are still set on the screen to  s/pdif, and the first is enabled.

---

### Post by Amorget on 2014-01-31
Well, that was weird.  All the sudden the HDMI audio showed up!  And it sort of works.  My receiver doesn't like it, but my TV directly is at least making noise... they sound like chipmunks!

Just confirmed that it sounds the same in YouTube, History.com, and a AVI file in Totem.

To note, the receiver acted funny in Windows, though I did get it working.  I think the age of my TV + a new receiver + a new laptop isn't too happy.  Didn't have any issues with the Xbox 360, a Sony Viao running *blech* Vista, or my 3 year old MSI 16F2 running 13.04 w/ a Nvidia 470M.

---

### Post by Dave_Tobin on 2014-03-04
Hi, has there been any more success with this? Does the sound work?

---

### Post by Amorget on 2014-03-04
> **Dave_Tobin said:**
> Hi, has there been any more success with this? Does the sound work?

I haven't messed with it at all since my initial sort of getting it to work.  It was mostly a play with the new laptop thing over something I actually use.

---

### Post by Dave_Tobin on 2014-03-04
> **Amorget said:**
> I haven't messed with it at all since my initial sort of getting it to work.  It was mostly a play with the new laptop thing over something I actually use.

OK, I might take a look at it when I get a chance. Looks like good progress.

---

