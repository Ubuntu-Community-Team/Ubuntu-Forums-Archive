---
title: "Am I secure ?? (what about /tmp ?)"
date: 2008-09-22
forum: Security
---

### Post by mat_london on 2008-09-22
Hi,

I've got a Truecrypt 6 encrypted home drive and don't use swap (2.5 gig of ram)
But I'm still paranoid about having my laptop stolen and my bank etc details nicked.
Is there an easy way to make my /tmp and /var/tmp directories secure ?
Is there anything else I should be worried about ??

Best

Mat

---

### Post by cdenley on 2008-09-22
> **mat_london said:**
> Hi,

I've got a Truecrypt 6 encrypted home drive and don't use swap (2.5 gig of ram)
But I'm still paranoid about having my laptop stolen and my bank etc details nicked.
Is there an easy way to make my /tmp and /var/tmp directories secure ?
Is there anything else I should be worried about ??

Best

Mat

Add a line like this in /etc/fstab
```

none /tmp tmpfs defaults 0 0

```
Now files written to /tmp will not be written disk. No need to worry about encryption. Just make sure you have enough extra memory for all your /tmp files.

I doubt bank details would be written to /tmp. If you're worried about your firefox cache, I think thats in your home.

---

### Post by mat_london on 2008-09-22
Great Thanks done it

Mat

---

### Post by cdenley on 2008-09-23
You can also do the same thing with home. I used to do this, but it got too annoying with noscript not remembering which sites are allowed. I haven't tested these commands, so use them at your own risk. Make sure you don't write too much data to /home, and remember that anything written to /home will not be there when you reboot.

boot into recovery mode
```

echo session required pam_mkhomedir.so skel=/etc/skel/>>/etc/pam.d/common-session
mv /home /home.orig
mkdir /home
echo none /home tmpfs defaults 0 0>>/etc/fstab

```

---

