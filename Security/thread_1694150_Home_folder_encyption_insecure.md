---
title: "Home folder encyption insecure?"
date: 2011-02-23
forum: Security
---

### Post by cham93086 on 2011-02-23
I have a question I can't seem to find the answer to.

I've encrypted my home folder using ubuntu's built in utility.  My main goal is to protect my data if I lose my laptop.  I was snooping around on myself and had a thought:

I logged in with a live CD and was able to look at my shadow file.  From there, I can get the salt and hash of my password.  Since rainbow tables are available for sha-1, (what I believe ubuntu uses as the default?) doesn't this mean that it would be a quick hit to get my password, and consequently allow a login and access to my data?

---

### Post by movieman on 2011-02-24
Unix passwords are -- or should be -- salted, so no.

---

### Post by doas777 on 2011-02-24
it is at least in theory possible (it is always prudent to assume that if your hash is captured it can be broken), though it would no doubt be hard to pull off. I would be surprised if they were using anything less than sha-256 (sha-2), but the salting is the real issue for the would be attacker. 

I don;t know if it would be correct to characterize this as an insecurity in the home folder encryption, so much as one in credentials storage, but the same vulnerability exists in all other commercial os's that I can think of as well. 

regardless, if you are worried about this, truecrypt is prolly your best bet, because it is not OS integrated. make sure you use a separate very strong password for your volume and don't set it up to automount. remember however, *Physical access => root access*.

---

### Post by rookcifer on 2011-02-24
The main problem with the home encryption option is that it uses your user password.  Since most people are not going to make their user password more than about 8 characters or so (for convenience whilst using sudo), it means a dictionary attack is a real possibility.  Rainbow tables, however, aren't much of a threat since Linux distros use salts.

On the other hand, if you use dm-crypt/LUKS, you can set a very strong password and only have to enter it once on boot.

---

### Post by cham93086 on 2011-02-24
> **rookcifer said:**
> The main problem with the home encryption option is that it uses your user password.  Since most people are not going to make their user password more than about 8 characters or so (for convenience whilst using sudo), it means a dictionary attack is a real possibility.  Rainbow tables, however, aren't much of a threat since Linux distros use salts.

On the other hand, if you use dm-crypt/LUKS, you can set a very strong password and only have to enter it once on boot.

The salt is just appended to your password, right?  The salt is also listed in the shadow file. hash==>rainbow==>remove salt==> Password??

 I misspoke before by the way, a little more research shows ubuntu used sha2 by default.  You're quite right that dm-crypt works well, as does true crypt.  I already use truecrypt for the actually sensitive stuff.  perhaps I'll switch back to using dm-crypt.  I did have a problem the last time with it though when I tried to upgrade the distro.  Thank heavens for good backups!

---

### Post by movieman on 2011-02-24
> **cham93086 said:**
> The salt is just appended to your password, right?

Yes. Which makes a table-based approach unfeasible with current hardware.

---

### Post by cham93086 on 2011-02-24
Thanks for the info guys!  You got me pointed in the right direction for my research!

---

### Post by kevdog on 2011-02-27
Someone on #ubuntu told me not to use truecrypt.  They recommended freeotfe instead: [http://www.freeotfe.org/](http://www.freeotfe.org/).  To be honest with you I don't have enough experience to tell you the pros and cons of each.

---

### Post by davesmith on 2011-04-27
I want to remove the encryption on my home folder. I recently upgraded from hardy 8.04LTS to maverick 10.10 and now I have audio problems playing mp3 files using VLC, also films will not play in sync with the audio. I think maybe when my player tries to buffer the stream, it has to wait for the decryption of the mp3 file, which is in the home folder. Could someone put me straight on this? Otherwise maverick installed ok and works well.

Thanks

---

