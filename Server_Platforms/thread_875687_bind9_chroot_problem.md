---
title: "bind9 chroot problem"
date: 2008-07-31
forum: Server Platforms
---

### Post by eentonig on 2008-07-31
Can someone give me some pointers or help?

I'm trying to get Bind9 to run in a chrooted environment.

The service runs fine as is, but when I move it to a chroot jail, I can't start it anymore.

Error messages during starting.
> 1 gauloises kernel: [180942.452046] audit(1217451274.744:5): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14130 profile="/usr/sbin/named" namespace="default"
1 gauloises kernel: [180942.453222] audit(1217451274.748:6): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14130 profile="/usr/sbin/named" namespace="default"
1 gauloises named: none:0: open: /etc/bind/named.conf: permission denied
1 gauloises named: loading configuration: permission denied
1 gauloises kernel: [180942.460655] audit(1217451274.756:7): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14131 profile="/usr/sbin/named" namespace="default"
1 gauloises kernel: [180942.460761] audit(1217451274.756:8): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/chroot/named/etc/bind/named.conf" pid=14131 profile="/usr/sbin/named" namespace="default"
1 gauloises kernel: [180942.460812] audit(1217451274.756:9): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14131 profile="/usr/sbin/named" namespace="default"
1 gauloises kernel: [180942.461179] audit(1217451274.756:10): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14131 profile="/usr/sbin/named" namespace="default"
1 gauloises kernel: [180942.461221] audit(1217451274.756:11): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=14131 profile="/usr/sbin/named" namespace="default"

