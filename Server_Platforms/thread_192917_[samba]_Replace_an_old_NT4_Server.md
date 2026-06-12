---
title: "[samba] Replace an old NT4 Server"
date: 2006-06-09
forum: Server Platforms
---

### Post by the_g_cat on 2006-06-09
Hi there,

I'm trying to replace an old (very...) NT4 server with a nice ubuntu server install. Unfortunately, the clients wil still be NT4 Desktops for some time. Basically, I only need one world-writable Share, and a password protected share for one user (the boss). Problem is: I don't even get the password-less share to work with NT4.

Here ist my smb.conf:
```
$ cat /etc/samba/smb.conf | grep -v "^#" | grep -v "^;" | grep -v "^$"
[global]
   workgroup = Report.age
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = samba
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
[Donald]
        comment = Fuer alle offen
        path = /home/samba/Global
        create mask = 664
        directory mask = 775
        browseable = yes
        writeable = yes
        guest only = yes
```

Basically, I took the default config file coming with ubuntu and edited what I know.

With that config file, I can log in from the ubuntu machine on itself without password, and I can read an write everything. From my OS X Laptop, I can log in with a blank username and password (think it is a Finder quirks rather than one of the server). From the NT4 Desktop though, he keeps asking me for a login and a passwor, even if I leave them blank.

If anyone could help me, it would be much appreciated, thanks in advance.

the_g_cat


P.S. I also need to set up the same shares with netatalk for OS 8 and 9 clients, but have quirks there too, maybe you could also help me [in this other topic]("http://www.ubuntuforums.org/showthread.php?t=192923")

---

### Post by Iowan on 2006-06-09
[QUOTE=the_g_cat] Problem is: I don't even get the password-less share to work with NT4.
[/QUOTE]
**security = share** should get you close(r) to the passwordless share

---

### Post by the_g_cat on 2006-06-11
Yes, but then I wouldn't be able to have one password-protected share, would I?

---

