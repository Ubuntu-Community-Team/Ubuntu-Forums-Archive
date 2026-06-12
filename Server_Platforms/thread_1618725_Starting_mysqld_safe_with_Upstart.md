---
title: "Starting mysqld_safe with Upstart"
date: 2010-11-11
forum: Server Platforms
---

### Post by epitom3 on 2010-11-11
I'm new to Upstart and I've tried to read through the documentation so I can start mysqld_safe instead of mysqld at startup, but can't seem to get it to work.

From what I've read, it appears that the *respawn * stanza in /etc/init/mysql.conf would give me the restart option if the daemon crashes, but I want to make sure other safety features of mysqld_safe are present as well.

My /etc/init/mysql.conf is the original. I've tried changing the *exec* stanza from /usr/sbin/mysqld to /usr/sbin/mysqld_safe but the job fails when I *sudo service mysql start*.

mysql.conf
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems
	  and runlevel [2345])
stop on runlevel [016]

respawn

env HOME=/etc/mysql
umask 007

pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    # Load AppArmor profile
    if aa-status --enabled 2>/dev/null; then
        apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld || true
    fi
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script

exec /usr/sbin/mysqld

post-start script
    for i in `seq 1 30` ; do
        /usr/bin/mysqladmin --defaults-file="${HOME}"/debian.cnf ping && {
            exec "${HOME}"/debian-start
            # should not reach this line
            exit 2
        }
        sleep 1
    done
    exit 1
end script


```

What changes do I need to make to fire mysqld_safe instead of mysqld?

Thanks in advance!

---

### Post by drakethegreat on 2011-05-04
I found that running it in pre-start works best and then explicitly sending the stop in post-stop. Something similar to how ufw works. My theory is that upstart has issues with detecting success if you just call it during the normal start state because it's expecting 1 pid and is instead getting back 2 or more and thinks the start failed so it attempts the restart (since you specific restart). Even if you turn off the restart command you will find that upstart can't figure out the job was successful. 

With that said, this is what I have:

```
description     "MySQL Server"
author          "Jonathan Drake"

start on local-filesystems
stop on runlevel [!2345]

pre-start script
        # Sanity Checks
        [ -r /etc/mysql/my.cnf ]
        [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld

        # Load AppArmor Profile
        if aa-status --enabled 2>/dev/null; then
                apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld || true
        fi

        /usr/bin/mysqld_multi --silent start
end script

post-stop exec /usr/bin/mysqld_multi stop
```

Feel free to modify it if you find issues but it's a much better setup for handling mysqld_safe then the one you have.

---

