---
title: "Somebody us tryng to break into m PC, see the logs. PLS HELP!"
date: 2009-01-28
forum: Security
---

### Post by bmwman on 2009-01-28
I come home today and find my PC rebooted. I never shut it off myself. Then I looked at the logs and find this:
```

Jan 25 16:17:01 office-desktop CRON[16965]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 16:17:01 office-desktop CRON[16965]: pam_unix(cron:session): session closed for user root
Jan 25 17:17:01 office-desktop CRON[17362]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 17:17:01 office-desktop CRON[17362]: pam_unix(cron:session): session closed for user root
Jan 25 18:17:01 office-desktop CRON[17943]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 18:17:01 office-desktop CRON[17943]: pam_unix(cron:session): session closed for user root
Jan 25 18:58:51 office-desktop gnome-keyring-daemon[6651]: adding removable location: volume_label_NO_NAME at /media/NO NAME
Jan 25 19:06:24 office-desktop gnome-keyring-daemon[6651]: removing removable location: volume_label_NO_NAME
Jan 25 19:07:27 office-desktop gnome-keyring-daemon[6651]: adding removable location: volume_uuid_0000_0C3C at /media/CASIO-DSC
Jan 25 19:17:01 office-desktop CRON[19041]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 19:17:01 office-desktop CRON[19041]: pam_unix(cron:session): session closed for user root
Jan 25 19:40:24 office-desktop gnome-keyring-daemon[6651]: removing removable location: volume_uuid_0000_0C3C
Jan 25 19:50:47 office-desktop gdm[6249]: pam_unix(gdm:session): session closed for user bmw-man
Jan 25 19:51:51 office-desktop sshd[5136]: Server listening on :: port 22.
Jan 25 19:51:51 office-desktop sshd[5136]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Jan 25 20:17:01 office-desktop CRON[6642]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 20:17:01 office-desktop CRON[6642]: pam_unix(cron:session): session closed for user root
Jan 25 21:17:01 office-desktop CRON[6648]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 21:17:01 office-desktop CRON[6648]: pam_unix(cron:session): session closed for user root
Jan 25 22:17:01 office-desktop CRON[6652]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 22:17:01 office-desktop CRON[6652]: pam_unix(cron:session): session closed for user root
Jan 25 23:09:28 office-desktop sshd[6655]: Did not receive identification string from 201.155.95.199
Jan 25 23:13:53 office-desktop sshd[6656]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:13:53 office-desktop sshd[6656]: Invalid user staff from 201.155.95.199
Jan 25 23:13:53 office-desktop sshd[6656]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:13:53 office-desktop sshd[6656]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:13:56 office-desktop sshd[6656]: Failed password for invalid user staff from 201.155.95.199 port 50721 ssh2
Jan 25 23:13:57 office-desktop sshd[6658]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:13:57 office-desktop sshd[6658]: Invalid user sales from 201.155.95.199
Jan 25 23:13:57 office-desktop sshd[6658]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:13:57 office-desktop sshd[6658]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:13:59 office-desktop sshd[6658]: Failed password for invalid user sales from 201.155.95.199 port 50871 ssh2
Jan 25 23:14:03 office-desktop sshd[6660]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:03 office-desktop sshd[6660]: Invalid user recruit from 201.155.95.199
Jan 25 23:14:03 office-desktop sshd[6660]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:03 office-desktop sshd[6660]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:05 office-desktop sshd[6660]: Failed password for invalid user recruit from 201.155.95.199 port 50984 ssh2
Jan 25 23:14:06 office-desktop sshd[6662]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:06 office-desktop sshd[6662]: Invalid user alias from 201.155.95.199
Jan 25 23:14:06 office-desktop sshd[6662]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:06 office-desktop sshd[6662]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:09 office-desktop sshd[6662]: Failed password for invalid user alias from 201.155.95.199 port 51173 ssh2
Jan 25 23:14:13 office-desktop sshd[6664]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:13 office-desktop sshd[6664]: Invalid user office from 201.155.95.199
Jan 25 23:14:13 office-desktop sshd[6664]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:13 office-desktop sshd[6664]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:15 office-desktop sshd[6664]: Failed password for invalid user office from 201.155.95.199 port 51284 ssh2
Jan 25 23:14:17 office-desktop sshd[6666]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:17 office-desktop sshd[6666]: Invalid user samba from 201.155.95.199
Jan 25 23:14:17 office-desktop sshd[6666]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:17 office-desktop sshd[6666]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:19 office-desktop sshd[6666]: Failed password for invalid user samba from 201.155.95.199 port 51505 ssh2
Jan 25 23:14:20 office-desktop sshd[6668]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:20 office-desktop sshd[6668]: Invalid user tomcat from 201.155.95.199
Jan 25 23:14:20 office-desktop sshd[6668]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:20 office-desktop sshd[6668]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:22 office-desktop sshd[6668]: Failed password for invalid user tomcat from 201.155.95.199 port 51610 ssh2
Jan 25 23:14:24 office-desktop sshd[6670]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:24 office-desktop sshd[6670]: Invalid user webadmin from 201.155.95.199
Jan 25 23:14:24 office-desktop sshd[6670]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:24 office-desktop sshd[6670]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:26 office-desktop sshd[6670]: Failed password for invalid user webadmin from 201.155.95.199 port 51733 ssh2
Jan 25 23:14:27 office-desktop sshd[6672]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:27 office-desktop sshd[6672]: Invalid user spam from 201.155.95.199
Jan 25 23:14:27 office-desktop sshd[6672]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:27 office-desktop sshd[6672]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:29 office-desktop sshd[6672]: Failed password for invalid user spam from 201.155.95.199 port 51838 ssh2
Jan 25 23:14:30 office-desktop sshd[6674]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:30 office-desktop sshd[6674]: Invalid user virus from 201.155.95.199
Jan 25 23:14:30 office-desktop sshd[6674]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:30 office-desktop sshd[6674]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:32 office-desktop sshd[6674]: Failed password for invalid user virus from 201.155.95.199 port 51941 ssh2
Jan 25 23:14:33 office-desktop sshd[6676]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:33 office-desktop sshd[6676]: Invalid user cyrus from 201.155.95.199
Jan 25 23:14:33 office-desktop sshd[6676]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:33 office-desktop sshd[6676]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:35 office-desktop sshd[6676]: Failed password for invalid user cyrus from 201.155.95.199 port 52019 ssh2
Jan 25 23:14:36 office-desktop sshd[6678]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:36 office-desktop sshd[6678]: Invalid user oracle from 201.155.95.199
Jan 25 23:14:36 office-desktop sshd[6678]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:36 office-desktop sshd[6678]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:39 office-desktop sshd[6678]: Failed password for invalid user oracle from 201.155.95.199 port 52117 ssh2
Jan 25 23:14:41 office-desktop sshd[6680]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:41 office-desktop sshd[6680]: Invalid user michael from 201.155.95.199
Jan 25 23:14:41 office-desktop sshd[6680]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:41 office-desktop sshd[6680]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:42 office-desktop sshd[6680]: Failed password for invalid user michael from 201.155.95.199 port 52231 ssh2
Jan 25 23:14:44 office-desktop sshd[6682]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:44 office-desktop sshd[6682]: Invalid user ftp from 201.155.95.199
Jan 25 23:14:44 office-desktop sshd[6682]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:44 office-desktop sshd[6682]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:46 office-desktop sshd[6682]: Failed password for invalid user ftp from 201.155.95.199 port 52329 ssh2
Jan 25 23:14:47 office-desktop sshd[6684]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:47 office-desktop sshd[6684]: Invalid user test from 201.155.95.199
Jan 25 23:14:47 office-desktop sshd[6684]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:47 office-desktop sshd[6684]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:50 office-desktop sshd[6684]: Failed password for invalid user test from 201.155.95.199 port 52416 ssh2
Jan 25 23:14:51 office-desktop sshd[6686]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:51 office-desktop sshd[6686]: Invalid user webmaster from 201.155.95.199
Jan 25 23:14:51 office-desktop sshd[6686]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:51 office-desktop sshd[6686]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:53 office-desktop sshd[6686]: Failed password for invalid user webmaster from 201.155.95.199 port 52518 ssh2
Jan 25 23:14:54 office-desktop sshd[6688]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:54 office-desktop sshd[6688]: Invalid user postmaster from 201.155.95.199
Jan 25 23:14:54 office-desktop sshd[6688]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:54 office-desktop sshd[6688]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:55 office-desktop sshd[6688]: Failed password for invalid user postmaster from 201.155.95.199 port 52600 ssh2
Jan 25 23:14:56 office-desktop sshd[6690]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:56 office-desktop sshd[6690]: Invalid user postfix from 201.155.95.199
Jan 25 23:14:56 office-desktop sshd[6690]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:56 office-desktop sshd[6690]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:59 office-desktop sshd[6690]: Failed password for invalid user postfix from 201.155.95.199 port 52674 ssh2
Jan 25 23:15:00 office-desktop sshd[6692]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:00 office-desktop sshd[6692]: Invalid user postgres from 201.155.95.199
Jan 25 23:15:00 office-desktop sshd[6692]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:00 office-desktop sshd[6692]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:02 office-desktop sshd[6692]: Failed password for invalid user postgres from 201.155.95.199 port 52770 ssh2
Jan 25 23:15:03 office-desktop sshd[6694]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:03 office-desktop sshd[6694]: Invalid user paul from 201.155.95.199
Jan 25 23:15:03 office-desktop sshd[6694]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:03 office-desktop sshd[6694]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:05 office-desktop sshd[6694]: Failed password for invalid user paul from 201.155.95.199 port 52856 ssh2
Jan 25 23:15:06 office-desktop sshd[6696]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:06 office-desktop sshd[6696]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:15:08 office-desktop sshd[6696]: Failed password for root from 201.155.95.199 port 52936 ssh2
Jan 25 23:15:09 office-desktop sshd[6698]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:09 office-desktop sshd[6698]: Invalid user guest from 201.155.95.199
Jan 25 23:15:09 office-desktop sshd[6698]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:09 office-desktop sshd[6698]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:11 office-desktop sshd[6698]: Failed password for invalid user guest from 201.155.95.199 port 53017 ssh2
Jan 25 23:15:12 office-desktop sshd[6700]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:12 office-desktop sshd[6700]: Invalid user admin from 201.155.95.199
Jan 25 23:15:12 office-desktop sshd[6700]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:12 office-desktop sshd[6700]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:15 office-desktop sshd[6700]: Failed password for invalid user admin from 201.155.95.199 port 53100 ssh2
Jan 25 23:15:16 office-desktop sshd[6702]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:16 office-desktop sshd[6702]: Invalid user linux from 201.155.95.199
Jan 25 23:15:16 office-desktop sshd[6702]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:16 office-desktop sshd[6702]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:17 office-desktop sshd[6702]: Failed password for invalid user linux from 201.155.95.199 port 53191 ssh2
Jan 25 23:15:19 office-desktop sshd[6704]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:19 office-desktop sshd[6704]: Invalid user user from 201.155.95.199
Jan 25 23:15:19 office-desktop sshd[6704]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:19 office-desktop sshd[6704]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:21 office-desktop sshd[6704]: Failed password for invalid user user from 201.155.95.199 port 53263 ssh2
Jan 25 23:15:23 office-desktop sshd[6706]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:23 office-desktop sshd[6706]: Invalid user david from 201.155.95.199
Jan 25 23:15:23 office-desktop sshd[6706]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:23 office-desktop sshd[6706]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:25 office-desktop sshd[6706]: Failed password for invalid user david from 201.155.95.199 port 53373 ssh2
Jan 25 23:15:26 office-desktop sshd[6708]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:26 office-desktop sshd[6708]: Invalid user web from 201.155.95.199
Jan 25 23:15:26 office-desktop sshd[6708]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:26 office-desktop sshd[6708]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:28 office-desktop sshd[6708]: Failed password for invalid user web from 201.155.95.199 port 53457 ssh2
Jan 25 23:15:29 office-desktop sshd[6710]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:29 office-desktop sshd[6710]: Invalid user apache from 201.155.95.199
Jan 25 23:15:29 office-desktop sshd[6710]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:29 office-desktop sshd[6710]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:31 office-desktop sshd[6710]: Failed password for invalid user apache from 201.155.95.199 port 53527 ssh2
Jan 25 23:15:32 office-desktop sshd[6712]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:32 office-desktop sshd[6712]: Invalid user pgsql from 201.155.95.199
Jan 25 23:15:32 office-desktop sshd[6712]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:32 office-desktop sshd[6712]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:34 office-desktop sshd[6712]: Failed password for invalid user pgsql from 201.155.95.199 port 53618 ssh2
Jan 25 23:15:35 office-desktop sshd[6714]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:35 office-desktop sshd[6714]: Invalid user mysql from 201.155.95.199
Jan 25 23:15:35 office-desktop sshd[6714]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:35 office-desktop sshd[6714]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:37 office-desktop sshd[6714]: Failed password for invalid user mysql from 201.155.95.199 port 53693 ssh2
Jan 25 23:15:39 office-desktop sshd[6716]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:39 office-desktop sshd[6716]: Invalid user info from 201.155.95.199
Jan 25 23:15:39 office-desktop sshd[6716]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:39 office-desktop sshd[6716]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:40 office-desktop sshd[6716]: Failed password for invalid user info from 201.155.95.199 port 53782 ssh2
Jan 25 23:15:42 office-desktop sshd[6718]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:42 office-desktop sshd[6718]: Invalid user tony from 201.155.95.199
Jan 25 23:15:42 office-desktop sshd[6718]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:42 office-desktop sshd[6718]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:44 office-desktop sshd[6718]: Failed password for invalid user tony from 201.155.95.199 port 53859 ssh2
Jan 25 23:15:45 office-desktop sshd[6720]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:45 office-desktop sshd[6720]: Invalid user core from 201.155.95.199
Jan 25 23:15:45 office-desktop sshd[6720]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:45 office-desktop sshd[6720]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:47 office-desktop sshd[6720]: Failed password for invalid user core from 201.155.95.199 port 53956 ssh2
Jan 25 23:15:48 office-desktop sshd[6722]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:48 office-desktop sshd[6722]: Invalid user newsletter from 201.155.95.199
Jan 25 23:15:48 office-desktop sshd[6722]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:48 office-desktop sshd[6722]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:51 office-desktop sshd[6722]: Failed password for invalid user newsletter from 201.155.95.199 port 54040 ssh2
Jan 25 23:15:52 office-desktop sshd[6724]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:52 office-desktop sshd[6724]: Invalid user named from 201.155.95.199
Jan 25 23:15:52 office-desktop sshd[6724]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:52 office-desktop sshd[6724]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:54 office-desktop sshd[6724]: Failed password for invalid user named from 201.155.95.199 port 54132 ssh2
Jan 25 23:15:58 office-desktop sshd[6726]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:58 office-desktop sshd[6726]: Invalid user visitor from 201.155.95.199
Jan 25 23:15:58 office-desktop sshd[6726]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:58 office-desktop sshd[6726]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:59 office-desktop sshd[6726]: Failed password for invalid user visitor from 201.155.95.199 port 54215 ssh2
Jan 25 23:16:01 office-desktop sshd[6728]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:01 office-desktop sshd[6728]: Invalid user ftpuser from 201.155.95.199
Jan 25 23:16:01 office-desktop sshd[6728]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:01 office-desktop sshd[6728]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:03 office-desktop sshd[6728]: Failed password for invalid user ftpuser from 201.155.95.199 port 54358 ssh2
Jan 25 23:16:04 office-desktop sshd[6730]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:04 office-desktop sshd[6730]: Invalid user username from 201.155.95.199
Jan 25 23:16:04 office-desktop sshd[6730]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:04 office-desktop sshd[6730]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:06 office-desktop sshd[6730]: Failed password for invalid user username from 201.155.95.199 port 54452 ssh2
Jan 25 23:16:08 office-desktop sshd[6732]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:08 office-desktop sshd[6732]: Invalid user administrator from 201.155.95.199
Jan 25 23:16:08 office-desktop sshd[6732]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:08 office-desktop sshd[6732]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:10 office-desktop sshd[6732]: Failed password for invalid user administrator from 201.155.95.199 port 54528 ssh2
Jan 25 23:16:11 office-desktop sshd[6734]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:11 office-desktop sshd[6734]: Invalid user library from 201.155.95.199
Jan 25 23:16:11 office-desktop sshd[6734]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:11 office-desktop sshd[6734]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:13 office-desktop sshd[6734]: Failed password for invalid user library from 201.155.95.199 port 54618 ssh2
Jan 25 23:16:14 office-desktop sshd[6736]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:14 office-desktop sshd[6736]: Invalid user test from 201.155.95.199
Jan 25 23:16:14 office-desktop sshd[6736]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:14 office-desktop sshd[6736]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:15 office-desktop sshd[6736]: Failed password for invalid user test from 201.155.95.199 port 54691 ssh2
Jan 25 23:16:16 office-desktop sshd[6738]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:16 office-desktop sshd[6738]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:18 office-desktop sshd[6738]: Failed password for root from 201.155.95.199 port 54748 ssh2
Jan 25 23:16:19 office-desktop sshd[6740]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:19 office-desktop sshd[6740]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:21 office-desktop sshd[6740]: Failed password for root from 201.155.95.199 port 54818 ssh2
Jan 25 23:16:23 office-desktop sshd[6742]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:23 office-desktop sshd[6742]: Invalid user admin from 201.155.95.199
Jan 25 23:16:23 office-desktop sshd[6742]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:23 office-desktop sshd[6742]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:25 office-desktop sshd[6742]: Failed password for invalid user admin from 201.155.95.199 port 54903 ssh2
Jan 25 23:16:26 office-desktop sshd[6744]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:26 office-desktop sshd[6744]: Invalid user guest from 201.155.95.199
Jan 25 23:16:26 office-desktop sshd[6744]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:26 office-desktop sshd[6744]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:27 office-desktop sshd[6744]: Failed password for invalid user guest from 201.155.95.199 port 54976 ssh2
Jan 25 23:16:28 office-desktop sshd[6746]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:28 office-desktop sshd[6746]: Invalid user master from 201.155.95.199
Jan 25 23:16:28 office-desktop sshd[6746]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:28 office-desktop sshd[6746]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:31 office-desktop sshd[6746]: Failed password for invalid user master from 201.155.95.199 port 55036 ssh2
Jan 25 23:16:32 office-desktop sshd[6748]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:32 office-desktop sshd[6748]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:34 office-desktop sshd[6748]: Failed password for root from 201.155.95.199 port 55114 ssh2
Jan 25 23:16:35 office-desktop sshd[6750]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:35 office-desktop sshd[6750]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:37 office-desktop sshd[6750]: Failed password for root from 201.155.95.199 port 55181 ssh2
Jan 25 23:16:38 office-desktop sshd[6752]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:38 office-desktop sshd[6752]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:39 office-desktop sshd[6752]: Failed password for root from 201.155.95.199 port 55255 ssh2
Jan 25 23:16:40 office-desktop sshd[6754]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:40 office-desktop sshd[6754]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:42 office-desktop sshd[6754]: Failed password for root from 201.155.95.199 port 55313 ssh2
Jan 25 23:16:44 office-desktop sshd[6756]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:44 office-desktop sshd[6756]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:46 office-desktop sshd[6756]: Failed password for root from 201.155.95.199 port 55387 ssh2
Jan 25 23:16:47 office-desktop sshd[6758]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:47 office-desktop sshd[6758]: Invalid user admin from 201.155.95.199
Jan 25 23:16:47 office-desktop sshd[6758]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:47 office-desktop sshd[6758]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:49 office-desktop sshd[6758]: Failed password for invalid user admin from 201.155.95.199 port 55451 ssh2
Jan 25 23:16:50 office-desktop sshd[6760]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:50 office-desktop sshd[6760]: Invalid user admin from 201.155.95.199
Jan 25 23:16:50 office-desktop sshd[6760]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:50 office-desktop sshd[6760]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:51 office-desktop sshd[6760]: Failed password for invalid user admin from 201.155.95.199 port 55522 ssh2
Jan 25 23:16:52 office-desktop sshd[6762]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:52 office-desktop sshd[6762]: Invalid user admin from 201.155.95.199
Jan 25 23:16:52 office-desktop sshd[6762]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:52 office-desktop sshd[6762]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:54 office-desktop sshd[6762]: Failed password for invalid user admin from 201.155.95.199 port 55580 ssh2
Jan 25 23:16:56 office-desktop sshd[6764]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:56 office-desktop sshd[6764]: Invalid user admin from 201.155.95.199
Jan 25 23:16:56 office-desktop sshd[6764]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:56 office-desktop sshd[6764]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:57 office-desktop sshd[6764]: Failed password for invalid user admin from 201.155.95.199 port 55658 ssh2
Jan 25 23:16:58 office-desktop sshd[6766]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:58 office-desktop sshd[6766]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:00 office-desktop sshd[6766]: Failed password for root from 201.155.95.199 port 55716 ssh2
Jan 25 23:17:01 office-desktop CRON[6770]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 23:17:01 office-desktop CRON[6770]: pam_unix(cron:session): session closed for user root
Jan 25 23:17:01 office-desktop sshd[6768]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:01 office-desktop sshd[6768]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:04 office-desktop sshd[6768]: Failed password for root from 201.155.95.199 port 55789 ssh2
Jan 25 23:17:05 office-desktop sshd[6773]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:05 office-desktop sshd[6773]: Invalid user test from 201.155.95.199
Jan 25 23:17:05 office-desktop sshd[6773]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:05 office-desktop sshd[6773]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:07 office-desktop sshd[6773]: Failed password for invalid user test from 201.155.95.199 port 55864 ssh2
Jan 25 23:17:08 office-desktop sshd[6775]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:08 office-desktop sshd[6775]: Invalid user test from 201.155.95.199
Jan 25 23:17:08 office-desktop sshd[6775]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:08 office-desktop sshd[6775]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:09 office-desktop sshd[6775]: Failed password for invalid user test from 201.155.95.199 port 55940 ssh2
Jan 25 23:17:11 office-desktop sshd[6777]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:11 office-desktop sshd[6777]: Invalid user webmaster from 201.155.95.199
Jan 25 23:17:11 office-desktop sshd[6777]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:11 office-desktop sshd[6777]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:12 office-desktop sshd[6777]: Failed password for invalid user webmaster from 201.155.95.199 port 55989 ssh2
Jan 25 23:17:14 office-desktop sshd[6779]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:14 office-desktop sshd[6779]: Invalid user username from 201.155.95.199
Jan 25 23:17:14 office-desktop sshd[6779]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:14 office-desktop sshd[6779]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:15 office-desktop sshd[6779]: Failed password for invalid user username from 201.155.95.199 port 56048 ssh2
Jan 25 23:17:16 office-desktop sshd[6781]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:16 office-desktop sshd[6781]: Invalid user user from 201.155.95.199
Jan 25 23:17:16 office-desktop sshd[6781]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:16 office-desktop sshd[6781]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:18 office-desktop sshd[6781]: Failed password for invalid user user from 201.155.95.199 port 56106 ssh2
Jan 25 23:17:19 office-desktop sshd[6783]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:19 office-desktop sshd[6783]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:21 office-desktop sshd[6783]: Failed password for root from 201.155.95.199 port 56172 ssh2
Jan 25 23:17:23 office-desktop sshd[6785]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:23 office-desktop sshd[6785]: Invalid user admin from 201.155.95.199
Jan 25 23:17:23 office-desktop sshd[6785]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:23 office-desktop sshd[6785]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:24 office-desktop sshd[6785]: Failed password for invalid user admin from 201.155.95.199 port 56239 ssh2
Jan 25 23:17:26 office-desktop sshd[6787]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:26 office-desktop sshd[6787]: Invalid user test from 201.155.95.199
Jan 25 23:17:26 office-desktop sshd[6787]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:26 office-desktop sshd[6787]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:27 office-desktop sshd[6787]: Failed password for invalid user test from 201.155.95.199 port 56298 ssh2
Jan 25 23:17:29 office-desktop sshd[6789]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:29 office-desktop sshd[6789]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:31 office-desktop sshd[6789]: Failed password for root from 201.155.95.199 port 56352 ssh2
Jan 25 23:17:32 office-desktop sshd[6791]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:32 office-desktop sshd[6791]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:33 office-desktop sshd[6791]: Failed password for root from 201.155.95.199 port 56414 ssh2
Jan 25 23:17:34 office-desktop sshd[6793]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:34 office-desktop sshd[6793]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:36 office-desktop sshd[6793]: Failed password for root from 201.155.95.199 port 56454 ssh2
Jan 25 23:17:40 office-desktop sshd[6795]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:40 office-desktop sshd[6795]: Invalid user danny from 201.155.95.199
Jan 25 23:17:40 office-desktop sshd[6795]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:40 office-desktop sshd[6795]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:42 office-desktop sshd[6795]: Failed password for invalid user danny from 201.155.95.199 port 56495 ssh2
Jan 25 23:17:44 office-desktop sshd[6797]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:44 office-desktop sshd[6797]: Invalid user alex from 201.155.95.199
Jan 25 23:17:44 office-desktop sshd[6797]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:44 office-desktop sshd[6797]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:45 office-desktop sshd[6797]: Failed password for invalid user alex from 201.155.95.199 port 56586 ssh2
Jan 25 23:17:47 office-desktop sshd[6799]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:47 office-desktop sshd[6799]: Invalid user brett from 201.155.95.199
Jan 25 23:17:47 office-desktop sshd[6799]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:47 office-desktop sshd[6799]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:48 office-desktop sshd[6799]: Failed password for invalid user brett from 201.155.95.199 port 56625 ssh2
Jan 25 23:17:50 office-desktop sshd[6801]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:50 office-desktop sshd[6801]: Invalid user mike from 201.155.95.199
Jan 25 23:17:50 office-desktop sshd[6801]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:50 office-desktop sshd[6801]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:52 office-desktop sshd[6801]: Failed password for invalid user mike from 201.155.95.199 port 56662 ssh2
Jan 25 23:17:53 office-desktop sshd[6803]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:53 office-desktop sshd[6803]: Invalid user alan from 201.155.95.199
Jan 25 23:17:53 office-desktop sshd[6803]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:53 office-desktop sshd[6803]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:55 office-desktop sshd[6803]: Failed password for invalid user alan from 201.155.95.199 port 56702 ssh2
Jan 25 23:17:56 office-desktop sshd[6805]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:56 office-desktop sshd[6805]: Invalid user data from 201.155.95.199
Jan 25 23:17:56 office-desktop sshd[6805]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:56 office-desktop sshd[6805]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:58 office-desktop sshd[6805]: Failed password for invalid user data from 201.155.95.199 port 56739 ssh2
Jan 25 23:17:59 office-desktop sshd[6807]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:59 office-desktop sshd[6807]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=www-data
Jan 25 23:18:01 office-desktop sshd[6807]: Failed password for www-data from 201.155.95.199 port 56776 ssh2
Jan 25 23:18:02 office-desktop sshd[6809]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:02 office-desktop sshd[6809]: Invalid user http from 201.155.95.199
Jan 25 23:18:02 office-desktop sshd[6809]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:02 office-desktop sshd[6809]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:04 office-desktop sshd[6809]: Failed password for invalid user http from 201.155.95.199 port 56815 ssh2
Jan 25 23:18:05 office-desktop sshd[6811]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:05 office-desktop sshd[6811]: Invalid user httpd from 201.155.95.199
Jan 25 23:18:05 office-desktop sshd[6811]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:05 office-desktop sshd[6811]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:07 office-desktop sshd[6811]: Failed password for invalid user httpd from 201.155.95.199 port 56850 ssh2
Jan 25 23:18:08 office-desktop sshd[6813]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:08 office-desktop sshd[6813]: Invalid user pop from 201.155.95.199
Jan 25 23:18:08 office-desktop sshd[6813]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:08 office-desktop sshd[6813]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:10 office-desktop sshd[6813]: Failed password for invalid user pop from 201.155.95.199 port 56884 ssh2
Jan 25 23:18:11 office-desktop sshd[6815]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:11 office-desktop sshd[6815]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=nobody
Jan 25 23:18:13 office-desktop sshd[6815]: Failed password for nobody from 201.155.95.199 port 56917 ssh2
Jan 25 23:18:14 office-desktop sshd[6817]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:14 office-desktop sshd[6817]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:18:16 office-desktop sshd[6817]: Failed password for root from 201.155.95.199 port 56954 ssh2
Jan 25 23:18:17 office-desktop sshd[6819]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:17 office-desktop sshd[6819]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=backup
Jan 25 23:18:19 office-desktop sshd[6819]: Failed password for backup from 201.155.95.199 port 56991 ssh2
Jan 25 23:18:20 office-desktop sshd[6821]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:20 office-desktop sshd[6821]: Invalid user info from 201.155.95.199
Jan 25 23:18:20 office-desktop sshd[6821]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:20 office-desktop sshd[6821]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:22 office-desktop sshd[6821]: Failed password for invalid user info from 201.155.95.199 port 57020 ssh2
Jan 25 23:18:23 office-desktop sshd[6823]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:23 office-desktop sshd[6823]: Invalid user shop from 201.155.95.199
Jan 25 23:18:23 office-desktop sshd[6823]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:23 office-desktop sshd[6823]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:25 office-desktop sshd[6823]: Failed password for invalid user shop from 201.155.95.199 port 57048 ssh2
Jan 25 23:18:26 office-desktop sshd[6825]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:26 office-desktop sshd[6825]: Invalid user sales from 201.155.95.199
Jan 25 23:18:26 office-desktop sshd[6825]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:26 office-desktop sshd[6825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:28 office-desktop sshd[6825]: Failed password for invalid user sales from 201.155.95.199 port 57084 ssh2
Jan 25 23:18:29 office-desktop sshd[6827]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:29 office-desktop sshd[6827]: Invalid user web from 201.155.95.199
Jan 25 23:18:29 office-desktop sshd[6827]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:29 office-desktop sshd[6827]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:31 office-desktop sshd[6827]: Failed password for invalid user web from 201.155.95.199 port 57120 ssh2
Jan 25 23:18:32 office-desktop sshd[6829]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:32 office-desktop sshd[6829]: Invalid user www from 201.155.95.199
Jan 25 23:18:32 office-desktop sshd[6829]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:32 office-desktop sshd[6829]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:34 office-desktop sshd[6829]: Failed password for invalid user www from 201.155.95.199 port 57150 ssh2
Jan 25 23:18:35 office-desktop sshd[6831]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:35 office-desktop sshd[6831]: Invalid user wwwrun from 201.155.95.199
Jan 25 23:18:35 office-desktop sshd[6831]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:35 office-desktop sshd[6831]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:37 office-desktop sshd[6831]: Failed password for invalid user wwwrun from 201.155.95.199 port 57183 ssh2
Jan 25 23:18:42 office-desktop sshd[6833]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:42 office-desktop sshd[6833]: Invalid user adam from 201.155.95.199
Jan 25 23:18:42 office-desktop sshd[6833]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:42 office-desktop sshd[6833]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:44 office-desktop sshd[6833]: Failed password for invalid user adam from 201.155.95.199 port 57219 ssh2
Jan 25 23:18:46 office-desktop sshd[6835]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:46 office-desktop sshd[6835]: Invalid user stephen from 201.155.95.199
Jan 25 23:18:46 office-desktop sshd[6835]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:46 office-desktop sshd[6835]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:48 office-desktop sshd[6835]: Failed password for invalid user stephen from 201.155.95.199 port 57750 ssh2
Jan 25 23:18:53 office-desktop sshd[6837]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:53 office-desktop sshd[6837]: Invalid user richard from 201.155.95.199
Jan 25 23:18:53 office-desktop sshd[6837]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:53 office-desktop sshd[6837]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:55 office-desktop sshd[6837]: Failed password for invalid user richard from 201.155.95.199 port 58187 ssh2
Jan 25 23:18:59 office-desktop sshd[6839]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:59 office-desktop sshd[6839]: Invalid user george from 201.155.95.199
Jan 25 23:18:59 office-desktop sshd[6839]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:59 office-desktop sshd[6839]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:01 office-desktop sshd[6839]: Failed password for invalid user george from 201.155.95.199 port 59017 ssh2
Jan 25 23:19:02 office-desktop sshd[6841]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:02 office-desktop sshd[6841]: Invalid user john from 201.155.95.199
Jan 25 23:19:02 office-desktop sshd[6841]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:02 office-desktop sshd[6841]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:04 office-desktop sshd[6841]: Failed password for invalid user john from 201.155.95.199 port 59545 ssh2
Jan 25 23:19:08 office-desktop sshd[6843]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:08 office-desktop sshd[6843]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=news
Jan 25 23:19:10 office-desktop sshd[6843]: Failed password for news from 201.155.95.199 port 59573 ssh2
Jan 25 23:19:15 office-desktop sshd[6845]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:15 office-desktop sshd[6845]: Invalid user angel from 201.155.95.199
Jan 25 23:19:15 office-desktop sshd[6845]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:15 office-desktop sshd[6845]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:17 office-desktop sshd[6845]: Failed password for invalid user angel from 201.155.95.199 port 60339 ssh2
Jan 25 23:19:18 office-desktop sshd[6847]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:18 office-desktop sshd[6847]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=games
Jan 25 23:19:20 office-desktop sshd[6847]: Failed password for games from 201.155.95.199 port 60838 ssh2
Jan 25 23:19:25 office-desktop sshd[6849]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:25 office-desktop sshd[6849]: Invalid user pgsql from 201.155.95.199
Jan 25 23:19:25 office-desktop sshd[6849]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:25 office-desktop sshd[6849]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:27 office-desktop sshd[6849]: Failed password for invalid user pgsql from 201.155.95.199 port 32962 ssh2
Jan 25 23:19:37 office-desktop sshd[6851]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:37 office-desktop sshd[6851]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=mail
Jan 25 23:19:39 office-desktop sshd[6851]: Failed password for mail from 201.155.95.199 port 33444 ssh2
Jan 26 00:17:01 office-desktop CRON[6853]: pam_unix(cron:session): session opened for user root by (uid=0)
```

