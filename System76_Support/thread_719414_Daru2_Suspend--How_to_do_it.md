---
title: "Daru2 Suspend--How to do it?"
date: 2008-03-09
forum: System76 Support
---

### Post by reh4c on 2008-03-09
I'm using Hardy Alpha 6 on my Daru2.  The brightness changing bug appears to be fixed, but the battery indicator is still inaccurate.  Anyway, my real question involves suspend to RAM.  The laptop appears to suspend with power and battery indicator flashing.  However, when I press the power button (is that right?), the laptop turns on for a second or two an then completely shuts off.  Any other users having this problem?  Am I doing something wrong?  Thanks.

---

### Post by lswest on 2008-03-09
usually to wake up from suspend you move the mouse (or touchpad), open the screen, or hit a key on the keyboard.  Don't know about your specific model laptop, but try those 3 options first, it may be that you turn the laptop on, then turn it off when you press the power button.  Usually you only need to press the power button to wake up from hibernate, as hibernate stores information on the hard drive, then shuts off the computer completely, which is why it is slightly slower than suspend, but uses less power.

---

### Post by gaussian on 2008-03-09
> **reh4c said:**
> I'm using Hardy Alpha 6 on my Daru2.  The brightness changing bug appears to be fixed, but the battery indicator is still inaccurate.  Anyway, my real question involves suspend to RAM.  The laptop appears to suspend with power and battery indicator flashing.  However, when I press the power button (is that right?), the laptop turns on for a second or two an then completely shuts off.  Any other users having this problem?  Am I doing something wrong?  Thanks.

Sounds like what DARU2 does when trying to suspend to RAM under (based on my experience): 32/64-bit Feisty and 32-bit Gutsy. Under 64-bit Gutsy it wakes up perfectly after you press the power button. Are you using 32 or 64-bit Hardy?

---

### Post by reh4c on 2008-03-09
I'm using 64-bit Hardy.  I tried clicking the trackpad button and pressing a key, but nothing happens to come out of suspend.

---

### Post by maartenlameris on 2008-03-10
Have u tried this?

[https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")

to debug the problem?

---

### Post by thomasaaron on 2008-03-10
On the DarU2, you have to press the power button to resume from suspend.
If you are using 64-bit Ubuntu, suspend should work fine.

That said, we've not gotten that far with Hardy yet. Testing is in process, but we will not start providing support for it until it is released in April.

---

### Post by reh4c on 2008-03-10
Thanks for the follow-up.  I'm a bit concerned with this portion of the debug instructions:

[B]Caveat Emptor: Using the following debug suggestions will radically change the values in your RTC chip, so much so that your file system will think it has been eons since the last fsck. You can avoid a long fsck delay by using 'tune2fs'. For example, 'tune2fs -i 0 /dev/sda1' disables fsck on boot. 

Q: What value does one set this back to at the end? tune2fs doesn't seem to have a "list current parameters" option -- Gerv 

A: I believe if you use 'tune2fs -l <device>' it will give you the current information of your settings. It might be a good idea to capture this information first before making any changes so you know how to restore things back to their original state. 

From a fresh Hardy install, the default time interval is 15552000, which is 6 months. 

NTP is not sufficient to recover the correct time of day. By default NTP is configured to to only correct for about an hour drift. You must use the 'date' command to get the RTC value within the drift tolerance. [/B]

Are there any dangers to performing this?  I'll probably just wait for Hardy support, but I'm willing to help test/report findings if it can be done safely.

---

### Post by thomasaaron on 2008-03-11
You do not need those instructions to suspend with the DarU2. Just install 64-bit, add ec_intr=0 as a kernel option and suspend.

---

