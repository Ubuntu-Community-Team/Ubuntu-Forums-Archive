---
title: "[SOLVED] NO RECORDING - serp2"
date: 2007-12-09
forum: System76 Support
---

### Post by asmiller-ke6seh on 2007-12-09
After pursuing all kinds of information, here is a record of what my current setup is for ALSA - nothing I have been able to try makes it possible for me to use either the built in microphone, or a microphone pugged into the front-side of my Serval Performance. I did a fresh install of Gutsy from the Live CD, and then applied the System76 Driver. I am hoping that there is a System76 driver solution on the way:

:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ alsamixer -Vall
[IMG]http://us.a2.yahoofs.com/groups/g_hr_10534336/3e80/__hr_/5da8.jpg?grgtPXHBVIifn.Lz[/IMG]

~$ grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: Realtek ALC883
/proc/asound/card0/codec#1:Codec: Generic 11c1 Si3054

Please let me know if you know of a way that I can fix this - or if a fix is on its way.

---

### Post by thomasaaron on 2007-12-10
If you installed Gutsy, it should have installed ALSA 1.0.15rc3 onto the SerP2.

Did you change the ALSA version? If not, please post the output of: uname -r

I just tested recording via the internal mic on the serp2 with 1.0.15rc3 and it worked. I think the thing for you to do is get back to that alsa version and post the details of your sound control settings.

---

### Post by asmiller-ke6seh on 2007-12-10
uname -r
2.6.22-14-generic

I did not change the alsa version. This was a clean install of Gutsy from a verified downloaded version of Ubuntu that I did at the end of November.

It was my understanding that there was a more recent version of ALSA available. Maybe i should follow the instructions on the ALSA site to install this new version.

Does the System76 driver touch ALSA at all - maybe i screwed up and maybe I ran the wrong version of the System76 Driver after the Gutsy install?

I am currenlty running the System76 driver: version 2.1.1

Maybe I should try running a RESTORE with this version?

---

### Post by thomasaaron on 2007-12-10
The System 76 driver doesn't mess with ALSA on the SerP2.

You said you did a fresh install of Gutsy? If you did an upgrade, it might have left ALSA however it found it on Feisty(?), but I'm not sure.

If you want to post the details of your sound control settings, maybe we can make it work. I would think it'd work fine with the version of ALSA you have becuase we've never messed with ALSA on the SerP2.

________________________

I just looked in the database and it says you have a SerP1. What model does it report in the System76 driver? Either way, though, it's the same story with ALSA.

---

### Post by asmiller-ke6seh on 2007-12-10
The version of ALSA listed in the official Ubuntu repositories is 1.0.14 (see below).

[IMG]http://us.a2.yahoofs.com/groups/g_hr_10534336/3e80/__hr_/3100.jpg?grgbbXHBKc5GCOK1[/IMG]

It was a fresh install of Gutsy - I backed up the key application subdirectories of my HOME directory (such as .evolution), did a brand new install off a new Gutsy LIVE CD, ran the System76 driver refresh, and then copied back the home directory applicaitons data.

Also, please check my first posting - there is an image of all the ALSA settings I am using - I captured it from **ALSAMIXER -Vall**.

---

### Post by thomasaaron on 2007-12-10
Right. My bad.
Gutsy does install v.14. Our server image installed v.15rc3.

I just set this SerP1 up with v.14 and recording works.

Here's what I did:

Double-click the speaker icon. In the resulting window go to edit>prefs. Then check all available checkboxes.

Under the Playback Tab:
Headphones muted
PCM all the way up
Front all the way up
Microphone muted

Under the Recording Tab:
Capture all the way up
Capture1 all the way down

Under the Switches Tab:
Nothing selected

