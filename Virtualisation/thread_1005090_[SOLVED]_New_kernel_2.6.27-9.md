---
title: "[SOLVED] New kernel 2.6.27-9"
date: 2008-12-07
forum: Virtualisation
---

### Post by quikone8 on 2008-12-07
Does anyone know how to overcome this?

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes]

---

### Post by gtdaqua on 2008-12-08
Just answer yes.

But before you do, ensure you have linux-headers for your running kernel. You also need build-essential package. You can install it by:

```

sudo apt-get install linux-headers-`uname -r` build-essential

```

---

### Post by delgurth on 2008-12-08
And it can be that you need to patch the config script, see my post in the vsock warning thread:

[http://ubuntuforums.org/showpost.php?p=6267637&postcount=17](http://ubuntuforums.org/showpost.php?p=6267637&postcount=17)

---

### Post by gtdaqua on 2008-12-08
> **delgurth said:**
> And it can be that you need to patch the config script, see my post in the vsock warning thread:

[http://ubuntuforums.org/showpost.php?p=6267637&postcount=17](http://ubuntuforums.org/showpost.php?p=6267637&postcount=17)

Patch is no more required for VMware Server 2.0 and 1.07 (last tested). The first post specifically talks about pre-compiled modules that are not present which is absolutely normal.

---

### Post by delgurth on 2008-12-08
> **gtdaqua said:**
> Patch is no more required for VMware Server 2.0 and 1.07 (last tested). The first post specifically talks about pre-compiled modules that are not present which is absolutely normal.

I know the first post talks about the pre-compiled modules, but in case someone needs to build the modules him/herself it could be useful to know about the vsock problem... And you say that patching is no longer needed... but the latest version is still "Version 2.0.0 | 122956 - 10/29/08" and that one had the vsock problem in my case. But as always, YMMV.

---

### Post by quikone8 on 2008-12-08
> **gtdaqua said:**
> Just answer yes.

But before you do, ensure you have linux-headers for your running kernel. You also need build-essential package. You can install it by:

```

sudo apt-get install linux-headers-`uname -r` build-essential

```

How do I determine if I do have the linux headers?

Also, do I type the command exactly as you did or do I replace 'uname -r' with something else?

---

### Post by delgurth on 2008-12-08
> **quikone8 said:**
> How do I determine if I do have the linux headers?

Also, do I type the command exactly as you did or do I replace 'uname -r' with something else?

To see if you have installed it you do:

```
dpkg -l linux-headers-`uname -r`
```

And it should return something like:

```
ii  linux-headers- 2.6.27-9.19    Linux kernel headers for version 2.6.27 on x
```

Where the ii stands for installed. If it doesn't return anything, you don't have the headers installed. 

Another way to find out if you have installed it, is just running the apt-get install, since running it while you have installed the headers already won't cause any problems.

And you don't have to replace the `uname -r` with anything, the idea behind that is that it finds out what version of the linux kernel you are using, so you don't have to look that up first and add it in the command. Please note that it's not a single quote but a backtick.

---

