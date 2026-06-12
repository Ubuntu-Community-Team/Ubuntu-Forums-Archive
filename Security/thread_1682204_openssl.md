---
title: "openssl"
date: 2011-02-05
forum: Security
---

### Post by num on 2011-02-05
Hello,

I am trying generate keys and certificates with openssl but i cannot get it to work properly.

i run it using superuser by doing sudo su first then running openssl but it gives me this error:

```
e is 65537 (0x10001)
```

i researched this issue on google and found the possible reason this happens is that i do not own the rand file, but i am new to ubuntu and don't know how to properly do this. can someone please advise?

---

### Post by num on 2011-02-06
please help?

---

### Post by anomie on 2011-02-08
What is the exact command you're running (which generates that error)?

---

### Post by num on 2011-02-09
> **anomie said:**
> What is the exact command you're running (which generates that error)?

openssl genrsa -out key.pem 2048

same goes when i try having that key encrypted.

---

### Post by anomie on 2011-02-09
So, per your own research (which I'm not necessarily vouching for :)), what does this show you: 

```
$ ls -l /dev/*rand*
```

(And for more complete information on this thread, which Ubuntu version is this?)

---

### Post by num on 2011-02-09
> **anomie said:**
> So, per your own research (which I'm not necessarily vouching for :)), what does this show you: 

```
$ ls -l /dev/*rand*
```

(And for more complete information on this thread, which Ubuntu version is this?)

Well I am not sure, I am new that's what my research got me, perhaps I am wrong?

Ubuntu 10.10

---

### Post by num on 2011-02-10
This is the documentation I found:

[http://www.openssl.org/support/faq.cgi#USER1](http://www.openssl.org/support/faq.cgi#USER1)

that takls about this issue, how can I fix it properly in Ubuntu or is Ubuntu unfixable?

---

### Post by anomie on 2011-02-10
A few things: 
[list=1]
[*] When you post a request for help, please include (from the beginning of the thread) exactly what you have tried, and the *exact* error message you're seeing. Do not leave parts of it out. 
[*] Let's see the output from the command I mentioned. Mainly just curious at this point. 
[*] Check out this thread: [http://www.mail-archive.com/openssl-users@openssl.org/msg51334.html](http://www.mail-archive.com/openssl-users@openssl.org/msg51334.html) It meanders a bit, but may shed light and/or put your mind at ease. 
[/list]

---

### Post by num on 2011-02-10
> **anomie said:**
> A few things: 
[list=1]
[*] When you post a request for help, please include (from the beginning of the thread) exactly what you have tried, and the *exact* error message you're seeing. Do not leave parts of it out. 
[*] Let's see the output from the command I mentioned. Mainly just curious at this point. 
[*] Check out this thread: [http://www.mail-archive.com/openssl-users@openssl.org/msg51334.html](http://www.mail-archive.com/openssl-users@openssl.org/msg51334.html) It meanders a bit, but may shed light and/or put your mind at ease. 
[/list]

so ignore the error? am i correct on understanding that?

---

