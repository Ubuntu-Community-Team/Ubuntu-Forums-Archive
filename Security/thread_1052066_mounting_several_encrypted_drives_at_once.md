---
title: "mounting several encrypted drives at once"
date: 2009-01-27
forum: Security
---

### Post by Thoralyon on 2009-01-27
i read several helpful guides about encrypting ubuntu during the installation, but before i actually start installing, I still have one problem.
I basically want to mount a second encrypted harddrive that gets its password from the (encrypted) root partition of the first harddrive, so i dont have to type it twice.
As I understand it it's basically the same as this: [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)
with a regular password substituted for the keyfile.
I don't like the keyfile because i can "loose" it (i.e if the first harddrive dies on me, i cannot acces the data on the second). I also want to be able to just plug the drive in somewhere else and access the data normally using the password.

I guess writing my password in the keyfile and using it should work, but that sounds really strange to me....

---

### Post by jerome1232 on 2009-01-27
There are multiple key slots with luks, so you can make the partition unlockable with a keyfile at slot 0 and  a passphrase at slot 1.

At least I believe that should work, maybe you have a spare partition to test it on and make sure.

This way if the keyfile is lost you can still unlock the partition with the passphrase.

---

### Post by hyper_ch on 2009-01-28
yes, luks can store multiple passphrases... in the ende even a "keyfile" is nothing more but a huge passphrase.

---

