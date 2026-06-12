---
title: "Wine acts weird"
date: 2009-10-11
forum: Wine
---

### Post by Felystax on 2009-10-11
Hello,

I've been using Ubuntu for over a year now, and i wanted to run some emulated windows applications. Well, of course i installed wine. It worked fine on my other pc, but since i got a new one wine won't do much... When i run any wine related applications such as wineconfig or the emulator itself, my computer starts acting really weird. For example: If i mouse-over AWN the icons move really slow. It doesn't completely freeze my pc, but it's close. Sometimes the lag goes away after say 10 minutes. Sometimes it just stays. But apart from that i managed to install the Devil May Cry 4 demo. But it just won't load! I figured my pc should be able to handle it...:

4 GB Ram
Amd Phenom Quad Core @ 2.2GHz
ATI Radeon HD 4650 (OC @ 690 MHz)

Am i horribly mistaken or is there another problem? 

Thanks in advance,

Alex

---

### Post by Felystax on 2009-10-11
I just ran winecfg from the terminal and i got this error (if it is an error):

teun@PCTEUN:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
teun@PCTEUN:~$ 

I don't why theres HDMI right there, because i use a VGA cable with DVI switch, so no HDMI there.

---

### Post by hikaricore on 2009-10-11
> **Felystax said:**
> I just ran winecfg from the terminal and i got this error (if it is an error):

teun@PCTEUN:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
teun@PCTEUN:~$ 

I don't why theres HDMI right there, because i use a VGA cable with DVI switch, so no HDMI there.

There are no errors in that output.
Fixme messages are for the wine devs and can be ignored.

Sorry I can't really help with your issue, but as far as what you posted it means nothing.

---

### Post by Felystax on 2009-10-11
Thanks for the reply. Maybe someone else can fix this. Till then im stuck to Tux Racer ;)

---

