---
title: "nfs4 - problems with idmapper"
date: 2010-10-05
forum: Server Platforms
---

### Post by azrael2010 on 2010-10-05
Hello,

i set up a ubuntu server (10.04) with LDAP, Kerberos and NFS4. Did a set up for a client (ubuntu desktop 10.04 32 / 64) to connect to ldap, kerberos and nfs4-mount. 
All is working fine except of the idmapping. Some uids are not mapped to names. the entrys, which cannot  be mapped, change. so 10 minutes before the uid was mapped to the correct name, after that time (i'm not sure if it's exactly 10 minutes) the name is mapped to nobody. sometimes the gid cannot be mapped too.
I mount the nfs-share via nfs4 with sec=krb5 (krb5i or krb5p result in the same problem) and after successfully mounting the device, i type ls -la. 
i never have problems with getent passwd or with logging in as ldap-user. i get all the entries of the ldap-db and i also get kerberos tickets. All is working fine with nfs3, but i would like to use nfs4 for security-reasons.

if i run the rpc.idmapd with many "-v" i get the following messages in the daemon.log-file:

```

....
rpc.idmapd[15953]: nfs4_name_to_uid: calling nsswitch->name_to_uid
rpc.idmapd[15953]: nss_getpwnam: name 'test@DOMAIN.TEST' domain 'DOMAIN.TEST': resulting localname 'test'
rpc.idmapd[15953]: nfs4_name_to_uid: nsswitch->name_to_uid returned 0
rpc.idmapd[15953]: nfs4_name_to_uid: final return value is 0
rpc.idmapd[15953]: Client 39: (user) name "test@DOMAIN.TEST" -> id "2022"
....
rpc.idmapd[15953]: nfs4_name_to_uid: calling nsswitch->name_to_uid
rpc.idmapd[15953]: nss_getpwnam: name 'blubber@DOMAIN.TEST' domain 'DOMAIN.TEST': resulting localname 'blubber'
rpc.idmapd[15953]: nss_getpwnam: name 'blubber' not found in domain 'DOMAIN.TEST'
rpc.idmapd[15953]: nfs4_name_to_uid: nsswitch->name_to_uid returned -9
rpc.idmapd[15953]: nfs4_name_to_uid: final return value is -9
....

```the first part is the response to a correct name-to-uid-mapping the second part is a failed one. both user exist, both users have the same ldap-entries (except of the different descriptions, uid and so on). the responses have the same timestamp, so the reply is in (nearly) the same second.

restarting the idmap-daemon every 5 minutes or other workarounds are not practicable in normal operating environment.


PS: Sorry about my bad English, i'm from Germany.

---

### Post by luvshines on 2010-10-05
Is this consistent behaviour or it keeps changing to working/not-working ??

Is the second user added to Kerberos ?

---

### Post by azrael2010 on 2010-10-05
hello,

it keeps working with errors. but consistent.
Even after reboot / restart services it keeps being buggy. only some names are displayed correctly, others are mapped to "nobody" (likewise the groups)

Yes, both users are added to kerberos (like others).

It's also possible to reproduce the error, when mounting the nfs-share directly on the server, so the network can't be a point of failure either.

---

### Post by luvshines on 2010-10-07
For the names that are being mapped to nobody, can you grep them in /etc/passwd OR /etc/group file

Also check for the names which are being mapped correctly.

Here is a gud tutorial:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by azrael2010 on 2010-10-07
Hi there,

yes, I can grep for the users and groups. If I use nfs3 it's no problem at all. This works fine.
When I remove the ldap-entry in the nsswitch.conf , the users are gone, so i'm 100% sure the users exist only in ldap.
i never have login-problem, nor problems when using getent or nfs3. only if i use nfs4 with idmapd. Even without the sec=krb5 - option, I get the mapping-problem.
Maybe it's only about 10% of the users, but that's too much ;-)

thanks for the link, I knew that howto, but still i get the problems.

I have really no idea, how to fix this. :confused:

---

### Post by azrael2010 on 2010-10-14
No other ideas? :confused: :confused: :confused:

---

