---
title: "[SOLVED] problems with loading vboxdrv"
date: 2008-11-05
forum: Virtualisation
---

### Post by king.pest on 2008-11-05
Hi, 

I have a strange problem with loading a kernel module for VirtualBox (same situation with virtualbox-ose and with virtualbox-2.0 package): while I'm able to compile the module without any problems, I'm not able to load it. I'm getting an error message
```

root@fermat:~# dmesg|grep vbox
vboxdrv: no symbol version for struct_module
vboxdrv: no symbol version for struct_module

```
The problem is probably with my custom kernel, however I do have a number of drivers loaded as modules and they don't cause any problems. Does VirtualBox need some special kernel configuration option?

---

### Post by king.pest on 2008-11-06
anyone?:(

---

### Post by Marabu on 2008-11-06
What version of the kernel are you using? And which version of VirtualBox? 

Did you compile the vbox module against the same headers and with the same config you built your running kernel? And when trying to insert the module, does it load or not?

---

### Post by king.pest on 2008-11-06
> **Marabu said:**
> What version of the kernel are you using? And which version of VirtualBox? 


kernel 2.6.26 (vanilla + tuxonice), virtualbox 2.0.4
> 
Did you compile the vbox module against the same headers and with the same config you built your running kernel?
yes I did.
> And when trying to insert the module, does it load or not?
no, it doesn't.

---

### Post by PatrickVogeli on 2008-11-06
I have a solution, or at least I think so.

Just copy the file Module.symversion from /lib/modules/your-kernel-name into the kernel source location.

I have my kernel source under /usr/src and have a symlink to /usr/src/linux, and copied the file into that directory, then cd /usr/src/linux && sudo make prepare scripts and at last compiled with sudo KERN_DIR=/usr/src/linux /etc/init.d/vboxdrv setup

it worked!

I lost a few hours until the log file gave me the clue.

cheers

---

### Post by king.pest on 2008-11-06
mate, you rock. this worked, thanks a lot!

---

### Post by Silvr2008 on 2009-05-16
I am having this same issue. I have tried 
KERN_DIR=/usr/src/linux-2.6.29.2-custom /etc/init.d/vboxdrv setup and the modprob fails with the dmesg mentioned above. I did some reading and found that it is really looking for the headers so I did a make headers_install and pointed it to the headers but still the same error. 

I am on a newer kernel, but I do not have Module.symversion just modules.symbols and it does not work the same as mentioned above. Is this fix adaptable to newer kernels?

---

### Post by LegoGT on 2009-06-23
> **Silvr2008 said:**
> I am having this same issue. I have tried 
KERN_DIR=/usr/src/linux-2.6.29.2-custom /etc/init.d/vboxdrv setup and the modprob fails with the dmesg mentioned above. I did some reading and found that it is really looking for the headers so I did a make headers_install and pointed it to the headers but still the same error. 

I am on a newer kernel, but I do not have Module.symversion just modules.symbols and it does not work the same as mentioned above. Is this fix adaptable to newer kernels?

I had a similar issue and was missing module.symversion, as well. So, I decided to pull down the kernel source via apt-get. Then I followed the process of building a kernel without doing the actual install: make oldconfig, make prepare scripts, make, make modules.

Once that finished I re-ran the vboxdrv setup and it finally worked.

Hope that works for you, too!

---

### Post by alonsoac007 on 2010-10-09
I had this same problem on Mandriva 2010. I had installed the default kernel, and had installed the kernel-source package. This was not enough to make it work. The trick was to install the kenel-xxxx-devel package. Make sure to install the same kernel-xxx-devel package as the kernel you have installed. Use uname -a to see the kernel version you are running.

Another way to do it if you have already installed the kernel souce package and don't want to install the kernel devel package: take a look in /lib/modules/<kernel version here>/ there are symbolic links build and source, make sure those point to the place where you have the corresponding kernel headers. 

Now the build should work.

---

