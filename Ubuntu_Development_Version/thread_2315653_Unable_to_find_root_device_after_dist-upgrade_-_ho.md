---
title: "Unable to find root device after dist-upgrade - how to repair?"
date: 2016-03-01
forum: Ubuntu Development Version
---

### Post by victorhooi on 2016-03-01
Hi,

So I just ran an aptitude dist-upgrade on a Linux box (which was on 16.04) - on rebooting afterwards, it doesn't boot and dumps me at a shell

Root volume is on BTRFS.

```

Begin: Running /scripts/local-block ... done.
done.
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls/dev)
ALERT! UUID=487dd7e20eda8-4476-b3a1-6fa737ac999 does not exist. Dropping to a shell!

BusyBox v1.22.a (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) $[    65.454193] random: nonblocking pool is initialized
$$$$

```

```

cat /proc/cmdline
BOOT_IMAGE=/@/boot/vmlinuz-4.4.0-8-generic root=UUID=487dd7e2-eda8-4476-b3a1-6fa73c7ac999 ro rootflags=subvoll=@

```


[IMG]http://i.imgur.com/UsBJxA0.png[/IMG]

What should I try next?

---

### Post by kansasnoob on 2016-03-01
I haven't messed with btrfs in over a year because I found it too unstable, but when I last messed with it I found that /boot needed to be on a ext3 or ext4 partition or else each time there was a kernel upgrade I ended up with a busybox boot error. Probably best to ask here:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

If you click on Report Post in the lower left hand corner of your OP and ask one of the mods will move it there for you.

---

### Post by QIII on 2016-03-01
Moved to Ubuntu Development Version

---

### Post by grahammechanical on 2016-03-01
Did you by any chance install apt-btrfs-snapshot?

If you did then, at the Grub menu we can select Advance options for Ubuntu and then load a recovery mode kernel and at the recovery menu first select Network to set up an internet connection and to mount the files system as read/write and not just read. Then when we are back at the recovery menu we should see an apt-snapshots - revert to an old snapshot and reboot option.

With apt-btrfs-snapshot installed a snapshot is taken whenever we update the system. Then with recovery menu apt-snapshots option we can revert back to where the system was before the update happened.

Regards.

---

### Post by victorhooi on 2016-03-02
Hmm, I don't recall to be honest - is it installed out of the box?

I did notice the Grub menu delay seems to be set **very** short - is there any way to freeze it, or get to it, if it's set very short?

I'll boot up a recovery menu, and try your suggestion, to see if we have any snapshots, and let you know. Thanks!

---

### Post by zika on 2016-03-02
Left Shift button...

---

### Post by victorhooi on 2016-03-05
> **zika said:**
> Left Shift button...

Thanks everybody!

Turns out it was the kernel upgrade - I used the Advanced menu, and picked the previous kernel version and the machine boots again.

I'll wait a bit, then run a update/dist-upgrade - and hopefully the new kernel version should address the issue. Failing that, guess I'll file a bug report.

Good to figure out the issue =).

---

