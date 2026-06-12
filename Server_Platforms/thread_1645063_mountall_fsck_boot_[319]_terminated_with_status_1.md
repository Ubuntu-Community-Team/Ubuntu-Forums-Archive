---
title: "mountall: fsck /boot [319] terminated with status 1"
date: 2010-12-14
forum: Server Platforms
---

### Post by warrenscorgie on 2010-12-14
Hi guys, 

I'm running a VM with ubuntu 10.4 installed and i ran apt-get update, and thereafter apt-get upgrade. When i restarted the VM, the following error messages were displayed:

```
init : udevtrigger main process (328) terminated with status 1 
init : udevtrigger post-stop process (331) terminated with status 1 
init : udevmonitor main process (327) killer by TERM signal 
mountall: fsck /boot [319] terminated with status 1 
init : ureadahead-other main process (383) terminated with status 4
```

Any help would be appreciated.

Regards
Warren

---

### Post by CharlesA on 2010-12-14
Does hitting "s" do anything?

---

### Post by warrenscorgie on 2010-12-14
Hi Charles, 

Unfortunately 's' doesn't work hey, it just hangs at the error message and when i select 'esc' then i get the ubuntu 10.4 splash screen also just hanging.

---

### Post by CharlesA on 2010-12-14
Try booting into recovery mode (hold down shift to get the Grub menu) and see what errors it throws up.

---

### Post by ZOMBitch on 2011-01-01
check if your paths is correct in /etc/fstab

---

