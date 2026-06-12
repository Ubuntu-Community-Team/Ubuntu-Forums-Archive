---
title: "dd urandom slower than dban?"
date: 2011-01-04
forum: Security
---

### Post by Jonahtan on 2011-01-04
I recently wiped a disk using dban but noticed that it wasn't completely  zeroed out by a hexdump in the Ubuntu terminal. Now I have tried to  overwrite the disk with 
sudo dd if=/dev/urandom of=/dev/sda  from a live cd. It's a 320 GB drive  and the computer is still chewing after 20 h. Is that really what should  be expected? DBAN was done in about 7 hours using the default wipe  method (DoD short I belive with three passes). Is "dd urandom" that much  slower?

---

### Post by rookcifer on 2011-01-04
> **Jonahtan said:**
> Is "dd urandom" that much  slower?

Yeah it's pretty slow.  I like to use OpenSSL for wiping as I have found it's ***much*** faster.  For instance, I just did a benchmark on my machine with /dev/urandom and openssl to write random data.  I ran both for 20 seconds.  Results:

/dev/urandom = 59MB written
openssl = **1.4GB** written

Also I tried /dev/zero and it was pretty fast too: after 20 seconds it wrote 869MB.  But writing zeros with openssl was even faster (again at 1.4GB).

If interested in using OpenSSL, here's the commands I use:

**For zeros:**

```
dd if=/dev/random bs=1k count=1 | openssl enc -kfile /dev/fd/0 -in /dev/zero -out filename
```

Or, you can use /dev/zero directly:

```
dd if=/dev/zero of=filename
```

**For random data:**

```
dd if=/dev/random bs=1k count=1 | openssl enc -kfile /dev/fd/0 -in /dev/zero -aes-128-cbc -out filename
```

NOTE: this will create a file and just keep filling it with data until the partition or drive is full.  Once you're done, just delete that file.  If you plan on doing this to wipe an entire drive, it's best to do it from a liveCD (the Ubuntu liveCD is probably the best choice here).

I suppose openssl is faster because it's using AES to write random data.  /dev/urandom itself uses hashing functions, so I suppose there is a speed difference (or a code optimization difference) between the two.  Plus /dev/urandom depends on /dev/random as a seed and there is a lot of entropy mixing in the pool and then hashing, etc.  Just a lot more steps involved.

---

