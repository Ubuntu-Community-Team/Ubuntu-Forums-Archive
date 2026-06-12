---
title: "Why do we need the hostname in BOTH the /etc/hostname &amp; /etc/hosts file anyway?"
date: 2011-03-07
forum: Security
---

### Post by rocksockdoc on 2011-03-07
As a minor measure of privacy & security while web surfing with Javascript on, I often change my hostname (in both the /etc/hostname and /etc/hosts file) & reboot.

Having come from the Windows world, where there is no need for both files, I wonder why the hostname is required in the two files for Ubuntu.

It would seem to me that one hostname location should suffice. 

If I were to only change one location, which is preferred to change (/etc/hosts or /etc/hostname)?

---

### Post by bodhi.zazen on 2011-03-08
You need to change both or you will break sudo.

The two files are used by different applications for different purposes.

See here:

[http://jblevins.org/log/hostname](http://jblevins.org/log/hostname)

---

### Post by rocksockdoc on 2011-03-10
> **bodhi.zazen said:**
> The two files are used by different applications for different purposes

Quick summary of that reference:

[LIST]
[*]We must distinguish between setting the unqualified hostname and setting the fully qualified domain name (FQDN)
[LIST]
[*]Hostname held in kernel (*but can be changed on the fly*)
[*]The FQDN is usually determined in /etc/hosts
[/LIST]
[*]Obtain the unqualified hostname via these methods
[LIST]
[*][FONT=Courier New]hostname[/FONT]
[*][FONT=Courier New]uname -n[/FONT]
[*][FONT=Courier New]cat /proc/sys/kernel/hostname[/FONT]
[*][FONT=Courier New]sysctl kernel.hostname[/FONT]
[/LIST]
[*]Obtain the fully qualified domain name via:
[LIST]
[*][FONT=Courier New]hostname -f[/FONT]
[/LIST]
[*]Changing the unqualified hostname permanently differs by distribution:
[LIST]
[*][FONT=Courier New]/etc/init.d/hostname.sh 
[/FONT]
[LIST]
[*][FONT=Courier New]/etc/hostname: foo[/FONT]
[/LIST]
[/LIST]
[*]Changing the hostname, emporarily, on the fly, as root:
[LIST]
[*][FONT=Courier New]echo "foo" > /etc/hostname; /etc/init.d/hostname.sh[/FONT]
[*][FONT=Courier New]hostname foo[/FONT]
[/LIST]
[/LIST]

---

