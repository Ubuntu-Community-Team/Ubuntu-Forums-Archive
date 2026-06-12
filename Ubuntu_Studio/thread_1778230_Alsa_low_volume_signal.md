---
title: "Alsa low volume signal"
date: 2011-06-08
forum: Ubuntu Studio
---

### Post by Bluesthang on 2011-06-08
Hi, 
so i'm having no luck with usb audio interfaces in Ubuntu 11.04.
I first bought a M-Audio Mobilepre this week. The sound is there, but very low. I have to put the volume knobs on the device at the maximum to get something decent. 
In a terminal with "alsamixer", it says the device has no volume controls.
So today, I exchanged it for a Lexicon Lambda wich I searched in forums finding that people had them working in ubuntu. 
But now I get the same exact problem with the Lexicon Lambda. So I'm guessing there it might have something to do with Alsa.
I'm on a Sony Vaio vgn 150d with Ubuntu 11.04.
When I try it in windows 7, the volume is at least double. 
There must be a solution to this... all I want is to get decent volume with the mics.
Need some help!!!!
Thanks

---

### Post by sgx on 2011-06-09
Hi, the alsamixergui should display all the inputs and outputs,
let you turn them on/off and adjust the volume. If its not installed,
it should be in synaptic, or here

[http://packages.debian.org/unstable/sound/alsamixergui](http://packages.debian.org/unstable/sound/alsamixergui)

Cheers

---

### Post by Bluesthang on 2011-06-09
hi thanks for the reply,
last night i tried an Alsamixer gui that I got from the software center.
When opend it, it showed my laptop volumes, and under it, it showed the Lexicon Lambda but with no sliders at all.
Not sure if its the same gui you are talking about.
Or is there something that i need to install or re-install on my system? do i have the proper version of Alsa?
I'm have the standard Ubuntu 11.04 and not the ubuntu studio installed... I did install jack and Ardour and audacity.
Is there something very differente when installing ubuntu studio vs standard ubuntu?

---

### Post by Pablo_F on 2011-06-09
Hi, I don't know much of USB devices but it is posible that they just don't have an internal mixer. 

Maybe you should search or ask in the alsa users mailing list. Also, run the alsa-info.sh script so people can see your software-hardware configuration and they can help you.

---

### Post by sgx on 2011-06-09
> **Bluesthang said:**
> hi thanks for the reply,
last night i tried an Alsamixer gui that I got from the software center.
When opend it, it showed my laptop volumes, and under it, it showed the Lexicon Lambda but with no sliders at all.
Not sure if its the same gui you are talking about.
Or is there something that i need to install or re-install on my system? do i have the proper version of Alsa?
I'm have the standard Ubuntu 11.04 and not the ubuntu studio installed... I did install jack and Ardour and audacity.
Is there something very differente when installing ubuntu studio vs standard ubuntu?
the setup panel of qjackctl

Input Device  >
Output Device >

click the > widgets, and choose the Lambda

The setting for Periods/buffer should be 3

sudo apt-get install alsamixergui

Lots of soundcards do not have alsa detected mixers, and still work.
Cheers

---

### Post by Bluesthang on 2011-06-10
OK, thanks again for the replies,
I will give that a try when I get home.
I just need that extra gain  for situations that aren,t close up to the mic ;)

---

### Post by sgx on 2011-06-10
Here is a short discussion with some good info on related issues, products, and standards.
Cheers

---

### Post by Bluesthang on 2011-06-11
ok, so I tried the alsamixer gui again, and stilll no sliders.
SGX I think you forgot to paste the link you mentioned in your last post.
I've been searching around and found 2 pages that might help me... but dont know how to go about it.
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)
They mention the alsa-base.conf file to edit it. 
But I'm not sure how to actually edit that file as they describe it.
Here is my alsa-base.conf:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

not sure if all that helps...

---

### Post by Pablo_F on 2011-06-11
Can you describe what you are doing? From scratch, as if it was your first post again. Include your hardware configuration and the things you do after the computer is up and running. The way you try to capture sounds and other bits of info that you might find relevant (but don't repeat what we already know about alsamixer, etc. I don't think the problem has to do with alsa). 

Cheers, Pablo

---

### Post by sgx on 2011-06-11
> **sgx said:**
> Here is a short discussion with some good info on related issues, products, and standards.
Cheers

actually, it's here, not back there :(

[http://www.dvinfo.net/forum/all-things-audio/470960-problem-lexicon-alpha-audio-device.html](http://www.dvinfo.net/forum/all-things-audio/470960-problem-lexicon-alpha-audio-device.html)

cheers

---

### Post by Bluesthang on 2011-06-13
Thanks for the link SGX.
At least when I record with my Lambda, the sound quality stays very good. Seems better than the M-Audio Mobilepre. So even with my GAINS high up, I don't get any white noise. The reason I'm trying to figure out if I can maximize the gain, is if i need to have a Mic capturing ambiant sound, having the mic farther away. 
Or could it have something to do with the mics I am using?
I am using a sure sm58 and sm57

And for Pablo,
I boot my computer with the Lambda plugged in.
I open Jack then Ardour.
Specs:
-Ubuntu 11.04 on a Sony Vaio vgn 150d laptop
- Running Jack and Ardour or Audactiy but mostly Ardour
-Lexicon Lambda usb audio interface
-SM58 and SM57 SURE mics
hmmm not sure what else i can say...
All in all, as I said, everything works, but for the gain being low. Sound quality is good.
Who knows, maybe everything is fine and I'm being picky... I just find it odd that my gain volumes need to be almost at the max.
Once again, thanks for all your help. I think Ubuntu and the linux community is great ;)

---

### Post by sgx on 2011-06-13
Another user, flaggmann, just reported a loud volume drop after upgrading from
10.04/10.10, to 11.04, so it may be worth trying the earlier versions.
Over the years, newer linux versions offer no guarantee of being better
for musicians.

Cheers

---

### Post by skrawboy on 2011-06-19
This worked for me:)

[http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html#comment-form](http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html#comment-form)

---

### Post by Bluesthang on 2011-06-20
skrawboy,  are you running ubuntu 11.04?
All my searches seem to point at 10.10 with alsa 1.0.24.

---

### Post by skrawboy on 2011-06-21
I'm running 10.10..

Regards Lars

---

