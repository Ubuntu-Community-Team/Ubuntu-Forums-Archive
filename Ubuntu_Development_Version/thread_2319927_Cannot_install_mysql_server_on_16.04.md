---
title: "Cannot install mysql server on 16.04"
date: 2016-04-08
forum: Ubuntu Development Version
---

### Post by garak on 2016-04-08
During upgrade from 14.04 to 16.04, I had an error on upgrading mysql.
So, I tried to remove mysql-server package and to re-install it, but I'm getting the following error

```

Configurazione di mysql-server-5.7 (5.7.11-0ubuntu5)...
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: errore nell'elaborare il pacchetto mysql-server-5.7 (--configure):
il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di mysql-server:
mysql-server dipende da mysql-server-5.7; comunque:
Il pacchetto mysql-server-5.7 non è ancora configurato.

dpkg: errore nell'elaborare il pacchetto mysql-server (--configure):
problemi con le dipendenze - lasciato non configurato
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
Si sono verificati degli errori nell'elaborazione:
mysql-server-5.7
mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

(sorry, some messages are in Italian, but I think that the most important ones are clear).

I tried "systemctl status mysql.service" and "journalctl -xe" commands, getting the following

```

apr 08 18:52:52 xps systemd[1]: Failed to start MySQL Community Server.
-- Subject: L'unità mysql.service è fallita
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- L'unità mysql.service è fallita.
-- 
-- Il risultato è failed.
apr 08 18:52:52 xps systemd[1]: mysql.service: Unit entered failed state.
apr 08 18:52:52 xps systemd[1]: mysql.service: Failed with result 'exit-code'.
apr 08 18:52:53 xps systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
apr 08 18:52:53 xps systemd[1]: Stopped MySQL Community Server.
-- Subject: L'unità mysql.service termina la fase di spegnimento
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- L'unità mysql.service ha terminato la fase di spegnimento.
apr 08 18:52:53 xps systemd[1]: Starting MySQL Community Server...
-- Subject: L'unità mysql.service inizia la fase di avvio
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- L'unità mysql.service ha iniziato la fase di avvio.
apr 08 18:52:55 xps systemd[1]: mysql.service: Main process exited, code=exited, status=1/FAILURE


```

---

### Post by crcarson on 2016-04-09
In my environment (WiFi connected server) I've needed to modify the /lib/systemd/system/mysql.service file.  The default process is to start this service after the "network" is up which is when the ethernet is available.  With a WiFi connected server this tries to start the mysqld before the WiFi is connected.  Change the line in mysql.service "After=network.target" to "After=network-online.target".

---

### Post by Doug S on 2016-04-09
mysql seems all messed up on my 16.04 server. It was a fresh install as of early March. It all happened with updates yesterday, although I was a bit behind on updates. I'll come back with more details, if and when I figure them out.

---

### Post by Doug S on 2016-04-15
> **Doug S said:**
> mysql seems all messed up on my 16.04 server. It was a fresh install as of early March. It all happened with updates yesterday, although I was a bit behind on updates. I'll come back with more details, if and when I figure them out.I think it was just that I updated at the wrong time, and now mysql does not even run of that computer. Since, I have updated two other 16.04 servers, and while mysql still runs on those servers, they both show mysql-server as a held back package (so it is staying on mysql-server 5.6.28-1ubuntu3, instead of going to 5.7). I'm nor sure how to get it to proceed with the held back package.

---

### Post by Doug S on 2016-04-18
> **Doug S said:**
> I think it was just that I updated at the wrong time, and now mysql does not even run of that computer. Since, I have updated two other 16.04 servers, and while mysql still runs on those servers, they both show mysql-server as a held back package (so it is staying on mysql-server 5.6.28-1ubuntu3, instead of going to 5.7). I'm nor sure how to get it to proceed with the held back package.I installed mysql again on all 3 servers and now have version 5.7. Everything seems fine.

---

### Post by wgarcia on 2016-04-18
In a fully updated xenial as of this morning, I noticed mysql-server was not running, and after investigating I saw that it was not even installed. mysql-server 5.6 seems to have been removed by a recent update. After doing

```
 sudo apt-get install mysql-server 
```

mysql-server 5.7 was installed and everything seems back to normal.

---

### Post by apos on 2016-04-26
You are not alone: 

* [https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279](https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279)

Also adressed in the XENIAL RELEASE NOTES the problem is already addressed and links to bug #1571865 :

* [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#MySQL_5.7](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#MySQL_5.7)

I did not get this to work until now on one of my machines yet !

---

### Post by Doug S on 2016-04-26
> **apos said:**
> You are not alone: 
* [https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279](https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1573279)
Also adressed in the XENIAL RELEASE NOTES the problem is already addressed and links to bug #1571865 :
* [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#MySQL_5.7](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#MySQL_5.7)
I did not get this to work until now on one of my machines yet !Thanks very much for your post. I added my 2 cents worth to the bug report.

---

### Post by ananthaprasad-ck on 2016-11-23
I had the standard MySQL installed in 14.04 Ubuntu. I upgraded the Ubuntu from 14.04 to 16.04 and found the MySQL failed to upgrade properly. I uninstalled mysql completely and re install I get this error Message as shown below. Please help me....................

Setting up mysql-server-5.7 (5.7.11-0ubuntu6) ...
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 112: /usr/share/mysql-common/configure-symlinks: No such file or directory
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for systemd (229-4ubuntu12) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2016-11-23
When dist-upgrading, you need first to deactivate external sources (like ppa) and downgrade to the genuine version. All the removed package have to be 'purged' (complete removal) to get rid of old configs/settings left behind by a simple 'remove'.

[http://askubuntu.com/questions/657091/whats-the-good-way-to-clean-up-the-system-and-is-bleachbit-safe-on-ubuntu-14](http://askubuntu.com/questions/657091/whats-the-good-way-to-clean-up-the-system-and-is-bleachbit-safe-on-ubuntu-14)

---

