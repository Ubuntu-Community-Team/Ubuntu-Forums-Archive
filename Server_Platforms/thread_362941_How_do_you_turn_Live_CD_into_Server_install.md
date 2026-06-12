---
title: "How do you turn Live CD into Server install?"
date: 2007-02-16
forum: Server Platforms
---

### Post by kwambus on 2007-02-16
Hi,

Situation is that the Ubuntu Server install will not work with my Adaptec i2o raid controller (system freezes on boot up, known issue with no solutions that I can find). However, my system does boot and install fine with the Edgy Live CD (Kubuntu in my case).

I have now installed the Lived CD Kubuntu o/s.

I have the following questions:

How can I stop XWindows (KDE) from loading at boot up?
Which packages do I need to add/remove to create what would be a basic Ubuntu Server install? I realise there may be many, but which are the primary ones to give me least overhead?

Many thanks in advance, been struggling with this machine for days.

---

### Post by Brazen on 2007-02-16
You could try going to synaptic and completely remove 'kubuntu-desktop'.  There is probably also a something-server package that you will want to install.

---

