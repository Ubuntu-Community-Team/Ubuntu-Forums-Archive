---
title: "Ubuntu server won't boot after updating."
date: 2011-06-29
forum: Server Platforms
---

### Post by jackbrennan2008 on 2011-06-29
Hi,

I'm planning on having a play with Ubuntu server. I'm running it on VMWare 7.

I installed Ubuntu server, after that i proceeded to update it.

sudo apt-get update
sudo apt-get upgrade
sudo reboot

After the reboot it just boots into a black screen with a blinking cursor.

I can boot into recovery mode if i hold down shift and i tried to [follow these instructions]("http://knowledge76.com/index.php/Restore_Grub_Bootloader") for repairing GRUB, but it didn't help.

Any ideas?

Thank you

---

### Post by TechSupportx86 on 2011-06-29
It's seems unlikely (not saying impossible) to me that updating apt-get had something to do with this. Now something like do-release-upgrade has the capability of screwing up the OS, but just upgrading the packages seems unlikely.

Are you sure you're allowing enough time for the OS to boot? Mine usually sits at a black screen and cursor for upto a minute. Also seeing as how you can boot into recovery mode, it seems that GRUB isn't your problem, or the BIOS wouldn't see anything as bootable.

You didn't install anything new before upgrading your packages?

---

### Post by ian dobson on 2011-06-30
Hi,

When you let the box boot normally can you ssh into the box? I had a problem with my server that the server monitor didn't display anything after upgrading to 10.10 or 11.04. In the end it was the framebuffer modules that killed the VGA output.

Just blacklist the framebuffer modules and you should be OK.


EDIT: Thinking about it I think I blacklisted the opensource nvidia driver and not the fb module.

Regards
Ian Dobson

---

