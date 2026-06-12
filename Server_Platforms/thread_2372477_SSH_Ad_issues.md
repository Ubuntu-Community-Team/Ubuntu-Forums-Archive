---
title: "SSH/ Ad issues"
date: 2017-09-25
forum: Server Platforms
---

### Post by customcables067 on 2017-09-25
[COLOR=#333333][FONT=&quot]when I SSH into an Ubuntu 16.04 LTS box, it authenticates me using AD and then immediately closes the session upon successful login (if I use a bad password, it will fail me and continue to run the session).[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]After successful local login via SSH, I AM able to su - [usernamehidden] and log in using AD credentials. What is going on here?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Finally, it is my understanding I was using SSSD to connect, but this would indicate WINBIND? Which service is in use? Is anyone able to help walk me through what I'm using? When I initially set this up, I tried multiple tutorials which I realize now in hindsight was using different protocols I assume. [/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Here are the auth logs:
[/FONT][/COLOR]
Sep 25 10:30:55 SVRNAMEHR sshd[2707]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=1.2.3.4  user=[usernamehidden]
Sep 25 10:30:55 SVRNAMEHR sshd[2707]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 10:30:55 SVRNAMEHR sshd[2707]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 10:30:55 SVRNAMEHR sshd[2707]: pam_winbind(sshd:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = '[usernamehidden]')
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_sss(sshd:auth): authentication success; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.4.156 user=[usernamehidden]
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: Accepted password for [usernamehidden] from 192.168.4.156 port 53200 ssh2
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_unix(sshd:session): session opened for user [usernamehidden] by (uid=0)
Sep 25 10:31:01 SVRNAMEHR systemd-logind[1363]: New session 14 of user [usernamehidden].
Sep 25 10:31:01 SVRNAMEHR systemd: pam_unix(systemd-user:session): session opened for user [usernamehidden] by (uid=0)
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_unix(sshd:session): session closed for user [usernamehidden]
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_winbind(sshd:setcred): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = '[usernamehidden]')
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_winbind(sshd:setcred): failed to logoff user [usernamehidden]: WBC_ERR_WINBIND_NOT_AVAILABLE
Sep 25 10:31:01 SVRNAMEHR sshd[2707]: pam_winbind(sshd:setcred): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = '[usernamehidden]')
Sep 25 10:31:01 SVRNAMEHR systemd-logind[1363]: Removed session 14.
Sep 25 10:31:01 SVRNAMEHR systemd: pam_unix(systemd-user:session): session closed for user [usernamehidden]

---

### Post by wonkite on 2018-05-15
Got exactly the same issue, this is either broken or all the blogs I've read are not the best! I think this just plain broken in ubuntu 16.04!!!

---

### Post by customcables067 on 2018-05-15
I eventually got this fixed, but I can't remember specifically what the problem was. I ended up re-doing the whole thing, though (without re-formatting..). Try uninstalling all the services it's trying to use, deleting the config files, and starting over. If it's a critical operation, or you aren't willing to "Start over" if that you break something entirely, I'll try to check what services I ended up killing with success and post back here in a few days.

---

### Post by wonkite on 2018-05-16
That  makes no sense, so you got it working but you don't know how?

---

### Post by customcables067 on 2018-05-16
It's been months since I looked into it, and I don't do this for a living. So no, I don't remember what I did to fix that specific issue 6 months ago. shame on me!

---

