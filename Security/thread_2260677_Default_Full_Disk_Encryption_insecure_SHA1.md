---
title: "Default Full Disk Encryption insecure? SHA1"
date: 2015-01-13
forum: Security
---

### Post by forever3 on 2015-01-13
[COLOR=#141414][FONT=verdana]Hello,[/FONT][/COLOR]

[COLOR=#141414][FONT=verdana]I'm wondering. Why is Ubuntu and Mint only using SHA1 for Full Disk Encryption? I heard several times that SHA1 shouldn't be used anymore because it is weak and it could be cracked. [/FONT][/COLOR]

[COLOR=#141414][FONT=verdana]Could you guys explain me why we should use the default GUI encryption if we can just encrypt the system over the terminal with like SHA512? I'm I paranoid or is it just a lie that SHA1 has been broken?

And

[/FONT][/COLOR][COLOR=#141414][FONT=verdana]"As hardware gets more powerful, password cracking in such an occasion becomes a lot more viable and SHA1, (Cryptsetup's default) which already we should be far away from (but aren't), looks even more deprecated."

Moreover: All the encryption programs like TrueCrypt and Veracrypt they all do not use SHA1 anymore because it is insecure. So why is cryptsetup encrypting the whole drive with SHA1? It does not seem secure, does it? 

I'm a rookie user so please explain me some stuff :)[/FONT][/COLOR]

---

### Post by kevdog on 2015-01-13
SHA-1 is a hash function, not an encryption tool.  You usually encrypt with something like AES-256 which is the default now-a-days although there are others which may be faster -- blowfish, twofish, etc.  You use hashes to verify the encrypted data or hash passwords.

---

### Post by bashiergui on 2015-01-13
+1 to Kevdog's comments.

If the OP would like details about the encryption Ubuntu uses, this had a decent answer:
[http://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption](http://security.stackexchange.com/questions/39306/how-secure-is-ubuntus-default-full-disk-encryption)

---

### Post by forever3 on 2015-01-14
I'm talking about the hash, guys.

I know that AES is supposed to be secure but why is the installer using sha1 for password hashing? I heard it is not secure and it can be brute forced quite easily. Why is it not using sha256 / 512 for whole disc encryption?

---

### Post by kevdog on 2015-01-14
I'm not too certain why SHA-1 was chosen, however although there have been some discovered vulnerabilities -- or more aptly put -- the chance of discovering a collision -- or two sets of data producing the same hash set -- is kind of overblown.  I think theoretically a research project found that the process of producing a collision could be lowered from 31 to 7 years.  That's seven years of continuously guessing passwords for brute force hacking via a computer that is processing this transformation at an extremely high rate. 

I'm not sure if there is a setting within the encryption setting to allow you to change the hash.  I believe whole disk encryption performs this by creating a dm-crypt volume on LUKS.  You may need to research this.  I believe you may be able to change the hash algorithm within the dm-crypt conf file.  You'll need to research this.  Of course this means that you'll probably have to do the partitioning yourself with a more manual process from a chroot environment -- which actually isn't all that hard, although you'll definitely need to research how to do everything and probably have to experiment a few times to get it exactly correct.

---

### Post by untrustytahr on 2015-01-14
> **forever3 said:**
> I'm talking about the hash, guys.

I know that AES is supposed to be secure but why is the installer using sha1 for password hashing? I heard it is not secure and it can be brute forced quite easily. Why is it not using sha256 / 512 for whole disc encryption?



[https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#5._Security_Aspects](https://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions#5._Security_Aspects)

> 
[LIST]
[*]**5.20 LUKS is broken! It uses SHA-1!**
[/LIST]
[INDENT]No, it is not. SHA-1 is (academically) broken for finding collisions,   but not for using it in a key-derivation function. And that collision  vulnerability is for non-iterated use only. And you need the   hash-value in verbatim.   [/INDENT]   
[INDENT]This basically means that if you already have a slot-key, and you  have set the PBKDF2 iteration count to 1 (it is > 10'000 normally),    you could (maybe) derive a different passphrase that gives you the  the same slot-key. But if you have the slot-key, you can already  unlock the key-slot and get the master key, breaking everything.  So basically, this SHA-1 vulnerability allows you to open   a LUKS container with high effort when you already have it   open.   [/INDENT][INDENT]The real problem here is people that do not understand crypto and  claim things are broken just because some mechanism is used that  has been broken for a specific different use. The way the mechanism   is used matters very much. A hash that is broken for one use can be  completely secure for other uses and here it is.   
[/INDENT]

---

### Post by forever3 on 2015-01-14
But all in all, the hardware gets faster every year, right?

And how about the iterations? Sha1 uses a high iteration cound but the boot time is fast as f***. So Brute Force can easily be done, huh?

---

### Post by bashiergui on 2015-01-15
> **forever3 said:**
> But all in all, the hardware gets faster every year, right?

And how about the iterations? Sha1 uses a high iteration cound but the boot time is fast as f***. So Brute Force can easily be done, huh?See this estimator that will tell you how long it would take to brute force a password of your length and complexity that uses raw sha1. [http://calc.opensecurityresearch.com](http://calc.opensecurityresearch.com)I chose a password of 10 characters with alphanumeric and symbols. It will currently take 11,000 years for continuous offline cracking, much longer for attempts directly on your machine. 

You can game it to see how much computing power an attacker needs to crack your password in a reasonable timeframe, then see if that kind of power exists today. 

Yes computers will improve but when they do just increase your password complexity. Done.

edit: you said you're assuming the attacker will brute force it on your computer. If he does that then the speed is fixed: your computer can only allow new attempts in X seconds. It doesn't matter how fast computers get, it only matters how fast *your* computer is. And that won't change during an attack.

---

### Post by forever3 on 2015-01-15
I found this one:

[http://hideandhack.blogspot.de/2013/05/do-not-use-sha-1-luks-disk-encryption.html](http://hideandhack.blogspot.de/2013/05/do-not-use-sha-1-luks-disk-encryption.html)

Moreover: Sha256 should be much more secure, shouldn't it? I'd like to see a dropdown box where I can chose a Hash :(

---

### Post by sudodus on 2015-01-15
Most people think that the security is good enough. You cannot expect them to improve it, but the source code is free, available for you to improve to satisfy what you want. You are welcome to do it :-)

It is also possible to search the internet for linux distros, that focus on security, for example ***Tails***.

Maybe you can find some valuable tips at the following link: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by forever3 on 2015-01-15
Found this on VeraCrypt forums:

[COLOR=#555555][FONT=sans-serif]Also, the statement that the underlaying hash function doesn't matter is completely false because there are security requirements that must be fulfilled by the hash function in order to the key derivation to be secure. Otherwise, there will be no need for cryptography and we can stick with 30 years old hash functions like MD4!![/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]Anyway, in such security topics, one must carefully check any statement or information before endorsing it or using it. There are many out there who mislead people either on purpose or because they are ignorants of cryptography basics.[/FONT][/COLOR]

---

### Post by bashiergui on 2015-01-15
Yes knowledge is power. Educate yourself. Here's a good overview of how a hash function is used in encryption.[http://searchsecurity.techtarget.com/definition/encryption](http://searchsecurity.techtarget.com/definition/encryption)


Here's the presentation of the theoretical crack of sha1. You can reproduce the math if you like.
[http://2012.sharcs.org/slides/stevens.pdf](http://2012.sharcs.org/slides/stevens.pdf)

---

