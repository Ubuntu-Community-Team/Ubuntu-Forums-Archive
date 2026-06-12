---
title: "Configuring ldaps"
date: 2009-12-17
forum: Server Platforms
---

### Post by ananthaprasada.jps on 2009-12-17
Hi, 

I am configuring ldaps on openldap in Ubuntu 9.04. I have created below certificates and files. 

[LIST]
[*]cacert.pem
[*]server.crt
[*]server.key
[/LIST]

After adding the openldap user to ssl-cert group and restarting the /etc/init.d/slapd service. I am getting this error. 

root@ldapserver:~# /etc/init.d/slapd restart
Stopping OpenLDAP: slapd.
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:///' -g openldap -u openldap -F /etc/ldap/slapd.d/
root@ldapserver:~#

---

