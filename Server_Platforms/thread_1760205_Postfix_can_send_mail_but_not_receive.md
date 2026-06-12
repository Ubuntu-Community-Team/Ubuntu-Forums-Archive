---
title: "Postfix can send mail but not receive"
date: 2011-05-16
forum: Server Platforms
---

### Post by NessDan on 2011-05-16
**_UPDATE:_**
The problem was because Comcast had recently blocked port 25 incoming because my mail server was used to relay spam (I fixed it now but I'm talking with Comcast about opening the port.) This explains the reason why I suddenly couldn't receive mail. Sorry to give such a confusing question!

Story:
About two to three weeks ago, I was running Ubuntu Server 10.10 with Postfix+Dovecot and it worked right - it would receive and send mail. Tried upgrading and stopped it in the middle of upgrading so I bricked the system. I backed up files and upgraded to 11.04.

Relevant information:
[LIST]
[*]Around this time I was transferring my domain name (nessdan.net) from Dynadot to Namecheap.
[*]I was put on the XBL blocklist. I was told a computer was infected with a Trojan and was spamming, yet my ISP blocks port 25 In AND Out. (I guess that's a story for another day.) I did resolve this and was removed from the block list.
[*]Comcast blocks port 25 In and Out. My server sends mail through Comcasts mail relay servers. 
[/LIST]

My rant:
Sending mail works on the server. Receiving does not. Some may ask that I check my /var/log/mail.log or turn on verbose logging. The thing is, the log is not detecting any connections from outside.

I truly don't think it's my server configuration. I actually restored my previously working configuration file for Postfix (and Dovecot, just in case,) and still nothing. I think it may have to do with my Host Records. 

Some questions that came up in my head:
"How did my server receive mail before?" If Comcast blocks port 25 In and Out, then how could I have received mail previously?

Which led to the question, "What port does mail come in on?" I've heard some stuff about port 587 but even opening that does nothing.

Since I've been trying to find the answer to this for quite some time I know some basic information that would be helpful. Here is "postconf -n", my Host Records, "main.cf", and "master.cf" :

[SIZE=3]*postconf -n*[/SIZE]
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
readme_directory = no
recipient_delimiter = +
relayhost = [smtp.comcast.net]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/comcast
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/startssl-req-ca.pem
smtpd_tls_cert_file = /etc/ssl/certs/startssl-crt.pem
smtpd_tls_key_file = /etc/ssl/private/server-key.pem
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache

```

[SIZE=3]*Host Records*[/SIZE]
```

Host Name | IP Address/URL | Record Type | MX Perf | TTL

    @     | 98.243.113.96  | A (Address) |   n/a   | 1800
   www    | 98.243.113.96  | A (Address) |   n/a   | 1800


Host Name | Mailserver Host Name | Mail Type | MX Pref | TTL

    @     |      nessdan.net.    |    MX     |   n/a   | 1800


(No clue what the below was for, it was titled "SRV SETTINGS")
_SERVICE._PROTOCOL | PRIORITY | WEIGHT | PORT | TARGET

```


[SIZE="3"]*main.cf*[/SIZE]
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

# SASL
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl/comcast
broken_sasl_auth_clients = yes

# SMTPD TLS parameters
smtpd_tls_security_level = may
smtpd_tls_cert_file = /etc/ssl/certs/startssl-crt.pem
smtpd_tls_key_file = /etc/ssl/private/server-key.pem
smtpd_tls_CAfile = /etc/ssl/certs/startssl-req-ca.pem
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache

# SMTP TLS parameters
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# Relay parameters
relayhost = [smtp.comcast.net]:587

# General/Misc.
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
recipient_delimiter = +

```



[SIZE="3"]*master.cf*[/SIZE]
```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```

---

### Post by elico on 2011-05-17
if they do offer you out band relay server maybe they can offer you an inside relay server..
and are you sure they are blocking the in 25 port?

---

### Post by falko on 2011-05-17
Can you post the outputs of ```
netstat -tap
``` and ```
iptables -L
```?

---

### Post by NessDan on 2011-05-17
Thanks for replying.

Falko, here are the results of "netstat -tap", "iptables -L", and "ufw status numbered":
[SIZE="3"]*netstat -tap*[/SIZE]
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      624/smbd
tcp        0      0 *:imaps                 *:*                     LISTEN      630/dovecot
tcp        0      0 *:pop3s                 *:*                     LISTEN      630/dovecot
tcp        0      0 localhost:mysql         *:*                     LISTEN      837/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      624/smbd
tcp        0      0 *:submission            *:*                     LISTEN      1053/master
tcp        0      0 *:pop3                  *:*                     LISTEN      630/dovecot
tcp        0      0 *:imap2                 *:*                     LISTEN      630/dovecot
tcp        0      0 *:www                   *:*                     LISTEN      1186/apache2
tcp        0      0 *:ssh                   *:*                     LISTEN      941/sshd
tcp        0      0 *:ipp                   *:*                     LISTEN      1022/cupsd
tcp        0      0 *:smtp                  *:*                     LISTEN      1053/master
tcp        0      0 BACKBONE:imap2          c-98-243-113-96.hs:1340 ESTABLISHED 2836/imap-login
tcp        0      0 BACKBONE:ssh            c-98-243-113-96.hs:1328 ESTABLISHED 2834/sshd: nessdan
tcp        0      0 BACKBONE:imap2          c-98-243-113-96.hs:1331 ESTABLISHED 1908/imap-login
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      941/sshd
tcp6       0      0 [::]:ipp                [::]:*                  LISTEN      1022/cupsd

```


[SIZE="3"]*iptables -L*[/SIZE]
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251         udp dpt:mdns 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports www,https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftps-data 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:989 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:imap2 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3 
ACCEPT     udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports netbios-ssn,microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ipp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ipp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:webmin 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssmtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:submission 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25565 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25565 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:25566 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:25566 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         

```


If this helps, I used UFW as my firewall so here are the ports being allowed in:
[SIZE="3"]*ufw status numbered*[/SIZE]
```

Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22                         ALLOW IN    Anywhere
[ 2] 80,443/tcp                 ALLOW IN    Anywhere
[ 3] 21/tcp                     ALLOW IN    Anywhere
[ 4] 25/tcp                     ALLOW IN    Anywhere
[ 5] 989                        ALLOW IN    Anywhere
[ 6] 143                        ALLOW IN    Anywhere
[ 7] 110/tcp                    ALLOW IN    Anywhere
[ 8] 137,138/udp                ALLOW IN    Anywhere
[ 9] 139,445/tcp                ALLOW IN    Anywhere
[10] 631                        ALLOW IN    Anywhere
[11] 10000/tcp                  ALLOW IN    Anywhere
[12] 465/tcp                    ALLOW IN    Anywhere
[13] 587/tcp                    ALLOW IN    Anywhere
[14] 25565                      ALLOW IN    Anywhere
[15] 25566                      ALLOW IN    Anywhere
[16] 993/tcp                    ALLOW IN    Anywhere
[17] 995/tcp                    ALLOW IN    Anywhere

```


To respond to elico, the Comcast website says they do and I'm also on a PBL (Policy Blocklist) so my IP subnet isn't allowed to send mail. I'm not sure how an incoming relay server would work though :?

---

### Post by elico on 2011-05-18
if you are in a PBL means you almost sure have wither dynamic IP from  comcast or you are a not a business class IP that has the option.
just contact their customer service to make sure they cannot offer you an IP that out of the PBL.
you will might need to pay for it but it will solve all of your problems and concerns.

---

### Post by NessDan on 2011-05-18
> **elico said:**
> if you are in a PBL means you almost sure have wither dynamic IP from  comcast or you are a not a business class IP that has the option.
just contact their customer service to make sure they cannot offer you an IP that out of the PBL.
you will might need to pay for it but it will solve all of your problems and concerns.

That's the thing though, the residential plan I have is fine and even though I'm limited to sending 2000 emails a day, that is more than enough. I've been on the Policy Blocklist ever since I had Comcast (roughly two years ago) yet even though that was the case, I could still receive mail to my server. Now, after reformatting my server/transferring my domain name to namecheap.com, I can no longer receive mail.

---

### Post by NessDan on 2011-05-18
I'm going to set this as solved since I was doing some digging around and Comcast actually contacted me a few weeks ago saying that port 25 (which is not blocked inbound by default) was being blocked.

Now I have to deal with this but thank you all for the help. If I do get the port unblocked and the problem persists I will let you know!

---

