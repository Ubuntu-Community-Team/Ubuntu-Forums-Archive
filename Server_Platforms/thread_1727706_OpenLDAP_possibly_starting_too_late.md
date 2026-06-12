---
title: "OpenLDAP possibly starting too late?"
date: 2011-04-12
forum: Server Platforms
---

### Post by tgice on 2011-04-12
Hi, I recently followed a [tutorial]("http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html") on how to get OpenLDAP running with Samba on Lucid.  It worked pretty well.

Here's my very frustrating problem with it.  For the first 5 - 10 minutes after rebooting, password handling (possibly PAM?) is hosed, including for users in LDAP authenticating via Samba.

In fact, I think the only reason I can SSH into the machine during that window is because I happen to have certificate authentication enabled and my client uses that.

When I try to do a sudo command after logging in, though, and have to enter the password, it hangs.  I've searched logs and haven't come up with much.

I *think* it's related to [this bug]("http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg51954.html"), but I'm not sure.

And here's what's killing me ... it's not easy for me to figure out how to ensure that slapd starts before smbd and rsyslog (I read somewhere else that it needs to start before that for some reason) b/c most of the jobs are upstart jobs, but slapd is not.

By default it runs at S19 in rc2.d, and I've tried manually lowering that as far as S05 or S07, but I'm still having trouble.

Has anyone fixed this satisfactorily in 10.04 or have an idea that might help me?

Thanks

---

### Post by tgice on 2011-04-12
Here's my /etc/nsswitch.conf, in case that's of interest, based on changes from the aforementioned HOWTO:

> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# pre_auth-client-config # passwd:         compat
passwd: files ldap
# pre_auth-client-config # group:          compat
group: files ldap
# pre_auth-client-config # shadow:         compat
shadow: files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# pre_auth-client-config # netgroup:       nis
netgroup: nis

---

### Post by tgice on 2012-03-06
Actually, as I get back to this problem much later, I've concluded that what I may have been experiencing was the exact same as this poster, and his solution may've solved my problem to (just doing the net rpc join command):

[http://ubuntuforums.org/showthread.php?t=1662120]("http://ubuntuforums.org/showthread.php?t=1662120")

---

