---
title: "System76 driver question"
date: 2007-12-16
forum: System76 Support
---

### Post by Rasputin_III on 2007-12-16
Does the system76 driver work on amd64 installations?

(I guess one line is enough sometimes)

---

### Post by asmiller-ke6seh on 2007-12-17
The System 76 is not designed for 64-bit Ubuntu. (I read this in another posting, the reply from thomasaaron of System 76.)

---

### Post by thomasaaron on 2007-12-17
The System 76 driver will RUN on 64-bit Ubuntu.
That said, I do not know how functional it will actually be. I suspect it will work
fine, but we've never done any testing with 64-bit.

---

### Post by asmiller-ke6seh on 2007-12-17
Then it is a fair statement that it was not DESIGNED for the 64-bit Ubuntu - right? Not that it won't work; if it has not been tested, then it probably was not designed for that system, because if it had been tested, and had there been need for design changes, and they had been worked into the driver, then it would be safe to say that it HAD been designed for the 64-bit Ubuntu.

---

### Post by thomasaaron on 2007-12-17
:lolflag: That is absolutely a correct statement. It was not DESIGNED for 64-bit.

And yet...

Rasputin_III:
> Does the system76 driver work on amd64 installations?

---

### Post by steveneddy on 2007-12-17
I have 64 bit installed on my system and I feel a small need for the System76 driver, whether it does any good or not.

FYI - after a clean install recently, everything worked without the driver installed, so do I need it?

I dunno.:-k

---

### Post by thomasaaron on 2007-12-17
That's like asking if you need your little toe.
Not really. But to you REALLY want to part with it?   :guitar:

---

### Post by asmiller-ke6seh on 2007-12-18
What does it mean for a driver to WORK in a system?

If your system operates and is fully functional WITHOUT applying the System 76 driver, and if running the System 76 driver does not (apparently) make any changes, what work was done? does it do any work?

If I have a baseball cap that keeps my head warm, and if someone takes the cap off my head and places an identical cap on my head, what's the difference? Does the new cap work? Yes. Did the old cap work? I guess so. Did I need to replace the other cap with an identical cap? :confused: Probably not? But then again, do I know the difference? Not if I wasn't awake when the caps were switched.

:lolflag:

---

### Post by Rasputin_III on 2007-12-18
With the 64-bit (as well as 32-bit) stock installation of Gutsy, sound didn't work on my Serval.  It had to do with the lack of alsa support for that specific chipset (or revision).  As near as I can tell, installation of the system76 drivers downloads an alternate package for that module from a more recent cvs release or downloads and builds some of the source for that module (made available from system76 servers).
I think it changed some mixer settings (as well as other tweaks unrelated to sound).

I believe (it's been a few weeks and I'm senile) that I had successfully installed the driver .deb file from within the amd64 livecd--so it didn't choke on architecture dependencies; but obviously the requisite reboot would be silly for a live-cd environment.

I plan on (eventually) running 64-bit ubuntu on this, and I was curious if the canned-tweak-scripts would work on it or if it'd be something I had to do myself manually.

Thanks to everyone for the replies,

Ras

---

