---
title: "Check rootkits warning"
date: 2010-05-01
forum: Security
---

### Post by jslick on 2010-05-01
I have two rootkit checks giving me warnings:  chkrootkit says
```

Checking `lkm'...                                           You have     2 process hidden for readdir command
You have     2 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

```
How do I find these processes and what they do?

Also, rkhunter says:
```

Checking for hidden files and directories                [ Warning ]

Checking application versions...

    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]
    Checking version of OpenSSH                              [ Warning ]

```

I run Kubuntu 9.10 64-bit
openSSH (without root logins)
I recently ran an update
I recently installed Kubuntu 10.04 on another partition
I ran chkrootkit probably the day before without these warnings.

How do I find out if there's a trojan on my computer or if this is a false positive?

I have my SSH server stopped for now.

---

### Post by unspawn on 2010-05-01
> **jslick said:**
> ```

Checking `lkm'...                                           You have     2 process hidden for readdir command
You have     2 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

```
Please see the on-line Chkrootkit FAQ. It has an entry about false positives due to transient processes.


> **jslick said:**
> How do I find these processes and what they do?
If they are not hidden processes then you could use Chkrootkits 'chkproc' or regular tools like 'ps' or 'lsof' listing verbosely or use a script to "walk" the /proc tree. Since transient processes have the habit of not showing up when you're checking these tools won't find anything. If you need to trace them then you'll have to log system calls (see for example Auditd or GRSecurity process logging functions).



> **jslick said:**
> 
```

Checking for hidden files and directories                [ Warning ]

```
Check rkhunter.log for details.


> **jslick said:**
> 
```

    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]
    Checking version of OpenSSH                              [ Warning ]

```
Check rkhunter.log for details. Probably could do with some white-listing.


* For efficiency sake please note most common questions are already answered in the documentation and FAQ RKH comes with and in the rkhunter-users mailing list archives.

---

### Post by jslick on 2010-05-01
Here are warnings in my rkhunter.log:
```
[00:35:42]   Checking for hidden files and directories       [ Warning ]
[00:35:43] Warning: Hidden directory found: /etc/.java
[00:35:43] Warning: Hidden directory found: /dev/.udev
[00:35:43] Warning: Hidden directory found: /dev/.initramfs
[00:35:43] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[00:35:43] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text

```
These seem pretty harmless, yes?

```

[00:36:10]   Checking version of GnuPG                       [ Warning ]
[00:36:10] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.

```

```
[00:36:10]   Checking version of OpenSSL                     [ Warning ]
[00:36:10] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.

```

```

[00:36:10]   Checking version of OpenSSH                     [ Warning ]
[00:36:10] Warning: Application 'sshd', version '5.1p1', is out of date, and possibly a security risk.

```

This was shortly after a system update.  Might this just be that rkhunter looks for openssh versions newer than those in ubuntu's repository?

---

### Post by unspawn on 2010-05-02
> **jslick said:**
> These seem pretty harmless, yes? (..) Might this just be that rkhunter looks for openssh versions newer than those in ubuntu's repository?
Yes and yes.

---

