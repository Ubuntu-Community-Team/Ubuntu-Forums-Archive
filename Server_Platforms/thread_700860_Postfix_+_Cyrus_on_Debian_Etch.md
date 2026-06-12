---
title: "Postfix + Cyrus on Debian Etch"
date: 2008-02-18
forum: Server Platforms
---

### Post by CptPicard on 2008-02-18
Hi guys,

I suppose Ubuntu geeks are knowledgeable about Debian too, so let's see if someone could help me here. It's my first time trying to set up a mail server, and I'm somewhat at a loss of how to proceed after running into trouble...

In setting up my Postfix+Cyrus combination, I adapted [this tutorial]("http://www.onlamp.com/pub/a/onlamp/2005/10/06/cyrus_imap.html?page=1").

Postfix does get mail nicely, but something goes wrong when it is then given over to Cyrus. In mail.log we get

```

Feb 19 02:11:26 nike postfix/lmtp[2146]: C9CE14B0031: to=<eero@voittoporukka.fi>, relay=none, delay=0.04, delays=0.02/0.01/0.01/0, dsn=4.4.1, status=deferred (connect to nike.voittoporukka.fi[/var/run/cyrus/socket/lmtp]: Permission denied)

```

which is a bit odd because the lmtp socket that is being used is

```

nike:/var/run/cyrus/socket# ls -l lmtp
srwxrwxrwx 1 root root 0 2008-02-19 01:35 lmtp

```

which should be perfectly well readable, no?

Another interesting point is that Cyrus does nicely allow a login with Thunderbird from outside (apparently, I've managed to configure my user's SASL password ok), but it then fails with "mailbox does not exist", although we've got

```

nike:/var/run/cyrus/socket# cyradm --user eero localhost
Password:
localhost.localdomain> lm
eero@voittoporukka.fi (\HasNoChildren)
voitto@voittoporukka.fi (\HasNoChildren)

```

Doesn't this mean the boxes (in particular for "eero") should be there?

Just in case you're interested, here are the relevant config files...

main.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = nike.voittoporukka.fi
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = nike.voittoporukka.fi, mail.voittoporukka.fi, voittoporukka.fi, localhost, localhost.voittoporukka.fi
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all



mailbox_transport       = lmtp:unix:/var/run/cyrus/socket/lmtp
virtual_transport       = lmtp:unix:/var/run/cyrus/socket/lmtp
virtual_alias_maps      = hash:/etc/postfix/virtual

```

cyrus.conf:

```

# Debian defaults for Cyrus IMAP server/cluster implementation
# see cyrus.conf(5) for more information
#
# All the tcp services are tcpd-wrapped. see hosts_access(5)
# $Id: cyrus.conf,v 1.17 2006-09-18 23:47:37 hmh Exp $

START {
	# do not delete this entry!
	recover		cmd="/usr/sbin/ctl_cyrusdb -r"
  
	# this is only necessary if using idled for IMAP IDLE
	# this is NOT to be enabled right now in Debian builds
	#idled		cmd="idled"

	# this is useful on backend nodes of a Murder cluster
	# it causes the backend to syncronize its mailbox list with
	# the mupdate master upon startup
	#mupdatepush   cmd="/usr/sbin/ctl_mboxlist -m"

	# this is recommended if using duplicate delivery suppression
	delprune	cmd="/usr/sbin/ctl_deliver -E 3"
	# this is recommended if caching TLS sessions
	tlsprune	cmd="/usr/sbin/tls_prune"
}

