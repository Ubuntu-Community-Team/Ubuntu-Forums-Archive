---
title: "DNS Update Failed!"
date: 2010-09-30
forum: Server Platforms
---

### Post by kinitsu on 2010-09-30
root@test:~# net ads join -U admin
Enter admin's password:
Using short domain name -- JUDICIALSERVICE
Joined 'TEST' to realm 'judicialservices.net'
DNS update failed!


I had it working before on a previous install the other day. The reason I reinstalled was to test my ability to replicate my ability to setup  linux proxy servers on my AD. Unfortunately I forgot how I fixed on my last working set. I remember that is has something to do with my Hosts file. So can I get help getting the hosts file setup properly to get my DNS to update.


Current hosts file:

127.0.0.1    test.judicialservices.net test.judicialservices.net test
192.168.6.103    test.judicialservices.net test.judicialservices.net test

---

### Post by SeijiSensei on 2010-09-30
replace the entries for 127.0.0.1 with "localhost.localdomain localhost"

Since both lines provide an IP address for test.judicialservices.net, my guess it that it's using the local interface.

Are you just trying to replicate the DNS on the AD server onto a Linux DNS server?  If so, it's a lot easier to make the Linux server a DNS slave to the AD box.

---

### Post by kinitsu on 2010-09-30
the AD server is the main box everything else operates under it. And it still fails to update the DNS. The AD server is also a DNS server so I am pointed to it for the DNS.

---

### Post by SeijiSensei on 2010-09-30
You mean that the AD server doesn't add the Linux box to its DNS tables?  The easiest solution for that is to assign the Linux box a static IP address and create a manual entry for it in the Microsoft DNS server software on the AD box.  That's how I handled getting a DNS record set up for other Linux servers I have running in clients' AD environments.

---

### Post by kinitsu on 2010-09-30
I got to to work before without having to do that, but me and my desire to make sure I can replicate setups and my stupidity to not backup the config and hosts files to save time I am stuck on this step again. Anywho, I'll try manually setting the DNS in the microsoft server side.  I hope this workd and I will remember to back up known good configurations before I try to replicate my success again.

Alright I have assigned my linux box the local static of 192.168.6.13 and manually added it to the DNS and i still get DNS updat Failed! Also, changed the hostname to proxy from test since this will be my proxy server. I updated the hostname and hosts files accordingly.

But it does add me to the AD but not the dns.

root@test:~# net ads join -U admin
Enter admin's password:
Using short domain name -- JUDICIALSERVICE
Joined 'PROXY' to realm 'judicialservices.net'
DNS update failed!

---

### Post by kinitsu on 2010-10-01
in prospects of this helping here is a debug lvl 10 run with net ads dns register

> root@proxy:~# net ads dns register -P -d 10
[2010/10/01 11:20:42,  5] lib/debug.c:407(debug_dump_status)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
    registry: False/0
[2010/10/01 11:20:42,  3] param/loadparm.c:9039(lp_load_ex)
  lp_load_ex: refreshing parameters
[2010/10/01 11:20:42,  3] param/loadparm.c:4848(init_globals)
  Initialising global parameters
[2010/10/01 11:20:42,  2] param/loadparm.c:4707(max_open_files)
  rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
[2010/10/01 11:20:42,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/10/01 11:20:42,  3] param/loadparm.c:7726(do_section)
  Processing section "[global]"
  doing parameter workgroup = judicialservice
  doing parameter password server = JCSCORP000.judicialservices.net
  doing parameter realm = JUDICIALSERVICES.NET
  doing parameter security = ads
  doing parameter idmap uid = 16777216-33554431
  doing parameter idmap gid = 16777216-33554431
  doing parameter template shell = /bin/bash
  doing parameter winbind use default domain = true
  doing parameter winbind offline logon = false
  doing parameter client ldap sasl wrapping = sign
  doing parameter winbind enum users = yes
  doing parameter winbind enum groups = yes
  doing parameter obey pam restrictions = yes
  doing parameter allow trusted domains = no
  doing parameter idmap backend = idmap_rid:judicialservices=16777216-33554431
  doing parameter server string = Linux Samba File Server
  doing parameter passdb backend = tdbsam
  doing parameter load printers = yes
  doing parameter cups options = raw
