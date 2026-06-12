---
title: "Self destroying HDD"
date: 2010-02-21
forum: Security
---

### Post by gardara on 2010-02-21
I've been wondering if hard drives or partitions can automatically be self destroyed if the wrong person gets their hand over it.

I have hard disks encrypted with truecrypt, but I'm wondering if someone would get their hands over it and begin brute forcing... So the drive would automatically wipe or damage itself after X many wrong password inputs.


I think I remember reading about such software for windows some years ago but I'm not quite sure.


Do you guys think it is/would be possible with software? Or would it require some mechanical modifications on the hard drive, like wiping the hard drive automatically with a magnet or sand paper.



(And yes, I know it's highly unlikely to actually happen to me, but I'm curious)

---

### Post by mkvnmtr on 2010-02-21
I believe you could write a script that would start wipe if so many password attemps were made. But be aware wipe takes a long time and the system has to be running.

---

### Post by SecretCode on 2010-02-21
It's an idea I've often thought about. 

But no, definitely not possible with regular hard drives or flash memory. Given the assumption that an "adversary" can attach the drive to their choice of host OS, there's no way you can guarantee any script held on the device would be run.

Such a drive would have to have its own processor and OS/firmware - which of course is technically no problem - many phones and MP3 players have firmware and can also appear as USB drives to a computer. And it would somehow have to prevent direct access to the disk platters or flash chips - which would mean some kind of closed encryption. Should be possible, but I haven't heard of anything like this.

---

### Post by gardara on 2010-02-21
> **SecretCode said:**
> It's an idea I've often thought about. 

But no, definitely not possible with regular hard drives or flash memory. Given the assumption that an "adversary" can attach the drive to their choice of host OS, there's no way you can guarantee any script held on the device would be run.

Such a drive would have to have its own processor and OS/firmware - which of course is technically no problem - many phones and MP3 players have firmware and can also appear as USB drives to a computer. And it would somehow have to prevent direct access to the disk platters or flash chips - which would mean some kind of closed encryption. Should be possible, but I haven't heard of anything like this.


What if this would get implemented into a application like truecrypt?
As far as I know, truecrypt devices can only be mounted and decrypted with truecrypt... And therefore truecrypt is a requirement on the computer that is supposed to read the disk.
 Couldn't there be some script on the disk that truecrypt would trigger if a incorrect password would be entered X many times?

---

### Post by SecretCode on 2010-02-21
But if I can use my own copy of truecrypt to access the raw data on your drive (probably involving opening up the case), I won't execute any script on the drive and I can run brute-force attacks ... just like I can with an ordinary truecrypt-encrypted drive.

---

