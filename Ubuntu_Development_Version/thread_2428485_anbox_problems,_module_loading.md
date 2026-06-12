---
title: "anbox problems, module loading"
date: 2019-10-04
forum: Ubuntu Development Version
---

### Post by Vasu_Muppalla on 2019-10-04
Installed anbox using apt - from the official ubuntu repos.
It wasn't starting because it needed modules ashmem_linux.ko  and binder_linux.ko.
Both these modules are compiled into the kernel not installed via dkms. They came with the kernel 5.3.
I am able to insert binder_linux with modprobe but

modprobe -v ashmem_linux

returns

insmod /lib/modules/5.3.0-13-generic/kernel/drivers/staging/android/ashmem_linux.ko 
modprobe: ERROR: could not insert 'ashmem_linux': Operation not permitted

as root.

---

