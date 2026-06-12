---
title: "SSSD - dyndns_update = True"
date: 2024-10-05
forum: System76 Support
---

### Post by michaldejmek on 2024-10-05
[SIZE=2][FONT=arial]Hello, 

I have a problem with an automatically created or updated DNS record in Samba 4 (ActiveDirectory). I am using DNS "DNS_INTERNAL".  I have an error in log:  "TSIG error with server: tsig indicates error - update failed: NOTAUTH(BADSIG)" -Has anyone encountered this problem ?
```

[sssd]
domains = domain.net
config_file_version = 2
services = nss, pam
debug_level = 9

[domain/domain.net]
debug_level = 9
id_provider = ad
auth_provider = ad
access_provider = ad
chpass_provider = ad
ldap_id_mapping = True
cache_credentials = True
enumerate = False

dyndns_update = True
dyndns_ttl = 300
dyndns_refresh_interval = 360
dyndns_update_ptr = True
krb5_store_password_if_offline = True

krb5_server = domain.net
krb5_kpasswd = domain.net

ldap_sasl_mech = GSSAPI
ldap_sasl_authid = host/client.domain.net
ldap_krb5_keytab = /etc/krb5.keytab

dns_discovery_domain = domain.net

```

```

[libdefaults]
default_realm = domain.net

kdc_timesync = 1
ccache_type = 4
forwardable = true
proxiable = true

domain.net = {
 }
udp_preference_limit = 0

[realms]

[domain_realm]
.domain.net = domain.net
domain.net = domain.net



```
[/FONT][/SIZE][COLOR=#0E0E0E][FONT=&amp]
Thank you.[/FONT][/COLOR]

---

