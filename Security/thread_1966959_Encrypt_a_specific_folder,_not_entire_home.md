---
title: "Encrypt a specific folder, not entire /home?"
date: 2012-04-27
forum: Security
---

### Post by Roasted on 2012-04-27
Just curious, is it possible to encrypt my Documents folder only and let the rest of my home folder alone and untouched? I'm interested in encryption but encrypting my entire desktop might be overkill. Just curious about Documents in particular.

Secondly, let's say it's possible. When I log in to Ubuntu, I have a startup application that rsync's my Documents folder to my file server. Is it possible to rsync even if the source is encrypted?

---

### Post by rookcifer on 2012-04-27
> **Roasted said:**
> Just curious, is it possible to encrypt my Documents folder only and let the rest of my home folder alone and untouched? I'm interested in encryption but encrypting my entire desktop might be overkill. Just curious about Documents in particular.

If you encrypt individual directories, they will remain encrypted until you decrypt them manually.  This might be a hassle for everyday use.  Moreover, there is no guarantee that someone can't find the files unencrypted on your swap partition.  The best defense against this is to encrypt the entire OS or at least /home.  

At any rate, if you want to encrypt an individual directory, there are two methods you can use that are already available in your default install.  Both rely on GPG. 

The first method is to simply encrypt it with a password.  Since you are wanting to encrypt an entire directory, you will first need to compress it into a .tar or .bz2 file.  You can do this by right-clicking the directory and selecting compress.  After that's done, you encrypt the .tar file like so:

```
gpg -ec name_of_file.tar.gz
```

It will ask you to create a password.  Be sure to remember the password and make it decently strong.

The second method is to create a gpg key-pair and use your public key to encrypt it.  This method is more convenient because the only password you need to remember is that of your private-key.  So, this way you can encrypt as many files as you want with the same key/password.  

But again, both of these methods are much better for sending a file securely over the Internet (like for backups) than they are for keeping it secure on your machine when someone might have physical access.  Again, the best way to protect against "leakage" is to encrypt the entire OS (or at least /home).


> Secondly, let's say it's possible. When I log in to Ubuntu, I have a startup application that rsync's my Documents folder to my file server. Is it possible to rsync even if the source is encrypted?

Yes, that should be possible.

---

### Post by Roasted on 2012-04-27
Hm, maybe encrypting my entire home folder is the way to go. I was worried about system performance so I figured I would just encrypt what was necessary, especially considering I'm running a RAID mirror for /home (even though I saw 0 performance change when I introduced RAID). Maybe I'll look into doing that...

EDIT - Judging by this link

[http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/09/home-directory-and-full-disk-encryption-in-ubuntu-11-04/)

The alternate installer CD is most logical if you want a full blown encryption to be set up. Only question is, if I set up / and /home to be on separate partitions, can I still achieve that same functionality?

---

### Post by rookcifer on 2012-04-27
> **Roasted said:**
> The alternate installer CD is most logical if you want a full blown encryption to be set up. Only question is, if I set up / and /home to be on separate partitions, can I still achieve that same functionality?

Yes you can.  The partitions themselves are logical partitions, not physical partitions.  So, essentially you encrypt one bug chunk of your physical disk and then setup logical volumes on top of that for /, /home, etc.

---

### Post by Roasted on 2012-04-27
Nice. I see. I just set up ecrypt from terminal and with two commands I had my home and swap positions encrypted. New question... From the desktop installer if I select the checkbox to encrypt my home directory, I have to assume it doesn't do swap by default, does it?

---

### Post by rookcifer on 2012-04-27
> **Roasted said:**
> Nice. I see. I just set up ecrypt from terminal and with two commands I had my home and swap positions encrypted. New question... From the desktop installer if I select the checkbox to encrypt my home directory, I have to assume it doesn't do swap by default, does it?

No it won't do swap, but encrypting swap can be done at any time, so that's not a problem.

---

### Post by Roasted on 2012-04-27
Good deal. I did swap manually in the terminal with a command I found online. It's actually really simple to set up... quite surprising.

I went into a live USB session to test it, and sure enough I could not get into my home directory. The only confusion I had is instead of just jason, I now have jason and jason.Pkmblahblahblah (bunch of random characters). Both directories seem encrypted, but I'm curious - what is the relevance and purpose of each one?

---

### Post by Dave_L on 2012-04-28
There is really only one encrypted home directory, but it's accessible via two file system paths.

---

### Post by Roasted on 2012-04-28
What would the protocol be if my SSD (which has / on it) suddenly tanks, and I have to install Ubuntu on a new drive and mount my encrypted home volume as /home? Can I do it without issue? Or do I need to install ecrypt-utils first?

---

### Post by Dave_L on 2012-04-28
Roasted, refer to these references:

Mounting your Encrypted Home from an Ubuntu LiveCD 
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

Introducing ecryptfs-recover-private -- Recover your Encrypted Private Directory! 
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

