---
title: "Using rsync on a different SSH port"
date: 2009-06-04
forum: Server Platforms
---

### Post by Kareeser on 2009-06-04
Quick question for y'all:

Computer A is trying to synchronize a folder with Computer B.

Computer B is behind a router which translates the external port 23 into the internal port 22 (ssh).

Computer A: rsync -avze ssh ~/MilitarySecrets/ user@computer-B:~/enemyHQ/

However, try as I might to mess around with switches, rsync just won't connect to computer B on port 22! It seems as though because I'm using an SSH tunnel, it uses the defaults and picks port 23, which isn't the correct computer.

--PORT=23 doesn't work, it uses port 22 anyway.

Help? :)

---

### Post by hictio on 2009-06-04
You can do it like this:

```

rsync -e 'ssh -p xxxx' src dst

```

Or, you can also try using a definiton for the remote server on your ~/.ssh/config file, specifying the alternate port number, then ssh has to honor that directive.

Like this:

```

Host easyToRememberName
        HostName FQDN
        User your.username.here
        Port xxxx

```

---

### Post by Kareeser on 2009-06-11
Worked like a charm. Thanks!

---