This is crazy!! It means that somebody was trying to break into my computer and tried invalid usernames or passwords. What should I do? I'm terrified.

Please help

P.S. My Firefox keeps crashing now and I've never had any problems before. Does this mean my PC is hacked already? <crying>

---

### Post by Nepherte on 2009-01-28
Here's a page about securing ssh server: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) I'd say the most important ones are changing the default ssh port, using password protected public/private key pairs and denyhosts.

---

### Post by bmwman on 2009-01-28
Look at the last line of the log > Jan 26 00:17:01 office-desktop CRON[6853]: pam_unix(cron:session): session opened for user root by (uid=0)
Does this mean I have been screwed royally already and it wasn't just an attempt? I certainly wasn't up on the computer at 00:17 o'clock.

---

### Post by cariboo on 2009-01-28
Probably, I hope you pulled the network cable, so the intruder can't do any more damage. If you want to find out what has happened, pull the drive and put in a new one and reinstall your system. Then you can check at your leisure to see what's happened.

Jim

---

### Post by bmwman on 2009-01-28
I already turned that PC off and removed the port forwarding from my router. Currently i have no other ways for access from the outside (I hope so). This was the only computer that was running SSH server because I was logging in it from work. Which other logs I can look for to see what the damn ******* did?

---

### Post by wirelessmonkey on 2009-01-28
Actually, I believe that line is just root's cron running, and is nothing to be worried about.

