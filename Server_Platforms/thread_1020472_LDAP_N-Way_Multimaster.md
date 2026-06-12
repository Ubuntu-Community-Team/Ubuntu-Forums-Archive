---
title: "LDAP N-Way Multimaster"
date: 2008-12-24
forum: Server Platforms
---

### Post by ibnkhaldun on 2008-12-24
**i installed openldap on Ubuntu 8.10 Server from [https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html#openldap-configuration) ,my replication setup didn't not work,I tested this document multiples times but no success would any body test this??**
[I][U]
Server 1 log:[/U][/I]
Dec 26 11:46:50 linux146 slapd[12614]: do_syncrepl: rid=002 retrying (4 retries left) 
Dec 26 11:47:06 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:06 linux146 slapd[12614]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 26 11:47:07 linux146 slapd[12614]: slap_client_connect: URI=ldap://10.1.1.146 DN="cn=admin,dc=ibnkhaldun,dc=com,dc=pk" ldap_sasl_bind_s failed (-5) 
Dec 26 11:47:07 linux146 slapd[12614]: do_syncrepl: rid=003 retrying (4 retries left) 
Dec 26 11:47:11 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:11 linux146 slapd[12614]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 26 11:47:12 linux146 slapd[12614]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 26 11:47:12 linux146 slapd[12614]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 26 11:47:16 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:16 linux146 slapd[12614]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 26 11:47:21 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:21 linux146 slapd[12614]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 26 11:47:22 linux146 slapd[12614]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 26 11:47:22 linux146 slapd[12614]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 26 11:47:26 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:26 linux146 slapd[12614]: do_syncrepl: rid=004 retrying 
Dec 26 11:47:31 linux146 slapd[12614]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 26 11:47:31 linux146 slapd[12614]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 26 11:47:32 linux146 slapd[12614]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 26 11:48:02 linux146 last message repeated 7 times
Dec 26 12:09:01 linux146 /USR/SBIN/CRON[12647]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

**Server 2 have empty log in starting but when i stop server 1 ,following log appears and when start again my server 1 ,once again server 2 have empty log**
[U][I]
Server2 log:[/I][/U]
Dec 26 11:52:09 erphost129 slapd[6519]: do_syncrep2: rid=001 (-1) Can't contact LDAP server 
Dec 26 11:52:09 erphost129 slapd[6519]: do_syncrepl: rid=001 retrying (4 retries left) 
Dec 26 11:52:14 erphost129 slapd[6519]: slap_client_connect: URI=ldap://10.1.1.146 DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1) 
Dec 26 11:52:14 erphost129 slapd[6519]: do_syncrepl: rid=001 retrying (3 retries left) 
Dec 26 11:52:19 erphost129 slapd[6519]: slap_client_connect: URI=ldap://10.1.1.146 DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1) 
Dec 26 11:52:19 erphost129 slapd[6519]: do_syncrepl: rid=001 retrying (2 retries left) 
Dec 26 11:52:24 erphost129 slapd[6519]: slap_client_connect: URI=ldap://10.1.1.146 DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1) 
Dec 26 11:52:24 erphost129 slapd[6519]: do_syncrepl: rid=001 retrying (1 retries left) 
Dec 26 11:52:29 erphost129 slapd[6519]: slap_client_connect: URI=ldap://10.1.1.146 DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1) 
Dec 26 11:52:29 erphost129 slapd[6519]: do_syncrepl: rid=001 retryin
Dec 26 11:57:34 erphost129 slapd[6519]: null_callback : error code 0x35 
Dec 26 11:57:34 erphost129 last message repeated 18 times
Dec 26 12:09:01 erphost129 /USR/SBIN/CRON[6550]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 26 12:17:01 erphost129 /USR/SBIN/CRON[6594]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)




Mudassir

---

### Post by logandzwon on 2008-12-27
I used the same guide your talking about and my set-up does work and replicate, however I get some of the same log errors you mention.  In particular;

 bdb_equality_candidates: (entryUUID) not indexed

but I think I got that before the sync.

---

### Post by logandzwon on 2008-12-27
ok, I think I kind of understand what it's tell us.  Some thing are indexed (like any DB.)  


I created this; 

file;  indexstuff.ldif 

dn: olcDatabase={1}hdb,cn=config
changetype: modify
replace: olcDbIndex
olcDbIndex: uid,entryUUID,uniqueMember,uidNumber,gidNumber,memberUid,objectclass eq


