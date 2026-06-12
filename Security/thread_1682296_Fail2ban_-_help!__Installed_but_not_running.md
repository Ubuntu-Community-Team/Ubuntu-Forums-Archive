---
title: "Fail2ban - help!  Installed but not running?"
date: 2011-02-05
forum: Security
---

### Post by wolfgang.rumpf on 2011-02-05
Hoping you can help me out....I installed fail2ban from the Ubuntu Software Center (Ubuntu 10.10) and everything seemed to go fine.  But when I try to access the client I get this output:

```
wolfgang@Culture:/var/log$ fail2ban-client status
ERROR  Unable to contact server. Is it running?
```

So I try to start it, and get this:

```
wolfgang@Culture:/var/log$ fail2ban-client start
WARNING 'findtime' not defined in 'apache-noscript'. Using default value
WARNING 'findtime' not defined in 'pam-generic'. Using default value
WARNING 'findtime' not defined in 'vsftpd'. Using default value
WARNING 'findtime' not defined in 'xinetd-fail'. Using default value
WARNING 'findtime' not defined in 'named-refused-udp'. Using default value
WARNING 'findtime' not defined in 'ssh-ddos'. Using default value
WARNING 'findtime' not defined in 'apache-multiport'. Using default value
WARNING 'findtime' not defined in 'apache-overflows'. Using default value
WARNING 'findtime' not defined in 'couriersmtp'. Using default value
WARNING 'findtime' not defined in 'wuftpd'. Using default value
WARNING 'findtime' not defined in 'ssh'. Using default value
WARNING 'findtime' not defined in 'postfix'. Using default value
WARNING 'findtime' not defined in 'sasl'. Using default value
WARNING 'findtime' not defined in 'apache'. Using default value
WARNING 'findtime' not defined in 'courierauth'. Using default value
WARNING 'findtime' not defined in 'proftpd'. Using default value
WARNING 'findtime' not defined in 'named-refused-tcp'. Using default value
2011-02-04 21:57:57,534 fail2ban.server : INFO   Starting Fail2ban v0.8.4
2011-02-04 21:57:57,534 fail2ban.server : INFO   Starting in daemon mode
ERROR  Could not start server. Maybe an old socket file is still present. Try to remove /var/run/fail2ban/fail2ban.sock. If you used fail2ban-client to start the server, adding the -x option will do it

```
So as suggested I tried adding the -x and got the same result.  Now, when I look inside the action.d directory, I don't see any .conf files for the above services:

```
wolfgang@Culture:/etc/fail2ban/action.d$ ls
complain.conf   ipfw.conf                iptables-multiport-log.conf  mail-whois.conf         sendmail.conf
dshield.conf    iptables-allports.conf   iptables-new.conf            mail-whois-lines.conf   sendmail-whois.conf
hostsdeny.conf  iptables.conf            mail-buffered.conf           mynetwatchman.conf      sendmail-whois-lines.conf
ipfilter.conf   iptables-multiport.conf  mail.conf                    sendmail-buffered.conf  shorewall.conf
```

I'm not sure what went wrong during the install - the server does appear to be running (I see it in the list when I check with [COLOR=Red]ps -el | grep fail[/COLOR]) and there is a logfile for it in[COLOR=Red] /var/log/fail2ban.log[/COLOR] but there haven't been any entries in the log since it was initialized, which is suspicious since I've had brute force attacks every day or two (not anything serious, but serious enough to want me to get fail2ban running).

One more thing, from the fail2ban log:

```
2011-02-04 21:38:44,802 fail2ban.actions.action: ERROR  iptables -D INPUT -p tcp
 -m multiport --dports ssh -j fail2ban-ssh
iptables -F fail2ban-ssh
iptables -X fail2ban-ssh returned 100
```

Any help you can provide would be awesome - thanks!

---

### Post by chengas123 on 2011-02-11
I've run into the same issue.  Does anyone have any ideas?

---

### Post by chengas123 on 2011-02-11
I figured it out.  It's because you have to run the command with sudo.  Too bad none of the docs mention that and the error message sucks.
sudo fail2ban-client status

---

