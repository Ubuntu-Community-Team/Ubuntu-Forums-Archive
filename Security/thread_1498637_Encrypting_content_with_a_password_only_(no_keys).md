---
title: "Encrypting content with a password only (no keys)"
date: 2010-06-01
forum: Security
---

### Post by 1awesomeguy on 2010-06-01
What is the easiest way to encrypt plain text content with a password only? I need to encrypt client login information, but I hate dealing with all the unnecessary complexities of Linux's encryption systems.

I know I am going to get a bunch of people telling me how perfect Seahorse and whatever is, but Seahorse and the default /home directly encryption have both given me too many problems when decrypting my information. I prefer to preserve my data rather than using these methods.

Thanks guys!

---

### Post by cryptotheslow on 2010-06-01
I use Truecrypt for this purpose. It is no longer in the repositories in Lucid but can easily be downloaded from their site.

Just use the basic (default) option to create an encrypted volume in a file. You then use Truecrypt to mount the volume when you need it and it appears as just another drive in Nautilus, so you can drag and drop whatever files you want encrypted.

---

### Post by 1awesomeguy on 2010-06-01
Thanks cryptotheslow! I will look more into Truecrypt although, from a quick glance, it does seem it is a little bit more complex than what I wanted.

What I am looking for is just for encrypting simple text files already in their own file system structure. Gedit has a plugin for encrypting/decrypting text files which would be perfect if it didn't use Seahorse and just required a simple password.

I am looking for the simplest method available that will be idiot-proof and does not necessarily rely on just a single program or preserving a single key file. My biggest goal is to make sure I never lose data due to encryption software again.

---

### Post by anomie on 2010-06-01
[QUOTE=1awesomeguy]What is the easiest way to encrypt plain text content with a password only?[/QUOTE]

CLI OK? 

I like openssl for this purpose. Most general-purpose Linux systems have it installed. (Keep in mind that the password you provide will be used to generate an encryption key.) 

**Encrypt**
```
$ openssl enc -bf -salt -in foo.txt -out foo.enc -e -a
```

**Decrypt**
```
$ openssl enc -bf -in foo.enc -out foo-clear.txt -d -a
```

---

The "encrypt" command uses the Blowfish cipher to encrypt, and then base64-encode, foo.txt. The resulting file is foo.enc. 

The "decrypt" command base64-decodes, and then decrypts, foo.enc. The resulting file is foo-clear.txt. 

I highly recommend reading the enc(1) manpages. There are several ciphers to choose from.

---

### Post by bodhi.zazen on 2010-06-01
Try cryptkeeper and keepassx , both are in the repositories.

[http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html](http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html)

