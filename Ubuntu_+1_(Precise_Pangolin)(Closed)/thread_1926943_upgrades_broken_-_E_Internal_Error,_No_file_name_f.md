---
title: "upgrades broken - E: Internal Error, No file name for libcomerr2"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TDK800 on 2012-02-17
Can't upgrade packages, gives error.

sudo apt-get install -f
E: Internal Error, No file name for libcomerr2


sudo aptitude upgrade --full-resolver
E: Internal Error, No file name for libcomerr2

anyone else?

---

### Post by dino99 on 2012-02-17
clean the room first (autoclean, autoremove)

then:
sudo dpkg-reconfigure -phigh -a
(can take a while , be patient)

---

### Post by TDK800 on 2012-02-17
> **dino99 said:**
> sudo dpkg-reconfigure -phigh -a


$ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop acpid
acpid stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start acpid
acpid start/running, process 7248
dpkg-maintscript-helper: error: couldn't identify the package

$

---

### Post by paul_in_london on 2012-02-17
> **TDK800 said:**
> $ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop acpid
acpid stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start acpid
acpid start/running, process 7248
dpkg-maintscript-helper: error: couldn't identify the package

$

First try:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get -f install
```

If that doesn't work, have a look at this post:

[ubuntuforums.org/showpost.php?p=11453698&postcount=92](ubuntuforums.org/showpost.php?p=11453698&postcount=92)

but before you resort to editing the **[COLOR="Red"]/var/lib/dpkg/status[/COLOR]** file manually, try this:

```
cd /var/lib/dpkg
sudo cp status status.orig
sudo cp status-old status-old.orig
sudo cp /var/backups/dpkg.status.0 status
sudo apt-get update
sudo apt-get upgrade
```

if the apt-get update/apt-get upgrade commands work ok, repeat with apt-get dist-upgrade.

If the **[COLOR="Red"]/var/backups/dpkg.status.0[/COLOR]** backup of your status file doesn't pre-date your errors, try uncompressing and using one of the other status backups from the same directory. You'll just end up re-applying more updates that you already have.

---

### Post by paul_in_london on 2012-02-17
Another thing you could try for the problematic packages is:

```
apt-get download libcomerr2 # downloads into current directory I think
sudo dpkg -i libcomerr2*.deb

```

etc.

---

### Post by TDK800 on 2012-02-17
Thanks, restoring old status file fixed it.

---

