---
title: "Unable to connect to Upstart"
date: 2018-01-11
forum: Server Platforms
---

### Post by raceface2nd on 2018-01-11
[LEFT][COLOR=#222222][FONT=Verdana]I have 3 image files that should be mounted to /dev/loop2 /dev/loop3 and /dev/loop4. I need to mount them after a specific mountpoint in fstab is mounted. To have them ready for ZFS they need to be mounted directly after the other mountpoint.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]So I created a upstart script, which seems not to be run[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
description     "Setup loop devices after filesystems are mounted"[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]start on mounted MOUNTPOINT=/data[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]task[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]exec losetup /dev/loop2 /data/lxd/device01.img[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]exec losetup /dev/loop3 /data/lxd/device02.img[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]exec losetup /dev/loop4 /data/lxd/device03.img[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
```When I try to run this script manually with service losetup start I get[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
Failed to start losetup.service: Unit losetup.service not found.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
```When I try to update the upstart config with initctl reload-configuration I get the following error[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]```
Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Is this a problem with upstart itself?[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Andy[/FONT][/COLOR][/LEFT]

---

### Post by Max303 on 2018-01-11
Why not use systemd.mount "Before" and "After" dependencies to define the mount order?

See systemd.mount man page and [https://copyninja.info/blog/systemd_automount_entry.html](https://copyninja.info/blog/systemd_automount_entry.html)

---

### Post by raceface2nd on 2018-01-11
Thank you for the hint but I could not get it working with systemd.mount. I built a workaround and got it running now.

Andy

---

