---
title: "LTSP and Kubuntu"
date: 2006-01-27
forum: Server Platforms
---

### Post by Divan Santana on 2006-01-27
Hello Everybody!

I am setting up a Kubuntu Server with/for LTSP and Thin Clients.

Question I have is I would like to install the MueKow version of LTSP from the repositories. Does anyone know the differences, advantages and disadvantages of MueKow vs Normal.

Another question I was wondering, does most of the processing power come from the server or the clientand what is the recomended server spec?

Any answers or feedback would be appreciated!

Thanks

---

### Post by KermitJr on 2006-02-26
I can't help with the MueKow question, but almost all processing power depends on the server for a true thin client.

I have clients that are 486/66Mhz and they run seemingly as fast as the server.

There are fat client solutions that offload some of the processing power to the client, but I think setup is easier with PXE or etherboot,unplugging the hdd and cdrom and running with just a mobo, psu and eth0.

KJ

---

