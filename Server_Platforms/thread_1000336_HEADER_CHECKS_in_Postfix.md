---
title: "HEADER_CHECKS in Postfix"
date: 2008-12-02
forum: Server Platforms
---

### Post by Mucker212 on 2008-12-02
Hi,

I been told to alter the header_checks file in /etc/postfix/

I cant find no "header_checks" file or folder. Can anyone help me or tell me why it isnt here?

Im using a Ubuntu dedicated web server with ubuntu 6.0.6

Please help.

---

### Post by Mucker212 on 2008-12-03
Ok,

I tried adding a header_checks to my /etc/postfix/ folder with the following  command:

/^X-Spam-Flag:.YES/ REJECT spam

I want to reject all spam as iam reciveing approx 200 a day.

There was no "header_checks" file in the appropriate folder.

How do I create one. I used text editor and copied it to the postfix folder on my server. Then renamed it and removed the .txt at the end of the file.

I then uncommented the line:
header_checks = regexp:/etc/postfix/header_checks

in main.cf   I then restarted postfix and now I cant send or recieve emails. So itake it either my "header_checks" file is wrong or something else.


Please anyone?

---

### Post by Mucker212 on 2008-12-03
Can anyone help me out here? What info am I required to post to help you know what my problem is?

Do people reply to this?

---

### Post by CrucifiedEgo on 2008-12-03
What's in your /var/log/mail.log when you try to send/recieve mail?  

Also, have you tried procmail on the MDA side to filter the mail?  Are you using any blacklists/greylisting?  All those can help much more than arbitrarily throwing out messages which could be ham.

For the record, one bump ever 24 hours is generally sufficient especially in the slower server subforum.

---

### Post by Mucker212 on 2008-12-03
/i will forward my mail log ASAP.

Also i couldnt get procmail to work either. I just want to remove spamassissn marked posts of 15* and higher. Aparrently postfix can do this. I get that many spam I dont care about the ham.

---

### Post by Mucker212 on 2008-12-03
My mail log is huge, also I dont understand most of it. I got a few failed things and choking going on

---

### Post by CrucifiedEgo on 2008-12-03
> **Mucker212 said:**
> My mail log is huge, also I dont understand most of it. I got a few failed things and choking going on

easy enough.  stop postfix, delete or mv the log, restart, send a test message, post the output.

---

### Post by Mucker212 on 2008-12-03
I moved the mail.log

Redone the emails with the settings and no mail.log file is there?

---

### Post by CrucifiedEgo on 2008-12-03
> **Mucker212 said:**
> I moved the mail.log

Redone the emails with the settings and no mail.log file is there?

Did you restart postfix?  otherwise, the file descriptor follows the mv and just writes to wherever you moved it to.

---

### Post by Mucker212 on 2008-12-03
There is a mail.warn file. 

Here is some of what it says.

```
Dec  3 18:00:57 ubuntu postfix/smtpd[30120]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:00:58 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30120 exit status 1
Dec  3 18:00:58 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:01:58 ubuntu postfix/smtpd[30130]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:01:59 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30130 exit status 1
Dec  3 18:01:59 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:02:59 ubuntu postfix/smtpd[30133]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:03:00 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30133 exit status 1
Dec  3 18:03:00 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:04:00 ubuntu postfix/smtpd[30135]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:04:01 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30135 exit status 1
Dec  3 18:04:01 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:05:01 ubuntu postfix/smtpd[30149]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:05:02 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30149 exit status 1
Dec  3 18:05:02 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:06:02 ubuntu postfix/smtpd[30161]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:06:03 ubuntu postfix/master[30084]: warning: process /usr/lib/postfix/smtpd pid 30161 exit status 1
Dec  3 18:06:03 ubuntu postfix/master[30084]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:22:55 ubuntu postfix/smtpd[31496]: warning: 201.170.187.125: hostname 201.170.187.125.dsl.dyn.telnor.net verification failed: Name or service not known
Dec  3 18:41:16 ubuntu postfix/smtpd[31803]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:41:17 ubuntu postfix/master[31778]: warning: process /usr/lib/postfix/smtpd pid 31803 exit status 1
Dec  3 18:41:17 ubuntu postfix/master[31778]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  3 18:42:17 ubuntu postfix/smtpd[31813]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  3 18:42:18 ubuntu postfix/master[31778]: warning: process /usr/lib/postfix/smtpd pid 31813 exit status 1
Dec  3 18:42:18 ubuntu postfix/master[31778]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

---

### Post by Mucker212 on 2008-12-03
> **CrucifiedEgo said:**
> Did you restart postfix?  otherwise, the file descriptor follows the mv and just writes to wherever you moved it to.

Yes I restarted postfix and no mail.log is there now?

---

### Post by Mucker212 on 2008-12-03
it seems to be dumping the junk mail but I cant send out any. and im getting no mail.log file now? Does it take time to update? I thought it would have been instantly

---

### Post by Mucker212 on 2008-12-04
Ok my Mail.log file has appeared again. And it is full from today. Mostly spammers sending stuff in.

My main Problem is getting the /etc/postfix/main.cf header_checks line to do anything. When ever I un comment the line my outgoing mail and incoming mail stops working.

Below is a copy of my main.cf

If I uncomment the highlighted line below then all my mail stops working. I also created the header_checks file and put the appropriate command in and it is simply not having it. So I comment the highlighted line out and restart postfix so I can send emails again.

PLEASE HELP!!!!

```
# Global Postfix configuration file. This file lists only a subset
# of all 300+ parameters. See the sample-xxx.cf files for a full list.
# 
# The general format is lines with parameter = value pairs. Lines
# that begin with whitespace continue the previous line. A value can
# contain references to other $names or ${name}s.
#
# NOTE - CHANGE NO MORE THAN 2-3 PARAMETERS AT A TIME, AND TEST IF
# POSTFIX STILL WORKS AFTER EVERY CHANGE.

