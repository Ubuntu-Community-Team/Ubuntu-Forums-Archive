---
title: "MYSQL stopped and it can't be restart - ubuntu 16.04.05 LTS"
date: 2018-12-18
forum: Server Platforms
---

### Post by edicande0477 on 2018-12-18
Hi all,

Please help me which I'm stuck with mysql service, please your expert and I'm newbie to servers and thanks in advance.

"Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "Journalctl -xe" for details.

```
is@rwisapache2:~# tail -30 /var/log/mysql/error.log
2018-12-05T11:56:22.047595Z 0 [Note] Shutting down plugin &#8216;INNODB*FT*DELETED&#8217;
2018-12-05T11:56:22.047599Z 0 [Note] Shutting down plugin &#8216;INNODB*FT*DEFAULT[I]STO PWORD&#8217;
2018-12-05T11:56:22.047602Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]METRICS&#8217;
2018-12-05T11:56:22.047605Z 0 [Note] Shutting down plugin &#8216;INNODB*TEMP*TABLE[I]INF O&#8217;
2018-12-05T11:56:22.047608Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]BUFFER*POOL*ST ATS&#8217;
2018-12-05T11:56:22.047611Z 0 [Note] Shutting down plugin &#8216;INNODB*BUFFER*PAGE[I]LR U&#8217;
2018-12-05T11:56:22.047615Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]BUFFER[I]PAGE&#8217;
2018-12-05T11:56:22.047618Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]CMP*PER*INDEX_ RESET&#8217;
2018-12-05T11:56:22.047621Z 0 [Note] Shutting down plugin &#8216;INNODB*CMP*PER[I]INDEX&#8217;
2018-12-05T11:56:22.047625Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]CMPMEM[I]RESET&#8217;
2018-12-05T11:56:22.047628Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]CMPMEM&#8217;
2018-12-05T11:56:22.047649Z 0 [Note] Shutting down plugin &#8216;INNODB*CMP*RESET&#8217;
2018-12-05T11:56:22.047653Z 0 [Note] Shutting down plugin &#8216;INNODB[I]CMP&#8217;
2018-12-05T11:56:22.047656Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]LOCK[I]WAITS&#8217;
2018-12-05T11:56:22.047659Z 0 [Note] Shutting down plugin &#8216;INNODB[/I]LOCKS&#8217;
2018-12-05T11:56:22.047661Z 0 [Note] Shutting down plugin &#8216;INNODB[I]TRX&#8217;
2018-12-05T11:56:22.047664Z 0 [Note] Shutting down plugin &#8216;InnoDB&#8217;
2018-12-05T11:56:22.047855Z 0 [Note] InnoDB: FTS optimize thread exiting.
2018-12-05T11:56:22.048380Z 0 [Note] InnoDB: Starting shutdown&#8230;
2018-12-05T11:56:22.149021Z 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/ mysql/ib_[/I]buffer_[I]pool
2018-12-05T11:56:22.149466Z 0 [Note] InnoDB: Buffer pool(s) dump completed at 181205 11:56:22
2018-12-05T11:56:23.370580Z 0 [Note] InnoDB: Shutdown completed; log sequence nu mber 2674079
2018-12-05T11:56:23.372460Z 0 [Note] InnoDB: Removed temporary tablespace data f ile: &#8220;ibtmp1&#8221;
2018-12-05T11:56:23.372481Z 0 [Note] Shutting down plugin &#8216;MEMORY&#8217;
2018-12-05T11:56:23.372494Z 0 [Note] Shutting down plugin &#8216;CSV&#8217;
2018-12-05T11:56:23.372500Z 0 [Note] Shutting down plugin &#8216;sha256_[/I]password&#8217;
2018-12-05T11:56:23.372503Z 0 [Note] Shutting down plugin &#8216;mysql_*native_*password &#8216;
2018-12-05T11:56:23.372914Z 0 [Note] Shutting down plugin &#8216;binlog&#8217;
2018-12-05T11:56:23.373409Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
```


Please help....

---

### Post by slickymaster on 2018-12-18
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2018-12-18
The last 30 lines of that log is only showing the shutdown procedure...not the reason for why it was shutting down which is probably further up.

Might want to make sure you did not run out of space as well
```
df -h
```

Also, check what the journal log says which was stated in the command:

```
Journalctl -xe
```

LHammonds

---

### Post by edicande0477 on 2018-12-18
journalctl -xe:
(see attachment)
[ATTACH=CONFIG]281963[/ATTACH][ATTACH=CONFIG]281962[/ATTACH]

---

### Post by LHammonds on 2018-12-19
Looks like AppArmor is blocking it.  If you do not have a Linux admin that knows AppArmor, then you might want to just remove it.

```

/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown
update-rc.d -f apparmor remove
apt-get remove apparmor
```

Or modify AppArmor: [https://askubuntu.com/questions/916009/mysql-wont-start-because-of-apparmor](https://askubuntu.com/questions/916009/mysql-wont-start-because-of-apparmor)

---

### Post by edicande0477 on 2018-12-23
> **LHammonds said:**
> Looks like AppArmor is blocking it. If you do not have a Linux admin that knows AppArmor, then you might want to just remove it.

```

/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown
update-rc.d -f apparmor remove
apt-get remove apparmor
```

Or modify AppArmor: [https://askubuntu.com/questions/916009/mysql-wont-start-because-of-apparmor](https://askubuntu.com/questions/916009/mysql-wont-start-because-of-apparmor)

@LHammonds: Thanks for your help.
Finally, I uninstall and reinstall MYSQL follow this link:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

