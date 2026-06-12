---
title: "SAMBA printer FTW?"
date: 2007-11-27
forum: Server Platforms
---

### Post by prodezigner on 2007-11-27
I don't have a printer installed on my server, yet my Windows network picks up my server as having a printer, my config for SAMBA has no mention of a printer, just shared drives... any idea how to make my home network not pick that up? It's a small annoyance, but I'd like to resolve it.

---

### Post by MJN on 2007-11-27
Are you sure it's not actually Windows putting a printer 'placeholder' in the network browser?
 
Take a look at the output of **smbclient -L localhost -N** to see how Samba is actually 'advertising' things.
 
(This is educated guesswork as I'm not at my machine right now to compare/configure)
 
Mathew

---

### Post by doogy2004 on 2007-11-27
Windows tends to do that it is simply cosmetic and does not mean that anything is configured improperly.

---

### Post by sciurus on 2007-11-29
fF there are any references to printer sharing in your smb.conf, comment them out.

---

### Post by prodezigner on 2007-11-29
smb.conf was wrote by hand...

Last login: Thu Nov 29 00:56:00 2007 from 192.168.1.109
Linux Ubuntu 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
root@Ubuntu:~# screen -r
[detached]
root@Ubuntu:~# smbclient -L localhost -N
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

        Sharename       Type      Comment
        ---------       ----      -------
        storage         Disk      storage
        public          Disk      public
        IPC$            IPC       IPC Service (Samba 3.0.26a)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]

        Server               Comment
        ---------            -------
        BRANDON-DESKTOP      Brandon's Desktop
        BRN_8A3592
        DAVE
        SHELLS
        UBUNTU               Samba 3.0.26a
        VICKII-DESKTOP       Vickii's Computer

        Workgroup            Master
        ---------            -------
        WORKGROUP            UBUNTU
root@Ubuntu:~#

that's my broadcasting info...

my .conf is

[global]
        workgroup = WORKGROUP
        security = share
        guest account = nobody

[storage]
        comment = storage
        path = /Storage/
        public = yes
        writable = yes
        browseable = yes
        force user = nobody
        force group = nogroup

[public]
        comment = public
        path = /public/
        public = yes
        writable = yes
        browseable = yes
        force user = nobody
        force group = nogroup

---

### Post by MJN on 2007-11-29
I think it's just a Windows-ism then.
 
Mathew

---

