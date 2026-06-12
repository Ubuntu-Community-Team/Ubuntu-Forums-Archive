---
title: "gpg signing key"
date: 2006-02-25
forum: Server Platforms
---

### Post by jchau on 2006-02-25
Can someone verify if I have the right keys & that they are good copies?  

When I type:
```
gpg --fingerprint 57548DCD
```I get
```
pub   1024D/57548DCD 1998-07-07 [expired: 2005-12-31)]
      Key fingerprint = 6BD9 050F D8FC 941B 4341  2DCC 68B7 AB89 5754 8DCD
uid                  Werner Koch (gnupg sig) <dd9jn@gnu.org>

```

and when I type:
```
gpg --fingerprint 1CE0C630
```I get
```
pub   1024R/1CE0C630 2006-01-01 [expires: 2008-12-31]
      Key fingerprint = 7B96 D396 E647 1601 754B  E4DB 53B6 20D0 1CE0 C630
uid                  Werner Koch (dist sig) <dd9jn@gnu.org>

```

Can someone help me verify that these are the right public keys for gnupg?

---

### Post by nanotube on 2006-02-27
what are these keys for?

---

### Post by jchau on 2006-02-27
gnupg.  If these keys are correct, I can use them to verify the signatures for gnupg source and binaries.  

I downloaded a copy of gnupg for my windows install & I would like to use my gnupg in my Ubuntu install and the gnupg key to verify that I downloaded something that has not been tampered with.  Once I verify this, I can be certain that I am getting the real gnupg.

---

### Post by nanotube on 2006-02-27
see this: [http://www.gnupg.org/(en)/download/integrity_check.html](http://www.gnupg.org/(en)/download/integrity_check.html)
and this: 
[http://www.gnupg.org/(en)/signature_key.html](http://www.gnupg.org/(en)/signature_key.html)

according to the keys posted on gnupg website, these are correct.

---

### Post by jchau on 2006-02-27
Thanks for checking for me.  I got my keys from the website too.  I was just afraid of a possible man in the middle.  But I guess if u get the same key from whereever you are, I assume they can't hijack both our connections & if they hijack the gnupg website, there would be news.  So I guees I can trust these keys.  Thanks again!

---

### Post by nanotube on 2006-02-28
no prob. never hurts to be careful :)

---

