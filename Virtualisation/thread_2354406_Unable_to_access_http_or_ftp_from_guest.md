---
title: "Unable to access http or ftp from guest"
date: 2017-03-02
forum: Virtualisation
---

### Post by andrewgerm2 on 2017-03-02
Good day all

I am running a few virtual machines on Ubuntu 16.04. One guest is Win XP. From that machine, I can ping any host (local or Internet). I can check emails to an external mail server. I can also ping the host machine, and my router / gateway.

However, I am unable to do anything via http, https or ftp. I do not have the firewall on the guest active.

Any ideas where to start? Most of what I have found when searching has referred to no Internet access at all. I do have NAT selected in the Virtual Machine Manager settings, accessed from an Ubuntu 16.10 desktop.

Thanks in advance...

---

### Post by &amp;KyT$0P# on 2017-03-02
What virtualisation technology are you using?

---

### Post by andrewgerm2 on 2017-03-02
Libvirt, connecting via a qemu link in Virt-Viewer, straight from the Ubuntu official repo (and please excuse any ignorant sounding answers, as I sometimes get lost with Ubuntu).

The machine runs headless. No GUI. And admin via SSH or Webmin

---

