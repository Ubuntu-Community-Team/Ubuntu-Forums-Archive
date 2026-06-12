---
title: "problem with sound in Wine, but its just for one program?"
date: 2010-01-02
forum: Wine
---

### Post by ILuvMontyPython on 2010-01-02
I have Wine installed in ubuntu/Kubuntu Jaunty and I can play games like Roller Coaster Tycoon fine in it (it works great and has sound)

but when I try to use my disk for Ear training (which is an .exe file) I can view/use the program perfectly except there is no sound, the disk works in the school computers so I know its not faulty, but the sound just doesn't work in Wine.

 I changed the format in Wine to all the different Windows (Vista, XP, 2000, etc.) and the sound didn't work in them either, 

everything in Alsa mixer is turned up 100% and I've tested it with both my head phones and computer speakers, but theres never any sound. 

I am just stumped on what to try next. any ideas?

---

### Post by Soulcage on 2010-01-03
Did you try to change from alsa to oss inside of winecfg ?

---

### Post by ILuvMontyPython on 2010-01-03
yes, I tried all the options under winecfg for sound and tried the test sound, it just made a faded *bump* sound. my alsa mixer is turned up all the way and I can listen to music from rhythembox just fine.

---

### Post by beastrace91 on 2010-01-03
Try disabling pulse audio in your audio settings - this has a tendency to give Wine issues.

~Jeff

---

