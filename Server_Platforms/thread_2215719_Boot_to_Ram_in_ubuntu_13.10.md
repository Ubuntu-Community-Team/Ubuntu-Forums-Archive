---
title: "Boot to Ram in ubuntu 13.10"
date: 2014-04-08
forum: Server Platforms
---

### Post by PyrexKidd on 2014-04-08
Hello,

I have a couple of servers that I would like to run without disks (well, I've come into some hardware, and would like to leverage the copute hardware but it came without disks... I have a Ceph cluster that I plan on writing persistent data to (it would be awesome to just present raw rbd2 devices, but now we're dreaming... heh libvirt for system filesystems...), but I've not found a way to boot from the raw rbd...  I'm not opposed to netbooting, but again, I don't want to write persistent data to the OS image, package installation/etc should be written to the image before booting or installed "in RAM").  

Essentially, I would like to boot from a USB drive, pull the USB drive, then perform any configuration via chef.

according to [the wiki]("https://wiki.ubuntu.com/BootToRAM") the livecd has a "toram" option, and this [forum post]("http://ubuntuforums.org/showthread.php?t=1583206") says "just press f6", but that only gives you the menu to pick "expert mode", "noacpi", etc. exiting to the text installer with "escape" does not accept the "toram" option (e.g. `install toram` just loads the standard install program)

If you select, expert mode, there is an option to install a "live" environment (which seems like what I want), but that option ends up kernel panicing when I try to boot from it.  It seems that the only difference is the grub option:

```

    # Non live install
    linux   /boot/vmlinuz-3.11.0-12-generic root=UUID=7b436b45-f1fd-441c-8742-405daec0aea4 ro

    # Live install
    linux   /boot/vmlinuz-3.11.0-12-generic root=UUID=1f83d930-804c-4c58-81e4-d6c4f225af8c ro boot=live plainroot

```

I was able to install to my thumb drive in expert mode not selecting the live option.  It boots fine, but when I add the "boot=live" option the server kernel panics.

Eventually I think I want to boot from a network location (e.g. http(s) server) but I'm trying not to run an NFS server so it would have to be a "readonly" and "boot to ram" solution.

I welcome any open discussion on the "how to run an ephemeral ubuntu instance", but I'm hoping someone can help with a solution to the specific "how do I boot from a usbstick that I can then remove?"

Thanks!

---

