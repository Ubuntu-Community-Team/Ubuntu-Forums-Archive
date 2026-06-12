---
title: "Upgrade to 13.04 on Lemur gone bad"
date: 2013-05-07
forum: System76 Support
---

### Post by oakhilltop on 2013-05-07
During boot I see
error file not found
error file not found
error file not found
press any key to continue

I login to unity desktop and the login screen stays on my screen. The system hangs occasionally also.

How do I re-enable the cinnamon repositories that were disabled during the the upgrade? I go to the software updater and the Other Software tabs, check the cinnamon repositories which say they are disabled, but don't see how to enable them.

Why O why do I upgrade a system that is working fine for me?  :-(

---

### Post by oakhilltop on 2013-05-07
I'm not sure what I did. I disabled the old cinnamon repositories, because I read that cinnamon is available in the ubuntu repos now. But I didn't update anything and somehow unity is back to normal. That's a relief.

I still get the can't find file messages at boot though.

---

### Post by isantop on 2013-05-08
That seems to be a common issue with upgrades. So far, it doesn't look like it represents an actual problem, so I would keep an eye on it, and, assuming you don't notice any problems, you can safely ignore those messages.

---

### Post by oakhilltop on 2013-05-08
> **isantop said:**
> That seems to be a common issue with upgrades. So far, it doesn't look like it represents an actual problem, so I would keep an eye on it, and, assuming you don't notice any problems, you can safely ignore those messages.


But I still have to "press any key" every time I boot. I quickly looked in dmesg but didn't see anything. Any idea how I can get back to booting up without pressing a key?

And thanks for the help.

---

### Post by oakhilltop on 2013-05-08
Tried sudo update-grub (output below), but I still get the boot error

Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by oakhilltop on 2013-05-08
Is it safe to remove the 3.5.0-28 kernel?

steve@chloe:~$ apt-cache policy linux-image-3.5.0-28-generic
linux-image-3.5.0-28-generic:
  Installed: 3.5.0-28.48
  Candidate: 3.5.0-28.48
  Version table:
 *** 3.5.0-28.48 0
        100 /var/lib/dpkg/status

---

### Post by isantop on 2013-05-09
If you're running 13.04, then yes, it is safe to remove the older kernel.

---

### Post by oakhilltop on 2013-05-09
> **isantop said:**
> If you're running 13.04, then yes, it is safe to remove the older kernel.

Thanks,

I removed it, hoping it would trigger a reconfiguration of the boot process. It did run grub's config, but I still get the error: file not found at boot and have to press a key.

I wish developers would learn to put
error: file name_of_file not found
in the message to give us a hint of what's going wrong.

---

### Post by isantop on 2013-05-10
Short of doing a reinstall, I don't know what other steps we can take to correct the problem. Unless you can live with the error, I woud reinstall. There is a slight chance that it may go away in time (i.e. with updates).

---

