---
title: "Postfix SMTP not working"
date: 2010-04-07
forum: Server Platforms
---

### Post by Norami on 2010-04-07
Hi all,

I've got a server running 9.10, and I'm having a few issues with SMTP. It's got Postfix and Dovecot installed, and eventually I'll add content filtering, but I need to get past this issue first.

I know there's a lot of posts out there for Postfix issues, but I haven'tbeen able to find one specific to my issue.

IMAP and POP3 work fine through SSL, and the server can send mail without any problems. That's all fine and dandy, but I need to utilize an e-mail client (like evolution or outlook). Everytime I set up a user in Evolution, the smtp connection times out, or is refused. I know it's not a firewall issue. Port 25 is open, as well as 465. So I should be able to connect through SSL. I want to be able to connect through SMTP using the same credentials as IMAP. 

Here's my main.cf file:
```

myhostname = mail.adamwgay.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = adamwgay.com, mail.adamwgay.com, localhost.adamwgay.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

```

I'm really new to mail serving, so I'm kind of stuck. I've tried a few tutorials, but everytime I get things rolling, this issue pops up. I don't know if it's something I'm setting up wrong in the client, or if it's a configuration error on my part in postfix.

I'm also having a bit of an issue with my aliases. I've basically got a lot of addresses going to root, then root going to the main user, but it's not actually delivering the mail to the main user. It sends it straight to root.

---

### Post by KB1JWQ on 2010-04-07
postconf -n output, please.

Can you telnet to the server on port 25 from the client that's running Evolution?  If it fails, we just found your problem.

---

### Post by Adina on 2010-04-07
I think you need to enter the subnet of the machine you have the email client (evolution) on in the  mynetworks parameter.

Like this example:
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24

```

anyway you should check /var/log/mail.log on the mail server.

that should give you hint of what is going wrong.

---

### Post by Norami on 2010-04-07
postconf -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = adamwgay.com, mail.adamwgay.com, localhost.adamwgay.com, localhost
myhostname = mail.adamwgay.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

I'm able to telnet in through 25. Here's the mail.log from when I try to Send/Receive in Evolution:

```

Apr  7 21:10:20 mail postfix/smtpd[14639]: NOQUEUE: reject: RCPT from 66-190-90-18.dhcp.athn.ga.charter.com[66.190.90.18]: 554 5.7.1 <adam.gay@gmail.com>: Relay access denied; from=<adam@adamwgay.com> to=<adam.gay@gmail.com> proto=ESMTP helo=<[192.168.1.107]>
Apr  7 21:10:20 mail postfix/smtpd[14639]: disconnect from 66-190-90-18.dhcp.athn.ga.charter.com[66.190.90.18]
Apr  7 21:10:31 mail postfix/smtpd[14599]: timeout after RCPT from m4c5e36d0.tmodns.net[208.54.94.76]
Apr  7 21:10:31 mail postfix/smtpd[14599]: disconnect from m4c5e36d0.tmodns.net[208.54.94.76]
Apr  7 21:10:33 mail dovecot: IMAP(adam): Connection closed bytes=68/516

```

Obviously, it's saying Relay access denied. Does that mean something with the authentication is wonky?

---

### Post by kewlrichie on 2010-04-08
Do what Adina mentioned I think it's that also. If you have a 192.168.1.1 network you would need to add 192.168.1.0/24 to the end of my mynetworks. So it looks like this. 

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24

```

The mynetwork part tells postfix what IP's/subnets can use it to send mail and being that you said it works from the server aka localhost so I think once you add the network that these email clients are on you should be good

after adding that change please reload or restart postfix, then try the clients again

---

### Post by Norami on 2010-04-08
I see what you're saying, but there must be an easier way? I have a few other domains that need to be served, and the clients are all using different IPs and subnets. Like accessing and using Mail through a mobile phone client, and then using Roundcube. I feel like there's another way to get SMTP working. If not, then I have to add every single IP and/or subnet that might use this SMTP?

Let me back-track for a second. Basically, I want my server to act like Gmail (on a smaller scale, of course). I want to access it from RounCube webmail, Mutt, and through any e-mail client I set-up on a system. There's got to be some sort of configuration I'm missing to allow SMTP connections through SSL using the UNIX user's login credentials. Since pretty much every freemail account on the net allows IMAP and/or POP3, there must be a way around having to add every IP/subnet I want to use to mynetworks.

**EDIT:**
Here's what Outlook says when I try to send mail:
```
The connection to the server has failed. Account: 'mail.adamwgay.com', Server: 'mail.adamwgay.com', Protocol: SMTP, Port: 465, Secure(SSL): Yes, Socket Error: 10060, Error Number: 0x800CCC0E
```

**EDIT 2:**
I did some more messing around, and enabled some TLS options that needed to be enabled. It got me a little further. At least now the e-mail client will talk to the server through port 465. When it's trying to send mail, it asks for user, pass and domain. Only problem is that no matter what I enter, it seems to do nothing. Is there a different user and password for SMTP connections?

