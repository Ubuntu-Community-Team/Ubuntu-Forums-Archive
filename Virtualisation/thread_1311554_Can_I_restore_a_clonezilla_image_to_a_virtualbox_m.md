---
title: "Can I restore a clonezilla image to a virtualbox machine?"
date: 2009-11-02
forum: Virtualisation
---

### Post by Vunutus on 2009-11-02
I have a clonezilla image of a Windows XP installation. Is it possible for me to load this clonezilla image into a virtualbox machine?

Like, what I thought about doing was booting clonezilla inside the VM and telling it to restore my image to the local disk (which in this case should actually be the VM's disk). Once this is finished, will I have a working XP VM or just a mess?

---

### Post by lykwydchykyn on 2009-11-02
In my experience, this can be done but it's not going to immediately work.  Due to differences between the virtualized hardware and the real hardware, it's very likely the virtual machine will just blue-screen because it's using the wrong HAL.

What you do in this case is boot the virtual machine to a Windows CD and run a repair installation (which presumes you have access to a real honest-to-goodness WinXP CD and not a "restore CD").

Sometimes this works, sometimes not.  I've gotten a few machines virtualized this way.

---

