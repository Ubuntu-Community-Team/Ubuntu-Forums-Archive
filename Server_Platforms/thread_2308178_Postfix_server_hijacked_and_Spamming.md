---
title: "Postfix server hijacked and Spamming"
date: 2015-12-31
forum: Server Platforms
---

### Post by Nick_Ellis on 2015-12-31
Server has been running great until perhaps a week or two ago. Since then it has been hijacked or something is misconfigured that some jerk has taken advantage of to use my server to spam and damage our IP reputation etc. I'm not a mail administrator or Linux pro, but always learning, following guides and trying to make things run well and be a good "internet citizen".

Currently I've blocked port 25 out, so that I can watch things such as mailq build up without the crap getting out of my system.

I thought I had it pretty tightly configured, but apparently not. 

Setup: used guide at workaround.org to configure the system. Server has a couple domains that it sends mail as. One of the domains sends via webmail (roundcube/dovecot). The 2nd domain is a MS Exchange server, which postfix relays messages from. 

Here is my postfix main.cf file

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version




# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname




smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
##Added by Nick 8/30/2014##
smtpd_tls_security_level=may


### Added by Nick to add Delay in sending messages to prevent sending of mass messages from hack ###
smtp_destination_concurrency_limit = 2
smtp_destination_rate_delay = 15s
smtp_extra_recipient_limit = 10
anvil_rate_time_unit = 900
anvil_status_update_time = 120s
smtpd_client_message_rate_limit = 10




# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = MyDomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $mydomain, localhost.$mydomain, localhost, Ronin
relayhost = 
mynetworks = 127.0.0.1 xxx.xxx.xxx.xxx (Exchange server IP)
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous


###Added by Nick 3/14/14###
disable_vrfy_command = yes
smtpd_delay_reject = yes


smtpd_helo_required = yes
smtpd_helo_restrictions = 
  permit_sasl_authenticated
  reject_invalid_helo_hostname
  reject_non_fqdn_hostname
  reject_invalid_hostname


smtpd_client_restrictions = 
  check_client_access cidr:/etc/postfix/client_access
  reject_unknown_client_hostname


smtpd_recipient_restrictions = 
  permit_mynetworks
  permit_sasl_authenticated


  ##ADded by Nick -- Include WhiteList/BlackList hosts from file##
  check_client_access hash:/etc/postfix/rbl_override


  reject_unauth_destination
  reject_unlisted_recipient


  ##Added by Nick -- 3/14/14##
  reject_invalid_hostname
  reject_non_fqdn_hostname
  reject_non_fqdn_sender
  reject_non_fqdn_recipient
  reject_unknown_sender_domain


  ##Added by Nick - Below is a realtime blacklist to help fight spam##
  reject_unknown_recipient_domain
  reject_rbl_client b.barracudacentral.org
  reject_rbl_client dnsbl.sorbs.net
  reject_rbl_client bl.spamcop.net
  reject_rbl_client zen.spamhaus.org
  reject_rbl_client psbl.surriel.com




smtpd_data_restrictions = 
  reject_unauth_pipelining 
  permit 


milter_protocol = 2
milter_default_action = accept


#content_filter = smtp-amavis:[127.0.0.1]:10024
#receive_override_options = no_address_mappings
#smtpd_milters = inet:127.0.0.1:54321
#non_smtpd_milters = inet:127.0.0.1:54321
smtpd_milters = inet:localhost:12301
non_smtpd_milters =  inet:localhost:12301




### Added by Nick 1/24/2015 to try and fix mail bounces from root@Ronin ###
smtp_host_lookup = dns, native

