---
title: "Error: Are you root?"
date: 2014-02-06
forum: Server Platforms
---

### Post by JnPson on 2014-02-06
I repeatedly run into this problem when I use sudo.
```
sudo apt-get update ; apt-get dist-upgrade
.......
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,330 kB in 4s (525 kB/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), **are you root**?
```
Why doesn't sudo work for me? I am in sudoers list, because I use the account I created during installation.

For me to do upgrades I have to enable root.

---

### Post by steeldriver on 2014-02-06
BOTH command need sudo

```

sudo apt-get update ; **sudo** apt-get dist-upgrade

```

---

### Post by deadflowr on 2014-02-06
sudo works per command, you're running it as two separate commands.
add sudo to the second command.

---

### Post by JnPson on 2014-02-06
Haha what a relief. It works as a charm now. 
Thank you  guys.

---

