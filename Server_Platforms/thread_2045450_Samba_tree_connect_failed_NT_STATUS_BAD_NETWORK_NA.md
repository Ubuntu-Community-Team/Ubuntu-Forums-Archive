---
title: "Samba tree connect failed: NT_STATUS_BAD_NETWORK_NAME"
date: 2012-08-21
forum: Server Platforms
---

### Post by apprentilinux on 2012-08-21
hello, 

I have a ubuntu 12.04 (Linux SAMBA 3.2.0-29-generic # 46-Ubuntu SMP Fri Jul 27 5:03:23 p.m. UTC 2012 x86_64 x86_64 x86_64 GNU / Linux).
I installed samba, I have a shared folder,  it   is accessible for all . 

I create a user like this:
```

root@SAMBA:/etc/samba# adduser myuser
Ajout de l'utilisateur « myuser » ...
Ajout du nouveau groupe « myuser » (1013) ...
Ajout du nouvel utilisateur « myuser » (1012) avec le groupe « myuser » ...
Création du répertoire personnel « /home/myuser »...
Copie des fichiers depuis « /etc/skel »...
Entrez le nouveau mot de passe UNIX : 
Retapez le nouveau mot de passe UNIX : 
passwd: password updated successfully
Changing the user information for myuser
Enter the new value, or press ENTER for the default
    Full Name []: myuser
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Cette information est-elle correcte ? [O/n] o
root@SAMBA:/etc/samba# smbpasswd -D6 -a myuser
Netbios name list:-
my_netbios_names[0]="SAMBA"
Attempting to register passdb backend ldapsam
Successfully added passdb backend 'ldapsam'
Attempting to register passdb backend ldapsam_compat
Successfully added passdb backend 'ldapsam_compat'
Attempting to register passdb backend NDS_ldapsam
Successfully added passdb backend 'NDS_ldapsam'
Attempting to register passdb backend NDS_ldapsam_compat
Successfully added passdb backend 'NDS_ldapsam_compat'
Attempting to register passdb backend IPA_ldapsam
Successfully added passdb backend 'IPA_ldapsam'
Attempting to register passdb backend smbpasswd
Successfully added passdb backend 'smbpasswd'
Attempting to register passdb backend tdbsam
Successfully added passdb backend 'tdbsam'
Attempting to register passdb backend wbc_sam
Successfully added passdb backend 'wbc_sam'
Attempting to find a passdb backend to match tdbsam (tdbsam)
Found pdb backend tdbsam
pdb backend tdbsam has a valid init
New SMB password:
Retype new SMB password:
tdbsam_open: successfully opened /var/lib/samba/passdb.tdb
pdb_getsampwnam (TDB): error fetching database.
 Key: USER_myuser
Finding user myuser
Trying _Get_Pwnam(), username as lowercase is myuser
Get_Pwnam_internals did find user [myuser]!
Home server: samba
Home server: samba
lookup_global_sam_rid: looking up RID 1001.
pdb_getsampwrid (TDB): error looking up RID 1001 by key RID_000003e9.
Opening cache file at /var/run/samba/gencache.tdb
Opening cache file at /var/run/samba/gencache_notrans.tdb
gid_to_sid: winbind failed to find a sid for gid 1013
Forcing Primary Group to 'Domain Users' for myuser
Storing (new) account myuser with RID 1001
Home server: samba
Substituting charset 'UTF-8' for LOCALE
Home server: samba
Finding user myuser
Trying _Get_Pwnam(), username as lowercase is myuser
Get_Pwnam_internals did find user [myuser]!
gid_to_sid: winbind failed to find a sid for gid 1013
Forcing Primary Group to 'Domain Users' for myuser
Home server: samba
Home server: samba
Home server: samba
Home server: samba
Storing account myuser with RID 1001
Added user myuser.

```when I try to connect myuser I get this error message 

```

root@SAMBA:/home# smbclient //SAMBA/home/myuser -U myuser
Enter myuser's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```
and log : 
```

[2012/08/21 13:51:02.888206,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.888304,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.888477,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.888638,  4] lib/substitute.c:527(automount_server)
  Home server: smb-server
[2012/08/21 13:51:02.888765,  4] lib/substitute.c:527(automount_server)
  Home server: smb-server
[2012/08/21 13:51:02.888906,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 3
[2012/08/21 13:51:02.889012,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 2
[2012/08/21 13:51:02.889113,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 3
[2012/08/21 13:51:02.889213,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.889311,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.889493,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.889623,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.889738,  5] lib/username.c:171(Get_Pwnam_alloc)
  Finding user myuser
[2012/08/21 13:51:02.889839,  5] lib/username.c:116(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as lowercase is myuser
[2012/08/21 13:51:02.889943,  5] lib/username.c:149(Get_Pwnam_internals)
  Get_Pwnam_internals did find user [myuser]!
[2012/08/21 13:51:02.890057,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.890174,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.890277,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2012/08/21 13:51:02.890377,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.890477,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.890575,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.890728,  5] passdb/pdb_interface.c:1605(lookup_global_sam_rid)
  lookup_global_sam_rid: looking up RID 513.
[2012/08/21 13:51:02.890834,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.890938,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2012/08/21 13:51:02.891038,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.891138,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.891235,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.891413,  5] passdb/pdb_tdb.c:614(tdbsam_getsampwrid)
  pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201.
[2012/08/21 13:51:02.891562,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.891668,  5] passdb/pdb_interface.c:1667(lookup_global_sam_rid)
  Can't find a unix id for an unmapped group
[2012/08/21 13:51:02.891777,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.891883,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.891985,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2012/08/21 13:51:02.892085,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.892185,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.892282,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.892435,  5] passdb/pdb_interface.c:1605(lookup_global_sam_rid)
  lookup_global_sam_rid: looking up RID 513.
[2012/08/21 13:51:02.892543,  4] smbd/sec_ctx.c:214(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.892683,  4] smbd/uid.c:460(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2012/08/21 13:51:02.892803,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2012/08/21 13:51:02.892906,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.893004,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.893183,  5] passdb/pdb_tdb.c:614(tdbsam_getsampwrid)
  pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201.
[2012/08/21 13:51:02.893326,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2012/08/21 13:51:02.893433,  5] passdb/pdb_interface.c:1667(lookup_global_sam_rid)
  Can't find a unix id for an unmapped group
[2012/08/21 13:51:02.893543,  4] smbd/sec_ctx.c:422(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.893711,  3] ../libcli/auth/ntlmssp_sign.c:535(ntlmssp_sign_init)
  NTLMSSP Sign/Seal - Initialising with flags:
[2012/08/21 13:51:02.893820,  3] ../libcli/auth/ntlmssp.c:34(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0x60088215
    NTLMSSP_NEGOTIATE_UNICODE
    NTLMSSP_REQUEST_TARGET
    NTLMSSP_NEGOTIATE_SIGN
    NTLMSSP_NEGOTIATE_NTLM
    NTLMSSP_NEGOTIATE_ALWAYS_SIGN
    NTLMSSP_NEGOTIATE_NTLM2
    NTLMSSP_NEGOTIATE_128
    NTLMSSP_NEGOTIATE_KEY_EXCH
[2012/08/21 13:51:02.894311,  3] smbd/password.c:297(register_existing_vuid)
  register_existing_vuid: User name: myuser    Real name: myuser
[2012/08/21 13:51:02.894418,  3] smbd/password.c:307(register_existing_vuid)
  register_existing_vuid: UNIX uid 1012 is UNIX user myuser, and will be vuid 100
[2012/08/21 13:51:02.894561,  4] auth/pampass.c:483(smb_pam_start)
  smb_pam_start: PAM: Init user: myuser
[2012/08/21 13:51:02.901005,  4] auth/pampass.c:492(smb_pam_start)
  smb_pam_start: PAM: setting rhost to: 192.168.0.150
[2012/08/21 13:51:02.901171,  4] auth/pampass.c:501(smb_pam_start)
  smb_pam_start: PAM: setting tty
[2012/08/21 13:51:02.901274,  4] auth/pampass.c:509(smb_pam_start)
  smb_pam_start: PAM: Init passed for user: myuser
[2012/08/21 13:51:02.901374,  4] auth/pampass.c:646(smb_internal_pam_session)
  smb_internal_pam_session: PAM: tty set to: smb/4425/100
[2012/08/21 13:51:02.902979,  4] auth/pampass.c:465(smb_pam_end)
  smb_pam_end: PAM: PAM_END OK.
[2012/08/21 13:51:02.903337,  5] lib/username.c:171(Get_Pwnam_alloc)
  Finding user myuser
[2012/08/21 13:51:02.903502,  5] lib/username.c:116(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as lowercase is myuser
[2012/08/21 13:51:02.903649,  5] lib/username.c:149(Get_Pwnam_internals)
  Get_Pwnam_internals did find user [myuser]!
[2012/08/21 13:51:02.903787,  3] smbd/password.c:238(register_homes_share)
  Adding homes service for user 'myuser' using home directory: '/home/myuser'
[2012/08/21 13:51:02.904045,  3] param/loadparm.c:6582(lp_add_home)
  adding home's share [myuser] for user 'myuser' at '/home/myuser'
[2012/08/21 13:51:02.904332,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.904426,  5] lib/util.c:342(show_msg)
  size=106
  smb_com=0x73
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=136
  smb_flg2=51203
  smb_tid=65535
  smb_pid=4424
  smb_uid=100
  smb_mid=3
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    0 (0x0)
  smb_vwv[ 3]=    9 (0x9)
  smb_bcc=63
[2012/08/21 13:51:02.906287,  3] smbd/process.c:1662(process_smb)
  Transaction 3 of length 94 (0 toread)
[2012/08/21 13:51:02.906496,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.906576,  5] lib/util.c:342(show_msg)
  size=90
  smb_com=0x75
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=8
  smb_flg2=51201
  smb_tid=65535
  smb_pid=4424
  smb_uid=100
  smb_mid=4
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    8 (0x8)
  smb_vwv[ 3]=    1 (0x1)
  smb_bcc=47
[2012/08/21 13:51:02.907589,  3] smbd/process.c:1467(switch_message)
  switch message SMBtconX (pid 4425) conn 0x0
[2012/08/21 13:51:02.907732,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.907900,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.908040,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.908256,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.908426,  4] smbd/reply.c:794(reply_tcon_and_X)
  Client requested device type [IPC] for share [IPC$]
[2012/08/21 13:51:02.908760,  5] smbd/service.c:1321(make_connection)
  making a connection to 'normal' service ipc$
[2012/08/21 13:51:02.909141,  3] lib/access.c:338(allow_access)
  Allowed connection from 192.168.0.150 (192.168.0.150)
[2012/08/21 13:51:02.909354,  5] lib/username.c:171(Get_Pwnam_alloc)
  Finding user myuser
[2012/08/21 13:51:02.909502,  5] lib/username.c:116(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as lowercase is myuser
[2012/08/21 13:51:02.909647,  5] lib/username.c:149(Get_Pwnam_internals)
  Get_Pwnam_internals did find user [myuser]!
[2012/08/21 13:51:02.909805,  3] smbd/service.c:837(make_connection_snum)
  Connect path is '/tmp' for service [IPC$]
[2012/08/21 13:51:02.910022,  3] smbd/vfs.c:102(vfs_init_default)
  Initialising default vfs hooks
[2012/08/21 13:51:02.910187,  5] smbd/vfs.c:92(smb_register_vfs)
  Successfully added vfs backend '/[Default VFS]/'
[2012/08/21 13:51:02.910338,  5] smbd/vfs.c:92(smb_register_vfs)
  Successfully added vfs backend 'posixacl'
[2012/08/21 13:51:02.910475,  3] smbd/vfs.c:128(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]
  Successfully loaded vfs module [/[Default VFS]/] with the new modules system
[2012/08/21 13:51:02.910680,  5] smbd/connection.c:134(claim_connection)
  claiming [IPC$]
[2012/08/21 13:51:02.911049,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (1012, 1013) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.911216,  5] ../libcli/security/security_token.c:63(security_token_debug)
  Security token SIDs (8):
    SID[  0]: S-1-5-21-170426220-3553132969-1075059826-1001
    SID[  1]: S-1-5-21-170426220-3553132969-1075059826-513
    SID[  2]: S-1-22-2-1013
    SID[  3]: S-1-1-0
    SID[  4]: S-1-5-2
    SID[  5]: S-1-5-11
    SID[  6]: S-1-22-1-1012
    SID[  7]: S-1-22-2-4294967295
   Privileges (0x               0):
   Rights (0x               0):
[2012/08/21 13:51:02.911995,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 1012
  Primary group is 1013 and contains 2 supplementary groups
  Group[  0]: 1013
  Group[  1]: 4294967295
[2012/08/21 13:51:02.912335,  5] smbd/uid.c:317(change_to_user_internal)
  Impersonated user: uid=(0,1012), gid=(0,1013)
[2012/08/21 13:51:02.912492,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.912918,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.913068,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.913292,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.913485,  3] smbd/service.c:1081(make_connection_snum)
  cesar (192.168.0.150) connect to service IPC$ initially as user myuser (uid=1012, gid=1013) (pid 4425)
[2012/08/21 13:51:02.913660,  3] smbd/reply.c:871(reply_tcon_and_X)
  tconX service=IPC$ 
[2012/08/21 13:51:02.914303,  3] smbd/process.c:1662(process_smb)
  Transaction 4 of length 128 (0 toread)
[2012/08/21 13:51:02.914505,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.914586,  5] lib/util.c:342(show_msg)
  size=124
  smb_com=0x32
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=8
  smb_flg2=51201
  smb_tid=1
  smb_pid=4424
  smb_uid=100
  smb_mid=5
  smt_wct=15
  smb_vwv[ 0]=   56 (0x38)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    2 (0x2)
  smb_vwv[ 3]=16644 (0x4104)
  smb_vwv[ 4]=    0 (0x0)
  smb_vwv[ 5]=    0 (0x0)
  smb_vwv[ 6]=    0 (0x0)
  smb_vwv[ 7]=    0 (0x0)
  smb_vwv[ 8]=    0 (0x0)
  smb_vwv[ 9]=   56 (0x38)
  smb_vwv[10]=   68 (0x44)
  smb_vwv[11]=    0 (0x0)
  smb_vwv[12]=  124 (0x7C)
  smb_vwv[13]=    1 (0x1)
  smb_vwv[14]=   16 (0x10)
  smb_bcc=59
[2012/08/21 13:51:02.916264,  3] smbd/process.c:1467(switch_message)
  switch message SMBtrans2 (pid 4425) conn 0x7fef5b39ed30
[2012/08/21 13:51:02.916419,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (1012, 1013) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.916596,  5] ../libcli/security/security_token.c:63(security_token_debug)
  Security token SIDs (8):
    SID[  0]: S-1-5-21-170426220-3553132969-1075059826-1001
    SID[  1]: S-1-5-21-170426220-3553132969-1075059826-513
    SID[  2]: S-1-22-2-1013
    SID[  3]: S-1-1-0
    SID[  4]: S-1-5-2
    SID[  5]: S-1-5-11
    SID[  6]: S-1-22-1-1012
    SID[  7]: S-1-22-2-4294967295
   Privileges (0x               0):
   Rights (0x               0):
[2012/08/21 13:51:02.917389,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 1012
  Primary group is 1013 and contains 2 supplementary groups
  Group[  0]: 1013
  Group[  1]: 4294967295
[2012/08/21 13:51:02.917734,  5] smbd/uid.c:317(change_to_user_internal)
  Impersonated user: uid=(0,1012), gid=(0,1013)
[2012/08/21 13:51:02.917897,  4] smbd/vfs.c:780(vfs_ChDir)
  vfs_ChDir to /tmp
[2012/08/21 13:51:02.918144,  5] lib/username.c:171(Get_Pwnam_alloc)
  Finding user home
[2012/08/21 13:51:02.918277,  5] lib/username.c:116(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as lowercase is home
[2012/08/21 13:51:02.918480,  5] lib/username.c:134(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as uppercase is HOME
[2012/08/21 13:51:02.918660,  5] lib/username.c:143(Get_Pwnam_internals)
  Checking combinations of 0 uppercase letters in home
[2012/08/21 13:51:02.918765,  5] lib/username.c:149(Get_Pwnam_internals)
  Get_Pwnam_internals didn't find user [home]!
[2012/08/21 13:51:02.918876,  3] smbd/service.c:343(find_service)
  checking for home directory home gave (NULL)
[2012/08/21 13:51:02.918986,  3] smbd/service.c:357(find_service)
  checking whether home is a valid printer name...
[2012/08/21 13:51:02.919128,  1] printing/printer_list.c:94(printer_list_get_printer)
  Failed to fetch record!
[2012/08/21 13:51:02.919231,  3] smbd/service.c:371(find_service)
  home is not a valid printer name
[2012/08/21 13:51:02.919360,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/home failed. Permission denied
[2012/08/21 13:51:02.919470,  3] smbd/service.c:444(find_service)
  find_service() failed to find service home
[2012/08/21 13:51:02.919587,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/trans2.c(8345) cmd=50 (SMBtrans2) NT_STATUS_NOT_FOUND
[2012/08/21 13:51:02.919702,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.919761,  5] lib/util.c:342(show_msg)
  size=35
  smb_com=0x32
  smb_rcls=37
  smb_reh=2
  smb_err=49152
  smb_flg=136
  smb_flg2=51203
  smb_tid=1
  smb_pid=4424
  smb_uid=100
  smb_mid=5
  smt_wct=0
  smb_bcc=0
[2012/08/21 13:51:02.920637,  3] smbd/process.c:1662(process_smb)
  Transaction 5 of length 39 (0 toread)
[2012/08/21 13:51:02.920806,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.920868,  5] lib/util.c:342(show_msg)
  size=35
  smb_com=0x71
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=8
  smb_flg2=51201
  smb_tid=1
  smb_pid=4424
  smb_uid=100
  smb_mid=6
  smt_wct=0
  smb_bcc=0
[2012/08/21 13:51:02.921435,  3] smbd/process.c:1467(switch_message)
  switch message SMBtdis (pid 4425) conn 0x7fef5b39ed30
[2012/08/21 13:51:02.921539,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.921642,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.921742,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.921908,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.922052,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.922158,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.922258,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.922411,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.922517,  3] smbd/service.c:1345(close_cnum)
  cesar (192.168.0.150) closed connection to service IPC$
[2012/08/21 13:51:02.922631,  3] smbd/connection.c:35(yield_connection)
  Yielding connection to IPC$
[2012/08/21 13:51:02.922781,  4] smbd/vfs.c:780(vfs_ChDir)
  vfs_ChDir to /
[2012/08/21 13:51:02.922894,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.922995,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.923093,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.923246,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.923369,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.923429,  5] lib/util.c:342(show_msg)
  size=35
  smb_com=0x71
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=136
  smb_flg2=51203
  smb_tid=1
  smb_pid=4424
  smb_uid=100
  smb_mid=6
  smt_wct=0
  smb_bcc=0
[2012/08/21 13:51:02.924294,  3] smbd/process.c:1662(process_smb)
  Transaction 6 of length 110 (0 toread)
[2012/08/21 13:51:02.924456,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.924515,  5] lib/util.c:342(show_msg)
  size=106
  smb_com=0x75
  smb_rcls=0
  smb_reh=0
  smb_err=0
  smb_flg=8
  smb_flg2=51201
  smb_tid=65535
  smb_pid=4424
  smb_uid=100
  smb_mid=7
  smt_wct=4
  smb_vwv[ 0]=  255 (0xFF)
  smb_vwv[ 1]=    0 (0x0)
  smb_vwv[ 2]=    8 (0x8)
  smb_vwv[ 3]=    1 (0x1)
  smb_bcc=63
[2012/08/21 13:51:02.925305,  3] smbd/process.c:1467(switch_message)
  switch message SMBtconX (pid 4425) conn 0x0
[2012/08/21 13:51:02.925411,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.925514,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.925614,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.925771,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.925891,  4] smbd/reply.c:794(reply_tcon_and_X)
  Client requested device type [?????] for share [HOME\MYUSER]
[2012/08/21 13:51:02.926019,  5] lib/username.c:171(Get_Pwnam_alloc)
  Finding user home/myuser
[2012/08/21 13:51:02.926121,  5] lib/username.c:116(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as lowercase is home/myuser
[2012/08/21 13:51:02.926321,  5] lib/username.c:134(Get_Pwnam_internals)
  Trying _Get_Pwnam(), username as uppercase is HOME/MYUSER
[2012/08/21 13:51:02.926501,  5] lib/username.c:143(Get_Pwnam_internals)
  Checking combinations of 0 uppercase letters in home/myuser
[2012/08/21 13:51:02.926606,  5] lib/username.c:149(Get_Pwnam_internals)
  Get_Pwnam_internals didn't find user [home/myuser]!
[2012/08/21 13:51:02.926713,  3] smbd/service.c:343(find_service)
  checking for home directory home/myuser gave (NULL)
[2012/08/21 13:51:02.926825,  3] smbd/service.c:357(find_service)
  checking whether home/myuser is a valid printer name...
[2012/08/21 13:51:02.926954,  1] printing/printer_list.c:94(printer_list_get_printer)
  Failed to fetch record!
[2012/08/21 13:51:02.927057,  3] smbd/service.c:371(find_service)
  home/myuser is not a valid printer name
[2012/08/21 13:51:02.927175,  0] param/loadparm.c:9095(process_usershare_file)
  process_usershare_file: share name home/myuser contains invalid characters (any of %<>*?|/\+=;:",)
[2012/08/21 13:51:02.927300,  3] smbd/service.c:444(find_service)
  find_service() failed to find service home/myuser
[2012/08/21 13:51:02.927404,  3] smbd/service.c:1307(make_connection)
  cesar (ipv4:192.168.0.150:40254) couldn't find service home/myuser
[2012/08/21 13:51:02.927536,  3] smbd/error.c:81(error_packet_set)
  error packet at smbd/reply.c(803) cmd=117 (SMBtconX) NT_STATUS_BAD_NETWORK_NAME
[2012/08/21 13:51:02.927644,  5] lib/util.c:332(show_msg)
[2012/08/21 13:51:02.927702,  5] lib/util.c:342(show_msg)
  size=35
  smb_com=0x75
  smb_rcls=204
  smb_reh=0
  smb_err=49152
  smb_flg=136
  smb_flg2=51203
  smb_tid=65535
  smb_pid=4424
  smb_uid=100
  smb_mid=7
  smt_wct=0
  smb_bcc=0
[2012/08/21 13:51:02.928720,  5] lib/util_sock.c:319(read_fd_with_timeout)
  read_fd_with_timeout: blocking read. EOF from client.
[2012/08/21 13:51:02.928936,  5] smbd/process.c:457(receive_smb_talloc)
  receive_smb_raw_talloc failed for client 192.168.0.150 read error = NT_STATUS_END_OF_FILE.
[2012/08/21 13:51:02.929088,  4] smbd/sec_ctx.c:314(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2012/08/21 13:51:02.929231,  5] ../libcli/security/security_token.c:53(security_token_debug)
  Security token: (NULL)
[2012/08/21 13:51:02.929367,  5] auth/token_util.c:527(debug_unix_user_token)
  UNIX token of user 0
  Primary group is 0 and contains 0 supplementary groups
[2012/08/21 13:51:02.929578,  5] smbd/uid.c:400(change_to_root_user)
  change_to_root_user: now uid=(0,0) gid=(0,0)
[2012/08/21 13:51:02.929767,  4] auth/pampass.c:483(smb_pam_start)
  smb_pam_start: PAM: Init user: myuser
[2012/08/21 13:51:02.937128,  4] auth/pampass.c:492(smb_pam_start)
  smb_pam_start: PAM: setting rhost to: 192.168.0.150
[2012/08/21 13:51:02.937290,  4] auth/pampass.c:501(smb_pam_start)
  smb_pam_start: PAM: setting tty
[2012/08/21 13:51:02.937393,  4] auth/pampass.c:509(smb_pam_start)
  smb_pam_start: PAM: Init passed for user: myuser
[2012/08/21 13:51:02.937494,  4] auth/pampass.c:646(smb_internal_pam_session)
  smb_internal_pam_session: PAM: tty set to: smb/4425/100
[2012/08/21 13:51:02.938339,  4] auth/pampass.c:465(smb_pam_end)
  smb_pam_end: PAM: PAM_END OK.
[2012/08/21 13:51:02.938677,  3] smbd/server_exit.c:180(exit_server_common)
  Server exit (failed to receive smb request)

```
Thanks for your help :p

---

### Post by redmk2 on 2012-08-21
> **apprentilinux said:**
> 

... when I try to connect myuser I get this error message 

```

root@SAMBA:/home# smbclient //SAMBA/home/myuser -U myuser
Enter myuser's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

Try this syntax for smbclient```
smbclient //server/share
```

...did you create a *share*?

---

### Post by apprentilinux on 2012-08-21
> **redmk2 said:**
> Try this syntax for smbclient```
smbclient //server/share
```...did you create a *share*?

yes i create a share folder, it works well. I don't have access to home user only

```


[Partage ]     comment = partage      path = /smb/partage     read only = No     guest ok = Yes


```

---

### Post by redmk2 on 2012-08-21
> **apprentilinux said:**
> yes i create a share folder, it works well. I don't have access to home user only

```


[Partage ]     comment = partage      path = /smb/partage     read only = No     guest ok = Yes


```

So we have a share defined in the smb.conf file like this```

[Partage ]
     comment = partage      
     path = /smb/partage
     read only = No
     guest ok = Yes

```

... The correct use of smbclient would be ```
smbclient //SAMBA/Partage
```

Have you tried this?

What do you mean by```
I don't have access to home user only

```...what is a home user?  Is it a directory?  Have you shared it?

---

### Post by apprentilinux on 2012-08-22
> **redmk2 said:**
> So we have a share defined in the smb.conf file like this```

[Partage ]
     comment = partage      
     path = /smb/partage
     read only = No
     guest ok = Yes

```... The correct use of smbclient would be ```
smbclient //SAMBA/Partage
```Have you tried this?

What do you mean by```
I don't have access to home user only

```...what is a home user?  Is it a directory?  Have you shared it?

Sorry for my english.

I have access to the shared common
 I don't have access to the home user ( like /home/myuser)

---

### Post by redmk2 on 2012-08-22
> **apprentilinux said:**
> Sorry for my english.

I have access to the shared common
 I don't have access to the home user ( like /home/myuser)

You need to share the it before you can access it via Samba.  You can do this using the [homes] share.  This is a special share that shares the users home directories.  See section in the man pages. ```
man smb.conf
```

---

