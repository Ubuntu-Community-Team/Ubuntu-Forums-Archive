---
title: "postfix/dovecot server Can't receive mails!"
date: 2012-07-27
forum: Server Platforms
---

### Post by dchen on 2012-07-27
In order to replace the old Linux box (currently running Fedora with postfix/dovecot mail server), I built an Ubuntu server 12.04 on a new hardware with same postfix/dovecot/squirrelmail services.  To keep my old Linux (Fedora) server intact, and for the purpose of testing the new Ubuntu mail server, I configured this new Ubuntu server on the subdomain, testmail.biokeyinc.com.      On this new testmail.biokeyinc.com machine, I was able to receive and send from/to external mails such as yahoo and gmail, so far so good, but only bother is that there is a constant line below (every 2 minutes) displayed in the /var/log/mail.log:

Jul 27 15:49:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
Jul 27 15:51:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
Jul 27 15:53:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
Jul 27 15:55:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
Jul 27 15:57:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
Jul 27 15:59:29 testmail dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
...

Just ignore the above the log msg for now, I changed and configured the new Ubuntu server as the main domain, biokeyinc.com, re-run the "sudo dpkg-reconfigure postfix", completely shut down the old Fedora server, and replaced it with the new Ubuntu server, reboot the system...
Now, the Outgoing mails to external i.e. gmail or yahoo mails were sent fine, but Incoming mail from yahoo or gmail CAN'T receive ! also there is No incoming mail activity showed in the /var/log/mail.log.

Here is the output of my "postconf -n" and "doveconf -n" on the new Ubuntu server on the biokeyinc.com domain for reference:

admin@server:/etc/postfix$ postconf -n
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
enable_original_recipient = no
header_checks = regexp:/etc/postfix/header_checks
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = server.biokeyinc.com, biokeyinc.com, localhost.biokeyinc.com, localhost
myhostname = server.biokeyinc.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.20.0/24
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450

admin@server:/etc/postfix$ doveconf -n
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-25-generic x86_64 Ubuntu 12.04 LTS 
auth_mechanisms = plain login
disable_plaintext_auth = no
mail_location = maildir:~/Maildir
passdb {
  driver = pam
}
protocols = " imap pop3"
service auth {
  unix_listener /var/spool/postfix/private/auth-client {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
  unix_listener /var/spool/postfix/private/dovecot-auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}
ssl_ca = </etc/ssl/certs/cacert.pem
ssl_cert = </etc/ssl/certs/dovecot.crt
ssl_key = </etc/ssl/private/dovecot.key
userdb {
  driver = passwd
}

Here is also the open ports output:

admin@server:~$ nmap 192.168.20.100

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-07-27 13:53 PDT
Nmap scan report for 192.168.20.100
Host is up (0.00025s latency).
Not shown: 984 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
110/tcp   open  pop3
139/tcp   open  netbios-ssn
143/tcp   open  imap
443/tcp   open  https
445/tcp   open  microsoft-ds
465/tcp   open  smtps
587/tcp   open  submission
993/tcp   open  imaps
995/tcp   open  pop3s
5900/tcp  open  vnc
8080/tcp  open  http-proxy
10000/tcp open  snet-sensor-mgmt


Hope anyone would shed some light !

---

### Post by DJ_Max on 2012-07-27
Run it through [http://www.mxtoolbox.com/](http://www.mxtoolbox.com/) to see if you have it configured correctly

---

