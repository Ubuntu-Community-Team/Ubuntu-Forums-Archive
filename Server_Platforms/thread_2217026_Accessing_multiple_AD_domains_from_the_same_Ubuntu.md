---
title: "Accessing multiple AD domains from the same Ubuntu Laptop with kerberos"
date: 2014-04-15
forum: Server Platforms
---

### Post by miguelpires on 2014-04-15
Hello all,
I'm administrating 3 servers with Openldap+Samba4. The method to authentication is with sssd+pam_mount.

If i do kinit "nameoftheuser"@SERVER-DOMAIN.LAN i can access the shares that the user have permission, but i can't test the login of the user.

Basically my question is:
- How can I access multiple domains from the same Laptop with sssd and pam? Can I put all servers in the files bellow?

Best regards
Miguel
PS: The files

   /etc/krb5.conf

 

 [libdefaults]  

         default_realm = SERVERNAME-DOMAIN.LAN  

         dns_lookup_kdc = true  

         dns_lookup_realm = true  

 

 

 

 /etc/sssd/sssd.conf
 [sssd]  
 config_file_version = 2  
 services = nss, pam  
 domains = SERVERNAME-DOMAIN.LAN  

 sbus_timeout = 30  

 #debug_level = 8  

 

 [nss]  

 filter_users = root  

 filter_groups = root  

 reconnection_retries = 3  

 

 [pam]  

 reconnection_retries = 3  

 offline_credentials_expiration = 0  

 

 [domain/SERVERNAME-DOMAIN.LAN]  

 min_id = 1000  

 id_provider = ldap  

 auth_provider = krb5  

 chpass_provider = krb5  

 ldap_schema = rfc2307bis  

 ldap_uri = ldap://servername-domain.lan:390  

 ldap_search_base = dc=servername-domain,dc=lan  

 cache_credentials = true  

 enumerate = true  

 krb5_server = servername-domain.lan:8880  

 krb5_realm= SERVERNAME-DOMAIN.LAN  

 ldap_default_bind_dn = cn=zentyalro,dc=servername-domain,dc=lan  

 ldap_default_authtok_type = password  

 ldap_default_authtok = the pass of ldap

---

### Post by miguelpires on 2014-04-17
No one have cross a situation like this?

---

