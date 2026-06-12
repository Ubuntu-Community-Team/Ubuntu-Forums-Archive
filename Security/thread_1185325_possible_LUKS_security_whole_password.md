---
title: "possible LUKS security whole: password"
date: 2009-06-12
forum: Security
---

### Post by gagatz on 2009-06-12
hi folks, 

Is the following attack on LUKS possible? (Eve tries to attack Alice's computer)

Eve waits until Alice leaves her computer (switched off) unattended, installs some keylogger in the boot-partition (which is where also the decryption program lies?) and modify grub or whatever to first start the keylogger and then the encryption thing.

Alice switches on her computer enters password, keylogger writes it into a file in the bootpartition. Alice writes some gpg-encrypted loveletters to bob and switches off her computer.

Eve returns to the computer and reads the passphrase from the file. Done.

Although I have no clue about actual programming this, it is an obvious possibility.
My solution would be to have a program in the encrypted part, that computes some sha-1 hashsum of the whole boot sector before and after boot and gives a warning if something changed (possibly noting the change).

A friend of mine has written part of such a script (in german) and it detects changes in /boot.

Have the developers taken care of this thing, or is the attack impossible anyway?

gagatz

---

### Post by grantemsley on 2009-06-12
If they have physical access to the machine, no amount of software is going to prevent a smart, determined attacker from breaking your security.

Even if you checked hashes on boot...what stops Eve from updating the hash when she installs the keylogger?

More importantly, what prevents Eve from installing a hardware keylogger attached to (or even inside!) Alice's keyboard?

If they can do things to your computer while you are not there to supervise, there's nothing you can do.  You can make it more difficult for them, but never impossible.

---

### Post by HermanAB on 2009-06-12
Encryption protects your data at rest - that is all.  It doesn't protect your data when the system is running.

---

### Post by bodhi.zazen on 2009-06-12
People who worry about such things md5sum (or sha256 or whatever) the contents of /boot

One can install not only a key logger, how about a custom kernel ?

The weak link here is physical access.

---

### Post by rookcifer on 2009-06-12
If you're worried about the /boot partition being compromised, then put it on a detachable USB flash drive.  That's really the only way to protect your install when other potentially malicious people have access to the machine.

---

### Post by Jekshadow on 2009-06-13
A hash could be forged, and the kernel could be replaced. Like rookcifer said, the most secure way would be to put the /boot partition on a totally separate device, even though if you lose that device, it would be hard to recover your data. I would recommend restricting physical access and if you are really that worried, setup your drive encryption to use your fingerprint to decrypt the drive, a large amount of modern day laptops have fingerprint scanners.

---

### Post by bodhi.zazen on 2009-06-13
forging a sha256 has on a custom kernel can be done in theory. In practice good luck.

Now add in initrd ...

And anyone concerned about hashing uses more then one, so now add in say md5sum, which is weaker then sha256, yet still ...

The hashes should be kept on the encrypted partition and from there it is simple to check the has during the boot process.

I would love to see you provide a custom kernel which passed these hash tests (I understand yo may not know how), but it is not really as easy as you say.

---

### Post by gagatz on 2009-06-17
Well I appreciate your answers. Of course keyloggers might be installed physically. Thats another thing I am just thinking of, might post the idea somewhere else.
I don't know to much about these kernel things, so I ask: If we would include such a test in the LUKS encryption, then there would be a predetermined location (on the encrypted part) where the checkingscript and the checksums lie. Would an intruder be able to manipulate the kernel in a way that instead of really calling the checksumscript he would just say 'yes, i checked the /boot, nothing changed, trust me'? Then the whole checking-thing wouldn't make any sense, would it?

---

### Post by bodhi.zazen on 2009-06-17
> **gagatz said:**
> Well I appreciate your answers. Of course keyloggers might be installed physically. Thats another thing I am just thinking of, might post the idea somewhere else.
I don't know to much about these kernel things, so I ask: If we would include such a test in the LUKS encryption, then there would be a predetermined location (on the encrypted part) where the checkingscript and the checksums lie. Would an intruder be able to manipulate the kernel in a way that instead of really calling the checksumscript he would just say 'yes, i checked the /boot, nothing changed, trust me'? Then the whole checking-thing wouldn't make any sense, would it?

Not without knowing your script / checksum.

There are too many strategies, and the scripts are all encrypted.

So you could  call a script from /etc/rc.local , you could write a boot script, you can write a log in scrpit, etc, etc.

And what will that script check exactly ? md5sum , sha1, sha256 ?
And on what ? kernel, initrd, grub (all stages), and menu.lst ?
Where do you store the sums ? local (encrypted disk? /etc ? /root ? ) or on a flash drive ?

Is your script written in bash ? Python ? perl ? C ?

Way too many variable here. Sure it is possible in theory, but in practice I doubt it.

---

### Post by The Tronyx on 2009-06-17
Why do people love to play the games of 'what if' concerning physical access?  If they have physical access they can steal your laptop and figure out what to do with it in the mean time.

These physical access threads are both old and busted.

---

### Post by gagatz on 2009-06-18
> **bodhi.zazen said:**
> Not without knowing your script / checksum.

There are too many strategies, and the scripts are all encrypted.

...

Way too many variable here. Sure it is possible in theory, but in practice I doubt it.

I am not thinking of a solution for a single pc (where noone could figure out all the things you mentioned, since the solution is always individual) but to include it at every luks installation. Then it would be in the code (luks installation files), where the script etc. lies and an intruder could use that information. 
a way out here is, to have kind of randomization during the install, so the path to the checksums and script is not determined by the code and, hence the same for each insallation but different for every pc. but these are all quite technical questions and i think i contact the developers to tell them about the idea, maybe they want to include it. i don't have a clue, about actually writing such a program.

greetings, gagatz

---

