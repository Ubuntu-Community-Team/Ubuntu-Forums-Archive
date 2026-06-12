---
title: "Domain Logon Samba 22.04 error"
date: 2024-05-21
forum: Server Platforms
---

### Post by stevehenderson710 on 2024-05-21
Created a ubuntu dc with Samba 4 on Ubuntu 22.04.
Followed the steps here:  [https://www.considerednormal.com/2022/11/samba-based-active-directory-on-ubuntu-22-04/](https://www.considerednormal.com/2022/11/samba-based-active-directory-on-ubuntu-22-04/)
Able to add user to the system and no errors during configuration.
--
Created a standard Ubuntu 22.04 test server

Test Server can't discover with: realm discover 
  output: No default domain received via DHCP or given by hostname
              realm: No default realm discovered

but running: realm discover --verbose mydomain.xxx returns the below.
  *Resolving:_ldap._tcp.mydomain.xxx
  * resolving: mydomain.xxx
  * No results: mydomain.xxx

mydomain.xxx
type: kerberos
realm-name: mydomain.xxx
domain-name: mydomain.xxx
configured: kerberos-member
serversoftware: active-directory
client-software: sssd
required-package: sssd-tools
required-package: sssd
required-package: libnss-sss
required-package: libpam-sss
required-package:  adclit
required-package: samba-common-bin
login-formats: %U@mydomain.xxx
login-policy: allow-realm-logins

I can joins with: sudo realm join -U Administrator IPaddress.
Can ping. DC and test server have manual IPs (Address, Netmask; No Gateway, No DNS set)

running nslookup on the test server: nslookup dcserver.mydomain.xxx returns:
Server:  127.0.0.53
address:  127.0.0.53#53

Name:  dcserver.mydomain.xxx
Address: ip of dcserver

No firewall are running on test server or DC.

I don't have a DNS server setup.  Just testing a ubuntu dc option.  Shouldn't I be able to log on with [EMAIL="userename@dcip.xxx"]userename@dcip.xxx[/EMAIL] ?  I tried all sort of logon formats but i can't logon on the domain on the test server.  any ideas what I'm missing?

The log on error I'm getting (on test server, trying to log on to domain) is:
   Sorry, password authentication did work.
   Please try again.

---

### Post by stevehenderson710 on 2024-05-21
resolved it...

I had to edit the /etc/resolv.conf accordingly and point to the dc

---

### Post by coffeecat on 2024-05-21
Not a chat thread. *Thread moved to **Server Platforms**.*

---

### Post by MAFoElffen on 2024-05-23
SO as I suspected, it is a DNS error? Where the DNS is not seeing your Samba DC... by a named service but can see it via IP.

---