# UNIX sockets start with a slash and are absolute paths
# you can use a maxchild=# to limit the maximum number of forks of a service
# you can use babysit=true and maxforkrate=# to keep tight tabs on the service
# most services also accept -U (limit number of reuses) and -T (timeout)
SERVICES {
	# --- Normal cyrus spool, or Murder backends ---
	# add or remove based on preferences
	imap		cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
	#imaps		cmd="imapd -s -U 30" listen="imaps" prefork=0 maxchild=100
	pop3		cmd="pop3d -U 30" listen="pop3" prefork=0 maxchild=50
	#pop3s		cmd="pop3d -s -U 30" listen="pop3s" prefork=0 maxchild=50

	# At least one form of LMTP is required for delivery
	# (you must keep the Unix socket name in sync with imap.conf)
	#lmtp		cmd="lmtpd" listen="localhost:lmtp" prefork=0 maxchild=20
	lmtpunix	cmd="lmtpd" listen="/var/run/cyrus/socket/lmtp" prefork=0 maxchild=20
	# ----------------------------------------------

	# useful if you need to give users remote access to sieve
	# by default, we limit this to localhost in Debian
  	sieve		cmd="timsieved" listen="localhost:sieve" prefork=0 maxchild=100

	# this one is needed for the notification services
	notify		cmd="notifyd" listen="/var/run/cyrus/socket/notify" proto="udp" prefork=1

	# --- Murder frontends -------------------------
	# enable these and disable the matching services above, 
	# except for sieve (which deals automatically with Murder)

	# mupdate database service - must prefork at least 1
	# (mupdate slaves)
	#mupdate       cmd="mupdate" listen=3905 prefork=1
	# (mupdate master, only one in the entire cluster)
	#mupdate       cmd="mupdate -m" listen=3905 prefork=1

	# proxies that will connect to the backends
	#imap		cmd="proxyd" listen="imap" prefork=0 maxchild=100
	#imaps		cmd="proxyd -s" listen="imaps" prefork=0 maxchild=100
	#pop3		cmd="pop3proxyd" listen="pop3" prefork=0 maxchild=50
	#pop3s		cmd="pop3proxyd -s" listen="pop3s" prefork=0 maxchild=50
	#lmtp		cmd="lmtpproxyd" listen="lmtp" prefork=1 maxchild=20
	# ----------------------------------------------
}

EVENTS {
	# this is required
	checkpoint	cmd="/usr/sbin/ctl_cyrusdb -c" period=30

	# this is only necessary if using duplicate delivery suppression
	delprune	cmd="/usr/sbin/ctl_deliver -E 3" at=0401

	# this is only necessary if caching TLS sessions
	tlsprune	cmd="/usr/sbin/tls_prune" at=0401

	## indexing of mailboxs for server side fulltext searches
	# reindex changed mailboxes (fulltext) approximately every other hour
	#squatter_1	cmd="/usr/bin/nice -n 19 /usr/sbin/squatter -s -r user" period=120
}

```

imapd.conf:

```

# Debian Cyrus imapd.conf
# See imapd.conf(5) for more information and more options

# Configuration directory
configdirectory: /var/lib/cyrus

# Which partition to use for default mailboxes
defaultpartition: default
partition-default: /var/spool/cyrus/mail

# News setup
partition-news: /var/spool/cyrus/news
newsspool: /var/spool/news

# Alternate namespace
# If enabled, activate the alternate namespace as documented in
# /usr/share/doc/cyrus21-doc/html/altnamespace.html, where an user's
# subfolders are in the same level as the INBOX
# See also userprefix and sharedprefix on imapd.conf(5)
altnamespace: no

# UNIX Hierarchy Convention
# Set to yes, and cyrus will accept dots in names, and use the forward
# slash "/" to delimit levels of the hierarchy. This is done by converting
# internally all dots to "^", and all "/" to dots. So the "rabbit.holes"
# mailbox of user "helmer.fudd" is stored in "user.elmer^fud.rabbit^holes"
unixhierarchysep: no

# Munging illegal characters in headers
# Headers of RFC2882 messages must not have characters with the 8th bit
# set. However, too many badly-written MUAs generate this, including most
# spamware.  Disable this if you want Cyrus to leave the crappage untouched
# and you don't care that IMAP SEARCH won't work right anymore.
#munge8bit: no

