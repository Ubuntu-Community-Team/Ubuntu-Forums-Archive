---
title: "libperl.so.5.18.2 Error login kern.log file"
date: 2014-05-07
forum: Server Platforms
---

### Post by mahi_nix on 2014-05-07
Hi Guys,

I upgraded my Ubuntu server on 14.04 trust OS. It has Amanda backup server 3.3.3 running on it and after upgradation i am facing below error message in syslog and kern.log files and amanda dont able to execute the amanda backup Job.

```
ERROR: 
 kernel: [ 5481.559464] amcheck-device[11231]: segfault at c ip 00007f4960156846 sp 00007fff17c0b290 error 4 in libperl.so.5.18.2[7f496008d000+180000]
```

Can anyone help me to sorted out the issue.

Its urgent issue as my Amanda backup server cant start amanda backup jobs and backup job fails everyday.

I will appriciate your help.

Regards,
Mahipal

---

### Post by kladiv on 2014-10-25
Hello,
i got same problem and it's related to the following Perl lib path:
- /usr/local/share/perl/X.XX.X/Amanda
- /usr/local/share/perl/X.XX.X/auto

In amanda client package these folders are not included so Action Plan i made is:

IF AMANDA SERVER OS TYPE/VERSION is different from Amanda Client:
1. remove amanda-backup-client
2. install amanda-backup-server
3. tar /usr/local/share/perl/X.XX.X/Amanda and /usr/local/share/perl/X.XX.X/auto
4. remove amanda-backup-server 
5. install amanda-backup-client
6. untar packages you create on Step3 into /usr/local/share/perl/X.XX.X/ or /usr/local/lib/site_perl/

IF AMANDA SERVER OS TYPE/VERSION is the same of Amanda Client:
1. tar /usr/local/share/perl/X.XX.X/Amanda and /usr/local/share/perl/X.XX.X/auto
2. upload tar archives on Amanda client
3. untar packages into /usr/local/share/perl/X.XX.X/ or /usr/local/lib/site_perl/ of the amanda client

For multiple clients you can use this procedure 1 time, then use the same tar archives (OS dependent)

Cya!
Claudio

---

