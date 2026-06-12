---
title: "Using the 2.6.33-rt kernel series on Ubuntu Lucid"
date: 2010-05-02
forum: Ubuntu Studio
---

### Post by trulan on 2010-05-02
Notes: There has been a lot of discussion as to the status of the Real Time kernel in Ubuntu Lucid and Ubuntu Studio Lucid.  Due to the timing of Ubuntu releases, Linux kernel releases, and Real Time Preemption patch releases, there is no full real time preemption patch available for the Lucid kernel (2.6.32).  Not to worry, there are other options.

**1. (64 bit users only)** There is a low-latency preempt kernel available.  This is the default kernel for an installation of Ubuntu Studio with the audio package.  It can also be installed by selecting **linux-preempt** and **linux-headers-preempt** in Synaptic Package Manager.

**2.** The Real Time kernel from Ubuntu Karmic (2.6.31-10-rt) is available in the Lucid repository, and can easily be installed via Synaptic Package Manager.
 
**3.** 2.6.33-rt can be installed from a ppa:
[https://launchpad.net/~bojo42/+archive/rt]("https://launchpad.net/%7Ebojo42/+archive/rt")
Or, from this one:  (Attention NVidia and ATI users:  Patched drivers are here!!)
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)

[CENTER]--------------------------------------------------------------------------------[/CENTER]

Known issues: (and workarounds)
1. NVidia drivers - module fails to build.
[SOLVED] Install nvidia-graphics-drivers from falktx's ppa:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)
If you have already installed the nvidia driver, you'll need to uninstall it before using the ppa version.  Be sure to run 'sudo nvidia-xconfig' after installing.  Then, reboot.

2. ATI drivers - module fails to build.
[SOLVED] Install fglrx-installer from falkTX's ppa:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)
If you already installed the drivers direct from ATI, you'll need to uninstall those before installing the ppa version.  Be sure to run 'sudo aticonfig --initial' after installing.  Then, reboot.

2. Broadcom driver - module fails to build, just needs one small edit:
[http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=20056&start=0&postdays=0&postorder=asc&highlight=](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=20056&start=0&postdays=0&postorder=asc&highlight=)

3: VMWare player - several modules fail, here's a patch:
[http://communities.vmware.com/message/1515928](http://communities.vmware.com/message/1515928)
This patch has a typo and misnames a file.  After running the patch, rename /usr/lib/vmware/modules/source/vblock.tar to vmblock.tar
[CENTER]--------------------------------------------------------------------------------[/CENTER]

**The original purpose of this post was for those who wanted to compile their own RT kernels.  That's not necessary anymore, but the instructions are here for anybody who may still find them useful.**
[B]
4.[/B] You can manually compile the 2.6.33-rt kernel and headers.

sources for this guide:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://www.nescivi.nl/?p=111](http://www.nescivi.nl/?p=111)
Horo's rt kernel for Sidux: (should work in Ubuntu, use at your own risk.)
[http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=9396&start=90](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=9396&start=90) 

Preparation:  Install a few packages.
```
sudo apt-get install fakeroot build-essential kernel-package
```Building the kernel:
note:  the kernel architecture (i386, AMD64) will be the same as the currently running system.

1. Download the source.  Find it here:
**mainline kernel source:** [http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)
**rt patch:** [http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/)
Make sure the version numbers of the kernel source and the rt patch are the same!!
(I create a /home/<username>/Downloads/kernel directory and put everything in there.)
Extract the kernel source and the rt patch.  Rename the extracted kernel source directory from linux-2.6.33.4 to linux-2.6.33.4-rt20.
Open a terminal and go to that directory - we'll run our commands from there.
```
cd /home/<username>/Downloads/kernel/linux-2.6.33.4-rt20
```2. Apply the rt patch:
```
cat /home/<username>/Downloads/kernel/patch-2.6.33.4-rt20 |patch -p1
```3. Configure the kernel:
```
make oldconfig
```(copies the configuration of the currently running kernel, asking questions about any new items.  The default selection will be capitalized - it's usually safest to select the default unless you know what you are doing.  Be sure to select 'Complete Preemption (Real Time)')
*Note:  If you install 2.6.33-rt from one of the ppa's above and build your new kernel from there, 'make oldconfig' should complete with no questions asked.*

```
make menuconfig
```(lets you further tweak kernel configuration)
    Essential changes:  (kernel build will fail unless these changes are made)
    Under device drivers/staging drivers, de-select Data acquisition support (comedi).
    Under device drivers/staging drivers, de-select POHMELFS filesystem support.
    
Suggested tweaks:
Under Processor Type and Features, set Timer frequency to 1000 Hz.  This will improve real time performance.
Under Processor Type and Features, make sure you have Preemption Mode set to Complete Preemption (Real Time).
    Under kernel hacking, de-select 'compile kernel with debug info'.  Not doing so results in an unnecessarily large kernel.
    Under kernel hacking, de-select tracers.  This eliminates a warning message on bootup and may help to keep latencies down.
```
make-kpkg clean
```(Removes allergy-causing dust mites from the package?  I don't know.  Some places suggest running this command, and it doesn't take long.)

3. Build the kernel:  (And be prepared to wait a while)
```
time fakeroot make-kpkg --initrd kernel-image kernel-headers
```4. Fix the kernel postinstall scripts:  (Only needs to be done the first time you build your kernel)
```
sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postinst.d/initramfs /etc/kernel/postinst.d/
```    (If this is not done, no initrd image will be generated and booting will fail.)
```
sudo mv /etc/kernel/postinst.d/nvidia-common /etc/kernel/postinst.d/nvidia-common.bak
```    (The nvidia-common script will cause installation to fail.)

5. Install the packages!  (kernel-image first, then kernel-headers.)
They will be in the same directory as your kernel source directory.  I usually double-click them in Nautilus and let gdebi do the installation.

With any luck, you should be able to reboot into a working system on the new kernel.

---

### Post by sgx on 2010-05-02
You've been busy! Thanks for putting things in order!
I'll look for your next book at Barnes&Noble.
There are 8 monthly linux magazines at the B&N here, you
should cash in :D

---

### Post by eric71 on 2010-05-03
I installed Ubuntu 10.04 this weekend, and I have tried the kernel made by Horo at the Sidux forums that you linked to above. I have been using his kernels in Mepis 8.5 for a while now. It installed and boots and seems to work fine in Ubuntu as well. Not sure if the performance is any better than the old Ubuntu 2.6.31-rt kernel. So I think it's definitely a good option for those (like me) that don't like to get their hands dirty rolling their own kernels.

I'm having other problems running Reaper with wineasio (tons of xruns and static). I'm not sure why that is, and haven't figured it out yet, but it happens with both the Horo kernel and the old Ubuntu RT kernel, so it's not a kernel issue. I've used both kernels before.

And just an edit: I installed only the kernel image package, if I recall there was some dependency issue with the metapackage or headers.

---

### Post by lunaparadox on 2010-05-03
I got my new kernel booting but can't get nvidia driver to install what do I need to do to get the 96.* driver to install. all help is appreciated thanks.

---

### Post by trulan on 2010-05-04
To fix the nvidia drivers, you need to make two changes to the nv-linux.h file in the driver package.  (I don't know how this will affect using the nvidia driver with the generic kernel.)

I got the 96 driver to build, but I can't actually test it.  Here's how I got it to build.  This should work for any current nvidia driver.

1. Download the latest  driver package from nvidia.

2. Extract it:
```
sh NVIDIA-Linux-x86_64-96.43.16-pkg2.run -x
```3. Fix nv-linux.h
```
gedit ./NVIDIA-Linux-x86_64-96.43.16.pkg2/usr/src/nv/nv-linux.h
```search for atomic_spinlock.  Change all instances of atomic to raw in the following few lines of code.  When you're done, it should look like this:
```
#if defined(CONFIG_PREEMPT_RT)
typedef raw_spinlock_t         nv_spinlock_t;
#define NV_SPIN_LOCK_INIT(lock)   raw_spin_lock_init(lock)
#define NV_SPIN_LOCK_IRQ(lock)    raw_spin_lock_irq(lock)
#define NV_SPIN_UNLOCK_IRQ(lock)  raw_spin_unlock_irq(lock)
#define NV_SPIN_LOCK_IRQSAVE(lock,flags) raw_spin_lock_irqsave(lock,flags)
#define NV_SPIN_UNLOCK_IRQRESTORE(lock,flags) \
  raw_spin_unlock_irqrestore(lock,flags)
#define NV_SPIN_LOCK(lock)        raw_spin_lock(lock)
#define NV_SPIN_UNLOCK(lock)      raw_spin_unlock(lock)
#define NV_SPIN_UNLOCK_WAIT(lock) raw_spin_unlock_wait(lock)
#else
```Then search for semaphore_init.  The first thing it finds should be this section:
```
#if defined(CONFIG_PREEMPT_RT)
#define NV_INIT_MUTEX(mutex) semaphore_init(mutex)
#else
```Change semaphore_init to sema_init and add a 1 after mutex, like this:
```
#if defined(CONFIG_PREEMPT_RT)
#define NV_INIT_MUTEX(mutex) sema_init(mutex,1)
#else
```Save the file and close gedit.

4. Then you can run ```
make module
``` and it should build successfully.  Or, you can skip that and execute (without x running) nvidia-installer in the top directory of the driver package.  Don't run sh NVIDIA-blah.blah as this will overwrite your changes.

Post back if it works.  Good luck!

---

### Post by lunaparadox on 2010-05-04
tried that and all was going well until I did the make module. got a message telling me to run make mrproper on the kernel dir after doing that now just spits out
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
 
I'm thinking I should not have ran the make mrproper command but not sure.

---

### Post by trulan on 2010-05-04
Are you attempting to build the module while running the new kernel?  I think I left out that part.

What happens if you boot 2.6.33.3-rt* into recovery mode, drop to a root shell, navigate to the nvidia driver's directory, and run nvidia-installer?

---

### Post by lunaparadox on 2010-05-04
there is no nvidia installer in the directory. so I need to boot to the recovery rt kernel? I am running the rt kernel while  I'm doing the above that is wrong?

---

### Post by trulan on 2010-05-04
No that's right, you should be running the RT kernel when you run the installer or build the module, otherwise you'll need to specify the kernel version to build on.  Using a root shell in recovery mode just makes it easier to install, because X never gets started and you need to be root to install the driver module anyway.

You should find nvidia-installer in /NVIDIA-Linux-x86_64-96.43.16.pkg2/, which was created when you extracted the package.

Oh, another thing - mine failed on first attempt because I had downloaded the 32 bit driver and I have a 64 bit system.  But that threw a different error.

---

### Post by lunaparadox on 2010-05-04
yeah I'm using the 32bit driver. running in the new rt kernel. the nvidia installer isn't in the /nvidia-96-96.43.17 directory would it be called somthing else in the 32bit ver.?

---

### Post by lunaparadox on 2010-05-04
ok so I was having a blond moment the installer is there. went through the recovery kernel and tried to run it but failed making the kernel module.

---

### Post by fedexnman on 2010-05-05
nice post,thx i might actually try this and get my feet a little wet here, and learn somemore linux stuff . lucid kinda reminds me of the 8.10 release a little (my 1st ubuntu install). im dual booting ubuntustudio karmic and lucid .  im glad i didnt install over karmic.

---

### Post by scotty64 on 2010-05-06
> **trulan said:**
> 
**1. (recommended)** There is a low-latency preempt kernel available.  This is the default kernel for an installation of Ubuntu Studio with the audio package.  It can also be installed by selecting **linux-preempt** and **linux-headers-preempt** in Synaptic Package Manager.  This should meet the needs of most users.


these packages do not exist on my system. I am using Kubuntu. The only available rt-kernel is the old one from Karmic that does not work with snd-hda-intel.
Do I need a ppa or another repo to get the preempt kernels ?

---

### Post by trulan on 2010-05-06
Oh...the preempt kernel is only available for 64 bit.  That's strange - I guess the dev's know what they are doing.

The only RT kernel I know of in a ppa is here:
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)
It's a bit more recent than the one in the Lucid repos, but it's still the same kernel series as Karmic.

---

### Post by soundcheck on 2010-05-11
Just installed the 2.6.33.3-rt19 on a headless streaming audio client  based on FitPc2.

Works like a charm. IMO better then the mainline 2.6.31-rt.

THX for the Nvidia tip to avoid making the image install fail.
However the headers install still fails, since it also runs that dkms install. Though that didn't have much of impact on the headers install.
I could install Alsa 1.0.23 afterwards without any problems. 

BTW: Somehow "make localmodconfig" for a minimalistic .config  failed all the time. Anybody around who made it work?

Cheers

---

### Post by scotty64 on 2010-05-11
> **soundcheck said:**
> Just installed the 2.6.33.3-rt19 on a headless streaming audio client  based on FitPc2.
Works like a charm.


Where did you get that kernel from? Self compiled or is there a ppa / repo?

SOLVED: It showed up in the package manager today.

---

### Post by trulan on 2010-05-13
As you may have noticed, there is a brand new 2.6.33-1.1-realtime kernel available in Alessio Igor Bogani's ppa.
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)
So anybody who's been wanting to try this kernel now has another way to do it besides compiling it manually.

Feel free to use this thread to discuss issues with using this kernel.  (NVidia drivers, etc.)

---

### Post by ruhtranayr on 2010-05-31
> **trulan said:**
> As you may have noticed, there is a brand new 2.6.33-1.1-realtime kernel available in Alessio Igor Bogani's ppa.
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)
So anybody who's been wanting to try this kernel now has another way to do it besides compiling it manually.

Feel free to use this thread to discuss issues with using this kernel.  (NVidia drivers, etc.)

Thanks a lot! Installing now....

---

### Post by ken78724 on 2010-05-31
Just installed Post 1 Option 1 via synaptic package manager, but what follows? Will I be able to run? :popcorn:

---

### Post by ken78724 on 2010-05-31
Trulan

[QUOTE=ken78724;9391051]synaptic package manager/QUOTE]installs helped but left questions like sound, seeing videos and more unanswered. How do you confirm that linux-preempt and linux-headers-preempt were in fact installed & then, how many of the steps given in Post #1 are also added. Guess it's my 71st birthday or something that leaves me in a quandary. 

If you can, tell me more about just installing linux-preempt and linux-headers-preempt....  Many thanks.

Kenneth

---

### Post by caffeinegum on 2010-06-01
> **trulan said:**
> 
 
