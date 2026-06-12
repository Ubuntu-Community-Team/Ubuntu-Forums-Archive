---
title: "Server can't boot with external HDD attached"
date: 2010-02-20
forum: Server Platforms
---

### Post by buntolith on 2010-02-20
Hi,

I have a NFS & SSH server for my private network. I have an external HDD attached via USB. I can mount it OK when the server is running and it works fine to do cronjob rsync to it to back up my important folders.

I tried to put the external HDD in the fstab for automount during boot but the server just can't start up when the HDD is attached. I have tried to reboot with the HDD in fstab and also without but the server just hangs at startup.

What can I do to fix this?

---

### Post by cariboo on 2010-02-20
Check the boot order in the bios, make sure your external drive is not in the boot order. Most bios let you set up 4 boot devices, if you only boot from the CD-Rom and hard drive, disable the other boot options.

---

### Post by buntolith on 2010-02-22
Ok, thanks for the tips. I just gave away my monitor so I will try this when I have a monitor again and report back...

---

