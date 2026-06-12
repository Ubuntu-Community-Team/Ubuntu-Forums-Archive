---
title: "Gazelle value microphone problem"
date: 2008-03-01
forum: System76 Support
---

### Post by mdozurk on 2008-03-01
Just got my new laptop yesterday.  Everything works fine except the microphone, cannot make skype calls.

I tested by recording using both the internal microphone and an external one.  The internal one gives me nothing but white noise the external one gives me laud clicking and I can hear my voice very faintly. 

I have mic boost at max, front at max, capture at max.

Any ideas on how I can fix this?

Thanks,

Mustafa

---

### Post by EdThaSlayer on 2008-03-02
Which program are you using to record your voice? 

I'm using Kubuntu, and in Kubuntu there is something called  Mic Boost 20db which you can click to make your microphone more sensitive(you have already done that). Also, there should be a microphone option in the "input" category, put that also to the max.

---

### Post by mdozurk on 2008-03-02
I have all the tracks selected and in the recording area I have only capture and digital.  No mic.  Is this my problem?

---

### Post by thomasaaron on 2008-03-03
Attached are screenshots of how I set up the internal mic to work with Sound Recorder.

To set it up with Skpe, you may need to set it up *within* skype. There is a little gear icon on the bottom of the GUI. Click it and then click Options > Sound Device.

In my experience, though, Skype does much better with an external mic or a USB mic.

---

### Post by mdozurk on 2008-03-08
I tried those settings and the best I've got is a lot of white noise and my voice in the background.

It seems like either the ALSA drivers suck at recording microphone input or the sound card used by gazelle value is incompatible with ALSA.

My drivers are 1.0.15rc3.

Please let me know if there is a solution to this issue.

---

### Post by thomasaaron on 2008-03-10
Yes, the ALSA drivers don't work so great with the internal mic.
The best work-around is to use an external mic or a USB mic.

We will be doing extensive testing in this area for Hardy's release and hope to come up with a much better internal mic recording solution for the GazV5.

---

### Post by mdozurk on 2008-03-10
I tried an external microphone -- it sucks as well.  I haven't tried a USB microphone but honestly I find that ridiculous: why buy a built in webcam when the mic isn't built in?  Also why does system76 advertise a microphone when the mic doesn't even work?  You are setting up your customers for disappointment.

---

### Post by thomasaaron on 2008-03-11
The external mic seems to work pretty good on ours. Attached are screenshots.
They are for an external mic and headphones. You can use the computer's speakers by muting headphones and unmuting Front.

---

### Post by mdozurk on 2008-03-17
Almost.  I tried with the settings you gave me and was able to use both the sound recorder and skype.  Turned off my computer happy and satisfied.  The next morning tried to make another call and again nothing worked.  I have been experimenting with the settings for the last few days, tried with several different external microphones and still have not been able to record anything.

I'm using the same mixing and recording settings as you posted.

Mustafa

---

### Post by thomasaaron on 2008-03-17
Try running your System76 driver. Maybe an update hosed ALSA.

---

### Post by mdozurk on 2008-03-17
I ran system76 and rebooted,  No help, still can't record ;(

---

### Post by thomasaaron on 2008-03-17
Can you post screenshots of our settings? Just turning your computer off should not affect this.

I realize this is a dangerous question, but... do you have your mic and headphone plugged into the right jacks? Mic should be in the red jack.

---

### Post by mdozurk on 2008-03-18
I've attached screenshots.

I understand you had ask; red goes to red, green goes to green. :)

---

### Post by thomasaaron on 2008-03-18
OK, that all looks good. Does your System > Preferences > Sound settings look like this? (See attached).

Also, please post the output of:
```
cat /proc/asound/version
```

---

### Post by mdozurk on 2008-03-18
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.15rc3.
Compiled on Jan  8 2008 for kernel 2.6.22-14-generic (SMP).

The sound settings are mostly the same, there are some diffs: screenshot attached.

---

### Post by thomasaaron on 2008-03-18
Hmmm. That is all correct. Perplexing.

Now,  post the output of:

```
cat /etc/modprobe.d/alsa-base
```

I'll compare it against the one I have here in the shop to see if there is something amuck.

---

### Post by mdozurk on 2008-03-18
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=toshiba

---

### Post by thomasaaron on 2008-03-18
That looks good too.
I'm not sure at this point.

Did you play with any gstreamer properties or download any other sound recording hardware? And you are trying to use Sound Recorder for our testing here, right?

---

### Post by mdozurk on 2008-03-19
No, I didn't touch any other setting.  I'm using the sound recorder to test.

---

### Post by thomasaaron on 2008-03-19
I'm starting to run out of ideas on this one. 
All of your settings are correct, you are running the correct ALSA version.
It worked with no problems and then just stopped working when you turned the computer back on.

Hmmmm......

I want to say "USER ERROR!" :)

*Double-check your connections. Don't go red-to-red, green-to-green. The jacks have a pic of a mic and headphones on them. Remove them, restart the computer, and then plug them back in. Make sure they are all the way in.

*Try saving your recordings as something besides WAV. Try OGG.

Are you getting any errors? When you try to play back what you recorded, what are you hearing? Silence? Static? Clicking?

---

### Post by mdozurk on 2008-03-19
I think I figured it out:  after I reboot the computer I go to volume settings switch to front mic, close, reopen, switch to mic and everything works.

Do you think we can get a software fix for this?

Mustafa

---

### Post by thomasaaron on 2008-03-19
You could file a bug report with Ubuntu so that they can fix it in future releases.
To do that, you would need to give them instructions on how to dupliate the problem.

---

