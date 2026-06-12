---
title: "Encrypt Mounted Hard Drive on Headless Server"
date: 2014-06-12
forum: Server Platforms
---

### Post by damo12 on 2014-06-12
Hi,

I support a small business which runs a small headless file server which is controlled through Webmin and SSH.  The server is currently running Ubuntu Server 12.04 but will soon migrate to 14.04.

In the server an internal hard drive is mounted as the "server" drive.  Each day this is backed up to another internal hard drive and also to a mounted external USB drive using RSync scripts.

Is is possible to encrypt the internal and external drives so that they could not be read in another computer without the encryption keys in a similar way to FreeNAS ([http://www.freenas.org/about/features.html#encryption]("http://www.freenas.org/about/features.html#encryption")).

I have seen some suggestions however they all seem to require Gnome or some other GUI installed which is something I want to avoid at all costs.

Is there any way to encrypt these drives without using a GUI?

Many thanks

---

### Post by thufirhawat2 on 2014-06-13
[http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/](http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/)

I have a 14.04 server at the house, and this is what I used to encrypt my external offsite backups. I pretty much do everything manually via SSH, but pretty much the same gig. I put in a USB hard drive, decrypt it with the [FONT=Courier New]cryptsetup luksOpen /dev/xvdc backup2[/FONT] command (replacing xvdc with sdc1, sdb1, etc. depending on where your external drive is allocated when you plug it in) and then I mount the partition with the [FONT=Courier New]mount /dev/mapper/backup2 /backup2[/FONT] command as shown in the tutorial replacing /backup2 with whatever directory you want to mount it in, and then I run my rsync scripts to perform the backups. Afterwards, I use the commands given in the tutorial to lock and unmount the USB drive. I do not encrypt any of the internal drives on the server, but for external backups, this method works for me.

---

### Post by damo12 on 2014-06-13
Hi thufirhawat2,

That is exactly what I was looking for.

Thanks so much for your help

---

