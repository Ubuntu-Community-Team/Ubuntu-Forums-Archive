---
title: "Netstat - Is someone else sshed in?"
date: 2010-07-12
forum: Security
---

### Post by oomar on 2010-07-12
logan@loganncserver:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.0.105:2222      s15405413.onlineh:49873 ESTABLISHED
tcp        0      0 192.168.0.105:2222      s15405413.onlineh:49887 ESTABLISHED
tcp        0      0 192.168.0.105:ssh       host-xx-xx-xxx-xx:42006 ESTABLISHED


logan@loganncserver:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.0.105:ssh       fw1.itt.com:52127       ESTABLISHED
tcp        0      0 192.168.0.105:ssh       host-xx-xx-xxx-xx:42006 ESTABLISHED


ok above are some of the results from a run of Netstat. I have x'd out some of the numbers in the bottom SSH session because those are my IP address and legitimate. The first listed was only there for a few seconds then went away.... so was that someone attempting to log in but failing?

the second, the fw1.itt.com connection has been there for a while. Is this someone SSHed into my server? 


Come on guys help me out.


EDIT: As of now the connection has gone away. I still want to know if my system was compromised. If it was I'm re-installing and going with SSH keys next time.

---

### Post by cdenley on 2010-07-12
Well, those were both connections to your SSH server, but not necessarily authenticated. Just because a host appears to have a connection every time you run netstat does not necessarily mean it is always the same connection, and is authenticated. They could simply be re-connecting continuously, attempting to authenticate with different passwords.

If you want to see who has authenticated successfully, search through /var/log/auth.log. That is what that log file is for. If you use a strong password, haven't set a password for root, and haven't compromised your password in some other way, then you shouldn't have a problem. It couldn't hurt to install fail2ban or denyhosts, though. Also, I suggest using the "-n" option with netstat to get actual IP's, not hostnames.

---

### Post by CharlesA on 2010-07-12
Definitely check /var/log/auth.log for any successful (and failed) authentications.

If you haven't locked SSH down and it's open to the internet on port 22, you'll get a bunch of hits from bots trying to get in by using commonly used passwords.

---

### Post by denver on 2010-07-12
A usefull command which shows you who is connected to a pty or tty is:

```

gabi@rossak:~$ w
 17:25:40 up  3:29, 11 users,  load average: 0.68, 0.51, 0.33
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
gabi     tty7     :0               13:56    3:29m  9:15   0.60s gnome-session
gabi     pts/0    :0.0             14:58    2:27m  0.21s  0.01s ssh root@192.168.0.1

```

As long as you have a long and random password set on your user account, you should be safe. If you are paranoid about brute force, you can always install CSF/LFD. It has built in brute force detection and prevention:

[http://www.configserver.com/cp/csf.html](http://www.configserver.com/cp/csf.html)

---

### Post by bodhi.zazen on 2010-07-12
> **denver said:**
> A usefull command which shows you who is connected to a pty or tty is:

```

gabi@rossak:~$ w
 17:25:40 up  3:29, 11 users,  load average: 0.68, 0.51, 0.33
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
gabi     tty7     :0               13:56    3:29m  9:15   0.60s gnome-session
gabi     pts/0    :0.0             14:58    2:27m  0.21s  0.01s ssh root@192.168.0.1

```As long as you have a long and random password set on your user account, you should be safe. If you are paranoid about brute force, you can always install CSF/LFD. It has built in brute force detection and prevention:

[http://www.configserver.com/cp/csf.html](http://www.configserver.com/cp/csf.html)

Brute forcing is an issue, IMO, and is probably the second most common crack on these forum (a long way behind VNC).

If you are running a ssh server, and connect on the internet, you should, IMO, at a minimum use keys and disable passwords. That will put a quick end to brute force attempts.

At that point, if you are still paranoid, either configure iptables to drop these attempts or consider an additional service such as denyhosts or fail2ban.

If you understand iptables it is a "one liner" (well 3 lines) but it is, IMO, more secure then adding another service.

On the other hand, fail2ban is very effective and covers more then just ssh.

---

### Post by oomar on 2010-07-12
Alright so I'm still going through the log file but so far it looks like my password was good enough to keep them out.

I've disabled logins by password, I've disabled root login, in fact I made it so that only the User I use can log in. I'm using non-standard ports and I'm looking into denyhosts/fail2ban. 

I've also added a little message for before they login.... Maybe that will scare away some of the more pathetic script kiddies.

I'm also looking into port knocking so that there aren't even any ports for them to open.

EDIT: Nevermind. Not looking at port knocking. It has too many security vulnerabilities.

---