# Forcing recipient user to lowercase
# Cyrus 2.1 is case-sensitive.  If all your mail users are in lowercase, it is
# probably a very good idea to set lmtp_downcase_rcpt to true.  The default is
# to assume the user knows what he is doing, and not downcase anything.
#lmtp_downcase_rcpt: yes

# Uncomment the following and add the space-separated users who 
# have admin rights for all services.
admins: cyrus eero

# Space-separated list of users that have lmtp "admin" status (i.e. that
# can deliver email through TCP/IP lmtp) in addition to those in the
# admins: entry above
#lmtp_admins: postman

# Space-separated list of users that have mupdate "admin" status, in
# addition to those in the admins: entry above. Note that mupdate slaves and 
# backends in a Murder cluster need to autenticate against the mupdate master
# as admin users.
#mupdate_admins: mupdateman

# Space-separated list of users that have imapd "admin" status, in
# addition to those in the admins: entry above
#imap_admins: cyrus

# Space-separated list of users that have sieve "admin" status, in
# addition to those in the admins: entry above
#sieve_admins: cyrus

# List of users and groups that are allowed to proxy for other users,
# seperated by spaces.  Any user listed in this will be allowed to login
# for any other user.  Like "admins:" above, you can have imap_proxyservers
# and sieve_proxyservers.
#proxyservers: cyrus

# No anonymous logins
allowanonymouslogin: no

# Minimum time between POP mail fetches in minutes
popminpoll: 1

# If nonzero, normal users may create their own IMAP accounts by creating
# the mailbox INBOX.  The user's quota is set to the value if it is positive,
# otherwise the user has unlimited quota.
autocreatequota: 0

# umask used by Cyrus programs
umask: 077

# Sendmail binary location
# DUE TO A BUG, Cyrus sends CRLF EOLs to this program. This breaks Exim 3. 
# For now, to work around the bug, set this to a wrapper that calls 
# /usr/sbin/sendmail -dropcr instead if you use Exim 3.
#sendmail: /usr/sbin/sendmail

# If enabled, cyrdeliver will look for Sieve scripts in user's home
# directories: ~user/.sieve.
sieveusehomedir: false

# If sieveusehomedir is false, this directory is searched for Sieve scripts.
sievedir: /var/spool/sieve

# notifyd(8) method to use for "MAIL" notifications.  If not set, "MAIL"
# notifications are disabled.  Valid methods are: null, log, zephyr
#mailnotifier: zephyr

# notifyd(8) method to use for "SIEVE" notifications.  If not set, "SIEVE"
# notifications are disabled.  This method is only used when no method is
# specified in the script.  Valid methods are null, log, zephyr, mailto
#sievenotifier: zephyr

# DRAC (pop-before-smtp, imap-before-smtp) support
# Set dracinterval to the time in minutes to call DRAC while a user is
# connected to the imap/pop services. Set to 0 to disable DRAC (default)
# Set drachost to the host where the rpc drac service is running
#dracinterval: 0
#drachost: localhost

# If enabled, the partitions will also be hashed, in addition to the hashing
# done on configuration directories. This is recommended if one partition has a
# very bushy mailbox tree.
hashimapspool: true

# Allow plaintext logins by default (SASL PLAIN)
allowplaintext: yes

# Force PLAIN/LOGIN authentication only
# (you need to uncomment this if you are not using an auxprop-based SASL
# mechanism.  saslauthd users, that means you!). And pay attention to
# sasl_minimum_layer and allowapop below, too.
#sasl_mech_list: PLAIN

# Allow use of the POP3 APOP authentication command.
# Note that this command requires that the plaintext passwords are 
# available in a SASL auxprop backend (eg. sasldb), and that the system
# can provide enough entropy (eg. from /dev/urandom) to create a challenge
# in the banner.
#allowapop: no

