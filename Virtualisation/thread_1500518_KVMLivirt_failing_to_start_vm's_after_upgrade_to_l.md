---
title: "KVM/Livirt failing to start vm's after upgrade to linux-image-2.6.32-22-generic"
date: 2010-06-03
forum: Virtualisation
---

### Post by duncs on 2010-06-03
My VM's were working fine yesterday on my up-to-date Lucid system.

Noticed a new kernel release this morning, did an upgrade and now my VM's wont boot.

This is as much as the /var/log/libvirt/qemu/dev10.log log file tells me:
```

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -cpu qemu32 -enable-kvm -m 812 -smp 1 -name dev10 -uuid 47615a48-2f06-c731-b20d-8db124f79f7e -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/dev10.monitor,server,nowait -monitor chardev:monitor -boot c -drive file=/srv/vm_disks/dev10/disk0.qcow2,if=ide,index=0,boot=on -drive if=ide,media=cdrom,index=2 -net nic,macaddr=52:54:00:24:c8:5a,vlan=0,name=nic.0 -net tap,fd=34,vlan=0,name=tap.0 -chardev pty,id=serial0 -serial chardev:serial0 -parallel none -usb -vnc 127.0.0.1:0 -k en-gb -vga cirrus 
char device redirected to /dev/pts/2
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"
```

The console for the VM is blank and cpu use in virt-manager is constant.  If i boot back into the previous kernel I have available the vm's can start again (however, due to nvidia driver silliness I cannot use that kernel easily as my dual screen don't work).

Anyone else upgraded and found a problem with their VM's?

  Duncs

---

### Post by Kokopelli on 2010-06-03
This is happening to me as well. I have not tried to debug it much, came here to see if anyone else has the same problem.  A quick search implies that is is a problem with libvirt.

---

