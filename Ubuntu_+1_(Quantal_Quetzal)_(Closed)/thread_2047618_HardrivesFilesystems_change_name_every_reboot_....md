---
title: "Hardrives/Filesystems change name every reboot ..."
date: 2012-08-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by xeizo on 2012-08-25
This is a joke, every time I reboot all filesystems except / change name. This breaks all symlinks every time. This is bad as I run the system on a mere 64GB SSD I depend on symlinks.

Ie drive_1, drive_2 and drive_3 has become first drive_11, drive_21 and drive_31 and after that drive_12, drive_22 and drive_32 and it keeps on and on and on on every succesive reboot. Very annoying.

Anyone have any idea what particular bug causes this strange behaviour?

It occured right after /run/media/user was moved to /media/user in the filesystem.

edit. 12.10 is very buggy right now, lots of different services crashing, some seems to be because I persist on using an old X and that in turn makes it impossible to file bug reports. And Xorg 1.13 is unusable before the next Nvidia-driver, catch22 right now.

---

### Post by MacUntu on 2012-08-25
Not sure what you are talking about, but you never should rely on /dev/sd** names.

---

### Post by xeizo on 2012-08-25
> **MacUntu said:**
> Not sure what you are talking about, but you never should rely on /dev/sd** names.

It's not the /dev/sd* that changes, it's the automatic mount points in the filesystem. Earlier they resided in /run/media/user(ie /run/media/user/drive_1), now they are in /media/user. These are the exact paths which Thunar uses when manouvering Thunar, or every other filemanager active for that matter. They are necessary to stay the same to have persistent symlinks. Too much work to manually mount every partition and create a new symlink for every new manual mount point every reboot.

When the OS does automatic mounting, why not use it? And when using it, it has to work. I can't have Thunar, or whatever, to invent new relative paths every reboot.

Windows has done this flawlessly since Windows 3.1 ...

---

### Post by Bucky Ball on 2012-08-25
Um, 12.10 is expected to be unstable. It is testing and not released until October (thus Ubuntu +1). It would be most helpful to the developers if you could report this as a bug on Launchpad:

[https://launchpad.net/](https://launchpad.net/)

You may find you are not alone. If you are after something stable please try the current LTS releases, 10.04 LTS (supported until next April) or 12.04 LTS (til April 2017).

---

### Post by coffeecat on 2012-08-25
> **xeizo said:**
> 
edit. 12.10 is very buggy right now,

Well - it's still in the testing phase, not yet released, and several things are problematic, which is expected at this stage of development. It sounds as though you might be using the not-yet released 12.10 on a production system, which is not advisable. 

But to your specific issue. If you are symlinking from one partition to another, relying on automatic mounting via the file manager is inadvisable, even with a released version of any Linux distro. You'd be much better off configuring /etc/fstab to do the mounting for you to the mountpoints you specify. You could be sure they don't change then.

---

### Post by mc4man on 2012-08-25
This doesn't seem to be xserver related, probably udisks2 or gvfs?
It's now using /media/<username> & for most mounts when unmounted the file is left behind so next time the mount name is appended

(doesn't affect certain usb drives,
screen shows 2 internel, 1 unaffected usb, (older), 1 affected usb where the volume label is Storage

Then unaffected usb would be ones that are "Direct-Access"

Edit: The apparent cause of this behavior is the new  gvfs*  1.13.7-0ubuntu1 packages

---

### Post by xeizo on 2012-08-25
I'm aware this is unstable, but the point of unstable is making it stable. Right?

Last two posts where very helpful though, I'll consider making an unbreakable /etc/fstab,  it may be in the Linux-universe that automatic mounting isn't intented to work. But it works in Windows and has done so for two decades so I don't think it's over the top to wish for a similar feature working in Linux as well.

Btw USB automount doesn't work at all right now.

edit. Ah! The answer; buggy gvfs! Thank you!  :)

---

### Post by mc4man on 2012-08-25
While I think you can still file some bugs or manually - took a look, didn't see any current on this so
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1041576](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1041576)

---

### Post by ronacc on 2012-08-25
they must have stolen the drive detection from ubiquity ! I have been bugging that about ubiquity for years , The live cd may not call the same drive the same thing on sucessive boots . I label all my partitions so I can sort things out when they get scrambled .

---

### Post by Bucky Ball on 2012-08-25
Is OP running from LiveCD or hard drive install?

---

### Post by mc4man on 2012-08-25
This could also be related to the  new udisks2 build

