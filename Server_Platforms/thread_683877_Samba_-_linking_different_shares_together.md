---
title: "Samba - linking different shares together"
date: 2008-01-31
forum: Server Platforms
---

### Post by Janthkin on 2008-01-31
Scenario: I have a samba 3 server (Ubuntu 7.10 server, if it matters) in a (Windows) business environment. We've set it up with a number of different shares, with different permissions for different groups of users, and different create masks for different shares. One share, for example, is simply "Public" - each employee has a folder set 0755 within the share. Another share is an "Inbox" - each employee has a world-writable folder to drop stuff in (1777).

General Problem: Too many drive letters. We have a lot of unsophisticated users, and we want to things to appear straightforward on the Windows end.

Attempted Solution: use symlinks in each employee folder to point to the appropriate folder in the Inbox share.

Specific problem: if you follow the symlink, Samba is applying the rules, create mask, etc. for the "Public" share rather than the "Inbox" share.

(Setting follow symlinks = no just disables symlinks entirely, and the description of wide links doesn't seem relevant here.)

Any ideas?

One odd thing: creating a Windows shortcut within a user's Public folder, pointing to the network path for the "Inbox" share, works exactly as it should (the "Inbox" rules are applied, rather than the "Public" rules). But I don't know any way to automate Windows shortcut (.lnk) generation in linux, and it seems wrong anyway.

Other funny thing: "deleting" a symlink to a folder via an Explorer window on a mapped samba share results in the deletion of the symlink AND the complete contents of the folder.

Relevant portions of smb.conf:
[global]
    ; General server settings
    netbios name = MHBfileserver
    server string =
    workgroup = MHB
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_\
SNDBUF=8192
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = yes
    printing = CUPS
    printcap name = CUPS
    syslog = 1
    syslog only = yes
    keepalive = 3600

[Public]
    path = /[path]/public
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    delete readonly = yes
    vfs object = recycle
        recycle:repository = .deleted/%U
        recycle:keeptree = Yes
        recycle:touch = Yes
        recycle:versions = Yes
        recycle:maxsize = 1000000000
        recycle:exclude = *.tmp

[Inbox]
        path = /[path]/inbox
        browseable = yes
        read only = no
        guest ok = no
        create mask = 1777
        directory mask = 1777
        follow symlinks=no
vfs object = recycle
    recycle:repository = .deleted/%U
    recycle:keeptree = Yes
    recycle:touch = Yes
    recycle:versions = Yes
    recycle:maxsize = 1000000000
    recycle:exclude = *.tmp

---

### Post by cdenley on 2008-01-31
Everything you described is basically what I would expect to happen. I'm not aware of any linux tools to create windows shortcuts, but you can create shortcuts at login by calling a command line program such as [this]("http://www.optimumx.com/download/#Shortcut") from your logon script.

---

