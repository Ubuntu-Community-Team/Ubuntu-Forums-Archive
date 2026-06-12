---
title: "Remote process viewer"
date: 2008-10-01
forum: Server Platforms
---

### Post by tr33m4n on 2008-10-01
Hello there,

I was wondering whether there was a command line process viewer that could display the running processes of a server running on my network remotely? I realise I could log in via ssh and type 'top', however id quite like to automate this... so maybe a script? any help would be greatly appreciated.

Many thanks
Dan

---

### Post by HermanAB on 2008-10-01
One line:
$ ssh user@server top

---

### Post by tr33m4n on 2008-10-01
```
doyle@doyle-desktop:~$ ssh doyle@192.168.0.101 top
doyle@192.168.0.101's password: 
TERM environment variable not set.
doyle@doyle-desktop:~$ ssh doyle@192.168.0.101 htop
doyle@192.168.0.101's password: 
Error opening terminal: unknown.
doyle@doyle-desktop:~$ 
```

Also I kind of need a way of not having to enter my password everytime.
Thanks

---

### Post by HermanAB on 2008-10-01
Here you go:
$ cd .ssh

$ ssh-keygen -b 1024 -t dsa
enter
y
enter
enter

$ scp id_dsa.pub user@server:~./ssh/authorized_keys
password
enter

$ ssh user@server top
la voila!

---

