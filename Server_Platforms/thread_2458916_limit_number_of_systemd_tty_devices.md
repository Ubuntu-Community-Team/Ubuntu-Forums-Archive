---
title: "limit number of systemd tty devices"
date: 2021-03-06
forum: Server Platforms
---

### Post by flblblbl on 2021-03-06
I have installed ubuntu server 20.04 (64 bit) on my raspberry pi and [FONT=courier new]systemctl list-units[/FONT] lists 256 different tty devices [FONT=courier new](sys-devices-virtual-tty-ttya0.device -  sys-devices-virtual-tty-ttyzf.device[/FONT]).

I would like to limit that number, just to get a better overview of the systemd units (256 out of 364 loaded units are tty devices...) and maybe to slightly decrease boot time.

What I tried and did not work:
[LIST]
[*]Set [FONT=courier new]NAutoVTs=6[FONT=arial] in [FONT=courier new]/etc/systemd/logind.conf[FONT=arial]
[/FONT][/FONT][/FONT][/FONT]
[*][FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]Change [FONT=courier new]CONFIG_LEGACY_PTY_COUNT=256[FONT=arial] to [FONT=courier new]CONFIG_LEGACY_PTY_COUNT=6[FONT=arial] and run [FONT=courier new]update-initramfs[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]
[/LIST]
[FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]
[/FONT][/FONT][/FONT][/FONT]

---