---

### Post by jerome1232 on 2009-01-28
I think it should be noted that if you have an ssh server running on port 22 it will be hit by bots, and it will be hit by bots all the time.

If you use a strong passphrase or keys then it's really nothing to worry about, although it does clutter your logs. 

Just read up at the link given earlier, for tips on securing the server, I personally use a strong passphrase along with denyhosts (gives each ip 5 attempts then permanently bans them from attempting to connect)

I'm also pretty sure that last entry is just a cron job, grep that log for sshd and if you see any accepted logins from ip's that aren't yours *then* I would get concerned.

---

### Post by abn91c on 2009-01-29
prod-empresarial.com.mx is a mexico ISP, go to whois and paste the domain or one of the offending IP's from the log and at least report to the abuse links there.

---

### Post by gtdaqua on 2009-01-29
> **bmwman said:**
> I come home today and find my PC rebooted. I never shut it off myself. Then I looked at the logs and find this:
```

Jan 25 16:17:01 office-desktop CRON[16965]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 16:17:01 office-desktop CRON[16965]: pam_unix(cron:session): session closed for user root
Jan 25 17:17:01 office-desktop CRON[17362]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 17:17:01 office-desktop CRON[17362]: pam_unix(cron:session): session closed for user root
Jan 25 18:17:01 office-desktop CRON[17943]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 18:17:01 office-desktop CRON[17943]: pam_unix(cron:session): session closed for user root
Jan 25 18:58:51 office-desktop gnome-keyring-daemon[6651]: adding removable location: volume_label_NO_NAME at /media/NO NAME
Jan 25 19:06:24 office-desktop gnome-keyring-daemon[6651]: removing removable location: volume_label_NO_NAME
Jan 25 19:07:27 office-desktop gnome-keyring-daemon[6651]: adding removable location: volume_uuid_0000_0C3C at /media/CASIO-DSC
Jan 25 19:17:01 office-desktop CRON[19041]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 19:17:01 office-desktop CRON[19041]: pam_unix(cron:session): session closed for user root
Jan 25 19:40:24 office-desktop gnome-keyring-daemon[6651]: removing removable location: volume_uuid_0000_0C3C
Jan 25 19:50:47 office-desktop gdm[6249]: pam_unix(gdm:session): session closed for user bmw-man
Jan 25 19:51:51 office-desktop sshd[5136]: Server listening on :: port 22.
Jan 25 19:51:51 office-desktop sshd[5136]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Jan 25 20:17:01 office-desktop CRON[6642]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 20:17:01 office-desktop CRON[6642]: pam_unix(cron:session): session closed for user root
Jan 25 21:17:01 office-desktop CRON[6648]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 21:17:01 office-desktop CRON[6648]: pam_unix(cron:session): session closed for user root
Jan 25 22:17:01 office-desktop CRON[6652]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 22:17:01 office-desktop CRON[6652]: pam_unix(cron:session): session closed for user root
Jan 25 23:09:28 office-desktop sshd[6655]: Did not receive identification string from 201.155.95.199
Jan 25 23:13:53 office-desktop sshd[6656]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:13:53 office-desktop sshd[6656]: Invalid user staff from 201.155.95.199
Jan 25 23:13:53 office-desktop sshd[6656]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:13:53 office-desktop sshd[6656]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:13:56 office-desktop sshd[6656]: Failed password for invalid user staff from 201.155.95.199 port 50721 ssh2
Jan 25 23:13:57 office-desktop sshd[6658]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:13:57 office-desktop sshd[6658]: Invalid user sales from 201.155.95.199
Jan 25 23:13:57 office-desktop sshd[6658]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:13:57 office-desktop sshd[6658]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:13:59 office-desktop sshd[6658]: Failed password for invalid user sales from 201.155.95.199 port 50871 ssh2
Jan 25 23:14:03 office-desktop sshd[6660]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:03 office-desktop sshd[6660]: Invalid user recruit from 201.155.95.199
Jan 25 23:14:03 office-desktop sshd[6660]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:03 office-desktop sshd[6660]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:05 office-desktop sshd[6660]: Failed password for invalid user recruit from 201.155.95.199 port 50984 ssh2
Jan 25 23:14:06 office-desktop sshd[6662]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:06 office-desktop sshd[6662]: Invalid user alias from 201.155.95.199
Jan 25 23:14:06 office-desktop sshd[6662]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:06 office-desktop sshd[6662]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:09 office-desktop sshd[6662]: Failed password for invalid user alias from 201.155.95.199 port 51173 ssh2
Jan 25 23:14:13 office-desktop sshd[6664]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:13 office-desktop sshd[6664]: Invalid user office from 201.155.95.199
Jan 25 23:14:13 office-desktop sshd[6664]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:13 office-desktop sshd[6664]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:15 office-desktop sshd[6664]: Failed password for invalid user office from 201.155.95.199 port 51284 ssh2
Jan 25 23:14:17 office-desktop sshd[6666]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:17 office-desktop sshd[6666]: Invalid user samba from 201.155.95.199
Jan 25 23:14:17 office-desktop sshd[6666]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:17 office-desktop sshd[6666]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:19 office-desktop sshd[6666]: Failed password for invalid user samba from 201.155.95.199 port 51505 ssh2
Jan 25 23:14:20 office-desktop sshd[6668]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:20 office-desktop sshd[6668]: Invalid user tomcat from 201.155.95.199
Jan 25 23:14:20 office-desktop sshd[6668]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:20 office-desktop sshd[6668]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:22 office-desktop sshd[6668]: Failed password for invalid user tomcat from 201.155.95.199 port 51610 ssh2
Jan 25 23:14:24 office-desktop sshd[6670]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:24 office-desktop sshd[6670]: Invalid user webadmin from 201.155.95.199
Jan 25 23:14:24 office-desktop sshd[6670]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:24 office-desktop sshd[6670]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:26 office-desktop sshd[6670]: Failed password for invalid user webadmin from 201.155.95.199 port 51733 ssh2
Jan 25 23:14:27 office-desktop sshd[6672]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:27 office-desktop sshd[6672]: Invalid user spam from 201.155.95.199
Jan 25 23:14:27 office-desktop sshd[6672]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:27 office-desktop sshd[6672]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:29 office-desktop sshd[6672]: Failed password for invalid user spam from 201.155.95.199 port 51838 ssh2
Jan 25 23:14:30 office-desktop sshd[6674]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:30 office-desktop sshd[6674]: Invalid user virus from 201.155.95.199
Jan 25 23:14:30 office-desktop sshd[6674]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:30 office-desktop sshd[6674]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:32 office-desktop sshd[6674]: Failed password for invalid user virus from 201.155.95.199 port 51941 ssh2
Jan 25 23:14:33 office-desktop sshd[6676]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:33 office-desktop sshd[6676]: Invalid user cyrus from 201.155.95.199
Jan 25 23:14:33 office-desktop sshd[6676]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:33 office-desktop sshd[6676]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:35 office-desktop sshd[6676]: Failed password for invalid user cyrus from 201.155.95.199 port 52019 ssh2
Jan 25 23:14:36 office-desktop sshd[6678]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:36 office-desktop sshd[6678]: Invalid user oracle from 201.155.95.199
Jan 25 23:14:36 office-desktop sshd[6678]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:36 office-desktop sshd[6678]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:39 office-desktop sshd[6678]: Failed password for invalid user oracle from 201.155.95.199 port 52117 ssh2
Jan 25 23:14:41 office-desktop sshd[6680]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:41 office-desktop sshd[6680]: Invalid user michael from 201.155.95.199
Jan 25 23:14:41 office-desktop sshd[6680]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:41 office-desktop sshd[6680]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:42 office-desktop sshd[6680]: Failed password for invalid user michael from 201.155.95.199 port 52231 ssh2
Jan 25 23:14:44 office-desktop sshd[6682]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:44 office-desktop sshd[6682]: Invalid user ftp from 201.155.95.199
Jan 25 23:14:44 office-desktop sshd[6682]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:44 office-desktop sshd[6682]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:46 office-desktop sshd[6682]: Failed password for invalid user ftp from 201.155.95.199 port 52329 ssh2
Jan 25 23:14:47 office-desktop sshd[6684]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:47 office-desktop sshd[6684]: Invalid user test from 201.155.95.199
Jan 25 23:14:47 office-desktop sshd[6684]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:47 office-desktop sshd[6684]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:50 office-desktop sshd[6684]: Failed password for invalid user test from 201.155.95.199 port 52416 ssh2
Jan 25 23:14:51 office-desktop sshd[6686]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:51 office-desktop sshd[6686]: Invalid user webmaster from 201.155.95.199
Jan 25 23:14:51 office-desktop sshd[6686]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:51 office-desktop sshd[6686]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:53 office-desktop sshd[6686]: Failed password for invalid user webmaster from 201.155.95.199 port 52518 ssh2
Jan 25 23:14:54 office-desktop sshd[6688]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:54 office-desktop sshd[6688]: Invalid user postmaster from 201.155.95.199
Jan 25 23:14:54 office-desktop sshd[6688]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:54 office-desktop sshd[6688]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:55 office-desktop sshd[6688]: Failed password for invalid user postmaster from 201.155.95.199 port 52600 ssh2
Jan 25 23:14:56 office-desktop sshd[6690]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:14:56 office-desktop sshd[6690]: Invalid user postfix from 201.155.95.199
Jan 25 23:14:56 office-desktop sshd[6690]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:14:56 office-desktop sshd[6690]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:14:59 office-desktop sshd[6690]: Failed password for invalid user postfix from 201.155.95.199 port 52674 ssh2
Jan 25 23:15:00 office-desktop sshd[6692]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:00 office-desktop sshd[6692]: Invalid user postgres from 201.155.95.199
Jan 25 23:15:00 office-desktop sshd[6692]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:00 office-desktop sshd[6692]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:02 office-desktop sshd[6692]: Failed password for invalid user postgres from 201.155.95.199 port 52770 ssh2
Jan 25 23:15:03 office-desktop sshd[6694]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:03 office-desktop sshd[6694]: Invalid user paul from 201.155.95.199
Jan 25 23:15:03 office-desktop sshd[6694]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:03 office-desktop sshd[6694]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:05 office-desktop sshd[6694]: Failed password for invalid user paul from 201.155.95.199 port 52856 ssh2
Jan 25 23:15:06 office-desktop sshd[6696]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:06 office-desktop sshd[6696]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:15:08 office-desktop sshd[6696]: Failed password for root from 201.155.95.199 port 52936 ssh2
Jan 25 23:15:09 office-desktop sshd[6698]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:09 office-desktop sshd[6698]: Invalid user guest from 201.155.95.199
Jan 25 23:15:09 office-desktop sshd[6698]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:09 office-desktop sshd[6698]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:11 office-desktop sshd[6698]: Failed password for invalid user guest from 201.155.95.199 port 53017 ssh2
Jan 25 23:15:12 office-desktop sshd[6700]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:12 office-desktop sshd[6700]: Invalid user admin from 201.155.95.199
Jan 25 23:15:12 office-desktop sshd[6700]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:12 office-desktop sshd[6700]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:15 office-desktop sshd[6700]: Failed password for invalid user admin from 201.155.95.199 port 53100 ssh2
Jan 25 23:15:16 office-desktop sshd[6702]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:16 office-desktop sshd[6702]: Invalid user linux from 201.155.95.199
Jan 25 23:15:16 office-desktop sshd[6702]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:16 office-desktop sshd[6702]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:17 office-desktop sshd[6702]: Failed password for invalid user linux from 201.155.95.199 port 53191 ssh2
Jan 25 23:15:19 office-desktop sshd[6704]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:19 office-desktop sshd[6704]: Invalid user user from 201.155.95.199
Jan 25 23:15:19 office-desktop sshd[6704]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:19 office-desktop sshd[6704]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:21 office-desktop sshd[6704]: Failed password for invalid user user from 201.155.95.199 port 53263 ssh2
Jan 25 23:15:23 office-desktop sshd[6706]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:23 office-desktop sshd[6706]: Invalid user david from 201.155.95.199
Jan 25 23:15:23 office-desktop sshd[6706]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:23 office-desktop sshd[6706]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:25 office-desktop sshd[6706]: Failed password for invalid user david from 201.155.95.199 port 53373 ssh2
Jan 25 23:15:26 office-desktop sshd[6708]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:26 office-desktop sshd[6708]: Invalid user web from 201.155.95.199
Jan 25 23:15:26 office-desktop sshd[6708]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:26 office-desktop sshd[6708]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:28 office-desktop sshd[6708]: Failed password for invalid user web from 201.155.95.199 port 53457 ssh2
Jan 25 23:15:29 office-desktop sshd[6710]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:29 office-desktop sshd[6710]: Invalid user apache from 201.155.95.199
Jan 25 23:15:29 office-desktop sshd[6710]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:29 office-desktop sshd[6710]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:31 office-desktop sshd[6710]: Failed password for invalid user apache from 201.155.95.199 port 53527 ssh2
Jan 25 23:15:32 office-desktop sshd[6712]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:32 office-desktop sshd[6712]: Invalid user pgsql from 201.155.95.199
Jan 25 23:15:32 office-desktop sshd[6712]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:32 office-desktop sshd[6712]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:34 office-desktop sshd[6712]: Failed password for invalid user pgsql from 201.155.95.199 port 53618 ssh2
Jan 25 23:15:35 office-desktop sshd[6714]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:35 office-desktop sshd[6714]: Invalid user mysql from 201.155.95.199
Jan 25 23:15:35 office-desktop sshd[6714]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:35 office-desktop sshd[6714]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:37 office-desktop sshd[6714]: Failed password for invalid user mysql from 201.155.95.199 port 53693 ssh2
Jan 25 23:15:39 office-desktop sshd[6716]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:39 office-desktop sshd[6716]: Invalid user info from 201.155.95.199
Jan 25 23:15:39 office-desktop sshd[6716]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:39 office-desktop sshd[6716]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:40 office-desktop sshd[6716]: Failed password for invalid user info from 201.155.95.199 port 53782 ssh2
Jan 25 23:15:42 office-desktop sshd[6718]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:42 office-desktop sshd[6718]: Invalid user tony from 201.155.95.199
Jan 25 23:15:42 office-desktop sshd[6718]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:42 office-desktop sshd[6718]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:44 office-desktop sshd[6718]: Failed password for invalid user tony from 201.155.95.199 port 53859 ssh2
Jan 25 23:15:45 office-desktop sshd[6720]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:45 office-desktop sshd[6720]: Invalid user core from 201.155.95.199
Jan 25 23:15:45 office-desktop sshd[6720]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:45 office-desktop sshd[6720]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:47 office-desktop sshd[6720]: Failed password for invalid user core from 201.155.95.199 port 53956 ssh2
Jan 25 23:15:48 office-desktop sshd[6722]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:48 office-desktop sshd[6722]: Invalid user newsletter from 201.155.95.199
Jan 25 23:15:48 office-desktop sshd[6722]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:48 office-desktop sshd[6722]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:51 office-desktop sshd[6722]: Failed password for invalid user newsletter from 201.155.95.199 port 54040 ssh2
Jan 25 23:15:52 office-desktop sshd[6724]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:52 office-desktop sshd[6724]: Invalid user named from 201.155.95.199
Jan 25 23:15:52 office-desktop sshd[6724]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:52 office-desktop sshd[6724]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:54 office-desktop sshd[6724]: Failed password for invalid user named from 201.155.95.199 port 54132 ssh2
Jan 25 23:15:58 office-desktop sshd[6726]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:15:58 office-desktop sshd[6726]: Invalid user visitor from 201.155.95.199
Jan 25 23:15:58 office-desktop sshd[6726]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:15:58 office-desktop sshd[6726]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:15:59 office-desktop sshd[6726]: Failed password for invalid user visitor from 201.155.95.199 port 54215 ssh2
Jan 25 23:16:01 office-desktop sshd[6728]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:01 office-desktop sshd[6728]: Invalid user ftpuser from 201.155.95.199
Jan 25 23:16:01 office-desktop sshd[6728]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:01 office-desktop sshd[6728]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:03 office-desktop sshd[6728]: Failed password for invalid user ftpuser from 201.155.95.199 port 54358 ssh2
Jan 25 23:16:04 office-desktop sshd[6730]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:04 office-desktop sshd[6730]: Invalid user username from 201.155.95.199
Jan 25 23:16:04 office-desktop sshd[6730]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:04 office-desktop sshd[6730]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:06 office-desktop sshd[6730]: Failed password for invalid user username from 201.155.95.199 port 54452 ssh2
Jan 25 23:16:08 office-desktop sshd[6732]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:08 office-desktop sshd[6732]: Invalid user administrator from 201.155.95.199
Jan 25 23:16:08 office-desktop sshd[6732]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:08 office-desktop sshd[6732]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:10 office-desktop sshd[6732]: Failed password for invalid user administrator from 201.155.95.199 port 54528 ssh2
Jan 25 23:16:11 office-desktop sshd[6734]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:11 office-desktop sshd[6734]: Invalid user library from 201.155.95.199
Jan 25 23:16:11 office-desktop sshd[6734]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:11 office-desktop sshd[6734]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:13 office-desktop sshd[6734]: Failed password for invalid user library from 201.155.95.199 port 54618 ssh2
Jan 25 23:16:14 office-desktop sshd[6736]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:14 office-desktop sshd[6736]: Invalid user test from 201.155.95.199
Jan 25 23:16:14 office-desktop sshd[6736]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:14 office-desktop sshd[6736]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:15 office-desktop sshd[6736]: Failed password for invalid user test from 201.155.95.199 port 54691 ssh2
Jan 25 23:16:16 office-desktop sshd[6738]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:16 office-desktop sshd[6738]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:18 office-desktop sshd[6738]: Failed password for root from 201.155.95.199 port 54748 ssh2
Jan 25 23:16:19 office-desktop sshd[6740]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:19 office-desktop sshd[6740]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:21 office-desktop sshd[6740]: Failed password for root from 201.155.95.199 port 54818 ssh2
Jan 25 23:16:23 office-desktop sshd[6742]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:23 office-desktop sshd[6742]: Invalid user admin from 201.155.95.199
Jan 25 23:16:23 office-desktop sshd[6742]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:23 office-desktop sshd[6742]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:25 office-desktop sshd[6742]: Failed password for invalid user admin from 201.155.95.199 port 54903 ssh2
Jan 25 23:16:26 office-desktop sshd[6744]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:26 office-desktop sshd[6744]: Invalid user guest from 201.155.95.199
Jan 25 23:16:26 office-desktop sshd[6744]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:26 office-desktop sshd[6744]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:27 office-desktop sshd[6744]: Failed password for invalid user guest from 201.155.95.199 port 54976 ssh2
Jan 25 23:16:28 office-desktop sshd[6746]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:28 office-desktop sshd[6746]: Invalid user master from 201.155.95.199
Jan 25 23:16:28 office-desktop sshd[6746]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:28 office-desktop sshd[6746]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:31 office-desktop sshd[6746]: Failed password for invalid user master from 201.155.95.199 port 55036 ssh2
Jan 25 23:16:32 office-desktop sshd[6748]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:32 office-desktop sshd[6748]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:34 office-desktop sshd[6748]: Failed password for root from 201.155.95.199 port 55114 ssh2
Jan 25 23:16:35 office-desktop sshd[6750]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:35 office-desktop sshd[6750]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:37 office-desktop sshd[6750]: Failed password for root from 201.155.95.199 port 55181 ssh2
Jan 25 23:16:38 office-desktop sshd[6752]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:38 office-desktop sshd[6752]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:39 office-desktop sshd[6752]: Failed password for root from 201.155.95.199 port 55255 ssh2
Jan 25 23:16:40 office-desktop sshd[6754]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:40 office-desktop sshd[6754]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:42 office-desktop sshd[6754]: Failed password for root from 201.155.95.199 port 55313 ssh2
Jan 25 23:16:44 office-desktop sshd[6756]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:44 office-desktop sshd[6756]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:16:46 office-desktop sshd[6756]: Failed password for root from 201.155.95.199 port 55387 ssh2
Jan 25 23:16:47 office-desktop sshd[6758]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:47 office-desktop sshd[6758]: Invalid user admin from 201.155.95.199
Jan 25 23:16:47 office-desktop sshd[6758]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:47 office-desktop sshd[6758]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:49 office-desktop sshd[6758]: Failed password for invalid user admin from 201.155.95.199 port 55451 ssh2
Jan 25 23:16:50 office-desktop sshd[6760]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:50 office-desktop sshd[6760]: Invalid user admin from 201.155.95.199
Jan 25 23:16:50 office-desktop sshd[6760]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:50 office-desktop sshd[6760]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:51 office-desktop sshd[6760]: Failed password for invalid user admin from 201.155.95.199 port 55522 ssh2
Jan 25 23:16:52 office-desktop sshd[6762]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:52 office-desktop sshd[6762]: Invalid user admin from 201.155.95.199
Jan 25 23:16:52 office-desktop sshd[6762]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:52 office-desktop sshd[6762]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:54 office-desktop sshd[6762]: Failed password for invalid user admin from 201.155.95.199 port 55580 ssh2
Jan 25 23:16:56 office-desktop sshd[6764]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:56 office-desktop sshd[6764]: Invalid user admin from 201.155.95.199
Jan 25 23:16:56 office-desktop sshd[6764]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:16:56 office-desktop sshd[6764]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:16:57 office-desktop sshd[6764]: Failed password for invalid user admin from 201.155.95.199 port 55658 ssh2
Jan 25 23:16:58 office-desktop sshd[6766]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:16:58 office-desktop sshd[6766]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:00 office-desktop sshd[6766]: Failed password for root from 201.155.95.199 port 55716 ssh2
Jan 25 23:17:01 office-desktop CRON[6770]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 25 23:17:01 office-desktop CRON[6770]: pam_unix(cron:session): session closed for user root
Jan 25 23:17:01 office-desktop sshd[6768]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:01 office-desktop sshd[6768]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:04 office-desktop sshd[6768]: Failed password for root from 201.155.95.199 port 55789 ssh2
Jan 25 23:17:05 office-desktop sshd[6773]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:05 office-desktop sshd[6773]: Invalid user test from 201.155.95.199
Jan 25 23:17:05 office-desktop sshd[6773]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:05 office-desktop sshd[6773]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:07 office-desktop sshd[6773]: Failed password for invalid user test from 201.155.95.199 port 55864 ssh2
Jan 25 23:17:08 office-desktop sshd[6775]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:08 office-desktop sshd[6775]: Invalid user test from 201.155.95.199
Jan 25 23:17:08 office-desktop sshd[6775]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:08 office-desktop sshd[6775]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:09 office-desktop sshd[6775]: Failed password for invalid user test from 201.155.95.199 port 55940 ssh2
Jan 25 23:17:11 office-desktop sshd[6777]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:11 office-desktop sshd[6777]: Invalid user webmaster from 201.155.95.199
Jan 25 23:17:11 office-desktop sshd[6777]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:11 office-desktop sshd[6777]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:12 office-desktop sshd[6777]: Failed password for invalid user webmaster from 201.155.95.199 port 55989 ssh2
Jan 25 23:17:14 office-desktop sshd[6779]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:14 office-desktop sshd[6779]: Invalid user username from 201.155.95.199
Jan 25 23:17:14 office-desktop sshd[6779]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:14 office-desktop sshd[6779]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:15 office-desktop sshd[6779]: Failed password for invalid user username from 201.155.95.199 port 56048 ssh2
Jan 25 23:17:16 office-desktop sshd[6781]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:16 office-desktop sshd[6781]: Invalid user user from 201.155.95.199
Jan 25 23:17:16 office-desktop sshd[6781]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:16 office-desktop sshd[6781]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:18 office-desktop sshd[6781]: Failed password for invalid user user from 201.155.95.199 port 56106 ssh2
Jan 25 23:17:19 office-desktop sshd[6783]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:19 office-desktop sshd[6783]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:21 office-desktop sshd[6783]: Failed password for root from 201.155.95.199 port 56172 ssh2
Jan 25 23:17:23 office-desktop sshd[6785]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:23 office-desktop sshd[6785]: Invalid user admin from 201.155.95.199
Jan 25 23:17:23 office-desktop sshd[6785]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:23 office-desktop sshd[6785]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:24 office-desktop sshd[6785]: Failed password for invalid user admin from 201.155.95.199 port 56239 ssh2
Jan 25 23:17:26 office-desktop sshd[6787]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:26 office-desktop sshd[6787]: Invalid user test from 201.155.95.199
Jan 25 23:17:26 office-desktop sshd[6787]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:26 office-desktop sshd[6787]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:27 office-desktop sshd[6787]: Failed password for invalid user test from 201.155.95.199 port 56298 ssh2
Jan 25 23:17:29 office-desktop sshd[6789]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:29 office-desktop sshd[6789]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:31 office-desktop sshd[6789]: Failed password for root from 201.155.95.199 port 56352 ssh2
Jan 25 23:17:32 office-desktop sshd[6791]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:32 office-desktop sshd[6791]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:33 office-desktop sshd[6791]: Failed password for root from 201.155.95.199 port 56414 ssh2
Jan 25 23:17:34 office-desktop sshd[6793]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:34 office-desktop sshd[6793]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:17:36 office-desktop sshd[6793]: Failed password for root from 201.155.95.199 port 56454 ssh2
Jan 25 23:17:40 office-desktop sshd[6795]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:40 office-desktop sshd[6795]: Invalid user danny from 201.155.95.199
Jan 25 23:17:40 office-desktop sshd[6795]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:40 office-desktop sshd[6795]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:42 office-desktop sshd[6795]: Failed password for invalid user danny from 201.155.95.199 port 56495 ssh2
Jan 25 23:17:44 office-desktop sshd[6797]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:44 office-desktop sshd[6797]: Invalid user alex from 201.155.95.199
Jan 25 23:17:44 office-desktop sshd[6797]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:44 office-desktop sshd[6797]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:45 office-desktop sshd[6797]: Failed password for invalid user alex from 201.155.95.199 port 56586 ssh2
Jan 25 23:17:47 office-desktop sshd[6799]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:47 office-desktop sshd[6799]: Invalid user brett from 201.155.95.199
Jan 25 23:17:47 office-desktop sshd[6799]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:47 office-desktop sshd[6799]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:48 office-desktop sshd[6799]: Failed password for invalid user brett from 201.155.95.199 port 56625 ssh2
Jan 25 23:17:50 office-desktop sshd[6801]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:50 office-desktop sshd[6801]: Invalid user mike from 201.155.95.199
Jan 25 23:17:50 office-desktop sshd[6801]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:50 office-desktop sshd[6801]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:52 office-desktop sshd[6801]: Failed password for invalid user mike from 201.155.95.199 port 56662 ssh2
Jan 25 23:17:53 office-desktop sshd[6803]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:53 office-desktop sshd[6803]: Invalid user alan from 201.155.95.199
Jan 25 23:17:53 office-desktop sshd[6803]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:53 office-desktop sshd[6803]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:55 office-desktop sshd[6803]: Failed password for invalid user alan from 201.155.95.199 port 56702 ssh2
Jan 25 23:17:56 office-desktop sshd[6805]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:56 office-desktop sshd[6805]: Invalid user data from 201.155.95.199
Jan 25 23:17:56 office-desktop sshd[6805]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:17:56 office-desktop sshd[6805]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:17:58 office-desktop sshd[6805]: Failed password for invalid user data from 201.155.95.199 port 56739 ssh2
Jan 25 23:17:59 office-desktop sshd[6807]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:17:59 office-desktop sshd[6807]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=www-data
Jan 25 23:18:01 office-desktop sshd[6807]: Failed password for www-data from 201.155.95.199 port 56776 ssh2
Jan 25 23:18:02 office-desktop sshd[6809]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:02 office-desktop sshd[6809]: Invalid user http from 201.155.95.199
Jan 25 23:18:02 office-desktop sshd[6809]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:02 office-desktop sshd[6809]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:04 office-desktop sshd[6809]: Failed password for invalid user http from 201.155.95.199 port 56815 ssh2
Jan 25 23:18:05 office-desktop sshd[6811]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:05 office-desktop sshd[6811]: Invalid user httpd from 201.155.95.199
Jan 25 23:18:05 office-desktop sshd[6811]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:05 office-desktop sshd[6811]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:07 office-desktop sshd[6811]: Failed password for invalid user httpd from 201.155.95.199 port 56850 ssh2
Jan 25 23:18:08 office-desktop sshd[6813]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:08 office-desktop sshd[6813]: Invalid user pop from 201.155.95.199
Jan 25 23:18:08 office-desktop sshd[6813]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:08 office-desktop sshd[6813]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:10 office-desktop sshd[6813]: Failed password for invalid user pop from 201.155.95.199 port 56884 ssh2
Jan 25 23:18:11 office-desktop sshd[6815]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:11 office-desktop sshd[6815]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=nobody
Jan 25 23:18:13 office-desktop sshd[6815]: Failed password for nobody from 201.155.95.199 port 56917 ssh2
Jan 25 23:18:14 office-desktop sshd[6817]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:14 office-desktop sshd[6817]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=root
Jan 25 23:18:16 office-desktop sshd[6817]: Failed password for root from 201.155.95.199 port 56954 ssh2
Jan 25 23:18:17 office-desktop sshd[6819]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:17 office-desktop sshd[6819]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=backup
Jan 25 23:18:19 office-desktop sshd[6819]: Failed password for backup from 201.155.95.199 port 56991 ssh2
Jan 25 23:18:20 office-desktop sshd[6821]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:20 office-desktop sshd[6821]: Invalid user info from 201.155.95.199
Jan 25 23:18:20 office-desktop sshd[6821]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:20 office-desktop sshd[6821]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:22 office-desktop sshd[6821]: Failed password for invalid user info from 201.155.95.199 port 57020 ssh2
Jan 25 23:18:23 office-desktop sshd[6823]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:23 office-desktop sshd[6823]: Invalid user shop from 201.155.95.199
Jan 25 23:18:23 office-desktop sshd[6823]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:23 office-desktop sshd[6823]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:25 office-desktop sshd[6823]: Failed password for invalid user shop from 201.155.95.199 port 57048 ssh2
Jan 25 23:18:26 office-desktop sshd[6825]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:26 office-desktop sshd[6825]: Invalid user sales from 201.155.95.199
Jan 25 23:18:26 office-desktop sshd[6825]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:26 office-desktop sshd[6825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:28 office-desktop sshd[6825]: Failed password for invalid user sales from 201.155.95.199 port 57084 ssh2
Jan 25 23:18:29 office-desktop sshd[6827]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:29 office-desktop sshd[6827]: Invalid user web from 201.155.95.199
Jan 25 23:18:29 office-desktop sshd[6827]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:29 office-desktop sshd[6827]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:31 office-desktop sshd[6827]: Failed password for invalid user web from 201.155.95.199 port 57120 ssh2
Jan 25 23:18:32 office-desktop sshd[6829]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:32 office-desktop sshd[6829]: Invalid user www from 201.155.95.199
Jan 25 23:18:32 office-desktop sshd[6829]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:32 office-desktop sshd[6829]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:34 office-desktop sshd[6829]: Failed password for invalid user www from 201.155.95.199 port 57150 ssh2
Jan 25 23:18:35 office-desktop sshd[6831]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:35 office-desktop sshd[6831]: Invalid user wwwrun from 201.155.95.199
Jan 25 23:18:35 office-desktop sshd[6831]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:35 office-desktop sshd[6831]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:37 office-desktop sshd[6831]: Failed password for invalid user wwwrun from 201.155.95.199 port 57183 ssh2
Jan 25 23:18:42 office-desktop sshd[6833]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:42 office-desktop sshd[6833]: Invalid user adam from 201.155.95.199
Jan 25 23:18:42 office-desktop sshd[6833]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:42 office-desktop sshd[6833]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:44 office-desktop sshd[6833]: Failed password for invalid user adam from 201.155.95.199 port 57219 ssh2
Jan 25 23:18:46 office-desktop sshd[6835]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:46 office-desktop sshd[6835]: Invalid user stephen from 201.155.95.199
Jan 25 23:18:46 office-desktop sshd[6835]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:46 office-desktop sshd[6835]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:48 office-desktop sshd[6835]: Failed password for invalid user stephen from 201.155.95.199 port 57750 ssh2
Jan 25 23:18:53 office-desktop sshd[6837]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:53 office-desktop sshd[6837]: Invalid user richard from 201.155.95.199
Jan 25 23:18:53 office-desktop sshd[6837]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:53 office-desktop sshd[6837]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:18:55 office-desktop sshd[6837]: Failed password for invalid user richard from 201.155.95.199 port 58187 ssh2
Jan 25 23:18:59 office-desktop sshd[6839]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:18:59 office-desktop sshd[6839]: Invalid user george from 201.155.95.199
Jan 25 23:18:59 office-desktop sshd[6839]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:18:59 office-desktop sshd[6839]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:01 office-desktop sshd[6839]: Failed password for invalid user george from 201.155.95.199 port 59017 ssh2
Jan 25 23:19:02 office-desktop sshd[6841]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:02 office-desktop sshd[6841]: Invalid user john from 201.155.95.199
Jan 25 23:19:02 office-desktop sshd[6841]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:02 office-desktop sshd[6841]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:04 office-desktop sshd[6841]: Failed password for invalid user john from 201.155.95.199 port 59545 ssh2
Jan 25 23:19:08 office-desktop sshd[6843]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:08 office-desktop sshd[6843]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=news
Jan 25 23:19:10 office-desktop sshd[6843]: Failed password for news from 201.155.95.199 port 59573 ssh2
Jan 25 23:19:15 office-desktop sshd[6845]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:15 office-desktop sshd[6845]: Invalid user angel from 201.155.95.199
Jan 25 23:19:15 office-desktop sshd[6845]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:15 office-desktop sshd[6845]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:17 office-desktop sshd[6845]: Failed password for invalid user angel from 201.155.95.199 port 60339 ssh2
Jan 25 23:19:18 office-desktop sshd[6847]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:18 office-desktop sshd[6847]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=games
Jan 25 23:19:20 office-desktop sshd[6847]: Failed password for games from 201.155.95.199 port 60838 ssh2
Jan 25 23:19:25 office-desktop sshd[6849]: reverse mapping checking getaddrinfo for dsl-201-155-95-199.prod-empresarial.com.mx [201.155.95.199] failed - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:25 office-desktop sshd[6849]: Invalid user pgsql from 201.155.95.199
Jan 25 23:19:25 office-desktop sshd[6849]: pam_unix(sshd:auth): check pass; user unknown
Jan 25 23:19:25 office-desktop sshd[6849]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199 
Jan 25 23:19:27 office-desktop sshd[6849]: Failed password for invalid user pgsql from 201.155.95.199 port 32962 ssh2
Jan 25 23:19:37 office-desktop sshd[6851]: Address 201.155.95.199 maps to dsl-201-155-95-199.prod-empresarial.com.mx, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Jan 25 23:19:37 office-desktop sshd[6851]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=201.155.95.199  user=mail
Jan 25 23:19:39 office-desktop sshd[6851]: Failed password for mail from 201.155.95.199 port 33444 ssh2
Jan 26 00:17:01 office-desktop CRON[6853]: pam_unix(cron:session): session opened for user root by (uid=0)
```