Under the Options Tab:
Both Input Source pulldowns set to "Mic"
(That's the only available option)

Open Sound Recorder (Apps > Sound and Vid > Sound Recorder)
Press the Record Button
Speak
Press the Stop Button
Press the Play Button

---

### Post by asmiller-ke6seh on 2007-12-10
Sounds promising.

I will try this as soon as I get home, this evening. I will post results as soon as I can confirm (either way).

As always, thank you for being johnny-on-the-spot with your replies.

---

### Post by asmiller-ke6seh on 2007-12-10
Well, I had mixed results. Yes, it recorded sound from the built-in microphone on my serp2, but at a very low volume, and I was unable to record from any microphone plugged into the side jack (yes, I used the correct one - the one towards the rear of the laptop, just behind the headphone jack).

Here's the output from **ALSAMIXER -Vall**:
[IMG]http://home.comcast.net/~ke6seh/ALSAMIXER.jpg[/IMG]

Here is the setup of gnome-sound-preferences:
[IMG]http://home.comcast.net/~ke6seh/gnome_sound_preferences.jpg[/IMG]

When I click on <test> next to **Sound capture:** I get this error:
[IMG]http://home.comcast.net/~ke6seh/Screenshot-gnome-sound-properties-FAILURE_MESSAGE.jpg[/IMG]

Do you want me to email my logs.tar file, captured out of the System76 driver tool?

If I set the **Sound capture** to something other than OSS, the recording flat out fails, or is so highly distorted and chopped up it is totally unintelligible.

---

### Post by thomasaaron on 2007-12-11
I just tested an external mic.

I did not have to change any settings at all. Just plugged in the mic, and it worked quite well.

---

### Post by asmiller-ke6seh on 2007-12-11
What mind of microphone were you using? Any idea what the impedance is (high impedance? low impedance?)? Maybe that's my problem.

What driver version are you using? 1.0.14 or 1.0.15?

Is my gnome-sound-preferences the same as yours?

And what does that error message mean?

I guess I have to start all over, again ... backup **/home**, reinstall Gutsy, rerun the System 76 driver, and then test the microphone before doing anything else (like restore **/home**, or install any other applications).

Then, if it doesn't work, I guess I will have to install ALSA 1.0.15 and see if that makes things work correctly.

Could it be that my Serval Performance is broken? Or maybe it's a different hardware version than the SERP2 you used for your testing?

---

### Post by thomasaaron on 2007-12-11
It's a Labtec mic. I don't know what the impedence is,but it is a standard computer microphone.

I'm using v.14 of the alsa driver.

My Sound Prefs are different than yours. Mine are:
autodetect
autodetect
autodetect
ALSA - Advanced....
HDA Intel (Alsa mixer)

I don't think you need to do a re-install. And I doubt your machine is broken.
It sounds to me like a configuration problem.

For now, use the sound control that you get by double-clicking on the speaker icon instead of the alsamixer panel. Just to make sure you're not missing anything.

---

### Post by asmiller-ke6seh on 2007-12-11
I'll pursue all of this when I get home, tonight.

BTW, are you using a traditional microphone (with a mini-phone plug) or one with a USB plug?

I am still hoping that it is just a configuration problem.

Once I get everything working, I am willing to write a HOWTO for the System 76 knowledge base: **HOWTO Make Sure the Sound on your SERP2 is Propertly Configured.**

My ultimate goal is to get EchoLink operating under WINE on my SERP2 ([EchoLink is Amateur Radio IPTelephony/Linking software]("http://www.echolink.org/")) which would allow me to communicate with other Radio Amateurs worldwide from my laptop to anywhere...which would be SO KOOL!! In case you haven't already figured it out, my call sign is KE6SEH.

As always,

Seth

-----------------LATER-------------------------------------LATER------------------------------------
No luck - same symptoms.

To make sure it is not the michrophone (I tried two different headphone/mics I had laying around) I will buy a new microphone and try it out. Also (or maybe instead) I will buy a USB headset and try this out: [Skype with Headset (from the System 76 Knowledge Base HOW TOs)]("http://knowledge76.com/index.php/Skype_With_headset"). I'll let you know how it goes.

BTW, is your first name Thomas, or is it Aaron?

---

### Post by asmiller-ke6seh on 2007-12-12
In the thread titled "a few frustrations from my serval performance", message #27, squish says, "Anyways, the mic slightly sucks as far as it goes for quality, is that a driver thing, or a hardware thing?" to which thomasaaron replies "It is an alsa thing. Tweaking it usually requires fine tuning the "Digital" slider. Also, the new System 76 driver might help some. It re-does alsa."

And yet, in this thread, in message #4 thomasaaron states"The System 76 driver doesn't mess with ALSA on the SerP2." I am confused.

1) Does the System76 driver tweak ALSA, and
2) Do I need to fine tune the "digital" slider to tweak the microphone input?

