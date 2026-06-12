---
title: "No Nvidia HDMI audio option in Ubuntu 14.04 LTS"
date: 2014-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by jason78 on 2014-04-17
Just installed 14.04 LTS and really like but the only issue I have so far, is, my laptop doesn't have the option to choose the nvidia hdmi audio output when switching to nvidia graphics mode. This is important as I use an external monitor all the time. I have searched this for hours and haven't found a solution. I am using the recommended nvidia driver currently, or 331.38.

I've read it could be a bug with the current kernel? Do I need to dowgrade to a previous kernel, and if so, which one, and how to go about it?

The OS isn't going to be usable to a lot of people I think without audio over hdmi, so there must be a solution out there.

---

### Post by EmpireITtech on 2014-04-18
I had the same issue on 13.10 with my AMD....very annoying. Once I get home I'll be testing this with 14.04.
I've had success with Linux Mint sending audio over HDMI, but never Ubuntu....which is weird lol

---

### Post by gstanden on 2014-05-01
Same problem.  It was working on 13.10 for me, but 14.04 upgrade broke it.  HDMI option does not appear at all in the sound panel now. Searching for a solution.

---

### Post by Eggnog on 2014-05-01
When I installed 14.04, I just added the parts in grub between the quotes for AMD HDMI with my 6850.  It's working fine for me.  Your mileage may vary.

GRUB_CMDLINE_LINUX="radeon.audio=1"

---