# SOFT BOUNCE
#
# The soft_bounce parameter provides a limited safety net for
# testing.  When soft_bounce is enabled, mail will remain queued that
# would otherwise bounce. This parameter disables locally-generated
# bounces, and prevents the SMTP server from rejecting mail permanently
# (by changing 5xx replies into 4xx replies). However, soft_bounce
# is no cure for address rewriting mistakes or mail routing mistakes.
#
#soft_bounce = no

# LOCAL PATHNAME INFORMATION
#
# The queue_directory specifies the location of the Postfix queue.
# This is also the root directory of Postfix daemons that run chrooted.
# See the files in examples/chroot-setup for setting up Postfix chroot
# environments on different UNIX systems.
#
queue_directory = /var/spool/postfix

# The command_directory parameter specifies the location of all
# postXXX commands.
#
command_directory = /usr/sbin

# The daemon_directory parameter specifies the location of all Postfix
# daemon programs (i.e. programs listed in the master.cf file). This
# directory must be owned by root.
#
daemon_directory = /usr/lib/postfix

# QUEUE AND PROCESS OWNERSHIP
#
# The mail_owner parameter specifies the owner of the Postfix queue
# and of most Postfix daemon processes.  Specify the name of a user
# account THAT DOES NOT SHARE ITS USER OR GROUP ID WITH OTHER ACCOUNTS
# AND THAT OWNS NO OTHER FILES OR PROCESSES ON THE SYSTEM.  In
# particular, don't specify nobody or daemon. PLEASE USE A DEDICATED
# USER.
#
mail_owner = postfix

# The default_privs parameter specifies the default rights used by
# the local delivery agent for delivery to external file or command.
# These rights are used in the absence of a recipient user context.
# DO NOT SPECIFY A PRIVILEGED USER OR THE POSTFIX OWNER.
#
#default_privs = nobody

# INTERNET HOST AND DOMAIN NAMES
# 
# The myhostname parameter specifies the internet hostname of this
# mail system. The default is to use the fully-qualified domain name
# from gethostname(). $myhostname is used as a default value for many
# other configuration parameters.
#
#myhostname = host.domain.tld
#myhostname = virtual.domain.tld

# The mydomain parameter specifies the local internet domain name.
# The default is to use $myhostname minus the first component.
# $mydomain is used as a default value for many other configuration
# parameters.
#
#mydomain = domain.tld

# SENDING MAIL
# 
# The myorigin parameter specifies the domain that locally-posted
# mail appears to come from. The default is to append $myhostname,
# which is fine for small sites.  If you run a domain with multiple
# machines, you should (1) change this to $mydomain and (2) set up
# a domain-wide alias database that aliases each user to
# user@that.users.mailhost.
#
# For the sake of consistency between sender and recipient addresses,
# myorigin also specifies the default domain name that is appended
# to recipient addresses that have no @domain part.
#
#myorigin = $myhostname
#myorigin = $mydomain

# RECEIVING MAIL

# The inet_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on.  By default,
# the software claims all active interfaces on the machine. The
# parameter also controls delivery of mail to user@[ip.address].
#
# See also the proxy_interfaces parameter, for network addresses that
# are forwarded to us via a proxy or network address translator.
#
# Note: you need to stop/start Postfix when this parameter changes.
#
#inet_interfaces = all
#inet_interfaces = $myhostname
#inet_interfaces = $myhostname, localhost
#inet_interfaces = all

# The proxy_interfaces parameter specifies the network interface
# addresses that this mail system receives mail on by way of a
# proxy or network address translation unit. This setting extends
# the address list specified with the inet_interfaces parameter.
#
# You must specify your proxy/NAT addresses when your system is a
# backup MX host for other domains, otherwise mail delivery loops
# will happen when the primary MX host is down.
#
#proxy_interfaces =
#proxy_interfaces = 1.2.3.4

