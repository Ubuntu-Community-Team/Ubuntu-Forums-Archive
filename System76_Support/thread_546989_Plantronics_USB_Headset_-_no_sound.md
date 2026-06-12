---
title: "Plantronics USB Headset - no sound"
date: 2007-09-09
forum: System76 Support
---

### Post by Canucktom on 2007-09-09
I know there was a thread concerning this problem ([http://system76.com/forums/viewtopic.php?t=1521&highlight=plantronics](http://system76.com/forums/viewtopic.php?t=1521&highlight=plantronics)) but even with the latest System76 Driver (2.0.9) my headset still would not work.

Reinstalling the System76 Driver and rebooting had no effect.

The volume control of the headset works fine but the speakers are dead. Instead I get the sound from my laptop speakers.

any suggestions?

Tom

---

### Post by thomasaaron on 2007-09-10
What is your System76 model number, so we can do testing here at the shop if necessary?

You might try looking at this post:
[http://ubuntuforums.org/showthread.php?t=525202&highlight=usb+headphones](http://ubuntuforums.org/showthread.php?t=525202&highlight=usb+headphones)

It also deals with Plantronics headsets. We've had a lot of success with Logitech USB headsets, but a lot of complaints about Plantronics ones.
This post has some settings you should try out.

---

### Post by Canucktom on 2007-09-10
I have a Gazelle Value GAZ-V4 with Feisty.

I've tried all of the advice from the thread you mentioned.
Strangely enough, if I hit the test buttons in the preference sound settings I get the test noise on the headset. But as soon as I try using Skype or any other application the speakers kick in and the headset's dead.

Here's what I changed:

1. Make sure your sound device is set to the USB device (Double-click speaker icon. In resulting window, go to File > Change Device > USB...)

yep

2. In the sound settings (System > Preferences > Sound) I set everything to the USB device in the drop down menus).

yes

then I restored the system76 drivers

and finally here's what I get typing this commands:

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.14rc3.
Compiled on Sep 10 2007 for kernel 2.6.20-16-generic (SMP).

lsmod | grep -i usb 

snd_usb_audio          81792  0 
snd_usb_lib            17664  1 snd_usb_audio
snd_hwdep              10372  1 snd_usb_audio
snd_rawmidi            25984  2 snd_usb_lib,snd_seq_midi
snd_pcm                81028  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
usbhid                 26592  0 
hid                    27392  1 usbhid
snd                    56452  15 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               134280  7 snd_usb_audio,snd_usb_lib,xpad,usbhid,ehci_hcd,uhci_hcd

Does that make sense to you?
Are there any other settings for the audio device I might have forgotten?

And thanks for the tip with the logitech headsets (if only I had known this in advance - they even were cheaper!). If it does not work out I'll try to get them exchanged.

Tom

---

### Post by thomasaaron on 2007-09-10
If you're getting the test sound with the Plantronics headset, that is good. At least we know they work. That's the first positive feedback I've gotten about them. And it looks like your modules are loaded.

Here is an interesting article in Ubuntu's Community Documentation about Plantronics Headsets. You might have a look at it and see if it helps.

[https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls](https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls)

---

### Post by Canucktom on 2007-09-10
nope, unfortunately no change.

I created the file but it had no effect.

And the volume controls worked just fine from the beginning...

Tom

---

### Post by Canucktom on 2007-09-12
Hi again,

meanwhile I exchanged the plantronics headset against a Logitech, happily looking forward to just plug it in and have a nice phone conversation.

But again exactly the same problem](*,)
It is a Logitech USB Headset 250.
I tried the same things as with the plantronics and again the testsound (system -> preferences -> sound) works fine over the headset but everything else comes over the speakers.

Maybe a detail of interest: when I reboot the machine, with the headset plugged in, system -> preferences -> sound says "USB audio device (not connected)".

What else can I do?
I also found other threads where it says that these headsets work fine if you just plug them in.
Is the only alternative to use the audio and mic ports?

Tom

---

### Post by thomasaaron on 2007-09-13
I'll be out today, but I'll start testing on Friday.

---

### Post by Canucktom on 2007-09-17
Hi Thomas,

and thanks for your patience :-)

