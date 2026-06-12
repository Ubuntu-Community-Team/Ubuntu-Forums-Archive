---
title: "FreeRADIUS + OpenLDAP (with TLS) returning Connection Error"
date: 2011-08-31
forum: Server Platforms
---

### Post by viniciusferrao on 2011-08-31
Hi folks,

I'm trying to set up a FreeRADIUS 2 server with a TLS connection to a LDAP Server.

But... TLS does not appears to work correctly, and I cannot debug it myself.

Can someone help-me with this?

Extra-infos:
/etc/freeradius/modules/ldap [Removed some useless info]

ldap {
       #
       #  Note that this needs to match the name in the LDAP
       #  server certificate, if you're using ldaps.
       server = "lol.risos.kkk"
       #  389 for ldap or 636 for ldaps
       port = 389
       identity = "cn=admin,dc=XX,dc=XX,dc=XX"
       password = lol
       basedn = "ou=people,dc=XX,dc=XX,dc=XX"
       filter = "(uid=%{%{Stripped-User-Name}:-%{User-Name}})"
       base_filter = "(objectclass=radiusprofile)"	

       tls {
               # Set this to 'yes' to use TLS encrypted connections
               # to the LDAP database by using the StartTLS extended
               # operation.
               #                       
               # The StartTLS operation is supposed to be
               # used with normal ldap connections instead of
               # using ldaps (port 689) connections
               start_tls = yes

               cacertfile      = /etc/freeradius/certs/ca.crt
               cacertdir       = /etc/freeradius/certs/
               certfile        = /etc/freeradius/certs/server.crt
               keyfile         = /etc/freeradius/certs/server.key
               randfile        = /etc/freeradius/certs/random
	}
}

What happens in when I invoke freeradius -X:

 [ldap] ldap_get_conn: Checking Id: 0
 [ldap] ldap_get_conn: Got Id: 0
 [ldap] attempting LDAP reconnection
 [ldap] (re)connect to XXXX.XX.XX.XX:389, authentication 0
 [ldap] setting TLS CACert File to /etc/freeradius/certs/ca.crt
 [ldap] setting TLS CACert Directory to /etc/freeradius/certs/
 [ldap] setting TLS Cert File to /etc/freeradius/certs/server.crt
 [ldap] setting TLS Key File to /etc/freeradius/certs/server.key
 [ldap] setting TLS Key File to /etc/freeradius/certs/random
 [ldap] starting TLS
 [ldap] ldap_start_tls_s()
 [ldap] could not start TLS Connect error
 [ldap] (re)connection attempt failed
[ldap] search failed
 [ldap] ldap_release_conn: Release Id: 0
++[ldap] returns fail

Thanks in advance,
Vinícius Ferrão

---

