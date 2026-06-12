---
title: "Filesystem has errors: /boot"
date: 2010-11-21
forum: Server Platforms
---

### Post by Frenky893 on 2010-11-21
Hi everyone,

I can't boot into my system anymore, it says "Filesystem has errors: /boot" and "Run fsck manually". The problem is that I use full volume encryption, and once I enter the passphrase all it does is show me these errors and won't give me a shell.

How do I decrypt my volume and run a file system check manually?

Really hope someone can help me out.

Greetings,
Frenky


Answer: [http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode](http://askubuntu.com/questions/8566/errors-when-performing-fsck-on-encrypted-partition-in-recovery-mode)

Edit:

I did the steps in the answer ^, but when I do:

sudo cryptsetup luksOpen /dev/hda5   crypt1

It says: Devide /dev/hda5 doesn't exist or access denied.

What do I do?

---

