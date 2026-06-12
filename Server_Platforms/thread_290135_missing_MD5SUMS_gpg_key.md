---
title: "missing MD5SUMS gpg key"
date: 2006-10-31
forum: Server Platforms
---

### Post by mjbjr on 2006-10-31
In the 6.10 mirror sites' distribution dir, there is a MD5SUMS file that
contains the md5sums for various ubuntu 6.10 iso files in that dir.

There is also a MD5SUMS.gpg file which I take to be the gpg signature
for the MD5SUMS file.

Where is the gpg public key that can be used to verify the MD5SUMS file?
Or a key id and fingerprint to facilitate the key import from a public
key server?

I've searched the ubuntu web site high and low, did a google search,
and I'll be damned if I can find it.

Thanks

---

### Post by panyuweimin on 2007-01-07
Hi, 

I did a search on pgp.mit.edu with "ubuntu signing key" and found this

pub  1024D/FBB75451  created: 2004-12-30  expires: never       usage: SC
                     trust: unknown       validity: unknown
[ unknown] (1). Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

 Primary key fingerprint: C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451

It is the key for my downloaded MD5SUMS.pgp file. 

I hope this helps.

---

