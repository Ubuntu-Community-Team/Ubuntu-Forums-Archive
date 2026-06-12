---
title: "apt-get update broken through regular update in dapper"
date: 2006-11-10
forum: Server Platforms
---

### Post by jsteidl on 2006-11-10
Hi there, i tried to solve this problem in various IRC-Sessions but always failed. So i decied to list all the necessary info here and try my luck again.

The System:
Ubuntu 6.06 "Dapper Drake"
Server Installation (Usage: Fileserver)

The Error:
When doing a 'sudo apt-get update' i get the following error (the systemlanguage is German and i dont know the exact words for the english version of the error)

```
jsteidl@hive:~$ sudo apt-get update
Password:
Fehl http://archive.ubuntu.com dapper Release.gpg
  Verbindung fehlgeschlagen [IP: 195.248.90.38 80]
Fehl http://security.ubuntu.com dapper-security Release.gpg                    
  Verbindung fehlgeschlagen
```

My first steps of action:
- Is the connection to the Internet working?
  -- Ping google.com worked
  -- wget [http://archive.ubuntu.com/](http://archive.ubuntu.com/) worked too
  -- Checked GPG-Keys

GPG-Keys:
```

jsteidl@hive:~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>


```

Okay, next step: sources.list. I had that one regenerated at [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to be sure it is not broken.

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
#deb http://de.archive.ubuntu.com/ubuntu dapper universe multiverse
#deb http://de.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
#deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

My Resume:
- Internet working
- GPG-Keys are in place
- sources.list is correct
- Untouched system, just the regular security-updates
- WTF?!?

Is there a way to clear this one out? Were there a broken update for apt-get? What did i miss? I could really need a hand here ...

---

### Post by jsteidl on 2006-11-12
i've dealed with this allready too long. i reinstalled the server. Problem sovled. Or Not. Depends on the view.

---

