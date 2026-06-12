---
title: "Linux 3.8-rc1"
date: 2012-12-21
forum: Ubuntu Development Version
---

### Post by wnelson on 2012-12-21
Is now available,


[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc1-raring/)

Walt

---

### Post by VinDSL on 2012-12-21
I just installed 3.8-rc1... sort of.  LoL! :D

Got some kind of dkms failure going on.

Unity & GS were no shows, but LXDE is working.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-dec-2012-4(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-dec-2012-4.png")[/INDENT]


I need to go back through the logs, and do some forensics...  ;)

---

### Post by cariboo on 2012-12-22
It looks like we are making some progress here, I can boot from this kernel, but Unity won't start, and compiz keeps crashing. I also had a dkms problem, with nvidia-current-updates not installing properly. Yay. :-D

**Edit:** I successfully booted into gnome-shell after removing nvidia-current-updates, using 3.8-rc1

---

### Post by zika on 2012-12-22
Got kernel panic with Unity...
Got kernel panic (it seems) without Unity...
Booted with```
text noapic nolapic noacpi
```and will try to get one by one from kernel line...
Startx rules...
But it is fast... And frugal with memory...
Yes, it can boot without any of no* but it hates compiz... Same thing with gnome-session and Unity... Gnome-session-fallback works OK... Also dwm spectrwm fvwm...
Yes, the only thing it hates is compiz...
Nope, it needs noapic,nolapic... Stallion...
As I said stallion, it's just a question of time until kernel panics...
Update&#8321;: It doesn't seem to like my tweaks about latency, dynpm, hugepage... We'll see...

---

### Post by jppr on 2012-12-22
Yep :D This kernel works FINALLY me too, without ANY PROBLEMS, HUH :popcorn:
No, Compiz or Unity problems = )

---

### Post by VinDSL on 2012-12-22
> **cariboo907 said:**
> I also had a dkms problem, with nvidia-current-updates not installing properly. Yay. :-D
Heh!  Same ol' story, here...

Checked: /var/lib/dkms/nvidia-current-updates/304.64/build/make.log

Bottom line:  3.8-rc1 doesn't recognize nvidia-current 304.64 **[EDIT]** Or, vice-versa.

I'll need to check my "Tomboy Notes", and see what the workaround was.

If memory serves, I installed nVidia proprietary drivers.

Unfortunately, I won't be able to get to it until this afternoon.

Anyway, nvidia-current problems are preferable to kernel panics, eh what, Zika?  :D

---

### Post by zika on 2012-12-22
> **VinDSL said:**
> Anyway, nvidia-current problems are preferable to kernel panics, eh what, Zika?  :DJust another day on playground... ;)
[http://www.youtube.com/watch?v=kDTHy-b5nqE](http://www.youtube.com/watch?v=kDTHy-b5nqE)

---

### Post by ventrical on 2012-12-22
A beautiful, seamless install here. Unity , up and at em' . :)

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)

---

### Post by ventrical on 2012-12-22
> **zika said:**
> Just another day on playground... ;)
[http://www.youtube.com/watch?v=kDTHy-b5nqE](http://www.youtube.com/watch?v=kDTHy-b5nqE)


That is an excellent depiction of how I see Unity3D Ubuntu Desktop works!:) Effortlessly, but with a lot of hard work in the background.

Bravo..

---

### Post by Yahoé on 2012-12-22
3.8-rc1 installed and Unity worked for me (Ati Radeon HD4250) but my AR922X Wireless Network Adapter wasn't detected.

---

### Post by JMB74 on 2012-12-22
> **Yahoé said:**
> 3.8-rc1 installed and Unity worked for me (Ati Radeon HD4250) but my AR922X Wireless Network Adapter wasn't detected.

Looking at the modules built and configs, a lot of wireless stuff wasn't built on that kernel due to missing entries in the configs. Looks like someone messed up configuring and building that kernel.

---

### Post by Milos_SD on 2012-12-22
Did anyone of you made a patch for nvidia binary?