then do a;
ldapmodify -x -D cn=admin,cn=config -W -f indexstuff.ldif 
then stop slapd and do a slapindex, then restart slapd

You only need to do this one machine.  It'll do the work and replicate the results over to the other servers.

oh, and by default only objectclass eq is indexed.

---

### Post by ibnkhaldun on 2008-12-28
Many thanks for your help ,when i run this on my one server  

*ldapmodify -x -D cn=admin,cn=config -W -f indexstuff.ldif *

it say's

modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Constraint violation (19)
	additional info: <olcDbIndex> extra cruft after <attr> <[pres,eq,approx,sub]>

after stopping slapd ,when i run *slapindex* it says

WARNING!
Runnig as root!
There's a fair chance slapd will fail to start.
Check file permissions!

My slapd.d file permission are 

ls -ltr slad.d
drwxr-x--- 3 openldap openldap 4096 2008-12-28 10:08 slapd.d


I previously add  ldapmodify -x -D cn=admin,cn=config -W -f uid_index.ldif on both servers as in document
 
file: uid_index.ldif
dn: olcDatabase={1}hdb,cn=config
add: olcDbIndex
olcDbIndex: uid eq,pres,sub

and got 

Enter LDAP Password: 
modifying entry "olcDatabase={1}hdb,cn=config"



**log file says:**
Dec 28 10:03:40 linux146 slapd[11465]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 10:03:40 linux146 slapd[11465]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 10:03:40 linux146 slapd[11465]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 10:03:40 linux146 slapd[11465]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 28 10:03:50 linux146 slapd[11465]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 10:04:30 linux146 last message repeated 8 times
Dec 28 10:05:30 linux146 last message repeated 13 times
Dec 28 10:05:40 linux146 last message repeated 2 times
Dec 28 10:05:40 linux146 slapd[11465]: olcDbIndex: value #0: <olcDbIndex> extra cruft after <attr> <[pres,eq,approx,sub]>. 
Dec 28 10:05:50 linux146 slapd[11465]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 10:06:30 linux146 last message repeated 8 times
Dec 28 10:07:00 linux146 last message repeated 7 times

i again find no replication!!! , i do this setup twice from beginning

**2nd Test logs:**

server1:

