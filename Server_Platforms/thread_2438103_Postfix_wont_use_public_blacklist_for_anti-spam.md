---
title: "Postfix wont use public blacklist for anti-spam"
date: 2020-03-05
forum: Server Platforms
---

### Post by rogerk03 on 2020-03-05
[COLOR=#141414][FONT=&amp]Hi,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I have postfix up and running, works very well.  But I see occasional spammers sending email despite their IP being on some (if not all) the various public blacklists ([/FONT][/COLOR][COLOR=#141414][FONT=&amp]spamhaus.org, etc[/FONT][/COLOR][COLOR=#141414][FONT=&amp]).  They seem to be able to connect and send email, and only get caught out/blocked when they trigger other things, like no PTR record, etc. I've searched high and low, tried many different configs, every variation on google search, searched the forums here, but cant find out why postfix seems to ignore the blacklists.
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]This is my postfix config (main.cf):[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]```

mydomain = x.com
[/FONT][/COLOR][COLOR=#141414][FONT=&amp]myhostname = mail.x.com[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]alias_maps = hash:/etc/aliases[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]alias_database = hash:/etc/aliases[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]myorigin = /etc/mailname[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]mydestination = localhost.$mydomain, $mydomain, $myhostname, localhost.com.au, localhost[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]mailbox_size_limit = 0[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]recipient_delimiter = +[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]inet_interfaces = all[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]inet_protocols = ipv4[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]home_mailbox = Maildir/[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]biff = no[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]append_dot_mydomain = no[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]readme_directory = no[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]compatibility_level = 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_use_tls=yes[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_client_connection_count_limit = 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_client_connection_rate_limit = 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_client_message_rate_limit = 2[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_client_recipient_rate_limit = 5[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_client_new_tls_session_rate_limit = 2[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_relay_restrictions = [/FONT][/COLOR][COLOR=#141414][FONT=&amp]permit_mynetworks, [/FONT][/COLOR][COLOR=#141414][FONT=&amp]permit_sasl_authenticated, [/FONT][/COLOR][COLOR=#141414][FONT=&amp]defer_unauth_destination[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]anvil_rate_time_unit = 2s[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]smtpd_client_message_rate_limit = 2[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_helo_required = yes[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_helo_restrictions =[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_mynetworks,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_sasl_authenticated,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rhsbl_helo bl.spamcop.net,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_helo zen.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_helo cbl.abuseat.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_helo dbl.spamhaus.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_invalid_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_non_fqdn_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_sender_restrictions =[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_mynetworks,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_sasl_authenticated,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_reverse_client_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_client_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_sender_domain,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unverified_sender,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_client_restrictions =[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_mynetworks,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_sasl_authenticated,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_auth_destination,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]permit_dnswl_client swl.spamhaus.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rbl_client bl.spamcop.net,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rbl_client zen.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rbl_client cbl.abuseat.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_invalid_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unauth_pipelining,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unauth_destination,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_non_fqdn_recipient,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rhsbl_helo dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_reverse_client dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_sender dbl.spamhaus.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rhsbl_helo dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_invalid_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_non_fqdn_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_recipient_domain,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unverified_recipient,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]smtpd_recipient_restrictions =[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_mynetworks,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_sasl_authenticated,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit_auth_destination,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]permit_dnswl_client swl.spamhaus.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rbl_client bl.spamcop.net,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rbl_client zen.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rbl_client cbl.abuseat.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_invalid_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unauth_pipelining,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unauth_destination,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_non_fqdn_recipient,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_rhsbl_helo dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_reverse_client dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_sender dbl.spamhaus.org,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]reject_unknown_reverse_client_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_rhsbl_helo dbl.spamhaus.org,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_invalid_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_non_fqdn_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_helo_hostname,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unknown_recipient_domain,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]reject_unverified_recipient,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]permit[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]default_destination_rate_delay = 3s[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]disable_vrfy_command = yes[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]strict_rfc821_envelopes = yes[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]virtual_alias_domains = ......[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]virtual_alias_maps = hash:/etc/postfix/virtual 

[/FONT][/COLOR]
```[COLOR=#141414][FONT=&amp]


[/FONT][/COLOR]

---

### Post by TheFu on 2020-03-06
postconf -n ?

---