[2010/10/01 11:20:42,  4] param/loadparm.c:9074(lp_load_ex)
  pm_process() returned Yes
[2010/10/01 11:20:42,  7] param/loadparm.c:9279(lp_servicenumber)
  lp_servicenumber: couldn't find homes
[2010/10/01 11:20:42, 10] param/loadparm.c:8287(set_server_role)
  set_server_role: role = ROLE_DOMAIN_MEMBER
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2LE
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2LE
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16LE
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16LE
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS-2BE
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS-2BE
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-16BE
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-16BE
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF8
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF8
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UTF-8
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UTF-8
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ASCII
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ASCII
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset 646
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset 646
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset ISO-8859-1
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset ISO-8859-1
[2010/10/01 11:20:42,  5] lib/iconv.c:104(smb_register_charset)
  Attempting to register new charset UCS2-HEX
[2010/10/01 11:20:42,  5] lib/iconv.c:112(smb_register_charset)
  Registered charset UCS2-HEX
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/util.c:266(init_names)
  Netbios name list:-
  my_netbios_names[0]="PROXY"
[2010/10/01 11:20:43,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=fe80::216:76ff:fecc:90f4%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
[2010/10/01 11:20:43,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=192.168.6.103 bcast=192.168.6.255 netmask=255.255.255.0
[2010/10/01 11:20:43,  6] libads/ldap.c:346(ads_find_dc)
  ads_find_dc: (ldap) looking for realm 'JUDICIALSERVICES.NET'
[2010/10/01 11:20:43,  5] lib/gencache.c:61(gencache_init)
  Opening cache file at /var/run/samba/gencache.tdb
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43,  4] libsmb/namequery_dc.c:73(ads_dc_name)
  ads_dc_name: domain=JUDICIALSERVICE
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43,  6] libads/ldap.c:366(ads_find_dc)
  ads_find_dc: (cldap) looking for realm 'JUDICIALSERVICES.NET'
[2010/10/01 11:20:43,  8] libsmb/namequery.c:2156(get_sorted_dc_list)
  get_sorted_dc_list: attempting lookup for name JUDICIALSERVICES.NET (sitename Default-First-Site-Name) using [ads]
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = SAFJOIN/DOMAIN/JUDICIALSERVICES.NET, value = JCSCORP000.judicialservices.net, timeout = Fri Oct  1 11:57:55 2010
[2010/10/01 11:20:43,  5] libsmb/namequery.c:185(saf_fetch)
  saf_fetch[join]: Returning "JCSCORP000.judicialservices.net" for "JUDICIALSERVICES.NET" domain
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1972(get_dc_list)
  get_dc_list: preferred server list: "JCSCORP000.judicialservices.net, JCSCORP000.judicialservices.net"
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning expired cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:05:14 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:208(namecache_fetch)
  no entry for JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1225(resolve_lmhosts)
  resolve_lmhosts: Attempting lmhosts lookup for name JCSCORP000.judicialservices.net<0x20>
[2010/10/01 11:20:43,  4] libsmb/namequery.c:839(startlmhosts)
  startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1089(resolve_wins)
  resolve_wins: Attempting wins lookup for name JCSCORP000.judicialservices.net<0x20>
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1093(resolve_wins)
  resolve_wins: WINS server resolution selected and no WINS servers listed.
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1307(resolve_hosts)
  resolve_hosts: Attempting host lookup for name JCSCORP000.judicialservices.net<0x20>
