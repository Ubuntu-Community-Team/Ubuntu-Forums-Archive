---
title: "update-initramfs not in /lib/modules/..."
date: 2011-03-01
forum: Ubuntu Dev Link Forum
---

### Post by migounette on 2011-03-01
I have a simple question, I am currently building my kernel out of the source not in root mode.

# All stuff go to MY OUTPUT
make -j8 KSRC=${MY_SOURCE} KERNEL_OUTPUT=${MY_OUTPUT} all

# Module installation in MY_MOD_PATH
make KSRC=${MY_SOURCE} KERNEL_OUTPUT=${MY_OUTPUT} INSTALL_MOD_PATH=${MY_MOD_PATH} modules_install

# ---> Here is my problem
/usr/sbin/update-initramfs -c -k ${MY_VERSION} -b ${MY_BOOT}

I have the following line, which is normal....
FATAL: Could not load /lib/modules/2.6.32.27/modules.dep

I would like to order to look in ${MY_MODE_PATH}/lib/modules

Moreover, I should be able to create a link from /lib/modules but this directory is owned by root and 755

---

