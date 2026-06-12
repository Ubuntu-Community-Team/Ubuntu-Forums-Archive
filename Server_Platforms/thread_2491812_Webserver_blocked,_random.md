---
title: "Webserver blocked, random"
date: 2023-10-21
forum: Server Platforms
---

### Post by WhiteTigerIT on 2023-10-21
I have a VPS with Ubuntu 22.04.3 LTS.
For a month now I have found it blocked in the entire web component: Joomla website and Roundcube webmail.
However, the mail system continues to work because I use it with Thunderbird, which doesn't even allow me to determine when the crash occurred.
The Acronis backup agent also seems to be working without any problems.


If I restart the server, it starts working completely again, but I find it blocked days later.


I thought there was a problem on MariaDB, but there are no error reports.
For example, the reports I found this morning (October 20th) seem to relate to the shutdown on the 17th.


The server has been active for months and only recently has it shown problems.
I thought about entering the reboot command after the backup is complete, but that would be a palliative.


Does anyone have an idea what might be causing it or how to debug it?

Thanks in advance for any help and advice.

---

### Post by LHammonds on 2023-10-22
You describe the issue as "blocked" but is that for a specific reason?  When you access the web sites, does the web browser say that?   If so, have you tried other web browsers?  There might be a plugin blocking the site.

I have not used Joomla or Roundcube.  Are there systemctl services you can check status on to see if they are running?   Is it on top of Apache or NGINX?  Look at all the components to see what is running and what isn't (if any).   If everything seems to be running, try adding a custom HTML file to the root of the website and see if you can pull that page up in a browser just to verify the web server can deliver a static page.  Then try dynamic pages (such as PHPInfo if using PHP)

LHammonds

---

### Post by WhiteTigerIT on 2023-10-25
> **LHammonds said:**
> You describe the issue as "blocked" but is that for a specific reason?  When you access the web sites, does the web browser say that?   If so, have you tried other web browsers?  There might be a plugin blocking the site.

I have not used Joomla or Roundcube.  Are there systemctl services you can check status on to see if they are running?   Is it on top of Apache or NGINX?  Look at all the components to see what is running and what isn't (if any).   If everything seems to be running, try adding a custom HTML file to the root of the website and see if you can pull that page up in a browser just to verify the web server can deliver a static page.  Then try dynamic pages (such as PHPInfo if using PHP)

This morning I found it still blocked.
There is a 500 error.

Both a php file with php info and an html page works.
There is a Nginx like Apache Reverse proxy and both are working.

It is MariaDB itself that crashes.

```
# systemctl status mariadb
× mariadb.service - MariaDB 10.6.12 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: failed (Result: oom-kill) since Mon 2023-10-23 15:18:27 CEST; 1 day 21h ago
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 1273 (code=killed, signal=KILL)
     Status: "Taking your SQL requests now..."
        CPU: 8min 5.286s


Oct 21 10:36:58 srv /etc/mysql/debian-start[2589]: Upgrading MySQL tables if necessary.
Oct 21 10:36:59 srv /etc/mysql/debian-start[2715]: Triggering myisam-recover for all MyISAM tables and aria-recover for all Aria tables
Oct 21 10:45:59 srv mariadbd[1273]: 2023-10-21 10:45:59 1194 [Warning] Aborted connection 1194 to db: 'psa' user: 'admin' host: 'localhost' (Got an error reading communication packets)
Oct 22 00:00:35 srv mariadbd[1273]: 2023-10-22  0:00:35 2217 [Note] InnoDB: Cannot close file ./cps@002dqs2/shlg5_extensions.ibd because of pending fsync
Oct 22 00:15:33 srv mariadbd[1273]: 2023-10-22  0:15:33 2705 [Warning] Aborted connection 2705 to db: 'psa' user: 'admin' host: 'localhost' (Got an error reading communication packets)
Oct 23 00:15:35 srv mariadbd[1273]: 2023-10-23  0:15:35 7006 [Warning] Aborted connection 7006 to db: 'psa' user: 'admin' host: 'localhost' (Got an error reading communication packets)
Oct 23 15:18:25 srv systemd[1]: mariadb.service: A process of this unit has been killed by the OOM killer.
Oct 23 15:18:27 srv systemd[1]: mariadb.service: Main process exited, code=killed, status=9/KILL
Oct 23 15:18:27 srv systemd[1]: mariadb.service: Failed with result 'oom-kill'.
Oct 23 15:18:27 srv systemd[1]: mariadb.service: Consumed 8min 5.286s CPU time.

```

---

