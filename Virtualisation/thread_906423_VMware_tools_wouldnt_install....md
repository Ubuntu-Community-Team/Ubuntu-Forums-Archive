---
title: "VMware tools wouldnt install..."
date: 2008-08-31
forum: Virtualisation
---

### Post by NetSkay on 2008-08-31
okay i did this and i have everything and i get this message, same as before...

What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/incclude]
i put this
/usr/src/linux-headers-2.6.24-19-generic/include

installer response
the directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match your running kernel (version 2.6.24-19-generic). even if the module were to compile successfully, it would not load into the running kernel

then it asks for the directory again wtf?!

---

### Post by HermanAB on 2008-08-31
VMware is compiled from source when you install it.  Therefore your software development system has to be configured properly before you start.

The easiest way to ensure that, is to compile the Linux kernel.  So, get the kernel source, install it, compile it and instal the compiled kernel, then reboot.

Now you can install VMware - and don't change or update the kernel again, unless you wish to do it all over again...

Cheers,

Herman

---

### Post by NetSkay on 2008-08-31
ubuntu is the guest OS, i just want to install the tools... im better of re-installing ubuntu and hoping it owuld work than recompiling the kernel
any other suggestions?

---

### Post by dpj23 on 2008-08-31
With the guest OS "Ubuntu" running...

1. select "VM" from the menu and then select "install vmtools"

2. you will need "su" permissions to install.

3. once this is complete you need to configure the tools...

4. sudo -l /usr/bin/vmware-config-tools.pl

5. this will complete the installation and allow you to configure the display....

hope this helps...

---