# The mydestination parameter specifies the list of domains that this
# machine considers itself the final destination for.
#
# These domains are routed to the delivery agent specified with the
# local_transport parameter setting. By default, that is the UNIX
# compatible delivery agent that lookups all recipients in /etc/passwd
# and /etc/aliases or their equivalent.
#
# The default is $myhostname + localhost.$mydomain.  On a mail domain
# gateway, you should also include $mydomain.
#
# Do not specify the names of virtual domains - those domains are
# specified elsewhere (see sample-virtual.cf).
#
# Do not specify the names of domains that this machine is backup MX
# host for. Specify those names via the relay_domains settings for
# the SMTP server, or use permit_mx_backup if you are lazy (see
# sample-smtpd.cf).
#
# The local machine is always the final destination for mail addressed
# to user@[the.net.work.address] of an interface that the mail system
# receives mail on (see the inet_interfaces parameter).
#
# Specify a list of host or domain names, /file/name or type:table
# patterns, separated by commas and/or whitespace. A /file/name
# pattern is replaced by its contents; a type:table is matched when
# a name matches a lookup key (the right-hand side is ignored).
# Continue long lines by starting the next line with whitespace.
#
# DO NOT LIST RELAY DESTINATIONS IN MYDESTINATION.
# SPECIFY RELAY DESTINATIONS IN RELAY_DOMAINS.
#
# See also below, section "REJECTING MAIL FOR UNKNOWN LOCAL USERS".
#
mydestination = $myhostname, localhost.$mydomain
#mydestination = $myhostname, localhost.$mydomain $mydomain
#mydestination = $myhostname, localhost.$mydomain, $mydomain,
#	mail.$mydomain, www.$mydomain, ftp.$mydomain

# REJECTING MAIL FOR UNKNOWN LOCAL USERS
#
# The local_recipient_maps parameter specifies optional lookup tables
# with all names or addresses of users that are local with respect
# to $mydestination and $inet_interfaces.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown local users. This parameter is defined by default.
#
# To turn off local recipient checking in the SMTP server, specify
# local_recipient_maps = (i.e. empty).
#
# The default setting assumes that you use the default Postfix local
# delivery agent for local delivery. You need to update the
# local_recipient_maps setting if:
#
# - You define $mydestination domain recipients in files other than
#   /etc/passwd, /etc/aliases, or the $virtual_alias_maps files.
#   For example, you define $mydestination domain recipients in    
#   the $virtual_mailbox_maps files.
#
# - You redefine the local delivery agent in master.cf.
#
# - You redefine the "local_transport" setting in main.cf.
#
# - You use the "luser_relay", "mailbox_transport", or "fallback_transport"
#   feature of the Postfix local delivery agent (see sample-local.cf).
#
# Details are described in the LOCAL_RECIPIENT_README file.
#
# Beware: if the Postfix SMTP server runs chrooted, you probably have
# to access the passwd file via the proxymap service, in order to
# overcome chroot restrictions. The alternative, having a copy of
# the system passwd file in the chroot jail is just not practical.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify a bare username, an @domain.tld
# wild-card, or specify a user@domain.tld address.
# 
#local_recipient_maps = unix:passwd.byname $alias_maps
#local_recipient_maps = proxy:unix:passwd.byname $alias_maps
#local_recipient_maps =

# The unknown_local_recipient_reject_code specifies the SMTP server
# response code when a recipient domain matches $mydestination or
# $inet_interfaces, while $local_recipient_maps is non-empty and the
# recipient address or address local-part is not found.
#
# The default setting is 550 (reject mail) but it is safer to start
# with 450 (try again later) until you are certain that your
# local_recipient_maps settings are OK.
#
#unknown_local_recipient_reject_code = 550
unknown_local_recipient_reject_code = 450

# TRUST AND RELAY CONTROL

# The mynetworks parameter specifies the list of "trusted" SMTP
# clients that have more privileges than "strangers".
#
# In particular, "trusted" SMTP clients are allowed to relay mail
# through Postfix.  See the smtpd_recipient_restrictions parameter
# in file sample-smtpd.cf.
#
# You can specify the list of "trusted" network addresses by hand
# or you can let Postfix do it for you (which is the default).
#
# By default (mynetworks_style = subnet), Postfix "trusts" SMTP
# clients in the same IP subnetworks as the local machine.
# On Linux, this does works correctly only with interfaces specified
# with the "ifconfig" command.
# 
# Specify "mynetworks_style = class" when Postfix should "trust" SMTP
# clients in the same IP class A/B/C networks as the local machine.
# Don't do this with a dialup site - it would cause Postfix to "trust"
# your entire provider's network.  Instead, specify an explicit
# mynetworks list by hand, as described below.
#  
# Specify "mynetworks_style = host" when Postfix should "trust"
# only the local machine.
# 
#mynetworks_style = class
#mynetworks_style = subnet
mynetworks_style = host

