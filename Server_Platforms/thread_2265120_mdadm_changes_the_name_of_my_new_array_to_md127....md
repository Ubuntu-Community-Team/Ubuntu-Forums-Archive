---
title: "mdadm changes the name of my new array to md127..."
date: 2015-02-12
forum: Server Platforms
---

### Post by ooboontwo on 2015-02-12
[COLOR=#ff0000]**THIS THREAD HAS BEEN SOLVED! SEE EDIT AT THE BOTTOM OF THIS ORIGINAL POST!**[/COLOR]

Hello everyone,

This has been bugging me for some time now. Every time I create a new array using mdadm the name is changed from what I originally specified.

Here's what I'm doing.

Created the array from two new disks:

```
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
```

Made the filesystem:

```
mkfs.ext3 /dev/md0
```

Updated mdadm.conf:

```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Added the array to /etc/fstab:

```
/dev/md0 /mnt/mymountpoint ext3 defaults 0 1
```

Everything looks great... until I reboot the machine.

Upon reboot I receive the message that the filesystem on /dev/md0 is either missing or busy. I skip this... and then discover that my new array is no longer called /dev/md0.

Now, it is /dev/md127.

What am I doing wrong? This happens every time I create an array and on multiple different systems. I'm assuming that I'm just being an idiot here but your help is greatly appreciated as I would prefer for my arrays to retain the name I specify when creating them.

Thank you!

[COLOR=#ff0000][B]SOLVED:

For anyone that may Google this thread:

Yes, running 'sudo update-initramfs -u' fixed the problem for me!

Thanks for the help, everyone![/B][/COLOR]

---

### Post by darkod on 2015-02-12
I have no idea why it happens, but it might be related to using the --detail --scan to make the entry in mdadm.conf. Now that I am thinking about it, something similar happened to me recently but only for a new array after using --detail --scan to make the entry. Two arrays that were created during OS install kept their names.

Searching on google, I solved it like this: Open mdadm.conf and in the ARRAY definition for md0 keep only the /dev/md0 and the UUID. Nothing else. Delete the device name (machine name) if it's there. Save and close the file and reboot.

That solved it for me. One blog I found says the /dev/mdX and the UUID are enough in the ARRAY definition. mdadm uses the uuid to assemble the array anyway so it makes sense.

---

### Post by rubylaser on 2015-02-13
Darko's directions are correct.  After you update your mdadm.conf file, you should also update your initramfs like this.
```

sudo update-initramfs -u

```

---

### Post by darkod on 2015-02-13
Yes, I forgot the initramfs update. Thanks rubylaser.

---

### Post by n00b123 on 2015-02-15
Using the UUID in the fstab is always the best practice

---

### Post by ooboontwo on 2015-02-19
Thank you for the replies, everyone. I haven't had a chance to test it out but I will as soon as I can! Hoping this solves the problem. Thanks again!

---

### Post by ooboontwo on 2015-03-27
For anyone that may Google this thread:

Yes, running 'sudo update-initramfs -u' fixed the problem for me!

Thanks for the help, everyone!

---

