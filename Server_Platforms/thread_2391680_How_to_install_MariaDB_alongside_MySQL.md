---
title: "How to install MariaDB alongside MySQL"
date: 2018-05-12
forum: Server Platforms
---

### Post by mbnoimi on 2018-05-12
I want to install MariaDB alongside MySQL. Under Windows install it is very easy because it only needs to change the port. While under Ubuntu it's a different story.

I did the following steps for installation but I always get this error message through ** journalctl -xe** although **my.cnf** already exists and has a prober permissions!
```

mysqld[26621]: Could not open required defaults file: /opt/mariadb-data/my.cnf
mysqld[26621]: Fatal error in defaults handling. Program aborted
systemd[1]: mariadb.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: mariadb.service: Unit entered failed state.
systemd[1]: mariadb.service: Failed with result 'exit-code'.
systemd[1]: mariadb.service: Service hold-off time over, scheduling restart.
systemd[1]: Stopped MariaDB Database.
```

[list]Installation steps:[/list]

```
cd /opt
tar -zxvpf mariadb-10.2.14-linux-x86_64.tar.gz
ln -s mariadb-10.2.14-linux-x86_64 mariadb
mkdir mariadb-data
mkdir /opt/mariadb-data/tmp
groupadd --system mariadb
useradd -c "MariaDB Server" -d /opt/mariadb -g mariadb --system mariadb
cp my.cnf mariadb-data/my.cnf #see the content below
chown -R mariadb:mariadb mariadb-10.2.14-linux-x86_64/
chown -R mariadb:mariadb mariadb-data/
chmod -R 700 mariadb-data/
cd mariadb
scripts/mysql_install_db --user=mariadb --defaults-file=/opt/mariadb-data/my.cnf
cd ..
cp mariadb.service /etc/systemd/system/ #see the content below
systemctl daemon-reload
systemctl start mariadb.service
```

[list]Result of **systemctl status mariadb.service** is:[/list]

```
&#9679; mariadb.service - MariaDB Database
   Loaded: loaded (/etc/systemd/system/mariadb.service; static; vendor preset: enabled)
  Drop-In: /etc/systemd/system/mariadb.service.d
           &#9492;&#9472;migrated-from-my.cnf-settings.conf
   Active: inactive (dead)

systemd[1]: mariadb.service: Service hold-off time over, scheduling restart.
systemd[1]: Stopped MariaDB Database.
systemd[1]: Started MariaDB Database.
systemd[1]: mariadb.service: Main process exited, code=exited, status=1/FAILURE
systemd[1]: mariadb.service: Unit entered failed state.
systemd[1]: mariadb.service: Failed with result 'exit-code'.
systemd[1]: mariadb.service: Service hold-off time over, scheduling restart.
systemd[1]: Stopped MariaDB Database.
systemd[1]: mariadb.service: Start request repeated too quickly.
systemd[1]: Failed to start MariaDB Database.
```

[list]Result of **/opt/mariadb/bin/mysqld_safe --user=mariadb --ledir=/opt/mariadb/bin** is:[/list]

```
# /opt/mariadb/bin/mysqld_safe --user=mariadb --ledir=/opt/mariadb/bin
180507 14:20:33 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
180507 14:20:33 mysqld_safe Logging to '/var/log/mysql/error.log'.
180507 14:20:33 mysqld_safe A mysqld process already exists
```

[list]/opt/mariadb-data/my.cnf[/list]
[https://gist.github.com/mbnoimi/b9daceca0e0e21da86b048b9883c5edf](https://gist.github.com/mbnoimi/b9daceca0e0e21da86b048b9883c5edf)

[list]/etc/systemd/system/mariadb.service[/list]
[https://gist.github.com/mbnoimi/5920301ff79dcb88aab3ef7fa459733e](https://gist.github.com/mbnoimi/5920301ff79dcb88aab3ef7fa459733e)

[list]Permissions of /opt[/list]

```
Access: (0755/drwxr-xr-x)  Uid: (0/root)   Gid: (0/root)
```

[list]Permissions of /opt/mariadb-data[/list]
```
Access: (0700/drwx------)  Uid: (999/mariadb)   Gid: (999/mariadb)
```

[list]Permissions of /opt/mariadb-data/my.cnf[/list]
```
Access: (0700/-rwx------)  Uid: (999/ mariadb)   Gid: (999/ mariadb)
```

---

### Post by TheFu on 2018-05-12
Assuming that /opt/mariadb-data/my.cnf exists and is configured correctly, then I have no idea, but these tools perform the same thing and have similar dependencies and on an ubuntu system, only 1 would normally be installed.  Config files would conflict between them, for example.  This is because the LAMP stack programs will work equally well with either DBMS.   The trade-off is that having both installed on the same system is non-trivial.

A few work-arounds:
* Load each into a Container like LXD/Docker provide.
* Create a virtual machine for each, load one into each VM.
* install 1 using the package manager and the other from source.  For the source install, ensure everything goes to /usr/local/.

There might be a way to tell the package manager to install to a different location than the default, but I think you'll have to use dpkg directly for that.  I've never done it.

If it were me, I'd go the container route.

---

### Post by mbnoimi on 2018-05-12
> * Load each into a Container like LXD/Docker provide.
* Create a virtual machine for each, load one into each VM.

Good point. Both suggestions may become pain in the ass because I use MariaDB for remote access so I'm afraid of poor performance and the complicated configurations.

> * install 1 using the package manager and the other from source. For the source install, ensure everything goes to /usr/local/.

In my installation steps you'll notice that I use MariaDB from zipped binaries (/opt/mariadb) while I use MySQL from Ubuntu repositories (package manager). So the files and the configs will not conflict at all.

---

### Post by TheFu on 2018-05-12
I did see that, but zipped binaries aren't the same as *built from source*.

IMHO, there will be much more pain by going outside the package management system than any VM or Container solution would entail. Being afraid of performance issues without seeing that they do/don't exist doesn't help things.  VMs bring all sorts of good things to systems management.  Mainly VMs abstract away any physical hardware dependencies, so systems maintenance is 100x easier.  I have VMs that were created in 2007-ish which have been moved forward from LTS to LTS all this time. Also, the underlying hardware has migrated 3 times too with ZERO issues.   I've had more problems going from 14.04 to 16.04 on a physical machine than any VM migration caused.
VM overhead for Windows is noticeable.  VM overhead for Linux isn't THAT bad, perhaps 8%. You can use LXD which effectively drops overhead to 0-2% and have a much smaller memory use than VMs at the expense of less segmentation between the virtual systems.  Containers claim 10x-100x more density than virtual machines on the same hardware. If you can run 10 VMs on a system, then as a rule of thumb, you can run 100 containers.  Hows that for minimizing overhead?

MariaDB and MySQL are API compatible. Unless there are specific support contracts involved with both of them.  I would dump mysql for MariaDB. 

I used to run a set of remote access systems for 22K people.  The DBMS checked for authorization and authentication wasn't important at all, at least in our setup, but we could only handle 5K concurrent users.

But these are your systems and only you know best.

---

### Post by Tadaen_Sylvermane on 2018-05-15
> Good point. Both suggestions may become pain in the ass because I use MariaDB for remote access so I'm afraid of poor performance and the complicated configurations.

Zero performance hit with lxd. Easy as pie to set up. Idk about docker.

---

