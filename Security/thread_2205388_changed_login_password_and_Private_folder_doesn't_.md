---
title: "changed login password and Private folder doesn't mount."
date: 2014-02-13
forum: Security
---

### Post by a-you on 2014-02-13
Just to be clear on this: I like ecryptfs, and in this case none of the problems were the fault of ecryptfs.

I have been using an encrypted Private directory. Today I decided to change my login password; I did that using the "Users and Groups" GUI. I'm not sure what really happened, but I'm pretty sure I recall that after I had entered both the "old" password and the "new" one twice there was a complaint that I had mistyped the "old" password, so I entered that again, leaving the "new" fields alone. That may or may not be significant, but I must say that I had given some thought to my choice of a new password, and it seems hard to believe that I could have somehow entered the "new" one twice with the same typo, and that after all that the typo would have been so odd that at least a dozen guesses (later, when I tried to reboot) were wrong. Hmm. I don't know, but until I have a chance to test this a bit perhaps by trying to retrace the steps all I can say is to be careful and make sure you have backups of any encrypted data that you plan on keeping, and make sure you have a way to recover those things if needs be. Anyway in my case I could no longer log in at all. To deal with this I booted into recovery mode, selected "drop to root shell" and first (based on a tip I read) did:

```
mount -o rw,remount
```

then did:

```
passwd
```

which allowed me to reset the login password. This worked, but then I discovered that ecryptfs would no longer mount Private. Based on a different tip I then, again using the "Users and Groups" gui, reset the login password back to what it had been. That tip had said that s/he had been able to get ecryptfs to mount Private by restoring the login password to its original state. Unfortunately this didn't work in my case.

Looking back, I think the problem was that if root changes a user's password ecryptfs doesn't update the "wrapped passphrase" using the new password.

Fortunately when I created the Private directory I had carefully saved the mount passphrase, and using this I was able to get the folder mounted in /tmp and recover my data.

But what I was trying to also do was to see if there might be a way to fix the apparently broken wrapped passphrase, and that's when I posted here; I have just now edited the post though, only to try to make it clearer and maybe somehow useful to others, if possible.

This is Ubuntu Studio Quantal 64 bit.

---

### Post by Dave_L on 2014-02-13
What about ecryptfs-wrap-passphrase? According to the man page, that doesn't require the old login password

---

### Post by a-you on 2014-02-14
Dave_L: thanks for your comment. After a little time to reflect I realized that indeed I have both parts of what's needed: the mount passphrase and the login passphrase/password too. Another idea I had was that I have been keeping backups and on that backup drive I must have a copy of the original ~/.ecryptfs/wrapped-passphrase file too, and since I'm now (intentionally) back to my original login password/passphrase it seems to me that possibly just replacing that file with the backup might work too.

I'll go try this and report back here.

---

### Post by a-you on 2014-02-14
as an update I want to say that I replaced these files:

~/.ecryptfs/auto-mount
~/.ecryptfs/auto-umount
~/.ecryptfs/Private.mnt
~/.ecryptfs/Private.sig
~/.ecryptfs/wrapped-passphrase

with copies I had in the backup of ~ that I had, and that worked!! Whew! Now when I log in the original ~/Private folder is mounted and shows the decrypted contents as usual. Perhaps the wrapped-passphrase file was the key to this, but I just replaced them all.

I'm still not sure what caused the original problem---not being able to log in at all after changing the login passphrase. It's not impossible that I could have somehow made a typo, twice, and a strange one at that. It would be pretty odd. Anything is possible though.

(Btw there doesn't seem to be a way to edit the title of the thread. Calling it an ecryptfs disaster seems wrong. If anybody knows how to change a thread title please let me know.)

---

### Post by Dave_L on 2014-02-14
> **a-you said:**
> (Btw there doesn't seem to be a way to edit the title of the thread. Calling it an ecryptfs disaster seems wrong. If anybody knows how to change a thread title please let me know.)

I don't think you can change the title yourself, but you can use the Report button to ask a moderator to do it.

---

