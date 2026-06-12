---
title: "How do I add support for md5 using crypt() with 8.04 LTS?"
date: 2008-09-22
forum: Server Platforms
---

### Post by obvious on 2008-09-22
RESOLVED!

I'm running Ubuntu 8.04 LTS Hardy and turned it into a LAMP server with the following:
sudo tasksel install lamp-server

The question is:
How do I get this system to support md5 hashes with crypt()?  Out of the box I've got DES and extended DES support, but no support for md5 and blowfish.

Suggestions?

---

### Post by cdenley on 2008-09-22
> **obvious said:**
> I'm running Ubuntu 8.04 LTS Hardy and turned it into a LAMP server with the following:
sudo tasksel install lamp-server

The question is:
How do I get this system to support md5 hashes with crypt()?  Out of the box I've got DES and extended DES support, but no support for md5 and blowfish.

Suggestions?

I have a few hardy systems, server and desktop, and they all supported md5 by default. Are you sure you don't have any md5 support? How did you determine you don't?

If you want to use blowfish, look here.
[http://ubuntuforums.org/showthread.php?t=300208](http://ubuntuforums.org/showthread.php?t=300208)

If you want to use SHA512, wait for intrepid.
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786)

---

### Post by obvious on 2008-09-22
I double checked myself and it looks like I do have MD5 support, but not Extended DES.  I had mistaken one for the other.  I did a quick check with the following:
echo("DES is " . CRYPT_STD_DES . "<br>Extended DES is " . CRYPT_EXT_DES . "<br>MD5 is " . CRYPT_MD5 . "<br>BlowFish is " . CRYPT_BLOWFISH);

Any idea how to add extended DES support?

My apologies for the initial mistake.

---

### Post by cdenley on 2008-09-22
If you're using crypt within php, I think that would involve re-compiling php.
[http://us3.php.net/manual/en/function.crypt.php](http://us3.php.net/manual/en/function.crypt.php)
> 
At install time, PHP determines the capabilities of the crypt function and will accept salts for other encryption types.


---

### Post by obvious on 2008-09-22
You're right.  Thanks for nudging me in the right direction.  Much appreciated.

---

