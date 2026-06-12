---
title: "/home will not automount but will manually, mysql bind address"
date: 2009-11-10
forum: Server Platforms
---

### Post by pksings on 2009-11-10
Hello all, I have an nvidia RAID, two drives mirrored. /dev/mapper/nbdiasdsomething,, 

The machine refuses to automount /home since the upgrade this morning to Karmic.

mount -a works fine.

Any suggestions are welcome, I'm stumped on this one.


My second issue is the Mysql will not bind to the IP address of the machine, it works fine on localhost, I need it to work on the IP address for Mythtv. Mysql-admin connects just fine on 127.0.0.1 but not on my IP.

I commented out the "Bind=127.0.0.1" line in my.cnf and it makes no difference.

Again, any ideas are welcome, 2 hours on it and I Still have no idea what is wrong.

Thank you very much..

PK

---

### Post by cariboo on 2009-11-10
What does /etc/fstab look like?

Mysql needs to bind to an interface, you could try adding the computers ip address instead of 127.0.0.1 or you could create a user that is allowed to connect remotely start up the mysql console:

```
mysql -u root -p
```

use the password you setup when you installed mysql. Next add the new user:

```
mysql>CREATE USER 'monty'@'localhost' IDENTIFIED BY 'some_pass';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost'
    ->     WITH GRANT OPTION;

mysql>CREATE USER 'monty'@'%' IDENTIFIED BY 'some_pass';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%'
    ->     WITH GRANT OPTION;

```

Add your own user and password, and use that user in MythTV.

---

### Post by pksings on 2009-11-11
Thanks for your help.

First. /etc/fstab.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/nvidia_fdbjceaf2 during installation
UUID=caf4fbb6-6eb4-4b84-9ed8-252fe248635c /               reiserfs relatime        0       1
# /boot was on /dev/mapper/nvidia_fdbjceaf1 during installation
UUID=f5b6919e-1f2e-4dda-8d97-884decad02bd /boot           reiserfs notail,relatime 0       2
# /home was on /dev/mapper/nvidia_fdbjceaf4 during installation
UUID=a96d2b4f-af43-4aee-9646-a9750eae39c8 /home           reiserfs relatime        0       2
/dev/mapper/nvidia_fdbjceaf3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


Second, Mysql.

I have alternate users configured in Mysql already for another purpose and I cannot connect with any username on 192.168.1.155. I also did put the IP of the eth0 interface in /etc/mysql/my.cnf, and I could still only connect to Mysql using 127.0.0.1. The outside IP is 192.168.1.155 so I had
the following. 

# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
bind-adddres            = 192.168.1.155

It has been tried with both addresses uncommented, with the 127.0.0.1 address commented out and with both addresses commented out.


Thanks again for your help.

PK

---

### Post by pksings on 2009-11-12
Never Mind, tonight's updates fixed both problems.

Thanks for your help.

PK:KS

---

