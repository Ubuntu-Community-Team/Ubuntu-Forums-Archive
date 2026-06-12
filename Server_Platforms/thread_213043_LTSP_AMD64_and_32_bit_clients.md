---
title: "LTSP AMD64 and 32 bit clients"
date: 2006-07-10
forum: Server Platforms
---

### Post by cesera on 2006-07-10
I have a kubuntu-AMD64 machine up and running and now would like to runLTSP with 32 bit thin clients, does anyone know if that is going towork out of the box, or do I have to do anything special to bridge the64/32 bit divide?

---

### Post by Yagisan on 2006-07-11
I added support for it a long time ago :) but you'll need to specify when you set up the ltsp chroot that you want i386 clients,

Just add --arch i386 to your ltsp-build-client command.

---

### Post by cesera on 2006-07-11
> **Yagisan said:**
> Just add --arch i386 to your ltsp-build-client command.
Thank you very much, I missed that in the man page. Just to double check, does that mean I can add support for multiple client architectures by running the ltsp-build-client command more than once?

---

### Post by Yagisan on 2006-07-13
You mightbe able too, but I did not have that in mind when I wrote the patch, nor have I ever tested it (to much work for no apparent gain). I run a 64bit server, and all clients are 32bit. Makes no difference to the client, as all it does is take keypresses, mouse movements and repaint the screen - basically a 233Mhz box can do that with cpu to spare.

---

### Post by cesera on 2006-07-14
I have no intention of using amd64 clients, but I was just interested if that would work. Thank you very much for your help.

---

### Post by Yagisan on 2006-07-14
You are quite welcome :)

---

