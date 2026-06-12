---
title: "[SOLVED] Grub"
date: 2008-11-25
forum: Server Platforms
---

### Post by tsucol11 on 2008-11-25
I want to install 8.10 server on a 250 gig external USB drive. Drive would probably be /dev/sdc as I have 2 internal SATA drives on the machine.

I do not want grub on the main HD (sda /hda). Will grub install on the usb drive or does it default to the first HD? I know that I have a choice with the desktop version but uncertain as to the server edition. In my case having grub on the first drive is not an option (divorce issue ;-)  )

 Thank you

Brian

---

### Post by psusi on 2008-11-25
The livecd always installs it to sda.  You should be able to use the alternate cd and choose not to install grub at all during the installation, then go install it on the external drive yourself.  Or just let the livecd do its thing then use your windows cd and the fixmbr command to remove grub from the internal disk after.

---

### Post by tsucol11 on 2008-11-26
Thanks, I did a reinstall onto vmware and noticed that Grub was installed automatically.

I will keep your post.

Brian


> **psusi said:**
> The livecd always installs it to sda.  You should be able to use the alternate cd and choose not to install grub at all during the installation, then go install it on the external drive yourself.  Or just let the livecd do its thing then use your windows cd and the fixmbr command to remove grub from the internal disk after.

---

### Post by ibutho on 2008-11-26
> **psusi said:**
> The livecd always installs it to sda.  You should be able to use the alternate cd and choose not to install grub at all during the installation, then go install it on the external drive yourself.  Or just let the livecd do its thing then use your windows cd and the fixmbr command to remove grub from the internal disk after.

If you click on the advanced tab using the live cd, you get an option on where to install grub.

---

### Post by tsucol11 on 2008-12-03
> **ibutho said:**
> If you click on the advanced tab using the live cd, you get an option on where to install grub.

I'll check it out.

Thank you

Brian

---

