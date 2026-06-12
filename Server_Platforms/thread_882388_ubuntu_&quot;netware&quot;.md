---
title: "ubuntu &quot;netware&quot;"
date: 2008-08-06
forum: Server Platforms
---

### Post by richardd2137 on 2008-08-06
I was wondering if there was an novell netware like application? Like Delevering applications, *assigned* network drives, and printers. But I recently looked into the [hannibal]("http://hannibal.solstice.nl/") and I was thinking about putting together a big package of OpenSource software. Heres Hannibal's list modified by me
The technical documents below describe the complete Hannibal stack. Starting to build from the top, all dependencies should be met. 

Foundation modules
Operatingsystem Base (A Debian-Linux system and ip-numberplan convention)
DNS and DHCP
Time server
Centralized syslog server
LDAP autorisation (client)
Certificate Authority
Basic modules
Redhat/Fedora LDAP directory server
File server (SMB/CIFS/NFS/FTP/WebDAV)
E-mail server
Postfix (MTA)
Cyrus (mail-store)
Apache web server
Gosa usermanagement tool
Optional modules
OpenVPN server
Webmail
Squid Proxy server
Reverse-proxy (Loadbalancing/HTTP-accelerator)
Documentation wiki
Hardware inventory system (OCS Inventory)
IT-Servicedesk Trouble Ticket System (GLPI)
Instant Messaging (Jabber XMPP-daemon)
Organisation wide Calendar server (no standard solution yet)
LDAP-administration (tools to maintain the LDAP-database content)
Monitoring (Nagios and Centreon)
Development server
Miscellaneous modules
Financial accounting (sql-ledger.org/eekboek.nl)
PHPaga server (Billing/Invoicing for small businesses)
Database server (MySQL server)
CRM/ERP (OpenBravo)
Project planning(eGroupware)
Timesheet administration(eGroupware)
Mailinglist manager(PHPlist)
Network backup (Backup-pc and Bacula)
Local apt repository mirror (local mirror of the debian software repository).
Firewall(standard linux firewall)
VOIP telephony
Application Delevery
....
But my question was before I started to put together and document this is that is there a sloution like this already?
When I get the site up I will post a link so that people can help me.
--
thanks,
Richard

---

### Post by windependence on 2008-08-07
This is going to be quite a bit to run on a single machine, even with lots of juice.

-Tim

---

