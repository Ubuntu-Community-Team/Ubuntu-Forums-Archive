---
title: "Can 67% Full HD Be Encrypted Contiguously w/o Backing Up?"
date: 2009-10-04
forum: Security
---

### Post by purport on 2009-10-04
I have a 67% (2/3) full external hard drive with no space on my other hard to drive back it up. So I want to encrypt it, but as far as I know mainstream encryption technology requires you to copy and paste (not cut and paste!) files into an archive, the size of which may or may not be variable (7zip appends to its archive, while Truecrypt's volume's are static).

I think it is possible to append to a 7zip file. I could copy 1/2 of the data in an encrypted archive, which would fill 1/3 of the disk, and subsequently delete that redundant (unencrypted) data. I would then add the remaining 1/2 to the archive, expanding it to 2/3 of the disk. Then I would delete the rest.

But is that really the best option? 7zip is horridly slow. I literally fear for my computer's life (hard drive is 1 TB, btw). I would prefer Truecrypt, but I don't think Truecrypt allows expanding volumes. This is a very real limitation and the only conceivable reason not to bow down to the Truecrypt devteam and worship them as gods.

...Any thoughts?

PS has anyone else memorized a 32+ character password for their data?

---

### Post by undecim on 2009-10-04
The only way I see of doing this is to use ecryptfs. This won't require a new partition, and has the added bonus that you don't need to encrypt everything -- just whatever you put into your ecryptfs mounted directory

---

### Post by purport on 2009-10-04
I should have mentioned that I don't access the files with Unix -> Linux -> Ubuntu (i.e. not Windows)

But with ecryptfs, can I just tell ecryptfs to encrypt all the data, even if it is inside NTFS? If so, then I could just use VMWare to load Ubuntu and access the HD to encrypt it.

---