I get this errors when I try to install v313.09
[http://pastebin.com/F30rJLmC](http://pastebin.com/F30rJLmC)

---

### Post by ronacc on 2012-12-22
I think they have applied the patches now , I was not able to boot ANY 3.7 kernel but the 3.8 rc1 booted right up and is running the nvidia 304.43 package .

---

### Post by Milos_SD on 2012-12-22
Then what is the problem with my configuration? Here is my kernel configuration: [http://pastebin.com/bmbdm6zr](http://pastebin.com/bmbdm6zr)

---

### Post by paul_in_london on 2012-12-22
> **ronacc said:**
> I think they have applied the patches now , I was not able to boot ANY 3.7 kernel but the 3.8 rc1 booted right up and is running the nvidia 304.43 package .

I'm using nvidia-current-updates (my graphics card isn't supported by nvidia-current unfortunately):

```
paul@lubuntu-64:~$ apt-cache policy nvidia-current-updates
nvidia-current-updates:
  Installed: **[COLOR="Red"]304.64-0ubuntu1[/COLOR]**
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted amd64 Packages
        100 /var/lib/dpkg/status
paul@lubuntu-64:~$
```

No problems with the 3.7 kernels, but for me the nvidia module fails to build with 3.8-rc1 or the daily. Haven't tried downgrading nvidia-current-updates. Will hold out for a newer version of this nvidia driver...

---

### Post by ronacc on 2012-12-22
I am not running the nvidia-updates so my version is 304.43  .

---

### Post by paul_in_london on 2012-12-22
> **ronacc said:**
> I am not running the nvidia-updates so my version is 304.43  .

Thanks ronacc - yes, I noticed that your driver version wasn't the same as mine! :smile:

---

### Post by mc4man on 2012-12-22
> **Milos_SD said:**
> Did anyone of you made a patch for nvidia binary?

I get this errors when I try to install v313.09
[http://pastebin.com/F30rJLmC](http://pastebin.com/F30rJLmC)
See the same with 3.8.0-030800rc1 & nvidia-current-updates (304.64

3.8.0-030800rc1 & nvidia-experimental-310 work fine (using 310.14-0ubuntu1

edit: actually see the same in the 310 make.log which builds fine...

---

### Post by Milos_SD on 2012-12-22
Strange, a patch that was used for pre-310.xx versions for 3.7 kernel worked. Driver 313.09 without that patch compiles on 3.7 and 3.7.1 kernel (and -rcX before that), but it needs that patch on 3.8-rc1. I looked at conftest.sh file, and the patch is integrated by nvidia, but on a little diffrent way than in is implemented in a actual patch I used.

---

### Post by cariboo on 2012-12-22
I've been using nvidia-current-update for the last few kernels, as that is all that would work on my system, but today I tried to install it, and it failed. Nvidia-current installed and is running with zero problems.

---

### Post by rrnbtter on 2012-12-22
Greetings,
Just follow Ventrical's lead on the 3.7 kernel I install 3.8 in Lucid.
rrnbtter-laptop:~$ cat /proc/version
Linux version 3.8.0-030800rc1-generic (root@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201212212135 SMP Sat Dec 22 02:45:41 UTC 2012

Everything was fast and working except that I didn't have any drivers for my Atheros WIFI, nor my US Cellular USB modem. 

After rebooting to my 2.6 kernel and doing some research on the internet. I rebooted back to the 3.8 kernel but had a boot failure do to a failed Home dir scan.  I put my RR harddrive back in my computer and I can access the Home dir on the Lucid drive just fine with my USB adapter.  So I may wait for an update on the kernel and give it another go.
FYI

---

### Post by rrnbtter on 2012-12-22
Greetings,

Well, when I rebooted my RR partition I plugged my Lucid disk into a USB port and it had a single bad sector. Now boots fine from the USB port into both 2.6 and 3.8 kernels.

rrnbtter-laptop:~$ cat /proc/version
Linux version 3.8.0-030800rc1-generic (root@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201212212135 SMP Sat Dec 22 02:45:41 UTC 2012

rrnbtter-laptop:~$ cat /proc/version
Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010

Other than no internet everything is working with no errors so far.

---

### Post by paul_in_london on 2012-12-22
Since I have to stick with the nvidia 304.x series, this is what worked for me.

[LIST=1]
[*]Purged nvidia-current-updates
[*]Installed nvidia-current
[*]Downgraded nvidia-current to the previous version
[*]Locked nvidia-current via synaptic and:
   ```
$ sudo -s
# echo nvidia-current hold | dpkg --set-selections
```
[/LIST]

```
paul@lubuntu-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu2
  Candidate: 313.09-0ubuntu1~xedgers~raring1
  Version table:
     313.09-0ubuntu1~xedgers~raring1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ raring/main amd64 Packages
 *** 304.51.really.304.43-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/restricted amd64 Packages
        100 /var/lib/dpkg/status
paul@lubuntu-64:~$
```

```
paul@lubuntu-64:~$ uname -a
Linux lubuntu-64 3.8.0-030800rc1-generic #201212212135 SMP Sat Dec 22 02:36:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

---

### Post by ventrical on 2012-12-22
I just installed the new kernel on:
amd64bit on Intel

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```raring ringtail , fully updated and this time around it dropped my USB wireless, so I had to plugg in my eth0 cable. Works great on other kernels.

I'll try an update.

---

### Post by ronacc on 2012-12-22
just FYI , my wireless is working fine with 3.8 rc1 , I have a realtek 8185 chip .

---

### Post by ventrical on 2012-12-22
> **rrnbtter said:**
> Greetings,

Well, when I rebooted my RR partition I plugged my Lucid disk into a USB port and it had a single bad sector. Now boots fine from the USB port into both 2.6 and 3.8 kernels.

rrnbtter-laptop:~$ cat /proc/version
Linux version 3.8.0-030800rc1-generic (root@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201212212135 SMP Sat Dec 22 02:45:41 UTC 2012

rrnbtter-laptop:~$ cat /proc/version
Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010

Other than no internet everything is working with no errors so far.

Thanks for this info.  I am about to install the 3.8RC on Lucid.  It works great except it has this funky bug with nvidia-96 drivers, but it is very stable , (no graphics) and a lot faster GNOME.  I am doing this experiment with these newer kernels with the hopes of dragging something out of Lucid that I can bring up into Raring :)

---

### Post by manulemaboul on 2012-12-22
After failing to boot all the 3.6.x and 3.7.x, 3.8.0 RC1 booted woohoo.

Now I'm struggling to get an nvidia driver that works with it. Wich one is actually working ?
Tried reverting to 304.43 but it fails to build for 3.8.0.

---

### Post by ronacc on 2012-12-22
nvidia-current is working for me NOT the nvidia-current-updates .

---

### Post by manulemaboul on 2012-12-22
313.09 ?

Building initial module for 3.8.0-030800rc1-generic
ERROR (dkms apport): kernel package linux-headers-3.8.0-030800rc1-generic is not supported
Error! Bad return status for module build on kernel: 3.8.0-030800rc1-generic (i686)

:/.

---

### Post by ronacc on 2012-12-22
304.43 in synaptic it is labeled 304.51  .

---

### Post by manulemaboul on 2012-12-22
I know, that's the one I tried and it failed to build for 3.8.0.

---

### Post by VinDSL on 2012-12-22
Alrighty, then!  I'm finally in!

Heh!  Seems like everybody is taking a different path.  :D

I had to install & patch nvidia-current 304.51, then re-install 3.8-rc1...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-22-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-dec-2012-1.png")[/INDENT]


I'm extremely pleased with the low CPU usage in 3.8-rc1.

Can't remember ever seeing Unity use so few resources...

---

### Post by manulemaboul on 2012-12-22
Would you mind providing me the patch you used and a brief "how to" please ? :)

---

### Post by ventrical on 2012-12-22
Nice work VinDSL ! :)

  I was getting so bored that I had to try the 3.8RC on a Lucid install.. lol:) I finally figured it out. First, do fresh install of Lucid. (don't update) then grab a few things from synaptic. Then install the 3.8RC kernel!! Result ? Turbo_Lucid on the RR kernel.

It's like using the new Raring Ringtail kernel as a core_frame_work and running Lucid as a virtual machine on it.  I'm having a riot:)

lol

Also it split my hypethreading 2.8GHz processor into a virtual dual-core!!:)

---

### Post by cariboo on 2012-12-22
I'm quite happy with the way things are running on my system now with the 3.8 kernel and nvidia-current 304.43.

Now it's time to sort out the problem on my netbook with network-manager using 90%+ cpu resources, when the bcmwl-kernel-source driver is installed. :-D

---

### Post by manulemaboul on 2012-12-22
Somebody could explain me how to make the 304.43 works please ?
It seems to need a patch, but I can't find it.

---

### Post by cariboo on 2012-12-22
> **manulemaboul said:**
> Somebody could explain me how to make the 304.43 works please ?
It seems to need a patch, but I can't find it.

I tried nvidia-current-updates first, but that didn't work, so I used aptitude purge to remove it and nvidia-settings-updates:

```
sudo aptitude purge nvidia-current-updates nvidia-settings-updates
```

then used:

```
sudo aptitude install nvidia-current nvidia-settings
```

and rebooted. No patches were needed.

---

### Post by manulemaboul on 2012-12-22
I've purged between each, tested current, current-updates, experimental-310 and current forced to 304.43.
The only time X server started was without any driver. 

I think I'll have to wait for an updated driver. At least I'm not stucked with 3.5.7 kernel anymore and this time I know what's going on:).
Weeks and weeks testing and searching to find out why kernel 3.6.x and 3.7 won't boot without finding any clue, that was driving me crazy.

---

### Post by VinDSL on 2012-12-23
> **manulemaboul said:**
> Would you mind providing me the patch you used and a brief "how to" please ? :)
Sure, if you don't mind a "rough overview".  I've only slept 2 hours, in the past 24, and I'm getting punchy.  LoL!  :D

Basically, I replicated what I did with 3.7-rc1, and it worked, again.

Reading the posts (starting here) might help:  [http://ubuntuforums.org/showthread.php?p=12342761](http://ubuntuforums.org/showthread.php?p=12342761)

For the most part...

I installed 3.8-rc1, then booted into it.

I logged into Unity, and was met with a "blank canvas" (no nVidia, Mesa, et cetera).

From CLI (alt-ctrl-t), I tried installing every nVidia driver which was stored on my HDD.  Some of them installed, some of them didn't, but 3.8-rc1 didn't care for any of them (fatal dkms errors).

Since I've had good luck with the edger's 304.51 drivers, in the past, I decided to go that route.

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  **[COLOR="Red"]Installed: 304.51-0ubuntu1~xedgers~quantal1[/COLOR]**
  Candidate: 313.09-0ubuntu1~xedgers~quantal1

```


Alternately, the patches *may* work on the official Ubu PPA 304.51 release (never tried it).  :)

Anyway, I installed edger's 304.51 nVidia drivers and patched the following two files.


**/usr/src/nvidia-current-304.51/nv-mmap.c**
```

/* _NVRM_COPYRIGHT_BEGIN_
 *
 * Copyright 1999-2011 by NVIDIA Corporation.  All rights reserved.  All
 * information contained herein is proprietary and confidential to NVIDIA
 * Corporation.  Any use, reproduction, or disclosure without the written
 * permission of NVIDIA Corporation is prohibited.
 *
 * _NVRM_COPYRIGHT_END_
 */

#define  __NO_VERSION__
#include "nv-misc.h"

#include "os-interface.h"
#include "nv-linux.h"

/*
 * The 'struct vm_operations' open() callback is called by the Linux
 * kernel when the parent VMA is split or copied, close() when the
 * current VMA is about to be deleted.
 *
 * We implement these callbacks to keep track of the number of user
 * mappings of system memory allocations. This was motivated by a
 * subtle interaction problem between the driver and the kernel with
 * respect to the bookkeeping of pages marked reserved and later
 * mapped with mmap().
 *
 * Traditionally, the Linux kernel ignored reserved pages, such that
 * when they were mapped via mmap(), the integrity of their usage
 * counts depended on the reserved bit being set for as long as user
 * mappings existed.
 *
 * Since we mark system memory pages allocated for DMA reserved and
 * typically map them with mmap(), we need to ensure they remain
 * reserved until the last mapping has been torn down. This worked
 * correctly in most cases, but in a few, the RM API called into the
 * RM to free memory before calling munmap() to unmap it.
 *
 * In the past, we allowed nv_free_pages() to remove the 'at' from
 * the parent device's allocation list in this case, but didn't
 * release the underlying pages until the last user mapping had been
 * destroyed:
 *
 * In nv_kern_vma_release(), we freed any resources associated with
 * the allocation (IOMMU/SWIOTLB mappings, etc.) and cleared the
 * underlying pages' reserved bits, but didn't free them. The kernel
 * was expected to do this.
 *
 * This worked in practise, but made dangerous assumptions about the
 * kernel's behavior and could fail in some cases. We now handle
 * this case differently (see below).
 */
static void
nv_kern_vma_open(struct vm_area_struct *vma)
{
    NV_PRINT_VMA(NV_DBG_MEMINFO, vma);

    if (NV_VMA_PRIVATE(vma))
    {
        nv_alloc_t *at = (nv_alloc_t *)NV_VMA_PRIVATE(vma);
        NV_ATOMIC_INC(at->usage_count);

        if (!NV_ALLOC_MAPPING_AGP(at->flags))
        {
            NV_PRINT_AT(NV_DBG_MEMINFO, at);
            nv_vm_list_page_count(at->page_table, at->num_pages);
        }
    }
}

/*
 * (see above for additional information)
 *
 * If the 'at' usage count drops to zero with the updated logic, the
 * VMA's file pointer is saved; nv_kern_close() uses it to find
 * these allocations when the parent file descriptor is closed. This
 * will typically happen when the process exits.
 *
 * Since this is technically a workaround to handle possible fallout
 * from misbehaving clients, we addtionally print a warning.
 */
static void
nv_kern_vma_release(struct vm_area_struct *vma)
{
    NV_PRINT_VMA(NV_DBG_MEMINFO, vma);

    if (NV_VMA_PRIVATE(vma))
    {
        nv_alloc_t *at = (nv_alloc_t *) NV_VMA_PRIVATE(vma);

        if (NV_ATOMIC_DEC_AND_TEST(at->usage_count))
        {
            static int count = 0;
            if ((at->pid == os_get_current_process()) &&
                (count++ < NV_MAX_RECURRING_WARNING_MESSAGES))
            {
                nv_printf(NV_DBG_MEMINFO,
                    "NVRM: VM: %s: late unmap, comm: %s, 0x%p\n",
                    __FUNCTION__, current->comm, at);
            }
            at->file = NV_VMA_FILE(vma);
        }

        if (!NV_ALLOC_MAPPING_AGP(at->flags))
        {
            NV_PRINT_AT(NV_DBG_MEMINFO, at);
            nv_vm_list_page_count(at->page_table, at->num_pages);
        }
    }
}

#if !defined(NV_VM_INSERT_PAGE_PRESENT)
static
struct page *nv_kern_vma_nopage(
    struct vm_area_struct *vma,
    unsigned long address,
#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 1))
    int *type
#else
    int write_access
#endif
)
{
    struct page *page;

    page = pfn_to_page(vma->vm_pgoff);
    get_page(page);

    return page;
}
#endif

struct vm_operations_struct nv_vm_ops = {
    .open   = nv_kern_vma_open,
    .close  = nv_kern_vma_release,
#if !defined(NV_VM_INSERT_PAGE_PRESENT)
    .nopage = nv_kern_vma_nopage,
#endif
};

int nv_encode_caching(
    pgprot_t *prot,
    NvU32     cache_type,
    NvU32     memory_type
)
{
    pgprot_t tmp;

    if (prot == NULL)
    {
        tmp = __pgprot(0);
        prot = &tmp;
    }

    switch (cache_type)
    {
        case NV_MEMORY_UNCACHED_WEAK:
#if defined(NVCPU_X86) || defined(NVCPU_X86_64)
            *prot = pgprot_noncached_weak(*prot);
            break;
#endif
        case NV_MEMORY_UNCACHED:
            *prot = pgprot_noncached(*prot);
            break;
#if defined(NVCPU_X86) || defined(NVCPU_X86_64)
        case NV_MEMORY_WRITECOMBINED:
#if defined(NV_ENABLE_PAT_SUPPORT)
            if ((nv_pat_mode != NV_PAT_MODE_DISABLED) &&
                    (memory_type != NV_MEMORY_TYPE_REGISTERS))
            {
                pgprot_val(*prot) &= ~(_PAGE_PSE | _PAGE_PCD | _PAGE_PWT);
                *prot = __pgprot(pgprot_val(*prot) | _PAGE_PWT);
                break;
            }
#endif
            /*
             * If PAT support is unavailable and the memory space isn't
             * NV_MEMORY_TYPE_AGP, we need to return an error code to
             * the caller, but do not print a warning message.
             *
             * In the case of AGP memory, we will have attempted to add
             * a WC MTRR for the AGP aperture and aborted the AGP
             * initialization if this failed, so we can safely return
             * success here.
             *
             * For frame buffer memory, callers are expected to use the
             * UC- memory type if we report WC as unsupported, which
             * translates to the effective memory type WC if a WC MTRR
             * exists or else UC.
             */
            if (memory_type == NV_MEMORY_TYPE_AGP)
                break;
            return 1;
#elif defined(NVCPU_ARM)
        case NV_MEMORY_WRITECOMBINED:
            *prot = pgprot_writecombine(*prot);
            break;
#endif
        case NV_MEMORY_CACHED:
#if !defined(NVCPU_X86) && !defined(NVCPU_X86_64)
            if (memory_type != NV_MEMORY_TYPE_REGISTERS)
                break;
#else
            /*
             * RAM is cached on Linux by default, we can assume there's
             * nothing to be done here. This is not the case for the
             * other memory spaces: as commented on above, we will have
             * added a WC MTRR for the AGP aperture (or else aborted
             * AGP initialization), and we will have made an attempt to
             * add a WC MTRR for the frame buffer.
             *
             * If a WC MTRR is present, we can't satisfy the WB mapping
             * attempt here, since the achievable effective memory
             * types in that case are WC and UC, if not it's typically
             * UC (MTRRdefType is UC); we could only satisfy WB mapping
             * requests with a WB MTRR.
             */
            if (memory_type == NV_MEMORY_TYPE_SYSTEM)
                break;
#endif
        default:
            nv_printf(NV_DBG_ERRORS,
                "NVRM: VM: cache type %d not supported for memory type %d!\n",
                cache_type, memory_type);
            return 1;
    }
    return 0;
}

int nv_kern_mmap(
    struct file *file,
    struct vm_area_struct *vma
)
{
    unsigned int pages;
    nv_alloc_t *at;
    nv_linux_state_t *nvl = NV_GET_NVL_FROM_FILEP(file);
    nv_state_t *nv = NV_STATE_PTR(nvl);
    nv_file_private_t *nvfp = NV_GET_FILE_PRIVATE(file);
    RM_STATUS rmStatus;
    int status = 0;
    nv_stack_t *sp = NULL;
    NvU32 prot;

    if (nv->flags & NV_FLAG_CONTROL)
        return -ENODEV;

    NV_PRINT_VMA(NV_DBG_MEMINFO, vma);

    down(&nvfp->fops_sp_lock[NV_FOPS_STACK_INDEX_MMAP]);
    sp = nvfp->fops_sp[NV_FOPS_STACK_INDEX_MMAP];

    NV_CHECK_PCI_CONFIG_SPACE(sp, nv, TRUE, TRUE, NV_MAY_SLEEP());

    pages = NV_VMA_SIZE(vma) >> PAGE_SHIFT;
    NV_VMA_PRIVATE(vma) = NULL;

    vma->vm_ops = &nv_vm_ops;

    rmStatus = rm_validate_mmap_request(sp, nv, NV_VMA_OFFSET(vma),
            NV_VMA_SIZE(vma), &prot);
    if (rmStatus != RM_OK)
    {
        status = -EINVAL;
        goto done;
    }

    if ((prot & NV_PROTECT_WRITEABLE) == 0)
    {
#if defined(NVCPU_X86) || defined(NVCPU_X86_64)
        pgprot_val(vma->vm_page_prot) &= ~_PAGE_RW;
#endif
        vma->vm_flags &= ~VM_WRITE;
        vma->vm_flags &= ~VM_MAYWRITE;
    }

    if (IS_REG_OFFSET(nv, NV_VMA_OFFSET(vma), NV_VMA_SIZE(vma)))
    {
        if (nv_encode_caching(&vma->vm_page_prot,
                              NV_MEMORY_UNCACHED,
                              NV_MEMORY_TYPE_REGISTERS))
        {
            status = -ENXIO;
            goto done;
        }

        if (NV_IO_REMAP_PAGE_RANGE(vma->vm_start, NV_VMA_OFFSET(vma),
                    NV_VMA_SIZE(vma), vma->vm_page_prot))
        {
            status = -EAGAIN;
            goto done;
        }

        vma->vm_flags |= VM_IO;
    }
    else if (IS_FB_OFFSET(nv, NV_VMA_OFFSET(vma), NV_VMA_SIZE(vma)))
    {
        if (IS_UD_OFFSET(nv, NV_VMA_OFFSET(vma), NV_VMA_SIZE(vma)))
        {
            if (nv_encode_caching(&vma->vm_page_prot,
                                      NV_MEMORY_UNCACHED,
                                      NV_MEMORY_TYPE_FRAMEBUFFER))
            {
                status = -ENXIO;
                goto done;
            }
        }
        else if (nv_encode_caching(&vma->vm_page_prot,
                                   NV_MEMORY_WRITECOMBINED,
                                   NV_MEMORY_TYPE_FRAMEBUFFER))
        {
            if (nv_encode_caching(&vma->vm_page_prot,
                                  NV_MEMORY_UNCACHED_WEAK,
                                  NV_MEMORY_TYPE_FRAMEBUFFER))
            {
                status = -ENXIO;
                goto done;
            }
        }

        if (NV_IO_REMAP_PAGE_RANGE(vma->vm_start, NV_VMA_OFFSET(vma),
                    NV_VMA_SIZE(vma), vma->vm_page_prot))
        {
            status = -EAGAIN;
            goto done;
        }

        vma->vm_flags |= VM_IO;
    }
#if defined(NVCPU_X86) || defined(NVCPU_X86_64)
    else if (IS_AGP_OFFSET(nv, NV_VMA_OFFSET(vma), NV_VMA_SIZE(vma)))
    {
        NvU32 i;

        down(&nvl->at_lock);
        at = nv_find_alloc(nvl, NV_VMA_OFFSET(vma), NV_ALLOC_TYPE_AGP);

        if (at == NULL)
        {
            static int count = 0;
            if (count++ < NV_MAX_RECURRING_WARNING_MESSAGES)
            {
                nv_printf(NV_DBG_ERRORS,
                    "NVRM: %s: invalid offset: 0x%08x @ 0x%016llx (AGP)\n",
                    __FUNCTION__, NV_VMA_SIZE(vma),
                    NV_VMA_OFFSET(vma));
            }
            up(&nvl->at_lock);
            status = -EINVAL;
            goto done;
        }

        if (nv_encode_caching(&vma->vm_page_prot,
                              NV_MEMORY_WRITECOMBINED,
                              NV_MEMORY_TYPE_AGP))
        {
            up(&nvl->at_lock);
            status = -ENXIO;
            goto done;
        }

        NV_VMA_PRIVATE(vma) = at;
        NV_ATOMIC_INC(at->usage_count);
        up(&nvl->at_lock);

        if (NV_IO_REMAP_PAGE_RANGE(vma->vm_start, NV_VMA_OFFSET(vma),
                    NV_VMA_SIZE(vma), vma->vm_page_prot))
        {
            NV_ATOMIC_DEC(at->usage_count);
            status = -EAGAIN;
            goto done;
        }

        i = ((NV_VMA_OFFSET(vma) - at->key) >> PAGE_SHIFT);

        NV_PRINT_AT(NV_DBG_MEMINFO, at);
        nv_vm_list_page_count(&at->page_table[i], pages);

        vma->vm_flags |= VM_IO;
    }
#endif
    else
    {
        unsigned long start = 0;
        unsigned int i, j;

        down(&nvl->at_lock);
        at = nv_find_alloc(nvl, NV_VMA_OFFSET(vma), NV_ALLOC_TYPE_PCI);

        if (at == NULL)
        {
            static int count = 0;
            up(&nvl->at_lock);
            if (count++ < NV_MAX_RECURRING_WARNING_MESSAGES)
            {
                nv_printf(NV_DBG_ERRORS,
                    "NVRM: %s: invalid offset: 0x%08x @ 0x%016llx (PCI)\n",
                    __FUNCTION__, NV_VMA_SIZE(vma),
                    NV_VMA_OFFSET(vma));
            }
            status = -EINVAL;
            goto done;
        }

        for (i = 0; i < at->num_pages; i++)
        {
            if ((NV_VMA_OFFSET(vma) == at->page_table[i]->phys_addr) ||
                (NV_VMA_OFFSET(vma) == at->page_table[i]->dma_addr))
            {
                break;
            }
        }

        if (i == at->num_pages)
        {
            up(&nvl->at_lock);
            status = -EINVAL;
            goto done;
        }

        if ((i + pages) > at->num_pages)
        {
            nv_printf(NV_DBG_ERRORS,
                "NVRM: requested mapping exceeds allocation's boundary!\n");
            up(&nvl->at_lock);
            status = -EINVAL;
            goto done;
        }

        if (nv_encode_caching(&vma->vm_page_prot,
                              NV_ALLOC_MAPPING(at->flags),
                              NV_MEMORY_TYPE_SYSTEM))
        {
            up(&nvl->at_lock);
            status = -ENXIO;
            goto done;
        }

        NV_VMA_PRIVATE(vma) = at;
        NV_ATOMIC_INC(at->usage_count);
        up(&nvl->at_lock);

        start = vma->vm_start;
        for (j = i; j < (i + pages); j++)
        {
            nv_verify_page_mappings(at->page_table[j],
                    NV_ALLOC_MAPPING(at->flags));
#if defined(NV_VM_INSERT_PAGE_PRESENT)
            if (NV_VM_INSERT_PAGE(vma, start,
                    NV_GET_PAGE_STRUCT(at->page_table[j]->phys_addr)))
#else
            if (NV_REMAP_PAGE_RANGE(start, at->page_table[j]->phys_addr,
                    PAGE_SIZE, vma->vm_page_prot))
#endif
            {
                NV_ATOMIC_DEC(at->usage_count);
                status = -EAGAIN;
                goto done;
            }
            start += PAGE_SIZE;
        }

        NV_PRINT_AT(NV_DBG_MEMINFO, at);
        nv_vm_list_page_count(&at->page_table[i], pages);

        vma->vm_flags |= (VM_IO | VM_LOCKED | (VM_DONTEXPAND | VM_DONTDUMP));

#if defined(VM_DRIVER_PAGES)
        vma->vm_flags |= VM_DRIVER_PAGES;
#endif
    }

    NV_VMA_FILE(vma) = file;

done:
    up(&nvfp->fops_sp_lock[NV_FOPS_STACK_INDEX_MMAP]);
    return status;
}

```


**/usr/src/nvidia-current-304.51/conftest.sh**
```

#!/bin/sh

# make sure we are in the directory containing this script
SCRIPTDIR=`dirname $0`
cd $SCRIPTDIR
PATH="${PATH}:/bin:/sbin"

#
# HOSTCC vs. CC - if a conftest needs to build and execute a test
# binary, like get_uname, then $HOSTCC needs to be used for this
# conftest in order for the host/build system to be able to execute
# it in X-compile environments.
# In all other cases, $CC should be used to minimize the risk of
# false failures due to conflicts with architecture specific header
# files.
#
CC="$1"
HOSTCC="$2"
ARCH=$3
ISYSTEM=`$CC -print-file-name=include 2> /dev/null`
SOURCES=$4
HEADERS=$SOURCES/include
HEADERSA=$SOURCES/include/uapi
OUTPUT=$5
XEN_PRESENT=1

test_xen() {
    #
    # Determine if the target kernel is a Xen kernel. It used to be
    # sufficient to check for CONFIG_XEN, but the introduction of
    # modular para-virtualization (CONFIG_PARAVIRT, etc.) and
    # Xen guest support, it is no longer possible to determine the
    # target environment at build time. Therefore, if both
    # CONFIG_XEN and CONFIG_PARAVIRT are present, text_xen() treats
    # the kernel as a stand-alone kernel.
    #
    OLD_FILE="linux/autoconf.h"
    NEW_FILE="generated/autoconf.h"

    if [ -f $HEADERS/$NEW_FILE -o -f $OUTPUT/include/$NEW_FILE ]; then
        FILE=$NEW_FILE
    fi
    if [ -f $HEADERS/$OLD_FILE -o -f $OUTPUT/include/$OLD_FILE ]; then
        FILE=$OLD_FILE
    fi

    if [ -n "$FILE" ]; then
        #
        # We are looking at a configured source tree; verify
        # that it's not a Xen kernel.
        #
        echo "#include <$FILE>
        #if defined(CONFIG_XEN) && !defined(CONFIG_PARAVIRT)
        #error CONFIG_XEN defined!
        #endif
        " > conftest$$.c

        $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
        rm -f conftest$$.c

        if [ -f conftest$$.o ]; then
            rm -f conftest$$.o
            XEN_PRESENT=0
        fi
    else
        CONFIG=$HEADERS/../.config
        if [ -f $CONFIG ]; then
            if [ -z "$(grep "^CONFIG_XEN=y" $CONFIG)" ]; then
                XEN_PRESENT="0"
                return
            fi
            if [ -n "$(grep "^CONFIG_PARAVIRT=y" $CONFIG)" ]; then
                XEN_PRESENT="0"
            fi
        fi
    fi
}

test_headers() {
    #
    # Determine which header files (of a set that may or may not be
    # present) are provided by the target kernel.
    #
    FILES="asm/system.h"
    FILES="$FILES generated/autoconf.h"
    FILES="$FILES generated/compile.h"
    FILES="$FILES generated/utsrelease.h"
    FILES="$FILES linux/kconfig.h"
    FILES="$FILES linux/screen_info.h"
    FILES="$FILES linux/semaphore.h"

    for FILE in $FILES; do
        FILE_DEFINE=NV_`echo $FILE | tr '/.' '_' | tr 'a-z' 'A-Z'`_PRESENT
        if [ -f $HEADERS/$FILE -o -f $OUTPUT/include/$FILE ]; then
            echo "#define $FILE_DEFINE" >> conftest.h
        else
            echo "#undef $FILE_DEFINE" >> conftest.h
        fi
    done
}

build_cflags() {
    BASE_CFLAGS="-O2 -D__KERNEL__ \
-DKBUILD_BASENAME=\"#conftest$$\" -DKBUILD_MODNAME=\"#conftest$$\" \
-nostdinc -isystem $ISYSTEM"

    if [ "$OUTPUT" != "$SOURCES" ]; then
        OUTPUT_CFLAGS="-I$OUTPUT/include2 -I$OUTPUT/include"
        if [ -f "$OUTPUT/include/generated/autoconf.h" ]; then
            AUTOCONF_CFLAGS="-include $OUTPUT/include/generated/autoconf.h"
        else
            AUTOCONF_CFLAGS="-include $OUTPUT/include/linux/autoconf.h"
        fi
    else
        if [ -f "$HEADERS/generated/autoconf.h" ]; then
            AUTOCONF_CFLAGS="-include $HEADERS/generated/autoconf.h"
        else
            AUTOCONF_CFLAGS="-include $HEADERS/linux/autoconf.h"
        fi
    fi

    CFLAGS="$CFLAGS $OUTPUT_CFLAGS -I$HEADERS -I$HEADERSA $AUTOCONF_CFLAGS"

    test_xen

    if [ "$OUTPUT" != "$SOURCES" ]; then
        MACH_CFLAGS="-I$HEADERS/asm-$ARCH/mach-default"
        if [ "$ARCH" = "i386" -o "$ARCH" = "x86_64" ]; then
            MACH_CFLAGS="$MACH_CFLAGS -I$HEADERS/asm-x86/mach-default"
            MACH_CFLAGS="$MACH_CFLAGS -I$SOURCES/arch/x86/include/asm/mach-default"
        elif [ "$ARCH" = "arm" ]; then
            MACH_CFLAGS="$MACH_CFLAGS -I$SOURCES/arch/arm/mach-tegra/include -D__LINUX_ARM_ARCH__=7"
        fi
        if [ "$XEN_PRESENT" != "0" ]; then
            MACH_CFLAGS="-I$HEADERS/asm-$ARCH/mach-xen $MACH_CFLAGS"
        fi
    else
        MACH_CFLAGS="-I$HEADERS/asm/mach-default"
        if [ "$ARCH" = "i386" -o "$ARCH" = "x86_64" ]; then
            MACH_CFLAGS="$MACH_CFLAGS -I$HEADERS/asm-x86/mach-default"
            MACH_CFLAGS="$MACH_CFLAGS -I$SOURCES/arch/x86/include/asm/mach-default"
        elif [ "$ARCH" = "arm" ]; then
            MACH_CFLAGS="$MACH_CFLAGS -I$SOURCES/arch/arm/mach-tegra/include -D__LINUX_ARM_ARCH__=7"
        fi
        if [ "$XEN_PRESENT" != "0" ]; then
            MACH_CFLAGS="-I$HEADERS/asm/mach-xen $MACH_CFLAGS"
        fi
    fi

    CFLAGS="$BASE_CFLAGS $MACH_CFLAGS $OUTPUT_CFLAGS -I$HEADERS -I$HEADERSA $AUTOCONF_CFLAGS"

    if [ "$ARCH" = "i386" -o "$ARCH" = "x86_64" ]; then
        CFLAGS="$CFLAGS -I$SOURCES/arch/x86/include -I$SOURCES/arch/x86/include/uapi -I$OUTPUT/arch/x86/include/generated -I$OUTPUT/arch/x86/include/generated/uapi"
    elif [ "$ARCH" = "arm" ]; then
        CFLAGS="$CFLAGS -I$SOURCES/arch/arm/include -I$OUTPUT/arch/arm/include/generated"
    fi
    if [ -n "$BUILD_PARAMS" ]; then
        CFLAGS="$CFLAGS -D$BUILD_PARAMS"
    fi
}

CONFTEST_PREAMBLE="#include \"conftest.h\"
    #if defined(NV_LINUX_KCONFIG_H_PRESENT)
    #include <linux/kconfig.h>
    #endif
    #if defined(NV_GENERATED_AUTOCONF_H_PRESENT)
    #include <generated/autoconf.h>
    #else
    #include <linux/autoconf.h>
    #endif
    #if defined(CONFIG_XEN) && \
        defined(CONFIG_XEN_INTERFACE_VERSION) &&  !defined(__XEN_INTERFACE_VERSION__)
    #define __XEN_INTERFACE_VERSION__ CONFIG_XEN_INTERFACE_VERSION
    #endif"

compile_test() {
    case "$1" in
        remap_page_range)
            #
            # Determine if the remap_page_range() function is present
            # and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/mm.h>
            void conftest_remap_page_range(void) {
                remap_page_range();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_REMAP_PAGE_RANGE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/mm.h>
            int conftest_remap_page_range(void) {
                pgprot_t pgprot = __pgprot(0);
                return remap_page_range(NULL, 0L, 0L, 0L, pgprot);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_REMAP_PAGE_RANGE_PRESENT" >> conftest.h
                echo "#define NV_REMAP_PAGE_RANGE_ARGUMENT_COUNT 5" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/mm.h>
            int conftest_remap_page_range(void) {
                pgprot_t pgprot = __pgprot(0);
                return remap_page_range(0L, 0L, 0L, pgprot);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_REMAP_PAGE_RANGE_PRESENT" >> conftest.h
                echo "#define NV_REMAP_PAGE_RANGE_ARGUMENT_COUNT 4" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error remap_page_range() conftest failed!" >> conftest.h
                return
            fi
        ;;

        set_memory_uc)
            #
            # Determine if the set_memory_uc() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <asm/cacheflush.h>
            void conftest_set_memory_uc(void) {
                set_memory_uc();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_SET_MEMORY_UC_PRESENT" >> conftest.h
                return
            else
                echo "#define NV_SET_MEMORY_UC_PRESENT" >> conftest.h
                return
            fi
        ;;

        set_pages_uc)
            #
            # Determine if the set_pages_uc() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <asm/cacheflush.h>
            void conftest_set_pages_uc(void) {
                set_pages_uc();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_SET_PAGES_UC_PRESENT" >> conftest.h
                return
            else
                echo "#define NV_SET_PAGES_UC_PRESENT" >> conftest.h
                return
            fi
        ;;

        change_page_attr)
            #
            # Determine if the change_page_attr() function is
            # present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/version.h>
            #include <linux/utsname.h>
            #include <linux/mm.h>
            #if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 0)
              #include <asm/cacheflush.h>
            #endif
            void conftest_change_page_attr(void) {
                change_page_attr();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_CHANGE_PAGE_ATTR_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_CHANGE_PAGE_ATTR_PRESENT" >> conftest.h
                return
            fi
        ;;

        pci_get_class)
            #
            # Determine if the pci_get_class() function is
            # present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/pci.h>
            void conftest_pci_get_class(void) {
                pci_get_class();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_PCI_GET_CLASS_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_PCI_GET_CLASS_PRESENT" >> conftest.h
                return
            fi
        ;;

        pci_get_domain_bus_and_slot)
            #
            # Determine if the pci_get_domain_bus_and_slot() function
            # is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/pci.h>
            void conftest_pci_get_domain_bus_and_slot(void) {
                pci_get_domain_bus_and_slot();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_PCI_GET_DOMAIN_BUS_AND_SLOT_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_PCI_GET_DOMAIN_BUS_AND_SLOT_PRESENT" >> conftest.h
                return
            fi
        ;;

        remap_pfn_range)
            #
            # Determine if the remap_pfn_range() function is
            # present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/mm.h>
            void conftest_remap_pfn_range(void) {
                remap_pfn_range();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_REMAP_PFN_RANGE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_REMAP_PFN_RANGE_PRESENT" >> conftest.h
                return
            fi
        ;;

        agp_backend_acquire)
            #
            # Determine if the agp_backend_acquire() function is
            # present and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/agp_backend.h>
            typedef struct agp_bridge_data agp_bridge_data;
            agp_bridge_data *conftest_agp_backend_acquire(struct pci_dev *dev) {
                return agp_backend_acquire(dev, 0L);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_AGP_BACKEND_ACQUIRE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/agp_backend.h>
            typedef struct agp_bridge_data agp_bridge_data;
            agp_bridge_data *conftest_agp_backend_acquire(struct pci_dev *dev) {
                return agp_backend_acquire(dev);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_AGP_BACKEND_ACQUIRE_PRESENT" >> conftest.h
                echo "#define NV_AGP_BACKEND_ACQUIRE_ARGUMENT_COUNT 1" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/agp_backend.h>
            typedef struct agp_bridge_data agp_bridge_data;
            agp_bridge_data *conftest_agp_backend_acquire(void) {
                return agp_backend_acquire();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_AGP_BACKEND_ACQUIRE_PRESENT" >> conftest.h
                echo "#define NV_AGP_BACKEND_ACQUIRE_ARGUMENT_COUNT 0" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error agp_backend_acquire() conftest failed!" >> conftest.h
                return
            fi
        ;;

        vmap)
            #
            # Determine if the vmap() function is present and how
            # many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/vmalloc.h>
            void conftest_vmap(void) {
                vmap();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_VMAP_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/vmalloc.h>
            void *conftest_vmap(struct page **pages, int count) {
                return vmap(pages, count);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_VMAP_PRESENT" >> conftest.h
                echo "#define NV_VMAP_ARGUMENT_COUNT 2" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/vmalloc.h>
            #include <linux/mm.h>
            void *conftest_vmap(struct page **pages, int count) {
                return vmap(pages, count, 0, PAGE_KERNEL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_VMAP_PRESENT" >> conftest.h
                echo "#define NV_VMAP_ARGUMENT_COUNT 4" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error vmap() conftest failed!" >> conftest.h
                return
            fi
        ;;

        i2c_adapter)
            #
            # Determine if the 'i2c_adapter' structure has inc_use()
            # and client_register() members.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/i2c.h>
            int conftest_i2c_adapter(void) {
                return offsetof(struct i2c_adapter, inc_use);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_I2C_ADAPTER_HAS_INC_USE" >> conftest.h
                rm -f conftest$$.o
            else
                echo "#undef NV_I2C_ADAPTER_HAS_INC_USE" >> conftest.h
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/i2c.h>
            int conftest_i2c_adapter(void) {
                return offsetof(struct i2c_adapter, client_register);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_I2C_ADAPTER_HAS_CLIENT_REGISTER" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#undef NV_I2C_ADAPTER_HAS_CLIENT_REGISTER" >> conftest.h
                return
            fi
        ;;

        pm_message_t)
            #
            # Determine if the 'pm_message_t' data type is present
            # and if it as an 'event' member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/pm.h>
            void conftest_pm_message_t(pm_message_t state) {
                pm_message_t *p = &state;
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_PM_MESSAGE_T_PRESENT" >> conftest.h
                rm -f conftest$$.o
            else
                echo "#undef NV_PM_MESSAGE_T_PRESENT" >> conftest.h
                echo "#undef NV_PM_MESSAGE_T_HAS_EVENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/pm.h>  
            int conftest_pm_message_t(void) {
                return offsetof(pm_message_t, event);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_PM_MESSAGE_T_HAS_EVENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#undef NV_PM_MESSAGE_T_HAS_EVENT" >> conftest.h
                return
            fi
        ;;

        pci_choose_state)
            #
            # Determine if the pci_choose_state() function is
            # present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/pci.h>
            void conftest_pci_choose_state(void) {
                pci_choose_state();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_PCI_CHOOSE_STATE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_PCI_CHOOSE_STATE_PRESENT" >> conftest.h
                return
            fi
        ;;

        vm_insert_page)
            #
            # Determine if the vm_insert_page() function is
            # present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/mm.h>
            void conftest_vm_insert_page(void) {
                vm_insert_page();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_VM_INSERT_PAGE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_VM_INSERT_PAGE_PRESENT" >> conftest.h
                return
            fi
        ;;

        irq_handler_t)
            #
            # Determine if the 'irq_handler_t' type is present and
            # if it takes a 'struct ptregs *' argument.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/interrupt.h>
            irq_handler_t conftest_isr;
            " > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ ! -f conftest$$.o ]; then
                echo "#undef NV_IRQ_HANDLER_T_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            rm -f conftest$$.o

            echo "$CONFTEST_PREAMBLE
            #include <linux/interrupt.h>
            irq_handler_t conftest_isr;
            int conftest_irq_handler_t(int irq, void *arg) {
                return conftest_isr(irq, arg);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_IRQ_HANDLER_T_PRESENT" >> conftest.h
                echo "#define NV_IRQ_HANDLER_T_ARGUMENT_COUNT 2" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/interrupt.h>
            irq_handler_t conftest_isr;
            int conftest_irq_handler_t(int irq, void *arg, struct pt_regs *regs) {
                return conftest_isr(irq, arg, regs);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_IRQ_HANDLER_T_PRESENT" >> conftest.h
                echo "#define NV_IRQ_HANDLER_T_ARGUMENT_COUNT 3" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error irq_handler_t() conftest failed!" >> conftest.h
                return
            fi
        ;;

        acpi_device_ops)
            #
            # Determine if the 'acpi_device_ops' structure has
            # a match() member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <acpi/acpi_bus.h>
            int conftest_acpi_device_ops(void) {
                return offsetof(struct acpi_device_ops, match);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_DEVICE_OPS_HAS_MATCH" >> conftest.h
                return
            else
                echo "#undef NV_ACPI_DEVICE_OPS_HAS_MATCH" >> conftest.h
                return
            fi
        ;;

        acpi_device_id)
            #
            # Determine if the 'acpi_device_id' structure has 
            # a 'driver_data' member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <acpi/acpi_drivers.h>
            int conftest_acpi_device_id(void) {
                return offsetof(struct acpi_device_id, driver_data);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_ACPI_DEVICE_ID_HAS_DRIVER_DATA" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#undef NV_ACPI_DEVICE_ID_HAS_DRIVER_DATA" >> conftest.h
                return
            fi
        ;;

        acquire_console_sem)
            #
            # Determine if the acquire_console_sem() function
            # is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/console.h>
            void conftest_acquire_console_sem(void) {
                acquire_console_sem(NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_ACQUIRE_CONSOLE_SEM_PRESENT" >> conftest.h
                return
            else
                echo "#define NV_ACQUIRE_CONSOLE_SEM_PRESENT" >> conftest.h
                return
            fi
        ;;

        kmem_cache_create)
            #
            # Determine if the kmem_cache_create() function is
            # present and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/slab.h>
            void conftest_kmem_cache_create(void) {
                kmem_cache_create();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_KMEM_CACHE_CREATE_PRESENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/slab.h>
            void conftest_kmem_cache_create(void) {
                kmem_cache_create(NULL, 0, 0, 0L, NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_KMEM_CACHE_CREATE_PRESENT" >> conftest.h
                echo "#define NV_KMEM_CACHE_CREATE_ARGUMENT_COUNT 6" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/slab.h>
            void conftest_kmem_cache_create(void) {
                kmem_cache_create(NULL, 0, 0, 0L, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_KMEM_CACHE_CREATE_PRESENT" >> conftest.h
                echo "#define NV_KMEM_CACHE_CREATE_ARGUMENT_COUNT 5" >> conftest.h
                return
            else
                echo "#error kmem_cache_create() conftest failed!" >> conftest.h
            fi
        ;;

        smp_call_function)
            #
            # Determine if the smp_call_function() function is
            # present and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_smp_call_function(void) {
            #ifdef CONFIG_SMP
                smp_call_function();
            #endif
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_SMP_CALL_FUNCTION_PRESENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_smp_call_function(void) {
                smp_call_function(NULL, NULL, 0, 0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_SMP_CALL_FUNCTION_PRESENT" >> conftest.h
                echo "#define NV_SMP_CALL_FUNCTION_ARGUMENT_COUNT 4" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_smp_call_function(void) {
                smp_call_function(NULL, NULL, 0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_SMP_CALL_FUNCTION_PRESENT" >> conftest.h
                echo "#define NV_SMP_CALL_FUNCTION_ARGUMENT_COUNT 3" >> conftest.h
                return
            else
                echo "#error smp_call_function() conftest failed!" >> conftest.h
            fi
        ;;

        on_each_cpu)
            #
            # Determine if the on_each_cpu() function is present
            # and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_on_each_cpu(void) {
            #ifdef CONFIG_SMP
                on_each_cpu();
            #endif
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_ON_EACH_CPU_PRESENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_on_each_cpu(void) {
                on_each_cpu(NULL, NULL, 0, 0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ON_EACH_CPU_PRESENT" >> conftest.h
                echo "#define NV_ON_EACH_CPU_ARGUMENT_COUNT 4" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/smp.h>
            void conftest_on_each_cpu(void) {
                on_each_cpu(NULL, NULL, 0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ON_EACH_CPU_PRESENT" >> conftest.h
                echo "#define NV_ON_EACH_CPU_ARGUMENT_COUNT 3" >> conftest.h
                return
            else
                echo "#error on_each_cpu() conftest failed!" >> conftest.h
            fi
        ;;

        vmm_support)
            # check if a VMM is supported (Xen only for now).
            if [ -f nv-xen.h ]; then
                echo "#define HAVE_NV_XEN 1" >> conftest.h
                return
            else
                echo "#undef HAVE_NV_XEN" >> conftest.h
            fi
        ;;

        acpi_evaluate_integer)
            #
            # Determine if the acpi_evaluate_integer() function is
            # present and the type of its 'data' argument.
            #

            echo "$CONFTEST_PREAMBLE
            #include <acpi/acpi_bus.h>
            acpi_status acpi_evaluate_integer(acpi_handle h, acpi_string s,
                struct acpi_object_list *l, unsigned long long *d) {
                return AE_OK;
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_EVALUATE_INTEGER_PRESENT" >> conftest.h
                echo "typedef unsigned long long nv_acpi_integer_t;" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <acpi/acpi_bus.h>
            acpi_status acpi_evaluate_integer(acpi_handle h, acpi_string s,
                struct acpi_object_list *l, unsigned long *d) {
                return AE_OK;
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_EVALUATE_INTEGER_PRESENT" >> conftest.h
                echo "typedef unsigned long nv_acpi_integer_t;" >> conftest.h
                return
            else
                #
                # We can't report a compile test failure here because
                # this is a catch-all for both kernels that don't
                # have acpi_evaluate_integer() and kernels that have
                # broken header files that make it impossible to
                # tell if the function is present.
                #
                echo "#undef NV_ACPI_EVALUATE_INTEGER_PRESENT" >> conftest.h
                echo "typedef unsigned long nv_acpi_integer_t;" >> conftest.h
            fi
        ;;

        acpi_walk_namespace)
            #
            # Determine if the acpi_walk_namespace() function is present
            # and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_walk_namespace(void) {
                acpi_walk_namespace();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_ACPI_WALK_NAMESPACE_PRESENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_walk_namespace(void) {
                acpi_walk_namespace(0, NULL, 0, NULL, NULL, NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_WALK_NAMESPACE_PRESENT" >> conftest.h
                echo "#define NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT 7" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_walk_namespace(void) {
                acpi_walk_namespace(0, NULL, 0, NULL, NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_WALK_NAMESPACE_PRESENT" >> conftest.h
                echo "#define NV_ACPI_WALK_NAMESPACE_ARGUMENT_COUNT 6" >> conftest.h
                return
            else
                echo "#error acpi_walk_namespace() conftest failed!" >> conftest.h
            fi
        ;;

        acpi_os_wait_events_complete)
            #
            # Determine if the acpi_os_wait_events_complete() function
            # is present and how many arguments it takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_os_wait_events_complete(void) {
                acpi_os_wait_events_complete(NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_ACPI_OS_WAIT_EVENTS_COMPLETE_PRESENT" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_os_wait_events_complete(void) {
                acpi_os_wait_events_complete(NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_OS_WAIT_EVENTS_COMPLETE_PRESENT" >> conftest.h
                echo "#define NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT 1" >> conftest.h
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/acpi.h>
            void conftest_acpi_os_wait_events_complete(void) {
                acpi_os_wait_events_complete();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#define NV_ACPI_OS_WAIT_EVENTS_COMPLETE_PRESENT" >> conftest.h
                echo "#define NV_ACPI_OS_WAIT_EVENTS_COMPLETE_ARGUMENT_COUNT 0" >> conftest.h
                return
            else
                echo "#error acpi_os_wait_events_complete() conftest failed!" >> conftest.h
            fi
        ;;

        ioremap_cache)
            #
            # Determine if the ioremap_cache() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <asm/io.h>
            void conftest_ioremap_cache(void) {
                ioremap_cache();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_IOREMAP_CACHE_PRESENT" >> conftest.h
                return
            else
                echo "#define NV_IOREMAP_CACHE_PRESENT" >> conftest.h
                return
            fi
        ;;

        ioremap_wc)
            #
            # Determine if the ioremap_wc() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <asm/io.h>
            void conftest_ioremap_wc(void) {
                ioremap_wc();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                rm -f conftest$$.o
                echo "#undef NV_IOREMAP_WC_PRESENT" >> conftest.h
                return
            else
                echo "#define NV_IOREMAP_WC_PRESENT" >> conftest.h
                return
            fi
        ;;

        proc_dir_entry)
            #
            # Determine if the 'proc_dir_entry' structure has 
            # an 'owner' member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/proc_fs.h>
            int conftest_proc_dir_entry(void) {
                return offsetof(struct proc_dir_entry, owner);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_PROC_DIR_ENTRY_HAS_OWNER" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#undef NV_PROC_DIR_ENTRY_HAS_OWNER" >> conftest.h
                return
            fi
        ;;

      INIT_WORK)
            #
            # Determine how many arguments the INIT_WORK() macro
            # takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/workqueue.h>
            void conftest_INIT_WORK(void) {
                INIT_WORK();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_INIT_WORK_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/workqueue.h>
            void conftest_INIT_WORK(void) {
                INIT_WORK((struct work_struct *)NULL, NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_INIT_WORK_PRESENT" >> conftest.h
                echo "#define NV_INIT_WORK_ARGUMENT_COUNT 3" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/workqueue.h>
            void conftest_INIT_WORK(void) {
                INIT_WORK((struct work_struct *)NULL, NULL);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_INIT_WORK_PRESENT" >> conftest.h
                echo "#define NV_INIT_WORK_ARGUMENT_COUNT 2" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error INIT_WORK() conftest failed!" >> conftest.h
                return
            fi
        ;;

      pci_dma_mapping_error)
            #
            # Determine how many arguments pci_dma_mapping_error()
            # takes.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/pci.h>
            int conftest_pci_dma_mapping_error(void) {
                return pci_dma_mapping_error(NULL, 0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_PCI_DMA_MAPPING_ERROR_PRESENT" >> conftest.h
                echo "#define NV_PCI_DMA_MAPPING_ERROR_ARGUMENT_COUNT 2" >> conftest.h
                rm -f conftest$$.o
                return
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/pci.h>
            int conftest_pci_dma_mapping_error(void) {
                return pci_dma_mapping_error(0);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_PCI_DMA_MAPPING_ERROR_PRESENT" >> conftest.h
                echo "#define NV_PCI_DMA_MAPPING_ERROR_ARGUMENT_COUNT 1" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#error pci_dma_mapping_error() conftest failed!" >> conftest.h
                return
            fi
        ;;

        agp_memory)
            #
            # Determine if the 'agp_memory' structure has
            # a 'pages' member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/agp_backend.h>
            int conftest_agp_memory(void) {
                return offsetof(struct agp_memory, pages);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_AGP_MEMORY_HAS_PAGES" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#undef NV_AGP_MEMORY_HAS_PAGES" >> conftest.h
                return
            fi
        ;;

        scatterlist)
            #
            # Determine if the 'scatterlist' structure has
            # a 'page_link' member.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/scatterlist.h>
            int conftest_scatterlist(void) {
                return offsetof(struct scatterlist, page_link);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_SCATTERLIST_HAS_PAGE" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_SCATTERLIST_HAS_PAGE" >> conftest.h
                return
            fi
        ;;

        pci_domain_nr)
            #
            # Determine if the pci_domain_nr() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/pci.h>
            int conftest_pci_domain_nr(struct pci_dev *dev) {
                return pci_domain_nr();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_PCI_DOMAIN_NR_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_PCI_DOMAIN_NR_PRESENT" >> conftest.h
                return
            fi
        ;;

        file_operations)
            #
            # Determine if the 'file_operations' structure has
            # 'ioctl', 'unlocked_ioctl' and 'compat_ioctl' fields.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/fs.h>
            int conftest_file_operations(void) {
                return offsetof(struct file_operations, ioctl);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_FILE_OPERATIONS_HAS_IOCTL" >> conftest.h
                rm -f conftest$$.o
            else
                echo "#undef NV_FILE_OPERATIONS_HAS_IOCTL" >> conftest.h
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/fs.h>
            int conftest_file_operations(void) {
                return offsetof(struct file_operations, unlocked_ioctl);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_FILE_OPERATIONS_HAS_UNLOCKED_IOCTL" >> conftest.h
                rm -f conftest$$.o
            else
                echo "#undef NV_FILE_OPERATIONS_HAS_UNLOCKED_IOCTL" >> conftest.h
            fi

            echo "$CONFTEST_PREAMBLE
            #include <linux/fs.h>
            int conftest_file_operations(void) {
                return offsetof(struct file_operations, compat_ioctl);
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#define NV_FILE_OPERATIONS_HAS_COMPAT_IOCTL" >> conftest.h
                rm -f conftest$$.o
            else
                echo "#undef NV_FILE_OPERATIONS_HAS_COMPAT_IOCTL" >> conftest.h
            fi
        ;;

        sg_init_table)
            #
            # Determine if the sg_init_table() function is present.
            #
            echo "$CONFTEST_PREAMBLE
            #include <linux/scatterlist.h>
            void conftest_sg_init_table(struct scatterlist *sgl,
                    unsigned int nents) {
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ ! -f conftest$$.o ]; then
                echo "#undef NV_SG_INIT_TABLE_PRESENT" >> conftest.h
                return

            fi
            rm -f conftest$$.o

            echo "$CONFTEST_PREAMBLE
            #include <linux/types.h>
            #include <linux/scatterlist.h>
            void conftest_sg_init_table(struct scatterlist *sgl,
                    unsigned int nents) {
                sg_init_table();
            }" > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1
            rm -f conftest$$.c

            if [ -f conftest$$.o ]; then
                echo "#undef NV_SG_INIT_TABLE_PRESENT" >> conftest.h
                rm -f conftest$$.o
                return
            else
                echo "#define NV_SG_INIT_TABLE_PRESENT" >> conftest.h
                return
            fi
        ;;

    esac
}

build_cflags

case "$6" in
    cc_sanity_check)
        #
        # Check if the selected compiler can create object files
        # in the current environment.
        #
        VERBOSE=$7

        echo "int cc_sanity_check(void) {
            return 0;
        }" > conftest$$.c

        $CC -c conftest$$.c > /dev/null 2>&1
        rm -f conftest$$.c

        if [ ! -f conftest$$.o ]; then
            if [ "$VERBOSE" = "full_output" ]; then
                echo "";
            fi
            if [ "$CC" != "cc" ]; then
                echo "The C compiler '$CC' does not appear to be able to"
                echo "create object files.  Please make sure you have "
                echo "your Linux distribution's libc development package"
                echo "installed and that '$CC' is a valid C compiler";
                echo "name."
            else
                echo "The C compiler '$CC' does not appear to be able to"
                echo "create executables.  Please make sure you have "
                echo "your Linux distribution's gcc and libc development"
                echo "packages installed."
            fi
            if [ "$VERBOSE" = "full_output" ]; then
                echo "";
                echo "*** Failed CC sanity check. Bailing out! ***";
                echo "";
            fi
            exit 1
        else
            rm -f conftest$$.o
            exit 0
        fi
    ;;

    cc_version_check)
        #
        # Verify that the same compiler is used for the kernel and kernel
        # module.
        #
        VERBOSE=$7
        
        if [ ! -f gcc-version-check.c ]; then
          #
          # gcc-version-check.c is not in the current working directory.
          # This can happen when building the kernel module from an
          # NVIDIA-internal intermediate directory prior to creating an
          # NVIDIA driver package.  Since the version check below is less
          # useful than it used to be, just silently skip the test if
          # gcc-version-check.c is missing.
          #
          IGNORE_CC_MISMATCH=1
        fi

        if [ -n "$IGNORE_CC_MISMATCH" -o -n "$SYSSRC" -o -n "$SYSINCLUDE" ]; then
          #
          # The user chose to disable the CC version test (which may or
          # may not be wise) or is building the module for a kernel not
          # currently running, which renders the test meaningless.
          #
          exit 0
        fi

        rm -f gcc-version-check
        $HOSTCC gcc-version-check.c -o gcc-version-check > /dev/null 2>&1
        if [ ! -f gcc-version-check ]; then
            if [ "$CC" != "cc" ]; then
                MSG="Could not compile 'gcc-version-check.c'.  Please be "
                MSG="$MSG sure you have your Linux distribution's libc "
                MSG="$MSG development package installed and that '$CC' "
                MSG="$MSG is a valid C compiler name."
            else
                MSG="Could not compile 'gcc-version-check.c'.  Please be "
                MSG="$MSG sure you have your Linux distribution's gcc "
                MSG="$MSG and libc development packages installed."
            fi
            RET=1
        else
            PROC_VERSION="/proc/version"
            if [ -f $PROC_VERSION ]; then
                MSG=`./gcc-version-check "$(cat $PROC_VERSION)"`
                RET=$?
            else
                MSG="$PROC_VERSION does not exist."
                RET=1
            fi
            rm -f gcc-version-check
        fi

        if [ "$RET" != "0" ]; then
            #
            # The gcc version check failed
            #
            
            if [ "$VERBOSE" = "full_output" ]; then
                echo "";
                echo "gcc-version-check failed:";
                echo "";
                echo "$MSG" | fmt -w 52
                echo "";
                echo "If you know what you are doing and want to override";
                echo "the gcc version check, you can do so by setting the";
                echo "IGNORE_CC_MISMATCH environment variable to \"1\".";
                echo "";
                echo "In any other case, set the CC environment variable";
                echo "to the name of the compiler that was used to compile";
                echo "the kernel.";
                echo ""
                echo "*** Failed CC version check. Bailing out! ***";
                echo "";
            else
                echo "$MSG";
            fi
            exit 1;
        else
            exit 0
        fi
    ;;

    suser_sanity_check)
        #
        # Determine the caller's user id to determine if we have sufficient
        # privileges for the requested operation.
        #
        if [ $(id -ur) != 0 ]; then
            echo "";
            echo "Please run \"make install\" as root.";
            echo "";
            echo "*** Failed super-user sanity check. Bailing out! ***";
            exit 1
        else
            exit 0
        fi
    ;;

    rmmod_sanity_check)
        #
        # Make sure that any currently loaded NVIDIA kernel module can be
        # unloaded.
        #
        MODULE="nvidia"

        if [ -n "$SYSSRC" -o -n "$SYSINCLUDE" ]; then
          #
          # Don't attempt to remove the kernel module if we're not
          # building against the running kernel.
          #
          exit 0
        fi

        if lsmod | grep -wq $MODULE; then
          rmmod $MODULE > /dev/null 2>&1
        fi

        if lsmod | grep -wq $MODULE; then
            #
            # The NVIDIA kernel module is still loaded, most likely because
            # it is busy.
            #
            echo "";
            echo "Unable to remove existing NVIDIA kernel module.";
            echo "Please be sure you have exited X before attempting";
            echo "to install the NVIDIA kernel module.";
            echo "";
            echo "*** Failed rmmod sanity check. Bailing out! ***";
            exit 1
        else
            exit 0
        fi
    ;;

    select_makefile)
        #
        # Select which Makefile to use based on the version of the
        # kernel we are building against: use the kbuild Makefile for
        # 2.6 and newer kernels, and the old Makefile for kernels older
        # than 2.6.
        #
        rm -f Makefile
        RET=1
        VERBOSE=$7
        FILE="linux/version.h"
        SELECTED_MAKEFILE=""

        if [ -f $HEADERS/$FILE -o -f $OUTPUT/include/$FILE ]; then
            #
            # We are either looking at a configured kernel source
            # tree or at headers shipped for a specific kernel.
            # Determine the kernel version using a compile check.
            #
            rm -f conftest.h
            test_headers

            echo "$CONFTEST_PREAMBLE
            #include <linux/version.h>
            #include <linux/utsname.h>
            #if defined(TEST_2_4) && (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,0))
              #error \"!KERNEL_2_4\"
            #endif
            #if defined(TEST_2_6_OR_3) && (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0))
              #error \"!KERNEL_2_6_OR_3\"
            #endif" > conftest$$.c

            $CC $CFLAGS -DTEST_2_6_OR_3 -c conftest$$.c > /dev/null 2>&1

            if [ -f conftest$$.o ]; then
                if [ -f Makefile.rmlite ]; then
                    SELECTED_MAKEFILE=Makefile.rmlite
                else
                    SELECTED_MAKEFILE=Makefile.kbuild
                fi
                RET=0
            else
                $CC $CFLAGS -DTEST_2_4 -c conftest$$.c > /dev/null 2>&1

                if [ -f conftest$$.o ]; then
                    SELECTED_MAKEFILE=Makefile.nvidia
                    RET=0
                fi
            fi

            rm -f conftest$$.c conftest$$.o
            rm -f conftest.h
        else
            MAKEFILE=$HEADERS/../Makefile
            CONFIG=$HEADERS/../.config

            if [ -f $MAKEFILE -a -f $CONFIG ]; then
                #
                # This source tree is not configured, but includes
                # a Makefile and a .config file. If this is a 2.6
                # kernel older than 2.6.6, that's all we require to
                # build the module.
                #
                PATCHLEVEL=$(grep "^PATCHLEVEL =" $MAKEFILE | cut -d " " -f 3)
                SUBLEVEL=$(grep "^SUBLEVEL =" $MAKEFILE | cut -d " " -f 3)

                if [ -n "$PATCHLEVEL" -a $PATCHLEVEL -ge 6 \
                        -a -n "$SUBLEVEL" -a $SUBLEVEL -le 5 ]; then
                    SELECTED_MAKEFILE=Makefile.kbuild
                    RET=0
                fi
            fi
        fi

        if [ "$RET" = "0" ]; then
            ln -s $SELECTED_MAKEFILE Makefile
            exit 0
        else
            echo "If you are using a Linux 2.4 kernel, please make sure";
            echo "you either have configured kernel sources matching your";
            echo "kernel or the correct set of kernel headers installed";
            echo "on your system.";
            echo "";
            echo "If you are using a Linux 2.6 kernel, please make sure";
            echo "you have configured kernel sources matching your kernel";
            echo "installed on your system. If you specified a separate";
            echo "output directory using either the \"KBUILD_OUTPUT\" or";
            echo "the \"O\" KBUILD parameter, make sure to specify this";
            echo "directory with the SYSOUT environment variable or with";
            echo "the equivalent nvidia-installer command line option.";
            echo "";
            echo "Depending on where and how the kernel sources (or the";
            echo "kernel headers) were installed, you may need to specify";
            echo "their location with the SYSSRC environment variable or";
            echo "the equivalent nvidia-installer command line option.";
            echo "";
            if [ "$VERBOSE" = "full_output" ]; then
                echo "*** Unable to determine the target kernel version. ***";
                echo "";
            fi
            exit 1
        fi
    ;;

    get_uname)
        #
        # Print UTS_RELEASE from the kernel sources, if the kernel header
        # file ../linux/version.h or ../linux/utsrelease.h exists. If
        # neither header file is found, but a Makefile is found, extract
        # PATCHLEVEL and SUBLEVEL, and use them to build the kernel
        # release name.
        #
        # If no source file is found, or if an error occurred, return the
        # output of `uname -r`.
        #
        RET=1
        DIRS="generated linux"
        FILE=""
        
        for DIR in $DIRS; do
            if [ -f $HEADERS/$DIR/utsrelease.h ]; then
                FILE="$HEADERS/$DIR/utsrelease.h"
                break
            elif [ -f $OUTPUT/include/$DIR/utsrelease.h ]; then
                FILE="$OUTPUT/include/$DIR/utsrelease.h"
                break
            fi
        done

        if [ -z "$FILE" ]; then
            if [ -f $HEADERS/linux/version.h ]; then
                FILE="$HEADERS/linux/version.h"
            elif [ -f $OUTPUT/include/linux/version.h ]; then
                FILE="$OUTPUT/include/linux/version.h"
            fi
        fi

        if [ -n "$FILE" ]; then
            #
            # We are either looking at a configured kernel source tree
            # or at headers shipped for a specific kernel.  Determine
            # the kernel version using a CPP check.
            #
            VERSION=`echo "UTS_RELEASE" | $CC - -E -P -include $FILE 2>&1`

            if [ "$?" = "0" -a "VERSION" != "UTS_RELEASE" ]; then
                echo "$VERSION"
                RET=0
            fi
        else
            #
            # If none of the kernel headers ar found, but a Makefile is,
            # extract PATCHLEVEL and SUBLEVEL and use them to find
            # the kernel version.
            #
            MAKEFILE=$HEADERS/../Makefile

            if [ -f $MAKEFILE ]; then
                #
                # This source tree is not configured, but includes
                # the top-level Makefile.
                #
                PATCHLEVEL=$(grep "^PATCHLEVEL =" $MAKEFILE | cut -d " " -f 3)
                SUBLEVEL=$(grep "^SUBLEVEL =" $MAKEFILE | cut -d " " -f 3)

                if [ -n "$PATCHLEVEL" -a -n "$SUBLEVEL" ]; then
                    echo 2.$PATCHLEVEL.$SUBLEVEL
                    RET=0
                fi
            fi
        fi

        if [ "$RET" != "0" ]; then
            uname -r
            exit 1
        else
            exit 0
        fi
    ;;

    rivafb_sanity_check)
        #
        # Check if the kernel was compiled with rivafb support. If so, then
        # exit, since the driver no longer works with rivafb.
        #
        RET=1
        VERBOSE=$7
        OLD_FILE="linux/autoconf.h"
        NEW_FILE="generated/autoconf.h"

        if [ -f $HEADERS/$NEW_FILE -o -f $OUTPUT/include/$NEW_FILE ]; then
            FILE=$NEW_FILE
        fi
        if [ -f $HEADERS/$OLD_FILE -o -f $OUTPUT/include/$OLD_FILE ]; then
            FILE=$OLD_FILE
        fi

        if [ -n "$FILE" ]; then
            #
            # We are looking at a configured source tree; verify
            # that its configuration doesn't include rivafb using
            # a compile check.
            #
            rm -f conftest.h
            test_headers

            echo "$CONFTEST_PREAMBLE
            #ifdef CONFIG_FB_RIVA
            #error CONFIG_FB_RIVA defined!
            #endif
            " > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1

            if [ -f conftest$$.o ]; then
                RET=0
            fi

            rm -f conftest$$.c conftest$$.o
            rm -f conftest.h
        else
            CONFIG=$HEADERS/../.config
            if [ -f $CONFIG ]; then
                if [ -z "$(grep "^CONFIG_FB_RIVA=y" $CONFIG)" ]; then
                    RET=0
                fi
            fi
        fi

        if [ "$RET" != "0" ]; then
            echo "Your kernel was configured to include rivafb support!";
            echo "";
            echo "The rivafb driver conflicts with the NVIDIA driver, please";
            echo "reconfigure your kernel and *disable* rivafb support, then";
            echo "try installing the NVIDIA kernel module again.";
            echo "";
            if [ "$VERBOSE" = "full_output" ]; then
                echo "*** Failed rivafb sanity check. Bailing out! ***";
                echo "";
            fi
            exit 1
        else
            exit 0
        fi
    ;;

    nvidiafb_sanity_check)
        #
        # Check if the kernel was compiled with nvidiafb support. If so, then
        # exit, since the driver doesn't work with nvidiafb.
        #
        RET=1
        VERBOSE=$7
        OLD_FILE="linux/autoconf.h"
        NEW_FILE="generated/autoconf.h"

        if [ -f $HEADERS/$NEW_FILE -o -f $OUTPUT/include/$NEW_FILE ]; then
            FILE=$NEW_FILE
        fi
        if [ -f $HEADERS/$OLD_FILE -o -f $OUTPUT/include/$OLD_FILE ]; then
            FILE=$OLD_FILE
        fi

        if [ -n "$FILE" ]; then
            #
            # We are looking at a configured source tree; verify
            # that its configuration doesn't include nvidiafb using
            # a compile check.
            #
            rm -f conftest.h
            test_headers

            echo "$CONFTEST_PREAMBLE
            #ifdef CONFIG_FB_NVIDIA
            #error CONFIG_FB_NVIDIA defined!
            #endif
            " > conftest$$.c

            $CC $CFLAGS -c conftest$$.c > /dev/null 2>&1

            if [ -f conftest$$.o ]; then
                RET=0
            fi

            rm -f conftest$$.c conftest$$.o
            rm -f conftest.h
        else
            CONFIG=$HEADERS/../.config
            if [ -f $CONFIG ]; then
                if [ -z "$(grep "^CONFIG_FB_NVIDIA=y" $CONFIG)" ]; then
                    RET=0
                fi
            fi
        fi

        if [ "$RET" != "0" ]; then
            echo "Your kernel was configured to include nvidiafb support!";
            echo "";
            echo "The nvidiafb driver conflicts with the NVIDIA driver, please";
            echo "reconfigure your kernel and *disable* nvidiafb support, then";
            echo "try installing the NVIDIA kernel module again.";
            echo "";
            if [ "$VERBOSE" = "full_output" ]; then
                echo "*** Failed nvidiafb sanity check. Bailing out! ***";
                echo "";
            fi
            exit 1
        else
            exit 0
        fi
    ;;

    xen_sanity_check)
        #
        # Check if the target kernel is a Xen kernel. If so, then exit, since
        # the driver doesn't currently work with Xen.
        #
        VERBOSE=$7

        if [ -n "$IGNORE_XEN_PRESENCE" ]; then
            exit 0
        fi

        if [ "$XEN_PRESENT" != "0" ]; then
            echo "The kernel you are installing for is a Xen kernel!";
            echo "";
            echo "The NVIDIA driver does not currently work on Xen kernels. If ";
            echo "you are using a stock distribution kernel, please install ";
            echo "a variant of this kernel without Xen support; if this is a ";
            echo "custom kernel, please install a standard Linux kernel.  Then ";
            echo "try installing the NVIDIA kernel module again.";
            echo "";
            if [ "$VERBOSE" = "full_output" ]; then
                echo "*** Failed Xen sanity check. Bailing out! ***";
                echo "";
            fi
            exit 1
        else
            exit 0
        fi
    ;;

    patch_check)
        #
        # Check for any "official" patches that may have been applied and
        # construct a description table for reporting purposes.
        #
        PATCHES=""

        for PATCH in patch-*.h; do
            if [ -f $PATCH ]; then
                echo "#include \"$PATCH\"" >> patches.h
                PATCHES="$PATCHES "`echo $PATCH | sed -s 's/patch-\(.*\)\.h/\1/'`
            fi
        done

        echo "static struct {
                const char *short_description;
                const char *description;
              } __nv_patches[] = {" >> patches.h
            for i in $PATCHES; do
                echo "{ \"$i\", NV_PATCH_${i}_DESCRIPTION }," >> patches.h
            done
        echo "{ NULL, NULL } };" >> patches.h

        exit 0
    ;;

    compile_tests)
        #
        # Run a series of compile tests to determine the set of interfaces
        # and features available in the target kernel.
        #
        shift 5

        rm -f conftest.h
        test_headers

        for i in $*; do compile_test $i; done

        if [ -n "$SHOW_COMPILE_TEST_RESULTS" -a -f conftest.h ]; then
            cat conftest.h
        fi

        exit 0
    ;;

esac

```


I'll attach the patched files to this post.  They should be drop-in replacements...  ;)

Finally, after I installed edger's 304.51 and patched the two files, I re-installed 3.8-rc-1 (nVidia module built this time), rebooted, and bingo!

Hope that helps...

---

### Post by manulemaboul on 2012-12-23
Thank you so much :).
I'll try it after a little sleep, it's 6:17 AM here and haven't slept yet :p.

---

### Post by JMB74 on 2012-12-23
> **ronacc said:**
> just FYI , my wireless is working fine with 3.8 rc1 , I have a realtek 8185 chip .

Looks like now it was mostly the various Atheros drivers that did not build. :/

---

### Post by rrnbtter on 2012-12-23
Greetings, 
Its possible that they are just compiling enough drivers to get the development team functional.  The download isn't as big as the current 3.7 kernel.  

I think I will abandon Lucid and install it on a working RR 13.04 with Unity removed just to keep it simple.  The new kernel should be able to use my current Atheros drivers.  Guess I will find out.

---

### Post by zenarcher on 2012-12-23
I'm still were I was with kernel 3.6 and 3.7.  Locks up when my USB KVM switch is detected during boot with AMD 64 bit system.  Everything was fine with kernel 3.5 and earlier.  I'm beginning to wonder if my dual system using the KVM switch is going to be a thing of the past with these new kernels.

zenarcher

---

### Post by rrnbtter on 2012-12-23
Greetings,
Installed kernel 3.8 over RR 13.04.
rrnbtter@rrnbtter-Satellite-L305:~$ uname -a
Linux rrnbtter-Satellite-L305 3.8.0-030800rc1-generic #201212212135 SMP Sat Dec 22 02:45:41 UTC 2012 i686 i686 i686 GNU/Linux

Intel Mobile Chipset with GM45 video. 
Everything working including Unity.
My Atheros Wifi is still not recognized however my US Cellular modem is working so I have internet which I could not get using Lucid.

---

### Post by rrnbtter on 2012-12-23
Greetings,

> **zenarcher said:**
>   I'm beginning to wonder if my dual system using the KVM switch is going to be a thing of the past with these new kernels.

Doubt it.  You are ahead of reality. You may not get specific support until Beta or Final release. 
That is the problem with testing.  Somethings don't work. Thats why it make a bit of sense to test on a separate drive and keep a stable version for default.

---

### Post by zenarcher on 2012-12-23
> **rrnbtter said:**
> Greetings,



Doubt it.  You are ahead of reality. You may not get specific support until Beta or Final release. 
That is the problem with testing.  Somethings don't work. Thats why it make a bit of sense to test on a separate drive and keep a stable version for default.

Yes, I understand that.  That's what the second machine is used for with the kVM switch....strictly for testing.

---

### Post by manulemaboul on 2012-12-23
@[VinDSL]("http://ubuntuforums.org/member.php?u=1131082"): You rocks, your patched files worked, thanks a lot :).

Idling at 0% cpu usage, my 2 dies are at 33 and 34°C, never been that low :o.

---

### Post by VinDSL on 2012-12-23
> **manulemaboul said:**
> @[VinDSL]("http://ubuntuforums.org/member.php?u=1131082"): You rocks, your patched files worked, thanks a lot :).

Idling at 0% cpu usage, my 2 dies are at 33 and 34°C, never been that low :o.
Glad it worked for you...  :)

---

### Post by ventrical on 2012-12-23
> **zenarcher said:**
> Yes, I understand that.  That's what the second machine is used for with the kVM switch....strictly for testing.

  I got 4 machines on my KVM. No probs at all, Raring or otherwise.

---

### Post by zenarcher on 2012-12-23
> **ventrical said:**
> I got 4 machines on my KVM. No probs at all, Raring or otherwise.

That is strange.  This is the first time, ever, I've had a problem like this.  Then booting, or trying to run the Live DVD, text scrolls along until it gets to the KVM switch....starts to identify it, then stops part way through the KVM switch identification and goes no further.  It's just a little USB KVM switch I've used for several years and never have had issues.  Works find with 12.10 and has always worked well with previous versions for the past few years that I've had it. 

It's a Linkskey 2 port KVM switch.

zenarcher

---

### Post by VinDSL on 2012-12-23
w00t!  This is the Best Christmas Present ever! :)


[INDENT][INDENT]**[COLOR="DarkOrange"]Ubu Raring / Gnome-Shell 3.7.3 / Linux 3.8  / 2-3% CPU Usage / And, Everything Works[/COLOR]**[/INDENT]
[[IMG]http://vindsl.com/images/vindsl-desktop-23-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-dec-2012-1.png")[/INDENT]


**EDIT**

Oops!  I forgot...  :oops:

Thanks, Canonical!

---

### Post by ronacc on 2012-12-23
@ zenarcher , I don't know if this has anything to do with your kvm problem but the kernel seems to check for one during boot because I get a message during boot about " kvm disabled in bios " and I don't have a kvm switch . maybe you can find where that check is called and comment it out to see what happens .

---

### Post by zenarcher on 2012-12-23
> **ronacc said:**
> @ zenarcher , I don't know if this has anything to do with your kvm problem but the kernel seems to check for one during boot because I get a message during boot about " kvm disabled in bios " and I don't have a kvm switch . maybe you can find where that check is called and comment it out to see what happens .

Thanks for that info.  I'm clueless as to where to look for a line like that to comment out, but perhaps someone can tell me.

zenarcher

---

### Post by VinDSL on 2012-12-23
You know... I was just *thinking* to myself...

[INDENT]Q: " What's stopping you from patching nvidia-current-updates 304.64?!?!? "

A: " Nothing, that I can see. "[/INDENT]

Soooo...


```

vindsl@Zuul:~$ apt-cache policy nvidia-current-updates
[B][COLOR="Red"]nvidia-current-updates:
  Installed: 304.64-0ubuntu1[/COLOR][/B]
  Candidate: 304.64-0ubuntu1
  Version table:
 *** 304.64-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/restricted i386 Packages
        100 /var/lib/dpkg/status
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
vindsl@Zuul:~$
```


```

vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Sun Dec 23 19:59:21 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
**[COLOR="Red"]Kernel Release: Linux 3.8.0-030800rc1-generic[/COLOR]**
Gnome Release: GNOME Shell 3.7.3
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
**[COLOR="Red"]OpenGL version string:  2.1.2 NVIDIA 304.64[/COLOR]**

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers~quantal
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.902+git20121207+server-1.13-branch.ede07c1a-0ubuntu0ricotz~quantal

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$
```

Do Ubu wonders never cease?  LoL! :D

**EDIT**

I'll attach the patched files to this post, in case anyone feels adventuresome...

---

### Post by ventrical on 2012-12-24
> **zenarcher said:**
> That is strange.  This is the first time, ever, I've had a problem like this.  Then booting, or trying to run the Live DVD, text scrolls along until it gets to the KVM switch....starts to identify it, then stops part way through the KVM switch identification and goes no further.  It's just a little USB KVM switch I've used for several years and never have had issues.  Works find with 12.10 and has always worked well with previous versions for the past few years that I've had it. 

It's a Linkskey 2 port KVM switch.

zenarcher


Mine is a Zonet, PS/2 -4 switch KVM. It's a real workhorse. I have 11 machines that I test with various Ubuntu installs. The KVM makes testing a lot easier.

---

### Post by ventrical on 2012-12-24
> **zenarcher said:**
> Thanks for that info.  I'm clueless as to where to look for a line like that to comment out, but perhaps someone can tell me.

zenarcher


 It could be problems with current USB detect.

Are you running the 'live' from actual DVD or USB stick? Just curious.

---

### Post by ventrical on 2012-12-24
> **zenarcher said:**
> I'm still were I was with kernel 3.6 and 3.7.  Locks up when my USB KVM switch is detected during boot with AMD 64 bit system.  Everything was fine with kernel 3.5 and earlier.  I'm beginning to wonder if my dual system using the KVM switch is going to be a thing of the past with these new kernels.

zenarcher

  I have 3 i386 installs and one AMD64 install running on my Zonet. No problems.   The AMD64 has 3.7.RC8. 

  I am using a Compaq Keyboard. Fairly old. Older than 10 years I think. Some keyboards will just not load up .. ie, Acer and Dell keyboards are very touchy and jumpy. They will work some machines and not detect others.

  Do you have an extra keyboard laying around to test with?

---

### Post by zenarcher on 2012-12-24
> **ventrical said:**
> I have 3 i386 installs and one AMD64 install running on my Zonet. No problems.   The AMD64 has 3.7.RC8. 

  I am using a Compaq Keyboard. Fairly old. Older than 10 years I think. Some keyboards will just not load up .. ie, Acer and Dell keyboards are very touchy and jumpy. They will work some machines and not detect others.

  Do you have an extra keyboard laying around to test with?

Thanks for that.  Yes, I do have a couple of extra old keyboards lying around and I will give that a try.  This just does happen to be an old Dell keyboard I'm using...several years old, as I recall.  But I'll give one of the other ones I have a try and see what happens.

Thanks,
zenarcher

---

### Post by ventrical on 2012-12-24
> **zenarcher said:**
> Thanks for that.  Yes, I do have a couple of extra old keyboards lying around and I will give that a try.  This just does happen to be an old Dell keyboard I'm using...several years old, as I recall.  But I'll give one of the other ones I have a try and see what happens.

Thanks,
zenarcher

The Compaq keyboard is probably the most universal for hybrid built systems. It is just the standard AT keyboard, no bells or whistles, but has been a workhorse on all my towers. It will interchange with any PC I have, no problems.

  I will zsync raring AMD64bit daily and see if I get an emulation that you have on my KVM setup.

---

### Post by ventrical on 2012-12-24
@zenarcher

I just zsynced the daily for Dec. 24. Yet another ubuntu raring-desktop-amd64.iso masterpiece (where the USB works faster than the hdd) running off KVM workstation #4.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
ubuntu@ubuntu:~$ 

```

---

### Post by jppr on 2012-12-24
3.8 PPA mainline kernel is the first that works after the 3.5 kernel on my computer

My lspci...
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

---

### Post by manulemaboul on 2012-12-24
> **jppr said:**
> 3.8 PPA mainline kernel is the first that works after the 3.5 kernel on my computer

My lspci...
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)

Same for me, awesome, isn't it ? :D
Like a little Christmas gift from Linus and canonical :).

I've to admit that after testing all kernels since 3.5, I made a ridiculous victory dance in front of my computer when 3.8 booted :p.

Mine:
00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev a2)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g
05:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
05:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)

Pretty old, but performing admirably great with 3.8.0, mate & compiz.

---

### Post by zenarcher on 2012-12-24
> **ventrical said:**
> The Compaq keyboard is probably the most universal for hybrid built systems. It is just the standard AT keyboard, no bells or whistles, but has been a workhorse on all my towers. It will interchange with any PC I have, no problems.

  I will zsync raring AMD64bit daily and see if I get an emulation that you have on my KVM setup.

I've tried a couple different generic keyboards, but still the same thing.  Text scrolls....gets to identifying the KVM switch....and about halfway through the Serial Number of the KVM switch, everything just stops.

zenarcher

---

### Post by wnelson on 2012-12-24
I have found a problem with syncing USB devices. For now going back to 3.7

Walt

---

### Post by ventrical on 2012-12-25
> **wnelson said:**
> I have found a problem with syncing USB devices. For now going back to 3.7

Walt

I can verify that. Using 3.8RC it will not detect my wii USB. With 3.7RC8 it works great but when I come out of suspend the wiiUSB stick actually works but the indicator light does not come on. I think , in part, that this has to do with @zenarchers problem with his USB KVM.

---

### Post by rrnbtter on 2012-12-25
Greetings,
Oddly, my 3.8 uses my USB Broadband modem perfectly. But my wifi card doesn't work. So right now I only have internet on my modem. 
I'm also using 3.7 full time. I think thats the purpose of this forum section anyway. Kernel 3.8 has been confined to this thread so far. So! If today has bugs I don't think I will make inappropriate demands on tomorrow.

---

### Post by NM5TF on 2012-12-25
curious if anyone has tried this kernel with AMD 64 X 2 4000+ procs
and Nvidia Ge Force 6150SE nForce 430 graphics card???

I never could make the 3.7 kernel work with my sys running 12.04.1 LTS

Tommy

---

### Post by manulemaboul on 2012-12-27
3.6 and 3.7 never booted on my opteron 170, 3.8 works, you should give it a try ;).

---

### Post by TiCPU on 2012-12-27
Since Atheros wireless drivers weren't build, my laptop ath9k based card isn't detected without manually building the kernel module.

Here's the relevant part in 0003-default-config
```
-CONFIG_ATH5K=m
-# CONFIG_ATH5K_DEBUG is not set
-CONFIG_ATH5K_PCI=y
-# CONFIG_ATH5K_TRACER is not set
-CONFIG_ATH6KL=m
-# CONFIG_ATH6KL_DEBUG is not set
-CONFIG_ATH6KL_SDIO=m
-CONFIG_ATH6KL_USB=m
-CONFIG_ATH9K=m
-CONFIG_ATH9K_AHB=y
-CONFIG_ATH9K_BTCOEX_SUPPORT=y
-CONFIG_ATH9K_COMMON=m
-CONFIG_ATH9K_DEBUGFS=y
-CONFIG_ATH9K_HTC=m
-CONFIG_ATH9K_HTC_DEBUGFS=y
-CONFIG_ATH9K_HW=m
-# CONFIG_ATH9K_MAC_DEBUG is not set
-CONFIG_ATH9K_PCI=y
-CONFIG_ATH9K_RATE_CONTROL=y
-CONFIG_ATH_COMMON=m
-# CONFIG_ATH_DEBUG is not set
+# CONFIG_ATH_CARDS is not set
```

---

### Post by JMB74 on 2012-12-27
> **TiCPU said:**
> Since Atheros wireless drivers weren't build, my laptop ath9k based card isn't detected without manually building the kernel module.

Here's the relevant part in 0003-default-config

If you look at the build logs for the 3.8 mainline builds, then you will see that they are still being based off the stock ubuntu 3.7 configs from git.

Seems that the config (kconfig) options changed somewhat between 3.7 and 3.8, so the script is just skipping/desecting the Atheros config options? 

I think.....? 

Presumably once 3.8 gets into the stock raring repo, scripts/configs are updated etc, then this glitch will be ironed out...

---

### Post by zika on 2012-12-28
At my place with rv635 it works only without compiz. As soon as compiz is introduced it panics with recursive...
Update&#8321;: Nope, it does not need compiz but without it it takes a bit longer, just about enough to think that everything is OK...

---

### Post by pqwoerituytrueiwoq on 2012-12-28
breaks the wifi on my old retired laptop (hp compaq cq60-215dx)

---

### Post by cariboo on 2012-12-29
> **pqwoerituytrueiwoq said:**
> breaks the wifi on my old retired laptop (hp compaq cq60-215dx)

I have the same problem with my Compaq Mini 110, I created a bug report: Bug #[lpbug]1094408[/lpbug]

---

### Post by zika on 2012-12-30
996 is working on this machine for some time today... Knock on the wood, 3 times...
I did not try compiz yet...
Update&#8321;: Nope, I've jinxed it...

---

### Post by JMB74 on 2012-12-30
> **zika said:**
> 996 is working on this machine for some time today... Knock on the wood, 3 times...
I did not try compiz yet...
Update&#8321;: Nope, I've jinxed it...

Well, the drm-next tree is likely to be even less stable for that sort of thing than the stock 3.8 RC/daily.

---

### Post by zika on 2012-12-30
> **JMB74 said:**
> Well, the drm-next tree **is likely** to be even less stable for that sort of thing than the stock 3.8 RC/daily.I know that but it is not always the case...
It's just my addiction, I've never been out of the game with kernel for such a long time... ;)

---

### Post by Harry33 on 2013-01-03
Now the rc2 is available.

Here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc2-raring/)

---

### Post by zika on 2013-01-03
;(

---

### Post by Yahoé on 2013-01-03
3.8-rc2 is now out but as with 3.8-rc1, my AR922X Wireless Network Adapter isn't detected, so it's another no go.

---

### Post by JMB74 on 2013-01-03
> **Yahoé said:**
> 3.8-rc2 is now out but as with 3.8-rc1, my AR922X Wireless Network Adapter isn't detected, so it's another no go.

Well, the RCs are still being built based on the 3.7 ubuntu kernel configs, which are not compatible with setting the Atheros drivers to build on the 3.8 kernels.

Hopefully the kernel team will soon rebase the ubuntu raring kernel to 3.8 (already done in master-next git) soon and update configs accordingly. The RC builds in the kernel-ppa would then pull in the correct configs and build the Atheros drivers. 

I've been doing my own kernel builds in the meantime correcting the configs, and can confirm that once done the 3.8 kernel plays nicely with my Atheros card. :)

---

### Post by wnelson on 2013-01-04
NO Atheros drivers are being compiled into the kernel, why? its there.

Walt

---

### Post by JMB74 on 2013-01-05
> **wnelson said:**
> NO Atheros drivers are being compiled into the kernel, why? its there.

Walt

Because the default configs haven't been updated yet.

From literally the post prior to yours.

> **JMB74 said:**
> Well, the RCs are still being built based on the 3.7 ubuntu kernel configs, which are not compatible with setting the Atheros drivers to build on the 3.8 kernels.

Hopefully the kernel team will soon rebase the ubuntu raring kernel to 3.8 (already done in master-next git) soon and update configs accordingly. The RC builds in the kernel-ppa would then pull in the correct configs and build the Atheros drivers. 

I've been doing my own kernel builds in the meantime correcting the configs, and can confirm that once done the 3.8 kernel plays nicely with my Atheros card. :)

---

### Post by zika on 2013-01-05
It seems that I'm in... ;)

---

### Post by iniside on 2013-01-05
I installed the newest rc2 version of kernel, but it seems to have problems with recognizing my USB keryboard and mouse (they just don't work).
Anyone had such problem ?

---

### Post by Intrepid Ibex on 2013-01-05
Because the Ubuntu Kernel Team (or some smaller part of it) apparently got in their heads that nobody cares about the configs as long as you get the new kernel.

---

### Post by irishbandit on 2013-01-05
Edit the config the way you want!!
##comments## commands are **Bold**
##You can dl 3.8rc2 from here
[http://www.kernel.org/pub/linux/kernel/v3.0/testing/linux-3.8-rc2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/testing/linux-3.8-rc2.tar.bz2)
##then extract it
**cd linux-3.8-rc2**
##then copy old config for a starting point
[B]cp -vi /boot/config-`uname -r` .config
make oldconfig[/B]
##then make changes that you want
**make menuconfig**
##set how many cores to use, how ever many cores you have plus 1
**export CONCURRENCY_LEVEL=5**
##make the kernel
**fakeroot make-kpkg --initrd kernel-image kernel-headers**
##then install
[B]cd ..
sudo dpkg -i *.deb[/B]
## This way you can build it the way you want.

---

### Post by wnelson on 2013-01-06
make localmodconfig

Only configures the currently used modules of active kernel. Some added modules are there for you removal also it is just a bit quicker of cleaning up for next compile.

walt

---

### Post by JMB74 on 2013-01-09
[https://wiki.ubuntu.com/KernelTeam/Meeting/2013-01-08](https://wiki.ubuntu.com/KernelTeam/Meeting/2013-01-08)

> **Status: Raring Development Kernel**

 We have rebased the Raring kernel to the latest v3.8-rc2 upstream kernel.  We have held off on uploading until we have resolved some DKMS package build failures.  Everyone should also review the ubuntu-raring/dropped.txt file to review anything that may have inadvertantly gone missing after the rebase. Important upcoming dates: 
[LIST]
[*]Raring:
[LIST]
[*]Fri Jan 18 - 13.04 Month 3 Milestone (1 week)
[*]Mon Feb 18 - 13.04 Month 4 Milestone (~6 weeks)
[/LIST]
 
[*]Precise:
[LIST]
[*]Thu Jan 10 - 12.04.2 Kernel Freeze (~2 days)
[*]Thu Feb 14 - 12.04.2 Release (~5 weeks)
[/LIST]
 
[/LIST]
We should have the last DKMS issues fixed tomorrow. We may have -rc3 by then as well. 

---

### Post by craig10x on 2013-01-09
Would one of you 13.04 testers post a message to this thread when you notice that they have uploaded the 3.8 kernel?  Would appreciate it, i want to check out the live session on the daily build when it is on there....

Thanks :)

---

### Post by cariboo on 2013-01-09
3.8-rc3 just showed up in the ppa, I'm just about to install it.

**Edit:** I'm up and running again without any hiccups. :-D

```
cariboo@alexis:~$ uname -a
Linux alexis 3.8.0-030800rc3-generic #201301092235 SMP Thu Jan 10 03:36:25 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by JMB74 on 2013-01-10
[https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Raring](https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Raring)

> We have rebased our Raring kernel to the latest upstream v3.8-rc2 Linux  kernel.  We are holding off on uploading until we resolve some DKMS  package build failures.  We anticipate these being resolved by end of  week and will plan to upload shortly thereafter.  This will be the first  v3.8 based Raring kernel uploaded to the archive.  We will continue to  remain on the v3.8 kernel for the remainder of the 13.04 cycle. 

---

### Post by craig10x on 2013-01-10
Would appreciate it if someone posts here when it is officially added to the 13.04 build....

Thanks ;)

---

### Post by JMB74 on 2013-01-10
1st 3.8 upload to the main ubuntu repos. :D

[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.1](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.1)

---

### Post by sacridex on 2013-01-10
> **JMB74 said:**
> 1st 3.8 upload to the main ubuntu repos. :D

[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.1](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.1)
Still kept back. :(

---

### Post by zika on 2013-01-10
> **sacridex said:**
> Still kept back. :(
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2)

---

### Post by JMB74 on 2013-01-10
Currently building. :D

For those that have been suffering from no Atheros wireless drivers in the mainline ppa builds, this upload/rebase should I hope fix that.

---

### Post by craig10x on 2013-01-10
hmmm...i wonder if the kernel would be on today's daily build...or would it be better to check it on friday?

---

### Post by JMB74 on 2013-01-10
> **craig10x said:**
> hmmm...i wonder if the kernel would be on today's daily build...or would it be better to check it on friday?

Well, since it's not even finished building, it's not going to be on today's.

It could be on tomorrows maybe.

As said previously, it's easy to check by downloading the .manifest file which is a few KB and listed all the packages and versions included in that daily build.

---

### Post by rtalcott on 2013-01-10
raring amd64 Successfully built (NEW)

---

### Post by craig10x on 2013-01-10
Thanks for the tip, jmb74...i will check it tomorrow :)

---

### Post by cariboo on 2013-01-10
@craig10x, you could subscribe to the [raring-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Raring-changes"), and get the info the same time as everyone else.

---

### Post by craig10x on 2013-01-10
Thank you cariboo907....will do :)

---

### Post by Nburnes on 2013-01-10
Seems it was just pushed as an update. 

```
nburnes@nburnes-GA-MA785G-UD3H:~$ uname -a
Linux nburnes-GA-MA785G-UD3H 3.8.0-0-generic #2-Ubuntu SMP Thu Jan 10 20:14:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by VinDSL on 2013-01-10
> **JMB74 said:**
> Looks like someone messed up configuring and building that (Linux 3.8-rc1) kernel.
Bwahahahaha! You were right!

Just discovered this, tonight...

[INDENT][https://lkml.org/lkml/2012/12/23/75](https://lkml.org/lkml/2012/12/23/75) ( **[COLOR="Red"]EXPLICIT LANGUAGE!!![/COLOR]** )[/INDENT]

Good ol' Linus  :D

---

### Post by cariboo on 2013-01-11
> **VinDSL said:**
> Bwahahahaha! You were right!

Just discovered this, tonight...

[INDENT][https://lkml.org/lkml/2012/12/23/75](https://lkml.org/lkml/2012/12/23/75) ( **[COLOR="Red"]EXPLICIT LANGUAGE!!![/COLOR]** )[/INDENT]

Good ol' Linus  :D

I have to agree, that is classic Linus. :-D

---

### Post by JMB74 on 2013-01-11
With the update to 3.8 configs, the daily build now appears to have working Atheros wireless drivers.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

Same should apply on the next RC build.

---

### Post by JMB74 on 2013-01-11
> **craig10x said:**
> Would appreciate it if someone posts here when it is officially added to the 13.04 build....

Thanks ;)

It is in todays live build.

[http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.manifest)

> lightdm    1.4.0-0ubuntu2 
lightdm-remote-session-freerdp    1.0-0ubuntu2 
lightdm-remote-session-uccsconfigure    1.1-0ubuntu2 
lintian    2.5.11ubuntu1 
linux-firmware    1.99 
linux-generic    3.8.0.0.13 
linux-headers-3.8.0-0    3.8.0-0.2 
linux-headers-3.8.0-0-generic    3.8.0-0.2 
linux-headers-generic    3.8.0.0.13 
[COLOR=DarkOrange][B]linux-image-3.8.0-0-generic    3.8.0-0.2 
linux-image-extra-3.8.0-0-generic    3.8.0-0.2 [/B][/COLOR]
linux-image-generic    3.8.0.0.13 
linux-libc-dev:amd64    3.8.0-0.2

---

### Post by ventrical on 2013-01-11
> **VinDSL said:**
> Bwahahahaha! You were right!

Just discovered this, tonight...
[INDENT][https://lkml.org/lkml/2012/12/23/75](https://lkml.org/lkml/2012/12/23/75) ( **[COLOR=Red]EXPLICIT LANGUAGE!!![/COLOR]** )[/INDENT]Good ol' Linus  :D

heheh .. thanks VinDSL..There is a certain amount of redemption there. And I thought I was bad  during the days of my BBS career ! lol :)

---

### Post by craig10x on 2013-01-11
Thank you JMB74 i was just going to check...i am downloading this iso now ;)

---

### Post by John_Swing on 2013-01-11
Hello,

My CPU is about 7°C (idle) warmer with Linux 3.8-rc3 than with 3.7. Is this a known bug ?

---

### Post by cariboo on 2013-01-11
My AMD X2 240 cpu is idling around 42° which is about the same as 3.8rc1, I haven't cleaned the cpu fan for about 6 - 8 months so I should see a temperature drop after doing that.

---

### Post by JMB74 on 2013-01-12
CPU temps have been consistent with previous kernels for me. 

I vaguely recall a bug (late 3.7 or early 3.8?) where the notify process hung and constantly maxed out one core. 

But I presume the cpu load would have been the 1st thing you checked. Especially as you say this occurs at "idle".

---

### Post by John_Swing on 2013-01-12
> **JMB74 said:**
> CPU temps have been consistent with previous kernels for me. 

I vaguely recall a bug (late 3.7 or early 3.8?) where the notify process hung and constantly maxed out one core. 

But I presume the cpu load would have been the 1st thing you checked. Especially as you say this occurs at "idle".

Yes the CPU load is normal with both kernels, but 3.8 (around 53°C) definitely makes the CPU warmer than 3.7 (around 46°C).

---

### Post by manulemaboul on 2013-01-12
> **John_Swing said:**
> Yes the CPU load is normal with both kernels, but 3.8 (around 46°C) definitely makes the CPU warmer than 3.7 (around 53°C).

Well, that's cooler :).

---

### Post by John_Swing on 2013-01-12
Sorry, I switched the two values ! ;)

---

### Post by John_Swing on 2013-01-12
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098874") the bug report I submitted for my overheating problem. Can someone help me add the necessary information for it to be complete ?

Thanks in advance.

---

### Post by zika on 2013-01-13
We've got ourselves lowlatency 3.8 also... Nice...

---

### Post by kevpan815 on 2013-01-13
How do you guys check the Temperature of the CPU and Hard Disk? Right now I am running the Latest Nightly Build on a Solid State Drive and am curious if there are going to be any problems with it?

---

### Post by VinDSL on 2013-01-13
> **kevpan815 said:**
> How do you guys check the Temperature of the CPU and Hard Disk?
Personally, I use Psensor...

---

### Post by cariboo on 2013-01-13
+1 to psensor, I took VinDSL's advice, and installed it a while back.

---

### Post by John_Swing on 2013-01-13
I use psensor too for CPU temps and hddtemp for hard drives.

---

### Post by VinDSL on 2013-01-13
As you can see, my HDD is quite chilly.  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-13-jan-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-jan-2013-2.png")[/INDENT]

---

### Post by irishbandit on 2013-01-13
I missed the update on 1-10-2013 for nvidia-current_313.09 xedgers
    - Add support for Linux 3.8.
[https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2921174/+listing-archive-extra](https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2921174/+listing-archive-extra)

Any way 313.09 works with 3.8rc3, and I assume 1 and 2.

For the hardware temps I use Hardware Sensors Indicator.
[https://launchpad.net/indicator-sensors](https://launchpad.net/indicator-sensors)

---

### Post by serdotlinecho on 2013-01-13
System monitor? Nagios...lol

---

### Post by zika on 2013-01-14
For quite some time I did not have my machine boot so quick (less than 20 sec. from boot screen to tty1 prompt (I use xinit) and awesome is up in a blink)...
```
Linux xx...xx 3.8.0-0-lowlatency #1-Ubuntu SMP PREEMPT Fri Jan 11 19:45:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by VinDSL on 2013-01-18
3.8-rc4 is available now...  ;)

**EDIT**

Working fine!

Hrm...

I wonder when those pesky KMOD errors are going to disappear?!?!?

---

### Post by jppr on 2013-01-18
> **VinDSL said:**
> 3.8-rc4 is available now...  ;)

**EDIT**

Working fine!

Hrm...

I wonder when those pesky KMOD errors are going to disappear?!?!?

It is soon in repos...

[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-1.5](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-1.5)

---

### Post by Starks on 2013-01-19
I'm having a speed regression with Intel wireless.

---

### Post by loukingjr on 2013-01-20
3.8.0-1.5 is broken in VirtualBox :( 

edit: VirtualBox can't build the guest additions with the matching headers.

---

### Post by rrnbtter on 2013-01-20
Greetings,

> **loukingjr said:**
> 3.8.0-1.5 is broken in VirtualBox :(  .

Works fine for me with 3.8 RC4 Running

---

### Post by loukingjr on 2013-01-20
> **rrnbtter said:**
> Greetings,



Works fine for me with 3.8 RC4 Running
3.8.0-0 worked fine for me as well. the problem seems to be 3.8.0-1.5 which is in the repos

---

### Post by iniside on 2013-01-22
New version from ubuntu repository still doesn't work with my USB keryboard and mouse.
Although after compiling manually it works fine.

---

### Post by Starks on 2013-01-22
iwlwifi regression

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1103314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1103314)

---

### Post by VinDSL on 2013-01-25
Linux 3.8-rc5 is available now...  ;)

---

### Post by jppr on 2013-01-26
> **VinDSL said:**
> Linux 3.8-rc5 is available now...  ;)

You are right, it´s soon in repos
[https://lists.ubuntu.com/archives/raring-changes/2013-January/004793.html](https://lists.ubuntu.com/archives/raring-changes/2013-January/004793.html)

---

### Post by ft_ on 2013-01-26
it is in the repos...
I'll check the wired ethernet bug (which affects me and others only in previous version).

---

### Post by loukingjr on 2013-01-26
> **ft_ said:**
> it is in the repos...
I'll check the wired ethernet bug (which affects me and others only in previous version).
hmmm, why isn't it in my repos?

---

### Post by ronacc on 2013-01-26
not seeing it here either (64bit)  tried both US and Main servers .

---

### Post by ft_ on 2013-01-26
I use the main server, amd64.
```
uname -a
Linux pignolo 3.8.0-2-generic #6-Ubuntu SMP Fri Jan 25 22:03:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
I'm still experiencing the same bug : the wired ethernet does not work at all, the "cable is not plugged in". Argh.
```
sudo ifup eth1
Ignoring **unknown interface** eth1=eth1.

```
:-\"
On 3.8.0-0 it is ok, but not in 3.8.0-1 and -2.

---

### Post by VinDSL on 2013-01-26
> **ft_ said:**
> I'll check the wired ethernet bug (which affects me and others only in previous version).
I started experiencing "wired ethernet" problems with >= Linux 3.2

I tried everything, for weeks, but the problem(s) persisted.

Eventually, I installed a [Netgear PCI Ethernet card]("http://support.netgear.com/product/FA310TX") with a real DEC "Tulip" chipset, and life has been good ever since.

I haven't reverted back to the pseudo, southbridge-driven, onboard LAN device, in this machine.  So, I don't know if it works with Linux 3.8 or not -- but, I doubt it.

In my mind, there could be a few culprits here:

[LIST]
[*]network-manager (wired LAN connection worked fine with WiCD, but not with NM)

[*]Linux kernel (older kernel(s) worked fine with network-manager, but not Linux 3.2 and newer)

[*]My onboard Intel LAN controller is no longer supported by NM and/or newer Linux kernels.
[/LIST]

Anyway, using a NIC with a "real" chipset, instead of a pseudo LAN device, took care of my "wired ethernet" issues.

Just saying...  ;)

---

### Post by ft_ on 2013-01-26
quite hard in a laptop to do that. ;)
And my hardware is Intel's (e1000e driver), not exotic at all.
I may be wrong, but imho it's clearly a kernel issue.
I do not know if an Ubuntu bug report is already done ? It is a critical issue.

---

### Post by dino99 on 2013-01-26
Get new issues with nvidia driver:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1106117](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1106117)

---

### Post by VinDSL on 2013-01-26
> **ft_ said:**
> quite hard in a laptop to do that. ;)
And my hardware is Intel's (e1000e driver), not exotic at all.
Mine is an Intel 1000T.  It's not exotic either, but...

That controller is going on 12 years-old, and I *think* the Linux maintainers clear out the cruft, from time-to-time.

My DEC "Tulip" card is equally non-exotic and old (I see them all the time at Goodwill for $4.99 USD), but...

There are zillions of DEC chipsets still being used in enterprise servers, et cetera.  If they quit supporting "Tulip" chipsets, everything would come crashing down like a house of cards. So, it's a safe bet, "they" aren't going to strip support any time soon.

If it was me, I'd replace network-manager with WiCD, and see it that gets you back online...  ;)

---

### Post by ft_ on 2013-01-29
Somebody here wrote a workaround that I quote here.
So :
1- do a ```
lspci
``` to note the ethernet controller pci number
2- go to ```
/sys/devices/pci0000:00/0000:00:xx.0/power
``` where xx is the above number
3- edit the ```
control
``` file and put ```
on
``` instead of ```
auto
```

This operation needs to be done again back from suspend.
Is there a bug report about that ?

---

