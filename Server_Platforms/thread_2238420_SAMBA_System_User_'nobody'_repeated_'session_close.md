---
title: "SAMBA: System User 'nobody' repeated 'session closed' in /var/log/auth.log"
date: 2014-08-07
forum: Server Platforms
---

### Post by jrollf on 2014-08-07
I was running 10.04 LTS, a power brown out corrupted the boot drive, so about two weeks ago I reset up my server with 14.04 LTS (same hardware).  It seems to be running fairly well.. until now.

Primary server tasks:
[LIST]
[*]Samba Server 
[*]SSH 
[*]VSFTP 
[*]Linux File Shares 
[*]Backup important files to CrashPlan Backup Service. 
[/LIST]

Over the last couple of days I've noticed the following showing up in my /var/log/auth.log

...
Aug  7 18:25:23 Rollf smbd[9422]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:26:23 Rollf smbd[9426]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:27:23 Rollf smbd[9430]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:28:20 Rollf smbd[9434]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:29:24 Rollf smbd[9439]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:30:24 Rollf smbd[9443]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:31:24 Rollf smbd[9445]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:32:24 Rollf smbd[9450]: pam_unix(samba:session): session closed for user nobody
Aug  7 18:33:24 Rollf smbd[9453]: pam_unix(samba:session): session closed for user nobody
...

Note that I never see a 'session opened for user nobody', always 'session closed'.

This repeats roughly every 60 seconds for several hours and then quits for a while and starts again.  Other than the system user 'nobody' auth.log records no successful log ins other than mine (there is only one user name on the system).  I've not encountered this before and I'm at a loss of what to look at to solve the issue... or is it really an issue?  Other then the messages in auth.log, I wouldn't know there are any issues, everything seems to be working fine.

Since the server is connected to the internet through my gateway, I run the following security measures:
[LIST]
[*]fail2ban 
[*]Denyhosts -also set to autoban ip address via iptables (the new fork that is still being supported) 
[*]ClamAV (to protect my windows clients) 
[/LIST]

Note: In addition to the standard server setup I have installed xfce because the backup service I use (CrashPlan) does not offer a command line interface for configuration of the background service. The system boots directly to command line, I only launch xfce if I have to change my backup service configuration.

Thanks!

---

### Post by Arronical on 2015-02-17
Did you ever find out what was causing this? I've got the same behaviour, and can't seem to get any answers any where!

---

