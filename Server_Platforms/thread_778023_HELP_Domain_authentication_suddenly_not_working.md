---
title: "HELP Domain authentication suddenly not working"
date: 2008-05-01
forum: Server Platforms
---

### Post by lokiset on 2008-05-01
I can't log on to my Ubuntu server with any domain accounts anymore, it was working perfectly for several weeks and now nothing.  I'm not sure where to start looking the error when I try to ssh in just say access denied.

can somebody point me in the right direction please?  what logs should I be looking in or other trouble shooting steps to take?

thanks

---

### Post by lokiset on 2008-05-02
any ideas?

---

### Post by lokiset on 2008-05-02
I seem to be getting ldap info, I get a responce from wbinfo -g and -u

here is some of my /var/log/auth.log file

```
May  2 12:05:06 XXXXX sshd[9117]: pam_winbind(ssh:auth): getting password (0x00000180)
May  2 12:05:06 XXXXX sshd[9117]: pam_unix(ssh:auth): check pass; user unknown
May  2 12:05:06 XXXXX sshd[9117]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=pcXXXXXXX-l.XXXX.XXXX.com
May  2 12:05:08 XXXXX sshd[9117]: Failed password for invalid user XXXXXX from XXX.XXX.X.XX port 4339 ssh2
May  2 12:05:14 XXXXX sshd[9117]: pam_winbind(ssh:auth): getting password (0x00000180)
May  2 12:05:14 XXXXX sshd[9117]: pam_unix(ssh:auth): check pass; user unknown
May  2 12:05:16 XXXXX sshd[9117]: Failed password for invalid user XXXXXXX from XXX.XXX.X.XX port 4339 ssh2
```

---

### Post by ghostknife on 2008-05-03
Please describe your setup and then paste the relevant configuration files like your /etc/ssh/sshd_config.

---

### Post by lokiset on 2008-05-14
my setup is taken from [ here](http://ubuntuforums.org/showthread.php?t=91510&highlight=domain+authentication) sshd config wouldn't that effect only ssh?  I can't log on locally with domain accounts anymore either, it was working just fine for about a month.

---

### Post by HermanAB on 2008-05-14
Mostly, the problem is that the clock is wrong.  The client and server need to be within 5 minutes of each other for Kerberos to work.

---

### Post by lokiset on 2008-05-14
> **HermanAB said:**
> Mostly, the problem is that the clock is wrong.  The client and server need to be within 5 minutes of each other for Kerberos to work.

thanks for your reply, I checked and the time was only off by about 1 minute, I synced it up with the server and still no go.  :(

---

