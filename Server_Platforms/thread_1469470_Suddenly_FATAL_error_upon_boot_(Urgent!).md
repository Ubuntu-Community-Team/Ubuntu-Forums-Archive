---
title: "Suddenly FATAL error upon boot (Urgent!)"
date: 2010-05-02
forum: Server Platforms
---

### Post by Burbruee on 2010-05-02
I Installed 10.04 LTS on my server, spent some hours configuring it, copied back some backup files to the server over SCP.

Decided to shut down the server and put it in my windows box with the ex2/3 driver from fs-driver.org instead because it would be faster than the network speed I'm getting. (1 MB/s)

But, the disk could not be read even though it's ext3. Figured it might be because I enabled encryption during install, so back in the server it goes.

Upon boot I get the following screen:
```

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 148755/15024128 files, 5527300/60082688 blocks
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-21-generic-pae/kernel/drivers/crypto/padlock_sha.ko): No such device

```

It stops right there and does not go further.
I googled the error, some say you could blacklist the padlock. But I can't get to a console! What do I do?



EDIT: After approximately 40 minutes it had succeded in booting up and I was able to blacklist the module. It works again. [SOLVED]

---

### Post by frederik@k153.dk on 2010-05-09
I have the exact same problem. Did you just wait for 40 minutes with the screen, and then the login screen came up, or did you do anything else?

Thx

/Frederik

---

### Post by Burbruee on 2010-05-09
> **frederik@k153.dk said:**
> I have the exact same problem. Did you just wait for 40 minutes with the screen, and then the login screen came up, or did you do anything else?

Thx

/Frederik

Yeah I just left it on and did other things, when I came back it asked me to log in and I was able to blacklist it.

---

### Post by Zaphans on 2010-06-21
I had the same issue.  From what I can tell, the problem of taking a long time to boot has nothing to do with the padlock error.  This is simply a bug that goes away once you blacklist the feature.

It's just taking time to boot because the disk didnt unmount cleanly when you last shutdown, so the boot decides to run a fsck disk check for you.  It doesnt display any text while it does this, but give it some time and it finishes the disk check.

---

### Post by dagnamit on 2010-07-22
I have the same issue.  I left it overnight but never got to the login prompt.  However if I hit 's' I see:

```
Skipping /data/secure at user request
```then get to the login prompt.

After logging in I see that /dev/mapper/secure doesn't exist so I then have to reopen it with cryptsetup:

```
$ sudo cryptsetup luksOpen /dev/sdb1 secure
```After that, issuing 'mount -a' mounts the encrypted device as /data/secure and all is fine.

The other thing out of the ordinary (other than the FATAL at boot and the missing /dev/mapper) is that when I issue the cryptsetup command I see:

```
device-mapper: remove ioctl failed: Device or resource busy
```

---

