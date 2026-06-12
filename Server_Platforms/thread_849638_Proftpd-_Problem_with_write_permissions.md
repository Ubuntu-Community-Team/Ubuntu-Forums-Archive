---
title: "Proftpd- Problem with write permissions"
date: 2008-07-04
forum: Server Platforms
---

### Post by bumstedmans on 2008-07-04
Hi,

I am currently setting up an FTP server and I'm having a bit of trouble getting the directory to be writeable. I've configured the /etc/proftpd/proftpd.conf file to direct my logon to my home folder, chmod 777'd the directory, and set the umask to '000', but I still cannot write to the directory upon logon. 

Why can't I write to my FTP directory???

The server is connected to a closed network, so, ideally, I'd like to have no security and completely open permissions.


Here is my proftpd.conf file without any comments:


```
Include /etc/proftpd/modules.conf
UseIPv6                         on

ServerName                      "BumstedFTP"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     10000

DisplayLogin                    welcome.msg
DisplayChdir                    .message true
ListOptions                     "-l"

DenyFilter                      \*.*/
Port                            21

User                            bumsted
Group                           nogroup

Umask                           000  000
AllowOverwrite                  on 

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>

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
```

Any help would be greatly appreciated!!

-Bumstedmans

---

### Post by nanog on 2008-07-04
proftp was hacked on one of my servers. i switched to vsftp...much more secure and easy to configure imo.

---

### Post by windependence on 2008-07-04
Check the OWNERSHIP of the files and directories. If they are owned by root they still might not be able to be accessed.

-Tim

---

### Post by bumstedmans on 2008-07-05
Thanks for your help guys, but

> Check the OWNERSHIP of the files and directories. If they are owned by root they still might not be able to be accessed.

It's not an ownership problem because I was able to confirm that the user that I'm using to log into FTP is the owner of the target folder.

any more suggestions?

EDIT:

> proftp was hacked on one of my servers. i switched to vsftp...much more secure and easy to configure imo.

I tried vsftpd and it seemed to set up alright- I edited the config file and started it up, but it doesn't want to work with my clent (Mac OS' Finder). Whatever.

It's almost 3.
I'm going to bed.

---

