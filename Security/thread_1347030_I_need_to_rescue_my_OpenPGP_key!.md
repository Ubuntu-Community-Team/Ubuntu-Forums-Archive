---
title: "I need to rescue my OpenPGP key!"
date: 2009-12-05
forum: Security
---

### Post by SydneyMyers on 2009-12-05
Hi to all!

I already posted my problem [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1346052").

I'm posting it in this froum as well as it is quite relevant.

The summary is that I messed up my Linux boot data and I need to get my OpenPGP key from my installation of Ubuntu 9.10. Everything (the partition, the data) is intact and I have access to it through the Live CD.

Can anyone help? Is there any way to get my key without booting into Ubuntu?

---

### Post by Agent ME on 2009-12-05
Copy the /home/*myuser*/.gnupg directory from your old partition to the new one.

---

### Post by tubbygweilo on 2009-12-05
You could also create revocation certificates for your keys if you have not yet done so as you never know when they might be needed;)

---

