---
title: "Encrypt system and/or encrypt home?"
date: 2016-12-07
forum: Security
---

### Post by sddfdds on 2016-12-07
If I choose to encrypt the system on an install, is there any difference/benefit to encrypting my home on top of that?

---

### Post by DuckHook on 2016-12-08
No. What it *will* do is make your system extremely brittle. BTW, whole disk encryption already makes your system fragile. It's necessity is over-estimated since, for most people, even an encrypted */home* is overkill when an encrypted "Private" data directory is enough. If you are storing highly sensitive data, or stuff that belongs to someone other than yourself, then that's a different matter and you may have no choice but to go to full disk encryption.

---

### Post by TheFu on 2016-12-08
> **DuckHook said:**
> No. What it *will* do is make your system extremely brittle. BTW, whole disk encryption already makes your system fragile. It's necessity is over-estimated since, for most people, even an encrypted */home* is overkill when an encrypted "Private" data directory is enough. If you are storing highly sensitive data, or stuff that belongs to someone other than yourself, then that's a different matter and you may have no choice but to go to full disk encryption.

I disagree about whole disk encryption.  Agree that encrypting just /home/ makes a funky system.  Making system-level backups on whole disk encrypted box isn't hard. Doing it efficiently on a /home/ encrypted box is nearly impossible (IME).  What gets backed up in the middle of the night when all users are logged off? I never found a good solution for encrypted /home/ backups.  That doesn't mean it can't be done, just that I never found a good answer.

All portable devices must be encrypted. Period. We don't get to choose when stuff gets lost or stolen. Best to NOT have that data/access available to whoever gets it.  I've seen an unlocked, unencrypted, phone disappear when on travel. The owner had to change all login accounts ASAP to prevent further encroachment.  All their contacts were hassled for months later (added to scam calling lists, scam SMS, and thousands of email scams).  I ended up switching phone numbers. Encrypt everything. Auto lock everything after a few minutes when outside the house.  Don't allow automatic logins for anything - including FB, Twitter, Instagram ... Anything, even an added PIN + RFID to slow it down would be useful.  Something like a 6-character password + yubikey device to access encrypted storage when outside home isn't that hard.

Also, we don't get to choose when storage devices fail. If we want warranty service without risk of data leaks, a whole encrypted disk shipped to the vendor is safer.  No telling what may be left in a swap partition or outside /home/.

However, when encryption is used in any capacity, that mandates the need for excellent backups.  If there is disk corruption due to any issues, retrieving data from encrypted storage is very hard.

It should go without saying, but for lurkers - do not use hibernation or standby when these devices are traveling. Turn them off. Encrypted data needs to be "at rest" to be most secure. Also read up about the "evil maid attack" vectors so mitigation steps can be taken. 

Also disable bluetooth in the BIOS. I've been hacked via bluetooth at hacker conferences. Seriously, disable it.

---

### Post by DuckHook on 2016-12-09
@ TheFu

An interesting and useful perspective. I'm always learning things from you.

However, a few points to consider:

This forum is filled with desperate cries for help from people who have gummed up their OS. Being able to fire up a LiveUSB and fix your OS is invaluable. Yes, it is possible to mount an encrypted volume in a LiveUSB and decrypt it (provided you have the encryption key and a pretty high-level understanding of Linux, the CLI and encryption), but such procedures are beyond the capacity of the general user.

I'm not suggesting throwing just the obvious stuff into an encrypted "Private" directory. All email and browser caches, all private keys, all data of any kind that could be even remotely sensitive would reside in the encrypted directory, and then be symlinked back to where the system expects to find them. If the computer falls into the wrong hands, they can read as much of the OS and /home as they like, but&#8213;*provided user has a strong passphrase*&#8213;the scoundrel will not be able to get at any sensitive data. The strong passphrase is absolutely critical to this scheme, but then, it is just as critical to whole disk encryption.

