---
title: "Kernal compile : What packages do I need to install"
date: 2008-05-12
forum: Server Platforms
---

### Post by phillhs on 2008-05-12
Hi,

I'm trying to set up a cluster based on Ubuntu server, and have to be able to compile a non-standard kernel (We're using Mosix, so it even has to be a perticular version and not an ubuntu one :( ).

However the default install of Hardy server, doesn't even install gcc :( So what packages do I need to install to allow me to do this.

Cheers.

Phill.

---

### Post by hermes0710 on 2008-05-12
Hi, try installing "build-essential" ```
sudo apt-get install build-essential
```

---

### Post by phillhs on 2008-05-13
> **hermes0710 said:**
> Hi, try installing "build-essential" ```
sudo apt-get install build-essential
```

Cheers, that got me almost there, apparently you also need libncurses5-dev too.

Cheers.

Phill.

---

### Post by hermes0710 on 2008-05-13
Yeap, you're right, my bad, i thought it would be installed through the build-essential

---

### Post by ajt on 2009-01-12
Hello,

I've started a new discussion, to try and bring together threads in different forums about Ubuntu clustering at:

[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

    Tony.

---

