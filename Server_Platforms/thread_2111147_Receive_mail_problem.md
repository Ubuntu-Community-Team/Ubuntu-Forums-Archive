---
title: "Receive mail problem"
date: 2013-02-01
forum: Server Platforms
---

### Post by mirceabondar on 2013-02-01
Hy. I have a mail server (postfix, dovecot) with mysql support. In database i added this:

users: [email]office@printpliante.ro[/email], [email]office@printech.ro[/email]
domains: printpliante.ro, printech.ro

The user [email]office@printech.ro[/email] receive mail from outlook.com, yahoo, google. When i try to send mail to [email]office@printpliante.ro[/email] from outlook or yahoo and other...the mail can't send. In outlook receive this message: If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<office@printpliante.ro>: unknown user: "office".

printpliante.ro is name server (ns1.printpliante.ro) for printech.ro.



postfix configuration:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

policy-spf_time_limit = 3600s
smtpd_recipient_restrictions =
     permit_sasl_authenticated
     permit_mynetworks
     reject_unauth_destination
     check_policy_service unix:private/policy-spf


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

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.printpliante.ro
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.printpliante.ro printpliante.ro, server, localhost.localdom                                                                              ain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains ='
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysq                                                                              l:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
dovecot_destination_recipient_limit = 1

```

and dovecot:

```
## Dovecot configuration file

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
listen = *

# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/
protocols = pop3 imap
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
info_log_path = /var/log/dovecot-info.log
mail_location = maildir:/home/vmail/%d/%n

protocol pop3 {
    pop3_uidl_format = %08Xu%08Xv
}

auth default {
    user = root

    passdb sql {
        args = /etc/dovecot/dovecot-sql.conf
    }

    userdb static {
        args = uid=5000 gid=5000 home=/home/vmail/%d/%n allow_all_users=yes
    }

    socket listen {
        master {
            path = /var/run/dovecot/auth-master
            mode = 0600
            user = vmail
        }

        client {
            path = /var/spool/postfix/private/auth
            mode = 0660
            user = postfix
            group = postfix
        }
    }
}

```

Everything works fine except officeprintpliante.ro or [email]webmaster@porintpliante.ro[/email](same problem)..

---

### Post by elico on 2013-02-01
I suggest you to try the postfix  mailing list and also take a look at:
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

This gives you all the knowledge you need to know on a full mail server.
There are are couple tutorials and examples in postfix site which I really recommend:
[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html](http://www.postfix.org/STANDARD_CONFIGURATION_README.html)

It makes the whole difference between knowing the problem and understanding what is wrong.

Regards

---