I gave it up and exchanged the USB headset against an analog Plantronics headset.
Result: sound over the earphones is nice but still I don't get the micro working. Instead the laptop micro is still switched on.
Did I forget any adjustment?
Is there any other location for sound settings (except alsa and sound preferences)?

Thanks,
Tom

---

### Post by Canucktom on 2007-09-19
I just realized that I don't have any slider / switch for "mic boost".

Could that be the reason?

Tom

---

### Post by thomasaaron on 2007-09-20
Not sure. I just remembered to bring in my USB headset today, so I'll try to test it today or tomorrow.

Plug in your headset, double click on your speaker icon, and then navigate to Edit > Prefs. Make sure all of the boxes are clicked. Does this give you a mic slider?

Best,
Tom

---

### Post by Canucktom on 2007-09-20
Plug in your headset, double click on your speaker icon, and then navigate to Edit > Prefs. Make sure all of the boxes are clicked. Does this give you a mic slider?

Checked them all. A have a mic and mic capture slider but no mic boost.
I also tried a different analog headset which had worked before but still the same problem.

Meanwhile I read a lot of different threads concerning sound problems but nothing seems to apply to me.

Tom

---

### Post by Canucktom on 2007-09-25
Hi guys,

nobody any idea?

I would also appreciate any alternative to a headset.
The problem is, that Gizmo is going to be my only phone number in a few days and it would be too bad if the quality is as crappy as it used to be.
:-k

cheerio,
Tom

---

### Post by thomasaaron on 2007-09-26
OK, I got it to work.

*GazV4
*7.04 Feisty Fawn
*Ran System 76 Driver (2.0.9)
*Logitech USB headphone/mic set-up (no further model number available, but it is definitely a nice set).

Boot up the computer FIRST. Then plug in the headphones. I'm not sure why yet, but if I boot up the machine with the headphones in the usb port, the following directions do not work.

Sound Device Setup
1. Double-click the speaker icon in the upper left.
2.File > Change Device > Logitech USB Headset (Alsa mixer)
3. Edit > Preferences (select all: Microphone, Microphone Capture, Speaker)
4. Under Recording tab, turn "Microphone Capture" all the way up. 
5. Under Playback tab, turn "Microphone" and "Speaker" about 3/4 the way up.

Sound Control Selections
6. Go to System > Preferences > Sound
7. Set all "Sound Playback" and "Sound Capture" pull-downs to USB Audio.
8. Set "Default Mixer Tracks" to "Logitech USB Headset (Alsa Mixer)"
9. In the list box below, highlight "speaker"

Sound Recorder
It is slightly hosed, but it is still usable if you know what to do.
10. Applications > Sound & Video > Sound Recorder
11.Click "Record" and say: "Ubuntu rules; Another very popular OS druels."
11. File > Save As.  Save it wherever. (NOTE: The save button does not work the first time you record. You will have to use "Save As."  The save button will work if you click it AFTER your first save.)
12. Now that you've saved, you can click your play button and enjoy listening yourself talk smack about other OS's in your usb headphones.

Hope this helps.

---

### Post by Canucktom on 2007-09-27
Hi Thomas,

I appreciate your effort but unfortunately it does not really help for I have the problem with an analog headset (I wrote that some postings ago).
The USB headsets did not work - neither Plantronics nor Logitech - so I got me an analog headset.
The earphones work fine but the micophone does not. The laptop micro is still on - no change after I plugged in the headset.

Tom

---

### Post by thomasaaron on 2007-09-27
You might want to start a separate thread for it, then.
It gets a little difficult to track subtle changes in topic in multi-page threads.

---