udisks2 updated on Weds to go back to /media/<username>, gvfs updated on fri. to a new upstream release, if using the old udisks2 with the new gvfs then all works as expected as does the old gvfs with the new udisks2

---

### Post by xeizo on 2012-08-26
I created a custom /etc/fstab, we'll see if it holds for now, but of course this stuff should work without even having to know what a /etc/fstab is.

I saw in one the threads that even more serious breakage is to be expected the week to come :popcorn:

---

### Post by kyleabaker on 2012-08-26
I've noticed this bug lately on my own system. It appears to occur for me when I have a drive mounted (the /media/<username>/<drivename> directory is created) and my system crashes while this drive is mounted or if I restart without properly unmounting first.

I've just been manually removing those directories to keep things clean for now.

---

### Post by kyleabaker on 2012-08-26
Also, this is not unique to Xubuntu as is suggested by the thread title prefix.

---

### Post by jerrylamos on 2012-08-26
> **MacUntu said:**
> Not sure what you are talking about, but you never should rely on /dev/sd** names.Can't rely on UUID's either.  I've had many a problem after install with Grub2 looking frantically for a UUID on one hard drive never occurs to Grub2 to look on the other where that UUID is actually installed.  Solution was to boot 10.04 and do a update-grub grub-install.

---

### Post by Bucky Ball on 2012-08-26
> **kyleabaker said:**
> I've noticed this bug lately on my own system. It appears to occur for me when I have a drive mounted (the /media/<username>/<drivename> directory is created) and my system crashes while this drive is mounted or if I restart without properly unmounting first.

I've just been manually removing those directories to keep things clean for now.

Presuming you are using the not yet released and still testing 12.10? If not, you're in the wrong place. Please post a new thread. Cheers. ;)

---

### Post by kyleabaker on 2012-08-27
> **Bucky Ball said:**
> Presuming you are using the not yet released and still testing 12.10? If not, you're in the wrong place. Please post a new thread. Cheers. ;)

I'm using Quantal. ;)

---

### Post by mc4man on 2012-08-27
Well at least here it's now back to normal, all mounts in /media/<username> are removed when volume is unmounted or ejected. No idea why they weren't before & now are...

---

### Post by xeizo on 2012-08-27
> **mc4man said:**
> Well at least here it's now back to normal, all mounts in /media/<username> are removed when volume is unmounted or ejected. No idea why they weren't before & now are...

Affirmative, it's back to normal after todays updates. I had to remove my custom /etc/fstab, otherwise the new gfvs got confused by it and presented doubled mounts with different names. After unediting /etc/fstab AND /etc/mtab all is ok again!

---

### Post by Bucky Ball on 2012-08-27
If solved, please mark as 'Solved' to help others. ;)

---

### Post by xeizo on 2012-08-28
It WAS solved, but after todays updates it's back to the same, I had to remake my custom /etc/fstab to have my persistent links otherwise drives in /media/<username> change name every new reboot AGAIN!

---

### Post by mc4man on 2012-08-28
> **xeizo said:**
> It WAS solved, but after todays updates it's back to the same, I had to remake my custom /etc/fstab to have my persistent links otherwise drives in /media/<username> change name every new reboot AGAIN!

See almost the same here. Previously when 'broken' if I did a mount, unmount the mount dir. remained.
Now with the gvfs of today mount/unmount works as expected but a restart with volumes mounted leaves the mount dir. behind.

Is that what you see? (when unmounting the current mount point is removed but a restart/shutdown with mounted volume(s) either doesn't remove the mount dir(s) or doesn't actually unmount the volume(s)?

---

### Post by xeizo on 2012-08-28
Exactly, that is what happens, while manual unmounting probably would work it is precisely that: extra work! And this is not what computers are for ;)
I expect this to start working automagically sooner or later.

Meanwhile, my static /etc/fstab works alright. But I had to do the extra work to make it ....

---

### Post by mc4man on 2012-08-28
Yeah you figure it'll be squared up at some point, not going to bother with a new bug because it keeps changing

when it was at /run/media/ I think it didn't matter if the mount points weren't cleaned up when doing a restart/shutdown. It seemed like run/media was like a tmpfs & was removed altogether on a restart/shutdown

See something else when using SDC. When the usb is remounted it goes to /media (user owned) and also not cleaned up, then root owned (haven't rechecked this today

Personally liked it better when mounts went to /media, not /media/<username or /run/media/<username

---

### Post by kyleabaker on 2012-08-28
> **mc4man said:**
> Personally liked it better when mounts went to /media, not /media/<username or /run/media/<username

Agreed.

---

