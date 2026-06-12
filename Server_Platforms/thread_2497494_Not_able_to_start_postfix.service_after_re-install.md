---
title: "Not able to start postfix.service after re-installing"
date: 2024-05-07
forum: Server Platforms
---

### Post by eclay on 2024-05-07
I was trying to setup postfix/dovecot and was having issues getting both to work.  My thought was to uninstall and then reinstall fresh and give it another try.  After using 'apt -y purge postfix'  Then trying to reinstall using 'apt install postfix'  The service fails to start.  Using 'systemctl start postfix' shows the following.

 systemctl status postfix
&#9679; postfix.service - Postfix Mail Transport Agent
     Loaded: loaded (/usr/lib/systemd/system/postfix.service; enabled; preset: enabled)
     Active: active (exited) since Tue 2024-05-07 16:40:48 MDT; 10min ago
       Docs: man:postfix(1)
    Process: 7151 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 7151 (code=exited, status=0/SUCCESS)
        CPU: 1ms


May 07 16:40:48 server.domain.com systemd[1]: Starting postfix.service - Postfix Mail Transport Agent...
May 07 16:40:48 server.domain.com systemd[1]: Finished postfix.service - Postfix Mail Transport Agent.

Not getting anything useful when running 'journalctl -xeu postfix.service'.  Just says that a start job has finished.

I am able to start it using the postfix commmand.
  postfix -c /etc/postfix startpostfix/postfix-script: starting the Postfix mail system

  ps aux|grep postfix
root        7654  0.0  0.0  42848  4764 ?        Ss   16:54   0:00 /usr/lib/postfix/sbin/master -w
postfix     7655  0.0  0.0  43300  7936 ?        S    16:54   0:00 pickup -l -t unix -u -c
postfix     7656  0.0  0.0  43340  7936 ?        S    16:54   0:00 qmgr -l -t unix -u

I can now connect to port 25.
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

Anyone have any ideas what might be preventing this from starting?  I believe that postfix runs in a chroot.  So I also try disabling that in /etc/postfix/master.cf.

---

### Post by eclay on 2024-05-08
I ran a similar test on ubuntu 22.04 by installing postfix and seeing that it was running.  I then did a 'apt purge postfix' followed by removing /etc/postfix and /var/spool/mail.  I then reinstalled postfix and the service shows running.  This seems to be an issue with 24.04 only.

root@ubuntu3:~# ps aux|grep postfix
root        1597  0.0  0.2  41232  4804 ?        Ss   16:46   0:00 /usr/lib/postfix/sbin/master -w
postfix     1599  0.0  0.3  41560  6988 ?        S    16:46   0:00 pickup -l -t unix -u -c
postfix     1600  0.0  0.3  41604  6996 ?        S    16:46   0:00 qmgr -l -t unix -u
root        1756  0.0  0.1   6480  2236 pts/1    S+   16:48   0:00 grep --color=auto postfix
root@ubuntu3:~# systemctl status postfix
&#9679; postfix.service - Postfix Mail Transport Agent
     Loaded: loaded (/lib/systemd/system/postfix.service; enabled; vendor preset: enabled)
     Active: active (exited) since Wed 2024-05-08 16:46:39 UTC; 1min 58s ago
       Docs: man:postfix(1)
    Process: 1598 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 1598 (code=exited, status=0/SUCCESS)
        CPU: 1ms


May 08 16:46:39 ubuntu3 systemd[1]: Starting Postfix Mail Transport Agent...
May 08 16:46:39 ubuntu3 systemd[1]: Finished Postfix Mail Transport Agent.

---

### Post by eclay on 2024-05-09
Found the solution.  I compared the /var/spool/postfix on my system with another ubuntu 24.04 system that postfix was installed and running on.  I found that serveral directories/files where missing.  I noticed that on my test system, I could uninstall postfix and reinstall it.  I also noticed that ssl-cert and libnsl2 packages where installing/uninstalling on the working system.  It looks like my server wasn't uninstalling ssl-cert package when I uninstalled postfix.  So when I delted the directories and then tried to reinstall things where missing.

solution:
apt purge postfix ssl-cert libnsl2
apt install postfix

---

