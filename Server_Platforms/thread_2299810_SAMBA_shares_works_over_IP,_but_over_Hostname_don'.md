---
title: "SAMBA shares works over IP, but over Hostname don't"
date: 2015-10-21
forum: Server Platforms
---

### Post by przemyslaw3 on 2015-10-21
Hello. I have a problem with simpla samba share. On clean install Ubuntu server with samba, after configuring samba shares (with Active Directory users and groups) I can:

- Connect (SSO) by IP to my share from Windows
- Connect by IP and hostname to my share from OS X (system prompts for user/password)

I can't connect by Hostname to my share from Windows. When I try to do it, Windows show me username/password window, but I cannot login to this share with correct username and password (I try user1 and DOMAIN\user1).

Few words about my server:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
```

```
$ smbd -V
Version 3.6.3
```


wbinfo -u show me our users correct, and wbinfo -g show me our groups. 

My smb.conf file:
```
$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Studio]"
Loaded services file OK.
'winbind separator = +' might cause problems with group membership.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
    workgroup = DOMAIN
    realm = DOMAIN.EXAMPLE.COM
    server string = %h server (Samba, Ubuntu)
    interfaces = 10.148.0.8
    bind interfaces only = Yes
    security = ADS
    map to guest = Bad User
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host lmhosts wins
    dns proxy = No
    pid directory = /var/run/samba/public
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    winbind separator = +
    winbind enum users = Yes
    winbind enum groups = Yes
    winbind use default domain = Yes
    idmap config * : range = 10000-20000
    idmap config * : backend = tdp
    veto files = /._*/.DS_Store/

[Studio]
    comment = Comment
    path = /mirroredData/Share
    valid users = "@DOMAIN+Studio RW", "@DOMAIN+Studio RO"
    write list = "@DOMAIN+Studio RW"
    create mask = 0666
    force create mode = 0666
    security mask = 0666
    force security mode = 0666
    directory mask = 0777
    force directory mode = 0777
    force directory security mode = 0777
    inherit permissions = Yes
    strict locking = Yes


```

There are logs from log.10.148.1.2 file after trying connec by Hostname:
```
[2015/10/21 12:46:03.959615,  3] lib/access.c:338(allow_access)
  Allowed connection from 10.148.1.2 (10.148.1.2)
[2015/10/21 12:46:03.959709,  3] smbd/oplock.c:922(init_oplocks)
  init_oplocks: initializing messages.
[2015/10/21 12:46:03.959797,  3] smbd/oplock_linux.c:226(linux_init_kernel_oplocks)
  Linux kernel oplocks enabled
[2015/10/21 12:46:03.959875,  3] smbd/process.c:1662(process_smb)
  Transaction 0 of length 159 (0 toread)
[2015/10/21 12:46:03.959914,  3] smbd/process.c:1467(switch_message)
  switch message SMBnegprot (pid 1782) conn 0x0
