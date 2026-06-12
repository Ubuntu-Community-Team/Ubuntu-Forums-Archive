---
title: "Running a postfix mail server with spamassassin, clamav, and amavis-new, questions"
date: 2013-08-03
forum: Server Platforms
---

### Post by steven6282 on 2013-08-03
I've ran plenty of ubuntu based web servers and even a few application servers, but this is the first mail server I'm going to be running myself.

Let me start by stating what I'm running.  I'm using Ubuntu Server 12.04 LTS 64 bit.  I followed this guide to setup my initial mail server configuration: [http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

I also added postfix.admin ([http://postfixadmin.sourceforge.net/](http://postfixadmin.sourceforge.net/)) and made some tweaks to all the database queries in order to get it's database structure working correctly.

I also configured roundcube to run on the server in order to have webmail access to the emails.

I will be running multiple domains on this server, each with their own individual users, so I'm doing virtual users and domains.  

I've got all of this working with two domains currently, am able to send and receive emails on them correctly.  (Reverse DNS on the IP is configured and such so that checks out when sending messages, etc)

This is my current /etc/postfix/main.cf
```

myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
mailbox_size_limit = 0
virtual_mailbox_limit = 0
recipient_delimiter = +
inet_interfaces = all
message_size_limit = 0


# SMTP Authentication (SASL)


smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =


# Encrypted transfer (SSL/TLS)


smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/private/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# Basic SPAM prevention


smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unverified_sender, reject_unknown_sender_domain, reject_non_fqdn_sender
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, permit_auth_destination, reject


# Force incoming mail to go through Amavis


content_filter = amavis:[127.0.0.1]:10025
receive_override_options = no_address_mappings


# Virtual user mappings


alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000
virtual_gid_maps =  static:5000
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf

```

So, with all that said, my first thing is do those restrictions look appropriate to filter outer emails sent to my server that shouldn't be, and to make sure no one tries to use my servers smtpd to send out spam?

Next question is concerning the smtpd.  I can't figure out where to make it force authentication when sending emails as well as receiving?  I thought the "smtpd_sasl_auth_enable = yes" setting would have done that, but if I set up a pop account in outlook and don't set it saying My outgoing server requires authentication, it still successfully sends messages.

And then the question on Spam.  I haven't gotten any spam at the addresses I've set up so far to see what it does.  This is the configuration for my /etc/amavis/conf.d/20-debian-defaults file:
```
use strict;


$QUARANTINEDIR = "$MYHOME/virusmails";
$quarantine_subdir_levels = 1; # enable quarantine dir hashing


$log_recip_templ = undef;    # disable by-recipient level-0 log entries
$DO_SYSLOG = 1;              # log via syslogd (preferred)
$syslog_ident = 'amavis';    # syslog ident tag, prepended to all messages
$syslog_facility = 'mail';
$syslog_priority = 'debug';  # switch to info to drop debug output, etc


$enable_db = 1;              # enable use of BerkeleyDB/libdb (SNMP and nanny)
$enable_global_cache = 1;    # enable use of libdb-based cache if $enable_db=1


$inet_socket_port = 10024;   # default listening socket


$sa_spam_subject_tag = '***SPAM*** ';
$sa_tag_level_deflt  = 2.0;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 6.31; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 6.31; # triggers spam evasive actions
$sa_dsn_cutoff_level = 10;   # spam level beyond which a DSN is not sent


$sa_mail_body_size_limit = 200*1024; # don't waste time on SA if mail is larger
$sa_local_tests_only = 0;    # only tests which do not require internet access?


# Quota limits to avoid bombs (like 42.zip)


$MAXLEVELS = 14;
$MAXFILES = 1500;
$MIN_EXPANSION_QUOTA =      100*1024;  # bytes
$MAX_EXPANSION_QUOTA = 300*1024*1024;  # bytes


$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_BOUNCE;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)
$enable_dkim_verification = 0; #disabled to prevent warning


$virus_admin = "postmaster\@$mydomain"; # due to D_DISCARD default


# Set to empty ("") to add no header
$X_HEADER_LINE = "Debian $myproduct_name at $mydomain";


@viruses_that_fake_sender_maps = (new_RE(
  [qr'\bEICAR\b'i => 0],            # av test pattern name
  [qr/.*/ => 1],  # true for everything else
));


@keep_decoded_original_maps = (new_RE(
# qr'^MAIL$',   # retain full original message for virus checking (can be slow)
  qr'^MAIL-UNDECIPHERABLE$', # recheck full mail if it contains undecipherables
  qr'^(ASCII(?! cpio)|text|uuencoded|xxencoded|binhex)'i,
# qr'^Zip archive data',     # don't trust Archive::Zip
));




# for $banned_namepath_re, a new-style of banned table, see amavisd.conf-sample


$banned_filename_re = new_RE(
  qr'\.[^./]*\.(exe|vbs|pif|scr|bat|cmd|com|cpl|dll)\.?$'i,
  qr'\{[0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12}\}?$'i, # Windows Class ID CLSID, strict
  qr'^application/x-msdownload$'i,                  # block these MIME types
  qr'^application/x-msdos-program$'i,
  qr'^application/hta$'i,
  qr'.\.(exe|vbs|pif|scr|bat|cmd|com|cpl)$'i, # banned extension - basic
  qr'^\.(exe-ms)$',                       # banned file(1) types
);

```

/etc/default/spamassassin
```

ENABLED=1
OPTIONS="--create-prefs --max-children 5 --helper-home-dir"
PIDFILE="/var/run/spamd.pid"
CRON=0

```

And /etc/spamassassin/local.cf
```

ifplugin Mail::SpamAssassin::Plugin::Shortcircuit
endif # Mail::SpamAssassin::Plugin::Shortcircuit


```


I'm not sure what exactly is going to happen if a message is flagged as spam level 1?  Is it just going to add the ***SPAM*** to the subject and let it continue to my inbox?  If so, is there anyway to automatically push these into a spam folder in the inbox?

If a spam message is out right denied delivery (which i think the 2nd level is doing?), is that noted somewhere so that I can see when messages are blocked?  I'm assuming it's logged somewhere at least, but not sure where offhand.

I run an online business and want to make sure I'm not going to miss too many customer emails because of spam rules, but at the same time I've been getting a lot of unrelated spam lately at my current email host that has no spam filter.  It's a inevitable thing that I'm going to receive some spam because I list my contact email addresses on the website for people to send me messages, and spam bots probably can just parse that out.  But I would like to be able to weed out the majority of it if possible.


Thanks for any assistance you can provide!  If you need more information, just let me know what you need and I'll be happy to provide it.


EDIT:
Ok so I'm pulling my hair trying to figure out this smtp requiring authentication thing.  I changed my sender and recipient restrions to:
smtpd_sender_restrictions = permit_sasl_authenticated, reject
smtpd_recipient_restrictions = permit_sasl_authenticated, reject
and that seems to force it to require authenticaiton.  However it's rejecting my username and password no matter what I try.

I've confirmed that the /etc/postfix/sasl/smtpd.conf is set to pw_check=saslauthd, and saslauthd is loading with the -a pam option.  /etc/pam.d/smtp has the correct database configuration for auth and account.  I'm not sure what the crypt=1 at the end means on that line though.

I'm at a loss as to why it won't accept my password for the smtp authentication :(

---

### Post by steven6282 on 2013-08-03
Ok, one update.  I still have the questions above about the spam but I think I've gotten the authentication required on sending done.

According to that guid you set /etc/postfix/sasl/smtpd.conf to (updated to my database user and password of course):
```

pwcheck_method: saslauthd
auxprop_plugin: sql
mech_list: plain login
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: mailuserpassword
sql_database: mail
sql_select: SELECT password FROM user WHERE email='%u@%r' AND enabled = 1

```[FONT=Verdana]

However I removed everything except pwcheck_method: saslauthd and mech_list: plain login, and it works now.  So I guess it was trying to use the sql auxprop method.. even though pwcheck_method was set to salsauthd, not aux.  According to postfix.org, auxprop method only works with plain text passwords, and I'm using encrypted passwords.  I don't understand why this change I made works, and if anyone can tell me why, I'd like to know.  It helps to understand why these thing behave the way they do in case I have another problem down the road that may be related =p


EDIT:

Grrrr.... now I remember why I had set the sender and recipient restrictions the way I did to begin with.  Got the authentication working, but now with the sender and recipient restrictions set like that, if I try to send an email in from an outside domain, it immediately gets rejected saying the sender address rejected: access denied.

I don't understand why these restrictions are being replied to sender domains coming from the outside...  I tried adding permit_auth_destination on the recipient restrictions but that didn't do any good either.

EDIT2:
Ok, adding permit_auth_destination to the sender restrictions lets it go through.  However it also makes it so that it doesn't require authentication on the smtp side if the email is going to a valid internal address.  While this should prevent anyone from using my server to send out spam emails to other, it also means someone could use my smtp server to send spam emails to me without authentication....

*sigh*[/FONT]

---

### Post by CharlesA on 2013-08-04
Interesting. I am working on doing the same thing on my VPS, but it is running Debian.

So far I was able to follow this guide:
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

As far as setting up spamassassin and stuff, I used this one:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

Hope that helps.

If you only want IMAP access, don't install dovecot-pop3d and also leave pop3 out of dovecot.conf and leave port 110 commented in 10-master.conf - assuming you follow the tutorial I linked above.

---

### Post by lisati on 2013-08-04
This is a trimmed down version of what mine has:
```

smtpd_recipient_restrictions =
     reject_invalid_hostname,
     reject_non_fqdn_sender,
     reject_non_fqdn_recipient,
     reject_unknown_sender_domain,
     reject_unknown_recipient_domain,
     reject_unauth_pipelining,
     permit_mynetworks,
     permit_sasl_authenticated,
     reject_unauth_destination,
     reject_rbl_client bl.spamcop.net,
     reject_rbl_client cbl.abuseat.org,
     reject_rbl_client pbl.spamhaus.org,
     reject_rbl_client dnsbl-1.uceprotect.net,
     permit

```

(Mine has a few extra lines, relating mainly to auto-generated access restrictions based on scanning my mail log, and a custom policy service.)

---

### Post by steven6282 on 2013-08-04
Have an additional question now.  I'm still working with the above settings to figure out the spam stuff, but I also need to know something else now.

My server is named mailServer, when I send an email from it, it's showing Received from mailServer.localdomain.  I think this is getting a lot of my emails flagged as spam since it's being received form somewhere different than the from domain on the email address.

How do I fix this?  I tried updating my hostname to mail, and that did not change where it is saying is received from.  So not sure what settings effect this.

Also if I do get this changed, is it just going to be stuck saying it was received from one specific domain even though I'm hosting multiple domains?  That kind of sucks if so, I'd rather it say it was received from the domain that I'm actually doing the sending with.  But I guess that would only be possible if I set up a different machine to host each individual domain?

EDIT:
Ok I found where the setting was coming from.  postconf -d showed the default of mydomain = localdomain and myhostname = mailServer.localdomain.  So I put these in my /etc/postfix/main.cf file and set them to one of my hosted domains.  But I'd really like to know if there is a way to make this show what domain it's supposed to be emailing from instead...

---

### Post by CharlesA on 2013-08-04
Check /etc/postfix/main.cf to see what myhostname says.

Mine says:

```
myhostname = enterprise.charlesa.net
```

---

### Post by steven6282 on 2013-08-05
Ok, yeah it definitely appears that my spamassassin isn't doing didley squat with the current settings.  In the last 24 hours since converting to this server fully I've gotten over 50 clearly spam emails.  With things anywhere from ****** in the subject, to things like "You qaulify for a 5000 loan".  Stuff any decently configured working spam software should easily pick up on.

Also had an additional question about the reject_rbl settings.  I'm assuming those are rejecting from black list websites, would spamassassin not check those black lists if it were working correctly?  Seems like something else any descent spam filtering software would do automatically.

EDIT:  see, even this website knows to filter out that word lol.  The male pill :)

---

### Post by steven6282 on 2013-08-06
So yeah... that guide that I used, had a major error which is what caused my spam filter to do nothing at all lol.

```

[COLOR=#110000][FONT=Trebuchet MS][TABLE="width: 574"]
[TR]
[TD="class: code, bgcolor: #EEEEEE"]adduser clamav amavis
[COLOR=#C20CB9]**cat**[/COLOR] [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]null [COLOR=#000000]**>**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]amavis[COLOR=#000000]**/**[/COLOR]conf.d[COLOR=#000000]**/**[/COLOR][COLOR=#000000]15[/COLOR]-content-filter-mode
[COLOR=#C20CB9]**vi**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]amavis[COLOR=#000000]**/**[/COLOR]conf.d[COLOR=#000000]**/**[/COLOR][COLOR=#000000]15[/COLOR]-content-filter-mode[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=Trebuchet MS]Copy/paste the following (no changes required):[/FONT][/COLOR]
[COLOR=#110000][FONT=Trebuchet MS][TABLE="width: 574"]
[TR]
[TD="class: code, bgcolor: #EEEEEE"]use strict;
 
@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);
 
@bypass_spam_checks_maps = (
   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks_re);
 
1;[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

```

Unfortunately the file is 15-content_filter_mode meaning my clamav, and spamassassin was never even enabled through amavis.

Awesome!

---

### Post by CharlesA on 2013-08-06
That should have enabled the spam and virus checks.

What did you do differently that enabled the checks?

---

### Post by nerdtron on 2013-08-06
Just saw your post today. This may sound like a product promotion but I would this mail solution saved my ass. If this is a new mail server installation, why not try iRedMail? A suit with postfix, dovecot, spamassassin, amavis and clamav. Plus complete with security like iptables, fail2ban and logwatch. Oh, and should I mention that it uses roundcube as the webmail?
I can't recommend it enough since it is what we use and the support in the forum is great.
Just my 2 cents :)

---

### Post by nw3f7fF on 2013-08-06
```
     reject_rbl_client cbl.abuseat.org, 
     reject_rbl_client pbl.spamhaus.org,
```

Save yourself the CPU cycles and DNS lookups .... replace those lines with zen.spamhaus.org.

Look it up  ;)

---

### Post by steven6282 on 2013-08-06
> **CharlesA said:**
> That should have enabled the spam and virus checks.

What did you do differently that enabled the checks?

I changed the file name.   I'm not sure why this makes a difference honestly. I was looking at it some more, and it looks like amavis is supposed to load files from conf.d folder in order so that you can add other files that you want and it loads settings from lowest to highest number.  However in this case it did not work for some reason.  Even though 15-content-filter-mode came before 15-content_filter_mode, and should have enabled the settings, it didn't.  As soon as I changed files and restarted amavis it started up correctly.  Maybe something was preventing it from actually starting before and I changed something else that effected it and it was just a coincidence that it started up after I changed the file?  I don't know.  I just know it started workign now.

However, the spamassassin still is not working worth crap.  Since fixing it last night, less than 12 hours ago, already another 15 spam emails have come through and only one had ***SPAM*** in the subject to even show that spamassassin at least thought it was spam and it completely blocked 1.  So it let 13 clearly spam emails come through no problem.

*sigh*

EDIT:
I think I figured out why amavis didn't work correctly initially.  It wasn't the file name that mattered, but 05-node_id.  I looked over the guide again and noticed that it never instructed you to restart amavis.  That is one problem because due to then changes to the files the guide tells you, amavis should be restarted.  The root of the problem, my servers hostname is not a FQDN.  So when I finally did attempt to restart amavis and saw the error that amavis failed to start due to this, I modified 05-node_id to specify $myhostname = "mail.example.com" (except using my domain of course).  I think this is where the real problem was and what prevented amavis from working initially.  It probably gave that error somewhere during the install or boot process and I simply didn't see it.

---

### Post by steven6282 on 2013-08-06
> **nerdtron said:**
> Just saw your post today. This may sound like a product promotion but I would this mail solution saved my ass. If this is a new mail server installation, why not try iRedMail? A suit with postfix, dovecot, spamassassin, amavis and clamav. Plus complete with security like iptables, fail2ban and logwatch. Oh, and should I mention that it uses roundcube as the webmail?
I can't recommend it enough since it is what we use and the support in the forum is great.
Just my 2 cents :)

