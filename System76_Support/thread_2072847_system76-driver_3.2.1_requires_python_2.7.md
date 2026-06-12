---
title: "system76-driver 3.2.1 requires python 2.7?"
date: 2012-10-18
forum: System76 Support
---

### Post by Dave_L on 2012-10-18
This morning the package "system76-driver" showed up as upgradable in synaptic, but when I try to upgrade it (version 3.2.0 to 3.2.1), I get a dependency error:

> system76-driver:
  Depends: python (>=2.7) but 2.6.5-0ubuntu1 is to be installed

I'm running Ubuntu 10.04.4, which is still supported, but has python 2.6.5.

Does system76-driver really require python >= 2.7?

---

### Post by isantop on 2012-10-18
> **Dave_L said:**
> This morning the package "system76-driver" showed up as upgradable in synaptic, but when I try to upgrade it (version 3.2.0 to 3.2.1), I get a dependency error:



I'm running Ubuntu 10.04.4, which is still supported, but has python 2.6.5.

Does system76-driver really require python >= 2.7?

Yes, the requirements are as low as we can keep them, however you will need at least python 2.7 in order for everything to run properly.

---

### Post by Dave_L on 2012-10-18
Thanks for the response.

Does that mean that System76 no longer supports Ubuntu 10.04?

---

### Post by isantop on 2012-10-19
> **Dave_L said:**
> Thanks for the response.

Does that mean that System76 no longer supports Ubuntu 10.04?

On Desktop/Laptop machines, we officially support the latest version of Ubuntu. We can usually also support the latest LTS. But for anything older than that, our ability to provide support is limited.

What model do you have? You shouldn't need anything newer than 3.0.0 for 10.04, since we only really make changes for the current Ubuntu version.

---

### Post by Dave_L on 2012-10-19
> **isantop said:**
> On Desktop/Laptop machines, we officially support the latest version of Ubuntu. We can usually also support the latest LTS. But for anything older than that, our ability to provide support is limited.

What model do you have? You shouldn't need anything newer than 3.0.0 for 10.04, since we only really make changes for the current Ubuntu version.

I have a star3.

Thanks for the advice. I'll stick with system76-driver 3.2.0. I've disabled the system76 repository so I won't get nagged about upgrades for the driver.

---

