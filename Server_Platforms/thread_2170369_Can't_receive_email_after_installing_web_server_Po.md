---
title: "Can't receive email after installing web server Postfix, Dovecot"
date: 2013-08-26
forum: Server Platforms
---

### Post by Guy_Tremblay on 2013-08-26
Hello, I am quite new to Ubuntu (2-3 weeks), after Windows 7 crashed I formatted everything and decided to move to Ubuntu.

In order to setup a mail server, I setup Postfix and Dovecot following [this]("https://help.ubuntu.com/community/MailServer"). 

I can send emails, but I can't receive them (from gmail or hotmail for example). I use Squirrelmail. I can auto-send emails via Squirrelmail.

When sent from outside, nothing appears in mail.log.

I did try telnet emailing and it worked. 

I use port 587 (uncommented "submission inet n       -       -       -       -       smtpd") because it seems that my ISP blocks port 25.

SMTP is from my internet provider. 

MX Record is: guytremblay.com priority 10 

Weird thing is when I do SMPTP test on [MX Toolbox]("http://mxtoolbox.com/") I get the following:
```
[COLOR=#333333][FONT=Courier New]8/26/2013 12:08:43 AM Connection attempt #1 - Unable to connect after 15 seconds. [15.04 sec][/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]MXTB-PWS3v2 15038ms[/FONT][/COLOR]
``` 

Here is the postfix main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

home_mailbox = Maildir/


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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = guytremblay.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server1.guytremblay.com, guytremblay.com, anabaena, localhost.localdomain, localhost
relayhost = smtp.electronicbox.net
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```



Here is the dovecot.conf : 
```
## Dovecot configuration file

mail_location = maildir:/home/%u/Maildir


protocols = pop3 imap


pop3_uidl_format = %08Xu%08Xv




ssl = yes


ssl_cert = /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key = /etc/ssl/private/ssl-cert-snakeoil.key


# If you're in a hurry, see http://wiki2.dovecot.org/QuickConfiguration


# "doveconf -n" command gives a clean output of the changed settings. Use it
# instead of copy&pasting files when posting to the Dovecot mailing list.


# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "


# Default values are shown for each setting, it's not required to uncomment
# those. These are exceptions to this though: No sections (e.g. namespace {})
# or plugin settings are added by default, they're listed only as examples.
# Paths are also just examples with the real defaults being based on configure
# options. The paths listed here are for configure --prefix=/usr
# --sysconfdir=/etc --localstatedir=/var


# Enable installed protocols
!include_try /usr/share/dovecot/protocols.d/*.protocol


# A comma separated list of IPs or hosts where to listen in for connections. 
# "*" listens in all IPv4 interfaces, "::" listens in all IPv6 interfaces.
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
#listen = *, [::]


# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/


# Name of this instance. Used to prefix all Dovecot processes in ps output.
#instance_name = dovecot


# Greeting message for clients.
#login_greeting = Dovecot ready.


# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
# these networks. Typically you'd specify your IMAP proxy servers here.
#login_trusted_networks =


# Sepace separated list of login access check sockets (e.g. tcpwrap)
#login_access_sockets = 


# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no


# Should all processes be killed when Dovecot master process shuts down.
# Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is e.g. because of a security fix).
#shutdown_clients = yes


# If non-zero, run mail commands via this many connections to doveadm server,
# instead of running them directly in the same process.
#doveadm_worker_count = 0
# UNIX socket or host:port used for connecting to doveadm server
#doveadm_socket_path = doveadm-server


# Space separated list of environment variables that are preserved on Dovecot
# startup and passed down to all of its child processes. You can also give
# key=value pairs to always set specific settings.
#import_environment = TZ


##
## Dictionary server settings
##


# Dictionary can be used to store key=value lists. This is used by several
# plugins. The dictionary can be accessed either directly or though a
# dictionary server. The following dict block maps dictionary names to URIs
# when the server is used. These can then be referenced using URIs in format
# "proxy::<name>".


dict {
  #quota = mysql:/etc/dovecot/dovecot-dict-sql.conf.ext
  #expire = sqlite:/etc/dovecot/dovecot-dict-sql.conf.ext
}


# Most of the actual configuration gets included below. The filenames are
# first sorted by their ASCII value and parsed in that order. The 00-prefixes
# in filenames are intended to make it easier to understand the ordering.
!include conf.d/*.conf


# A config file can also tried to be included without giving an error if
# it's not found:
!include_try local.conf
```

Thank you in advance for your insight!

---

### Post by SeijiSensei on 2013-08-26
Your provider probably blocks inbound connections on port 25.  Are you on a residential or a commercial connection?  If it's a residential Internet service, your Terms of Service probably forbid the use of servers, and the ISP is enforcing that rule by blocking incoming traffic.

Give them a call.

---

### Post by Guy_Tremblay on 2013-08-26
> **SeijiSensei said:**
> Your provider probably blocks inbound connections on port 25.  Are you on a residential or a commercial connection?  If it's a residential Internet service, your Terms of Service probably forbid the use of servers, and the ISP is enforcing that rule by blocking incoming traffic.

Thanks" It is residential on cable. Port 25 is blocked by ISP, but not port 587. My ISP apparently does not forbid the use of servers. As I did test with telnet from outside and it worked, makes me wonder whether if setup of Dovecot may be incorrect on my side. Also I wonder if it is not MX Record that is wrong somehow as described elsewhere on this forum.
PS: I have a dynamic IP address and a DNS service where MX Record can be set.

---

