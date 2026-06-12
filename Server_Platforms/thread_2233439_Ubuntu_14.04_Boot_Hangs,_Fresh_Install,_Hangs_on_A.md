---
title: "Ubuntu 14.04 Boot Hangs, Fresh Install, Hangs on Adding Swap at boot"
date: 2014-07-08
forum: Server Platforms
---

### Post by link3 on 2014-07-08
Just freshly installed Ubuntu 14.04 Server bare-metal to a machine, and first attemp at boot gave a few errors:
```
plymouth upstart bridge respawning too fast
```
A bunch of those, then it did this
```
[     7.028097] Adding 7794684k swap on /dev/sda3. Priority :-1 extents:1 across: 7794684k FS
```

Then the system hangs.

I get around this by booting into recovery than simply resuming normal boot. What is the issue here?

Ive tried editing /etc/default/grub; [PHP]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"[/PHP] which didn't solve the issue.

Any help would be much appreciated.

Regards,
Link

---

### Post by ibjsb4 on 2014-07-08
I found a bug report that seems to apply.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1309617](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1309617)
Found that here
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=plymouth+upstart+bridge+respawning+too+fast&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=plymouth+upstart+bridge+respawning+too+fast&sa=Search&cof=FORID:9)

This thread has several ideas about disabling plymouth that may be of help with your server install.
[http://ubuntuforums.org/showthread.php?t=1886633](http://ubuntuforums.org/showthread.php?t=1886633)

Thats all I got, hope it helps, good luck.

---

### Post by agnimon-gmail on 2014-12-07
I encountered exactly the same problem as you. 
This helped me out:
[http://serverfault.com/questions/546079/ubuntu-server-hanging-on-adding-swap](http://serverfault.com/questions/546079/ubuntu-server-hanging-on-adding-swap)

---

