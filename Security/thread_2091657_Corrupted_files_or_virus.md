---
title: "Corrupted files or virus?"
date: 2012-12-05
forum: Security
---

### Post by Ender Shadow on 2012-12-05
Yesterday I discovered what may be a virus on my thumb drive. Or it could just be corrupted files, but I don't know which.
Why do I think its a virus? Because:
1)  Whenever I mess with them (e. g. Attempting to copy or move them [which fails] or      
     going in to the folder) causes my thumb drive to go into read-only mode.
2) Their combined file size is over 1  terabyte, although my thumb drive only holds 16 GB
3) Their are hidden folders that I can only see on Windows

I found them in the files folder of a web page (two actually) that I saved to my computer.
I could probably delete them, but I would like to save them for further study (but not on the thumb drive that has my *_backups_* on it).

This virus(?) does not appear to be affecting Ubuntu.

---

### Post by lisati on 2012-12-05
Going by the apparent inconsistency in the file sizes, I'm inclined to think that it's more like that something has been scrambled.

---

### Post by ibjsb4 on 2012-12-05
Have you been copying CD's or DVD to it?

---

### Post by Ender Shadow on 2012-12-05
> **lisati said:**
> Going by the apparent inconsistency in the file sizes, I'm inclined to think that it's more like that something has been scrambled.

That's what I thought. But why is my thumb drive switching to read-only mode?

> **ibjsb4 said:**
> Have you been copying CD's or DVD to it?

Nope.

---

### Post by bfmetcalf on 2012-12-05
Reminds me of this...

[http://en.wikipedia.org/wiki/Zip_bomb](http://en.wikipedia.org/wiki/Zip_bomb)

---

### Post by Ender Shadow on 2012-12-05
> **bfmetcalf said:**
> Reminds me of this...

[http://en.wikipedia.org/wiki/Zip_bomb](http://en.wikipedia.org/wiki/Zip_bomb)

They aren't .zip files though. But that "Zip Bomb" sounds nasty.

---

### Post by Frogs Hair on 2012-12-05
Make sure you eject the properly if it is used on Windows or the drive can be damaged and cause the kind of problems you are describing.

---

### Post by Ender Shadow on 2012-12-05
> **Frogs Hair said:**
> Make sure you eject the properly if it is used on Windows or the drive can be damaged and cause the kind of problems you are describing.

I've always ejected my thumb drive properly (although Windows doesn't actually turn it off).

---

### Post by Ender Shadow on 2012-12-05
I guess I'll just delete the files then, since they were most likely just corrupted.
Here are some screenshots of them.

---

### Post by CharlesA on 2012-12-05
Run a chkdsk on the drive if it is running NTFS and fsck if it is running ext*.

---

### Post by freacert on 2012-12-05
> **Ender Shadow said:**
> I guess I'll just delete the files then, since they were most likely just corrupted.
Here are some screenshots of them.


for me, old type virus. maybe run an online virusscanner on it? (haven't done that in years ;) )

---

### Post by Ender Shadow on 2012-12-05
> **freacert said:**
> for me, old type virus. maybe run an online virusscanner on it? (haven't done that in years ;) )

I tried AVG, but it didn't find anything. I really don't think it's a virus anymore (but I could be wrong).

CharlesA, I am currently running a chkdisk on my thumb drive. It'll take while...

---

### Post by Ender Shadow on 2012-12-05
I ran chkdisk, but I don't know if it found anything. I'm deleting the corrupted files now, which will take a while due to the incorrect file sizes.

---

### Post by CharlesA on 2012-12-05
You might be better off just copying the files you want off it and reformatting it.

---

### Post by cariboo on 2012-12-06
I've seen something similar a couple of times, it's usually because of a corrupted file system.

---

### Post by Ender Shadow on 2012-12-06
Actually, chkdisk did do something. I found a folder called "FOUND.000" and in it were the files that were corrupted. All of them except the text files are fine, and the other files have correct file sizes now. I'll probably just delete those, because I can just save the web pages again. Even so, I think that I will reformat my thumb drive, just in case chkdisk missed something. 
Thank you for your help everyone, and I'll be even more careful with my thumb drive in the future.

---

### Post by Synoc on 2012-12-09
I know you have this issue technically solved, and it may be, but if I get a drive that badly messed up. I photorec my files I need on it, reformat zero out out the drive, then smash it with a hammer. I do this for multiple reasons
1. I nearly always have a bad drive
2. it always good practice to wipe information off the drive
3. while that format and zeroing is usually enough to wipe information off the disk. Hitting it with a hammer makes me feel better after I spent hours finding and restoring my files.

Again this is my personal experience. As inexpensive as flash drives are it's not worth the risk of loosing valuable data. I had to do this for someone. after hours of trying to "fix" her drive I just ended up photorec'ing it and making a DVD of all her files. The drive was unrecoverable

regarding being more careful with your drive, if you are removing it correctly, there is little you can do. the fact is drives go bad, they have a shelf-life of so many read-writes before it just wears out.

---

### Post by CharlesA on 2012-12-09
It would be easier to just drill holes in the platters... but then it wouldn't make you feel better. :p

---

### Post by cariboo on 2012-12-09
if you go look at the first post, the op asked about files on a usb thumb drive. Why destroy it, if a format solves the problem? :-D

---

