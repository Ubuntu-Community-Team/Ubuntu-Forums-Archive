---
title: "New root kit?"
date: 2016-09-06
forum: Security
---

### Post by Autodave on 2016-09-06
Just reading on PC World about Umbreon: a new root kit that can affect Linux. Is this something to worry about or not? If worth worrying about, what can be done to protect against it?

---

### Post by Frogs Hair on 2016-09-06
Moved to *Security.*

---

### Post by #&amp;thj^% on 2016-09-07
> **Autodave said:**
> Just reading on PC World about Umbreon: a new root kit that can affect Linux. Is this something to worry about or not? If worth worrying about, what can be done to protect against it?

This could be very worrisome (for some)...no known way to prevent it yet outside of staying fully updated. (And that may not be enough) And it has to be installed.(So Heads up on what you install)
More Information from Trend Micro: [http://blog.trendmicro.com/trendlabs-security-intelligence/pokemon-themed-umbreon-linux-rootkit-hits-x86-arm-systems/](http://blog.trendmicro.com/trendlabs-security-intelligence/pokemon-themed-umbreon-linux-rootkit-hits-x86-arm-systems/)
Also in that link above is a how-to to remove it. (Not for the faint of heart)
This has been classified as a *"ring 3 rootkit">>>>*meaning that it runs from user mode and doesn't need kernel privileges. Despite this apparent limitation, it is quite capable of hiding itself and persisting on the system.[I]
> [It targets Linux-based systems on the x86, x86-64 and ARM architectures, including many embedded devices such as routers.]

[/I]Ring 3 Usermode rootkits
Ring 0 Kernelmode rootkits
Ring -1 Hypervisor rootkits (Bluepill)
Ring -2 SMM rootkits

---

### Post by HermanAB on 2016-09-07
Well, I have not been troubled by a rootkit in more than ten years, so the risk is probably very small, but one has to be ever vigilant.

---

### Post by miker_alpha on 2016-09-12
> **Autodave said:**
> Just reading on PC World about Umbreon: a new root kit that can affect Linux. Is this something to worry about or not? If worth worrying about, what can be done to protect against it?

You could test for and remove following instructions on:
[http://blog.trendmicro.com/trendlabs-security-intelligence/pokemon-themed-umbreon-linux-rootkit-hits-x86-arm-systems/](http://blog.trendmicro.com/trendlabs-security-intelligence/pokemon-themed-umbreon-linux-rootkit-hits-x86-arm-systems/)
(mind the wrap)
As for myself: I am too scared to get involved, it seems dangerous.

---