I may look into this but other than spamassassin not filtering out obvious spam, I'm mostly configured at this point.  That package would've been great a few days ago when I initially started on this lol.  The only thing on it that really appeals to me now is the admin panel that comes with it might be better than the postfix.admin panel I'm currently using.  However, what I'm using is functional :)

But at least I've learned some things on the way.  I'm a lot more familiar with how postfix works now, so can better handle problems that crop up in the future with it.  If I can just figure out the tricks to making spamassassin actually work I'll be golden! haha.

---

### Post by CharlesA on 2013-08-06
> **nerdtron said:**
> Just saw your post today. This may sound like a product promotion but I would this mail solution saved my ass. If this is a new mail server installation, why not try iRedMail? A suit with postfix, dovecot, spamassassin, amavis and clamav. Plus complete with security like iptables, fail2ban and logwatch. Oh, and should I mention that it uses roundcube as the webmail?
I can't recommend it enough since it is what we use and the support in the forum is great.
Just my 2 cents :)

I've used it before, but it was a bit heavy for the VPS I was using. If you have the resources, it's a decent solution.

> **nw3f7fF said:**
> ```
     reject_rbl_client cbl.abuseat.org, 
     reject_rbl_client pbl.spamhaus.org,
```

Save yourself the CPU cycles and DNS lookups .... replace those lines with zen.spamhaus.org.

Look it up  ;)

Sounds handy. It can be found at [http://www.spamhaus.org/zen/](http://www.spamhaus.org/zen/) if anyone is interested.

---

