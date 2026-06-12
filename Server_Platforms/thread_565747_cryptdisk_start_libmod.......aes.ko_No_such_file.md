---
title: "cryptdisk start: /lib/mod.../..../aes*.ko: No such file"
date: 2007-10-02
forum: Server Platforms
---

### Post by emil.s on 2007-10-02
I have folowed this guide for setting up som encrypted disks:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto5](https://help.ubuntu.com/community/EncryptedFilesystemHowto5)

I don't want to encrypt the root partition, but all other disks should be nice. :)

I encrypted the disks with "cryptsetup --verify-passphrase --verbose --hash=sha256 --cipher=aes-cbc-essiv:sha256 --key-size=256 luksFormat /dev/*disk*".
Good so far...

But when the computer boot, /etc/init.d/cryptdisk can't mount them bacause of the "/lib/modules/2.6.22.9-emil.s/kernel/arch/*/*/aes*.ko" is missing.
And that is, (as you see), becaus of my own compiled kernel (where i have built in support for AES and SHA).

But i can mount it manualy:
```
root@servern: /home/emil # cryptsetup luksOpen /dev/hda2 encrypted-files
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.
```

```
root@servern: /home/emil # /etc/init.d/cryptdisks restart 
 * Stopping remaining crypto disks...
 * encrypted-swap (stopped)...
 * filer (stopped)...
   ...done.
 * Starting remaining crypto disks...
ls: /lib/modules/2.6.22.9-emil.s/kernel/arch/*/*/aes*.ko: No such file or directory

```

```
root@servern: /home/emil # cat /etc/crypttab 
# <target name>	<source device>		<key file>	<options>
encrypted-swap  /dev/hda3       	/dev/urandom    swap                                                                                       
filer		/dev/hda2		none		luks

```

How do i solve this?

---

### Post by /etc/init.d/ on 2007-10-03
By default, AES is compiled as a module, not built in to the kernel.  I would think cryptsetup is probing for the AES module and can't find it because it has been built in.

Posting the config you used to build your kernel would help (/boot/`uname -r`-config), specifically any *CRYPTO* sections.

---

### Post by emil.s on 2007-10-03
> **/etc/init.d/ said:**
> By default, AES is compiled as a module, not built in to the kernel.  I would think cryptsetup is probing for the AES module and can't find it because it has been built in.

Posting the config you used to build your kernel would help (/boot/`uname -r`-config), specifically any *CRYPTO* sections.

The cryptographic section:
```
#
# Security options
#
# CONFIG_KEYS is not set
# CONFIG_SECURITY is not set

#
# Cryptographic options
#
CONFIG_CRYPTO=y
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_ABLKCIPHER=m
CONFIG_CRYPTO_BLKCIPHER=y
CONFIG_CRYPTO_HASH=m
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_HMAC=m
CONFIG_CRYPTO_XCBC=m
CONFIG_CRYPTO_NULL=m
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_SHA1=y
CONFIG_CRYPTO_SHA256=y
CONFIG_CRYPTO_SHA512=y
CONFIG_CRYPTO_WP512=y
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_ECB=m
CONFIG_CRYPTO_CBC=y
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_CRYPTD=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_TWOFISH=y
CONFIG_CRYPTO_TWOFISH_COMMON=y
CONFIG_CRYPTO_TWOFISH_586=y
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_AES=y
CONFIG_CRYPTO_AES_586=y
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_CRC32C=m
CONFIG_CRYPTO_CAMELLIA=m
# CONFIG_CRYPTO_TEST is not set

#
# Hardware crypto devices
#
# CONFIG_CRYPTO_DEV_PADLOCK is not set
# CONFIG_CRYPTO_DEV_GEODE is not set

```

Full config:
[http://sandnabba.se/~emil/filer/servern_kernel_config_v2](http://sandnabba.se/~emil/filer/servern_kernel_config_v2)

I'm trying to have the kernel so monolithic as possible. So i can run it without needing any modules.

---

### Post by /etc/init.d/ on 2007-10-18
Sorry for the late response.

Quote from [http://www.rocklinux.org/wiki/Encrypted_Root](http://www.rocklinux.org/wiki/Encrypted_Root)

> You must have dmcrypt **and aes-i586 configured as modules in your kernel**.

Looks as though dmcrypt does not support AES being built in.

---

### Post by emil.s on 2007-10-21
> **/etc/init.d/ said:**
> Sorry for the late response.

Quote from [http://www.rocklinux.org/wiki/Encrypted_Root](http://www.rocklinux.org/wiki/Encrypted_Root)



Looks as though dmcrypt does not support AES being built in.

Ok... I wrote a script which fixed it. But thanks anyway! :)

---

