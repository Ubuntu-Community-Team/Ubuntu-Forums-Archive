---
title: "basic root server - services optimization"
date: 2019-12-06
forum: Server Platforms
---

### Post by clusterix on 2019-12-06
I switched from debian to ubuntu as a base system for a new webserver installation ...
what about this stuff ... should these be set disabled for a server setup?


- haveged.service
- apt-daily-upgrade.timer
- apt-daily.timer
- motd-news.timer
- keyboard-setup.service


any further recommendations for a basic webserver ubuntu optimization?

---

### Post by howefield on 2019-12-06
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2019-12-06
"basic webserver optimization" is a subjective ideal.
I block all automatic APT updates of any sort, including updating the DB.
I block all Canonical messages of any sort.
I don't leave development tools on the system unless they are absolutely required.  Why leave hackers with useful tools?

Lots of changes have happened between 14.04, 16.04, and 18.04.  Also, which webserver are you running? There are a bunch.

What about security, like never allowing admin webapp access from anywhere except localhost?
I also like to use read-only mounts for static files.  Watching a noob hacker trying to change files on a read-only mount or files that have been marked immutable is fun.

I've never heard of haveged.

If I wanted to limit what got started, I'd use systemd-analyze to see what is being started that is wasteful, starting with things that start slowly.

---

### Post by clusterix on 2019-12-07
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
Kernel: 4.15.0-72-generic


thanks, I just want to switch off all non-required services, I have already removed snapd.
```

systemctl disable snapd.snap-repair.timer
systemctl disable snapd.socket
systemctl disable snapd.autoimport.service
systemctl disable snapd.core-fixup.service
systemctl disable snapd.seeded.service
systemctl disable snapd.service
systemctl disable snapd.system-shutdown.service
apt purge snapd

```

can/should all these services be safely deactivated for a webserver setup?
It seems these are included w/ a basc 18.04 lts installation
- haveged.service
- apt-daily-upgrade.timer
- apt-daily.timer
- motd-news.timer
- keyboard-setup.service

also fstrim ... makes it sense to keep it enabled w/ a 1TB NVME SSD,
is there any other stuff which should be deactivated?

```

systemctl list-unit-files --state=enabled --no-pager
ntp-systemd-netif.path                enabled
resolvconf-pull-resolved.path         enabled
apache2.service                       enabled
apparmor.service                      enabled
atd.service                           enabled
autovt@.service                       enabled
bind9-resolvconf.service              enabled
bind9.service                         enabled
blk-availability.service              enabled
clamav-daemon.service                 enabled
clamav-freshclam.service              enabled
console-setup.service                 enabled
cron.service                          enabled
dbus-org.freedesktop.resolve1.service enabled
dovecot.service                       enabled
fail2ban.service                      enabled
firewall.service                      enabled
getty@.service                        enabled
haveged.service                       enabled
imscp_daemon.service                  enabled
imscp_mountall.service                enabled
imscp_panel.service                   enabled
imscp_traffic.service                 enabled
keyboard-setup.service                enabled
lvm2-monitor.service                  enabled
mariadb.service                       enabled
mysql.service                         enabled
mysqld.service                        enabled
netfilter-persistent.service          enabled
networking.service                    enabled
nginx.service                         enabled
ntp.service                           enabled
ondemand.service                      enabled
opendkim.service                      enabled
php7.0-fpm.service                    enabled
postfix.service                       enabled
psw5.6-fpm.service                    enabled
psw7.1-fpm.service                    enabled
psw7.2-fpm.service                    enabled
psw7.3-fpm.service                    enabled
resolvconf.service                    enabled
rsync.service                         enabled
rsyslog.service                       enabled
setvtrgb.service                      enabled
spamassassin.service                  enabled
ssh.service                           enabled
sshd.service                          enabled
syslog.service                        enabled
systemd-resolved.service              enabled
systemd-timesyncd.service             enabled
dm-event.socket                       enabled
lvm2-lvmetad.socket                   enabled
lvm2-lvmpolld.socket                  enabled
uuidd.socket                          enabled
remote-fs.target                      enabled
apt-daily-upgrade.timer               enabled
apt-daily.timer                       enabled
fstrim.timer                          enabled
motd-news.timer                       enabled
phpsessionclean.timer                 enabled

```

---

### Post by clusterix on 2019-12-07
I have removed all these stuff ... I do not think that these are needed for a webserver installation
```

systemctl disable snapd.snap-repair.timer
systemctl disable snapd.socket
systemctl disable snapd.autoimport.service
systemctl disable snapd.core-fixup.service
systemctl disable snapd.seeded.service
systemctl disable snapd.service
systemctl disable snapd.system-shutdown.service
systemctl disable apt-daily-upgrade.timer
systemctl disable apt-daily.timer
systemctl disable haveged.service
systemctl disable motd-news.timer
apt purge haveged snapd
apt autoremove

```

---

### Post by TheFu on 2019-12-07
There's a bunch of stuff in that list that have NOTHING to do with a web server and are huge security risks.
bind, dovecot, postfix, rsync, php, mariadb, mysql .... why have 2 web servers and 2 DBMSes loaded?  Seems foolish to me.

Only run the services that are actually being used and no way would I run email on the same machine as a web server. Same for BIND. Certain things need to be compartmentalized - email, and BIND are two of the most important to have separate.

What's the point of spamassassin and clamav on a web server?  None.
Are you using LVM? If not, you don't need that either.  I use LVM, so it is required. You might not.

---

### Post by clusterix on 2019-12-07
yep [COLOR=#000000]LVM can be disabled too, I do not use ...
I use IMSCP as controlpanel so the other stuff is related to the panel installation (incl. all needed services) apache2 is running for the website & nginx is used for the controlpanel.
[/COLOR][https://i-mscp.net/](https://i-mscp.net/)

---

### Post by TheFu on 2019-12-07
if you want a minimal, base, web server - don't load some unneeded panel software. That's just another way to be hacked.

---