```

In trouble shooting, I removed both IP's from the "mynetworks" (as my understanding is whatever IP's are listed postfix will receive mail from), however even with BOTH the 127 and the Exchange removed, things still pile up in the mail queue.

Can anyone suggest where I might go from here?

Thanks for your help! Hate these spammer chumps!

---

### Post by Nick_Ellis on 2015-12-31
Also here are some mail logs if it's useful. Strangely -- the FROM domain (@Charter) we host the website for, but NOT email. They are not in my mySQL table, and I thought the server was configured so that it would only send mail if it matched a user from the mySQL table and domain as per the workaround.org tutorial. So 1. Don't know how these messages are getting relayed and 2. Don't know why it's even sending mails from users not in the mySQL table! (intentionally messed up email domain names to prevent robots from collecting useful data)

```
3864043 Dec 31 18:30:58 MyDomain postfix/error[30946]: B612025C8C4: to=<alwaysfreshtodeathyo@@--@@yahoo.com>, relay=none, delay=150, delays=0/150/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mta5.am0.yahood        ns.net[66.196.118.34]:25: Connection timed out)
3864044 Dec 31 18:30:58 MyDomain postfix/error[30744]: 21DD525C8DB: to=<redclawb@@--@@yahoo.com>, relay=none, delay=46, delays=0/46/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mta5.am0.yahoodns.net[66.196.        118.34]:25: Connection timed out)
3864045 Dec 31 18:30:58 MyDomain postfix/error[30945]: 48CA425C8E6: to=<collins8806@@--@@hotmail.com>, relay=none, delay=45, delays=0.01/45/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mx2.hotmail.com[207.4        6.8.199]:25: Connection timed out)
3864046 Dec 31 18:30:58 MyDomain postfix/error[30705]: 27FA525C8DD: to=<drossnaked4u@@--@@yahoo.com>, relay=none, delay=46, delays=0.01/46/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mta5.am0.yahoodns.net[        66.196.118.34]:25: Connection timed out)
3864047 Dec 31 18:30:58 MyDomain postfix/error[30947]: 18C8025C8D8: to=<brandy_fut_23@@--@@hotmail.com>, relay=none, delay=46, delays=0.01/46/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mx2.hotmail.com[207        .46.8.199]:25: Connection timed out)
3864048 Dec 31 18:30:58 MyDomain postfix/smtp[30234]: connect to mx3.hotmail.com[65.55.37.120]:25: Connection timed out
3864049 Dec 31 18:30:58 MyDomain postfix/smtp[30234]: BB46625C8C6: to=<blanco93@@--@@live.com>, relay=none, delay=150, delays=0/0/150/0, dsn=4.4.1, status=deferred (connect to mx3.hotmail.com[65.55.37.120]:25: Connection timed out)
3864050 Dec 31 18:31:13 MyDomain postfix/smtp[30700]: connect to yeahmx01.mxmail.netease.com[123.58.177.220]:25: Connection timed out
3864051 Dec 31 18:31:13 MyDomain postfix/smtp[30685]: connect to mx3.hotmail.com[65.55.37.72]:25: Connection timed out
3864052 Dec 31 18:31:13 MyDomain postfix/smtp[30686]: connect to frf-mailrelay.att.net[204.127.217.21]:25: Connection timed out
3864053 Dec 31 18:31:13 MyDomain postfix/smtp[30688]: connect to mailin-02.mx.aol.com[64.12.88.163]:25: Connection timed out
3864054 Dec 31 18:31:43 MyDomain postfix/smtp[30700]: connect to yeahmx01.mxmail.netease.com[123.58.177.213]:25: Connection timed out
3864055 Dec 31 18:31:43 MyDomain postfix/smtp[30685]: connect to mx3.hotmail.com[65.55.92.168]:25: Connection timed out
3864056 Dec 31 18:31:43 MyDomain postfix/smtp[30686]: connect to aln-mailrelay.att.net[12.102.252.75]:25: Connection timed out
3864057 Dec 31 18:31:43 MyDomain postfix/smtp[30688]: connect to mailin-03.mx.aol.com[64.12.91.196]:25: Connection timed out
3864058 Dec 31 18:31:56 MyDomain postfix/pickup[30678]: 200AB25C8EF: uid=33 from=<bridget_holloway@@--@@chartercommercial.net>
3864059 Dec 31 18:31:56 MyDomain postfix/cleanup[30952]: 200AB25C8EF: message-id=<02c4939eef9e9d38f3656df80a500716@@--@@chartercommercial.net>
3864060 Dec 31 18:31:56 MyDomain opendkim[4680]: 200AB25C8EF: no signing table match for 'bridget_holloway@@--@@chartercommercial.net'
3864061 Dec 31 18:31:58 MyDomain opendkim[4680]: 200AB25C8EF: no signature data
3864062 Dec 31 18:31:58 MyDomain postfix/qmgr[29300]: 200AB25C8EF: from=<bridget_holloway@@--@@chartercommercial.net>, size=1452, nrcpt=1 (queue active)
3864063 Dec 31 18:31:58 MyDomain postfix/pickup[30678]: 78CA525C8F0: uid=33 from=<nancy_evans@@--@@chartercommercial.net>
3864064 Dec 31 18:31:58 MyDomain postfix/cleanup[30952]: 78CA525C8F0: message-id=<2d3d7276cef80c0009e2340203738e58@@--@@chartercommercial.net>
3864065 Dec 31 18:31:58 MyDomain opendkim[4680]: 78CA525C8F0: no signing table match for 'nancy_evans@@--@@chartercommercial.net'
3864066 Dec 31 18:31:58 MyDomain opendkim[4680]: 78CA525C8F0: no signature data
3864067 Dec 31 18:31:58 MyDomain postfix/qmgr[29300]: 78CA525C8F0: from=<nancy_evans@@--@@chartercommercial.net>, size=1430, nrcpt=1 (queue active)
3864068 Dec 31 18:31:58 MyDomain postfix/pickup[30678]: 7A00825C8F1: uid=33 from=<bridget_holloway@@--@@chartercommercial.net>
3864069 Dec 31 18:31:58 MyDomain postfix/cleanup[30952]: 7A00825C8F1: message-id=<9fad284759195b015c9545fa91aba0e2@@--@@chartercommercial.net>
3864070 Dec 31 18:31:58 MyDomain opendkim[4680]: 7A00825C8F1: no signing table match for 'bridget_holloway@@--@@chartercommercial.net'
3864071 Dec 31 18:31:58 MyDomain opendkim[4680]: 7A00825C8F1: no signature data

```

---

### Post by lisati on 2015-12-31
It has been a while since I've run a postfix server, but at the very least, I'd recommend something like this for the smtpd_recipient_restrictions settings to help prevent someone from outside your network using your system as an open relay:
```

smtpd_recipient_restrictions =
    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_rbl_client bl.spamcop.net 
    permit

```

---

### Post by lisati on 2015-12-31
*Thread moved to **Server Platforms**.*

---

### Post by Nick_Ellis on 2015-12-31
I'll look into that. According to what I've read that's what the "mynetworks" setting does, only IP's in the "mynetworks" can send mail. 

I've actually solved the problem. The spam was not coming from postfix/relaying/exchange; it was coming from the Charter drupal site. It was running an old version - so perhaps through some exploit they were able to drop in a php file, that... somehow was sending mail. I figured this out for anyone else by stopping apache, and noticed no more mails were building up in the queue. Then I checked access logs of the Charter since all the mails were "from charter" according to postfix. Saw an odd php file being accessed over and over (in my case /sites/default/files/js/general77.php). Removed that file, and restarted apache, and still no more spam in the queue.

So on my To-Do list is to figure out how/if there is a way to prevent drupal hacks from sending mail, while still allowing forms to work (probably no way, but a research project). 

Updated Drupal Core for the offending site as well in an attempt to prevent such an attack again.

Thank you guys for your help.

---

