---
title: "Need suggestion for my server - Ubuntu/Redhat server"
date: 2011-02-01
forum: Server Platforms
---

### Post by sajidis11 on 2011-02-01
Hi Every one,
 
I'm new to this forum. I need suggestions from forum members for selecting server OS platform (ubuntu or redhat or sun solaris) for our business network. Currently we have Ubuntu server for our Inventory system and helpdesk ticketing system (glpi) and also want to use Squid proxy server and sarg reports.
 
I want your personal experience using Ubuntu server for business purpose in a big network. Also how if we switch from windows network to all new ubuntu server netwok i mean our domain controller , mail server , database server etc..
 
Thank you...

---

### Post by Thirtysixway on 2011-02-01
You can use samba to setup an Ubuntu domain controller for a windows network.

---

### Post by Simian Man on 2011-02-01
I'd recommend CentOS, a free version of Red Hat Enterprise Linux.  It is rock solid, has great documentation, many IT people are familiar with it and, if you ever need payed support, you can upgrade to RHEL easily.

---

### Post by rudelgurke on 2011-02-01
Dou yourself a favor and keep Windows for the Domain Controller if you've Windows clents running on the network.
Samba can do much, yes, still it can't fully replace a Domain Controller when it comes to remote MSI packages, group policies etc. - short the reason one sets up a domain controller on a Windows network.
If you switch completely from Windows also with your clients, a Unix might be the better choice - LDAP, Kerberos do the job really fine.

About the distro, I highly recommend using a Unix like FreeBSD or a Linux distro with rolling releases. Anything else is pretty much unsuited for a real server.
Debian and all based distro's (like Ubuntu) have the problem to rely on given release cycles. Since maintainers stopped marking security patches for their software as critical, less critical, minimal you can run into the problem running insecure software for a long time on a production system just because the package maintainer overlooked the Changelog and didn't noticed that "patch for exim/smtp.c - fix for a backend ..." is a security related patch that must be used.

Yes - Geeks may workaround this problem, still I'm sure running a large network you've other "geeky" things to do than caring about such things. ;)

So - running Windows clients, use Windows as Domain Controller. For Mailserver, DB server etc. - a Linux distro with rolling releases like Gentoo.
Arch may be another well known distro using rolling releases, still Arch's focus isn't the server, more the desktop, and there's no security mailing list for Arch - even the Arch developers state the desktop is their primary focus.

---

