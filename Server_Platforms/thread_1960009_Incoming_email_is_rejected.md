---
title: "Incoming email is rejected"
date: 2012-04-16
forum: Server Platforms
---

### Post by faroutliving on 2012-04-16
I'm running an 11.04 server with webmin/virtualmin hosting several  domains with shared and unique ip addresses. Only one of those domains  was being used for email (and just as a test I did when I set the server  up). Now I want to move my email for another domain to the server, and  initially it was receiving emails and I could not send. I made what I  thought were minor changes to try and resolve the outgoing email problem  and instead broke incoming email! I put everything back (to the best of  my knowledge) and it still won't work. The other domain however is  still functional :smile:

What happens is when I try and send email from another server the email  is rejected with the error prepended to the returned email:

The mail server could not deliver mail to _[EMAIL="me@virtualdomain.tld"]me@virtualdomain.tld[/EMAIL]_  The account or domain may not exist, they may be blacklisted, or missing the proper dns entries.
  

The auth.log entry shows:
Apr 16 14:08:03 lisn-mdv dovecot-auth: pam_unix(dovecot:auth): check pass; user unknown
Apr 16 14:08:03 lisn-mdv dovecot-auth: pam_unix(dovecot:auth):  authentication failure; logname= uid=0 euid=0 tty=dovecot  ruser=emailuser rhost=75.104.6.189
Apr 16 14:08:12 lisn-mdv dovecot-auth: pam_unix(dovecot:auth): check pass; user unknown
Apr 16 14:08:12 lisn-mdv dovecot-auth: pam_unix(dovecot:auth):  authentication failure; logname= uid=0 euid=0 tty=dovecot  ruser=emailuser rhost=75.104.6.189
Apr 16 14:08:29 lisn-mdv dovecot-auth: pam_unix(dovecot:auth): check pass; user unknown
Apr 16 14:08:29 lisn-mdv dovecot-auth: pam_unix(dovecot:auth):  authentication failure; logname= uid=0 euid=0 tty=dovecot  ruser=me@myvirtualdomain.tld rhost=75.104.6.189
Apr 16 14:08:39 lisn-mdv dovecot-auth: pam_unix(dovecot:auth): check  pass; user unknown Apr 16 14:08:39 lisn-mdv dovecot-auth:  pam_unix(dovecot:auth): authentication failure; logname= uid=0 euid=0  tty=dovecot ruser=me@myvirtualdomain.tld rhost=75.104.6.189 


and "dig [EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL] mx" returns

; <<>> DiG 9.7.3-P3 <<>> [EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL] mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59498
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 1

;; QUESTION SECTION:
;[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].            IN    MX

;; ANSWER SECTION:
[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].        38400    IN    MX    5 mail.[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].

;; AUTHORITY SECTION:
[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].        19663    IN    NS    ns1.nsdomain.com.
[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].        19663    IN    NS    ns2.nsdomain.com.

;; ADDITIONAL SECTION:
mail.[EMAIL="me@virtualdomain.tld"]virtualdomain.tld[/EMAIL].    25624    IN    A    xxx.xxx.xxx.xxx

;; Query time: 1975 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Mon Apr 16 15:39:14 2012
;; MSG SIZE  rcvd: 117

and: nslookup mail.virtualdomain.tld

Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    mail.virtualdomain.tld
Address: xxx.xxx.xxx.xxx

So, my limited knowledge makes me believe it is a problem with authentication, but where to go from here is my problem.

Thanks for any help!

---

### Post by faroutliving on 2012-04-17
HELP! About at wits end here. If I send email to kazmaier at marksteiner dot ag, syslog gets the entry:

Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: connect from a2s61.a2hosting.com[75.98.165.130]
Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: NOQUEUE: reject: RCPT from a2s61.a2hosting.com[75.98.165.130]: 554 5.7.1 <kazmaier at marksteiner dot ag>: Recipient address rejected: Access denied; from=<support at pagestream dot org> to=<kazmaier at marksteiner dot ag> proto=ESMTP helo=<a2s61.a2hosting.com>
Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: disconnect from a2s61.a2hosting.com[75.98.165.130]

Does that spark an idea from anyone?

---

### Post by nsnidanko on 2012-04-17
First, lets try troubleshooting why postfix rejects email from a2s61.a2hosting.com (I am guessing it rejects from another hosts as well, right?). Can you please post you postfix's config file main.cf (located in /etc/postfix)

---

### Post by SeijiSensei on 2012-04-17
deleted

---

### Post by lisati on 2012-04-17
> **faroutliving said:**
> HELP! About at wits end here. If I send email to kazmaier at marksteiner dot ag, syslog gets the entry:

Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: connect from a2s61.a2hosting.com[75.98.165.130]
Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: NOQUEUE: reject: RCPT from a2s61.a2hosting.com[75.98.165.130]: 554 5.7.1 <kazmaier at marksteiner dot ag>: Recipient address rejected: Access denied; from=<support at pagestream dot org> to=<kazmaier at marksteiner dot ag> proto=ESMTP helo=<a2s61.a2hosting.com>
Apr 17 10:16:34 lisn-mdv postfix/smtpd[9873]: disconnect from a2s61.a2hosting.com[75.98.165.130]

Does that spark an idea from anyone?

The "Access denied" message without further explanation is a generic message. My server (postfix) spits that out when I've manually blacklisted an IP address or email address and haven't bothered providing an explanation in the relevant configuration file. You might need to contact the recipient another way.

---

