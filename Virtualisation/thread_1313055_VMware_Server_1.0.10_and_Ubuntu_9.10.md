---
title: "VMware Server 1.0.10 and Ubuntu 9.10"
date: 2009-11-03
forum: Virtualisation
---

### Post by fjgaude on 2009-11-03
Has anyone got the title combo to work?

---

### Post by lukebuntu on 2009-11-04
I have just tried a fresh installation of VMware Server 1.0.10 on Karmic... No way :sad:

---

### Post by and1251 on 2009-11-04
the same result: not working

---

### Post by fjgaude on 2009-11-04
No way! I uninstalled Player 3.0, which works perfectly, and then tried Server 1.0.10, no way with kernel 2.6.31-14.

Gosh, that new installer is progress I guess. <smile>

Anyway, I'll keep a partition with 1.0.9 on it just to be sure I can make new VMs. But it seems Player 3.0 can do that. And it runs with 2 or more CPUs and handles accelerated graphics! Maybe the Server is no longer needed, at least the non-browser one. <sigh>

---

### Post by lukebuntu on 2009-11-05
Here my next steps...
I will try VMware server 1.0.9 and 1.0.10 with kernel 2.6.28.

Hope to get good news

---

### Post by lukebuntu on 2009-11-05
Little news:

VMware Server 1.0.10 on Karmic works right BUT with kernel 2.6.28 and [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz) patch.

How to...
1. Download patch
2. Install VMware but answer NO when asked to invoke vmware-config.pl; if, during installation process, you get a warning about gcc version, ignore it.
3. Install patch (as superuser); installing patch vmware-config.pl will be invoked automatically

Soon i will try with the newest 2.6.31 kernel

---

### Post by fjgaude on 2009-11-05
Thanks, can you tell us what is new about 1.0.10?

That patch worked on 2.6.28 with 1.0.09.

---

### Post by MichiX on 2009-11-05
To install VMWare Server 1.0.9 on Ubuntu Karmic Coala (9.10) I found the following blog entry very helpful:

[http://www.it-psycho.de/2009/10/09/vmware-server-1-0-9-und-kernel-2-6-31-3/](http://www.it-psycho.de/2009/10/09/vmware-server-1-0-9-und-kernel-2-6-31-3/)

It is easy to apply the patch to Kernel  2.6.31-14 which is shipped with Ubuntu.  Just install the sources:

```
apt-get install linux-source-2.6.31
```and the following packages required to build your own kernel:

```
apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge apt-get build-dep linux
```The following has to be done as root:

```
sudo bash
```Next, unpack the kernel sources:

```
cd /usr/src
tar xvfj linux-source-2.6.31.tar.bz2
```and change to the source directory:

```
cd linux-source-2.6.31
```Now, copy the kernel-config you use (I use the generic-pae one):

```
cp /boot/config-2.6.31-14-generic-pae .config
```Now, patch the kernel sources manually:

```
  vi arch/x86/kernel/init_task.c
```    after line:
      ```
static struct sighand_struct init_sighand = INIT_SIGHAND(init_sighand);
```    add new line:
      ```
EXPORT_UNUSED_SYMBOL(init_mm);
```  ```
vi include/linux/init_task.h
```    after line:
      ```
extern struct fs_struct init_fs;
```    add new lines:
```
      #define INIT_MM(name) \
      {                                                               \
              .mm_rb          = RB_ROOT,                              \
              .pgd            = swapper_pg_dir,                       \
              .mm_users       = ATOMIC_INIT(2),                       \
              .mm_count       = ATOMIC_INIT(1),                       \
              .mmap_sem       = __RWSEM_INITIALIZER(name.mmap_sem),   \
              .page_table_lock =  __SPIN_LOCK_UNLOCKED(name.page_table_lock), \
              .mmlist         = LIST_HEAD_INIT(name.mmlist),          \
              .cpu_vm_mask    = CPU_MASK_ALL,                         \
      }
```That's it.  Now you need to build the kernel as documented:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

and install the kernel with

```
dpkg -i linux-image-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb linux-headers-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb
```Don't forget to use the kernel modules provided by IT-Psycho to get VMWare
running.  Here, you might need to change all calls:

```
compat_smp_call_function(LinuxDriverIPIHandler, NULL, 1, 1);
```into:

```
compat_smp_call_function(LinuxDriverIPIHandler, NULL, 1);
```for the files vmmon-only/linux/driver.c and vmmon-only/linux/hostif.c

For better comfort you may want to download the fixed kernel (only based on
generic-pae) and the VMWare module files here:

[http://in-flux.de/docs/linux-image-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb](http://in-flux.de/docs/linux-image-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb)
[http://in-flux.de/docs/linux-headers-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb](http://in-flux.de/docs/linux-headers-2.6.31-14-vmware-pae_2.6.31-14.48_i386.deb)
[http://in-flux.de/docs/vmmon.tar](http://in-flux.de/docs/vmmon.tar)
[http://in-flux.de/docs/vmnet.tar](http://in-flux.de/docs/vmnet.tar)

Best regards,
Michael.

---

### Post by fjgaude on 2009-11-05
Thank you... that's a lot of work... I've decided beacuse of the increased features of VMware Player 3.0 to use it. I can't see why Server 1.0.xx can't be made to work the way the player installs... I intalled Player 3.0, which can create VMs, and with the tools installed is better than anything I've seen from the Server.

Player 3.0 seems to be a cut-down version of Workstation 7.0 ===> like WS 5.0 for Windows; 6.5 for Linux! Wow, all for free.

---

### Post by frankabel on 2009-11-06
Hi all,

Can I use VMware Player 3.0 to connect to a vmware server 1.0.10? I have some servers(8.04LTS) with vmware server 1.0.10 and want manager it from a desktop pc with 9.10.

Cheers
Frank Abel

---

### Post by fjgaude on 2009-11-06
I'm not in a position to try what you want but Player 3.0 has NAT, brigded, and local net capabilities, and can open any vmx file created by any vmware product. So why not simply trying it?

---

### Post by frankabel on 2009-11-06
Thanks fjgaude,

You see some option to connect to a remote server? If don't have that options, can't be used as client for vmware server 1.0.10

Cheers
Frank Abel

---

### Post by fjgaude on 2009-11-06
Okay, I've looked at all the options of Player 3.0, running under 9.10, and can't see anyway to connect to a client down the LAN... so I think you have to seek another way.

---

### Post by frankabel on 2009-11-06
Thanks again fjgaude, I will try with the MichiX steps then.

Cheers
Frank Abel

---

### Post by fjgaude on 2009-11-06
Yes, I will too, but I'm gonna wait at least two months to see if someone comes up with a better, easier way to get 1.0.10 to work with kernel 2.6.31.

Thanks, MichX, for making it clear what whas to be done.

---

### Post by nathanlhc on 2009-12-15
I found a tutorial for how to install vmware server 1.0.10 on an ubuntu 9.10 desktop.

Here is the link [http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop](http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop)

---

### Post by fjgaude on 2009-12-15
I'm still waiting, but thanks for the link... we've seen similar... kernel 2.6.31-16 is out... I'm staying with Player 3.0 as it doesn't need to use nm to get down the LAN, it stays local.

---

### Post by shairozan on 2009-12-15
Is there any specific reason you're still using server 1? Server 2 is a pretty nice system. We run it for production where I work until we decide if ESX is worth the investment.

---

### Post by fjgaude on 2009-12-15
Well, the few times I tried Server 2.0.x I didn't like even the idea of a browser working with it, what with the interface being so nice with 1.0.x

I'm a one-person shop and use Server to go down the LAN to run a VM. On my main box I now use Player 3.0, which seems to work with an kernel as they get updated.

That's about it.

---

### Post by tester321 on 2010-05-27
(I know this is a bit late)

Have to agree with fjgaude, vmware server 1.0.x >> 2.x, in my opinion and for my purposes.

Thanks for the patching info!  I am going to try it on a Netbook that I had to install 9.10 on (to support various hardware), but could not get 1.0.x working on.

---

