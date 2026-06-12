---
title: "[SOLVED] Adding a new hard drive with full encryption?"
date: 2008-07-29
forum: Security
---

### Post by kerryhall on 2008-07-29
Hey all! So I did a Gutsy install on my computer, with full encryption. It works great and I love it! I upgraded to Hardy when it came out.

I recently purchased a new hard drive. I would like to add this hard drive, possibly making it my home directory, and I would like it to be fully encrypted as well, using the same password as the encryption of my installation. Does anyone know how to do this? I have searched the forums, but I couldn't find info about this. Thank you!!

---

### Post by hyper_ch on 2008-07-29
(1) encrypt the partition
[http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks) --> look from step 5

(2) copy all the stuff in your home to it (keep permissions and stuff)

(3) have it automounted as /home (just change the path accordingly in the fstab)
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by kerryhall on 2008-07-29
So this will still ask me for my password at boot up, with the gui?


Thanks!!

---

### Post by blastus on 2008-07-30
> **kerryhall said:**
> So this will still ask me for my password at boot up, with the gui?

Thanks!!

No. What you want to do is add a key file to the encrypted partition and store the key file on your root partition (which is encrypted as well.) Then configure crypttab to use the key file to unlock the encrypted partition.

I use full encryption on root. I have a key file on the root filesystem that is automatically used to unlock three other partitions that are encrypted. This way I only have to enter in a passphrase once during bootup and everything gets unlocked.

---

### Post by kerryhall on 2008-08-15
Wow, awesome. Thanks for that! I think I am going to set up a test machine to make sure all this works in case I seriously screw things up.

---

