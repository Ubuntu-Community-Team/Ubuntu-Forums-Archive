---
title: "backup and encrypt using gpg"
date: 2010-01-20
forum: Security
---

### Post by Mash909 on 2010-01-20
hi All

I'm currently writing a simple script which uses luckyBackup to backup my /home directory to /tmp.  I then want to tar it, encrypt it with gpg and move it onto a usb stick.

My question is that suppose my hard disk died and I needed to restore from this USB backup, would I still be able to decrypt the file given that I would have lost gpg keys etc when the disk died? (I would still know the passphrase though).  Should I be backing up gpg files separately?

thanks

---

### Post by sp0nge on 2010-01-20
I would also backup the PGP key somehow. Personally, I use gmail to hold things like the PGP key, then if I am on a machine which requires it, I can easily import it without issue.

---

### Post by FuturePilot on 2010-01-20
> **Mash909 said:**
> 

My question is that suppose my hard disk died and I needed to restore from this USB backup, would I still be able to decrypt the file given that I would have lost gpg keys etc when the disk died? (I would still know the passphrase though).  Should I be backing up gpg files separately?

No. If you lose the key you will not be able to decrypt the backup. You will need to have the key backed up somewhere safe. Alternatively, you could use gpg with symmetric encryption which does not require a key that way you don't have to worry about losing it.

---

### Post by Mash909 on 2010-01-21
Thanks for the replies - symmetric encryption seems to be the best solution for me.

---

### Post by Lars Noodén on 2010-01-21
> **Mash909 said:**
> Thanks for the replies - symmetric encryption seems to be the best solution for me.

Or you can make backups of the keys, too.

---

### Post by Sarmacid on 2010-01-21
The keys are stored in the /home/$USER/.gnupg folder, so they would be encrypted too. You'll need to back them up.

---

### Post by Mash909 on 2010-01-21
So presumably it's safe just to copy everything in the .gnupg folder - presumably the encrypted backup can't be compromised even if someone got hold of this folder? (ie they'd need to know the passphrase?)

---

### Post by jflaker on 2010-01-21
Place the PGP keys on multiple CD or DVD and store in a firesafe and/or backup with a reputable offsite backup service....Without your PGP keys, your data is forever locked away and you can never get it back.  I found that out the hard way...

As long as you have your PGP keys, you should be able to decrypt your data.

Another option would be to use TrueCrypt and create a few small volume containers to store your data in and backup the storage container(s)...That you only need a passphrase for.....

I have my PGP keys in a 1MB TrueCrypt container which is backuped up to an offsite service along with my PGP encrypted and other data.  That way I can get my PGP keys back if my disk fails

---

### Post by Lars Noodén on 2010-01-22
> **jflaker said:**
> Place the PGP keys on multiple CD or DVD and store in a firesafe and/or backup with a reputable offsite backup service...

The idea is right, but perhaps a better medium could be found.  CDs hold about 700MB, DVDs just under 4G but keys are only a few KB.  CDs take a lot of space and are very vulnerable to polluted air and common high or low temperatures.  

Papers ignite at around 218°-246°C (424-474°F), so any plastics will be scotched by a regular firesafe for papers.  The offsite storage safe, such as a bank's safedeposit box should be rated for computer storage media.

Most digital storage media, and many analog, are destroyed at a much lower temperature.  For example, LPs warp just by leaving them in the warm sunlight.  If left in hot sunlight, say in the back of a car or in a trunk, they more or less melt.  

CD-R, CD-RW, DVD-R, DVD+R, DVD-RW, and DVD+RW are all different physical structures.   You can look up what layers of plastics, organic solvents, polarizers, and metals are in each type and then guess. 

You can get very small hard drives or even compact flash cheaply. The small SD compact flash units that go in cameras are available, depending on size, for less than 5 EUR.  Those are the size of a postage stamp and thinner than a coin.  You can get ones for mobile phones, Mini SD, for less than 10 EUR and those are the size of a small person's finger nail and as thick as a thin piece of card board.  They'll take less space.

---

### Post by jflaker on 2010-01-22
> **Lars Noodén said:**
> 

You can get very small hard drives or even compact flash cheaply. The small SD compact flash units that go in cameras are available, depending on size, for less than 5 EUR.  Those are the size of a postage stamp and thinner than a coin.  You can get ones for mobile phones, Mini SD, for less than 10 EUR and those are the size of a small person's finger nail and as thick as a thin piece of card board.  They'll take less space.

[/QUOTE]
Disaster Recovery 101 says to back up often and take media offsite.
Holding such files on ANY available media is an eventual disaster waiting for a place to happen.  

I still believe that a small TrueCrypt volume to hold the PGP/GPG keys is most idea. A TrueCrypt Volume file, which itself is impenetrable currently, can be sent to an offsite service with confidence it can't be opened unless you know the passphrase.  Now that the keys are in a "Lock box", the PGP/GPG encrypted files can be stored offsite also....It probably wouldn't hurt to store a copy of TrueCrypt and pgp that you are using, but that brings your backup time and storage way up.

---

### Post by Mash909 on 2010-02-23
I've exported my keys and backed them up to disk.
One other question:  If I change the passphrase associated with the keys, will I need to back them up again, or is the passphrase independent of the keys?
thanks

---

### Post by ushills on 2010-02-23
Also look at paperkey in the repos, you can print something off and restore a key manually this may be a final resort but removes the issue of electrons and vulnerable media.

---

### Post by tubbygweilo on 2010-02-23
> I've exported my keys and backed them up to disk. Secret/private key as well?

---

