---
title: "Disk encryption question - TrueCrypt, dm-crypt"
date: 2009-01-28
forum: Security
---

### Post by Waffles385 on 2009-01-28
Hey, I just got a new laptop and was looking into full HD encryptions. I was planning on using TrueCrypt so I could use it on a Windows partition too. After searching the forums a bit, it seems like some people have performance issues with TrueCrypt, taking ridiculous amounts of time to copy files to and from the encrypted partition. They resolved this problem by using dm-crypt. I was wondering if people are still having problems with TrueCrypt or if the newer versions have resolved these. If they haven't, it looks like you can't use dm-crypt with an NTFS partition. Am I correct in this? What would everyone suggest for encrypting partitions for both Ubuntu, Windows, and possibly other flavors of Linux?

Thanks

---

### Post by hyper_ch on 2009-01-29
sure you can use dm-crypt with a ntfs partition...

---

### Post by tubbygweilo on 2009-01-29
Waffles385, would it be possible for you to give truecrypt a try on your machine with your data and then give dm-ctypt a try? I ask because what is fast on one user's configuration may be slow on yours and visa versa. If you are looking for something that you will use many times each and every day then I feel you do owe it to your self to give them both a try. 

After all if some users suggest that truecrypt is slow performing a task does that mean that all others users find it incredibly fast?

---

### Post by Waffles385 on 2009-01-29
Yeah I think that's what I am going to do. My main issue is if I can encrypt a partition with Windows on it using dm-crypt. I've seen stuff about FreeOTFE being able to access dm-crpyt partitions, and I am assuming since dm-crypt is below the file system it doesn't matter what file system sits on it.

---

### Post by hyper_ch on 2009-01-29
dm-crypt is not below the file system. The file system is below dm-crypt.

---

### Post by LodeRunner on 2009-02-21
> **Waffles385 said:**
> After searching the forums a bit, it seems like some people have performance issues with TrueCrypt, taking ridiculous amounts of time to copy files to and from the encrypted partition.

FWIW, I've never had a problem with TrueCrypt performance.  If you do a triple cipher cascade then yeah, you're going to see *some* slowdown but I think that 30 megs/second is pretty respectable under those conditions. AES encryption is very decent performing; I haven't noticed *any* slowdown.

Truecrypt does have issues, but (in my experience) read/write performance isn't one of them.

---