# Alternatively, you can specify the mynetworks list by hand, in
# which case Postfix ignores the mynetworks_style setting.
#
# Specify an explicit list of network/netmask patterns, where the
# mask specifies the number of bits in the network part of a host
# address.
#
# You can also specify the absolute pathname of a pattern file instead
# of listing the patterns here. Specify type:table for table-based lookups
# (the value on the table right-hand side is not used).
#
#mynetworks = 168.100.189.0/28, 127.0.0.0/8
#mynetworks = $config_directory/mynetworks
#mynetworks = hash:/etc/postfix/network_table

# The relay_domains parameter restricts what destinations this system will
# relay mail to.  See the smtpd_recipient_restrictions restriction in the
# file sample-smtpd.cf for detailed information.
#
# By default, Postfix relays mail
# - from "trusted" clients (IP address matches $mynetworks) to any destination,
# - from "untrusted" clients to destinations that match $relay_domains or
#   subdomains thereof, except addresses with sender-specified routing.
# The default relay_domains value is $mydestination.
# 
# In addition to the above, the Postfix SMTP server by default accepts mail
# that Postfix is final destination for:
# - destinations that match $inet_interfaces,
# - destinations that match $mydestination
# - destinations that match $virtual_alias_domains,
# - destinations that match $virtual_mailbox_domains.
# These destinations do not need to be listed in $relay_domains.
# 
# Specify a list of hosts or domains, /file/name patterns or type:name
# lookup tables, separated by commas and/or whitespace.  Continue
# long lines by starting the next line with whitespace. A file name
# is replaced by its contents; a type:name table is matched when a
# (parent) domain appears as lookup key.
#
# NOTE: Postfix will not automatically forward mail for domains that
# list this system as their primary or backup MX host. See the
# permit_mx_backup restriction in the file sample-smtpd.cf.
#
#relay_domaixxxns = $mydestination

# INTERNET OR INTRANET

# The relayhost parameter specifies the default host to send mail to
# when no entry is matched in the optional transport(5) table. When
# no relayhost is given, mail is routed directly to the destination.
#
# On an intranet, specify the organizational domain name. If your
# internal DNS uses no MX records, specify the name of the intranet
# gateway host instead.
#
# In the case of SMTP, specify a domain, host, host:port, [host]:port,
# [address] or [address]:port; the form [host] turns off MX lookups.
#
# If you're connected via UUCP, see also the default_transport parameter.
#
#relayhost = $mydomain
#relayhost = gateway.my.domain
#relayhost = uucphost
#relayhost = [an.ip.add.ress]

# REJECTING UNKNOWN RELAY USERS
#
# The relay_recipient_maps parameter specifies optional lookup tables
# with all addresses in the domains that match $relay_domains.
#
# If this parameter is defined, then the SMTP server will reject
# mail for unknown relay users. This feature is off by default.
#
# The right-hand side of the lookup tables is conveniently ignored.
# In the left-hand side, specify an @domain.tld wild-card, or specify
# a user@domain.tld address.
# 
#relay_recipient_maps = hash:/etc/postfix/relay_recipients

# INPUT RATE CONTROL
#
# The in_flow_delay configuration parameter implements mail input
# flow control. This feature is turned on by default, although it
# still needs further development (it's disabled on SCO UNIX due
# to an SCO bug).
# 
# A Postfix process will pause for $in_flow_delay seconds before
# accepting a new message, when the message arrival rate exceeds the
# message delivery rate. With the default 100 SMTP server process
# limit, this limits the mail inflow to 100 messages a second more
# than the number of messages delivered per second.
# 
# Specify 0 to disable the feature. Valid delays are 0..10.
# 
#in_flow_delay = 1s

# ADDRESS REWRITING
#
# Insert text from sample-rewrite.cf if you need to do address
# masquerading.
#
# Insert text from sample-canonical.cf if you need to do address
# rewriting, or if you need username->Firstname.Lastname mapping.

# ADDRESS REDIRECTION (VIRTUAL DOMAIN)
#
# Insert text from sample-virtual.cf if you need virtual domain support.

# "USER HAS MOVED" BOUNCE MESSAGES
#
# Insert text from sample-relocated.cf if you need "user has moved"
# style bounce messages. Alternatively, you can bounce recipients
# with an SMTP server access table. See sample-smtpd.cf.

# TRANSPORT MAP
#
# Insert text from sample-transport.cf if you need explicit routing.

