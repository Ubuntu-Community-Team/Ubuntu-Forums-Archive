---
title: "kernel compilation Ubuntu Server 12.04 Error 2"
date: 2012-08-28
forum: Server Platforms
---

### Post by d80k on 2012-08-28
Hi
I'm fighting for a few days to compile the kernel in Ubuntu 12.04 and appending grsecurity patch. I tried a few instructions from the net.
I tried to download a new kernel from kernel.org and sources. Compilation always ends in the following error:
   
  *** End of the configuration.
*** Execute ‘make’ to start the build Or try ‘make help’
  [COLOR=windowtext]dk@dk:~/linux-3.2.0$[/COLOR] sudo make
scripts/config/config –silentoldconfig Kconfig
make [1]: *[FONT=&quot]Nothing[/FONT]* to be done for `*[FONT=&quot]relocs[/FONT]*'.
  CHK       include/linux/version.h
CHK       include/generated/utsrelease.h
UPD       include/generated/utsrelease.h
CALL      scripts/checksyscalls.sh
CC          init/main.o
  In file included from init/main.c:40:0:
include/Linux/cpuset.h: In function put_mems_allowed:
**include/Linux/cpuset.h:121:2:  error:** dekrement of read-only location *(const volatile
 rrent()->mems_allowed_change_disable
init/main.c: At top level:
**init/main.c:335:19: warning:** pass_unknown_bootoptions defined but not used [-Wunused-
make[1]: *** [init/main.o] Error 1
make: *** [init] Error 2

what is it? I do not understand what this error means?

please help

d80k

---

### Post by Doug S on 2012-08-31
Did you get your kernel compile issues sorted out?
 
This thread might be seen by more kernel compile types over on the "Development & Programming" - "Packaging and Compiling Prgrams" forum.
 
The error is because some code is trying to modify a constant. Why, I don't know, I would have to look at the code.
 
As a fisrt step for kernel compiling, I recommend not making any changes or applying any patches. That gives you a basline compile, just to know that compile (and load and run) works.
 
Many "how to compile the kernel" references are incorrect, or confusing, or obsolete. The process can be very very frustrating for someone trying to learn. For kernels from kernel.org, I have had some success with these steps (I can not recall the reference):```
1. get the kernel history, if you don't already have it:
  git clone \
    git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
2. get point releases:
  cd linux
  git remote add stable \
    git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git
  git fetch stable
3. apply patch, test:
  git checkout stable/linux-3.2.y   [COLOR=red]#<<< Yes, use "y". I wasted a few days thinking they meant to subsitute "22" or "23" or whatever (which you can do for a specific kernel).[/COLOR]
  git am -3sc /path/to/the/patch   #[COLOR=red]<<< For me this rarely works. I manually apply.[/COLOR]
  cp /boot/config-$(uname -r) .config; # current configuration
  [COLOR=red]cp  /boot/config-3.2.0-26-generic .config  #<<< or this for a specific config[/COLOR]
  scripts/config --disable DEBUG_INFO
  make localmodconfig; # optional: minimize configuration [COLOR=red]#<<< I don't bother[/COLOR]
  make deb-pkg; # optionally with -j<num> for parallel build
  dpkg -i ../<name of package>; # as root
  reboot
```I had tried before without git, but had troubles, so before the above (I actually already had build-essential):```
sudo apt-get install git build-essential
```For compling Ubuntu kernel source, I recommend: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
 
I think the grsecurity patch is pretty complicated (I don't know it, though) so you will want to be sure that the patch and kernel are matched for each other (i.e. you probably would have grief trying to manually apply the patch.)
 
Hope this helps.

---