**3.** 2.6.33-rt can be installed from several ppa's:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")
[https://launchpad.net/~bojo42/+archive/rt]("https://launchpad.net/%7Ebojo42/+archive/rt")




Sorry to chime in here with a silly question, but what exactly is the difference between these two repositories? Is  the one 'vanilla'? :P

Edit: Just installed the rt kernel from bojo42's PPA. Everything works fine it seem, minus wireless. I'm guessing this is why you guys are brewing your own kernel?

---

### Post by trulan on 2010-06-01
@ken:  Is something not working that you're trying to fix?  You shouldn't see any differences by running a lower latency kernel, unless you were having latency problems in the first place.

When you install a new kernel, you should see it in your grub menu at boot-up.  If the grub menu is hidden, hold 'shift' right after your bios screen.  Then you can choose which kernel to boot.  To check the currently running kernel, do:
```
uname -a
```in a terminal.

@caffienegum:  I don't know what the difference is, except they're packaged by different people.  If one gives trouble, you can always try the other one. There are probably a few minor configuration differences.   At the time I started this thread, this kernel was not available in any  ppa's - so the only way was to build your own.

You said wireless isn't working.  The newer kernel most likely breaks something (like causing a module build to fail), and no, building your own kernel won't help.  I have a broadcom card so I know how to fix those - what is your wireless card?

---

### Post by caffeinegum on 2010-06-02
> **trulan said:**
> 
You said wireless isn't working.  The newer kernel most likely breaks something (like causing a module build to fail), and no, building your own kernel won't help.  I have a broadcom card so I know how to fix those - what is your wireless card?

Ok I see, thanks for clearing that up for me!

I have Broadcom wireless also (BCM4322) and was just having a look at the workaround you posted a link to. Maybe if I am feeling brave this weekend I will give this a try!

I also tried the karmic real time kernel, works fine, only thing I've noticed is the wireless switch doesn't work properly on the side of my laptop (turns off, but will not turn back on again).

---

### Post by bojo42 on 2010-06-03
just to explain the differences between my packages and those from abogani:

a main difference is that i stay with the linux-rt package name so people who already have the RT package installed from universe, will get an update as soon as they add my PPA.

i also try to stay close to the mainline kernels, as we don't have a 2.6.33 kernel in Ubuntu and people should have a kernel with no difference beside RT usage to check if RT is the root of possible problems or not. this means i rebase the kernel configuration against the mainline kernels, so the difference is minimal and contains only needed adjustments.

because of that i leave the staging drivers enabled as far as they compile with the rt patchset, where abogani's package has them disabled completely. regarding RT related kernel configuration we are almost identical since my 2.6.33-3.3 release.

then are some slight changes regarding the packaging itself, but that isn't of interest when you just use the packages.

the last but probably big difference are the used versions of vanilla and the rt patchset. my 2.6.33-3.3 currently is on vanilla 2.6.33.5 and rt22 patchset (i try to keep that up-to-date) where abogani's package is AFAIK on vanilla 2.6.33.3 and rt19.

hope that sheds some light ;)

cheers
bojo42

---

### Post by caffeinegum on 2010-06-05
Bojo, many thanks for explaining everything! Much appreciate all of your hard work! :)

---

### Post by ken78724 on 2010-06-06
No apologies. I got my answer a day after my last post. Update manager asked if I'd consent to install, which I did. Apparently the kernel update met with incompatibility, causing a dark screen +/- crash which I had to report as an xorg fatal server error... Up to then, I thought mine to be solely a stand alone PC w/o having ever installed a server OS. Bugs of the Xorg error brand best be reported by going to System > Administration > Log Viewer File and it helps us all if these get sent to [http://ubuntu.org/X/Reporting](http://ubuntu.org/X/Reporting) if I am recalling correctly. 

Am amidst work arounds but find little to run on to decide what is needed. Unlike bugs that go to launpad.net one appears to need you more and more Trulan and other PPA creators... Thanks to all.

Ken

---

### Post by jwmislan on 2010-06-07
'' Oh, another thing - mine failed on first attempt because I had  downloaded the 32 bit driver and I have a 64 bit system.  But that threw  a different error. ''

  Speaking of different errors, I followed your instructions - manually patching from the diff file to the linux-nvidia.h file and the compile was successful with NVIDIA-Linux-x86_64-195.36.24 .
I copied the new nvidia.ko module installed in /kernel/drivers/video to /lib/modules/2.6.33-3-rt/updates/dkms/nvidia-current.ko .
  Booting up stops at the - ( Ubuntu is running in low graphs mode warning ), so I - ( ctrl+alt+F1 ) to root, and did service gdm stop , then modprobe nvidia-current - checked lsmod to see that it loaded - and it was. Then I did service gdm start - but still Ubuntu is running in low graphics mode message - so I chose  ( restart X ) in the options list - and finely accelerated graphics mode working. 

What a mess to have to go through -  until I figure out why the system insists on ignoring the nvidia-current I put in there, I'l have to do these steps every boot for 2.6.33-rt .

  BTW the 2.6.32-preempt kernel, ( has 1000ms clock set in the config. ), works pretty decent for my real time requirements I was impressed with it. May have to use that until the dust clears around the rt kernels for Ubuntu studio.

Thanks for the help regarding the patch solution.

---

### Post by mango42 on 2010-06-08
> What a mess to have to go through - until I figure out why the system insists on ignoring the nvidia-current I put in there, I'l have to do these steps every boot for 2.6.33-rt .

Seems to be that way for me too - I finally got the 'recommended (195?)' nvidia drivers working on the preemptive kernel - silly me switching to 2.6.33-rt - now I have to start all over again.

