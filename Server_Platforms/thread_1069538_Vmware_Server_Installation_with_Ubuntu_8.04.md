---
title: "Vmware Server Installation with Ubuntu 8.04"
date: 2009-02-14
forum: Server Platforms
---

### Post by garciamanel on 2009-02-14
Hello, I have a problem with Vmware installation in Ubuntu Hardy.

I use the Kernel 2.6.24-23-server with Vmware Server 1.07 build 108231, and I aplied the patch vmware-any-any-update-116.tgz but I can't start install because appears the next message:

Your kernel was built with "gcc" version "4.2.3", while you are trying to use "/usr/bin/gcc" version "4.2.4". This configuration is not recommended and VMware Server may crash if you'll continue. Please try to use exactly same compiler as one used for building your kernel. Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway? [no]

For more information on how to troubleshoot module-related problems, please visit our Web site at "http://www.vmware.com/download/modules modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

How do I fix this?
There are many people with this problem and can not find the solution.

---

### Post by hyper_ch on 2009-02-14
what happesn if you say "yes"?

---

### Post by garciamanel on 2009-02-14
If I answer "yes" the installation is continuing and appears the message:

[I]The configuration of VMware Server 1.0.7 build-108231 for Linux for this 

running kernel completed successfully.
[/I]

But when I execute the command *sudo vmware* the program not run and appears the nest message in the console:

[I]/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
[/I]

I appreciate your interest.

M. Garcia - Spain

---

