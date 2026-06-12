---
title: "Postfix: Ubuntu Configuration"
date: 2010-01-03
forum: Server Platforms
---

### Post by jwir3 on 2010-01-03
Hello Everyone.  I have a postfix server running on a virtual machine hosted by vpslink.com.  I have followed the following configuration guide to install the system with dovecot, sasl smtpd authentication, and postfix as an mta: [http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html)

(I know it says it's a debian configuration, but it seemed legitimate that I could follow it).

Anyway, in sending email from my primary email account, I have found that roughly 1/2 of the messages are delivered, and 1/2 of them are rejected with a message similar to the following:
> 
[FONT=-moz-fixed]This is the Postfix program at host mail.cs.umn.edu.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The Postfix program

[EMAIL="scottj@glasstowerstudios.com"]<scottj@glasstowerstudios.com>[/EMAIL]: host
    mailstore1.secureserver.net[216.69.186.201] said: 550 #5.1.0 Address
    rejected [EMAIL="scottj@glasstowerstudios.com"]scottj@glasstowerstudios.com[/EMAIL] (in reply to RCPT TO command)
[/FONT]
[FONT=-moz-fixed]

Reporting-MTA: dns; mail.cs.umn.edu
X-Postfix-Queue-ID: 16CE84DEBB
X-Postfix-Sender: rfc822; [EMAIL="scottj@cs.umn.edu"]scottj@cs.umn.edu[/EMAIL]
Arrival-Date: Sun,  3 Jan 2010 18:14:15 -0600 (CST)

Final-Recipient: rfc822; [EMAIL="scottj@glasstowerstudios.com"]scottj@glasstowerstudios.com[/EMAIL]
Original-Recipient: rfc822;scottj@glasstowerstudios.com
Action: failed
Status: 5.0.0
Remote-MTA: dns; mailstore1.secureserver.net
Diagnostic-Code: smtp; 550 #5.1.0 Address rejected [EMAIL="scottj@glasstowerstudios.com"]scottj@glasstowerstudios.co[/EMAIL][/FONT]
I am having trouble understanding what is causing this errant behaviour.  It seems to me that godaddy, the dns service that I use, doesn't allow mail through for glasstowerstudios.com, but sometimes it does?  I'm not sure how to correct this.  I have worked with a number of postfix configurations, and I don't think that it's the postfix configuration that seems to be the problem.  Instead, it seems as though the messages aren't getting to postfix to be processed (the logs don't seem to show anything for the messages that are rejected).

Here are my DNS settings:

> 
A Records
Host                                        | Points to
@                                            | 64.79.219.177
dagobah.glasstowerstudios.com | 64.79.219.177

CNAME Records
Host | Points to
mail | dagobah.glasstowerstudios.com

MX Records
Priority | Host | Goes to
10        | @     | mail.glasstowerstudios.com
My configuration files follow.  I'm at a complete loss as to why this isn't working.  Any help would be greatly appreciated!  Thank you, 

~Scott

master.cf config file:
> 
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
#       -o content_filter=spamassassin
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
#628      inet  n       -       -       -       -       qmqpd
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

#spamassassin unix -    n       n       -       -       pipe
#       user=spamd argv=/usr/bin/spamc -f -e
#       /usr/sbin/sendmail -oi -f ${sender} ${recipient}
main.cf config file:
> 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# setup for local generated mails
#append_dot_mydomain = yes
#masquerade_domains = glasstowerstudios.com

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

#readme_directory = no
#html_directory = no

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# general stuff
myhostname = mail.glasstowerstudios.com
relay_domains = glasstowerstudios.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = glasstowerstudios.com
mydestination = mail.glasstowerstudios.com, mail, localhost, localhost.localdomain, glasstowerstudios.com
relay_host =
mynetworks = 127.0.0.0/8
recipient_delimiter = +
mailbox_size_limit = 0
inet_interfaces = all

home_mailbox = Maildir/
mailbox_command =

