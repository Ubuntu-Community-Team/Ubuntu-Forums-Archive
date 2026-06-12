---
title: "encrypt /home partition in place"
date: 2008-07-17
forum: Security
---

### Post by reeseslover531 on 2008-07-17
hello.  So I have my computer set up to have a /home partition and a / partition.  I want to encrypt my /home partition, but my system is already installed and all and I don't want to have to re install.  How can I encrypt my /home partition without having to move data around?  or is this even possible at all?

thanks!

---

### Post by hyper_ch on 2008-07-18
you can't

---

### Post by Biochem on 2008-07-18
You could try encfs ( [http://www.gatorlug.org/node/123](http://www.gatorlug.org/node/123) )

Better try it with a fake user or better a virtual system) before doing anything that would results in data loss. 

Have your backup nearby.

---

### Post by bp1509 on 2008-07-18
you have to move data around, point blank.

you can create a partition for /home, use Luks to encrypt it, copy your data somewhere you'll be able to access it, get crypttab and fstab setup so your newly encrypted home partition mounts at boot, copy your home back to the newly created partition, reboot and see how it goes.

---

### Post by dendrobates on 2008-07-19
In intrepid, we have added support for easy encrypted private directories.  It won't be default, but it will be very simple to configure and use.

dendrobates

---

### Post by hyper_ch on 2008-07-19
how secure will that feature be in intrepid? I think you need to encrypt more like swap, /tmp folder, ......

---

### Post by vermoos on 2008-07-21
tiny problem with encfs: sudo updatedb doesn't hash the encrypted directory!

even if its mounted, the files in the encrypted directory aren't picked up by updatedb

ghaaaargh! what's the point of having an encrypted partition if you can't find anything that's in it?

anyone know of a means of getting around this?

Mitch

---

