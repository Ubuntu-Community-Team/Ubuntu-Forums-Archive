---
title: "gtk-recordMyDesktop, no sound, (occasional 768 error)"
date: 2010-03-12
forum: Ubuntu Studio
---

### Post by robinPain on 2010-03-12
1. Click  the "Advanced" button
2. Select the "Sound" tab
3. In the "Device" box, re-type "DEFAULT" as "default"
4. Now the sound works!

(I am using a USB Logitech mike/head-set on a 64bit version of 9.10)

---

### Post by AutoStatic on 2010-03-15
Or, alternatively:
3a. Open a terminal and enter **aplay -l**
3b. In the "Device" box, enter the name of your device that is outputted by aplay (the part after 'card x: '), preceded by 'hw:'. In my case the name of the card is 'Intel', so in the device box I enter 'hw:Intel'.

---

### Post by hanzj on 2010-05-13
> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0I tried the following:

**CK804**
and
[B]Intel 
[/B]and[B]
hw:CK804
[/B]and[B]
hw:Intel
[/B] as the text in the Device blank, but on all occasions, I got this errror message:
> 
recordMyDesktop has exited wiht status: 768
Description:Could not open/configure sound card.

---

### Post by hanzj on 2010-05-13
by the way, i'm trying to record a video that's playing on my screen. I do not have any audio coming from my microphone. Can recordMyDesktop capture the audio that I hear from my speakers?

---

### Post by Gimmie5Bukks on 2010-05-14
> **hanzj said:**
> by the way, i'm trying to record a video that's playing on my screen. I do not have any audio coming from my microphone. Can recordMyDesktop caputer the audio that I hear from my speakers?

click on the sound daemon on your panel and select **Sound Preferences**

On the **Hardware** tab under **Profile** select your sound card name (in this case CK804)

If that doesn't work select or the option is not present,choose **Analog Surround Output** (or something like that)which will use the audio chip of your motherboard - this will record the all audio coming from your screen 

If you want the audio to be recorded from your microphone or headset,choose the profile that says something like:**Analog Surround Output + Analog Stereo Input** ,then on the **Input** tab make sure the device is selected and select the connector (**microphone 1**).

In both cases on the RecordMyDesktop sound tab type &#733;default&#733; in device box

---

### Post by hanzj on 2010-05-14
> **Gimmie5Bukks said:**
> click on the sound daemon on your panel and select **Sound Preferences**

On the **Hardware** tab under **Profile** select your sound card name (in this case CK804)

...
...
...

My sound card name is not there but " IEC598" is. Please see screenshots.

I'll try Analog Stereo Output (originally Analog Stereo Duplex).


I'll change RMD/Sound/Device from "DEFAULT" to "default" as you suggested.

---

### Post by hanzj on 2010-05-14
gimmie5bukks,
thanks. your info helped solve my problem!!!

---

### Post by hanzj on 2010-05-14
I discovered that Gizmo5 / Gizmo Project doesn't have output sound when I have the Sound Preferences / Hardware Tab / Profile set to Analog Stereo Output.

I had to revert the Profile back to Analag Stereo Duplex.


Hmmmm... Is there a configuration that will work for all my programs (Gizmo5, recordmydesktop, VLC, firefox flash, etc)?

---

### Post by srw2d on 2010-06-13
> **robinPain said:**
> 1. Click  the "Advanced" button
2. Select the "Sound" tab
3. In the "Device" box, re-type "DEFAULT" as "default"
4. Now the sound works!

(I am using a USB Logitech mike/head-set on a 64bit version of 9.10)

This worked for me!  10.04 Ubuntu with a Plantronics 955 headset.

Thanks

---

### Post by volobiz on 2010-06-16
Fantastic -- this worked for me on an older Ubuntu 8.04 LTS that I have by making this simple change.

---

### Post by petrasflorin on 2010-10-22
I can't open Advanced window, just doesn't open when I click on it.
My question is how do I modify my settings ?
I searched for the config file, found it, but don't know what to write under "Sound device"
currently it was "DEFAULT" which should work (skype is set the same, with default, and it works).

anyway here is the output of my aplay -l


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


What should I put under "Device" in the gtk-recordmydesktop settings? I tried "Intel" , "hw:Intel" and "ALC882 Digital" - none worked. Ideas ?

---

### Post by deoanam2002 on 2011-08-08
This worked for me. Thanks so much.

> **AutoStatic said:**
> Or, alternatively:
3a. Open a terminal and enter **aplay -l**
3b. In the "Device" box, enter the name of your device that is outputted by aplay (the part after 'card x: '), preceded by 'hw:'. In my case the name of the card is 'Intel', so in the device box I enter 'hw:Intel'.

---

### Post by MikeCyber on 2013-02-20
Needed to change from duplex to analog stereo output in system - hardware settings. Maybe helpful for somebody.

---

### Post by overdrank on 2013-02-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

