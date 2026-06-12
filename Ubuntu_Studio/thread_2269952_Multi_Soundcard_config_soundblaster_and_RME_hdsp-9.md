---
title: "Multi Soundcard config soundblaster and RME hdsp-9632"
date: 2015-03-19
forum: Ubuntu Studio
---

### Post by drboontu on 2015-03-19
I'm running ubuntu 14.04.2 LTS (xfce desktop) with ubuntustudio essentials installed using M-Audio keystation 61es midi keyboard. 

The emu10k1 soundcard is for desktop use and RME hdsp-9632 card for studio work. The problem i'm having is regarding getting qjack to auto configure when I start qjack control then rosegarden or other software. 

At present when I start qjack then say rosegarden it auto connects to system playback_1 and playback_2. 

I have to disconnect playback_1 and playback_2 and connect to playback_11 and playback_12 to get any sound, then all is fine. I have to do this every time I open any audio software after qjack control. 

I've put my config settings below. Is there a way to get the system/playback to auto configure correctly. 

=============== 

$ cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_hdsp
 2 snd_usb_audio 

=============== 

$ cat /etc/modprobe.d/alsa-base.conf 

 alias snd-card-0 snd-emu10k1

 options snd-emul10k1 index=0

 alias snd-card-1 snd-hdsp

 options snd-hdsp index=1

 alias snd-card-2 snd-usb-audio

 options snd-usb-audio index=2 

=============== 

$ cat ~/.asoundrc

pcm.hdsp {
        type hw
        card 1
}

ctl.hdsp {
        type hw
        card 1
}

pcm.hdsp_analog {
        type plug
        ttable.0.0 1
        ttable.1.1 1
        ttable.2.2 1
        ttable.3.3 1
        ttable.4.4 1
        ttable.5.5 1
        ttable.6.6 1
        ttable.7.7 1
        slave.pcm hdsp
}

pcm.hdsp_adat {
        type plug
        ttable.0.8  1
        ttable.1.9  1
        ttable.2.10 1
        ttable.3.11 1
        ttable.4.12 1
        ttable.5.13 1
        ttable.6.14 1
        ttable.7.15 1
        slave.pcm hdsp
}

pcm.hdsp_spdif {
    type plug
    ttable.0.16 1
    ttable.1.17 1
    slave.pcm hdsp
}

=============== 

Thanks! Dave.

---

