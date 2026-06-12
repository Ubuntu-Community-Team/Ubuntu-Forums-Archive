---
title: "Can't run VirtualBox"
date: 2011-04-25
forum: Virtualisation
---

### Post by MickSulley on 2011-04-25
I cannot get VirtualBox to run on my laptop.  I am running Ubuntu 10.10 64 bit, VB seems to install OK but when I run it I get an error
> VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libGL.so.1: cannot open shared object file: No such file or directory

I have tried VB 4 and VB 3.2 and get the same problem with both.  I have had VB running previously but since I did a fresh install of Ubuntu I cannot get it to work.  The file virtualbox/VirtualBox.so does exist, I have tried changing permissions but then I just get a different error 
> 
VirtualBox: supR3HardenedVerifyFileInternal: Cannot trust the file "/usr/lib/virtualbox/VirtualBox.so": group and/or other writable (st_mode=0100764)
Any ideas?
Thanks
Mick

---

### Post by CharlesA on 2011-04-25
Permission problem.

The permissions should be this:

```
charles@Thor:~$ ls -l /usr/lib/virtualbox/VirtualBox.so
-rw-r--r-- 1 root root 5583120 2011-04-21 05:06 /usr/lib/virtualbox/VirtualBox.so

```

Try running this:

```
sudo chmod 644 /usr/lib/virtualbox/VirtualBox.so
```

---

### Post by MickSulley on 2011-04-25
Fixed it!!

It couldn't find libGL.so.1 so I found it in a different directory so I copied it to /usr/lib/virtualbox/ and now it works!!

---

### Post by CharlesA on 2011-04-25
Glad you got it working. :)

---

### Post by CharlesA on 2011-04-26
> **naikvarda said:**
> What is the virtulabox? please give  me some basic idea about that.
It is software that does virtualization.

See [here]("http://www.virtualbox.org/").

---

### Post by SelbyRowleyCannon on 2012-08-07
Does anyone know how to fix this error on 32-bit?:guitar:

---