# ALIAS DATABASE
#
# The alias_maps parameter specifies the list of alias databases used
# by the local delivery agent. The default list is system dependent.
#
# On systems with NIS, the default is to search the local alias
# database, then the NIS alias database. See aliases(5) for syntax
# details.
# 
# If you change the alias database, run "postalias /etc/aliases" (or
# wherever your system stores the mail alias file), or simply run
# "newaliases" to build the necessary DBM or DB file.
#
# It will take a minute or so before changes become visible.  Use
# "postfix reload" to eliminate the delay.
#
#alias_maps = dbm:/etc/aliases
alias_maps = hash:/etc/aliases
#alias_maps = hash:/etc/aliases, nis:mail.aliases
#alias_maps = netinfo:/aliases

# The alias_database parameter specifies the alias database(s) that
# are built with "newaliases" or "sendmail -bi".  This is a separate
# configuration parameter, because alias_maps (see above) may specify
# tables that are not necessarily all under control by Postfix.
#
#alias_database = dbm:/etc/aliases
#alias_database = dbm:/etc/mail/aliases
#alias_database = hash:/etc/aliases
#alias_database = hash:/etc/aliases, hash:/opt/majordomo/aliases

# ADDRESS EXTENSIONS (e.g., user+foo)
#
# The recipient_delimiter parameter specifies the separator between
# user names and address extensions (user+foo). See canonical(5),
# local(8), relocated(5) and virtual(5) for the effects this has on
# aliases, canonical, virtual, relocated and .forward file lookups.
# Basically, the software tries user+foo and .forward+foo before
# trying user and .forward.
#
#recipient_delimiter = +

# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
#
#home_mailbox = Mailbox
#home_mailbox = Maildir/
 
# The mail_spool_directory parameter specifies the directory where
# UNIX-style mailboxes are kept. The default setting depends on the
# system type.
#
#mail_spool_directory = /var/mail
#mail_spool_directory = /var/spool/mail

# The mailbox_command parameter specifies the optional external
# command to use instead of mailbox delivery. The command is run as
# the recipient with proper HOME, SHELL and LOGNAME environment settings.
# Exception:  delivery for root is done as $default_user.
#
# Other environment variables of interest: USER (recipient username),
# EXTENSION (address extension), DOMAIN (domain part of address),
# and LOCAL (the address localpart).
#
# Unlike other Postfix configuration parameters, the mailbox_command
# parameter is not subjected to $parameter substitutions. This is to
# make it easier to specify shell syntax (see example below).
#
# Avoid shell meta characters because they will force Postfix to run
# an expensive shell process. Procmail alone is expensive enough.
#
# IF YOU USE THIS TO DELIVER MAIL SYSTEM-WIDE, YOU MUST SET UP AN
# ALIAS THAT FORWARDS MAIL FOR ROOT TO A REAL USER.
#
#mailbox_command = /some/where/procmail
#mailbox_command = /some/where/procmail -a "$EXTENSION"
#mailbox_command = /usr/bin/procmail -f- -a "$USER"
# The mailbox_transport specifies the optional transport in master.cf
# to use after processing aliases and .forward files. This parameter
# has precedence over the mailbox_command, fallback_transport and
# luser_relay parameters.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#mailbox_transport = lmtp:unix:/file/name
#mailbox_transport = cyrus

# The fallback_transport specifies the optional transport in master.cf
# to use for recipients that are not found in the UNIX passwd database.
# This parameter has precedence over the luser_relay parameter.
#
# Specify a string of the form transport:nexthop, where transport is
# the name of a mail delivery transport defined in master.cf.  The
# :nexthop part is optional. For more details see the sample transport
# configuration file.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must update the "local_recipient_maps" setting in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#fallback_transport = lmtp:unix:/file/name
#fallback_transport = cyrus
#fallback_transport =

# The luser_relay parameter specifies an optional destination address
# for unknown recipients.  By default, mail for unknown@$mydestination
# and unknown@[$inet_interfaces] is returned as undeliverable.
#
# The following expansions are done on luser_relay: $user (recipient
# username), $shell (recipient shell), $home (recipient home directory),
# $recipient (full recipient address), $extension (recipient address
# extension), $domain (recipient domain), $local (entire recipient
# localpart), $recipient_delimiter. Specify ${name?value} or
# ${name:value} to expand value only when $name does (does not) exist.
#
# luser_relay works only for the default Postfix local delivery agent.
#
# NOTE: if you use this feature for accounts not in the UNIX password
# file, then you must specify "local_recipient_maps =" (i.e. empty) in
# the main.cf file, otherwise the SMTP server will reject mail for    
# non-UNIX accounts with "User unknown in local recipient table".
#
#luser_relay = $user@other.host
#luser_relay = $local@other.host
#luser_relay = admin+$local
  
# JUNK MAIL CONTROLS
# 
# The controls listed here are only a very small subset. See the file
# sample-smtpd.cf for an elaborate list of anti-UCE controls.

