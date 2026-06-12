---
title: "Can't access shared folder in VBox"
date: 2012-10-23
forum: Virtualisation
---

### Post by uRock on 2012-10-23
Host: Windows 7 Pro
Client: Ubuntu 12.04
VM software: VirtualBox
Guest additions: installed
Shared directory: E:\ubuntushare (NTFS)
NTFS folder permissions: Everyone = full control

I can see the shared folder in ubuntu, but I can't do anything with it. When I try, I get, > You do not have the permissions necessary to view the contents of "sf_ubuntushare". I have tried chowning it, but that does not change the permissions visible in ubuntu.

What else can I do to get ubuntu to mount, preferably automatically, to this folder?

---

### Post by Habitual on 2012-10-24
Host > Settings > Shared Folders > Double click the share
Read-only and auto mount checked?

---

### Post by wheeze on 2012-10-24
> **uRock said:**
> Host: Windows 7 Pro
Client: Ubuntu 12.04
VM software: VirtualBox
Guest additions: installed
Shared directory: E:\ubuntushare (NTFS)
NTFS folder permissions: Everyone = full control

I can see the shared folder in ubuntu, but I can't do anything with it. When I try, I get,  I have tried chowning it, but that does not change the permissions visible in ubuntu.

What else can I do to get ubuntu to mount, preferably automatically, to this folder?

From the VBox User Manual:

> **Note**

Access to auto-mounted shared folders is only                 granted to the user group                 vboxsf, which is created by                 the VirtualBox Guest Additions installer. Hence guest users                 have to be member of that group to have read/write                 access or to have read-only access in case the folder is not                 mapped writable.



Your user account in Ubuntu guest OS needs to be in the vboxsf group.

---

### Post by uRock on 2012-10-24
> **Habitual said:**
> Host > Settings > Shared Folders > Double click the share
Read-only and auto mount checked?Yes.:)

> **wheeze said:**
> From the VBox User Manual:



Your user account in Ubuntu guest OS needs to be in the vboxsf group.

Thanks! Next on my list is finding the correct command.```
urock@uRock-ubuntu:~$ sudo adduser urock vboxsf
[sudo] password for urock: 
Adding user `urock' to group `vboxsf' ...
Adding user urock to group vboxsf
Done.
```

---

### Post by uRock on 2012-10-24
Alright, that worked. Thanx!

---

### Post by wheeze on 2012-10-25
> **uRock said:**
> Alright, that worked. Thanx!

Good to hear you got it sorted out.

I always add gnome-system-tools to any installation I'm using to get a nice GUI for dealing with users, groups and things.

---

