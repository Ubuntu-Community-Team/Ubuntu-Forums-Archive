---
title: "[SOLVED] I think SAMBA has me beat :("
date: 2008-07-02
forum: Server Platforms
---

### Post by SJI on 2008-07-02
Hello everyone,

I've been trying to get an 8.04 server to offer a drive up as a public, read-only SAMBA share without prompting for a user name on windows clients.

I've read lord knows how many posts/sites saying set security = share and define your share with these: 
public = yes
read only = yes
available = yes
browseable = yes
guest ok = yes

And you're pretty much done.

No matter what I try I'm always prompted with x.x.x.x/guest and then with Software is not accessible. You might not have permission...

My smb.conf is:
[global]
        server string = %h server (Samba, Ubuntu)
        interfaces = 127.0.0.0/8, eth1
        bind interfaces only = Yes
        security = SHARE
        map to guest = Bad User
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts host wins bcast
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j


And my share definition is:
[Share]
        comment = old stuff
        path = /mnt/store1/test
        public = yes
        read only = yes
        available = yes
        browseable = yes
        guest ok = yes
        

/dev/sda1 is mounted under /mnt/store1 and test is a directory in the root of the drive.

ls -alh /mnt/store1 returns:
drwxrwxrwx  2 root root 4.0K 2008-07-02 04:36 test

Many thanks,

Stephen

---

### Post by windependence on 2008-07-02
I could be wrong on this but it looks like it is only allowing access on the local machine:

```
interfaces = 127.0.0.0/8, eth1
```

-Tim

---

### Post by SJI on 2008-07-02
It's currently running on eth1 (192.168.0.250) and the loopback IF.

I've tried it with that restriction omitted and allowed it to bind to all interfaces, it makes no difference to its operation.

Stephen

---

### Post by promodus on 2008-07-02
I tried your configuration and only changed the path to the [share]... it works.

What version of samba are you using? 

What do you get when you run
```
smbstatus
``` 
From your server after restarting the samba service.

---

### Post by SJI on 2008-07-02
Output from smbstatus:

Samba version 3.0.28a
PID     Username      Group         Machine
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files


I also get these entries in the log.x.x.x.x file of the machine trying to connect:

smbd/service.c:make_connection_snum(1003)
  '/mnt/store1/test' does not exist or permission denied when connecting to [Software] Error was Permission denied

Stephen

---

### Post by promodus on 2008-07-02
Can you return the output from ```
mount
```

My other suggestion would be to comment
```
unix password sync = Yes
```

and restart the server.

---

### Post by SJI on 2008-07-02
Output from mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /mnt/store1 type ext3 (rw)


Commenting the unix password sync = Yes line has no effect.

Stephen

---

### Post by windependence on 2008-07-02
OK a few things to check.

Does the samba user exist on the other box? It must be the same user (case sensitive) and the same password on both boxes.

Does /mnt/store1/test exist and is it mounted?

Try chmodding the /mnt/store1/test directory to 775.

See if any of that makes a difference.

-Tim

---

### Post by SJI on 2008-07-02
Update:

I've just created a share on hda1 using the same settings as the original share on sda1.  That works fine, so my problem is isolated to sda1.

Stephen

---

### Post by SJI on 2008-07-02
> **windependence said:**
> OK a few things to check.

Does the samba user exist on the other box? It must be the same user (case sensitive) and the same password on both boxes.

I'm trying to create a public share whereby no user is required.
Do I need to create a user for this?

> **windependence said:**
> 
Does /mnt/store1/test exist and is it mounted?

Yes. I've just posted the output of mount command.

> **windependence said:**
> 
Try chmodding the /mnt/store1/test directory to 775.

See if any of that makes a difference.

/mnt/store1/test was 777. Chmod to 775 and restart samba has had no effect. 


Stephen

---

### Post by promodus on 2008-07-02
> 
Does the samba user exist on the other box? It must be the same user (case sensitive) and the same password on both boxes.


With Security set to share and guest ok set to yes I don't think this makes a difference.

---

### Post by windependence on 2008-07-02
> **promodus said:**
> With Security set to share and guest ok set to yes I don't think this makes a difference.

You're probably right. I'm definitely not a samba expert by any means. I have one samba box in the house, and I don't ever mess with it. It just works. :)

-Tim

---

### Post by SJI on 2008-07-02
It seems there was something awry with /mnt.

I unmounted the drive /dev/sda1 removed /mnt and it's contents.
Created a new /mnt and used chmod 755 /mnt on it.
Recreated the directory store1 and used chmod 777 /mnt/store1 on that.

Restarted SAMBA and i can see the test files i have stored.

Thank you everyone who commented.

Stephen

---