### Post by faroutliving on 2012-04-17
> **nsnidanko said:**
> First, lets try troubleshooting why postfix rejects email from a2s61.a2hosting.com (I am guessing it rejects from another hosts as well, right?). Can you please post you postfix's config file main.cf (located in /etc/postfix)

I should have been clear about that. I can send email to another (virtual) domain on the same server, and all emails to this domain are rejected regardless of where I send them from.

Thanks!

Here is my main.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = lisn-mdv.razercut.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = lisn-mdv.razercut.com, localhost.razercut.com, , localhost
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject
allow_percent_hack = no

```

---

### Post by lisati on 2012-04-17
Nothing in your main.cf file jumps out to me as obviously "wrong". 

The "access denied" message you are receiving is a generic error that could mean anything. You will need to contact the people who run the other server to get more details from them as to why your email is being rejected: on my server it usually (but not necessarily) means that I have manually blocked an IP address or email address, other people could have other reasons.

---

### Post by faroutliving on 2012-04-17
??? lisati, I guess I'm more in the dark than I thought. The errors are on my server, where emails to me are being rejected on my server. It doesn't matter who sends me an email, it gets rejected on my server. Another domain of mine that I host on my server is not rejecting incoming emails.

Why would I contact someone at another server? If my server is rejecting emails from everyone because it thinks they are all blacklisted, wouldn't I need to fix it on my end?

More confused than when I started this...

---

### Post by faroutliving on 2012-04-17
Ok, I think I have some details that someone more knowledgable could resolve this with. I added debug_peer_level = 5 and tried to send an email to this broken domain.

Here is what I think the relevant parts of the log reveal. It seems it can't find the email address in the "virtual address table". I'm sure I saw email -> username in the virtual file. Could the file be unparseable, or is this info from some other file?

Here is the mail.log:
```

Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: < a2s61.a2hosting.com[75.98.165.130]: RCPT TO:<kazmaier@marksteiner.ag>
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: extract_addr: input: <kazmaier@marksteiner.ag>
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: smtpd_check_addr: addr=kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: event_request_timer: reset 0x7f7f75e8d1e0 0x7f7f787875a0 5
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr request = rewrite
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr rule = local
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr address = kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_fflush_some: fd 20 flush 60
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_buf_get_ready: fd 20 got 41
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: 0
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: address
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: address
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: (list terminator)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: (end)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: rewrite_clnt: local: kazmaier@marksteiner.ag -> kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: event_request_timer: reset 0x7f7f75e8d1e0 0x7f7f787875a0 5
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr request = resolve
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr sender = 
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr address = kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_fflush_some: fd 20 flush 57
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_buf_get_ready: fd 20 got 113
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: 0
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: transport
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: transport
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: error
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: nexthop
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: nexthop
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: User unknown in virtual alias table
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: recipient
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: recipient
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: 512
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: (list terminator)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: (end)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: resolve_clnt: `' -> `kazmaier@marksteiner.ag' -> transp=`error' host=`User unknown in virtual alias table' rcpt=`kazmaier@marksteiner.ag' flags= class=alias
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: ctable_locate: install entry key kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: extract_addr: in: <kazmaier@marksteiner.ag>, result: kazmaier@marksteiner.ag
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: event_request_timer: reset 0x7f7f75e8d1e0 0x7f7f787875a0 5
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr request = rewrite
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr rule = local
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: send attr address = double-bounce
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_fflush_some: fd 20 flush 50
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: vstream_buf_get_ready: fd 20 got 53
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: flags
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: 0
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: address
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: address
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute value: double-bounce@lisn-mdv.razercut.com
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: private/rewrite socket: wanted attribute: (list terminator)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: input attribute name: (end)
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: rewrite_clnt: local: double-bounce -> double-bounce@lisn-mdv.razercut.com
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: >>> START Recipient address RESTRICTIONS <<<
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=permit_mynetworks
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: permit_mynetworks: a2s61.a2hosting.com 75.98.165.130
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostname: a2s61.a2hosting.com ~? 127.0.0.0/8
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostaddr: 75.98.165.130 ~? 127.0.0.0/8
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostname: a2s61.a2hosting.com ~? [::ffff:127.0.0.0]/104
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostaddr: 75.98.165.130 ~? [::ffff:127.0.0.0]/104
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostname: a2s61.a2hosting.com ~? [::1]/128
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_hostaddr: 75.98.165.130 ~? [::1]/128
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_list_match: a2s61.a2hosting.com: no match
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: match_list_match: 75.98.165.130: no match
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=permit_mynetworks status=0
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=permit_sasl_authenticated
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=permit_sasl_authenticated status=0
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=reject
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: NOQUEUE: reject: RCPT from a2s61.a2hosting.com[75.98.165.130]: 554 5.7.1 <kazmaier@marksteiner.ag>: Recipient address rejected: Access denied; from=<support@pagestream.org> to=<kazmaier@marksteiner.ag> proto=ESMTP helo=<a2s61.a2hosting.com>
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: generic_checks: name=reject status=2
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: > a2s61.a2hosting.com[75.98.165.130]: 554 5.7.1 <kazmaier@marksteiner.ag>: Recipient address rejected: Access denied
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: watchdog_pat: 0x7f7f78768e00
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: < a2s61.a2hosting.com[75.98.165.130]: DATA
Apr 17 22:59:42 lisn-mdv postfix/smtpd[13465]: > a2s61.a2hosting.com[75.98.165.130]: 554 5.5.1 Error: no valid recipients

```

---

