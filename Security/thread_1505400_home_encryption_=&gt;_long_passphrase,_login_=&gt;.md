---
title: "home encryption =&gt; long passphrase, login =&gt; short passphrase"
date: 2010-06-09
forum: Security
---

### Post by jomex on 2010-06-09
i just set up Ubuntu 10.10 with the new home directory encryption instead of dmcrypt from the alternate installer. they say you need about 20 characters for secure encryption but if you use such a passphrase with home encryption you also have to type it everytime you need to "sudo" something. do you have any ideas and suggestions on how to get both secure home encryption and quick sudo?

it's okay to enter the long passphrase during at first login.
and i know that a short sudo passprase will compromise security a little WHILE the computer is running.

---

### Post by anomie on 2010-06-09
[QUOTE=jomex]but if you use such a passphrase with home encryption you also have to type it everytime you need to "sudo" something. do you have any ideas and suggestions on how to get both secure home encryption and quick sudo?[/QUOTE]

I haven't tinkered with filesystem encryption on Ubuntu, but that doesn't sound quite right. You should have to provide your encryption password/key once at boot time (or sometime prior to login). Each time you sudo, you should have to provide your own user's password. 

I may be mistaken, but it doesn't seem logical that you'd be working in your home directory already and then get prompted again for your encryption password/key when trying to sudo...

---

### Post by jomex on 2010-06-09
> You should have to provide your encryption password/key once at boot  time (or sometime prior to login).

yes, that is exactly what i want :)
the problem is by default the user login password is coupled with the home encryption password.

---

### Post by anomie on 2010-06-09
I'm not saying/implying that I do not believe you, but would you be willing to walk through a contrived test and post a screenshot that demonstrates what are you describing? (With respect, if that's how the "new" filesystem encryption is implemented, it sounds horrible.)

---

### Post by movieman on 2010-06-09
> **anomie said:**
> (With respect, if that's how the "new" filesystem encryption is implemented, it sounds horrible.)

If you're talking about ecryptfs, it generates a random encryption key and then encrypts it with your login password: so when you log in it decrypts the key and can then use it to decrypt your home directory... if you change the password it just reencrypts the key with your new password so it doesn't need to reencrypt all the files.

So I believe the problem the OP is talking about is that if you have a long login password to keep the home encryption secure then you have to type the same long password whenever you 'sudo'.

To make it secure with a short login password I think you'd need to mount /home as an encrypted partition and then you'd enter the long passphrase for the encrypted partition once at boot time. However, I've never used partition encryption so I'm not sure what that involves; ecryptfs is secure enough against most threats if you use a sensible password, even though the NSA could probably break it in a few months if they had to.

---

### Post by anomie on 2010-06-09
[QUOTE=movieman]If you're talking about ecryptfs, it generates a random encryption key and then encrypts it with your login password...[/QUOTE]

I'm not precisely sure what OP is referring to. ;) I just replied to a thread that had 45 views (at the time) and not a single suggestion. Thanks for clarifying.

---

### Post by jomex on 2010-06-10
thank you Movieman for clarifing :)

[quote="Movieman"]To make it secure with a short login password I think you'd need to  mount /home as an encrypted partition and then you'd enter the long  passphrase for the encrypted partition once at boot time.[/quote]

actually i don't want to make it secure with a short login password (as it shouldn't be possible anyway), i just want a short password for sudo-ing. i avoided the full encrypted /home partition btw because it wasn't working with the 10.04 alternate installer so i stuck with the per user home directory encryption.

i'm a little bit puzzled actually about how Ubuntu deals with this case because i think that my case stated above is pretty common: long encryption passphrase, short sudo  passphrase. but i like to hear your opinions! :)

---

### Post by rookcifer on 2010-06-10
OP,

The only way around this issue is to use the alternate install CD and create encrypted partitions with dm-crypt/LUKS.  This way, you are prompted on boot for the passphrase which will unlock the drive (you can encrypt everything, including swap).  And, if you use this method, the passphrase will not be the same as your sudo password.

The downside to this is you must do a fresh install.

---

### Post by jomex on 2010-06-11
[]("http://ubuntuforums.org/showthread.php?t=1498991")[Encryption is not working for me on RAID]("http://ubuntuforums.org/showthread.php?t=1498991")

btw: i think swap is now encrypted randomly by default (i get "cryptoswap is still loading" messages on boot time).

---

### Post by coderam on 2010-06-13
Does anyone know how to recover the passphrase - I remember Ubuntu gave me the command when I first setup the encrypted home directory, but I never wrote it down.

---

### Post by jomex on 2010-06-18
type in console: ecryptfs-unwrap-passphrase

---

### Post by BkkBonanza on 2010-06-19
@jomex,
You may want to read here ( [http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html](http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html) ) to get more familiar with how ecryptfs works. He has other good artcles about it on his blog. 

I don't think it makes much sense to have a shorter password for sudo than login/ecrypt mounting since anyone gaining sudo access will already have full access to your home directory, assuming it was mounted at boot. They could just copy material to non-home areas for later use.

If you are serious about security I would recommend using your encrypted home with 2-factor authentication. Use a regular password and a usb flash stick as KEY disk. That blog above also has info on how to set that up and it's very easy. Put one of those tiny usb keys on your key ring so only having both password and key will allow access. I do this when traveling.

Another nice thing about an encrypted home is that it locks when you suspend or the screen saver kicks in so that you can leave your computer and it will secure itself if you forget - probably the biggest class of vulnerabilities is user forgetfulness / errors.

---

