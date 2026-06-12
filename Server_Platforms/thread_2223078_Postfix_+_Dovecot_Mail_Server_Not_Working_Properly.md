---
title: "Postfix + Dovecot Mail Server Not Working Properly Ubuntu 12.04"
date: 2014-05-09
forum: Server Platforms
---

### Post by spider.netpln on 2014-05-09
[SIZE=3][FONT=arial black][B]Problem List
[/B][/FONT][/SIZE]
[LIST=1]
[*][SIZE=3][FONT=arial black]**From the SquirrelMail E-mail is sending but not Receiving in INBOX**[/FONT][/SIZE]
[*][SIZE=3][FONT=arial black]**All E-mails are going in Spam**[/FONT][/SIZE]
[/LIST]
**PLEASE HELP ME OUT OF THIS, THANKS IN ADVANCE**

My Postfix 
main.cf

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version



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
#smtpd_recipient_restrictions = permit_sasl_authenticated
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = ubuntu-server-new
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.xyz, localhost.localdomain, ubuntu-server-xyz, xyz.com, mail.abc.com
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128  x.x.x.x.0/27
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4





[FONT=arial][B][SIZE=5]
dovecot settings file
dovecot.conf[/SIZE][/B][/FONT]

> ## Dovecot configuration file

# If you're in a hurry, see [http://wiki2.dovecot.org/QuickConfiguration](http://wiki2.dovecot.org/QuickConfiguration)


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
#listen = *, ::


# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/


# Name of this instance. Used to prefix all Dovecot processes in ps output.
#instance_name = dovecot


# Greeting message for clients.
#login_greeting = Dovecot ready.


# Space separated list of trusted network ranges. Connections from these
# IPs are allowed to override their IP addresses and ports (for logging and
# for authentication checks). disable_plaintext_auth is also ignored for
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


protocols = imap pop3
#disable_plaintext_auth = no
mail_location = mbox:~/mail:INBOX=/var/mail/%u
mail_location = maildir:~/Maildir







BIND CONFIGURATION
Forward Zone

> 
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.xyz.com. root.xyz.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.xyz.com.
@       IN      A       x.x.x.x
ns1     IN      A       x.x.x.x
        IN      MX 10   mail.xyz.com.
www     IN      CNAME   ns1
mail    IN      CNAME   ns1





**Reverse Zone**

> 
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.xyz.com. root.xyz.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.xyz.com.
x.x.x.x.in-addr.arpa       IN      PTR     ns1.xyz.com.
x.x.x.x.in-addr.arpa       IN      PTR     mail.xyz.com.


[SIZE=4][B]NSLOOKUP MAIL.XYZ.COM
[/B][/SIZE]
> 
root@ubuntu-server-xyz:/etc/bind# nslookup mail.xyz.com
Server:         8.8.8.8
Address:        8.8.8.8#53


Non-authoritative answer:
mail.xyz    canonical name = ns1.xyz.
Name:   ns1.xyz.com
Address: x.x.x.x


[B]dig mail.xyz.com
[/B]> 
; <<>> DiG 9.8.1-P1 <<>> mail.xyz.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4345
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;mail.xyz.com.            IN      A


;; ANSWER SECTION:
mail.xyz.com.     21599   IN      CNAME   ns1.xyz.com.
ns1.xyz.com.      21599   IN      A       x.x.x.x


;; Query time: 67 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Fri May  9 15:34:11 2014
;; MSG SIZE  rcvd: 70


[B]

test of squirrelmail   [/B][h=1]SquirrelMail configtest[/h]> 

[h=1]SquirrelMail configtest[/h][COLOR=#000000][FONT=Times New Roman]This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.[/FONT][/COLOR]
[TABLE]
[TR]
[TD]SquirrelMail version:[/TD]
[TD]**1.4.22**[/TD]
[/TR]
[TR]
[TD]Config file version:[/TD]
[TD]**1.4.0**[/TD]
[/TR]
[TR]
[TD]Config file last modified:[/TD]
[TD]**08 May 2014 09:38:44**[/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Times New Roman]Checking PHP configuration...[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    PHP version 5.3.10-1ubuntu3.11 OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Running as www-data(33) / www-data(33)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    display_errors: [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    error_reporting: 22527[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    variables_order OK: GPCS.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    PHP extensions OK. Dynamic loading is disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking paths...[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Data dir OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Attachment dir OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Plugins OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Themes OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Default language OK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Base URL detected as: [/FONT][/COLOR]http://mail.xyz.com/src[COLOR=#000000][FONT=Times New Roman] (location base autodetected)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking outgoing mail service....[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    SMTP server OK ([/FONT][/COLOR]220 ubuntu-server-xyz ESMTP Postfix (Ubuntu)[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking IMAP service....[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    IMAP server ready ([/FONT][/COLOR]* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    Capabilities: [/FONT][/COLOR]* CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN 
[COLOR=#000000][FONT=Times New Roman]Checking internationalization (i18n) settings...[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]     gettext - Gettext functions are available. On some systems you must have appropriate system locales compiled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]     mbstring - Mbstring functions are available.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]     recode - Recode functions are unavailable.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]     iconv - Iconv functions are available.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]     timezone - Webmail users can change their time zone settings.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Checking database functions...[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]    not using database functionality.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Congratulations, your SquirrelMail setup looks fine to me![/FONT][/COLOR]
[B]


[SIZE=4]Please help me to resolve it.....mail goes in spam. and squirrel mail is not receiving mail.

[/SIZE][/B]

---

