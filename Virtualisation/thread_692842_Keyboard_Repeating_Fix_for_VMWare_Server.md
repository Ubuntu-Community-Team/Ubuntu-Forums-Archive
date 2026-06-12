---
title: "Keyboard Repeating Fix for VMWare Server"
date: 2008-02-10
forum: Virtualisation
---

### Post by techstop on 2008-02-10
I recently found that my virtual machines in VMWare Server had a crazy keyboard repeat rate. It was very frustrating as it kept making wrong commands and passwords etc. I found the answer after a lot of searching. Hope this helps someone.  Credit at bottom of post...

1. In your virtual machine, edit /boot/grub/menu.lst

```
sudo gedit /boot/grub/menu.lst
```

2. Find the section relating to your default boot, eg.

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=44b331d8-c84a-463d-aa60-04b6b0efca20 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

3. At the end of the kernel line, add "acpi=off". Save your changes.

4. Reboot and marvel at the lack of crazy keyboard repeating.

Credit: [http://people.vnoss.org/~hxizan/?p=15](http://people.vnoss.org/~hxizan/?p=15)

Cheers! :)

---

### Post by danielriegel on 2008-07-18
I just wanted to thank you for posting this message.  I recently encountered that problem in my VMWare Ubuntu installation, and this fixed it right up, saving me a potentially unlimited amount of time.  I wish more people did things like this.

Dan

---

### Post by win2456 on 2010-06-12
This not only works for VMWare but also other keyboard repeating issues.  Here is the problem I was encountering:

Upgrading to Lucid from Karmic and login screen would seem unresponsive.  Could not switch to other consoles either (CTRL+ALT+F1..etc).  Reboot, immediately try console one but as soon as GDM would load I would visually see the last character pressed on the keyboard repeat indefinitely.

Being lazy, and not trying to fix the issue, I re-installed fresh.  Same exact issue after install.  Used the alternate CD to boot, go into recovery mode and jumped into shell.  Edited /etc/default/grub (since I'm using grub2 now).  Found the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and added acpi=off.  End result:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

Problem solved!  Also, you can do the same thing if you have grub by adding acpi=off to your default menu.lst (found in /boot/grub/menu.lst)

Enjoy and thanks to the poster for this awesome solution that worked right off the bat!

---

