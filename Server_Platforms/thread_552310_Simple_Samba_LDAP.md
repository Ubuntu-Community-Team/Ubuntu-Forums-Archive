---
title: "Simple Samba LDAP"
date: 2007-09-16
forum: Server Platforms
---

### Post by dexter2 on 2007-09-16
Hi,
I'd like to setup Samba authenticate through LAP. I do not need Domain controller, just simple file server. I'm strugling with it already for a few days. It was already working, but then i changed GID of files and directories and also GID for user group. Now it doesn't work. I get this in  syslog:

Sep 16 15:12:17 server slapd[5877]: conn=1221 fd=17 ACCEPT from IP=127.0.0.1:37884 (IP=0.0.0.0:389) 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=0 BIND dn="cn=admin,dc=land" method=128 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=0 BIND dn="cn=admin,dc=land" mech=SIMPLE ssf=0 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=0 RESULT tag=97 err=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=1 SRCH base="" scope=0 deref=0 filter="(objectClass=*)" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=1 SRCH attr=supportedControl 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=2 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(gidNumber=65534))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=2 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=2 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=3 SRCH base="dc=land" scope=2 deref=0 filter="(&(sambaSID=s-1-5-21-4133141370-4244664593-1540297714-513)(objectClass=sambaSamAccount))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=3 SRCH attr=uid uidNumber gidNumber homeDirectory sambaPwdLastSet sambaPwdCanChange sambaPwdMustChange sambaLogonTime sambaLogoffTime sambaKickoffTime cn sn displayName sambaHomeDrive sambaHomePath sambaLogonScript sambaProfilePath description sambaUserWorkstations sambaSID sambaPrimaryGroupSID sambaLMPassword sambaNTPassword sambaDomainName objectClass sambaAcctFlags sambaMungedDial sambaBadPasswordCount sambaBadPasswordTime sambaPasswordHistory modifyTimestamp sambaLogonHours modifyTimestamp uidNumber 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=3 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=4 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-21-4133141370-4244664593-1540297714-513))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=4 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=4 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=5 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-32-544))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=5 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=5 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server smbd[3709]: [2007/09/16 15:12:17, 0] auth/auth_util.c:create_builtin_administrators(785) 
Sep 16 15:12:17 server smbd[3709]:   create_builtin_administrators: Failed to create Administrators 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=6 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-32-545))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=6 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=6 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server smbd[3709]: [2007/09/16 15:12:17, 0] auth/auth_util.c:create_builtin_users(751) 
Sep 16 15:12:17 server smbd[3709]:   create_builtin_users: Failed to create Users 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=7 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(|(objectClass=sambaGroupMapping)(sambaGroupType=4))(|(sambaSIDList=s-1-5-21-4133141370-4244664593-1540297714-501)(sambaSIDList=s-1-1-0)(sambaSIDList=s-1-5-2)(sambaSIDList=s-1-5-32-546)))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=7 SRCH attr=sambaSID 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=7 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=8 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(|(objectClass=sambaGroupMapping)(sambaGroupType=4))(|(sambaSIDList=s-1-5-21-4133141370-4244664593-1540297714-501)(sambaSIDList=s-1-1-0)(sambaSIDList=s-1-5-2)(sambaSIDList=s-1-5-32-546)))" 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=8 SRCH attr=sambaSID 
Sep 16 15:12:17 server slapd[5877]: conn=1221 op=8 SEARCH RESULT tag=101 err=0 nentries=0 text= 
...............
Sep 16 15:12:17 server slapd[5877]: conn=1224 fd=44 ACCEPT from IP=127.0.0.1:37887 (IP=0.0.0.0:389) 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=0 BIND dn="cn=admin,dc=land" method=128 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=0 BIND dn="cn=admin,dc=land" mech=SIMPLE ssf=0 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=0 RESULT tag=97 err=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=1 SRCH base="ou=Users,dc=land" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=dexter2))" 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=3 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(gidNumber=10000))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=3 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=3 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=4 SRCH base="dc=land" scope=2 deref=0 filter="(&(sambaSID=s-1-5-21-4133141370-4244664593-1540297714-513)(objectClass=sambaSamAccount))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=4 SRCH attr=uid uidNumber gidNumber homeDirectory sambaPwdLastSet sambaPwdCanChange sambaPwdMustChange sambaLogonTime sambaLogoffTime sambaKickoffTime cn sn displayName sambaHomeDrive sambaHomePath sambaLogonScript sambaProfilePath description sambaUserWorkstations sambaSID sambaPrimaryGroupSID sambaLMPassword sambaNTPassword sambaDomainName objectClass sambaAcctFlags sambaMungedDial sambaBadPasswordCount sambaBadPasswordTime sambaPasswordHistory modifyTimestamp sambaLogonHours modifyTimestamp uidNumber 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=4 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=5 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-21-4133141370-4244664593-1540297714-513))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=5 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=5 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=2 SRCH base="ou=Users,dc=land" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=dexter2))" 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=3 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=posixGroup)(|(memberUid=dexter2)(uniqueMember=cn=viliam kocinsky,ou=users,dc=land)))" 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=3 SRCH attr=gidNumber 
Sep 16 15:12:17 server slapd[5877]: <= bdb_equality_candidates: (uniqueMember) index_param failed (18) 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=3 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=4 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=posixGroup)(uniqueMember=cn=landsk,ou=groups,dc=land))" 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=4 SRCH attr=gidNumber 
Sep 16 15:12:17 server slapd[5877]: <= bdb_equality_candidates: (uniqueMember) index_param failed (18) 
Sep 16 15:12:17 server slapd[5877]: conn=1224 op=4 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=6 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(gidNumber=10000))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=6 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=6 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=7 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-32-544))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=7 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=7 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server smbd[3710]: [2007/09/16 15:12:17, 0] auth/auth_util.c:create_builtin_administrators(785) 
Sep 16 15:12:17 server smbd[3710]:   create_builtin_administrators: Failed to create Administrators 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=8 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-32-545))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=8 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=8 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server smbd[3710]: [2007/09/16 15:12:17, 0] auth/auth_util.c:create_builtin_users(751) 
Sep 16 15:12:17 server smbd[3710]:   create_builtin_users: Failed to create Users 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=9 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(|(objectClass=sambaGroupMapping)(sambaGroupType=4))(|(sambaSIDList=s-1-5-21-4133141370-4244664593-1540297714-0)(sambaSIDList=s-1-5-21-2583134554-285144478-3637973259-0)(sambaSIDList=s-1-1-0)(sambaSIDList=s-1-5-2)(sambaSIDList=s-1-5-11)(sambaSIDList=s-1-22-2-10000)))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=9 SRCH attr=sambaSID 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=9 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=10 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(|(objectClass=sambaGroupMapping)(sambaGroupType=4))(|(sambaSIDList=s-1-5-21-4133141370-4244664593-1540297714-0)(sambaSIDList=s-1-5-21-2583134554-285144478-3637973259-0)(sambaSIDList=s-1-1-0)(sambaSIDList=s-1-5-2)(sambaSIDList=s-1-5-11)(sambaSIDList=s-1-22-2-10000)))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=10 SRCH attr=sambaSID 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=10 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=11 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-1-0))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=11 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=11 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=12 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-2))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=12 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=12 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=13 SRCH base="ou=Groups,dc=land" scope=2 deref=0 filter="(&(objectClass=sambaGroupMapping)(sambaSID=s-1-5-11))" 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=13 SRCH attr=gidNumber sambaSID sambaGroupType sambaSIDList description displayName cn objectClass 
Sep 16 15:12:17 server slapd[5877]: conn=1223 op=13 SEARCH RESULT tag=101 err=0 nentries=0 text= 
Sep 16 15:12:17 server smbd[3710]: [2007/09/16 15:12:17, 0] smbd/service.c:make_connection_snum(920) 
Sep 16 15:12:17 server smbd[3710]:   '/var/share/land/Install' does not exist or permission denied when connecting to [Install] Error was Permission denied 
Sep 16 15:12:17 server smbd[3710]: [2007/09/16 15:12:17, 0] smbd/service.c:make_connection_snum(920) 
.....................
Sep 16 15:12:18 server smbd[3710]:   '/var/share/land/Install' does not exist or permission denied when connecting to [Install] Error was Permission denied 
Sep 16 15:12:27 server slapd[5877]: conn=1223 fd=17 closed (connection lost) 
Sep 16 15:12:27 server slapd[5877]: conn=1224 fd=44 closed (connection lost) 



any idea?
Thanks

---

### Post by dexter2 on 2007-09-16
So I found the mistake:
Directory /var/share/land did not have read permission for samba user.

---

