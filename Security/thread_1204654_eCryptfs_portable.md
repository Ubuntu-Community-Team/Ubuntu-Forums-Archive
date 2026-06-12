---
title: "eCryptfs portable?"
date: 2009-07-05
forum: Security
---

### Post by cd-r80 on 2009-07-05
How I move with eCryptfs files? Do I just copy the file from Private directory on USB stick. How I open it on other Ubuntu box? How it does not get messed with another box Private directory?

---

### Post by Agent ME on 2009-07-05
If you copy the ~/.ecryptfs directory over, then files from ~/.Private will work there too.

---

### Post by cd-r80 on 2009-07-05
And Private files will be erased / overwritten on the the other machine then? It destroys files on other machine?

---

### Post by cd-r80 on 2009-07-05
I read this article. I understood wrong or is the article wrong?
[http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html)

It says: "eCryptfs stores cryptographic metadata in the header of each file written" What the h*** is then .ecryptfs folder?

And:"so that encrypted files can be copied between hosts; the file will be decryptable with the proper key, **and there is no need to keep track of any additional information aside from what is already in the encrypted file itself."**

If I copy the file from /Private to USB stick it is decrypted. Unmounted I cannot copy.

With gzip & mcrypt everything looks easier?

---

### Post by Agent ME on 2009-07-05
That article you linked to is pretty out of date.

---

### Post by cd-r80 on 2009-07-05
Why you say out of date. January 2009?

---

### Post by Agent ME on 2009-07-05
Whoever made the article seems to just be repeating old information, and making things too complex. Way too complicated.

To set up an automatically mounting Private folder encrypted by your password, "sudo apt-get install ecryptfs-utils ; ecryptfs-setup-private" is all that needs to be done.

---

### Post by HermanAB on 2009-07-05
Howdy,

Depending on how portable you need things to be, you could use LUKS and FreeOTFE as described here:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)
[http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