This is crazy!! It means that somebody was trying to break into my computer and tried invalid usernames or passwords. What should I do? I'm terrified.

Please help

P.S. My Firefox keeps crashing now and I've never had any problems before. Does this mean my PC is hacked already? <crying>

Don't worry about CRON in the log. They're cron jobs. Worry about failed logins on sshd. I have public ssh server and it is always hit by bots. Secure your ssh server by installing denyhosts.
```

sudo apt-get install denyhosts

```

Configure the file /etc/denyhosts.conf. Its easy to configure the values. The default ones shud instantly block brute-force attempts and ban the IP permanently to access via ssh. Banned IPs will be in a text file /etc/hosts.deny

There is also a section in the beginning of denyhosts.conf to ban the IP for ALL services/ports in your machine, not just ssh.

Don't need to panic or bring in a new drive. Always check the auth.log this way for ssh attempts:
```

cat /var/log/auth.log | grep sshd

```
And worry about lines that contain 'Accepted password' like the one below:
```

Jan 29 08:44:50 cloud1-desktop sshd[3561]: Server listening on :: port 22.
Jan 29 09:07:03 cloud1-desktop sshd[4989]: [COLOR="Red"]Accepted password for Daniel from 208.67.222.222 port 37746 ssh2[/COLOR]
Jan 29 09:07:03 cloud1-desktop sshd[4989]: pam_unix(sshd:session): [COLOR="Red"]session opened[/COLOR] for user [COLOR="Red"]Daniel[/COLOR] by (uid=0)

```

