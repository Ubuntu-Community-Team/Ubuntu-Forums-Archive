---
title: "Removed Winbind... ADS Problems"
date: 2010-09-21
forum: Server Platforms
---

### Post by dudemanbubba on 2010-09-21
I believe I made a significant mistake.  I had been getting routine errors in my syslog file such as:

Sep 21 07:14:29 ls1 winbindd[5827]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend.

I did some looking and found that this could be a problem using winbind.  I am not using winbind as part  of my samba configuration.  So I removed it to see if it would clean up my issues.

Well, I am a newbie and set this server up about 8 months ago to replace file storage on my network.  I went through some processes to join our domain using ADS and had grand ideas of having it all integrated with our Windows domain.  I ran out of time, luck and patience and ended up abandoning the integration through samba and removed all of the ADS, winbind, etc. and have been using simple shares.  Once I apt-get removed winbind I have been unable to log into the server at all.  The network shares appear to be functioning properly but I have no way of getting into the server to reinstall winbind that I can tell.

Is there anyway to put winbind back remotely?  I have tried logging in at the server, through ssh.  For some reason, I have access through my Webmin web console.  Is there a way to put it back through that?

Here is a sample of the auth log file errors I am getting now:

Sep 21 07:47:57 ls1 sshd[6796]: pam_unix(sshd:auth): auth could not identify password for [administrator] Sep 21 07:47:57 ls1 sshd[6796]: Failed password for administrator from 192.168.0.36 port 1594 ssh2 Sep 21 07:48:15 ls1 sshd[6798]: reverse mapping checking getaddrinfo for jasons-laptop [192.168.0.36] failed - POSSIBLE BREAK-IN ATTEMPT! Sep 21 07:48:15 ls1 sshd[6798]: PAM unable to dlopen(/lib/security/pam_winbind.so) Sep 21 07:48:15 ls1 sshd[6798]: PAM [error: /lib/security/pam_winbind.so: cannot open shared object file: No such file or directory] Sep 21 07:48:15 ls1 sshd[6798]: PAM adding faulty module: /lib/security/pam_winbind.so Sep 21 07:48:17 ls1 sshd[6798]: pam_unix(sshd:auth): auth could not identify password for [jsadmin] Sep 21 07:48:17 ls1 sshd[6798]: Failed password for jsadmin from 192.168.0.36 port 1596 ssh2 Sep 21 07:48:22 ls1 sshd[6798]: pam_unix(sshd:auth): auth could not identify password for [jsadmin] Sep 21 07:48:22 ls1 sshd[6798]: Failed password for jsadmin from 192.168.0.36 port 1596 ssh2 Sep 21 07:48:43 ls1 sshd[6801]: reverse mapping checking getaddrinfo for jasons-laptop [192.168.0.36] failed - POSSIBLE BREAK-IN ATTEMPT! Sep 21 07:48:43 ls1 sshd[6801]: PAM unable to dlopen(/lib/security/pam_winbind.so) Sep 21 07:48:43 ls1 sshd[6801]: PAM [error: /lib/security/pam_winbind.so: cannot open shared object file: No such file or directory] Sep 21 07:48:43 ls1 sshd[6801]: PAM adding faulty module: /lib/security/pam_winbind.so Sep 21 07:48:45 ls1 sshd[6801]: pam_unix(sshd:auth): auth could not identify password for [root] Sep 21 07:48:45 ls1 sshd[6801]: Failed password for root from 192.168.0.36 port 1597 ssh2 Sep 21 08:09:01 ls1 CRON[7099]: PAM unable to dlopen(/lib/security/pam_winbind.so) Sep 21 08:09:01 ls1 CRON[7099]: PAM [error: /lib/security/pam_winbind.so: cannot open shared object file: No such file or directory] Sep 21 08:09:01 ls1 CRON[7099]: PAM adding faulty module: /lib/security/pam_winbind.so Sep 21 08:09:01 ls1 CRON[7099]: pam_unix(cron:session): session opened for user root by (uid=0) Sep 21 08:09:01 ls1 CRON[7099]: pam_mkhomedir(cron:session): unknown option: unmask=0022 Sep 21 08:09:01 ls1 CRON[7099]: pam_unix(cron:session): session closed for user root.

Obviously, I am in crisis mode by my own doing.  I am limited in the office the next couple of days and I am looking for any assistance anyone can offer.

Thanks.

---

### Post by dudemanbubba on 2010-09-21
I had not seen the package install function in Webmin, but it was there.  I used it to reinstall winbind and all appears to be functional!

Later!

---

