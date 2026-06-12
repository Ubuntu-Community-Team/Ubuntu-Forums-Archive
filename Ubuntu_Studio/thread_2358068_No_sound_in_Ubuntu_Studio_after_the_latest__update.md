---
title: "No sound in Ubuntu Studio after the latest  update"
date: 2017-04-09
forum: Ubuntu Studio
---

### Post by strategos on 2017-04-09
Hello,
        I've spent many hrs trying to fix problem with no sound in Ubuntu Studio 16,04 LTS and failed.
Problem occurred after last official update few days ago. No problems with sound before .
All steps from b/m link have been followed:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

To be sure it is not hardware problems, I've used Knoppix an FC25 live distros to check it/them - sounds are OK on both.

As to hw info , OS info , settings
uname -r  4.4.0-72-lowlatency

Link to full ALSA diagnostic report
[http://www.alsa-project.org/db/?f=27282d58d5b754f876761b96f8b018c403938638](http://www.alsa-project.org/db/?f=27282d58d5b754f876761b96f8b018c403938638)


Integrated audio - disabled in BIOS (just to be sure ).

I've tried to send bug report using "ubuntu-bug audio" at least four times - after a 30 min of "collecting info about reported bug"
nothing happens.

PC is used as DAW ,thus without sound is only  either dummy or heater( or maybe both)

Any idea how to fix this problem?


Brgds

Strategos

---

### Post by flocculant on 2017-04-09
>  Any idea how to fix this problem?

I'd start by looking in /var/log/apt/history.log to see what the last update was for if you're positive something in the last update killed sound.

---

### Post by strategos on 2017-04-09
Hello,
        logs show only packets downloaded and installed.
I am not able to determine which of them caused problems 
Maybe new kernel?

I guess , that "no sound" could be caused by pulseaudio ,as it shows "dumb output" in "Pavucontrol".
ALSA /ALSA mixer sends signal to pulseaudio , as meter in "pavucotrols" shows it

I've checked all possible setting for my audio device and I  am not able to change this "dumb output"
I've also tried to disable pulseaudio using   "autospawn = no" in /etc/pulse/client.conf - no change.


Brgds

Strategos

---

### Post by marseille2 on 2017-04-09
The log shows that you have sound set to use HDMI (card 0 -- the default sound card).

 If you want to use the M Audio card (set to Card 1), you'll have to choose it (for pulseaudio, see this [post]("https://ubuntuforums.org/showthread.php?t=2345894&p=13580637#post13580637")).


```

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by strategos on 2017-04-09
Hello,
        well, internal audio device is disabled in BIOS!!
It should not have  to do anything to do with sound!!

If it's really accepted by OS as an active hw piece , then it's very strange!!

Once more , I've tried to deactivate pulseaudio using
less  /etc/pulse/client.conf


; autospawn = no
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog



Dammed pulseaudio is still working! What is going on?


Brgds


Strategos

---

### Post by marseille2 on 2017-04-10
Try removing the semi-colon in front of "autospawn=no"

---

### Post by strategos on 2017-04-11
Hello,
       it's been done.
After " autospawn = no" w/t semicolons finally pulseaudio is "dead".

Unfortunately no change in status. No sound.

Despite  internal audio is disabled in BIOS , system want to use it as  a  main audio device all the time -very strange and fishy,

In ALSAMIXER ( started in terminal)  all is set to M Audio Audiophle 24/96 as audio.

What is funny, GUI of ALSAMIXER ( started in LXDE)  shows disabled HDA  ATI HDMI (chip ATI RS670/780 HDMI ) as main and active device in the  system - instead of M Audio.

I really do not know how it's possible!

I really do not know how to fix it !

As for me  it seems to be a bug , probably system bug.



Brgds

Strategos


PS. Knoppix has no problem with disabled on board audio and shows only M Audio as active audio device.
S.

---

### Post by strategos on 2017-04-12
Hello,
further digging in problem - results rather poor.
As per  Pulseuadio :
-------------
studio@studio-PC:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=M2496
    M Audio Audiophile 24/96, ICE1712 multi
    Default Audio Device
---------------
As per me both ALSA and Pulseuadio want to use disabled ( in BIOS) audio device (0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19).
I do not know how this could be possible!
Well ,maybe it has something to do with Studio's RT ALSA?

Brgds

Strategos

---

### Post by strategos on 2017-04-12
Hello,
        I suppose I've found at least temporary solution to my "No sound" problem.
It seems it's caused by wrong ALSA config (??? -means probably) after setting last OS patches/updates to my PC.
For unknown reason system refuses to accept hw;1 as a master audio card ,trying to use  all the time disabled in BIOS on board audio ( hw:0)!
Why - I really do not know and hope it will be fixed by developers of Ubuntu Studio in near future.

As to solution -this temporary solution is very simple.
I've created using editor ( could be  vi, nano , gedit etc)  .asoundrc file in my home directory
-------------------------------------------
studio@studio-PC:~$ more  .asoundrc
pcm.cmipci {
    type hw
    card 1
}

ctl.cmipci {
    type hw
    card 1
}
-------------------------

I've found this solutions on alsawiki home page .


It works for a while and I hope it will last for a while.

Be aware , that this is valid for one user only/actual user  ( studio in my case) , as I don want to edit global ALSA config file.

Brgds

Strategos

---

### Post by nik.charles on 2017-04-14
Your sound device listed for hw:0 is not your motherboard sound card. It is your ATI Graphics Card HMDI digital audio. The HDMI uses same HDA Intel sound driver for ALSA, so can get confused with onboard sound device.

As you already disabled onboard sound device (and probably don't need the HDMI audio either) solution would be to blacklist the HDA Intel Driver

Use Root access (sudo) to create a file /etc/modprobe.d/sound.blacklist.conf (or edit file if already exists)
add this line to file: 'blacklist snd_hda_intel'
Save file
delete the .asoundrc file you mentioned in previous post
Reboot

The HDMI sound device should be gone, with only your M-Audio card shown as device hw:0

---

