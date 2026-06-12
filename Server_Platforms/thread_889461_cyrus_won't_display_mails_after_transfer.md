---
title: "cyrus won't display mails after transfer"
date: 2008-08-14
forum: Server Platforms
---

### Post by DER_julu on 2008-08-14
hi everybody...
recently we started to kill our ages-old, misconfigured RHEL-box which acted as a mailserver with cyrus and sendmail, and transfering the mails to a new hardy-server-box, using cyrus and postfix (since it's delivered with cyrus from the repos...). the new box will only do it's job in the lan, without a connect to the net, as a semi-backup-server for the mails.

i set up the server, installed the packages and configured saslauthd, cyrus and postfix with this [doku from the german wiki](http://wiki.ubuntuusers.de/Cyrus_IMAPD); i chowned the contents of /var/spool/cyrus/ to cyrus:mail, since i got permission errors when trying to create new users, which solved the problem. afterwards, i took the contents of the user-folder from the old server, created a new user (useradd, passwd), created the cyrus-user in the cyradm-prompt (cm user.xxx) and copied the contents of the backupped user-folder to the newly created folder on the new server-machine. 
using cyrreconstruct (sudo -u cyrus /usr/sbin/cyrreconstruct -C /etc/imapd.conf -rf user.xxx) after stopping cyrus, i restarted cyrus and connected with the mailclient hoping to see everything allright. instead, all i got was the empty folders, not a single mail...

the weird thing is, neither mail.err, mail.info nor mail.log return any error-messages, everything seems to be running as intended, still, not a single mail (of over a few hundred...);

anyone of got any experience with that kinda problem ?
thanks in advance, julu

**imapd.conf**
```

configdirectory: /var/lib/cyrus
partition-default: /var/spool/cyrus/mail
partition-news: /var/spool/cyrus/news
newsspool: /var/spool/news
altnamespace: no
unixhierarchysep: no
lmtp_downcase_rcpt: yes
admins: cyrus
imap_admins: cyrus
sieve_admins: cyrus
allowanonymouslogin: no
autocreatequota: 0
umask: 077
sieveusehomedir: false
sievedir: /var/spool/sieve
hashimapspool: true
allowplaintext: yes
sasl_pwcheck_method: saslauthd
sasl_auto_transition: no
tls_ca_path: /etc/ssl/certs
tls_session_timeout: 1440
tls_cipher_list: TLSv1+HIGH:!aNULL:@STRENGTH
lmtpsocket: /var/run/cyrus/socket/lmtp
idlemethod: poll
idlesocket: /var/run/cyrus/socket/idle
notifysocket: /var/run/cyrus/socket/notify
syslog_prefix: cyrus

```

**cyrus.conf**
```

# Debian defaults for Cyrus IMAP server/cluster implementation
# see cyrus.conf(5) for more information
#
# All the tcp services are tcpd-wrapped. see hosts_access(5)
# $Id: cyrus.conf 567 2006-08-14 18:19:32Z sven $

START {
        # do not delete this entry!
        recover         cmd="/usr/sbin/ctl_cyrusdb -r"

        # this is only necessary if idlemethod is set to "idled" in imapd.conf
        #idled          cmd="idled"

        # this is useful on backend nodes of a Murder cluster
        # it causes the backend to syncronize its mailbox list with
        # the mupdate master upon startup
        #mupdatepush   cmd="/usr/sbin/ctl_mboxlist -m"

        # this is recommended if using duplicate delivery suppression
        delprune        cmd="/usr/sbin/cyr_expire -E 3"
        # this is recommended if caching TLS sessions
        tlsprune        cmd="/usr/sbin/tls_prune"
}

# UNIX sockets start with a slash and are absolute paths
# you can use a maxchild=# to limit the maximum number of forks of a service
# you can use babysit=true and maxforkrate=# to keep tight tabs on the service
# most services also accept -U (limit number of reuses) and -T (timeout)
SERVICES {
        # --- Normal cyrus spool, or Murder backends ---
        # add or remove based on preferences
        imap            cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
        imaps           cmd="imapd -s -U 30" listen="imaps" prefork=0 maxchild=100
        pop3            cmd="pop3d -U 30" listen="pop3" prefork=0 maxchild=50
        #pop3s          cmd="pop3d -s -U 30" listen="pop3s" prefork=0 maxchild=50
        nntp            cmd="nntpd -U 30" listen="nntp" prefork=0 maxchild=100
        #nntps          cmd="nntpd -s -U 30" listen="nntps" prefork=0 maxchild=100

        # At least one form of LMTP is required for delivery
        # (you must keep the Unix socket name in sync with imap.conf)
        #lmtp           cmd="lmtpd" listen="localhost:lmtp" prefork=0 maxchild=20
        lmtpunix        cmd="lmtpd" listen="/var/run/cyrus/socket/lmtp" prefork=0 maxchild=20
        # ----------------------------------------------

        # useful if you need to give users remote access to sieve
        # by default, we limit this to localhost in Debian
        sieve           cmd="timsieved" listen="localhost:sieve" prefork=0 maxchild=100

        # this one is needed for the notification services
        notify          cmd="notifyd" listen="/var/run/cyrus/socket/notify" proto="udp" prefork=1

        # --- Murder frontends -------------------------
        # enable these and disable the matching services above,
        # except for sieve (which deals automatically with Murder)

        # mupdate database service - must prefork at least 1
        # (mupdate slaves)
        #mupdate       cmd="mupdate" listen=3905 prefork=1
        # (mupdate master, only one in the entire cluster)
        #mupdate       cmd="mupdate -m" listen=3905 prefork=1

        # proxies that will connect to the backends
        #imap           cmd="proxyd" listen="imap" prefork=0 maxchild=100
       #imaps          cmd="proxyd -s" listen="imaps" prefork=0 maxchild=100
        #pop3           cmd="pop3proxyd" listen="pop3" prefork=0 maxchild=50
        #pop3s          cmd="pop3proxyd -s" listen="pop3s" prefork=0 maxchild=50
        #lmtp           cmd="lmtpproxyd" listen="lmtp" prefork=1 maxchild=20
        # ----------------------------------------------
}

EVENTS {
        # this is required
        checkpoint      cmd="/usr/sbin/ctl_cyrusdb -c" period=30

        # this is only necessary if using duplicate delivery suppression
        delprune        cmd="/usr/sbin/cyr_expire -E 3" at=0401

        # this is only necessary if caching TLS sessions
        tlsprune        cmd="/usr/sbin/tls_prune" at=0401
        # indexing of mailboxs for server side fulltext searches

        # reindex changed mailboxes (fulltext) approximately every other hour
        #squatter_1     cmd="/usr/bin/nice -n 19 /usr/sbin/squatter -s" period=120

        # reindex all mailboxes (fulltext) daily
        #squatter_a     cmd="/usr/sbin/squatter" at=0517
}

```

**saslauth**
```

# Settings for saslauthd daemon
# Please read /usr/share/doc/sasl2-bin/README.Debian for details.
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

# Description of this saslauthd instance. Recommended.
# (suggestion: SASL Authentication Daemon)
DESC="SASL Authentication Daemon"

# Short name of this saslauthd instance. Strongly recommended.
# (suggestion: saslauthd)
NAME="saslauthd"

# Which authentication mechanisms should saslauthd use? (default: pam)
#
# Available options in this Debian package:
# getpwent  -- use the getpwent() library function
# kerberos5 -- use Kerberos 5
# pam       -- use PAM
# rimap     -- use a remote IMAP server
# shadow    -- use the local shadow password file
# sasldb    -- use the local sasldb database file
# ldap      -- use LDAP (configuration is in /etc/saslauthd.conf)
#
# Only one option may be used at a time. See the saslauthd man page
# for more information.
#
# Example: MECHANISMS="pam"
MECHANISMS="pam"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c -m /var/run/saslauthd)
# Note: You MUST specify the -m option or saslauthd won't run!
#
# See /usr/share/doc/sasl2-bin/README.Debian for Debian-specific information.
# See the saslauthd man page for general information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
OPTIONS="-c -m /var/run/saslauthd"

```

---

### Post by NaOH on 2009-03-26
Sounds similar to a recent oversight of mine:

Neglected to specify cyrus as the transport in main.cf

---

