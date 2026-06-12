---
title: "Postfix + Dovecot + Frustration"
date: 2012-07-02
forum: Server Platforms
---

### Post by jumpyjester on 2012-07-02
Good Evening All,

I have looked through some of the previous posts and am struggling, after implementing all the forum advice so far and still not fixing the issue I have decided to start from scratch.

Issue: I cant send from my ubuntu 12.04 server to any external address. This has been tested using telnet dontpaniccomputing.co.uk 25 and using external mail clients both have failed. 

Error Message: Relay access denied.

To recreate this I simply have to:

> jumpyjester@ubuntu-desktop:~$ telnet dontpaniccomputing.co.uk 25
Trying 192.168.1.200...
Connected to dontpaniccomputing.co.uk.
Escape character is '^]'.
220 dontpaniccomputing.co.uk ESMTP Postfix (Ubuntu)
mail from: [email]jumpyjester@dontpaniccomputing.co.uk[/email]
250 2.1.0 Ok
rcpt to: [email]jumpyjester@googlemail.com[/email]
554 5.7.1 <jumpyjester@googlemail.com>: Relay access denied

here is my /etc/postfix/main.cf
> 
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = dontpaniccomputing.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dontpaniccomputing.co.uk, localhost.co.uk, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/


here is /var/log/mail.log
> Jul  2 18:31:29 dontpaniccomputing postfix/smtpd[2769]: connect from unknown[192.168.1.100]
Jul  2 18:31:29 dontpaniccomputing postfix/smtpd[2769]: NOQUEUE: reject: RCPT from unknown[192.168.1.100]: 554 5.7.1 <joannegoth@yahoo.co.uk>: Relay access denied; from=<jumpyjester@dontpaniccomputing.co.uk> to=<joannegoth@yahoo.co.uk> proto=ESMTP helo=<[192.168.1.100]>
Jul  2 18:31:29 dontpaniccomputing postfix/smtpd[2769]: lost connection after RCPT from unknown[192.168.1.100]
Jul  2 18:31:29 dontpaniccomputing postfix/smtpd[2769]: disconnect from unknown[192.168.1.100]
Jul  2 18:31:39 dontpaniccomputing postfix/smtpd[2769]: connect from unknown[192.168.1.100]
Jul  2 18:31:39 dontpaniccomputing postfix/smtpd[2769]: NOQUEUE: reject: RCPT from unknown[192.168.1.100]: 554 5.7.1 <joannegoth@yahoo.co.uk>: Relay access denied; from=<jumpyjester@dontpaniccomputing.co.uk> to=<joannegoth@yahoo.co.uk> proto=ESMTP helo=<[192.168.1.100]>
Jul  2 18:31:39 dontpaniccomputing postfix/smtpd[2769]: lost connection after RCPT from unknown[192.168.1.100]
Jul  2 18:31:39 dontpaniccomputing postfix/smtpd[2769]: disconnect from unknown[192.168.1.100]
Jul  2 18:32:27 dontpaniccomputing postfix/anvil[2732]: statistics: max connection rate 2/60s for (smtp:192.168.1.100) at Jul  2 18:31:39
Jul  2 18:32:27 dontpaniccomputing postfix/anvil[2732]: statistics: max connection count 1 for (smtp:192.168.1.100) at Jul  2 18:22:27
Jul  2 18:32:27 dontpaniccomputing postfix/anvil[2732]: statistics: max cache size 2 at Jul  2 18:30:52
Jul  2 18:50:43 dontpaniccomputing postfix/smtpd[3059]: connect from unknown[192.168.1.100]
Jul  2 18:51:19 dontpaniccomputing postfix/smtpd[3059]: NOQUEUE: reject: RCPT from unknown[192.168.1.100]: 554 5.7.1 <jumpyjester@googlemail.com>: Relay access denied; from=<jumpyjester@dontpaniccomputing.co.uk> to=<jumpyjester@googlemail.com> proto=SMTP
Jul  2 18:51:34 dontpaniccomputing postfix/smtpd[3059]: warning: non-SMTP command from unknown[192.168.1.100]: Issue: I cant send from my ubuntu 12.04 server to any external address. This has been tested using t
Jul  2 18:51:34 dontpaniccomputing postfix/smtpd[3059]: disconnect from unknown[192.168.1.100]


