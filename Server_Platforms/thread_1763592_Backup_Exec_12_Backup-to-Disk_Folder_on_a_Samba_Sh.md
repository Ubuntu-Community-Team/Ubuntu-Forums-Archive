---
title: "Backup Exec 12 Backup-to-Disk Folder on a Samba Share"
date: 2011-05-20
forum: Server Platforms
---

### Post by jbutz on 2011-05-20
I am trying to setup Backup Exec 12 to use a samba share on an Ubuntu 10.04 server as a Backup-to-Disk folder. I get an error that says "Unable to create new backup folder. Access denied." when I try to add the Backup-to-Disk.

The following is what shows up in the Samba log for the server I am connecting from.
```
[2011/05/20 14:37:06,  3] smbd/process.c:1459(process_smb)
  Transaction 4 of length 1570 (0 toread)
[2011/05/20 14:37:06,  3] smbd/process.c:1273(switch_message)
  switch message SMBsesssetupX (pid 12330) conn 0x0
[2011/05/20 14:37:06,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1404(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2011/05/20 14:37:06,  2] smbd/sesssetup.c:1360(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1160(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1202(reply_sesssetup_and_X_spnego)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:786(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 1309
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:378(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: enc type [23] failed to decrypt with error Decrypt integrity check failed
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:568(ads_verify_ticket)
  ads_verify_ticket: krb5_rd_req with auth failed (Bad encryption type)
[2011/05/20 14:37:06,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/05/20 14:37:06,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2011/05/20 14:37:06,  3] smbd/process.c:1459(process_smb)
  Transaction 5 of length 1570 (0 toread)
[2011/05/20 14:37:06,  3] smbd/process.c:1273(switch_message)
  switch message SMBsesssetupX (pid 12330) conn 0x0
[2011/05/20 14:37:06,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1404(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2011/05/20 14:37:06,  2] smbd/sesssetup.c:1360(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1160(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1202(reply_sesssetup_and_X_spnego)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:786(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 1309
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:378(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: enc type [23] failed to decrypt with error Decrypt integrity check failed
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:568(ads_verify_ticket)
  ads_verify_ticket: krb5_rd_req with auth failed (Bad encryption type)
[2011/05/20 14:37:06,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/05/20 14:37:06,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2011/05/20 14:37:06,  3] smbd/process.c:1459(process_smb)
  Transaction 6 of length 1570 (0 toread)
[2011/05/20 14:37:06,  3] smbd/process.c:1273(switch_message)
  switch message SMBsesssetupX (pid 12330) conn 0x0
[2011/05/20 14:37:06,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1404(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2011/05/20 14:37:06,  2] smbd/sesssetup.c:1360(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1160(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:1202(reply_sesssetup_and_X_spnego)
  NativeOS=[Windows Server 2003 3790 Service Pack 2] NativeLanMan=[] PrimaryDomain=[Windows Server 2003 5.2]
[2011/05/20 14:37:06,  3] smbd/sesssetup.c:786(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 1309
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:378(ads_secrets_verify_ticket)
  ads_secrets_verify_ticket: enc type [23] failed to decrypt with error Decrypt integrity check failed
[2011/05/20 14:37:06,  3] libads/kerberos_verify.c:568(ads_verify_ticket)
  ads_verify_ticket: krb5_rd_req with auth failed (Bad encryption type)
[2011/05/20 14:37:06,  1] smbd/sesssetup.c:342(reply_spnego_kerberos)
  Failed to verify incoming ticket with error NT_STATUS_LOGON_FAILURE!
[2011/05/20 14:37:06,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/sesssetup.c(344) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
```I was trying to add it to a share that required authentication. But I was able to get it to connect to my desktop's public share so now I am trying to get it to go to a public share. Below is the Samba config for the share:
```
[backupexec$]
        comment = Backup Exec
        path = /home/backupexec
        browsable = yes
        writable = yes
        read only = no
        guest only = yes
        create mask = 0644
        directory mask = 0755
```

Does anyone have any insight to share?

---

