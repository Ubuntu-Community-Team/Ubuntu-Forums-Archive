---
title: "RK Hunter warnings seem concerning?"
date: 2014-05-21
forum: Security
---

### Post by vik2 on 2014-05-21
Just ran RK Hunter and got these, should I be worried?

1./usr/bin/GET   Warning: The file '/usr/bin/GET' exists on the system, but it is not$

2. Checking for packet capturing applications      [ Warning ]
[11:50:24] Warning: Process '/sbin/dhclient' (PID 831) is listening on the netw$

3. Checking running processes for deleted files    [ Warning ]
[11:50:10] Warning: The following processes are using deleted files:
[11:50:10]          Process: /sbin/init    PID: 1    File: /var/log/upstart/mod$
[11:50:10]          Process: /sbin/init    PID: 2207    File: /home/pcone/.cach$
[11:50:10]          Process: /usr/lib/chromium-browser/chromium-browser    PID:$
[11:50:10]          Process: /usr/lib/chromium-browser/chromium-browser    PID:$
[11:50:10]          Process: /usr/lib/chromium-browser/chromium-browser    PID:$
[11:50:10]          Process: /usr/lib/chromium-browser/chromium-browser    PID:$
[11:50:10]          Process: /usr/lib/chromium-browser/chromium-browser    PID:$
[11:50:10]          Process: /usr/bin/python3.4    PID: 4814    File: /var/lib/$
[11:50:10]          Process: /usr/bin/gnome-terminal    PID: 4856    File: /tmp$

4. Info: Starting test name 'passwd_changes'
[11:50:25]   Checking for passwd file changes                [ Warning ]
[11:50:25] Warning: User 'snort' has been added to the passwd file.
[11:50:25]
[11:50:25] Info: Starting test name 'group_changes'
[11:50:25]   Checking for group file changes                 [ Warning ]
[11:50:25] Warning: Group 'snort' has been added to the group file.

System checks summary
[11:50:32] =====================
[11:50:32]
[11:50:32] File properties checks...
[11:50:32] Files checked: 137
[11:50:32] Suspect files: 5
[11:50:32]
[11:50:32] Rootkit checks...
[11:50:32] Rootkits checked : 292
[11:50:32] Possible rootkits: 0
Applications checks...
[11:50:32] Applications checked: 3
[11:50:32] Suspect applications: 0

---

### Post by cariboo on 2014-05-22
Did you run:

```
rkhunter --propupd
```

before running a scan? If not your results are invalid, for more info, open a terminal and run:

```
man rkhunter
```

---

### Post by vik2 on 2014-05-22
Entered rkhunter  --propupd and re ran RK Hunter, now received the following, 

/usr/bin/unhide.rb  [ Warning ]

Performing malware checks
Checking running processes for deleted files [ Warning ]

Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

---

### Post by unspawn on 2014-05-23
> **vik2 said:**
> Entered rkhunter  --propupd and re ran RK Hunter, now received the following,   /usr/bin/unhide.rb  [ Warning ]  Performing malware checks Checking running processes for deleted files [ Warning ]  Performing filesystem checks     Checking /dev for suspicious file types                  [ Warning ]     Checking for hidden files and directories                [ Warning ] Check your rkhunter.log file for clues, check RKH's README and FAQ for details and don't use "unhide.rb" but 'unhide" package.

---

