---
title: "SNAP not working?"
date: 2018-12-20
forum: Ubuntu Cloud and Juju
---

### Post by khbkhb on 2018-12-20
Following [https://docs.maas.io/2.3/en/installconfig-snap-install](https://docs.maas.io/2.3/en/installconfig-snap-install) on 16.05.5. The install appeared ok, the status plausible (although some migrations failed) but the GUI is stuck with the message "MAAS is starting". This seems odd, in that I've installed in other VMs before without this issue. But it seems repeatable now. I'd even upgraded VirtualBox to 6 to see if that changed things ... but it doesn't.


 sudo snap install --devmode --stable maas
2018-12-20T13:02:20-07:00 INFO Waiting for restart...
maas 2.3.3-6498-ge4db91d-snap from 'canonical' installed
khb@kvbox:~$ sudo maas init --mode all
MAAS URL [default=http://10.0.2.15:5240/MAAS]:
Failed to perfom migrations:ations
Operations to perform:
  Synchronize unmigrated apps: staticfiles, messages
  Apply all migrations: contenttypes, sessions, piston3, maasserver, auth, metadataserver, sites
Synchronizing apps without migrations:
  Creating tables...
    Running deferred SQL...
  Installing custom SQL...
Running migrations:
  Rendering model states...


                                  khb@kvbox:~$ sudo maas config
[sudo] password for khb:
Mode: all
Settings:
maas_url=http://10.0.2.15:5240/MAAS
khb@kvbox:~$ sudo maas status
bind9                            RUNNING   pid 23684, uptime 0:29:59
dhcpd                            STOPPED   Not started
dhcpd6                           STOPPED   Not started
ntp                              RUNNING   pid 23686, uptime 0:29:59
postgresql                       RUNNING   pid 23689, uptime 0:29:59
proxy                            STOPPED   Not started
rackd                            RUNNING   pid 23685, uptime 0:29:59
regiond:regiond-0                RUNNING   pid 23679, uptime 0:29:59
regiond:regiond-1                RUNNING   pid 23682, uptime 0:29:59
regiond:regiond-2                RUNNING   pid 23681, uptime 0:29:59
regiond:regiond-3                RUNNING   pid 23680, uptime 0:29:59
tgt                              FATAL     Exited too quickly (process log may have details)
khb@kvbox:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial
khb@kvbox:~$

HOST OS: Mac OS X 10.14.2
VirtualBox: 6.0.0 r127566 (Qt5.6.3)

---

### Post by khbkhb on 2018-12-21
FWIW, same with Bionic 18.04.1Note that the initial login to the GUI (to establish the admin ) isn't happening.Trying the CLI, note the "does not exist" error .. sudo maas createadmin --username=khb  --email=khbkhb@gmail.omPassword: Again: Import SSH keys [] (lp:user-id or gh:user-id): usage: maas [-h] COMMAND ...optional arguments:  -h, --help      show this help message and exit.....relation "auth_user" does not existLINE 1: INSERT INTO "auth_user" ("password", "last_login", "is_super...===

---

