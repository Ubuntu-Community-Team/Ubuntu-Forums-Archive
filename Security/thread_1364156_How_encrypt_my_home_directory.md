---
title: "How encrypt my home directory?"
date: 2009-12-25
forum: Security
---

### Post by Neo40 on 2009-12-25
Hello,

I installed Jolicloud into my Aspire One. Jolicloud is based on Ubuntu 9.04.
I would like to encrypt my home directory just like Karmic does.
Someone could help me how can I do that?

Thank you for your help!

---

### Post by BkkBonanza on 2009-12-25
The easiest way is to use ecryptfs and choose it at install time. Since you are already going you can use this tutorial to convert to ecryptfs. I did it and it worked well for me. It's written by one of the core Ubuntu developers.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

Check out his other blog entries as well related to ecryptfs - very useful.

---

### Post by HermanAB on 2009-12-26
You can use LUKS and the little wizards that you'll find here:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

The howto is written for USB disks, but in principle it works on any partition.

---

