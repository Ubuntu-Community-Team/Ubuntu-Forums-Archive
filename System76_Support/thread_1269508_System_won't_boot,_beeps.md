---
title: "System won't boot, beeps"
date: 2009-09-18
forum: System76 Support
---

### Post by awoade on 2009-09-18
Hi, this problem just began yesterday evening. I turned off my 76 (and I didn't watch it, assumed it would turn off okay) and when I tried to turn it on again, it was giving me consistent beeping after the kubuntu screen loaded.

I checked the BIOS and I don't see anything weird, and the computer was fine when I was just looking at the settings, but once I went to get into the operating system it just. keeps. beeping.

Oh, until it just shuts down.

HELP!

(It did complain about the graphics right before it stopped working, but it's done that before and been fine.)

---

### Post by thomasaaron on 2009-09-18
What System76 model do you have?

Sounds like it could be a memory problem. You might want to make sure your memory cards are well-seated. If the machine took a bump, it good have jarred them loose.

Also, try to run memtest86 from a live Ubuntu CD.

---

### Post by awoade on 2009-09-18
It's a Pangolin Performance (model: panp4n).  I'll check the memory, thanks.

---

### Post by awoade on 2009-09-21
Okay, so I did a memtest and it beeped and shut down partway through.  (I just got home from a vacation, that's the only reason this reply has taken so long.)  I don't think the memory is out of place as I opened the machine and it seemed pretty sturdy in there, but it must be busted because I did a disk check and booted from CD and that was all fine.

The only thing I'm nervous about now is: A) do I have to go out and buy myself new memory or is this covered? I bought the machine less than a year ago.

B) When I was in the boot from the live CD, I looked at some files (not many) and they said they were unreadable.  Will this continue to be a problem when I'm not on live CD?

Thanks again for all your help!

---

### Post by satsujinka on 2009-09-21
I can't answer A, but I can give a bit of help on B.

Since the live cd logs in as a user that is not you, it can't access your files unless you move up to root (sudo.) This is probably your issue, and thus there won't be any problems once you do manage to boot from the disk. A way to check; 
1. boot the live cd
2. open konsole
3. type "sudo dolphin" (maybe kdesudo, I don't use kde so the exact command to open something as root escapes me)
4. from root mode dolphin try to access the file in question
5. if it works then there's no problem, if it doesn't work post pack that it didn't work

---

### Post by thomasaaron on 2009-09-22
Did memtest86 throw any errors before it shut down?

Do you notice whether or not your fan is running? (This kind of sounds like it might be overheating.)

Is it very dusty inside the machine? Or is the cooling fan clogged by a dust bunny?

If you're within your warranty period, it'll be covered by warranty as long as the problem isn't determined to be user-inflicted damage.

Shoot me an email if you want us to bring it in and have a look. It is really sounding to me like hardware.

---

### Post by awoade on 2009-09-22
It's not dusty, the fan does run, and I didn't notice any errors coming up, but I'll run memtest86 again and watch.  I think it just began to beep and shut down without any visual warning, as it was generally doing.

---

### Post by thomasaaron on 2009-09-22
The next time it turns off, turn it immediately back on and go straight to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

---

### Post by awoade on 2009-09-22
There was a dustbunny in there, actually, and now the memtest is running fine.  It's only at 16%, but it wasn't even getting that far previously.  Maybe it was a fan/dust issue, though I was pretty certain the fan was working.  I'll update this when/if the memtest finishes/crashes out.

ETA: The memtest worked out fine, the disks were checked and worked out fine.  My desktop layout information all disappeared, but all my data appears to be fine.  Fan is definitely running (I looked at it while the computer was on, it was spinning), so I guess it was just a dust bunny.  Boy, do I feel silly.

---

### Post by thomasaaron on 2009-09-23
You've got to watch those dust bunnies. As cute and cuddly as they are...:lolflag:

---

### Post by dsipma on 2011-02-01
Got my lemur ultra thin (less than 6 months old) into this problem.  Some simple blowing got it right back up and running.  Thank you for saving me a ton of time.

---

### Post by isantop on 2011-02-02
We're glad to be of service! Let us know if there are any other problems you have.

---

### Post by pablomme on 2011-10-18
Got hit by this problem too on a lemu2 - dust in the fan as well. Funny, it's the first time I get this on any of the laptops I've had.

---