Please help guys I am losing my hair with this.

Thanks in advance John.

---

### Post by kennethconn on 2012-07-02
Not my area here, but:
 
1) Can you send mail to that address (from the google mail account to the domain mail account)?
 
2) Can you sent email internally between two domail mail users?
 
3) A lot of ISPs block port 25 so try a different port.
 
4) Your postfix main.cf file has relayhost = , should that be completed?
 
As I said, not my area.

---

### Post by jumpyjester on 2012-07-02
Hi Kennethconn, thanks for taking the time to help.
1. I can receive mail to the [email]jumpyjester@dontpaniccomputing.co.uk[/email] address
2. I can send internally between accounts on the dontpaniccomputing.co.uk server
3. I am not sure if that is why it isnt working but I am not sure how to test if it is blocked.
4. I am not using a relay the intention is to send mail directly from the server so in theory relay should be blank but it doesn't make a difference if i comment it out.

looking forward to getting it working.

---

### Post by kennethconn on 2012-07-02
Have you tried setting relayhost = your ISP mail server?
 
Either that or change the default port from 25.

---

### Post by jumpyjester on 2012-07-03
Hi Kennethconn,

I have tried adding the relay host as described in the linked readme 

[http://frugi.co.uk/wordpress/unix/configure-postfix-to-use-o2-mail-relay-smtp-o2-co-uk/](http://frugi.co.uk/wordpress/unix/configure-postfix-to-use-o2-mail-relay-smtp-o2-co-uk/)

This hasn't worked :( how do I change the port for postfix?

---

### Post by Doug S on 2012-07-03
I guess I don't understand something about what you are trying to do.
I would not expect you to be able to send e-mails the way you have described.
Wouldn't you have to send e-mail from a validated account within your server?
By telneting into the server and claiming to be jumpytester, there is no proof or validation.
To send a test e-mail to [EMAIL="jumpyjester@googlemail.com"]jumpyjester@googlemail.com[/EMAIL] I would log onto the server as jumpytester and issue this:```
echo foo | mail -s 'test' [EMAIL="jumpyjester@googlemail.com"]jumpyjester@googlemail.com[/EMAIL]
```I tried the telnet method on my stuff and got your same denied result (as expected). I also tried the test I gave (but to my ISP e-mail address) and it worked (as expected).

---

### Post by kennethconn on 2012-07-03
A quick online search:
 
[http://www.linuxmail.info/postfix-change-port/](http://www.linuxmail.info/postfix-change-port/)

---

### Post by jumpyjester on 2012-07-03
Thank you both for your replies. Doug your code worked so now I don't understand why it did and if it can send then why wouldnt it send after being setup in evolution?

---

### Post by jumpyjester on 2012-07-03
other thing is when i send direct from the server and try to reply in evolution from my googlemail account it works however the reply to the googlemail message in evelution with the imap dontpanic account i get the same relay denied error

---

### Post by jumpyjester on 2012-07-04
> **Doug S said:**
> I guess I don't understand something about what you are trying to do.
I would not expect you to be able to send e-mails the way you have described.
Wouldn't you have to send e-mail from a validated account within your server?
By telneting into the server and claiming to be jumpytester, there is no proof or validation.
To send a test e-mail to [EMAIL="jumpyjester@googlemail.com"]jumpyjester@googlemail.com[/EMAIL] I would log onto the server as jumpytester and issue this:```
echo foo | mail -s 'test' [EMAIL="jumpyjester@googlemail.com"]jumpyjester@googlemail.com[/EMAIL]
```I tried the telnet method on my stuff and got your same denied result (as expected). I also tried the test I gave (but to my ISP e-mail address) and it worked (as expected).

Any ideas why this works but the first post doesnt?

---

### Post by Doug S on 2012-07-05
In the example I gave "mail" is acting like a user agent, making and delivering an e-mail to the local MTA (Mail Transport Agent). It runs under your local, authenticated, user ID. When you telnet in you are pretending to be an external MTA attempting to connect to the local MTA and deliver an e-mail. However, instead of asking to deliever an e-mail you ask it to relay it on to somewhere else, which is denied.
I don't know about evolution and cann't comment on it.

---

### Post by jumpyjester on 2012-07-05
Doug,
 
thanks for getting back to me, so in light of the above how do i set up so i can send mail from computers other than the server?

---

### Post by Doug S on 2012-07-05
Hi jumpytester,
I have been giving you some bad advise, sorry. We should have had this figured out a couple of days ago.
My "mail" example worked because it was using an interface declared in the "mynetworks" directive in main.cf. For both you and I, the telenet method did not work because, even though we were coming from a computer on our LAN, that LAN was not declared in the "mynetworks" directive. I am saying change this line:```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

```to this:```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
```(I guessed at the netmask for your LAN from your server at .200 and your client at .100, but you check it). Of course, re-start postfix:```

sudo /etc/init.d/postfix restart

```On my server, I went back and forth a few times and the telnet method worked or gave "relay access denied" as expected, based on that directive.

---

### Post by jumpyjester on 2012-07-05
Doug,

fantastic help it now works. last question i suspect you can answer. if i put i map email settings on to a mobile device if its not connected on my wifi it will get the relay access denied. how do i get round this or do i need to add a VPN?

regards,

John

---

### Post by Doug S on 2012-07-06
> **jumpyjester said:**
> Doug,
 
fantastic help it now works. last question i suspect you can answer. if i put i map email settings on to a mobile device if its not connected on my wifi it will get the relay access denied. how do i get round this or do i need to add a VPN?
 
regards,
 
JohnHi jumpytester,
I do not know the answer. perhaps someone else can help.

---

### Post by jumpyjester on 2012-07-08
Doug S,

Thank you so much fro your help.

Regards,

John

---

### Post by consamartzis on 2013-04-26
Hey all, got an issue seems to be the same, getting the "Relay access denied" during i send mail to external mailboxes via telnet. [COLOR=#000000][FONT=Ubuntu Mono]mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24[/FONT][/COLOR] is not working for me. mayve i need to add something differend there.

[COLOR=#000000]i ll post u one try from server mail to server mail (that woks!)[/COLOR]
[COLOR=#000000]and follows one try from server mail to [/COLOR][EMAIL="consamartzis@gmail.com"]consamartzis@gmail.com[/EMAIL][COLOR=#000000](that returns the error)[/COLOR]

[COLOR=#000000]so i go via telnet:[/COLOR]

```

root@diaitaplus:~# telnet aceworx.com 25Trying 37.123.115.133...
Connected to aceworx.com.
Escape character is '^]'.
220 mail.aceworx.com ESMTP Postfix (Ubuntu)
EHLO mail.aceworx.com
250-mail.aceworx.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: <info@aceworx.com>
250 2.1.0 Ok
RCPT TO: <csamartzis@aceworx.com>
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
blah blah
more blah
.
250 2.0.0 Ok: queued as 5D9D0E16F
MAIL FROM: <info@aceworx.com>
250 2.1.0 Ok
RCPT TO: <consamartzis@gmail.com>
554 5.7.1 <consamartzis@gmail.com>: Relay access denied

```

[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]
[/COLOR]Apr 23 20:36:43 diaitaplus postfix/smtpd[12563]: connect from diaitaplus[37.123.115.133]
Apr 23 20:37:52 diaitaplus postfix/smtpd[12563]: 5D9D0E16F: client=diaitaplus[37.123.115.133]
Apr 23 20:38:06 diaitaplus postfix/cleanup[12568]: 5D9D0E16F: message-id=<20130423203752.5D9D0E16F@mail.aceworx.com>
Apr 23 20:38:06 diaitaplus postfix/qmgr[12552]: 5D9D0E16F: from=<info@aceworx.com>, size=339, nrcpt=1 (queue active)
Apr 23 20:38:06 diaitaplus postfix/virtual[12570]: 5D9D0E16F: to=<csamartzis@aceworx.com>, relay=virtual, delay=31, delays=31/0.01/0/0.69, dsn=2.0.0, status=sent (delivered to maildir)
Apr 23 20:38:06 diaitaplus postfix/qmgr[12552]: 5D9D0E16F: removed
Apr 23 20:38:57 diaitaplus postfix/smtpd[12563]: NOQUEUE: reject: RCPT from diaitaplus[37.123.115.133]: 554 5.7.1 <consamartzis@gmail.com>: Relay access denied; from=<info@aceworx.com> to=<consamartzis@gmail.com> proto=ESMTP helo=<mail.aceworx.com>

```

[COLOR=#000000]thats my mysql log tailing:[/COLOR]

[COLOR=#000000]```
[/COLOR]109 Query SELECT destination FROM aliases WHERE mail='csamartzis@aceworx.com' and enabled = 1130423 20:38:06 106 Query SELECT destination FROM aliases WHERE mail='aceworx.com' and enabled = 1
107 Query SELECT domain FROM domains WHERE domain='aceworx.com' and enabled = 1
110 Connect mail@localhost on maildb
110 Query SELECT maildir FROM users WHERE id='csamartzis@aceworx.com' and enabled = 1
130423 20:38:52 109 Quit
130423 20:38:57 106 Query SELECT destination FROM aliases WHERE mail='gmail.com' and enabled = 1
107 Query SELECT domain FROM domains WHERE domain='gmail.com' and enabled = 1
130423 20:39:06 110 Quit
130423 20:39:57 106 Quit
107 Quit

```


[COLOR=#000000]and thats my main.cf (as u advised in post):[/COLOR]

```
[COLOR=#000000]
[/COLOR]# See /usr/share/postfix/main.cf.dist for a commented, more complete version








# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin = aceworx.com




smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


{...}


myhostname = mail.aceworx.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
local_recipient_maps =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks = host










{...}

```

[COLOR=#000000]i also give u one ifconfig command resault because i think u may need that.[/COLOR]

```
[COLOR=#000000]
[/COLOR]root@diaitaplus:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:3e:bc:01:88
          inet addr:37.123.115.133  Bcast:37.123.115.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:febc:188/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:289162 errors:0 dropped:120 overruns:0 frame:0
          TX packets:25365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:67813040 (67.8 MB)  TX bytes:2981835 (2.9 MB)
          Interrupt:32




lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:118527 (118.5 KB)  TX bytes:118527 (118.5 KB)

```[COLOR=#000000]
[/COLOR]
Anyone knows what i have to add in "my networks" value to permit sending external mail from my mail server?

---

### Post by Doug S on 2013-04-26
Hi, and welcome to Ubuntu forums.

I think you need to telnet to your lo interface from the same machine, not your external interface.```
 telnet 127.0.0.1 25
```> Hey all, got an issue seems to be the same, getting the "Relay access denied" during i send mail to external mailboxes via telnet. [COLOR=#000000][FONT=Ubuntu Mono]mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 [/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]192.168.1.0/24[/FONT] [/COLOR]is not working for me. may[COLOR=#ff0000]b[/COLOR]e i need to add something differen[COLOR=#ff0000]t[/COLOR] there.
Yes, that was for an internal network on 192.168.1.0, which you do not seem to have. It is not clear to me if you could or should add 37.123.115.133/32 there, or if that might create external relay allowed issues. Experiment with it (I don't have time at the moment).

---

### Post by tad1073 on 2013-04-29
I'm having the same issues.

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = tekcom.dyndns.org, thomthom, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/27
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
mydomain = tekcom.dyndns.org
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes

```

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
smtp       inet  n       -        n      -       -       smtpd
#smtp      inet  n       -       -       -       1       #postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtps      inet  n       -       n       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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
relay     unix  -       -       -       -       -       smtp
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```

---

