---
title: "Using CVS to obtain source code for W3C CSS Validator"
date: 2009-03-12
forum: Server Platforms
---

### Post by botfish on 2009-03-12
I would like to install the W3C CSS validator on my Ubuntu 8.04 server.

How do I download source from a CVS server? 

I am following the instructions at
[http://jigsaw.w3.org/css-validator/DOWNLOAD.html](http://jigsaw.w3.org/css-validator/DOWNLOAD.html)
but it skips very quickly over the CVS part

Thanks

---

### Post by JeppeM on 2009-03-12
Hey botfish,

you can do the following from the terminal:
```

sudo apt-get install cvs
CVSROOT=:pserver:anonymous@dev.w3.org:/sources/public cvs login

```
And then enter the password *anonymous* when asked. After that, you can do this:
```

CVSROOT=:pserver:anonymous@dev.w3.org:/sources/public cvs checkout src/

```
Which will make a dir in the directory you're in called 2002, and inside that you will find the directory css-validator which contain the code of the css validator.

good luck :)

---

### Post by botfish on 2009-03-13
Thanks JeppeM
That clears things up for me

---

