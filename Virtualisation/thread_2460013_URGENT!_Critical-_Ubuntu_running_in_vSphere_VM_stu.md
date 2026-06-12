---
title: "URGENT! Critical- Ubuntu running in vSphere VM stuck at 'Started GNOME Desktop'"
date: 2021-03-31
forum: Virtualisation
---

### Post by araczek2 on 2021-03-31
Just upgraded all our Cisco UCS Standalone C240 servers from vSphere 6.5U3 to vSphere 6.7U3. The VM in question was running perfectly fine before. The VM is configured with 2 nVidia Tesla M60
GPU's. On powerup the VM gets stuck at "Started GNOME Display Manager". Could there be a problem with ECC being enabled on the host? VMware tools is not installed. I don't work with Ubuntu much
at all so I  was wondering how to get into a sort of "safe mode" and poke around to see what's going on. At least install VMware tools.

But the main problem is booting. This is a critical VM and I need to get this up. Talked with VMware support and they are almost deferring to Ubuntu to help TS this.

...Alan

---

### Post by TheFu on 2021-03-31
These forums are mainly for home Ubuntu users. Nobody here works for Canonical.  The last time I saw any UCS was around 2008 at my corporate job. None had any GPUs. We used text console for initial access and ssh access for everything else.

Have you contacted the UCS support guys at Cisco?  I knew a few back then and they all knew their stuff.

If you have business critical systems, might I suggest a support contract with Canonical is needed? Just don't want you to be frustrated by complete lack of relevant replies here.

---

### Post by ActionParsnip on 2021-03-31
Revert to snapshot. You do snapshot your VMs before doing anything... Right (not domain controllers)

---

### Post by howefield on 2021-04-02
Thread moved to the "*Virtualisation*" forum.

---

### Post by luca31 on 2021-04-03
is there any boot loader installed? try to press esc during boot and edit the menu to append the kernel option systemd.unit=multi-user.target to avoid windows manager startup and get access to a console for further analysis.

---

