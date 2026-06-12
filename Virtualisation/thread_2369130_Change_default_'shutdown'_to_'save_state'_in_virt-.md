---
title: "Change default 'shutdown' to 'save state' in virt-manager on host shutdown"
date: 2017-08-18
forum: Virtualisation
---

### Post by accounts0 on 2017-08-18
Right now I have a VM set to start at boot, but when I reboot or shutdown it tries to do a shutdown within I think 110 seconds. This works at the moment, but before long I intend to have an app running in the VM that'll interrupt a graceful shutdown indefinitely.

So I'd like to find a way to set this one guest VM OS to save state rather than shutdown upon host shutdown. The either boot fresh or restore saved state upon the host's booting up.

I don't see any way in any settings in virt-manager to make this change. Is there a way?

Thanks...

---

### Post by lammert-nijhof on 2017-08-20
It helps is you mention which Virtual Management product you use.

---

### Post by accounts0 on 2017-08-21
> **lammert-nijhof said:**
> It helps is you mention which Virtual Management product you use.
Virt-manager 1.3.2 virt-manager.org

---

### Post by lammert-nijhof on 2017-08-27
Sorry has been on holiday for a few days. I'm not familiar with Virt-manager. I use Virtualbox myself and I can recommend it.

---

