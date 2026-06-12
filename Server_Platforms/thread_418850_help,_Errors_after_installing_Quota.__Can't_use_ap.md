---
title: "help, Errors after installing Quota.  Can't use apt-get or edit files"
date: 2007-04-22
forum: Server Platforms
---

### Post by adaml52 on 2007-04-22
I recently set up a new Ubuntu 7.04 Server.  I decided to set up the using the guide found on Howtoforge ([The Perfect Setup - Ubuntu Feisty Fawn ]("http://www.howtoforge.com/perfect_setup_ubuntu704")).  

Every thing was going great until I reached page 4 and tried to install Quota.  The install worked, and I changed /etc/fstab like the guide requested.  touch /quota.user /quota.group and chmod 600 /quota.* also seamed to work, but when I ran the next command I got an error.

```

# mount -o remount /
mount: / not mounted already, or bad option

```

I'm not sure what happened, but now I can't do much of anything.  I get errors when I try to apt-get
```

# apt-get install bind9
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

and I can't edit any files as now.  Does anybody have any ideas on what I did to mess things up or how to fix it?

Thanks,
AdamL52

---

