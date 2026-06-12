---
title: "should I stick my backups on a luks partition?"
date: 2011-06-14
forum: The Cafe
---

### Post by nerdy_kid on 2011-06-14
I have some important backups that I don't want to have lost, anyone know how safe it is to put them on a luks partition, assuming I don't forget the password?  Is it worth the risk?

---

### Post by 3Miro on 2011-06-14
The only risk that I can think of is to forget the password. I am running my entire laptop on lusk and it works just fine.

If you are worried about data corruption, this can happen with regular ext partition too. I don't think lusk is any less reliable. You can also use liveCD to open the partition if you have to, all that you need is the password.

---

### Post by DZ* on 2011-06-15
I've been backing up to two luks-formatted usb drives since 2008. Both drives still work fine. Obviously the luks header is a single point of failure: if it's gone, everything is gone. But I would back up to two drives anyway (with or without encryption).

---

### Post by DZ* on 2011-06-15
Some humor from luks developers ([http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions](http://code.google.com/p/cryptsetup/wiki/FrequentlyAskedQuestions))

"The LUKS header contains a 256 bit "salt" value and without that no decryption is possible. While the salt is not secret, it is key-grade material and cannot be reconstructed. This is a cryptographically strong "cannot". From observations on the cryptsetup mailing-list, people typically go though the usual stages of grief (Denial, Anger, Bargaining, Depression, Acceptance) when this happens to them. Observed times vary between 1 day and 2 weeks to complete the cycle. Seeking help on the mailing-list is fine. Even if we usually cannot help with getting back your data, most people found the feedback comforting.

If your header does not contain an intact salt, best go directly to the last stage ("Acceptance") and think about what to do now."

---

### Post by nerdy_kid on 2011-06-19
Thanks for the info :)

---

