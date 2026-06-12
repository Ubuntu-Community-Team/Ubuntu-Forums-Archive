---
title: "Linux kernel 5.7"
date: 2020-04-13
forum: Ubuntu Development Version
---

### Post by zika on 2020-04-13
```
:~$ uname -a
Linux **** 5.7.0-999-generic #202004122204 SMP Mon Apr 13 02:07:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
:~$ apt search 5.7|grep installed
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
linux-headers-5.7.0-050700rc1/now 5.7.0-050700rc1.202004122032 all [installed,local]
linux-headers-5.7.0-050700rc1-generic/now 5.7.0-050700rc1.202004122032 amd64 [installed,local]
linux-headers-5.7.0-999/now 5.7.0-999.202004122204 all [installed,local]
linux-headers-5.7.0-999-generic/now 5.7.0-999.202004122204 amd64 [installed,local]
linux-image-unsigned-5.7.0-050700rc1-generic/now 5.7.0-050700rc1.202004122032 amd64 [installed,local]
linux-image-unsigned-5.7.0-999-generic/now 5.7.0-999.202004122204 amd64 [installed,local]
linux-modules-5.7.0-050700rc1-generic/now 5.7.0-050700rc1.202004122032 amd64 [installed,local]
linux-modules-5.7.0-999-generic/now 5.7.0-999.202004122204 amd64 [installed,local]

```
It looks very nice. Seems that inode-tree bug has been (re)solved... Fast and stable... Smooth.

---

### Post by Doug S on 2020-04-27
Kernel 5.7-rc3 is [available]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7-rc3/").
I have only been running it a few minutes, so far.

