---
title: "Seahorse question"
date: 2009-08-06
forum: Security
---

### Post by EM man on 2009-08-06
I created a key using Seahorse, and when I exported it to my desktop and opened the file, it is labelled as a "private key".  Specifically, I see "-----BEGIN PGP PRIVATE KEY BLOCK-----
Version: GnuPG v1.4.9 (GNU/Linux)" folowed by the key, followed by "-----END PGP PRIVATE KEY BLOCK-----"


Isn't Seahorse supposed to export the public key?

---

### Post by niteshifter on 2009-08-07
Hi,

Not if you tell it to Export Complete Key (Properties, Details tab) - you get both parts. If you just want to export the public key right click on the key and click Export Public Key.

---

### Post by EM man on 2009-08-07
> **niteshifter said:**
> Hi,

Not if you tell it to Export Complete Key (Properties, Details tab) - you get both parts. If you just want to export the public key right click on the key and click Export Public Key.

I deleted the existing key, started over, and did that, and I still get a text file than only refers to a private key (twice, before and after the key itself), with no mention of a public key.

---

### Post by ybH65aJM on 2009-08-19
This is happening to me as well. It seems that old versions of Seahorse have a button that says "Export Public Key" (from tutorials I've found on Google) but I can't for the life of me find it in this version (whatever version comes on 9.04).  Anyone know what's going on? This renders Seahorse completely useless to me.

---

### Post by student68 on 2010-03-15
I know this is old, but as reference for people who are searching the forums:
you just right click your key and select copy. Then you can paste it in a test file etc.

---

### Post by sefs on 2012-01-11
Ok I am having some troubles....

How can I export both keys into one file.

If i right click and export it exports the public part

If i go into properties and export it exports the private part.

When i try to import the private file into gnu privacy assistant (gpa)  it just imports what looks like a public key (blue) in color as opposed to both the private/public key.

How can I create a key in seahorse that is properly importable to gpa.

Thanks.

---

