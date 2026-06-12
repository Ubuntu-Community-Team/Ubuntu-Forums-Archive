---
title: "Unable to create qcow2: Invalid image size specified!"
date: 2015-07-22
forum: Virtualisation
---

### Post by paul215 on 2015-07-22
Hello all,
I am trying to create a qcow2 using

 " # qemu-img create qcow2 windows.qcow2 8G " 

This commands results in this error :

" qemu-img: Invalid image size specified! You may use k, M, G or T suffixes for
  qemu-img: kilobytes, megabytes, gigabytes and terabytes"

I have tryed k,m,g,t upper and lower case all this the same result. Also tried different sizes. I have used this exact command before and it worked fine. This is a fresh install of ubuntu 12.04 LTS. 

Thanks!

---

### Post by TheFu on 2015-07-22
Try (corrected after the fact for later lurkers [Lars answer below is correct]):
```
$ sudo qemu-img create -f qcow2 windows.qcow2 8G
```

but I doubt you can load any recent Windows into just 8G.

---

### Post by paul215 on 2015-07-23
Thanks for the replay. I have run this with sudo as well as in root. Same result.

For now, its not a recent Windows.It is a ancient UN-secure XP. [-X 

I don't understand why this is happening. I have reinstalled qemu and all the bells and whistles associated with it. This just does not make any sense to me...

---

### Post by Lars Noodén on 2015-07-23
You're missing the -f in there for [qemu-img](http://manpages.ubuntu.com/manpages/trusty/en/man1/qemu-img.1.html)

```

qemu-img create **-f** qcow2 windows.qcow2 8G 

```

The -f is needed to tell it which image format to use.

---

### Post by TheFu on 2015-07-23
My first command created a RAW file - not what you want. Sorry.

This worked for me. See the output?
```
$ sudo qemu-img create -f qcow2  windows.qcow2 8G
Formatting 'windows.qcow2', fmt=qcow2 size=8589934592 encryption=off cluster_size=65536 lazy_refcounts=off
```

Took less than 1 sec.

Ah - I see Lars nailed the solution. Thanks Lars!

---

### Post by paul215 on 2015-07-23
wow thanks lars and thefu! I cant believe I missed that. I tryed so many different formats of the same command but apparently never tryed with -f. The error message threw me off completely.

---

