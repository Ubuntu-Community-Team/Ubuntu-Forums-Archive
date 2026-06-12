---
title: "ssh_exchange_identification: Connection closed by remote host"
date: 2011-10-09
forum: Server Platforms
---

### Post by Andylau on 2011-10-09
Learnt from [http://ericlondon.com/setting-passwordless-automated-rsync-backup](http://ericlondon.com/setting-passwordless-automated-rsync-backup),
I am setting up a passwordless automated rsync backup

After I would like to SCP the public key file (id_dsa.pub) to the computer that will receive the files, referred to as "remote".

local$ scp ~/.ssh/id_dsa.pub [email]Eric@remote:~/.ssh/id_dsa.pub.transf[/email]erred

The terminal gives this message:
ssh_exchange_identification: Connection closed by remote host
lost connection

Any help appreciated please.

---

### Post by Doug S on 2011-10-09
Does passworless SSH to that same remote server work?
If so, do you have this line in your sshd_config file (enables sftp):```
Subsystem sftp /usr/lib/openssh/sftp-server
```
There should be some entries in /var/log/auth.log that might help to understand what is wrong.

---

### Post by Andylau on 2011-10-09
No, it doesnt.
If I type the command:
local$ ssh Eric@remote

Eric is my username
remote is my IP address

It gives the same message as well:
ssh_exchange_identification: Connection closed by remote host

I havnt seen the sshd_config file (enables sftp) before.
I follow the instructions given by Eric on [http://ericlondon.com/setting-passwordless-automated-rsync-backup](http://ericlondon.com/setting-passwordless-automated-rsync-backup).

Everything works well until the connection to server part.

I have found the auth.log. here is its content:

Oct  9 03:09:01 qs10 CRON[1728]: pam_unix(cron:session): session opened for user root by (uid=0)

Oct  9 03:09:01 qs10 CRON[1728]: pam_unix(cron:session): session closed for user root

Oct  9 03:17:02 qs10 CRON[1738]: pam_unix(cron:session): session opened for user root by (uid=0)

Oct  9 03:17:02 qs10 CRON[1738]: pam_unix(cron:session): session closed for user root

Oct  9 03:39:01 qs10 CRON[1920]: pam_unix(cron:session): session opened for user root by (uid=0)

Oct  9 03:39:01 qs10 CRON[1920]: pam_unix(cron:session): session closed for user root

Oct  9 04:09:01 qs10 CRON[1985]: pam_unix(cron:session): session opened for user root by (uid=0)

Oct  9 04:09:01 qs10 CRON[1985]: pam_unix(cron:session): session closed for user root

Oct  9 04:17:01 qs10 CRON[2094]: pam_unix(cron:session): session opened for user root by (uid=0)

Oct  9 04:17:01 qs10 CRON[2094]: pam_unix(cron:session): session closed for user root


Do you know what this is about?
Hope to understand what is wrong.

---

### Post by Doug S on 2011-10-09
The sshd_config file should be in the /etc/ssh folder.
On the remote computer is the ssh server running? Example:```
doug@doug-64:~$ [COLOR=red]ps aux | grep sshd[/COLOR]
root       919  0.0  0.0  49312  2644 ?        Ss   Sep27   0:00 [COLOR=red]/usr/sbin/sshd -D[/COLOR]
root      7541  0.0  0.1 106628  5048 ?        Ss   Oct01   0:01 sshd: doug [priv]
doug      7555  0.0  0.0 106628  2212 ?        S    Oct01   0:13 sshd: doug@pts/0
root     10489  0.0  0.1 106628  5124 ?        Ss   Oct06   0:00 sshd: doug [priv]
doug     10503  0.0  0.0 106628  2212 ?        S    Oct06   0:03 sshd: doug@pts/1
doug     29375  0.0  0.0   8900   852 pts/1    S+   07:11   0:00 grep --color=auto sshd
```
The auth.log files contains many entries. The ones you listed are normal and from the periodic cron jobs. Entries from the ssh server on the remote machine will have an sshd prefix. (Edited) Example:```
grep sshd /var/log/auth.log
Oct  9 05:47:26 doug-64 sshd[29079]: Set /proc/self/oom_adj to 0
Oct  9 05:47:26 doug-64 sshd[29079]: Connection from 1.202.249.106 port 27997
Oct  9 05:47:28 doug-64 sshd[29079]: User root from 1.202.249.106 not allowed because not listed in AllowUsers
Oct  9 05:47:28 doug-64 sshd[29079]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=1.202.249.106  user=root
Oct  9 05:47:28 doug-64 sshd[29079]: pam_winbind(sshd:auth): getting password (0x00000388)
Oct  9 05:47:28 doug-64 sshd[29079]: pam_winbind(sshd:auth): pam_get_item returned a password
Oct  9 05:47:28 doug-64 sshd[29079]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_SYSTEM_ERR (4), NTSTATUS: NT_STATUS_INVALID_HANDLE, Error message was: Invalid handle
Oct  9 05:47:28 doug-64 sshd[29079]: pam_winbind(sshd:auth): internal module error (retval = PAM_SYSTEM_ERR(4), user = 'root')
Oct  9 05:47:30 doug-64 sshd[29079]: Failed password for invalid user root from 1.202.249.106 port 27997 ssh2
```
 
A posting on another thread by Dangertux ( [http://ubuntuforums.org/showpost.php?p=11325054&postcount=6](http://ubuntuforums.org/showpost.php?p=11325054&postcount=6) ) reminded me that I had meant to mention that I run at LogLevel VERBOSE, instead of the default INFO. You might want to go even higher to help investigate this.
 
Hope this helps.

---

