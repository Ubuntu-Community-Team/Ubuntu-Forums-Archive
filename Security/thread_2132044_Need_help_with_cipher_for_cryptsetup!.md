---
title: "Need help with cipher for cryptsetup!"
date: 2013-04-03
forum: Security
---

### Post by daKoolaid on 2013-04-03
I am encrypting a partition on an external drive I take to work. I read a little on encryption but have some questions about which cipher options to use.

Where can I find the available ciphers cryptsetup can use? This is not in the man page.

Say I choose aes-xts-**plain**. What is the difference between that and aes-xts-**plain64**? Would this be a stronger option over the default aes-cbc-essiv:sha256?

I found the site below very helpful but why does it use AES key size of 512 bits when AES cipher only supports up to 256? Is this an error?
[http://blog.markloiseau.com/2012/05/ubuntu-aes-xts-plain64/](http://blog.markloiseau.com/2012/05/ubuntu-aes-xts-plain64/)

Thanks in advance!

---

### Post by daKoolaid on 2013-04-03
Well, I just went with aes-xts-plain since it's the newest version of aes. Can't go wrong with that I guess.

---

### Post by KaosuX on 2013-04-06
> **daKoolaid said:**
> Well, I just went with aes-xts-plain since it's the newest version of aes. Can't go wrong with that I guess.

XTS-PLAIN is perfectly fine when encrypting hard drives that are smaller than 2TB's. However, using XTS-PLAIN on hard drives larger than 2TB's will dramatically reduce your security because of repeating initialization vectors. Since XTS-PLAIN64 is backwards compatible with XTS-PLAIN, I usually just choose XTS-PLAIN64. However, if you are using a drive smaller than 2TB's then there is no reason to use XTS-PLAIN64 over XTS-PLAIN. Also, make sure to correctly double your key size when using the XTS mode of operation to achieve your desired end-result. For example, if you wanted to use AES256 in the XTS mode of operation then you would want to specify your key size to be 512-bits, likewise specifying a key size of 256-bits would result in AES128 being used in the XTS mode of operation. This is because when you use XTS you need to double the key size to be as effective as the other modes of operation. 

Hopefully this was able to answer you question clearly.

---

### Post by Stonecold1995 on 2013-05-04
Like said before, xts-plain64 can secure larger amounts of data with the same key than xts-plain.  And [COLOR=#000000]aes-cbc-essiv:sha256 is a lot weaker (still powerful though).  So yeah, I'd go with xts-plain64.
[/COLOR]

---