Understood?

---

### Post by gtdaqua on 2009-01-29
You definitely don't have anything to worry about. I parsed your log for the keyword "password" and there no "Accepted" entries. Below is the parsed output of YOUR log. 

```

$ cat sam-log | grep password
Jan 25 23:13:56 office-desktop sshd[6656]: Failed password for invalid user staff from 201.155.95.199 port 50721 ssh2
Jan 25 23:13:59 office-desktop sshd[6658]: Failed password for invalid user sales from 201.155.95.199 port 50871 ssh2
Jan 25 23:14:05 office-desktop sshd[6660]: Failed password for invalid user recruit from 201.155.95.199 port 50984 ssh2
Jan 25 23:14:09 office-desktop sshd[6662]: Failed password for invalid user alias from 201.155.95.199 port 51173 ssh2
Jan 25 23:14:15 office-desktop sshd[6664]: Failed password for invalid user office from 201.155.95.199 port 51284 ssh2
Jan 25 23:14:19 office-desktop sshd[6666]: Failed password for invalid user samba from 201.155.95.199 port 51505 ssh2
Jan 25 23:14:22 office-desktop sshd[6668]: Failed password for invalid user tomcat from 201.155.95.199 port 51610 ssh2
Jan 25 23:14:26 office-desktop sshd[6670]: Failed password for invalid user webadmin from 201.155.95.199 port 51733 ssh2
Jan 25 23:14:29 office-desktop sshd[6672]: Failed password for invalid user spam from 201.155.95.199 port 51838 ssh2
Jan 25 23:14:32 office-desktop sshd[6674]: Failed password for invalid user virus from 201.155.95.199 port 51941 ssh2
Jan 25 23:14:35 office-desktop sshd[6676]: Failed password for invalid user cyrus from 201.155.95.199 port 52019 ssh2
Jan 25 23:14:39 office-desktop sshd[6678]: Failed password for invalid user oracle from 201.155.95.199 port 52117 ssh2
Jan 25 23:14:42 office-desktop sshd[6680]: Failed password for invalid user michael from 201.155.95.199 port 52231 ssh2
Jan 25 23:14:46 office-desktop sshd[6682]: Failed password for invalid user ftp from 201.155.95.199 port 52329 ssh2
Jan 25 23:14:50 office-desktop sshd[6684]: Failed password for invalid user test from 201.155.95.199 port 52416 ssh2
Jan 25 23:14:53 office-desktop sshd[6686]: Failed password for invalid user webmaster from 201.155.95.199 port 52518 ssh2
Jan 25 23:14:55 office-desktop sshd[6688]: Failed password for invalid user postmaster from 201.155.95.199 port 52600 ssh2
Jan 25 23:14:59 office-desktop sshd[6690]: Failed password for invalid user postfix from 201.155.95.199 port 52674 ssh2
Jan 25 23:15:02 office-desktop sshd[6692]: Failed password for invalid user postgres from 201.155.95.199 port 52770 ssh2
Jan 25 23:15:05 office-desktop sshd[6694]: Failed password for invalid user paul from 201.155.95.199 port 52856 ssh2
Jan 25 23:15:08 office-desktop sshd[6696]: Failed password for root from 201.155.95.199 port 52936 ssh2
Jan 25 23:15:11 office-desktop sshd[6698]: Failed password for invalid user guest from 201.155.95.199 port 53017 ssh2
Jan 25 23:15:15 office-desktop sshd[6700]: Failed password for invalid user admin from 201.155.95.199 port 53100 ssh2
Jan 25 23:15:17 office-desktop sshd[6702]: Failed password for invalid user linux from 201.155.95.199 port 53191 ssh2
Jan 25 23:15:21 office-desktop sshd[6704]: Failed password for invalid user user from 201.155.95.199 port 53263 ssh2
Jan 25 23:15:25 office-desktop sshd[6706]: Failed password for invalid user david from 201.155.95.199 port 53373 ssh2
Jan 25 23:15:28 office-desktop sshd[6708]: Failed password for invalid user web from 201.155.95.199 port 53457 ssh2
Jan 25 23:15:31 office-desktop sshd[6710]: Failed password for invalid user apache from 201.155.95.199 port 53527 ssh2
Jan 25 23:15:34 office-desktop sshd[6712]: Failed password for invalid user pgsql from 201.155.95.199 port 53618 ssh2
Jan 25 23:15:37 office-desktop sshd[6714]: Failed password for invalid user mysql from 201.155.95.199 port 53693 ssh2
Jan 25 23:15:40 office-desktop sshd[6716]: Failed password for invalid user info from 201.155.95.199 port 53782 ssh2
Jan 25 23:15:44 office-desktop sshd[6718]: Failed password for invalid user tony from 201.155.95.199 port 53859 ssh2
Jan 25 23:15:47 office-desktop sshd[6720]: Failed password for invalid user core from 201.155.95.199 port 53956 ssh2
Jan 25 23:15:51 office-desktop sshd[6722]: Failed password for invalid user newsletter from 201.155.95.199 port 54040 ssh2
Jan 25 23:15:54 office-desktop sshd[6724]: Failed password for invalid user named from 201.155.95.199 port 54132 ssh2
Jan 25 23:15:59 office-desktop sshd[6726]: Failed password for invalid user visitor from 201.155.95.199 port 54215 ssh2
Jan 25 23:16:03 office-desktop sshd[6728]: Failed password for invalid user ftpuser from 201.155.95.199 port 54358 ssh2
Jan 25 23:16:06 office-desktop sshd[6730]: Failed password for invalid user username from 201.155.95.199 port 54452 ssh2
Jan 25 23:16:10 office-desktop sshd[6732]: Failed password for invalid user administrator from 201.155.95.199 port 54528 
Jan 25 23:16:13 office-desktop sshd[6734]: Failed password for invalid user library from 201.155.95.199 port 54618 ssh2
Jan 25 23:16:15 office-desktop sshd[6736]: Failed password for invalid user test from 201.155.95.199 port 54691 ssh2
Jan 25 23:16:18 office-desktop sshd[6738]: Failed password for root from 201.155.95.199 port 54748 ssh2
Jan 25 23:16:21 office-desktop sshd[6740]: Failed password for root from 201.155.95.199 port 54818 ssh2
Jan 25 23:16:25 office-desktop sshd[6742]: Failed password for invalid user admin from 201.155.95.199 port 54903 ssh2
Jan 25 23:16:27 office-desktop sshd[6744]: Failed password for invalid user guest from 201.155.95.199 port 54976 ssh2
Jan 25 23:16:31 office-desktop sshd[6746]: Failed password for invalid user master from 201.155.95.199 port 55036 ssh2
Jan 25 23:16:34 office-desktop sshd[6748]: Failed password for root from 201.155.95.199 port 55114 ssh2
Jan 25 23:16:37 office-desktop sshd[6750]: Failed password for root from 201.155.95.199 port 55181 ssh2
Jan 25 23:16:39 office-desktop sshd[6752]: Failed password for root from 201.155.95.199 port 55255 ssh2
Jan 25 23:16:42 office-desktop sshd[6754]: Failed password for root from 201.155.95.199 port 55313 ssh2
Jan 25 23:16:46 office-desktop sshd[6756]: Failed password for root from 201.155.95.199 port 55387 ssh2
Jan 25 23:16:49 office-desktop sshd[6758]: Failed password for invalid user admin from 201.155.95.199 port 55451 ssh2
Jan 25 23:16:51 office-desktop sshd[6760]: Failed password for invalid user admin from 201.155.95.199 port 55522 ssh2
Jan 25 23:16:54 office-desktop sshd[6762]: Failed password for invalid user admin from 201.155.95.199 port 55580 ssh2
Jan 25 23:16:57 office-desktop sshd[6764]: Failed password for invalid user admin from 201.155.95.199 port 55658 ssh2
Jan 25 23:17:00 office-desktop sshd[6766]: Failed password for root from 201.155.95.199 port 55716 ssh2
Jan 25 23:17:04 office-desktop sshd[6768]: Failed password for root from 201.155.95.199 port 55789 ssh2
Jan 25 23:17:07 office-desktop sshd[6773]: Failed password for invalid user test from 201.155.95.199 port 55864 ssh2
Jan 25 23:17:09 office-desktop sshd[6775]: Failed password for invalid user test from 201.155.95.199 port 55940 ssh2
Jan 25 23:17:12 office-desktop sshd[6777]: Failed password for invalid user webmaster from 201.155.95.199 port 55989 ssh2
Jan 25 23:17:15 office-desktop sshd[6779]: Failed password for invalid user username from 201.155.95.199 port 56048 ssh2
Jan 25 23:17:18 office-desktop sshd[6781]: Failed password for invalid user user from 201.155.95.199 port 56106 ssh2
Jan 25 23:17:21 office-desktop sshd[6783]: Failed password for root from 201.155.95.199 port 56172 ssh2
Jan 25 23:17:24 office-desktop sshd[6785]: Failed password for invalid user admin from 201.155.95.199 port 56239 ssh2
Jan 25 23:17:27 office-desktop sshd[6787]: Failed password for invalid user test from 201.155.95.199 port 56298 ssh2
Jan 25 23:17:31 office-desktop sshd[6789]: Failed password for root from 201.155.95.199 port 56352 ssh2
Jan 25 23:17:33 office-desktop sshd[6791]: Failed password for root from 201.155.95.199 port 56414 ssh2
Jan 25 23:17:36 office-desktop sshd[6793]: Failed password for root from 201.155.95.199 port 56454 ssh2
Jan 25 23:17:42 office-desktop sshd[6795]: Failed password for invalid user danny from 201.155.95.199 port 56495 ssh2
Jan 25 23:17:45 office-desktop sshd[6797]: Failed password for invalid user alex from 201.155.95.199 port 56586 ssh2
Jan 25 23:17:48 office-desktop sshd[6799]: Failed password for invalid user brett from 201.155.95.199 port 56625 ssh2
Jan 25 23:17:52 office-desktop sshd[6801]: Failed password for invalid user mike from 201.155.95.199 port 56662 ssh2
Jan 25 23:17:55 office-desktop sshd[6803]: Failed password for invalid user alan from 201.155.95.199 port 56702 ssh2
Jan 25 23:17:58 office-desktop sshd[6805]: Failed password for invalid user data from 201.155.95.199 port 56739 ssh2
Jan 25 23:18:01 office-desktop sshd[6807]: Failed password for www-data from 201.155.95.199 port 56776 ssh2
Jan 25 23:18:04 office-desktop sshd[6809]: Failed password for invalid user http from 201.155.95.199 port 56815 ssh2
Jan 25 23:18:07 office-desktop sshd[6811]: Failed password for invalid user httpd from 201.155.95.199 port 56850 ssh2
Jan 25 23:18:10 office-desktop sshd[6813]: Failed password for invalid user pop from 201.155.95.199 port 56884 ssh2
Jan 25 23:18:13 office-desktop sshd[6815]: Failed password for nobody from 201.155.95.199 port 56917 ssh2
Jan 25 23:18:16 office-desktop sshd[6817]: Failed password for root from 201.155.95.199 port 56954 ssh2
Jan 25 23:18:19 office-desktop sshd[6819]: Failed password for backup from 201.155.95.199 port 56991 ssh2
Jan 25 23:18:22 office-desktop sshd[6821]: Failed password for invalid user info from 201.155.95.199 port 57020 ssh2
Jan 25 23:18:25 office-desktop sshd[6823]: Failed password for invalid user shop from 201.155.95.199 port 57048 ssh2
Jan 25 23:18:28 office-desktop sshd[6825]: Failed password for invalid user sales from 201.155.95.199 port 57084 ssh2
Jan 25 23:18:31 office-desktop sshd[6827]: Failed password for invalid user web from 201.155.95.199 port 57120 ssh2
Jan 25 23:18:34 office-desktop sshd[6829]: Failed password for invalid user www from 201.155.95.199 port 57150 ssh2
Jan 25 23:18:37 office-desktop sshd[6831]: Failed password for invalid user wwwrun from 201.155.95.199 port 57183 ssh2
Jan 25 23:18:44 office-desktop sshd[6833]: Failed password for invalid user adam from 201.155.95.199 port 57219 ssh2
Jan 25 23:18:48 office-desktop sshd[6835]: Failed password for invalid user stephen from 201.155.95.199 port 57750 ssh2
Jan 25 23:18:55 office-desktop sshd[6837]: Failed password for invalid user richard from 201.155.95.199 port 58187 ssh2
Jan 25 23:19:01 office-desktop sshd[6839]: Failed password for invalid user george from 201.155.95.199 port 59017 ssh2
Jan 25 23:19:04 office-desktop sshd[6841]: Failed password for invalid user john from 201.155.95.199 port 59545 ssh2
Jan 25 23:19:10 office-desktop sshd[6843]: Failed password for news from 201.155.95.199 port 59573 ssh2
Jan 25 23:19:17 office-desktop sshd[6845]: Failed password for invalid user angel from 201.155.95.199 port 60339 ssh2
Jan 25 23:19:20 office-desktop sshd[6847]: Failed password for games from 201.155.95.199 port 60838 ssh2
Jan 25 23:19:27 office-desktop sshd[6849]: Failed password for invalid user pgsql from 201.155.95.199 port 32962 ssh2
Jan 25 23:19:39 office-desktop sshd[6851]: Failed password for mail from 201.155.95.199 port 33444 ssh2

```

