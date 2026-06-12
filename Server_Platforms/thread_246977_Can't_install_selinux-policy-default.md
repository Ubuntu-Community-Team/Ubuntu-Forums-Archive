---
title: "Can't install selinux-policy-default"
date: 2006-08-30
forum: Server Platforms
---

### Post by kiddyliu on 2006-08-30
I have installed ubuntu6.06(kernel 2.6.15-26)on my computer.Yesterday I downloaded a new kernel(2.6.16.28)from the [www.kernel.org](www.kernel.org) and compiled it.After installed the new kernel I reboot my computer and entered into the new kernel.But when I tried to install selinux-policy-default_1.26-7_all.deb,an error encounterd:selinuxfs unknown filesytem type!Before installing selinux-policy-default,I have already installed the pre-depend packages:
libc6
checkpolicy
coreutils
cron
dpkg
fileutils
initscripts
libpam0g
libpam0g-dev
libpam-cracklib
libpam-doc
libpam-modules
libpam-runtime
libselinux1
logrotate
policycoreutils
procps
selinux-doc
selinux-utils
shellutils
strace
sysvinit
sysv-rc
textutils
The parameters related with selinux in the kernel's config are as 
follow:
CONFIG_KEYS=y
# CONFIG_KEYS_DEBUG_PROC_KEYS is not set
CONFIG_SECURITY=y
CONFIG_SECURITY_NETWORK=y
# CONFIG_SECURITY_NETWORK_XFRM is not set
CONFIG_SECURITY_CAPABILITIES=m
CONFIG_SECURITY_ROOTPLUG=m
CONFIG_SECURITY_SECLVL=m
CONFIG_SECURITY_SELINUX=y
CONFIG_SECURITY_SELINUX_BOOTPARAM=y
CONFIG_SECURITY_SELINUX_BOOTPARAM_VALUE=0
CONFIG_SECURITY_SELINUX_DISABLE=y
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1

CONFIG_AUDIT=y
CONFIG_AUDITSYSCALL=y
So what's the promble?How can I install the selinux-policy-default?
Thanks.

---

### Post by ewaldo on 2006-09-03
You must add selinux=1 enforcing=0 to your kernel boot options under /boot/grub/menu.lst.

---

