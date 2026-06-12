---
title: "why luksOpen need a long time(4minutes)"
date: 2008-06-29
forum: Security
---

### Post by say2sky on 2008-06-29
use cryptsetup luksOpen to mapping a luks encrypt drive partition, but 4 minutes need to complete this mapping.

What I should do to short this time? 

```

time sudo cryptsetup luksOpen /dev/sda8 sda8 -d /etc/keys/sda8.key 
key slot 1 unlocked.
Command successful.

real	4m40.223s
user	0m5.024s
sys	0m0.456s


```

---

### Post by hyper_ch on 2008-06-29
how big is the key?

---

### Post by say2sky on 2008-06-29
> **hyper_ch said:**
> how big is the key?

```

sudo dd if=/dev/urandom of=/etc/keys/sda8.key bs=1K count=1

```

```

sudo cryptsetup --verify-passphrase --verbose --hash=sha512 --cipher=aes-xts-benbi:sha512 --key-size=512 luksFormat /dev/sda8


```

---

### Post by hyper_ch on 2008-06-29
so the key is small? and not like 20gb?

---

### Post by say2sky on 2008-06-29
> **hyper_ch said:**
> so the key is small? and not like 20gb?

it is a small key, in fact only 512 bit is effective, right. 

anyone have met similar problem?

---

### Post by hyper_ch on 2008-06-29
well, then it shouldn't take that long to unlock the partition... that is really strange...

---

### Post by say2sky on 2008-06-29
> **hyper_ch said:**
> well, then it shouldn't take that long to unlock the partition... that is really strange...

on the situation it take a long time, it show

```

sudo dmsetup ls
temporary-cryptsetup-9330	(254, 2)


```

---

### Post by hyper_ch on 2008-06-29
what about devices "254, 0" and "254, 1"?

---

### Post by say2sky on 2008-06-29
> **hyper_ch said:**
> what about devices "254, 0" and "254, 1"?

it's also luks encrypted partition and unlocked during booting. In fact mapping is normal during booting and no delay.

Another info is that when automatically mapping usb hard drive, every time delay happen.

```

ls -la /dev/mapper/
total 0
drwxr-xr-x  2 root root     160 2008-06-30 04:15 .
drwxr-xr-x 14 root root   13860 2008-06-30 04:16 ..
crw-rw----  1 root root  10, 63 2008-06-30 11:55 control
brw-rw----  1 root disk 254,  0 2008-06-30 03:56 sda2
brw-rw----  1 root disk 254,  1 2008-06-30 03:56 sda3


```

---

### Post by ekerazha on 2008-07-20
> **say2sky said:**
> 

```

sudo cryptsetup --verify-passphrase --verbose --hash=sha512 --cipher=aes-xts-benbi:sha512 --key-size=512 luksFormat /dev/sda8


```

--hash=sha512 doesn't have any effect using LUKS (it uses its own hashing mathod).

--cipher=aes-xts-benbi:sha512 isn't correct, why ":sha512"? You aren't using CBC-ESSIV, and why "xts-benbi"? The proper usage is "xts-plain".

---

### Post by say2sky on 2008-07-22
> **ekerazha said:**
> --hash=sha512 doesn't have any effect using LUKS (it uses its own hashing mathod).

--cipher=aes-xts-benbi:sha512 isn't correct, why ":sha512"? You aren't using CBC-ESSIV, and why "xts-benbi"? The proper usage is "xts-plain".


about --hash=sha512, following is from man cryptsetup and it tell how cryptsetup can accept user's chosed hash
```

 --hash, -h
              specifies  hash  to use for password hashing. This option is only relevant for
              the "create" action. The hash string is passed to  libgcrypt,  so  all  hashes
              accepted by gcrypt are supported. Default is "ripemd160".

```

