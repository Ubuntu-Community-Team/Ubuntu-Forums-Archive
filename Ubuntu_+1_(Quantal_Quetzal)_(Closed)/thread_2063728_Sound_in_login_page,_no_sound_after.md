---
title: "Sound in login page, no sound after"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kripkenstein on 2012-09-27
I have 12.10 installed on a Thinkpad x230. It works great except for sound. I do have sound in the login page, but after I log in and get to the desktop, everything is perfectly silent.

I went through all the guides, nothing is muted, alsamixer looks ok in the console etc, but no sound plays and no errors are reported that I can see. I tried restarting pulseaudio and alsa but no change. Rebooting doesn't help either.

Is anyone else seeing this? Anything I can try to fix this?

---

### Post by Bazon on 2012-09-28
For me, installing the kernel linked [there]("https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1052499/comments/15") helped.

As this kernel is older than the most recent one, you have to install it via command line. e.g. by running
sudo dpkg -i *.deb
in the directory you downloaded kernel+header+extras.

But I don't have a thinkpad, so I don't know whether your hardware also works with that.

---

### Post by philinux on 2012-09-28
> **kripkenstein said:**
> I have 12.10 installed on a Thinkpad x230. It works great except for sound. I do have sound in the login page, but after I log in and get to the desktop, everything is perfectly silent.

I went through all the guides, nothing is muted, alsamixer looks ok in the console etc, but no sound plays and no errors are reported that I can see. I tried restarting pulseaudio and alsa but no change. Rebooting doesn't help either.

Is anyone else seeing this? Anything I can try to fix this?

Create a new user or use the guest user and log in with it. See if you got sound then.

---

### Post by kripkenstein on 2012-10-01
Thanks for the tips.

I did some more testing, including with a new account. It seems like sometimes when I boot I don't get sound, but sometimes I do (both with a new account and an old one) Also, it seems like i often lose sound when I suspect and resume.

Is there some way to completely reset sound in a session? So I don't need to reboot several times until it works?

---

### Post by pqwoerituytrueiwoq on 2012-10-01
to reset a users sound:
[FONT=Courier New]rm -rf .pulse[/FONT]
logout
login

---

### Post by kripkenstein on 2012-10-02
> **pqwoerituytrueiwoq said:**
> to reset a users sound:
[FONT=Courier New]rm -rf .pulse[/FONT]
logout
login

Thanks pqwoerituytrueiwoq, I'll try that next time the problem happens.

---

### Post by kripkenstein on 2012-10-04
Doesn't seem to help. The only thing that helps is a complete shutdown (not even restart or logout).

---

### Post by pqwoerituytrueiwoq on 2012-10-04
maybe alsa is crashing, or it is acting like my NIC on my desktop (stops working till i cut power)
[FONT=Courier New]alsa reload[/FONT] might do it (may need sudo)
edit:
if it happens when you suspend you may need to restart alsa after it wakes up, and if there is a error from the command hopefully it will help

---

### Post by kripkenstein on 2012-10-15
> **pqwoerituytrueiwoq said:**
> maybe alsa is crashing, or it is acting like my NIC on my desktop (stops working till i cut power)


Maybe this is a NIC issue somehow. Turns out the headphone always works, it's just the builtin speakers and don't (until I power down/power up). I don't have any idea how to tell if this is a hardware problem or not. But headphones working is good enough for me.

---

