---
title: "Postfix sending external mail...."
date: 2006-05-17
forum: Server Platforms
---

### Post by und3rtug4 on 2006-05-17
Hi there!

I hade configured a postfix, pop, imap server, and using squirrelmail as webmail!
Everything seens to work ok, but i just can't send any email to external recipients like *@gmail.com and so!

It sends the mail to the internal accounts nicely, but I wanna send mail to the outside world and just dont know how! ](*,) ](*,) 


Thanks in advance!

---

### Post by rickyjones on 2006-05-18
Since I just managed to get my own email system working at home, I think I might be able to lend a hand in this situation.

Wanna list what you've done thus far (as in, installing programs and configurations) - probably might be wise to post the /etc/postfix/main.cf file as well.

Also, what kind of internet do you have at home?

-Richard

---

### Post by und3rtug4 on 2006-05-18
I followed this guide[ here]("http://flurdy.com/docs/postfix/"), mencioned in this [post]("http://ubuntuforums.org/showthread.php?t=97600&highlight=mail")!

Every thing  went  smooth, unitl i tried to send an email to "the outside worlld"!!

Any suggestions on what i did wrong, or what needs to be done??

Thanks in advance!

und3rtug4

---

### Post by Glut on 2006-05-18
What's the error?
Are you using a smarthost or connecting directly (main.cf)?

---

### Post by und3rtug4 on 2006-05-19
Well, has asked by you guys, here's my main.cf file:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = Bunk3r IT Industries ESMTP
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

myhostname = mail.bunk3r.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
local_recipient_maps =
relayhost =
mynetworks = all
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unauth_pipelining, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_helo_required = yes

smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.c

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

                                                                                                            


```

The error displayed at first was this:
```

Transaction failed
Server replied: 554 <undertuga@gmail.com>: Relay access denied

```

Then, after that error, i added the gmail.com domain to my domain table, then, i got this error:

```

Requested action not taken: mailbox unavailable
Server replied: 550 <undertuga@gmail.com>: Recipient address rejected: User unknown in virtual mailbox table

```

but, i think this method is not the right one, because do you imagine the big list that i had to type in order to send emails to everyone i wanted (lots and lots of domains and users to add, just too much), understand my point??

I hope this could help on helping me!


Thanks to all in advance!

---

### Post by Glut on 2006-05-22
gmail shouldn't be a part of your domain table, it's not your domain. 
Can you put me straight, are you trying to send from a gmail account using your own smtp server?

---

### Post by und3rtug4 on 2006-05-22
----

---

### Post by und3rtug4 on 2006-05-22
[QUOTE=Glut]gmail shouldn't be a part of your domain table, it's not your domain. 
Can you put me straight, are you trying to send from a gmail account using your own smtp server?[/QUOTE]


No, i'm trying to send mails from my smtp server to external email accounts such *@gmail.com or *@somedomain.*, and it just won't mail send them!

How do I "tell" the smtp server to let the mails been sent to "the outside world"??

Thanks to all in advance.
Regards

---

### Post by Glut on 2006-05-22
Ok, Can I just check some config settings:
I'm hoping that mydestination was blanked out by you, if not fill it in.
Change mynetworks to be your network + 127.0.0.0/8 I understand that you're testing, but making it right now souldn't cause an issue.

You have 2 smtpd_sender_restrictions lines, just keep the one that you want. Also, check /etc/mailname you may need to change it - generally it's set to $mydomain
You may also want to add more warn_of_reject prefixes to your sender restrictions, so you can receive logs when an send has failed due to your ruels.

If more problems, you may want to check out the postfix users list: [http://www.postfix.org/lists.html](http://www.postfix.org/lists.html), it's active and helpful.

---

### Post by und3rtug4 on 2006-05-23
> Ok, Can I just check some config settings:
I'm hoping that mydestination was blanked out by you, if not fill it in.
Change mynetworks to be your network + 127.0.0.0/8 I understand that you're testing, but making it right now souldn't cause an issue.

You have 2 smtpd_sender_restrictions lines, just keep the one that you want. Also, check /etc/mailname you may need to change it - generally it's set to $mydomain
You may also want to add more warn_of_reject prefixes to your sender restrictions, so you can receive logs when an send has failed due to your ruels.

If more problems, you may want to check out the postfix users list: [http://www.postfix.org/lists.html](http://www.postfix.org/lists.html), it's active and helpful.


YEAHHHHH IT'S WORKING!!!

Just follow your tips, and changed mynetworks field to:

```
mynetworks = host 127.0.0.0/8 10.0.0.0/20
```

and also changed the restrictions to this:

```
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_helo_required = yes

```

reloaded the MTA and it's working!

For those who may have this problem in the future, here's my main.cf file in order to guide you folks on the config stage!

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = Bunk3r IT Industries ESMTP
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

myhostname = your.domain.here
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
local_recipient_maps =
relayhost =
mynetworks = host 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_helo_required = yes

smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.c

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

```

Thanks to all for the help!;) ;) 

Regards,

und3rtug4

---

### Post by wb7ubb on 2006-06-02
Moved to the Newbie section

---

