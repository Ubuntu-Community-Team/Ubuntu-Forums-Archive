---
title: "Only Single AD Group of Several Allowed On Samba Shares"
date: 2016-10-01
forum: Server Platforms
---

### Post by TheHackMan on 2016-10-01
I've been scratching my head over this for a while and have tried removing and adding just about everything in the smb.conf file to see if I could get this to work. Basically I have several AD groups that I see on the server but the problem comes in with the fact only the "Domain Users" group is allowed to access any of the samba shares. If I change it to something like "Domain Admins" for a share, I lose access, but when I change it back to "Domain Users" I gain access back. If anybody could help point me in the right direction or see if I missed something by accident that would be greatly appreciated. If I didn't include something let me know.

Server Version: Ubuntu Server 16.04 x64


I've check the logs for samba and see nothing but:
> [2016/10/01 13:53:34.520666,  3] ../source3/lib/access.c:338(allow_access)

Under the logs.IP ADDRESS I see this for some reason:
> [2016/10/01 14:10:23.546251,  3] ../source3/auth/auth.c:178(auth_check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [DOMAIN]\[thehackman]@[DESKTOP-H2TRMF2] with the new password interface
[2016/10/01 14:10:23.546272,  3] ../source3/auth/auth.c:181(auth_check_ntlm_password)
  check_ntlm_password:  mapped user is: [DOMAIN]\[thehackman]@[DESKTOP-H2TRMF2]
[2016/10/01 14:10:23.548518,  3] ../source3/auth/auth.c:249(auth_check_ntlm_password)
  check_ntlm_password: winbind authentication for user [thehackman] succeeded
[2016/10/01 14:10:23.554576,  2] ../source3/auth/pampass.c:577(smb_pam_account)
  smb_pam_account: PAM: There was an authentication error for user DOMAIN\thehackman@DOMAIN.LOCAL
[2016/10/01 14:10:23.554603,  2] ../source3/auth/pampass.c:89(smb_pam_error_handler)
  smb_pam_error_handler: PAM: Account Check Failed : Authentication failure
[2016/10/01 14:10:23.554722,  0] ../source3/auth/pampass.c:797(smb_pam_accountcheck)
  smb_pam_accountcheck: PAM: Account Validation Failed - Rejecting User DOMAIN\thehackman@DOMAIN.LOCAL!
[2016/10/01 14:10:23.555217,  3] ../source3/auth/auth.c:295(auth_check_ntlm_password)
  check_ntlm_password:  PAM Account for user [DOMAIN\thehackman@DOMAIN.LOCAL] FAILED with error NT_STATUS_WRONG_PASSWORD
[2016/10/01 14:10:23.555260,  2] ../auth/gensec/spnego.c:716(gensec_spnego_server_negTokenTarg)
  SPNEGO login failed: NT_STATUS_WRONG_PASSWORD
[2016/10/01 14:10:23.555933,  3] ../source3/smbd/server_exit.c:252(exit_server_common)
  Server exit (NT_STATUS_CONNECTION_RESET)

smb.conf
```
[global]
        realm = DOMAIN.LOCAL
        server string = %h server (Samba, Ubuntu)
        security = ADS
        workgroup = DOMAIN
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccess$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        log level = 3
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        idmap config * :range = 102000-109999
        allow trusted domains = Yes
       #idmap config for domain
        idmap config DOMAIN:backend = rid
        idmap config DOMAIN:schema_mode = rfc2307
        idmap config DOMAIN:range = 10000-99999
        idmap config DOMAIN:default = yes
        idmap config DOMAIN:readonly = no
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        winbind nested groups = yes
        winbind refresh tickets = yes
        encrypt passwords = true
       # Use settings from AD for login shell and home directory
        winbind nss info = rfc2307
		
		
		
-------------------------------------------------------------------------------------
NOT WORKING
-------------------------------------------------------------------------------------
[Media_Backup]
        comment = Media_Backup
        path = /media/nas/media
        valid users = @DOMAIN\"Samba Admin"
        admin users = @DOMAIN\"Samba Admin"
        read only = No
        create mask = 0755


-------------------------------------------------------------------------------------
WORKING
-------------------------------------------------------------------------------------
[Remodel_Backup]
        comment = Remodel_Backup
        path = /media/nas/remodeling
        valid users = @DOMAIN\"Domain Users"
        admin users = @DOMAIN\"Domain Users"
        read only = No
        create mask = 0755

```



Edit:
The only other piece of information I managed to gather after a couple hours of trying different things was seeing this message as well:

> string_to_sid: SID is not in a valid format

I've tried tracking down any information on it but everything just leads to a dead end.

---

### Post by TheHackMan on 2016-10-02
I THINK I might have fixed it but I'm not 100% sure. After a lot of poking around I stumbled upon this command here:
sudo net sam rights grant "DOMAIN\Domain Admins" SeDiskOperatorPrivilege -U Administrator

I issued that command and after a couple tweaks to the smb.conf file
Added the line "winbind separator = +"
Changed  the 'valid users' line to 'valid users = @"DOMAIN+Domain Admins"

I also followed these two guides to re-setup everything on the server for SAMBA before doing the above:
[https://www.server-world.info/en/note?os=Ubuntu_14.04&p=samba&f=4](https://www.server-world.info/en/note?os=Ubuntu_14.04&p=samba&f=4)
[https://jimshaver.net/2016/05/30/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-16-04/](https://jimshaver.net/2016/05/30/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-16-04/)


So I'm not sure if what I did was 100% correct, and if it wasn't please let me know.

---

