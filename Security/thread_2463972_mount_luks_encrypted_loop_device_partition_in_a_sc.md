---
title: "mount luks encrypted loop device partition in a script"
date: 2021-06-22
forum: Security
---

### Post by Steve_Silvi on 2021-06-22
Hi,
I am trying to execute a script I found on github: [https://github.com/rufferson/pureos-pinephone](https://github.com/rufferson/pureos-pinephone). This script builds a PureOS image for a Pinephone 64 2GB model. However, the image won't boot on the 3GB model due to differences in RAM access. From what I can find on the internet, the loop device setup part of the script needs to include commands to create (and mount) a luks-formatted file system on the second partition of the loop device created by the 'losetup -f' command. When I execute the script as is, it returns a "mount: /home/steve/purepp/sd: unknown filesystem type 'crypto_LUKS'" error. Could someone tell me exactly which commands to add (and where) to luks-encrypt partition 2 of the created loop device? I have tried many different commands to do this, but I have very little knowledge of encryption and am unwilling to try to decipher the manpage document which is about 1000 lines long. I'd appreciate any assistance provided.

Regards,
delta1071

---

### Post by freedombacon on 2021-06-22
It looks like the script's dev is already aware of the issue: [https://github.com/rufferson/pureos-pinephone/issues/2](https://github.com/rufferson/pureos-pinephone/issues/2)

He says the script needs to be updated to use cryptsetup, but to me the error seems to be that losetup command not returning a loopback device like it's supposed to. I would try to replace that line.

> LO=`sudo losetup -f`

to this

> LO = /dev/loop1

---

### Post by Steve_Silvi on 2021-06-23
@freedombacon:
Changing that line allows the script to complete successfully, although the built image won't boot on the Pinephone. I'll keep tinkering with it. Thanks for the suggestion.

---

