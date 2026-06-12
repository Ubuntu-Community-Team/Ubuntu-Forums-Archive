---
title: "Apache Server: 32 or 64?"
date: 2011-12-02
forum: Server Platforms
---

### Post by nickos on 2011-12-02
Apache2 web server using ubuntu 10.10.
32 or 64 bit?

---

### Post by volkswagner on 2011-12-03
Run the following command to find out if you are running i686 or 64bit.

```
uname -a
```

---

### Post by newbie-user on 2011-12-03
The question is kinda vague.  If you're asking whether to use 32-bit or 64-bit, I'd say it doesn't really matter.  I've used both for apache servers and they work the same.

---

### Post by stmiller on 2011-12-03
yes

---

### Post by hawkmage on 2011-12-03
The default package that you install with apt-get matches the OS so if you are running 64 bit Ubuntu then you will be running 64 bit Apache.  

So are you asking if you should run the 32 or 64 bit Ubuntu?  OR are you planning on not using the default package?

---

### Post by insane_alien on 2011-12-04
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

would indicate that 64-bit will give you greater performance

---

