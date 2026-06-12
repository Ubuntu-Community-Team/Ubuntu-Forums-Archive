---
title: "Kerberos fails on boot"
date: 2017-08-15
forum: Server Platforms
---

### Post by vbowers on 2017-08-15
I have Ubuntu 16.04, running SAMBA as an AD DC. Configuration seemed to go fine, but my Kerberos tests failed. I rebooted the system and noticed that the Kerberos system failed during boot. In reviewing the boot-up log file, the first sign of a problem was:
 
kadmind: kadmind: Configuation file does not specify default realm while initializing, aborting
kadmind: Configuation file does not specify default realm while initializing, aborting
krb5kdc: Configuration file does not specify default realm -  while attempting to retrieve default realm
krb5kdc: krb5kdc: Configuration file does not specify default realm, attempting to retrieve default realm
systemd: krb5-kdc.service: Control process exited, code=exited status=1
systemd: Failed to start Kerberos 5 Key Distribution Center

Here is what I have in my /var/lib/samba/private/krb5.conf:

[libdefaults]
default_realm = EXAMPLE.LOCAL
dns_lookup_realm = false
dns_lookup_kdc = true

[realms]
admin_server = servername
default_domain = example
kdc = servername
master_kdc = servername

[appdefaults]
pam = {
debug = false
ticket_lifetime = 36000
renew_lifetime = 36000
forwardable = true
krb4_convert = false
}


As far as my limited knowledge goes, I have properly set the Kerberos realm in this system. I don't know where I have gone wrong, but obviously somehow I am not passing the realm info on properly. Can anyone give me any suggestions on where to go next?   Thanks!

---

### Post by vbowers on 2017-08-15
Oh, I forgot to mention, I have done a link from the /var/lib/samba/private/krb5.conf file to /etc/krb5.conf. Just in case anyone might suggest that the /etc/krb5.conf file might be the issue. I did not include the [logging] section of my krb5.conf file because I did not see how that could contribute to the primary issue.

---

### Post by thseeger on 2017-08-16
I do not know much about the samba kerberos server, but i would think you need something like 

...
[realms]
  EXAMPLE.LOCAL = {
    kdc = kdc01.example.local
    admin_server = kdc01.example.local
...
  }
...

---

### Post by vbowers on 2017-08-16
thseeger,
Thanks for your reply. My understanding is that my default_realm statement in [libdefaults] eliminates the need to append the domain\realm info from the server name. BUT, just in case I'm all wet, I went ahead and entered your edits to see if it would change anything.

I made the edits, then rebooted the system. I have the same errors occurring as I did previously. The boot log error messages are unchanged. That doesn't mean that your statement is incorrect, it just means it wasn't enough to fix whatever I **do** have wrong.

---

