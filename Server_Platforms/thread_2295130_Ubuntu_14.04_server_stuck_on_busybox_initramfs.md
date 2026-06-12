---
title: "Ubuntu 14.04 server stuck on busybox initramfs"
date: 2015-09-16
forum: Server Platforms
---

### Post by Mititelu_Radu on 2015-09-16
I admit that I did it. I had a working server running on RAID 1 and wanted to see if I had a working RAID. So I shut it down, unplugged HD1 and start it, then the same thing with HD 0, and everything worked fine except when I plugged both of them back , I was stuck with busybox initramfs msg at boot. I am new to Linux and I am a bit lost. I did a little research and some users advice to reinstall grub, but I don't know how that will work out with my RAID 1 setting. Can you give me some advise please? If anything else fails I could wipe it all ans start over but it will be a pain to recreate all users with shared folders and samba server.

---

### Post by darkod on 2015-09-16
Did you check the raid status from live mode? You can boot the server (provided it's in your home) with the desktop live cd into live mode, and check mdadm status. Note that the desktop cd does not include mdadm by default, so you need to apt-get install mdadm first. Every time you reboot with the cd.

Once the package is installed you can check basic status with:
cat /proc/mdstat

Post the output here if you don't understand it.

Reinstalling grub is no problem, raid or no raid, but the status of the array is more important to check first. Because you were disconnecting both disks one after another mdadm might have lost track which disk is "good" and which needs resync. You left them to sync fully before each unplugging right?

---

### Post by Mititelu_Radu on 2015-09-16
I am not to sure. I just made the settings for raid on server install, and never touched on anything related to raid, so it is on default settings. I am getting live cd now. Thank you.

---

