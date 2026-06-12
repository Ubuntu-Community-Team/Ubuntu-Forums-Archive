---
title: "Displayed on boot:  &quot;broken pipe&quot; &quot;could not write bits&quot;"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by buzzingrobot on 2012-04-25
Running flgrx-update, via "Additional Drivers", with a Radeon 6870, I am seeing a split-second display of large white text on the purple background as the system boots.  The text contains this:  "broken pipe" "could not write bits".

When I reboot or shutdown, I see a screenful of the same large type against a purple background, this time displaying what appears to be a register dump.  The system locks at that point and I need to hit the power button.

These don't appear when I use the open driver for the Radeon card.

What is generating the messages? 

I'm trying both drivers in an attempt to get some more fan info and control. The GPU fans appears to be running at a constant speed at all times.  lm-sensors provides no info about fan speed. I don't need to run the proprietary driver but will if it gives me that info and control.

[EDIT:  Top says compiz consumes much less of the CPU with the open driver.  My ears tell me the fans rev up at  boot and stay there with the open driver, but slow down with the AMD driver.]

---

### Post by xyzzyman on 2012-04-25
I get the broken pipe error with the nvidia binary. I think it's happening but just hidden when you use the open-source AMD driver.

---

