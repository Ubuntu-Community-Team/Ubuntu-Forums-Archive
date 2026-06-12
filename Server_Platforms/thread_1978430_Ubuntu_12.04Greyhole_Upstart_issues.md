---
title: "Ubuntu 12.04/Greyhole Upstart issues"
date: 2012-05-11
forum: Server Platforms
---

### Post by vidkun on 2012-05-11
I have a fresh install of 64 bit ubuntu server 12.04 and have installed Greyhole from the repo. However when I try to start it with either "sudo start greyhole" or "sudo service greyhole start" I get the following error message:

```
start: Unknown job: greyhole
```

I have verified that there is an upstart script installed in /etc/init/greyhole.conf and that it has the correct permissions according to the developer of greyhole. I have also tried doing an apt-get remove, then rm the previously fetched deb file, and doing a new install of greyhole with no luck. I also ran an initctl reload-configuration as was mentioned in another user's thread about the same error with ssh. Still no luck.

Anyone have any other ideas why it won't recognize the upstart script is there?

Thanks

---

### Post by gboudreau on 2012-05-12
Maybe try checking the conf file syntax:

```
sudo apt-get install dbus-x11
dbus-launch --auto-syntax
init-checkconf /etc/init/greyhole.conf
```

On Ubuntu 11, I get:
```
$ init-checkconf /etc/init/greyhole.conf
File /etc/init/greyhole.conf: syntax ok
```

You can remove dbus-x11 after:
```
sudo apt-get remove dbus-x11
```

---

### Post by vidkun on 2012-05-12
It fails to ask upstart to check:

```
$init-checkconf /etc/init/greyhole.conf 
ERROR: failed to ask Upstart to check conf file
```

---

### Post by gboudreau on 2012-05-12
> **vidkun said:**
> It fails to ask upstart to check:

```
$init-checkconf /etc/init/greyhole.conf 
ERROR: failed to ask Upstart to check conf file
```
That would happen if dbus isn't running.

What was the result of this command:
```
dbus-launch --auto-syntax
```

---

### Post by vidkun on 2012-05-12
> **gboudreau said:**
> That would happen if dbus isn't running.

What was the result of this command:
```
dbus-launch --auto-syntax
```

```
vidkun@odin:/mnt/disk1$ dbus-launch --auto-syntax
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-KVovGK2RbN,guid=74ac9545ebdc934d467bbcb000025492';
export DBUS_SESSION_BUS_ADDRESS;
DBUS_SESSION_BUS_PID=7310;
```

---

### Post by gboudreau on 2012-05-12
If, after you launched dbus with that command, running init-checkconf in the same terminal gives "failed to ask Upstart to check conf file", then I don't know. I had that error before starting dbus, and after I started it, it was able to check the conf correctly.

---

### Post by vidkun on 2012-05-12
> **gboudreau said:**
> If, after you launched dbus with that command, running init-checkconf in the same terminal gives "failed to ask Upstart to check conf file", then I don't know. I had that error before starting dbus, and after I started it, it was able to check the conf correctly.

That's correct. Same terminal. I'm SSHd in. I noticed that the package you had me install was dubs-x11. Would it make a difference that X11 is not installed? I don't run X on any of my servers.

---

### Post by gboudreau on 2012-05-13
I don't have X installed either.
If dbus-x11 was missing packages to work, they would have been installed by apt-get. That package works fine by itself.

I'll try in a VM sometimes today, if I can.
*edit: it works fine in my VM...

---

