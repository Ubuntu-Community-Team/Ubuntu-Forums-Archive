---
title: "SSH access using PuTTY from Windows: lost connections"
date: 2006-04-01
forum: Server Platforms
---

### Post by allenlux on 2006-04-01
I'm using PuTTY from Windows XP to access a new Ubuntu 5.10 server setup, using SSH (with password).

I can login with no problems, but I'm seeing apparently random lost connections after anything from 30 seconds to 5 minutes or more, with a message at the PuTTY end saying "network error: software caused connection abort".

From the same PC I can access my main server (a Gentoo setup which has been running for several years) with no problems; I'd never seen this error message until I connected to the Ubuntu server box.

I've read the PuTTY docs and considered whether there might be a network hardware problem, but I swapped the ethernet cable and switch without seeing any change. I also recompiled the kernel (the Gentoo user's reflex) but this made no difference either.

What else should I look at?

---

### Post by olie on 2006-04-07
I once experienced the exact same problem, and it turned out that the static IP number I had assigned to the server was used by another machine, which  confused PuTTY (D'oh!). Obvious of course, but it fooled me. ;)

---

### Post by allenlux on 2006-04-07
Thanks, Olie. In fact, that was exactly the problem, as I discovered a few hours after my original post. I had made a note of all the static IP addresses in use on my home LAN, but I got one wrong and then assigned the existing address to the new Ubuntu setup.

Two computers with the same IP address on a LAN is a recipe for serious confusion, since the symptoms bear no obvious relationship to the cause of the problem.

---

