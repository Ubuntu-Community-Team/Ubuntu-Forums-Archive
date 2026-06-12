---
title: "Keyboard and Mouse buttons unresponsive (Gutsy)"
date: 2008-05-13
forum: System76 Support
---

### Post by elusivespoon on 2008-05-13
I'm having an occasional problem on my Daru2 where neither my keyboard, nor mouse buttons work. I am still able to use the touch-pad to move the mouse. This has mostly happened when coming out of Suspend mode, but has also happened once shortly after booting up. The interesting thing is it's not unusable immediately. I am always able unlock or login. The last time it happened I was able to start a couple applications, but when I tried to use them things were unusable again. A reboot fixes it.

---

### Post by thomasaaron on 2008-05-14
The next time it happens, please post the output of...
cat /var/log/syslog

I know you said you had a DarU2. I just want to confirm, as there was a freezing bug with the original Darter -- the DarU1 (the white one).

---

### Post by elusivespoon on 2008-05-14
It is definitely a DarU2. I just recently purchased it.

I've attached a syslog file from Monday night, May 12, when I know it happened. It happened around 8pm.
You can see in the file at 20:03:27 the computer comes out of sleep mode (though that's when it logs the messages for entering sleep mode for some reason).
Then at 20:04:15 you can see I press the power button (and held it for a hard shut down). Then the next message is the restart message. So hopefully there is something useful in all that.

---

