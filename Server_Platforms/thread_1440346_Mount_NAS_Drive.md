---
title: "Mount NAS Drive"
date: 2010-03-27
forum: Server Platforms
---

### Post by damo12 on 2010-03-27
[FONT="Comic Sans MS"]I have reccently bought a NAS drive to work as a backup and storage device for my network.  I eventually plan to backup my files from my server to the NAS drive which will also give me the option to take the drive elsewhere if I need to.

The problem I have is mounting the NAS drive in Ubuntu.  I usually access my server through Webmin but when I try to mount the drive I get the error message:

> mount error: could not find target server. TCP name storage-702b/public not found
No ip address specified and hostname not found


I have tried manually mounting the drive by modifying my fstab but I get the same message.

I am running Ubuntu Server 8.04.

Thanks in advance.[/FONT]

---

### Post by dipeshmehta on 2010-03-28
You may mount NAS with something like this:
```
mount -t cifs //192.168.x.x/data /mnt/nas -o username=username,password=password
```

Just make sure that, your kernel supports CIFS.

Dipesh

---

### Post by damo12 on 2010-03-28
[FONT="Comic Sans MS"]Thank you for the help.  That works a treat.[/FONT]

---

