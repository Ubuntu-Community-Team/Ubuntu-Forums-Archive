---
title: "Upgrade from 14.04 to 16.04 messed-up my server"
date: 2016-10-30
forum: Server Platforms
---

### Post by sevynos on 2016-10-30
Hi,

I recently upgraded from Ubuntu Server 14.04 to 16.04 and it made a mess on my setup:

Fail2ban is not working anymore. Here's what I've done to try to repair:

Removed it with "sudo aptitude remove --purge fail2ban";
Deleted the folder fail2ban in etc to have a clean install;
Reinstalled with "sudo apt-get install fail2ban".

Installation went flawlessly apart from all configuration files didn't install.
I tried to find the default fail2ban.conf and jail.conf on the net without any success.  So I restored the original file from a backup and I still get the same error from the previous installation: "ERROR Failed during configuration: While reading from '/etc/fail2ban/jail.conf' [line 148]: option 'port' in section 'pam-generic' already exists"

Making Fail2ban work again is my first priority but I also have Dovecot which is messed-up.  I can't connect to pop server anymore since the upgrade.

Any help is welcome!

Thanks

---

### Post by darkod on 2016-10-31
Maybe this can help?
[https://github.com/fail2ban/fail2ban/issues/1396](https://github.com/fail2ban/fail2ban/issues/1396)

It seems the port parameter gets doubled up somehow in the config file (not sure if the config file is fail2ban.conf or jail.conf. Check both.

---

### Post by sevynos on 2016-10-31
Thanks,

Will look at this as soon as possible.

---

### Post by sevynos on 2016-11-02
Finally found that I can't connect to Postfix and apache too.

So I'll temporary get back my 14.04 backup online while I install a new 16.04 from scratch.

Thanks for your help darkod.

---

### Post by mastablasta on 2016-11-03
> **darkod said:**
> Maybe this can help?
[https://github.com/fail2ban/fail2ban/issues/1396](https://github.com/fail2ban/fail2ban/issues/1396)

It seems the port parameter gets doubled up somehow in the config file (not sure if the config file is fail2ban.conf or jail.conf. Check both.

that's a pretty bad bug for an app in the repos. is a a bug opened on launchpad?

---