# SMTPD Server - old restrictions
smtpd_recipient_limit = 250
smtpd_client_restrictions =
smtpd_sender_restrictions =
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients =  yes
smtpd_tls_cert_file = /etc/ssl/certs/dovecot.crt
smtpd_tls_key_file = /etc/ssl/private/dovecot.key
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtpd_tls_log_level =4
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_use_tls = yes

# SMTP Client
smtp_sasl_application_name = smtpd
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes



---

### Post by sylvester_0 on 2010-01-03
Take a look at my nslookup output:

```
$ nslookup
> set type=mx
> glasstowerstudios.com
Server:		10.2.1.1
Address:	10.2.1.1#53

Non-authoritative answer:
glasstowerstudios.com	mail exchanger = 10 mailstore1.secureserver.net.
glasstowerstudios.com	mail exchanger = 0 mail.glasstowerstudios.com.

Authoritative answers can be found from:

```

It seems that the mailstore1.secureserver.net is a Godaddy server (which you don't want to use.) Simply delete that one from your Godaddy total dns control panel and you should be good!

EDIT: I should also mention that you should allow some time for that change to propagate through the DNS system (TTLs and caching etc.)

---

### Post by jwir3 on 2010-01-03
Hi sylvester_0:

Thanks for the reply.  I didn't even think to look at an nslookup (a duh).  You're right, there is another server taking some of my mail.  I don't have that mail server in my total dns control, though.  The only one I have is for mail.glasstowerstudios.com.  So, it doesn't appear that I can delete it.

What I did was set the priority of my server to 0, since the godaddy one seems to be set at 10.  This seems to be working now, but do you think that it will always work, or will it just decrease the amount of mail that gets forwarded to mailstore1.secureserver.net? 

Thanks, 

~Scott

---

### Post by sylvester_0 on 2010-01-03
Yeah, the first thing I thought of was to do an mx lookup when you said you're getting your mail half of the time. It's confirmed in the bounceback that you posted that mail.cs.umn.edu is trying to deliver mail to mailstore1.secureserver.net (GoDaddy's mail server.)

By doing a whois and subsequent nslookup on your domain's MX I can see that GoDaddy's DNS servers do indeed still have their own mail server as a MX record.

```
$ whois glasstowerstudios.com
...
Domain servers in listed order:
      NS09.DOMAINCONTROL.COM
      NS10.DOMAINCONTROL.COM

$ nslookup
> server ns09.domaincontrol.com
Default server: ns09.domaincontrol.com
Address: 216.69.185.5#53
> set type=mx
> glasstowerstudios.com
Server:		ns09.domaincontrol.com
Address:	216.69.185.5#53

glasstowerstudios.com	mail exchanger = 0 mail.glasstowerstudios.com.
glasstowerstudios.com	mail exchanger = 10 mailstore1.secureserver.net.
> server ns10.domaincontrol.com
Default server: ns10.domaincontrol.com
Address: 208.109.255.5#53
> glasstowerstudios.com
Server:		ns10.domaincontrol.com
Address:	208.109.255.5#53

glasstowerstudios.com	mail exchanger = 0 mail.glasstowerstudios.com.
glasstowerstudios.com	mail exchanger = 10 mailstore1.secureserver.net.

```

Bottom line is that if you're sure you're not seeing that MX "10 mailstore1.secureserver.net." in your total DNS control panel and you didn't just delete it, something is wrong and you should get in contact with GoDaddy. It wouldn't be good practice to leave an inactive MX laying around in DNS.

OT: I just noticed that you're in my area! I'm in West Fargo myself :)

---

### Post by jwir3 on 2010-01-03
Right on, I'll contact them as soon as I get a chance. 

OT:  Cool, yeah I'm originally from Grand Forks.  Living in the twin cities now, but I get home every now and then for a Sioux hockey game.  :)

---

### Post by volkswagner on 2010-01-04
If you can't remove the GoDaddy MX record, you can change your DNS server to vpslink.com's DNS Server.  That way you should be able to have full control on your DNS profile from vpslink.com's control panel.

Although if you still want to use godaddy's DNS, there should be no problem pointing the MX record to your mail server at vpslink.  Do check again because there are two MX listing in the DNS control at GoDaddy, one for smtp and one for mailstore1.

---

