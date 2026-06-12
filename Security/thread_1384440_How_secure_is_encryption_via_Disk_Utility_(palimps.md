---
title: "How secure is encryption via Disk Utility (palimpsest)"
date: 2010-01-18
forum: Security
---

### Post by pir on 2010-01-18
Hi,
I encrypted a harddisk via Disk Utiluty. What alogythm is it encrypted by now?
Is it safe? What should I be aware about?

Thanks for the info :)

---

### Post by kiranmurari on 2010-01-19
Hi,
   	Palimpsest uses Linux Unified Key Setup (LUKS) which is a disk encryption specification. The reference implementation for LUKS works on Linux and is based on an enhanced version of cryptsetup ([http://en.wikipedia.org/wiki/Cryptsetup](http://en.wikipedia.org/wiki/Cryptsetup)), using dm-crypt ([http://en.wikipedia.org/wiki/Dm-crypt](http://en.wikipedia.org/wiki/Dm-crypt)) as the disk encryption backend
   	

For further information, please refer: [http://code.google.com/p/cryptsetup/](http://code.google.com/p/cryptsetup/)
   	

Hope this helps.
   	

Regards,
Kiran

---

### Post by leorolla on 2010-06-28
I'm also very interested in this question and I couldn't find the answer on these links.  When you use luks/cryptsetup/dm-crypt from terminal you have a bunch of options to choose concerning the algorithm, the key lenght, etc.  When you do it form the Disk Utility (which is the only way for normal people), all it tells you is "encrypted".

---

### Post by dino99 on 2010-06-28
[http://blog.carsoncheng.ca/2010/05/user-home-encryption-on-ubuntu-1004.html](http://blog.carsoncheng.ca/2010/05/user-home-encryption-on-ubuntu-1004.html)

---

### Post by leorolla on 2010-06-28
Couldn't find it there either.

---

### Post by rookcifer on 2010-06-28
> **pir said:**
> Hi,
I encrypted a harddisk via Disk Utiluty. What alogythm is it encrypted by now?
Is it safe? What should I be aware about?

Thanks for the info :)

Probably AES-256, which is pretty much the standard secure symmetric algorithm in the public world.  I typically use AES-128 as it will be quite a bit faster than 256 (and just as secure).

The only thing you should be concerned about is to make sure your key (pass phrase) is kept secret and is difficult to guess.

---

### Post by jbrown96 on 2010-06-28
Your passphrase is always the weakest part. There's no need to worry about the cipher, mode, or hash; they are secure beyond anything you can imagine.

---

### Post by leorolla on 2010-06-29
Thanks.

Do you know how faster is AES-128 compared to AES-256?

I know the passphrase is the weakest part.

But still I would be happy to know for sure what is the encryption+hash+salt+keystrenghening that palimpsest uses.

It's fantastic that my grandmother can use encryption and Ubuntu makes it easy for her, more user-friendly than Windows. But I would expect that the real difference here is that Ubuntu user interfaces also told us things instead of just making choises for us.

---

### Post by ThorX89 on 2011-12-19
> **leorolla said:**
> Thanks.

Do you know how faster is AES-128 compared to AES-256?

I know the passphrase is the weakest part.

But still I would be happy to know for sure what is the encryption+hash+salt+keystrenghening that palimpsest uses.

It's fantastic that my grandmother can use encryption and Ubuntu makes it easy for her, more user-friendly than Windows. But I would expect that the real difference here is that Ubuntu user interfaces also told us things instead of just making choises for us.

Hi. It's AES-256 for sure. At least, that's what I get on my partition encrypted with palimpsest.
You can re-check this on your own machine:
[LIST=1]
[*]Create an encrypted partition with palimpsest
[*]Use palimpsest to unlock it and mount it.
[*]Use the `mount` command (no parameters) to find which device in /dev/mapper corresponds to your encrypted partition
[*]Run ```
sudo cryptsetup status /dev/mapper/$UR_ENCRYPTED_DEVICE 
```
[/LIST]

Using this procedure, I get the following output:
> /dev/mapper/udisks-luks-uuid-0353e1b0-b793-4667-8d21-c39eaacc0b55-uid1000 is active:
  cipher:  aes-cbc-essiv:sha256
**  keysize: 256 bits**
  device:  /dev/sdb6
  offset:  2056 sectors
  size:    33552376 sectors
  mode:    read/write

---

