---
title: "update_security_db.sh fails on landscape 23.03 with Expecting value: line 1 column 1"
date: 2023-03-15
forum: Ubuntu Development Version
---

### Post by scahartner on 2023-03-15
Our Landscape on prem setup reports that the update_security_db.sh  fails consistently. 

Running the command manually 
```

sudo -u landscape bash -x /opt/canonical/landscape/scripts/update_security_db.sh

```

Results in the following error

```

+ . /opt/canonical/landscape/scripts/landscape-env.sh
++ ROOTDIR=/opt/canonical
++ export PYTHONPATH
++ export STORM_CEXTENSIONS=1
++ STORM_CEXTENSIONS=1
++ export LANDSCAPE_CONFIG=standalone
++ LANDSCAPE_CONFIG=standalone
++ export LANG=C
++ LANG=C
++ export TZ=UTC
++ TZ=UTC
++ PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
++ PYTHON=/usr/bin/python3
++ LSROOT=/opt/canonical/landscape
++ LSUSER=landscape
++ DESC='Landscape standalone'
++ DEFAULTS_FILE=/etc/default/landscape-server
++ ENVIRONMENT_FILE=/etc/environment
++ '[' -f /etc/environment ']'
++ . /etc/environment
+++ PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
++ export http_proxy https_proxy no_proxy
++ export HTTP_PROXY HTTPS_PROXY NO_PROXY
++ SERVICE_CONF_FILE=/etc/landscape/service.conf
++ '[' -r /etc/landscape/service.conf ']'
+++ awk -F '[\t ]*=[\t ]*' '/^syslog-address/ { print $2; };' /etc/landscape/service.conf
++ SYSLOG_ADDRESS=/dev/log
++ PIDDIR=/var/run/landscape
++ LOCKDIR=/var/lock
++ MAINTENANCE_FILE=/opt/canonical/landscape/maintenance.txt
++ background=
++ '[' -f /etc/default/landscape-server ']'
++ . /etc/default/landscape-server
+++ RUN_ALL=yes
+++ RUN_APPSERVER=no
+++ RUN_ASYNC_FRONTEND=no
+++ RUN_JOBHANDLER=no
+++ RUN_MSGSERVER=no
+++ RUN_PINGSERVER=no
+++ RUN_APISERVER=no
+++ RUN_PACKAGEUPLOADSERVER=no
+++ RUN_JUJU_SYNC=no
+++ RUN_PACKAGESEARCH=no
+++ RUN_CRON=yes
+++ UPGRADE_SCHEMA=yes
++ . /lib/lsb/init-functions
++++ run-parts --lsbsysinit --list /lib/lsb/init-functions.d
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/00-verbose ']'
+++ . /lib/lsb/init-functions.d/00-verbose
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/40-systemd ']'
+++ . /lib/lsb/init-functions.d/40-systemd
++++ _use_systemctl=0
++++ '[' -d /run/systemd/system ']'
++++ '[' -n '' ']'
++++ '[' update_security_db.sh = init-d-script ']'
++++ '[' update_security_db.sh = '' ']'
++++ executable=/opt/canonical/landscape/scripts/update_security_db.sh
++++ argument=
++++ prog=update_security_db.sh
++++ service=update_security_db.service
+++++ systemctl -p LoadState --value show update_security_db.service
++++ state=not-found
++++ '[' not-found = masked ']'
++++ '[' 3155 -ne 1 ']'
++++ '[' -z '' ']'
++++ case $(readlink -f "$executable") in
+++++ readlink -f /opt/canonical/landscape/scripts/update_security_db.sh
++++ '[' 0 = 1 ']'
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/50-ubuntu-logging ']'
+++ . /lib/lsb/init-functions.d/50-ubuntu-logging
++++ LOG_DAEMON_MSG=
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/99-plymouth ']'
+++ . /lib/lsb/init-functions.d/99-plymouth
++++ plymouth --ping
++++ return
+++ FANCYTTY=
+++ '[' -e /etc/lsb-base-logging.sh ']'
+++ true
+ LOGGER_NAME=update-security-db
+ SCRIPT_NAME=update_security_db.sh
+ exit_if_not_running_cron
+ '[' yes = no -a yes = no ']'
+ exit_if_maintenance_mode update-security-db
+ '[' -f /opt/canonical/landscape/maintenance.txt ']'
+ load_proxy_config
++ /opt/canonical/landscape/get-proxy-config
+ eval export http_proxy=http://XXXX:3128 export https_proxy=http://XXXX:3128
++ export http_proxy=http://XXXX:3128 export https_proxy=http://XXXX:3128
++ http_proxy=http://XXXX:3128
++ https_proxy=http://XXXX:3128
+ OUTPUT_FILE=/var/lib/landscape/usndb.json.bz2
+ URL=https://usn.ubuntu.com/usn-db/database.json.bz2
+ LOCKFILE=/var/lock/update_security.lock
+ CONNECT_TIMEOUT=60
+ LOW_SPEED_LIMIT=1
+ SPEED_TIME=120
+ CURL_OPTIONS='-f -y 120 -Y 1 -L --max-redirs 10'
+ CURL_OPTIONS='-f -y 120 -Y 1 -L --max-redirs 10 --connect-timeout 60'
+ acquire_lock update_security_db.sh
+ get_distributed_lock update_security_db.sh
+ local command=/opt/canonical/landscape/get-distributed-lock
+ /opt/canonical/landscape/get-distributed-lock update_security_db.sh
+ trap 'release_lock update_security_db.sh; rm -f /var/lock/update_security.lock' EXIT
+ lockfile -r0 -l 5400 /var/lock/update_security.lock
+ '[' 0 -ne 0 ']'
+ sleep 316
++ curl -f -y 120 -Y 1 -L --max-redirs 10 --connect-timeout 60 --output /var/lib/landscape/usndb.json.bz2-new https://usn.ubuntu.com/usn-db/database.json.bz2
+ output='  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 27.3M  100 27.3M    0     0  39.0M      0 --:--:-- --:--:-- --:--:-- 38.9M'
+ '[' 0 -ne 0 ']'
+ mv -f /var/lib/landscape/usndb.json.bz2-new /var/lib/landscape/usndb.json.bz2
+ cd /opt/canonical/landscape
+ set -o pipefail
+ bzcat /var/lib/landscape/usndb.json.bz2
+ ./process-usns /dev/stdin
+ pipe_to_syslog update-security-db
+ tag=update-security-db
++ get_logger_arguments
++ echo /dev/log
++ grep -q :
++ '[' -n /dev/log ']'
++ '[' /dev/log '!=' /dev/log ']'
++ echo ''
+ args=
+ logger -s -p user.error -t update-security-db
<11>Mar 16 00:20:24 update-security-db: Traceback (most recent call last):
<11>Mar 16 00:21:11 update-security-db:   File "./process-usns", line 7, in <module>
<11>Mar 16 00:21:11 update-security-db:     canonical.landscape.scripts.usn.run()
<11>Mar 16 00:21:11 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts/batch.py", line 84, in __call__
<11>Mar 16 00:21:11 update-security-db:     code = self.run()
<11>Mar 16 00:21:11 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts/usn.py", line 37, in run
<11>Mar 16 00:21:11 update-security-db:     changeset = update_from_usn_tool_db(db)
<11>Mar 16 00:21:11 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/usn.py", line 274, in update_from_usn_tool_db
<11>Mar 16 00:21:11 update-security-db:     search_client.update_usns(
<11>Mar 16 00:21:11 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 40, in query
<11>Mar 16 00:21:11 update-security-db:     return self._query(method, params)
<11>Mar 16 00:21:11 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 62, in _query
<11>Mar 16 00:21:11 update-security-db:     raise PackageSearchRequestError(loads(error.body)["Error"])
<11>Mar 16 00:21:11 update-security-db:   File "/usr/lib/python3.8/json/__init__.py", line 357, in loads
<11>Mar 16 00:21:11 update-security-db:     return _default_decoder.decode(s)
<11>Mar 16 00:21:11 update-security-db:   File "/usr/lib/python3.8/json/decoder.py", line 337, in decode
<11>Mar 16 00:21:11 update-security-db:     obj, end = self.raw_decode(s, idx=_w(s, 0).end())
<11>Mar 16 00:21:11 update-security-db:   File "/usr/lib/python3.8/json/decoder.py", line 355, in raw_decode
<11>Mar 16 00:21:11 update-security-db:     raise JSONDecodeError("Expecting value", s, err.value) from None
<11>Mar 16 00:21:11 update-security-db: json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)
+ '[' 1 -ne 0 ']'
+ alert_admin update_security_db.sh
+ echo 'Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0'
Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0
+ echo 'Check out the syslog output for script update_security_db.sh.'
Check out the syslog output for script update_security_db.sh.
+ exit 1
+ release_lock update_security_db.sh
+ get_distributed_lock update_security_db.sh --release
+ local command=/opt/canonical/landscape/get-distributed-lock
+ /opt/canonical/landscape/get-distributed-lock update_security_db.sh --release
+ rm -f /var/lock/update_security.lock


```

