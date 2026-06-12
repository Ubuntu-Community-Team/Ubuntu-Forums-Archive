---
title: "Kernel 4.17RC (Release Candidate) series"
date: 2018-04-18
forum: Ubuntu Development Version
---

### Post by Doug S on 2018-04-18
Kernel 4.17-rc1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc1/").

There is a major re-work of the idle loop included, and some users may or may not notice an improvement in energy consumption. See also [here]("https://bugzilla.kernel.org/show_bug.cgi?id=199227"). Please post here (or directly on the bug report) any energy observations.

---

### Post by zika on 2018-04-20
For those following [drm-tip]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/") or [daily]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/"): wait for modules .deb file since image-unsigned depends on it not only on paper but really...
[Drm-next]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/") is not yet affected but is stale anyway......
Update&#8321;: Nice to see that 4.15.0-19-generic from Canonical PPA already adopted that compartmentalisation... Waiting for mainline to do so too and fulfill declared dependency that prevent use of cooked .deb files...
Update&#8322;: All is good now in drm-tip... ;)

---

### Post by Doug S on 2018-04-29
Kernel 4.17-RC3 is available, but the [mainline PPA build]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc3/") seems to have failed.
If it isn't fixed by tomorrow, I'll ask about it on the kernel team IRC channel.

Myself, I am still testing the idle loop changes, using kernel 4.16 and the same + the idle loop changes.

Are others noticing any power saving with the 4.17 rc series? The savings should be most noticeable on computers with many CPUs.

EDIT: Someone already mentioned on the kernel team IRC channel that the mainline build for kernel 4.16.6 failed, so I added a note about the 4.17-rc3 failed build.

---

### Post by fyfe54 on 2018-04-29
4.16.6 mainline available now.

---

### Post by zika on 2018-04-30
> **Doug S said:**
> Are others noticing any power saving with the 4.17 rc series? The savings should be most noticeable on computers with many CPUs.I've noticed difference between lowlatency and generic, latter more frugal... Not having 4.16 fom the start of 4.17 makes it difficult for me to tell, summer came here early, just at that time... ;) Will check 4.16.6 soon...

---

### Post by Doug S on 2018-04-30
The mainline kernel [4.17-rc3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.17-rc3/") is now there, however, I can not install it, because of dependency issues:
```
dpkg: dependency problems prevent configuration of linux-headers-4.17.0-041700rc3-lowlatency:
 linux-headers-4.17.0-041700rc3-lowlatency depends on libssl1.1 (>= 1.1.0); however:
  Package libssl1.1 is not installed.

```Because my main test server is still using 16.04.4, I suppose.
If I compile and install the kernel myself, it works fine.

EDIT: What a mess. Things now seem to need a program, "linux-update-symlinks", which I do not have on my computer. It it used by /var/lib/dpkg/info/linux-image-unsigned-4.17.0-041700rc3-lowlatency.postinst and /var/lib/dpkg/info/linux-image-unsigned-4.17.0-041700rc3-lowlatency.postrm. so I can not purge or completely install the kernel.

...Later... I was able to completely purge by first removing these files:
```

/var/lib/dpkg/info/linux-image-unsigned-4.17.0-041700rc3-lowlatency.prerm
/var/lib/dpkg/info/linux-image-unsigned-4.17.0-041700rc3-lowlatency.postrm
/var/lib/dpkg/info/linux-image-unsigned-4.17.0-041700rc3-lowlatency.postinst

```
Summary: The package "linux-base (4.0ubuntu1)" for Xenial doesn't have the files they are now using. The package "linux-base (4.5ubuntu1)" for artful and bionic does have the files.
Conclusion: Be careful.

EDIT 2: Someone on the kernel team IRC suggested that I install linux-base from xenial-proposed. That did solve my removal problems, but not the libssl version dependency problem. However the kernel does seems to install, and does seem to boot, even though linux-headers-4.17.0-041700rc3-lowlatency ends up unconfigured. Anyway, I can steal /boot/config-4.17.0-041700rc3-lowlatency and use it as .config in my kernel.org git source tree to compile the kernel myself, which is really all I ever want from the mainline PPA.

---

### Post by P-I H on 2018-05-26
Installed the 4.17.0-041700rc6 kernel.
Downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
- linux-headers-4.17.0-041700rc6
- linux-headers-4.17.0-041700rc6-generic
- linux-image-unsigned-4.17.0-041700rc6-generic
- linux-modules-4.17.0-041700rc6-generic
Installed with sudo dpkg -i *.deb
Works fine.
journalctl -p err -b, gives some new errors, but some has vanished.
Ubuntu Cosmic Cuttlefish
```
-- Logs begin at Sun 2018-04-29 13:05:05 CEST, end at Sat 2018-05-26 22:20:34 CEST. --
maj 26 22:20:09 pi-MS-7A34 [518]: failed to execute '/lib/udev/ifupdown-hotplug' 'ifupdown-hotplug': Permission denied
maj 26 22:20:09 pi-MS-7A34 [541]: failed to execute '/lib/udev/ifupdown-hotplug' 'ifupdown-hotplug': Permission denied
maj 26 22:20:09 pi-MS-7A34 kernel: kvm: disabled by bios
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: Duplicate cookie detected
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: O-cookie c=00000000f944d7ee [p=00000000ad78168b fl=222 nc=0 na=1]
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: O-cookie d=00000000e59a4ae0 n=00000000391237d2
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: O-key=[10] '040002000801c0a80106'
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: N-cookie c=00000000d648520d [p=00000000ad78168b fl=2 nc=0 na=1]
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: N-cookie d=00000000e59a4ae0 n=00000000ab66cfbf
maj 26 22:20:13 pi-MS-7A34 kernel: FS-Cache: N-key=[10] '040002000801c0a80106'
maj 26 22:20:13 pi-MS-7A34 gnome-session-binary[1352]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freede
maj 26 22:20:14 pi-MS-7A34 systemd[1]: Failed to start resolvconf-pull-resolved.service.
maj 26 22:20:14 pi-MS-7A34 colord-sane[1061]: io/hpmud/pp.c 627: unable to read device-id ret=-1
maj 26 22:20:15 pi-MS-7A34 spice-vdagent[1500]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
maj 26 22:20:27 pi-MS-7A34 spice-vdagent[2003]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
~
```
Ubuntu 18.04
```
-- Logs begin at Mon 2018-04-16 18:28:05 CEST, end at Sat 2018-05-26 22:18:11 CEST. --
maj 26 22:17:47 pi-MS-7A34 kernel: Couldn't get size: 0x800000000000000e
maj 26 22:17:47 pi-MS-7A34 kernel: MODSIGN: Couldn't get UEFI db list
maj 26 22:17:47 pi-MS-7A34 kernel: Couldn't get size: 0x800000000000000e
maj 26 22:17:47 pi-MS-7A34 kernel: amdgpu 0000:21:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
maj 26 22:17:47 pi-MS-7A34 systemd-udevd[443]: Invalid rule /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14: unknown key 'SYSFS{idVendor}'
maj 26 22:17:48 pi-MS-7A34 avahi-daemon[1101]: chroot.c: open() failed: No such file or directory
maj 26 22:17:53 pi-MS-7A34 colord-sane[1192]: io/hpmud/pp.c 627: unable to read device-id ret=-1
maj 26 22:17:54 pi-MS-7A34 spice-vdagent[2051]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
maj 26 22:18:04 pi-MS-7A34 spice-vdagent[2667]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
~

```

---

### Post by Cheltspy on 2018-05-29
I complained about this weeks ago to no answer. whatever has changed is also affecting stable builds.

The last build I could install was 4.17-rc1.

---

