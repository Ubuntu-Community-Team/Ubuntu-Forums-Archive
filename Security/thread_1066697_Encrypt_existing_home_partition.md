---
title: "Encrypt existing home partition"
date: 2009-02-11
forum: Security
---

### Post by ushills on 2009-02-11
I want to encrypt my home partition with cryptsetup, however, in order to do this I need to do the following.

[LIST=1]
[*]Split my current home partition in two (home1, home2)

[*]Encrypt the new partition, home2, with cryptsetup

[*]Copy the data from home1 to home2

[*]Remove home1
[/LIST]

Increase the size of the encrypted partition home 2 to include the space left from home1.

Unlock home partition for 4 users with just them logging in to make it transparent to the user.

Can I do this, mostly concerned with increasing size of encrypted partion with cryptsetup and unlocking transparently.

---

### Post by hyper_ch on 2009-02-11
you can increase the size of a luks partition. And as for unlocking the encrypted partition, you'll need to install according drivers and load the modules at boot and then make an entry in /etc/crypttab.

But depending on what you want to do it might be faster and a lot simpler to re-install everything witht the altnerate cd and enable full disk encryption.

---

### Post by HermanAB on 2009-02-11
It won't work.

You can grow a partition one way only - towards the end.  So you can grow partition 1 into partition 2, but you cannot grow partition 2 into partition 1.

Cheers,

Herman

---

