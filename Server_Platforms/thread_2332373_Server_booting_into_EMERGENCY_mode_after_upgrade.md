---
title: "Server booting into EMERGENCY mode after upgrade"
date: 2016-07-31
forum: Server Platforms
---

### Post by gtozzi on 2016-07-31
Hi there,

so, I've finally found some time to upgrade my server from 15.10 to 16.04 and here come the troubles.

When rebooting, the server starts its boot process, then goes into "emergency mode" apparently for no reason. Is there a way to see what's happened?

Thank you

---

### Post by Graham_Willis on 2016-07-31
Doesn't it display any suggestions? From what I've found on the Internet, it seems that it should display something like that:

```
after logging in type journalctl -xb
```

Have you checked what it shows? If it's not possible to issue this command or it doesn't display any output, mount from live CD and check logs manually. I think that /var/log/kern.log is the first thing worth checking (I don't really know if emergency comes from GRUB or from kernel, but my quick research on the web seems to suggest that from kernel). It seems that the fairly common reasons for this behaviour can be if it isn't possible to mount a device or if filesystem's broken, worth running fsck (keep remember that if you want to repair filesystem it should be unmounted if you don't want to do any damage).

---

### Post by gtozzi on 2016-07-31
Thank you!

There is a lot of stuff in the logs, but the errors are apprarently "Timed out waiting for device <uuid link here>".

It looks like the system is waiting for devices that are not present at boot time, and failing to boot because it can't find it&#8230; *sigh* I miss the good old sysV init.

---

### Post by Bashing-om on 2016-07-31
gtozzi; Hello;

> **gtozzi said:**
> Thank you!

There is a lot of stuff in the logs, but the errors are apprarently "Timed out waiting for device <uuid link here>".

It looks like the system is waiting for devices that are not present at boot time, and failing to boot because it can't find it… *sigh* I miss the good old sysV init.


In the event that the above is true .. one can have a look at the /etc/fstab file and know what the system expects and mounts at boot time.
```

cat /etc/fstab

```
and compare the UUIDs in the file to :
```

sudo blkid

```

Yeah, the times they are a-chang'n .. every one wants faster bootup .. and activating services in parallel is one solution .. welcome to systemd.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by gtozzi on 2016-07-31
Thank you for the hint!

Apparently *"noauto"* is no longer enough: I've solved by also adding *"nofail"* to the relevant devices in both *fstab* and *crypttab*.

P.S. *almost* everyone wants a faster bootup :) I (re)boot this server once a month and it's not a big deal to see how much complexity has been added just to save a few seconds. But yep, I understand the times are changing ;)

---

### Post by Bashing-om on 2016-07-31
gtozzi; Hey hey; wadda ya know.

Glad ya got it fingered out ; and provided your solution.

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

