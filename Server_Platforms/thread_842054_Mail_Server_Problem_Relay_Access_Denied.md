---
title: "Mail Server Problem Relay Access Denied"
date: 2008-06-27
forum: Server Platforms
---

### Post by solidus23 on 2008-06-27
Hello everyone. I have been searching all over for a solution to my problems and have found some help but nothing has worked. I have my mail server setup and can send mail internally on my home network and can send out ex. I can send an email to my gmail account. Though when I go to send an email from gmail to my email server I get the 554 Error Relay Access Denied. I have my server setup at No-IP temporarily to test things out. I know it is pointing to the correct IP and everything. I just cannot figure it out. If you need me to post any configurations just tell me. Thanks.

---

### Post by MJN on 2008-06-27
[Edit: I have assumed Postfix here but notice now you didn't specify]
 
Your mail config (/etc/postfix/main.cf) would help!
 
It is most likely a problem with the definition (or lack of) of which domains your MTA think's it is responsible for.
 
Mathew

---

### Post by solidus23 on 2008-06-27
Yes I am using Postfix... I can't believe I didn't state that before. I have I  feeling it is actually the lack of domains, can I have it responsible for more than one? Do I seperate them with a space, coma, or something else? Here is the main.cf:

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

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = strausmail.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = strausmail.com, mail.strausmail.com, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 51200000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination,check_policy_service inet:127.0.0.1:60000
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
content_filter = smtp-amavis:[127.0.0.1]:10024

---

### Post by MJN on 2008-06-27
Is strausmail.com your real domain?

If not, we'll need to know that before proceeding (and please mention if you've modified the config prior to posting!)

Mathew

---

### Post by solidus23 on 2008-06-27
As of right now no... it is strausmail.no-ip.org. I plan on buying the domain strausmail.com later after I get this all figured out. I have only changed a few things after I posted the main.cf. I added the strausmail.no-ip.org to the myhostname and mydestination sections.

---

### Post by MJN on 2008-06-27
Oh I see. It should work now.
 
If that's the domain you want I'd get it right now before you do anything else!
 
Mathew

---

### Post by solidus23 on 2008-06-27
Yes... It just started working lol. Thanks for all you help. I should have tried this before I posted... but I wasn't sure if it was the right thing to do. I hope others benefit from this post.

---

### Post by MJN on 2008-06-27
That's excellent. By the way, remove the no-ip name from the myhostname directive as this should only contain the name of the server (and be fully-qualified i.e. something.strausmail.com).
 
Mathew

---

### Post by solidus23 on 2008-06-27
Does anyone have experience setting up domain names they bought? I have bought the strausmail.com domain name from godaddy. Though I don't really know how to get it to point to my server. Any help is appreciated.

EDIT:
I got it working now.

---

### Post by solidus23 on 2008-06-27
I am now getting a new error. Everything was working before, but now I get the 553 error relaying denied. I don't know what has caused this... I was messing around with some settings to transition my mail server to strausmail.com and now when send an email to [email]username@strausmail.com[/email] I get this error.

---

### Post by MJN on 2008-06-27
There are a number of problems, neither of which explains the relay denial but until they're fixed we can't proceed.

Firstly, your DNS is broken - specifically your MX record for strausmail.com resolves to a name that has no corresponding A record.

```
$ dig strausmail.com MX
; <<>> DiG 9.3.2 <<>> strausmail.com MX
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5719
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;strausmail.com.                        IN      MX

;; ANSWER SECTION:
strausmail.com.         3392    IN      MX      0 smtp.strausmail.net.

;; Query time: 26 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jun 27 18:15:50 2008
;; MSG SIZE  rcvd: 67

$ dig smtp.strausmail.net A

; <<>> DiG 9.3.2 <<>> smtp.strausmail.net A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 33601
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;smtp.strausmail.net.           IN      A

;; Query time: 17 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Fri Jun 27 18:16:24 2008
;; MSG SIZE  rcvd: 37[code]

However, some MTAs may fall back on resolving the A record directly for strausmail.com which does currently resolve to 71.230.13.106 (same as your strausmail.no-ip.org).

When connecting to 71.230.13.106 though it fails to connect:

[code]$ telnet 71.230.13.106 25
Trying 71.230.13.106...
```You need to check your mail server us up-and-running and that your DNS is configured correctly to point at your IP (which I'm guessing may well have changed since the last DNS update).

Mathew

---

### Post by solidus23 on 2008-06-27
Thanks for the info... I have reinstalled ubuntu server and am reconfiguring everything again. When I get to the point of testing email sending I will check to make sure it is working. I dont really understand though what you were saying in your last post.

---

### Post by MJN on 2008-06-27
Which bit? The stuff about DNS?

Basically, you need to enter what's known as an MX record for your domain - this tells other MTAs who handles the mail for you. The MX record needs to point to another name/record which in turns gets resolved in to an IP address.

So, you need an MX record for strausmail.com pointing to something like mail.strausmail.com (call it what you like) and then an A record for mail.strausmail.com pointing to your IP address.

It looks like you were getting somewhere with putting in the MX record but you pointed it to a name that doesn't exist (and is not within your domain) - smtp.strausmail.net

Mathew

---

### Post by solidus23 on 2008-06-27
I understand what you are saying now... thank. I will definitely take a look at it and configure it so it will work. It gets a little confusing with all the pointing lol.

Here is a screenshot of my godaddy dns config.... tell me what is wrong with it lol. I don't know.

---

### Post by MJN on 2008-06-27
Unfortunately the linked image is too small for me to make out.

Mathew

---

### Post by solidus23 on 2008-06-27
Try saving the image and then zooming in on it. Sorry about that.

---

### Post by MJN on 2008-06-27
No joy. The resolution (426x266) just doesn't cut it.

Mathew

---

### Post by solidus23 on 2008-06-28
I have the file if you want me to email it to you? Since I can't get it to play nice with the site.

---

### Post by MJN on 2008-06-29
Sure - you can send it to uf @ newtonnet.co.uk

Mathew

---

### Post by MJN on 2008-06-30
Okay, picture received (all 4MB of it!).
 
The only thing you need to change is the MX record/section. Change it to point to mail.strausmail.com
 
It is currently pointing to smtp.strausmail.net but this domain is not yours (i.e. the .net suffix variation). Changing it to mail. is a personal thing, I prefer it as smtp implies (to me) an outgoing mail server which as far as your MX records are concerned it is not.
 
Mathew

---

### Post by solidus23 on 2008-07-01
Thank you for that. I can't believe I did not see that, especially the strausmail.net which I don't even own. Thanks again.

---

### Post by MJN on 2008-07-02
It's easily done - a classic case of not being able to see the wood for the trees!
 
Mathew

---

### Post by windependence on 2008-07-02
> **solidus23 said:**
> Does anyone have experience setting up domain names they bought? I have bought the strausmail.com domain name from godaddy. Though I don't really know how to get it to point to my server. Any help is appreciated.

EDIT:
I got it working now.

You need to go in to your domain control panel at Godaddy and configure your settings there. If you call them, they will walk you through it over the phone for free. They have excellent tech support, and this is part of their service. You will have to set up your A record and MX record to point it at your IP address. You really should consider buying a static address because many servers on the net now block dynamic IP services.

-Tim

---