Would I be better off with a USB microphone, an external analog microphone, or the internal microphone?

---

### Post by thomasaaron on 2007-12-12
> 1) Does the System76 driver tweak ALSA, and

It depends on the computer. On yours, it does not tweak ALSA.
On his it does.

> 2) Do I need to fine tune the "digital" slider to tweak the microphone input?

No. You should only need to set up your sliders the way I described them earlier with ALSA 1.0.14. You said this gave you success with the internal mic. All I had to do on my SerP1 (which is what our databse says you have) is plug in the external mic to make it work.

Could you please confirm what model number you actually have by going to the System 76 driver. If you have a SerP2, then I may need to test on a different computer.

> Would I be better off with a USB microphone, an external analog microphone, or the internal microphone?
In my experience, the best quality comes with a USB mic, the next best with an external analog mic, and the worst with the internal mic.

---

### Post by asmiller-ke6seh on 2007-12-12
I titled this thread "NO RECORDING - serp2" because that is what the System 76 driver says I have. It's the Serval Performance with the 1680x1050 wide screen, brushed aluminum top, and brushed aluminum keyboard surround with the copper-colored trim. If you provide me with your email address at System 76, I will email you with the serial number - or I can email it to Erik or Carl (I have their email addresses) if you want.

After reading the other thread, I went home and turned on the DIGITAL control. Then I tweaked the DIGITAL slider. Then I played with the CAPTURE slider. I found the best results with the CAPTURE slider and the DIGITAL slider both at 50%.

:guitar:   **success!**

So, I deduce that on the **serp2** that the following should be done to allow for full use of the sound system for analog mike input and good sound output through either the front speakers (I love the laptop sound) with speaker disconnect when plugging in an analog headphone:

1) Open the Sound Preferences by selecting **SYSTEM** | **PREFERENCES** | **SOUND** from the menu.
- On the **DEVICES** tab, use the following selection:
  **Sound Events**
  - Sound playback: Autodetect
  **Music and Movies**
 - Sound playback: Autodetect
  **Audio Conferencing**
  - Sound playback: Autodetect
  - Sound capture: ALSA - Advanced Linux Sound Architecture
  **Default Mixer tracks**
  - **Device: HDA Intel (ALSA mixer)**
*device and tracks to control (from the list) use Control and the mouse click to select all of the following, only:*
  PCM
  Front
  Capture
Click **CLOSE** to continue

2A) Open the **Volume Control: HDA Intel (ALSA mixer)** dialog by double clicking on the speaker icon in the panel.
  a) Select **EDIT** | **PREFERENCES** and select these items (check boxes) only:
  -  Headphone
  -  PCM
  -  Front
  -  Microphone
  -  Capture
  -  Capture 1
  -  Digital
  -  Input Source
  -  Input Source
  b) Click **CLOSE** to close the Volume Control Preferences dialog to continue

2B) On the **PLAYBACK** tab, set the controls as follows:
  a) **Headphone** full down - muted
  b) **PCM** full up - unmuted
  c) **Front** full up - unmuted
  d) **Microphone** full down - muted

2C) On the **RECORDING** tab, set the controls as follows:
  a) **Capture** half way- unmuted
  b) **Capture 1** full down - unmuted
  c) **Digital** half way - unnmuted

2D) On the **OPTIONS** tab, leave the Input Source (both of them) set to **Mic** (the only setting available).

Close the **Volume Control: HDA INTEL (Alsa Mixer)** dialog to finish.

Now you can open the Sound Recorder application (**SOUND & VIDEO** | **SOUND RECORDER** from the menu), click on **RECORD,** talk, then **STOP,** then **PLAY.** You should hear your recording clearly and easily.

---------------------------

At this point, it doesn't matter how I got there - just that I got there.

---

