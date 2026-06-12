---
title: "log full of &quot;POSSIBLE BREAK-IN ATTEMPT!&quot;"
date: 2011-06-01
forum: Security
---

### Post by m-momr on 2011-06-01
Is this normal when you run a ssh server on port 22?


```
May 29 13:05:53 tux sshd[15365]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:05:56 tux sshd[15365]: Failed password for invalid user matt from 79.113.0.243 port 38155 ssh2
May 29 13:05:57 tux sshd[15367]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
May 29 13:05:57 tux sshd[15367]: Invalid user matt from 79.113.0.243
May 29 13:05:57 tux sshd[15367]: pam_unix(sshd:auth): check pass; user unknown
May 29 13:05:57 tux sshd[15367]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:05:58 tux sshd[15367]: Failed password for invalid user matt from 79.113.0.243 port 38522 ssh2
May 29 13:05:59 tux sshd[15369]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
May 29 13:05:59 tux sshd[15369]: Invalid user monica from 79.113.0.243
May 29 13:05:59 tux sshd[15369]: pam_unix(sshd:auth): check pass; user unknown
May 29 13:05:59 tux sshd[15369]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:06:01 tux sshd[15369]: Failed password for invalid user monica from 79.113.0.243 port 38830 ssh2
May 29 13:06:02 tux sshd[15371]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
May 29 13:06:02 tux sshd[15371]: Invalid user monica from 79.113.0.243
May 29 13:06:02 tux sshd[15371]: pam_unix(sshd:auth): check pass; user unknown
May 29 13:06:02 tux sshd[15371]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:06:04 tux sshd[15371]: Failed password for invalid user monica from 79.113.0.243 port 39226 ssh2
May 29 13:06:04 tux sshd[15373]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
May 29 13:06:04 tux sshd[15373]: Invalid user monica from 79.113.0.243
May 29 13:06:04 tux sshd[15373]: pam_unix(sshd:auth): check pass; user unknown
May 29 13:06:04 tux sshd[15373]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:06:06 tux sshd[15373]: Failed password for invalid user monica from 79.113.0.243 port 39625 ssh2
May 29 13:06:07 tux sshd[15375]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
May 29 13:06:07 tux sshd[15375]: Invalid user nicole from 79.113.0.243
May 29 13:06:07 tux sshd[15375]: pam_unix(sshd:auth): check pass; user unknown
May 29 13:06:07 tux sshd[15375]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=79.113.0.243 
May 29 13:06:08 tux sshd[15375]: Failed password for invalid user nicole from 79.113.0.243 port 39962 ssh2
May 29 13:06:09 tux sshd[15377]: reverse mapping checking getaddrinfo for 79-113-0-243.rdsnet.ro [79.113.0.243] failed - POSSIBLE BREAK-IN ATTEMPT!
```

---

### Post by CharlesA on 2011-06-01
The invalid logins are normal, since there are bots that try to bruteforce servers.

As for the "possible break-in attempt" message, The system is trying to do a reverse DNS lookup to match the connecting IP with the hostname that is trying to connect and fails to do so.

The setting that controls that is "UseDNS" in /etc/ssh/sshd_config

I checked on my install of 10.04, and that setting wasn't listed in sshd_config. Check yours to see what it says.

See [here]("http://www.yaleman.org/2007/12/09/ssh-reverse-dns-lookup-disable/").

---

### Post by jramshu on 2011-06-02
I get that too, then DenyHosts blacklists the ip.

Looks like you have passwordauthentication set to yes.
You may want to generate a key and disable password auth.

---

### Post by m-momr on 2011-06-02
I use rsa cert. for logon from my laptop, its nice to be able to log on with passwd from my windows desktop that does not have a encrypted directory for keys :P


can i block 10 invalid password attempts for lets say 2 hours?

---

### Post by CharlesA on 2011-06-02
> **m-momr said:**
> I use rsa cert. for logon from my laptop, its nice to be able to log on with passwd from my windows desktop that does not have a encrypted directory for keys :P

You can use keys with Putty.


> can i block 10 invalid password attempts for lets say 2 hours?

Look into iptables. [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by bodhi.zazen on 2011-06-02
Covered on this page as well:

[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

---

### Post by jramshu on 2011-06-03
Used these tutorials to set mine up. They are easy to understand.

Still learning iptables, when I have time. Seems like a better way to go than using DenyHosts.

---

### Post by m-momr on 2011-06-03
Thanks everyone :)

---

