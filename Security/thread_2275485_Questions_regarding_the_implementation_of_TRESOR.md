---
title: "Questions regarding the implementation of TRESOR"
date: 2015-04-26
forum: Security
---

### Post by squirrel2003 on 2015-04-26
I am trying to get Tresor running on my ubuntu 14.04 system.
Regarding the tutorial [http://www1.cs.fau.de/tresor?q=content/readme](http://www1.cs.fau.de/tresor?q=content/readme) i am having some questions.

1. What does line III. exactly mean? I did not manage to correctly  execute this line could you please tell me step by step for  a noob what i exactly have to do?

2. After i am through applying the steps explained in the Start System of the readme i  guess the encryption keys of my already installed system will still be stored in RAM, or will tresor work with my system in place when i choose the TRESOR kernel during boot? I guess i will have to follow the steps to create a partition using tresor and afterwards make it a root partition and install ubuntu in it to make tresor really work or could i somehow configure my already working system to use TRESOR for encryption?

Thanks for your help in advance.

---

### Post by matt_symes on 2015-04-26
Hi

> **squirrel2003 said:**
> I am trying to get Tresor running on my ubuntu 14.04 system.
Regarding the tutorial [http://www1.cs.fau.de/tresor?q=content/readme](http://www1.cs.fau.de/tresor?q=content/readme) i am having some questions.

1. What does line III. exactly mean? I did not manage to correctly  execute this line could you please tell me step by step for  a noob what i exactly have to do?


```
matthew-laptop:/home/matthew:2 % cd && wget http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.2.tar.gz
--2015-04-26 22:54:54--  http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.2.tar.gz
Resolving www.kernel.org (www.kernel.org)... 198.145.20.140, 149.20.4.69, 199.204.44.194, ...
Connecting to www.kernel.org (www.kernel.org)|198.145.20.140|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.2.tar.gz [following]
--2015-04-26 22:54:55--  https://www.kernel.org/pub/linux/kernel/v3.0/linux-3.6.2.tar.gz
Connecting to www.kernel.org (www.kernel.org)|198.145.20.140|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 103930088 (99M) [application/x-gzip]
Saving to: &#8216;linux-3.6.2.tar.gz&#8217;

100%[====================================================================================>] 103,930,088 2.31MB/s   in 88s    

2015-04-26 22:56:23 (1.13 MB/s) - &#8216;linux-3.6.2.tar.gz&#8217; saved [103930088/103930088]

matthew-laptop:/home/matthew:2 % sudo tar -xf linux-3.6.2.tar.gz -C /usr/src
[sudo] password for matthew: 
matthew-laptop:/home/matthew:2 % wget http://www1.informatik.uni-erlangen.de/filepool/projects/tresor/tresor-patch-3.6.2_i686
--2015-04-26 23:09:09--  http://www1.informatik.uni-erlangen.de/filepool/projects/tresor/tresor-patch-3.6.2_i686
Resolving www1.informatik.uni-erlangen.de (www1.informatik.uni-erlangen.de)... 131.188.31.225, 2001:638:a000:4104::225
Connecting to www1.informatik.uni-erlangen.de (www1.informatik.uni-erlangen.de)|131.188.31.225|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://www1.cs.fau.de/filepool/projects/tresor/tresor-patch-3.6.2_i686 [following]
--2015-04-26 23:09:10--  https://www1.cs.fau.de/filepool/projects/tresor/tresor-patch-3.6.2_i686
Resolving www1.cs.fau.de (www1.cs.fau.de)... 131.188.31.225, 2001:638:a000:4104::225
Connecting to www1.cs.fau.de (www1.cs.fau.de)|131.188.31.225|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47050 (46K)
Saving to: &#8216;tresor-patch-3.6.2_i686&#8217;

100%[====================================================================================>] 47,050      --.-K/s   in 0.1s    

2015-04-26 23:09:10 (399 KB/s) - &#8216;tresor-patch-3.6.2_i686&#8217; saved [47050/47050]

matthew-laptop:/home/matthew:2 % sudo patch --directory /usr/src/linux-3.6.2 -p1 < tresor-patch-3.6.2_i686 
patching file Makefile
patching file arch/x86/crypto/Makefile
patching file arch/x86/crypto/tresor_asm.S
patching file arch/x86/crypto/tresor_glue.c
patching file arch/x86/crypto/tresor_key.c
patching file arch/x86/include/asm/debugreg.h
patching file arch/x86/include/asm/hw_breakpoint.h
patching file arch/x86/include/asm/processor.h
patching file arch/x86/kernel/ptrace.c
patching file crypto/Kconfig
patching file crypto/testmgr.c
patching file drivers/tty/vt/vt.c
patching file include/crypto/tresor.h
patching file init/main.c
patching file kernel/power/process.c
patching file kernel/power/suspend.c
matthew-laptop:/home/matthew:2 % matthew-laptop:/home/matthew:2 % sudo apt-get -qq install libncurses5-dev
Selecting previously unselected package libtinfo-dev:amd64.
(Reading database ... 284212 files and directories currently installed.)
Preparing to unpack .../libtinfo-dev_5.9+20140118-1ubuntu1_amd64.deb ...
Unpacking libtinfo-dev:amd64 (5.9+20140118-1ubuntu1) ...
Selecting previously unselected package libncurses5-dev:amd64.
Preparing to unpack .../libncurses5-dev_5.9+20140118-1ubuntu1_amd64.deb ...
Unpacking libncurses5-dev:amd64 (5.9+20140118-1ubuntu1) ...
Setting up libtinfo-dev:amd64 (5.9+20140118-1ubuntu1) ...
Setting up libncurses5-dev:amd64 (5.9+20140118-1ubuntu1) ...
matthew-laptop:/home/matthew:2 % cd /usr/src/linux-3.6.2     
matthew-laptop:/usr/src/linux-3.6.2:2 % sudo make mrproper
....            
matthew-laptop:/usr/src/linux-3.6.2:2 % sudo make menuconfig 
......

```

Hopefully the above will help a bit. Of course you need to make sure you get the correct patch and build for 32 or 64 bit.

> 2. After i am through applying the steps explained in the Start System of the readme i  guess the encryption keys of my already installed system will still be stored in RAM, or will tresor work with my system in place when i choose the TRESOR kernel during boot? I guess i will have to follow the steps to create a partition using tresor and afterwards make it a root partition and install ubuntu in it to make tresor really work or could i somehow configure my already working system to use TRESOR for encryption?

Thanks for your help in advance.

No idea. Never heard of TRESOR until i read your post. I'll be reading through some of the information about it tomorrow evening though.

It looks interesting.

Kind regards

---

### Post by ant2ne on 2015-04-28
>  /usr/src/> patch --directory /usr/src/linux-3.6.2 -p1 < tresor-patch-3.6.2
This line implies you are in the path '/usr/src' and there is a file called 'patch' which is executable and knows how to handle the switch '--directory' and '-p1'. And then it is going to do something in the path of /usr/src/linux-3.6.2, probably modify your kernel.

---

### Post by squirrel2003 on 2015-04-28
For me executing this line in a terminal did not really work maybe because i was curious and skipped part III of the tutorial when i did not manage to get it done quickly and continued with step IV and V.
Is there a way to undo the changes i have done by applying those steps and try it again besides reverting back to an earlier system state by imaging?

---

### Post by squirrel2003 on 2015-07-18
> **matt_symes said:**
> Hi
....
Hopefully the above will help a bit. Of course you need to make sure you get the correct patch and build for 32 or 64 bit.



No idea. Never heard of TRESOR until i read your post. I'll be reading through some of the information about it tomorrow evening though.

It looks interesting.

Kind regards

Thanks  i managed to install tresor inside a virtual ubuntu 14.04.2  machine without any updates copy pasting  the commands in your post,  just had to apply for a 64 bit System.
Running menuconfig i left everything default and pressed ESC.
I think that is what i should do but when rebooting and entering grub i have only the standard kernels to choose i guess i did something wrong configuring the tutorial on their homepage says the next time one reboots there should be a new kernel to chose.
The kernel patch should be fit for ubuntu 14.04.2 right?

Regards, squirrel2003

---

### Post by squirrel2003 on 2015-07-19
So i have tried to apply the patch by installing 12.04 in avirtual machine,  then i installed 3.6.2 kernel and followed the steps described by matt.
After running menuconfig i am pressing ESC and the tresor config menu asks me if i want so save the new configuration i accept but after rebboting i still have only the standard kernels (linux 3.6.2 + linux 3.6.2 memtest + old kernels) in my grub menu to chose from.
Has anyone an idea what i may have done wrong?
Maybe a virtual machine is not the right enviroment for tresor and i would have to specify an option in the menu config menu?

Regards, squirrel2003

---

### Post by squirrel2003 on 2015-07-19
So i have tried to apply the patch by installing 12.04 in avirtual machine,  then i installed 3.6.2 kernel and followed the steps described by matt.
After running menuconfig i am pressing ESC and the tresor config menu asks me if i want so save the new configuration i accept but after rebboting i still have only the standard kernels (linux 3.6.2 + linux 3.6.2 memtest + old kernels) in my grub menu to chose from.
Has anyone an idea what i may have done wrong?
Maybe a virtual machine is not the right enviroment for tresor and i would have to specify an option in the menu config menu?

Regards, squirrel2003

---

### Post by squirrel2003 on 2015-07-22
I realise i forgot to apply the last three steps of the tutorial so no wonder it did not work.

Running 

make-kpkg kernel_image --initrd --revision tresor1

I am getting an error message:

CC [M]  lib/zlib_deflate/deftree.o
  CC [M]  lib/zlib_deflate/deflate_syms.o
  LD [M]  lib/zlib_deflate/zlib_deflate.o
  Building modules, stage 2.
  MODPOST 2695 modules
ERROR: "__modver_version_show" [drivers/staging/rts5139/rts5139.ko] undefined!
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving Directory '/usr/src/linux-3.6.2'
make: *** [debian/stamp/build/kernel]  Error 2

Furthermore in the next step of the tutorial they say one should run:
/usr/src/> dpkg -i linux-image-3.6.2-tresor1.deb

I am not able to find the .deb file anywhere is this a result of the unsuccessful completion of the step before?

---

### Post by matt_symes on 2015-07-23
Hi

I'll take a look at the over the weekend squirrel2003 and see if i can get it built.

Kind regards

---

### Post by anon9815 on 2015-07-23
not sure if you know this but cold boot attacks aren't feasible against systems using ddr3 ram or ddr4 ram  though if you have a old computer it might be necessary if they can get physical access i would worry more about keyloggers and other bugging devices.

---

### Post by squirrel2003 on 2015-07-24
> Hi  I'll take a look at the over the weekend squirrel2003 and see if i can get it built.  Kind regards  Thanks matt, i really appreciate it, but i realised that there maybe is a way to bypass tresor so i might not finish the implementation on my system i will look deeper into TRESOR Hunt first and see if it would really work to defeat TRESOR on my settings here.   > not sure if you know this but cold boot attacks aren't feasible against  systems using ddr3 ram or ddr4 ram  though if you have a old computer it  might be necessary if they can get physical access i would worry more  about keyloggers and other bugging devices.  I am not 100% sure if cold boot will not work with ddr3 ram and also if DMA attacks would work or not.

---

### Post by squirrel2003 on 2015-07-24
Okay maybe there is a way to bypass TRESOR.
[http://dl.acm.org/citation.cfm?doid=2420950.2420961](http://dl.acm.org/citation.cfm?doid=2420950.2420961)

---

