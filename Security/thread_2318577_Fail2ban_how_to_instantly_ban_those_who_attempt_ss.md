---
title: "Fail2ban: how to instantly ban those who attempt ssh password logins"
date: 2016-03-27
forum: Security
---

### Post by wbmilleriii on 2016-03-27
My OpenSSH server is set up to only allow key based logins.  I get many attacks each day by bots trying to login using a userid and password.  I have fail2ban configured and running already.  How can I add a jail to immediately ban any IP address which attempts to login using a userid?  No retrys, no timeouts, just instantly ban them, because by definition I know it's an attack.

---

### Post by CharlesA on 2016-03-27
Read this:
[https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-12-04)

As far as my set up goes... I only allow certain IPs to connect via SSH. When I had SSH open to the Internet with keys only, I used a iptables one liner to block attacks. Read this:
[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

---

### Post by Habitual on 2016-03-28
for openssh:
edit and verify these 2 options in /etc/ssh/sshd_config
```
PermitRootLogin no
...
PasswordAuthentication no
```

for **fail2ban**:
```
[ssh]
enabled  = true
port     = ssh
filter   = sshd
action   = iptables-allports[name=ssh, port="ssh"]
logpath  = /var/log/auth.log
findtime = 86400   ; 1 day
bantime  = 31556926 ; 1 year in seconds
maxretry = 1
```

I just wrote a short how-to on tcwrappers. See [http://ubuntuforums.org/showthread.php?t=2318000&p=13459876#post13459876](http://ubuntuforums.org/showthread.php?t=2318000&p=13459876#post13459876)

---

### Post by wbmilleriii on 2016-04-04
Thanks.  The fail2ban code looks interesting.

---

### Post by Habitual on 2016-04-04
> **wbmilleriii said:**
> Thanks.  The fail2ban code looks interesting.

You're welcome.
You could also use
```
bantime  = -1
maxretry = 1
```

---

