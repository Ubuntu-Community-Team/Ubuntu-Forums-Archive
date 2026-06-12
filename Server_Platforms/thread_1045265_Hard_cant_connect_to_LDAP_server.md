---
title: "Hard: cant connect to LDAP server"
date: 2009-01-20
forum: Server Platforms
---

### Post by stonneway on 2009-01-20
Hi chaps,

I’m running a Ubuntu Apache server (apache version 2.2.8) which serves up only SVN and TRAC sites. All the SVN and TRAC repos use LDAP to authenticate, and the LDAP server is a Windows Active Directory server on the same network. 

We are seeing a problem with the server giving end users an “internal error” page at random when viewing trac sites or checking out SVN files. If you hit F5 a few times, for between 1 and 10’ish seconds, the pages start being served up again. This isn’t awful in a browser, but for people using SVN via a piece of client software, which may not have an F5 alternative, it’s bad as they just get an error. 

When this occurs the apache error.log shows very little other than “Can’t contact ldap server”. The debug listing from the error.log is below.

****************************
139874420-[Mon Jan 19 18:16:56 2009] [info] Initial (No.1) HTTPS request received for child 4 (server dev.company.com:443)
139874531-[Mon Jan 19 18:16:56 2009] [debug] mod_authnz_ldap.c(373): [client 10.1.37.13] [21455] auth_ldap authenticate: using URL ldap://10.1.37.250:389/OU=Users,OU=Company LLP,DC=company,DC=local?sAMAccountName?sub?(objectClass=*), referer: [https://dev.company.com/trac/technical/report](https://dev.company.com/trac/technical/report)
139874804:[Mon Jan 19 18:16:56 2009] [warn] [client 10.1.37.13] [21455] auth_ldap authenticate: user john.blogs authentication failed; URI /trac/technical/newticket [LDAP: ldap_simple_bind_s() failed][Can't contact LDAP server], referer: [https://dev.company.com/trac/technical/report](https://dev.company.com/trac/technical/report)
139875080-[Mon Jan 19 18:16:56 2009] [debug] ssl_engine_kernel.c(1770): OpenSSL: Write: SSL negotiation finished successfully
139875196-[Mon Jan 19 18:16:56 2009] [info] [client 10.1.37.13] Connection closed to child 4 with standard shutdown (server dev.company.com:443)
139875329-[Mon Jan 19 18:16:56 2009] [info] [client 10.1.37.13] Connection to child 3 established (server dev.company.com:443)
****************************

When this happens, you *can* happily do an ldap-search from the terminal and get valid results, and other boxes which authenticate against the AD server all work fine during this time. It’s just this one box. 

Also, when this happens its ALWAYS directly after a line similar to this which apparently may be odd;

[info] Initial (No.1) HTTPS request received for child x (server dev.company.com:443)

The LDAP params we are using in the apache conf is;

*****************************
<Location />
  AuthType Basic
  AuthBasicProvider ldap
  AuthzLDAPAuthoritative on
  AuthLDAPBindDN "CN=LDAP USER,CN=Users,DC=company,DC=local"
  AuthLDAPBindPassword PASSWORD
  AuthLDAPURL "ldap://10.1.37.250:389/OU=Users,OU=Company LLP,DC=company,DC=local?sAMAccountName?sub?(objectClass=*)" NONE
  AuthLDAPGroupAttributeIsDN on
</Location>
*****************************

I’ve changed a few of the LDAP cacheing entries in order to rule out some kind of connection-limit issue, but that hasnt helped a bit. The LDAP config we are using now in apache2.conf is this;

*****************************
LDAPSharedCacheSize 200000
LDAPCacheEntries 2024
LDAPCacheTTL 3600
LDAPOpCacheEntries 2024
LDAPOpCacheTTL 600
LDAPConnectionTimeout 60

LDAPVerifyServerCert Off

<Location /ldap/cache-info>
          SetHandler ldap-status
</Location>
***************************

There’s a few bugs on the Ubuntu site which relate mainly to the version of libgnutls13 ([https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/306897](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/306897)). According to the results of “aptitude search libgnutls13” I’m already running that – that is to say that the results of that command show “i   libgnutls13” which I take to mean that libgnutls13 is installed. Also, we arent using SSL or TLS for the LDAP authentication between the ubuntu box and the LDAP server so I’m not sure it applies.

Any idea how I can find out more about what’s happening or even better how I can resolve the issue? We’ve been at this about a week now, every day for 8 hours or more and could do with any advice you can give. 

I’m wondering whether we have found a bug of sorts, as no one who we get involved can find any reason for this happening.

Olly

---

