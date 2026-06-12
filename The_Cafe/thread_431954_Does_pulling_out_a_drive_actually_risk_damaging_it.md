---
title: "Does pulling out a drive actually risk damaging it?"
date: 2007-05-03
forum: The Cafe
---

### Post by ThinkBuntu on 2007-05-03
I used a thumb drive for about a year in school on strictly Windows machines and always just yanked it out (I hate how long it takes to "Safely Remove Hardware"), and although the computer flashed a warning, I never lost any data. This included migrating data between a Mac, a Linux and many PCs. Now I'm a little more careful because I have a theory that maybe some data recently added is written to the drive on eject. But even so...does yanking a drive out actually do anything wrong?

---

### Post by gerscht on 2007-05-03
Although I most of the time do the same :)  modern OS try to be as efficient as possible and wait for a bunch of data to be written. If you yank it then, the files won't be written. This is mostly likely the case if you're writing many small files to the drive.... Writing just one big file and pulling it out as soon as the copy window disapears shouldn't do any harm

---

### Post by use a name on 2007-05-03
It might. I've seen writes being postponed as long as possible, even until after I 'ejected' it. Didn't work...

---

### Post by ThinkBuntu on 2007-05-03
I don't want to turn this into a question post, because I intended it as a curiosity one (hence the location), but I wonder if there's a way to make your system take care of the writes immediately...?

---

### Post by lcg on 2007-05-03
> **ThinkBuntu said:**
> I used a thumb drive for about a year in school on strictly Windows machines and always just yanked it out (I hate how long it takes to "Safely Remove Hardware"), and although the computer flashed a warning, I never lost any data. This included migrating data between a Mac, a Linux and many PCs. Now I'm a little more careful because I have a theory that maybe some data recently added is written to the drive on eject. But even so...does yanking a drive out actually do anything wrong?

Well, you cannot physically damage a USB storage device by simply unplugging it.

However, the file system on the device is a different story. If you just pull it out, the operating system might be in the middle of writing to it. In that case, you may lose the data you were writing partially or completely. Or it could create inconsistencies between what is actually on the file system and the administrative data. Also, Ubuntu caches data before actually writing it to a file system, so if you just unplug it, the OS cannot flush the cache to the file system. (IIRC, Windows does not use a cache for removable drives by default, for exactly this reason.)
If you eject the medium (or use Windows' "Safely Remove Hardware"), you instruct the operating system to sync the data to the file system and then unmount it. That way, the data is comletely and consistently written to the file system before unplugging the medium.

HTH,
Lars

---

### Post by LaRoza on 2007-05-03
YES. At the least, you'll wipe the formatting and have to reformat it, at the most you can destroy the circuitry.

Learn from others mistakes.

---

### Post by lcg on 2007-05-03
> **ThinkBuntu said:**
> I don't want to turn this into a question post, because I intended it as a curiosity one (hence the location), but I wonder if there's a way to make your system take care of the writes immediately...?

There is a mount option 'sync' (see 'man mount') which instructs the OS to make all write operations on that file system synchronously, i.e. without caching. I don't know, however, how to make Ubuntu mount all removable media with that option.

HTH,
Lars

---

### Post by richbiskit on 2007-05-03
I have found that with my generic mp3/usb storage device that if i just pull it out it doesn't save any changes that i have made but unmounting it in Ubuntu/safely remove in Kubuntu everything is fine. As for actually damaging it i doubt it very much.

---

### Post by gerscht on 2007-05-03
> **lcg said:**
> There is a mount option 'sync' (see 'man mount') which instructs the OS to make all write operations on that file system synchronously, i.e. without caching. I don't know, however, how to make Ubuntu mount all removable media with that option.
The option is in 
```
/etc/hal/fdi/policy/preferences.fdi
```
The default is that devices smaller than 1gb are mounted for synchronously write.

---

### Post by zek725 on 2007-05-27
So, in layman terms, **Unmounting/Ejecting** the drive is the Ubuntu counterpart of Windows' **Safely Remove Hardware**?

---

### Post by FuturePilot on 2007-05-27
I've never had a problem just pulling it out from XP. Although I always eject it in Linux. To me that Safely Remove option in Windows is crap and useless. It's so confusing since it lists a ton of stuff that you're not concerned with like the USB bridges:roll:

So the easiest way to safely remove a drive from Windows is to just open My Computer, find the removable drive, right click and select Eject. Much easier than searching through a whole list of stuff just to find your device. I never could figure that out. I think I always end up ejecting the wrong thing.

---

### Post by prizrak on 2007-05-27
XP is set for quick removal, meaning that all the data is written to a removable drive as soon as it is set to copy. As someone mentioned Ubuntu does that to any drive smaller than 1 gig. So if you are using something bigger than that in Ubuntu and use Nautilus your data might not be written until after you choose to eject it. In my experiece rsync actually pushes all the data as soon as possible.

---

### Post by Quillz on 2007-05-27
For the most part, you can simply plug/unplug a USB drive in any OS without ill side effects. But it's always better (when possible) to use the safely remove hardware option, just in case.

---

### Post by smoker on 2007-05-28
having borked a usb flash drive before (128mb in windows), by unceremoniously unplugging without using the safe removal procedure, i always verge on safety now, on windows and linux.

the files in the borked 128mb drive started reading at 4GB (yes!) in size and couldn't be opened. reformatting the drive didn't work, it was well fubar. so, lesson learned!:-)

---

