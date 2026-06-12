---
title: "Confessional:  &quot;How I Got My Mic To Work, Made Friends &amp; Convinced People&quot;"
date: 2007-05-07
forum: Testimonials &amp; Experiences
---

### Post by Blofeld on 2007-05-07
Hi, I'm using Xubuntu 7.04 on a PIII-800 with 256 MB and 30 + 10 GB HDDs, with onboard Intel sound.
In 6.10 I couldn't get my mic to work, which was very annoying as it meant I couldn't VoIP.  After I installed 7.10 it did work, then I installed Ekiga Softfon, it still worked, but then the next day it STOPPED working.
I was deflated flabberghasted, despondent.  Messing with mixer didn't do any good.
So here is the solution I found:

To the file ...
*/etc/modprobe.d/alsa-base*
... append the line ...
*options snd-hda-intel model=ref*
... and reboot.

Best of luck to you!
:guitar:

---

### Post by wPwLUi3N on 2008-04-04
Thanks for sharing.

It will surely going to be very helpfull to newbies.

---

