---
title: "Whole DIsk Encription"
date: 2006-09-17
forum: Server Platforms
---

### Post by yustr on 2006-09-17
Does anyone know of an application that will encript an entire HD? I'm using 6.06.

The ideal would be one that allows me to open the drive for an entire session then close it once on save. I'd hate to have to enter a PW on every file save but I could make that work.

---

### Post by Jussi Kukkonen on 2006-09-18
Cryptoloop would be the normal solution I believe: [http://encryptionhowto.sourceforge.net/Encryption-HOWTO.html](http://encryptionhowto.sourceforge.net/Encryption-HOWTO.html)

You might want to look at TrueCrypt too ([http://www.truecrypt.org/](http://www.truecrypt.org/)). this is new though, and hardly proven.

Both methods require kernel recompiles, I believe.

---

### Post by skymt on 2006-09-18
There's already a [HOWTO](https://help.ubuntu.com/community/EncryptedFilesystemHowto) for this on the Wiki.

By the way, Truecrypt doesn't need a kernel recompile, it just needs to be compiled for your kernel. You just need to grab the appropriate kernel-source package.

---

### Post by yustr on 2006-09-18
The article mentioned by Jussi is 6 years old and according to the HOWTO: 

>   This is not finished (but then isn't this the nature of the web?)
    These procedures could damage the information on your computer. Make backups first.
    Be careful. Read the documentation, again. You have been warned. Twice.

Anybody know of anything current & proven?

---

### Post by karamba_kid on 2006-09-18
Remember encryption is only secure if it's correctly implemented.  That means make sure the swap partition is also encrypted or disabled (if you have enough memory for that). Also if you have a processor with HyperThreading I believe disabling that feature would be a smart move.

---

### Post by skymt on 2006-09-19
Truecrypt is probably what you want. It's stable, current, proven, and very secure. See the [homepage](http://www.truecrypt.org/) for more information. Note that the Ubuntu packages they provide probably won't work, you need to compile it yourself.

---

### Post by Porch on 2006-09-20
Encrypting the entire drive is not easy to do. 

I use TrueCrypt to encrypt my home directory. 
I have mine setup based on an USB key. 
If the thumb drive is in the laptop on boot, then it decrypts and mounts my "real" home directory over the "fake" directory. No passwords to enter, and someone could be looking over my sholder and not notice a thing. 
 

This way, if someone was to take my laptop or force me to show what is on it, I just boot it without the USB key. It starts up with the "fake" desktop by default. It would take someone really good to even figure out that my "real" desktop was hidden, and then, if they do, no way to decrypt it. 

I don't encrypt the swap for preformance. I do wipe it along with all the freespace on a cron job.

---

### Post by roaryyyj on 2006-10-04
> **Porch said:**
> Encrypting the entire drive is not easy to do. 

I use TrueCrypt to encrypt my home directory. 
I have mine setup based on an USB key. 
If the thumb drive is in the laptop on boot, then it decrypts and mounts my "real" home directory over the "fake" directory. No passwords to enter, and someone could be looking over my sholder and not notice a thing. 
 

This way, if someone was to take my laptop or force me to show what is on it, I just boot it without the USB key. It starts up with the "fake" desktop by default. It would take someone really good to even figure out that my "real" desktop was hidden, and then, if they do, no way to decrypt it. 

I don't encrypt the swap for preformance. I do wipe it along with all the freespace on a cron job.

what did you use to do this?
or did you write the scripts yourself?
im really interested in this method...

---

### Post by Sagotis on 2006-10-04
> **Porch said:**
> I do wipe it along with all the freespace on a cron job.

Umm, what prog are you using to do this with?

Sagotis

---

