---
title: "Missing library when trying to run Truecrypt"
date: 2008-08-05
forum: Server Platforms
---

### Post by matt_b on 2008-08-05
Hi,

I am running Hardy Server x86, and have downloaded & installed truecrypt using the Ubuntu .deb from truecrypt.org, but whenever I try to run it, I get the message:

```
error while loading shared libraries: libSM.so.6: cannot open shared object file: No such file or directory
```

I think this error appears because the library comes with X, and I have not installed X on this machine. Can someone tell me what package I need to install to get this library? I have tried libx11-dev but no dice.

Thanks
Matt

---

### Post by hyper_ch on 2008-08-05
(1) ```

sudo apt-get install apt-file

```

(2) ```

sudo apt-file update

```

(3) ```

apt-file search libSM.so.6

```

---

### Post by matt_b on 2008-08-05
Excellent, thanks!

The package was libsm6, quick apt-get, job done!

---

### Post by windependence on 2008-08-05
Thanks hyper_ch. Didn't know about that one. :)

-Tim

---

