---
title: "Monitor users' access times in Ubuntu Server"
date: 2008-01-31
forum: Server Platforms
---

### Post by Alex1200GS on 2008-01-31
Hi all,

here's the issue: I have set up an Ubuntu Server with Gutsy Gibbon, a nice Samba with a few shares, and all this is accessible from within a local area network full of Windows PC's. This machine acts as a file server, and it's where we all store our common data.

Before this machine, I used a Clackconnect PC, for the exact same purpose. With that machine, I used to SSH there from my desk, then issue a "finger" or "who" or "w" or "last" command and see what users are connected to the machine, what time they connected, what they're currently doing, etc.

It seems that the Ubuntu machine does not work the same way, and all the above commands only "see" users that have logged in via SSH or locally, and they all ignore samba users and their whereabouts.

I can't find anything helpful in smb.conf or the commands' man pages. How can I monitor samba users' access in an Ubuntu Server machine?

Thanks,

Alex

---

### Post by cdenley on 2008-01-31
```

smbstatus -b

```

---

