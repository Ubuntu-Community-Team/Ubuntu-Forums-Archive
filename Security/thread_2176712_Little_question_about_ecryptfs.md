---
title: "Little question about ecryptfs"
date: 2013-09-25
forum: Security
---

### Post by TheOnlyChosenOne on 2013-09-25
Hi

I encrypted my home partition during the installation. Now I want to mount my home partition manually (via the terminal).
```
mount -t ecryptfs /home/username/.Private /home/username/Private
```
It asks my passphrase, but also other things I never set up.
I know that ecryptfs uses two passwords. One password for logging in (the user password) and a second, mount, passphrase for mounting the partition manually.

Now when I first logged on, I kind of skipped the part where I had to set up this second passphrase (because I didn't really understand why it was necessary - I already had  a password). Two questions for you guys:
Is it possible to set up this mount passphrase afterwards?
Can I manually mount my home partition with my user password?

I just want to be sure that when I break my display manager, I can still reach my files.

Thanks!

---

### Post by Dave_L on 2013-09-26
You didn't say which version of Ubuntu you're using, but if it's a recent one, the utility ecryptfs-recover-private manually mounts your encrypted home directory. Here's its man page for Ubuntu 12.04: [http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html)

The name "recover" is misleading. It simply mounts the directory.

You can test this by booting into recovery mode, by booting from a LiveUSB, or by logging in as a different user.

The ecryptfs passphrase was generated automatically, and encrypted using your login password. You can view it with the utility ecryptfs-unwrap-passphrase: [http://manpages.ubuntu.com/manpages/precise/man1/ecryptfs-unwrap-passphrase.1.html](http://manpages.ubuntu.com/manpages/precise/man1/ecryptfs-unwrap-passphrase.1.html)

It's a good idea to record the unwrapped (decrypted) passphrase in a safe place; in some scenarios you would need it to access the encrypted home directory.

---

### Post by TheOnlyChosenOne on 2013-09-26
Thank you for this easy explanation!

---

