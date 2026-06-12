---
title: "Samba server not asking for passwords."
date: 2011-02-21
forum: Server Platforms
---

### Post by Tactical Fart on 2011-02-21
I'm trying to set up the server to at least ask for a password. I can connect to it without any trouble, but so can everyone else. Here is my smb.conf.

```

[global]
    ; General server settings
    netbios name = SERVER
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = false
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /home/tactical
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tactical
    force group = tactical

```

I pretty much removed anything that talked about printing. How can I make samba ask for a password?

---

### Post by dtfinch on 2011-02-21
If their samba passwords match their Windows login passwords, Windows would log them in automatically without prompting.

You can use the "valid users" option to limit a share to specific users or groups (prefixed with @). Otherwise anyone who can log into the server can view the share.

Unrelated to your issue, I'd take out the "SO_RCVBUF=8192 SO_SNDBUF=8192" if you have a gigabit network. 8192 was good on 100mbit networks, but it's limiting on gigabit. I used to use 64240, but have lately stopped messing with socket options entirely.

---

### Post by Tactical Fart on 2011-02-21
So my configuration is good, but windows is just silently authenticating? This is neat but my windows user name starts with a capital. 

Anyway I tried from another machine that does not share the same username and it asked for a password. Thanks for the help!

---

