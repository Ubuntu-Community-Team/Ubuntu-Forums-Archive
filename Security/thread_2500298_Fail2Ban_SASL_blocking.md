---
title: "Fail2Ban SASL blocking"
date: 2024-08-29
forum: Security
---

### Post by robbo008 on 2024-08-29
Hi Guys,
I've got fail2ban installed under Ubuntu and can't seem to get the blocking working for failed SASL login attempts. Any help most appreciated. These are the errors I'm seeing in my logs:

postfix/smtpd[1823363]: warning: unknown[80.94.95.239]: SASL LOGIN authentication failed: (reason unavailable), sasl_username=bob@mydomain.com

my /etc/fail2ban/jail.local has the following:

[DEFAULT]
# here you can overwrite some defaults:

[pure-ftpd]
enabled = true
port = ftp
filter = pure-ftpd
logpath = /var/log/syslog
maxretry = 3

[dovecot]
enabled = true
filter = dovecot
action = iptables-multiport[name=dovecot-pop3imap, port="pop3,pop3s,imap,imaps", protocol=tcp]
logpath = /var/log/mail.log
maxretry = 5

[postfix-sasl]
enabled = true
filter = postfix[mode=auth]
logpath = /var/log/mail.log
maxretry = 3
findtime = 10h

[sshd]
enabled   = true
maxretry  = 5
findtime  = 10m
bantime   = 1d

port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s

---

### Post by currentshaft on 2024-08-30
Does the regex in /etc/fail2ban/filter.d/postfix-sasl.conf actually match your log line?

---

### Post by sterence2 on 2024-09-03
Ah, fail2ban, always up to some tricks... Are you sure the postfix filter is set up correctly? If it&#8217;s not blocking those SASL attempts, maybe something&#8217;s off in your jail.local file. And honestly, if you&#8217;re seeing weird stuff like that, it almost feels like someone&#8217;s trying to hack in, like some sneaky intrusion attempt that&#8217;s slipping through the cracks. Double-check those logs&#8212;it might be a sign that someone&#8217;s trying to mess with your server. Better safe than sorry, right?
______________
Here to [[FONT=Arial]learn hacking on hdna[/FONT]]("https://hackerdna.com")

---

### Post by Irihapeti on 2024-09-03
*Thread moved to **Security** as it's a support request.*

---

