---
title: "Use udevadm to test for printer offline?"
date: 2014-03-07
forum: Ubuntu Application Development
---

### Post by Eric_Lee on 2014-03-07
[COLOR=#000000][FONT=Tahoma]I want to test that a printer on a parallel port is available, that sending a file to it will not fail because it is offline, off, cover open, out of paper.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]My reading of the udevadm manpage suggests that it might be used for this but it isn't clear how, or maybe my reading is too hopeful.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Is this the right approach; is there a better way?[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Ubuntu: 12.04.4[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]The printer is on /dev/lp0, can be written to, and is defined for udev:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Tahoma]    $ udevadm info --name=/dev/lp0 --query=all[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    P: /devices/pnp0/00:07/printer/lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    N: lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: DEVNAME=/dev/lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: DEVPATH=/devices/pnp0/00:07/printer/lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: MAJOR=6[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: MINOR=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: SUBSYSTEM=printer[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: TAGS=:udev-configure-printer:[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: UDEV_LOG=3[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    E: USEC_INITIALIZED=8006083[/FONT][/COLOR]

```[COLOR=#000000][FONT=Tahoma]and:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Tahoma]    $ udevadm info -a -n /dev/lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    looking at device '/devices/pnp0/00:07/printer/lp0':[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      KERNEL=="lp0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      SUBSYSTEM=="printer"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      DRIVER==""[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]    looking at parent device '/devices/pnp0/00:07':[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      KERNELS=="00:07"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      SUBSYSTEMS=="pnp"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      DRIVERS=="parport_pc"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      ATTRS{id}=="PNP0400"[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]    looking at parent device '/devices/pnp0':[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      KERNELS=="pnp0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      SUBSYSTEMS==""[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]      DRIVERS==""[/FONT][/COLOR]
```

---

