---
title: "Why is Dm-Crypt forwarding discard command a security issue?"
date: 2011-10-26
forum: Security
---

### Post by nrundy on 2011-10-26
In the Linux Kernel 3.1, "Dm-crypt is now able to forward[]("https://github.com/torvalds/linux/commit/772ae5f54d69c38a5e3c4352c5fdbdaff141af21")  discard commands to the underlying disk. This is useful for SSDs, as it  allows them to be informed of freed blocks via ATA trim, improving both  speed and lifespan. For security reasons – to prevent attackers from  being able to make inferences from the extent of disk use – this  function is deactivated by default."

[https://github.com/torvalds/linux/commit/772ae5f54d69c38a5e3c4352c5fdbdaff141af21](https://github.com/torvalds/linux/commit/772ae5f54d69c38a5e3c4352c5fdbdaff141af21)

Would someone kindly explain more about why this is a security problem? How can an attacker make inferences about disk use on an encrypted drive? What exactly are users vulnerable to if this feature is enabled?

Anybody know how I can ENABLE this feature on Linux 3.1?

---

### Post by Seq on 2011-10-26
I found [this message]("http://www.saout.de/pipermail/dm-crypt/2011-July/001825.html") on how to enable it from July. At that time there was no userspace support, so you had to manually alter the dmcrypt entry table.

Considering his first warning is to backup data, and his last warning is not to do this until there is userspace support, it probably isn't completely safe to dabble around in it yet.

Checking on userspace support, it seems [cryptsetup 1.4.0]("https://code.google.com/p/cryptsetup/wiki/Cryptsetup140") has support for discard. It has to be enabled at every open, so it might require changes to the boot scripts as well (new args in crypttab, etc). However, cryptsetup 1.4.0 was released (checks watch) about two hours ago. It's pretty safe to assume that missed the shipping window for 11.10 :)

The changelog links to a [pretty good article]("http://asalor.blogspot.com/2011/08/trim-dm-crypt-problems.html") and asks you to read it before enabling discard. In short, discard allows some filesystem information to leak out. For example, he was able to fingerprint what type of filesystem is on an encrypted device. There may theoretically be future attacks that can exploit the elimination of the 'noise' from unused parts of the filesystem. It also removes the plausible deniability feature some people use with other encryption technologies (eg. truecrypt).

Some SSDs (i.e. better ones than I have) already have a few extra gigs reserved specifically for use with the garbage collector (you don't get to actually see that extra capacity -- it's for internal use only). Myself, I have a 64GB SSD without internal reserved space, so I simply left 5GB unallocated for use with the garbage collector. I haven't had any slowdown issues at all.

---

