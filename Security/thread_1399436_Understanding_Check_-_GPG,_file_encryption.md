---
title: "Understanding Check - GPG, file encryption"
date: 2010-02-05
forum: Security
---

### Post by NertSkull on 2010-02-05
So I feel like I've read a thousand webpages on this, and I think I'm getting it figured out, but I wanted to make sure I was understanding before moving forward.

Basically I want to encrypt a few important files/folder on my computer such that if my computer was ever to be stolen I wouldn't have to worry about someone having access to them.

So I've read a ton on GPG and it seems to make sense that it would work.  But, my question is, I end up just storing my GPG key on the same computer that I'm encrypting my files on.  So if someone steals my computer, they also have my GPG key, right?  Seems like that may not be the best way to encrypt files.  I understand I should still (and would) have a passphrase set up for that GPG key, but still seems like not the best method.

Next, everything I read about GPG says something like, you encrypt the files with someone else's public key so that when you send it to them, they can decrypt it.  Fine, that makes sense.  But if I encrypt my own file with MY gpg key, is that a problem in anyway.  I can't see how it would be.  I assume then that I encrypt my files with my own public gpg key, and then later if I need to access them I use my private key to decrypt them.  Is this the way to go?

Now on a completely different gear.  The other thing I've looked into a lot is Trucrypt.  It seems pretty promising, but for some reason GPG feels safer/better to me.  I could be totally wrong though.  Would I be better of only using Truecrypt? Or should I use GPG?  

Or is there a much better way to do this?  Something I have missed altogether?  I have a couple hundred Megs worth of sensitive work information I would really like to stop storing on a USB drive I keep with me all the time.

Thanks everyone, I'm sure I'm still a noob at all this, so let me know if I've left out anything I should have mentioned.  Thanks again

---

### Post by tubbygweilo on 2010-02-05
NertSkull, for encrypting something sensitive that resides upon your hard disk then may I suggest you consider [truecrypt]("http://www.truecrypt.org/")? it is used by many who inhabit this forum and most have found it more than suitable for keeping data safe from prying eyes. I find the [documentation]("http://www.truecrypt.org/docs/") well written and well up to the task of explaining in simple phrases how things work and the [beginners guide]("http://www.truecrypt.org/docs/?s=tutorial") a good place to start. When using truecrypt your passphrase is the only way to read things to from what I understand truecrypt encrypted files are not meant for sharing, not even with the NSA and others of that ilk. 

Encryption using private and public keys I use when sending emails to others using [Gnupg]("http://www.gnupg.org/") from within Mozilla Thunderbird plus the Enigmail extension. A set of [HOW TO]("http://www.gnupg.org/documentation/howtos.en.html") documents will take you through the [concepts]("http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html#toc1.2") of private/public keys, encrypton & signing messages and might illustrate the different workings of Truecrypt and Gnupg. 

Hope this helps but if not then someone with a bigger brain and better writing skill will be along sometime soon to offer more advice.

---

### Post by rookcifer on 2010-02-06
> **NertSkull said:**
> So I've read a ton on GPG and it seems to make sense that it would work.  But, my question is, I end up just storing my GPG key on the same computer that I'm encrypting my files on.  So if someone steals my computer, they also have my GPG key, right?  

It doesn't work that way.  The keys are not stored in plain text for anyone and everyone to see.  The keys themselves are encrypted, only to be decrypted if one has the pass phrase. (Note, there is one caveat to this as I will explain below).

> Next, everything I read about GPG says something like, you encrypt the files with someone else's public key so that when you send it to them, they can decrypt it.  Fine, that makes sense.  But if I encrypt my own file with MY gpg key, is that a problem in anyway.  I can't see how it would be.  I assume then that I encrypt my files with my own public gpg key, and then later if I need to access them I use my private key to decrypt them.  Is this the way to go?

That's correct.  There are two different forms of encryption: symmetric and asymmetric.  Symmetric means that the same key is used for encrypting and decrypting.  Asymmetric means you have a public key that is shared openly with the world and a private key that only you have access to, which works in conjunction with the public key.  When encrypting files on your own hard drive, you use a symmetric key, thus there is no public key in that case.  Asymmetric encryption is only used for e-mail encryption so that people don't have to share keys in private.  It's a convenience thing.

> Now on a completely different gear.  The other thing I've looked into a lot is Trucrypt.  It seems pretty promising, but for some reason GPG feels safer/better to me.  I could be totally wrong though.  Would I be better of only using Truecrypt? Or should I use GPG?  

If you just want to encrypt individual files, stick with GPG.  If you want to encrypt whole volumes, Truecrypt would be better.  However, if it were me, I wouldn't use either of them -- I would use dm-crypt/LUKS which is native to Linux and comes as an option of the Ubuntu alternate install CD.  It allows you to encrypt the entire drive, which is by far the safest option.  Truecrypt also allows this, but I prefer LUKS since it was written for Linux from day one.

The problem with using anything but whole disk encryption is that when you encrypt/decrypt a file, the key is temporarily stored in memory and might end up in swap space (or somewhere else on the drive).  This means someone can do a forensic analysis and *perhaps* find your key (pass phrase) on the drive.  The best way to stop this is to encrypt the whole disk, including the swap space.

---