Dec 28 11:32:01 mehran slapd[6181]: do_syncrepl: rid=001 retrying (1 retries left) 
Dec 28 11:32:06 mehran slapd[6181]: slap_client_connect: URI=ldap://10.1.1.151 DN="cn=admin,cn=config" ldap_sasl_bind_s failed (-1) 
Dec 28 11:32:06 mehran slapd[6181]: do_syncrepl: rid=001 retrying 
Dec 28 11:32:11 mehran slapd[6181]: null_callback : error code 0x35 
.Dec 28 11:32:11 mehran last message repeated 18 times
Dec 28 11:36:18 mehran kernel: [ 7213.985659] type=1503 audit(1230446178.746:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/4214/net/if_inet6" pid=4215 profile="/usr/sbin/named"

server2:

Dec 28 11:32:15 khyber slapd[5779]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 28 11:32:20 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:32:20 khyber slapd[5779]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 11:32:20 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:32:20 khyber slapd[5779]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 28 11:32:25 khyber slapd[5779]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 11:32:25 khyber slapd[5779]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 28 11:32:30 khyber slapd[5779]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 11:32:30 khyber slapd[5779]: do_syncrepl: rid=004 retrying 
Dec 28 11:32:30 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:32:30 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:32:35 khyber slapd[5779]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 11:32:35 khyber slapd[5779]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 28 11:32:40 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:33:10 khyber last message repeated 7 times
Dec 28 11:34:10 khyber last message repeated 12 times
Dec 28 11:35:10 khyber last message repeated 12 times
Dec 28 11:36:10 khyber last message repeated 12 times
Dec 28 11:37:10 khyber last message repeated 12 times
Dec 28 11:37:30 khyber last message repeated 4 times
Dec 28 11:37:35 khyber slapd[5779]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 28 11:37:35 khyber slapd[5779]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 28 11:37:40 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:37:50 khyber last message repeated 3 times
Dec 28 11:37:51 khyber kernel: [ 3621.282653] type=1503 audit(1230446271.565:13): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/4054/net/if_inet6" pid=4056 profile="/usr/sbin/named"
Dec 28 11:38:00 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 28 11:38:40 khyber last message repeated 8 times
Dec 28 11:39:00 khyber last message repeated 5 times
Dec 28 11:39:01 khyber /USR/SBIN/CRON[5801]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 28 11:39:10 khyber slapd[5779]: <= bdb_equality_candidates: (entryUUID) not indexed 

Again *i have following errors on both servers:*

Dec 29 12:38:39 khyber kernel: [10820.533115] type=1503 audit(1230536319.815:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=104 name="/proc/4080/net/if_inet6" pid=4082 profile="/usr/sbin/named"
Dec 29 12:39:01 khyber /USR/SBIN/CRON[6376]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 29 12:40:01 khyber /USR/SBIN/CRON[6408]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)


Mudassir

---

### Post by ibnkhaldun on 2008-12-29
What about these errors:

server 1 log:
Dec 29 13:26:33 erphost129 slapd[5647]: send_search_entry: conn 11  ber write failed. 
Dec 29 13:31:33 erphost129 slapd[5647]: send_search_entry: conn 13  ber write failed. 
Dec 29 13:36:33 erphost129 slapd[5647]: send_search_entry: conn 14  ber write failed. 
Dec 29 13:39:01 erphost129 /USR/SBIN/CRON[5675]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 29 13:41:33 erphost129 slapd[5647]: send_search_entry: conn 15  ber write failed. 
Dec 29 13:46:33 erphost129 slapd[5647]: send_search_entry: conn 16  ber write failed. 


Server2 log:
Dec 29 13:20:41 linux146 last message repeated 11 times
Dec 29 13:20:44 linux146 slapd[14090]: do_syncrep2: rid=002 (-1) Can't contact LDAP server 
Dec 29 13:20:44 linux146 slapd[14090]: do_syncrepl: rid=002 retrying (4 retries left) 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrep2: rid=003 got search entry without Sync State control 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrepl: rid=003 retrying (4 retries left) 
Dec 29 13:21:15 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:15 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 29 13:21:15 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 

Dec 29 13:21:15 linux146 last message repeated 5 times
Dec 29 13:21:20 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:20 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 29 13:21:25 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:21:25 linux146 last message repeated 5 times
Dec 29 13:21:25 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:25 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 29 13:21:30 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:30 linux146 slapd[14090]: do_syncrepl: rid=004 retrying 
Dec 29 13:21:35 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:21:35 linux146 last message repeated 5 times
Dec 29 13:21:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 29 13:21:45 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:22:25 linux146 last message repeated 24 times
Dec 29 13:23:25 linux146 last message repeated 41 times
Dec 29 13:26:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:26:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 29 13:31:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:31:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 29 13:36:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:36:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 29 13:39:01 linux146 /USR/SBIN/CRON[14109]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 29 13:41:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:41:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying 
Dec 29 13:44:54 linux146 pulseaudio[5411]: protocol-native.c: Failed to push data into queue
Dec 29 13:44:59 linux146 last message repeated 13241 times
Dec 29 13:46:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:46:35 linux146 slapd[14090]: do_syncrepl: rid=004 quitting

---

### Post by ibnkhaldun on 2008-12-29
What about these errors:

server 1 log:
Dec 29 13:26:33 erphost129 slapd[5647]: send_search_entry: conn 11  ber write failed. 
Dec 29 13:31:33 erphost129 slapd[5647]: send_search_entry: conn 13  ber write failed. 
Dec 29 13:36:33 erphost129 slapd[5647]: send_search_entry: conn 14  ber write failed. 
Dec 29 13:39:01 erphost129 /USR/SBIN/CRON[5675]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 29 13:41:33 erphost129 slapd[5647]: send_search_entry: conn 15  ber write failed. 
Dec 29 13:46:33 erphost129 slapd[5647]: send_search_entry: conn 16  ber write failed. 


Server2 log:
Dec 29 13:20:41 linux146 last message repeated 11 times
Dec 29 13:20:44 linux146 slapd[14090]: do_syncrep2: rid=002 (-1) Can't contact LDAP server 
Dec 29 13:20:44 linux146 slapd[14090]: do_syncrepl: rid=002 retrying (4 retries left) 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrep2: rid=003 got search entry without Sync State control 
Dec 29 13:21:10 linux146 slapd[14090]: do_syncrepl: rid=003 retrying (4 retries left) 
Dec 29 13:21:15 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:15 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 29 13:21:15 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 

Dec 29 13:21:15 linux146 last message repeated 5 times
Dec 29 13:21:20 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:20 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 29 13:21:25 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:21:25 linux146 last message repeated 5 times
Dec 29 13:21:25 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:25 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 29 13:21:30 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:30 linux146 slapd[14090]: do_syncrepl: rid=004 retrying 
Dec 29 13:21:35 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:21:35 linux146 last message repeated 5 times
Dec 29 13:21:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:21:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (4 retries left) 
Dec 29 13:21:45 linux146 slapd[14090]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 29 13:22:25 linux146 last message repeated 24 times
Dec 29 13:23:25 linux146 last message repeated 41 times
Dec 29 13:26:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:26:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (3 retries left) 
Dec 29 13:31:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:31:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (2 retries left) 
Dec 29 13:36:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:36:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying (1 retries left) 
Dec 29 13:39:01 linux146 /USR/SBIN/CRON[14109]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 29 13:41:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:41:35 linux146 slapd[14090]: do_syncrepl: rid=004 retrying 
Dec 29 13:44:54 linux146 pulseaudio[5411]: protocol-native.c: Failed to push data into queue
Dec 29 13:44:59 linux146 last message repeated 13241 times
Dec 29 13:46:35 linux146 slapd[14090]: do_syncrep2: rid=004 got search entry without Sync State control 
Dec 29 13:46:35 linux146 slapd[14090]: do_syncrepl: rid=004 quitting

---

### Post by jpugh on 2009-01-05
Not sure which messages you want a response on...

For the sync state message, you have not configured sync correctly. You need to configure syncprov overlay on the master.

I believe the write error is related to the above.

I would suggest searching a bit more and you will find your errors in the configuration.

If you want further help, you need to post your slapd.conf file.

---

### Post by asommer on 2009-01-17
You might want to also make sure that each replication server can access LDAP on each other server.  So, make sure that /etc/default/slapd has been changed to listen on the network, and /etc/hosts is correct so that each server knows that 127.0.0.1 is servername.domain.com.

---

### Post by visuburi on 2009-05-07
i have openldap(2.4.9) installed in ubuntu 8.04 server.
i want to create a multi master set up with two such machines.
first i tried to follow [http://www.openldap.org/doc/admin24/replication.html](http://www.openldap.org/doc/admin24/replication.html) to form n-way master setup.
but in starting only i got a problem saying database(dc=mytest,dc=com) is not configured to hold "cn=config"
then  i tried setting up cn=config using  [http://www.zytrax.com/books/ldap/ch6/slapd-config.html](http://www.zytrax.com/books/ldap/ch6/slapd-config.html) 
but that doesn't help me meaning even after configuring that cn=config as he mentioned in the site i got the same error
so i removed everything(slapd.d) what i did earlier so now i have slapd.conf in  both of my servers

finally i found one more link
[http://itsecureadmin.com/wiki/index.php/OpenLDAP_Multi-Master_Replication](http://itsecureadmin.com/wiki/index.php/OpenLDAP_Multi-Master_Replication)
that displays sample config file 
so i followed that
you can check the slapd.conf below
so now i set up the same configuration in the second server too.

after writing these slapd.conf i just restared slapd on both servers.
for the first time when i add some data the first server it got replicated on the other server only when restart slapd on second server.
that is fine.
when i tried to add some other data on second server its not getting replicated on the other server even if i restart slapd.
after that wherever i add data not getting replicated adding locally only.

what could be the problem.
plz check my slapd.conf file and suggetst me how to do multi master replication on ubuntu 8.04 server.
 
so my slapd.conf is below.

# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_hdb
moduleload	ppolicy.la
moduleload	syncprov.la
moduleload	back_monitor.la
		

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

database        config
rootdn "cn=admin,cn=config"
rootpw admin123

database        monitor
rootdn cn=monitor
rootpw admin123

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=mytest,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=mytest,dc=com"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

serverid  3   ldap://192.168.7.88:389
serverid  4   ldap://192.168.7.89:389

cachesize 1000
checkpoint 256 5

syncrepl rid=003
	provider=ldap://192.168.7.88:389	
	binddn="cn=admin,dc=mytest,dc=com"
	bindmethod=simple
	credentials=admin123
	searchbase="dc=mytest,dc=com"
	type=refreshAndPersist
	interval=00:00:00:10
	retry="5 5 300 5"
	timeout=1

syncrepl rid=004
	provider=ldap://192.168.7.89:389	
	binddn="cn=admin,dc=mytest,dc=com"
	bindmethod=simple
	credentials=admin123
	searchbase="dc=mytest,dc=com"
	type=refreshAndPersist
	interval=00:00:00:10
	retry="5 5 300 5"
	timeout=1

mirrormode true

overlay syncprov
syncprov-checkpoint 100 10
syncprov-sessionlog 100

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057) for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq
index           cn,mail,surname,givenname eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=mytest,dc=com" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=mytest,dc=com" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=mytest,dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"
---------------------------------------------------------------------
Thanks 
Visu

---

### Post by visuburi on 2009-05-07
hi
what you want more about?
I didn't get you.
I need to set up openldap n-way multi master on ubuntu 8.04 server.
And I tried with multiple ways as i have mentioned in my previous post.
slapd.conf is same in both of my servers.so thats why i didn't post the other.
Can You guide me to establish set up for n-way multi master on ubuntu 8.04

plz guide if you guys have set up working.

Thanks in Advance

visu

---

### Post by halensmith01 on 2009-05-12
Is this any error and warning.I didn't get what you want to say.

---

### Post by visuburi on 2009-05-12
Hi,

I am not able to setup openldap 2.4.9 multi master setup on ubuntu 8.04

the above messages are regarding that setup.

I wanted your help to setup this.

And from openldap technical forum i came to know that openldap-2.4.9 has lot many fixes so they suggested me to use openldap-2.4.16

Now i am trying with that .
since apt-get is not installing 2.4.16 i am downloading source and using it for installation

here i am not able to install openldap-2.4.16 its stopping in the middle
the procedure i am giving below.


 I have downloaded openldap 2.4.16.tgz (both release and stable versions i
    have tried)
    and db-4.7.25.tar.gz
    first i have installed bdb
    copied into /usr/local/ by untar it then
    cd db-4.7.25/build_unix
                    ../dist/configure --prefix=/usr/local/
                     make
                     make install
     now i have installed openldap by following method:
    copy to /usr/local and
    untar openldap-2.4.16.tgz
    cd /usr/local/openldap-2.4.16/
    then
    export LD_LIBRARY_PATH=/usr/local/db-4.7.25/build_unuix/.libs
    ./configure
    make depend

- Ignored:
    make

    upto here its fine
    now after this when i run

    make test


    at the case of

    >>>> Starting test001-slapadd ...
    running defines.sh
    Running slapadd to build slapd database...

    its not coming out and its keep on waiting at that line


    what could be the problem


plz provide me some solution to install openldap-2.4.16 and the best way to set up openldap N-way multi master set up on ubuntu 8.04

Thanks in Advance..

Visu

---

### Post by Mers2009 on 2009-06-21
I followed [the same tutorial]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html") about LDAP replication . Yesterday I managed to get two servers replicating. I've tested to modify an entry in one server and soon it was replicated to the other server. Today I've stared up the Ubuntu boxs again and now it isn't replicating the data. I haven't do absolute anything in the Ububtu servers between yesterday and today and now I don't have the replication working, it seems quite strange :(

Here is the logs from **server1**:
```

Jun 21 14:53:57 ubuntu slapd[4429]: do_syncrep2: rid=001 (32) No such object
Jun 21 14:53:57 ubuntu slapd[4429]: do_syncrepl: rid=001 retrying (4 retries left)
Jun 21 14:53:58 ubuntu slapd[4429]: do_syncrep2: rid=002 (32) No such object
Jun 21 14:53:58 ubuntu slapd[4429]: do_syncrepl: rid=002 retrying (4 retries left)
Jun 21 14:54:02 ubuntu slapd[4429]: findbase failed! 32
Jun 21 14:54:02 ubuntu slapd[4429]: do_syncrep2: rid=001 (32) No such object
Jun 21 14:54:02 ubuntu slapd[4429]: do_syncrepl: rid=001 retrying (4 retries left)
Jun 21 14:54:02 ubuntu slapd[4429]: findbase failed! 32
Jun 21 14:54:03 ubuntu slapd[4429]: do_syncrep2: rid=002 (32) No such object
Jun 21 14:54:03 ubuntu slapd[4429]: do_syncrepl: rid=002 retrying (4 retries left)

```**and for server2:**

```
Jun 21 14:53:11 ubuntu slapd[4409]: do_syncrep2: rid=002 (32) No such object
Jun 21 14:53:11 ubuntu slapd[4409]: do_syncrep2: rid=001 (32) No such object
Jun 21 14:53:11 ubuntu slapd[4409]: do_syncrepl: rid=001 retrying (4 retries left)
Jun 21 14:53:11 ubuntu slapd[4409]: do_syncrepl: rid=002 retrying (3 retries left)
Jun 21 14:53:12 ubuntu slapd[4409]: findbase failed! 32
Jun 21 14:53:16 ubuntu slapd[4409]: do_syncrep2: rid=001 (32) No such object
Jun 21 14:53:16 ubuntu slapd[4409]: do_syncrepl: rid=001 retrying (4 retries left)
Jun 21 14:53:16 ubuntu slapd[4409]: findbase failed! 32
Jun 21 14:53:16 ubuntu slapd[4409]: do_syncrep2: rid=002 (32) No such object
Jun 21 14:53:16 ubuntu slapd[4409]: do_syncrepl: rid=002 retrying (4 retries left)
```Here are the ldif files I've runned:

```
dn: cn=module{0},cn=config
changetype: modify
add: olcModuleLoad
olcModuleLoad: syncprov

dn: cn=config
changetype: modify
replace: olcServerID
olcServerID: 1 ldap://ldap1.server
olcServerID: 2 ldap://ldap2.server

dn: olcOverlay=syncprov,olcDatabase={0}config,cn=config
changetype: add
objectClass: olcOverlayConfig
objectClass: olcSyncProvConfig
olcOverlay: syncprov

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcSyncRepl
olcSyncRepl: rid=001 provider=ldap://ldap1.server binddn="cn=admin,dc=server,dc=local" bindmethod=simple
  credentials="ii" searchbase="cn=config" type=refreshAndPersist
  retry="5 5 300 5" timeout=1
olcSyncRepl: rid=002 provider=ldap://ldap2.server binddn="cn=admin,dc=server,dc=local" bindmethod=simple
  credentials="ii" searchbase="cn=config" type=refreshAndPersist
  retry="5 5 300 5" timeout=1
-
add: olcMirrorMode
olcMirrorMode: TRUE

```
```
dn: olcDatabase={1}bdb,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,dc=server,dc=local
-
add: olcSyncRepl
olcSyncRepl: rid=003 provider=ldap://ldap1.server binddn="cn=admin,dc=server,dc=local" bindmethod=simple credentials="ii" searchbase="dc=server,dc=local" type=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
olcSyncRepl: rid=004 provider=ldap://ldap2.server binddn="cn=admin,dc=server,dc=local" bindmethod=simple credentials="ii" searchbase="dc=server,dc=local" type=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
-
add: olcMirrorMode
olcMirrorMode: TRUE

dn: olcOverlay=syncprov,olcDatabase={1}bdb,cn=config
changetype: add
objectClass: olcOverlayConfig
objectClass: olcSyncProvConfig
olcOverlay: syncprov


```
Both servers are accessible because I'm connected to both from another machine with Apache Directory Studio

---

### Post by receptiveit on 2009-08-01
I thought that I would post my finding here, as I have spent quite a bit of time getting things working. 

I initially had a few issues with the multi-master setup on the Ubuntu server doc, but I now have it working. I will probably go it all again just to get it clear in my head though.

[LIST]
[*]/etc/hosts - Make sure that you have your FQDN in /etc/hosts as 127.0.0.1. I skipped over this initially and it was a big problem.
[*]cn=config replication - I haven't got this working at the moment. To simplify my config, I copied the contents of /etc/ldap/slapd.d from one server to the other. In my next attempt, I think you shouldn't do a dpkg-reconfigure, just add the replication ldif and all should be good.
[*]Indexes - entryCSN and entryUUID must be indexed. Do this first.
[*]Log files - When all else fails, tail the log file!
[/LIST]

I have probably forgotten something, but that was what my problems boiled down to. Now I have a multi-master replicated LDAP tree across a VPN from one side of Australia to the other. It tooks me about 5 hours to get the multi-master replication working, and about 5 minutes to get my mail config using LDAP.

I love LDAP.

---

### Post by davemc on 2011-02-09
If you copy from the example above at post #3, the memberUid seems to have a space in it. Remove that in the indexstuff.ldif file you create, as memberUid is the name of a field (column).

> **logandzwon said:**
> 
mem berUid


slapd runs as user openldap.  The warnings appear because the user openldap might not be able to read the recreated index files at /var/lib/ldap or /etc/ldap

---

