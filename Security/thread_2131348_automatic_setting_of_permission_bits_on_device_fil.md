---
title: "automatic setting of permission bits on device files"
date: 2013-04-01
forum: Security
---

### Post by dspeterson on 2013-04-01
I'm using xubuntu 12.04, and I notice that periodically, the permissions
on some device special files are changed.  For instance, if I manually
change the permissions on /dev/sdc to 666, they will eventually get
changed back to 660.  How do I disable this behavior?  I looked around
in the various cron-related configuration files under /etc, and also in the
scripts in /etc/init.d, and didn't see anything that looked like it might be
changing permissions in /dev.

---

### Post by unspawn on 2013-04-06
It may be PAM (/etc/security/*) or Udev (/etc/udev/rules*/) but regardless of what could be causing it weakening OS security by changing any access rights to 777 or 666 is ill-advised. 
Simply put it isn't a problem with the OS or the distribution but IMHO a problem with *understanding how discretionary access controls (should) work*.

---

### Post by matt_symes on 2013-04-08
Hi

> **dspeterson said:**
> if I manually
change the permissions on /dev/sdc to 666, they will eventually get
changed back to 660.

Which device files are you changing and why ?

> **unspawn said:**
> but IMHO a problem with *understanding how discretionary access controls (should) work*.

Agreed.

@OP: What are you trying to achieve by changing the access controls on device files ?

Kind regards

---

### Post by dspeterson on 2013-04-08
> **matt_symes said:**
> Hi
Which device files are you changing and why ?



Agreed.

@OP: What are you trying to achieve by changing the access controls on device files ?
Kind regards

I'm just changing /dev/sdc.  It's on a development VM which is used only by me.  /dev/sdc
is a virtual disk I created for use by a daemon I'm working on, which is running without root
privileges and needs access to the entire block device.  In this case, the security of the
data on /dev/sdc isn't a concern.

I suspect udev may be causing the observed behavior.  I created a file
/etc/udev/rules.d/10-local.rules that contains the following line:

KERNEL="sdc" MODE="0666"

Hopefully this will produce the desired behavior.

---

### Post by matt_symes on 2013-04-08
Hi

I still don't really understand what you are trying to do however world writeable permissions is really not the way to do it.

You could make the daemon run under its own user and group and make the device node created by udev be owned by that user or group.

I haven't read through all of it but i think this gives the general idea.

[http://www.weather-watch.com/smf/index.php?topic=39257.0](http://www.weather-watch.com/smf/index.php?topic=39257.0)

You also have ACL you may be able to use.

Kind regards

---

### Post by dspeterson on 2013-04-09
Yes I know that in general world writable permissions are a bad thing.  However
this is just in a development VM where I'm making code changes to a daemon
that accesses the block device.  Since the VM is used only by me for
development purposes, I'm not concerned about permissions on the block
device.  I'm just trying to set things up as simply as possible for development,
so I can quickly iterate on code changes without having to run the daemon
under its own user or group each time I want to test my code changes.
Creating the above-mentioned [COLOR=#000000]/etc/udev/rules.d/10-local.rules file appears to
have worked, so it looks like I'm all set.

Thanks,
Dave

[/COLOR]

---

