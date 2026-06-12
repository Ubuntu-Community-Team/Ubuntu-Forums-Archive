---
title: "Password required to Encrypt home folder"
date: 2012-04-23
forum: Security
---

### Post by wh33t on 2012-04-23
Hey Ubucrew,

I've got a rather general question about Encrypted home folders. First off, I'd like to know what exactly that means. Does that mean that my home directory is somehow scrambled? And if so, does that mean if someone put a LiveCD into my computer and booted to a Ram environment linux (like the Ubuntu installer for example) would they not be able to see my home directory? If they couldn't see it, what would they see instead?

Lastly, twice now my computer has asked me to generate the passphrase to recover my password. Is this because I installed the latest updates?

I'm on Ubuntu 10.04 LTS

---

### Post by ortermagic on 2012-04-23
Be very careful with the encrypt home folder option...If, for whatever reason you have to ever do a complete reinstall you will not be able to recover your docs from the encrypted file. I had a problem when I first tried Natty. I installed compiz (turned out there were bug issues between unity and compiz) lost all desktop functionality. Forgetting that I had encrypted I went ahead and made copies of everything in home (luckily not a lot) to a dvd.
 Later when I tried to drop them back into a freshly installed 11.04 I discovered that they were all unreadable.  I had reformatted and reinstalled over the original encrypted Natty, thereby losing it forever  (are files like these decryptable forensically, I wonder?)
So, I'm just warning you to be very careful with home folder encryption and ensure you keep the unlock code in a safe place.
So far I have not been able to restore any of the encrypted files on the dvd, if anyone has a solution I would be interested to hear.

---

### Post by rookcifer on 2012-04-23
> **wh33t said:**
> Hey Ubucrew,

I've got a rather general question about Encrypted home folders. First off, I'd like to know what exactly that means. Does that mean that my home directory is somehow scrambled? 

Yes.  That's what [encryption]("https://en.wikipedia.org/wiki/Encryption") does -- scrambles data so that it cannot be read by anyone who does not have the key.

> And if so, does that mean if someone put a LiveCD into my computer and booted to a Ram environment linux (like the Ubuntu installer for example) would they not be able to see my home directory? If they couldn't see it, what would they see instead?

They could not see your data.  Instead if they looked at it (with a hex editor for instance) they would see random hex data that makes no sense.  

> Lastly, twice now my computer has asked me to generate the passphrase to recover my password. Is this because I installed the latest updates?

I'm on Ubuntu 10.04 LTS

It's probably just asking for you to create a password so that if you get locked out of Linux somehow you can still access the data through some other means with the password.  But, I don't know for sure as I don't use the option. (I hate it, not because it doesn't work, but because of how it works.  I much prefer to use LUKS/dm-crypt to encrypt my entire operating system).

---

### Post by wh33t on 2012-04-23
> **rookcifer said:**
> YI hate it, not because it doesn't work, but because of how it works.  I much prefer to use LUKS/dm-crypt to encrypt my entire operating system).

Does that slow your machine down quite a bit? I guess it would boot to a password screen which would decrypt your entire OS?

ortermagic also had an interesting question. He copied over his Encrypted home directory to a disk but till this still hasn't retrieved it. Is there any utility out there that can brute force the encryption until they get access to it? I'm probably ok with that, as long as it takes a little while, more while than it's worth is what I'm thinking.

---

### Post by rookcifer on 2012-04-23
> **wh33t said:**
> Does that slow your machine down quite a bit? I guess it would boot to a password screen which would decrypt your entire OS?

Won't be noticeable on a modern CPU.

> ortermagic also had an interesting question. He copied over his Encrypted home directory to a disk but till this still hasn't retrieved it. Is there any utility out there that can brute force the encryption until they get access to it? I'm probably ok with that, as long as it takes a little while, more while than it's worth is what I'm thinking.

There is nothing that can brute force it.  If there were, it would make the encryption pretty worthless.  The only thing an attacker could do would be to brute force your *password.*

---

### Post by wh33t on 2012-04-23
> **rookcifer said:**
> There is nothing that can brute force it.  If there were, it would make the encryption pretty worthless.  The only thing an attacker could do would be to brute force your *password.*

Of course! The password. I guess depending on how good your password is the longer/shorter it takes to brute force it. It could be brute forced fairly quickly these days couldn't it? Surely a modern cpu could run through millions of possible password combinations every hour or so?

---

### Post by Hungry Man on 2012-04-23
How quickly it can be bruteforced depends on what method the password is hashed. Different hashing mechanisms taken different amounts of time + you can hash multiple times (multiple passes) to increase bruteforce time.

I don't know what Ubuntu uses. Just use a 12+ character password and you're fine.

---

### Post by rookcifer on 2012-04-24
> **wh33t said:**
> Of course! The password. I guess depending on how good your password is the longer/shorter it takes to brute force it. It could be brute forced fairly quickly these days couldn't it? Surely a modern cpu could run through millions of possible password combinations every hour or so?

Basically what Hungryman said.  There is a standard for password hashing known as [PBKDF2]("https://en.wikipedia.org/wiki/PBKDF2") which basically runs your password through a hash a bunch of times so that it takes longer to access the volume with the password (that's a very simplified description).

I don't know if the /home folder encryption does this or not.  But, as Hungryman said, just use a good strong password and it shouldn't be an issue anyway.  12+ characters with upper/lowercase and a few numbers is good enough.

---

### Post by wh33t on 2012-04-27
> **rookcifer said:**
>  I much prefer to use LUKS/dm-crypt to encrypt my entire operating system).

I've been trying to find guides on LUKS/dm-crypt and I can't seem to find any ones that really explain what I'm looking for. Can you recommend any guides on how to encrypt the entire Ubuntu OS?

---

### Post by Blackbird_13 on 2012-04-27
As someone who knew nothing about encryption I followed this guide and it worked for me.

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

---

### Post by rookcifer on 2012-04-27
> **wh33t said:**
> I've been trying to find guides on LUKS/dm-crypt and I can't seem to find any ones that really explain what I'm looking for. Can you recommend any guides on how to encrypt the entire Ubuntu OS?

Follow the guide Blackbird posted.  Also, just to be clear, you will need the alternate installer CD.  The regular install CD will *not* work.

---

### Post by wh33t on 2012-04-27
> **rookcifer said:**
> Follow the guide Blackbird posted.  Also, just to be clear, you will need the alternate installer CD.  The regular install CD will *not* work.

Darn, Ok. I'll give that a shot.

---

### Post by Blackbird_13 on 2012-04-28
One further thought.

I usually test new things in a virtual environment using VirtualBox. This means that any errors I make don't matter as they can't impact on my real operating system. I also find that I usually want to tweak my initial configuration when I trial something new and this is very easy to do in VirtualBox.

---

