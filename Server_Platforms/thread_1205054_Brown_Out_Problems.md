---
title: "Brown Out Problems"
date: 2009-07-05
forum: Server Platforms
---

### Post by uptwobucks on 2009-07-05
We suffered a electrical Brown out 2 weeks ago. Power surge knocked out lots of electronic. My ubuntu server is still working and still online with my websites but I am experiencing a problem at boot up. The message is:

Mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing code page or helper program, or other error. Try viewing dmesg |tail

The results of dmesg | tail:

etho: no IPv6 routers present
ppdev: user-space parallel port driver
Bridge firewalling registered
vnet0 starting userspace failed STP failed, starting kernel STP
nf_conntrack version 0.5.0
config_nf_ct_acct is deprecated and will be removed soon. Please use
nf_conntract.acct=1 kernel paramater, acct=1 nf_conntrack module option or 
sysctl net.netfilter.nf_conntrsck_acc=1 to enable it.
clock source tsc unstable (delta = 179983542 ns)
vnet0 no IPv6 routers present

The system boots but then goes into a file system check that says "allocating"

Does this for 30 minutes then boots up.

Any advice? Please be specific in your reply, I'm a newbie.

Thanks a million..

---

### Post by ajgreeny on 2009-07-05
Perhaps try a manual fsck.  Boot into the live CD and from that in terminal run ```
sudo fsck /dev/sdx
```changing the sdx to the correct, obviously.
Sometimes this does a better job that the fsck at bootup; I've no idea why, but it does appear to be the case.  If you can't run a CD on your server, try a live install on USB drive, but otherwise, I don't know what else to suggest.

---

### Post by HermanAB on 2009-07-05
First of all, go and buy a battery backup power supply.  It costs less than $100 and will make your server last a few years longer than when it is directly on the mains.

I second the manual fsck, but make a backup before you do that.

---

### Post by uptwobucks on 2009-07-06
Thanks very much! Working great now. I do have a battery back up on the server, but didnt know it had a bad battery and was running direct. Guess I need a better back up system. Will definitely get another. Again..thanks.

---

