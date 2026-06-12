---
title: "Samba Interdomain Trust - wbinfo works, getent doesn't work"
date: 2008-07-17
forum: Server Platforms
---

### Post by beazer on 2008-07-17
Hi

I have a problem with an interdomain trust between DomainA and DomainB.  On the PDC for DomainA, everything works perfectly.  getent returns local and DomainB usernames.

On the PDC for DomainB, getent only returns local usernames and groups, it doesn't return the usernames or groups for DomainA.  wbinfo -u and wbinfo -g work fine and return all DomainA's usernames and groups.

This means that I can set permissions for DomainB staff on DomainA, and they can successfully map shares and access files on DomainA. 

I can't set permissions for DomainA staff on DomainB, and DomainA staff cannot access DomainB using their own username and password :-(

I initially tried with a single WINS server on ServerA (DomainA's PDC), then local WINS servers on ServerA and ServerB with static pointers to the other Domain and PDC.  The behaviour of wbinfo and getent was the same as above for both configurations of WINS.

Given that wbinfo is working, is there a misconfiguration or a corrupted database somewhere that is stopping getent working?


ServerA (PDC for DomainA)

Ubuntu 6.06 LTS, Samba Version 3.0.22

/etc/samba/smb.conf
#======================= Global Settings =======================
[global]
  workgroup = DOMAINA
  wins support = yes
  netbios name = SERVERA
  host msdfs = yes
  time server = yes

#### Networking ####
   interfaces = 127.0.0.0/8 192.168.2.1
   bind interfaces only = true
   name resolve order = wins bcast hosts
####### Authentication #######
;   security = user
  encrypt passwords = true
  passdb backend = tdbsam
  obey pam restrictions = yes
  unix password sync = yes
########## Domains ###########
  domain logons = yes
  logon drive = M:
  logon path = \\%N\profiles\%U
  logon script = %U.cmd
  domain master = yes
  preferred master = yes

  enable privileges = yes

  #
  # Winbind
  #
  idmap uid = 10000-20000
  idmap gid = 10000-20000
  template shell = /bin/bash


ServerB (PDC for DomainB)

Ubuntu 8.04 LTS Samba version Version 3.0.28a

#======================= Global Settings =======================
[global]
  workgroup = DOMAINB
  time server = yes
  netbios name = SERVERB
#### Networking ####
   interfaces = 127.0.0.0/8 192.168.3.0/24
   bind interfaces only = true
  wins support = no
 wins server = 192.168.2.1
name resolve order = wins bcast hosts

####### Authentication #######
;   security = user
  encrypt passwords = true
  passdb backend = tdbsam
  obey pam restrictions = yes
  unix password sync = yes
########## Domains ###########
  domain logons = yes
  logon drive = M:
  logon path = \\%N\profiles\%U
  logon script = %U.cmd
  domain master = yes
  preferred master = yes

  enable privileges = yes

  host msdfs = yes

  # Winbind
  #
  idmap uid = 30000-40000
  idmap gid = 30000-40000
  template shell = /bin/bash
  winbind enum users = yes
  winbind enum groups = yes


ServerB's /var/log/samba/log.winbindd log shows

[2008/07/17 12:12:18, 3] nsswitch/winbindd_misc.c:winbindd_ping(470)
  [10049]: ping
[2008/07/17 12:15:44, 3] nsswitch/winbindd_misc.c:winbindd_interface_version(491)
  [10059]: request interface version
[2008/07/17 12:15:44, 3] nsswitch/winbindd_misc.c:winbindd_priv_pipe_dir(524)
  [10059]: request location of privileged pipe
[2008/07/17 12:15:44, 3] nsswitch/winbindd_group.c:winbindd_getgroups(1273)
  [10059]: getgroups root
[2008/07/17 12:15:44, 3] nsswitch/winbindd_sid.c:winbindd_gid_to_sid(477)
  [ 6180]: gid to sid 0
[2008/07/17 12:15:45, 3] nsswitch/winbindd_misc.c:winbindd_interface_version(491)
  [10061]: request interface version
[2008/07/17 12:15:45, 3] nsswitch/winbindd_misc.c:winbindd_priv_pipe_dir(524)
  [10061]: request location of privileged pipe
[2008/07/17 12:15:45, 3] nsswitch/winbindd_group.c:winbindd_getgroups(1273)
  [10061]: getgroups root
[2008/07/17 12:16:09, 3] nsswitch/winbindd_misc.c:winbindd_interface_version(491)
  [10075]: request interface version
[2008/07/17 12:16:09, 3] nsswitch/winbindd_misc.c:winbindd_priv_pipe_dir(524)
  [10075]: request location of privileged pipe
[2008/07/17 12:16:09, 3] nsswitch/winbindd_user.c:winbindd_setpwent_internal(445)
  [10075]: setpwent
[2008/07/17 12:16:09, 3] nsswitch/winbindd_user.c:winbindd_getpwent(636)
  [10075]: getpwent
[2008/07/17 12:16:09, 3] nsswitch/winbindd_rpc.c:query_user_list(46)
  rpc: query_user_list
[2008/07/17 12:16:10, 1] nsswitch/winbindd_user.c:winbindd_fill_pwent(85)
  error getting user id for sid S-1-5-21-2824201121-3407686785-855272569-1010
[2008/07/17 12:16:10, 1] nsswitch/winbindd_user.c:winbindd_getpwent(728)
  could not lookup domain user user1
[2008/07/17 12:16:10, 1] nsswitch/winbindd_user.c:winbindd_fill_pwent(85)
  error getting user id for sid S-1-5-21-2824201121-3407686785-855272569-501
[2008/07/17 12:16:10, 1] nsswitch/winbindd_user.c:winbindd_getpwent(728)
  could not lookup domain user user2
etc etc through all the users

There are quite a few of these as I suppose individual DomainA users try to access ServerB:

  [20557]: getpwnam user3
[2008/07/16 11:54:09, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20557]: getpwnam USER3
[2008/07/16 11:54:09, 3] nsswitch/winbindd_misc.c:winbindd_ping(470)
  [20557]: ping
[2008/07/16 11:54:10, 3] nsswitch/winbindd_misc.c:winbindd_interface_version(491)
  [20558]: request interface version
[2008/07/16 11:54:10, 3] nsswitch/winbindd_misc.c:winbindd_priv_pipe_dir(524)
  [20558]: request location of privileged pipe
[2008/07/16 11:54:10, 3] nsswitch/winbindd_pam.c:winbindd_pam_auth_crap(1685)
  [20558]: pam auth crap domain: [DOMAINA] user: user3
[2008/07/16 11:54:10, 3] nsswitch/winbindd_misc.c:winbindd_interface_version(491)
  [20558]: request interface version
[2008/07/16 11:54:10, 3] nsswitch/winbindd_misc.c:winbindd_priv_pipe_dir(524)
  [20558]: request location of privileged pipe
[2008/07/16 11:54:10, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20558]: getpwnam domaina\user3
[2008/07/16 11:54:10, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20558]: getpwnam DOMAINA\user3
[2008/07/16 11:54:10, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20558]: getpwnam DOMAINA\USER3
[2008/07/16 11:54:10, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20558]: getpwnam user3
[2008/07/16 11:54:10, 3] nsswitch/winbindd_user.c:winbindd_getpwnam(346)
  [20558]: getpwnam USER3


I can supply any other logs if required

Thanks for any help or pointers.
Rob

---

