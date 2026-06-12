---
title: "Help with installing packages via the console"
date: 2005-12-26
forum: Server Platforms
---

### Post by CompiledMonkey on 2005-12-26
I thought I heard that Ubuntu uses APT-GET for package management.  Can anyone help me figure out how I can install GCC and an assembler via the console (over SSH)?

---

### Post by kabus on 2005-12-26
To install a package :
```
sudo apt-get install *packagename*
```

To search for gcc packages :
```
apt-cache search gcc
```

To show information about a package :
```
apt-cache show *packagename*
```

I'm not sure which packages you need to install, but you'll probably need build-essential.

---

### Post by CompiledMonkey on 2005-12-26
Perfect, thank you.

---

### Post by az on 2005-12-26
sudo apt-get install build-essential


if you need to compile stuff for the kernel, you need gcc-3.4

sudo apt-get install gcc-3.4

You need a differnet compiler because the kernel would not build with gcc-4.0 at release time.

You need to enable repositores

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Via ssh, you can just edit /etc/apt/sources.list and uncomment the appropriate lines.

EDIT :  I am too slow....

---

### Post by CompiledMonkey on 2005-12-26
I appreciate the replies.  I was able to get gcc4 and nasm installed.  Thanks again!

---

