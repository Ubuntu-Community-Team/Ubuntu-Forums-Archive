---
title: "How to set up truecrypt"
date: 2010-04-08
forum: Security
---

### Post by Thystra on 2010-04-08
I've been looking at setting up truecrypt on my laptop, but the guides on the truecrypt site and the ubuntu documentation seems to be incomplete or not address what i want to do.

What I have:

dual boot windows 7 / Ubuntu (lucid)

What I want is to dual boot with the hidden OS system:

Windows 7 (plausable)
Ubuntu (plausable)

Ubuntu (hidden install)

Is this possible?  or is it better to make a hidden /home partition?

Thanks.

---

### Post by EJeanmaire on 2010-04-08
The sticky on the top of this forum gives step by step directions on Truecrypt installation, and it is frequently updated.  Here is the link: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I am not following on what you mean by "plausible", yes those OS's can be encrypted.  If you mean it in the sense of it may not be proven that you are running a given OS... all data encrypted on the drive is "hidden", hence the reason for encryption.  TrueCrypt does have a feature to create a fake OS in the event that you were forced to divulge your encryption key (instead you would hand over the encryption key for the fake os, and the recipient being none the wiser, and you avoid exposing your true OS).  To set this up it is a feature directly accessed in the TrueCrypt program when you set up a drive for encryption.

Making /home encrypted is not as secure is the full disk.  Personal files that are in /tmp or in Swap could still be read by a third-party.

---

