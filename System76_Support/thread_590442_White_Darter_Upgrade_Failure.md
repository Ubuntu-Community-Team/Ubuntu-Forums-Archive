---
title: "White Darter Upgrade Failure"
date: 2007-10-24
forum: System76 Support
---

### Post by esundstr on 2007-10-24
I decided to upgrade to Gutsy today.  I ran the ubuntu upgrade using the update manager.  Everything went fine till I did the reboot.  Where after showing the ubuntu boot screen for a very short period of time it dropped me to a BusyBox terminal.  I found a post about how some of the various Macs are having similar problems:

[http://ubuntuforums.org/showpost.php?p=3566460&postcount=9](http://ubuntuforums.org/showpost.php?p=3566460&postcount=9)

But so far the solutions given don't work for me.  I'm hoping you guys can help.

Thanks in advance.

---

### Post by riseringseeker on 2007-10-24
> **esundstr said:**
> I decided to upgrade to Gutsy today.  I ran the ubuntu upgrade using the update manager.  Everything went fine till I did the reboot.  Where after showing the ubuntu boot screen for a very short period of time it dropped me to a BusyBox terminal.  I found a post about how some of the various Macs are having similar problems:

[http://ubuntuforums.org/showpost.php?p=3566460&postcount=9](http://ubuntuforums.org/showpost.php?p=3566460&postcount=9)

But so far the solutions given don't work for me.  I'm hoping you guys can help.

Thanks in advance.

I did mine white darter as a clean install, good chance for some housekeeping I figured.

You might try this mentioned by Tom in another thread:

```
sudo apt-get update && sudo apt-get --assume-yes dist-upgrade
```

Make sure you have a good stable (preferably wired) connection.

---

### Post by esundstr on 2007-10-24
Apparently it was some problem with GRUB.  I currently have it getting to gnome where as it wasn't before.  For others info I had to pressed esc during the GRUB sequence and select a different Kernel number.  I'm currently in Gnome, going to get the Sys76 drivers and see what happens.  I'm not sure that the problem is completely fixed but I'm going to see if I can't fix it.

---

### Post by esundstr on 2007-10-24
Ok, it still occurs when I reboot.  Does anyone happen to know what file to edit in order to set the kernel to boot to?

Thanks.

---

### Post by palintheus on 2007-10-25
> **esundstr said:**
> Ok, it still occurs when I reboot.  Does anyone happen to know what file to edit in order to set the kernel to boot to?

Thanks.

You would have to edit "/boot/grub/menu.list" to set which kernel boots by default.

I have never changed grub that much, so I can't help there, I can just suggest to be VERY careful.

---

### Post by riseringseeker on 2007-10-25
> **palintheus said:**
> You would have to edit "/boot/grub/menu.list" to set which kernel boots by default.

I have never changed grub that much, so I can't help there, I can just suggest to be VERY careful.

Another, and perhaps better option is to go to synaptic and search for "startupmanager".  It's a Gui that allows editing of grub.  Why this isn't installed by default I have no idea.

After installation it will show in Administration -> Startup-Manager, just click the tabs and have a ball.

---