This is so weird. I have UbuntuStudio 9.10 running so smoothly on a grungy old T43 Thinkpad - Jack/Hydrogen/Qtractor/ZynSubFx/LV2 plugins - you name it and not an xrun in sight - yet on a sooper-hyper-amd64 laptop with Lucid Studio, Jack chucks out backend xruns even without anything else loaded; Hydrogen sounds like the audio jack socket is broken (it isn't!) - so much distortion,clicks,clacks,plops it's unusable. I haven't even tried the new version of Qtractor yet. The distortion and xrun issue is why I loaded **bojo's** realtime kernel...but maybe it cannot deal with nVidia SLI drivers, I dunno. :confused:

Still, it's all in a very good cause (if this was happening on Wondoze it would have been chucked out the window[tm] by now - just like people are doing with some DJ kit, where they have to reinstall USB drivers every time they reconnect the cable!!) and I ain't complaining - just getting a bit weary...

---

### Post by trulan on 2010-06-08
> **mango42 said:**
> This is so weird. I have UbuntuStudio 9.10 running so smoothly on a grungy old T43 Thinkpad - Jack/Hydrogen/Qtractor/ZynSubFx/LV2 plugins - you name it and not an xrun in sight - yet on a sooper-hyper-amd64 laptop with Lucid Studio, Jack chucks out backend xruns even without anything else loaded; Hydrogen sounds like the audio jack socket is broken (it isn't!) - so much distortion,clicks,clacks,plops it's unusable.
I don't remember if I mentioned this to you before, but I could give the same story about my own old and new laptops.  My issue on the new laptop is, the wireless card shares an irq with my firewire card.  If I have wireless turned on and try to run Jack, forget it.  I don't know if you have looked into the possibilities of an irq conflict or not.  If you haven't, run
```
cat /proc/interrupts
```
and post the output if you want.

---

### Post by mango42 on 2010-06-08
Thanks indeed for the reminder, **trulan** and apologies for being such a pain - I guess my present attitude has a lot to do with septuagenarian brain-*** - lousy excuse {;-)

I'm about to boot up the Alien monster and will get back to you with the **cat** command output - that's assuming I don't have to spend the rest of the day trying to get nVidia to behave...

---

### Post by jwmislan on 2010-06-08
> **trulan said:**
> I   My issue on the new laptop is, the wireless card shares an irq with my firewire card.  If I have wireless turned on and try to run Jack, forget it.  I don't know if you have looked into the possibilities of an irq conflict or not.  If you haven't, run
```
cat /proc/interrupts
```and post the output if you want.

   I can't find it yet in the new grub2, but I had  kopt=pci=routeirq  in my old grub1 menu.lst .
Some kernels were seting different irq's than others, and setting kopt=pci=routeirq usually fixed it on my msi laptop.

Computer
Model            MS-1633X (version MS-1633)
Manufacturer Micro-Star International
Form Factor    Laptop - amd64 dual-core Turion X2 Mobil TL-56,  with Nvidia chip sets 
OS                  Ubuntu - Lucid Lynx/Studio 10.04 - Upgraded from Ubuntu Hardy/Studio 8.04

cat /proc/interupts
         CPU0       CPU1 
 0:          128                54             IO-APIC-edge      timer
  1:          1550             1353        IO-APIC-edge      i8042
  7:             1                      0            IO-APIC-edge    
  8:             0                      1              IO-APIC-edge      rtc0
  9:           6698           15650    IO-APIC-fasteoi   acpi
 12:         52151        47069      IO-APIC-edge      i8042
 14:             0                     0             IO-APIC-edge      pata_amd
 15:           528             96797     IO-APIC-edge      pata_amd
 16:            97              274431   IO-APIC-fasteoi   0000:05:09.0
 17:             0                     3           IO-APIC-fasteoi   ohci1394, mmc0
 18:          7896      5112       IO-APIC-fasteoi   nvidia
 21:             0                    20           IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2
 22:         15385    49662      IO-APIC-fasteoi   sata_nv
 23:             6                   773          IO-APIC-fasteoi   HDA Intel
 27:        179052  22            PCI-MSI-edge      eth0
NMI:           0           0            Non-maskable interrupts

   Yea I'm getting a little frustrated too .. that Lucid-Studio has the conflicting kernel versions, with set System-Administration-Hardware Drivers-nvidia  the ones available from Ubuntu. So far I get kernel-generic-2.6.32, and kernel-preempt-2.6.32 to work with those - but no other kernel versions, it appears, are allowed to work with the provided nvidia drivers.

  I used to download, and  compile the drivers from nvidia on Hardy-Studio with any versions, and number of kernels that I had installed - usually 2 versions of generic, and 2 of rt - one to use and, one in case of problems. I'm wondering if I should go back to that way, and if it will even still work on Lucid.
I wanted to try the Ubuntu Drivers through the menu for a change, figuring it would be more convenient, but if we're locked by code to one set of drivers, and kernels, it's beginning to look problematic. 

  That's the solution I was looking for, we could just easily go with the Ubuntu standard so kernel updates are easier, with less compiling, and more time for our Studio work.
  A little more ( heads-up ) about these user concerns from Ubuntu would be a good thing !!
  
Jwm

---

### Post by psy-man on 2010-06-08
hi,
I am trying to "make" the nvidia-173.14.22 patched as described earlier for the 2.6.33-1-realtime kernel but I am struggling.
When I try to run make in a root shell on the 2.6.33-1 kernel I get this
 
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1

here's what is in /usr/src
/usr/src$ ls
linux-headers-2.6.31-10-rt       linux-rt-headers-2.6.31-9
linux-headers-2.6.33-1-realtime  nvidia-173-173.14.22-patched
linux-realtime-headers-2.6.33-1  virtualbox-ose-3.1.6
linux-rt-headers-2.6.31-10

---

### Post by trulan on 2010-06-08
A little more info on the state of the NVidia drivers and 2.6.33-rt can be found here:
[http://www.nvnews.net/vbulletin/showthread.php?t=148509](http://www.nvnews.net/vbulletin/showthread.php?t=148509)

It would be possible to patch the drivers and put them up in a ppa.  Any takers?  (I haven't got my ppa-ing degree yet...)

---

### Post by mango42 on 2010-06-09
> **trulan said:**
> A little more info on the state of the NVidia drivers and 2.6.33-rt can be found here:
[http://www.nvnews.net/vbulletin/showthread.php?t=148509](http://www.nvnews.net/vbulletin/showthread.php?t=148509)

I came; I saw; I fled ;-)

> It would be possible to patch the drivers and put them up in a ppa.  Any takers?  (I haven't got my ppa-ing degree yet...)

++ 1 :KS

---

### Post by psy-man on 2010-06-09
Trying to make this nvidia module is not much fun, I just don't feel competent, brings it home just how much work all you guy's put into this fantastic os. 
I will to stick with 2.6.31 for the time being. I wish you all the best of luck. Cheers

---

### Post by jwmislan on 2010-06-10
> **jwmislan said:**
> I can't find it yet in the new grub2, but I had  kopt=pci=routeirq  in my old grub1 menu.lst .
Some kernels were seting different irq's than others, and setting kopt=pci=routeirq usually fixed it on my msi laptop.

Computer
Model            MS-1633X (version MS-1633)
Manufacturer Micro-Star International
Form Factor    Laptop - amd64 dual-core Turion X2 Mobil TL-56,  with Nvidia chip sets 
OS                  Ubuntu - Lucid Lynx/Studio 10.04 - Upgraded from Ubuntu Hardy/Studio 8.04

  I used to download, and  compile the drivers from nvidia on Hardy-Studio with any versions, and number of kernels that I had installed - usually 2 versions of generic, and 2 of rt - one to use and, one in case of problems. I'm wondering if I should go back to that way, and if it will even still work on Lucid.
I wanted to try the Ubuntu Drivers through the menu for a change, figuring it would be more convenient, but if we're locked by code to one set of drivers, and kernels, it's beginning to look problematic. 

  That's the solution I was looking for, we could just easily go with the Ubuntu standard so kernel updates are easier, with less compiling, and more time for our Studio work.
  A little more ( heads-up ) about these user concerns from Ubuntu would be a good thing !!
  
Jwm

OK I finely decided to remove all the Ubuntu drivers, and go back to compiling the downloaded Nvidia drivers for each kernel I have installed. I have 2.6.32-generic, 2.6.32-preempt, and the 2.6.33-3-rt .

Side Note: During the compile process for nvidia drivers, it wants to delete your other kernel's nvidia drivers, it does not delete a backup though so, I put a backup next to each in the /lib/modules/kernel#/kernel/drivers/video/nvidia.ko .
I name it like this, nvidia-jwm-backup.ko if nvidia.ko gets deleted, I copy the backup back to nvidia.ko in the same folder. 

I found this post at Ubuntu-Geek -  
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

the post explains how to purge - remove the Ubuntu nvidia drivers, download the newest nvidia drivers, and install them.

Following that, I have everything running beautifully. I had already tried trulan's suggestions for manually patching the extracted NVIDIA-Linux-x86_64-195.36.24-pkg2.run file, and compiling the module. That worked out fine but on reboot I got the ( Ubuntu is running in low graphics ) message window.

Now after removing all the Ubuntu nvidia drivers according to  [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html) ,
and compiling the drivers for 2.6.32 generic, and 2.6.32-preempt, I checked to see if the module I had compiled for the 2.6.33-3-rt was still in /lib/modules/2.6.33-3-rt - it was still there - great.
I rebooted for 2.6.33-3-rt, and it booted straight through to the log in prompt with no problem.
After logged in - checking Ctl-Alt-F1 for a terminal - there was only black screen.
I found out by checking, turns out that there is no vesafb.ko module in the modules folder.
Fix it at boot by grub - edit (e) on the end of linux line remove the vga-791 entry.
 I may try adding a menuentry in custom grub for that kernel - I tried the nvidiafb.ko with fbcon.ko, but that doesn't work - I fixed it always, before by temporarily adding fbcon,and vesafb in the /etc/initramfs-tools/initramfs.conf file, and running update-initramfs, but now there's no vesafb.ko compiled for 2.6.33-3-rt. 

The improvement over the Ubuntu issued nvidia drivers is immediately discernible, with improved image quality, and resource handling.

I am very pleased with the results - was well worth the extra efforts .
    
Thanks to trulan for tips on manually patching the new nvidia driver.

---

### Post by falkTX on 2010-06-17
> **trulan said:**
> A little more info on the state of the NVidia drivers and 2.6.33-rt can be found here:
[http://www.nvnews.net/vbulletin/showthread.php?t=148509](http://www.nvnews.net/vbulletin/showthread.php?t=148509)

It would be possible to patch the drivers and put them up in a ppa.  Any takers?  (I haven't got my ppa-ing degree yet...)

I'll put them on my ppa, but be warned: lots and lots of stuff there :p
[https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid)

Should be ready by the end of the day, I'll let you know how it goes

---

### Post by falkTX on 2010-06-17
It seems that abogani already took care of this bug, and fixed it on his PPA.
The problem now is that his PPA no longer has RT kernel for Lucid (moved to 10.10, Maverick).

I Copied the maverick rt kernel to my lucid PPA and it compiled and runs fine.
It should work you guys that have nvidia cards!

---

### Post by trulan on 2010-06-17
> **falkTX said:**
> It seems that abogani already took care of this bug, and fixed it on his PPA.
The problem now is that his PPA no longer has RT kernel for Lucid (moved to 10.10, Maverick).

I Copied the maverick rt kernel to my lucid PPA and it compiled and runs fine.
It should work you guys that have nvidia cards!
Thanks a whole lot!  You're our hero!!  I'll update the OP to reflect these changes.

I won't have time to test this until next week, for now I'll recommend this on the basis of all your excellent work in the past.

---

### Post by Breambutt on 2010-06-18
Falk for president.

And... fffgdfndfbh I've visited this thread on a regular basis and just now noticed all the NVIDIA stuff, was wondering what I'm doing wrong this time. It is said that sleep deprivation does things to you. ;(

Anyway, cheers to everyone who's bothered doing something for this cause.

---

### Post by falkTX on 2010-06-18
> **trulan said:**
> Thanks a whole lot!  You're our hero!!  I'll update the OP to reflect these changes.

I won't have time to test this until next week, for now I'll recommend this on the basis of all your excellent work in the past.

I also can't test this, no nVidia here (crappy Intel instead...).
Actually for now, it can't be installed, but I'm fixing it now and it should be fixed in ~2hours.

---

### Post by falkTX on 2010-06-18
Weee!

Fixed now!
linux-realtime is now installable!

I'll test it on the weekend!

---

### Post by badvanilla on 2010-06-20
> **falkTX said:**
> Weee!

Fixed now!
linux-realtime is now installable!

I'll test it on the weekend!

I can't wait to hear it's working fine now, any chance to have a feedback ?

---

### Post by falkTX on 2010-06-20
> **badvanilla said:**
> I can't wait to hear it's working fine now, any chance to have a feedback ?

It does work for me, but I'm not using nVidia, so I guess it doesn't count.

---

### Post by trulan on 2010-06-21
> **falkTX said:**
> It seems that abogani already took care of this bug, and fixed it on his PPA.
The problem now is that his PPA no longer has RT kernel for Lucid (moved to 10.10, Maverick).

I Copied the maverick rt kernel to my lucid PPA and it compiled and runs fine.
It should work you guys that have nvidia cards!
????
The kernel installs and boots just fine - in safe graphics mode.  Where are the fixed nvidia drivers?  The dkms module build fails as usual.  Did abogani put up patched drivers somewhere, or am I missing something?

I'd venture a guess that hand-patching /var/lib/dkms/nvidia-current/195.36.24/source/nv-linux.h as I have done previously will make this work, but that's not what I was expecting.  I'm curious as to what bug abogani fixed - and I hope I'm not losing my mind...

---

### Post by Breambutt on 2010-06-22
NVIDIA man here as well, I went to extraordinary lengths just to pull a wedgie on my machine. I've been messing around with this stuff so much that I wasn't even sure if it's my own doing or something wrong with the kernel. Emphasis on "messing", as in unscientific resorts.

On a bright side it seemed extremely stable in safe graphics mode!

---

### Post by falkTX on 2010-06-22
> **trulan said:**
> ????
The kernel installs and boots just fine - in safe graphics mode.  Where are the fixed nvidia drivers?  The dkms module build fails as usual.  Did abogani put up patched drivers somewhere, or am I missing something?

I'd venture a guess that hand-patching /var/lib/dkms/nvidia-current/195.36.24/source/nv-linux.h as I have done previously will make this work, but that's not what I was expecting.  I'm curious as to what bug abogani fixed - and I hope I'm not losing my mind...

I checked the sources, the nvidia patch is there.
Maybe it's not applied ? (I'll look around it soon)

I'm having some trouble getting all kernels to work, but, for now, the v2.6.31-rt seems to work nice.

I want to get the 2.6.32-lowlatency to work first, then I'll focus on 2.6.33-rt.
Also, 2.6.34 is already available too

---

### Post by bluesscream on 2010-06-22
Do the patched for -rt proprietary nvidia drivers work as well in the generic and preempt kernels? 
The original 173.15.25 compiles here successfully even in 2.6.34 and 2.6.35-rc1.
If not I don't see any benefit for patching the more so as I don't need 3D for audio work with rt-kernel and in my old amd64x2/nvidiafx5200 machine I keep using a startup script to select the matching xorg. conf file from two with nvidia resp. nv entries. See: [http://ubuntuforums.org/showthread.php?t=1287967](http://ubuntuforums.org/showthread.php?t=1287967)  
There never will be no all-in-one cofiguration suitable for every purpose.
By my own experiences using the proprietary nvidia graphic driver in no case improves audio performance. On the other hand for video, graphics, gaming, surfing and office applications better reliability can be expected in standard (non rt) kernels (using fitting proprietary nvidia drivers). 
To be honest: Even with all communities help I never succeeded patching nvidiadrivers for not yet supported front-end rt-kernels and I gratefully leave this field to better qualified technical experts ;)

---

### Post by falkTX on 2010-06-22
I think the solution will be to create a new package, something like "nvidia-drivers-rt" with the nvidia patch applied inside the nvidia driver, instead of patching a kernel (bad thing to do!).

The lowlatency kernel is going fine, and should be ready soon.
I should be able to get the v33+nvidia to work soon

---

### Post by hardcopy on 2010-06-22
ive found that the rt kernel doesnt like the fglrx ati driver (or is it the other way round...)

unfortunately for me the basic ati driver wont detect my lcds highest resolution, and installing fglrx with a realtime kernel present causes 'problems' (tried the lucid rt kernel and both from falks repo)

i ended up installing fglrx before installing the realtime kernel, so that even though fglrx doesnt work when im using the rt kernel i still get the highest resolution

window redraw is painfully slow though, can get annoying so im using the preemptive kernel for composition & sound design, and switch to rt when i want to mixdown

theres probably some other way of doing it but its working now and i dont really want to spend another week effing about with terminal (save for tweaking sound performance)

incidentally, when fglrx is running i need the associated kernel wireless backport headers to ensure my wifi works properly and they dont seem to exist for rt kernels

---

### Post by falkTX on 2010-06-22
> **hardcopy said:**
> ive found that the rt kernel doesnt like the fglrx ati driver (or is it the other way round...)

unfortunately for me the basic ati driver wont detect my lcds highest resolution, and installing fglrx with a realtime kernel present causes 'problems' (tried the lucid rt kernel and both from falks repo)

i ended up installing fglrx before installing the realtime kernel, so that even though fglrx doesnt work when im using the rt kernel i still get the highest resolution

window redraw is painfully slow though, can get annoying so im using the preemptive kernel for composition & sound design, and switch to rt when i want to mixdown

theres probably some other way of doing it but its working now and i dont really want to spend another week effing about with terminal (save for tweaking sound performance)

incidentally, when fglrx is running i need the associated kernel wireless backport headers to ensure my wifi works properly and they dont seem to exist for rt kernels


Maybe we should all just use the lowlatency kernel now... it's stable and works with the drivers.

realtime kernels+proprietary drivers is really hard to get going...


I'll see if I can manually patch the nvidia drivers to work in the realtime kernel, but then they will probably fail under a normal kernel...
We'll see how that goes...

---

### Post by falkTX on 2010-06-22
Ok, I've patched the sources of "nvidia-graphics-drivers-173", so the 173-* nvidia drivers may now work with kernel 2.6.33-rt

Please test!

---

### Post by badvanilla on 2010-06-22
> **falkTX said:**
> Ok, I've patched the sources of "nvidia-graphics-drivers-173", so the 173-* nvidia drivers may now work with kernel 2.6.33-rt

Please test!

I've taken the **nvidia-graphics-drivers-173** and the rt kernel on your ppa and still no luck for me...
restarted in safe graphic mode, tried to install the nvidia drivers but the install ended crashing.
:(

---

### Post by bluesscream on 2010-06-22
> **falkTX said:**
> Please test!
no luck on my 32bit experimental installation. Ran into dkms conflicts with preinstalled kernels. Maybe on a clean system with only a single 2.6.33.23-realtime kernel it might work. I don't think there is a  short way for making nvidia proprietary drivers run on generic/preempt as well as on -rt kernels; these atomic/raw spinlock things either must have been unified in linux kernel source for both kernel lines or driver patches must handle both atomic and spin. So far each version will run into incompatibility with the alternative kernel type.
Respect for your engagements in this linux/nvidia brownfield.=D>

---

### Post by psy-man on 2010-06-22
> **falkTX said:**
> Ok, I've patched the sources of "nvidia-graphics-drivers-173", so the 173-* nvidia drivers may now work with kernel 2.6.33-rt

Please test!

Well I'm sorry to tell you the patched 173 driver did not load  on 2.6.33-23-realtime.
                    neither does it work on 2.6.31-10-rt 
 No worries though, I can switch xorg.conf to run the nv driver if I need to see the whole screen or reinstall 173.14.25 on the 2.6.31-10-rt kernel when I need to use two heads! plus; I'm getting to like the vesa driver on my dual head when recording. 
good work

---

### Post by trulan on 2010-06-22
The patched drivers, as we have been patching them so far, should work on the generic kernel I believe, as the areas affected are specific to the RT kernels.  It will break them though for use on 2.6.31-rt, as that needs the 'atomic_spinlock' stuff.  I'll boot over into Lucid and give these drivers a go...

Edit:  Yup, the build fails on 2.6.33-realtime - gives this error:
```
*** Unable to determine the target kernel version. ***
```FWIW, this nvidia driver does work with the generic kernel.  Is it something with the way the realtime kernel is compiled, or is it something with the patched nvidia package?  The nvidia driver from Ubuntu (on this kernel) fails with the expected messages about atomic_spinlock;  this one can't seem to find the kernel headers or something.

---

### Post by falkTX on 2010-06-23
The thing is that the kernel header files are different between normal kernels and realtime. The realtime devs, by whatever reason, decided to rename some functions...
And, I believe, this should never happen...

Anyway, I'm deeply interested on getting this thing fixed.
Anyone with an nvidia card is welcome to join IRC #ubuntustudio-devel and discuss this in --live--
I really want to see this fixed.

---

### Post by sawtdk on 2010-06-23
Hey FalkTX.

The libdrm +interaccel updates crashed my computer.

When i booted up today the display was totally messed up so I started in graphic safe mode or something like that and went back to the original version.

My chipset is GMA950.

---

### Post by falkTX on 2010-06-23
> **sawtdk said:**
> Hey FalkTX.

The libdrm +interaccel updates crashed my computer.

When i booted up today the display was totally messed up so I started in graphic safe mode or something like that and went back to the original version.

My chipset is GMA950.

hm... what makes you so sure it's the libdrm ?
If it really is the new lib crashing, then I should really removed it!

---

### Post by sawtdk on 2010-06-23
It was the only thing I had updated since the last boot, so I figured out it was that (it looked also like a graphic issue).
So I downgraded the packages in graphic safe mode and rebooted and the it worked properly again.

---

### Post by falkTX on 2010-06-23
> **sawtdk said:**
> It was the only thing I had updated since the last boot, so I figured out it was that (it looked also like a graphic issue).
So I downgraded the packages in graphic safe mode and rebooted and the it worked properly again.

ok, thanks for the info!
I will revert the changes now.

---

### Post by sawtdk on 2010-06-23
Of interest, what was the reason for the +intelaccel update??

---

### Post by falkTX on 2010-06-23
> **sawtdk said:**
> Of interest, what was the reason for the +intelaccel update??

for a friend, to get video acceleration on a netbook.
the next step was to manually patch a kernel...

hm, too much work... I'll leave that stuff on the testing ppa (not the "lucid-latest" one) next time

---

### Post by sawtdk on 2010-06-23
> **falkTX said:**
> for a friend, to get video acceleration on a netbook.
the next step was to manually patch a kernel...

hm, too much work... I'll leave that stuff on the testing ppa (not the "lucid-latest" one) next time

Yeah, that would be a great idea :)

Otherwise a very nice PPA, thanks

---

### Post by falkTX on 2010-06-24
Ok, both versions 173 and 256 are now on my PPA, patched for 2.6.33-realtime.

I can get version 256 ("nvidia-current" package) to build, but I can't test it...
version 173 ("nvidia-glx-173") doesn't here though...

Please test it! ...and report back... hehe


EDIT:
to test it, enable my ppa (ppa:falk-t-j/lucid), update/upgrade, and install "linux-realtime", "linux-headers-realtime" and "nvidia-current"

---

### Post by Totalchaos on 2010-06-24
Works fine for me, thanks =D>

---

### Post by trulan on 2010-06-24
> **falkTX said:**
> to test it, enable my ppa (ppa:falk-t-j/lucid), update/upgrade, and install "linux-realtime", "linux-headers-realtime" and "nvidia-current"
Wonderful!  Working with no problems here.  I had to run sudo nvidia-xconfig after installing so it would actually use the 256 nvidia driver, but the module built just fine, Compiz effects are working, and I just ran a race in Extreme Tux Racer, everything is working splendidly.  Good work!

Edit:  ppa packaged nvidia-current also works on the generic kernel.  May not work for 2.6.31-rt though - depends on how the patches are applied.  I didn't test it with 2.6.31-rt, just with 2.6.33-realtime and with the stock generic kernel for Lucid.

---

### Post by falkTX on 2010-06-25
> **trulan said:**
> Wonderful!  Working with no problems here.  I had to run sudo nvidia-xconfig after installing so it would actually use the 256 nvidia driver, but the module built just fine, Compiz effects are working, and I just ran a race in Extreme Tux Racer, everything is working splendidly.  Good work!

Edit:  ppa packaged nvidia-current also works on the generic kernel.  May not work for 2.6.31-rt though - depends on how the patches are applied.  I didn't test it with 2.6.31-rt, just with 2.6.33-realtime and with the stock generic kernel for Lucid.

Nice to know that it works!

Time to rock then! :guitar:

---

### Post by jwmislan on 2010-06-25
" *** Ok, both versions 173 and 256 are now on my PPA, patched for  2.6.33-realtime. *** "

Will the versions 173 and 256 ("nvidia-current" packages) be upgraded to newer versions by Ubuntu ?

There was an Xorg security-update a few days ago that for only a few small changes, caused my compiled proprietary NVIDIA-Linux-x86_64-195.36.24-pkg2 drivers to fail - as I expected, I had to recompile for all 3 kernels I have installed. 

This situation prevails for Xorg updates, kernel updates, and some other related stuff.

BTW ** Renaming /usr/lib/xorg/modules/extensions/libglx.so - and making an symbolic link to the new compiled eg. nvidia libglx.so.195.36.24 ....

The  /usr/lib/xorg/modules/extensions/libglx.so  ( is not a link ) - is a factor in question - Nvidia driver compiles - complains that it is not a link but puts a new eg.  libglx.so.195.36.24 (file) there on any new compile, and all versions installed have to use the same, last version you compiled.

So far my 2.6.32-22-generic, 2.6.32-22-preempt, and 2.6.33-4-rt are all working with the same /usr/lib/xorg/modules/extensions/libglx.so link to nvidia libglx.so.195.36.24 .

Probably it's similar enough for there to be no conflicts ??

I'm just trying to help a little here as much as I can with my limited experiences with the Nvidia stuff - but still quite a bit of experiences with having to deal with existing conditions.

One big concern is that things change so often that there is a state of constant instability, and not enough settling of conditions to be conducive to a Production System.

So can we eventually get settled to some conditions that are stable, and stay there for a decent while until there is necessity for major upgrades ?

The 2.6.33-4-rt, and 2.6.32-22-preempt are working fine for me at this time for Studio needs. I don't use the 2.6.32-22-generic, but still keep it installed for standard Ubuntu issued.

The Audio Studio Distro is a moving target though, and we all still have to keep track of developments.

 Jwm:guitar:

---

### Post by badvanilla on 2010-06-25
well, there's definitely something I'm doing wrong, but I don't know what it is... :confused:
I still have this error :

[IMG]http://img535.imageshack.us/img535/421/screenshotchangesapplie.png[/IMG]

I'm a bit puzzled.


here's the info in the make.log :
[I][B]*** Unable to determine the target kernel version. ***
make: *** [select_makefile] Error 1[/B][/I]

---

### Post by trulan on 2010-06-25
> **badvanilla said:**
> [I][B]*** Unable to determine the target kernel version. ***
make: *** [select_makefile] Error 1[/B][/I]

Are you using the 256 driver or the 173 driver?  I don't think the 173 driver is working yet.

---

### Post by badvanilla on 2010-06-25
> **trulan said:**
> Are you using the 256 driver or the 173 driver?  I don't think the 173 driver is working yet.
oh, well now I know what was wrong in all my attempts... :oops:
I'm gonna try again with the 256 driver !

---

### Post by falkTX on 2010-06-25
I can't get the v173 to compile for me either.
But that happened with the default ubuntu packages too...

---

### Post by sh0099 on 2010-06-27
i still have no luck with your nvidia driver.
thanks for your efford.

i don't really know what information i can give you beside this:


 Loading new nvidia-current-256.35 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.33-23-realtime
Building for architecture i686
Building initial module for 2.6.33-23-realtime
 Error! Bad return status for module build on kernel:  2.6.33-23-realtime (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/256.35/build/ for more  information.

---

### Post by sh0099 on 2010-06-27
the problem i had was that i did install the linux-headers-realtime but not the linux-headers.

after installing them i had no problem installing (building) the nvidia-current driver.
but i could not use them... (no nvidia modul :-) ?? says X at startup)

so i installed also nvidia-common (173) this time with no problem

with using the gnome-closedsource-driver-install-tool (sorry i dont know the name now)
i could activate the common driver.

thanks to you all 
olaf

---

### Post by bluesscream on 2010-06-27
Some months ago I made a holy oath I'd never again would try to DIY my FX5200's driver for realtime patched kernels. But it's like Ikea furniture, everytime I swear never again but when something is broken or missing  my way is to them again  and then I stand there again in a mess with the Allen key in my bruised fingers...
Here my actual results:
First of all 173.14.22 which is still provided by default in ubuntu 10.04 is obsolete and does not support kernels >~30. Have a look at 173.14.25 [http://www.nvidia.com/object/linux_display_ia32_173.14.25.html](http://www.nvidia.com/object/linux_display_ia32_173.14.25.html) 
It's easy to install: boot into recovery mode, go to the root shell, cd into the directory where you saved the driver and run sh NVIDIA....
I didn't find a way to run any original or customized nvidia173... in 2.6.33-realtime patched kernels, neither in self compiled nor in ppa ones. 
On the other side nvidia's 173.14.25 seems to compile against all other available 2.6 kernels, even 2.6.35-rc.., -ck, -generic, -pae, -preempt and works properly as long as you do not run into conflicts with bleeding edge xorg stuff i.e. from xorg-edgers ppa.
Untouched 173.14.25 compiles against 2.6.31-11-rt! 
I opened and compared patches 2.6.31-11-rt and 2.6.33-5-rt in diffuse, there is a lot new in 33, not only raw | atomic | spinlock stuff. Contentwise I don't understand nothing at all.
For all these kernels I did not find significant differences in performance and latencies for working with synthesizers and effects like zynadd.., rackarrack as well as for recording with ardour or wine/reaper; ceterum censeo: much more important will be adjusting cpu frequency at highest levels.

---

### Post by badvanilla on 2010-06-29
> **sh0099 said:**
> the problem i had was that i did install the linux-headers-realtime but not the linux-headers.

after installing them i had no problem installing (building) the nvidia-current driver.
but i could not use them... (no nvidia modul :-) ?? says X at startup)

so i installed also nvidia-common (173) this time with no problem

with using the gnome-closedsource-driver-install-tool (sorry i dont know the name now)
i could activate the common driver.

thanks to you all 
olaf

Thank you so much for this tip !!
Installing the linux-headers (not the realtime ones) was also the step that I skipped.
It finally worked fine for me, at long last.
Excellent.

---

### Post by trulan on 2010-06-29
> **badvanilla said:**
> Installing the linux-headers (not the realtime ones) was also the step that I skipped.
It finally worked fine for me, at long last.
Interesting - I wonder why it would need those headers too?  I never noticed because I already have them (and the generic kernel) installed.  Oh well, at least it's working.

---

### Post by psy-man on 2010-06-30
hi fellas,
I need expert advise
 I am happy to test the 2.6.33-rt kernel,
 I am continuing to use 2.6.31-11-rt kernel to have my nvidia fx5200 work with the standard 173.14.25 driver. (I need two screens for my desktop when I am editing) (the patched version does not work in either 2.6.31-11-rt or 2.6.33-rt);
 but every time my system is updating it attempts to load the patched driver and I am having to rerun the nvidia installer to undo the patch, there must be an easier way; how do I stop the system update utility from attempting to load the patched nvidia driver? 
did I miss something in a previous post?

---

### Post by trulan on 2010-06-30
To keep Update Manager from installing the new patched driver, you can pin the driver package in Synaptic.  If the newer package is installed, you can 'force version' and make it roll back to the non-patched version.  Then select 'hold package' or 'pin package' (in Synaptic's menu under 'package'), and Update Manager will leave it alone.

---

### Post by psy-man on 2010-07-01
cheers

---

### Post by wbm on 2010-07-02
I have a few questions please.
1.
I have Ubuntu Studio 10.4 installed. If I now add the RT Kernel from Synaptic, will I then be able to choose during boot which kernel I want to use?
E.g. right now Grub shows me the last 3 kernels listed. Would I then see the RT Kernel listed too?

2.
Secondly, how will the updates work? Will both kernels be updated automatically regardless of which one I am using at the time, or will the RT kernel only be updated when I boot into it, and of course would the "normal" kernel then only be updated when I am booted using that.

3.
I have tried doing this on my test Virtual Box install, but now Grub does not show up at all during boot. How can I make that visible?

4.
Lastly, is there anything I should know about having both the regular and the rt kernel installed at the same time? Any unpleasant surprises?

Thanks!!!

---

### Post by bluesscream on 2010-07-02
> **wbm said:**
> I have a few questions please.
1.
I have Ubuntu Studio 10.4 installed. If I now add the RT Kernel from Synaptic, will I then be able to choose during boot which kernel I want to use?
E.g. right now Grub shows me the last 3 kernels listed. Would I then see the RT Kernel listed too?

Yes

> **wbm said:**
> 2.
Secondly, how will the updates work? Will both kernels be updated automatically regardless of which one I am using at the time,
Yes

> **wbm said:**
>  or will the RT kernel only be updated when I boot into it, and of course would the "normal" kernel then only be updated when I am booted using that.

No


> **wbm said:**
> 3.
I have tried doing this on my test Virtual Box install, but now Grub does not show up at all during boot. How can I make that visible?

Don't know exactly, plz search for 'virtualbox grub'. Editing /etc/default/grub in your virtual ubuntu might help if grub only doesn't show up in the virtual box.

> **wbm said:**
> 4.
Lastly, is there anything I should know about having both the regular and the rt kernel installed at the same time? Any unpleasant surprises?

As long as you are in virtualbox there should be no surprise, but your audio performance will be poor at all.
In native installations you might not be able to run nvidia's  proprietary drivers on rt-kernels allthough they run smoothly on generic/preempt ones. The latter is topic of this thread.

---

### Post by wbm on 2010-07-02
Thank you bluesscream.

I'll try this on my regular install. The VirtualBox install is on a different machine where I test things out.
So if I have that NVidea video driver issues using the RT Kernel, I can just reboot and use my regular kernel. That is good to know.

---

### Post by ondrejch on 2010-07-10
Hi, the fglrx Catalyst ATI driver does not compile with 2.6.33-4-rt
I am using version 10.6 for amd64

```


/usr/src/fglrx-8.741# ./make.sh 
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.33-4-rt/build SUBDIRS=/usr/src/fglrx-8.741/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.33-4-rt'
  CC [M]  /usr/src/fglrx-8.741/2.6.x/firegl_public.o
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:34:28: error: linux/autoconf.h: No such file or directory
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:173:30: error: linux/utsrelease.h: No such file or directory
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:255: error: &#8216;UTS_RELEASE&#8217; undeclared here (not in a function)
In file included from /usr/src/fglrx-8.741/2.6.x/firegl_public.c:451:
/usr/src/fglrx-8.741/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/usr/src/fglrx-8.741/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/usr/src/fglrx-8.741/2.6.x/firegl_public.c: In function &#8216;fglrx_pci_suspend&#8217;:
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:841: error: implicit declaration of function &#8216;acquire_console_sem&#8217;
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:863: error: implicit declaration of function &#8216;release_console_sem&#8217;
/usr/src/fglrx-8.741/2.6.x/firegl_public.c: In function &#8216;firegl_init_module&#8217;:
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:1036: error: expected expression before &#8216;{&#8217; token
/usr/src/fglrx-8.741/2.6.x/firegl_public.c: In function &#8216;KAS_Mutex_Initialize&#8217;:
/usr/src/fglrx-8.741/2.6.x/firegl_public.c:5081: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/usr/src/fglrx-8.741/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/usr/src/fglrx-8.741/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.33-4-rt'
make: *** [kmod_build] Error 2
build failed with return value 2
```

They do compile with the regular kernel. Thanks for ev. help :)

---

### Post by mystery1 on 2010-07-25
Sorry for posting my link again. But, I thought I would like to be involved in this discussion.

I have managed to build and install ATI Catalyst 10.5 to work with 2.6.33.5rt22 ( That is kernel.org 2.6.33.5 patched with real-time PREEMPT_RT rt22). Unfortunately, I am not using Ubuntu (I am using Fedora 12).

Here is the link to my patch:
[http://www.phoronix.com/forums/showthread.php?t=24807]("http://www.phoronix.com/forums/showthread.php?t=24807")

I have not tried Catalyst 10.6 since it is not fully tested for ATI Stream SDK 2.1 (OpenCL) yet.

---

### Post by auroraa9420 on 2010-07-25
iv been trying to compile the 2.6.34.1 kernel for a long time can anyone tell me how can i do it from source or at least tell me that the lucid version is stable enougth for server and home using

yes im trying to compile it because of my 5830 card and the evergreen driver requires the 2.6.34 kernel 

please anyone help me D:

pease :guitar:

---

### Post by auroraa9420 on 2010-07-25
> **auroraa9420 said:**
> iv been trying to compile the 2.6.34.1 kernel for a long time can anyone tell me how can i do it from source or at least tell me that the lucid version is stable enougth for server and home using

yes im trying to compile it because of my 5830 card and the evergreen driver requires the 2.6.34 kernel 

please anyone help me D:

pease :guitar:

what i whanted to say un there about "is the lucid version stable enougth for servers and home usage" i was saying about ppa

---

### Post by trulan on 2010-07-25
> **mystery1 said:**
> I have managed to build and install ATI Catalyst 10.5 to work with 2.6.33.5rt22
Excellent work!  It makes me wish I had some ATI hardware to test this.  Hopefully some of the people who have been asking about the ATI driver are seeing this.

> **auroraa9420 said:**
> iv been trying to compile the 2.6.34.1 kernel for a long time can anyone tell me how can i do it from source or at least tell me that the lucid version is stable enougth for server and home using
The kernel building instructions on the first page of this thread should work, just omit the part about applying the RT patch.  I don't know about stability, I've never worked with 2.6.34.

---

### Post by falkTX on 2010-07-26
> **mystery1 said:**
> Sorry for posting my link again. But, I thought I would like to be involved in this discussion.

I have managed to build and install ATI Catalyst 10.5 to work with 2.6.33.5rt22 ( That is kernel.org 2.6.33.5 patched with real-time PREEMPT_RT rt22). Unfortunately, I am not using Ubuntu (I am using Fedora 12).

Here is the link to my patch:
[http://www.phoronix.com/forums/showthread.php?t=24807]("http://www.phoronix.com/forums/showthread.php?t=24807")

I have not tried Catalyst 10.6 since it is not fully tested for ATI Stream SDK 2.1 (OpenCL) yet.

Thanks!

I'll try to add this patch to official ubuntu ATI debs, and if it goes well, I'll add it to my ppa.

---

### Post by mystery1 on 2010-07-26
Thank you. Let me know how it goes. I am not familiar with .deb and ppa, but I am willing to help out if I could.

---

### Post by falkTX on 2010-07-26
> **mystery1 said:**
> Thank you. Let me know how it goes. I am not familiar with .deb and ppa, but I am willing to help out if I could.

Your patch was a success!

I just had to do some small changes (re-creating the patch),
but it now compiles fine on both 2.6.32-generic and 2.6.33-realtime

I don't have an ATI card to test how it works though.

Anyway, the package will be available on my PPA soon (already uploaded)

---

### Post by hardcopy on 2010-07-26
im up for giving it a go, will i need to remove my current fglrx first?

---

### Post by falkTX on 2010-07-26
> **hardcopy said:**
> im up for giving it a go, will i need to remove my current fglrx first?

If you installed from the ATI website, yes.
If you installed through Synaptic/Jockey ("Hardware Drivers"), no.

anyway, the package will take a 1 hour to compile,
but a 64bit deb is already available:
[https://launchpad.net/~falk-t-j/+archive/lucid/+build/1890595/+files/fglrx_8.741-0ubuntu1+rt1_amd64.deb](https://launchpad.net/~falk-t-j/+archive/lucid/+build/1890595/+files/fglrx_8.741-0ubuntu1+rt1_amd64.deb)

---

### Post by hardcopy on 2010-07-26
i did it from the ati website should be interesting to see if i can remove it correctly

at least i can use the 64bit deb youve done already, i just love your ppa man!

---

### Post by mystery1 on 2010-07-26
> **falkTX said:**
> Your patch was a success!

I don't have an ATI card to test how it works though.

Anyway, the package will be available on my PPA soon (already uploaded)

> **hardcopy said:**
> i did it from the ati website should be interesting to see if i can remove it correctly

at least i can use the 64bit deb youve done already, i just love your ppa man!

Thank you for your effort, guys. I am tempted to install Ubuntu and follow the instructions in this thread (thanks, everyone!) to test it in my platform too (ATI Radeon HD4650). It will take some time for me as I have to do it in my spare time, and I'd also see if I have time to try out the latest ATI driver (10.7). I also have an NVIDIA card to test the driver described here. My work is mainly focused to get OpenCL running with linux-rt.

Please post any updates you have and I'll do likewise.

You guys ROCK!!!!
:guitar:

---

### Post by hardcopy on 2010-07-27
sorry guys i couldnt get it to work, although im a bit behind on software updates so i might try again after im updated

the error messages seemed pretty much the same as when fglrx was failing on the realtime kernel previously (dkms failure), so i had to remove the rt kernel and reinstall the official 10-5 ati package

of course i cant rule out user error for the failure

---

### Post by mystery1 on 2010-07-27
> **hardcopy said:**
> sorry guys i couldnt get it to work, although im a bit behind on software updates so i might try again after im updated

the error messages seemed pretty much the same as when fglrx was failing on the realtime kernel previously (dkms failure), so i had to remove the rt kernel and reinstall the official 10-5 ati package

of course i cant rule out user error for the failure

Unfortunately, I cannot help with that. I am downloading Ubuntu Studio at the moment and will try it out.

In the meantime if you want to use the ati installer instead you can try this:

Copy the patch in my previous message to a file in your directory e.g., ~/fglrx-rt.patch

Make sure you are running your rt kernel and have kernel-devel and kernel-headers packages installed. Use 'uname -r' to be sure.

Extract the ati driver source code  (here i call the directory ati-10-5
```
%sh ati-driver-installer-10-5-x86_64.run  --extract ati-10-5
```

patch the ati source code
```
%cd ati-10-5/common/lib/modules/fglrx
```

```
%patch -p1 < ~/fglrx-rt.patch
```

Make sure the patch runs ok and install it

```
%cd ../../../..
```

```
%./ati-installer.sh fglrx --install

```

That works for me in Fedora 12.

Good luck.

---

### Post by falkTX on 2010-07-27
> **mystery1 said:**
> Unfortunately, I cannot help with that. I am downloading Ubuntu Studio at the moment and will try it out.

In the meantime if you want to use the ati installer instead you can try this:

Copy the patch in my previous message to a file in your directory e.g., ~/fglrx-rt.patch

Make sure you are running your rt kernel and have kernel-devel and kernel-headers packages installed. Use 'uname -r' to be sure.

Extract the ati driver source code  (here i call the directory ati-10-5
```
%sh ati-driver-installer-10-5-x86_64.run  --extract ati-10-5
```

patch the ati source code
```
%cd ati-10-5/common/lib/modules/fglrx
```

```
%patch -p1 < ~/fglrx-rt.patch
```

Make sure the patch runs ok and install it

```
%cd ../../../..
```

```
%./ati-installer.sh fglrx --install

```

That works for me in Fedora 12.

Good luck.

No need to do that in Ubuntu anymore, I fixed that.

The command can be easily replaced with:
```
sudo add-apt-repository ppa:falk-t-j/lucid #Adds my PPA, may give an error at the end
sudo apt-key adv --keyserver pool.sks-keyservers.net --recv-keys 736E4F0B #Fix the error above
sudo apt-get update #Update sources
sudo apt-get install fglrx #Install ATI Drivers (patched)
```

That is enough to get the patched ATI driver installed, which will compile on a 2.6.32-generic/preempt/lowlatency or 2.6.33-realtime kernel.

For NVIDIA users, install "nvidia-current" or "nvidia-glx-173" instead of the 'fglrx' package

---

### Post by mystery1 on 2010-07-27
Nice!

I was going to ask that question as I am new to Ubuntu and setting up its repo (PPA?).
I will try it out as soon as I have the Ubuntu Studio installation image downloaded or should I download the Ubuntu standard distro?

Which RT patch and kernel source are used for the 2.6.33-rt?

I will be using an NVIDIA GeForce GTS250 with Core i7 FortSumter (Intel's Customer Reference Board).

Thanks.

---

### Post by falkTX on 2010-07-27
> **mystery1 said:**
> Nice!

I was going to ask that question as I am new to Ubuntu and setting up its repo (PPA?).
I will try it out as soon as I have the Ubuntu Studio installation image downloaded or should I download the Ubuntu standard distro?

Which RT patch and kernel source are used for the 2.6.33-rt?

I will be using an NVIDIA GeForce GTS250 with Core i7 FortSumter (Intel's Customer Reference Board).

Thanks.

Whatever you use standard ubuntu or ubuntustudio is up to you...

I found the NVIDIA patches around the web, and after some checking, I added the patch to the nvidia debs of ubuntu.
Basically it justs patches the nvidia-kernel-driver if the kernel it is about to compile is 2.6.33. There is no 2.6.32-rt and 2.6.33 is not available for Lucid (only on PPAs, which most have realtime).

But I can't test how it works...
I'm a sad Intel consumer... :(

---

### Post by mystery1 on 2010-07-27
I finally installed Ubuntu in my system. Unfortunately, could not add your PPA. I get the following error:

> ikurnian@FortSumter-Lucid:~$ sudo add-apt-repository ppa:falk-t-j/lucid
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 74E4CE730C706BE5C646499A133EAF26736E4F0B
gpg: requesting key 736E4F0B from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

:(

---

### Post by falkTX on 2010-07-28
> **mystery1 said:**
> I finally installed Ubuntu in my system. Unfortunately, could not add your PPA. I get the following error:



:(

Damn it Launchpad!

This error happens all the time, why hasn't Canonical fixed it yet?


Anyway, the PPA is actually added, just not the pgp key (to mark the PPA as trusted).
A solution is to run this command, after the 'add-apt-repo...' thing:
```
sudo apt-key adv --keyserver pool.sks-keyservers.net --recv-keys 736E4F0B
```
That will get the PPA key from somewhere else, which fixes the problem

---

### Post by mystery1 on 2010-07-28
Thanks, falkTX.

The problem with GPG server was actually on my side. It is the office firewall that does not allow any communication using port 11371 (apparently that is the port being used for this).

I was able to install all that I want. linux-rt kernel from bojo42 and ati and/or nvidia rt-patched from your PPA.
AWESOME!! Sometimes, I did have to remove the driver and re-install, but that's probably just me not being familiar enough to do it right.

I have not tried to tune the performance or run OpenCL with the NVIDIA driver but that will come next. I stumbled upon setting up GRUB to give the menu options on boot-up, but this forum is full of information!!

Thanks again to all of you and this is one nice thread!!

I will update from time to time on my work with the linux-rt stuff...

Time to sit back, relax, and enjoy my new Ubuntu system.

:popcorn:

---

### Post by mystery1 on 2010-07-28
I forgot to mention that I had to do the following after installing the drivers before restarting. 

NVIDIA driver:

```
%nvidia-xconfig
```

ATI driver:

```
%aticonfig --initial
```

---

### Post by texla on 2010-08-01
Just added the 2.6.31-10-rt kernel to my new laptop and it's doing great on a dual core 2.0GHz Asus X83VB-X2 w/ 4GB ram.  Just recorded a song using 4 channels with firewire (Presonus Inspire).  This is the first session I've ever done that had absolutely 0 xruns in Ardour as well as during the Jamin mastering mix.  Crazy!

 I have not dealt with the nvidia driver fix yet so the screen looks a little 1990-ish but it's very usable - but maybe I'll tackle that next.... :KS

edit: got the nvidia working with the help of this thread!

---

### Post by MikeRivers on 2010-08-02
Can someone please help me before I put a bullet through this disk drive and go back to Windows?

I've been trying to set up a Linux system for audio with the primary goal of getting it to work with a Firewire audio device, specifically the Mackie Onyx Firewire option card (since that's the only on on the FFADO "fully supported" list that I own. I try this every couple of years and I can't get there, so I set it aside. Last week was my most recent effort.

I don't use Linux, I don't speak Linux, but I've been around computers long enough to follow instructions and pretty much understand what I'm doing as long as it's presented in a way that I know where to start and where to go. I'm having trouble figuring out from the documentation and posts on this forum whether:

(a) there's still this FFADO - real time kernel incompatibility.

(b) if my installation has already been "fixed."

(c) might there be some other problem?

Although there are some things about which I'm not too sure, I'm able to get audio working using either the computer's built-in sound card or a Behringer UCA-202 USB audio interface. I can get that working using the ALSF driver with Audacity and Ardour, and I even tried installing Wine and running Sound Forge (a Windows audio program) which worked. However, FFADO doesn't show up as an option either in the basic Linux Sound/Hardware configuration nor in the jACK setup. 

As far as driver choices in jACK (setup), ALSF works with the UCA-202 or internal (Intel) sound card, but the only Firewire-like choices are freebob and firewire, neither of which get me anywhere but a message "Could not connect to JACK serve as a client." 

I'm unclear as to how the audio devices are identified. I see the following choices:

(default)  -  I have this set up as the UCA202 in the Sound/Hardware settings
hw:0
plughwdsp
/dev/dsp
/dev/audio

Selecting (default) gets me a connection and record/playback functionality. Selecting any of the others gets me zilch.

In trying to follow up on the real time kernel issue and perhaps replace what's in my installation with the one which can be "easily obtained using the Synaptic Package Manager" I discovered that I already had something by that name, with the installed version 2.6.3-10.153.  Is that a good one or a bad one?

If I need to replace it, could someone please give me baby-step-by-step instructions on how to do that?  What to look for, where to get it, what to get, and what else I need to do besides let the package manager do its thing? I've used that tool to install other things and they've worked fine, but if I need to download and compile something, I'll need detailed instructions on what to type. 

For what it's worth, the Firewire card that I have in the computer uses the VIA chipset. I've confirmed that it works with the Mackie mixer card (yeah, I know the i series is a different, and currently unsupported animal). The GNOME Device Manager (displays a tree-like display) shows the 1394 card and the entry below it identifies the Mackie Onyx mixer by name, so I believe that the hardware parts are working. The computer is an older Dell, 800 MHz Pentium 3, with, I believe 512 MB RAM. 

In the interest of full disclosure, I don't really have to get this working. I'm happy with my Windows installations. But every now and then I want to see if Linux is ready for the musician-user with no more system level computer knowledge than what I have, so I get into this little project for a week or so, beat my head against the table, then set it aside. I'll be happy with getting the software to recognize the hardware and worry about latency and clicks'n'pops later if ever, but I can't even get to second base here. 

I decided to work with Ubuntu Studio since the distribution included FFADO with versions that presumably work correctly together. I actually tried installing the stock Lucid 10.04 (not Studio), then installed FFADO, then uninstalled and re-installed jACK (per instructions that indicated that jACK needed to know that FFADO was available when it was building itself) and that gave me the same results. 

I'm perfectly willing to accept that I don't know enough to do this, but I'd like to believe that, particularly the Studio distribution that seems to be oriented toward multimedia production, would have enough kinks worked out so that a novice could get it working. Admittedly, I did get it working, just not with the hardware I wanted to use, which FFADO claims is fully supported.

Friendly help is welcome. RTFM is, at this point, not welcome without very specific pointers. Linux isn't my life.

---

### Post by trulan on 2010-08-02
A few answers for you:

1.  the FFADO driver is called 'firewire' in Jack Control.  The 'freebob' entry is a leftover and won't work in anything newer than Ubuntu 9.04 IIRC.  So 'firewire' is the only choice here.

2. Selecting [default] for the device is also the correct option.  Unless you are daisychaining firewire devices and need to manually specify their order, there's no need to do anything else here either.

3. There's no incompatibility between ffado and the real time kernel; actually it's difficult to get a stable firewire audio setup without it.

Frustration is one of the biggest causes of failure for people trying to set up something like this, so hang in there and stay cool.  ;)  So, in the interest of helping you, could you open a terminal, run these commands one-at-a-time, and copy/paste the output of each one here?  Maybe we can get a few clues as to what's going on.

This will tell us what kernel you are actually using:```
uname -a
```
This is necessary to know what permissions you have granted to your username:```
groups
```
This reports the basic status of the firewire interface:```
ls -al /dev/raw1394
```

and, finally,
```
ffado-test ListDevices
```There's some more tweaks to get things more stable and get latency lower, but first things first - and that would be actually getting it to work.

Oh one more thing - a copy/paste of the content of the Jack Messages window can also be informative.

---

### Post by MikeRivers on 2010-08-02
> **trulan said:**
> A few answers for you:

1.  the FFADO driver is called 'firewire' in Jack Control.  The 'freebob' entry is a leftover and won't work in anything newer than Ubuntu 9.04 IIRC.  So 'firewire' is the only choice here.

2. Selecting [default] for the device is also the correct option.  Unless you are daisychaining firewire devices and need to manually specify their order, there's no need to do anything else here either.

OK, that clears up a couple of things. I knew that FreeBoB was the original development and that FFADO superseded it. I figured that either FreeBoB was still there for old compatibility but I guess it's just a case of something that didn't get cleaned up. 

I have only one Firewire interface (so far anyway) so there's no need to complicate things until I know that they work in their simplest form first. "default" it is, then. 

Is there any relation between this "default" and the audio device that I select when I open the Linux Preferences/Sound/Hardware window? I see only the internal sound card and the external USB interface there. Should I see the Onyx Firewire interface there as well if everything is working correctly, or does that only appear in applications after jACK is running and FFADO is happy?
> 
3. There's no incompatibility between ffado and the real time kernel; actually it's difficult to get a stable firewire audio setup without it.

Obviously both are needed. My interpretation of that post about the real time kernel was that it got broken with this Ubuntu distribution. If that isn't what it means, can you clarify what it's about, if it matters, and the explanation isn't too complicated?

> 
open a terminal, run these commands one-at-a-time, and copy/paste the output of each one here?  Maybe we can get a few clues as to what's going on.

This will tell us what kernel you are actually using:```
uname -a
```

Linux mike-ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

[QUOTE]
This is necessary to know what permissions you have granted to your username:```
groups
```

mike adm dialout cdrom audio plugdev lpadmin admin sambashare

> 
This reports the basic status of the firewire interface:```
ls -al /dev/raw1394
```

crw-rw---- 1 root audio 171, 0 2010-08-02 21:22 /dev/raw1394

> and, finally,
```
ffado-test ListDevices
```

FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.0.0
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00000ff200017427  0x0000000F  0x00010065   Mackie - Onyx Firewire
   1       0x0008000800080149  0x00000800  0x00000000   Linux - ohci1394  - 
no message buffer overruns

(this looks encouraging)

> copy/paste of the content of the Jack Messages window can also be informative.

With the Firewire driver selected:

21:57:59.885 JACK is starting...
21:57:59.888 /usr/bin/jackd -r -dfirewire -r44100 -p1024 -n3
21:57:59.905 JACK was started with PID=1624.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    283941
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
libffado 2.0.0 built Mar 31 2010 14:47:42
21:58:01.942 Server configuration saved to "/home/mike/.jackdrc".
21:58:01.952 Statistics reset.
21:58:01.982 Client activated.
21:58:02.034 JACK connection graph change.
21:58:04.377 JACK connection graph change.
21:58:04.400 JACK connection change.
21:58:09.872 XRUN callback (1).
21:58:12.215 XRUN callback (2).
21:58:18.833 XRUN callback (3).
21:58:22.824 XRUN callback (4).
21:58:24.219 XRUN callback (5).
21:58:29.680 XRUN callback (6).
21:58:32.259 XRUN callback (7).
21:58:41.093 XRUN callback (8).
21:58:43.603 XRUN callback (10).
(and more of the same)


And just for reference, with the ALSA driver selected:
21:51:47.386 Patchbay deactivated.
21:51:47.559 Statistics reset.
21:51:47.866 Startup script...
21:51:47.869 artsshell -q terminate
21:51:47.930 ALSA connection graph change.
sh: artsshell: not found
21:51:48.579 Startup script terminated with exit status=32512.
21:51:48.581 JACK is starting...
21:51:48.586 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    283941
21:51:48.625 JACK was started with PID=1570.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
21:51:48.918 ALSA connection change.
21:51:50.948 Server configuration saved to "/home/mike/.jackdrc".
21:51:50.966 Statistics reset.
21:51:51.026 Client activated.
21:51:51.037 JACK connection change.
21:51:51.064 JACK connection graph change.

Well, I'll be darned! For the first time in a week, seemingly without doing anything different other than executing those commends to look into the system, jACK isn't complaining. So I started Ardour, expecting it to tell me "Could not connect to jack server as client" it didn't complain either. And for the first time, I was able to add plugs in the patchbay. Not only that, but for the first time, I was able to record and play from the Mackie in Ardour. There were the expected unoptimized dropouts and squeals, but there was audio. This is exciting. 

I hate when something gets fixed and I don't know what I've done to fix it. It may never work again, but it's encouraging that it worked once. I'll let you know what happens after the next restart. 

:popcorn:

---

### Post by mango42 on 2010-08-03
Your 'groups' needs to include 'video' too. Wow, **trulan** is doing you proud! ;-)

> Friendly help is welcome. RTFM is, at this point, not welcome without very specific pointers. Linux isn't my life.

But it can become a way of life ;-) 

Me, I am still awaiting the brilliant programmers here and over at **ffado** to get the Focusrite Saffire Pro 40 working smoothly under JACK, but, knowing how much sheer effort and *vocational* brainpower goes into making Linux Audio, once tuned, work so much better than any commercial offerings, I am more than content to wait, offering what little I can in support and feedback.

Mike Rivers - hmm - RAP? Wonderful expositions on compressors? Ace duelist versus Fletcher? Ah, those were the good 'ole usenet days ;)

Bottom line? Co-operative ventures beat commercial rat-races any day - just add humanity and as much input as one is capable of, IMO

---

### Post by MikeRivers on 2010-08-03
> **MikeRivers (that's me!) said:**
> 
I hate when something gets fixed and I don't know what I've done to fix it. 
Well, I didn't dream it, it still worked when I booted up this morning. Maybe all it took was the command ffado-test ListDevices to convince it that there really was something out there, and after that it believed it. 

There's lots I have to learn about jACK connections and Ardour but that can come along at my leisure, if ever. Ardour has a routing option that just seems to work even without any connections showing in the jACK windows - input 1 to track 1, input 2 to track 2, etc but I'll need to poke around and learn the syntax if I want to make a "patch" that, say, routes input 1 to all the tracks. I'm still confused about ffado's description as a "back end" to jACK. As an audio guy, I'd call it a front end because I'm more concerned with inputs than outputs. And I guess that for the "Start JACK when the application starts" check box in qjackctl, "the application" is qjackctl, not an application (like Ardour) that needs JACK. I was told that JACK starts automatically "most of the time" but I have to start it first to keep Ardour from complaining about a lack of connections. 

Anyway, thanks for taking the time to read through my woes. I wish I could thank you for whatever did the trick. I wish I knew what it was.

---

### Post by MikeRivers on 2010-08-03
> **mango42 said:**
> Your 'groups' needs to include 'video' too. Wow, **trulan** is doing you proud! ;-)
Well, I don't know anything about video, so better to show my ignorance in the general pool.
> 
Me, I am still awaiting the brilliant programmers here and over at **ffado** to get the Focusrite Saffire Pro 40 working smoothly under JACK
It's exactly stuff like this that has led me to checking out Linux-for-audio every couple of years and deciding that it's not ready for prime time. One of the things that the majority of DAW users like about the concept is the flexibility, both in software and hardware, with which they can build and upgrade their systems. While I acknowledge that two tracks in and out makes a lot of people happy, there's a lot of calls for multi-channel I/O devices if for no other reason than to be able to record a full drum kit on multiple tracks (cheap microphones have contributed to that, but that's another story). 

The number of multi-channel devices that were supported, either under ALSA or ffado, was, and still is, pretty skimpy. Same for pure Linux applications. So there really aren't very many options in setting up an initial multitrack system, and upgrading it when new products come on the market. When you bought your Saffire Pro 40, it came with a Windows driver disk (probably out of date, but you could get a more recent one from the web site) and it runs without a special driver under the Mac Core Audio. And if the Windows driver doesn't work, you have only one place to go to complain - Focusrite. But you're still waiting for the ffado ffolks to come up with support for your interface. And when you do, it's unlikely that it will have the nice mixer control panel that the factory support program offers. Furthermore, the way things are going, it'll become a discontinued product before you get your ffado support. These things don't last very long before they're replaced by something newer and cooler.
> 
. . . knowing how much sheer effort and *vocational* brainpower goes into making Linux Audio, once tuned, work so much better than any commercial offerings, I am more than content to wait, offering what little I can in support and feedback.
If that's OK for you, fine. But I can't tell a client of mine that if he wants to use the interface that he's been working productively with under Windows for the last year he'll have to wait if he wants to switch to Linux. Also, "so much better" depends on how you see it. We get spoiled by cheap computer horsepower these days, and brute force can overcome a lot of sloppy programming. 
> 
Mike Rivers - hmm - RAP? Wonderful expositions on compressors? Ace duelist versus Fletcher? Ah, those were the good 'ole usenet days ;)

Yup, that's me. Fletcher is really a friend, but he does tend to come on a bit strong sometimes. ;)
> 
Bottom line? Co-operative ventures beat commercial rat-races any day - just add humanity and as much input as one is capable of, IMO
Sure, if you have the time, or have the support. Harrison makes excellent recording and broadcast consoles based on Linux. They keep up with the developments and core updates, and were an Ardour development supporter for many years. But the difference between someone who buys a Harrison console and a musician who wants to record himself and has decided that Linux will be his operating system of choice is this - Harrison is the support and software maintenance point for their products. They don't expect (or condone) users to try to make the system into anything but a Harrison console. When there's an update, you'll get it from them, they will have tested it with the same hardware and software that you and all their other customers have, and they'll know that it works. The fact that there are so many distributions of Ubuntu (and other flavors of Linux), people getting pieces from different sources, and often not enough resources to do thorough testing before releasing a software build put the users in the position of being testers. Sure, not all Windows software works right either, but I think the odds are better most of the time. 

Anyway, enough of this drivel. I'm going to play before I break something else. ;)

---

### Post by fengxing on 2010-08-03
I was very pleased to find this site.I wanted to thank you for this great read!! I definitely enjoying every little bit of it and I have you bookmarked to check out new stuff you post.

---

### Post by mango42 on 2010-08-06
Sorry for the delay, Mike, but there's just one thing I'd like to mention about why I'm happy to view the Focusrite unit as a brick for a while longer - I bought it for one reason only (Revox B & an old Fostex + [www.recordplayer.com](www.recordplayer.com) still preferred!) - 

***Focusrite supports Linux and has near enough open source drivers***

So it's an ideological thing for me and my few but precious 'clients' - Windows went in the bin the day Vista came out.

---

### Post by texla on 2010-08-06
Thanks to this thread and all the hard work of the people here, I was able to get the newer realtime kernel installed and my nvidia card working fairly easily - here's how:

added this ppa here: 
[https://launchpad.net/~falk-t-j/+archive/lucid/]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/")

then added a realtime kernel:
2.6.33 (the .29 pae version)  image and headers

then added all the nvidia stuff in the ppa

(the 98 failed to install but the 173 did just fine)

then restarted into the kernel and ran the nvidia settings program in:

system - administration - nvidia x server settings

it told me to run a command in the terminal (i did not write it down but i ran it in the terminal like it suggested)
then restarted. - now all is pretty good - starting in the vanilla kernel does seem to send me to low graphics mode but I'm not worried sine the realtime is working

---

### Post by MikeRivers on 2010-08-06
> **mango42 said:**
> I'm happy to view the Focusrite unit as a brick for a while longer - I bought it for one reason only 
***Focusrite supports Linux and has near enough open source drivers***

So it's an ideological thing for me and my few but precious 'clients' - Windows went in the bin the day Vista came out.
Out of curiosity, did Focusrite supply the drivers (or the data to write them) or did some clever programmer figure it out?  I know that Mackie doesn't give a hoot about supporting Linux, but the Firewire card in my Onyx mixer works, and the 1200F is supposedly in the works. 

Honestly, I pretty much use the 1200F as a brick (under Windows) myself, with everything going in and out through a full featured analog console, so I don't really need the DSP mixer that's built into it (just like in your Focusrite interface).

When Vista came out, I decided to stay with WinXP. When Windows 7 came out, I decided to stay with XP. When all the hardware that I'm using is supported under Win7, maybe I'll make a switch, which will probably be about the time Win8 comes out.

---

### Post by mango42 on 2010-08-06
[QUOTE="Really Mike Rivers"]Out of curiosity, did Focusrite supply the drivers (or the data to write them) or did some clever programmer figure it out?[/QUOTE]

I was searching for the email that Focusrite sent me a year back that could have answered your query categorically, but it's evaporated. I bought the unit so I must have been satisfied with their answer.

AFAIK, Focusrite give 'every assistance' to the ffado team, themselves indeed very clever programmers. ;)

---

### Post by MikeRivers on 2010-08-06
> **mango42 said:**
> AFAIK, Focusrite give 'every assistance' to the ffado team, themselves indeed very clever programmers. ;)
Focusrite is good folks. 

So you're using Firewire. What software application are you using with it? Have you been following my problem of JACK not starting by itself, so I must start it manually (I use qjackctl) in order for Ardour to recognize that there's some hardware for it to talk to? 

Do you have your system set up so that JACK starts on boot-up?  I followed transmogrifox's instructions for configuring the /etc/default/jackd file [HELP! I'm starting to talk like a Linux user!!!!] but it still doesn't go. "yes" and my user name on the system are simple enough. The only thing I'm unsure of is the options line. What are you using for that? 

Will it work with nothing there? (mine doesn't). Since you can set all of that stuff in Ardour, there may not be any need to preset it with options read from this file. If there's a simple way to do it, I'd rather start with simple first.

---

### Post by MikeRivers on 2010-08-07
I've found a work-around that makes things a little more convenient. I discovered the tool in the Ubuntu menu for setting up programs to start on log-in and added qjackctl to the list (as well as discovered some things that were starting that I didn't need). Now when I boot up and log in, since I have "start jACK when application starts" checked in qjackclt, I have jACK running, before I start an audio program and the audio programs that need it are happy. 

That makes me happy, too.

---

### Post by mango42 on 2010-08-08
[QUOTE="MikeRivers"]If there's a simple way to do it, I'd rather start with simple first.[/QUOTE]

That's why knowledgeable people here have suggested you try Qtractor... ;-) It's probably not what you are used to, is 'only' at v0.4.6 alpha code yet aleady brings that original AtariST flavour and simplicity to a DAW. Did anyone mention its excellent ergonomics?

I also note from the other thread you are active in, your unfortunate choice of comparison with ex-BrokenPlanet CEO Tony Wayward, possibly set to be the most reviled public figure *ever* once people start getting a grip on the true (and ongoing!) extent of the 'disaster'.

eg: [http://blog.alexanderhiggins.com/2010/08/07/crime-century-bp-government-dont/](http://blog.alexanderhiggins.com/2010/08/07/crime-century-bp-government-dont/)

Do you really want to be likened to a man ducking his responsibilities to humanity, whilst being showered with gold?

Personally, I would rather be compared to such folks as Dr Zangari, an independent Italian physicist who is working vocationally to get to the real truth of the Gulf Oil Gusher(s)...

eg: [http://yowusa.com/earth/2010/earth-0810-01a/1.shtml](http://yowusa.com/earth/2010/earth-0810-01a/1.shtml)

Hey ho :popcorn:

---

### Post by MikeRivers on 2010-08-08
> **mango42 said:**
> That's why knowledgeable people here have suggested you try Qtractor... ;-) It's probably not what you are used to, is 'only' at v0.4.6 alpha code yet aleady brings that original AtariST flavour and simplicity to a DAW. 
Yes, since it came along with this distribution. It's so basic that I didn't spend more than a couple of minutes with it. 
> 
Did anyone mention its excellent ergonomics?
Not yet, but I will. I wasn't impressed. Ergonomics isn't what I'm looking for anyway. 
> 
Do you really want to be likened to a man ducking his responsibilities to humanity, whilst being showered with gold?
Do you really have such a tiny sense of humor that you didn't get what I wrote? 

As I'm sure I've said here before, my goal isn't just to get a DAW working under Linux. It was to learn about the process of getting a DAW working under Linux, and not just any DAW, but one with similar capabilities that someone with a Mac or Windows system could get with one of the popular commercial products. Audacity was a good test case, so was Ardour. QTractor is not. 

At this point, I have Ardour running predictably using the Mackie Firewire mixer, which means I'm successfully using jACK and at least one element of FFADO. I don't have to manually start jACK. I can shut the computer down without manually stopping it. In other words it works pretty much like I'd use Windows with a DAW application. 

There are still some hitches. If I want to use a program that doesn't use jACK, like a media player, or I want to use a different audio interface, I need to fiddle with some things, but I feel like I no longer have a total lack of control, and I have a little better understanding of how Linux handles audio. 

I found a pretty good web page that gives a broad picture of the various audio driver-like applications and why there really can't be a straightforward installation process. 

[http://tinyurl.com/LinuxAudioTowerOfBabel](http://tinyurl.com/LinuxAudioTowerOfBabel)

A bit out of date, but then that's typical of Linux documentation. 

Anyway, I'll fiddle around with it a bit more, but I'm just about ready to pack that computer away for another year or so, put the mixer back to where it normally lives, and get back to normal. 

I appreciate all the input from this forum. Just about everything has been useful and pretty friendly. Thanks.

---

### Post by sgx on 2010-08-08
Hi, most of what I do involves
Reaper
qjackctl
Hydrogen
zynaddsubfx
rakarrack
timemachine (a simple recorder)
audacity

a Yamaha rompler, and around 20 windoze vst plugins.

Its a simple and powerful creation setup, works in
almost any linux, and has no serious sonic limitations.

I keep all downloaded packages from synaptic, so I can
build a daw without going online. I have a separate /home partition
so I don't have much to reconfigure when I tinker my system to oblivion
(at least I admit my bad habits ;) )

I think millenium, xp, vista, beta-7 etc are the pathetic creations of control-freaks, 
and since I have never used any Mac, I cannot comment on those, except in uninformed jest.

Hope you find a useful linux setup! Barebones linux, plus a few apps, is the way to go, if one is a recording musician.

Cheers

---

### Post by maghoxfr on 2010-08-11
...

---

### Post by MikeRivers on 2010-08-11
> **maghoxfr said:**
> Is all of this a joke?
P.S:

Maybe I misunderstood all the quoted at the beginning, maybe my lousy english doesn't allow me to understand it properly. If someone feels this comment this post is out of place, I'll delete it.
No joke. Well, OK, the part about putting a bullet through the disk drive was a joke. I came here looking for some help. A few folks came to my assistance and I feel that I'm over the hump now. This doesn't mean that I'm a Linux expert like you, but I fell like I know more than when I came in. I'm grateful for the help. 

Sorry if you think I wasted your, or others' time.

---

### Post by maghoxfr on 2010-08-11
...

---

### Post by MikeRivers on 2010-08-11
> **maghoxfr said:**
> I don't think you wasted nobody's time, but ranting over how you dislike linux and telling how much you think windows is better etc. is not the way of asking for help. The form you directed to the forum, _demanding_ help is not the proper form either, in my opinion. 
I don't say this to many people, but dude, you're WAY out of line here. Ranting about how I dislike Linux?  Telling how much I think Windows is better?  Get a grip!
> 
If you can't solve the problems you have with linux by yourself then you should do some research and not expect people solve them for you. 
This is so typical of SOME members of the Linux community, and it's this sort of attitude that keeps people like me who would like to investigate it at a distance. Some people here were very helpful so I know everyone here isn't like you. But sadly, the fact that there are people who share your "go learn it yourself like WE had to" attitude are keeping people like me who might be interested from continuing on the path we've chosen to investigate. I keep trying to believe that this isn't typical, that times have changed, but you're sure convincing me that there are still people like that popping unnecessarily. 

I help a lot of total beginners who have questions about audio hardware and software. I could tell them to just read the manuals, but I remember that I learned from people who were around when I needed help. Sorry if you feel that everyone should suffer like you. I try to be helpful when I can. You should try it, too. You might feel proud that you've learned enough to show another beginner the way.

I won't darken your doorway again. No need for further discussion.

---

### Post by maghoxfr on 2010-08-11
...

---

### Post by transmogrifox on 2010-08-12
@MikeRivers: I'm glad you ended up getting some good suggestions in this thread. Seems there is always the better, best, and worst ... and some people who just have to rant :P

Anyway, the other day I was hanging out in the #lad IRC channel and they were talking about traverso.  You may be interested in trying it now that it appears you have your Jack problems mostly under control:
[http://traverso-daw.org/](http://traverso-daw.org/)

If you're looking for a Win/Mac DAW clone, this may not be it, but from what I read about it, the design is very intuitive, innovative, and would likely be friendly to the typical Windows or Mac user.

If you continue down the Linux road and explore what is out there, I think you will find that stock Ubuntu or even Ubuntu Studio is not the best choice for a dedicated DAW & mastering system.  As time goes on and desktop systems get more and more fancy, I go backwards.  Now my system boots to the console interface, I have a script to launch X & applications I want to use.  You would be surprised how much CPU a system monitor applet & clock applet can consume.  At the same time, Ubuntu is probably the best supported & a great learning platform.  Once you learn the programs through the GUI, then it's not as difficult step from GUI to CLI and text files.

---

### Post by falkTX on 2010-08-12
Here goes another suggestion:

Try KXStudio, an Ubuntu based Operative system,
similar to UbuntuStudio, but uses KDE as the Desktop Environment.

[http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)

I'm actually the proud author of it... ;)

---

### Post by MikeRivers on 2010-08-12
> **transmogrifox said:**
> @MikeRivers: I'm glad you ended up getting some good suggestions in this thread. Seems there is always the better, best, and worst ... and some people who just have to rant
Oh, I fully understand. I've done my share of ranting too. I thought I was being reasonably humble and trying to ask questions that were direct enough to either lead me to a solution or to another place to look. I freely admit that I'm a novice at this, and that I was hoping that I could get things up and running without becoming a dyed-in-the-wool Linux user first. Your straightforward answers were among those which were a big help in getting me on track without digging in too deeply, and I really appreciate it. 
> 
Anyway, the other day I was hanging out in the #lad IRC channel and they were talking about traverso.  
I took a peek at it, but didn't bother to download it. It looks more musician-oriented than Ardour and if I were doing a comparison of applications, I'd certainly give it a further look, but I'm not doing that now, so I'll continue to fiddle around with the applications with which I've become at least a little friendly. Same goes for KXStudio. 
> 
If you continue down the Linux road and explore what is out there, I think you will find that stock Ubuntu or even Ubuntu Studio is not the best choice for a dedicated DAW & mastering system. 
What matters is the applications, not the distribution. The distribution just makes it easier to get the applications installed if they're not pre-installed. Maybe some day I'll be invited to contribute to the functional specifications of a distribution oriented toward professional audio production.  
> 
As time goes on and desktop systems get more and more fancy, I go backwards.  Now my system boots to the console interface, I have a script to launch X & applications I want to use.  You would be surprised how much CPU a system monitor applet & clock applet can consume.  At the same time, Ubuntu is probably the best supported & a great learning platform.  
That's what I concluded from looking around at the various distributions. In theory, you can get any one and enough stuff so that you can (if you know enough) install any applications and tools to make it do what you want. I don't remember what I was trying to install (from the source files) and on which distribution (I had two disk drives, one with Ubuntu, the other with Ubuntu Studio) but the first error message I got when following the installation instructions was that there was no C++ compiler to be found. Fortunately, the error message pointed me to where to get it. 

I spent enough time with the terminal to start getting familiar with the commands, though I never studied the operating system and its interdependencies. These days, it should be possible to install software and run it from a GUI, and in most cases it's true. But I'll admit to dropping into a DOS box in Windows now and then to do something quicker (or that I never figured out how to do) than I could from the GUI tools. 

It must be a pretty personal thing, though. I had a friend over one afternoon who has been working with Unix systems for at least 20 years (he won't let a PC on to his network!) to see if he could help me find some of the missing links, and the first thing he did was install his favorite shell (tsch, I think) and editor (jove) so he'd know how to do whatever he wanted. And, no, he didn't figure it out either.

---

### Post by trulan on 2010-08-13
Sorry Mike, I asked you a whole bunch of questions, then dropped off the face of the earth.  Glad to know things are going well, for the most part.
> **MikeRivers said:**
> My interpretation of that post about the real time kernel was that it got broken with this Ubuntu distribution. If that isn't what it means, can you clarify what it's about, if it matters, and the explanation isn't too complicated?
Nothing's exactly broken here.  It's just that Ubuntu is not providing the newer real time kernel for Lucid, so we're doing it ourselves.
> Linux mike-ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/LinuxSo you're using the generic kernel.  That's fine, but you probably won't get >10ms latency running stable without the RT kernel.

ls -al /dev/raw1394
> crw-rw---- 1 root audio 171, 0 2010-08-02 21:22 /dev/raw1394This is crucial - the word 'audio' in there, combined with 'audio' also being in your groups list, is absolutely necessary.  The group that raw1394 is assigned to has moved around, it was 'disk' then 'video' and now it's 'audio' in Lucid.  IMHO 'audio' is the best choice but I hate it when they keep changing these things.
> 21:58:41.093 XRUN callback (8).Don't worry - jack is smiling on you. ;)

So what fixed it?  I've found that it can be a little hassle to get raw1394 to load properly the first run on a new system.  I usually reboot with my firepod hooked up and turned on and that takes care of it.  So I'd venture a guess that something you did triggered a reload of the raw1394 module, and it'll be good to go from now on.

> **MikeRivers said:**
> I appreciate all the input from this forum. Just about everything has been useful and pretty friendly. Thanks.
Ooops - you spoke too soon.  ;)  Resistance to RTM'ing is a sensitive issue, I actually deleted a snide remark from my first response to you before I posted it.  And since I've strayed into confessions:
> **sgx said:**
> ...when I tinker my system to oblivion
(at least I admit my bad habits ;) )
You are not alone...:shock:

So Mike, come back in a few months for Ubuntu Maverick Meerkat, when raw1394 has been deprecated and firewire audio will use the long-awaited 'new' firewire driver stack!  Maybe, just maybe, you'll finally get the plug-and-pay functionality you've been hoping for.  (Now if I could only figure out what is going on with the RT kernel in Maverick - but Lucid taught me to build my own kernels and I haven't forgotten just yet...)

---

### Post by MikeRivers on 2010-08-13
> **trulan said:**
> Nothing's exactly broken here.  It's just that Ubuntu is not providing the newer real time kernel for Lucid, so we're doing it ourselves.
So you're using the generic kernel.  That's fine, but you probably won't get >10ms latency running stable without the RT kernel.
Aha, so what this (on topic) thread is really about is an improved real time kernel, not that there's none, or a broken one, as part of the distribution, but that the new one is better. True, I don't get very stable performance without a lot of latency. I suppose that what's to understand, from a functional standpoint, is that by replacing this kernel, I could operate with lower latency. Good to know, at the time I asked initially, it wasn't working at all, and I thought that perhaps the kernel could be the problem. Guess it wasn't. 
> 
ls -al /dev/raw1394
This is crucial - the word 'audio' in there, combined with 'audio' also being in your groups list, is absolutely necessary.  The group that raw1394 is assigned to has moved around, it was 'disk' then 'video' and now it's 'audio' in Lucid.  IMHO 'audio' is the best choice but I hate it when they keep 
changing these things.
The concept of groups (as Linux uses them) is new to me, and now I know that it applies to programs as well as users. I first ran into it when I was playing with the standard (at least not the Studio) Ubuntu release and couldn't get the Firewire device recognized at all. That turned out to be that I (mike) wasn't a member of the audio group. I don't remember exactly what the symptom or error message (if any) was, but adding myself to the audio group got me over that hurdle. 

In looking at the output of that ls command, I didn't realize that one of the switches told it to display the group to which the file belonged. Yes, it's annoying when things get moved from where you expect them, and that it matters. I particularly have a problem when things on the user interface get changed, moved, deleted, or re-named. 
> 
So what fixed it?  I've found that it can be a little hassle to get raw1394 to load properly the first run on a new system.  I usually reboot with my firepod hooked up and turned on and that takes care of it.  So I'd venture a guess that something you did triggered a reload of the raw1394 module, and it'll be good to go from now on.
That's about all I can guess. I know that Windows doesn't always recognize a Firewire device if it's not booted with the device connected and powered up, so I was always careful to do that, or if I realized that I had booted without the Firewire mixer connected or turned off, shut down before I tried to do anything with it, and restarted after powering it up. I guess this will remain a mystery. 
> 
Ooops - you spoke too soon.  ;)  Resistance to RTM'ing is a sensitive issue, I actually deleted a snide remark from my first response to you before I posted it.  
Well, thanks for keeping your cool. I actually have read a lot, but it's confusing because there's really no "manual" but rather a lot of distributed information, and sometimes I have no idea of what I'm looking for. And more than once when looking for documentation on something I was trying to figure out (maybe JACK, maybe FFADO, I found statements like "the documentation is in progress but here's an FAQ." In asking for specifics as to what I needed to do or type in order to accomplish a task, my intent was to see if that would actually solve a problem first, then try to figure out what it actually solved. I write manuals myself, so I, too, will sometimes tell someone to RTFM, but I usually point out where to look and what to look for. 
> 
So Mike, come back in a few months for Ubuntu Maverick Meerkat, when raw1394 has been deprecated and firewire audio will use the long-awaited 'new' firewire driver stack!  Maybe, just maybe, you'll finally get the plug-and-pay functionality you've been hoping for.  
Well, is that in the software design specification?  ;)  

While the latency may still be a real world problem, it seems that the firewire driver stack (I guess we're talking about what talks to the Firewire I/O card, not the Firewire audio device) that I presently have is at least communicating with the card on some level. But what's still apparently on a catch-as-catch-can basis is FFADO which only works with devices that it knows about, or are similar enough to work anyway. And that's going to continue to be a limitation

---

### Post by maghoxfr on 2010-08-13
_[Here's]("http://wiki.linuxmusicians.com/doku.php")_ a cool place to find information on linuxaudio, I've found lifesaving stuff over there. It's not a manual but it has info and lots of links. The forums over there are great too. _[Here's]("https://help.ubuntu.com/community/UbuntuStudio")_ another one.

About routing pulseaudio through jack (I haven't tried it yet, I've been struggling with kernels and stuff in the few moments Im spending on my house), this looks helpful, but I haven't read it thoroughly. I want to try this next because it's annoying switching on/off jack to listen to music, watching tutorials etc.

[link 1]("http://danielnouri.org/notes/2009/6/9/pulseaudio-through-jack-on-jaunty")
[link 2]("http://wiki.archlinux.org/index.php/PulseAudio")
[link 3]("http://ubuntuforums.org/showthread.php?t=1470407")

I'm using 2.6.33-6-rt and got 4ms latency, which is great for me. I couldn't get the drivers of the graphic card to work for this kernel as well as for the general one, so I sticked to the general (I don't need graphics while recording for now).

Thanks for the help.

@MikeRivers and @everyone.
Sorry for behaving as an idiot.

---

### Post by MikeRivers on 2010-08-13
Thanks for those links. I ran across a few of them myself, but I suppose you can never have too many references for this stuff. I've bookmarked them so I'll have them all in one place.

I'll have to take a look at the FFADO configuration file in my system and see if it's the same one that's linked in one of those references. That one includes the Mackie 1200F, of which I have one. Out of curiosity, after I got the Mackie Firewire mixer card working, I tried connecting the 1200F and it didn't have a clue. At the time the only list of supported devices that I believed was the data base on the FFADO web page which reported the 1200F as "unknown."

---

### Post by bojo42 on 2010-08-18
for all those really trying to use the nvidia CS drivers the following might be of interest:

[http://permalink.gmane.org/gmane.linux.rt.user/6229](http://permalink.gmane.org/gmane.linux.rt.user/6229)

[http://permalink.gmane.org/gmane.linux.rt.user/6230](http://permalink.gmane.org/gmane.linux.rt.user/6230)

---

### Post by marcoharder on 2010-09-19
Hi!

I just installed the vanilla Ubuntu on my studio PC and I am planning to have the RT kernel from falkTX's ppa installed. However, I have a few questions, as I failed miserably the last time I tried to install it.

First off, the hardware:

Video Card:
ATI Radeon 9250 256MB

Soundcards:
EMU 1212m v1
ENS1371

Wireless:
Realtek 8188SU USB Wireless Adapter

Now, all of these things work well in vanilla Ubuntu. The last time I tried to use the PPA in this thread, the following happened: Compiz didn't work, I couldn't activate the wireless, and only one sound card would be detected.

I am going to try it again, as I really need to use the RT kernel for recording purposes. Before I do it though, I want to run things by you guys first to make sure I don't ruin my system again. Please check my steps if their order is wrong or whether I missed something:


1. Add falkTX's PPA.

2. Download latest RT kernel.

3. Reboot into the RT kernel. [Hopefully, both soundcards will be detected and Compiz will will work].

4. Compile Realtek USB wireless driver into the new kernel.

5. Reboot into RT kernel.

6. Install fglrx [I did not have to install ATI drivers from the ATI website when I ran Ubuntu vanilla].

Hopefully, this should have both my soundcards in, Compiz working and wireless connecting to the internet.

Any help and feedback would be appreciated.

MH

---

### Post by bojo42 on 2010-09-20
@marcoharder: first you shouldn't use falkTX's PPA if you just want an RT kernel, cause in that case you can go directly for [https://launchpad.net/~abogani/+archive/ppa/](https://launchpad.net/~abogani/+archive/ppa/) .

as for the kernel your a upgrading from 2.6.32 to 2.6.33 and of course that can have some side effects plus. on top of that you change to realtime usage what can also have some surprises. that's why i provide a PPA with kernels that are rebased against the mainline builds from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) , so that you can test 2.6.33 with and without RT usage. see [https://launchpad.net/~bojo42/+archive/rt](https://launchpad.net/~bojo42/+archive/rt) for more.

your steps are right in exception of 6. as you can't use the fglrx driver on a Radeon 9250 and it's good to stay on the open source drivers if you are running a RT kernel.

anyway you can choose your kernel on every boot and it's no big thing to remove the kernel packages again if you run into problems.

---

### Post by marcoharder on 2010-09-21
> **bojo42 said:**
> @marcoharder: first you shouldn't use falkTX's PPA if you just want an RT kernel, cause in that case you can go directly for [https://launchpad.net/~abogani/+archive/ppa/]("https://launchpad.net/%7Eabogani/+archive/ppa/") .

as for the kernel your a upgrading from 2.6.32 to 2.6.33 and of course that can have some side effects plus. on top of that you change to realtime usage what can also have some surprises. that's why i provide a PPA with kernels that are rebased against the mainline builds from [http://kernel.ubuntu.com/~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline") , so that you can test 2.6.33 with and without RT usage. see [https://launchpad.net/~bojo42/+archive/rt]("https://launchpad.net/%7Ebojo42/+archive/rt") for more.

your steps are right in exception of 6. as you can't use the fglrx driver on a Radeon 9250 and it's good to stay on the open source drivers if you are running a RT kernel.

anyway you can choose your kernel on every boot and it's no big thing to remove the kernel packages again if you run into problems.

Thanks, bojo42! So if I get you guys correctly, I do NOT need falktx's PPA if I just need to make sure that the machine can run as a studio PC, is that correct? 

Also, I went into Synaptic and typed in 'real time kernel' and it showed two RT kernels. Should I download those, or should I get abogani's instead?

---

### Post by bojo42 on 2010-09-21
@marcoharder: stock Ubuntu 10.04 does ship an RT kernel (2.6.32) but it's older than Ubuntu's standard kernel (2.6.32) because there are no RT patches for 2.6.32. That was why i started to update the RT kernel packages to 2.6.33 and provide them through a PPA, so did abogani a little later.

So if you can just use the 2.6.31 one or instaldatel a 2.6.33 one via our PPAs (bojo42 or abogani). You shouldn't uses falkTX's when you're want a 2.6.33 kernel, because the kernel packages are just copied from abogani's PPA and it provides really a lot of other new packages that you may don't want.

If you have installed the 2.6.31 kernel package "linux-rt" that comes with Ubuntu and you enable my PPA you will just recieve the 2.6.33 one as an update. When you use abogani's you need to install the new "linux-realtime" package.

---

### Post by marcoharder on 2010-09-22
> **bojo42 said:**
> @marcoharder: stock Ubuntu 10.04 does ship an RT kernel (2.6.32) but it's older than Ubuntu's standard kernel (2.6.32) because there are no RT patches for 2.6.32. That was why i started to update the RT kernel packages to 2.6.33 and provide them through a PPA, so did abogani a little later.

So if you can just use the 2.6.31 one or instaldatel a 2.6.33 one via our PPAs (bojo42 or abogani). You shouldn't uses falkTX's when you're want a 2.6.33 kernel, because the kernel packages are just copied from abogani's PPA and it provides really a lot of other new packages that you may don't want.

If you have installed the 2.6.31 kernel package "linux-rt" that comes with Ubuntu and you enable my PPA you will just recieve the 2.6.33 one as an update. When you use abogani's you need to install the new "linux-realtime" package.

Great, I will try that out this weekend and update you guys. Thanks!

---

### Post by falkTX on 2010-09-24
> **bojo42 said:**
> @marcoharder: first you shouldn't use falkTX's PPA if you just want an RT kernel, cause in that case you can go directly for [https://launchpad.net/~abogani/+archive/ppa/](https://launchpad.net/~abogani/+archive/ppa/) .

as for the kernel your a upgrading from 2.6.32 to 2.6.33 and of course that can have some side effects plus. on top of that you change to realtime usage what can also have some surprises. that's why i provide a PPA with kernels that are rebased against the mainline builds from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) , so that you can test 2.6.33 with and without RT usage. see [https://launchpad.net/~bojo42/+archive/rt](https://launchpad.net/~bojo42/+archive/rt) for more.

your steps are right in exception of 6. as you can't use the fglrx driver on a Radeon 9250 and it's good to stay on the open source drivers if you are running a RT kernel.

anyway you can choose your kernel on every boot and it's no big thing to remove the kernel packages again if you run into problems.

You CAN use fglrx driver on real-time kernels!

My PPA has the realtime packages (copied from abogani's PPA) but the NVIDIA and ATI drivers have special patches to work with the 2.6.33-rt kernel.

I know it will update a lot of your packages (audio app, plugins, etc), but... hm... isn't that suppose to be a good thing? :-k

And, of course, I'll be happy to fix any issue you guys find in those packages.
Sometimes, I even make/apply patches to make sure they work. For example, to get LADI lv1 support ([http://ladish.org/wiki/level1](http://ladish.org/wiki/level1)), I patched Ardour (and ArdourVST), Jack-Mixer and I even made my own patch for Rosegarden: [http://www.mail-archive.com/rosegarden-devel@lists.sourceforge.net/msg14900.html](http://www.mail-archive.com/rosegarden-devel@lists.sourceforge.net/msg14900.html)

---

### Post by bojo42 on 2010-09-24
> **falkTX said:**
> You CAN use fglrx driver on real-time kernels!

i only said that he can't use it on anything less than R600. and of course you can, but the RT patch even touches the open source radeon stuff in the kernel, so it's safe to argue that the integration will be better on open source drivers.

> **falkTX said:**
> 
My PPA has the realtime packages (copied from abogani's PPA) but the NVIDIA and ATI drivers have special patches to work with the 2.6.33-rt kernel.

oops i missed them. btw i like that you make it that easy to use CS drivers on RT :)

> **falkTX said:**
> 
I know it will update a lot of your packages (audio app, plugins, etc), but... hm... isn't that suppose to be a good thing? :-k

yep, but with many changes comes many possibilities for new bugs and unwanted changes. and when you just want a new RT kernel, you shouldn't blindly activate all those changes. and you have a lot of stuff in there ;).

---

### Post by falkTX on 2010-09-26
> **bojo42 said:**
> yep, but with many changes comes many possibilities for new bugs and unwanted changes. and when you just want a new RT kernel, you shouldn't blindly activate all those changes. and you have a lot of stuff in there ;).

I understand.
For those who just want the realtime kernel, a specific PPA for that is good enough.

I dont like to use many PPAs (trusting issue..?), so I just copy what I found useful.
btw, I also have a "bleeding-edge" PPA, with Ardour 3.0 and many SVN packages:
[https://launchpad.net/~falk-t-j/+archive/lucid-latest](https://launchpad.net/~falk-t-j/+archive/lucid-latest)

---

### Post by marcoharder on 2010-09-26
Hi guys,

Finally got to install the 2.6.33 realtime kernel through abogani's PPA but I seem to be having a problem compiling the Realtek 8188 driver. It gives me an error that contains the last few lines when I type in 'make':

> 625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/os_intf/osdep_service.c: In function ‘_rtl_rwlock_init’:
/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/os_intf/osdep_service.c:302: error: implicit declaration of function  ‘init_MUTEX’
make[2]: ***  [/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/os_intf/osdep_service.o] Error 1
make[1]: ***  [_module_/home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100   625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100  625]  Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.33-realtime'
make: *** [modules] Error 2 			 		

Help?

---

### Post by trulan on 2010-09-26
Does that driver even build on 2.6.31-rt?  AFAIK, init_MUTEX(mutex) was removed in the 2.6.31-rt patch and replaced by semaphore_init(mutex).  Then this changed to sema_init(mutex) in 2.6.33-rt.  I know nothing about the code, but I do remember these changes breaking the NVidia binary drivers with each new RT kernel version.  It looks like osdep_service.c will need to be patched to work with these changes.  But I'm afraid that will have to be done by someone who actually knows how to code.  :P

---

### Post by marcoharder on 2010-09-26
Nope, I tried it before on 2.6.31.rt and it won't build in it :( 

Any workaround to this, aside from keeping the generic kernel for my WIFI needs?

MH

---

### Post by trulan on 2010-09-26
I presumed as much.  You're going to either need to patch the Realtek driver, use the generic kernel, or use an old RT kernel (like the one from Hardy or Jaunty), no other options here.

I guess you could try finding line 302 in the file /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/os_intf/osdep_service.c
and see if you can find any references to init_MUTEX, it's possible that changing that to semaphore_init would make it build on 2.6.31-rt, and changing it to sema_init will make it build on 2.6.33-rt.  More than that I don't know what to say.

---

### Post by marcoharder on 2010-09-27
> **trulan said:**
> I presumed as much.  You're going to either need to patch the Realtek driver, use the generic kernel, or use an old RT kernel (like the one from Hardy or Jaunty), no other options here.

I guess you could try finding line 302 in the file /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/os_intf/osdep_service.c
and see if you can find any references to init_MUTEX, it's possible that changing that to semaphore_init would make it build on 2.6.31-rt, and changing it to sema_init will make it build on 2.6.33-rt.  More than that I don't know what to say.


OK, I will try that. Thanks again!

---

### Post by mendred on 2010-10-10
Hi all,

Just thought would let you know that i have managed to get Catalyst 10.9 hotfix working with 2.6.33-rt from abogani's repo.

Note that i tried using the debs from ubuntu swat and falk's repos, but my system would hang on bootup.So i went ahead and made my own

steps
1. Install the kernel image and headers for 2.6.33 from abogani's repo (Refer [https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa) on howto)

1. Download the package [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

2. unzip the 
catalyst_10.9_linux_hotfix_sep27.zip to get 
fglrx-8.771.2

3. in a shell
cd fglrx-8.771.2

4. You need to patch the code before it can work with the rt kernel. Therefore first extract the code


./ati-driver-installer-8.771.2-x86.x86_64.run --extract

This will create  a folder like fglrx-install.n9r7rT (the chars post the dot can change)

Go to 
cd fglrx-install.*
cd common/lib/modules/fglrx/build_mod/ 

Unzip and drop the attached file (firegl_public.c) and replace the same inside. These have been patched as per 
[http://www.phoronix.com/forums/showthread.php?t=24807](http://www.phoronix.com/forums/showthread.php?t=24807)

Note that the patch described in the thread was for a earlier version of fglrx..and therefore it cannot be applied directly but needs to be compared and applied systematically. For all other files, the changes described by the patch are already present in the HF as they relate to getting the driver working with 2.6.33 and beyond. The patches for firegl_public.c relate to the checks to for the realtime patch

5. Once you have dropped the file and overwritten the same, return to the fglrx-install.<your folder name> folder.

6. generate the debs by firing
./ati-installer.sh 8.771 --buildpkg Ubuntu/lucid

7. This will generate deb files in the parent folder. Go to the parent folder 
cd ..
and install the debs
sudo dpkg -i fglrx*.debs

Observe the dpkg readings..the dkms build should be successful and you the packages should be installed.

8. Reboot the system. X should work with the new fglrx on a rt kernel. 

Just a note that these new drivers are awesome. I am getting anywhere between 60-144 fps on redeclipse on the sauerbraten aqueducts map on maxed out settings (whic on 1920x1080 (catalyst 10.3 crawled at 20-30 fps). In addition the earlier 10.9 without hotfix would slow down after soe time of usage, but the hotfix seems to be stable

My ATI card is ATI Mobility HD 5870

Hope this helps. Perhaps someone could package the new debs?


regards,
Bharat

---

### Post by marcoharder on 2010-10-11
> **trulan said:**
> I presumed as much.  You're going to either need to patch the Realtek driver, use the generic kernel, or use an old RT kernel (like the one from Hardy or Jaunty), no other options here.

I guess you could try finding line 302 in the file /home/marcoharder/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100    625/os_intf/osdep_service.c
and see if you can find any references to init_MUTEX, it's possible that changing that to semaphore_init would make it build on 2.6.31-rt, and changing it to sema_init will make it build on 2.6.33-rt.  More than that I don't know what to say.


Didn't work :(

---

### Post by trulan on 2010-10-11
> **marcoharder said:**
> Didn't work :(
OK try this.  Find line 302 of that file (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.c)
and change it from this:
```
#ifdef PLATFORM_LINUX

    init_MUTEX(prwlock);

```to this:
```
#ifdef PLATFORM_LINUX

    sema_init(prwlock,0);
```It also builds with a 1 instead of that 0, we used a 1 in a similar patch on the NVidia driver.  But the line right below it uses a 0 (for XP) so I'd try that first.  But like I said it builds either way, the point is it needs more than one argument for sema_init. Like I said before I know nothing about the code, and I have no way to test it further than this - let me know if it works.

---

### Post by mango42 on 2010-10-14
Hi - this whole thread is way too deep for my poor old brain! :confused:

All I want to do is install an -rt kernel (*any* -rt kernel!) into 10.04 64bit Studio so I can continue trying to get a firewire i/f working but now there's a secondary snag - DVD burning is not possible here at the moment so I used **Unetbootin** to make a USB flashdrive install. It worked perfectly (except for not loading -rt!) but now I'm stuck not knowing how to get Synaptic to recognise that its repositories are on a flash drive and NOT on a DVD!

I asked over on the 'Installation & Upgrade' sub-forum, but I guess they're way too busy dealing with 10.10 issues just now? Also I couldn't get the **nm-applet** .debs to install properly by accessing the /pool/n/ directory (worked last time I tried!) so I can't get that machine on the net to sort it either!

Any suggestions, including 'go away, Linux doesn't need dumb users', gratefully received ;-)

---

### Post by trulan on 2010-10-14
**Edit:** just re-read your post and saw you have net issues as well.  If you can download these three .deb's and copy them to that machine, you should be able to install them manually. This will give you the 2.6.31-rt kernel.
[http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-image-2.6.31-10-rt_2.6.31-10.153_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-image-2.6.31-10-rt_2.6.31-10.153_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-headers-2.6.31-10-rt_2.6.31-10.153_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-headers-2.6.31-10-rt_2.6.31-10.153_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-rt-headers-2.6.31-10_2.6.31-10.153_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/linux-rt/linux-rt-headers-2.6.31-10_2.6.31-10.153_all.deb)

**Then,** reboot.  If your grub menu is hidden (which it will be if you only have one OS installed) hold down 'shift' during bootup to access the menu.  Select 2.6.31-10-rt and hit enter!

---

### Post by mango42 on 2010-10-14
Thanks so much for those links to lead me out of the mire, **trulan**; you're a star! :KS

Should those .debs be installed in any particular order? The 'suck it and see' approach might not be appropriate!

I'm beginning to get the impression that my Synaptic query might be a hot potato, so I'll desist...

Oh, and apologies for hijacking your 'rarified' thread ;-)

---

### Post by trulan on 2010-10-14
Install the linux-image package first, then the headers package (order doesn't matter on those).  Actually, the order isn't a big deal, it will just complain that a dependency is not met if you try the wrong one first.  No harm done.

I don't know about your synaptic problem, never ran into that one.

---

### Post by mango42 on 2010-10-15
> **trulan said:**
> Install the linux-image package first, then the headers package (order doesn't matter on those).  Actually, the order isn't a big deal, it will just complain that a dependency is not met if you try the wrong one first.  No harm done.

Thanks again - my natural inclination would have been to load the headers first ;-)

> 
I don't know about your synaptic problem, never ran into that one.

Seems nobody has - yet USB flash drives have long since superceded CD/DVD, so I figured there must be a way to make Synaptic 'aware' of this rapid progress in bootable storage media...

---

### Post by marcoharder on 2010-10-25
My god. You guys are killer -- typing this via the realtime kernel with the WiFi installed! Woohoo!

> **trulan said:**
> OK try this.  Find line 302 of that file (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/os_intf/osdep_service.c)
and change it from this:
```
#ifdef PLATFORM_LINUX

    init_MUTEX(prwlock);

```to this:
```
#ifdef PLATFORM_LINUX

    sema_init(prwlock,0);
```It also builds with a 1 instead of that 0, we used a 1 in a similar patch on the NVidia driver.  But the line right below it uses a 0 (for XP) so I'd try that first.  But like I said it builds either way, the point is it needs more than one argument for sema_init. Like I said before I know nothing about the code, and I have no way to test it further than this - let me know if it works.

---

### Post by marcoharder on 2010-10-25
Hmm, out of curiosity, is abogani's PPA still updated? I'm getting that red exclamation-point-in-a-triangle in the notification area saying the update information is out of date. I'm thinking that this might be caused by the lack of updates in the PPAs I have in my rig [which are abogani's and Medibuntu, aside from the usual stock Ubuntu repositories]. How can I fix this?

Also, I've been reading reviews about 10.10. How is it from a recording standpoint? Is it really that fast? Does it now have a realtime kernel?

MH

---

### Post by trulan on 2010-10-25
> **marcoharder said:**
> My god. You guys are killer -- typing this  via the realtime kernel with the WiFi installed! Woohoo!
Awesome!!
> **marcoharder said:**
> Also, I've been reading reviews about 10.10. How is it from a recording standpoint? Is it really that fast? Does it now have a realtime kernel?
OK, maybe, and no.  For more info check these threads:
[http://ubuntuforums.org/showthread.php?t=1602827](http://ubuntuforums.org/showthread.php?t=1602827)
[http://ubuntuforums.org/showthread.php?t=1592067](http://ubuntuforums.org/showthread.php?t=1592067)

---

### Post by marcoharder on 2010-10-25
> **trulan said:**
> Awesome!!

OK, maybe, and no.  For more info check these threads:
[http://ubuntuforums.org/showthread.php?t=1602827](http://ubuntuforums.org/showthread.php?t=1602827)
[http://ubuntuforums.org/showthread.php?t=1592067](http://ubuntuforums.org/showthread.php?t=1592067)

Looks like I'll have to stay with 10.04 then, which isn't so much of a bad deal since I have at least a year and a half of support remaining for it! 

Started working on a demo a few minutes ago. I am seriously about to dump WinXP!

MH

---

