---
title: "Intel DN2800MT motherboard, video black with Ubuntu server &gt;= 12.04.3"
date: 2014-10-29
forum: Server Platforms
---

### Post by Jonathan L on 2014-10-29
Hi All

Documenting a fix for video problems with this motherboard and **server edition** Ubuntu.  (There are many threads on this an other noticeboards about black screen with desktop edition, and complaints about this quite rare graphics system, and perhaps these notes will help those people too.)

I have about half a dozen of these installed (as various kinds of chemical plant monitoring systems) with solid state mSata drives.  They have been working perfectly well with Ubuntu 12.04.2 server; when we tried later versions, the video is black on startup.  This was a problem in case we needed to upgrade Ubuntu for any reason.

Just to be clear: we're using long-term support server images only, and are only interested in command line 'video'.  We normally have them with text mode graphics (ie, [FONT=courier new]GRUB_TERMINAL=console[/FONT] in /etc/defaults/grub), but the higher resolution 'bitmapped text' also works, (and I'd guess proper graphics would also work, though I haven't tried it). Although some have screens, they are normally used headless over ssh.

In brief, the gma500.gfx driver fails in some way and the screen is blanked.  Extensive experimentation with [FONT=courier new]nomodeset[/FONT] and similar didn't succeed, but blacklisting the driver did.  Video is presumably driven by default video driver, presumably more slowly than whatever optimisations the gma500 driver has.

Tried with very plain server installations (just SSH, no other packages added)

[LIST]
[*]ubuntu-12.04-server-i386.iso works fine (no gma500_gfx.ko) 
[*]ubuntu-12.04.1-server-i386.iso works fine (no gma500_gfx.co) 
[*]ubuntu-12.04.2-server-i386.iso works fine with gma500_gfx.ko of 2013-01-25 filestamp 
[*]ubuntu-12.04.3-server-i386.iso **works if gma500_gfx is blacklisted** 
[*]ubuntu-12.04.4-server-i386.iso **works if gma500_gfx is blacklisted** 
[*]ubuntu-12.04.5-server-i386.iso **works if gma500_gfx is blacklisted** 
[*]ubuntu-14.04.1-server-i386.iso **works if gma500_gfx is blacklisted ** 
[/LIST]

Blacklisting the gma500_gfx can be done at installation time with the standard installer, per-boot with GRUB menu, or permanently in /etc/modprobe.d/blacklist.conf

To blacklist with installer: Select Install Ubuntu Server, press F6 Other Options, Escape.  Now you can edit the boot line.  Add [FONT=courier new]gma500_gfx.blacklist=yes[/FONT] just after [FONT=courier new]quiet[/FONT]

To blacklist just once in GRUB menu: boot, get to GRUB menu, press 'e' for edit, edit the [FONT=courier new]linux[/FONT] line, add [FONT=courier new]modprobe.blacklist=gma500_gfx[/FONT] at end of line just after [FONT=courier new]ro[/FONT]

To blacklist once logged in (perhaps by ssh or GRUB method): edit /etc/modprobe.d/blacklist.conf or create /etc/modprobe.d/blacklist.local.conf and add a line ```
blacklist gma500_gfx
```

Hope that helps someone.  Certainly it's given a new lease of life to this hardware in my environment.

Kind regards,

Jonathan.

PS. It's not clear what the actual problem is.  In case anyone knows, here's some log output:

With the gma500_gfx driver loaded (ie, with blacked-out video), 12.04.4 (kernel 3.11.0-15-generic) shows the following in syslog:

```
Oct 29 15:47:42 shakespeare kernel: [    3.421995] gma500 0000:00:02.0: setting latency timer to 64
Oct 29 15:47:42 shakespeare kernel: [    3.424324] gma500 0000:00:02.0: irq 45 for MSI/MSI-X
Oct 29 15:47:42 shakespeare kernel: [    3.424464] gma500 0000:00:02.0: GPU: power management timed out.
Oct 29 15:47:44 shakespeare kernel: [    5.338137] [drm] Initialized gma500 1.0.0 2011-06-06 for 0000:00:02.0 on minor 0
```

I suspect the actual problem is the 'power management timed out'

```
lshw -C video
  *-display               
       description: VGA compatible controller
       product: Atom Processor D2xxx/N2xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:45 memory:d0500000-d05fffff ioport:30d0(size=8)


```

---

### Post by Jonathan L on 2014-10-29
Link to bug report: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)

---

