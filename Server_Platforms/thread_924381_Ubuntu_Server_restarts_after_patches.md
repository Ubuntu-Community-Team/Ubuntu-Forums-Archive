---
title: "Ubuntu Server restarts after patches"
date: 2008-09-19
forum: Server Platforms
---

### Post by Aeonsies on 2008-09-19
Greetings everyone,

I've been a Ubuntu user since 6.06 and have loved every minute of it.  Recently I've expanded my experience with Ubuntu and create a Ubuntu Server.  

I was wondering if anyone knew why it seems most of the patches for Ubuntu Server lately require a restart of the system?

I was rather under the impression from all my reading of Linux that the system hardly ever needs a reboot, and yet it seems like every patch lately requires just that.

A penny for for your thoughts?  Anyone?

Thanks,

---

### Post by linuxone on 2008-09-19
Hi,

> **Aeonsies said:**
> I was wondering if anyone knew why it seems most of the patches for Ubuntu Server lately require a restart of the system

a complete reboot is only required if a new kernel or a new libc was installed.

Having X installed a restart of the X-Server may be necessary when updating some X or Window manager specific libraries. X-Server restart - not a complete reboot.
But of course a Server machine does not require and should not have installed X, so this point shouldn't happen.

Thomas

---

