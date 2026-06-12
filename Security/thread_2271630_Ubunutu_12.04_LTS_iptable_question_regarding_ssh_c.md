---
title: "Ubunutu 12.04 LTS iptable question regarding ssh connection"
date: 2015-03-31
forum: Security
---

### Post by edwin22 on 2015-03-31
This is my first question in the forum and i believe already a strange one :-) How do i block access to and SSH server once the First SSH connection is established?  What i try to achieve is this:  I have build a GNS3 server on ubuntu 12.04 LTS As only 1 person at the time can work on the labs with real cisco switches attached to them, i must be able to allow only the first incoming SSH from any source. (yes i know not so secure but its on the private corporate lan so i am not to worried there :-)  I cannot figure out how to do this, i was looking at iptables and have configured something like the below here, but it only allows the first person to start 1 connection, it does not prevent the second person from starting his "first" session:  -A INPUT -p tcp -m tcp --dport 22 -m connlimit --connlimit-above 1 -j REJECT -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT  So my question is: How can i make sure that, when 1 person is connected, the second person (from different pc) cannot connect?  I appreciate any help!

---

### Post by SeijiSensei on 2015-03-31
Try setting "MaxSessions" to one in /etc/ssh/sshd_config. Alternatively you could limit the authorized users to one account with the "AllowUsers" parameter.  See "man sshd_config" for details.

---

### Post by edwin22 on 2015-04-01
Hi SeijiSensei,

I am afraid its not that simple, what i want to do is limit ssh connections to 1, when a second one (from different ip address but with same username) comes in, the server should block it because there is already one ssh connection established. the Maxsessions will only work for the same connection meaning if the first one logs in, the maxsessions setting will only limit the sessions the first one can make on his connection, it will not affect a second persons ability to establish a new ssh connection, and that's just what i want.

So in short, i want to use only 1 user account, and only 1 ssh connection at the time can exist ( from any source), when he next person tries to log in with the same useraccount, it should be dropped because their is already an established ssh connection.
I cannot find how to do thins anywhere.. :-(

I appreciate all the help

---

### Post by SeijiSensei on 2015-04-02
Probably because it's not possible. You'll have to find a way to keep the sshd daemon from spawning additional listeners when a request comes in.  A quick Google search doesn't turn up anything.

One method might be to "wrap" the SSH service with [xinetd]("https://help.ubuntu.com/community/SSH/OpenSSH/Advanced#Running_from_.28x.29inetd").  It has an "instances" parameter that can limit the number of simultaneous connections.

---

### Post by Doug S on 2015-04-02
I think your objective might be achievable indirectly via the /etc/security/limits.conf file. I tried it on one of my test servers. I did this:```
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4
[COLOR=#ff0000]doug             hard    maxlogins       3[/COLOR]

# End of file
``` And once I get to here:```
doug@test-smy:~$ w
 09:05:30 up 16 min,  3 users,  load average: 0.10, 0.22, 0.29
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
doug     tty1                      08:55    9:38   2.74s  1.52s -bash
doug     pts/0    doug-xps2.smythi 09:01    4:02   1.44s  1.44s -bash
doug     pts/1    doug-xps2.smythi 09:02    2.00s  1.57s  0.05s w
```When I attempt to add another ssh session, it starts, but then kicks me out. The following was observed in /var/log/auth.log:```
Apr  2 09:02:30 test-smy sshd[1413]: pam_limits(sshd:session): Too many logins (max 3) for doug
```

---

### Post by SeijiSensei on 2015-04-02
That's a great solution, Doug!

---

### Post by edwin22 on 2015-04-03
Seijisensei,Doug,

Thanks!

i will try this out this weekend and get back too you,both solutions seem interresting!
xinetd concept is new to me ( i am stil green behind the ears on linux, lot to learn!) but it does seem to offer some interresting options like the fail banner possibility and such..i have to read-up!

you guys rock! :)

---

### Post by SeijiSensei on 2015-04-04
Xinetd is not used very often any more, since most services are now designed to run as daemons.  But it still offers a variety of useful features for access control like consulting /etc/hosts.allow and /etc/hosts.deny.

---

### Post by edwin22 on 2015-04-05
Hi Doug, SeijiSensei,

The limits.conf under /etc/security did the trick!

Thanks a million for your help! :-)

Regards,
Edwin

---

