---
title: "Bios Password"
date: 2007-06-19
forum: Server Platforms
---

### Post by Typeface on 2007-06-19
I recently stumbled upon a cheap secondhand PC, however when i came to install Linux i realised the Bois has been passworded and not knowing anyway to find it out i was wondering what my options where in finding it out.

---

### Post by 5-HT on 2007-06-19
> **Typeface said:**
> I recently stumbled upon a cheap secondhand PC, however when i came to install Linux i realised the Bois has been passworded and not knowing anyway to find it out i was wondering what my options where in finding it out.
Have you tried taking out the CMOS battery for a bit to reset the BIOS?

---

### Post by dfreer on 2007-06-19
yep, standard way to disable the BIOS password is by shutting the PC down, take out the CMOS battery, turn it back on, turn it back off, and put the battery back in. some older MoBo's include a jumper near the battery that does the exact same thing.

---

### Post by Typeface on 2007-06-20
Thanks for the advice, i didn't think it would be that simple.

---

### Post by matt_b on 2007-06-20
You may find there is a jumper on the mobo labelled [CMOS or CLEAR CMOS]("http://www.dansdata.com/images/133aboards/cmos360.jpg") - with the power off you can move this jumper to cover the other pins (2 and 3 instead of 1 and 2), leave for a few seconds then put it back to where it was. This should reset the BIOS, including password - you'll probably need to do a "load optimised defaults" once you boot it back up. Alternatively you may even find that there is a specific jumper just for resetting the password, as there is on my Intel server board.

matt_b

---

### Post by Tekovro on 2008-07-07
I have a laptop with the same issue but i can't open it, is there any other way to get the bios password? 

im running ubuntu on Samsung-P10C-Pentium-4- M

---

### Post by dfreer on 2008-07-07
Try removing the main rechargable battery from the laptop and unplug the power cord for a couple of hours.

---

