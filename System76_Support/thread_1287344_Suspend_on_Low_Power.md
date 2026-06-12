---
title: "Suspend on Low Power"
date: 2009-10-10
forum: System76 Support
---

### Post by Temposs on 2009-10-10
I've got a Darter Ultra.

I have my power management set to suspend when the power is critically low. However, all it does is shut off when it runs out of power.

Is there a way to fix this up?

---

### Post by thomasaaron on 2009-10-12
Go to System > Administration > System76 Driver and click the Install tab and the Install button. Then reboot.

Edit: Which Darter Ultra do you have? Are you running 64-bit Ubuntu?

---

### Post by Temposs on 2009-10-12
Ah, yeah, some of the specs are in my signature. And yes, I'm running 64-bit.

---

### Post by Temposs on 2009-10-12
I've run the driver installer, rebooted, and tested draining the battery. It gives a Battery Low notification, dims the screen automatically. But it also just shuts off once it gets low enough. 

I'm attaching a screenshot of my power management settings and the relevant setting in the Gconf editor.

This is the original install of Ubuntu 9.04 that came from the factory.

---

### Post by thomasaaron on 2009-10-12
Please go to the System76 Driver and tell me what it says for System Model. Then click the About button and tell me what version of the System76 Driver it reports.

---

### Post by Temposs on 2009-10-12
System model is daru3.

Driver version: 2.3.8

---

### Post by thomasaaron on 2009-10-12
Please go to planet76.com/repositories and download, install and run the 2.3.7 driver (it will be the second link from the bottom). Then reboot. Did that fix it.

You will notice the 2.3.8 driver is gone.

---

### Post by Temposs on 2009-10-12
Installing driver version 2.3.7 hasn't fixed the problem.

I'm attaching a screenshot showing the current System76 information you requested before.

---

### Post by PrePenguin on 2009-10-12
You have told the computer what to do in low battery scenarios? Correct in your settings?

---

### Post by Temposs on 2009-10-12
Yes. See the previous posts.

---

### Post by thomasaaron on 2009-10-13
One final question: does it suspend and resume correctly if you manually suspend it?

I'm imaging a darter now for testing.

---

### Post by Temposs on 2009-10-13
Suspend works perfectly when I manually initiate it, either by closing the lid or using the Fn+F4 shortcut or Ubuntu's session menu.

---

### Post by thomasaaron on 2009-10-14
OK. I've got a Darter imaged. Letting the battery drain and will report back.

---

### Post by thomasaaron on 2009-10-14
Alright, I have the same problem.

There is some sort of power management issue with the Darter, and this seems to be one of the side-effects of it.

There is a fix for it (I think), but it involves re-compiling the kernel, which is a bit beyond the scope of what we do. But, I've also heard that the fix should be applied in Karmic (although I know it's not fixed in Karmic YET). 

Please bump this if the problem isn't fixed with the stable release of Karmic on 10/29. If it's not, we'll dig deeper.

---

### Post by mcallenSchmee on 2009-10-17
When on suspend the computer still requires power. I think what you want it to do is Hibernate.

---

### Post by Temposs on 2009-10-17
> **mcallenSchmee said:**
> When on suspend the computer still requires power. I think what you want it to do is Hibernate.

Regardless, it should still be able to go into suspend when it gets to a low power level, and it doesn't.

---

### Post by HotShotDJ on 2009-10-18
If you're having the same problem as I have with the PanP5, the issue is that the gnome power manager is not calculating the time remaining.  This is actually a new bug in Karmic -- recompiling the kernel doesn't fix it like it did in Jaunty.

But, some good news for you... just change some settings using the configuration editor.  Open a terminal and type:```
gconf-editor
```Find apps -> gnome-power-manager -> general

Now, uncheck "use_time_for_policy"

Next, find apps -> gnome-power-manager -> thresholds.  I recommend setting "percentage_low" to 10%, "percentage_critical" to 6%, and "percentage_action" to 5%.

Now you can safely exit out of the configuration editor.  Log out then log back in (you don't need a full reboot).  If you have multiple users on your computer, you'll need to make the above adjustments in each account.

I hope this helps get you through until they get things sorted in Ubuntu-land. :)

---

