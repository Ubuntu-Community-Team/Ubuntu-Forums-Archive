---
title: "mount a USB drive in rc.local with /sbin/mount and UUID instead of fstab?"
date: 2010-02-06
forum: Server Platforms
---

### Post by prupert on 2010-02-06
Hi

I run a headless Ubuntu 8.04 server, which acts as a web, email and file server. I am sticking with 8.04 as it is a LTS release and will upgrade to the next LTS when it is released.

I have two external USB drives, that I need to mount at boot. I have been using /etc/fstab up until now, with the following entries:
```

# USB old backup now video drive
UUID=a853c219-6e7f-496c-91f5-9a70bd12c775 /media/video ext3 defaults 0 2
# USB old video now backup drive
UUID=1a07009e-6318-49c8-8bcd-1372af9e4b6b /media/disk ext3 defaults 0 2
```

However, as I gather from doing searches is quite common, occasionally I get an error during boot (causing the system to drop to a recovery shell) because the USB drives take time to wake up and the system hasn't found them by the time it reads /etc/fstab.

From doing searches, it seems there is nothing you can do to fstab to fix this, so you need to mount them using an rc.local script instead, using:

```
/sbin/mount /dev/sdxx /somewhere
```

The problem is, as I have two USB drives, their /dev/sdxx location changes between boots. I thus want to use UUID codes as I do in fstab, however I haven't found anything about this.

Does anyone know how I can use the mount command and UUID to mount a drive in rc.local and what options I have to use the mount the drive with the same options that I am using in my fstab entry? Obvisouly, I can't refer back to fstab using the mount command, because then I will still get the boot error issue if they are listed in fstab. And there is no space internally for the USB drives as there is already two internal drives.

Any answers gratefully received.

---

### Post by BkkBonanza on 2010-02-07
There are a few useful things on the "man mount" page that can help you out.

1. to prevent error messages during boot you can use "quiet" as an option in the fstab file, eg. default,quiet for the options part will cause no error messages during boot. BUT this will still result in the partition not being mounted if it's not recognized during boot so you could just run "mount -a" in rc.local which will fix up any missing mounts defined in fstab.

2. you can use the -U <uuid> option with mount eg.

mount -U my-big-uuid-value  /media/video

---

### Post by prupert on 2010-02-07
Wow, how did I miss the -U option.

Cool, so I guess I can add the quiet option to default, then leave those entries in fstab, then put a mount script in rc.local for the drives. They'll use the options from fstab and if they are already mounted, I guess nothing will happen and if they aren't mounted they will mount.

Cheers for the info.

---

### Post by prupert on 2010-02-07
Hmm, actually is seems that the quiet option doesn't work with ext3 file systems. According to the man page for mount, it only works for fat and hfs systems. After a little bit more reading, it turns out that I should be using the errors=continue option and then have a sudo mount -a command in rc.local.

This way, any mount errors on those two USB drives are ignored and the mount -a command should mount them once the system has booted.

Cheers for your input, I didn't realise fstab was simply a file that mount read during boot, so I didn't know what man page to look at. 

Man man is cool ;)

Rgds

I was wondering if this info (using the errors=continue option in fstab and mount -a in rc.local) would be worth adding to the Ubuntu wiki, since it might help a lot of people out, since the current page for fstab says you should use gnome-utils for USB drives, which is useless if you run a headless server with no desktop....

Can I just edit the wiki or do you need to get approval first? Any one know?

---

