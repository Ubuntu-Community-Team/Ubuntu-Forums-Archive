---
title: "Postfix SMTP"
date: 2006-05-02
forum: Server Platforms
---

### Post by Sprinker on 2006-05-02
Hi All,

I have a Postfix SMTP server, which, has stopped working.](*,)  I can send email from the computer which Postfix SMTP is running on, with absolutely no worries.  However, whenever I try and send an email using my email server from the internet, it denies relay access (to external domains only).  Does anyone know how to fix this?  I have tried, to no avail.  HELP!!!  I have a feeling that it is in the Postfix main.cf file, but I have no idea where.  Any ideas?

Cheers,

Sprinker

---

### Post by Sprinker on 2006-05-02
Never mind people.  I found what was not working. I had a "myhosts" set.  I commented this out and then everything worked again.  Thanks to anyone who read this anyway.

---

### Post by Sprinker on 2006-05-02
Sorry People, but I have now hit another wall.

Now whenever I attempt to connect to the SMTP server and send mail from the internet, it says:

RCPT TO <*****@gmail.com> Transaction Failed

Please Help.

Cheers,

Sprinker (feeling like an idiot)](*,)

---

### Post by Sprinker on 2006-05-03
Does anyone have any ideas?   If so, please let me know because this is relly starting to effect my business operations.

---

### Post by ape on 2006-05-03
Sprinker,

 The "Transaction failed" message is the default REJECT message from Postfix.  Check your main.cf for the relay_domains directive.  Make sure that this is set correctly for your site.

  You can post your main.cf as that might help with the issue also.

---

### Post by Sprinker on 2006-05-03
Ok, I have found my relay_domains directive, but it is commented out.  I want my SMTP srver to forward to all domains, so people in the office can send email to external addresses,  (it does not give me a error message when I send an email to an internal email address).  I was wondering if you could give me an idea as what is supposed to be in the relay_domains directive.

Cheers,

Sprinker

---

### Post by Sprinker on 2006-05-03
If it helps, here is my main.cf file.  It is the example configuration file, with the appropiate changes made.  Hope somebody can see where I went wrong.

```
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
#mail_owner = postfix
#default_privs = nobody
myhostname = www.techbyteit.ath.cx
mydomain = techbyteit.ath.cx
#myorigin = /etc/mailname
#myorigin = $myhostname
#myorigin = $mydomain
inet_interfaces = all
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost
#proxy_interfaces =
#proxy_interfaces = 1.2.3.4
mydestination =  
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain,
#	mail.$mydomain, www.$mydomain, ftp.$mydomain
#local_recipient_maps = unix:passwd.byname $alias_maps
#local_recipient_maps = proxy:unix:passwd.byname $alias_maps
local_recipient_maps =
unknown_local_recipient_reject_code = 550
#mynetworks_style = class
#mynetworks_style = subnet
mynetworks_style = host
relay_domains = 
#relayhost = $mydomain
#relayhost = [gateway.my.domain]
#relayhost = [mailserver.isp.tld]
#relayhost = uucphost
relayhost = 
#relay_recipient_maps = hash:/etc/postfix/relay_recipients
#in_flow_delay = 1s
#alias_maps = dbm:/etc/aliases
alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases
#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases
#home_mailbox = Mailbox
#home_mailbox = Maildir/
#mail_spool_directory = /var/mail
mail_spool_directory = /var/spool/mail
#mailbox_command = /usr/bin/procmail
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"
#mailbox_transport = lmtp:unix:/file/name
#mailbox_transport = cyrus
#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =
#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
#header_checks = regexp:/etc/postfix/header_checks
#fast_flush_domains = $relay_domains
#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)
smtpd_banner = $myhostname ESMTP $mail_name 
#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20
#debug_peer_level = 2
#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain
debugger_command =
	 PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
	 xxgdb $daemon_directory/$process_name $process_id & sleep 5
# debugger_command =
#	PATH=/bin:/usr/bin:/usr/local/bin; export PATH; (echo cont;
#	echo where) | gdb $daemon_directory/$process_name $process_id 2>&1
#	>$config_directory/$process_name.$process_id.log & sleep 5
# debugger_command =
#	PATH=/bin:/usr/bin:/sbin:/usr/sbin; export PATH; screen
#	-dmS $process_name gdb $daemon_directory/$process_name
#	$process_id & sleep 1
#sendmail_path =
#newaliases_path =
#mailq_path =
setgid_group = virtual
#html_directory =
#manpage_directory =
#sample_directory =
#readme_directory =
delay_warning_time = 4h 
unknown_local_recipient_reject_code = 450 
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
#content_filter = amavis:[127.0.0.1]:10024
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, 
	permit_sasl_authenticated, reject_non_fqdn_recipient, 
	reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, 
	permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,
 reject_non_fqdn_sender, reject_unknown_sender_domain,
 reject_unauth_pipelining, permit
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key 
smtpd_data_restrictions = reject_unauth_pipelining
```

I should also point out that I am using MySQL authentication and MySQL lookups, as well as Virtual Domains.

Cheers,

Sprinker

---

### Post by ape on 2006-05-03
So, from your main.cf you've posted, I see a few issues:

1. mydestination should not be left blank like that.  I personally don't have this set at all in my main.cf.

2. The mynetworks_style = host directive is telling postfix that it will only trust the local machine to send mail.  This is more than likely not what you want.  I have no mynetworks_style directive, but rather use the mynetworks directive and set it equal to the networks of my local LAN that will be connecting to the machine.

    mynetworks = 127.0.0.0/8, 192.168.25.0/24

3. mydestination should be set to at least your domain name (techbytiet.ath.cx).

4. relay_domains should be set to $mydestination at least.


Try adding these items in and restarting the postfix processes.

---

### Post by Sprinker on 2006-05-03
Thanks for your input, but I have added your recommendations to my main.cf file, however, I still get a Transaction Failed message in evolution, and a relay access denied message in thunderbird.  We can all send email from within our local network, however, as some employees are out of the office, they can not use our SMTP server over the internet :confused:.  Do you have any ideas?  Could it be something in my master.cf file??

---

### Post by ape on 2006-05-04
okay, so here is a comment from my main.cf:

# The relay_domains parameter restricts what clients this mail system
# will relay mail from, or what destinations this system will relay
# mail to.  See the smtpd_recipient_restrictions restriction in the
# file sample-smtpd.cf for detailed information.
#
# By default, Postfix relays mail
# - from "trusted" clients whose IP address matches $mynetworks,
# - from "trusted" clients matching $relay_domains or subdomains thereof,
# - from untrusted clients to destinations that match $relay_domains
#   or subdomains thereof, except addresses with sender-specified routing.
# The default relay_domains value is $mydestination.


What I'm thinking here is that the employees that are connecting in from outside the network are not coming in through a VPN or dial-in, and so are not connecting to the postfix server as a network address that would match the $mynetworks directive, or a domain that matches your $relay_domains directive.  Take a look at the /usr/share/doc/postfix/SMTPD_ACCESS_README.gz document for more info on this (pretty good read).

Since you obviously don't want to be an open relay, you need to find some common method for these external employees to be able to be recognized by the postfix server to be allowed to relay through.

---

