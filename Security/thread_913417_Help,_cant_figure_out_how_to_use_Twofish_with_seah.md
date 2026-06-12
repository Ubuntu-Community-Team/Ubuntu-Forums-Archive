---
title: "Help, cant figure out how to use Twofish with seahorse"
date: 2008-09-07
forum: Security
---

### Post by Drizzel on 2008-09-07
I have been scouring the net trying to figure out how to use the Twofish algorithm and other algorithms with Seahorse. I want to create a key with Twofish instead of the using the default DSA/RSA that Seahorse offers under advanced key options. I read that GnuPG supports Twofish, but for the life of me I cant figure out how to create keys using Twofish. I know Seahorse is just a gui for GnuPG.. Seems adding other algorithms shouldnt be so difficult. If it cant be done with Seahorse/GnuPG, is there another encryption app I can use that does have Twofish support when creating keys?

---

### Post by Drizzel on 2008-09-10
So nobody uses Twofish? There is like zero documentation on an encryption app that works with ubuntu.. :( I'm seriously shocked.. I thought linux users were security savvy.

---

### Post by yetanothersteve on 2008-09-10
I don't think that is an option.
The key creation is really a function of GnuPG. If you use gpg to generate a key, these are the options given:
```
$ gpg --gen-key
gpg (GnuPG) 1.4.6; Copyright (C) 2006 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
Your selection? 
```

If you just want symmetrically encrypt, then use gpg directly and specify the algorithm you want, like so.

```
$ gpg -c --cipher-algo TWOFISH test
File `test.gpg' exists. Overwrite? (y/N) y

```

You may want to check out the comments at the bottom of this page regarding the gpg.conf file:
[http://php.8ez.com/drsmall/blog/?p=209]("http://php.8ez.com/drsmall/blog/?p=209")

---

### Post by kevdog on 2008-09-11
You guys are really misconstruing key creation algorithm and algorithm used for the symmetric cipher.

I wrote an advanced gnupg tutorial a long time ago but never finished, however I thought it useful:

[http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)

---

### Post by Drizzel on 2008-09-12
Thx both of you! I know.. I'm OC about my encryption keys. I have done a lot of research on TWOFISH and I love it. I used PGP desktop on my windows setup before I made the switch and had a really nice TWOFISH keypair. I still have the keys, but for some reason Seahorse doesnt like them. Great tut kevdog! Your effort is appreciated. :) Take care guys!

---

### Post by kevdog on 2008-09-13
Just for your information -- TWOFISH is a good algorith -- but even Bruce Schneier -- TWOFISH's creator -- does not recommend use of TWOFISH since the AES competition.

Here is a snippet of a conversation I've had on the GnuPG mailing list, and Bruce Schneier's direct response when I emailed him to comment on the statement:

The RFC which specifies the OpenPGP protocol first came out in 1998.  It
began to receive revisions almost immediately (the -bis series:
RFC2440bis1, RFC2440bis2, etc.).  These -bis series were meant as
previews of the next official RFC, whenever it would be published.

However, the original RFC remained canonical.  That specified DSA-1024.
 In order to closely follow the RFC, GnuPG left the default as DSA-1024.
 This was probably the right call to make for interoperability reasons.

As an example of what happens when people decide to move beyond the RFC,
look at PGP 7.0.  Management at PGP Security decided that Twofish was
the likely winner of the AES competition, and so they put Twofish into
PGP.  This put pressure on GnuPG to put Twofish into GnuPG, in order to
interoperate with PGP.

Twofish is almost entirely abandoned nowadays, but it still exists in
PGP and GnuPG.  Once a bad decision is made in engineering, the
engineers are stuck supporting it forever.  Take a look through the
archives sometime and see how many people have bitterly complained about
TIGER192 no longer being supported, despite the fact it was part of
GnuPG for about three and a half milliseconds.

I suspect--although I do not know--that a similar motivation drove
GnuPG's decision to leave DSA-1024 as the standard.

Now that RFC4880 has come out, supplanting RFC2440, I imagine the way is
clear to make all new keys DSA-2048 or DSA-3072.  After all, now it's
part of the standard.

Bruce recommends against using Twofish for crypto applications.

He has never backed off from either of two claims:

       1.  Twofish is a secure cipher that would have made an
           excellent AES.
       2.  People should use AES for symmetric crypto needs.

He has said #1 many times and keeps a page on his site devoted to the
most recent research into Twofish.  He has said #2 many times,
particularly in his book _Practical Cryptography_.


Bruce's Response:

Honestly, I think there's more value in using a single standard.  There's nothing wrong with using Twofish -- it's not insecure or anything -- I just think that we should all use AES.

Many, many products use Twofish:

       [http://www.schneier.com/twofish-products.html](http://www.schneier.com/twofish-products.html)


When he is referring to AES, he's really referring to GnuPG's implementation of the Rijndael (pronounced "Rain doll") algorithm.  Those in the cryptographic community always refer to Rijndael, rather than AES -- since AES = American Encryption Standard, could be subject to change with time.

---