[http://www.keepassx.org/](http://www.keepassx.org/)

What problem are you having with encryption ? If you loose a password, you will have data loss with all encryption technologies, such is the nature of encryption (that is kind of the point).

Understanding how these things work is, IMO, the best protection against data loss.

---

### Post by 1awesomeguy on 2010-06-02
> **anomie said:**
> CLI OK? 

I like openssl for this purpose. Most general-purpose Linux systems have it installed. (Keep in mind that the password you provide will be used to generate an encryption key.) 

**Encrypt**
```
$ openssl enc -bf -salt -in foo.txt -out foo.enc -e -a
```

**Decrypt**
```
$ openssl enc -bf -in foo.enc -out foo-clear.txt -d -a
```

---

The "encrypt" command uses the Blowfish cipher to encrypt, and then base64-encode, foo.txt. The resulting file is foo.enc. 

The "decrypt" command base64-decodes, and then decrypts, foo.enc. The resulting file is foo-clear.txt. 

I highly recommend reading the enc(1) manpages. There are several ciphers to choose from.

Thanks! I asked MetaFilter this same question and the two recomendations which people gave me that fit the bill perfectly seemed be be gpg using the -c parameter and openssl. I have not used openssl, but will look into it some more. It looks to be what I am looking for!

When you say "the password you provide will be used to generate an encryption key"... Does that mean, I need to save this key elsewhere, or can I just use my password to decrypt information on any computer? My main problem with the Seahorse program is the use of key files I need to store.

> **bodhi.zazen said:**
> Try cryptkeeper and keepassx , both are in the repositories.

[http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html](http://subbass.blogspot.com/2009/09/howto-simple-encrypted-folder.html)

[http://www.keepassx.org/](http://www.keepassx.org/)

What problem are you having with encryption ? If you loose a password, you will have data loss with all encryption technologies, such is the nature of encryption (that is kind of the point).

Understanding how these things work is, IMO, the best protection against data loss.

Thanks! I always thought those two programs were more for storing passwords. I am looking to encrypt plain text content with a password. But I will look into those solutions.

I understand how encryption works and the reason it was developed. I like encryption, but do not like using the most standard systems which require maintaining separate key files and remembering passwords. Seahorse and PGP are mainly used for email communication as far as I know (which is the reason public and private key files are used). I am looking for a solution which I do not need to bother with key files. I never forget my passwords, but have lost key files several times. It is just not worth the risk for me.

Another issue I have faced was faulty programming in the default Ubuntu /home encryption program which lead to many many hours of work on my part to decrypt my /home directly (even with the proper password and passphrase). There is already a bug report on this issue and it will hopefully be fixed in the near future. I have also had problems decrypting text due to an unrelated bug in the Gedit Seahorse plugin.

---

### Post by anomie on 2010-06-02
[QUOTE=1awesomeguy]When you say "the password you provide will be used to generate an encryption key"... Does that mean, I need to save this key elsewhere, or can I just use my password to decrypt information on any computer?[/QUOTE]

The encryption key will be derived from the password your provide. You won't need to hang onto an external key file in this case. So, for your purposes, really you just need to remember a password. 

I wanted to mention all this because you seemed adamant to not have to use a key, but it's important to note that [encryption](http://en.wikipedia.org/wiki/Encryption) *requires* a key. There's a huge difference between a "password-protected" plain text file and an encrypted file where a key is derived from a password. (The former is virtually useless.)

---

### Post by Bachstelze on 2010-06-02
> **anomie said:**
> 
I wanted to mention all this because you seemed adamant to not have to use a key, but it's important to note that [encryption](http://en.wikipedia.org/wiki/Encryption) *requires* a key. There's a huge difference between a "password-protected" plain text file and an encrypted file where a key is derived from a password. (The former is virtually useless.)

The difference between a key and a password is mostly terminology, though. A key is really just a long password (or a password is a short key, depending on your point of view). I remember back in Cryptology 101, we used to encrypt text (by hand, with pencil and paper) using RSA with a 8-bit key that was generally a two-letter word. Is it a password or a key, then?

---

### Post by anomie on 2010-06-02
[QUOTE=Bachstelze]The difference between a key and a password is mostly terminology, though.[/QUOTE]

My point was "password protection" (i.e. a hurdle a given app throws in the way) without encryption is a very different animal, and should not be considered secure. OP seeks to avoid a *key file*, not a *key* (and in the context of this thread, the distinction is more than just semantics, IMO).

---

### Post by frostschutz on 2010-06-02
I just use gpg -c ...

---

### Post by rookcifer on 2010-06-02
Why not just go ahead and generate a GPG key?  You can use it for just about every form of encryption (except disk encryption).

```
gpg --gen-key
```

Pick RSA/RSA, enter your email address and desired pass-phrase and you're ready to go.  From there you can just right click any file and it will encrypt it with the key.  Just backup the .gnupg folder somewhere so you can transplant the key if you ever reinstall or get a new machine.

Of course, you can also do as suggested above:

```
openssl aes-256-cbc -a -salt -in secret_file -out new_secret_file
```

decrypt:

```
openssl aes-256-cbc -d -a -in new_secret_file -out secret_file
```

Personally I like having a GPG key so that I can also use it for e-mail encryption and authentication.

---

### Post by 1awesomeguy on 2010-06-03
> **anomie said:**
> I wanted to mention all this because you seemed adamant to not have to use a key, but it's important to note that [encryption](http://en.wikipedia.org/wiki/Encryption) *requires* a key. There's a huge difference between a "password-protected" plain text file and an encrypted file where a key is derived from a password. (The former is virtually useless.)

Right! Thanks for clarifying to everyone. My thread title is a little bit incorrect. What I wanted to do is generate an encrypted file with only a password (on the fly) instead of a password and a key file which I must save separately. I just wanted to avoid a key file. I agree with you that a password-protected text file is virtually useless and much less secure.

Though Bachstelze makes a good point that passwords and keys are virtually the same thing. The main difference we were talking about is generating a key on the fly from a password using 128 or 256 bit encryption versus securing a text file with just the password itself. The former is secure while the latter can be easily hacked (depending on your password complexity).


> **rookcifer said:**
> Why not just go ahead and generate a GPG key?  You can use it for just about every form of encryption (except disk encryption).

[...]

Just backup the .gnupg folder somewhere so you can transplant the key if you ever reinstall or get a new machine.

I never knew where the key files were kept to be honest. Now, thinking about it, it is obvious that they would be in my /home directory. Still, however, if the file ever becomes corrupt or if something happens to my key file or if there is a bug in Seahorse, all my data would be rendered useless. It seems like such a big risk that can be avoided by using gpg -c.

What are the advantages of using a key file in addition to a password with GPG?

Assuming I tell nobody about my password, the only way for a person to decrypt my files would be with a brute force attack. If I use gpg -c and 256 bit AES encryption, it would still take many many years for a computer to be able to decrypt the information:

> AES permits the use of 256-bit keys. Breaking a symmetric 256-bit key by brute force requires 2128 times more computational power than a 128-bit key. A device that could check a billion billion (1018) AES keys per second would require about 3×1051 years to exhaust the 256-bit key space. - [Wikipedia]("http://en.wikipedia.org/wiki/Brute_force_attack")

---

### Post by rookcifer on 2010-06-03
> **1awesomeguy said:**
> I never knew where the key files were kept to be honest. Now, thinking about it, it is obvious that they would be in my /home directory. Still, however, if the file ever becomes corrupt or if something happens to my key file or if there is a bug in Seahorse, all my data would be rendered useless. It seems like such a big risk that can be avoided by using gpg -c.

That's why there's something called backups.  Backup the key on physical media locally and also send it to a remote server like Ubuntu One.  You can encrypt the key before sending it to a remote server (actually the password that is generated for the key upon creation is used to encrypt the private key, so even if an attacker had access to your private key it would be worthless without the password).  Besides, even if you do lose the key, it's not the end of the world if you have a revocation cert.

> What are the advantages of using a key file in addition to a password with GPG?

The key file is encrypted and that encryption can only be unlocked by the password.  That is because a private key is, well, private, and if a villain has access to it, it's game over for all your past and future encrypted data.  SSH, for instance, allows you to create keys without passphrases, but if a villain gets access to your PC and is able to physically steal the key, it's game over.  GPG, by default, makes you create a password (though I am sure this can be overcame somehow).  Again, the password is what keeps your key "physically" secure from malicious people who have either physical access to the machine or have somehow cracked the machine.

> Assuming I tell nobody about my password, the only way for a person to decrypt my files would be with a brute force attack. If I use gpg -c and 256 bit AES encryption, it would still take many many years for a computer to be able to decrypt the information:

Please understand that your encryption likely will not be as strong as AES-256 even if the cipher used is AES-256.  Why?  Because the encryption is only as strong as the weakest link in the chain, and most certainly that weakest link will be your passphrase.  If your passphrase is not equal in strength (or entropy to be more precise) to AES-256, then it will be the weak link.  It will be *much* easier for a villain to brute force your 50-60 bit passphrase than to brute force a 256 bit AES key.  Bottom line: if you want AES-256 protection, you need to use a 256 bit passphrase, which, unless you are Rainman, will be difficult for anyone to remember.

Here is an example of a 256 bit passphrase (255.5 bits to be precise):

```
O85fbC]SB$Txc6hW}IA*S$qfT}S_mcw1Gk(^\C2
```

Is your passphrase this strong and random?  If not, you are wasting resources by using AES-256.  You would be better off with AES-128 (which is still incredibly resistant to brute force).

---

### Post by 1awesomeguy on 2010-06-03
rookcifer everything you said does make sense. I tested my typical password strength using some statistical analysis and it is not as secure as I thought. The passwords themselves would take about 150 days to brute force as opposed to many many years. This may still serve my purpose however. The little-bit-worst security is probably worth the convenience. For more important files, I will probably still use normal key files.

---

### Post by The Cog on 2010-06-03
I can well understand wanting to just use a passphrase and not rely on a key file. You say it is weaker, but I would probably use a sentence, maybe like this:
> Bottom line: if you want AES-256 protection, you need to use a 256 bit passphrase.
Does that seem reasonable?

---

### Post by rookcifer on 2010-06-03
> **The Cog said:**
> I can well understand wanting to just use a passphrase and not rely on a key file. You say it is weaker, but I would probably use a sentence, maybe like this:

Does that seem reasonable?

For marginal security, that's fine.  For real security, no.  The reason is that it contains nothing but English words and a few numbers.  That is, the entropy is not very great and a dictionary attack would likely be effective in a relatively short time period.

---

### Post by 1awesomeguy on 2010-06-04
> **rookcifer said:**
> For marginal security, that's fine.  For real security, no.  The reason is that it contains nothing but English words and a few numbers.  That is, the entropy is not very great and a dictionary attack would likely be effective in a relatively short time period.

Well this may be true for typical computer users, but I and probably most (?) current Ubuntu users probably do not use weak passwords with real dictionary words in them. At least I hope!

Related: > "NIST recommends 80-bits for the most secure passwords, which can nearly be achieved with a 95-character choice (e.g., the original ASCII character set) with a 12-character random password (12 x 6.5 bits = 78). [[2]("http://en.wikipedia.org/wiki/Password_strength#cite_note-NIST-1")]"

---

### Post by anomie on 2010-06-04
[QUOTE=1awesomeguy]What are the advantages of using a key file in addition to a password with GPG?[/QUOTE]

Since you asked, another big advantage of this (and [asymmetric encryption](http://en.wikipedia.org/wiki/Public-key_cryptography), in general) is: 
[list]
[*] You can encrypt data using the public key. 
[*] To encrypt data, you must use the private key. 
[/list]

This means you can safely share your public key with others. They'll be able to encrypt (but not decrypt) data using that public key. 

Other implications? You can keep *just* the public key on a system where data needs to be encrypted; if the system is compromised, there is no private key on the system to aid with an attack. 

As for GPG backups, there are some export commands available to capture your keys and trust db, or you can simply back up ~/.gnupg.

---

### Post by anomie on 2010-06-04
[QUOTE=rookcifer]Bottom line: if you want AES-256 protection, you need to use a 256 bit passphrase, which, unless you are Rainman, will be difficult for anyone to remember.[/QUOTE]

Hash your password? 

```
$ _HASHED=$(echo ${_MYPASS} | openssl dgst -sha256)

$ openssl enc -aes256 -in foo.plain -out foo.enc -pass env:_HASHED -e -a
```

All you need to remember is the password.

---

### Post by 1awesomeguy on 2010-06-04
> **anomie said:**
> Hash your password? 

```
$ _HASHED=$(echo ${_MYPASS} | openssl dgst -sha256)

$ openssl enc -aes256 -in foo.plain -out foo.enc -pass env:_HASHED -e -a
```

All you need to remember is the password.

This is a really interesting approach. I will think a lot about this and try to come up with a good script I would be able to use securely.

The main problem I see with the above is that it can expose your plain text password in terminal or in the terminal log. Another problem is that if I create a script for this and store it in a place a possible cracker can easily find, it renders the whole hashing process almost useless. Nonetheless, this is the best solution I have seen for what I am trying to do and get the same level of protection as using key files (it basically does the same thing, but on the fly). I will try to come up with a cleaver way of using this practically in some sort of script. I am all ears if anyone has any suggestions!

---

### Post by rookcifer on 2010-06-04
> **anomie said:**
> Hash your password? 

```
$ _HASHED=$(echo ${_MYPASS} | openssl dgst -sha256)

$ openssl enc -aes256 -in foo.plain -out foo.enc -pass env:_HASHED -e -a
```

All you need to remember is the password.

A hash is nothing but a one-way function that is easy to create but very difficult to reverse.  Theoretically, it should be very difficult to find two messages that have the same (or partially the same) hash.  If such messages are found (and they are occasionally), the hash function is known to have "collisions."  MD5 has been, for the most part, broken due to all the collisions that have been found, and SHA-1 has theoretical flaws. (SHA-224, 256, 384, 512 are still secure).  In other words, every character, word, and group of words has an accompanying hash.

In any case, my point is that hashing a weak password is really not that much protection because of the phenomenon known as Rainbow tables.  A Rainbow table is simply a dictionary of passwords *and* their accompanying hashes.  So if you create a password like "p@$$word" and then hash it and think you have suddenly created a 256 bit password, you're wrong.  A Rainbow table will have that password hash in its database and will crack it in seconds.

For instance, the SHA-1 hash for "p@$$word" is:

```
578329e138895c329e97ed0f3da0dd81aeb64b19
```

p@$$word will *always* have this same SHA-1 hash and the Rainbow Tables will have it indexed.

Bottom line:  there is no substitute for a good, long, random password.  The problem is remembering them.

---

### Post by anomie on 2010-06-05
For the record, I wasn't implying that creating a 256-bit hash based on a weak password was the same as creating a strong 256-bit password, or that this would survive a dedicated offline attack. But this extra step makes it marginally more computationally expensive, and significantly more cumbersome to determine the encryption key.

---

### Post by 1awesomeguy on 2010-06-05
Couldn't you just encrypt a file with a strong hash? No one would know you used a hash, what hash function you used, what salts you added to the original password, etc. You then just need to remember your password and the hash you used. Whenever you want to decrypt your file, you just open up a web browser or terminal and find out the hash of your password... Assuming you used a strong encryption and hash function, this method would theoretically stand up to any brute force attack (due to physics and the limits of computer power)...

Even if you use anomie's method in a script that does both hashing and encrypting/decrypting together, if the cracker does not have access to the script or know where to look for it, it would still be impossible to brute force the file.

---

### Post by anomie on 2010-06-05
@1awesomeguy: That's the idea I am floating as slightly better than using a less-than-ideal password (i.e. hash it first.) 

When thinking through attack scenarios, though, be sure to consider one where the attacker understands the way you implemented your encryption. Otherwise, we'd be relying on obscurity, which is not real security. ;)

---

