---
title: "Virtualbox locks Pulseaudio output"
date: 2008-04-05
forum: Virtualisation
---

### Post by aaron552 on 2008-04-05
Whenever I start a virtual machine in virtualbox that uses the pulseaudio sound output driver, all sound on the host stops working. The sound in the guest works fine. Once the virtual machine is stopped apps that use sound have to be restarted but the sound works fine again afer this.
Is there any way to get sound working on both the host and the guest at the same time?

Only the pulseaudio driver works at all (apart from null audio)

---

### Post by VitaLiNux on 2008-04-05
Have you tried ALSA? OSS? You have to give more information in order to give you a hand. It seems there are conflicts with your hardware/sound driver settings and your virtual machine. Also, you need to provide wich OS you are emulating.

---

### Post by aaron552 on 2008-04-06
Alsa and OSS output methods do not work.
I'm running Windows XP and gentoo as guests.
If I try to start more than one guest using pulseaudio output for the virtual sound card, only the first will work

EDIT: New pulseaudio updates have fixed the Alsa and OSS ouput drivers, I haven't tried more than one virtual machine since, though.

---

