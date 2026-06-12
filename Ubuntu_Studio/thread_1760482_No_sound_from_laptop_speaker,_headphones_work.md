---
title: "No sound from laptop speaker, headphones work"
date: 2011-05-17
forum: Ubuntu Studio
---

### Post by edwardoclese on 2011-05-17
...but everything worked just fine under Ubuntu Desktop. Did they change something in Studio?

I've tried Lucid, Maverick, and Natty on my machines, and the regular desktop i386 distros work just fine.
When I install the Maverick and Natty versions of Ubuntu Studio, I get no sound from the laptop speakers.

I've tried modifying the /etc/modprobe.d/alsa-base.conf file with the addition of [FONT=Courier New]options snd-hda-intel model=panasonic[FONT=Verdana] with no difference.

Any suggestions?


[/FONT][/FONT]

---

### Post by Pablo_F on 2011-05-17
Does this happen with the default audio server (pulseaudio) or when using jack?

Can you run the alsa-info.sh script and upload it somewhere so we can try to see the problem? This command will do this at once (give here the URL):

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Cheers, Pablo

---

### Post by edwardoclese on 2011-05-18
PabloF,

Here is the alsa-project info you requested.

 [http://www.alsa-project.org/db/?f=969f4cd2b4d3767f6564d05bd29dc40ad1bebf00](http://www.alsa-project.org/db/?f=969f4cd2b4d3767f6564d05bd29dc40ad1bebf00)

I have yet to try JACK, so this must be under PulseAudio. Please forgive this noob for his newbieness.
Thank you for your help!

---

### Post by Pablo_F on 2011-05-18
I am not sure what model you should specify, if any.

I suggest you boot from a generic ubuntu Live CD (same version than the ubuntustudio you are currently running), check that sound works as expected, run the alsa-info.sh script and compare the outputs, specially under the header "Loaded sound module options". Give the new output if in doubt. 

Cheers, Pablo

---

