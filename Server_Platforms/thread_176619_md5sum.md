---
title: "md5sum"
date: 2006-05-15
forum: Server Platforms
---

### Post by mlind on 2006-05-15
Is md5sum supposed to a reference implementation of [RFC 1321]("http://www.faqs.org/rfcs/rfc1321.html") as hinted on md5sum's man page?

That RFC spec contains a test suite
```

MD5 test suite:
MD5 ("") = d41d8cd98f00b204e9800998ecf8427e
MD5 ("a") = 0cc175b9c0f1b6a831c399e269772661
MD5 ("abc") = 900150983cd24fb0d6963f7d28e17f72
MD5 ("message digest") = f96b697d7cb7938d525a2f31aaf161d0
MD5 ("abcdefghijklmnopqrstuvwxyz") = c3fcd3d76192e4007dfb496cca67e13b
MD5 ("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789") =
d174ab98d277d9f5a5611c2c9f419d9f
MD5 ("123456789012345678901234567890123456789012345678901234567890123456
78901234567890") = 57edf4a22be3c955ac49da2e2107b67a

```

But I'm unable to reproduce any of these, 
```

echo a | md5sum
60b725f10c9c85c70d97880dfe8191b3

```

when it should be 0cc175b9c0f1b6a831c399e269772661 as stated above. How
am I supposed to use md5sum for these? I'm able to produce correct digests with
Apache commons-codec tho.


(probably a wrong forum for this thread..?)

---

### Post by Sef on 2006-05-15
Sometimes it takes a few downloads before it downloads right.  Once it took me about 5 or 6 times to match the numbers.

---

### Post by mlind on 2006-05-15
Huh? :confused:  

I was wondering if someone could reproduce results in that RFC test suite using md5sum

---

### Post by Slim Odds on 2006-05-15
[QUOTE=mlind]Huh? :confused:  

I was wondering if someone could reproduce results in that RFC test suite using md5sum[/QUOTE]

"echo a" outputs 2 characters!

use "echo -n a"

---

### Post by mlind on 2006-05-15
[QUOTE=Slim Odds]"echo a" outputs 2 characters!

use "echo -n a"[/QUOTE]

Thanks! :cool:  

```

-n     do not output the trailing newline

```

next time, I should at least try to read the first page of the manual..  :rolleyes:

---

