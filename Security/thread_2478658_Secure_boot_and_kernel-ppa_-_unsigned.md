---
title: "Secure boot and kernel-ppa - unsigned?"
date: 2022-09-01
forum: Security
---

### Post by luckyknight on 2022-09-01
Hello,

I've tried upgrading my included kernel in 22.04 with a newer one from:

[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

Unfortunately this does not work as it just throws an error on boot:

[COLOR=#24292F][FONT=-apple-system]"error: bad shim signature.
error: you need to load the kernel first.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Press any key to continue..."

[/FONT][/COLOR]
Could the kernels off this repo be signed so they can be used with secure boot?

I need a newer kernel to support hardware found in my ASUS G14 2022 model, specifically the keyboard back light.

---