# The header_checks parameter specifies an optional table with patterns
# that each logical message header is matched against, including
# headers that span multiple physical lines.
#
# By default, these patterns also apply to MIME headers and to the
# headers of attached messages. With older Postfix versions, MIME and
# attached message headers were treated as body text.
#
# For details, see the sample-filter.cf file.
#
[COLOR="Purple"]# header_checks = regexp:/etc/postfix/header_checks[/COLOR]
# header_checks = pcre:/etc/postfix/header_checks

# FAST ETRN SERVICE
#
# Postfix maintains per-destination logfiles with information about
# deferred mail, so that mail can be flushed quickly with the SMTP
# "ETRN domain.tld" command, or by executing "sendmail -qRdomain.tld".
# 
# By default, Postfix maintains deferred mail logfile information
# only for destinations that Postfix is willing to relay to (as
# specified in the relay_domains parameter). For other destinations,
# Postfix attempts to deliver ALL queued mail after receiving the
# SMTP "ETRN domain.tld" command, or after execution of "sendmail
# -qRdomain.tld". This can be slow when a lot of mail is queued.
# 
# The fast_flush_domains parameter controls what destinations are
# eligible for this "fast ETRN/sendmail -qR" service.
# 
#fast_flush_domains = $relay_domains
#fast_flush_domains =

# SHOW SOFTWARE VERSION OR NOT
#
# The smtpd_banner parameter specifies the text that follows the 220
# code in the SMTP server's greeting banner. Some people like to see
# the mail version advertised. By default, Postfix shows no version.
#
# You MUST specify $myhostname at the start of the text. That is an
# RFC requirement. Postfix itself does not care.
#
#smtpd_banner = $myhostname ESMTP $mail_name
#smtpd_banner = $myhostname ESMTP $mail_name ($mail_version)

# PARALLEL DELIVERY TO THE SAME DESTINATION
#
# How many parallel deliveries to the same user or domain? With local
# delivery, it does not make sense to do massively parallel delivery
# to the same user, because mailbox updates must happen sequentially,
# and expensive pipelines in .forward files can cause disasters when
# too many are run at the same time. With SMTP deliveries, 10
# simultaneous connections to the same domain could be sufficient to
# raise eyebrows.
# 
# Each message delivery transport has its XXX_destination_concurrency_limit
# parameter.  The default is $default_destination_concurrency_limit for
# most delivery transports. For the local delivery agent the default is 2.

#local_destination_concurrency_limit = 2
#default_destination_concurrency_limit = 20

# DEBUGGING CONTROL
#
# The debug_peer_level parameter specifies the increment in verbose
# logging level when an SMTP client or server host name or address
# matches a pattern in the debug_peer_list parameter.
#
debug_peer_level = 2

# The debug_peer_list parameter specifies an optional list of domain
# or network patterns, /file/name patterns or type:name tables. When
# an SMTP client or server host name or address matches a pattern,
# increase the verbose logging level by the amount specified in the
# debug_peer_level parameter.
#
#debug_peer_list = 127.0.0.1
#debug_peer_list = some.domain

# The debugger_command specifies the external command that is executed
# when a Postfix daemon program is run with the -D option.
#
# Use "command .. & sleep 5" so that the debugger can attach before
# the process marches on. If you use an X-based debugger, be sure to
# set up your XAUTHORITY environment variable before starting Postfix.
#
debugger_command =
	 PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
	 ddd $daemon_directory/$process_name $process_id & sleep 5

# If you don't have X installed on the Postfix machine, try:
# debugger_command =
#	PATH=/bin:/usr/bin:/usr/local/bin; export PATH; (echo cont;
#	echo where) | gdb $daemon_directory/$process_name $process_id 2>&1
#	>$config_directory/$process_name.$process_id.log & sleep 5

# INSTALL-TIME CONFIGURATION INFORMATION
#
# The following parameters are used when installing a new Postfix version.
# 
# sendmail_path: The full pathname of the Postfix sendmail command.
# This is the Sendmail-compatible mail posting interface.
# 
sendmail_path = /usr/sbin/sendmail.postfix

# newaliases_path: The full pathname of the Postfix newaliases command.
# This is the Sendmail-compatible command to build alias databases.
#
newaliases_path = /usr/bin/newaliases.postfix

# mailq_path: The full pathname of the Postfix mailq command.  This
# is the Sendmail-compatible mail queue listing command.
# 
mailq_path = /usr/bin/mailq.postfix

# setgid_group: The group for mail submission and queue management
# commands.  This must be a group name with a numerical group ID that
# is not shared with other accounts, not even with the Postfix account.
#
setgid_group = postdrop

# manpage_directory: The location of the Postfix on-line manual pages.
#
manpage_directory = /usr/share/man

# sample_directory: The location of the Postfix sample configuration files.
#
sample_directory = /usr/share/doc/postfix-2.0.18/samples

