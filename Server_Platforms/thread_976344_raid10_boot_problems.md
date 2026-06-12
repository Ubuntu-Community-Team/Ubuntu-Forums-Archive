---
title: "raid10 boot problems"
date: 2008-11-09
forum: Server Platforms
---

### Post by sminded on 2008-11-09
Short version:
My RAID10 array is not automatically detected at boot. I'm dropped to Busybox. If I then do mdadm --assemble, followed by CTRL-D, everything works fine, and boots fine. Btw, its not degraded.
Whats the catch, what am I missing?

I could easily modify the kernel startup scripts to do an assemble for me and everything would work just fine. But that should not be necessary.

HELP

---

### Post by fjgaude on 2008-11-09
You might try this, if you have a race condition, add the sleep line in:

/usr/share/initramfs-tools/init   # to stop a race condition with md

   157 maybe_break mount
   158 sleep 5
   159 log_begin_msg "Mounting root file system..."

```
sudo /usr/sbin/update-initramfs -uk all
```    # run to rebuild the image

You might have to go to even 10 seconds if you have a slow computer and drives. The line numbers may be different in your setup.

Let us know how you make out.

---

### Post by sminded on 2008-11-09
Nope, that did not work.

Thanks for the tip though.

---

### Post by fjgaude on 2008-11-10
Another tip that has worked for many:

Delete the **/etc/mdadm/mdadm.conf** file, remove **mdadm** using **apt-get**, reboot. Then re-install mdadm and run:

```
sudo mdadm --assemble --scan
```

That will auto re-create your mdadm.conf file, and you should be able to mount the array. I'm sure you already have a line in /etc/fstab to do the mount on bootup.

See how this works.

---

