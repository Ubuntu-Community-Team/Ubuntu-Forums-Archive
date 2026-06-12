---
title: "Binding mysqld to localhost interface"
date: 2010-01-02
forum: Server Platforms
---

### Post by memilanuk on 2010-01-02
Hello,

I'm curious... anybody out there have any luck binding mysqld to the localhost or 127.0.0.1 interface?  Elsewhere it was suggested to me to try 

```

bind_address 127.0.0.1

```

or

```

skip_networking

```

in the config file to help in 'locking down' an XAMPP install so that mysqld isn't by default listening on the external interface.  Problem is... when I make said edits and restart mysqld... it starts and then exits.  

Any hints or suggestions would be welcome,

Monte

---

### Post by Vegan on 2010-01-02
MySQL is local host only until your configure it to be a stand-alone SQL server.

So do not worry about it.

---

### Post by memilanuk on 2010-01-02
Much appreciated.  I got the problems solved (line needed to be 'bind_address**=**127.0.0.1').  

In all fairness... it was actually XAMPP for Windows on a usb stick, where the default install has everything listening on the external interface if I'm not mistaken.  I'd taken some steps to reduce that exposure, and just wanted to lock it down a bit more.  I asked here because I figured it was more of a generic mysqld problem than a Windows/Ubuntu problem (which it was, just a syntax error in the config file).

Thanks,

Monte

---

### Post by Vegan on 2010-01-02
I was unaware you were on a USB stick, I use an old machine with a 500GB disk as my server. I use MySQL heavily on it.

---

