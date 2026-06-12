---
title: "VirtualBox and Windows XP"
date: 2008-03-20
forum: Virtualisation
---

### Post by rpainter on 2008-03-20
I have Windows XP running in VirtualBox with no problems. My question is this: Do I need to have a firewall running in XP, or will my Linux install protect it?

---

### Post by Hero of Time on 2008-03-20
It is still advised to run a firewall in Windows. The default firewall just plain sucks, so a 3rd party is needed. I found that if I disable something in the Host OS, the Guest can still go thought or be accessible. Note that if you use NAT, a firewall is less needed, as the VBox process will use the internet, not the VM directly, thus using the Host protection.

---

