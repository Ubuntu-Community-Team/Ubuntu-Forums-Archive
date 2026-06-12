---
title: "Is it possible to create encrypted containers within an already encrypted device/hd?"
date: 2013-01-08
forum: Security
---

### Post by thaitang on 2013-01-08
Is it possible to create encrypted containers within an already encrypted device/hd?

I used truecrypt to encrypt a 1TB hd because my wife needs to access the hd onp her winblowz PC at work. I also had to create what I consider a less than secure passphrase to make it usable for my wife. No probs I thought since I was intending to simply create additional encrypted containers withing the encrypted hd to keep other files I would like to store on there more secure from prying eyes, especially if the hd will be lying around on my wife's desk at work.

I have tried using truecrypt to make an encrypted container on the encrypted hd, however, after the process begins and gets as far as 1-2% of creating a 100GB container the process bails out complaining the disk is unavailable. Yet it is still listed with a df command and available to ls commands and general browsing using nautilus.

Iniitially I did try to make an ext2 container (using truecrypt), and then thought that maybe b/c I encrypted the drive using vfat that I had to settle for containers fobrmatted using vfat, but that process bails out in a similar fashion as earlier attempts specifying ext2.

---

### Post by Hungry Man on 2013-01-08
It should be possible. Sounds like a bug.

---

### Post by thaitang on 2013-01-09
> **Hungry Man said:**
> It should be possible. Sounds like a bug.

yeah well i thought it was possible or i would have looked further. but to be honest i found squat about encrypting containers inside of encrypted drives/containers.

so if anyone has an experience trying the same or similar i would appteciate reading it. the thought of re-encryting a 1tb drive does not excite me.

---

### Post by thaitang on 2013-01-09
so nobody has any success or experience trying to create an encrypted container within an encrypted partition?

---

### Post by thaitang on 2013-01-17
not that it seems like this is an issue or consideration for anyone else, ever, but I finally realized my problem was that by using vfat to encrypt the entire disk that I could not create encrypted containers larger than 4gb.

So I just decided to re-partition, encrypt 100Gb using dm-crypt for my own shiz with an ext2 fs and truecrypted the rest of the disk with vfat so my wife can use the ext drive as well on her winblowz box.

I think if I dug deeper I might have been able to utilize NTFS but for some reason that option does not present itself during the truecrypt process, and unfortunately they require a non-free (as in no gmail/hotmail/yahoo) email account in order to register to post questions in their forums. And so that is where my inquiry ended with that.

---

### Post by Paddy Landau on 2013-01-18
I believe that Truecrypt shows an NTFS option only when creating a partition from Windows.

However, you can reformat the partition after creating it. Use Truecrypt to mount the partition, but choose "Do not mount" in the advanced options. Then you can format the partition as NTFS. Obviously, any data already on the partition will be erased. The device will be something like /dev/mapper/truecrypt1 (right-click the device in the Truecrypt window and select properties to see the exact device).

BTW, why ext2 and not ext4?

---

