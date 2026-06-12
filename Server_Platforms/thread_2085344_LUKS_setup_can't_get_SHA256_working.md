---
title: "LUKS setup can't get SHA256 working"
date: 2012-11-17
forum: Server Platforms
---

### Post by rubylaser on 2012-11-17
Hello, I'm in the process of setting up an encrypted external drive for backups and can't get the sha256 module to load (Ubuntu 12.04).  This is a Xeon 3075, and it does not have a hardware cryptographic device, so that's the root of my issue.
```
FATAL: Module sha256 not found.
```

I've tried adding an alias to my /etc/modprobe.d/aliases.conf, but the module still won't load. Any ideas?
```
root@fileserver:~# cat /etc/modprobe.d/aliases.conf 
alias sha256 sha256_generic
```

```
root@fileserver:~# modprobe sha256
FATAL: Module sha256_generic not found.
```

Edit:
It also does show up in my list of crypto modules...
```

root@fileserver:~# cat /proc/crypto 
name         : aes
driver       : aes-asm
module       : aes_x86_64
priority     : 200
refcnt       : 1
selftest     : passed
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

name         : hmac(sha256)
driver       : hmac(sha256-generic)
module       : kernel
priority     : 0
refcnt       : 2
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 32

name         : hmac(sha1)
driver       : hmac(sha1-generic)
module       : kernel
priority     : 0
refcnt       : 2
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 20

name         : stdrng
driver       : krng
module       : kernel
priority     : 200
refcnt       : 1
selftest     : passed
type         : rng
seedsize     : 0

name         : crc32c
driver       : crc32c-generic
module       : kernel
priority     : 100
refcnt       : 1
selftest     : passed
type         : shash
blocksize    : 1
digestsize   : 4

name         : aes
driver       : aes-generic
module       : kernel
priority     : 100
refcnt       : 1
selftest     : passed
type         : cipher
blocksize    : 16
min keysize  : 16
max keysize  : 32

[B]name         : sha256
driver       : sha256-generic[/B]
module       : kernel
priority     : 0
refcnt       : 3
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 32

name         : sha224
driver       : sha224-generic
module       : kernel
priority     : 0
refcnt       : 1
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 28

name         : sha1
driver       : sha1-generic
module       : kernel
priority     : 0
refcnt       : 3
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 20

name         : md5
driver       : md5-generic
module       : kernel
priority     : 0
refcnt       : 1
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 16

```

I'm guessing I'll either need to grab a different kernel, or compile my own (I haven't had to do that in years :) ).

---

### Post by rubylaser on 2012-11-18
Well, I just got it working using a workaround (I used SHA512 instead).
```
cryptsetup --hash sha512 --key-size 256 --cipher aes-cbc-essiv:sha256 luksFormat /dev/sdg1
```

---

