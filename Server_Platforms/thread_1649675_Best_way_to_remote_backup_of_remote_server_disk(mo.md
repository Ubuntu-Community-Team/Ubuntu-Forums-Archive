---
title: "Best way to remote backup of remote server disk(mounted)"
date: 2010-12-20
forum: Server Platforms
---

### Post by rado3105 on 2010-12-20
Is possible to backup disk(whole) on remote server which is mounted? If yes how, thanks.

---

### Post by lukeiamyourfather on 2010-12-20
Likely you've mounted a partition or a shared directory from a remote system which isn't the same thing as mounting a physical disk on a local machine. In that case, no, you can't backup the entire disk as the entire disk isn't mounted on the client side (nor can it be). If you just want to backup the contents of the mount then use rsync with the archive option (-a).

---

### Post by rado3105 on 2010-12-25
It can be done mounting partition as ro, using this command:
dd if=/dev/sda | ssh root@target "(cat >/root/backup.img)"

where /dev/sda is disk on server, target is ip of pc I am trying to do the download from.

Everything works fine, but when I do the backup using that command it makes the backup image of size of hardisk(32gb), but only 4gb are with data. So is any way to backup just that data(something similar to acronis true image)?

---

