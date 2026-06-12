---
title: "Pangolin Battery Power Mangement Tab Missing"
date: 2009-04-18
forum: System76 Support
---

### Post by bill516 on 2009-04-18
I do not ordinarily run on battery unless I need it, but I did so this morning and immediately noticed that System/Preferences/Power Management brings up the Power Management Preferences window, but with only the "General" and "On AC Power" tabs.  The "On Battery Power" tab is missing.

Is this a characteristic o 64 bit 8.10 Ubuntu?

Does this reflect a System 76 modification?

I believe I can use apt to reinstall the power management suite including the front end, but I do not want to do that if I am upsetting some larger apple cart in the process.

Any wisdom among the 76'ers?

---

### Post by Guille Damke on 2009-04-18
Hi, I think there is something wrong in your install. I have a Pangolin panp4n and it has the "On Battery Power" tab.

---

### Post by bill516 on 2009-04-18
> **Guille Damke said:**
> Hi, I think there is something wrong in your install. I have a Pangolin panp4n and it has the "On Battery Power" tab.

Thank you Guille.  That is what I suspect as well.  If we are right the fix should be a fairly simple reinstall.

---

### Post by bill516 on 2009-04-19
> **bill516 said:**
> Thank you Guille.  That is what I suspect as well.  If we are right the fix should be a fairly simple reinstall.

Well we may be wrong in our suspicions.  The Pangolin does not come with an Ubuntu system disk (or for that matter a System 76 driver disk) so I fired up my own 8.10 64 bit Live CD.  Interesting.  There is no tab on that CD for managing battery power utilization.  So the "install" may have been right.

Now I did larn that 64 bit Ubuntu does not include the settings manager or Compiz-Fusion, which I downloaded and installed (though I don't do much with it, truthfully).

Is Power Management another case of this?  It seems odd given the importance of managing power while using a battery.

I am going to be traveling for some time but Ill check in as I can and see if someone knows the answer.  As it stands it looks as though we have to download an application for battery power management.

---

### Post by thomasaaron on 2009-04-20
There must be a battery connected for the batter tab to appear. Please turn your computer off, remove the battery, let everything cool down to room temperature and reconnect your battery and start your machine.

If that doesn't fix it, resetting the cmos might. Email me for those instructions.

---

### Post by bill516 on 2009-04-22
As usual Thomas has it right.  I thought perhaps the tab might not appear unless the battery was in place.  I think I did not let the machine cool down sufficiently when I initially tried this test.  So, if you normally do not bother with the battery let the machine sit idle a few minutes before you restart and the tab will be there.

Thanks Thomas, much appreciated.

---

