---
title: "Kernal Panic - Not Syncing....... Ubuntu 6.06.2LTS"
date: 2009-09-02
forum: Server Platforms
---

### Post by chrislynch8 on 2009-09-02
When booting to the must recent Kernel release I get a Kernel Panic adn the server will not boot. Here is the Boot message

```

Booting 'Ubuntu, kernel 2.6.15-54-amd64-server'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0xfd
kernel  /boot/vmlinuz-2.6.15-54-amd64-server root=/dev/md0 ro quiet splash
    [Linux-bzImage, setup=0x1c00, size=ox168810]
initrd  /boot/inited.img-2.6.15-54-amd64-server
    [Linux-initrd @ 0x37fef000, 0x32 bytes]
savedefault
boot    

```

Then I get
```

Decompressing Linux....dones.
Booting the kernel,
[   70.125964] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```
Then I just get a flashing cursor and I have to hold in the power button to shut down the Server.

BUT 

Then I can boot it again and I can select a previous Kernel and the server boths up as Normal. Any ideas why this would happen.

Rgds
Chris

---

### Post by chrislynch8 on 2009-09-02
The issue was related to a previous issue I had. regarding missing files, I was also missing the /usr/bin/find file so the update-initrdfs -u command wasn't running.

Rgds
Chris

---

