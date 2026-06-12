---
title: "[SOLVED] XKCD Crypto"
date: 2008-12-03
forum: The Cafe
---

### Post by Yuki_Nagato on 2008-12-03
Google search buries it beneath cryptography related topics.

What is this "crypto" mentioned in here?

_[http://www.xkcd.com/504/](http://www.xkcd.com/504/)_

I have heard nothing about it on the Linux Today feeds.

---

### Post by MaxIBoy on 2008-12-03
"Crypto" is short for "Cryptography."

In the past, it was illegal to export information related to encryption. Encryption was brought into sophistication during the second world war for use by spies, and thus was considered a defensive weapon and a reconnaissance tool.

Similarly, some of the first computers were for decryption. To this day, it is illegal for any company based in the USA to export any computer capable of performing more than 190 billion operations per second. (As of 2002, at least.) [http://www.wisconsinproject.org/pubs/editorials/2002/latimes-7-30-02.htm](http://www.wisconsinproject.org/pubs/editorials/2002/latimes-7-30-02.htm) That's why the Beowulf cluster website has been taken down in the past.

---

### Post by zmjjmz on 2008-12-03
> **MaxIBoy said:**
> "Crypto" is short for "Cryptography."

In the past, it was illegal to export information related to encryption. Encryption was brought into sophistication during the second world war for use by spies, and thus was considered a defensive weapon and a reconnaissance tool.

Similarly, some of the first computers were for decryption. To this day, it is illegal for any company based in the USA to export any computer capable of performing more than 190 billion operations per second. (As of 2002, at least.) [http://www.wisconsinproject.org/pubs/editorials/2002/latimes-7-30-02.htm](http://www.wisconsinproject.org/pubs/editorials/2002/latimes-7-30-02.htm) That's why the Beowulf cluster website has been taken down in the past.
Oh, wow, really?
I hope we use stronger encryption these days.

---

### Post by Grant A. on 2008-12-03
The US NIST is hosting a competition to choose the successor to SHA 1 & 2

[http://en.wikipedia.org/wiki/NIST_hash_function_competition]("http://en.wikipedia.org/wiki/NIST_hash_function_competition")

MD6 is currently entered in the competition.

---

### Post by MaxIBoy on 2008-12-03
> **Grant A. said:**
> The US NIST is hosting a competition to choose the successor to SHA 1 & 2

[http://en.wikipedia.org/wiki/NIST_hash_function_competition]("http://en.wikipedia.org/wiki/NIST_hash_function_competition")

MD6 is currently entered in the competition.

Somewhere in the encryption algorithm, the following hash MUST be involved as a seed:
2595b6adb903d7c770a79b0429423f8d


In case you're wondering what that is:
```
maxtothemax@maxtothemax-desktop:~$ md5 '/home/maxtothemax/Music/Jimi Hendrix/Voodoo Child: The Jimi Hendrix Collection/15 - Stepping Stone.ogg' 
2595b6adb903d7c770a79b0429423f8d	/home/maxtothemax/Music/Jimi Hendrix/Voodoo Child: The Jimi Hendrix Collection/15 - Stepping Stone.ogg
maxtothemax@maxtothemax-desktop:~$ 

```

---

### Post by Yuki_Nagato on 2008-12-04
In other words, "Crypto" is not an actual program to prevent Comcast from burying its head in my packets to "sell me some advertisments."

Thank you.

---

