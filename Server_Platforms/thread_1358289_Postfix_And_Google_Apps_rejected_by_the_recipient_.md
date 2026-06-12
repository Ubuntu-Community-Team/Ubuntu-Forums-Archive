---
title: "Postfix And Google Apps rejected by the recipient domain"
date: 2009-12-18
forum: Server Platforms
---

### Post by boukisny on 2009-12-18
[COLOR=black][FONT=Verdana]Have a postfix mail server and I set it up to forward mail from an account ([EMAIL="mail@example.com"]mail@example.com[/EMAIL]) to a new email account that is hosted to Google apps ([EMAIL="mail@example.info"]mail@example.info[/EMAIL])[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have set up Google apps account (@info)to Send mail as my @com account.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thus when sending emails from Google apps to any email address everything works but when trying to send mail to my domain it fails and I get the below error message from Google.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]"Technical details of permanent failure:[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 Invalid recipient/sender mailing address (state 18)."[/COLOR][/FONT]
 
 
[COLOR=black][FONT=Verdana]Probably mail is rejected from my postfix server but how do I go about fixing this?[/FONT][/COLOR]

---

### Post by kadeous on 2009-12-18
Do postfix -n and post results here please, I'll try to help you the best I can.

Edit: Also check your mail logs to see what they say about the connection, it may give more detailed information.

---

### Post by kadeous on 2009-12-18
So I did some searching and found the following:

Spam blocking, make sure this isn't causing issues. [http://www200.pair.com/mecham/spam/reject_unverified.html](http://www200.pair.com/mecham/spam/reject_unverified.html)

Again, review your log files to see what's going on in the background.

Hope it helps

---

### Post by boukisny on 2009-12-21
> **kadeous said:**
> Do postfix -n and post results here please, I'll try to help you the best I can.

Edit: Also check your mail logs to see what they say about the connection, it may give more detailed information.
Hope you mean Main.cf

# These are only the parameters changed from a default install
# see /etc/postfix/main.cf.dist for a commented, fuller version of this file.

# These are changed by postfix install script
readme_directory = /usr/share/doc/postfix-2.1.4/README_FILES
sample_directory = /usr/share/doc/postfix-2.1.4/samples
html_directory = /usr/share/doc/postfix-2.1.4/html
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
command_directory = /usr/sbin
manpage_directory = /usr/share/man
daemon_directory = /usr/lib/postfix
newaliases_path = /usr/bin/newaliases.postfix
mailq_path = /usr/bin/mailq.postfix

# User configurable parameters

mynetworks_style = host
mynetworks = 192.168.10.0/24 
delay_warning_time = 4h
smtpd_banner = $myhostname ESMTP $mail_name
unknown_local_recipient_reject_code = 450
smtp-filter_destination_concurrency_limit = 2
lmtp-filter_destination_concurrency_limit = 2
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
# mydestination = $myhostname, localhost.$mydomain
mydestination = $myhostname, localhost.$mydomain, $mydomain, mydomain.com
virtual_maps = hash:/etc/postfix/virtual
canonical_maps = hash:/etc/postfix/canonical
masquerade_domains = mydomain.com
myorigin = mydomain.com
relay_domains = mydomain.com
mailbox_size_limit = 512000000
header_size_limit = 1024000
relayhost = 192.168.10.10
message_size_limit = 0

--------------------------------------------

There was talk about etc/postfix/transport but mine seems to be the original with no configurations

---

