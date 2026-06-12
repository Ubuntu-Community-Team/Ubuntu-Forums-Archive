---
title: "Recovering Server - Which config files?"
date: 2009-11-04
forum: Server Platforms
---

### Post by zzzBrett on 2009-11-04
I attempted to upgrade my 9.04 server to 9.10 via ssh, and failed. So, I am getting a fresh install up and running this weekend, but would rather do minimal configuration.

My plan is to retrieve all of the config files from the server applications I use, including:

Apache
PHP5
Samba
MythTV
lirc
OpenSSH


What is the best way to get these services up and running again? For the applications with multiple config files, could I copy and paste the entire directory after installation?

Also, any other config files I might want to grab before deleting the partition?

Any help would be appreciated!

---

### Post by falconindy on 2009-11-04
The /etc/ directory contains all config files.

---

### Post by zzzBrett on 2009-11-04
So on my new install, would it be wise to create a separate partition for /etc?

---

### Post by falconindy on 2009-11-06
I wouldn't make a whole new partition just for /etc mainly because of its size. I've just checked my own and its barely 10mb. Just make sure you're including it in your regular backups. You **do** make backups, right?

---

### Post by R.Bucky on 2009-11-07
Assuming this is a Server edition and not a GUI box? Additional options may include:

BIND9
DHCP
and of course your server files and databases.

If you operate a GUI server, you might want to save your Firefox profile located in /home/<username>/.mozilla/firefox/.

---

