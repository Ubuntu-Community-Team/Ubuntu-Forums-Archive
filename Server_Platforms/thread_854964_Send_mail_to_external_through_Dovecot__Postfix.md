---
title: "Send mail to external through Dovecot / Postfix"
date: 2008-07-10
forum: Server Platforms
---

### Post by skunkbad on 2008-07-10
Ubuntu 8.04 / Postfix / Dovecot

List of what works:
[LIST]
[*]PHP mail() function works
[*]ddclient can send email notifications
[*]Send mail internally user to user
[*]telnet mail internally user to user
[*]mail sent from world to user appears in Maildir/new/
[*]Externally, Mozilla Thunderbird gets mail from user's Maildir/new/
[*]Externally, Mozilla Thunderbird sends mail to user's Maildir/new/
[/LIST]

What doesn't work:
[LIST]
[*]Externally, Mozilla Thunderbird will not send mail to server to relay to world (other external)
[/LIST]

For instance, when I am at home, and try to use Thunderbird to send an email from my user to [email]anybody@gmail.com[/email], I get a "...does not relay mail..." message. I'm assuming this is because I have not configured that users can relay to the world.

The tutorial I followed that most closely represents my current configuration of Postfix is at [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto")

My current main.cf:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all

```

I need help with the mail relay issue.

---

### Post by skunkbad on 2008-07-10
I just want to add that I do have relayhost = in the main.cf. From reading, I assumed this was all I needed to do to let users send mail to external hosts, but it isn't working.

---

### Post by skunkbad on 2008-07-12
I'm still stuck. I wanted to include the tail of mail.log in case it helps:

```

Jul 11 23:32:13 webserver postfix/smtpd[5029]: connect from pool-71-177-134-19.lsanca.fios.verizon.net[71.177.134.19]
Jul 11 23:32:14 webserver postfix/smtpd[5029]: NOQUEUE: reject: RCPT from pool-71-177-134-19.lsanca.fios.verizon.net[71.177.134.19]: 554 5.7.1 <alive@somewhere.com>: Relay access denied; from=<name@homedomain.com> to=<alive@somewhere.com> proto=ESMTP helo=<new-host.home>
Jul 11 23:32:23 webserver postfix/smtpd[5029]: disconnect from pool-71-177-134-19.lsanca.fios.verizon.net[71.177.134.19]

```

---

