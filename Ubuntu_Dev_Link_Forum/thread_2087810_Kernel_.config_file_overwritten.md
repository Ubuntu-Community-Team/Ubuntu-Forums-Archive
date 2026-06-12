---
title: "Kernel .config file overwritten"
date: 2012-11-24
forum: Ubuntu Dev Link Forum
---

### Post by daniel488 on 2012-11-24
Hello,

I wanted to compile my kernel from sources. I needed to add one line in .config file, because that option is not possible to change by 'make menuconfig' (it is there when I search with '/' but there is no access to change it in menu).

But then when I start compilation, these lines are shown at startup:

```
scripts/kconfig/conf --silentoldconfig Kconfig
#
# configuration written to .config
#

```

and my .config is saved as .config.old file and new .config is created. 

How can I use my manually modified .config file?

---