---

### Post by MAFoElffen on 2023-03-15
<<Thread should be moved to https://ubuntuforums.org/forumdisplay.php?f=427>>

Ubuntu 23.04 Lunar Lobster is still in beta, and not release yet. Is still a Development Release.

Next... AFAIK, as I just posted about this in another thread, about adding Landscape for Ubuntu Server Edition 22.04 LTS ([https://ubuntuforums.org/showthread.php?t=2484928&p=14134877#post14134877](https://ubuntuforums.org/showthread.php?t=2484928&p=14134877#post14134877)), Landscape is still in beta for 18.04 and will not be released for 20.04 and 22.04 until Q1 2023... I know that announcement said sometime about what should be now, but I haven't seen the official release notes on that "yet". So not for 23.04 at all (yet). 

Do you have "Paid Landscape Support." You said "premium"... Landscape is usually supported just for LTS releases. What does the Landscape Support Team say about supporting 23.04? If you do have paid Landscape Support, then you have 24/7 phone support: [https://ubuntu.com/support/contact-us](https://ubuntu.com/support/contact-us)

More information is really needed on what you are trying to do.

---

### Post by scahartner on 2023-03-15
We are currently doing a POC for Landscape on premises and as you pointed out are using the BETA. Just wondered if anyone has any insight into this issue. 

If all else fails, I will reach out via the support channel.

Thanks for taking a look

---

### Post by MAFoElffen on 2023-03-15
Tracing through the log, I see this:
```

+++++ [COLOR=#ff0000]systemctl -p LoadState --value show update_security_db.service[/COLOR]
++++ [COLOR=#ff0000]state=not-found[/COLOR]
++++ '[[COLOR=#ff0000]' not-found = masked '[/COLOR]]'
++++ '[' 3155 -ne 1 ']'
++++ '[' -z '' ']'
++++ case $(readlink -f "$executable") in

```
For example, on my server:
```

mafoelffen@Mikes-B460M:~$ systemctl -p LoadState --value show systemd-networkd.service
loaded
mafoelffen@Mikes-B460M:~$ systemctl -p LoadState --value show rc.service
masked

```
I would look at the output of
```

sudo systemctl status update_security_db.service

```
If it is 'masked', you should be able to unmask it via
```

sudo systemctl unmask update_security_db.service
sudo systemctl enable update_security_db.service
sudo systemctl start update_security_db.service
sudo systemctl status update_security_db.service

```
If for some reason the first command comes back with an error on unmasking it, that would mean that the symlink at '/lib/systemd/system/update_security_db.service' is pointing to a missing service file in '/etc/systemd/system/'...

And if you checked
```

file /lib/systemd/system/update_security_db.service

```
Then it might say something like
```

/lib/systemd/system/update_security_db.service: symbolic link to /dev/null

```
That is what it is going to look like if it is masked... 

If
```

ls /etc/systemd/system/update_security_db.service

```
...returns null, then remove the symbolic link in '/lib/systemd/system/' and reinstall Landscape to make sure that service file is installed in /etc/systemd/system/

That is just from what i see there. I hope that helps.

---

### Post by DuckHook on 2023-03-15
*Thread moved to **Ubuntu Development Version** as the more appropriate forum.*

---

### Post by scahartner on 2023-03-16
Thanks for these steps.

```

root@dc0b-landscape:/home/scadmin# systemctl status update_security_db.service
Unit update_security_db.service could not be found.
root@dc0b-landscape:/home/scadmin# file /lib/systemd/system/update_security_db.service
/lib/systemd/system/update_security_db.service: cannot open `/lib/systemd/system/update_security_db.service' (No such file or direc
```

I then reinstalled landscape-server

```

root@dc0b-landscape:/home/scadmin# apt install landscape-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
landscape-server is already the newest version (23.03+1-0landscape0).
landscape-server set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
root@dc0b-landscape:/home/scadmin# apt reinstall landscape-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 27 not upgraded.
Need to get 0 B/12.0 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 133696 files and directories currently installed.)
Preparing to unpack .../landscape-server_23.03+1-0landscape0_amd64.deb ...
Unpacking landscape-server (23.03+1-0landscape0) over (23.03+1-0landscape0) ...
Setting up landscape-server (23.03+1-0landscape0) ...
========================================================================
Attempting schema upgrade as requested.
WARNING: this could take several minutes or more.
========================================================================
2023-03-16 21:49:08.001Z INFO landscape-setup "Bootstrapping from service.conf file ..."
2023-03-16 21:49:08.120Z INFO landscape-setup "Skipping configuration migration ..."
2023-03-16 21:49:08.121Z INFO landscape-setup "Checking Landscape databases ..."
2023-03-16 21:49:08.135Z INFO landscape-setup "Checking database schema ..."
2023-03-16 21:49:09.331Z INFO landscape-setup "Schema configuration output:\n\nLoading site configuration...\nW
ARNING: PostgreSQL has max_prepared_transactions set to 0, not using two-phase commit.\nSetting up database sch
emas (will timeout after 86400 seconds) ...\nSchema patch version: 483\n"
2023-03-16 21:49:09.331Z INFO landscape-setup "Checking package database initial data ..."
2023-03-16 21:49:09.357Z INFO landscape-setup "Package database already initialized."
2023-03-16 21:49:09.358Z INFO landscape-setup "Renaming stock hash-id stores ..."
2023-03-16 21:49:09.360Z INFO landscape-setup "Stock package database not loaded, ignoring stock hash-id stores
."
Processing triggers for systemd (245.4-4ubuntu3.20) ...
Processing triggers for rsyslog (8.2001.0-1ubuntu1.3) ...

```

However this did not resolve the problem.
```

root@dc0b-landscape:/home/scadmin# file /lib/systemd/system/update_security_db.service
/lib/systemd/system/update_security_db.service: cannot open `/lib/systemd/system/update_security_db.service' (No such file or directory)

```


Do you know what package provides this file ?

```

root@dc0b-landscape:/home/scadmin# dpkg -S /lib/systemd/system/update_security_db.service
dpkg-query: no path found matching pattern /lib/systemd/system/update_security_db.service

root@dc0b-landscape:/lib/systemd/system# apt-file find /lib/systemd/system |grep landscape
landscape-client: /lib/systemd/system/landscape-client.service

```

---

### Post by lorenzomaurizi on 2023-09-05
I have the very same problem.
In other posts I saw that this problem may arise if Landscape is installed while the server has a certain hostname, then it's changed.
My first installation was done in this way, and experienced this problem right away.
So I deleted the VM and started from scratch, setting the correct hostname since the installation of Ubuntu 22.04.

Then it seemed to work correctly, but today, after applying some updates to the Landscape server and after rebooting the server, this problem came again.

THis is what comes from a manual run of the script with 
```
sudo -u landscape bash -x /opt/canonical/landscape/scripts/update_security_db.sh
```

```

+ . /opt/canonical/landscape/scripts/landscape-env.sh
++ ROOTDIR=/opt/canonical
++ export PYTHONPATH
++ export STORM_CEXTENSIONS=1
++ STORM_CEXTENSIONS=1
++ export LANDSCAPE_CONFIG=standalone
++ LANDSCAPE_CONFIG=standalone
++ export LANG=C
++ LANG=C
++ export TZ=UTC
++ TZ=UTC
++ PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
++ PYTHON=/usr/bin/python3
++ LSROOT=/opt/canonical/landscape
++ LSUSER=landscape
++ DESC='Landscape standalone'
++ DEFAULTS_FILE=/etc/default/landscape-server
++ ENVIRONMENT_FILE=/etc/environment
++ '[' -f /etc/environment ']'
++ . /etc/environment
+++ PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
++ export http_proxy https_proxy no_proxy
++ export HTTP_PROXY HTTPS_PROXY NO_PROXY
++ SERVICE_CONF_FILE=/etc/landscape/service.conf
++ '[' -r /etc/landscape/service.conf ']'
+++ awk -F '[\t ]*=[\t ]*' '/^syslog-address/ { print $2; };' /etc/landscape/service.conf
++ SYSLOG_ADDRESS=/dev/log
++ PIDDIR=/var/run/landscape
++ LOCKDIR=/var/lock
++ MAINTENANCE_FILE=/opt/canonical/landscape/maintenance.txt
++ background=
++ '[' -f /etc/default/landscape-server ']'
++ . /etc/default/landscape-server
+++ RUN_ALL=yes
+++ RUN_APPSERVER=no
+++ RUN_ASYNC_FRONTEND=no
+++ RUN_JOBHANDLER=no
+++ RUN_MSGSERVER=no
+++ RUN_PINGSERVER=no
+++ RUN_APISERVER=no
+++ RUN_PACKAGEUPLOADSERVER=no
+++ RUN_JUJU_SYNC=no
+++ RUN_PACKAGESEARCH=no
+++ RUN_CRON=yes
+++ UPGRADE_SCHEMA=yes
++ . /lib/lsb/init-functions
++++ run-parts --lsbsysinit --list /lib/lsb/init-functions.d
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/00-verbose ']'
+++ . /lib/lsb/init-functions.d/00-verbose
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/40-systemd ']'
+++ . /lib/lsb/init-functions.d/40-systemd
++++ _use_systemctl=0
++++ '[' -d /run/systemd/system ']'
++++ '[' -n '' ']'
++++ '[' update_security_db.sh = init-d-script ']'
++++ '[' update_security_db.sh = '' ']'
++++ executable=/opt/canonical/landscape/scripts/update_security_db.sh
++++ argument=
++++ prog=update_security_db.sh
++++ service=update_security_db.service
+++++ systemctl -p LoadState --value show update_security_db.service
++++ state=not-found
++++ '[' not-found = masked ']'
++++ '[' 79154 -ne 1 ']'
++++ '[' -z '' ']'
++++ case $(readlink -f "$executable") in
+++++ readlink -f /opt/canonical/landscape/scripts/update_security_db.sh
++++ '[' 0 = 1 ']'
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/50-ubuntu-logging ']'
+++ . /lib/lsb/init-functions.d/50-ubuntu-logging
++++ LOG_DAEMON_MSG=
+++ for hook in $(run-parts --lsbsysinit --list /lib/lsb/init-functions.d 2>/dev/null)
+++ '[' -r /lib/lsb/init-functions.d/99-plymouth ']'
+++ . /lib/lsb/init-functions.d/99-plymouth
++++ plymouth --ping
++++ return
+++ FANCYTTY=
+++ '[' -e /etc/lsb-base-logging.sh ']'
+++ true
+ LOGGER_NAME=update-security-db
+ SCRIPT_NAME=update_security_db.sh
+ exit_if_not_running_cron
+ '[' yes = no -a yes = no ']'
+ exit_if_maintenance_mode update-security-db
+ '[' -f /opt/canonical/landscape/maintenance.txt ']'
+ load_proxy_config
++ /opt/canonical/landscape/get-proxy-config
+ eval export http_proxy=http://proxyaddress:3128 export https_proxy=http://proxyaddress:3128 export 'no_proxy='\''*.localdomain'\'''
++ export http_proxy=http://proxyaddress:3128 export https_proxy=http://proxyaddress:3128 export 'no_proxy=*.localdomain'
++ http_proxy=http://proxyaddress:3128
++ https_proxy=http://proxyaddress:3128
++ no_proxy='*.localdomain'
+ OUTPUT_FILE=/var/lib/landscape/usndb.json.bz2
+ URL=https://usn.ubuntu.com/usn-db/database.json.bz2
+ LOCKFILE=/var/lock/update_security.lock
+ CONNECT_TIMEOUT=60
+ LOW_SPEED_LIMIT=1
+ SPEED_TIME=120
+ CURL_OPTIONS='-f -y 120 -Y 1 -L --max-redirs 10'
+ CURL_OPTIONS='-f -y 120 -Y 1 -L --max-redirs 10 --connect-timeout 60'
+ acquire_lock update_security_db.sh
+ get_distributed_lock update_security_db.sh
+ local command=/opt/canonical/landscape/get-distributed-lock
+ /opt/canonical/landscape/get-distributed-lock update_security_db.sh
+ trap 'release_lock update_security_db.sh; rm -f /var/lock/update_security.lock' EXIT
+ lockfile -r0 -l 5400 /var/lock/update_security.lock
+ '[' 0 -ne 0 ']'
+ sleep 513
++ curl -f -y 120 -Y 1 -L --max-redirs 10 --connect-timeout 60 --output /var/lib/landscape/usndb.json.bz2-new https://usn.ubuntu.com/usn-db/database.json.bz2
+ output='  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 29.5M  100 29.5M    0     0  29.6M      0 --:--:-- --:--:-- --:--:-- 29.6M'
+ '[' 0 -ne 0 ']'
+ mv -f /var/lib/landscape/usndb.json.bz2-new /var/lib/landscape/usndb.json.bz2
+ cd /opt/canonical/landscape
+ set -o pipefail
+ bzcat /var/lib/landscape/usndb.json.bz2
+ ./process-usns /dev/stdin
+ pipe_to_syslog update-security-db
+ tag=update-security-db
++ get_logger_arguments
++ echo /dev/log
++ grep -q :
++ '[' -n /dev/log ']'
++ '[' /dev/log '!=' /dev/log ']'
++ echo ''
+ args=
+ logger -s -p user.error -t update-security-db
<11>Sep  5 14:39:25 update-security-db: Traceback (most recent call last):
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/./process-usns", line 7, in <module>
<11>Sep  5 14:40:32 update-security-db:     canonical.landscape.scripts.usn.run()
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts/batch.py", line 84, in __call__
<11>Sep  5 14:40:32 update-security-db:     code = self.run()
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/scripts/usn.py", line 37, in run
<11>Sep  5 14:40:32 update-security-db:     changeset = update_from_usn_tool_db(db)
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/usn.py", line 274, in update_from_usn_tool_db
<11>Sep  5 14:40:32 update-security-db:     search_client.update_usns(
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 40, in query
<11>Sep  5 14:40:32 update-security-db:     return self._query(method, params)
<11>Sep  5 14:40:32 update-security-db:   File "/opt/canonical/landscape/canonical/landscape/model/package/client.py", line 62, in _query
<11>Sep  5 14:40:32 update-security-db:     raise PackageSearchRequestError(loads(error.body)["Error"])
<11>Sep  5 14:40:32 update-security-db:   File "/usr/lib/python3.10/json/__init__.py", line 346, in loads
<11>Sep  5 14:40:32 update-security-db:     return _default_decoder.decode(s)
<11>Sep  5 14:40:32 update-security-db:   File "/usr/lib/python3.10/json/decoder.py", line 337, in decode
<11>Sep  5 14:40:32 update-security-db:     obj, end = self.raw_decode(s, idx=_w(s, 0).end())
<11>Sep  5 14:40:32 update-security-db:   File "/usr/lib/python3.10/json/decoder.py", line 355, in raw_decode
<11>Sep  5 14:40:32 update-security-db:     raise JSONDecodeError("Expecting value", s, err.value) from None
<11>Sep  5 14:40:32 update-security-db: json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)
+ '[' 1 -ne 0 ']'
+ alert_admin update_security_db.sh
+ echo 'Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0'
Error running /opt/canonical/landscape/scripts/update_security_db.sh: 0
+ echo 'Check out the syslog output for script update_security_db.sh.'
Check out the syslog output for script update_security_db.sh.
+ exit 1
+ release_lock update_security_db.sh
+ get_distributed_lock update_security_db.sh --release
+ local command=/opt/canonical/landscape/get-distributed-lock
+ /opt/canonical/landscape/get-distributed-lock update_security_db.sh --release
+ rm -f /var/lock/update_security.lock

```

any idea?

Thanks in advance.
Lorenzo

---

### Post by lorenzomaurizi on 2023-09-07
To go further in the analysis, I can see that the file [COLOR=#000000][FONT=&quot]/var/lib/landscape/usndb.json.bz2[/FONT][/COLOR] is correctly downloaded and it contains what seems to be a correct JSON file, as the json_xs utility is able to print out the "beautified" form of the compressed form into the bz2 file.
I'll try to go deep in the python code, but it's a little too much for me.
Regards

---

### Post by lorenzomaurizi on 2023-09-07
After some digging into the python code, I can see that the part that is failing is the connection to the local search service "landscape-package-search-service" where it tries to compare the newly downloaded security list of packages to the list of current packages, file [COLOR=#000000][FONT=&amp]/opt/canonical/landscape/canonical/landscape/model/package/client.py[/FONT][/COLOR]

I noticed that in the /etc/hosts file there wasn't the complete FQDN of the Landscape server in the 127.0.1.1 row. I added the complete fqdn just after the hostname and **it worked**!!

```
127.0.1.1 landscape **landscape.localdomain**
```

where landscape is the hostname and landscape.localdomain is the complete fqdn of the landscape server.

Moreover, I think I had a bad proxy configuration.
I used the form *.localdomain in the "No Proxy for" Landscape configuration setting, that could be wrong. Now I put:

```
localhost,127.0.0.1,127.0.1.1,landscape.localdomain,.localdomain
```

At my end this problem is solved.
I hope this helps someone who falls in the same problem.

Regards
Lorenzo

---

