---
title: "Planning Server Build with VMWare"
date: 2008-01-23
forum: Virtualisation
---

### Post by mcouture on 2008-01-23
I'm planning on building a machine based on Ubuntu and running a couple VMWare systems on it.   This is a home project.  This will be my primary PC.

I want to be able to have:

- my primary desktop running the usual email, Internet browsing, video editing etc
- an Ubuntu server running LAMP, ZoneMinder for my home security system, and be the core storage server for the other PCs in the house (samba shared)
- a Windows desktop partition for those one-off applications


My question is this....would I build an Ubuntu server as the primary system and then VM my desktops or should I create an Ubuntu desktop and VM the server and WinX box?

---

### Post by HermanAB on 2008-01-24
Hmm, I would do all the Linux stuff on the host and only make one VM for Windows XP.  You can make an Ubuntu VM for doing experiments though, so that if you wish to try something out, you don't screw up your host system accidentally.

Cheers,

H.

---

### Post by dcstar on 2008-01-26
> **HermanAB said:**
> Hmm, I would do all the Linux stuff on the host and only make one VM for Windows XP.  You can make an Ubuntu VM for doing experiments though, so that if you wish to try something out, you don't screw up your host system accidentally.


Agreed, install "normal" Ubuntu and then install the LAMP packages, then install VMware server (from the repos!) and install as many VMs as you like.

Read the various posts on getting maximum performance from your VM environment too.

---

