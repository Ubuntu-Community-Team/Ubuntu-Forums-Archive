---
title: "How can I encrypt a Ubuntu 9.10 flash drive"
date: 2010-02-16
forum: Security
---

### Post by ulg on 2010-02-16
I loaded Ubuntu desktop onto my flash drive with the USB Installer For Ubuntu from [http://www.pendrivelinux.com/create-...sb-in-windows/](http://www.pendrivelinux.com/create-...sb-in-windows/)  

I'll be placing sensitive data on the drive & need to figure out how to encrypt it. From what i've read so far, the easiest way will be to encrypt the swap, /home, tmp, temp files. Not quite sure how to do this. I'd prefer to encrypt the whole drive, but this seems quite complicated. 

Any suggestions appreciated.

---

### Post by Megaptera on 2010-02-16
Have you considered using TrueCrypt in portable mode to creat an encrypted & hidden file on your flashdrive?

[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

---

### Post by bodhi.zazen on 2010-02-16
> **ulg said:**
> I loaded Ubuntu desktop onto my flash drive with the USB Installer For Ubuntu from [http://www.pendrivelinux.com/create-...sb-in-windows/](http://www.pendrivelinux.com/create-...sb-in-windows/)  

I'll be placing sensitive data on the drive & need to figure out how to encrypt it. From what i've read so far, the easiest way will be to encrypt the swap, /home, tmp, temp files. Not quite sure how to do this. I'd prefer to encrypt the whole drive, but this seems quite complicated. 

Any suggestions appreciated.

Personally I would simply make a crypt for your sensitive data.

You can use ecryptfs

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

You can also perform an encrypted installation using LUKS.

You could also use truecrypt which is cross platform, and thus has some advantages.

> **Megaptera said:**
> Have you considered using TrueCrypt in portable mode to creat an encrypted & hidden file on your flashdrive?

[http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable)

I would not consider a crypt to be "hidden", they stick out like the 4th of July (The crypt itself is pretty obvious, and I do not buy into the "plausible deniability" of truecrypt).

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by ulg on 2010-02-17
You can also perform an encrypted installation using LUKS.
  How would I make an encrypted installation using LUKS?       I worry about encrypting my data and having other information accessible/decrypted.  Thanks.

---

### Post by bodhi.zazen on 2010-02-17
> **ulg said:**
> You can also perform an encrypted installation using LUKS.
  How would I make an encrypted installation using LUKS?       I worry about encrypting my data and having other information accessible/decrypted.  Thanks.

Use the alternate CD

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

---

### Post by giammy on 2010-02-17
Hi,

I prepared for the same reason a usb stick - see [http://www.cloudusb.net](http://www.cloudusb.net)
using EncFS to crypt the directory where I put sensible data.

bye
Giammy

---

