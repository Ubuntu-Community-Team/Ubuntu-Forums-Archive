---
title: "What is best cheap audio input card?"
date: 2012-01-22
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-01-22
I was using digitech RPx400 to input guitar.

But I want quality line inputs for a mixing board/microphones etc. and playback.

Is there a pci card that is easy to use with Linux shareware studio stuff,
and is also cheap, but with good A/D converters?

What is recommended, and what is easy to install, and cheap?

I don't want to buy an mbox outboard unit, because this is like $200 or more.

I was hoping for a cheap card with good D/A converters which is recognizable and compatible with Linux. (I can't go back to Windoze)

thank you for any advice here.

---

### Post by satanselbow on 2012-01-22
I use behringer stuff for misc audio input ie uca200 for phono inputs (mixer etc) [http://www.behringer.com/EN/Products/UCA202.aspx](http://www.behringer.com/EN/Products/UCA202.aspx) (i've got 2 of them at the moment) as well as their guitar link. Also use their UMX25 for music keyboard / midi triggering ;)

All recognised as "standard" devices in their own respective class under 11.10 (though I use LM12) with the 3.0.0-13-lowlatency-pae kernel keeping every lag free :D

Very much depends how many simultaneous inputs you need?

---

### Post by nazaroo2 on 2012-01-22
> **satanselbow said:**
> I use behringer stuff for misc audio input ie uca200 for phono inputs (mixer etc) [http://www.behringer.com/EN/Products/UCA202.aspx](http://www.behringer.com/EN/Products/UCA202.aspx) (i've got 2 of them at the moment) as well as their guitar link. Also use their UMX25 for music keyboard / midi triggering ;)

All recognised as "standard" devices in their own respective class under 11.10 (though I use LM12) with the 3.0.0-13-lowlatency-pae kernel keeping every lag free :D

Very much depends how many simultaneous inputs you need?

Thanks for this:

I see they are on the internet for about $25.00

Do you know what is the difference bewteen the 202 and the UCA222?

On one site they say:
High-resolution 48 kHz converters for high-end audio quality  

does this mean that the 202 has only 44 kHz?

---

### Post by sgx on 2012-01-22
There are a few pci cards from m-audio that use the snd_ice1712
kernel module, and envy24control mixer, since years of tweaking them have passed,
any config help is already on google, and common in
forums. The AV Linux dev uses  m-audio Delta1010 or 1010LT,
and I think two at once sometimes. Several topics are here, in the archives.
Cheers

---

### Post by nazaroo2 on 2012-01-23
> **sgx said:**
> There are a few pci cards from m-audio that use the snd_ice1712
kernel module, and envy24control mixer, since years of tweaking them have passed,
any config help is already on google, and common in
forums. The AV Linux dev uses  m-audio Delta1010 or 1010LT,
and I think two at once sometimes. Several topics are here, in the archives.
Cheers

Thanks for you help.
I will do a search for the snd_ice1712 because I have no idea what that is right now.

---

### Post by sgx on 2012-01-23
> **nazaroo2 said:**
> Thanks for you help.
I will do a search for the snd_ice1712 because I have no idea what that is right now.
the command  lsmod  outputs your system kernel modules.
Some modules interact others, as shown in the list below
from the audio portion of the lsmod output on my setup:

snd_ice1712            50334  0 
snd_ice17xx_ak4xxx      1992  1 snd_ice1712
snd_ak4xxx_adda         7570  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              5944  1 snd_ice1712
snd_ac97_codec         90143  1 snd_ice1712
ac97_bus                 850  1 snd_ac97_codec
snd_i2c                 3141  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         4983  1 snd_ice1712
snd_rawmidi            15287  2 snd_usbmidi_lib,snd_mpu401_uart
snd_seq_dummy           1135  0 
snd_seq_oss            25264  0 
snd_seq_midi_event      4648  1 snd_seq_oss
snd_seq                42136  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          4457  4 snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            33854  0 
snd_pcm                60702  4 snd_usb_audio,snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              15383  2 snd_seq,snd_pcm
snd_page_alloc          6037  1 snd_pcm
snd_mixer_oss          12981  1 snd_pcm_oss
snd                    43189  17 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss

modprobe is a command to load a kernel module that is needed for
new hardware,
modprobe snd_ice1712

This step likely won't be needed, but it's good to know.
Cheers

---

