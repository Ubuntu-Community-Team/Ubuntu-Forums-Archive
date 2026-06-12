---
title: "Another postfix with dovecot can send emails but not receive"
date: 2018-09-15
forum: Server Platforms
---

### Post by ftiersch on 2018-09-15
Hi,

I've been searching for hours but I'm getting nowhere with this problem.

On my Ubuntu 16.04 root server I have installed a postfix server with dovecot for IMAP and POP3. I can send emails from Thunderbird but for the life of me I cannot get receiving emails to work. 
Nothing shows up in the mail.log (or mail.err) for receiving messages. If I send messages a log entry shows up.

First up: DNS.

I've created an A DNS record with mail.domain.com pointing to my server's IP address. 
The MX record points to mail.domain.com . rDNS record is set up and also points to mail.domain.com 

Here is the dig result for *dig mx domain.com*:
```

domain.com.     1799    IN      MX      0 mail.domain.com.

```

And for rDNS the result for [I]dig -x 123.123.123.123
[/I]```

12.119.214.85.in-addr.arpa. 1800 IN     PTR     mail.domain.com.

```

*hostname* returns mail.domain.com and *hostname -f* returns domain.com

The /etc/hosts file looks like this:
```

127.0.0.1       domain.com mail.domain.com localhost
85.214.119.12        subdomain.serverprovider.net

```

And *ufw status* returns this:
```

22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
Nginx Full                 ALLOW       Anywhere
110                        ALLOW       Anywhere
143                        ALLOW       Anywhere
25/tcp                     ALLOW       Anywhere
Postfix                    ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)
Nginx Full (v6)            ALLOW       Anywhere (v6)
110 (v6)                   ALLOW       Anywhere (v6)
143 (v6)                   ALLOW       Anywhere (v6)
25/tcp (v6)                ALLOW       Anywhere (v6)
Postfix (v6)               ALLOW       Anywhere (v6)

```

I can telnet from another server onto port 25 with the IP, mail.domain.com and domain.com and am greeted by SMTP.
Also I've tried sending emails to [EMAIL="info@mail.domain.com"]info@mail.domain.com[/EMAIL] instead of [EMAIL="info@domain.com"]info@domain.com[/EMAIL] which actually returns in a bounce with the error, that that recipient isn't configured (which makes sense, because I've only set up [EMAIL="info@domain.com"]info@domain.com[/EMAIL]) but if I send it to [EMAIL="info@domain.com"]info@domain.com[/EMAIL] no bounce happens.
I've tried sending an email via telnet and that worked and showed up in Thunderbird immediately. 

Here is the result of *postconf -n*:
```

anvil_rate_time_unit = 60s
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
inet_interfaces = all
mailbox_size_limit = 0
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mydomain = domain.com
myhostname = mail.domain.com
mynetworks = 127.0.0.0/8
myorigin = $mydomain
readme_directory = no
recipient_delimiter = +
smtp_tls_security_level = may
smtpd_banner = $myhostname ESMTP
smtpd_client_connection_count_limit = 5
smtpd_client_connection_rate_limit = 5
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unknown_client_hostname, reject_unauth_pipelining, reject_rbl_client zen.spamhaus.org
smtpd_delay_reject = yes
smtpd_error_sleep_time = 5s
smtpd_hard_error_limit = 3
smtpd_helo_required = yes
smtpd_helo_restrictions = reject_non_fqdn_hostname, reject_invalid_helo_hostname, reject_unknown_helo_hostname
smtpd_recipient_limit = 250
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_invalid_hostname, reject_non_fqdn_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unauth_destination, reject_unauth_pipelining, reject_rbl_client zen.spamhaus.org, reject_rbl_client cbl.abuseat.org, reject_rbl_client dul.dnsbl.sorbs.net
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $mydomain
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_non_fqdn_sender, reject_unknown_sender_domain
smtpd_soft_error_limit = 2
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/mail.domain.com/cert.pem
smtpd_tls_key_file = /etc/letsencrypt/live/mail.domain.com/privkey.pem
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
strict_rfc821_envelopes = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual_alias
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_domains = /etc/postfix/virtual_domains
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_transport = lmtp:unix:private/dovecot-lmtp
virtual_uid_maps = static:5000

```

If you need any more info I'm happy to provide it and I would appreciate every help! Been looking at every tutorial and post I could find and tried basically everything but E-Mails don't come through from the outside.

Thanks
Frank

---

### Post by darkod on 2018-09-15
1. The rDNS you mention, is it public or on your own bind? I am asking because even though it will resolve when your own servers use your own bind, it's irrelevant for the world. The ISP that owns that subnet is the only one that can set rDNS records that will be valid worldwide.

2. Same goes for the mail.domain.com A record. You posted the MX reply from dig and said the mail record exists, but is that testing from your own infrastructure or from anywhere on the internet? You have to have the public A record mail.domain.com working correctly.

3. Go here and test your mail.domain.com mail server: [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx). It will show you if any issues are found.

PS. Your hostname and hostname -f output seems to be reversed. The hostname should give you only the machine name, and the -f the whole FQDN. Modify the /etc/hosts file.
a. The 127.0.0.1 should point only to localhost (it's the loopback address, I wouldn't leave it resolving to fqdn)
b. The public IP should point to (in this order): mail.domain.com   mail

Do the tests above after modifying this. Reboot if necessary to apply the changes.

---

### Post by ftiersch on 2018-09-15
Hi Darko,

thanks already for the help.

1. I've set the rDNS record with the provider and the records come from a different server (although with the same provider). Just to make sure I've just tried it on a Digital Ocean droplet and the same values are shown there (both for rDNS and A record). The DNS is set via namecheap.com

3. I've tested it on mxtoolbox and everything is tested green.
Just reversed the hostname and FQDN hostname and rebooted but unfortunately the result is still the same -> no incoming mail.

---

