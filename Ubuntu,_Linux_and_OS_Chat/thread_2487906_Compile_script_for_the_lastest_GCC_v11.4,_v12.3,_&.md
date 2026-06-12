---
title: "Compile script for the lastest GCC v11.4, v12.3, &amp; v13.1 on Jammy"
date: 2023-06-17
forum: Ubuntu, Linux and OS Chat
---

### Post by slyfox1186 on 2023-06-17
I couldn't take waiting for gcc-13 on Jammy so I went all out and made a compile script.

It compiles GCC versions 11.4.0, 12.3.0, & 13.2.0.

Add or remove anything you desire. There is a "debug" variable at the top of the script that you can toggle if issues arise.

It seems to work pretty good for me.

I thought someone might want to give it a try and report back.

=)

Fixed a build issue some were having for zstd, zlib, and bison libs.

[https://github.com/slyfox1186/script-repo/blob/main/Bash/Installer%20Scripts/GNU%20Software/build-gcc](https://github.com/slyfox1186/script-repo/blob/main/Bash/Installer%20Scripts/GNU%20Software/build-gcc)

```
bash <(curl -sSL https://gcc.optimizethis.net)
```

---

