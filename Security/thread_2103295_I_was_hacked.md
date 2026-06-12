---
title: "I was hacked"
date: 2013-01-09
forum: Security
---

### Post by p2ranger on 2013-01-09
I'm running Ubuntu 12.04 server. I just this past week finished reinstalling my server due to a botched upgrade. Just a little while ago, my server stopped responding. I had to reboot it and as I looked in the log files, I had been hacked. I'm thinking it was through the ssh port.

Wonderful

So, how do I go about securing this and making sure there wasn't something malicious installed on there during this time? I discovered I had accidentally left port 22 open on my router. I just closed it and had no intention on it being open.

Which log files do I need to look through to see what may have happened?

Below is how I know it was hacked:

```

.
.
hundreds of lines like the top ones
.
.
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:38 lfs sshd[31114]: Failed password for root from 118.192.2.50 port 55649 ssh2
Jan  9 13:43:38 lfs sshd[31114]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:45 lfs sshd[31116]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:47 lfs sshd[31116]: Failed password for root from 118.192.2.50 port 58004 ssh2
Jan  9 13:43:47 lfs sshd[31116]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:54 lfs sshd[31118]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:56 lfs sshd[31118]: Failed password for root from 118.192.2.50 port 60447 ssh2
Jan  9 13:43:57 lfs sshd[31118]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:03 lfs sshd[31121]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:06 lfs sshd[31121]: Failed password for root from 118.192.2.50 port 34919 ssh2
Jan  9 13:44:06 lfs sshd[31121]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:13 lfs sshd[31123]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:14 lfs sshd[31123]: Failed password for root from 118.192.2.50 port 37515 ssh2
Jan  9 13:44:14 lfs sshd[31123]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:21 lfs sshd[31125]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:23 lfs sshd[31125]: Failed password for root from 118.192.2.50 port 39918 ssh2
Jan  9 13:44:23 lfs sshd[31125]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:30 lfs sshd[31127]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:32 lfs sshd[31127]: Failed password for root from 118.192.2.50 port 42414 ssh2
Jan  9 13:44:33 lfs sshd[31127]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 14:09:01 lfs CRON[31360]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:09:01 lfs CRON[31360]: pam_unix(cron:session): session closed for user root
Jan  9 14:17:01 lfs CRON[31416]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:17:01 lfs CRON[31416]: pam_unix(cron:session): session closed for user root
Jan  9 14:39:01 lfs CRON[31600]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:39:01 lfs CRON[31600]: pam_unix(cron:session): session closed for user root
Jan  9 15:09:02 lfs CRON[31879]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:09:02 lfs CRON[31879]: pam_unix(cron:session): session closed for user root
Jan  9 15:17:01 lfs CRON[31969]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:17:01 lfs CRON[31969]: pam_unix(cron:session): session closed for user root
Jan  9 15:39:01 lfs CRON[32155]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:39:01 lfs CRON[32155]: pam_unix(cron:session): session closed for user root
Jan  9 16:09:01 lfs CRON[32434]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:09:01 lfs CRON[32434]: pam_unix(cron:session): session closed for user root
Jan  9 16:17:01 lfs CRON[32525]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:17:01 lfs CRON[32525]: pam_unix(cron:session): session closed for user root
Jan  9 16:39:01 lfs CRON[32715]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:39:01 lfs CRON[32715]: pam_unix(cron:session): session closed for user root
Jan  9 16:50:49 lfs sshd[587]: Received signal 15; terminating.
Jan  9 16:50:49 lfs sshd[891]: Server listening on 0.0.0.0 port 22.
Jan  9 16:50:49 lfs sshd[891]: Server listening on :: port 22.
Jan  9 16:50:53 lfs sshd[926]: Accepted publickey for jason from 192.168.1.100 port 51132 ssh2
Jan  9 16:50:53 lfs sshd[926]: pam_unix(sshd:session): session opened for user jason by (uid=0)
Jan  9 16:50:54 lfs smbd[948]: pam_unix(samba:session): session opened for user jason by (uid=0)

```

Around 1650 is where I rebooted and logged back in

I know there's a lot that I don't know about this

Thanks for any help

Jason

---

