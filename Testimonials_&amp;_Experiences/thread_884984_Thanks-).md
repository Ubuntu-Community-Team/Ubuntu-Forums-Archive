---
title: "Thanks:-)"
date: 2008-08-09
forum: Testimonials &amp; Experiences
---

### Post by 6mil928 on 2008-08-09
I just wanted to leave a quick post to all those that contributed to and continue to contribute to Ubuntu.  I've used Ubuntu off and on since 6 and must say Ubuntu 8 is excellent. Thanks for all the hard work to make this happen.  With 8 I'm very close to dumping "MS" for good.  Well done:)

Moderator if this is in the wrong forum I apologize.  Please move it as you see fit.;-)

---

### Post by p_quarles on 2008-08-09
Moved to Testimonials & Experiences. :)

---

### Post by 6mil928 on 2008-08-09
Thanks p_quarles.

---

### Post by tamoneya on 2008-08-09
> **6mil928 said:**
> I just wanted to leave a quick post to all those that contributed to and continue to contribute to Ubuntu.  I've used Ubuntu off and on since 6 and must say Ubuntu 8 is excellent. Thanks for all the hard work to make this happen.  With 8 I'm very close to dumping "MS" for good.  Well done:)

Moderator if this is in the wrong forum I apologize.  Please move it as you see fit.;-)

What are your current blockers for dumping microsoft.  maybe we can solve them.

---

### Post by 6mil928 on 2008-08-09
> **tamoneya said:**
> What are your current blockers for dumping microsoft.  maybe we can solve them.


No major issues as of yet only thing that's bugging me is the sound quality of my Audigy XFI card but that's not a deal breaker. Using Wine has also made windows less mandatory.  Oh yea and my sound is always back to full blast when I reboot.  Scares the C*** out of me if I forget to turn my speakers off.  These are small things that I'll work out in a bit but for now I'm loving it:)

---

### Post by p_quarles on 2008-08-09
> **6mil928 said:**
> Oh yea and my sound is always back to full blast when I reboot.  Scares the C*** out of me if I forget to turn my speakers off.
It's possible that this problem can be fixed by running:
```
sudo alsactl store
```
when you have the volume at the level you want it. This presumes that you are using ALSA (and not Pulseaudio) and that ALSA is working correctly. Worth a try.

---

### Post by 6mil928 on 2008-08-09
> **p_quarles said:**
> It's possible that this problem can be fixed by running:
```
sudo alsactl store
```
when you have the volume at the level you want it. This presumes that you are using ALSA (and not Pulseaudio) and that ALSA is working correctly. Worth a try.

Tried it got this

sudo: unable to resolve host jason-ubuntu8

Any ideas?  Thanks for the help:)

---

### Post by p_quarles on 2008-08-09
> **6mil928 said:**
> Tried it got this

sudo: unable to resolve host jason-ubuntu8

Any ideas?  Thanks for the help:)
Oh, yeah, that's another (and completely unrelated) known bug. To fix it, you need to make sure that /etc/hosts and /etc/hostname share the same name for the local computer. 

This is simple to fix, but requires rebooting into the "recovery"/system maintenance mode from the GRUB boot menu (right after the BIOS during startup).
1) Select "recovery mode" from the boot menu
2) When it loads, type the following two commands:
```
cat /etc/hosts
```
and 
```
cat /etc/hostname
```
This will display the contents of these two files. The second line of the first file needs to match the content of the second file, and probably doesn't right now. To fix,
3) ```
nano /etc/hosts
```
This will open the file /etc/hosts for editing. Replace the incorrect information in line 2 (should say something like "jason-ubuntu8") with whatever was in /etc/hostname. Leave the IP address (127.0.1.1) intact.
4) After you've made the edit and saved the file, type
```
reboot
```
to restart your computer. You will now be able to use "sudo" to perform root operations.

---

### Post by 6mil928 on 2008-08-09
Thank you.  I will do that when I get back to the computer and reboot.

---

