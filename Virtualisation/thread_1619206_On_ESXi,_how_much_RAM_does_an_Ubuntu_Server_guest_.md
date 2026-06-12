---
title: "On ESXi, how much RAM does an Ubuntu Server guest need?"
date: 2010-11-11
forum: Virtualisation
---

### Post by samosamo on 2010-11-11
Ubuntu 10.04 Server w/ virtual kernel.  How much RAM?

---

### Post by CharlesA on 2010-11-11
The memory usage of a normal install of server vs a virtual install of server is negligible. I don't have one of those installed atm, but when I did, a clean install used around 40-50MB of RAM IIRC. Could be wrong ofc, since it's been a while.

[https://help.ubuntu.com/community/ServerFaq#What%20are%20the%20differences%20between%20the%20server%20and%20virtual%20kernels?](https://help.ubuntu.com/community/ServerFaq#What%20are%20the%20differences%20between%20the%20server%20and%20virtual%20kernels?)

EDIT: Checked one of my normal installs that is only running SSH and this is what it says:

```
charles@luna:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999        216        782          0         26        128
-/+ buffers/cache:         [COLOR="Blue"]62[/COLOR]        937
Swap:         1101          0       1101

```

---

### Post by samosamo on 2010-11-12
Is there any documentation on this?  So you have 1024MB for your guests?  python-vm-builder by default does 128MB, and I have to wonder why it does.  Once you install most (or any) applications, it's going to run out of RAM and start swapping real fast.

---

### Post by CharlesA on 2010-11-12
I'd say 128MB of RAM is too little. Ubuntu would like 256MB of RAM at least.

As for memory usage, I don't know if there is any documentation on it, but I checked what my server is using on bare metal and it's not all that much:

```
charles@thor:~/scripts$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       4471       1509          0        112       3847
-/+ buffers/cache:        511       5469
Swap:        12401          0      12401

```

---

### Post by dcstar on 2010-11-13
> **CharlesA said:**
> I'd say 128MB of RAM is too little. Ubuntu would like 256MB of RAM at least.
.........

A server will "need" as much RAM as the requirements of the services it is supposed to run.

If you just want a server to boot up and do nothing (that is, be basically useless) then the amount of RAM needed for that will be much less than a server providing 1,000 web pages requests a second with 500 e-mail users also hitting it.

The **minimum** RAM (which we seem to be **guessing** that the OP is asking about) is whatever is in the requirements for each release:

[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

---

### Post by CharlesA on 2010-11-13
> **dcstar said:**
> A server will "need" as much RAM as the requirements of the services it is supposed to run.

If you just want a server to boot up and do nothing (that is, be basically useless) then the amount of RAM needed for that will be much less than a server providing 1,000 web pages requests a second with 500 e-mail users also hitting it.

Yep, that's true. It's all relative to what the server is going to do. There's no real point in trying to "min/max" VM configuration imo, most of the VMs I'm running have around 512MB of RAM allocated to them, some have 1 GB. It all depends on what they'll be used for.

---

