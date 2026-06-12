---
title: "Mount a Virtual Box .vdi as a logical drive in Ubuntu"
date: 2008-07-26
forum: Virtualisation
---

### Post by xvistafan on 2008-07-26
Is there any way I could mount a .vdi (with XP installed) as a logical partition? Or infact just veiw the contents of the .vdi and copy them to an empty logical drive that I have and Boot from it (yes I will have to check the boot flag on that partition using GParted or something or repair it with the XP CD but that doesn't take much time compared to installing it fresh and installing all the app's etc on it)
(I read that something called [losetup]("http://linuxcommand.org/man_pages/losetup8.html")can do it but I have no clue how to use it)
Any help people? 
PS: Ubuntu with Compiz Fusion kicks Vista+OSX butt \\:D/

---

### Post by przemoc on 2008-11-10
Look at my how-to based on basic shell tools:
[Mounting partition from VDI fixed-size image]("http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image")

Unfortunately this works only with fixed-size images on little-endian machines.

---

### Post by stinger30au on 2008-11-10
> **przemoc said:**
> Look at my how-to based on basic shell tools:
[Mounting partition from VDI fixed-size image]("http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image")

Unfortunately this works only with fixed-size images on little-endian machines.


i hate to sound stupid, but what is a little-endian???
where do you get it??

---

### Post by przemoc on 2008-11-10
> **stinger30au said:**
> i hate to sound stupid, but what is a little-endian???

Long answer: [http://en.wikipedia.org/wiki/Endianness]("http://en.wikipedia.org/wiki/Endianness").
Short answer (part from wikipedia): Well known processor architectures that use the little-endian format include x86, 6502, Z80, VAX, and, largely, PDP-11.

So anyone with x86 or x86_64 CPU has little-endian machine. VirtualBox currently doesn't support any other architectures, but linux works also on big-endian machines and that is why I made a comment about endianness.

---

### Post by imi1984 on 2009-10-02
[You are wanting to clone.]("http://srackham.wordpress.com/cloning-and-copying-virtualbox-virtual-machines/")

---

### Post by antiplex on 2011-06-23
yes, i do know this thread is somewhat old, nevertheless i came across this multiple times during my search for a possibility to directly access a virtualbox .vdi .

after quite some browsing and reading i came across [this very helpful blogentry by jeff waugh]("http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/") describing the following solution that takes advantage of the nbd (network block device) kernel module + qemu-nbd:

- make sure you have qemu-nbd available (can be found in the qemu-kvm package)
- load the nbd module through ' [FONT="Courier New"]**sudo modprobe nbd**[/FONT] '
- let qemu-nbd provide a loopback block device for the vdi ' [FONT="Courier New"]**sudo qemu-nbd -c /dev/nbd0 <vdi-file>**[/FONT] ' and find your .vdi in the device /dev/nbd0 and its partitions in /dev/nbd0p1, /dev/nbd0p2 and so on.
- mount your desired partition(s) or do whatever you want with these devices (format, change partitions...)
- when done, remove the blockdevices (after unmounting etc) through ' [FONT="Courier New"]**sudo qemu-nbd -d /dev/nbd0**[/FONT] '.

the original author states that this also works with both, static and dynamically sized .vdi images but so far i only tried static ones which worked just fine!

many thanks to the original author jeff!


**edit:**
just in case virtualbox refuses to run a vm after you went through the previously described scenario with an error mentioning something like '*VirtualBox can't enable the AMD-V extension. Please disable the KVM kernel extension, recompile your kernel and reboot*' it might be necessary to unload the kvm-modules bei either issuing ' [FONT="Courier New"]**sudo rmmod kvm-intel**[/FONT] ' or ' [FONT="Courier New"]**sudo rmmod kvm-amd**[/FONT] '. you can use ' [FONT="Courier New"]**sudo lsmod**[/FONT] ' to see which modules are currently loaded.

enjoy,
antiplex

---

### Post by humilleitor on 2011-07-12
Thank you for this, but it doesn't work for me. When running qemu-nbd -c /dev/nbd0 /image.vdi I get an error (originating from the ndb.c module): "Failed setting NBD block size".

Any suggestions?

---

