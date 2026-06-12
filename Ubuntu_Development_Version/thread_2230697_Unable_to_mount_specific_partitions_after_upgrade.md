---
title: "Unable to mount specific partitions after upgrade"
date: 2014-06-20
forum: Ubuntu Development Version
---

### Post by LastDino on 2014-06-20
After installing 14.10 I got around to running following commands with everything enabled in ''software and update'' manager. And server was ''main server''

```

sudo apt-get update && sudo apt-get upgrade
```

Then
```

sudo apt-get dist-upgrade
```
Everything was completed as expected.
Except when I try to open few of these partition now, I get following error. and all other partitions seem to be mounted by default.

[ATTACH=CONFIG]254111[/ATTACH]

Any ideas?

---

### Post by rrnbtter on 2014-06-20
Greetings,
Load an install disk in "Try" mode. Open a terminal and type "fsck.ext4 /dev/sda(whatever the partition is). Hopefully you have journaled partitions. I recently had a Utopic install tearing up my root partition. I continued to fix it with the above process. I finally did a reinstall from the latest daily.

---

### Post by rrnbtter on 2014-06-20
Greetings,
In addition. Even though Saucy and Trusty were rather tame upgrades I personally think that enabling "proposed" in updates is dangerous business with Utopic. I would say that one is for true testers only. Also dist-upgrade as opposed to upgrade can also give you more than what you may want.

---

### Post by LastDino on 2014-06-21
Well, it fixed itself when I restarted the PC. Also, nothing really is broken on my other operating systems. But thanks for quick response ^^

---

