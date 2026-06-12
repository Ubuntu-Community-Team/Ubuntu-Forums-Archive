---
title: "Hibernation in PanP7, Maverick 64 bit"
date: 2011-02-25
forum: System76 Support
---

### Post by Tank Jr on 2011-02-25
Hi,
I notice that I am unable to hibernate on my laptop. It is a Pangolin Performance 7, and running Maverick 64 bit. I do have more than double my RAM as swap space.
When I tell it to hibernate, it goes down as it should, but instead of powering off completely it immediately turns back on ( stating something like 'waking up' at the System76 splash screen). 
Any help would be appreciated.
Thanks

---

### Post by ZeroAdam on 2011-02-25
I'll have to test this on mine as well. I haven't done hibernate as you described, only sleep, as I close my laptop lid and leave it for a period of time and it wakes up just fine. I brought it with me to work today so I'll give it a try here shortly!

---

### Post by ZeroAdam on 2011-02-25
Ok, first test. I powered up my panp7, without external power, let it sit for a few minutes and then clicked for hibernate. It went to a black screen with a blinking cursor for a few seconds, then gave me 3 strange messages about "irq 17: nobody cared" and then powered off completely.

I'm getting ready to press the power button to bring it back up.

---

### Post by scarey9 on 2011-02-25
I just tested and had the same issue. The cursor blinks for a few seconds then the computer restarts. i get no error messages or anything.

---

### Post by scarey9 on 2011-02-28
bump....anybody?

---

### Post by peterfernandes1 on 2011-03-01
it goes down as it should, but instead of powering off completely it  immediately turns back on ( stating something like 'waking up' at the  System76 splash screen).
----------
Peter

---

### Post by Tank Jr on 2011-03-01
bump

---

### Post by Tank Jr on 2011-03-02
Any ideas anyone?
Any one from System76 ?
Thanks in advance.

---

### Post by isantop on 2011-03-02
Sorry for the slow responses. We're short-staffed this week, and things are moving a little slower than usual.

What happens if you try to suspend?

---

### Post by Tank Jr on 2011-03-02
I tried suspend, and the screen went blank,and the laptop looked like it powered off; pressing keys did not bring it back up. Pressing the power button brought it back to the same state as before suspend.
And yes, while the machine was powered off, the leftmost light at the fron of the machine (power indicator, I believe) was flashing slowly. I suppose suspend works, for this is a close analogy of what suspend looks like on my other computer.

---

### Post by isantop on 2011-03-02
Yep, sounds like a perfect suspend to me.

Next step is to look at swap space. Go to System > Administration > System Monitor. Then, open the resources tab and press Alt+PrtSc to take a screen shot. Post that here, and I'll make sure you have enough Swap space available.

---

### Post by Tank Jr on 2011-03-02
Here is the screenshot.

---

### Post by Tank Jr on 2011-03-04
Any ideas? I would really like the computer to hibernate.

---

### Post by isantop on 2011-03-04
Let's try and rule out a hardware or BIOS issue. Please boot into an Ubuntu LiveCD, and try to hibernate from there. It should work; if not, then the issue is in the hardware or BIOS.

---

### Post by Tank Jr on 2011-03-04
> **isantop said:**
> Let's try and rule out a hardware or BIOS issue. Please boot into an Ubuntu LiveCD, and try to hibernate from there. It should work; if not, then the issue is in the hardware or BIOS.

Nope, does not work. It gets stuck at the blinking cursor.
I have a Dell desktop (came with Ubuntu 8.04) on which Karmic wouldn't hibernate. But on Hardy, Lucid and Maverick hibernation worked fine. I suppose there is a chance that Natty might fix hibernation on the panp7, though I wouldn't hold my breath.

---

### Post by isantop on 2011-03-07
You get a blinking cursor when booting the LiveCD? That would indicate a bad CD, so you might want to consider re-downloading and re-burning at the slowest speed possible, to help rule out disk corruption.

---

### Post by Tank Jr on 2011-03-07
> **isantop said:**
> You get a blinking cursor when booting the LiveCD? That would indicate a bad CD, so you might want to consider re-downloading and re-burning at the slowest speed possible, to help rule out disk corruption.
It's actually a blinking cursor when I try to hibernate. The CD should be fine, I think--I installed the OS from it, and everything else works perfectly.

---

### Post by Tank Jr on 2011-03-09
Any ideas?
Is there log files that I could send to system76 people?

---

### Post by isantop on 2011-03-10
That's not a bad idea. Let's continue this in email. support...at...system76...dot...com.

---

