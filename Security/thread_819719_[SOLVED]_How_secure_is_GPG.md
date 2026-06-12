---
title: "[SOLVED] How secure is GPG?"
date: 2008-06-05
forum: Security
---

### Post by Rytron on 2008-06-05
How secure is GPG? Is it Hardware proof & US DoD standard?

I refer to using GPG in this way and not with public keys(haven't figured out yet public keys):

```
gpg -c filename

```

Any ideas welcome. Thanks.

---

### Post by F4l3 on 2008-06-05
In every case you create and use public keys ;).

Actually GPG have never been broken and is an asymmetric cryptation system.
Right now is impossible to say how much is secure, and this will be until someone will be able to break it. If you want be more sure, you can create longher keys (ie 2048).

---

### Post by Dr Small on 2008-06-05
If you are still interested, stop by and read my Beginners Guide to GnuPG:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

---

### Post by kevdog on 2008-06-05
GPG can work with asymmetric and symmetric keys.  Symmetric keys are otherwise known as a password -- ie gpg can use a symmetric cipher to encrypt a file and later decrypt the file use the same password.  GPG with the use of asymmetric keys (the GPG use most people think of) actually uses a combination of asymmetric and symmetric methods.  The asymmetric key is used to encrypt a randomly generated session key.  The session key on the otherhand is the password, used for the symmetric encrypting of the contents of the email, file, etc.  With decryption, the other private encryption key decrypts the session key, which in turn decrypts the  letter,file contents.

How secure is GnuPG?  Who really knows?  Only the NSA knows for sure -- and you think they would tell us?  By best accounts from the world's leading mathematicians however, the algorithms used with GnuPG today would take the best computer, many years to break (if at all).  Again however, the downside of gnupg, is the loss of the password, or private keys.  Its much easier for a rogue per se to do something to obtain the keys through subversive another process, than break the underlying algorithm.  This topic has been brought up many times on the gnupg mailing list!

---

### Post by AndyCee on 2008-06-05
GPG, replaces PGP.

How good?
By definition: "Pretty Good".

But Kevdog, isn't GPG open-source? Why do you say "Only the NSA knows"?

---

### Post by Dr Small on 2008-06-05
> **AndyCee said:**
> GPG, replaces PGP.

How good?
By definition: "Pretty Good".

But Kevdog, isn't GPG open-source? Why do you say "Only the NSA knows"?
I thought I read somewhere awhile back that it is possible that the NSA has a backdoor in GPG 1.5

---

