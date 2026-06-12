---
title: "wouldn't the snaps become a target for virus authors?"
date: 2018-09-05
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-09-05
Correct me if I'm wrong, I've heard that snaps is being considered a universal installer package for all Linux systems, so instead of having multiple installer type files, snaps is suppose to replace installer packages like .deb, .rpm, .tar, etc.

As far as I can tell, snaps is similar to exe files, as in, the snaps package contains everything you need to install and run the program you are installing, the application itself and it's dependencies are all included in one package, making it very easy to install applications on Linux systems.

Wouldn't this be a target for virus and malware authors wanting to infect Linux?

Based on what I've heard and read, one of the reasons why Linux isn't as vulnerable to malware as Windows is because Linux has different installer types while Windows only has one, the exe file, so if you want to infect Debian-like systems like Ubuntu, create a .deb virus, however, your .deb virus won't be able to infect Fedora, because they use .rpm installer.

Now with snaps, if a virus author creates a virus snaps package, wouldn't this virus be capable of infecting multiple distros?

---

### Post by pauljw on 2018-09-05
I could be wrong, but I was under the impression that snaps are sandboxed.  In that case, the virus just gets to play with itself, no?

---

### Post by #&amp;thj^% on 2018-09-05
"Without providing custom flags at installation, snaps run confined under a restrictive security sandbox.
The security policies and store policies work together to allow developers to quickly update their applications and to provide safety to end users."
[https://forum.snapcraft.io/t/security-policy-and-sandboxing/554](https://forum.snapcraft.io/t/security-policy-and-sandboxing/554)

---

### Post by pauljw on 2018-09-05
> **1fallen said:**
> "Without providing custom flags at installation, snaps run confined under a restrictive security sandbox.
The security policies and store policies work together to allow developers to quickly update their applications and to provide safety to end users."
[https://forum.snapcraft.io/t/security-policy-and-sandboxing/554](https://forum.snapcraft.io/t/security-policy-and-sandboxing/554)

Thanks! :)

---

