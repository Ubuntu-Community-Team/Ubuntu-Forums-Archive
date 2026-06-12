---
title: "Help to join an Ubuntu 12.04 server to a W2k domain"
date: 2014-02-21
forum: Server Platforms
---

### Post by Carlos Pena on 2014-02-21
Hello to everybody in the forum.

I am trying to join a ubuntu server as a member of a domain controlled by a Windows 2000 Server.

When i execute the join the system return de followin error:

sudo net ads join -U administrator
Enter administrator's password:
Using short domain name -- FAMILY
Joined 'CHILD-SERVER' to realm 'Family.local'
net_update_dns_internal: Failed to connect to our DC!
DNS update failed!

Can anybody help me? Any ideas?

Sincerely,

Carlos

****************************************************
Here is the detailed information about my installation.


Domain      = FAMILY.LOCAL

DC
Server Name = PARENT-SERVER
IP          = 26.4.0.1
OS          = Windows 2000 Server
Admin User  = administrator


Member Server to be Joined to the Domain
Server Name = CHILD-SERVER
IP          = 26.4.0.2
OS          = Ubuntu 12.04
Admin User  = administrator



*************************************************************************
/etc/hosts

127.0.0.1 CHILD-SERVER CHILD-SERVER.FAMILY.LOCAL localhost
26.4.0.1 PARENT-SERVER PARENT-SERVER.FAMILY.LOCAL
26.4.0.2 CHILD-SERVER CHILD-SERVER.FAMILY.LOCAL

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

**************************************************************************
/etc/krb5.conf

[libdefaults]
        default_realm = FAMILY.LOCAL
        ticket_lifetime = 24000
        clock_skew = 300


[realms]
        FAMILY.LOCAL = {
                kdc = PARENT-SERVER.FAMILY.LOCAL
                admin_server = PARENT-SERVER.FAMILY.LOCAL
                default_domain = FAMILY.LOCAL
        }


[domain_realm]
        .family.local = FAMILY.LOCAL
        family.local = FAMILY.LOCAL


********************************************************************************
/etc/samba/smb.conf

[global]
   security = ads
   realm = FAMILY.LOCAL
   password server = 26.4.0.1
   workgroup = FAMILY
   server string = %h server (Samba, Ubuntu)
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   winbind enum users = yes
   winbind enum groups = yes
   winbind cache time = 10
   winbind use default domain = yes

   client use spnego = yes
   client ntlmv2 auth = yes
   encrypt passwords = true
   restrict anonymous = 2

   domain master = no
   local master = no
   preferred master = no
   os level = 0

[OurShare]
   commend = Our Share
   valid users = @FAMILY\PEOPLE, FAMILY/ADMINISTRATOR, administrator
   admin users = FAMILY/ADMINISTRATOR, administrator
   browseable = no
   path = /OurShare
   read only = no
   public = no
   force create mode = 777
   create mask = 777
   security mask = 777
   force security mode = 777

   directory mask = 2777
   force directory mode = 2777
   directory security mask = 2777
   force directory security mode = 2777

---

### Post by lingpanda on 2014-02-21
Maybe the Samba Wiki on this topic can help you.

[https://wiki.samba.org/index.php/Samba/Domain_Member](https://wiki.samba.org/index.php/Samba/Domain_Member)

---

