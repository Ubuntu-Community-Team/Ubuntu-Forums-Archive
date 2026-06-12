---
title: "Email Server Can't Send Email"
date: 2009-04-21
forum: Server Platforms
---

### Post by kevin11951 on 2009-04-21
I setup an email server for a testing environment (so it dosent matter if this ends up badly :))

The problem is that i cant send any emails from it, i can receive them, but not send, when i send it i get this error > connect to alt4.gmail-smtp-in.l.google.com[72.14.253.27]:25: Connection timed out (for gmail in this case)

not sure how to fix this.

Its the default "tasksel" email stack (postfix and dovecot).

Also, i am very new to email servers.

---

### Post by Dr Small on 2009-04-21
Can you telnet to it?
```
telnet alt4.gmail-smtp-in.l.google.com 25
```

Also, do you have a FQDN?
[http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)

Dr Small

---

### Post by HermanAB on 2009-04-21
Most newbie email server problems are due to a misconfigured hostname and DNS.  You *must* have a FQDN, A, PTR and MX records. Get your network configured correctly and the trouble will likely go away.

---

### Post by kevin11951 on 2009-04-21
Yes, i have a FQDN, its kviero.com, and its in the hosts file.

The mx records on godaddy's (my domin registrar) side are all set to my external ip, that includes smtp.* imap.* pop.* mail.* etc... and to top it all off, my router is set to dmz the servers internal ip.

i know i am over looking something simple.

(also, im not sure if you meant it that way, but "newbie" has a very negative meaning to it, for me)

---

### Post by kevin11951 on 2009-04-21
How do you setup a FQDN?  this is my hosts file, is it right?

```
127.0.0.1	kviero.com	localhost
127.0.1.1	kviero.com	Kviero-64

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by ephmanjmm on 2009-04-21
I am not getting any info about an mx record when I dig mx kviero.com.  nslookup responds with no answer for the mx record.

---

### Post by kevin11951 on 2009-04-21
> **ephmanjmm said:**
> I am not getting any info about an mx record when I dig mx kviero.com.  nslookup responds with no answer for the mx record.

does anyone here have any experience setting up an email server with a godaddy domain name?

---

### Post by Dr Small on 2009-04-21
Well, let's sort things out in order.

Your first problem of Connection timed out. Try telneting like I showed, to see if it telnets properly. If so, we can move on.

Also, please post the output of this:
```
sudo postconf -n
```

---

### Post by kevin11951 on 2009-04-21
> **Dr Small said:**
> Well, let's sort things out in order.

Your first problem of Connection timed out. Try telneting like I showed, to see if it telnets properly. If so, we can move on.

Also, please post the output of this:
```
sudo postconf -n
```

telnet didn't work, but a ping did...

output of above:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_protocols = all
mailbox_command = 
mailbox_size_limit = 0
mydestination = kviero.com, Kviero-64.gateway.2wire.net, localhost.gateway.2wire.net, localhost
myhostname = kviero.com
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unknown_sender_domain reject_unknown_recipient_domain reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_unauth_destination permit_inet_interfaces
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

---

### Post by HermanAB on 2009-04-21
Everybody is a newbie at some point. No offense meant.

Your MX record doesn't resolve for kviero.com:

$ dig kviero.com MX
...ANSWER 0...

Setting it up in GoDaddy should be straight forward.  I created a new domain just last night, but I don't have my account details where I am now, so I cannot have a look at what I did.

Anyhoo, if you still haven't gotten it working by tonight, send me a private message and I'll send you a screen capture of my GoDaddy configuration.

---

### Post by kevin11951 on 2009-04-21
> **HermanAB said:**
> Everybody is a newbie at some point. No offense meant.

Your MX record doesn't resolve for kviero.com:

$ dig kviero.com MX
...ANSWER 0...

Setting it up in GoDaddy should be straight forward.  I created a new domain just last night, but I don't have my account details where I am now, so I cannot have a look at what I did.

Anyhoo, if you still haven't gotten it working by tonight, send me a private message and I'll send you a screen capture of my GoDaddy configuration.

the problem is i have no idea what to put in the mx records... i know my ip, and thats it.

---

### Post by wsonar on 2009-04-21
I use easydns
Created two a records one for my domain name and one for my mailserver name both pointing to the same ip
then they had a section labled I want to specify my own mail server where I put my mail server name which is essentially my MX record

I also had to call my ISP and have them create a ptr record to my domain otherwise places like live.com would reject me

---

### Post by kevin11951 on 2009-04-21
a screen shot of my dns records (all sensitive data removed):

---

### Post by Spikerok on 2009-04-22
thats cnames you have their my friend..
	
Type       Name               Data
MX	domain.com.	mail.domain.com.

basicly change mail to type MX

---

### Post by kevin11951 on 2009-10-11
> **wsonar said:**
> I use easydns
Created two a records one for my domain name and one for my mailserver name both pointing to the same ip
then they had a section labled I want to specify my own mail server where I put my mail server name which is essentially my MX record

**I also had to call my ISP and have them create a ptr record to my domain otherwise places like live.com would reject me**

your isp? or your domain registrar?

---

### Post by rnodal on 2009-10-13
Dr Small is right. Your connection to gmail is timing out.
That has nothing to do with DNS. Your email server is trying to deliver email via port 25 and if gmail does not accept email via that port (which would be weird) then you are wasting your time. The only consequences of not having the DNS MX record setup correctly is that google will not(may not) accept your email.

If you telnet google to port 25 and it does not work then there is your answer. 

-r

---

### Post by rnodal on 2009-10-13
> **kevin11951 said:**
> your isp? or your domain registrar?

Where is your server? At home or is it a virtual(or real) dedicated server?
If it is a server at home then your ISP may be the reason for all this problems. Most ISP block outgoing email from their network and that will explain why your connection to gmail is timing out. 

-r

---

