---
title: "[SOLVED] Xen on server 8.04, problem with apt-get upgrade"
date: 2008-07-08
forum: Virtualisation
---

### Post by Krusty Ruffle on 2008-07-08
I installed hardy server edition, set up xen, installed hardy into 4 DomU virtual machines on LVM, everything works fine, until I do apt-get upgrade in a DomU, then it overwrites all of the configuration files for anything I've done that happens to be upgrading!!!

OUCH.. should I have installed something before attempting to upgrade packages inside a DomU? That seems kind of silly, even virtual machines would need updates for security, and I'm pretty sure nobody wants to reconfigure everything by hand after every package upgrade.

So, in a nutshell, how can I keep apt-get upgrade from overwriting configuration files, or at least make it ask me before overwriting with the maintainers version like it does on the server and workstations without virtualization?

Thank you very much to anybody who can help me with this...

[edit]-------------------------------------------------------
Hmm... After testing some things, namely setting up new Virtual machines and running apt-get upgrade in them, I've found that the new ones are working properly and asking before overwriting files I've modified.

I'm not sure what happened, but given this evidence I'm going to chalk it up to user error somewhere and just go on about fixing it???

---

