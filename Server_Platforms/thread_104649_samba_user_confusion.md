---
title: "samba user confusion"
date: 2005-12-16
forum: Server Platforms
---

### Post by gaspedalo on 2005-12-16
Hi! I use a ubuntu machine as PDC and fileserver for a WinXP base SOHO network. Actually so far everything runs fine, share are there and accessable, workstation logins work like a charme. But when I installed the startup.bat in combination with "ifmember.exe" I experienced strange things. The groups that get listed by "ifmember /list" are never those I asigned within /etc/group. 
Maybe I am wrong in my workflow or my understanding, so please correct me. This is what I did, in that sequence: 
[LIST=1]
[*]I installed the unix-users
[*]I added users to smbpasswd
[*]I installed the unix-groups
[*]I groupmapped those to windows groups (three standard domain groups for workstation-login, 4 more for sharing rights)
[*]I added the users to the groups inside /etc/group
[/LIST]

Now if I look at "ifmember /l" on the client machine, the whole thing is mixed up, and that's why my startup.bat is not working. Am I confusing something or did I miss a step?

---

### Post by gaspedalo on 2005-12-16
```
[INDENT]Here's my groupmap list:

[FONT="Courier New"][SIZE="2"]System Operators (xxx) -> -1 
Domain Guests (xxx) -> b-guests 
Replicators (S-1-5-32-552) -> -1 
Guests (S-1-5-32-546) -> -1 
A-Work (S-1-5-21-3573664633-1311056012-1221547432-3007) -> a-work 
A-Maingroup (S-1-5-21-3573664633-1311056012-1221547432-2999) -> a-maingroup 
A-Machines (S-1-5-21-3573664633-1311056012-1221547432-3021) -> a-machines 
Domain Users (S-1-5-21-3573664633-1311056012-1221547432-513) -> b-users 
Power Users (S-1-5-32-547) -> -1 
Print Operators (S-1-5-32-550) -> -1 
Administrators (S-1-5-32-544) -> -1 
A-Office (S-1-5-21-3573664633-1311056012-1221547432-1000) -> a-office 
Account Operators (S-1-5-32-548) -> -1 
Remotedesktopbenutzer (S-1-5-21-3573664633-1311056012-1221547432-3023) -> b-remotes 
A-Guests (S-1-5-21-3573664633-1311056012-1221547432-3005) -> a-guests 
Backup Operators (S-1-5-32-551) -> -1 
Users (S-1-5-32-545) -> -1 
Domain Admins (S-1-5-21-3573664633-1311056012-1221547432-512) -> b-admins[/SIZE][/FONT]



An here's my /etc/group:

[FONT="Courier New"][SIZE="2"]root:x:0: 
daemon:x:1: 
bin:x:2: 
sys:x:3: 
adm:x:4: 
tty:x:5: 
disk:x:6: 
lp:x:7:cupsys 
mail:x:8: 
news:x:9: 
uucp:x:10: 
man:x:12: 
proxy:x:13: 
kmem:x:15: 
dialout:x:20:xing,richardtecht,danielbauer 
fax:x:21:xing,richardtecht,danielbauer 
voice:x:22: 
cdrom:x:24:hal,xing,richardtecht,danielbauer 
floppy:x:25:hal,xing,richardtecht,danielbauer 
tape:x:26:xing,richardtecht,danielbauer 
sudo:x:27: 
audio:x:29:xing,richardtecht,danielbauer 
dip:x:30:xing,richardtecht,danielbauer 
www-data:x:33: 
backup:x:34: 
operator:x:37: 
list:x:38: 
irc:x:39: 
src:x:40: 
gnats:x:41: 
shadow:x:42: 
utmp:x:43: 
video:x:44:xing,richardtecht,danielbauer 
sasl:x:45: 
plugdev:x:46:hal,xing,richardtecht,danielbauer 
staff:x:50: 
games:x:60: 
users:x:100: 
nogroup:x:65534: 
dhcp:x:101: 
syslog:x:102: 
klog:x:103: 
lpadmin:x:104:xing,richardtecht,danielbauer 
scanner:x:105:xing,richardtecht,danielbauer 
admin:x:106: 
crontab:x:107: 
ssh:x:108: 
slocate:x:109: 
messagebus:x:110: 
hal:x:111: 
saned:x:112: 
gdm:x:113: 
ntp:x:114: 
a-maingroup:x:1100: 
a-work:x:1101:richardtecht,renderman,danielbauer 
a-office:x:1102:richardtecht,danielbauer 
a-guests:x:1103:xing 
a-machines:x:1110: 
b-admins:x:1121:root,danielbauer 
b-users:x:1122:richardtecht,renderman,danielbauer 
b-guests:x:1123: 
b-remotes:x:1124:root,renderman,danielbauer 
danielbauer:x:1012: 
dhcpd:x:115:
[/SIZE][/FONT][/INDENT]
```

---

