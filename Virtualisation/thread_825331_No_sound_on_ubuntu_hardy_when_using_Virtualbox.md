---
title: "No sound on ubuntu hardy when using Virtualbox"
date: 2008-06-10
forum: Virtualisation
---

### Post by benhur99ph on 2008-06-10
Hello! I just noticed this today, I was using virtualbox (winxp is my VM) and whenever I run Vbox, the sound on my Ubuntu Hardy disappears, but the sound on my VM worked fine... It's not really a major problem for me... but I can't hear the sound alerts especially on pidgin whenever I'm working using the VM... anyone else got this problem -- and if is there a fix? Thanks! :confused:

---

### Post by thomasaaron on 2008-06-12
Yep, I've got the same problem. Working on it.

---

### Post by thomasaaron on 2008-06-12
OK, I think they may have intended for this to be the case. I found a workaround, though. It's not the greatest thing in the world, but it works for me.

If I set the audio device on VBox to either alsa or oss, I get sound only from VBox (not from Ubuntu) when the guest OS (Vi$ta, in my case) is booted.

If I set it to pulse audio, I get sound from both Ubuntu and the guest os.

Hope that helps somebody.

---

### Post by cybersmoker on 2008-06-15
> **thomasaaron said:**
> OK, I think they may have intended for this to be the case. I found a workaround, though. It's not the greatest thing in the world, but it works for me.

If I set the audio device on VBox to either alsa or oss, I get sound only from VBox (not from Ubuntu) when the guest OS (Vi$ta, in my case) is booted.

If I set it to pulse audio, I get sound from both Ubuntu and the guest os.

Hope that helps somebody.

Hey that worked for me, Thanks!

You think that is because maybe some of these audio drivers lock the sound system? Similar to Windows COM devices locking the port to poll it?

---

