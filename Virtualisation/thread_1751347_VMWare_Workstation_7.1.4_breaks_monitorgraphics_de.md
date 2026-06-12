---
title: "VMWare Workstation 7.1.4 breaks monitor/graphics device detection?"
date: 2011-05-06
forum: Virtualisation
---

### Post by jwatte on 2011-05-06
I have been using Ubuntu 10.10 for a long time running within VMWare Workstation. In fact, this machine has gone from 9.04 to 10.04 to 10.10, and from Workstation 7.0 to 7.1, over its lifetime. It's Ubuntu 32-bit.

I am running this on a Dell XPS 1340 laptop with a dual Intel/NVIDIA graphics card.

All through this time, I've been able to make the VM fit the display of the laptop (1280x800) or the attached external display (1200x1600) as appropriate, and it's been great!

However, when I upgraded to Workstation 7.1.4 from 7.1.3, and re-installed the appropriate VMWare Tools, Ubuntu 10.10 no longer recognizes the graphics device. The maximum resolution it will let me run at is 1280x720, which doesn't fill the laptop screen, much less the larger external screen. In the Ubuntu Monitors control panel, the monitor is displayed as "unknown."

I have tried various settings in VMWare Workstation, including enabling/disabling 3D acceleration, and enabling/disabling automatic graphics device allocation -- including setting it to always providing 2 devices of size 2560x1600, which should be plenty to cover the physical desktop.

I tried re-creating the VM from scratch, pointing it at a copy of the disk image, but still have the same problem, so my guess is that it's something on the Ubuntu side that's going wrong, rather than the hosting environment. I've tried poking around at the XFree86 system side, but I'm not very well versed in what kinds of controls and configurations would affect this problem -- the last time I played around with Xdefaults and Xresources and device specifications was at the time of X11R3, and apparently things have changed enough since then that I don't quite feel at home :-)

So, I'm looking for any help or hints in debugging this problem. What config files can I edit on the Ubuntu side to make it believe that I have a device capable of sizing to 1280x800 and/or 1200x1600 (portrait). I only need one of them at a time -- I don't need multi-monitor coverage.

I've kept a question open on the VMWare Workstation forums for a long time, but gotten no suggestions there, btw.

---

### Post by jwatte on 2011-05-08
Nobody can even tell me where to look for information on how to debug this? I'm out in the cold here.

When trying to enable VMWare Unity (host and guest windows mixed on the desktop), VMWare complains that the guest does not support changing the display resolution, which is consistent with what I see in the Monitors control panel.

The only VGA/display related things I could find in /var/log/messages is:

```
May  6 14:13:02 jwatte-hello-ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
May  6 14:13:02 jwatte-hello-ubuntu kernel: [    0.547481] vgaarb: device added: PCI:0000:00:0f.0,decodes=io+mem,owns=io+mem,locks=none
May  6 14:13:02 jwatte-hello-ubuntu kernel: [    0.547504] vgaarb: loaded

```

Here's a screen shot of that control panel:

[IMG]http://watte.net/monitors-ubuntu-control-panel.png[/IMG]

The problem might be that the system does not recognize the virtual graphics device as having enough RAM, or being capable of extended resolutions. What log files and config files should I look in to start debugging this?

---

### Post by jwatte on 2011-05-08
So, after digging a fair bit more, I've found and looked through /var/log/Xorg.0.log, which has some lines that may or may not matter:

[    25.355] (II) VESA(0): VESA VBE PanelID invalid
...
[    25.452] (WW) VESA(0): Unable to estimate virtual size
...

It ends up assuming some conservative defaults which do not allow 1280x800, or anything larger like 1200x1600.

The xorg.conf files that exist on the system are:
```
10-evdev.conf      50-vmmouse.conf  51-synaptics-quirks.conf
50-synaptics.conf  50-wacom.conf    60-magictrackpad.conf

```

... there are no others. Specifically, there is no file that contains a Monitor or Display or Mode or ModeLine directive.

Given that the defaults are detected as such low spec, and that this worked before, what's wrong with this configuration? Is there a file that should be installed/created for the VMWare VGA device to be properly detected?

---

### Post by jwatte on 2011-05-08
More clues. I re-ran the vmware-config-tools.pl, and carefully inspected the output. Here's what it says:

```
Detected Xorg X server version 1.9.0.

Distribution provided drivers for Xorg X server are used.

Skipping X configuration because X drivers are not included.

```

Aptitude does claim that xserver-org-video-vmware drivers are included in the xserver-org-video-all package. However, apparently, these drivers don't correctly recognize my system after upgrading to VMWare 7.1.4?

Or is there some xorg.conf file I should have that specifies graphics devices and monitors, and it's somehow gotten lost? If so, how do I re-create it?

---

