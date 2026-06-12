---
title: "Server not starting after update: I'm stuck!"
date: 2015-09-17
forum: Server Platforms
---

### Post by Matteo_Civera on 2015-09-17
HHi everybody, Matteo's writing.

Today I had a normal "apt-get update" on an Ubuntu Server but after the reboot it didn't start and there was this message:

Alert /dev/mapper/srv002-root does not exist. dropping to a shell!

Does anybody know how to try to fix this problem? I can start from a live distro.

Thanks guys!

Matteo

---

### Post by darkod on 2015-09-17
That message is complaining that the LVM is not running. Are you using only LVM or software raid too?

---

### Post by Matteo_Civera on 2015-09-17
There's a hardware RAID 1 (mirroring) made with a LSI SCSI device

---

### Post by darkod on 2015-09-17
And I assume you have checked that the raid array is working correctly right?

You can check the LVM by booting in live mode, then add the lvm2 package and try to activate all LVs:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

That should activate all LVs (it will tell you which ones have been activated). Double check if all of your LVs activate correctly.

---

### Post by Matteo_Civera on 2015-09-17
I did it and it activated all the LVs (root + swap).
What do I have to do now?

---

### Post by darkod on 2015-09-17
It seems the LVM is functioning. Try restarting it and see if it will boot normal. Maybe it will "fix itself". :)

---

### Post by Matteo_Civera on 2015-09-17
Nothing to do: same error... :(
Now I'm going make an image with CloneZilla

---

### Post by darkod on 2015-09-17
I just remembered, try this... Boot the server and when the grub menu shows up press any key (like the space bar) to stop it from booting. Be fast because I think the boot menu shows only for 3 seconds by default. But if you hit any key it will stop the count.

Then look in the grub menu options. The top option is the default one, the latest kernel. But below it there should be like "Older ubuntu versions" or "Avanced options" or something. When you select that and hit Enter it should open list of older kernel. Try the second older kernel and see if it boots ok. If not, try the third, etc. See if that helps.

---

### Post by Matteo_Civera on 2015-09-20
Hi Darko. I finally did it. I couldn't choose the start menu because the monitor was out of range, so I decided to virtualize the server!
After a couple of attempts, I reconfigured the network and started using the older kernel with success!
Now I backup all the services, I migrate all the files and then try another update!
Thanks all!!!

---

