---
title: "email won't get delivered &quot;address rejected: User unknown in virtual mailbox table&quot;"
date: 2012-09-19
forum: Server Platforms
---

### Post by Ortix on 2012-09-19
So I have ran into a little problem with my email.

I'm running openpanel with postfix and my email is the only one (i have other domains too which work fine) which gets this error:
address rejected: User unknown in virtual mailbox table

In other words, I can't receive any mail (sending is not set up yet)

I THINK that the problem lies with the fact that i have a user on ubuntu called "ortix" but my email is owned by ortix92 (due to conflicts) and my email is ortix @ tld.com

any ideas?

I'm using
[http://network-tools.com/default.asp?prog=test&noncache=yes&host=ortix%40ortixdesign.com](http://network-tools.com/default.asp?prog=test&noncache=yes&host=ortix%40ortixdesign.com)

to check what's going on.. help would be appreciated!

EDIT:
I tested another username with the same result, basically NO email works with my domain... all the DNS settings are correct! dig mx gives proper answers and everything! Could it be permission issues on the server?

main.cf:
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = icarus.ledigroup.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localmail.icarus.ledigroup.com
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_relay_domains, reject_unauth_destination
virtual_mailbox_domains = $virtual_mailbox_maps, hash:/etc/postfix/openpanel/virtual_mailbox_domains
virtual_mailbox_maps = hash:/etc/postfix/openpanel/virtual_mailbox
virtual_alias_maps = $virtual_maps, hash:/etc/postfix/openpanel/virtual_alias
transport_maps = hash:/etc/postfix/openpanel/transport_map
relay_domains = $mydestination, hash:/etc/postfix/openpanel/transport_map
network tools:
> [FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][FONT=Arial][SIZE=3][COLOR=Green][Resolving mail.tld.com...][/COLOR]
[FONT=Arial][SIZE=3][COLOR=Green][Contacting mail.tld.com ****]...][/COLOR]
[FONT=Arial][SIZE=3][COLOR=Green][Connected][/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]220 icarus.***.com ESMTP Postfix (Ubuntu)[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]EHLO Network-Tools.com[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-icarus.***.com[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-PIPELINING[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-SIZE 10240000[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-VRFY[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-ETRN[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-STARTTLS[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-AUTH PLAIN LOGIN[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-ENHANCEDSTATUSCODES[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250-8BITMIME[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 DSN[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]VRFY ortix[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]550 5.1.1 <ortix>: Recipient address rejected: User unknown in virtual mailbox table[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]RSET[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 2.0.0 Ok[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]EXPN ortix[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]502 5.5.2 Error: command not recognized[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]RSET[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 2.0.0 Ok[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]MAIL FROM:<admin@Network-Tools.com>[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 2.1.0 Ok[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]RCPT TO:<ortix@tld.com>[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 2.1.5 Ok[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]RSET[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]250 2.0.0 Ok[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Navy]QUIT[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Black]221 2.0.0 Bye[/COLOR]
[FONT=Arial][SIZE=3][COLOR=Green][Connection closed][/COLOR][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT](note: removed my domain name against spam)

---

### Post by volkswagner on 2012-09-20
When modifying addresses and domains did you update postfix?

like:

```
command = postmap /etc/postfix/openpanel/virtual_mailbox_domains
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox
```


I don't recall if you have to restart postfix after running postmap commands.

Of course your new domains and mailboxes would need to actually be in the above files.

---

### Post by Ortix on 2012-09-20
> **volkswagner said:**
> When modifying addresses and domains did you update postfix?

like:

```
command = postmap /etc/postfix/openpanel/virtual_mailbox_domains
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox
```
I don't recall if you have to restart postfix after running postmap commands.

Of course your new domains and mailboxes would need to actually be in the above files.

how in the world did this end up working? Just these two simple commands and my email is back online! Holy cow! Thanks a trillion!

---

### Post by Ortix on 2012-09-21
actually.. this did NOT end up working.. somehow i got 3 emails which were test mails that i send the night before and somehow i received them.. still not receiving any mail..

---

### Post by volkswagner on 2012-09-21
Did you restart postfix after running postmap commands?

I notice the first command I gave you is missing the 'hash:" portion.

Should be:
```
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox_domains
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox
```

What is the out put of the following:

```
 postmap -q brokenaddress@yourdomain.com  cidr:/etc/postfix/networktable
```

Where brokenaddress =  the mailbox that can't receive mail.

---

### Post by Ortix on 2012-09-21
> **volkswagner said:**
> Did you restart postfix after running postmap commands?

I notice the first command I gave you is missing the 'hash:" portion.

Should be:
```
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox_domains
command = postmap hash:/etc/postfix/openpanel/virtual_mailbox
```What is the out put of the following:

```
 postmap -q brokenaddress@yourdomain.com  cidr:/etc/postfix/networktable
```Where brokenaddress =  the mailbox that can't receive mail.

yes i restart it like this: postmap stop, postmap start and then i do postmap reload just in case.

I ran your two commands, restarted postfix and no luck. Then i ran the other command and got this:
```
root@icarus:/etc/postfix# postmap -q user@domain.com  cidr:/etc/postfix/networktable
postmap: fatal: open /etc/postfix/networktable: No such file or directory

```Also NO single mailbox can receive email on this domain.

---

### Post by volkswagner on 2012-09-21
Sorry my paste edit problem:

Should be:

```
postmap -q email@problem.com cidr:/etc/postfix/openpanel/virtual_mailbox
```

You should mask your email address when posting to the forum.  You are exposing yourself to much spam.  Well if you ever get the address working :)

If it is a domain wide problem, try:

```
postmap -q problemdomain.com cidr:/etc/postfix/openpanel/virtual_mailbox_domains
```

or


How many unique domains did you have working prior the problem with the current domain?

Are all the expected domains in transport_map?

```
postmap -q brokendomain.com cidr:/etc/postfix/openpanel/transport_map
```

---

### Post by Ortix on 2012-09-22
I ran the first two commands with output:
```

postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 1: bad address pattern: "user@workingdomain.info": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 2: bad address pattern: "user@workingdomain.com": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 3: bad address pattern: "myuser@nonworkingdomain.com": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 4: bad address pattern: "myuser@nonworkingdomain.com": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 5: bad address pattern: "user@workingdomain.com": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox, line 6: bad address pattern: "myuser@nonworkingdomain.com": skipping this rule

``````

postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox_domains, line 1: bad address pattern: "workingdomain.com": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox_domains, line 2: bad address pattern: "workingdomain.info": skipping this rule
postmap: warning: cidr map /etc/postfix/openpanel/virtual_mailbox_domains, line 3: bad address pattern: "nonworkingdomain.com": skipping this rule

```so my domain is the only one not working.. The rest works (total 2 which work) fine even though they all give the same error/warning

Also. The transport_map file is empty.. there's nothing in there

---

### Post by volkswagner on 2012-09-22
By any chance is the working domain listed under "mydestination"?

Although the errors _may_ not be related, it is bad practice to assume.  You should clear these errors by using the correct syntax for those files.

These files need a left and right hand column.  The left hand shall be the search item, the right hand can be anything... like:

```
myuser@domain1.com ok
user1@otherdomain.info ok
user3@mydomain.com ok
```

or

```
domain1.com yes
domain2.info yes
mydomain.net ok
```

Again what you put on the right side does not matter but it must exist for the left side to be honored.  So even if you put "mydomain.com no" it will still read as ok or yes.

Have a look a the [Postfix Maildrop docs]("http://www.postfix.org/MAILDROP_README.html").

You can try temporarily stopping the user/domain checks to see if the mail gets through.

Change:

```
virtual_mailbox_maps = hash:/etc/postfix/virtual_mailbox
```
to
```
virtual_mailbox_maps =
```

I would focus on the errors from your last post before making additional changes.

---

### Post by Ortix on 2012-09-23
So i decided to take the quick and dirty way and my hopes became true. I went into openpanel, removed the entire domain from the system and restarted postfix. Then my client started complaining that my password for my email was wrong, so I figured something is gonna work. So i recreated my email, restarted postfix, sent a couple of test mails and it seems to work now.. Let's hope it KEEPS working :)

I would just like to let you know that I am extremely grateful for your help and time! Much appreciated!

---

