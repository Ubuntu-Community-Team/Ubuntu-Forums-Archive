---
title: "Garbled sound with Skype and some other applications."
date: 2013-09-19
forum: Ubuntu Development Version
---

### Post by Sslaxx on 2013-09-19
Just upgraded to Kubuntu 13.10 and the sound with Skype is now garbled. It hangs, skips, crackles etc. This appears to be an issue with Pulseaudio - anyone else been having issues? It had been working fine with 13.04.

---

### Post by VMC on 2013-09-19
I'll check later, but what hardware do you have?

---

### Post by Sslaxx on 2013-09-19
Onboard sound stuff, AC 97 I think.

---

### Post by VMC on 2013-09-19
I just tried using sound in Kubuntu 13.10. I re-read your post, and realized its regarding Skype.
 Does your sound work ok playing music. I use VLC if that matters.

```
lspci|grep audioThu Sep 19 
$ lspci|grep Audio
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)

```

---

### Post by Sslaxx on 2013-09-19
No issues there. I fixed it by changing a line in /etc/pulse/default.pa.

It now reads: ```
load-module module-udev-detect use_ucm=0 tsched=0
```

---

### Post by amjjawad on 2013-09-20
> **Sslaxx said:**
> Just upgraded to Kubuntu 13.10...

Hi,

You do realize 13.10 is still under heavy development and it is not yet released as a stable version, right? just want to make sure you know that :)

What Skype version do you have?

---

### Post by Sslaxx on 2013-09-20
Indeed, quite aware that 13.10 isn't officially released yet. Latest version of Skype from their site.

---

### Post by amjjawad on 2013-09-20
> **Sslaxx said:**
> Indeed, quite aware that 13.10 isn't officially released yet. Latest version of Skype from their site.

Great ;)
Just wanted to make sure, that is all :D

I will try to test that ... I have Ubuntu GNOME 13.10 installed on this machine but I need to reboot and install Skype!

---

### Post by Sslaxx on 2013-09-20
As a side note, the fix above messes up Audacity, unfortunately.

---

### Post by ms3811 on 2013-10-18
Solution here: [http://community.skype.com/t5/Linux/No-sound-or-crappy-sound-on-Kubuntu-13-10/td-p/1839659](http://community.skype.com/t5/Linux/No-sound-or-crappy-sound-on-Kubuntu-13-10/td-p/1839659)

---

### Post by peter_f_calder on 2013-10-25
> **Sslaxx said:**
> No issues there. I fixed it by changing a line in /etc/pulse/default.pa.

It now reads: ```
load-module module-udev-detect use_ucm=0 tsched=0
```

Hi 

I had the same problem and tried as you said. I couldn't save as when i went into properties it said i don't have permission to change the file. I tried by opening Default.pa but it is read only.

This problem was on my laptop. I have just tried to use my desktop for a call on Skype only to find the same problem.

Peterfc

---

