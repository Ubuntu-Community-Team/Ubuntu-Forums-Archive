---
title: "proftpd and AuthUserFile"
date: 2008-11-20
forum: Server Platforms
---

### Post by [pl]ice on 2008-11-20
Hi,
 somehow proftpd won't look into the user file. Its looking for user/passwd to /etc/passwd.My config:
Include /etc/proftpd/modules.conf
#UseIPv6                                on

ServerName                      "Monkey"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
ListOptions                     "-l"

DenyFilter                      \*.*/


 DefaultRoot                    /var/www/ftp/

 RequireValidShell              off

Port                            21

# PassivePorts                  49152 65534

MaxInstances                    30

User                            proftpd
Group                           nogroup
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on
AuthOrder                      *mod_auth_pam.c mod_auth_unix.c
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

AuthUserFile /etc/proftpd/ftpd.passwa
<Global>
RootLogin off
</Global>

<Limit LOGIN>
AllowUser test
AllowUser user2

DenyALL
</Limit>
i still get 530 error.

/etc/proftpd/ftpd.passwd:
test:$1$SzLe5zoK$dsj7Pxz/9oLyiTVZq29BV.:100:100::/var/www/ftp:/bin/false

logs:
Nov 21 00:42:39 test proftpd[7507] localhost.localdomain (localhost.locald                                   omain[::ffff:127.0.0.1]): USER misiek: no such user found from localhost.loc                                   aldomain [::ffff:127.0.0.1] to ::ffff:127.0.0.1:21
Nov 21 00:42:42 test proftpd[7507] localhost.localdomain (localhost.locald                                   omain[::ffff:127.0.0.1]): FTP session closed.

it will read/login easily if i add user to /etc/passwd

I don't get it, like the Auth doesn't work at all!

thanks :)

---

