---
title: "Compiling systemd"
date: 2020-09-09
forum: Ubuntu Development Version
---

### Post by rafimoor on 2020-09-09
Hi,

I have hard time compiling some Ubuntu packages from source (see previous post about glibc).

I now try to compile systemd. On Ubunu 18.04 I've used apt source to get the source that is supposed to include Ubunu patches. After compilation, I replace  libsystemd-shared-237.so with the one I've compiled. Programs that are linked with this shared object complain about reference to undefined symbol sd_bus_enqueue_for_read. using readelf I can see that the original library has this symbol but the new one doesn't. I've tried to apply CVE-2020-1712-2.patch but then the compilation fails on missing function bus_message_ref_queued(). This function is included in systemd version 246 but not in 237 which is the version on Ubuntu 18.04.

How can I compile systemd so that I get files identical to those of Ubuntu 18.04?

Thanks
Rafi

---

### Post by mc4man on 2020-09-12
This sub-forum is for 20.10

---

