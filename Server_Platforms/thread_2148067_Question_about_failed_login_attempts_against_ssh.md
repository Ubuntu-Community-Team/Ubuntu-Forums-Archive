---
title: "Question about failed login attempts against ssh"
date: 2013-05-23
forum: Server Platforms
---

### Post by andrewhamming on 2013-05-23
I have disabled root login through ssh.

Here is a message I got from fail2ban. It looks as though it is letting them try to login as root or am I missreading?


"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Hi,

The IP 114.112.171.67 has just been banned by Fail2Ban after
5 attempts against ssh.


Here are more information about 114.112.171.67:

% [whois.apnic.net node-3]
% Whois data copyright terms    [http://www.apnic.net/db/dbcopyright.html](http://www.apnic.net/db/dbcopyright.html)

inetnum:        114.112.160.0 - 114.112.191.255
netname:        WORLDCOM
descr:          WORLDCOM TEDA NETWORKS TECHNOLOGY CO.,LTD
descr:          BeiJing Haidian District Garden East B9 316 room
country:        CN
admin-c:        DS885-AP
tech-c:         DS885-AP
status:         allocated non-portable
mnt-by:         MAINT-NET-AP
mnt-irt:        IRT-NET-AP
changed:        [email]ip@cnisp.org.cn[/email] 20120920
source:         APNIC

person:         Di Song
nic-hdl:        DS885-AP
e-mail:         [email]disong@126.com[/email]
address:        BeiJing Haidian District Garden East B9 316 room
phone:          +86-10-62372840
fax-no:         +86-10-62372840
country:        CN
changed:        [email]ip@cnisp.org.cn[/email] 20120401
mnt-by:         MAINT-NEW
source:         APNIC


Lines containing IP:114.112.171.67 in /var/log/auth.log

May 24 01:30:23 home sshd[23900]: Did not receive identification string from 114.112.171.67
May 24 01:30:27 home sshd[23901]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:28 home sshd[23901]: Failed password for root from 114.112.171.67 port 1788 ssh2
May 24 01:30:28 home sshd[23902]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:28 home sshd[23903]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:28 home sshd[23904]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:29 home sshd[23901]: Connection closed by 114.112.171.67 [preauth]
May 24 01:30:29 home sshd[23905]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:30 home sshd[23902]: Failed password for root from 114.112.171.67 port 1789 ssh2
May 24 01:30:30 home sshd[23903]: Failed password for root from 114.112.171.67 port 1790 ssh2
May 24 01:30:30 home sshd[23904]: Failed password for root from 114.112.171.67 port 1791 ssh2
May 24 01:30:30 home sshd[23902]: Connection closed by 114.112.171.67 [preauth]
May 24 01:30:30 home sshd[23903]: Connection closed by 114.112.171.67 [preauth]
May 24 01:30:30 home sshd[23904]: Connection closed by 114.112.171.67 [preauth]
May 24 01:30:30 home sshd[23905]: Failed password for root from 114.112.171.67 port 1792 ssh2
May 24 01:30:31 home sshd[23905]: Connection closed by 114.112.171.67 [preauth]
May 24 01:30:32 home sshd[23912]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:33 home sshd[23914]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:33 home sshd[23915]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root
May 24 01:30:33 home sshd[23916]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=114.112.171.67  user=root


Regards,

Fail2Ban

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

---

### Post by CharlesA on 2013-05-24
That is fine. Bots will still try to login via root even if you have it disabled or not allowed via sshd_config.

---

### Post by andrewhamming on 2013-06-05
Lovely.... :) ty for reply

---

### Post by d4rk0wl on 2013-06-05
Yeah those bots can get very annoying, I ended up changing my default SSH port to some random port (out of typical scan range) and I have not had an attempt since. Also, if you are not already, I would recommend disabling passwd auth and move toward RSA keys to further stop the bots.

Regards,
d4rk0wl

---

