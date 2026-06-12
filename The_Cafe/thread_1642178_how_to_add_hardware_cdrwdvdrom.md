---
title: "how to add hardware cdrw/dvdrom"
date: 2010-12-10
forum: The Cafe
---

### Post by djedyed on 2010-12-10
I am running ubuntu server 10.10 with a desktop gui however i am trying to add a cdrw/dvdrom please help
Thanks in advance
I am a fascinated newbie to the unix/linux platform so a bit of elaboration will be highly appreciated.
I typed: sudo -o loop /dev/cdrom /mnt
and I got
sudo: invalid option -- 'o'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u username|#uid] file ...
username@server:~$ usage: sudo -h | -K | -k | -L | -V
Itried to google it but no luck

---

### Post by handy on 2010-12-10
Could you post a copy of your /etc/fstab file?

More details regarding whether you have just added the hardware, is it USB or SATA external?

Do you know about the mount command?

Try "sudo mount -a" in the terminal.


This is likely not the most appropriate part of the forum for seeking this kind of technical help, but carry on, it may get moved at a later time.

Welcome to the forum too, by the way. :)

---

### Post by ssam on 2010-12-10
did you try just putting a CD/DVD in?

---

