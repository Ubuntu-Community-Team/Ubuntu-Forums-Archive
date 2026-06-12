---
title: "Asus K43E screen brightness problem"
date: 2012-04-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-04-27
I have noticed that when my laptop screen is dimmed and I do anything, like press a key or touch the touchpad, screen brightness go to eye-burning maximum level. I have to use keyboard brightness keys to bring it back to usable brightness levels. Then it dims again after a while of inactivity and max again as I touch it, it's a tedious cycle.

g-c-c / "Brightness and Lock" / "Brightness" Slider is set to Minimum and "Dim screen to save power" is checked.

I'd like it to dim between 0% and 50% more or less.

I know I had this bug with a Dell laptop on Oneiric but am not sure about Asus K43E during this cycle, haven't really noticed as far as I remember. Seems like similar reports for other hardware were considered fixed in PP cycle. This is a fresh install of PP, now QQ lol.

Does anyone knows if this is normal and/or if there's a workaround? 

Thanks,
Effenberg

---

### Post by cromat on 2012-04-27
Is the auto adjust brightness option enabled? I have an Asus Zenbook I run 12.04 on and every reboot I need to turn down the brightness as my settings are not saved no matter where I adjust it from however, the option to auto-dim screen does save for me. Is this the behavior your describing?

---

### Post by effenberg0x0 on 2012-04-27
> **cromat said:**
> Is the auto adjust brightness option enabled? I have an Asus Zenbook I run 12.04 on and every reboot I need to turn down the brightness as my settings are not saved no matter where I adjust it from however, the option to auto-dim screen does save for me. Is this the behavior your describing?

Hi,
I'm not sure I have the "Auto-Adjust Brightness" option. See my settings in the screenshot below:
[ATTACH]216682[/ATTACH]
The slider always goes back to maximum when I use the laptop after it has dimmed.

Regards,
Effenberg

---

### Post by cromat on 2012-04-27
Sorry its the "Dim Screen to Save Power".

"The slider always goes back to maximum when I use the laptop after it has dimmed."

That is the same behavior I have, no matter where I adjust it after restart it always returns to max brightness. However, I think if you turn off the "Dim .... " it will stop the auto-adjustment at least it does for me. I always turn the brightness to the lowest level to save battery and my eyes. :p

---

### Post by effenberg0x0 on 2012-04-27
> **cromat said:**
> Sorry its the "Dim Screen to Save Power".

"The slider always goes back to maximum when I use the laptop after it has dimmed."

That is the same behavior I have, no matter where I adjust it after restart it always returns to max brightness. However, I think if you turn off the "Dim .... " it will stop the auto-adjustment at least it does for me. I always turn the brightness to the lowest level to save battery and my eyes. :p

You're right, if I set the brightness to any low level and uncheck "Dim screen to save power", brightness stays always at this level. Not the best solution, but makes the laptop more usable.

I really thought this was fixed during OO cycle.

Regards,
Effenberg

---

### Post by cromat on 2012-04-27
I don't know if it was fixed or not. I have always had this problem on the Zenbook since I bought it. Maybe this should be reported as a defect.

---

### Post by effenberg0x0 on 2012-04-27
I just did a quick search. There are many Launchpad bug reports about this issue on Asus and other Laptop brands. In fact many reports are from 2010/2011. I'll have to search and read each one with more attention to see if it's necessary to start another report. Looks like many of them could be triaged as dups actually.

Regards,
Effenberg

---

### Post by cromat on 2012-04-27
Yikes, well good luck with that. I can probably help out looking through the bugs. Anyway atleast the work-around is sufficient for now.

---

### Post by jerrylamos on 2012-04-27
> **cromat said:**
> Yikes, well good luck with that. I can probably help out looking through the bugs. Anyway atleast the work-around is sufficient for now.
Yeah, I've got the ultimate fix, a 1280x1024 flat screen 2nd display.

Ubuntu invariably boots on my Acer Aspire 5253 notebook on FULL BRIGHT SHOUT!  THEN I HAVE TO USE SOFTWARE SETTINGS to put it back to tolerable, about 30%.  Every time.  In development testing with multiple partitions I boot a lot.  Yes I submitted a bug.  No interest from ubuntu development.

The 1280x1024 flat screen has its own manual settings which it remembers every time, thank you.  On ubuntu pangolin/quetzal boot the Acer behind on the table flashes brightly then goes off.

Jerry

---

### Post by ventrical on 2012-04-28
I have none of these probs with my Acer Apsire 3620, Dell Inspiron B130  or Acer Extensa 4420.

 I'll double check..

---

### Post by ventrical on 2012-04-28
That tool is absolutely useless on my Dell B130.

  I can only dim using the keyboard F keys.

---