# readme_directory: The location of the Postfix README files.
#
readme_directory = /usr/share/doc/postfix-2.0.18/README_FILES
alias_database = hash:/etc/aliases

# Following entries REQUIRED by Matrix control panel
virtual_maps = hash:/etc/postfix/virtual
transport_maps = hash:/etc/postfix/transport
virtual_mailbox_domains = $transport_maps
local_destination_concurrency_limit=1
maildrop_destination_concurrency_limit=1
maildrop_destination_recipient_limit=1
relay_domains=$mydestination
smtpd_recipient_restrictions=permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable=yes
smtpd_sasl_security_options=noanonymous
```

---

### Post by CrucifiedEgo on 2008-12-04
Which line are you uncommenting?  they're two different formats(PCRE vs regexp).  Can you post the /etc/postfix/header_checks file contents as well?

---

### Post by Mucker212 on 2008-12-04
Im uncommenting the regexp one . I added the pcre one to test it.

```
/^X-Spam-Level: \*{15,}.*/ DISCARD
```

I had to create this header checks file as I didnt have one already

---

### Post by Mucker212 on 2008-12-05
Ok,

Here is a a few lines at the bottom of my mail.log file after I set postfix to do header_checks.

The emails dont come in properly and sending emails just sits there in my email client not sending out.

D```
ec  5 14:01:34 ubuntu postfix/smtp[21488]: D83FB2B2CF: to=<spiror@fiiqmx.net>, relay=none, delay=117105, status=deferred (connect to bounce.powerparcel.com[38.98.193.102]: Connection timed out)
Dec  5 14:01:45 ubuntu postfix/smtp[21489]: 56EBA2B2F4: host colossus.xo.com[207.155.253.126] said: 452 <clutterwtg19@grablecpa.com>: Recipient address rejected: Domain not active [1DJID10L9700] (in reply to RCPT TO command)
Dec  5 14:01:47 ubuntu postfix/smtpd[21500]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:01:48 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21500 exit status 1
Dec  5 14:01:48 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:02:26 ubuntu postfix/smtp[21489]: 56EBA2B2F4: to=<clutterwtg19@grablecpa.com>, relay=tremendous.xo.com[207.155.249.233], delay=11749, status=deferred (host tremendous.xo.com[207.155.249.233] said: 452 <clutterwtg19@grablecpa.com>: Recipient address rejected: Domain not active [0UJID296JC00] (in reply to RCPT TO command))
```

---

### Post by Mucker212 on 2008-12-05
Im thinking this line in mail.log has something to do with something. Inbox emails and out goings dont work now.

```
Dec  5 14:08:54 ubuntu postfix/smtpd[21555]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
```

---

### Post by Mucker212 on 2008-12-05
here is more of my mail.log

```
Dec  5 14:34:25 ubuntu postfix/smtp[21743]: F1E0A2B2E9: to=<gyytyeqimkosu@atlaswebmail.com>, relay=none, delay=338796, status=deferred (connect to atlaswebmail.com[64.251.30.195]: Connection refused)
Dec  5 14:34:25 ubuntu postfix/smtp[21736]: connect to phayze.com[208.73.210.121]: Connection refused (port 25)
Dec  5 14:34:25 ubuntu postfix/smtp[21736]: E7C412B2EE: to=<todde@phayze.com>, relay=none, delay=108568, status=deferred (connect to phayze.com[208.73.210.121]: Connection refused)
Dec  5 14:34:25 ubuntu postfix/smtp[21740]: connect to mail.jc-schools.net[96.4.88.131]: Connection refused (port 25)
Dec  5 14:34:25 ubuntu postfix/smtp[21740]: 3C23F2B2E1: to=<TerrisnivelDenton@jc-schools.net>, relay=none, delay=371451, status=deferred (connect to mail.jc-schools.net[96.4.88.131]: Connection refused)
Dec  5 14:34:28 ubuntu postfix/smtp[21738]: connect to mx1.thesignandtravel.com[208.73.210.50]: Connection refused (port 25)
Dec  5 14:34:28 ubuntu postfix/smtp[21738]: BDF962B2EC: to=<1-5374100-e-flog-it.com?laura@mx1.thesignandtravel.com>, relay=none, delay=104447, status=deferred (connect to mx1.thesignandtravel.com[208.73.210.50]: Connection refused)
Dec  5 14:34:55 ubuntu postfix/smtp[21735]: connect to bounce.powerparcel.com[38.98.193.102]: Connection timed out (port 25)
Dec  5 14:34:55 ubuntu postfix/smtp[21735]: 114C42B2F2: to=<souaf@fiiqmx.net>, relay=none, delay=26852, status=deferred (connect to bounce.powerparcel.com[38.98.193.102]: Connection timed out)
Dec  5 14:34:55 ubuntu postfix/smtp[21739]: connect to hideakifan.com[69.46.228.60]: Connection timed out (port 25)
Dec  5 14:34:55 ubuntu postfix/smtp[21741]: connect to bounce.powerparcel.com[38.98.193.102]: Connection timed out (port 25)
Dec  5 14:34:55 ubuntu postfix/smtp[21739]: 9A6012B2E8: to=<shigenarp@hideakifan.com>, relay=none, delay=318413, status=deferred (connect to hideakifan.com[69.46.228.60]: Connection timed out)
Dec  5 14:34:55 ubuntu postfix/smtp[21741]: 395562B2D7: to=<shivaprab@fiiqmx.net>, relay=none, delay=163628, status=deferred (connect to bounce.powerparcel.com[38.98.193.102]: Connection timed out)
Dec  5 14:35:20 ubuntu postfix/smtpd[21748]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:35:21 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21748 exit status 1
Dec  5 14:35:21 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:36:21 ubuntu postfix/smtpd[21760]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:36:22 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21760 exit status 1
Dec  5 14:36:22 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:37:22 ubuntu postfix/smtpd[21764]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:37:23 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21764 exit status 1
Dec  5 14:37:23 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:38:23 ubuntu postfix/smtpd[21768]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:38:24 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21768 exit status 1
Dec  5 14:38:24 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:39:24 ubuntu postfix/smtpd[21781]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:39:25 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21781 exit status 1
Dec  5 14:39:25 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:40:25 ubuntu postfix/smtpd[21783]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:40:26 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21783 exit status 1
Dec  5 14:40:26 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec  5 14:41:26 ubuntu postfix/smtpd[21796]: fatal: open dictionary: expecting "type:name" form instead of "header_checks"
Dec  5 14:41:27 ubuntu postfix/master[21483]: warning: process /usr/lib/postfix/smtpd pid 21796 exit status 1
Dec  5 14:41:27 ubuntu postfix/master[21483]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

