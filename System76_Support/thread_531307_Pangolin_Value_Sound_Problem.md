---
title: "Pangolin Value Sound Problem"
date: 2007-08-21
forum: System76 Support
---

### Post by NaturalScience on 2007-08-21
Hi,

I've been reading some posts about this problem occurring on other System76 machines.  I have a Pangolin Value.  My problem is that under sound control, I have three controls:  Headphone, PCM, and Front.  Headphone appears to have no effect on any volume, and sounds comes out of both the main speakers and the headphone jack.  If I mute the "Front", I get no sound at all.  I've checked the S76 driver folder and saw that this morning a new alsa tarball was pushed out, and I tried adding an option line to /etc/modprobe.d/alsa-base using "model=targa-dig", but to no avail.  The text file ALSA-configuration.txt gives some options but I'm not sure if any of them are valid.  Any advice or is a fix forthcoming and perhaps I just should just sit tight?

Much appreciated,
NS

---

### Post by thomasaaron on 2007-08-21
Hi.

1. Did you re-image your machine?
2. Please tell me the model number of your machine. (If you don't know, go to the System 76 driver. It will tell you.)
3. You should not have to re-compile alsa or add anything yourself to the alsa-base file. All you should have to do is run the restore function on the System 76 driver. This sets things correctly.

To get all available options on your sound control:
1. Double click the speaker icon.
2. In the resulting window, File > Change Devices > Alsa
3, Edit > Preferences. Check ALL available boxes.

To mute the headphones, there is a checkbox, I believe, under the switches tab,

If your Pangolin is an S96F, there is a jack sense problem with the headphones that has not yet been resolved. There is a bug opened for it already.

---

### Post by octathlon on 2007-08-21
Natural science,

I don't know if you have the old or new Pangolin Value.  I recently got the new one (model panv3 :)), and I found that there is a Mute button at the top of the keyboard (right-most button).  This button toggles the speakers on and off, but lets the headphones continue to work.

I still don't know what some of the buttons are supposed to do.  Unfortunately the user manual only names the buttons but doesn't enlighten us as to their functions.

BTW, on this panv3, the speakers do not automatically mute when the headphones are plugged in.  I don't know if that is the correct behavior or not, but since the mute button is right there, it's OK for me.

---

### Post by NaturalScience on 2007-08-21
Thanks for the responses, my Pangolin is a S96F (panv2).  I did do a re-install in order to run 64-bit Feisty.  Ah well, I'll wait for the bug to be resolved.  Thanks again for the help.

---

### Post by crichell on 2007-08-21
> **octathlon said:**
> Natural science,

I still don't know what some of the buttons are supposed to do.  Unfortunately the user manual only names the buttons but doesn't enlighten us as to their functions.

BTW, on this panv3, the speakers do not automatically mute when the headphones are plugged in.  I don't know if that is the correct behavior or not, but since the mute button is right there, it's OK for me.

Hi octathlon,

The buttons on the top should open Email (Evolution), Web Browser (Firefox), Movie Player (WoW Video button), and Rhythmbox (WoW audio button).

Let me know if the keys aren't opening the applications as they should.  I'll help you set them.

---

### Post by crichell on 2007-08-21
> **NaturalScience said:**
> Hi,

My problem is that under sound control, I have three controls:  Headphone, PCM, and Front.  Headphone appears to have no effect on any volume, and sounds comes out of both the main speakers and the headphone jack.  If I mute the "Front", I get no sound at all.  I've checked the S76 driver folder and saw that this morning a new alsa tarball was pushed out, and I tried adding an option line to /etc/modprobe.d/alsa-base using "model=targa-dig", but to no avail.  The text file ALSA-configuration.txt gives some options but I'm not sure if any of them are valid.  Any advice or is a fix forthcoming and perhaps I just should just sit tight?

Much appreciated,
NS

Hi Natural Science,

The bug report Tom mentioned is located here:
[https://bugs.launchpad.net/system76/+bug/113610](https://bugs.launchpad.net/system76/+bug/113610)

We'll be tackling this soon.  It appears that the sound chip revision changed on us.  The bug surfaced a couple of months ago; however, it did not effect Pangolins prior to that.

---

### Post by octathlon on 2007-08-22
> **crichell said:**
> Hi octathlon,

The buttons on the top should open Email (Evolution), Web Browser (Firefox), Movie Player (WoW Video button), and Rhythmbox (WoW audio button).

Let me know if the keys aren't opening the applications as they should.  I'll help you set them.

Yes, they are working perfectly.  :-D What about the 2 buttons on the left though: "Q-Charging" and "Power USB"?  I figure they are related to those 2 USB ports having more power available for devices that may need it, but when and for what would I use each of those buttons? 

thanks,

---

### Post by crichell on 2007-08-22
Those are actually very cool buttons.  I have to get some documentation somewhere :-).

The button with the USB signal turns power on to the USB port while the system is turned off.  For instance, is you need to charge your phone or IPOD but don't need your computer on you simply press the button and plug in your USB device.

The button that looks like a power cord is designed to charge your laptops battery faster when it's turned off.  (This button seems a little silly to me.)  Now that I think about I may need to clarify - why would one need a button for that?

---

### Post by octathlon on 2007-08-22
Very interesting!  I wouldn't have thought of that, the USB thing is a great idea.

---

### Post by NaturalScience on 2007-09-21
Sorry to bump this, but is there any further developments on this issue?  The bug report has been silent for a week and a half.  I understand this may be a low priority issue.

---

### Post by thomasaaron on 2007-09-21
Hi, Natural Science.

I actually updated the bug report, but it doesn't look like anyone has tried my suggestions yet.

Also, I just noticed your running 64-bit ubuntu. That's not something we are going to be able to test on. I have no idea if it has *any* effect on ALSA, but, if it does, we're gonna be spinning our wheels here.

---EDIT---
Now that I've thought about it for a minute, ALSA does compile against the kernel. If you have a totally different kernel than what we are working with...
I'll try to do some research on it, though.

---

### Post by NaturalScience on 2007-11-08
Just wanted to bump this to see if there's any further developments.  On 64-bit Gutsy I still have a jack sense problem on a Panv2.  I'm running kernel 2.6.22-14-generic and the latest sys76 driver (2.1.1).  Look like the ALSA in the sys76 src folder is 1.0.14rc3.

Edit:  My last option on /etc/modprobe.d/alsa-base is

options snd-hda-intel model=auto

---

### Post by thomasaaron on 2007-11-08
Hi, Naturalscience.

We don't support 64-bit ubuntu and do not have the bandwidth right now to do 64 bit testing on the panv2. The bug report mentioned earlier in this post is for jack sense problems specific to 32-bit ubuntu.

The questions that immediately come to mind are:

1. Did jack sensing work under 32-bit Ubuntu?

2. Have you tried to compile the latest ALSA and see if that helps?

3. I only know of two PanV2's that had jack sensing problems under 32-bit. So, I would be surprised if it were not a settings issue. It might be helpful if you were to post screenshots of all tabs on your sound control window so that we can have a look at how you're set up.

---

