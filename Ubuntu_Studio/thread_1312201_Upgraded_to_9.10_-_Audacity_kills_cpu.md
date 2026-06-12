---
title: "Upgraded to 9.10 - Audacity kills cpu"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by Lupurus on 2009-11-02
Hello,

I've been using Audacity in 9.04 for a while with no problems, but now in 9.10, pressing the record button causes my cpu to go to 100%. Any ideas?

While we're at it, I can't get Ubuntu (any version) to recognize my mic when I plug it into the front of my computer. Ubuntu insists on using my crappy internal mic.

I'm pretty Ubuntu-illiterate, so I'm afraid I don't know what pieces of information would be helpful to you.

Thanks!

---

### Post by Lupurus on 2009-11-04
If there's a better place to ask about this, let me know : )

---

### Post by kayosiii on 2009-11-04
Pulse Audio would be high on the list of usual suspects for heavy cpu usage.

As for the microphone settings - that should be in the mixer settings somewhere... If for some reason the settings are not in the mixer or can't be added to the mixer. There is a package called amixer which generally gives you access to all the hardware settings of your soundcard.

Hope that helps.

---

### Post by Lupurus on 2009-11-04
Thanks!

So would you recommend trying to get in and sort out what Pulse Audio is doing wrong, or switch to a viable alternative?

---

### Post by mgouin on 2010-11-22
Hi, were you able to find the solution? I have the same issue, but using ubuntu 10.04.  Thanks,
Mathieu

---

