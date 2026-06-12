---
title: "Trying to install virtual box on my ubuntu 12.04 server"
date: 2013-03-30
forum: Virtualisation
---

### Post by molnar20 on 2013-03-30
This command 
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```
Gives me this:
```
mktemp: failed to create file via template `/tmp/tmp.XXXXXXXXXX': No such file or directory

```

---

### Post by sasbock on 2013-03-31
Make sure the "/tmp" directory exists and has the correct permissions:

$ sudo mkdir /tmp
$ sudo chmod 777 /tmp

---

