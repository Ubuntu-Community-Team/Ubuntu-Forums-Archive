---
title: "Running Ubuntu Web Remix in a VM"
date: 2021-11-14
forum: Ubuntu/Debian BASED
---

### Post by hornetster on 2021-11-14
Trying to run Ubuntu Web Remix in VirtualBox, and booting from the ISO to install.
Brings up the install bootscreen, and then drops me back to an **(initramfs)** prompt.
Anyone?

---

### Post by guiverc on 2021-11-15
I don't know what release you're asking about, and don't even know what installer they use, nor what build process was used to make the ISO, so I can't offer much sorry.

The obvious check I'd perform would be validating the ISO as being valid; did you?   The following applies to all Ubuntu releases (including *flavors*), but sorry I don't know if it applies to your remix.  I'd check the web site where you downloaded it.

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

If a boot failed for me; I'd verify the ISO firstly, then the write to installation media (*which doesn't generally apply for virtualbox installs but I've used USB media to boot VMs myself so it still may apply*).

I do know most support for Ubuntu remixes is done on Telegram; in fact it's mentioned at [https://discourse.ubuntu.com/t/ubuntu-web-remix/19394](https://discourse.ubuntu.com/t/ubuntu-web-remix/19394)

---

### Post by hornetster on 2021-11-16
Yes, verified the download prior to posting, then downloaded again, just to make sure!!
After subsequent testing, have found that a 'workaround(?)', is to enable uefi in the vm machine, and can get it installed...
Thanks.

---

### Post by TheFu on 2021-11-16
Is Ubuntu Web Remix an official ubuntu?
If not, check about requirements from the creator.  Official Ubuntu ISOs support legacy AND UEFI booting.

Also, if this thread is solved, please use the "Thread Tools" button near the top to mark it that way to save community members time.

---

