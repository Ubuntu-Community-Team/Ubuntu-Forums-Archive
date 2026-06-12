---
title: "samba server group"
date: 2009-12-16
forum: Server Platforms
---

### Post by bilal_jan on 2009-12-16
hello everyone
i wanna add a group to samba share such that all members of that group can access samba.
like if i have system user named temp and i add it to group named access
now if i add group access to samba share then user temp can access that as well.
can anyone help me how can i do that???

---

### Post by cj13579 on 2009-12-16
try this in your /etc/samba/smb.conf file:

```
[share]
    path = /path/to/dir
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force group = access

```

---

### Post by Krupski on 2009-12-16
> **bilal_jan said:**
> hello everyone
i wanna add a group to samba share such that all members of that group can access samba.
like if i have system user named temp and i add it to group named access
now if i add group access to samba share then user temp can access that as well.
can anyone help me how can i do that???

Here's my "smb.conf" file which allows complete access to all files on the file server without any usernames or passwords required. Note that there is NO security... anyone on your local intranet can access the files.


```

#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#
#======================= Global Settings =======================

[global]
        server string = Storage Drive
        security = SHARE
        deadtime = 5
        socket options = tcp_nodelay iptos_lowdelay so_keepalive so_rcvbuf=32768 so_sndbuf=32768
        load printers = No
        show add printer wizard = No
        os level = 65
        preferred master = Yes
        dns proxy = No
        wins support = Yes
        create mask = 0644
        guest ok = Yes
        hide dot files = Yes
        store dos attributes = Yes
        dos filemode = Yes

[shared]
        comment = storage
        path = /home/shared
        read only = No

```

---

### Post by Iowan on 2009-12-16
There is an "valid users=" option for shares that can include groups```
valid users=@access
```

---