### Post by mgu on 2010-06-03
All the same here :(

The message log you put does not seems to be relevant since it is also displayed when VMs works fine (with **2.6.32-21)**

> char device redirected to /dev/pts/2
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"I boot back with the previous kernel too.
Best regards

---

### Post by Kokopelli on 2010-06-03
The pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin" is a red herring.  Adding the kvm-pxe package gets rid of that message but the VMs still do not start.  I am not sure what is causing it yet.  Has anyone tried launching directly from the command line using "kvm <options>"?

EDIT tried a simple "kvm -m 1024 -drive file=/dev/eli/test1" and it never even got to the launching of the BIOS.

---

### Post by cajsaj on 2010-06-03
Same problem here too. Switched to previous kernel and everything looks ok.

Log file shows:
    Could not open option rom 'pxe-rtl8139.bin': No such file or directory

I tried the other network devices, and they each gave a similar message. It looks like the rom files have been removed..? May be related to this:
    [https://bugs.launchpad.net/ubuntu/+source/etherboot/+bug/472485](https://bugs.launchpad.net/ubuntu/+source/etherboot/+bug/472485)

---

### Post by duncs on 2010-06-03
> **Kokopelli said:**
> The pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin" is a red herring.  Adding the kvm-pxe package gets rid of that message but the VMs still do not start.  

I have that installed and I still get the error, but yes it is probably a red herring.

> **Kokopelli said:**
> I am not sure what is causing it yet.  Has anyone tried launching directly from the command line using "kvm <options>"?

EDIT tried a simple "kvm -m 1024 -drive file=/dev/eli/test1" and it never even got to the launching of the BIOS.

Yes, I tried the command line running too and make no difference for me.

  Duncs

---

### Post by duncs on 2010-06-03
> **mgu said:**
> All the same here :(

The message log you put does not seems to be relevant since it is also displayed when VMs works fine (with **2.6.32-21)**

Trouble is I haven't yet found any relevant logging about the problem.

A quick strace shows
```

[pid  3641] rt_sigprocmask(SIG_BLOCK, [BUS ALRM IO], NULL, 8) = 0
[pid  3641] signalfd(4294967295, [BUS ALRM IO], 8) = 16
[pid  3641] fcntl(16, F_GETFD)          = 0
[pid  3641] fcntl(16, F_SETFD, FD_CLOEXEC) = 0
[pid  3641] fcntl(16, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
[pid  3641] write(15, "\1\0\0\0\0\0\0\0", 8) = 8
[pid  3641] futex(0x869ae4, FUTEX_CMP_REQUEUE_PRIVATE, 1, 2147483647, 0x869a60, 2) = 1
[pid  3641] futex(0x869a60, FUTEX_WAKE_PRIVATE, 1 <unfinished ...>
[pid  3642] <... futex resumed> )       = 0
[pid  3641] <... futex resumed> )       = 0
[pid  3642] futex(0x869a60, FUTEX_WAKE_PRIVATE, 1 <unfinished ...>
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {0, 0} <unfinished ...>
[pid  3642] <... futex resumed> )       = 0
[pid  3641] <... select resumed> )      = -1 EBADF (Bad file descriptor)
[pid  3642] rt_sigtimedwait([BUS RT_6],  <unfinished ...>
[pid  3641] timer_gettime(0, {it_interval={0, 0}, it_value={0, 0}}) = 0
[pid  3641] timer_settime(0, 0, {it_interval={0, 0}, it_value={0, 250000}}, NULL) = 0
[pid  3641] write(15, "\1\0\0\0\0\0\0\0", 8) = 8
[pid  3641] timer_gettime(0, {it_interval={0, 0}, it_value={0, 182897}}) = 0
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
[pid  3641] select(35, [4 5 8 11 13 14 16 34], [], [], {1, 0}) = -1 EBADF (Bad file descriptor)
.... last line repeats continually ....

```

More digging required.

  Duncs

---

### Post by bbrand on 2010-06-03
Sigh, same here, been trying to get something working all day. No luck so far. Did anyone log this bug yet?

---

### Post by Frogs Hair on 2010-06-03
I have found my computer is flaky when it comes to kernel updates . what works every time for me is removing the proprietary Nvidia driver prior to kernel installation and then booting with the new kernel and reinstalling the driver. This requires changing the update settings to notify only.

---

### Post by Kokopelli on 2010-06-03
It has not been logged as a bug yet as far as I can see.  Since this bug directly effects kvm I am guessing it effects cloud install as well.  I expect that it will get noticed fairly quickly if that is the case.

---

### Post by duncs on 2010-06-03
I have logged as [https://bugs.launchpad.net/ubuntu/+bug/589223](https://bugs.launchpad.net/ubuntu/+bug/589223) against qemu-kvm though it may get moved to kernel.

  Duncs

---

### Post by Jimbob0i0 on 2010-06-03
Beat you to that bug report - spent most of this afternoon debugging ;)

See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/589163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/589163)

I've managed to isolate it to a change between 2.6.32-22.33 and 2.6.21-22.35...

The .33 kernel was on proposed but .35 skipped proposed and went straight to release.

The .33 kernel is no longer in the proposed repo so if you want to install it you have to get it straight from the launchpad build here:

[https://launchpad.net/ubuntu/lucid/amd64/linux-image-2.6.32-22-generic/2.6.32-22.33](https://launchpad.net/ubuntu/lucid/amd64/linux-image-2.6.32-22-generic/2.6.32-22.33)

I can confirm that kernel does work on my system for the KVM guests and the .35 kernel breaks KVM.

The only think that appeared to touch KVM in that release was a fix for CVE-2010-0419 ....

---

### Post by duncs on 2010-06-03
> **Jimbob0i0 said:**
> Beat you to that bug report - spent most of this afternoon debugging ;)

Thanks - it helps when someone knows what they are meant to be doing ;-)

I have downgraded to .33 and a Win7 vm works ok, but a Lenny vm hangs - however, this is better than it was...

I have marked by bug as a dup of yours.  I'll have to learn how to search for bugs better.

  Duncs

---

### Post by Jimbob0i0 on 2010-06-03
> **duncs said:**
> Thanks - it helps when someone knows what they are meant to be doing ;-)

