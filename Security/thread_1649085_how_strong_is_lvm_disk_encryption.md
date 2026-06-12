---
title: "how strong is lvm disk encryption?"
date: 2010-12-19
forum: Security
---

### Post by pizztry on 2010-12-19
I'm using ubuntu 10.10 installed with the alternate disk with that lvm full disk encryption option. I can't find any details on what the lvm disk encryption is or its strengths/weaknesses.

does it offer the same level of protection as truecrypt or is it a fairly weak level of security?

---

### Post by cariboo on 2010-12-19
LVM and encryption are two separate things, for more in for on LVM have a look [here]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)"), I haven't used full disk encryption, so I'll leave it to the others to explain that.

---

### Post by rookcifer on 2010-12-19
The full disk crypto options offered by Ubuntu are just as strong as Truecrypt, while offering more choices.  With TC you can choose between three algorithms -- AES, Serpent, Twofish (or a cascade).  With Ubuntu you can use any of those algorithms as well as others.  The default is AES-CBC-essiv:sha256.  This is good enough for anything and is extremely strong. If you're extremely paranoid you can use 256 bit keys (which are overkill and not necessary).

---

