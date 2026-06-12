---
title: "Prevent automatic kernel updates - how?"
date: 2007-12-10
forum: Server Platforms
---

### Post by bproven on 2007-12-10
I am looking for a method that would allow me to run my security updates on my dapper 6.0.6 server without running kernel updates automatically.  I would rather look at the kernel errata before deciding to upgrade my kernel.  I know I can set my sources.list to security repositories only, but I want to disallow kernel upgrades/updates from these repositories.  I do not have X installed on any of my servers so I am looking for a solution that would allow me to run "apt-get update && apt-get upgrade" and exclude kernel packages.

I have seen some documentation on pinning packages, but have not found anything that was very comprehensive (many resources and forum posts have in fact been contradictory in nature).  Does Ubuntu have an official documented process on doing this?  Seems like it would be a common request(?)

Anyway, I just want to enable automatic security updates via cron (or maybe kick them off manually) BUT ignore all kernel updates so I can choose to run those separately (or not at all).  The reason for this extra caution is that I want to avoid issues with kernel upgrades and my servers - and "yes"  I understand the security implications in delaying kernel upgrades ;)

Thanks to anyone who can help me or point me to the doc/post with the solution

---

### Post by g2g591 on 2007-12-10
you need to uninstall the kernel metapackage. such as apt-get remove linux-image-server. be sure to reinstall your current kernels as I think apt might want to autoremove them.

---

### Post by bproven on 2007-12-10
OK, I run "apt-get remove linux-image-server -s" and get the following:

```

$ sudo apt-get remove linux-image-server -s
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  linux-image-server linux-server
0 upgraded, 0 newly installed, 2 to remove and 57 not upgraded.
Remv linux-server [2.6.15.24]
Remv linux-image-server [2.6.15.24]

```

If I run "uname -r" I see my current kernel is this:
```

2.6.15-26-server

```

So do I have to reinstall "linux-server"?  What effect would it have if I did/did not?  Better question is once this is done, how would I manually upgrade my kernel (by itself) later if desired?

Sorry about the questions - some things I am still noob on regarding Ubuntu.  This really needs to get into the Ubuntu docs at some point as I see a bunch of posts on this and a bunch of diff answers ;)

---

### Post by craigp84 on 2007-12-12
Another approach is to ```
sudo apt-get install unattended-upgrades
```

You then should tweak /etc/apt/apt.conf.d/50unattended-upgrades to suit your needs, i'd guess something like the below would be good for you -

```

// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu dapper-security";
// Don't want feature enhancements etc.. just security updates
//      "Ubuntu dapper-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
        "linux-server";
        "linux-image-server";
};


```

Might need some tweaking, i don't have an ubuntu box to hand for testing this...

-c

---

### Post by bproven on 2007-12-15
Neat - I'll give a whirl since I have a Ubuntu vm here to test it on.  Thanks for the info.  Is there a place we can put this kind of stuff in the Wiki for other users?

---

