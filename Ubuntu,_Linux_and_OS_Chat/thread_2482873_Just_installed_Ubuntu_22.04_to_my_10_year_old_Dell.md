---
title: "Just installed Ubuntu 22.04 to my 10 year old Dell and not sure"
date: 2023-01-12
forum: Ubuntu, Linux and OS Chat
---

### Post by brevardo2 on 2023-01-12
I'm not sure if I installed it correctly as far as the partitions go and if I used GPArted correctly. My Dell has a 989 GB Hardrive. I think because I was having difficulty installing this version of Ubuntu from a USB Drive, I may have set it up so I can only use 95 GB of my hard drive. Could you look at the picture I took and tell if I'm okay? It looks like 2 or 3 different Mounts or Partitions? I'm concerned that if I download files and use up the 95 GB, this Install is going to think I have no Disk Space available? I accidentally set it up to have a 495 GB Mount and another 425 Mount ( see picture ) Will this current install work for me or is there something else I could still do to fix it so I can easily access the entire 985 GB Hard drive.

---

### Post by TheFu on 2023-01-13
Run this command, please:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
```
and post the output inside forum code-tags.  My signature has a link for what that means, if you don't know.

Images are hard to copy/paste and highly important things. Also, that image doesn't provide much information.

---