Time to install denyhosts and keep those bots away!

---

### Post by bmwman on 2009-01-29
Thank you all for the feedback. I guess I should have been more prepared. I thought OpenSSH is secure by default but I guess there're ways to improve it even more. I think I will wipe the PC and reload it. I just use it to surf the net and remote in from work so I don't have to back up anything.Then I will try changing all the options for using keys and denyhosts. I'll report back when I'm back up and running. Thanks again to all

---

### Post by dagriff on 2009-01-29
OpenSSH is only as secure as you make it.

If you are **never** going to log into that machine remotely then you may wish to turn off sshd completely.

```

sudo /etc/init.d/ssh stop
sudo rm /etc/rc2.d/S16ssh

```

If you are wanting the ability to log in remotely then you can start to think about some additional security methods, such as:

[LIST]
[*]Using keys rather than passwords
[*]Changing the default port
[*]DenyHosts (as mentioned before)
[*]Restricting who can log in via sshd
[*]Restricting where they can log in from
[/LIST]

---

### Post by cb951303 on 2009-01-29
> **bmwman said:**
> Thank you all for the feedback. I guess I should have been more prepared. I thought OpenSSH is secure by default but I guess there're ways to improve it even more. I think I will wipe the PC and reload it. I just use it to surf the net and remote in from work so I don't have to back up anything.Then I will try changing all the options for using keys and denyhosts. I'll report back when I'm back up and running. Thanks again to all

