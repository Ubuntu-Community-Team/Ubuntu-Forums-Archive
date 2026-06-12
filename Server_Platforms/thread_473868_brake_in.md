---
title: "brake in"
date: 2007-06-14
forum: Server Platforms
---

### Post by Geir102 on 2007-06-14
Hi I have alott of people trying to brake in to my server. Im running the 7.04 whit ssh. I found someting in my auth.log. Im new at this but it looks bad. Is this a sucessfull brake inn?

Jun 12 06:25:02 linux su[4207]: Successful su for nobody by root
Jun 12 06:25:02 linux su[4207]: + ??? root:nobody
Jun 12 06:25:02 linux su[4207]: (pam_unix) session opened for user nobody by (uid=0)
Jun 12 06:25:02 linux su[4207]: (pam_unix) session closed for user nobody
Jun 12 06:25:02 linux su[4211]: Successful su for nobody by root
Jun 12 06:25:02 linux su[4211]: + ??? root:nobody
Jun 12 06:25:02 linux su[4211]: (pam_unix) session opened for user nobody by (uid=0)
Jun 12 06:25:02 linux su[4211]: (pam_unix) session closed for user nobody
Jun 12 06:25:02 linux su[4213]: Successful su for nobody by root
Jun 12 06:25:02 linux su[4213]: + ??? root:nobody
Jun 12 06:25:02 linux su[4213]: (pam_unix) session opened for user nobody by (uid=0)
Jun 12 06:25:11 linux su[4213]: (pam_unix) session closed for user nobody

I have no user named nobody. Only one user and that is me

---

### Post by eentonig on 2007-06-14
Probably it's some sort of cron job. or a program that needs root access.

These are hacking attempts on my ssh running box. Makes me remember, I need to change my public port for ssh.
> Jun 14 13:37:36 tigra sshd[24521]: Failed password for invalid user adm from 82.229.114.177 port 40310 ssh2
Jun 14 13:37:36 tigra sshd[24525]: Disabling protocol version 1. Could not load host key
Jun 14 13:37:36 tigra sshd[24525]: Invalid user adm from 82.229.114.177
Jun 14 13:37:36 tigra sshd[24525]: (pam_unix) check pass; user unknown
Jun 14 13:37:36 tigra sshd[24525]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=sar45-1-82-229-114-
177.fbx.proxad.net 
Jun 14 13:37:38 tigra sshd[24525]: Failed password for invalid user adm from 82.229.114.177 port 41253 ssh2
Jun 14 13:37:38 tigra sshd[24527]: Disabling protocol version 1. Could not load host key
Jun 14 13:37:39 tigra sshd[24527]: Invalid user adm from 82.229.114.177
Jun 14 13:37:39 tigra sshd[24527]: (pam_unix) check pass; user unknown
Jun 14 13:37:39 tigra sshd[24527]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=sar45-1-82-229-114-
177.fbx.proxad.net 
Jun 14 13:37:42 tigra sshd[24527]: Failed password for invalid user adm from 82.229.114.177 port 41621 ssh2
Jun 14 13:37:42 tigra sshd[24531]: Disabling protocol version 1. Could not load host key
Jun 14 13:37:43 tigra sshd[24531]: Invalid user adm from 82.229.114.177
Jun 14 13:37:43 tigra sshd[24531]: (pam_unix) check pass; user unknown
Jun 14 13:37:43 tigra sshd[24531]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=sar45-1-82-229-114-
177.fbx.proxad.net 
Jun 14 13:37:45 tigra sshd[24531]: Failed password for invalid user adm from 82.229.114.177 port 42574 ssh2
Jun 14 13:37:46 tigra sshd[24535]: Disabling protocol version 1. Could not load host key
Jun 14 13:37:46 tigra sshd[24535]: Invalid user adm from 82.229.114.177
Jun 14 13:37:46 tigra sshd[24535]: (pam_unix) check pass; user unknown
Jun 14 13:37:46 tigra sshd[24535]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=sar45-1-82-229-114-
177.fbx.proxad.net 

---

### Post by Geir102 on 2007-06-14
Okay but there shod not by any cron jobs running on the server i think

---

### Post by Chayak on 2007-06-14
Your server is fine.  It's simply your system doing housekeeping tasks.  nobody is a system user in linux/unix that's used by quite a few processes.

---

### Post by Geir102 on 2007-06-14
Ok thanks a lott:-) Trying to learn all this. A littel scared off rootkits and stuff like that

---

