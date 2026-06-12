---
title: "Hard Drive Spinning"
date: 2009-12-01
forum: Server Platforms
---

### Post by JumpForJoy on 2009-12-01
Hey,
The hard drive on my Ubuntu server doesn't stop spinning.  I as long as its on, my computer makes this horridness sound.  To me, it sounds like my hard drive spinning, but it could also be the fan (it's an old computer).  Is there any commands I can use, to test wether or not my hard drive is spinning? or what my computer's internal temperature is (or at least if the fan is spinning, because I doubt my computer has a thermostat inside)?  And if it is my hard drive spinning, is there any way I can force it to spin down after a certain time on inactivity?  Any help/advice would be greatly appreciated.

Thanks,
JumpForJoy

**Edit:** Also, I have mounted another hard drive to my computer, which is the one that I suspect is spinning non-stop.  There is a great chance that I mounted it wrong, but I can't remember how I mounted it.  I don't often read/write to this hard drive, so it puzzles me why it doesn't stop spinning.

Thanks,
Jump For Joy

**Edit:** I just ran "sudo hdparm -S 2 /dev/sdb" and "sudo hdparm -S 2 /dev/sda", but only sdb idles, sda keeps spenning (according to sudo hdparm -C /dev/sda)

Thanks,
Jump For Joy

---

### Post by Vegan on 2009-12-01
You could try badblocks which tests disks for errors.

read the man page if you want to see how to use it.

---

### Post by munky99999 on 2009-12-02
Have you recently installed some heavier software on the computer? That the computer simply cant handle. You thusly are tossing data into the swap space. Which keeps in spinning.

If you happen to have gui + 9.1 karmic running. There is Disk Utility in the system -admin area which can do SMART testing on the drive and give a little report on it. It might be dying.

---

### Post by JumpForJoy on 2009-12-02
> **munky99999 said:**
> Have you recently installed some heavier software on the computer? That the computer simply cant handle. You thusly are tossing data into the swap space. Which keeps in spinning.

If you happen to have gui + 9.1 karmic running. There is Disk Utility in the system -admin area which can do SMART testing on the drive and give a little report on it. It might be dying.

No, I haven't recently installed any heavy software, it has been making this sound sense I first installed ubuntu server on it.  I also don't have gui installed on it.  And I don't think its a bad block, it just doesn't spin down.

Thanks
JumpForJoy

---

### Post by munky99999 on 2009-12-02
how much ram does the system have?

also. suggest getting an ubuntu-desktop livecd in order to check out the disk utilities.

---

### Post by JumpForJoy on 2009-12-02
I don't have much ram, and I will look at into the disk utilities with my live cd, thanks for the idea.

Thanks
JumpForJoy

---

