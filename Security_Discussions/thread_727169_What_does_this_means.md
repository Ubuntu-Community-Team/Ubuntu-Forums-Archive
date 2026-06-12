---
title: "What does this means?"
date: 2008-03-17
forum: Security Discussions
---

### Post by rasco on 2008-03-17
Can someone tell me if this means , that someone conected to my ssh server... please advice.

how do i correct this from happening again.?

```
Mar 17 06:47:37 lewisky sshd[5217]: Server listening on :: port 22.
Mar 17 06:47:37 lewisky sshd[5217]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Mar 17 07:17:01 lewisky CRON[6482]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 07:17:01 lewisky CRON[6482]: pam_unix(cron:session): session closed for user root
Mar 17 07:30:01 lewisky CRON[6485]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 07:30:01 lewisky CRON[6485]: pam_unix(cron:session): session closed for user root
Mar 17 08:17:01 lewisky CRON[6513]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 08:17:01 lewisky CRON[6513]: pam_unix(cron:session): session closed for user root
Mar 17 09:17:01 lewisky CRON[6516]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 09:17:01 lewisky CRON[6516]: pam_unix(cron:session): session closed for user root
Mar 17 10:17:01 lewisky CRON[6519]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 10:17:01 lewisky CRON[6519]: pam_unix(cron:session): session closed for user root
Mar 17 11:17:01 lewisky CRON[6522]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 11:17:01 lewisky CRON[6522]: pam_unix(cron:session): session closed for user root
Mar 17 12:17:01 lewisky CRON[6525]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 12:17:01 lewisky CRON[6525]: pam_unix(cron:session): session closed for user root
Mar 17 13:01:10 lewisky sshd[6528]: Accepted password for rasco from <snip> port 55708 ssh2
Mar 17 13:01:10 lewisky sshd[6530]: pam_unix(ssh:session): session opened for user rasco by (uid=0)
Mar 17 13:02:46 lewisky sshd[6530]: pam_unix(ssh:session): session closed for user rasco
Mar 17 13:02:58 lewisky sshd[6548]: Accepted password for rasco **from <snip> port 3482 ssh2**
Mar 17 13:02:58 lewisky sshd[6550]: pam_unix(ssh:session): session opened for user rasco by (uid=0)
Mar 17 13:17:01 lewisky CRON[6599]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 13:17:01 lewisky CRON[6599]: pam_unix(cron:session): session closed for user root
Mar 17 13:44:09 lewisky sshd[6550]: pam_unix(ssh:session): session closed for user rasco
Mar 17 13:55:52 lewisky sshd[6602]: Accepted password for root from <snip> port 57375 ssh2
Mar 17 13:55:52 lewisky sshd[6604]: pam_unix(ssh:session): session opened for user root by root(uid=0)
Mar 17 14:17:01 lewisky CRON[6618]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 17 14:17:01 lewisky CRON[6618]: pam_unix(cron:session): session closed for user root
Mar 17 14:25:38 lewisky sshd[6621]: Accepted password for rasco from <snip> port 48298 ssh2
Mar 17 14:25:38 lewisky sshd[6623]: pam_unix(ssh:session): session opened for user rasco by (uid=0)
```

---

### Post by p_quarles on 2008-03-17
Yes, someone logged into your SSH server. I have reason to believe that it was you. 

If you browse to the following page, it will tell you your current public IP address:
[http://whatismyip.com/](http://whatismyip.com/)

EDIT: Since your log file exposed not only your IP address, but your username and the fact that you have an SSH server listening on the default port, I've removed the IP address itself. Please note that posting that log file in raw form gives potential crackers way too much information.

---

