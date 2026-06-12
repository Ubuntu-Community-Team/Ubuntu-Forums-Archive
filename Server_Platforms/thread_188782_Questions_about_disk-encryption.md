---
title: "Questions about disk-encryption"
date: 2006-06-04
forum: Server Platforms
---

### Post by hamil on 2006-06-04
Hello!

I have a partition on my machine, that I would like to encrypt. It is 60GB in size. I read somewhere that, since it was so big, I could not use TrueCrypt to encrypt it.
Is there some other tools that I can use to encrypt it? 
I would like this partition to be invisible, until I mount it, so that no one else that is using this computer, can see the content of that partition.

I was also wondering, if it is possible to encrypt and make an folder in e.g my home folder invisble?

I have never encrypted anything else than my mail before, so some hints to the right direction, would be highly appreciated!

---

### Post by lcg on 2006-06-05
[QUOTE=hamil]I have a partition on my machine, that I would like to encrypt. It is 60GB in size. I read somewhere that, since it was so big, I could not use TrueCrypt to encrypt it.
Is there some other tools that I can use to encrypt it?[/QUOTE]
I don't know of any size restriction for TrueCrypt, I have never used it in Linux.
There's a new howto in the [wiki]("https://wiki.ubuntu.com/EncryptedFilesystemHowto3"). However, I have only looked at it briefly, but it uses LUKS which is a good design, IMO.

[QUOTE=hamil]I would like this partition to be invisible, until I mount it, so that no one else that is using this computer, can see the content of that partition.[/QUOTE]
A partition is visible by design. However, if the partition is encrypted, the content will look like random data (if it doesn't, the encryption algorithm is broken).

[QUOTE=hamil]I was also wondering, if it is possible to encrypt and make an folder in e.g my home folder invisble?[/QUOTE]
I'm not sure what you are trying to do, but invisible files or folder are a difficult concept. If an encrypted file (or folder) were invisible, how would the decryption software find it? And even if that were possible somehow, what's to prevent other software from overwriting the invisible (i.e. nonexistent) data?

If you are aiming for plausible deniability, I think your best bet is TrueCrypt with a hidden partition.

[QUOTE=hamil]I have never encrypted anything else than my mail before, so some hints to the right direction, would be highly appreciated![/QUOTE]
I suggest you look at the page in the wiki I mentioned earlier and the links at the end of that page. That should give you some ideas.

HTH,
Lars

---

### Post by hamil on 2006-06-05
[QUOTE=lcg]I don't know of any size restriction for TrueCrypt, I have never used it in Linux.
There's a new howto in the [wiki]("https://wiki.ubuntu.com/EncryptedFilesystemHowto3"). However, I have only looked at it briefly, but it uses LUKS which is a good design, IMO.[/quote]

Thank you for this link. I am checking it out now!

[quote="lcg"]
I'm not sure what you are trying to do, but invisible files or folder are a difficult concept. If an encrypted file (or folder) were invisible, how would the decryption software find it? And even if that were possible somehow, what's to prevent other software from overwriting the invisible (i.e. nonexistent) data?

If you are aiming for plausible deniability, I think your best bet is TrueCrypt with a hidden partition.[/quote]

I am sorry for my language, but I do not speak English as my native tongue. What I did mean, was that I do not want anyone to see these files and folders. E.g. I have a "school computer", I do not want the sysadmins at school to see the content of my home folder, when they are checking my computer. Also, I do have alot of different work on my laptop. If it gets stolen, I do not want the thief to be able to see any of my contents.

[quote="lcg"]
I suggest you look at the page in the wiki I mentioned earlier and the links at the end of that page. That should give you some ideas.
[/QUOTE]

Thank you for the link. It really helped me in the right direction!

Brgds
Lasse

---

### Post by lcg on 2006-06-05
[QUOTE=hamil]I am sorry for my language, but I do not speak English as my native tongue.[/QUOTE]
Well, actually, I did understand your language perfectly fine. I was a bit unclear about what exactly you were trying to do.

And for the record, I'm not a native speaker myself. :)

[QUOTE=hamil]What I did mean, was that I do not want anyone to see these files and folders. E.g. I have a "school computer", I do not want the sysadmins at school to see the content of my home folder, when they are checking my computer. Also, I do have alot of different work on my laptop. If it gets stolen, I do not want the thief to be able to see any of my contents.[/QUOTE]
OK, I see. As I explained before, it's (nearly) impossible to make data invisible. An attacker (be it an admin or a thief) can usually **see** the fact that there is an existing file/directory/partition (except for Steganography which really hides data, however I'm pretty sure that is impractical for your purpose).
On the other hand, if you encrypt your data, any attacker can have a lot of fun trying to break the encryption (actually, because we are all human, a brute force attack on the password used to encrypt the actual key is usually easier).

Now, for the school computer you mentioned: almost all encryption programs I can think of (at least the useful ones) mount the encrypted file, which means you would probably need root privileges on that machine. And a completely encrypted ~ would definitely require root access because of all the changes necessary.
On your own laptop, where you have the necessary access, you might want to look at encrypting your ~ or even your /, which shouldn't be too hard using cryptsetup.

[QUOTE=hamil]Thank you for the link. It really helped me in the right direction![/QUOTE]
Glad I could be of help.

Lars

---

