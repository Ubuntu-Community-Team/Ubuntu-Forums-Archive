---
title: "Can't boot with 3.16.0-24, hangs at resume: libgcrypt version: 1.5.4"
date: 2014-11-08
forum: System76 Support
---

### Post by moschops on 2014-11-08
I can no longer seem to boot with the latest kernel 3.16.0-24, even in recovery mode.  According to the on-screen output it seems to hang at

```
resume: libgcrypt version: 1.5.4
```

If I select the previous kernel 3.16.0-23 my system boots fine.  I don't seem to have a dmesg log from when the system fails to boot - do I have a bad resume image?   

I didn't notice this right after the latest update because I don't reboot from cold very often.  Just suspend and resume all the time.  My system is fully updated and upgraded on 14.10.

---

### Post by moschops on 2014-11-12
For the record... after much Googling I found a clue here:

[https://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/]("https://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/")

After which I tried

```
# update-initramfs -c -k 3.16.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-24-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     ddee2014-313d-4b1f-a20d-cdad2504bc13
                     515f69a2-fa38-4cef-a153-984de2532574
```

Which although it looks like it might be problematic actually worked.  I can now boot into 3.16.0-24 kernel again.

After searching on the cryptsetup warning I see this post that suggests it is caused by a difference opinion about the swap device in /etc/uswsusp.conf and /etc/initramfs-tools/conf.d/resume

The weird thing is a) I don't have a swap device configured and b) neither of the device ids exist in /dev/disk/by-uuid

After the update and reboot I no longer see any mention of resume: libgcrypt in my boot.log

---