as you see from logs openssh is pretty secure. in the end they couldn't pentrate to your system.

---

### Post by jerome1232 on 2009-01-29
> **bmwman said:**
> Thank you all for the feedback. I guess I should have been more prepared. I thought OpenSSH is secure by default but I guess there're ways to improve it even more. I think I will wipe the PC and reload it. I just use it to surf the net and remote in from work so I don't have to back up anything.Then I will try changing all the options for using keys and denyhosts. I'll report back when I'm back up and running. Thanks again to all

Honestly Openssh is very secure by default, as long as your account passwords are good passwords. There's no need to wipe the pc it never got compromised.

---

### Post by bmwman on 2009-01-29
I can change my password and create a weird named user for login. I need to read some more on how to restrict only ONE user that I desginate to be able to login and use key instead of password, of coarse the denyhosts as well.

---

### Post by argie on 2009-01-30
Coincidentally, I did the same thing just yesterday (locked down my ssh server). A few tips are mentioned on the Ubuntu Wiki here: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by bodhi.zazen on 2009-01-30
> **bmwman said:**
> I can change my password and create a weird named user for login. I need to read some more on how to restrict only ONE user that I desginate to be able to login and use key instead of password, of coarse the denyhosts as well.

a few modifications to iptables is all you need.

See :

