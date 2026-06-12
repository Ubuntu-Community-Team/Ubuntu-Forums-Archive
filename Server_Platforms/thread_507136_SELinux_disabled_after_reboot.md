---
title: "SELinux disabled after reboot"
date: 2007-07-22
forum: Server Platforms
---

### Post by k_grdn on 2007-07-22
Hi,

Ubuntu 6.06-Server

Enabled kernel 2.6.15-26 support, installed selinux-policy-default and related packages.

sestatus returns:

SELinux status: enabled
SELinuxfs mount: /selinux
Current mode: permissive

Must of missed something cause after reboot sestatus returns disabled, running make load in the current policy directory sestatus again returns enabled.

My thoughts are that checkpolicy creates a binary file to be loaded into the kernel, by making the file maybe this binary gets loaded and returns enabled.  How do I get this binary to load into the kernel during init?  I have sysvinit installed, has anyone got selinux successfully running on ubuntu servers.  

Regards,

k_grdn

---

### Post by ruibernardo on 2007-07-23
Hi k_grdn,

you need to enable the selinux option on the boot kernel options.

```
sudo nano /boot/grub/menu.lst
```Search for the line "# kopt=" (just with a cardinal) and add "selinux=1" at the end. Then update your kernel options to all the kernels you have installed with:

```
sudo update-grub
```I've used this in Feisty, never in Dapper, but I think the ubuntu kernel is compiled with SElinux options since Breezy, so this should work.

Cheers.

---

### Post by k_grdn on 2007-07-23
Hi epimeteo,

Thanks for the reply.

I have previously enabled kernel support, dmesg indicates that selinux has initialized in permissive mode:

dmesg | grep SELinux 

[42949375.960000] SELinux:  Initializing.
[42949375.960000] SELinux:  Starting in permissive mode
[42949376.720000] SELinux:  Registering netfilter hooks

Also:

dmesg | grep selinux
[42949372.960000] Kernel command line: root=/dev/sda7 ro selinux=1 enforcing=0 quiet splash
[42949377.920000] selinux_register_security:  Registering secondary module capability

sestatus returns disabled, but after installing selnux-policy-default returns enabled, after system reboot returns disabled!

Regards,

k_grdn

---

### Post by ruibernardo on 2007-07-23
Sorry, I didn't read all your message. I though it was another problem.

I think the problem about the module loading on boot can be solved by installing the package **initrd-tools** and executing

```
 sudo update-initramfs -u -k
```

right after SElinux is installed and running.

I've tried to install SElinux with selinux-policy-default (on Feisty), and I got problems too. From my personal notes, I've found this two links: [http://packages.debian.org/changelogs/pool/main/r/refpolicy/refpolicy_0.0.20061018-5/changelog](http://packages.debian.org/changelogs/pool/main/r/refpolicy/refpolicy_0.0.20061018-5/changelog) and [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384850](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384850). 

I don't know if this is related to your problem, but in Feisty this two pages helped me to get SElinux working with selinux-policy-default (only with a fresh install of Ubuntu. I never got it working after uninstall and reinstall any of the policy packages).

With the package selinux-policy-refpolicy-targeted I got no problem.


Hope this helps.

---

### Post by k_grdn on 2007-07-23
Hi epimeteo,

Thanks again for the help.

Tried the initrd-tools still same result after reboot, think the bug is related to upstart not working with selinux: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/124865](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/124865).

Previously tried the sysvinit fix without success, but with selinux-default-policy not selinux-policy-targeted.  Dpkg is exiting with errors installing seliunx-policy-targeted from:
[http://pearls.tuxedo-es.org/selinux/ubuntu/](http://pearls.tuxedo-es.org/selinux/ubuntu/) ./

Can anyone suggest sources for selinux-policy-targeted or selinux-policy-refpolicy-targeted?

Regards,

k_grdn

---

### Post by ruibernardo on 2007-07-25
Hi k_grdn,

your problem is very strange and does not seem to be related with SElinux. 

That bug is related with upstart. You said in your first post that you got Dapper, and upstart started to be shipped in Edgy.

The selinux-policy-refpolicy-targeted is on the official repos, you don't need to use 3rd party repos to install it.

---

### Post by k_grdn on 2007-07-25
Hello again epimeteo,

apt can't find the package selinux-policy-refpolicy targeted, I'm in the process of migrating servers from SLES to Ubuntu went for 6.06 Dapper for the long term support.  Hoping to protect Web Servers with SELinux at present testing with VM's.

What I can gather is the policy is not be loaded by init.

The next option I think is to try from source, any ideas?

Thanks Again

k_grdn

---

### Post by k_grdn on 2007-07-25
One more thing, after reboot.

id -Z returns:

Sorry, --context (-Z) can be used only on a selinux-enabled kernel.

dmesg returns

dmesg | egrep "selinux|SELinux"
[42949372.960000] Kernel command line: root=/dev/sda7 ro selinux=1 enforcing=0 quiet splash
[42949374.810000] SELinux:  Initializing.
[42949374.810000] SELinux:  Starting in permissive mode
[42949375.660000] SELinux:  Registering netfilter hooks
[42949376.820000] selinux_register_security:  Registering secondary module capability

Regards,

k_grdn

---

### Post by ruibernardo on 2007-07-25
The package is there (EDIT: at least here in Feisty):

```
user@ubuntu:~$ apt-cache search selinux-policy-refpolicy-targeted
selinux-policy-refpolicy-targeted - Targeted variant of the SELinux reference policy

```No, no ideas. That package didn't gave me any problem.

---

### Post by k_grdn on 2007-07-25
apt-cache returns nothing.

These are my repositories.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
                                                         
Regards,

k_grdn

---

### Post by k_grdn on 2007-07-25
Error using load_policy,

Loading Policy ...
/usr/sbin/load_policy:  Warning!  Policy file argument (/etc/selinux/./policy/policy.20) is no longer supported, installed policy is always loaded.

---

