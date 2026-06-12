---
title: "Apache2 Missing commands after aptitude install"
date: 2016-12-29
forum: Server Platforms
---

### Post by Pandee on 2016-12-29
Hello!

So I fixed my broken packages and installed apache2 via aptitude. However I come across a new issue.


When i attempt to start apache2 in numerous ways it keeps saying that..

command not found
apache2ctl: command not found
 Unknown job: apache2
/etc/init.d/apache2: command not found

Just to name a few.

Where did I go wrong? 

Many thanks.

---

### Post by Pandee on 2016-12-30
I have attempted a purge and removal - and when i start again from scratch i get:

```
ERROR: Config file dir.conf not properly enabled: /etc/apache2/mods-enabled/dir.conf is a real file, not touching it
dpkg: error processing package apache2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apache2-doc (2.4.7-1ubuntu4.13) ...
apache2_invoke: Enable configuration apache2-doc
Action 'configtest' failed.
The Apache error log may have more information.
apache2_reload: Your configuration is broken. Not reloading Apache 2
Setting up apache2-utils (2.4.7-1ubuntu4.13) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Errors were encountered while processing:
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by cariboo on 2016-12-30
First before removing apache, make sure it isn't running pre 16.04 use:

```
sudo service apache2 stop
```

16.04 and later:

```
systemctl stop apache2.service
```

Once apache is stopped remove it:

```
sudo apt-get purge apache2
```

make sure that /etc/apache2 is empty, then remove it.

You should be able to install apache2 now.

I'd suggest you have a look at the [Ubuntu Server guide]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf").

---

### Post by Pandee on 2016-12-30
Hello Cariboo! Thank you so much! Now i have it installed it has one last error:

```
 (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
 *
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems
invoke-rc.d: initscript apache2, action "start" failed.
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...


```

Does this mean that port 80 is being used right now? Do i simply find out what and kill the process and attempt a restart?

---

### Post by cariboo on 2016-12-30
A quick way to see which ports are in use, is to install nmap, and then run the following command:

```
nmap localhost
```

On my server the output looks like this:

```
nmap localhost

Starting Nmap 7.01 ( https://nmap.org ) at 2016-12-30 09:46 PST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000095s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
3306/tcp open  mysql
8000/tcp open  http-alt
8080/tcp open  http-proxy
```

---

### Post by SeijiSensei on 2016-12-30
Is this your first experience with 16.04 and specifically systemd?

Systemd uses different commands from earlier Linux versions to manage daemons.  To start Apache on 16.04 use
```
sudo systemctl start apache2.service
```
Other options besides "start" include stop, restart, and status.  See "man systemctl" for details.

---

