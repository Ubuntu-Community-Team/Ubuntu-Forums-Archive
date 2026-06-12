---
title: "mount points/partitions"
date: 2008-09-16
forum: Server Platforms
---

### Post by geoffDeGeoffGeoff on 2008-09-16
I have a server which is set up like this:
root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.6G  1.9G  2.6G  42% /
varrun                1.5G   48K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  124K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
/dev/sda8             449G  1.8G  425G   1% /home
/dev/sda7             4.6G  421M  4.0G  10% /var

Trouble is I need a whole lot more space on / (I am installing zimbra that must go in /opt/zimbra)
How can I shrink the space available to /home and give it to /.  Bear in mind I only have ssh access to this server so cannot use any live cds or graphical tools.

Thanks in advance,
Steve

---

### Post by cdenley on 2008-09-16
> **geoffDeGeoffGeoff said:**
> I have a server which is set up like this:
root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.6G  1.9G  2.6G  42% /
varrun                1.5G   48K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  124K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
/dev/sda8             449G  1.8G  425G   1% /home
/dev/sda7             4.6G  421M  4.0G  10% /var

Trouble is I need a whole lot more space on / (I am installing zimbra that must go in /opt/zimbra)
How can I shrink the space available to /home and give it to /.  Bear in mind I only have ssh access to this server so cannot use any live cds or graphical tools.

Thanks in advance,
Steve

I don't think it is possible to resize your root filesystem while it is mounted. Perhaps you could create a link to force zimbra to install on your /home partition (or wherever you want)?
```

sudo mkdir /home/zimbra
sudo ln -s /home/zimbra /opt/zimbra

```

---