# The minimum SSF that the server will allow a client to negotiate. A
# value of 1 requires integrity protection; any higher value requires some
# amount of encryption.
#sasl_minimum_layer: 0

# The maximum SSF that the server will allow a client to negotiate. A
# value of 1 requires integrity protection; any higher value requires some
# amount of encryption.
#sasl_maximum_layer: 256

# List of remote realms whose users may log in using cross-realm
# authentications.  Seperate each realm name by a space. A cross-realm
# identity is considered any identity returned by SASL with an "@" in it.
#loginrealms:

#
# SASL library options (these are handled directly by the SASL libraries,
# refer to SASL documentation for an up-to-date list of these)
#

# The mechanism(s) used by the server to verify plaintext passwords. Possible
# values are "saslauthd", "auxprop", "pwcheck" and "alwaystrue".  They
# are tried in order, you can specify more than one, separated by spaces.
#
# Do note that, since sasl will be run as user cyrus, you may have a lot of
# trouble to set this up right.
sasl_pwcheck_method: auxprop

# What auxpropd plugins to load, if using sasl_pwcheck_method: auxprop
# by default, all plugins are tried (which is probably NOT what you want).
#sasl_auxprop_plugin: sasldb

# If enabled, the SASL library will automatically create authentication secrets
# when given a plaintext password. Refer to SASL documentation 
sasl_auto_transition: no

#
# SSL/TLS Options
#
# Remember that Cyrus needs to access these as user cyrus, not as root,
# you will need to take care of file permissions according to your system's
# policy.
#

# File containing the global certificate used for ALL services (imap, pop3,
# lmtp, sieve)
#tls_cert_file: /etc/ssl/certs/cyrus-global.pem

# File containing the private key belonging to the global server certificate.
#tls_key_file: /etc/ssl/private-cyrus/cyrus-global.key

# File containing the certificate used for imap. If not specified, the global
# certificate is used.  A value of "disabled" will disable SSL/TLS for imap.
#tls_imap_cert_file: /etc/ssl/certs/cyrus-imap.pem

# File containing the private key belonging to the imap-specific server
# certificate.  If not specified, the global private key is used.  A value of
# "disabled" will disable SSL/TLS for imap.
#tls_imap_key_file: /etc/ssl/private-cyrus/cyrus-imap.key

# File containing the certificate used for pop3. If not specified, the global
# certificate is used.  A value of "disabled" will disable SSL/TLS for pop3.
#tls_pop3_cert_file: /etc/ssl/certs/cyrus-pop3.pem

# File containing the private key belonging to the pop3-specific server
# certificate.  If not specified, the global private key is used.  A value of
# "disabled" will disable SSL/TLS for pop3.
#tls_pop3_key_file: /etc/ssl/private-cyrus/cyrus-pop3.key

# File containing the certificate used for lmtp. If not specified, the global
# certificate is used.  A value of "disabled" will disable SSL/TLS for lmtp.
#tls_lmtp_cert_file: /etc/ssl/certs/cyrus-lmtp.pem

# File containing the private key belonging to the lmtp-specific server
# certificate.  If not specified, the global private key is used.  A value of
# "disabled" will disable SSL/TLS for lmtp.
#tls_lmtp_key_file: /etc/ssl/private-cyrus/cyrus-lmtp.key

# File containing the certificate used for sieve. If not specified, the global
# certificate is used.  A value of "disabled" will disable SSL/TLS for sieve.
#tls_sieve_cert_file: /etc/ssl/certs/cyrus-sieve.pem

# File containing the private key belonging to the sieve-specific server
# certificate.  If not specified, the global private key is used.  A value of
# "disabled" will disable SSL/TLS for sieve.
#tls_sieve_key_file: /etc/ssl/private-cyrus/cyrus-sieve.key

# File containing one or more Certificate Authority (CA) certificates.
#tls_ca_file: /etc/ssl/certs/cyrus-imapd-ca.pem