[http://bodhizazen.net/beginners/Firewall/index.html](http://bodhizazen.net/beginners/Firewall/index.html)

I know it is a long an ugly page, I am working on it as time allows :twisted:

Scroll down to the tips section "Block Brute Force attempts (SSH or other connections)"

And use ssh keys.

Deny hosts is nice as well, as is fail2ban.

---

### Post by bmwman on 2009-02-01
I just installed DenyHost and I'm configuring it. Here is what changes I did:

```
# To block all services for the offending host:
BLOCK_SERVICE = ALL
```

 ```
DENY_THRESHOLD_INVALID: block each host after the number of failed login 
# attempts has exceeded this value.  This value applies to invalid
# user login attempts (eg. non-existent user accounts)
#
DENY_THRESHOLD_INVALID = 2
```
```

# DENY_THRESHOLD_VALID: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to valid
# user login attempts (eg. user accounts that exist in /etc/passwd) except
# for the "root" user
#
DENY_THRESHOLD_VALID = 2
```
The rest is the defaults. Is there anything else that I should change in DenyHost?

P.S. I Also followed this guide:[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")and did the recommended changes to my config file. I also generated my RSA keys **id_rsa** and **id_rsa.pub**. Now I don't understand how can I use those from my other Ubuntu computer at work or with my XP/Putty laptop? The guide is a little confusing at that point.

---

### Post by cjacobsen on 2009-02-02
> **gtdaqua said:**
> Time to install denyhosts and keep those bots away!

Or Fail2Ban. I *my*opinion Fail2Ban is a better service than denyhost. However for the guy who started the post: get a move on it and secure your server!:o

---

