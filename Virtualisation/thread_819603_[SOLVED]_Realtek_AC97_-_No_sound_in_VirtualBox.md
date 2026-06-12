---
title: "[SOLVED] Realtek AC97 - No sound in VirtualBox"
date: 2008-06-05
forum: Virtualisation
---

### Post by SatishP on 2008-06-05
Hi All,
I am a total newbie in Ubuntu. To try it, I installed Sun xVM VirtualBox 1.6.0 on my Windows XP SP2 host. I then installed Ubuntu 8.04 on the virtual machine in VirtualBox. With a lot of help, I successfully installed Ubuntu. The network access is also working and I can browse the internet through the Ubuntu guest. The only problem I am facing is configuration of my sound card. I use vlc media player. It plays the audio files I have but no sound comes from the speakers. Infact, no sound at all when I am in Ubuntu. I searched for tips on configuration (similar to graphics card configuration to get various screen resolution modes) but to no avail.
Can anyone help me in configuring my sound card (Realtek AC97 Audio as seen from Windows XP host)?

Thanks
Satish

---

### Post by Oldsoldier2003 on 2008-06-05
> **SatishP said:**
> Hi All,
I am a total newbie in Ubuntu. To try it, I installed Sun xVM VirtualBox 1.6.0 on my Windows XP SP2 host. I then installed Ubuntu 8.04 on the virtual machine in VirtualBox. With a lot of help, I successfully installed Ubuntu. The network access is also working and I can browse the internet through the Ubuntu guest. The only problem I am facing is configuration of my sound card. I use vlc media player. It plays the audio files I have but no sound comes from the speakers. Infact, no sound at all when I am in Ubuntu. I searched for tips on configuration (similar to graphics card configuration to get various screen resolution modes) but to no avail.
Can anyone help me in configuring my sound card (Realtek AC97 Audio as seen from Windows XP host)?

Thanks
Satish
have you enabled sound in the virtual machine? if so try setting it to pulse instead of nullaudio

---

### Post by Drakkor on 2008-06-05
Yeah, I also had no sound,but changed the audio driver to alsa, and it works fine now. :)

---

### Post by SatishP on 2008-06-06
Hi,
Yes, I enabled sound in the virtual machine. But set it to nullaudio. Will check with pulse and report back. Thank you for your help.
Drakkor, I did set my playback to ALSA Audio Driver inside Ubuntu but it has no effect. But I do not get the option of ALSA Audio Driver in the drop down of VirtualBox (my host is WinXP).

Thanks for your help
Satish

---

### Post by Drakkor on 2008-06-06
I had to go to Innotek v. 1.5.4 , not the Sun version of virtual box to get mouse support anyway, if you click on the highlighted "Audio" in the screenshot , it might have an error box,something about no usb support, I don't know what that's all about,coz I have a usb mouse and keyboard,but just click never show again,and you'll get the screen I previously posted to change the audio driver. Click the attached thumbnail 3X to get full screen.

---

### Post by SatishP on 2008-06-06
Hiiii,
I succeeded in getting my sound working in Ubuntu.
I did not have the 'pulse' option in the drop down for VirtualBox. But I had 'Windows DirectSound' and I tried after selecting that. My sound card works well with Ubuntu too!!!
Thanks Oldsodier2003 and Drakkor!!

Cheers,
Satish

---

