---
title: "Why is /dev/urandom so dreadfully slow?"
date: 2008-10-21
forum: The Cafe
---

### Post by u-slayer on 2008-10-21
There are faster and secure ways to produce random data.

```

$dd if=/dev/urandom bs=1M count=100 > /dev/null
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 11.6463 s, 9.0 MB/s

$ dd if=/dev/zero bs=1M count=100 | gpg --symmetric --passphrase password - > /dev/null
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 1.77988 s, 58.9 MB/s
```:)

or for different random data every time:
```

dd if=/dev/zero bs=1M count=100 | gpg --symmetric --passphrase `dd if=/dev/random bs=4 count=8 2>&1 | sha256sum | head -c 64` - > /dev/null
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 1.76055 s, 59.6 MB/s

```

GPG is producing random data over 6.5 times faster using the highly secure AES encryption standard. Why can't we replace urandom with something like this?

This would make programs like shred and wiping hard drives work so much quicker.
sorry if this is a noob question.

---

### Post by gnomeuser on 2008-10-21
First off, you are in the wrong forum. This is not general support this it idea development for future versions of Ubuntu.

Secondly, there are good reasons why urandom is slow, most importantly you do not want to deplete your entropy pool. Instead you want to seed a pseudo random number generator with urandom.

There is no safe way to make this fast, unless you have a fast truly random hardware device, some modern CPUs have this like the VIA Nano. That being said, what you you will never be the right way to wipe a hardrive securely.

Look at:
[http://www.dban.org/](http://www.dban.org/)
[http://www.linux-kurser.dk/secure_harddisk_eraser.html](http://www.linux-kurser.dk/secure_harddisk_eraser.html)

---

### Post by Sef on 2008-10-21
Moved to Community Cafe.

---

### Post by u-slayer on 2008-10-22
> **gnomeuser said:**
> Secondly, there are good reasons why urandom is slow, most importantly you do not want to deplete your entropy pool. Instead you want to seed a pseudo random number generator with urandom.
[http://www.dban.org/](http://www.dban.org/)
[http://www.linux-kurser.dk/secure_harddisk_eraser.html](http://www.linux-kurser.dk/secure_harddisk_eraser.html)


First off, GPG IS a psuedo random number generator.

Second, if you think urandom is slower and ergo more secure, you are wrong. AES is the most trusted encryption standard in existence and if it produces faulty random data, then nothing will.

---

