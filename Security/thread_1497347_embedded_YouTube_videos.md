---
title: "embedded YouTube videos"
date: 2010-05-30
forum: Security
---

### Post by sm4sh1t on 2010-05-30
i know people use youtube to spread there viruses etc, but would this also effect ubuntu? or is it only windows?

---

### Post by OpSecShellshock on 2010-05-30
First, as often as not, those are fake YouTube pages designed to trick users into loading something else. The real site will take stuff down if it's reported as serving malware.

The actual answer to you question, though, is both. Flash was made for the purpose of being cross-platform. As such, Flash exploits themselves will affect the vulnerable versions on all platforms. The reason I say both is because on Linux it's most likely to simply cause the application to crash, whereas on other systems it would be followed by further code execution or the delivery of a second-stage payload. That payload will almost certainly be written for Windows.

---

### Post by sm4sh1t on 2010-05-30
> **OpSecShellshock said:**
> First, as often as not, those are fake YouTube pages designed to trick users into loading something else. The real site will take stuff down if it's reported as serving malware.

The actual answer to you question, though, is both. Flash was made for the purpose of being cross-platform. As such, Flash exploits themselves will affect the vulnerable versions on all platforms. The reason I say both is because on Linux it's most likely to simply cause the application to crash, whereas on other systems it would be followed by further code execution or the delivery of a second-stage payload. That payload will almost certainly be written for Windows.

thank you for the info :)

---