On my 20.04 server computers, during boot, mainline kernels of recent (don't recall exactly when it started) have continued to spew stuff to the screen (I have grub set to show stuff during boot) after the login prompt. More just annoying than a real issue.

---

### Post by corradoventu on 2020-04-27
And I can see the temperature of my M2 storage
```
corrado@corrado-x2-focal:~$ uname -a
Linux corrado-x2-focal 5.7.0-050700rc3-generic #202004262131 SMP Sun Apr 26 21:34:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-x2-focal:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +33.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:        +32.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:        +32.0°C  (high = +80.0°C, crit = +100.0°C)

nvme-pci-0100
Adapter: PCI adapter
Composite:    +30.9°C  (low  =  -0.1°C, high = +74.8°C)
                       (crit = +79.8°C)

pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  

corrado@corrado-x2-focal:~$ 

```

---

### Post by zika on 2020-05-01
Any news why [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) stalled?

---

### Post by Doug S on 2020-05-04
> **zika said:**
> Any news why [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) stalled?No, and I there hasn't been anything on the kernel team IRC channel. I looked at the kernel team e-mail archives also and didn't find anything (which doesn't mean there isn't something relevant there, just that if there is, I didn't find it).

I was able to compile the upstream kernel yesterday, before the -rc4 tag, but it would have been close to -rc4.

Eventually, if the mainline builds don't return, I will ask about it on IRC.

---

### Post by zika on 2020-05-05
Thank You.

---

### Post by Doug S on 2020-05-05
> **Doug S said:**
> Eventually, if the mainline builds don't return, I will ask about it on IRC.The IRC channel doesn't seem to be used like it used to be. Still, there seems to be 134 people on the channel. I have inquired there.

EDIT: For unknown reasons the hourly irc logs update did not add the kernel channel. If it does catch up at some point the link should be: [https://irclogs.ubuntu.com/2020/05/05/%23ubuntu-kernel.html]("https://irclogs.ubuntu.com/2020/05/05/%23ubuntu-kernel.html") (currently 404 - not found).
EDIT 2: I do not understand why the Kernel team IRC was never added to the published logs, now it is even the next day (UTC), and it still thinks [the latest entry]("https://irclogs.ubuntu.com/latest/%23ubuntu-kernel.html") was March 14th. Anyway, no reply yet.
EDIT 3: Oh. [Kernel 5.7-rc4 is there]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.7-rc4/"), but the daily, current, next, ... are all still old.
EDIT 4: By accident, I went off the IRC channel last night. The published logs are still not updating, so I don't know if there was any related traffic. (it is also considered bad form not to wait around at least a day for any reply.)

---

### Post by zika on 2020-05-06
E pur si muove.
Thank You.
```
:~$ uname -a
Linux *.* 5.7.0-050700rc4-generic #202005051752 SMP Tue May 5 21:56:32 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
Update&#8321;: daily and drm-tip are there fresh new, again, so all is good. Thank You for all the help.

---

### Post by corradoventu on 2020-05-06
Also Gorilla with new kernel
```
corrado@corrado-p3-gorilla:~$ inxi -Sx
System:
  Host: corrado-p3-gorilla Kernel: 5.7.0-050700rc4-generic x86_64 bits: 64 
  compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.1 
  Distro: Ubuntu 20.10 (Groovy Gorilla) 
corrado@corrado-p3-gorilla:~$ 

```

---

### Post by Doug S on 2020-05-06
The problem with the mainline builds was (copied from IRC):

```
(11:37:19 AM) apw: dsmythies: tl;dr is the trigger process was hung, cleared up and they [mainline] have since been caught up
```

---

### Post by mrfelker on 2020-05-12
Kernel 5.7 rc5 is working well so on Kubuntu with the Ubuntu Gnome just added as an alternate desktop

---

### Post by mrfelker on 2020-05-17
Upgrade to kernel .7.0-050700rc6-generic comopletely without incident.   I am interested in whether the system freezing overnight when using Gnome desktop is improved.

---

### Post by zika on 2020-05-24
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
(994)drm-next:
```

  CC [M]  drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.o
/home/kernel/COD/linux/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c: In function 'amdgpu_amdkfd_gpuvm_free_memory_of_gpu':
/home/kernel/COD/linux/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c:1357:2: error: implicit declaration of function 'drm_gem_object_put_unlocked'; did you mean 'drm_gem_object_put_locked'? [-Werror=implicit-function-declaration]
 1357 |  drm_gem_object_put_unlocked(&mem->bo->tbo.base);
      |  ^~~~~~~~~~~~~~~~~~~~~~~~~~~
      |  drm_gem_object_put_locked
cc1: some warnings being treated as errors
make[6]: *** [/home/kernel/COD/linux/scripts/Makefile.build:267: drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.o] Error 1
make[5]: *** [/home/kernel/COD/linux/scripts/Makefile.build:488: drivers/gpu/drm/amd/amdgpu] Error 2
make[5]: *** Waiting for unfinished jobs....
  GEN     kernel/kheaders_data.tar.xz
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.build:488: drivers/gpu/drm] Error 2
make[3]: *** [/home/kernel/COD/linux/scripts/Makefile.build:488: drivers/gpu] Error 2
make[2]: *** [/home/kernel/COD/linux/Makefile:1729: drivers] Error 2
make[2]: *** Waiting for unfinished jobs....
  CC [M]  kernel/kheaders.o
make[2]: Leaving directory '/home/kernel/COD/linux/debian/build/build-generic'
make[1]: *** [Makefile:180: sub-make] Error 2
make[1]: Leaving directory '/home/kernel/COD/linux'
make: *** [debian/rules.d/2-binary-arch.mk:50: /home/kernel/COD/linux/debian/stamps/stamp-build-generic] Error 2
```For few days it did not come even here... ;)
(999)daily is OK.

---

### Post by Doug S on 2020-05-24
> **zika said:**
> [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
(994)drm-next:
For few days it did not come even here... ;)
(999)daily is OK.Related to this commit:

```
doug@s15:~/temp-k-git/linux$ git show 39b3128d7ffd
commit 39b3128d7ffd44e400e581e6f49e88cb42bef9a1
Author: Felix Kuehling <Felix.Kuehling@amd.com>
Date:   Tue May 5 14:02:43 2020 -0400

    drm/amdgpu: Use GEM obj reference for KFD BOs

    Releasing the AMDGPU BO ref directly leads to problems when BOs were
    exported as DMA bufs. Releasing the GEM reference makes sure that the
    AMDGPU/TTM BO is not freed too early.

    Also take a GEM reference when importing BOs from DMABufs to keep
    references to imported BOs balances properly.

    Signed-off-by: Felix Kuehling <Felix.Kuehling@amd.com>
    Tested-by: Alex Sierra <alex.sierra@amd.com>
    Acked-by: Christian König <christian.koenig@amd.com>
    Reviewed-by: Alex Sierra <alex.sierra@amd.com>
    Signed-off-by: Alex Deucher <alexander.deucher@amd.com>

diff --git a/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c b/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c
index 9dff792c9290..6a5b91d23fd9 100644
--- a/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c
+++ b/drivers/gpu/drm/amd/amdgpu/amdgpu_amdkfd_gpuvm.c
@@ -1343,7 +1343,7 @@ int amdgpu_amdkfd_gpuvm_free_memory_of_gpu(
        }

        /* Free the BO*/
-       amdgpu_bo_unref(&mem->bo);
+       drm_gem_object_put_unlocked(&mem->bo->tbo.base);
        mutex_destroy(&mem->lock);
        kfree(mem);

@@ -1688,7 +1688,8 @@ int amdgpu_amdkfd_gpuvm_import_dmabuf(struct kgd_dev *kgd,
                | KFD_IOC_ALLOC_MEM_FLAGS_WRITABLE
                | KFD_IOC_ALLOC_MEM_FLAGS_EXECUTABLE;

-       (*mem)->bo = amdgpu_bo_ref(bo);
+       drm_gem_object_get(&bo->tbo.base);
+       (*mem)->bo = bo;
        (*mem)->va = va;
        (*mem)->domain = (bo->preferred_domains & AMDGPU_GEM_DOMAIN_VRAM) ?
                AMDGPU_GEM_DOMAIN_VRAM : AMDGPU_GEM_DOMAIN_GTT;

```And I observe that commit being picked up by [downstream maintainers]("https://lkml.org/lkml/2020/5/22/602").
I could not find if this was a fix for something else or something was done to fix what you observed in the 994 build, but I did observe some amdgpu related mode changes/deletions in my git pull. I am not knowledgeable enough with git go further, short of trying a compile right at commit  39b3128d7ffd (which I am not going to do, even though I am curious, I just don't have the time).

---

### Post by corradoventu on 2020-05-27
Last RC announced for kernel 5.7 [http://lkml.iu.edu/hypermail/linux/kernel/2005.3/00406.html](http://lkml.iu.edu/hypermail/linux/kernel/2005.3/00406.html)

---