We are well aware, I think, that convenience and security are oil and water&#8213;they don't mix well. The more secure, the less convenient; the more convenient, the less secure. This is the everlasting tug-of-war between these two divergent needs. The problem with an entirely encrypted computer is that it maxes out security at the cost of *practical* recovery in the event of even a small glitch (with emphasis on the "practical").

Please don't take this as me trying to be argumentative. In particular, I think your warnings about bluetooth, residual info in swap or tmp files, auto logins, hibernation or standby, locking phones and habitual back-ups are spot on. I disagree only on the matter of whole-disk encryption, though I admit that this is the biggest item on that list.

I will be the first to admit that my approach does not provide the same security as a fully encrypted disk. I have elected to value a certain amount of convenience and operating versatility over whole-hog security. But I am counting on the fact that my measures are sufficiently robust that a scoundrel will go after much lower hanging fruit before trying to crack me.

I suppose that, in the end, the user gets to make up his/her own mind as to where on the security/convenience spectrum he/she wishes to fall. These discussions are always useful for bringing all of the issues to light.

---

### Post by TheFu on 2016-12-09
@DuckHook 

I'm always learning new things here and elsewhere and sometimes on my own. ;0 We all are.  Lots of smart people everywhere who alter our views. I have a habit of assuming too much technical knowledge and understanding from everyone. Not all minds "click" with this stuff - they are busy being smart about other, important, things, which baffle me, like gardening, cooking, people management, ... The point is we all have different aptitudes.

The complex, long, passphrase used for whole disk encryption just unlocks the access, it is not used in the actual data storage. There are 8 slots for gaining that access, most people use just 1, the one they typed in during the creation.  This can be changed without requiring the disk be re-encrypted because those 8 slots are just for unlocking the other, real, encryption, used on the disk.  An average use wouldn't have read the manpages to know this.  IMHO, we don't push manpages enough here, but that is a different topic completely.

We are in the "Security" subforum here, so my answers are written for that audience.  People looking for security are probably NOT average end-users and are willing to have a little inconvenience.  Probably. ;)

If you have a desktop that doesn't move and don't travel much, then perhaps whole disk encryption is overkill? I still think it is useful, if only to protect data from vendor warranty returns.  I don't use it everywhere, just where the risk is high for loss - portable devices.  There I consider it mandatory.

The scoundrels don't know if we are using encryption or not IME. They are opportunistic.  If you work at a cafe for an hour daily  (morning coffee?) or travel or take your device in the car and run in/out of a grocery store quickly, then you are a target.  On mass transit, we play *finger the thief*, after having a few interesting experiences. A friend had 2 laptops stolen from the passenger seat in a smash-n-grab in SF and other friend had something similar happen in the suburbs of a 100K person town. We don't need to be in big cities for theft to happen. 

Everyone has different life experiences which lead to their decisions.  It was many decades before I saw the need for much security. Now, due to my life situation, I see it everywhere.

Good discussion. Hopefully others are getting some ideas too.

---

### Post by DuckHook on 2016-12-09
@OP

There you have it. Two differing views on whether whole-disk encryption is worth the trouble. What the TheFu and I agree on, however, is that encrypting /home in addition to whole-disk will give you little additional benefit, but will make your system very brittle in case of even a minor OS hiccup.

Actually, whole-disk encryption, as recommended by TheFu, is easier to set up than my method. You just activate it during install, make sure both your encryption key and your passphrase are robust, and you're done.

My method requires the more involved and painstaking post-installation steps: from invoking ecryptfs-setup-private to moving a dizzying collection of files and directories into it, then encrypting swap, then redirecting /tmp to a tmpfs, etc. If you are still interested in my method, start a new thread and I will try to answer.

In the meantime, if you consider your question answered, please mark thread "solved" so that others can benefit from your solution.

---

### Post by sddfdds on 2016-12-09
Yea, thanks for the discussion, was very interesting.  I'm definitely in the user/skill level of just check the box on install...just the home encryption on top of it made me think

---

