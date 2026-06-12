---
title: "Modifying an encrypted LVM"
date: 2008-11-13
forum: Security
---

### Post by Orestes on 2008-11-13
Hi all,

I've recently installed 8.10 on my laptop, using encrypted LVM from the alternate install CD. I used a twenty digit random hexadecimal passkey for the password.

After tweaking and installing all my favourite software and kernel modules, I had the wonderful idea of maybe using a USB memory stick to store the passkey on  and let the system automatically read it so I don't have to keep typing it every time I boot it.

Unfortunately, all of the tutorials appear to require a fresh install. Does anybody know if there is a way I can be lazy and put my existing key in a textfile on my USB key without starting from scratch?

Any suggestions would be gratefully appreciated!

---

### Post by Nostalos on 2008-11-13
Should just be able to add a new key to the device.  You can have up to 10.  

Here's the Link to a wiki on how to create a new key on the USB. [http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq](http://www.saout.de/tikiwiki/tiki-index.php?page=LUKSFaq)

Should just be a matter of modifying your /etc/crypttab to use that key rather than password.    Havn't dont this particular scenario myself. But it should work.

---

### Post by laughlin.bill on 2010-05-03
Any luck with this?  I'm looking to make the same change and would really appreciate someone's experience before I "dive in"

---