---

### Post by MJN on 2008-12-05
A few questions:

1. Have you actually set this server up yourself? If so, has it ever worked? Post **your** config (i.e. not including the defaults) by posting the output of [B]postconf -n

[/B]2. Are you restarting Postfix (**sudo /etc/init.d/postfix restart**) after modifying the config?

Mathew

---

### Post by Mucker212 on 2008-12-05
Answers:

1. It sets up default automaticly with postfix and everything working with out spamassassin. Check out "FASTHOSTS DEDICATED SERVERS".

2. Below is the resluts of postconf -n

```
root@ubuntu:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases header_checks = regexp:/etc/postfix/header_checks
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
debug_peer_level = 2
local_destination_concurrency_limit = 1
mail_owner = postfix
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
mydestination = $myhostname, localhost.$mydomain
mynetworks_style = host
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.0.18/README_FILES
relay_domains = $mydestination
sample_directory = /usr/share/doc/postfix-2.0.18/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
transport_maps = hash:/etc/postfix/transport
unknown_local_recipient_reject_code = 450
virtual_mailbox_domains = $transport_maps
```

---

### Post by MJN on 2008-12-05
> **Mucker212 said:**
> Answers:

1. It sets up default automaticly with postfix and everything working with out spamassassin. Check out "FASTHOSTS DEDICATED SERVERS".

Ah, so this isn't your machine? Not that it matters, but it explains the peculiar configuration.

> ```
alias_maps = hash:/etc/aliases header_checks = regexp:/etc/postfix/header_checks
```There's your problem - your alias_maps directive either doesn't have a linefeed at the end of it or your header_checks directive starts with a space (hence implying a continuation of the previous line).

Mathew

---

### Post by Mucker212 on 2008-12-05
So how do I fix this?

Would this stop me sending and recieving emails?

If I remove the header_check command in main.cf then my emails work but I still get marked spam and lots of it.

---

### Post by MJN on 2008-12-05
> **Mucker212 said:**
> So how do I fix this?Make sure your header_checks line doesn't have any leading spaces at the beginning. Post your full (main.cf) config again (in its non-working state) if you're not sure.

> Would this stop me sending and receiving emails?Yes. Any 'fatal' error stops Postfix working.

Mathew

---

### Post by Mucker212 on 2008-12-05
MJN you seem to have sorted my problem out Thanks man. My emails are going out and reciving now. There was a space before the the header_checks line in main.cf I removed the psaces at the beginning and it seems to be working.

Im waiting to see if I get any spam above Spamassassin rating 15 yet. Heres what my header_checks file has in it. Is this correct?

```
/^X-Spam-Level: \*{15,}.*/ DISCARD
```

Thanks for all your help, your a diamond :guitar:

---

### Post by Mucker212 on 2008-12-05
All seems to be working!!!!

YOU ARE DA MAN!!!!):P

Thanks a million

---

### Post by MJN on 2008-12-07
You're welcome - glad to see you got it working!

Mathew

---

