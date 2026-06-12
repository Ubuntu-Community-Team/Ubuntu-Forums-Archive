---
title: "PXE Boot Fails on Ethernet Configuration - IP-Config"
date: 2018-10-15
forum: Server Platforms
---

### Post by Qchan on 2018-10-15
There are a lot of people who have problems with this. I know I've had issues with this. So, I felt like it was a good enough time to show the world the solution I've found.

So, here's the log and short of it...

When booting up a PXE diskless client, if that client happens to have multiple networking interfaces, the kernel may either crash into a kernel panic, or IP-Config will hang.

The reason this happens is because there's a bug in IP-Config and nobody really cares to fix it. Essentially, IP-Config is hitting the DHCP server too quickly and repetitively. Because of that, the DHCP doesn't respond the second (or third) time the IP-Config hits it. Therefore, IP-Config is unable to resolve a DHCP and without an IP, the root directory can't be set up and then the kernel crashes.

The work around is this (if you're using iPXE):

```

kernel ${base-url}vmlinuz-4.4.0-43-generic boot=nfs netboot=nfs quiet splash panic=30 nfsroot=10.0.0.1/root network ksdevice=bootif BOOTIF=${netX/mac} ip=${ip}:192.168.1.1:192.168.1.1:255.255.255.0:::none
initrd ${base-url}initrd.img-4.4.0-43-generic

```

If you're using regular PXE:

```

KERNEL vmlinuz-4.4.0-43-generic
IPAPPEND 2
APPEND vga=794 boot=nfs root=/dev/nfs initrd=initrd.img-4.4.0-43-generic quiet splash panic=30 -- nfsroot=192.168.1.1:/root ip=192.168.1.2:192.168.1.1:192.168.1.1:255.255.255.0:::none

```

I don't expect that your entries will look exactly like this. These are just __examples__. So, edit yours accordingly.

1) You need to set a static IP address directly in the kernel params (or the append). If you don't, IP-Config is going to try to run DHCP and __you don't want that__. 

2) You want to force PXE to only query from one NIC interface and not from all of them. To force it to only use one interface, you use "network ksdevice=bootif BOOTIF=${netX/mac}" in iPXE and you use "IPAPPEND 2" in regular PXE. Write it exactly as shown above.

That's it! Two easy steps and you'll be on your way.

The BOOTIF forces PXE to only use the primary interface that the PXE was loaded on. It'll ignore all the other interfaces. IPAPPEND does the exact same thing.

---

