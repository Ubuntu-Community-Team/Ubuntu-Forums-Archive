---
title: "Resources in XEN vs. OpenVZ"
date: 2009-01-31
forum: Virtualisation
---

### Post by narcisgarcia on 2009-01-31
I've been reading about different virtualization software, and to setup a server I'm focusing between two solucions: XEN and OpenVZ. VServer seems to be a discontinued project.

About the performance point, I understood that XEN separates host kernel from guest kernels, and also separates free reserved memory for guests.
OpenVZ makes run on 1 kernel for everybody, and makes possible to share free memory for being used by any guest.
XEN project seems to be an IBM friend, and OpenVZ/Virtuozzo is transparently supported by Parallel inc. Both are GPL licensed.

I don't need different kernels, and I need in a scenario with 1GB of RAM and 4 guests using 100MB, any of the guests can use 500MB when necessary, for example.

The important questions for me are:
- Can I make overbooking with free RAM with XEN software in Ubuntu?
- If so, how to do it?

---

