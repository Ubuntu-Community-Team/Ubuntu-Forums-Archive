---
title: "Libpam_mysql"
date: 2012-07-24
forum: Security
---

### Post by fluo75 on 2012-07-24
Hi all, :)

Not sure if this is the right place to ask this question...
I have noticed that the library [libpam_mysql]("http://pam-mysql.sourceforge.net/") does not seems to be supported since 2006.
At the moment, we are using a release candidate 1 of 2006 !! :confused:

Shouldn't this library not be used anymore and even not be available anymore in the Ubuntu packet management?

Thanks in advance,

David

---

### Post by raja.genupula on 2012-07-24
No fluo7 , just now i have installed in my pc of Ubuntu 12.04 

```
sudo aptitude install  libpam-mysql 
```

---

### Post by fluo75 on 2012-07-24
> **raja.genupula said:**
> No fluo7 , just now i have installed in my pc of Ubuntu 12.04 

```
sudo aptitude install  libpam-mysql 
```

Thanks for your reply.
Sorry, I was probably not clear.

I know it is possible to install it.
My problem is that this is an old, unmaintained library since 2006.
There is no correction of any bug, no response to support request, no patches since 2006.
I believe one of my server has been hacked through this library. (not entirely sure)

Please visit the website, it's scary: [http://pam-mysql.sourceforge.net/](http://pam-mysql.sourceforge.net/)
You will notice that the majority of the BUG reports are guys using the forum to share some porn links... :):)

David
PS: raja.genupula: If you don't need it, I would really recommend you delete this library from your system.

---

