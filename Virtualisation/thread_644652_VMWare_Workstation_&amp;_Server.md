---
title: "VMWare Workstation &amp; Server"
date: 2007-12-19
forum: Virtualisation
---

### Post by markymarknz on 2007-12-19
Hi Everyone,

I just had a quick question about whether its ok/possible to have both vmware workstation and server running on the same Ubuntu host.
For development if I want to run servers on the server install and win xp on the workstation install.
My only real concern is that the virtual networks that they setup will conflict or there might be other issue I'm not aware of.

Cheers

Mark

---

### Post by fjgaude on 2007-12-19
As far as I have tried the answerto it is, "No."

You can't install one if the other has already been installed, in fact, you can't if any piece of the other is installed, else an error.

---

### Post by markymarknz on 2007-12-20
Thanks for your reply.
I think I'll give VBox a go anyway.

---

### Post by dpj23 on 2007-12-22
One thing to consider is this...  If you create virtual machines using workstation 6 they won't play in vmserver...  This is one of the changes they made with the release of 6...  In fact, they won't play on ESX server either...  So, don't feel so bad...

---

