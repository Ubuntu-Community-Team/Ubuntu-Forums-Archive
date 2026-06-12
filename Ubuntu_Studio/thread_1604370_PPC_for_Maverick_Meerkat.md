---
title: "PPC for Maverick Meerkat?"
date: 2010-10-23
forum: Ubuntu Studio
---

### Post by cicada1 on 2010-10-23
Hello, does anyone know if there will be a PPC version of Ubuntu Studio 10.10 I am finding some success with the alternate-powerpc Ubuntu distribution on another internal serial ata drive in my PPC G5, and was interested in this Kernel for audio purposes. Also could someone tell me the state of firewire drivers for this distribution. Thank you.

---

### Post by trulan on 2010-10-24
I can't help you on the PPC front, but I can tell you what I know of the state of the firewire drivers.

In Maverick, the new Juju driver stack is enabled by default.  The legacy driver stack is still there, but it is disabled.  The legacy stack can be re-enabled with some modprobe blacklisting magic.

The new firewire stack seems to work very well, with one major drawback (for audio work anyway).  You can't daisy-chain devices - only one interface at a time.  Other than that it's great.  CPU usage is lower, configuration is much easier, and I guess security is better as well.  That's pretty much it - it's better unless you need multiple devices.

---

### Post by cicada1 on 2010-10-24
Thank you for this information.

---

### Post by JOHNNYG713 on 2010-10-27
I don't know about PPC Ubuntu studio release, BUT you can go to synaptic and search "ubuntu studio" and there you should find all you need,I think, as I remember Buntu PPC uses special repos, give it a try!:)

---

### Post by cicada1 on 2010-11-06
Thank you. I have installed these via the Package Manager and am now exploring Ubuntu Studio.

---

### Post by Sakrecoer on 2011-02-05
I love you guys, this was the easiest thing in the world, and my dusty old G4 is nothing but a powerfull G thing!
Thank you so much!!!!

---

