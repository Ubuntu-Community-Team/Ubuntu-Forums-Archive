---
title: "OpenSSH does not log failed authentication attempts with PublicKeys"
date: 2010-02-15
forum: Security
---

### Post by nizuri on 2010-02-15
My server runs Karmic Koala and OpenSSH. (the version you get from apt)
I am using public keys and no passwords. When I try to connect with a correct username and a invalid keypair the login fails but I don't get a log message telling me so! Only this:
```
Feb 16 03:49:26 hybris sshd[3180]: Connection from 192.168.1.31 port 49277
```

Using invalid usernames and successful logins both result in meaningful messages, so does using a wrong password, why doesn't a failed key-attempt?

I googled it and came across two similar problems:
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/304598](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/304598)
[https://bugzilla.mindrot.org/show_bug.cgi?id=1468](https://bugzilla.mindrot.org/show_bug.cgi?id=1468)

The solution was upping the LogLevel from INFO to VERBOSE, but if I try that I still don't get a appropriate message. I even tried out DEBUG, but still no luck. (Apart from making it really hard to read the logfile...)

Am I the only one with this problem? I find it hard to believe that nobody is missing this message. An attacker could try thousands of keys without anyone ever noticing - including fail2ban.

---

### Post by Bachstelze on 2010-02-16
Same behaviour on my two servers (one FreeBSD and one Debian). This is probably not a bug but normal default behaviour.

---

### Post by bodhi.zazen on 2010-02-16
> **nizuri said:**
> Am I the only one with this problem? I find it hard to believe that nobody is missing this message. An attacker could try thousands of keys without anyone ever noticing - including fail2ban.

Which is why I use iptables. Why install another service such as fail2ban or deny hosts when iptables is perfectly capable (both of logging and blocking these attempts) ?

And yes, my iptables rules work with keys or passwords =)

In terms of using thousands of keys, good luck on that. You would first need to somehow duplicate my private key, then get the user name, then get the password. Nothing is impossible, but cracking my server by using thousands of keys is highly improbable.

---

### Post by nizuri on 2010-02-16
Thanks to both of you. :)
> Same behaviour on my two servers (one FreeBSD and one Debian). This is probably not a bug but normal default behaviour.
I'm afraid so. Im going to file a bug report anyway. Especially as it worked with OpenSSH 5.0, at least with a high enough LogLevel.

> Which is why I use iptables. Why install another service such as fail2ban or deny hosts when iptables is perfectly capable (both of logging and blocking these attempts) ?

And yes, my iptables rules work with keys or passwords =)
Hm, sounds good. How do you manage that? Block every IP that tries to connect too often in a given timeframe? (That's the only way I found using iptables.) 
It looks like it's no possible for iptables to differentiate between failed and successful attempts.
On the other hand it's not very likely that I or scripts of mine try to connect in such short intervals anyway. :D

Something like those two scripts? 

script in /etc/network/if-down.d/
```
#!/bin/bash
[ "${METHOD}" != loopback ] || exit 0
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP
```

script in /etc/network/if-up.d/
```
#!/bin/bash
[ "${METHOD}" != loopback ] || exit 0
/sbin/iptables -D INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
/sbin/iptables -D INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP
```

[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/)

> In terms of using thousands of keys, good luck on that. You would first need to somehow duplicate my private key, then get the user name, then get the password. Nothing is impossible, but cracking my server by using thousands of keys is highly improbable.
Of course you are right, that's not very likely. It just bugged me, that I'd have no way of telling if it would indeed happen. Or at least not a very obvious way.

---

### Post by bodhi.zazen on 2010-02-16
Those rules look fine, be sure to test them.

You are correct, iptables tracks NEW connections, but of course, for the most part,

multiple failed attempts == multiple new connections.

The only thing you may run across is scp, sftp, or other file transfers (SVN over SSH), each file may a new connection, so if you do a lot of transfers liberalize the number of new connections. If you are using keys and strong passwords you can always allow 10-20 new connections if needed.

---

### Post by nizuri on 2010-02-16
Oh, I completely  forgot about scp and git. I wrote a script that copies a backup of all my repos over scp, but I wanted to rewrite it anyway, so that it tars all those small blobs into a single archive  before the transfer.
But that still leaves git itself. I'll have to try if it triggers the rules, when cloning large repos. I hope it's a single connection.

Edit: I compiled 5.3p1 and the problem still exists, so I filed a bug-report. (I wonder why one still gets 5.1p1 with the sources in apt-get.)  
Both git and scp only open one connection, so at least that works. I set the iptables hitcount to 15 and kept 6 attempts for fail2ban. 

Thanks again. :)

---