I have downgraded to .33 and a Win7 vm works ok, but a Lenny vm hangs - however, this is better than it was...

I have marked by bug as a dup of yours.  I'll have to learn how to search for bugs better.

  Duncs

Hehe no prob... besides I just got there first next time it'll be someone else and I'll be marking my bug a dup ;)

According to the report it has been triaged and fixed with a new kernel being built now so we should get an update soon with a working kernel :)

Not bad really... 4 1/2 hours from bug lodged to fix committed.... :)

---

### Post by awry on 2010-06-03
I got bit by this bug this morning and wasted a good 4-6 hours on it.

This is truly frightening, especially in an LTS release.

How did this kernel get released without going through the normal process???

I'd like to hear some answers!

---

### Post by Jimbob0i0 on 2010-06-03
> **awry said:**
> I got bit by this bug this morning and wasted a good 4-6 hours on it.

This is truly frightening, especially in an LTS release.

How did this kernel get released without going through the normal process???

I'd like to hear some answers!

I asked this very question on the mailing list. It was a security update which has a different qa process to standard updates and doesn't go through proposed... and in this case wa failed. It happens and just serves as a reminder to always test an update on a non-critical system you can safely revert before pushing out to others :-) 

4 1/2 hours from report to fix committed is pretty impressive... at least we don't have to wait for the next patch Tuesday ;-)

---

### Post by Jimbob0i0 on 2010-06-04
FYI fix released ...

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-June/001101.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-June/001101.html)

---

### Post by wcorey on 2010-06-27
I have never seen that message starting cloud instances, perhaps it is obscured. However I do see that message when natively starting an image under kvm, 

sudo kvm -m 2048 -drive  file=image.img,if=scsi,index=0,boot=on -boot c -net nic -net user -cpu kvm64 -vnc :0
[sudo] password for walt: 
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"


The image does, however, start just fine.

current system -
$ uname -r
2.6.32-22-generic

Maybe I am already at the fixed level yet I still receive the message.

---

### Post by ottont on 2010-07-02
Hi,

Forgive my dumbness, but what is the best way to install this kernel patch?

I've two Dell servers with intel core duo 64 bit processors. I tried to download
the 4 arch independent packages and 43 packages listed under the amd64 arch,
and install them one-by-one using: dpkg -i packagename

Right off the bat, it tells me linux-image-2.6.32-22-virtual_2.6.32-22.36_amd64.deb
conflicts with linux-image-2.6.32-22-server_2.6.32-22.36_amd64.deb, and there are 
interdependencies among packages so it will complain about dependency missing.

This KVM migration error with lucid ubuntu is driving me mad :(

---

### Post by wcorey on 2010-07-05
> **Jimbob0i0 said:**
> FYI fix released ...

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-June/001101.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2010-June/001101.html)


OK, you are running two machines both running ubuntu server. You may have already done this but did you try the command lines:

sudo apt-get update
sudo apt-get dist-upgrade

I've never done it via dpkg. I am not sure what that may or may not have done to your system.

Just so you'll know, I have a ubuntu 10.4, fedora13, and Windows2003 all running perfectly as guests started via virt-manager on my system here at

2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux.

What I am wanting to do is convert them to EKI, ERI, and EMI under UEC. Best of all there is no or virtually no (pun intended) dual mouse pointer lag.

---

### Post by robertlight on 2010-11-09
I'm running an image of ubuntu-2.6.32-24-server on a node controller.  The first image is launched just fine, from then on...the same image launched again gives me the error:

libvirt: operation failed: failed to retrieve chardev info in qemu with 'info chardev' (code=9)

---

### Post by robertlight on 2010-11-10
I am stubbing my toe on this very problem...first instance starts up fine...if I try to start it again (and have 2 or more) it fails with the "failed to retrieve chardev info in qemu with 'info chardev' (code=9)" error.

How did you ultimately solve this problem?

---