### Post by jerome1232 on 2013-01-09
Do you think you can grep that log for sshd and repost it? All I see from what you posted are failed ssh attempts on the root account (which is disabled in Ubuntu) which is fairly normal for a ssh server exposed to the Internet.

```
grep sshd /var/log/auth.log
```

---

### Post by p2ranger on 2013-01-09
Its a lot of output, and the file is too large to attach. Any better idea how I can get the data on here?

The reason I think I was hacked is because all the lines saying getting password. But looking through it all, it shows that a lot of times. The server shut down and I then restarted around 1650. Looking at most of those attempts they happened around 1330. So maybe nothing happened. There's lots more attempts than what I'm including, but they were longer ago.

The reason I knew something was wrong was because my samba share disconnected suddenly from the desktop I was using. Then I  noticed the ssh terminal I had connected to the server wouldn't respond and the server wouldn't respond to a ping.

I'll include more of the output, but I don't want to post a huge post as I don't want to be rude. This is from the beginning of the attempt to the time the server shutdown and I turned it back on.

```

Jan  9 12:12:47 lfs sshd[30056]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=cpdns2.h100.com.br  user=root
Jan  9 12:12:47 lfs sshd[30056]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 12:12:47 lfs sshd[30056]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 12:12:47 lfs sshd[30056]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 12:12:48 lfs sshd[30056]: Failed password for root from 173.203.238.229 port 51418 ssh2
Jan  9 12:12:48 lfs sshd[30056]: Received disconnect from 173.203.238.229: 11: Bye Bye [preauth]
Jan  9 12:17:01 lfs CRON[30101]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 12:17:01 lfs CRON[30101]: pam_unix(cron:session): session closed for user root
Jan  9 12:39:01 lfs CRON[30290]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 12:39:01 lfs CRON[30290]: pam_unix(cron:session): session closed for user root
Jan  9 13:09:01 lfs CRON[30569]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 13:09:01 lfs CRON[30569]: pam_unix(cron:session): session closed for user root
Jan  9 13:17:01 lfs CRON[30632]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 13:17:01 lfs CRON[30632]: pam_unix(cron:session): session closed for user root
Jan  9 13:27:46 lfs sshd[30729]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:27:46 lfs sshd[30729]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:27:46 lfs sshd[30729]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:27:46 lfs sshd[30729]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:27:49 lfs sshd[30729]: Failed password for root from 118.192.2.50 port 39754 ssh2
Jan  9 13:27:49 lfs sshd[30729]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:27:56 lfs sshd[30742]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:27:56 lfs sshd[30742]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:27:56 lfs sshd[30742]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:27:56 lfs sshd[30742]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:27:58 lfs sshd[30742]: Failed password for root from 118.192.2.50 port 42585 ssh2
Jan  9 13:27:58 lfs sshd[30742]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:28:05 lfs sshd[30767]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:28:05 lfs sshd[30767]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:28:05 lfs sshd[30767]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:28:05 lfs sshd[30767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:28:07 lfs sshd[30767]: Failed password for root from 118.192.2.50 port 45365 ssh2
Jan  9 13:28:07 lfs sshd[30767]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:28:14 lfs sshd[30769]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:28:14 lfs sshd[30769]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:28:14 lfs sshd[30769]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:28:14 lfs sshd[30769]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:28:16 lfs sshd[30769]: Failed password for root from 118.192.2.50 port 47963 ssh2
Jan  9 13:28:16 lfs sshd[30769]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:28:23 lfs sshd[30771]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:28:23 lfs sshd[30771]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:28:23 lfs sshd[30771]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:28:23 lfs sshd[30771]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:28:25 lfs sshd[30771]: Failed password for root from 118.192.2.50 port 50569 ssh2
Jan  9 13:28:25 lfs sshd[30771]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:28:32 lfs sshd[30773]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:28:32 lfs sshd[30773]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:28:32 lfs sshd[30773]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:28:32 lfs sshd[30773]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:28:35 lfs sshd[30773]: Failed password for root from 118.192.2.50 port 53187 ssh2
Jan  9 13:28:35 lfs sshd[30773]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:28:42 lfs sshd[30775]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:28:42 lfs sshd[30775]: pam_winbind(sshd:auth): getting password (0x00000388)

.
.
.
.
.
.
Jan  9 13:36:34 lfs sshd[30932]: Failed password for root from 118.192.2.50 port 45492 ssh2
Jan  9 13:36:34 lfs sshd[30932]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:36:41 lfs sshd[30934]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:36:41 lfs sshd[30934]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:36:41 lfs sshd[30934]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:36:41 lfs sshd[30934]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:36:43 lfs sshd[30934]: Failed password for root from 118.192.2.50 port 48198 ssh2
Jan  9 13:36:43 lfs sshd[30934]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:36:50 lfs sshd[30936]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:36:50 lfs sshd[30936]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:36:50 lfs sshd[30936]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:36:50 lfs sshd[30936]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:36:52 lfs sshd[30936]: Failed password for root from 118.192.2.50 port 50750 ssh2
Jan  9 13:36:52 lfs sshd[30936]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:36:59 lfs sshd[30939]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:36:59 lfs sshd[30939]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:36:59 lfs sshd[30939]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:36:59 lfs sshd[30939]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:01 lfs sshd[30939]: Failed password for root from 118.192.2.50 port 53415 ssh2
Jan  9 13:37:01 lfs sshd[30939]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:08 lfs sshd[30941]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:08 lfs sshd[30941]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:08 lfs sshd[30941]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:08 lfs sshd[30941]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:10 lfs sshd[30941]: Failed password for root from 118.192.2.50 port 56043 ssh2
Jan  9 13:37:10 lfs sshd[30941]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:17 lfs sshd[30943]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:17 lfs sshd[30943]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:17 lfs sshd[30943]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:17 lfs sshd[30943]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:19 lfs sshd[30943]: Failed password for root from 118.192.2.50 port 58742 ssh2
Jan  9 13:37:19 lfs sshd[30943]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:26 lfs sshd[30945]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:26 lfs sshd[30945]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:26 lfs sshd[30945]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:26 lfs sshd[30945]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:28 lfs sshd[30945]: Failed password for root from 118.192.2.50 port 33082 ssh2
Jan  9 13:37:28 lfs sshd[30945]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:35 lfs sshd[30947]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:35 lfs sshd[30947]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:35 lfs sshd[30947]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:35 lfs sshd[30947]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:37 lfs sshd[30947]: Failed password for root from 118.192.2.50 port 35795 ssh2
Jan  9 13:37:37 lfs sshd[30947]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:44 lfs sshd[30949]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:44 lfs sshd[30949]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:44 lfs sshd[30949]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:44 lfs sshd[30949]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:46 lfs sshd[30949]: Failed password for root from 118.192.2.50 port 38395 ssh2
Jan  9 13:37:46 lfs sshd[30949]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:37:53 lfs sshd[30951]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:37:53 lfs sshd[30951]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:37:53 lfs sshd[30951]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:37:53 lfs sshd[30951]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:37:55 lfs sshd[30951]: Failed password for root from 118.192.2.50 port 40950 ssh2
Jan  9 13:37:55 lfs sshd[30951]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:02 lfs sshd[30953]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:02 lfs sshd[30953]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:02 lfs sshd[30953]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:02 lfs sshd[30953]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:04 lfs sshd[30953]: Failed password for root from 118.192.2.50 port 43591 ssh2
Jan  9 13:38:05 lfs sshd[30953]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:11 lfs sshd[30956]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:11 lfs sshd[30956]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:11 lfs sshd[30956]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:11 lfs sshd[30956]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:13 lfs sshd[30956]: Failed password for root from 118.192.2.50 port 46308 ssh2
Jan  9 13:38:13 lfs sshd[30956]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:20 lfs sshd[30992]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:20 lfs sshd[30992]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:20 lfs sshd[30992]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:20 lfs sshd[30992]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:23 lfs sshd[30992]: Failed password for root from 118.192.2.50 port 48842 ssh2
Jan  9 13:38:23 lfs sshd[30992]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:30 lfs sshd[30994]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:30 lfs sshd[30994]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:30 lfs sshd[30994]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:30 lfs sshd[30994]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:32 lfs sshd[30994]: Failed password for root from 118.192.2.50 port 51624 ssh2
Jan  9 13:38:32 lfs sshd[30994]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:39 lfs sshd[30996]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:39 lfs sshd[30996]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:39 lfs sshd[30996]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:39 lfs sshd[30996]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:40 lfs sshd[30996]: Failed password for root from 118.192.2.50 port 54311 ssh2
Jan  9 13:38:41 lfs sshd[30996]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:47 lfs sshd[30999]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:47 lfs sshd[30999]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:47 lfs sshd[30999]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:47 lfs sshd[30999]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:50 lfs sshd[30999]: Failed password for root from 118.192.2.50 port 56871 ssh2
Jan  9 13:38:50 lfs sshd[30999]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:38:57 lfs sshd[31003]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:38:57 lfs sshd[31003]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:38:57 lfs sshd[31003]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:38:57 lfs sshd[31003]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:38:58 lfs sshd[31003]: Failed password for root from 118.192.2.50 port 59573 ssh2
Jan  9 13:38:58 lfs sshd[31003]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:01 lfs CRON[31007]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 13:39:01 lfs CRON[31007]: pam_unix(cron:session): session closed for user root
Jan  9 13:39:05 lfs sshd[31005]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:05 lfs sshd[31005]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:05 lfs sshd[31005]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:05 lfs sshd[31005]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:07 lfs sshd[31005]: Failed password for root from 118.192.2.50 port 33826 ssh2
Jan  9 13:39:07 lfs sshd[31005]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:14 lfs sshd[31014]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:14 lfs sshd[31014]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:14 lfs sshd[31014]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:14 lfs sshd[31014]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:17 lfs sshd[31014]: Failed password for root from 118.192.2.50 port 36464 ssh2
Jan  9 13:39:17 lfs sshd[31014]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:24 lfs sshd[31017]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:24 lfs sshd[31017]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:24 lfs sshd[31017]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:24 lfs sshd[31017]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:26 lfs sshd[31017]: Failed password for root from 118.192.2.50 port 39262 ssh2
Jan  9 13:39:26 lfs sshd[31017]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:33 lfs sshd[31019]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:33 lfs sshd[31019]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:33 lfs sshd[31019]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:33 lfs sshd[31019]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:34 lfs sshd[31019]: Failed password for root from 118.192.2.50 port 42018 ssh2
Jan  9 13:39:35 lfs sshd[31019]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:42 lfs sshd[31021]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:42 lfs sshd[31021]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:42 lfs sshd[31021]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:42 lfs sshd[31021]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:44 lfs sshd[31021]: Failed password for root from 118.192.2.50 port 44567 ssh2
Jan  9 13:39:44 lfs sshd[31021]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:39:51 lfs sshd[31024]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:39:51 lfs sshd[31024]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:39:51 lfs sshd[31024]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:39:51 lfs sshd[31024]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:39:53 lfs sshd[31024]: Failed password for root from 118.192.2.50 port 47220 ssh2
Jan  9 13:39:53 lfs sshd[31024]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:00 lfs sshd[31026]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:00 lfs sshd[31026]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:00 lfs sshd[31026]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:00 lfs sshd[31026]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:02 lfs sshd[31026]: Failed password for root from 118.192.2.50 port 49932 ssh2
Jan  9 13:40:02 lfs sshd[31026]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:09 lfs sshd[31028]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:09 lfs sshd[31028]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:09 lfs sshd[31028]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:09 lfs sshd[31028]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:11 lfs sshd[31028]: Failed password for root from 118.192.2.50 port 52665 ssh2
Jan  9 13:40:12 lfs sshd[31028]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:18 lfs sshd[31030]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:18 lfs sshd[31030]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:18 lfs sshd[31030]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:18 lfs sshd[31030]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:20 lfs sshd[31030]: Failed password for root from 118.192.2.50 port 55306 ssh2
Jan  9 13:40:20 lfs sshd[31030]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:27 lfs sshd[31033]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:27 lfs sshd[31033]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:27 lfs sshd[31033]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:27 lfs sshd[31033]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:30 lfs sshd[31033]: Failed password for root from 118.192.2.50 port 57916 ssh2
Jan  9 13:40:30 lfs sshd[31033]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:37 lfs sshd[31035]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:37 lfs sshd[31035]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:37 lfs sshd[31035]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:37 lfs sshd[31035]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:39 lfs sshd[31035]: Failed password for root from 118.192.2.50 port 60756 ssh2
Jan  9 13:40:40 lfs sshd[31035]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:46 lfs sshd[31037]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:46 lfs sshd[31037]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:46 lfs sshd[31037]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:46 lfs sshd[31037]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:49 lfs sshd[31037]: Failed password for root from 118.192.2.50 port 35222 ssh2
Jan  9 13:40:49 lfs sshd[31037]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:40:56 lfs sshd[31039]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:40:56 lfs sshd[31039]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:40:56 lfs sshd[31039]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:40:56 lfs sshd[31039]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:40:57 lfs sshd[31039]: Failed password for root from 118.192.2.50 port 37854 ssh2
Jan  9 13:40:58 lfs sshd[31039]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:04 lfs sshd[31041]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:04 lfs sshd[31041]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:04 lfs sshd[31041]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:04 lfs sshd[31041]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:06 lfs sshd[31041]: Failed password for root from 118.192.2.50 port 40435 ssh2
Jan  9 13:41:06 lfs sshd[31041]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:13 lfs sshd[31043]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:13 lfs sshd[31043]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:13 lfs sshd[31043]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:13 lfs sshd[31043]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:15 lfs sshd[31043]: Failed password for root from 118.192.2.50 port 42825 ssh2
Jan  9 13:41:15 lfs sshd[31043]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:22 lfs sshd[31045]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:22 lfs sshd[31045]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:22 lfs sshd[31045]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:22 lfs sshd[31045]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:25 lfs sshd[31045]: Failed password for root from 118.192.2.50 port 45557 ssh2
Jan  9 13:41:25 lfs sshd[31045]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:32 lfs sshd[31047]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:32 lfs sshd[31047]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:32 lfs sshd[31047]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:32 lfs sshd[31047]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:33 lfs sshd[31047]: Failed password for root from 118.192.2.50 port 48267 ssh2
Jan  9 13:41:34 lfs sshd[31047]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:40 lfs sshd[31052]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:40 lfs sshd[31052]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:40 lfs sshd[31052]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:40 lfs sshd[31052]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:43 lfs sshd[31052]: Failed password for root from 118.192.2.50 port 50798 ssh2
Jan  9 13:41:43 lfs sshd[31052]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:50 lfs sshd[31054]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:50 lfs sshd[31054]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:50 lfs sshd[31054]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:50 lfs sshd[31054]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:41:51 lfs sshd[31054]: Failed password for root from 118.192.2.50 port 53450 ssh2
Jan  9 13:41:51 lfs sshd[31054]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:41:58 lfs sshd[31057]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:41:58 lfs sshd[31057]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:41:58 lfs sshd[31057]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:41:58 lfs sshd[31057]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:01 lfs sshd[31057]: Failed password for root from 118.192.2.50 port 55889 ssh2
Jan  9 13:42:01 lfs sshd[31057]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:08 lfs sshd[31059]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:08 lfs sshd[31059]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:08 lfs sshd[31059]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:08 lfs sshd[31059]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:10 lfs sshd[31059]: Failed password for root from 118.192.2.50 port 58672 ssh2
Jan  9 13:42:10 lfs sshd[31059]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:17 lfs sshd[31061]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:17 lfs sshd[31061]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:17 lfs sshd[31061]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:17 lfs sshd[31061]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:18 lfs sshd[31061]: Failed password for root from 118.192.2.50 port 33004 ssh2
Jan  9 13:42:19 lfs sshd[31061]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:26 lfs sshd[31063]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:26 lfs sshd[31063]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:26 lfs sshd[31063]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:26 lfs sshd[31063]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:27 lfs sshd[31063]: Failed password for root from 118.192.2.50 port 35456 ssh2
Jan  9 13:42:28 lfs sshd[31063]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:34 lfs sshd[31065]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:34 lfs sshd[31065]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:34 lfs sshd[31065]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:34 lfs sshd[31065]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:37 lfs sshd[31065]: Failed password for root from 118.192.2.50 port 37965 ssh2
Jan  9 13:42:37 lfs sshd[31065]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:44 lfs sshd[31067]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:44 lfs sshd[31067]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:44 lfs sshd[31067]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:44 lfs sshd[31067]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:45 lfs sshd[31067]: Failed password for root from 118.192.2.50 port 40618 ssh2
Jan  9 13:42:46 lfs sshd[31067]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:42:52 lfs sshd[31070]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:42:52 lfs sshd[31070]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:42:52 lfs sshd[31070]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:42:52 lfs sshd[31070]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:42:54 lfs sshd[31070]: Failed password for root from 118.192.2.50 port 43094 ssh2
Jan  9 13:42:55 lfs sshd[31070]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:01 lfs sshd[31072]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:01 lfs sshd[31072]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:01 lfs sshd[31072]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:01 lfs sshd[31072]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:03 lfs sshd[31072]: Failed password for root from 118.192.2.50 port 45649 ssh2
Jan  9 13:43:03 lfs sshd[31072]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:10 lfs sshd[31074]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:10 lfs sshd[31074]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:10 lfs sshd[31074]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:10 lfs sshd[31074]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:12 lfs sshd[31074]: Failed password for root from 118.192.2.50 port 48131 ssh2
Jan  9 13:43:12 lfs sshd[31074]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:19 lfs sshd[31110]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:19 lfs sshd[31110]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:19 lfs sshd[31110]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:19 lfs sshd[31110]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:21 lfs sshd[31110]: Failed password for root from 118.192.2.50 port 50606 ssh2
Jan  9 13:43:21 lfs sshd[31110]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:28 lfs sshd[31112]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:28 lfs sshd[31112]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:28 lfs sshd[31112]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:28 lfs sshd[31112]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:30 lfs sshd[31112]: Failed password for root from 118.192.2.50 port 53020 ssh2
Jan  9 13:43:30 lfs sshd[31112]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:37 lfs sshd[31114]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:37 lfs sshd[31114]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:38 lfs sshd[31114]: Failed password for root from 118.192.2.50 port 55649 ssh2
Jan  9 13:43:38 lfs sshd[31114]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:45 lfs sshd[31116]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:45 lfs sshd[31116]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:47 lfs sshd[31116]: Failed password for root from 118.192.2.50 port 58004 ssh2
Jan  9 13:43:47 lfs sshd[31116]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:43:54 lfs sshd[31118]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:43:54 lfs sshd[31118]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:43:56 lfs sshd[31118]: Failed password for root from 118.192.2.50 port 60447 ssh2
Jan  9 13:43:57 lfs sshd[31118]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:03 lfs sshd[31121]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:03 lfs sshd[31121]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:06 lfs sshd[31121]: Failed password for root from 118.192.2.50 port 34919 ssh2
Jan  9 13:44:06 lfs sshd[31121]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:13 lfs sshd[31123]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:13 lfs sshd[31123]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:14 lfs sshd[31123]: Failed password for root from 118.192.2.50 port 37515 ssh2
Jan  9 13:44:14 lfs sshd[31123]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:21 lfs sshd[31125]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:21 lfs sshd[31125]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:23 lfs sshd[31125]: Failed password for root from 118.192.2.50 port 39918 ssh2
Jan  9 13:44:23 lfs sshd[31125]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 13:44:30 lfs sshd[31127]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=118.192.2.50  user=root
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): getting password (0x00000388)
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): pam_get_item returned a password
Jan  9 13:44:30 lfs sshd[31127]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 13:44:32 lfs sshd[31127]: Failed password for root from 118.192.2.50 port 42414 ssh2
Jan  9 13:44:33 lfs sshd[31127]: Received disconnect from 118.192.2.50: 11: Bye Bye [preauth]
Jan  9 14:09:01 lfs CRON[31360]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:09:01 lfs CRON[31360]: pam_unix(cron:session): session closed for user root
Jan  9 14:17:01 lfs CRON[31416]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:17:01 lfs CRON[31416]: pam_unix(cron:session): session closed for user root
Jan  9 14:39:01 lfs CRON[31600]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 14:39:01 lfs CRON[31600]: pam_unix(cron:session): session closed for user root
Jan  9 15:09:02 lfs CRON[31879]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:09:02 lfs CRON[31879]: pam_unix(cron:session): session closed for user root
Jan  9 15:17:01 lfs CRON[31969]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:17:01 lfs CRON[31969]: pam_unix(cron:session): session closed for user root
Jan  9 15:39:01 lfs CRON[32155]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 15:39:01 lfs CRON[32155]: pam_unix(cron:session): session closed for user root
Jan  9 16:09:01 lfs CRON[32434]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:09:01 lfs CRON[32434]: pam_unix(cron:session): session closed for user root
Jan  9 16:17:01 lfs CRON[32525]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:17:01 lfs CRON[32525]: pam_unix(cron:session): session closed for user root
Jan  9 16:39:01 lfs CRON[32715]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 16:39:01 lfs CRON[32715]: pam_unix(cron:session): session closed for user root
Jan  9 16:50:49 lfs sshd[587]: Received signal 15; terminating.
Jan  9 16:50:49 lfs sshd[891]: Server listening on 0.0.0.0 port 22.
Jan  9 16:50:49 lfs sshd[891]: Server listening on :: port 22.
Jan  9 16:50:53 lfs sshd[926]: Accepted publickey for jason from 192.168.1.100 port 51132 ssh2
Jan  9 16:50:53 lfs sshd[926]: pam_unix(sshd:session): session opened for user jason by (uid=0)
Jan  9 16:50:54 lfs smbd[948]: pam_unix(samba:session): session opened for user jason by (uid=0)
Jan  9 16:51:12 lfs perl: pam_unix(webmin:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Jan  9 16:51:12 lfs perl: pam_winbind(webmin:auth): getting password (0x00000388)
Jan  9 16:51:12 lfs perl: pam_winbind(webmin:auth): pam_get_item returned a password
Jan  9 16:51:12 lfs perl: pam_winbind(webmin:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jan  9 16:51:14 lfs webmin[1868]: Webmin starting
Jan  9 17:09:01 lfs CRON[2385]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 17:09:01 lfs CRON[2385]: pam_unix(cron:session): session closed for user root
Jan  9 17:17:02 lfs CRON[2471]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  9 17:17:02 lfs CRON[2471]: pam_unix(cron:session): session closed for user root


```


