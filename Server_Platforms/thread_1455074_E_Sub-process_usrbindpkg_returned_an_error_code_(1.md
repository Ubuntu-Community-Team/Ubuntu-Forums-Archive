---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-04-15
forum: Server Platforms
---

### Post by waloshin on 2010-04-15
When I type in sudo dpkg --configure -a 

phpmyadmin wants to setup, I enter my mysql database password and I get error 1045 (28000)

Password wrong for user root@localhost

Then I get next step:

abort
retry
retry (skip questions)
ignore

And when I go to click down I get:

General error mounting filesystem A maintenace shell will be started 

Control-D will terminate this shell and re-try

GIve password for maintenance (or type Control-D to continue. 

Then it just freezes and I have to restart!

---

### Post by cdenley on 2010-04-15
So you're installing phpmyadmin, you choose to configure your database with dbconfig, then when you are prompted for the root password for the mysql database, you enter the incorrect password. Well, if you forgot the root password for mysql, reset it:
```

sudo dpkg-reconfigure mysql-server-5.1

```

Then you lost me with "click down". Did you reboot when it failed to mount a filesystem? Also, posting the actual output for dpkg might be helpful.

---

### Post by waloshin on 2010-04-15
> **cdenley said:**
> So you're installing phpmyadmin, you choose to configure your database with dbconfig, then when you are prompted for the root password for the mysql database, you enter the incorrect password. Well, if you forgot the root password for mysql, reset it:
```

sudo dpkg-reconfigure mysql-server-5.1

```

Then you lost me with "click down". Did you reboot when it failed to mount a filesystem? Also, posting the actual output for dpkg might be helpful.

Havent forgot the root password, and yes i rebooted when it failed to mount the filesystem.

---

### Post by cdenley on 2010-04-15
> **waloshin said:**
> Havent forgot the root password, and yes i rebooted when it failed to mount the filesystem.

The root MYSQL password? This is separate from your system's root password. Are you sure you entered it correctly? Error 1045 indicates you did not. If you failed to mount a filesystem after a reboot, I doubt that has anything to do with dpkg, and belongs in a separate thread if it is a problem that still needs to be resolved.

---

### Post by waloshin on 2010-04-15
> **cdenley said:**
> The root MYSQL password? This is separate from your system's root password. Are you sure you entered it correctly? Error 1045 indicates you did not. If you failed to mount a filesystem after a reboot, I doubt that has anything to do with dpkg, and belongs in a separate thread if it is a problem that still needs to be resolved.

After cancelling the phpmyadmin installation the screen has red text on it saying that it failed to mount filesystem. 

And I have run dpkg --configure -a and ran the phpmyadmin and clicked cancel so now the dpkg error is gone.

---

