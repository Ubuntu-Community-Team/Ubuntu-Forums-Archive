---
title: "where the login-log file is located?"
date: 2007-09-23
forum: Server Platforms
---

### Post by adhg on 2007-09-23
Hi there,

When I ssh my Linux machine I get this message:

.
.
Last login: Sat Sep 22 19:20:54 2007 from pool-70-39-25-361.ny138.east.verizon.net

this is great because it provides a log of all connections to my server. I wonder where this file is located, assuming I would like to see all connections to the server in the past month.

thanks
adhg

---

### Post by bodhi.zazen on 2007-09-23
You can look at /var/log/auth.log

And see if this helps : [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by adhg on 2007-09-23
got it thanks!

I get this message, do you think someone is trying to break in?
if so, what can I do to prevent this? 


Sep 21 12:46:18 localhost sshd[10012]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:19 localhost sshd[10012]: Failed password for invalid user ernie from 85.31.200.8 port 41423 ssh2
Sep 21 12:46:20 localhost sshd[10014]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:23 localhost sshd[10014]: Failed password for root from 85.31.200.8 port 41517 ssh2
Sep 21 12:46:24 localhost sshd[10016]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:26 localhost sshd[10016]: Failed password for root from 85.31.200.8 port 41628 ssh2
Sep 21 12:46:27 localhost sshd[10018]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:29 localhost sshd[10018]: Failed password for root from 85.31.200.8 port 41741 ssh2
Sep 21 12:46:30 localhost sshd[10020]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:32 localhost sshd[10020]: Failed password for root from 85.31.200.8 port 41845 ssh2
Sep 21 12:46:33 localhost sshd[10022]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:34 localhost sshd[10022]: Failed password for root from 85.31.200.8 port 41949 ssh2
Sep 21 12:46:35 localhost sshd[10024]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:37 localhost sshd[10024]: Failed password for root from 85.31.200.8 port 42029 ssh2
Sep 21 12:46:38 localhost sshd[10026]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:46:40 localhost sshd[10026]: Failed password for root from 85.31.200.8 port 42132 ssh2
Sep 21 12:46:42 localhost sshd[10028]: Invalid user nokia from 85.31.200.8
Sep 21 12:46:42 localhost sshd[10028]: (pam_unix) check pass; user unknown
Sep 21 12:46:42 localhost sshd[10028]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:43 localhost sshd[10028]: Failed password for invalid user nokia from 85.31.200.8 port 42239 ssh2
Sep 21 12:46:45 localhost sshd[10030]: Invalid user download from 85.31.200.8
Sep 21 12:46:45 localhost sshd[10030]: (pam_unix) check pass; user unknown
Sep 21 12:46:45 localhost sshd[10030]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:46 localhost sshd[10030]: Failed password for invalid user download from 85.31.200.8 port 42329 ssh2
Sep 21 12:46:47 localhost sshd[10032]: Invalid user transfer from 85.31.200.8
Sep 21 12:46:47 localhost sshd[10032]: (pam_unix) check pass; user unknown
Sep 21 12:46:47 localhost sshd[10032]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:49 localhost sshd[10032]: Failed password for invalid user transfer from 85.31.200.8 port 42413 ssh2
Sep 21 12:46:50 localhost sshd[10034]: Invalid user oracle from 85.31.200.8
Sep 21 12:46:50 localhost sshd[10034]: (pam_unix) check pass; user unknown
Sep 21 12:46:50 localhost sshd[10034]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:53 localhost sshd[10034]: Failed password for invalid user oracle from 85.31.200.8 port 42526 ssh2
Sep 21 12:46:54 localhost sshd[10036]: Invalid user admin from 85.31.200.8
Sep 21 12:46:54 localhost sshd[10036]: (pam_unix) check pass; user unknown
Sep 21 12:46:54 localhost sshd[10036]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:46:55 localhost sshd[10036]: Failed password for invalid user admin from 85.31.200.8 port 42637 ssh2
Sep 21 12:47:01 localhost sshd[10038]: Invalid user michal from 85.31.200.8
Sep 21 12:47:01 localhost sshd[10038]: (pam_unix) check pass; user unknown
Sep 21 12:47:01 localhost sshd[10038]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:03 localhost sshd[10038]: Failed password for invalid user michal from 85.31.200.8 port 42722 ssh2
Sep 21 12:47:04 localhost sshd[10040]: Invalid user informix from 85.31.200.8
Sep 21 12:47:04 localhost sshd[10040]: (pam_unix) check pass; user unknown
Sep 21 12:47:04 localhost sshd[10040]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:06 localhost sshd[10040]: Failed password for invalid user informix from 85.31.200.8 port 42973 ssh2
Sep 21 12:47:07 localhost sshd[10042]: Invalid user xbox from 85.31.200.8
Sep 21 12:47:07 localhost sshd[10042]: (pam_unix) check pass; user unknown
Sep 21 12:47:07 localhost sshd[10042]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:09 localhost sshd[10042]: Failed password for invalid user xbox from 85.31.200.8 port 43053 ssh2
Sep 21 12:47:10 localhost sshd[10044]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:47:12 localhost sshd[10044]: Failed password for root from 85.31.200.8 port 43150 ssh2
Sep 21 12:47:14 localhost sshd[10046]: Invalid user cindy from 85.31.200.8
Sep 21 12:47:14 localhost sshd[10046]: (pam_unix) check pass; user unknown
Sep 21 12:47:14 localhost sshd[10046]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:16 localhost sshd[10046]: Failed password for invalid user cindy from 85.31.200.8 port 43264 ssh2
Sep 21 12:47:18 localhost sshd[10048]: Invalid user reboot from 85.31.200.8
Sep 21 12:47:18 localhost sshd[10048]: (pam_unix) check pass; user unknown
Sep 21 12:47:18 localhost sshd[10048]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:19 localhost sshd[10048]: Failed password for invalid user reboot from 85.31.200.8 port 43366 ssh2
Sep 21 12:47:21 localhost sshd[10050]: Invalid user restart from 85.31.200.8
Sep 21 12:47:21 localhost sshd[10050]: (pam_unix) check pass; user unknown
Sep 21 12:47:21 localhost sshd[10050]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:23 localhost sshd[10050]: Failed password for invalid user restart from 85.31.200.8 port 43472 ssh2
Sep 21 12:47:24 localhost sshd[10052]: Invalid user anna from 85.31.200.8
Sep 21 12:47:24 localhost sshd[10052]: (pam_unix) check pass; user unknown
Sep 21 12:47:24 localhost sshd[10052]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:26 localhost sshd[10052]: Failed password for invalid user anna from 85.31.200.8 port 43581 ssh2
Sep 21 12:47:27 localhost sshd[10054]: Invalid user image from 85.31.200.8
Sep 21 12:47:27 localhost sshd[10054]: (pam_unix) check pass; user unknown
Sep 21 12:47:27 localhost sshd[10054]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:29 localhost sshd[10054]: Failed password for invalid user image from 85.31.200.8 port 43679 ssh2
Sep 21 12:47:30 localhost sshd[10056]: Invalid user linda from 85.31.200.8
Sep 21 12:47:30 localhost sshd[10056]: (pam_unix) check pass; user unknown
Sep 21 12:47:30 localhost sshd[10056]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:32 localhost sshd[10056]: Failed password for invalid user linda from 85.31.200.8 port 43753 ssh2
Sep 21 12:47:33 localhost sshd[10058]: Invalid user mia from 85.31.200.8
Sep 21 12:47:33 localhost sshd[10058]: (pam_unix) check pass; user unknown
Sep 21 12:47:33 localhost sshd[10058]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:35 localhost sshd[10058]: Failed password for invalid user mia from 85.31.200.8 port 43865 ssh2
Sep 21 12:47:36 localhost sshd[10060]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com  user=root
Sep 21 12:47:38 localhost sshd[10060]: Failed password for root from 85.31.200.8 port 43963 ssh2
Sep 21 12:47:39 localhost sshd[10062]: Invalid user tone from 85.31.200.8
Sep 21 12:47:39 localhost sshd[10062]: (pam_unix) check pass; user unknown
Sep 21 12:47:39 localhost sshd[10062]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:41 localhost sshd[10062]: Failed password for invalid user tone from 85.31.200.8 port 44057 ssh2
Sep 21 12:47:42 localhost sshd[10064]: Invalid user sponsor from 85.31.200.8
Sep 21 12:47:42 localhost sshd[10064]: (pam_unix) check pass; user unknown
Sep 21 12:47:42 localhost sshd[10064]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ns1.moodsystem.com 
Sep 21 12:47:44 localhost sshd[10064]: Failed password for invalid user sponsor from 85.31.200.8 port 44137 ssh2

---

### Post by JBAlaska on 2007-09-23
Contact abuse & see if you get a answer, also you might want to block that IP range in iptables.
whois 85.31.200.8
% This is the RIPE Whois query server #1.
% The objects are in RPSL format.
%
% Rights restricted by copyright.
% See [http://www.ripe.net/db/copyright.html](http://www.ripe.net/db/copyright.html)

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '85.31.200.0 - 85.31.200.255'

inetnum:        85.31.200.0 - 85.31.200.255
netname:        FR-JAGUAR-COLO-MAR-2
descr:          Jaguar Network
country:        FR
admin-c:        JAGN-RIPE
tech-c:         JAGN-RIPE
status:         ASSIGNED PA
mnt-by:         JAGUAR-MNT
source:         RIPE # Filtered

role:           Jaguar-Network Engineering
address:        7 Avenue Andre Roussin
address:        13016 Marseille
address:        France
phone:          +33 4 91 60 56 14
fax-no:         +33 4 42 56 54 90
remarks:        trouble:      [email]abuse@as30781.net[/email]
admin-c:        POLK-RIPE
admin-c:        NINI-RIPE
tech-c:         RMBO-RIPE
tech-c:         JEDE-RIPE
tech-c:         VAYU-RIPE
tech-c:         AMON-RIPE
nic-hdl:        JAGN-RIPE
mnt-by:         JAGUAR-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@as30781.net[/email]

% Information related to '85.31.192.0/19AS30781'

route:          85.31.192.0/19
descr:          FR.JAGUAR LIR Range
origin:         AS30781
mnt-by:         JAGUAR-MNT
source:         RIPE # Filtered

---

### Post by bodhi.zazen on 2007-09-23
> **adhg said:**
> got it thanks!

I get this message, do you think someone is trying to break in?
if so, what can I do to prevent this? 

<clip>



Yep. port 22 (ssh) gets hammered.

If you are NOT running a ssh server, you can ignore those attempts.

If you want to block them, add firestarter to configure your firewall (ip tables)

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

If you are running a ssh server you need to secure it. I

See this page [uwiki]AdvancedOpenSSH[/uwiki] and this [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

