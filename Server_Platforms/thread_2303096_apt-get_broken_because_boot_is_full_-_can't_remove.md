---
title: "apt-get broken because /boot is full - can't remove kernels"
date: 2015-11-16
forum: Server Platforms
---

### Post by Bjoern on 2015-11-16
Hi,

apt-get doesn't work anymore on my server because it can't meet some dependency to a newer kernel. I can not change anything because /boot is full (too many old kernel images).

I've found this documentation: [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

It says to use apt-get autoremove to remove the old kernels, but that doesn't work for me because apt-get tries to fix it's dependency tree before it does anything.

Any other way?

Thanks!

Björn

---

### Post by darkod on 2015-11-16
Yes. Manually deleting the files in /boot, but be VERY CAREFUL what you delete.

Check your currently loaded kernel with:
```
uname -r
```

In general, it is safe to delete all older kernel before the currently loaded (note that the currently loaded might not be the latest, it depends if and when there was a reboot of the machine).

Check the file sizes in /boot and start deleting the biggest files first, related to the oldest kernels (pay attention to the vmlinuz and initrd files for the appropriate kernels, they are the biggest in size):
```
ls -lh /boot
```

Depending on your /boot size, you don't need to delete everything. After you have deleted few, try apt-get again. The last update is probably broken when it ran out of space, so you might need to fix apt-get first before it can work, even after you create free space. The amount of sufficient free space I can't tell exactly, aim for 100-150MB free on /boot partition.

To fix apt-get try something like:
```
sudo apt-get install -f
sudo dpkg-reconfigure -a
```

That should try to fix dependencies and also finish configuring all pending packages... See how it goes...

---

### Post by bab1 on 2015-11-16
> **Bjoern said:**
> Hi,

apt-get doesn't work anymore on my server because it can't meet some dependency to a newer kernel. I can not change anything because /boot is full (too many old kernel images).

I've found this documentation: [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

It says to use apt-get autoremove to remove the old kernels, but that doesn't work for me because apt-get tries to fix it's dependency tree before it does anything.

Any other way?

Thanks!

Björn
As @darkod has said: BE VERY CAREFUL.  If you want to remove the earlier kernels, you can locate them with this command in the terminal  ```
ls -l /boot | grep config
```  This should look similar to this```

ls -l /boot | grep config
-rw-r--r-- 1 root root   165763 Oct 23 07:39 config-[COLOR="#FF0000"]**3.13.0-67-generic**[/COLOR]
-rw-r--r-- 1 root root   165763 Nov  6 11:57 config-3.13.0-68-generic

```

You can remove the older kernel images with this command```

sudo apt-get purge linux-image-[COLOR="#FF0000"]**<image_number-generic>**[/COLOR]
```...where the image number is the one you want to delete.  

This will remove the kernel and update grub.  There is no need to use multiple commands when you use this method.  Remember to check that you do not remove the latest 2 kernels.  The earlier one is a fall back in case the current kernel has a failure.

---

### Post by darkod on 2015-11-16
apt-get purge is the preffered way but not right now. I believe apt-get will not work because /boot is full and the last update process "broke down" because of it. That's why apt-get autoremove doesn't work for the OP too... Right?

---

### Post by bab1 on 2015-11-16
> **darkod said:**
> apt-get purge is the preffered way but not right now. I believe apt-get will not work because /boot is full and the last update process "broke down" because of it. That's why apt-get autoremove doesn't work for the OP too... Right?

Not necessarily so.  It depends on why autormove does not work.  The command I gave just should remove the the image and it's dependencies.  Then it will update the grub file.  It does not go looking for missing dependencies.  I use the apt-get purge command when autoremove fails for me.  The last time I tried autoremove for removing kernel images it failed, but the apt-get purge method worked for me.  This was just last week.

---

### Post by darkod on 2015-11-17
Interesting... In the cases of full /boot I have encountered so far, apt-get was completely out so purge couldn't help me... But I'll remember to try it just in case the next time.

---

