---
title: "How do you recompile kernel with -march=ivybridge?"
date: 2018-02-22
forum: Ubuntu Development Version
---

### Post by nbritton on 2018-02-22
I want to recompile the stock Bionic kernel with the "-march=ivybridge -O2" GCC optimization flags, how do I do this? Is it just: export CFLAGS=[FONT=Verdana]"-march=ivybridge -O2" and then follow this [guide]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel")?

I'm seeing 18.8% less cpu performance compared to the stock kernel with CentOS 7, see [here]("https://browser.geekbench.com/v4/cpu/compare/7164775?baseline=7164169").

[/FONT]

---

