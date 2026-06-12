---
title: "linux-headers-server  package gone from 14.04?"
date: 2014-08-16
forum: Server Platforms
---

### Post by MakOwner on 2014-08-16
Using the server install image from 12.04 LTS I always ended up with the linux-headers-server package installed.

New installs of 14.04.1 LTS don't seem to include this package.  

Am i just missing a part of the install or has that package been deprecated?

---

### Post by TheFu on 2014-08-17
linux-headers-generic-lts-raring and linux-headers-generic are the names here.

I only installed the linux-headers-generic - don't know why the other was pulled in.  Check on a KVM host with very little other software installed. No GUI on that machine either.

---

### Post by ibjsb4 on 2014-08-17
Its there

[http://packages.ubuntu.com/trusty/linux-headers-server](http://packages.ubuntu.com/trusty/linux-headers-server)

I have never used it, but I would say just install it if you want it.  I wouldn't combine it with the other header packages (the above post).

---

### Post by varunendra on 2014-08-17
As far as I know, the linux-image-generic and linux-image-server are the same now. That is - both the desktop and server kernels are same, since 12.04 if I remember correctly. Any kernel/header package that contains the word "server" is only there to satisfy packages that may still expect it.

The description of the package linux-headers-server says -
> Depends: linux-headers-generic (= 3.13.0.34.40)
....
Description: Transitional package.
 This package will always depend on linux-headers-generic.
Which means exactly what I said above. There is a nice, descriptive wiki page about it, I just can't find its link right now.

---

