---
title: "Problème postfix envoi de mail: qmgr ne se connecte plus à smtp"
date: 2009-03-12
forum: Server Platforms
---

### Post by fredux200175 on 2009-03-12
Bonjour,
 
Je suis confronté à un problème avec postfix qui m'échappe complètement. Le qmgr ne communique plus avec le smtp suite à un upgrade du serveur.  
 
Voici mes infos:
 
postconf -n:
 
> alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
debug_peer_list = 127.0.0.1
default_transport = smtp
home_mailbox = .maildir/
inet_interfaces = all
mailbox_command = /usr/bin/procmail
mailbox_size_limit = 0
mydestination = red.tiny.be, localhost.tiny.be, localhost
myhostname = red.tiny.be
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = smtp.tinyerp.com
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_policy_service inet:127.0.0.1:60000, reject_unauth_destination,        reject_rbl_client zen.spamhaus.org,        reject_rbl_client bl.spamcop.net,        reject_rbl_client cbl.abuseat.org,        reject_rbl_client list.dsbl.org,        permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport
unknown_local_recipient_reject_code = 450
virtual_alias_maps = hash:/etc/postfix/virtual_aliases, hash:/var/lib/mailman/data/virtual-mailman
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/mail/vmailbox/
virtual_mailbox_domains = tinyerp.com
virtual_mailbox_maps = ldap:tiny, ldap:tinyindia, hash:/etc/postfix/virtual_mailbox
virtual_uid_maps = static:5000


 
le master.cf:
 
> smtp inet n - n - - smtpd
2525 inet n - n - - smtpd
#submission inet n      -       -       -       -       smtpd
# -o smtpd_etrn_restrictions=reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       n       60      1       pickup
cleanup   unix  n       -       n       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
rewrite   unix  -       -       n       -       -       trivial-rewrite
bounce    unix  -       -       n       -       0       bounce
defer     unix  -       -       n       -       0       bounce
trace     unix  -       -       n       -       0       bounce
verify    unix  -       -       n       -       1       verify
flush     unix  n       -       n       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
#smtp      unix  -       -       n       -       -       smtpd
relay     unix  -       -       n       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       n       -       -       showq
error     unix  -       -       n       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
#
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# maildrop. See the Postfix MAILDROP_README file for details.
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
 
# only used by postfix-tls
#tlsmgr   fifo - - n 300 1 tlsmgr
#smtps   inet n - n - - smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
#587   inet n - n - - smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
scache    unix  -       -       -       -       1       scache
discard   unix  -       -       -       -       -       discard
#gnarwl    unix  -       n       n       -       -       pipe flags=F user=gnarwl argv=/usr/local/bin/gnarwl -v $sender $recipient
#spamassassin unix  -       n       n       -       -       pipe   user=nobody argv=/usr/bin/spamc -e /usr/sbin/sendmail -oi -f ${sender} ${recipient}


 
Mon message d'erreur dans les logs (var/log/mail.log):
 
> postfix/qmgr[23389]: warning: connect to transport smtp: Connection refused
 
L'envoi de mail se fait bien par d'autres biais: local, virtual. Seul le smtp foire.
 
Voici le résultat d'un strace de qmgr:
 
> Process 23389 attached - interrupt to quit
select(16, [5 6 10], [], [5 6 10], {5, 816000}) = 0 (Timeout)
time(NULL)                              = 1236854378
alarm(333)                              = 315
socket(PF_FILE, SOCK_STREAM, 0)         = 8
fcntl64(8, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(8, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(8, {sa_family=AF_FILE, path="private/smtp"}, 110) = -1 ECONNREFUSED (Connection refused)
close(8)                                = 0
time(NULL)                              = 1236854378
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2945, ...}) = 0
send(7, "<20>Mar 12 11:39:38 postfix/qmgr"..., 95, MSG_NOSIGNAL) = 95
time(NULL)                              = 1236854378
ioctl(3, FIONREAD, [100])               = 0
time(NULL)                              = 1236854378
 
Là, je sèche, s'il y en a qui ont des idées. Merci d'avance!

---

