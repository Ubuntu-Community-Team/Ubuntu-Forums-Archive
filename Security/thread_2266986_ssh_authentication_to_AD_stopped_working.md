---
title: "ssh authentication to AD stopped working"
date: 2015-02-26
forum: Security
---

### Post by nenad-cuturic on 2015-02-26
Last evening after power failure and reboot ssh authentication to Windows AD stopped working.
Samba (AD) is still working and even unix login but when trying to login with AD account the following error is logged:

Feb 26 18:01:02 <server_name> sshd[2839]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 26 18:01:02 <server_name> sshd[2839]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 26 18:01:03 <server_name> sshd[2839]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_SYSTEM_ERR (4), NTSTATUS: NT_STATUS_OBJECT_NAME_NOT_FOUND, Error message was: NT_STATUS_OBJECT_NAME_NOT_FOUND
Feb 26 18:01:03 <server_name> sshd[2839]: pam_winbind(sshd:auth): internal module error (retval = PAM_SYSTEM_ERR(4), user = 'user_name')
Feb 26 18:01:04 <server_name> sshd[2837]: error: PAM: Authentication failure for user_name from <client computer>

That was when password is correct. With wrong password:

Feb 26 18:15:46 <server_name> sshd[3264]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_LOGON_FAILURE, Error message was: Logon failure
Feb 26 18:15:46 <server_name> sshd[3264]: pam_winbind(sshd:auth): user 'user_name' denied access (incorrect password or invalid membership)
Feb 26 18:15:49 <server_name> sshd[3262]: error: PAM: Authentication failure for user_name from <client computer>

No change in any related conf-file is made prior to this or at least not for almost a year.
After reboot I did system upgrade which could've also broken something but that is probably a long shot.
id/wbinfo -u|-g|-a/kinit work as expected.

System details:
Ubuntu 10.04.4 LTS
Linux 2.6.32-71-server #138-Ubuntu SMP Thu Dec 18 17:51:53 UTC 2014 x86_64 GNU/Linux
Samba version 3.4.7
Kerberos 5 release 1.8.1

Any suggestion/clue/hint about what I should check or do?

---

### Post by nenad-cuturic on 2015-02-26
Additional (debug) info:

Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] ENTER: pam_sm_authenticate (flags: 0x0001)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_SERVICE) = "sshd" (0x7f811a395fb0)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_USER) = "user_name" (0x7f811a39f3b0)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_TTY) = "ssh" (0x7f811a39df20)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_RHOST) = "client" (0x7f811a39e160)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_AUTHTOK) = 0x7f811a39f3d0
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_CONV) = 0x7f811a39df40
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): getting password (0x00001389)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): Verify user 'user_name'
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): PAM config: krb5_ccache_type 'FILE'
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): enabling krb5 login flag
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): enabling cached login flag
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): enabling request for a FILE krb5 ccache
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_SYSTEM_ERR (4), NTSTATUS: NT_STATUS_OBJECT_NAME_NOT_FOUND, Error message was: NT_STATUS_OBJECT_NAME_NOT_FOUND
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): internal module error (retval = PAM_SYSTEM_ERR(4), user = 'user_name')
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] LEAVE: pam_sm_authenticate returning 4 (PAM_SYSTEM_ERR)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_SERVICE) = "sshd" (0x7f811a395fb0)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_USER) = "user_name" (0x7f811a39f3b0)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_TTY) = "ssh" (0x7f811a39df20)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_RHOST) = "client" (0x7f811a39e160)
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_AUTHTOK) = 0x7f811a39f3d0
Feb 26 23:14:58 <server_name> sshd[9644]: pam_winbind(sshd:auth): [pamh: 0x7f811a39f230] STATE: ITEM(PAM_CONV) = 0x7f811a39df40
Feb 26 23:15:00 <server_name> sshd[9640]: error: PAM: Authentication failure for user_name from client

plus:

kerberos ticken is obtained in /tmp/krb5cc_10130 (uid=10130)

---

### Post by nenad-cuturic on 2015-02-27
After a lot of googling (not so helpfull though it gave me some ideas what I could experiment with) and experimenting I've got it working again. I'm not sure whether there are some side effects of this solution but so far no problems discovered.
What I did is to change pam_winbind setting in **/etc/pam.d/common-auth**:
from:
*auth    [success=1 default=ignore]      pam_winbind.so krb5_ccache_type=FILE cached_login try_first_pass*
to
*auth    [success=1 default=ignore]      pam_winbind.so krb5_auth try_first_pass* 

Without "try_first_pass" it required typing password two times. I guess it is because the first attempt is made to login with pam_unix and then it falls back to pam_windbind.
Does anybody see any possible problem with this setting?

It wasn't who set up the server originally (almost 4 years ago) and I haven't been working with samba/AD authentication that much so this was just quick and dirty self course/fix to solve urgent problem (students sftp access to home maps).

---

