---
title: "Preseeds on USB server-install"
date: 2009-03-21
forum: Server Platforms
---

### Post by lennartu on 2009-03-21
I am making an automated installation of Ubuntu 8.04 Server from USB, this way: [https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

Everything seems OK. Manual installation from the USB-stick is working OK.
But, I am not able to automate installation using preseed-files...

As documented on page: [https://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html](https://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html)
> - if you're installing from USB media (put the preconfiguration file in the
  toplevel directory of the USB stick):
  preseed/file=/hd-media/preseed.cfg


Has tried to refer to the files as /hd-media/preseed.cfg in syslinux.cfg and put the preseed.cfg in the toplevel directory of the USB-stick. Has also tried to put the preseed.cfg into the Ubuntu .iso file (located on the USB-stick).

Has anyone tried this and got it to work??
And do you see what I do wrong?

---

