---
title: "Fedora 11 help."
date: 2009-07-05
forum: The Cafe
---

### Post by waloshin on 2009-07-05
The fedora forum is a little slow so:

I have an Lamp server installed. 

I tried to add a password to the root account on the Mysql , but it said their was not a mysql.users database. 

And how do I change the apache listen port from 80 to say something like 8080. 

------------------------------------------------------------------------------------

Of coarse Selinux annoyance:


Summary:

SELinux is preventing the http daemon from connecting to the itself or the relay
ports

Detailed Description:

SELinux has denied the http daemon from connecting to itself or the relay ports.
An httpd script is trying to do a network connect to an http/ftp port. If you
did not setup httpd to network connections, this could signal a intrusion
attempt.

Allowing Access:

If you want httpd to connect to httpd/ftp ports you need to turn on the
httpd_can_network_relay boolean: "setsebool -P httpd_can_network_relay=1"

Fix Command:

setsebool -P httpd_can_network_relay=1

Additional Information:

Source Context unconfined_u:system_r:httpd_t:s0
Target Context system_u:object_r:ftp_port_t:s0
Target Objects None [ tcp_socket ]
Source httpd
Source Path /usr/sbin/httpd
Port 21
Host server
Source RPM Packages httpd-2.2.11-8
Target RPM Packages 
Policy RPM selinux-policy-3.6.12-53.fc11
Selinux Enabled True
Policy Type targeted
MLS Enabled True
Enforcing Mode Enforcing
Plugin Name httpd_can_network_relay
Host Name server
Platform Linux server 2.6.29.5-191.fc11.i686.PAE #1 SMP Tue
Jun 16 23:19:53 EDT 2009 i686 athlon
Alert Count 10
First Seen Sun 05 Jul 2009 12:34:28 AM CST
Last Seen Sun 05 Jul 2009 12:38:02 AM CST
Local ID f18b1582-536f-4fca-a1a9-209f10574831
Line Numbers 

Raw Audit Messages 

node=server type=AVC msg=audit(1246775882.329:44618): avc: denied { name_connect } for pid=2653 comm="httpd" dest=21 scontext=unconfined_u:system_r:httpd_t:s0 tcontext=system_u:object_r:ftp_port_t:s0 tclass=tcp_socket

node=server type=SYSCALL msg=audit(1246775882.329:44618): arch=40000003 syscall=102 success=no exit=-13 a0=3 a1=bfa9bd60 a2=61eca68 a3=11 items=0 ppid=2648 pid=2653 auid=500 uid=48 gid=48 euid=48 suid=48 fsuid=48 egid=48 sgid=48 fsgid=48 tty=(none) ses=1 comm="httpd" exe="/usr/sbin/httpd" subj=unconfined_u:system_r:httpd_t:s0 key=(null)


Thanks

---

