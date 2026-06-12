---
title: "Encrypt with right click safe?"
date: 2011-07-13
forum: Security
---

### Post by PDA1 on 2011-07-13
Tell me if I'm wrong.

I just found a neat way to encrypt a file in Ubuntu 10.04.

I right click on a file and select the Encrypt option.  The program
prompts me to "Choose Recipient" so I choose myself on the list. Then it
prompts me to enter my passphrase.  

Once all that's done I hit enter and it adds .pgp to the end of whatever
file just encrypted. The same basic method is used to Sign the file.

Does it sound as though what I said is correct and that the file I wanted to encrypt was indeed  encrypted?

Can anyone crack my files without the passphrase?  I'm sure it depends
on the complexity and length of the passphrase.


Thanks.

---

### Post by Chayak on 2011-07-13
PGP and OpenPGP are two of the most trusted encryption programs available.

The security of your encrypted file revolves around the complexity of your passphrase and the security of your private keys.  It's not feasible to attempt brute forcing a pgp encrypted file without the private keys to begin with, and if someone does manage to get your private keyring they still have to brute force your passphrase.  If your passphrase is something like "The drunken fox ducked the b@r t@b and kicked th3 tripping cow over the m00n" it's not likely to be brute forced.

In the past the FBI has been known to install keyloggers on high profile suspect's computers to get their passphrases.

---

### Post by PDA1 on 2011-07-13
Thank you. 

Isn''t my private key readily available on my computer?  

All I do have to do is enter;  gpg --list-secret-keys  and I get to see the secret key.

Also, on my other computer I can't do the "right click" and select Encrypt for any file as there's no option to encrypt the file.  

Why's that and how do I fix it?

---

### Post by Chayak on 2011-07-13
Your private keyring is in the .gnupg directory of your home folder.  I know some people who keep theirs on flash drives, one in an ironkey encrypted flashdrive.

You can get the right click encryption by

```
sudo apt-get install seahorse-plugins
```

Then the easiest thing to do is log out and log back in and you'll have the option to encrypt when you right click.

---

### Post by tubbygweilo on 2011-07-13
> **PDA1 said:**
> ...All I do have to do is enter;  gpg --list-secret-keys  and I get to see the secret key...

Physical access is all; you could make things harder by employing fulldisk encryption along with passwording the bios and never letting the kit out of your sight:D

---

### Post by PDA1 on 2011-07-13
That's great!  The Seahorse plugins were installed and now I can encrypt with the right click method.  

As the public and secret rings are located on .gpupg, if my computer gets stolen then whoever has enough brains in their head to understand Ubuntu they could find my rings at the aforementioned location and wreak some havoc using my machine.

I assume the passphrase, only known to me, is the strong link in the chain and the thief not knowing the passphrase renders the system largely uselesss.

Is that assumption correct?

---

### Post by DZ* on 2011-07-16
> **PDA1 said:**
> That's great!  The Seahorse plugins were installed and now I can encrypt with the right click method.  

As the public and secret rings are located on .gpupg, if my computer gets stolen then whoever has enough brains in their head to understand Ubuntu they could find my rings at the aforementioned location and wreak some havoc using my machine.

I assume the passphrase, only known to me, is the strong link in the chain and the thief not knowing the passphrase renders the system largely uselesss.

Is that assumption correct?

The secret key is encrypted with CAST5 by default (man gpg). It's the same default as for the symmetric encryption. So, unless you keep the secret key separately from encrypted files, there is no advantage in encryption of your files using your own public/private keys.

Dolphin, when kgpg is installed, lets you right-click-encrypt using the symmetric encryption that you can use without having to have your keys around (the terminal command is gpg -c).

---

