---
title: "can't authenticate with Postfix"
date: 2008-06-02
forum: Server Platforms
---

### Post by skunkwerk on 2008-06-02
i can send an email when i'm on the localhost just fine, but when i try to connect remotely through the smtp server using SASL authentication, i can't authenticate (i connect to the server, but it times out and doesn't say the password is incorrect)...i've tried this both from telnet and thunderbird.

there's no error in my /var/log/mail.log file on the server (just a connect & timeout message), and i've confirmed the saslauthd process is running.

i followed the guide here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

here's my /etc/postfix/sasl/smtpd.conf:
pwcheck_method: saslauthd
mech_list: plain login

and my /etc/postfix/main.cf:
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
myhostname = (domainname)
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = (domainname), localhost.(domainname), localhost
relayhost =
mynetworks = 127.0.0.1/32 10.251.106.64/32
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

any ideas?
thanks

---

### Post by quelx on 2008-06-02
some posibilities

-Your ISP is blocking port 25
-Your router is not forwarding port 25 to the server running postfix
-firewall rules on the server are blocking requests from the Internet

---

### Post by skunkwerk on 2008-06-02
thanks quelx,
   i'm not running on port 25 for exactly that reason - i'm running on port 587.  i know requests are going through because i'm actually connecting to the server, and its responding.  it just doesn't respond during the authentication.

any further suggestions?
thanks

---

### Post by quelx on 2008-06-02
Have you tried telneting to port 587 from outside your network?

Google terms: *test postfix sasl telnet*

---

### Post by MJN on 2008-06-03
> **skunkwerk said:**
> (just a connect & timeout message),
 
What exactly do you mean by this? Are you getting any SMTP dialogue at all?
 
If not, then it's nothing to do with SASL authentication (as that is a later step).
 
If you are then try upping the logging verbosity (by adding -v or -vv to the smtp command at the end of the smtpd transport in /etc/postfix/master.cf). Post this and we can see exactly what's happening (or not).
 
Mathew

---

### Post by skunkwerk on 2008-06-03
MJN: yes, i am getting dialogue with the SMTP server

(following the guide here: [http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html))
here's my telnet to port 587 commands/output (domain/base64 disguised):

Trying 75.100.128.109
Connected to domain.com
Escape character is '^]'.
220 domain.com ESMTP Postfix (Ubuntu)
ehlo domain.com
250-domain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN base64hash

after that, there's no response

i'll try again with the verbose setting you asked for

---

### Post by skunkwerk on 2008-06-03
here's my mail log with -vv enabled (i've skipped a ton of dict_lookup/mac_parse lines, and masked the domain).  it seems like there's some match_list_match error.

daemon started -- version 2.4.5, configuration /etc/postfix
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: dict_lookup: syslog_facility = (notfound)
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: mac_parse: mail
.........
.........
.........
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: connect from DNab4383dd.Stanford.EDU[171.67.131.221]
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: DNab4383dd.Stanford.EDU: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: 171.67.131.221: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: DNab4383dd.Stanford.EDU: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: 171.67.131.221: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_hostname: DNab4383dd.Stanford.EDU ~? 127.0.0.1/32
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_hostaddr: 171.67.131.221 ~? 127.0.0.1/32
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_hostname: DNab4383dd.Stanford.EDU ~? 10.251.106.64/32
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_hostaddr: 171.67.131.221 ~? 10.251.106.64/32
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: DNab4383dd.Stanford.EDU: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: 171.67.131.221: no match
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: auto_clnt_open: connected to private/anvil
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: send attr request = connect
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: send attr ident = 587:171.67.131.221
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: private/anvil: wanted attribute: status
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute name: status
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute value: 0
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: private/anvil: wanted attribute: count
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute name: count
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute value: 1
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: private/anvil: wanted attribute: rate
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute name: rate
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute value: 1
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: private/anvil: wanted attribute: (list terminator)
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: input attribute name: (end)
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 220 shadowpush.com ESMTP Postfix (Ubuntu)
Jun  3 08:35:37 ip-10-251-106-64 postfix/smtpd[3893]: watchdog_pat: 0x807e7b0
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: < DNab4383dd.Stanford.EDU[171.67.131.221]: ehlo domain.com
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-domain.com
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-PIPELINING
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-SIZE 10240000
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-VRFY
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-ETRN
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-AUTH LOGIN PLAIN
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: DNab4383dd.Stanford.EDU: no match
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: match_list_match: 171.67.131.221: no match
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-AUTH=LOGIN PLAIN
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-ENHANCEDSTATUSCODES
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250-8BITMIME
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: > DNab4383dd.Stanford.EDU[171.67.131.221]: 250 DSN
Jun  3 08:35:48 ip-10-251-106-64 postfix/smtpd[3893]: watchdog_pat: 0x807e7b0

thank you

---

### Post by skunkwerk on 2008-06-04
the output of some debugging:

postconf -n: [http://pastebin.com/m5b48c531](http://pastebin.com/m5b48c531)
saslfinger -s: [http://pastebin.com/m78a2bb98](http://pastebin.com/m78a2bb98)

thanks

---

