---
title: "Postfix bounces all incoming mail. No local delivery."
date: 2011-07-15
forum: Server Platforms
---

### Post by thetitan on 2011-07-15
Hello,

I spent all day yesterday trying to figure this out. I have a feeling that is something very simple. I am just not seeing it.

I set up a new box - Ubuntu 10.04. The mail system is Postfix, Dovecot, SpamAssasin and ClamAV. Virtualmin (I use it as my web interface to manage the server and users) is setup to configure virus/spam filtering per user.

Here are the contents of /etc/procmailrc
```
LOGFILE=/var/log/procmail.log
TRAP=/etc/webmin/virtual-server/procmail-logger.pl
:0wi
VIRTUALMIN=|/etc/webmin/virtual-server/lookup-domain.pl $LOGNAME
EXITCODE=$?
:0
* ?/usr/bin/test "$EXITCODE" = "73"
/dev/null
EXITCODE=0
:0
* ?/usr/bin/test "$VIRTUALMIN" != ""
{
INCLUDERC=/etc/webmin/virtual-server/procmail/$VIRTUALMIN
}
ORGMAIL=$HOME/Maildir/
DEFAULT=$HOME/Maildir/
DROPPRIVS=yes
```I have determined that:

* Mail clients can connect to the server and download existing messages in the mail boxes (I synced the mail boxes to the ones on my old server - CentOS 5.2).
* I can send outgoing mail.
* Local mail is sent, but not received and there is no bounce message.
* All external mail bounces with the following message:

The mail system
 
```
<support.theclient.com@ops01.thesystem.com> (expanded from
    <support@theclient.com>): unknown user: "support.theclient.com"
``````
Reporting-MTA: dns; ops01.thesystem.com
X-Postfix-Queue-ID: 9FEC910C16D7
X-Postfix-Sender: rfc822; theclient@live.com
Arrival-Date: Fri, 15 Jul 2011 06:48:33 -0500 (CDT)

Final-Recipient: rfc822; support.theclient.com@ops01.thesystem.com
Original-Recipient: rfc822;support@theclient.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "support.theclient.com"
```The mailboxes are not virtual they are also users on the system. I am able to login via Dovecot and download messages. It just that something is preventing Postfix from seeing the mail account/user.

The is the output from:

hostname
```
ops01.thesystem.com
```hostname -f
```
ops01.thesystem.com
```hostname -s
```
ops01
```grep myhostname /etc/postfix/main.cf
```
smtpd_banner = $myhostname ESMTP
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
relay_domains = $myhostname, localhost.$mydomain, localhost, $mydomain

```postconf -n
```
alias_maps = hash:/etc/aliases
biff = no
broken_sasl_auth_clients = yes
canonical_maps = hash:/etc/postfix/canonical
config_directory = /etc/postfix
deliver_lock_delay = 3s
disable_vrfy_command = yes
fork_delay = 3s
header_checks = regexp:/etc/postfix/header_checks
header_size_limit = 5242880
home_mailbox = Maildir/
ipc_idle = 60s
mail_spool_directory = /var/spool/mail
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
mailbox_size_limit = 52428800
message_size_limit = 15728640
minimal_backoff_time = 1000s
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks = 127.0.0.0/8, 71.23.160.130, 67.159.45.42, 97.16.50.186
myorigin = /etc/mailname
qmgr_message_active_limit = 1000
qmgr_message_recipient_limit = 2000
queue_run_delay = 1000s
readme_directory = no
recipient_canonical_maps = hash:/etc/postfix/recipient_canonical
recipient_delimiter = .
relay_domains = $myhostname, localhost.$mydomain, localhost, $mydomain
relocated_maps = hash:/etc/postfix/relocated
sender_bcc_maps = hash:/etc/postfix/bcc
sender_canonical_maps = hash:/etc/postfix/sender_canonical
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP
smtpd_client_restrictions = permit_mynetworks permit_inet_interfaces reject_unknown_reverse_client_hostname
smtpd_error_sleep_time = 10s
smtpd_hard_error_limit = 20
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_mynetworks permit_inet_interfaces reject_unknown_reverse_client_hostname permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/sender_access
smtpd_timeout = 300s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = hash:/etc/postfix/transport
virtual_alias_maps = hash:/etc/postfix/virtual
```

---

### Post by Bachstelze on 2011-07-15
You probably have an alias of sorts somewhere that makes Postfix expand the address like that. Look at [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

---

### Post by thetitan on 2011-07-15
I pinpoint the problem to recipient_delimiter.

On my new system I had changed it to *recipient_delimiter = .*. It is best to either not use this parameter or set it to *recipient_delimiter = +*, which is the default configuration for a fresh Ubuntu Postfix install.

More here [http://www.virtualmin.com/node/18861]("http://www.virtualmin.com/node/18861")

---

