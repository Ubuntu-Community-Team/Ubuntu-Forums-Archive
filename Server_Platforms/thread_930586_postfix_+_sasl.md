---
title: "postfix + sasl"
date: 2008-09-26
forum: Server Platforms
---

### Post by xxxYURAxxx on 2008-09-26
Hi,
my server configuration: postfix+dovecot+SASL(shadow) on debian etch

my logs:

postfix/smtpd[13314]: NOQUEUE: reject: RCPT from unknown[80.94.225.150]: 554 5.7.1 <my_mailbox@gmail.com>: Relay access denied; from=<my_mailbox@my_server.com> 
to=<my_mailbox@gmail.com> proto=ESMTP helo=<localhost>
postfix/smtpd[13314]: Write 57 chars: 554 5.7.1 <my_mailbox@gmail.com>: Rela
disconnect from unknown[80.94.225.150]


my configs:

/etc/postfix/main.cf
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain =
smtpd_sasl_security_option = nonananymous
smtpd_sasl_auth_enable = yes
smtpd_sasl_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

/etc/default/saslauthd
START=yes
MECHANISMS="shadow"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c"

/etc/postfix/sasl/smtpd.conf
mech_list: PLAIN LOGIN
pwcheck_method: shadow

Thanks.

---

### Post by MJN on 2008-09-26
It might be helpful if you stated what the problem is. What you were doing, what you were trying to do etc!
 
I'm guessing you are 80.94.225.150 and that you tried to send a message via your server to a gmail account? And that your server refused to do so?
 
Did you authenticate with the server first?
 
Mathew

---

### Post by xxxYURAxxx on 2008-09-26
/etc/dovecot/dovecot.conf
auth default {
mechanisms = plain login
passdb pam {
}
passdb passwd {
}
passdb shadow {
}
socket listen {
client {
path = /var/spool/postfix/private/auth
mode = 0660
user = postfix
group = postfix
}
}

/usr/sbin/testsaslauthd -u login -p password
is ok

telnet server 25
auth plain crypted_login&pass
is ok too

but from thunderbird or evolution i have message "Relay access denied"

---

### Post by xxxYURAxxx on 2008-09-26
it's error in postfix config
smtpd_sasl_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
should be replaced by:
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
and sasl works correctly

---

### Post by lopes_andre on 2008-10-05
> **xxxYURAxxx said:**
> it's error in postfix config
smtpd_sasl_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
should be replaced by:
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
and sasl works correctly

Hi,

Wich Tutorial you have read to configure the SmartHost way of sending SMTP?

I can't get my SMTP Auth to work, my guide was, [http://newbiedoc.berlios.de/wiki/Mail_-_sending](http://newbiedoc.berlios.de/wiki/Mail_-_sending)

My mail.log gives me this:

Oct  5 00:58:00 localhost postfix/master[4804]: daemon started -- version 2.5.1, configuration /etc/postfix
Oct  5 00:58:05 localhost postfix/pickup[4805]: 169D86787: uid=1000 from=<andre>
Oct  5 00:58:05 localhost postfix/cleanup[4812]: 169D86787: message-id=<20081004235805.169D86787@localhost.info>
Oct  5 00:58:05 localhost postfix/qmgr[4807]: 169D86787: from=<andre@localhost.info>, size=328, nrcpt=1 (queue active)
Oct  5 00:58:35 localhost postfix/smtp[4814]: connect to relay.netvisao.pt[213.228.128.59]:25: Connection timed out
Oct  5 00:58:35 localhost postfix/smtp[4814]: 169D86787: to=<andresousa80@gmail.com>, relay=none, delay=30, delays=0.03/0.01/30/0, dsn=4.4.1, status=deferred (connect to relay.netvisao.pt[213.228.128.59]:25: Connection timed out)

What can I do?

Best Regards, André.

---

