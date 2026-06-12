---
title: "Best centralized authentication scheme for multiple platforms with dynamic addressing"
date: 2013-10-13
forum: Security
---

### Post by 1clue on 2013-10-13
Hi,

I need a centralized security scheme for a bunch of VMs and a bunch of real boxes.  This is my home office, but it's getting unwieldy.

I started to install NIS but it gave me a warning about dynamic addresses being a security vulnerability.

What's the best approach?

My household is using:
[LIST=1]
[*]Windows Vista & 8 real hardware.
[*]Mac OS X real hardware
[*]Android real hardware
[*]Linux real hardware
[*]A whole lot of Linux VMs
[*]A few Windows VMs.
[/LIST]

I obviously don't need authentication on the android stuff, not really on the Mac either.  But the Linux and Windows stuff I'd really like to have use common passwords.

Thanks.

---

### Post by TheFu on 2013-10-13
I don't know if this is the best scheme, but we use an LDAP server. There are PAM modules for Linux. Never bothered to do anything for Windows ... only have 2 installs - TV recording/Quicken inside a VM and one on a dual-boot laptop. Everything else - EVERYTHING - is Linux.

However, managing passwords isn't really anything I do. ssh-keys replace that for 99.9999% of the systems. Can't think of the last time I used a password login except on 2 main machines. All other logins are ssh-based. Web-App logins are easily configured to use LDAP, almost always.

In the 1990s, I used NIS ... vaguely recall that trust was based on IP.  I thought NIS+ resolved that.  If you need real security, look to Kerberos.

---

### Post by 1clue on 2013-10-13
I will not use shared ssh keys.  That doesn't solve any problems, it only creates them.

I need to synchronize passwords across many systems, not ignore passwords altogether.

Actually that brings on another thing.  I want to use a central authentication server, but if that server is inaccessible for some reason (for example, a laptop being used at a remote site) I want it to enforce the last known password for awhile.

So it's evidently a contest between ldap and kerberos.

Thanks, I'll look into them.

---

### Post by Amorphous Serendipity on 2013-10-13
Any LDAP solution should work fine (you may want to use Samba and OpenLDAP). Alternatively, you may want to look into ClearOS. It's more of an all-in-one solution and will most likely have additional features that you do not need, but it would be simple solution for a home office.

Additional information on CleaOS can be found here - ([http://www.clearfoundation.com/](http://www.clearfoundation.com/))

---

### Post by sandyd on 2013-10-13
> **1clue said:**
> I will not use shared ssh keys.  That doesn't solve any problems, it only creates them.

I need to synchronize passwords across many systems, not ignore passwords altogether.

Actually that brings on another thing.  I want to use a central authentication server, but if that server is inaccessible for some reason (for example, a laptop being used at a remote site) I want it to enforce the last known password for awhile.

So it's evidently a contest between ldap and kerberos.

Thanks, I'll look into them.

use ldap (nslcd). If you configure NSCD, you can cache the ldap requests, including the password. This allows you to continue to use the computer as long it hasnt been turned off since the LDAP server failed

Easiest way to configure is to install libpam-ldapd (and dpkg-reconfigure nslcd if the configuration dialog doesn't show up) on the clients - which will auto-setup everything you need.

Make sure that you have the LDAP SSL Cert set in /etc/ldap/ldap.conf as well or else weird things can happen.

---

### Post by 1clue on 2013-10-13
What type of OS is clearOS?  I'm trying to convert a VirtualBox image for KVM.  Is it UNIX, Linux, Other, ??

---

### Post by 1clue on 2013-10-13
Never mind, I got it.

---