Thanks

Jason

---

### Post by jerome1232 on 2013-01-09
I suppose you can scan it for any logins that were accepted like this

```
grep sshd /var/log/auth.log | grep Accepted
```

I doubt you were though, those messages about getting password are normal.

---

### Post by chadk5utc on 2013-01-09
China, Beijing, shantou city tianying information technology Co. (118.192.2.50) This is no surprise...
Just for your ref heres another thread same issue [http://ubuntuforums.org/showthread.php?t=1520313](http://ubuntuforums.org/showthread.php?t=1520313)
In a terminal type last, this will show the last successful connections 
also check
> cat /etc/passwd
This maybe redundant

---

### Post by chadk5utc on 2013-01-09
> **jerome1232 said:**
> I suppose you can scan it for any logins that were accepted like this

```
grep sshd /var/log/auth.log | grep Accepted
```

I doubt you were though, those messages about getting password are normal.

In addition to this you can output the results to a text file like so
> grep sshd /var/log/auth.log | grep Accepted > somefilename

---

### Post by iponeverything on 2013-01-09
From what you posted, there was not a remote login.

---

### Post by p2ranger on 2013-01-09
Wow, thank you everyone for putting me at ease. I obviously have a lot to learn. Sorry for the false alarm.

Thanks

Jason

---

### Post by chadk5utc on 2013-01-09
> **p2ranger said:**
> Wow, thank you everyone for putting me at ease. I obviously have a lot to learn. Sorry for the false alarm.

Thanks

Jason

No worries it happens to a lot of us I had a recent incident myself. I would suggest though changing that ssh port to a higher one you wont believe how quiet your auth log will get. Also look into ssh key based logins as this is also much more secure.
[https://help.ubuntu.com/8.04/serverguide/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/openssh-server.html)

---

### Post by CharlesA on 2013-01-09
> **chadk5utc said:**
> No worries it happens to a lot of us I had a recent incident myself. I would suggest though changing that ssh port to a higher one you wont believe how quiet your auth log will get. Also look into ssh key based logins as this is also much more secure.
[https://help.ubuntu.com/8.04/serverguide/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/openssh-server.html)

What they said ^.

I made the mistake of forgetting to reenable the firewall rules on my server after flushing them while troubleshooting and had a nasty mess in the auth.log - but no successful login due to using keys instead of passwords for external logins.

When I checked the logs, there were something like 3000 attempted logins by root (which all failed due to the use of AllowUser and a locked root account...).

---

