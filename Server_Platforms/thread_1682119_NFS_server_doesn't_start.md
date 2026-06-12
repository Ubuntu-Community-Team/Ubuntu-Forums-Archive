---
title: "NFS server doesn't start"
date: 2011-02-05
forum: Server Platforms
---

### Post by DeepThoughts on 2011-02-05
So I thought I'd try enabling NFS on my Ubuntu Server (10.04) and found this guide: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Since the guide is tested on 10.04 I thought it would go great. That didn't happen. It didn't go at all. The last step of the server-part is this:
```
# /etc/init.d/nfs-kernel-server restart
```

You'd think that it is the easiest step but it has proven to be the hardest. Why? Because /etc/init.d/nfs-kernel-server doesn't even respond to any commands you send it (doesn't work when using service nfs-kernel-server either). If you try to start, stop, reload or any of the other commands it will just start spitting out this (repeated ad infinitum): 
```

y
y
y
y
y
y
y
y
y
y

```
To be honest I have no idea how to troubleshoot this and I don't understand whats wrong. Is the launch-script corrupt? Is it something else? No idea since I don't get a real error message I don't really now where to begin. Help is very much appreciated.

---

### Post by luvshines on 2011-02-05
Whenever I am bumped with such stuff, I always run the script with bash debugging```

bash -x /etc/init.d/<service> start
```

---

### Post by DeepThoughts on 2011-02-05
> **luvshines said:**
> When I am bumped with such stuff, I always use run the script with bash debugging```

bash -x /etc/init.d/<service> start
```
Thank you!

Awesome little tip there. :) When I ran it in debug mode I noticed a space that had snuck in to /etc/default/nfs-kernel-server and when I corrected that it solved the issue.

---