[2010/10/01 11:20:43, 10] libsmb/namequery.c:583(remove_duplicate_addrs2)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2010/10/01 11:20:43,  5] libsmb/namecache.c:122(namecache_store)
  namecache_store: storing 1 address for JCSCORP000.judicialservices.net#20: 192.168.6.18
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20; value = 192.168.6.18:0 and timeout = Fri Oct  1 11:31:43 2010
   (660 seconds ahead)
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1653(internal_resolve_name)
  internal_resolve_name: returning 1 addresses: 192.168.6.18:0 
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:31:43 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:212(namecache_fetch)
  name JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] libsmb/namequery.c:583(remove_duplicate_addrs2)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2105(get_dc_list)
  get_dc_list: returning 1 ip addresses in an ordered list
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2106(get_dc_list)
  get_dc_list: 192.168.6.18:389 
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43,  5] libads/ldap.c:203(ads_try_connect)
  ads_try_connect: sending CLDAP request to 192.168.6.18 (realm: JUDICIALSERVICES.NET)
[2010/10/01 11:20:43, 10] libads/dns.c:778(sitename_store)
  sitename_store: realm = [JUDICIALSERVICE], sitename = [Default-First-Site-Name], expire = [2147483647]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = AD_SITENAME/DOMAIN/JUDICIALSERVICE; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (861537204 seconds ahead)
[2010/10/01 11:20:43, 10] libads/dns.c:778(sitename_store)
  sitename_store: realm = [judicialservices.net], sitename = [Default-First-Site-Name], expire = [2147483647]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (861537204 seconds ahead)
[2010/10/01 11:20:43,  3] libads/ldap.c:621(ads_connect)
  Successfully contacted LDAP server 192.168.6.18
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libads/ldap.c:165(ads_closest_dc)
  ads_closest_dc: NBT_SERVER_CLOSEST flag set
[2010/10/01 11:20:43, 10] libads/kerberos.c:853(create_local_private_krb5_conf_for_domain)
  create_local_private_krb5_conf_for_domain: fname = /var/run/samba/smb_krb5/krb5.conf.JUDICIALSERVICE, realm = JUDICIALSERVICES.NET, domain = JUDICIALSERVICE
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = SAFJOIN/DOMAIN/JUDICIALSERVICES.NET, value = JCSCORP000.judicialservices.net, timeout = Fri Oct  1 11:57:55 2010
[2010/10/01 11:20:43,  5] libsmb/namequery.c:185(saf_fetch)
  saf_fetch[join]: Returning "JCSCORP000.judicialservices.net" for "JUDICIALSERVICES.NET" domain
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1972(get_dc_list)
  get_dc_list: preferred server list: "JCSCORP000.judicialservices.net, JCSCORP000.judicialservices.net"
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:31:43 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:212(namecache_fetch)
  name JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:31:43 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:212(namecache_fetch)
  name JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] libsmb/namequery.c:583(remove_duplicate_addrs2)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2105(get_dc_list)
  get_dc_list: returning 1 ip addresses in an ordered list
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2106(get_dc_list)
  get_dc_list: 192.168.6.18:389 
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = SAFJOIN/DOMAIN/JUDICIALSERVICES.NET, value = JCSCORP000.judicialservices.net, timeout = Fri Oct  1 11:57:55 2010
[2010/10/01 11:20:43,  5] libsmb/namequery.c:185(saf_fetch)
  saf_fetch[join]: Returning "JCSCORP000.judicialservices.net" for "JUDICIALSERVICES.NET" domain
[2010/10/01 11:20:43,  3] libsmb/namequery.c:1972(get_dc_list)
  get_dc_list: preferred server list: "JCSCORP000.judicialservices.net, JCSCORP000.judicialservices.net"
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:31:43 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:212(namecache_fetch)
  name JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2010/10/01 11:20:43,  5] libads/dns.c:817(sitename_fetch)
  sitename_fetch: Returning sitename for JUDICIALSERVICES.NET: "Default-First-Site-Name"
