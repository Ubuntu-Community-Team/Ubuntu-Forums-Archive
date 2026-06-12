---
title: "LDAP Client Auth."
date: 2008-05-21
forum: Server Platforms
---

### Post by sbutton on 2008-05-21
Hi,

I'm trying to get Ubuntu 8.04 to authenticate against an OpenLDAP server we have here (which I installed last week on RedHat and is working OK with RedHat and HP-UX clients)... but Ubuntu just doesn't want to play. 

I've installed the relevant packages using the instructions in [LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication") but I can't work out why it's not talking to the LDAP server. 

Before I installed the packages there was already an /etc/ldap/ldap.conf, but now there is also a /etc/ldap.conf, and I've tried filling in both of these with the server details, but still I get this...

# ldapsearch -vv -x -b 'dc=company,dc=com' '(objectclass=*)'
ldap_initialize( <DEFAULT> )
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

I've also tried with -d1 option, which tells me it's not picking up the correct server to bind to....


# ldapsearch -vv -x -b 'dc=company,dc=com' '(objectclass=*)' -d1
ldap_initialize( <DEFAULT> )
ldap_create
ldap_sasl_bind
ldap_send_initial_request
ldap_new_connection 1 1 0
ldap_int_open_connection
ldap_connect_to_host: TCP localhost:389
ldap_new_socket: 3
ldap_prepare_socket: 3
ldap_connect_to_host: Trying 127.0.0.1:389
ldap_pvt_connect: fd: 3 tm: -1 async: 0
ldap_close_socket: 3
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

How do I tell which ldap.conf it's trying to use (perhaps it should be somewhere else completely? - I've tried different debug levels, 7,15...255 but don't get much more verbosity)

Here's my (snipped) ldap.conf...

# egrep -v -e "^#|^$" /etc/ldap.conf
host my_ldap_host
base dc=company,dc=com
uri ldapi:///my_ldap_host
ldap_version 3
rootbinddn cn=Manager,dc=company,dc=com
pam_password md5

Thanks,

Steve

---

### Post by bluefrog on 2008-05-21
rootbinddn is admin not manager in latest ubuntu but you are using redhat so it is maybe still Manager.
get rid of uri ldapi eventually

---

### Post by sbutton on 2008-05-22
> **bluefrog said:**
> rootbinddn is admin not manager in latest ubuntu but you are using redhat so it is maybe still Manager.
get rid of uri ldapi eventually

Manager is correct, and you can set that to be whatever you like, on Red Hat or Ubuntu (on the LDAP server).

The URI is the new way of specifying the server, and "host" is the obsolete (but still supported) way... but I've tried either/both and it still doesn't help.

Steve

---

### Post by bluefrog on 2008-05-22
of course you can change the rdn, I just meant that on ubuntu it is admin by default when you install slapd (and you must change it by hand afterwards if not happy with it).

on a ubuntu client my tests gave the following

**ldapsearch will work with /etc/ldap/ldap.conf as follows (complete file)**
base my-base
uri ldap://my-ldap-srv-IP

**ldap authentication will work with /etc/ldap.conf(snipped file)**
base my-base
uri ldap://my-ldap-srv-IP
bind_policy soft #(to reduce the login time, bug reported)

uri ldapi:///IP is maybe the new stuff around but it doesn't work (at least with ubuntu, will check if a bug has been reported)

---

### Post by sbutton on 2008-05-22
> **bluefrog said:**
> of course you can change the rdn, I just meant that on ubuntu it is admin by default when you install slapd (and you must change it by hand afterwards if not happy with it).

on a ubuntu client my tests gave the following

**ldapsearch will work with /etc/ldap/ldap.conf as follows (complete file)**
base my-base
uri ldap://my-ldap-srv-IP

**ldap authentication will work with /etc/ldap.conf(snipped file)**
base my-base
uri ldap://my-ldap-srv-IP
bind_policy soft #(to reduce the login time, bug reported)

uri ldapi:///IP is maybe the new stuff around but it doesn't work (at least with ubuntu, will check if a bug has been reported)

Thanks for you help with this. 

I've just run strace on my ldapsearch command, which confirms it's reading /etc/ldap/ldap.conf, as you say. It's also reading /etc/host.conf and /etc/resolv.conf, so I thought perhaps it needs the FQDN as returned by nslookup and I've tried putting that into the host line in ldap.conf... 

but still no joy. :-(

This is crazy that it uses a different ldap.conf for ldapsearch, to the one for authentication... this could cause immense confusion, but anyway is not the cause of my problems here. I guess i'll just put a symlink in to avoid future headaches. 

Now where's that banging head against the wall smiley?

Steve

---

### Post by elesueur on 2008-07-16
I know it's late, but I believe URI's require a trailing slash.

---

