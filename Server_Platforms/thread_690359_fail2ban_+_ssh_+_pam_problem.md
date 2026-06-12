---
title: "fail2ban + ssh + pam problem"
date: 2008-02-07
forum: Server Platforms
---

### Post by PiGal on 2008-02-07
I wish to use fail2ban to secure my u7.10 server (64bit). It works with vsftpd but it won't with ssd. Probably reason: auth.log contain empty rhost so fail2ban don't knew which ip shoul be block. In fact I have no idea why there is no ip in auth.log. I'll be thankful for any idea. Line from auth.log:

pam_unix(su:auth): authentication failure; logname=jedi uid=1000 euid=0 tty=tty1 ruser=jedi rhost=  user=root

---

