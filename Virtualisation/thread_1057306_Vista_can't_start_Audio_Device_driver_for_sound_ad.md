---
title: "Vista can't start Audio Device driver for sound adapter"
date: 2009-02-01
forum: Virtualisation
---

### Post by dansan on 2009-02-01
I am currently using VB 1.2.1, but this problem started several versions ago.

Installing Vista in VB has always gone smoothly for me on the surface, but none of the installations has ever been able to set up a USB sound adapter (Andrea or Parrott half-duplex sound pod). I have done all file modifications in Ubuntu to enable USB in VB, and Vista responds when I plug in the sound pod. The Device Manager initially shows the pod as an Audio Device but ends up showing a yellow triangle with a question mark. Details say that the device could not be started. I have Googled this problem numerous times, and have tried this and that "cure" -- e.g., updating AC'97 drivers, replacing Vista's usbaudio.sys with the one from Win XP, yada-yada-yada. Along the way I posted a query [here]("http://ubuntuforums.org/showthread.php?t=1029403"),but no answer. I am now trying a hopefully simpler description.

All of my initial tries were with Pulse Audio set in Hardy and VB, but today I remove all of Pulse Audio and set up Sound Preferences for ALSA.
Still no joy.

Has anyone had this problem? Solved it?

---

### Post by ajmorris on 2009-02-02
hi there,
have you told VirtualBox which host sound driver and controller to use? The guest should be able to directly access your host sound driver to play sound...
Also, are you using the PEUL or OSE version of VirtualBox?


AJ

---

### Post by dansan on 2009-02-03
Hi AJ,

Thanks for replying.

> **ajmorris said:**
> ...have you told VirtualBox which host sound driver and controller to use?

Yes to both. Before I removed Pulse Audio, the settings were Pulse Audio and ICH AC97. After removal, I set Sound Preferences for ALSA in Ubuntu and changed Pulse Audio to ALSA in VB. These settings work perfectly for XP.

> **ajmorris said:**
> 
...
Also, are you using the PEUL or OSE version of VirtualBox?



I'm using the PUEL version and set up Ubuntu for USB use in VB. I added the sound adapter in VB's settings, and the device is listed as available. Vista registers the device and launches into setting up a driver. As I understand it, USBAUDIO.SYS should supply the necessary driver, but for some reason it can't. The manufacturer, Andrea, says it doesn't encounter this problem, so no help from them. Here is a list of what I've tried so far, without success:

1. Replacing Vista's USBAUDIO.SYS with the USBAUDIO.SYS file in XP.
2. Applying a Vista Hotfix for USB device issues
3. Updating to Vista SP1. 

Without a sound adapter for mics, WSR (speech recognition) in Vista is crippled, and I am dead in the water since my work requires speaking text all day. 

People have told me to reformat my Ubuntu laptop and reinstall Vista, but I won't consider that. I run Hardy on my desktop at my office and have no problem. Vista running in VB sets up the same sound adapter without a hitch.

I am not very Linux-savvy. Please ask me for other details that could help solve this riddle.

---

### Post by dansan on 2009-03-29
I forgot to record the solution I found to this problem, so here goes:

The Andrea sound pod turned out not to be usable with Vista on **my** machine. Notice the emphasis. I know the Andrea works on many other laptops, but it never did on mine. My short way of explaining this is that the pod could not "speak" Vista well enough to get all the way through installation. I don't know the technical explanation, but it perhaps has to do with Vista and Win7's handling of DRMs.

The solution that worked was to buy a newer sound pod, in my case the Buddy 6G. It worked beautifully at first plug-in, and I am enjoying Windows Speech Recognition in both Vista and Windows 7 beta running in VirtualBox running in Hardy.

---

