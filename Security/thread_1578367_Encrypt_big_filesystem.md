---
title: "Encrypt big filesystem"
date: 2010-09-20
forum: Security
---

### Post by Blackbird++ on 2010-09-20
Hi,

I want to encrypt my movie collection. On Windows I used Truecrypt.
I'm going to encrypt a whole partition, the filesystem will be ext4 or something.
And I want a secure, but **fast** and **easy to use** method.

So, which one would you advise me to choose?
Maybe Truecrypt again, or dm-crypt, or LUKS?

Should be automatizable, so I've just to press a button or something and type the password.

---

### Post by jhayes on 2010-09-20
i have only run truecrypt briefly, and the problems i had were hardware related. i don't see any reason why truecrypt wouldn't work.
[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
it claims to only slow your system down something like 1-5%, and unless you run prime or seti ALL the time should not be a problem. i cannot speak for dm-crypt, but true crypt is cross platform. so say for soem reason you need to take that hard drive out and give to a friend. you can stick it in windows and un-encrpyt it ( then us e2fs or something to read the partition)

---

### Post by Blackbird++ on 2010-09-21
Ok thank you. Are there any reasons to use something different than Truecrypt for my purposes?

---

### Post by HermanAB on 2010-09-21
Howdy,

LUKS is the standard Linux way to encrypt file systems on enterprise and government systems.  All my Linux machines are encrypted with LUKS and AES256 - there is no noticeable slowdown (it has been measured at about 3%).

The Ubuntu alternate install uses EncFS, which is also good.

---

### Post by Blackbird++ on 2010-09-21
Ah, now come the arguments. ;) What differences do they all have, and again:

Which of them do you think would be the best choice for me?

---

