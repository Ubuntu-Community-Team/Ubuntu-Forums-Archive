---
title: "Skype on Linux: Which distro just works"
date: 2010-10-13
forum: The Cafe
---

### Post by shuttleworthwannabe on 2010-10-13
Now I must say, I do not use Skype on Linux (Ubuntu mainly), because i can never for the life me figure out why the sound devices have to be so complicated to configure in skype. So my microphone does not work and i can use VOIP on linux. I have tried most distros, and even those those that come bundled with this non-free app, also do not work.

I have just installed Skype for linux beta x64 version from skype website and my sound microphone does not register any sound.

Tell me which distro just works with skype out of the box.

S

---

### Post by kaldor on 2010-10-13
-opensuse worked wonderfully for me.
-Sabayon was hit/miss
-Ubuntu was dreadful (all versions so far)
-Mint not much better than Ubuntu
-LMDE worked great AFTER I installed proprietary nvidia drivers
-Fedora was similar to Ubuntu


I'd pick OpenSUSE if you have the time to learn.

---

### Post by Trougedoor122 on 2010-10-13
Skype works just fine for me. I'm running Ubuntu 10.04 32-bit and Skype (Beta) version 2.1.0.81 (32-bit). I didn't have to do any advanced configuration, it just worked, right out of the box.

---

### Post by Random_Dude on 2010-10-13
I had some issues with the mic. Mainly because I use an external mic and not the one that comes with the laptop, but I figured how to fix that.
As for the camera it was up-side down, I had to fix that too.

I haven't tried skype on other distos, but from my limited experience, Ubuntu is probably not the best.

Cheers :cool:

---

### Post by fatality_uk on 2010-10-13
Ubuntu perfectly. Not sure why you getting sound issues.

---

### Post by gradinaruvasile on 2010-10-13
I never had problems on Ubuntu neither on Debian. A basic understanding of the Linux sound is required however on any distro (ALSA and PulseAudio).
Skype does not have anything special it just uses the systems sounds (PulseAudio if available and if not, ALSA). The problem is that people sometimes dont have their sound set up correctly on their system (mostly the capture device is ignored until it is needed).

---

### Post by inobe on 2010-10-13
kubuntu and opensuse, works just fine.

i think you should ask what hardware works with skype, you will get a better idea, or at least search your model at the skype forums.

---

### Post by Simian Man on 2010-10-13
Works great for me on Fedora.  I think it has much more to do with your sound devices than the distro you run.

---

### Post by beastrace91 on 2010-10-13
> **Simian Man said:**
>  I think it has much more to do with your sound devices than the distro you run.

That would be a correct assumption. Some audio hardware still fails to work properly with modern open source drivers. Try installing the audio kernel backport modules and see if they help.

~Jeff

---

### Post by mrebanza on 2010-10-13
> **Trougedoor122 said:**
> Skype works just fine for me. I'm running Ubuntu 10.04 32-bit and Skype (Beta) version 2.1.0.81 (32-bit). I didn't have to do any advanced configuration, it just worked, right out of the box.

Same here 32-bit works like a dream . . . ubuntu

---

### Post by oldsoundguy on 2010-10-13
Doesn't work for me.  Have video when I test .. have NO sound when I test .. and Skype will not even connect to it's own test program (or anything else for that matter).

The problem is in the 3rd party Skype software not being able to work with the Linux kernel/hardware in some instances. And Skype really couldn't give a sh** about the small amount of users in Linux, so little or no effort is expended in our direction!  They have been running that same screwed up BETA for the last three builds!!!

---

### Post by beetleman64 on 2010-10-13
Skype is a little hit and miss for me. It usually works, but sometimes it doesn't.

---

