---
title: "server kernel vs default ubuntu kernel"
date: 2009-07-24
forum: Server Platforms
---

### Post by pythonscript on 2009-07-24
I received a tip earlier about installing the server kernel 

```

sudo apt-get install linux-server linux-headers-server
```

so my 32-bit system will support all 4 gb of ram in my notebook. How will this affect my everyday usage, and will installing these packages either install a bunch of useless stuff I don't need (since my laptop isn't a server, I'm only in this for the added ram support) or cause any other problems with my other ubuntu apps? I'm aware of the complications with the video driver, but I know how to work around that. Thanks!

---

### Post by ibutho on 2009-07-24
The command just installs the server kernel (and required modules) and nothing else, so you do not need to worry about other stuff being installed.

---

### Post by pythonscript on 2009-07-24
Thank you. That's what I was hoping to hear.

---

### Post by cdenley on 2009-07-24
The server kernel does not depend on restricted modules last I checked. This means if you use the nvidia or fglrx video driver, a kernel update can cause X to stop working until you manually install the restricted modules for your new kernel.

**EDIT:** Nevermind. I just checked, and in 9.04 (and 8.10) restricted modules are a dependency of linux-server.

---

### Post by Cheesemill on 2009-07-24
More to the point, are you actually getting anywhere near using the 3GB of RAM that is currently recognised?
 
If the answer is no (it is in 90% of cases) then you're probably better of sticking with the standard kernel.

---

### Post by pythonscript on 2009-07-24
> **Cheesemill said:**
> More to the point, are you actually getting anywhere near using the 3GB of RAM that is currently recognised?

I operate quite a few virtual machines, so yes, I was quickly approaching that 3 gb limit.

---