Config changes to get chroot working
> sudo mkdir -p /var/chroot/named
sudo cd /var/chroot/named/
sudo mkdir -p /var/chroot/named/etc
sudo mkdir /var/chroot/named/dev
sudo mkdir -p /var/chroot/named/var/cache/bind
sudo mkdir -p /var/chroot/named/var/run/bind/run
sudo mv /etc/bind /var/chroot/named/etc
sudo ln -s /var/chroot/named/etc/bind /etc/bind
sudo mknod /var/chroot/named/dev/null c 1 3
sudo mknod /var/chroot/named/dev/random c 1 8
sudo chmod 666 /var/chroot/named/dev/null /var/chroot/named/dev/random
sudo chown -R bind:bind /var/chroot/named/var/*
sudo chown -R bind:bind /var/chroot/named/etc/bind
sudo vi /etc/default/bind9
# changed "OPTIONS="-u bind" to
OPTIONS="-u bind -t /var/chroot/named"

---

### Post by windependence on 2008-07-31
I could be wrong but I think your permissions and/or ownership is incorrect on your /etc/bind/named.conf file. I would open it up and see if it helps, and then take the permissions down gradually from there until you get what you want.

Just curious, why chroot for this?

-Tim

---

### Post by eentonig on 2008-07-31
> **windependence said:**
> I could be wrong but I think your permissions and/or ownership is incorrect on your /etc/bind/named.conf file. I would open it up and see if it helps, and then take the permissions down gradually from there until you get what you want.

Just curious, why chroot for this?

-Tim

I'll try that indeed. 

Why not implement good security practices?

Actually, for my home setup, I don't care. But I'm helping a colleague with a server his setting up for his business. And he asked me to take  security as a top concern.

---

### Post by eentonig on 2008-07-31
> Jul 31 20:39:04 gauloises named[8030]: found 1 CPU, using 1 worker thread
Jul 31 20:39:04 gauloises named[8030]: loading configuration from '/etc/bind/named.conf'
Jul 31 20:39:04 gauloises named[8030]: none:0: open: /etc/bind/named.conf: permission denied
Jul 31 20:39:04 gauloises named[8030]: loading configuration: permission denied
Jul 31 20:39:04 gauloises named[8030]: exiting (due to fatal error)
Jul 31 20:39:04 gauloises kernel: [259130.937804] audit(1217529544.792:20): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=8031 profile="/usr/sbin/named" namespace="default"
Jul 31 20:39:04 gauloises kernel: [259130.937895] audit(1217529544.792:21): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/chroot/named/etc/bind/named.conf" pid=8031 profile="/usr/sbin/named" namespace="default"
Jul 31 20:39:04 gauloises kernel: [259130.937941] audit(1217529544.792:22): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=8031 profile="/usr/sbin/named" namespace="default"
Jul 31 20:39:04 gauloises kernel: [259130.938251] audit(1217529544.792:23): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=8031 profile="/usr/sbin/named" namespace="default"
Jul 31 20:39:04 gauloises kernel: [259130.938293] audit(1217529544.792:24): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/var/chroot/named/etc/localtime" pid=8031 profile="/usr/sbin/named" namespace="default"


Didnn't solve a thing. As you can see from the output below. Everybody has full access to named.conf. But I still get "permission denied" as error message.

> root@gauloises:/var/chroot/named/etc/bind# ls -Al
total 52
-rw-r--r-- 1 bind bind  237 2008-07-30 22:53 db.0
-rw-r--r-- 1 bind bind  312 2008-07-30 22:53 db.1.168.192.rev
-rw-r--r-- 1 bind bind  271 2008-07-30 22:53 db.127
-rw-r--r-- 1 bind bind  237 2008-07-30 22:53 db.255
-rw-r--r-- 1 bind bind  353 2008-07-30 22:53 db.empty
-rw-r--r-- 1 bind bind  410 2008-07-30 22:53 db.home.bogus
-rw-r--r-- 1 bind bind  270 2008-07-30 22:53 db.local
-rw-r--r-- 1 bind bind 2878 2008-07-30 22:53 db.root
-rwxrwxrwx 1 bind bind 1079 2008-07-30 22:53 named.conf
-rw-r--r-- 1 bind bind  333 2008-07-30 22:53 named.conf.local
-rw-r--r-- 1 bind bind  878 2008-07-30 22:53 named.conf.options
-rw-r----- 1 bind bind   77 2008-07-30 22:53 rndc.key
-rw-r--r-- 1 bind bind 1317 2008-07-30 22:53 zones.rfc1918


---

### Post by ngaur on 2009-08-16
This is kind of an old thread now, but since others will arive here from google much as I did, I thought I'd provide the answer that wasn't given at the time.

The error is being generated by the kernel because apparmor is turned on and it limits which files named has access to.  

See the configuration in /etc/apparmor.d/usr.sbin.named .  It's fairly self explanatory.  `man apparmor.d` might make things clearer, though it's rather formally written (it goes straight into BNF format description).  It's probably easier to just follow your nose.

Some people prefer to just turn off apparmor. (`/etc/init.d/apparmor stop`).  Your choice really.  If you actually read log files when you have a problem, and if you now recognise what apparmor's log entries look like, then it shouldn't cause you too much trouble, and does add significantly to security.

---

### Post by tnttrx on 2010-07-15
> **ngaur said:**
> This is kind of an old thread now, but since others will arive here from google much as I did, I thought I'd provide the answer that wasn't given at the time.

The error is being generated by the kernel because apparmor is turned on and it limits which files named has access to.  

See the configuration in /etc/apparmor.d/usr.sbin.named .  It's fairly self explanatory.  `man apparmor.d` might make things clearer, though it's rather formally written (it goes straight into BNF format description).  It's probably easier to just follow your nose.

Some people prefer to just turn off apparmor. (`/etc/init.d/apparmor stop`).  Your choice really.  If you actually read log files when you have a problem, and if you now recognise what apparmor's log entries look like, then it shouldn't cause you too much trouble, and does add significantly to security.


thank you very much!

---

### Post by wessexmario on 2011-11-03
The apparmour problem is caused when chrooting bind by having to move the configuration files to a different real path.

```
vi /etc/apparmor.d/usr.sbin.named
```
add the second line after the first

```
/etc/bind/** r,
**/var/lib/named/etc/bind/** r,**
```
save the file, then

```
service apparmor restart
service bind9 restart
```
Job done!

---

