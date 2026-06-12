---
title: "Mail question"
date: 2011-11-13
forum: Server Platforms
---

### Post by donsmouse on 2011-11-13
im going to setup a fresh install of ubuntu server 11.10 64 bit
my isp blocks port 25 and tells me to use port 587 is there a guide that i can read to accomplish this?
 
 
Thanks In Advance

---

### Post by Wayne_V on 2011-11-14
you can run your mailserver on port 25 and just map external port 587 to internal port 25 on your router/firewall.

---

### Post by donsmouse on 2011-11-14
How do I do that?

---

### Post by boast on 2011-11-14
> **donsmouse said:**
> How do I do that?

read your manual for your home router

---

### Post by SeijiSensei on 2011-11-14
If your ISP blocks *outbound* port 25, which is a common blocking strategy to limit spam from infected desktop computers, port-forwarding won't solve that.  Search Google for "postfix outbound 587" for some suggestions.

---

### Post by donsmouse on 2011-11-14
ill try my best thank you all for all your help

---

### Post by donsmouse on 2011-11-14
I tried my best and just cant get it, here is my main.cf file:


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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = smousecomputers.dyndns-server.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = smousecomputers.dyndns-server.com,localhost.localdomain,localhost,smousecomputers.dyndns-server.com
relayhost = smtp.comcast.net
mynetworks = 127.0.0.0/8,192.168.1.101
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf, hash:/var/lib/mailman/data/virtual-mailman
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
inet_protocols = ipv4
message_size_limit = 0
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
```

---

### Post by SeijiSensei on 2011-11-15
The [man page for Postfix configuration](http://www.postfix.org/postconf.5.html) states that the *relayhost* directive can include both a server and a port number.  So you could try using

relayhost = smtp.comcast.net:587

and see if that fixes the problem.  That port is open on smtp.comcast.net even, surprisingly, to machines outside the Comcast network.

---

### Post by donsmouse on 2011-11-15
now why didnt i think of doing that duh lol

i put the relay host in the main.cf file right?


Thank You

Disregard that last question im such a newb

---

### Post by dbecker on 2011-11-15
i think the bigger q. is what to do if (highly likely) that your ISP blocks incoming port 25. 
Cox does this, so i had to sign up for $10/yr mail rely service. 

If someone from hotmail sends an email to [email]you@yourdomain.com[/email], it will be sent on port25 and if your ISP blocks incoming port25, you'll never get the email. So, you setup a DNS record to point all mail.yourdomain.com traffic to the rely host. The rely host gets the email on port25, and in turn re-sends you the email on a port of your choosing, (one that isn't blocked by your isp). 

it took me a few wks to fig. this out when i setup postfix about 4 months ago. Has been working flawlessly since then.

---

### Post by donsmouse on 2011-11-15
Here is what my isp says:

**What ports are blocked by XFINITY Internet?**

             
Comcast is committed to providing a secure internet experience for all  of our customers.  For the protection of the network and our customers,  certain ports are blocked by XFINITY and XFINITY Internet.  The blocking  of these ports protects against common viruses and worms, malicious  intruders, and other security exploits.
 [LEFT]                       [LEFT][SIZE=-2]Port [/SIZE][/LEFT]
                     [LEFT][SIZE=-2]Transport [/SIZE][/LEFT]
                     [LEFT][SIZE=-2]Protocol [/SIZE][/LEFT]
                     [LEFT][SIZE=-2]Inbound/ Outbound [/SIZE][/LEFT]
                     [LEFT][SIZE=-2]Reason for block [/SIZE][/LEFT]
                     [LEFT][SIZE=-2]XFINITY/
      Comcast
      Internet[/SIZE][/LEFT]
                     [LEFT][SIZE=-2]XFINITY/
      Comcast
      WiFi[/SIZE][/LEFT]
                     [LEFT][SIZE=-2]XFINITY
      Internet2Go[/SIZE][/LEFT]
                               [CENTER][SIZE=-1]**25** [/SIZE][/CENTER]
                     [CENTER][SIZE=-1]TCP[/SIZE][/CENTER]
                     [CENTER][SIZE=-1]SMTP[/SIZE][/CENTER]
                     [CENTER][SIZE=-1]Both[/SIZE][/CENTER]
                     [SIZE=-1]Port 25 is an unsecured port on a computer  Botnet spammers can take control of to send spam - often without the  user ever knowing his/her computer has been compromised.  When spam from  a compromised computer is detected, Comcast's anti-spam systems  automatically apply a sending block and send an email notification to  the affected subscriber's comcast.net email address. This block does not  interrupt mail service for Webmail (e.g. Comcast webmail, Yahoo, Gmail,  or Hotmail); however, this block does prevent email programs or clients  (e.g. Outlook Express) from sending email.  Client email programs will  still receive email. Email clients should be reconfigured to use port  587,  _[view more FAQs]("http://sitesearch.comcast.com/?q=port+587&cat=ccentral")_ to learn about configuring common email client programs. [/SIZE]
                     [CENTER][SIZE=-1]No. Case by case blocking.[/SIZE][/CENTER]
                     [SIZE=-1]   Yes[/SIZE]
[/LEFT]

So now what do i do?, it says to use port 587

---

### Post by hawkmage on 2011-11-15
Do you realize by Comcast's terms of service running  a "public service", like SMTP, is forbidden and if they want to get picky about it they can shut down your service for it.

---

### Post by donsmouse on 2011-11-15
no i didnt relize that but ill keep that in mind

---

### Post by donsmouse on 2011-11-15
so my best bet woudl be go through a hosting company wouldnt it?

---

### Post by CharlesA on 2011-11-15
> **donsmouse said:**
> so my best bet woudl be go through a hosting company wouldnt it?
Probably.

I have a local SMTP server set to reply mail thru gmail but I only use it for email notifications from my server.

---

### Post by dbecker on 2011-11-16
> **donsmouse said:**
> so my best bet woudl be go through a hosting company wouldnt it?

its 100% up to you. like i've said, my ISP doesn't want everyone running web/email servers, and I'm guessing that's 50% of the reason why they block in/out traffic on ports 80 and 25. 

However, you pay your monthly bill and unless explicitly stated in ISP policies, you have a right to use your internet service how you like. 

As long as you don't have tons of email accts, I think you'll be fine. 

I used this guide to setup the server (chapters 1-7):
hxxp://www.howtoforge.com/perfect-server-debian-lenny-ispconfig2

then used this guide to setup postfix/squirrelmail:
hxxp://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-debian-lenny

I followed everything, exactly and it works great...from any email client, phone or through a browser.

---

### Post by boast on 2011-11-16
Luckily for me HTTP/SMTP/service ports have never been blocked. But then again I always try to get a small ISP.

---

### Post by pdoes on 2011-11-16
donsmouse:

If the SMTP server is accessible just by your internal network, which based on your main,cf it is, there's no problem with Comcast.

I just set up a similar server myself, with multiple relays to different mail servers, like Comcast and gMail.

---

### Post by acc61287 on 2011-11-16
What would be the problem if you cannot send mail? For ex. sending mail to [email]user@gmail.com[/email] or [email]user@yahoo.com[/email]?:confused: But I can receive mail from gmail:)

btw Im using postfix

---

### Post by pdoes on 2011-11-16
What does the mail log say?

I forgot where it is on Ubuntu, my guess would be /var/log/mail/maillog , I'm using FreeBSD for my server now.

---

### Post by hawkmage on 2011-11-16
The logs for postfix should be in /var/log named mail.log and mail.err.

The only way I can think of getting mail delivery is to use a relay service that will deliver to you on an alternate port.  On that I know of is [http://dyn.com/email](http://dyn.com/email) but it is a $50 a year service.

---

### Post by boast on 2011-11-16
> **acc61287 said:**
> What would be the problem if you cannot send mail? For ex. sending mail to [email]user@gmail.com[/email] or [email]user@yahoo.com[/email]?:confused: But I can receive mail from gmail:)

btw Im using postfix

I know for me, gmail would deny my emails because it was coming from a dynamic /residential IP block. So I had to use my ISPs email server as a relayhost.

---

### Post by acc61287 on 2011-11-17
Here's the logs
> 
/var/log/mail.log
Nov 17 12:26:06 #### postfix/smtp[4284]: connect to alt1.gmail-smtp-in.l.google.com[74.125.65.27]:25: Connection timed out

/var/log/mail.info
Nov 17 12:26:48 #### postfix/smtp[4284]: 46F82C0FB4: to=<****@gmail.com>, orig_to=<****@****.edu.ph>, relay=none, delay=8831, delays=8764/0.11/67/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.143.26]:25: Connection timed out)

/var/log/mail.err
Nov 17 11:16:58 #### postfix/trivial-rewrite[7974]: fatal: open dictionary: expecting "type:name" form instead of "proxy:"



I'm using webmin, ubuntu 10.04

---

### Post by acc61287 on 2011-11-17
> **boast said:**
> I know for me, gmail would deny my emails because it was coming from a dynamic /residential IP block. So I had to use my ISPs email server as a relayhost.

Do I have to contact my ISP provided to serve as relayhost?

---

### Post by boast on 2011-11-17
> **acc61287 said:**
> Do I have to contact my ISP provided to serve as relayhost?

you should check their website first. It was in a FAQ for mine, and I just needed "relayhost = smtp.ISP.com" in my main.cf and that was it.

---

### Post by pdoes on 2011-11-18
> **acc61287 said:**
> Here's the logs


I'm using webmin, ubuntu 10.04

Google uses port 587 the log shows you are using port 25

---

### Post by acc61287 on 2011-11-19
Thank you very much guys!

---

### Post by donsmouse on 2011-12-12
so how should my main.cf file look like with port 587?

and will i be able to receive mail from external domains?

any help would be appreciated
Thank you all

---

### Post by SeijiSensei on 2011-12-13
> **donsmouse said:**
> so how should my main.cf file look like with port 587?

Did you try changing the relayhost parameter as I mentioned [above]("http://ubuntuforums.org/showthread.php?p=11459100#post11459100") some weeks ago?

---

### Post by donsmouse on 2011-12-13
yes i did and i still cant get it to work
i dont kn what else to do, i will retry your steps again and thank you once again
 
ill let you know if i get it or not lol

---

### Post by donsmouse on 2011-12-14
i still cant get it
where is there a how to for relaying through gmail possibly?

---

