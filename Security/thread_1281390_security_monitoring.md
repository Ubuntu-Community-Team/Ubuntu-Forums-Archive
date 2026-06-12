---
title: "security monitoring"
date: 2009-10-03
forum: Security
---

### Post by raucous on 2009-10-03
I believe my roommate is going into my computer and making some setting changes. Is there any way of seeing a record of the changes that have been made? The password for the wifi won't save anymore and when I try to save a document in openoffice it says that "object is not accessible; object cannot be accessed due to insufficient user rights."

How can I reset these and see when or how the changes were made?

Thanks

---

### Post by Lars Noodén on 2009-10-03
Assuming the logs are not changed :

```

# see when you have last logged in
last $USER

# see who logged and when
sudo less /var/log/auth.log

# see which packages where added or removed
sudo less /var/log/dpkg.log

```

If you figure the machine is compromised, then back up your data and do a fresh install.  Be sure then to set the password for Grub so that you cannot enter single user mode.  If the machine uses BIOS, set those so that you cannot boot from anything except the hard drive and set the BIOS configuration cannot be changed.  Set your screen saver to require a password to deactivate and consider using [blueproximity](http://packages.ubuntu.com/jaunty/blueproximity) to activate it faster when you step out for a moment.

Also, if you do a fresh install, make your own user account after the installation is complete and use the initial account *only* for administration, like adding packages or making updates.

---

