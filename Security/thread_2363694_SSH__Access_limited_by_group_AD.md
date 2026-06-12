---
title: "SSH : Access limited by group AD"
date: 2017-06-13
forum: Security
---

### Post by arcocide on 2017-06-13
Hi,

I connect my Ubuntu 16.04 server to my AD.
I would like now to limited the access to SSH with  group AD.

I try with the option "AllowGroups ADGROUP" but i have error :

Jun 13 11:22:32 SRV-DEV-UBUNTU sshd[1737]: User inf_user from 192.168.90.80 not allowed because none of user's groups are listed in AllowGroups
Jun 13 11:22:32 SRV-DEV-UBUNTU sshd[1737]: input_userauth_request: invalid user inf_user [preauth]
Jun 13 11:22:37 SRV-DEV-UBUNTU sshd[1737]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.90.80  user=inf_user
Jun 13 11:22:37 SRV-DEV-UBUNTU sshd[1737]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 13 11:22:37 SRV-DEV-UBUNTU sshd[1737]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 13 11:22:38 SRV-DEV-UBUNTU sshd[1737]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_LOGON_FAILURE, Errr message was: Logon failure
Jun 13 11:22:38 SRV-DEV-UBUNTU sshd[1737]: pam_winbind(sshd:auth): user 'inf_user' denied access (incorrect password or invalid membership)
Jun 13 11:22:40 SRV-DEV-UBUNTU sshd[1737]: Failed password for invalid user inf_user from 192.168.90.80 port 54540 ssh2

For infirmation i can to connect in SSH with any user AD if I don't use AllowGroups

---

### Post by deadflowr on 2017-06-13
Is the group name actually ADGROUP or something else.

---

### Post by arcocide on 2017-06-14
The group's name is DOMAINE\INFRA_ADmins

So i put : AllowGroups INFRA_ADmins

It's only AD group.

---

