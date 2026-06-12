---
title: "ntlm_auth helper for squid3 - problems with ntlm authentication"
date: 2012-08-06
forum: Server Platforms
---

### Post by puszamba on 2012-08-06
Dear All,
At first I would like to say hello as this is my first post here.
Thank you in advance for any thoughts, tips and solutions.

**Problem descritpion:**
I have installed squid3 and would like to set it as proxy with 'require-member-of' ntlm_auth helper for squid. It should authenticate against Active Directory (2003 schema).
Problem is that basic authentication works but ntlm does not.
I have run winbindd in debug mode and this is what I got when username/password prompts from IE:

```
process_request: unknown request fn number 14
winbind_client_response_written[13395:unknown request]: delivered response to client
```

When squid.conf is set to use just basic authentication it works fine (from FireFox).
Server was successfully joined to the AD and
```
wbinfo -a
wbinfo -t
wbinfo -g
```
and so on... all succeed or just work fine. 

EDIT:
Strange thing I have noticed is that example:
```
# /usr/local/bin/ntlm_auth --helper-protocol=squid-2.5-basic
mydomain+myuser mypasswd
OK
``` from [http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm](http://wiki.squid-cache.org/ConfigExamples/Authenticate/Ntlm)
Does not work in my case. It just freezes the cli and winbindd debug says:
```
accepted socket 24
process_request: request fn INTERFACE_VERSION
[14665]: request interface version
winbind_client_response_written[14665:INTERFACE_VERSION]: delivered response to client
process_request: request fn WINBINDD_PRIV_PIPE_DIR
[14665]: request location of privileged pipe
winbind_client_response_written[14665:WINBINDD_PRIV_PIPE_DIR]: delivered response to client
process_request: request fn DOMAIN_NAME
[14665]: request domain name
winbind_client_response_written[14665:DOMAIN_NAME]: delivered response to client 
```
It does nothing until ctrl+c is hit.
/EDIT

**System:**
Ubuntu 12.04 x64 running as guest on MS Hyper-V, installed latest updates, samba, winbind and squid3 installed with apt.
Package versions:
Samba and winbid: 2:3.6.3-2ubuntu2.3
Squid3 version: 3.1.19-1ubuntu3.12.0.4.1

**Configuration files:**
_squid.conf_ - it is based on default one, cut to minimal as I intended to test ntlm helper; also fields such as MYDOMAIN are set correctly and were changed for puprose of this post...
```
auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp --require-membership-of="MYDOMAIN+mygroup"
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
acl mygroupusers proxy_auth REQUIRED
http_access allow mygroupusers
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_port 3128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320
```

_smb.conf_
```
[global]
local master = no
security = ADS
workgroup = MYDOMAIN
realm = MYDOMAIN.REALM
netbios name = mynetbiosname
winbind uid = 10000-20000
winbind gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind separator = +
client use spnego = yes
ntlm auth = yes
client ntlmv2 auth = yes
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
```

Thank you!

---

### Post by jaimerosario on 2012-08-07
Did you run the following command in the cli?

```
sudo chown -R root:proxy /var/run/samba/winbindd_privileged
```

---

### Post by puszamba on 2012-08-07
Jaimerosario, you are the MAN. And you have nailed the problem.
I have to admit that I have tried that before but after that I have restarted winbind service and... It did not work.
Now I was debugging interactively and the winbind initial script was omitted. And it worked that way.

I have added the line to /etc/init.d/winbind so it looks like this:
```
...
mkdir -p /var/run/samba/winbindd_privileged || return 1
                chgrp winbindd_priv $PIDDIR/winbindd_privileged/ || return 1
                chmod 0750 $PIDDIR/winbindd_privileged/ || return 1
                chown -R root:proxy /var/run/samba/winbindd_privileged
                start-stop-daemon --start --quiet --oknodo --exec $DAEMON -- $WINBINDD_OPTS
...
```

And it seems to work fine after restarting winbind service.

If you could explain me one more thing: for what stands 'proxy' for in the line of code you have posted?
My username is other than 'proxy' and I am unable to connect this phrase with anything...

Once again - thank you and best regards!

---

### Post by horace26 on 2013-03-29
Thank you! This post lights me.

When i update my ubuntu 12.04.2 LTS Precise 3.2.0-39-generic, i lost the Apache NTLM authentification. 
in my Apache site config:
NTLMAuthHelper "/usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp"

if the group winbindd_priv   exists, then check:
ls -l /var/run/samba/winbindd_privileged 
8157    0 drwxr-x---   2 root     winbindd_priv       60 Mar 29 15:50 /var/run/samba/winbindd_privileged
Add the user 'apache' to the group "winbindd_priv"
useradd -G winbindd_priv www-data

---