Here's an updated postconf -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
html_directory = /usr/share/doc/postfix/html
mailbox_size_limit = 0
mydestination = adamwgay.com, mail.adamwgay.com, localhost.adamwgay.com, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_sasl_authenticated
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = encrypt
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

---

### Post by ruuden on 2010-04-08
> I see what you're saying, but there must be an easier way? I have a few other domains that need to be served, and the clients are all using different IPs and subnets. Like accessing and using Mail through a mobile phone client, and then using Roundcube. I feel like there's another way to get SMTP working. If not, then I have to add every single IP and/or subnet that might use this SMTP?
I believe VPN tunneling is commonly used for this purpose.

---

### Post by masterxunil on 2010-04-08
Me too i got almost the same problem.But my telnet localhost 25 doesn't work .i just have this message: 
Trying ::1...
connected to localhost
Escape character is '^]'.
  Connection closed by foreign host.

Please help me!

---

### Post by kewlrichie on 2010-04-08
If you notice in your main.cf you'll see "smtpd_recipient_restrictions =" and it should have "permit_mynetworks" which is your local network and also has "permit_sasl_authenticated" for outside of your network SMTP authentication. You can find more info on how to set that up at the link below

"So let's say your users are going away for holidays but need to use your mail server to relay mail from outside the organization... Let's set up SMTP authentication for the secure port only and allow access to this from outside your network." [http://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only]("http://www.howtoforge.com/postfix-smtp-authentication-on-the-secure-port-only")

---

### Post by boxalek on 2010-04-18
> **masterxunil said:**
> Me too i got almost the same problem.But my telnet localhost 25 doesn't work .i just have this message: 
Trying ::1...
connected to localhost
Escape character is '^]'.
Connection closed by foreign host.
 
Please help me!
 
hello from my
 
i am new in this forum and ubuntu
 
i have the same problem :confused::confused::confused:

---

### Post by Norami on 2010-04-19
Hi all. Sorry for not replying to let you know this issue was solved. I'm changing the prefix on the thread title to reflect it. Here's my postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = adamwgay.com, mail.adamwgay.com, localhost.adamwgay.com, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination reject_sender_login_mismatch
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = adamwgay.com
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous, noplaintext
smtpd_sasl_tls_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```As was stated above, the "smtpd_recipient_restrictions" was a bit out of whack. After I added in everything in the order above, it worked perfectly.

---

### Post by jduhls on 2011-04-11
I followed this article:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

...and I can't telnet mydomain.com 25. Nothin's there. Can't send email through my own SMTP server. Helps? I opened port 25 via UFW and everything.

Here's my main.cf:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = scan:127.0.0.1:10026
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
myhostname = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = $myhostname
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noplaintext,noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
```

...and master.cf:

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
# AV scan filter (used by content_filter)
scan      unix  -       -       n       -       16      smtp
        -o smtp_send_xforward_command=yes
# For injecting mail back into postfix from the filter
127.0.0.1:10025 inet  n -       n       -       16      smtpd
        -o content_filter=
        -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
        -o smtpd_helo_restrictions=
        -o smtpd_client_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o mynetworks_style=host
        -o smtpd_authorized_xforward_hosts=127.0.0.0/8
#submission inet n       -       -       -       -       smtpd
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

```

...and dovecot.conf:

```
base_dir = /var/run/dovecot/
protocols = imap pop3
disable_plaintext_auth = yes
shutdown_clients = yes
log_path = /var/log/dovecot
info_log_path = /var/log/dovecot.info
log_timestamp = "%Y-%m-%d %H:%M:%S "
#ssl_disable = yes
ssl = no
login_dir = /var/run/dovecot/login
login_chroot = yes
login_user = dovecot
login_greeting = Dovecot ready.
mail_location = maildir:/home/vmail/%d/%n
mmap_disable = no
valid_chroot_dirs = /var/spool/vmail
protocol imap {
  login_executable = /usr/lib/dovecot/imap-login
  mail_executable = /usr/lib/dovecot/imap
}
protocol pop3 {
  login_executable = /usr/lib/dovecot/pop3-login
  mail_executable = /usr/lib/dovecot/pop3
  pop3_uidl_format = %08Xu%08Xv
}
#auth_debug_passwords = yes
mail_debug = yes
auth_executable = /usr/lib/dovecot/dovecot-auth
auth_verbose = yes
auth default {
  mechanisms = plain cram-md5
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
  socket listen {
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
```

...but here's telnet from the server to itself on 25:

```
root@webserver:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost ESMTP Postfix (Ubuntu)
```

---

### Post by jduhls on 2011-04-11
Ha..duh.

Changed smtp port from default 25 to another less defaulty number after reading many "ISP's block port 25". I can now send email thru my SMTP server no problem.

---

