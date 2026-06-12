---
title: "wbinfo -r ad-user ==&gt; group missing &amp; duplicates"
date: 2020-01-03
forum: Server Platforms
---

### Post by gregor8 on 2020-01-03
[COLOR=#000000][FONT=Verdana]I installed samba and winbind on ubuntu 18 and the os is joined to the domain.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]when I do a wbinfo -r ad-user I see there is a group missing. Very persistently.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I tried:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]net flush[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]deleted the tdb files[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]restarted winbind & smb[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rebooted[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]with a centos 7 machine I see the group.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]when I do a "wbinfo -r ad-user |wc -l" I get 70 lines on both OS![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]only the two last group is's differ:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ubuntu (wrong):[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]121361[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]232554[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]232494[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]3004[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]3001[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]centos (correct):[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]121361[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]232554[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]232494[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]236337[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]16777217[/FONT][/COLOR]



[FONT=fixedsys]UBUNTU --------------------------------------------------------------- CENTOS
[FONT=lucida console]g[SIZE=3]-srv-lsudo-srv00767:232494: - g-srv-lsudo-srv00767:232494:
gl-appl-beheerders:110191: --- gl-appl-beheerders:110191:
gl-appl-beheerders:3000:------ g-lnx-administrators:236337:
.............................. BUILTIN+users:16777217:


[/SIZE][/FONT][/FONT]Both machines have no sssd installed or running.


CENTOS & UBUNTU 

/etc/nsswitch.conf
shadow: files winbind
group: files winbind
passwd:     files winbind


[global]
interfaces = ens192
ldap suffix = dc=saszl,dc=local
load printers = No
log file = /var/log/samba/log.%m
max log size = 50
password server = SRV00214.saszl.local
realm = saszl.LOCAL
security = ADS
server string = Samba Server Version %v
template homedir = /net/lfs.saszl.local/home/%U
template shell = /bin/bash
winbind offline logon = Yes
winbind separator = +
winbind use default domain = Yes
workgroup = saszl
idmap config saszl:base_rid = 0
idmap config saszl: range = 100000-89999999
idmap config saszl: backend = rid
idmap config * : range = 3000-9999
idmap config * : backend = tdb
username map = /etc/samba/usermap
username map script = /etc/samba/usermap.sh
log level = 0

UBUNTU:
wbinfo -r user1 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|sort -u|wc -l
69
wbinfo -r user1 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|wc -l
70
One duplicate

wbinfo -r user2 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|sort -u|wc -l
94
wbinfo -r user2 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|wc -l
139
45 duplicates


CENTOS:
wbinfo -r user1 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|sort -u|wc -l
70
wbinfo -r user1 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|wc -l
70
No duplicates

wbinfo -r user2 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|sort -u|wc -l
92
wbinfo -r user2 |while read xx; do getent group $xx; done|awk -F: '{print $1}'|wc -l
92
No duplicates


is this a bug?



gl-appl-beheerders is twice in Ubuntu
g-lnx-administrators and BUILTIN+users are not in Ubuntu.

---

### Post by gregor8 on 2020-01-07
When I do a "wbinfo -a user%passwd" then I get the missing group.
Still duplicates however.

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454670](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454670)

---

