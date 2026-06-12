---
title: "cryptsetup LUKS conversion"
date: 2009-12-16
forum: Security
---

### Post by Jonnyuser on 2009-12-16
Hi.

I have a storage server with some TB capacity, full of data, and encrypted with cryptsetup. It was problem free in the last years, but now there is a demand to have more passwords to mount it. 
I know LUKS extension has this feature, but I don't know how to convert the whole storage to the format of the LUKS, and add more keys to it.
Is there any way to do this without reformat the whole storage ? 

Thank you. 
Jonny

---

### Post by HermanAB on 2009-12-17
You cannot convert on the fly.  You need to save the data somewhere else, then reformat the partition with LUKS and then copy the data back.

See the LUKS wizards available here:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by shaggy999 on 2009-12-18
All you need to do is add more passwords, right? You don't need to reformat anything. You can use a LiveCD to unlock the LUKS partition and then there's a command to add additional keys.

---

