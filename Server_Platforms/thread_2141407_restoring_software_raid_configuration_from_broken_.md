---
title: "restoring software raid configuration from broken OS drive"
date: 2013-05-02
forum: Server Platforms
---

### Post by underpen on 2013-05-02
Hello,

I have a file server setup with Ubuntu Server 12.x, where the OS (Ubuntu) is installed to an SSD and I have a software raid on 4 other harddrives. Yesterday, the OS drive crashed. I was able to boot into Helix and get the mdadm.conf off, but nothing else would read and after another reboot I could not read anything. It still seems like the drive is dead now as well.

I ordered another SSD from newegg and was hoping it would be a straightforward task to get the raid readable again by reinstalling Ubuntu on the new SSD and then loading the old mdadm.conf on it. From there, hopefully the raid would just be readable and start as normal.

Will this work? Is there something else I should know about the process?

Thanks!!

---

### Post by darkod on 2013-05-02
As first try don't even bother with the mdadm.conf, but keep it safe at hand. The beauty of mdadm is that it can assemble itself from the raid disks.

It should detect your array right away when installing.
Even if it doesn't, once you have the OS installed you can do:
```
sudo mdadm --assemble --scan
```

That will scan all disks/partitions and assemble any good arrays. After that you might need to insert them into mdadm.cong and update the initramfs (only if it wasn't detected during install), but that's easy.

---

### Post by rubylaser on 2013-05-02
Don't forget to install mdadm before trying to run the assemble :)
```
sudo apt-get install mdadm
```

---

### Post by darkod on 2013-05-02
Isn't it included on the server? Or it doesn't add it unless you use raid during partition setup?

On the other hand, the OP said "fileserver" which doesn't necessarily mean the server OS.

Yes, mdadm doesn't come with the desktop version. You will need to install the package before running any mdadm commands.

---

