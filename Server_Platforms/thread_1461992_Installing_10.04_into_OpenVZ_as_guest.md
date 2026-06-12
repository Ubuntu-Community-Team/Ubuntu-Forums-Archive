---
title: "Installing 10.04 into OpenVZ as guest"
date: 2010-04-25
forum: Server Platforms
---

### Post by litos on 2010-04-25
Anybody know how to upgrade 9.04 to 10.04 on the OpenVZ VE?

I tried to update system via dist-upgrade and scripts stoped on plymouth and upstart-udev-bridge proccess
I had remove plymouth* and upstart-udev-bridge.conf from /etc/init/ but other proccess (such as /etc/init/ssh) does not start.

How to fix upstart or add sysinit (old /etc/init.d) support?

---

### Post by litos on 2010-04-25
I have made upgrade my systems having following steps. The problem is solved :)

Create "hack" for OpenVZ first

```
mkdir /etc/init/
```

```
cat << EOF >  /etc/init/openvz.conf
description "Fix OpenVZ"
start on startup

task
pre-start script
mount -t devpts devpts /dev/pts
mount -t tmpfs varrun /var/run
mount -t tmpfs varlock /var/lock
mkdir -p /var/run/network
touch /var/run/utmp
chmod 664 /var/run/utmp
chown root.utmp /var/run/utmp
if [ "$(find /etc/network/ -name upstart -type f)" ]; then
chmod -x /etc/network/*/upstart || true
fi
end script

script
start networking
initctl emit filesystem --no-wait
initctl emit local-filesystems --no-wait
initctl emit virtual-filesystems --no-wait
init 2
exec /etc/init.d/rc 2
end script
EOF
```

Change repos to lucid

```
perl -p -i -e 's/jaunty/lucid/g' /etc/apt/sources.list
```

Update and upgrade your system

```
apt-get update
apt-get dist-upgrade

dpkg --force-all -i /var/cache/apt/archives/util-linux*
apt-get -f install

apt-get dist-upgrade

```

Remove no needed services

```
rm /etc/init/plymouth*
rm /etc/init/tty*
rm /etc/init/upstart-udev-bridge.conf

update-rc.d -f quotarpc remove
update-rc.d -f ondemand remove

rm /etc/rc2.d/S15ssh_gen_host_keys
```


Bugfix for ssh
```
perl -p -i -e 's/oom never/#oom never/g' /etc/init/ssh.conf
```

Restart your system
```
reboot
```

Clean disk space
```
apt-get clean
dpkg -l | grep "^rc" | awk '{print $2}' | xargs dpkg --purge
apt-get autoremove

```

---

### Post by bodhi.zazen on 2010-04-29
To make an Ubuntu 10.04 (LTS) template see:

[http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/)

---

### Post by bodhi.zazen on 2010-04-29
> **litos said:**
> I have made upgrade my systems having following steps. 

<clip>



Found this via a search of openvz, just looking at your steps now.

I would NOT remove the quota or ssh_gen_host_keys boot scripts.

quota is helpful in VPS for what should be obvious reasons (not as critical on your own personal VPS I suppose).

The ssh_gen_host_keys script is necessary so that each ssh server (host) has a unique set of host keys. This is IMO critical for ssh security.

---

### Post by bodhi.zazen on 2010-05-03
After using Ubuntu 10.04 as an OpenVZ gust for a few days I would advise the following caution :

The upstart / init scripts do not work well, so, for example, when adding a new service (mysql), mysql would not start when the Ubuntu 10.04 guest is started without editing the /etc/init/mysql.conf file.

So while you may not mind tweaking your guests, use with caution in a "production" setting where you may be giving an Ubuntu guest to someone without much experience with such scripts.

---

### Post by blueyed on 2010-10-12
I've noticed that munin-node failed to start automatically in my containers.

Since munin-node is configured to start on "(filesystem and net-device-up IFACE=lo)", apparently "net-device-up IFACE=lo" never gets emitted.
This appears to get done via udev or something else emitting "net-device-added" normally.

My workaround/fix for this has been to manually start the local interface via the "network-interface" upstart script (from the openvz upstart script):

```
# diff -u /vz/private/X/etc/init/openvz.conf.old /vz/private/X/etc/init/openvz.conf
--- /vz/private/111/etc/init/openvz.conf.old    2010-10-12 22:40:59.000000000 +0200
+++ /vz/private/111/etc/init/openvz.conf        2010-10-12 22:41:06.000000000 +0200
@@ -24,6 +24,7 @@

 script
 start networking
+start network-interface INTERFACE=lo
 initctl emit filesystem --no-wait
 initctl emit local-filesystems --no-wait
 initctl emit virtual-filesystems --no-wait
```

(openvz.conf is from above / [http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/) (currently down))

---