# Path to directory with certificates of CAs.
tls_ca_path: /etc/ssl/certs

# The length of time (in minutes) that a TLS session will be cached for later
# reuse.  The maximum value is 1440 (24 hours), the default.  A value of 0 will
# disable session caching.
tls_session_timeout: 1440

# The list of SSL/TLS ciphers to allow.  The format of the string is described
# in ciphers(1). THIS DISABLES THE WEAK 'FOR EXPORT' CRAP!
tls_cipher_list: TLSv1:SSLv3:SSLv2:!NULL:!EXPORT:!DES:!LOW:@STRENGTH

# Require a client certificate for ALL services (imap, pop3, lmtp, sieve).
#tls_require_cert: false

# Require a client certificate for imap ONLY.
#tls_imap_require_cert: false

# Require a client certificate for pop3 ONLY.
#tls_pop3_require_cert: false

# Require a client certificate for lmtp ONLY.
#tls_lmtp_require_cert: false

# Require a client certificate for sieve ONLY.
#tls_sieve_require_cert: false

#
# Cyrus Murder cluster configuration
#
# Set the following options to the values needed for this server to
# autenticate against the mupdate master server:
# mupdate_server
# mupdate_port
# mupdate_username
# mupdate_authname
# mupdate_realm
# mupdate_password
# mupdate_retry_delay

##
## KEEP THESE IN SYNC WITH cyrus.conf
##
# Unix domain socket that lmtpd listens on.
lmtpsocket: /var/run/cyrus/socket/lmtp

# Unix domain socket that idled listens on.
idlesocket: /var/run/cyrus/socket/idle

# Unix domain socket that the new mail notification daemon listens on.
notifysocket: /var/run/cyrus/socket/notify

##
## DEBUGGING
##
# Debugging hook. See /usr/share/doc/cyrus21-common/README.Debian.debug
# Keep the hook disabled when it is not in use
#
# gdb Back-traces
#debug_command: /usr/bin/gdb -batch -cd=/tmp -x /usr/lib/cyrus/get-backtrace.gdb /usr/lib/cyrus/bin/%s %d >/tmp/gdb-backtrace.cyrus.%1$s.%2$d <&- 2>&1 &
#
# system-call traces
#debug_command: /usr/bin/strace -tt -o /tmp/strace.cyrus.%s.%d -p %2$d <&- 2>&1 &
#
# library traces
#debug_command: /usr/bin/ltrace -tt -n 2 -o /tmp/ltrace.cyrus.%s.%d -p %2$d <&- 2>&1 &


# own config stuff

defaultdomain: voittoporukka.fi
loginrealms: voittoporukka.fi

```


Finally, Postfix's virtual hashmap file contains

```

eero@voittoporukka.fi  eero@voittoporukka.fi

```

(As per the tutorial...)

Would really appreciate all insight, I'm a bit out of my depth here and don't know where to begin troubleshooting...

EDIT: Ok, so I fixed the postfix permission issue. Now I'm getting through to Cyrus, that still doesn't actually find the mailbox... :(

---

### Post by astrotech226 on 2008-02-18
I know nothing about Postfix, but I do use Cyrus IMAP.  Your mailbox format doesn't look right.  Usually, mailboxes will have have "user" in front of them.  How are you creating the mailboxes?  Your "lm" command on one of my servers would look more like this:

```

localhost.localdomain> lm
user/eero@voittoporukka.fi (\HasNoChildren)
user/voitto@voittoporukka.fi (\HasNoChildren)
```

The other problem is that in your imapd.conf file, you should probably change this line:

```
unixhierarchysep: yes
```

Cyrus normally uses periods to distinguish the breaks in folder names.  You are using email addresses for mailbox names so you have a real problem.  Changing the unixhierarchysep to yes will use forward slashes for the breaks and won't split the email address into two parts.

Good luck!

---

