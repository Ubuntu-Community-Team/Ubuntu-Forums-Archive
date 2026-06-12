---
title: "chkrootkit and known good binaries"
date: 2007-01-29
forum: Server Platforms
---

### Post by neill on 2007-01-29
hi

anyone know how to run chkrootkit with the -p option ?

it's something i used to do in fedora - burn the known good binaries (awk, echo etc etc) to a CD following a clean install, mount that somewhere like /mnt/chk_bin, then run chkrootkit -p /mnt/chk-bin

it's been a while now but i can't seem to get it to work in ubuntu - the CD mounts as /media/cdrom0 and if i use sudo chkrootkit -p /media/cdrom0/bin (which is where the binaries are) i get permissions errors

but all the binaries have appropriate permissions 555

any ideas ?

thanks

neill

---