### Post by kevdog on 2008-06-05
GnuPG is open source, PGP is not.  GnuPG did not replace PGP, PGP is very much alive: [http://www.pgp.com/](http://www.pgp.com/).  Both adhere to the OpenPGP standard (which is a minimum).  Both however do things differently by choosing different default algorithms, hashes, etc. plus additional added features not specified by the OpenGPG standard.  

If the NSA does have a backdoor in Gnupg 1.5 that would be the first I know about it.  Its possible, however the code is after all opensource.  By meaning a backdoor, could you be more specific?  I've never heard Werner Koch address these rumors.  If you know a link I'll post the question on the gpg mailing list (and likely be taken to task by Robert Hansen --- however its always fun to bring up controversy!)

---

### Post by Dr Small on 2008-06-05
I probably read about it on Slashdot awhile back (like that means anything...). I can't find any links to it, so it was probably just a rumor I read anyhow.

---

### Post by kevdog on 2008-06-05
Not that this is the best source -- I found it like the 4th link on Google:  [http://www.wilderssecurity.com/showthread.php?t=199105](http://www.wilderssecurity.com/showthread.php?t=199105)

Its apparently related to PGP -- whole disk encryption -- and is really second or backup password.  I'm not sure this counts as a backdoor, but some find it objectionable.

Again GnuPG has no such mechanism.

---

### Post by abiallan007 on 2008-10-16
Use public keys every where:)

---

### Post by kevdog on 2008-10-18
???:confused:

---

### Post by bnsmith001 on 2010-01-21
Okay, this is **not a definitive answer** if you risk downloading a precompiled version from someone who you are not completely confident did not build a "back door" into the tool that you are installing.  Yet, if you get the source, review it yourself, and then compile it, you should be completely safe.


**Phil Zimmerman** on his "[_No Back Doors_]("http://www.philzimmermann.com/EN/faq/index.html")" page states clearly that the source code for PGP is available.  You can download the source, and take your time reading through the source.  Legally, you cannot change the source, because the source is patented or copywritten, and the patents/copywrights are owned by [_PGP Corporation_]("http://www.pgp.com/?l=prz"). 


- **PGP** -
If you are confident that the source did not contain a "back door", then you can compile it and use the compiled version with complete confidence that there is no Government/Investigators key that allows law enforcement to open any file without throwing massive amounts of CPU time into cracking a decryption key (might not be your key)... and that your unchanged compiled version of PGP abides by the laws in the US and outside.

Last point on PGP product - 
You put your privacy at risk if you download a pre-compiled version of PGP that does not identically match the compiled version that you could have created by compiling it yourself.


- **GPG** -
GNU Privacy Guard (also known as "Gnu PG" and GPG) are Open Source products.  They also distribute for FREE "original" source distributions, which you can read to verify that GPG is safe and has no "back doors". Then, you can use the included "make" to build your "safe" executable GPG tool, and encrypt safely. As with PGP, GPG is safe... in that law enforcement cannot open any file without throwing massive amounts of CPU time into cracking a decryption key, especially if you take the extra step of never storing your key on any computer which you use.

Last point on GPG -
(very similar to the last point on PGP above) 
You put your privacy at risk if you download a pre-compiled version of GPG that does not identically match the compiled version that you could have created by compiling it yourself.


**Lay persons description of Encrytion/Decryption process** --
GPG and PGP both define a keypair. The public key is used to encrypt, and the private/secret key is used to decrypt.  You share your public key (including posting the public key on keyservers) with other people's keys so that you can can exchange encrypted notes and files with each other. You keep your private key private and post it **_nowhere_**.

Okay, once law enforcement officers (LEOs is an acronym that I have seen) find any note/file to decrypt, they can get a list of keys used to encrypt the message/file from a GPG or PGP tool, but they cannot decrypt everything on your computer, especially if you have taken the step to remove your keys and keyrings from your local computer.  Besides, if multiple keys or different groups of keys are used to encrypt a note or file, they can analyze the file for a long while, and they may find one of the keys and get access to much of the encrypted data on your computer. Yet if you encrypt to multiple groups of people, then their job is more complicated.  So long as you NEVER post your private key online (which is REALLY the whole idea behind a keypair containing a public key and a private/secret key) then they will have to dedicate time and money to recreate your private key if it is not present on your computer. To complicate things even more, encrypt some files on your computer to others without encrypting to yourself. This will confuse them even more.

The only "rub" is that most of the time, keyrings and decryption keys are usually stored on the local computer hard drives, accessible by a local install of GPG.  If you were to get a small USB drive (I'm working on what the minimum requirements would be) and install a portable version of GPG there (along with any GUI for your OS) and store all keys and keyrings and related GPG config and trust and keyrings etc on the USB, then you would have a portable GPG solution that also contained all of your encryption and decryption keys.

This would force LEOs to take the long method in having to crack your key (investing years of processing time).

**All-in-all** GPG is as secure as your habits are.

Peace.

---

### Post by Rytron on 2010-01-21
Hello bnsmith001. Thanks for the info.

---

### Post by zollie on 2010-01-21
It'd be much easier for law enforcement to beat the password outta you than try to crack it with supercomputers.

Widespread availability of quantum computing will mean the end of ALL cryptography based on prime number factorization.  (this means GPG/PGP, etc.)

The gov DOES have quantum encryption deployed already but as far as we know, real quantum computing is still many years away.

Quantum encryption in THEORY is unbreakable, however real world implementations have sometimes been shown to be vulnerable.

---

### Post by rookcifer on 2010-01-21
> **dr small said:**
> i thought i read somewhere awhile back that it is possible that the nsa has a backdoor in gpg 1.5

lol

---

### Post by Jekshadow on 2010-01-24
As long as you use strong keys and and encrypt/hide your private keys (2 layers of 2048 bit encryption minimum), GPG is nearly unbreakable. It would be easier, cheaper and faster for the NSA to torture you until you gave them the info they needed.

---

### Post by tubbygweilo on 2010-01-24
IIRC the secret key without the pass phrase is not worth all that much [but]("http://xckd.com/538/")...

---

### Post by rookcifer on 2010-01-24
> **Jekshadow said:**
> As long as you use strong keys and and encrypt/hide your private keys (2 layers of 2048 bit encryption minimum), GPG is nearly unbreakable. It would be easier, cheaper and faster for the NSA to torture you until you gave them the info they needed.

Yep.  Trying to brute force a 128 bit random key would be a futile endeavor, even if *every computer on earth* tried to crack it at once.  It would still take longer than the age of the universe.

Then you have to take into account the Von Neumann-Landauer Limit.  This is a theoretical lower limit on how much energy it takes for a computer to "fight" the entropy that the actual computation takes.  In other words, the laws of thermodynamics dictate that all computers must use a minimum amount of energy in order to make a computation.  So, if one was to use supercomputers to try and brute force a 128 bit cipher, they would need *nuclear power plants* dedicated to the attack.  This is not feasible, even for the NSA.

Basically the NSA can crack your keys in three possible ways:

1) A side-channel attack.  This is an error in the encryption implementation and not a flaw in the cipher itself.  This also includes BIOS rootkits and the "evil maid" attack.
2) Brute Forcing the key (impossible as I outlined above)
3) Mathematically breaking the cipher.  This would mean the NSA has a mathematical genius working for it (possible but unlikely).
4) Torturing you (the most likely scenario)

---

