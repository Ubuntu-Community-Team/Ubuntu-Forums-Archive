---
title: "Deleted file warnings - RKHunter"
date: 2015-07-17
forum: Security
---

### Post by k-shane on 2015-07-17
A perennial question i have yet to find an answer to.

RKHunter - Spits out warnings such as

```
[14:26:54] Info: Starting test name 'deleted_files'
[14:26:58]   Checking running processes for deleted files    [ Warning ]
[14:26:58] Warning: The following processes are using deleted files:
[14:26:58]          Process: /usr/sbin/mysqld    PID: 694    File: /tmp/ib1Q8Pni
[14:26:58]          Process: /usr/sbin/apache2    PID: 880    File: /run/lock/apache2/ssl-cache.875
[14:26:58]          Process: /usr/sbin/apache2    PID: 887    File: /run/lock/apache2/ssl-cache.875
[14:26:58]          Process: /usr/sbin/apache2    PID: 888    File: /run/lock/apache2/ssl-cache.875
[14:26:58]          Process: /usr/sbin/apache2    PID: 889    File: /run/lock/apache2/ssl-cache.875
[14:26:58]          Process: /usr/sbin/apache2    PID: 890    File: /run/lock/apache2/ssl-cache.875
[14:26:58]          Process: /usr/sbin/apache2    PID: 891    File: /run/lock/apache2/ssl-cache.875
```

Every forum seems to tell the person to read their logs (where these came from), update RKHunter (on latest version already) or run sudo rkhunter --propupd
( done already)

So -it would be good to find a fix as it is a question which seems to have had no decent answer to it. 

Why post it here? It seems to affect Ubuntu servers a lot more than others by the volume of questions on the net.

Basically the message is only a warning, it says the process is using a deleted file and a seach for the file mentioned would show it doesn't exist. 
The warning can be disabled in the .conf file - but it is obviously there for a reason so turning it off is not a wise choice. If it was then it should be depricated or removed by default. 

The warning does not go away after a fresh restart of the server.  shutdown - r now, sudo rkhunter --propupd, sudo rkhunter -c --enable all --disable none

Theoretically restarting the server should mean all file andles are dropped. If a process is referencing a file that is deletedafter a freesh restart then it must be opening that file, and it is being deleted after it is referenced,. that would point to a bug in the OS or the process. as this seems to affect multiple applications I would suggest it is an OS issue or a spurious RKhunter warning. 

Any thoughts?

Server is latest LTS, hardend to the hilt (fail2ban, rkhunter, vnas, ssl security key on an obfuscated ssl port, latest updates, scanned daily, cleared by two x virus checkers and with the latest version of apache, php, suhosin  and mysql running etc etc etc.)

 It has no presence on the internet as its dns is not registered and it has no websites hosted on it yet.

---

### Post by todd_schlichter on 2015-11-22
I have the exact same output with a clean LAMP install and fully updated RKHunter.

---

### Post by Habitual on 2015-11-23
> **k-shane said:**
> The warning does not go away after a fresh restart of the server.  shutdown - r now, sudo rkhunter --propupd, sudo rkhunter -c --enable all --disable noneI don't know the answer to your initial query, but I wanted to advise you that this routine in that order is not the best way to do  a scan for rootkits because when you run ```
rkhunter --propupd
``` you tell rkhunter that **everything on the system is OK**, when in fact it may not be.

and you said "latest". the 'latest' is 1.4.3 and the repo is at 1.4.2

---

### Post by unspawn on 2015-11-30
> **k-shane said:**
> The warning can be disabled in the .conf file - but it is obviously there for a reason so turning it off is not a wise choice. If it was then it should be depricated or removed by default. The warning is there to notify you of just that: processes using deleted files. As RKH aims to be a generic useful post-op tool we can't cater for every exception and white list it by default. In general this means anyone deploying RKH without understanding what it can (and can not) do and not customizing it for use isn't running it like it's intended. It's not a fire-and-forget thing. In short: investigate, verify, then white list. Also please note "--propupd" should obviously only be run after you've verified things. Else it's just Ostrich tactics...

---

