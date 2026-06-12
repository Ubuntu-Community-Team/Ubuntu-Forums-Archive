---
title: "UsePAM Yes Problem in sshd_config"
date: 2017-03-27
forum: Security
---

### Post by MeharGags on 2017-03-27
what do you find wrong it this [B]sshd_config 
[/B]

```
PermitRootLogin no
PasswordAuthentication no
UsePAM no
PermitRootLogin without-password
ChallengeResponseAuthentication no

```

Order of the config parameters ?
or
conflicting arguments ?


I just did the above on a dedicated server, after reboot I got : ***no supported authentication methods available when trying to connect***  when trying to login using my SSH key


If I leave **UsePAM Yes** then it all works fine

I think disabling **ChallengeResponseAuthentication** , the server doesn't send key challenge at all for authentication.
[https://mail-index.netbsd.org/tech-security/2009/01/04/msg000153.html](https://mail-index.netbsd.org/tech-security/2009/01/04/msg000153.html)

Please suggest best secure config that should work for SSH key only logins

---

### Post by bonestabone on 2017-04-03
I have the same setup on my Ubuntu server except one difference with [B]PermitRootLogin

[/B]```
PermitRootLogin no
```

For me UsePAM is set to no, and it works fine.

---

### Post by Habitual on 2017-04-04
UsePAM yes here on 
```
ssh -V
OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.8, OpenSSL 1.0.1f 6 Jan 2014
```

The shown directives except for "UsePAM no" are fine.

Kind of fond of [https://help.ubuntu.com/community/StricterDefaults#SSH_Settings](https://help.ubuntu.com/community/StricterDefaults#SSH_Settings) myself for reference and a  good iptables rule.
And maybe a tcpwrapper/denyhosts/other layer up in front of that.

---