[2015/10/21 12:46:03.960184,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2015/10/21 12:46:03.960222,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN1.0]
[2015/10/21 12:46:03.960254,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [Windows for Workgroups 3.1a]
[2015/10/21 12:46:03.960286,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LM1.2X002]
[2015/10/21 12:46:03.960318,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN2.1]
[2015/10/21 12:46:03.960349,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [NT LM 0.12]
[2015/10/21 12:46:03.960381,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.002]
[2015/10/21 12:46:03.960412,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.???]
[2015/10/21 12:46:03.960511,  3] smbd/negprot.c:419(reply_nt1)
  using SPNEGO
[2015/10/21 12:46:03.960543,  3] smbd/negprot.c:704(reply_negprot)
  Selected protocol NT LM 0.12
[2015/10/21 12:46:03.963726,  3] smbd/process.c:1662(process_smb)
  Transaction 1 of length 142 (0 toread)
[2015/10/21 12:46:03.963784,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1782) conn 0x0
[2015/10/21 12:46:03.963827,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:03.963862,  2] smbd/sesssetup.c:1279(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2015/10/21 12:46:03.963895,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:03.963929,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:03.963978,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 40
[2015/10/21 12:46:03.964154,  3] ../libcli/auth/ntlmssp.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088297
[2015/10/21 12:46:03.967162,  3] smbd/process.c:1662(process_smb)
  Transaction 2 of length 502 (0 toread)
[2015/10/21 12:46:03.967201,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1782) conn 0x0
[2015/10/21 12:46:03.967237,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:03.967268,  2] smbd/sesssetup.c:1279(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2015/10/21 12:46:03.967298,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:03.967329,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:03.967373,  3] ../libcli/auth/ntlmssp_server.c:348(ntlmssp_server_preauth)
  Got user=[user1] domain=[DOMAIN] workstation=[PC1] len1=24 len2=260
[2015/10/21 12:46:04.295747,  3] lib/access.c:338(allow_access)
  Allowed connection from 10.148.1.2 (10.148.1.2)
[2015/10/21 12:46:04.295839,  3] smbd/oplock.c:922(init_oplocks)
  init_oplocks: initializing messages.
[2015/10/21 12:46:04.295921,  3] smbd/oplock_linux.c:226(linux_init_kernel_oplocks)
  Linux kernel oplocks enabled
[2015/10/21 12:46:04.295995,  3] smbd/process.c:1662(process_smb)
  Transaction 0 of length 159 (0 toread)
[2015/10/21 12:46:04.296033,  3] smbd/process.c:1467(switch_message)
  switch message SMBnegprot (pid 1783) conn 0x0
[2015/10/21 12:46:04.296274,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2015/10/21 12:46:04.296310,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN1.0]
[2015/10/21 12:46:04.296341,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [Windows for Workgroups 3.1a]
[2015/10/21 12:46:04.296372,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LM1.2X002]
[2015/10/21 12:46:04.296402,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN2.1]
[2015/10/21 12:46:04.296432,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [NT LM 0.12]
[2015/10/21 12:46:04.296462,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.002]
[2015/10/21 12:46:04.296492,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.???]
[2015/10/21 12:46:04.296584,  3] smbd/negprot.c:419(reply_nt1)
  using SPNEGO
[2015/10/21 12:46:04.296615,  3] smbd/negprot.c:704(reply_negprot)
  Selected protocol NT LM 0.12
[2015/10/21 12:46:04.301916,  3] smbd/process.c:1662(process_smb)
  Transaction 1 of length 6004 (0 toread)
[2015/10/21 12:46:04.301971,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1783) conn 0x0
[2015/10/21 12:46:04.302017,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:04.302051,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:04.302087,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:04.302152,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5858
[2015/10/21 12:46:04.338251,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:04.338301,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:04.338330,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:06.892948,  3] lib/access.c:338(allow_access)
  Allowed connection from 10.148.1.2 (10.148.1.2)
[2015/10/21 12:46:06.893025,  3] smbd/oplock.c:922(init_oplocks)
  init_oplocks: initializing messages.
[2015/10/21 12:46:06.893113,  3] smbd/oplock_linux.c:226(linux_init_kernel_oplocks)
  Linux kernel oplocks enabled
[2015/10/21 12:46:06.893186,  3] smbd/process.c:1662(process_smb)
  Transaction 0 of length 159 (0 toread)
[2015/10/21 12:46:06.893222,  3] smbd/process.c:1467(switch_message)
  switch message SMBnegprot (pid 1784) conn 0x0
[2015/10/21 12:46:06.893474,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2015/10/21 12:46:06.893510,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN1.0]
[2015/10/21 12:46:06.893542,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [Windows for Workgroups 3.1a]
[2015/10/21 12:46:06.893572,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LM1.2X002]
[2015/10/21 12:46:06.893603,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN2.1]
[2015/10/21 12:46:06.893633,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [NT LM 0.12]
[2015/10/21 12:46:06.893663,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.002]
[2015/10/21 12:46:06.893693,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.???]
[2015/10/21 12:46:06.893784,  3] smbd/negprot.c:419(reply_nt1)
  using SPNEGO
[2015/10/21 12:46:06.893823,  3] smbd/negprot.c:704(reply_negprot)
  Selected protocol NT LM 0.12
[2015/10/21 12:46:06.894648,  3] smbd/process.c:1662(process_smb)
  Transaction 1 of length 6004 (0 toread)
[2015/10/21 12:46:06.894701,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1784) conn 0x0
[2015/10/21 12:46:06.894743,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:06.894776,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:06.894812,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:06.894877,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5858
[2015/10/21 12:46:06.895354,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:06.895403,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:06.895440,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:12.220360,  3] smbd/process.c:1662(process_smb)
  Transaction 2 of length 6004 (0 toread)
[2015/10/21 12:46:12.220408,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1783) conn 0x0
[2015/10/21 12:46:12.220447,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:12.220483,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:12.220515,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:12.220572,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5858
[2015/10/21 12:46:12.220878,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:12.220917,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:12.220949,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:12.222303,  3] smbd/process.c:1662(process_smb)
  Transaction 3 of length 6004 (0 toread)
[2015/10/21 12:46:12.222344,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1783) conn 0x0
[2015/10/21 12:46:12.222379,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:12.222409,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:12.222440,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:12.222494,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5858
[2015/10/21 12:46:12.222791,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:12.222829,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:12.222861,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:19.059719,  3] smbd/process.c:1662(process_smb)
  Transaction 4 of length 5876 (0 toread)
[2015/10/21 12:46:19.059772,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1783) conn 0x0
[2015/10/21 12:46:19.059811,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:19.059847,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:19.059891,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:19.059950,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5731
[2015/10/21 12:46:19.060271,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:19.060311,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:19.060343,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:19.839771,  3] smbd/process.c:1662(process_smb)
  Transaction 5 of length 5876 (0 toread)
[2015/10/21 12:46:19.839814,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1783) conn 0x0
[2015/10/21 12:46:19.839852,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:46:19.839887,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:46:19.839919,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:46:19.839973,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 5731
[2015/10/21 12:46:19.840272,  3] libads/kerberos_verify.c:632(ads_verify_ticket)
  libads/kerberos_verify.c:632: krb5_rd_req with auth failed (Bad encryption type)
[2015/10/21 12:46:19.840310,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2015/10/21 12:46:19.840342,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2015/10/21 12:46:21.589397,  1] smbd/process.c:457(receive_smb_talloc)
  receive_smb_raw_talloc failed for client 10.148.1.2 read error = NT_STATUS_CONNECTION_RESET.
[2015/10/21 12:46:21.589496,  3] smbd/server_exit.c:180(exit_server_common)
  Server exit (failed to receive smb request)


```

And this is log from this same file after trying connect over IP address:

```
[2015/10/21 12:47:40.119047,  3] lib/access.c:338(allow_access)
  Allowed connection from 10.148.1.2 (10.148.1.2)
[2015/10/21 12:47:40.119136,  3] smbd/oplock.c:922(init_oplocks)
  init_oplocks: initializing messages.
[2015/10/21 12:47:40.119231,  3] smbd/oplock_linux.c:226(linux_init_kernel_oplocks)
  Linux kernel oplocks enabled
[2015/10/21 12:47:40.119308,  3] smbd/process.c:1662(process_smb)
  Transaction 0 of length 159 (0 toread)
[2015/10/21 12:47:40.119347,  3] smbd/process.c:1467(switch_message)
  switch message SMBnegprot (pid 1801) conn 0x0
[2015/10/21 12:47:40.119603,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2015/10/21 12:47:40.119640,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN1.0]
[2015/10/21 12:47:40.119673,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [Windows for Workgroups 3.1a]
[2015/10/21 12:47:40.119704,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LM1.2X002]
[2015/10/21 12:47:40.119736,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [LANMAN2.1]
[2015/10/21 12:47:40.119767,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [NT LM 0.12]
[2015/10/21 12:47:40.119798,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.002]
[2015/10/21 12:47:40.119829,  3] smbd/negprot.c:598(reply_negprot)
  Requested protocol [SMB 2.???]
[2015/10/21 12:47:40.119925,  3] smbd/negprot.c:419(reply_nt1)
  using SPNEGO
[2015/10/21 12:47:40.119958,  3] smbd/negprot.c:704(reply_negprot)
  Selected protocol NT LM 0.12
[2015/10/21 12:47:40.120554,  3] smbd/process.c:1662(process_smb)
  Transaction 1 of length 142 (0 toread)
[2015/10/21 12:47:40.120620,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1801) conn 0x0
[2015/10/21 12:47:40.120664,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:47:40.120700,  2] smbd/sesssetup.c:1279(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2015/10/21 12:47:40.120730,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:47:40.120764,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:47:40.120810,  3] smbd/sesssetup.c:660(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 40
[2015/10/21 12:47:40.120976,  3] ../libcli/auth/ntlmssp.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088297
[2015/10/21 12:47:40.121345,  3] smbd/process.c:1662(process_smb)
  Transaction 2 of length 502 (0 toread)
[2015/10/21 12:47:40.121410,  3] smbd/process.c:1467(switch_message)
  switch message SMBsesssetupX (pid 1801) conn 0x0
[2015/10/21 12:47:40.121446,  3] smbd/sesssetup.c:1333(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2015/10/21 12:47:40.121475,  2] smbd/sesssetup.c:1279(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2015/10/21 12:47:40.121504,  3] smbd/sesssetup.c:1065(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2015/10/21 12:47:40.121535,  3] smbd/sesssetup.c:1107(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2015/10/21 12:47:40.121577,  3] ../libcli/auth/ntlmssp_server.c:348(ntlmssp_server_preauth)
  Got user=[user1] domain=[DOMAIN] workstation=[PC1] len1=24 len2=260


```

kinit works ok on my server. I can authenticate user1.

And about *mbd processes:
```

$ ps aux | grep mbd
root      1189  0.0  0.1 126672  5092 ?        Ss   14:53   0:00 smbd -D
root      1218  0.0  0.0  91256  2096 ?        Ss   14:53   0:01 nmbd -D
root      1471  0.0  0.0 126776  1768 ?        S    14:53   0:00 smbd -D
1000      2774  0.0  0.0   8076   656 pts/0    S+   18:03   0:00 grep --color=auto mbd

```

This is my first samba share, and I don't know what I do wrong.

---

### Post by lingpanda on 2015-10-21
I would start here on building a member server.

[https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server)

 Is this authenticating against a Windows or Samba AD?

---

### Post by TheFu on 2015-10-24
> **lingpanda said:**
> I would start here on building a member server.

[https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server)

 Is this authenticating against a Windows or Samba AD?

Specifically:
[https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server#Name_resolution_.28DNS.29](https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server#Name_resolution_.28DNS.29)

---

