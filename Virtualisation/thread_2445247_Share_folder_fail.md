---
title: "Share folder fail"
date: 2020-06-11
forum: Virtualisation
---

### Post by satimis on 2020-06-11
Hi all,

VM - Ubuntu 20.04 Gnome desktop newly installed
Host - Ubuntu 18.04

Sharing folder and copy & paste between Host and VM fail
GuestAddition already installed

Warning - please see attached screenshots

Please help.  Thanks

Edit
===
$ ls -ald /media/sf_Transfer_Folder/```

drwxrwx--- 1 root vboxsf 4096 Jun 11 10:30 /media/sf_Transfer_Folder/

```
Do I need to change it as```

$ ls -ald /media/sf_Transfer_Folder/
drwxrwx--- 1 satimis vboxsf 4096 Jun 11 10:30 /media/sf_Transfer_Folder/

```


Regards
satimis

---

### Post by satimis on 2020-06-11
Hi all,

Share folders works after running```

$ sudo adduser satimis vboxsf

```

But copy & paste between VM and Host still unable to work

Settings -> General -> Advanced
Shared Clipboard: [Bidirectional]
Drag'n'Drop: [Bidirectional]

It is very strange to me.  This is not my first time running Ubuntu.

Advice would be appreciated.

Regards
satimis

---

