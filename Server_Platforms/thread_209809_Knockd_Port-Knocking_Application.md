---
title: "Knockd Port-Knocking Application"
date: 2006-07-05
forum: Server Platforms
---

### Post by lordfoul on 2006-07-05
How does a port knocker work?

    * we install the port knocker daemon on our server (knockd)
    * we configure some port sequences (tcp, udp, or both), and the appropriate actions for each sequence.
    * the knockd daemon will be running in the background, at low level passively on the network interface. It is completely stealth and it will not open any ports on the server.
    * once it will see a port sequence it will run the configured action for the sequence.

[http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/#more-85](http://www.ducea.com/2006/07/05/how-to-safely-connect-from-anywhere-to-your-closed-linux-firewall/#more-85)

---

### Post by falcon15500 on 2006-07-07
Port knocking is one of those contentious issues.  Some people think it is awesome and some think it is stupid.  Personally?  I think you should use it if you want to, but understand its limitations.
  
The main argument against it, is that it is a form of security through obscurity - which most security experts are against.  It can lead to a false sense of security.  However your port knock sequences are vulnerable to observation by others, who can then imitate them.

But on the other hand...  Realistically, who would be prepared to do that?  They would have to suspect port knocking first.

falc

---

### Post by Gouki on 2006-08-20
IMHO, port knocking is another layer of security. No matter what people say, it will AT LEAST, keep our logs clean from all those script kiddies trying brute-force against FTP and SSH.

> **falcon15500 said:**
> However your port knock sequences are vulnerable to observation by others, who can then imitate them.


The author of Knockd is/was aware of that problem and created the 'one-time-sequencee', which is similar to one-time-passwords.

```
  [options]
        logfile = /var/log/knockd.log

  [opencloseSMTP]
        one_time_sequences = /etc/knockd/smtp_sequences
        seq_timeout        = 15
        tcpflags           = fin,!ack
        start_command      = /usr/sbin/iptables -A input -s %IP% -p tcp --dport 25 -j ACCEPT
        cmd_timeout        = 5
        stop_command       = /usr/sbin/iptables -D INPUT -s %IP% -p tcp --dport 25 -j ACCEPT
```

[Knockd Wiki](http://www.zeroflux.org/cgi-bin/cvstrac.cgi/knock/wiki).

---

