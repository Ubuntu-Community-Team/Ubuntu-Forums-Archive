---
title: "SecureBoot"
date: 2023-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2023-09-29
Can someone explain why Kubuntu will load on my PC with SecureBoot on, but other distributions will not.

---

### Post by #&amp;thj^% on 2023-09-29
Easy the better OS of course :P
Ubuntu and Microsoft work closely with each other.
BTW Suse does as well.

---

### Post by iamjiwjr on 2023-09-30
While I don't know about Microsoft, OpenSUSE will not boot with Secure Boot on my Dell Precision desktop (Intel and AMD), but Ubuntu, Debian, Kubuntu, and Fedora boot fine with Secure Boot. OpenSUSE has had a broken SHIM for 6 months, but I don't know about other distros vs Kubuntu Secure Boot. Hardware differences?

---

### Post by #&amp;thj^% on 2023-09-30
All my lenovo's AMD Intel all work with openSUSE SecureBoot 

[https://pulse.microsoft.com/en/transform-en/na/fa2-canonical-a-partnership-that-delivers-the-best-and-most-secure-open-source-for-customers/](https://pulse.microsoft.com/en/transform-en/na/fa2-canonical-a-partnership-that-delivers-the-best-and-most-secure-open-source-for-customers/)

---

### Post by TheFu on 2023-09-30
secureboot is about signed boot code.  There is a nominal charge ($100?) to have a key signed, so many of the small players don't bother.  The different codes used are installed into the BIOS, usually by the vendor getting MSFT's validation cert stuffed into the BIOS firmware.  Some firmware allows people to manage these keys, but I get the feeling it isn't well tested for any besides MSFT's keys.

You can google to find more specific details about secureboot and keys.

Canonical definitely worked with MSFT to implement it.  Additionally, the Linux Foundation Workstation Security recommendations have recommended using SecureBoot since at least 2017, perhaps longer.

Basically, if a distro can't be bothered to pay MSFT $100, that's on them.  One of the multi-ISO boot tools I like, Ventoy, has struggled to support this too, which is why don't think it really as trivial to get and install signed keys as we all may think. I've never done it, that's certain.  I know a security guy who was playing around with the ability to self-sign boot code and was flashing the BIOS in his test rig to make it work.  He bricked the motherboard.

---