according to this link [http://www.spinics.net/lists/dm-crypt/msg01073.html](http://www.spinics.net/lists/dm-crypt/msg01073.html)
benbi uses 64 bit tweaks for xts where plain uses 32 bit. so it is more security choice

---

### Post by ekerazha on 2008-07-22
> **say2sky said:**
> about --hash=sha512, following is from man cryptsetup and it tell how cryptsetup can accept user's chosed hash
```

 --hash, -h
              specifies  hash  to use for password hashing. This option is only relevant for
              the "create" action. The hash string is passed to  libgcrypt,  so  all  hashes
              accepted by gcrypt are supported. Default is "ripemd160".

```

Yeah, if you use cryptsetup without LUKS. But if you use LUKS, --hash is ignored because LUKS always uses SHA1/HMAC.

MAN:
```

Password processing is totally different for LUKS. LUKS uses PBKDF2 to protect against dictionary attacks (see RFC 2898). LUKS will always use SHA1 in HMAC mode, and no other mode is supported at the moment. Hence, -h is ignored. 

```

> 
according to this link [http://www.spinics.net/lists/dm-crypt/msg01073.html](http://www.spinics.net/lists/dm-crypt/msg01073.html)
benbi uses 64 bit tweaks for xts where plain uses 32 bit. so it is more security choice
AES-XTS specs [http://grouper.ieee.org/groups/1619/email/pdf00086.pdf](http://grouper.ieee.org/groups/1619/email/pdf00086.pdf) says it uses a little-endian byte array (ex. -plain), "-benbi" was implemented because LRW required a big-endian array.

---

### Post by say2sky on 2008-07-23
> **ekerazha said:**
> Yeah, if you use cryptsetup without LUKS. But if you use LUKS, --hash is ignored because LUKS always uses SHA1/HMAC.

MAN:
```

Password processing is totally different for LUKS. LUKS uses PBKDF2 to protect against dictionary attacks (see RFC 2898). LUKS will always use SHA1 in HMAC mode, and no other mode is supported at the moment. Hence, -h is ignored. 

```


AES-XTS specs [http://grouper.ieee.org/groups/1619/email/pdf00086.pdf](http://grouper.ieee.org/groups/1619/email/pdf00086.pdf) says it uses a little-endian byte array (ex. -plain), "-benbi" was implemented because LRW required a big-endian array.

OK, that mean they will use the best possibility for the user's option, right? So my command option don't have bad effect if sha512 is not implemented by LUKS. You know I try a lot to make system more security.

---

### Post by ekerazha on 2008-07-23
> **say2sky said:**
> OK, that mean they will use the best possibility for the user's option, right? So my command option don't have bad effect if sha512 is not implemented by LUKS. You know I try a lot to make system more security.

"-h sha512" doesn't have any effect because it is ignored. About :sha512 after the cipher, it is wrong because you don't use ESSIV, but I don't know the effect, *maybe* it's just ignored too.

I use
```

cryptsetup -c aes-xts-plain -y -s 512 luksFormat /dev/sdax

```

---

### Post by say2sky on 2008-07-23
> **ekerazha said:**
> "-h sha512" doesn't have any effect because it is ignored. About :sha512 after the cipher, it is wrong because you don't use ESSIV, but I don't know the effect, *maybe* it's just ignored too.

I use
```

cryptsetup -c aes-xts-plain -y -s 512 luksFormat /dev/sdax

```


I don't use ESSIV, because  xts is more security. 

-h sha512 is ignored, doesn't necessary meaning :sha512 is useless, is it right?

---

### Post by ekerazha on 2008-07-23
> **say2sky said:**
> I don't use ESSIV, because  xts is more security. 

-h sha512 is ignored, doesn't necessary meaning :sha512 is useless, is it right?

"-h sha512" and ":sha512" are two different things, the first is ignored, the second is wrong (and *maybe* ignored too) because you don't use ESSIV: ":sha512" would be the hash used to generate IVs using the ESSIV method. No ESSIV no ":HASH".

---

### Post by say2sky on 2008-07-23
> **ekerazha said:**
> "-h sha512" and ":sha512" are two different things, the first is ignored, the second is wrong (and *maybe* ignored too) because you don't use ESSIV: ":sha512" would be the hash used to generate IVs using the ESSIV method. No ESSIV no ":HASH".


OK, thanks a lot for your help and useful info. I will not use this :sha512 again.

---

