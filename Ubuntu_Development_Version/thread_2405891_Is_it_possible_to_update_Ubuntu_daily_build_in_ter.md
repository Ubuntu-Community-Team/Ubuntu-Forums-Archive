---
title: "Is it possible to update Ubuntu daily build in terminal, also is their a change log?"
date: 2018-11-12
forum: Ubuntu Development Version
---

### Post by sonyboyj on 2018-11-12
If i download and install a 19.04 daily build can i update it to a newer daily build via the terminal every few days? Also does Canonical have a change log for daily builds?

---

### Post by oldfred on 2018-11-12
This is still Cosmic, but I expect as some point it will be disco, so you can use same zsync each time.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If you go here you can see the most recent:
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

Then you can zsync your current ISO with just the changes, as of today it is 20181112, but you have to check each time until it is daily-live:
My first zsync is my last copy of Cosmic ISO, renamed.
zsync [http://cdimage.ubuntu.com/daily-live/20181112/disco-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/20181112/disco-desktop-amd64.iso.zsync)

I directly boot ISO from grub. But I always forget to update grub, so now use a configfile in my /ISO folder. I have one on each drive, so I can install to the other drive. I do copy from download location into /ISO partition on each drive, so path is /ISO, not /home/fred/ISO.
```

menuentry 'Live ISOs on SSD' {
configfile (hd0,3)/ISO/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,3)/ISO/livecdimage.cfg
} 

```

```

# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd0,3)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 19.04 Disco amd64" {
    set isofile="/ISO/disco-desktop-amd64.iso"
    loopback loop (hd0,3)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram
    initrd (loop)/casper/initrd
}


```

---

### Post by coffeecat on 2018-11-13
*Thread moved to **Ubuntu Development Version**.*

---

### Post by jbicha on 2018-11-13
For changelogs, see [https://lists.ubuntu.com/mailman/listinfo/disco-changes](https://lists.ubuntu.com/mailman/listinfo/disco-changes)

But many Ubuntu changes come directly from Debian.Years ago, those changes were published to that list too, but that was stopped to try to make that list more focused.

So you may also want to look at [https://lists.debian.org/debian-devel-changes/](https://lists.debian.org/debian-devel-changes/)

The tricky part is that not every Debian change makes it into Ubuntu, at least not right away.

Some packages get delayed in -proposed for a while because of [what -proposed is]("https://wiki.ubuntu.com/ProposedMigration") (during the development cycle) so there are changes you will see in the lists that won't show up yet in current Ubuntu.

---

### Post by ping-wu on 2018-11-22
> **oldfred said:**
> I directly boot ISO from grub. But I always forget to update grub, so now use a configfile in my /ISO folder. I have one on each drive, so I can install to the other drive. I do copy from download location into /ISO partition on each drive, so path is /ISO, not /home/fred/ISO.

Can you do persistence when boot from iso?

---

### Post by oldfred on 2018-11-22
No, booting ISO directly is just the live installer. But I have all the folders in the system. But most you cannot write into as live user is 999 where folders all are user 1000.

---

