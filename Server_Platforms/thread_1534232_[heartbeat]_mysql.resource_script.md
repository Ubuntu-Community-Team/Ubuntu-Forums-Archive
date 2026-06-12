---
title: "[heartbeat] mysql.resource script"
date: 2010-07-19
forum: Server Platforms
---

### Post by BOK on 2010-07-19
Since the update to Ubuntu 10.04 this mysql.resource file (/etc/ha.d/resource.d/mysql - see URL below) doesn't work anymore, since 10.04 is using "service" / "upstart-job"...

Original: [http://dev.mysql.com/doc/refman/5.1/en/ha-heartbeat-drbd.html](http://dev.mysql.com/doc/refman/5.1/en/ha-heartbeat-drbd.html)

Is it OK to change it into something like this instead?

```

start)
        #res=`/etc/init.d/mysql start`
        [COLOR="Red"]res=`/usr/sbin/service mysql start`[/COLOR]
        ret=$?
        ha_log $res
        exit $ret
        ;;
```

Or has anyone found the updated resource-script(s)? TIA!

---

### Post by richardjh on 2010-07-19
That should work fine.

Only caveat though is to check this file after updates to check it is not overwritten in future.

---

### Post by BOK on 2010-07-20
> **richardjh said:**
> That should work fine.

Only caveat though is to check this file after updates to check it is not overwritten in future.

Thanks. I'll give it a try this Thursday in a PRD-cluster.
AFAIK this specific file is not included in any package.

---

### Post by BOK on 2010-07-22
FYI - the above solution DOES NOT work!! :(

```

Jul 22 11:17:08 hostname ResourceManager[4420]: [4698]: info: Running /etc/ha.d/resource.d/mysql  stop
Jul 22 11:17:08 hostname ResourceManager[4420]: [4711]: ERROR: Return code 1 from /etc/ha.d/resource.d/mysql
Jul 22 11:17:09 hostname ResourceManager[4420]: [4715]: info: Retrying failed stop operation [mysql]
Jul 22 11:17:09 hostname ResourceManager[4420]: [4725]: info: Running /etc/ha.d/resource.d/mysql  stop
Jul 22 11:17:09 hostname ResourceManager[4420]: [4738]: ERROR: Return code 1 from /etc/ha.d/resource.d/mysql
Jul 22 11:17:09 hostname ResourceManager[4420]: [4755]: ERROR: Resource script for mysql probably not LSB-compliant.
Jul 22 11:17:09 hostname ResourceManager[4420]: [4757]: WARN: it (mysql) MUST succeed on a stop when already stopped
Jul 22 11:17:09 hostname ResourceManager[4420]: [4759]: WARN: Machine reboot narrowly avoided!
Jul 22 11:17:09 hostname ResourceManager[4420]: [4774]: info: Running /etc/ha.d/resource.d/Filesystem /dev/drbd0 /var/lib/mysql ext4 stop
```

Now looking into replacing the upstart-script with an "old" init.d-script.

---