[2010/10/01 11:20:43, 10] libsmb/namequery.c:1506(internal_resolve_name)
  internal_resolve_name: looking up JCSCORP000.judicialservices.net#20 (sitename Default-First-Site-Name)
[2010/10/01 11:20:43, 10] lib/gencache.c:208(gencache_get)
  Returning valid cache entry: key = NBT/JCSCORP000.JUDICIALSERVICES.NET#20, value = 192.168.6.18:0, timeout = Fri Oct  1 11:31:43 2010
[2010/10/01 11:20:43,  5] libsmb/namecache.c:212(namecache_fetch)
  name JCSCORP000.judicialservices.net#20 found.
[2010/10/01 11:20:43, 10] lib/gencache.c:194(gencache_get)
  Cache entry with key = NEG_CONN_CACHE/JUDICIALSERVICES.NET,192.168.6.18 couldn't be found
[2010/10/01 11:20:43,  9] libsmb/conncache.c:150(check_negative_conn_cache)
  check_negative_conn_cache returning result 0 for domain JUDICIALSERVICES.NET server 192.168.6.18
[2010/10/01 11:20:43, 10] libsmb/namequery.c:583(remove_duplicate_addrs2)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2105(get_dc_list)
  get_dc_list: returning 1 ip addresses in an ordered list
[2010/10/01 11:20:43,  4] libsmb/namequery.c:2106(get_dc_list)
  get_dc_list: 192.168.6.18:389 
[2010/10/01 11:20:43, 10] libads/kerberos.c:804(get_kdc_ip_string)
  get_kdc_ip_string: Returning     kdc = 192.168.6.18
  
[2010/10/01 11:20:43,  5] libads/kerberos.c:921(create_local_private_krb5_conf_for_domain)
  create_local_private_krb5_conf_for_domain: wrote file /var/run/samba/smb_krb5/krb5.conf.JUDICIALSERVICE with realm JUDICIALSERVICES.NET KDC list =     kdc = 192.168.6.18
  
[2010/10/01 11:20:43,  4] libsmb/namequery_dc.c:143(ads_dc_name)
  ads_dc_name: using server='JCSCORP000.JUDICIALSERVICES.NET' IP=192.168.6.18
[2010/10/01 11:20:43,  5] libads/ldap.c:203(ads_try_connect)
  ads_try_connect: sending CLDAP request to JCSCORP000.JUDICIALSERVICES.NET (realm: JUDICIALSERVICES.NET)
[2010/10/01 11:20:43, 10] libads/dns.c:778(sitename_store)
  sitename_store: realm = [JUDICIALSERVICE], sitename = [Default-First-Site-Name], expire = [2147483647]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = AD_SITENAME/DOMAIN/JUDICIALSERVICE; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (861537204 seconds ahead)
[2010/10/01 11:20:43, 10] libads/dns.c:778(sitename_store)
  sitename_store: realm = [judicialservices.net], sitename = [Default-First-Site-Name], expire = [2147483647]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = AD_SITENAME/DOMAIN/JUDICIALSERVICES.NET; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (861537204 seconds ahead)
[2010/10/01 11:20:43,  3] libads/ldap.c:621(ads_connect)
  Successfully contacted LDAP server 192.168.6.18
[2010/10/01 11:20:43, 10] libads/ldap.c:62(ldap_open_with_timeout)
  Opening connection to LDAP server 'JCSCORP000.judicialservices.net:389', timeout 15 seconds
[2010/10/01 11:20:43, 10] libads/ldap.c:76(ldap_open_with_timeout)
  Connected to LDAP server 'JCSCORP000.judicialservices.net:389'
[2010/10/01 11:20:43,  3] libads/ldap.c:675(ads_connect)
  Connected to LDAP server JCSCORP000.judicialservices.net
[2010/10/01 11:20:43, 10] libads/ldap.c:165(ads_closest_dc)
  ads_closest_dc: NBT_SERVER_CLOSEST flag set
