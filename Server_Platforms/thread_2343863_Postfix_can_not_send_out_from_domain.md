---
title: "Postfix can not send out from domain"
date: 2016-11-20
forum: Server Platforms
---

### Post by davespace on 2016-11-20
Postfix is working fine for my email clients and such. However, I am trying to send mails from ruby;and they do not  show up in /var/log/mail.log.
Upon further investigation, I found out that mails sent with mailutils were not being delivered. I did notice in the logs that the mails were attempted to be sent
like  [EMAIL="user@mail.mydomain.com"]user@mail.mydomain.com[/EMAIL] resulting in looping back to itself. I have another domain setup with exactly the same main.cf. - it does not send out from  mailutils either,
however the logs show that the emails are queued , but they are being sent as [EMAIL="user@domain.com"]user@domain.com[/EMAIL], instead of [EMAIL="user@mail.domain.com"]user@mail.domain.com[/EMAIL]. The dns is the same for both domains,
hostname setup as mail.mydomain.com on both machines. /etc/hosts are the same for both machines. So, effectively, neither host is sending from itself, but works in all other aspects.
of course when i say mydomain- i am using my unique FQDN, I do not have the FQDN listed in mydestination- tried , but it had no effect.

literally whats on this line for both machines in main.cf-------------->mydestination = $myhostname, localhost.$mydomain, localhost

---

### Post by TheFu on 2016-11-20
Welcome to the forums.

Please provide some background. I don't want to dig in technically if the connection type and domain setup isn't correct first.

* What type of connection to the internet does it have?  Residential ISP or business ISP?
* Where is the server located? In a data center, at home? at work?
* Is the domain through a registrar or just something made up?
* Is the DNS setup WITH proper MX, SFP, and DKIM TXT records?
* Where are you trying to send email to?  Same machine, same subnet? Only 1 email address or on the internet at large? Being able to email 1 address is possible without full domain setup, BTW.

Sorry to ask so many non-technical questions, but we see lots of questions here about email and many people don't realize how a simple protocol that should be easily used by every computer on the internet has become fairly complicated due to spam email senders so that basically blocking spammers is almost more important than allowing every system to send email.

If you don't know the answer to each of those questions, don't guess, but please answer them all.

---

### Post by davespace on 2016-11-20
geez the way its going... tried to post a lengthy reply-first time Im here- when I hit reply, the site lost everything.
1. digital ocean droplets  
2. cloud
3. registered domains
4. dns has MX, SFP,- no DKIM yet
5. trying to send mail out that originates from localhost, to me.com(apple) or gmail- I'm trying to get the ruby gem mail working for a rails project;

---

### Post by wildmanne39 on 2016-11-20
>  geez the way its going... tried to post a lengthy reply-first time Im here- when I hit reply, the site lost everything.We are having a few forum issues right now, that happened to me yesterday I just hit the back button and the reply was sill there so I copied it in case it happened again but it did not.

---

### Post by TheFu on 2016-11-20
Ok. Thanks. Won't waste time on residential issues for email servers.

So is the gem trying to use the local MTA or trying to connect via SMTP to a remote system itself?  What do the log files show - ruby/app?  Lots of scripting languages don't use the local MTA, which would explain why nothing shows in the mail.log.  Many gems will expect a configuration too. I expect this is the root issue.

BTW, it isn't clear if this specific mail server sends and receives email outside of the ruby program or not. Please clarify.

---

### Post by davespace on 2016-11-20
Yes , the gem connects to smtp; and I am trying to use irb- ruby's interactive shell to send at the moment,
but actuallly, I need to receive mail into the app as well. [https://github.com/mikel/mail](https://github.com/mikel/mail) 
> The purpose of this library is to provide a single point of access to handle all email functions, including sending and receiving emails.  All network type actions are done through proxy methods to Net::SMTP, Net::POP3 etc.

                                                                ^POP3

---

### Post by TheFu on 2016-11-20
I think it is still a ruby issue.  Perhaps if you asked in that IRC or forum?  If nothing is showing up in the postfix logs, I have suspicions that the system MTA isn't being used. Sure, I could be wrong.

I did program in ruby for a few years, but left for another language that didn't change every other year. ;)  Which gem?

To check this, use regular "Mail" tools - does that work with postfix or not?

---

### Post by davespace on 2016-11-20
I installed mailutils,(explained in op) which should mail from the command line. like so. "mail [email]me@gmail.com[/email] or mail [email]me@me.com[/email]", does not work. The gem is fine, it is integrated into stock ruby.

This is how I tested the domains and realized there was an issue. I cant really test the gem if emails are not being sent, now can I? First things First

---

### Post by TheFu on 2016-11-21
**postconf -n** please.
If you obfuscate, please use "example.com"

---

### Post by davespace on 2016-11-21
postconf -n

```
postconf: warning: /etc/postfix/main.cf, line 685: overriding earlier entry: inet_interfaces=localhost
postconf: warning: /etc/postfix/main.cf, line 686: overriding earlier entry: mydestination=$myhostname, localhost.$mydomain, localhost
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
daemon_directory = /usr/libexec/postfix
data_directory = /var/lib/postfix
debug_peer_level = 2
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin ddd $daemon_directory/$process_name $process_id & sleep 5
home_mailbox = Maildir/
html_directory = no
inet_interfaces = all
inet_protocols = all
mail_owner = postfix
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mydomain = davomail.com
myhostname = mail.davomail.com
mynetworks = 127.0.0.0/8
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.10.1/README_FILES
relay_domains = $mydestination
relayhost = mail.davomail.com:993
sample_directory = /usr/share/doc/postfix-2.10.1/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = login
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/postfix/ssl/server.crt
smtpd_tls_key_file = /etc/postfix/ssl/server.key
smtpd_tls_loglevel = 1
smtpd_tls_security_level = may
unknown_local_recipient_reject_code = 550
```
===================================================
thank you, for helping with this. I solved the issue with the other domain. I forgot that is Centos 7, so I had it configured to a different client. I had to use mailx [email]me@gmail.com[/email] instead of mail. So this domain is working from localhost.
The warnings are from me changing things in postconf -n

---

### Post by wildmanne39 on 2016-11-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by davespace on 2016-11-21
I reinstalled postfix purge/install, but  there were too many problems with missing files after this operation, so I ditched the vps and spun up another.
thanks for anyone who invested time in this.
closing thread/discussion now.

---

