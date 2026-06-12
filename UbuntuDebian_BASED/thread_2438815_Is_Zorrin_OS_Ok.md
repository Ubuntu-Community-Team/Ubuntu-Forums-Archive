---
title: "Is Zorrin OS Ok?"
date: 2020-03-18
forum: Ubuntu/Debian BASED
---

### Post by alvinrr on 2020-03-18
Is Zorrin OS Ok? Can I dual boot with Ubuntu and Zorrin?

---

### Post by HermanAB on 2020-03-18
It looks like an over hyped fork of Ubuntu, so it is probably OK... but why bother?

---

### Post by howefield on 2020-03-18
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Frogs Hair on 2020-03-18
> **alvinrr said:**
> Is Zorrin OS Ok? Can I dual boot with Ubuntu and Zorrin?

Boot a live disk or usb to see if you like it. Zorin has different desktop configuration options and the same software as Ubuntu. Their focus  is people switching from Windows.

---

### Post by yancek on 2020-03-18
It would be easier with an MBR/Legacy install.  If you are doing an EFI install of Zorin alongside an EFI install of Ubuntu, you would need to find out if the EFI directory used for Zorin is also called Ubuntu.  This is the case with a number of Ubuntu derivaties so if that is the case with Zorin, installing it will overwrite the current Ubuntu EFI files.  Zorin should detect Ubuntu and create a menuentry for it.  Should you decide at a later data that you do not want Zorin but want to stick with Ubuntu you will have problems booting if you format the Zorin partition because the required Grub files including menu will also be deleted.  You coul copy the current ubuntu EFI directory to another location as a backup and if you later decide you don't want Zorin, copy the ubuntu EFI directory back to the EFI partition.

---

### Post by stephanie-s on 2020-03-20
I was looking for a replacement distro for Linux Mint 19.3 ( it was too sluggish) so I installed Zorin Core it on my MacMini and tried it for a couple of days.  Had no problems with the installation, everything worked out of the box.  I didn't find anything that made me want to keep it, so I installed Ubuntu over it.  One thing I didn't like was the fact that they wanted $39.00 US for the Ultimate Version.\

---

### Post by alvinrr on 2020-03-21
Thank you for your answers. I will just wait for Focal Fossa.

---

### Post by kurt18947 on 2020-03-22
I haven't used either beyond casual exploration but I think Zorin and Mint with the Cinnamon desktop would be the most familiar to Windows users. Both have a 'start' button of sorts in the lower left corner, have a sort of task bar etc. etc. Remember that to non-technical sorts the desktop/UI IS the computer, they know nothing of the underpinnings.

---