[2010/10/01 11:20:43, 10] libsmb/namequery.c:86(saf_store)
  saf_store: domain = [JUDICIALSERVICE], server = [JCSCORP000.judicialservices.net], expire = [1285947343]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = SAF/DOMAIN/JUDICIALSERVICE; value = JCSCORP000.judicialservices.net and timeout = Fri Oct  1 11:35:43 2010
   (900 seconds ahead)
[2010/10/01 11:20:43, 10] libsmb/namequery.c:86(saf_store)
  saf_store: domain = [JUDICIALSERVICES.NET], server = [JCSCORP000.judicialservices.net], expire = [1285947343]
[2010/10/01 11:20:43, 10] lib/gencache.c:131(gencache_set)
  Adding cache entry with key = SAF/DOMAIN/JUDICIALSERVICES.NET; value = JCSCORP000.judicialservices.net and timeout = Fri Oct  1 11:35:43 2010
   (900 seconds ahead)
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  5] lib/charcnv.c:82(charset_name)
  Substituting charset 'UTF-8' for LOCALE
[2010/10/01 11:20:43,  4] libads/ldap.c:2851(ads_current_time)
  time offset is 0 seconds
[2010/10/01 11:20:43,  4] libads/sasl.c:1112(ads_sasl_bind)
  Found SASL mechanism GSS-SPNEGO
[2010/10/01 11:20:43,  3] libads/sasl.c:780(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got OID=1.3.6.1.4.1.311.2.2.30
[2010/10/01 11:20:43,  3] libads/sasl.c:780(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got OID=1.2.840.48018.1.2.2
[2010/10/01 11:20:43,  3] libads/sasl.c:780(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got OID=1.2.840.113554.1.2.2
[2010/10/01 11:20:43,  3] libads/sasl.c:780(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got OID=1.2.840.113554.1.2.2.3
[2010/10/01 11:20:43,  3] libads/sasl.c:780(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got OID=1.3.6.1.4.1.311.2.2.10
[2010/10/01 11:20:43,  3] libads/sasl.c:789(ads_sasl_spnego_bind)
  ads_sasl_spnego_bind: got server principal name = not_defined_in_RFC4178@please_ignore
[2010/10/01 11:20:43, 10] libads/sasl.c:810(ads_sasl_spnego_bind)
  ads_sasl_spnego_krb5_bind failed with: Unspecified GSS failure.  Minor code may provide more information : No credentials cache found, calling kinit
[2010/10/01 11:20:43, 10] libads/kerberos.c:188(kerberos_kinit_password_ext)
  kerberos_kinit_password: as PROXY$@JUDICIALSERVICES.NET using [MEMORY:net_ads] as ccache and config [/var/run/samba/smb_krb5/krb5.conf.JUDICIALSERVICE]
[2010/10/01 11:20:43, 10] libads/ldap.c:165(ads_closest_dc)
  ads_closest_dc: NBT_SERVER_CLOSEST flag set
[2010/10/01 11:20:43, 10] lib/util.c:2626(name_to_fqdn)
  name_to_fqdn: lookup for PROXY -> proxy.judicialservices.net.
[2010/10/01 11:20:43,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=fe80::216:76ff:fecc:90f4%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
[2010/10/01 11:20:43,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=192.168.6.103 bcast=192.168.6.255 netmask=255.255.255.0
[2010/10/01 11:20:43,  4] libads/dns.c:620(ads_dns_lookup_ns)
  ads_dns_lookup_ns: 2 records returned in the answer section.
[2010/10/01 11:20:43, 10] intl/lang_tdb.c:138(lang_tdb_init)
  lang_tdb_init: /usr/share/samba/en_US.UTF-8.msg: No such file or directory
DNS update failed!
[2010/10/01 11:20:43,  2] utils/net.c:779(main)
  return code = -1


---

