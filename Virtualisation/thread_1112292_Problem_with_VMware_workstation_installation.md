---
title: "Problem with VMware workstation installation"
date: 2009-03-31
forum: Virtualisation
---

### Post by Bourlog on 2009-03-31
Hello guys! I have been going trough all the guides here on the forums on how to install VMware workstation on my ubuntu laptop.

The problem is that, when im starting to "configure" the installation it says:

```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

make: *** /tmp/vmware-config0/vmmon-only: No such file or directory.  Stop.
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by HermanAB on 2009-03-31
Install the kernel source, compile and install the kernel.  That will ensure that you have a perfect setup with the kernel headers and tools matching the running kernel.  Following that, VMware will install without a hitch.

Google for kernel install guides or look at this:
[http://aeronetworks.ca/kernel-compile-howto.html](http://aeronetworks.ca/kernel-compile-howto.html)

---

### Post by lewtwo on 2009-04-01
from the errors youare getting I am guessing WS 5.5.x. It was last supported on EDGY. Afterspending several day trying to get 5.5.9 to install I upgraded to 6.5. Much easier and smoother install.

---

### Post by James_Lochhead on 2009-04-01
> **lewtwo said:**
> from the errors youare getting I am guessing WS 5.5.x. It was last supported on EDGY. Afterspending several day trying to get 5.5.9 to install I upgraded to 6.5. Much easier and smoother install.

...until you upgrade to Jaunty. You need to compile some stuff on Jaunty to make it work. Takes about 10 mins though.

---

