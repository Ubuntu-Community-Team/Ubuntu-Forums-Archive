---
title: "PHPldapadmin + ldaps"
date: 2009-10-10
forum: Server Platforms
---

### Post by jagnikam on 2009-10-10
Hey guys, 

please help me for configuring phpldapadmin to connect ldaps server. 

Phpldapadmin config file : 
$ldapservers->SetValue($i,'server','host','ldaps://localhost/');
$ldapservers->SetValue($i,'server','port','636');
$ldapservers->SetValue($i,'server','tls',false);

Getting error 
Could not start TLS. Please check your LDAP server configuration.

Thank In Advance.....

---

### Post by Despot on 2009-10-10
I would check to make sure your Apache/PHP user has access to the appropriate access, and restarting the apache daemon. Sometimes rebooting the whole server can clear up odd errors like that as well.

You might find useful info in the Apache logs.

Also, if you have an authentication mech set up through SASL, that might be interfering if you don't have PLA configured to handle it correctly. I'd check set the loglevel of slapd to 256 (connections) and then do a "tail -f" of your slapd log (/var/log/syslog by default) while you try to connect in PHPldapAdmin

You may have more luck using TLS instead of SSL.

---

