---
title: "Postfix PCI DSS 3.1 Unencrypted Communication Channel Accessibility port 25"
date: 2016-07-26
forum: Server Platforms
---

### Post by jlittle on 2016-07-26
I have only 1 issue causing my to fail PCI compliance on my mailserver, and I have been frustrated finding a solution. 16.04 server with Postfix 3.1 I have TLS set up and working for submission port. All is working from the client side only use Secure POP3 & Secure IMAP but Trustwave is flagging 'Unencrypted Communication Channel Accessibility port 25'. But that is MTA to MTA and can not force encryption public mail server or may prevent receiving email form other servers, right? More I read the more confused I am getting. 

In my main.cf I have
 
```
...
# enable opportunistic TLS support
smtpd_tls_security_level = may
smtp_tls_security_level = may
# offer authentication after starttls
smtpd_tls_auth_only = yes
tls_ssl_options = NO_COMPRESSION

# disable banned protocals for PCI DSS 3.1 [v0.2] [v0.3]
smtpd_tls_protocols = !SSLv2,!SSLv3
smtp_tls_protocols = !SSLv2,!SSLv3
smtpd_tls_mandatory_protocols = !SSLv2,!SSLv3
smtp_tls_mandatory_protocols = !SSLv2,!SSLv3

# manditory high level ciphers
smtpd_tls_mandatory_ciphers=high
# enforce the server cipher preference
tls_preempt_cipherlist = yes
# disable following ciphers [v0.3]
smtpd_tls_mandatory_exclude_ciphers = MD5, DES, ADH, RC4, PSD, SRP, 3DES, eNULL, aNULL
smtpd_tls_exclude_ciphers = MD5, DES, ADH, RC4, PSD, SRP, 3DES, eNULL, aNULL
smtp_tls_mandatory_exclude_ciphers = MD5, DES, ADH, RC4, PSD, SRP, 3DES, eNULL, aNULL

# [v0.4] EDH Server support 
smtpd_tls_dh1024_param_file = ${config_directory}/dh2048.pem
smtpd_tls_dh512_param_file = ${config_directory}/dh512.pem

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
...
```

In master.cf

```
...
smtp      inet  n       -       y       -       -       smtpd
#smtp      inet  n       -       y       -       1       postscreen
#smtpd     pass  -       -       y       -       -       smtpd
#dnsblog   unix  -       -       y       -       0       dnsblog
#tlsproxy  unix  -       -       y       -       0       tlsproxy
submission inet n       -       y       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
# added 
  -o tls_preempt_cipherlist=yes
# Since Thunderbird/SeaMonkey uses TLSv1.2 can disable TLSv1.0 on submission
  -o smtpd_tls_protocols=!SSLv2,!SSLv3,!TLSv1
  -o smtpd_tls_mandatory_protocols=!SSLv2,!SSLv3,!TLSv1
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       y       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
...
```

They note the problem with telnet test:

```

$ telnet 107.xxx.xxx.75 25
Trying 107.xxx.xxx.75...
Connected to 107.xxx.xxx.75.
Escape character is '^]'.
220 mail.littleworksstudio.com
EHLO 107.xxx.xxx.75
250-mail.littleworksstudio.com
250-PIPELINING
250-SIZE 40960000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: user_test@trustwave.com
250 2.1.0 Ok

```

What do I need to do to satisfy compliance and NOT prevent me from receiving email?

-- 
Jonathan

---

