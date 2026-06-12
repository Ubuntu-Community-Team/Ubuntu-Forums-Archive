---
title: "Vmware Server 2.0.2 install error ubuntu 12.04"
date: 2012-06-07
forum: Virtualisation
---

### Post by fire_blade on 2012-06-07
Help !!

how can i install vmware server 2.0.2 on ubuntu 12.04 . i tryed install but get error installing. 


Ubuntu kernel version 3.2.0.24
gcc version 4.6.3

error code :

```
Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 




None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.6.3", while you are trying to use 
"/usr/bin/gcc" version "4.6". This configuration is not recommended and VMware 
Server may crash if you'll continue. Please try to use exactly same compiler as
one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.6" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```



help me
thnx!!

---

### Post by hawkmage on 2012-06-08
VMWare Server was end of life almost a year ago.  You may want to look at VMWare Player or even Oracle VirtualBox.

---

### Post by jocampo on 2012-09-03
You need to say "YES" ... or won't continue ...

Did you install the development tools?

```

sudo apt-get install make
sudo apt-get install gcc

```

If you have not, tried that ...

On my case, that fixed that error, but you may get this one...

```


The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.33).  Even if the module were to compile
successfully, it would not load into the running kernel.
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]


```

I fixed that one, adding this line to version.h file

```

#define UTS_RELEASE "2.6.33"

```

where the number, should be your Ubuntu release, of course ...

Those changes, force the installation to compile, but it failed. I am trying to fix the last error. Let me know if works for you.

I know VMware server support ended, but I don't want VMware Player.

By the way, I am using Ubuntu Server Precise...

---

### Post by blyefd on 2012-10-06
> **jocampo said:**
> 
I am trying to fix the last error. 

Did you ever get it to work?

If so can you please post your solution?

thanks

---

### Post by lisati on 2012-10-06
*Thread moved to **Virtualization**.*

---

