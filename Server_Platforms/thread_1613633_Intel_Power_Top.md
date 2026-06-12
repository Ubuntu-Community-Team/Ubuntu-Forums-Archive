---
title: "Intel Power Top"
date: 2010-11-04
forum: Server Platforms
---

### Post by Vegan on 2010-11-04
I am evaluating Intel's PowerTop tool to see how mu CPU load is guzzling power.

Apache2 uses a lot of disk so disk savings are not being realized so easily.

I noticed PowerTOP wanted

CONFIG_PM_ADVANCED_DEBUG

in the boot options, how do I enable that?

---

### Post by Vegan on 2010-11-04
Crawling with Google finds its a known defect.

Bug 632327 is in bug number

---

### Post by Vegan on 2010-11-05
Can somebody manage to fix the problem so Intel users can use PowerTop which Intel graciously developed for GNU open source community.

---

### Post by Decatf on 2010-11-05
If you really need it that badly you can recompile the kernel with it enabled.
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by psusi on 2010-11-05
PowerTop works just fine for me without this option.

---

### Post by Vegan on 2010-11-05
Why can't that and the other lengthy list of bugs all get fixed sooner rather than later?

I realize I can fix the kernel to suit my needs, but that is not the real direction I wanted to go.

Powertop runs OK, but it still wants the module to be able to read C states.

Seems if that was available then the console for a server could leave it running and the KVM can scan the machines and see the loads easily.

---

### Post by Vegan on 2010-11-06
Another festering gripe is cpufrequtil which is useless and needs to be fixed.


:guitar:

---

