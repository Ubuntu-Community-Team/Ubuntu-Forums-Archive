---
title: "Encrypt Home Encryption Strength?"
date: 2016-05-07
forum: Security
---

### Post by uRock on 2016-05-07
Hi all,

I've been looking around and read that the full disk encryption uses AES with 512bit keys, but I cannot find anything about the type and strength of the "Encrypt Home" feature offered in the *buntu installer.

That said, what type of encryption is used and what size key does it use?

Thanks!

Cheers & Beers,
uRock

---

### Post by DuckHook on 2016-05-07
> **uRock said:**
> That said, what type of encryption is used and what size key does it use?uRock, all I could find was the following:
[https://wiki.archlinux.org/index.php/ECryptfs#Using_the_Ubuntu_tools](https://wiki.archlinux.org/index.php/ECryptfs#Using_the_Ubuntu_tools)
which states that it is 128 bit AES, which seems on the skimpy side and is concerning me now that you've brought it up on this thread.

I use it to encrypt a *Private* directory but imagine that */home* must similar.

---

### Post by uRock on 2016-05-08
> **DuckHook said:**
> uRock, all I could find was the following:
[https://wiki.archlinux.org/index.php/ECryptfs#Using_the_Ubuntu_tools](https://wiki.archlinux.org/index.php/ECryptfs#Using_the_Ubuntu_tools)
which states that it is 128 bit AES, which seems on the skimpy side and is concerning me now that you've brought it up on this thread.

I use it to encrypt a *Private* directory but imagine that */home* must similar.

I was hoping it would be stronger, too. I guess this means my next install will be full disk encryption. I usually just encrypt the /home.

I also use Truecrypt for some of my files.

---

### Post by DuckHook on 2016-05-08
> **uRock said:**
> ...I also use Truecrypt for some of my files.I thought Truecrypt was abandoned by its developers and is no longer maintained.

---

### Post by uRock on 2016-05-08
It's no longer maintained, but it is still a strong tool. The most current Security+ textbook(published 2015) [s] lists it as a reliable tool.[/s] says "Truecrypt is a depreciated (but still widely used) personal encryption tool."

I am still looking to get away from it by having a strong system encryption. I always shut my system down when I am done with it for the day.

---

