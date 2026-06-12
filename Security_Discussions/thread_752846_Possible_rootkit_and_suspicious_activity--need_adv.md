---
title: "Possible rootkit and suspicious activity--need advice"
date: 2008-04-12
forum: Security Discussions
---

### Post by escape on 2008-04-12
A run of rkhunter -c on an updated hardy heron (desktop version) on my laptop gives me hash mismatches on /sbin/init, /sbin/runlevel, /usr/sbin/unhide, and /usr/sbin/unhide-linux26. The last two bring up warnings because I think rkhunter.dat does not know about these binaries (they are part of the "unhide" package which checks for hidden processes) even after an rkhunter --update; the first two, however, worry me. I've messed around with sysv-rc-conf, but I don't think this should have any effect on these binaries. rkhunter log shows these hash mismatches:

[23:34:16] Warning: The file properties have changed:
[23:34:16]          File: /sbin/init
[23:34:16]          Current hash: f69357049a0bec86919683514d4795fc6a960912
[23:34:16]          Stored hash : 6eb21ea2b644ceb21450a50d58aaba73e8b601a4
[23:34:16]          Current inode: 3352246    Stored inode: 3352213
[23:34:16]          Current size: 89604    Stored size: 89492
[23:34:16]          Current file modification time: 1207921804
[23:34:17]          Stored file modification time : 1193869005

[23:34:18] Warning: The file properties have changed:
[23:34:18]          File: /sbin/runlevel
[23:34:18]          Current hash: 6606daaeb55fea588edf010a1dd36738e52b1ab8
[23:34:18]          Stored hash : 5de21a4dc0bcc33d56b30f43388d42ecc5e88776
[23:34:18]          Current inode: 3352191    Stored inode: 3352298
[23:34:18]          Current file modification time: 1207921804
[23:34:19]          Stored file modification time : 1193869005

Also, I am not (but should have been) running syslog; I have recently restarted it. I am pretty sure I manually disabled this as part of cutting down startup time. Browsing the tail of syslog before removing it from startup as well as the new entries from just restarting it bring up other issues. In auth.log I get these PAM errors:

Mar 27 16:15:01 ascalon sudo: PAM unable to dlopen(/lib/security/pam_foreground.so)
Mar 27 16:15:01 ascalon sudo: PAM [error: /lib/security/pam_foreground.so: cannot open shared object file: No such file or directory]

Apr 11 23:47:25 ascalon sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 11 23:47:25 ascalon sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

I'm guessing this could be from development instability, but nobody mentions these files on the forum. So this also seems a little suspicious.

More damning is that chkrootkit thinks I have an LKM (loadable kernel module?) trojan because some processes are hidden: 

Checking `lkm'... You have     5 process hidden for readdir command
You have     7 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

The unhide command also reveals a number of hidden kernel(?)-level (I got MANY PID hits for sys, through getsid and sched_getparam, although in the end it oddly only says one hidden process was found) and user-level (less here, only four PIDS, does not report any actual hidden processes though...) "processes". I haven't run unhide before on any other machine, notably any known clean machine, so I'm a bit troubled by this as I don't know if it's normal. 

As far as potential vulnerabilities, I've been primarily running 2.6.24.7-generic as I haven't updated grub to point to newer kernels yet. However, I don't know of any vulnerabilities on 24.7 (such as vmsplice, etc..). I can duplicate these results on the newer(est) 2.6.24.16-generic. I am not firewalled on the laptop but am running behind a router with no ports forwarded to this machine. sshd is not running. root has been !'d in shadow. I like to think the 18 character, 4 class password I have for my own account, which is the only non *'d or !'d account in shadow and which has requires a password for sudo, is somewhat secure. w gives expected output. nmap does not show any open ports. I use betas of Firefox 3 with noscript, so that attack vector is at best minimal. I should add I am the only user of this laptop, I do not share it with others. It is actually very rare for the laptop to be more than a few feet from me, so I think a local exploit is somewhat unlikely. I haven't used anything but stock repositories, and I don't recall installing anything apart from what is in these repositories.

Perhaps the init, runlevel, and hidden process problems are false positives. If someone can either confirm they get similar hash issues on an updated hardy heron for init and runlevel or give me a copy of their binaries I'd be very grateful. Also, any insight on the PAM errors, hidden processes, or general advice at this point, is appreciated as well. A reformat would not be very hard, but I'd prefer to avoid one.

Thanks!

edit: posting this as I go; looks like PAM stuff is normal: 
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/198714](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/198714)
[http://www.linuxforums.org/forum/servers/77756-swat-pam-problem-wont-read-passwds-tdbsam.html](http://www.linuxforums.org/forum/servers/77756-swat-pam-problem-wont-read-passwds-tdbsam.html)

---

### Post by The Tronyx on 2008-04-12
My first question would be, what ports do you have forwarded to the internet?

---

### Post by escape on 2008-04-12
> **2point0 said:**
> My first question would be, what ports do you have forwarded to the internet?

Err, what do you mean? On the router no port forwarding is done to the laptop. I don't know how you would forward ports from the laptop to the internet though.

---

### Post by The Tronyx on 2008-04-12
Check your PMs please.

---

