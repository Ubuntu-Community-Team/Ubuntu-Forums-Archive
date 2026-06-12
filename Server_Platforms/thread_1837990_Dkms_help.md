---
title: "Dkms help"
date: 2011-09-02
forum: Server Platforms
---

### Post by dmovad on 2011-09-02
I'm trying to add a RocketRaid 644 to a system running 10.04.3-64-Server LTS and have been trying to follow:

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

When I get to the point of building the module I get the following ending with an error:

[COLOR="Red"]root@server:/home/dovad/rr64x-linux-src-v1.0# dkms build -m rr64xla -v 1.0

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-10-server -C product/rr64x/linux/ KERNELDIR=/lib/modules/2.6.38-10-server/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.38-10-server (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rr64xla/1.0/build/ for more information.
0
0
ERROR: binary package for rr64xla: 1.0 not fount[/COLOR]

I'm pulling my hair out (I have little to spare) and would appreciate some help.

Thanks...
Dave

---

### Post by Entilza on 2011-09-04
Can you show what kernel you are using?

uname -r

make sure you are pointing it to the correct kernel source.

---

### Post by dmovad on 2011-09-05
I updated my kernel to:

2.6.38-10-server

I had read that the default kernel that I had would not work.

thanks for taking a look at this for me.

Dave

---

### Post by Entilza on 2011-09-05
I've built a dkms for another raid controller, you just have to make sure it's all pointing to the right locations... Hmm

Did you check the make.log ?

You can also try moving it to the kernel source and rebuild the entire kernel with that as a module, much more work but if you can't get this working.

---

