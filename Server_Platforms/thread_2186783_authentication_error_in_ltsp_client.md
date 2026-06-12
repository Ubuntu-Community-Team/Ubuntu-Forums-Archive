---
title: "authentication error in ltsp client"
date: 2013-11-09
forum: Server Platforms
---

### Post by bksyssathish on 2013-11-09
I am building a LTSP server with LDAP authentication for LTSP  Clients. I have configured LDAP server. When I try to login from  LTSP client in GUI, I am getting **No response from server, restarting**.  Then, It's restarting the GUI and comes to the login screen again. I  thought that there could be a problem with LDAP authentication. But,  When I try to login from **Alt+Ctrl+F1** terminal in LTSP client, it is logged in successfully with LDAP user. LDAP Server and authentication is working fine.

  Even, after executing the below commands, still I am getting the same error.
  ```
ltsp-update-sshkeys

ltsp-update-kernels

ltsp-update-image --arch i386

``` 
 Whether I need to configure anything for GUI login from LTSP Client?
  How to fix this issue?

Help to get rid of this problem..

---

### Post by hanwurst123 on 2014-02-26
When you log in from the LTSP client using the GUI, authentication is done via ssh, i.e. the password is checked as if you log into server using ssh. That means the LTSP-server checks the password.
If you log in after pressing **Alt+Ctrl+F1** terminal at the client, the client tries to check the password (and connects to the ldap server).

Hence, to make it work, you have to make sure that you can log in to your SERVER with an ldap user.

What ubuntu distribution are you using? Since I have some problems using ubuntu 13.10 as an ldap-client ;-)

---

### Post by bksyssathish on 2014-04-15
Thanks for your reply. You are right.

Here is a log, When I log in from LTSP Client ( /var/log/ldm.log ):

```

Apr 15 18:15:53: [ldm] INFO: started on client with IP address: 192.168.12.34
Apr 15 18:15:53: [ldm] INFO: calling rc.d init scripts
Apr 15 18:15:55: [ldm] INFO: authenticating with backend: ssh
Apr 15 18:16:09: [ssh] INFO: calling rc.d pressh scripts
Apr 15 18:16:32: [ssh] CRITICAL: no response, restarting
Apr 15 18:16:34: [ldm] INFO: started on client with IP address: 192.168.12.34
Apr 15 18:16:34: [ldm] INFO: calling rc.d init scripts
Apr 15 18:16:35: [ldm] INFO: authenticating with backend: ssh
Apr 15 18:30:55: [ssh] INFO: calling rc.d pressh scripts
Apr 15 18:31:18: [ssh] CRITICAL: no response, restarting
```

Here is a log, When I log in from **Atl+Ctrl+F1** in LTSP Client ( /var/log/auth.log )

```
Apr 15 18:16:49 client2 login[1036]: pam_unix(login:session): session opened for user myusername by LOGIN(uid=0)
Apr 15 18:17:01 client2 CRON[1812]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 15 18:17:01 client2 CRON[1812]: pam_unix(cron:session): session closed for user root
Apr 15 18:17:35 client2 su[1815]: Successful su for root by myusername
```

As you suggested, When I try to log in to SERVER as a LDAP user, I am getting the error.

```
Apr 15 18:52:45 dennis sshd[3385]: Invalid user myusername from 192.168.12.175
Apr 15 18:52:45 dennis sshd[3385]: input_userauth_request: invalid user myusername [preauth]
Apr 15 18:53:05 dennis sshd[3385]: pam_unix(sshd:auth): check pass; user unknown
Apr 15 18:53:05 dennis sshd[3385]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=debian.local 
Apr 15 18:53:08 dennis sshd[3385]: Failed password for invalid user myusername from 192.168.12.175 port 40986 ssh2
Apr 15 18:53:11 dennis sshd[3385]: pam_unix(sshd:auth): check pass; user unknown
Apr 15 18:53:14 dennis sshd[3385]: Failed password for invalid user myusername from 192.168.12.175 port 40986 ssh2
Apr 15 18:53:17 dennis sshd[3385]: pam_unix(sshd:auth): check pass; user unknown
Apr 15 18:53:19 dennis sshd[3385]: Failed password for invalid user myusername from 192.168.12.175 port 40986 ssh2
Apr 15 18:53:19 dennis sshd[3385]: Connection closed by 192.168.12.175 [preauth]
Apr 15 18:53:19 dennis sshd[3385]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=debian
```

Please suggest a way to solve this problem.

I have another doubt.
Whether GUI is using ssh for doing authentication **(OR)** the whole LTSP client will work like login into SERVER via ssh (with -X option).

I am using Ubuntu 12.04 LTS.

---

