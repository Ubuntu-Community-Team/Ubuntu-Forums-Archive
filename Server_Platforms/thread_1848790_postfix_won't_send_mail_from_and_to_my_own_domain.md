---
title: "postfix won't send mail from and to my own domain?"
date: 2011-09-23
forum: Server Platforms
---

### Post by kazimir82 on 2011-09-23
Running Ubuntu 11.04 with Postfix 2.8.2. For some reason, it won't send emails from [email]anything@mydomain.com[/email] to [email]whatever@mydomain.com[/email] :(

By "won't send emails" I mean using PHP's mail function, which actually returns true (indicating success) regardless whether the mail is actually sent or not.

Note: it DOES send from [email]anything@mydomain.com[/email] to [email]whatever@anyotherdomain.com[/email], as well as from [email]anything@anyotherdomain.com[/email] to [email]whatever@mydomain.com[/email]. Just not from and to @mydomain.com combined.

After looking in mail.log (mail.err is empty by the way) I've got a feeling there's something fishy going on. Here's the deal:

[list][*]my webserver is for [www.mydomain.com](www.mydomain.com) (it just hosts the website), whereas mydomain.com (without www**.) resolves to a different IP.[*][www.mydomain.com](www.mydomain.com) only has a DNS A record set to this server's IP.[*]mydomain.com has an MX record set to 'mydomain.com', and an A record to the other server's IP.[*]mail forwarding is configured at the other server, that works all fine (anyone can email me at [email]anything@mydomain.com[/email] which just forwards to hotmail).[/list]
When trying to send a mail from [email]kazimir@mydomain.com[/email] to [email]test@mydomain.com[/email], here's what appears in mail.log:

> Sep 23 10:17:30 vps179 postfix/pickup[1690]: BC48BE1A37: uid=33 from=<kazimir@mydomain.com>
Sep 23 10:17:30 vps179 postfix/cleanup[4793]: BC48BE1A37: message-id=<20110923101730.BC48BE1A37@vps179.myhostingprovider.com>
Sep 23 10:17:30 vps179 postfix/qmgr[1691]: BC48BE1A37: from=<kazimir@mydomain.com>, size=338, nrcpt=1 (queue active)
Sep 23 10:17:31 vps179 postfix/smtp[4795]: BC48BE1A37: to=<test@mydomain.com>, relay=mydomain.com[xx.xx.xx.xx]:25, delay=0.84, delays=0.28/0.02/0.13/0.41, dsn=5.0.0, status=bounced (host mydomain.com[xx.xx.xx.xx] said: 550-Verification failed for <kazimir@mydomain.com> 550-invalid address 550 Sender verify failed (in reply to RCPT TO command))
Sep 23 10:17:31 vps179 postfix/cleanup[4793]: 983EFE1A35: message-id=<20110923101731.983EFE1A35@vps179.myhostingprovider.com>
Sep 23 10:17:31 vps179 postfix/bounce[4796]: BC48BE1A37: sender non-delivery notification: 983EFE1A35
Sep 23 10:17:31 vps179 postfix/qmgr[1691]: 983EFE1A35: from=<>, size=2322, nrcpt=1 (queue active)
Sep 23 10:17:32 vps179 postfix/qmgr[1691]: BC48BE1A37: removed
Sep 23 10:17:32 vps179 postfix/smtp[4795]: 983EFE1A35: to=<kazimir@mydomain.com>, relay=mydomain.com[xx.xx.xx.xx]:25, delay=0.59, delays=0.38/0/0.12/0.09, dsn=5.0.0, status=bounced (host mydomain.com[xx.xx.xx.xx] said: 550 invalid address (in reply to RCPT TO command))
Sep 23 10:17:32 vps179 postfix/qmgr[1691]: 983EFE1A35: removed
(xx.xx.xx.xx is the other server's IP)

Again: when using [email]anything@anotherdomain.com[/email] (even non-existing ones) as from address, it works fine. And when sending to [email]anything@anotherdomain.com[/email], it also works fine.

Did I misconfigure something??

---

### Post by kazimir82 on 2011-09-23
Oh, perhaps it's useful to post my /etc/postfix/main.cf:

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

myhostname = vps179.myhostingprovider.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4

---

### Post by kazimir82 on 2011-09-24
Addition: I don't know if postfix is only for sending, or also possibly receiving mail, but is it somehow possible that postfix thinks the mail is directed at someone at that same machine, and therefore doesn't actually send out anything?

---

### Post by Ryan Dwyer on 2011-09-24
The error in your mail.log indicates that it rejected the mail because [email]kazimir@mydomain.com[/email] (the From address) doesn't exist.

When some mailservers are receiving a message, they'll connect to the sending domain's mailserver and verify that the From address exists before accepting the message. In this case it looks like that check is failing.

Alternatively, there's probably some way to whitelist your webserver's IP in Postfix so it always accepts email from that IP.

---

### Post by kazimir82 on 2011-09-24
> **Ryan Dwyer said:**
> The error in your mail.log indicates that it rejected the mail because [email]kazimir@mydomain.com[/email] (the From address) doesn't exist.

When some mailservers are receiving a message, they'll connect to the sending domain's mailserver and verify that the From address exists before accepting the message. In this case it looks like that check is failing.
Hmm OK I see, but the strange thing is, it *does* work when I send a mail from [email]kazimir@mydomain.com[/email] to [email]anyone@anyotherdomain.com[/email].

And it even works fine if I send a mail from [email]randomname@randomnonexistentdomain.com[/email] to no matter what address (either @mydomain.com or @anotherdomain.com).

It *only* fails if BOTH the from AND to address are @mydomain.com. If either one (or both) is @anotherdomain.com it sends just fine... I'm completely clueless!

> Alternatively, there's probably some way to whitelist your webserver's IP in Postfix so it always accepts email from that IP.
Would love to try, any idea how/where to set this?

---

### Post by Ryan Dwyer on 2011-09-24
> **kazimir82 said:**
> Hmm OK I see, but the strange thing is, it *does* work when I send a mail from [email]kazimir@mydomain.com[/email] to [email]anyone@anyotherdomain.com[/email].

That's because the anyotherdomain.com mailserver isn't doing this check. There would be some domains where this fails.

> **kazimir82 said:**
> And it even works fine if I send a mail from [email]randomname@randomnonexistentdomain.com[/email] to no matter what address (either @mydomain.com or @anotherdomain.com).

I believe this is more often going to fail than work. You have no authority to send from any other domain than your own, and any recipient mailservers that do any of the most basic checks will notice this. They might accept the mail but it could be going into spam.

> **kazimir82 said:**
> Would love to try, any idea how/where to set this?

The real problem is that you're sending email from an address that doesn't exist. Even if you whitelisted your webserver, other mailservers may reject the message depending on what checks they do. If you whitelist it, you should make sure any addresses it sends from are also able to accept mail.

[http://www.google.com.au/search?q=postfix+whitelist+ip](http://www.google.com.au/search?q=postfix+whitelist+ip)

Any of the top results on that page look like they'll work, except the official Postfix documentation. After 3 minutes of looking at the Postfix docs I still can't find anything similar to the other Google results which mentions how to whitelist anything.

---

### Post by kazimir82 on 2011-09-27
> **Ryan Dwyer said:**
> I believe this is more often going to fail than work. You have no authority to send from any other domain than your own, and any recipient mailservers that do any of the most basic checks will notice this. They might accept the mail but it could be going into spam.
OK, but isn't it strange that when sending mail to @mydomain.com, it works when sending from a non-existent domain, but it doesn't when sending from @mydomain.com? Even though the server I'm sending to actually is supposed to deal with those addresses itself!? (so it "knows" the address does exist!)

> The real problem is that you're sending email from an address that doesn't exist.
But it does! I can send email from [email]kazimir@mydomain.com[/email] to anyone, and receive from anyone to [email]kazimir@mydomain.com[/email] (or [email]anything@mydomain.com[/email] for that matter) just fine. It works, it's valid, the address exists! It just doesn't work if from and to are BOTH @mydomain.com - now that just seems plain wrong to me?! And actually I wouldn't know what to whitelist where (since it already accepts mail from OR to such addresses without problems, just not at the same time).

Much appreciated, if you or anyone else has any further toughts about this, please let me know cause it's driving me nuts!

---

### Post by Ryan Dwyer on 2011-09-27
Well according to your logs, your server believes [email]kazimir@mydomain.com[/email] doesn't exist.

I'm thinking maybe your server is unable to resolve its own MX record properly.

Try the following on the mailserver:
dig mydomain.com mx +short

Then for each name returned, try telnetting to it on port 25:
telnet <name> 25

I'm thinking the MX records might be returning a hostname (your own) which your mailserver is incorrectly resolving to its own external IP. If this is the case then when it tries to connect it won't work. It then assumes that the address doesn't exist because it can't connect to any mailserver for that domain.

---

### Post by kazimir82 on 2011-09-29
Ah, interesting! 

dig mydomain.com mx +short gives:
> 0 mydomain.com.

Telnet mydomain.com 25 seems to connect to the SMTP server:
> vps179.myhostingprovider.com ESMTP Exim 4.69 etc...

Then, when I try to send a mail through telnet manually, similar to what fails when I do it through postfix from my main server, it works:
> helo mydomain.com
mail from: [email]kazimir@mydomain.com[/email]
rcpt to: [email]test@mydomain.com[/email]
data
subject: anybody home?
to: [email]test@mydomain.com[/email]
from: [email]kazimir@mydomain.com[/email]

hello
.
quit
And this test message is sent correctly!

> **Ryan Dwyer said:**
> I'm thinking the MX records might be returning a hostname (your own)
Indeed it does (see dig result above),
> which your mailserver is incorrectly resolving to its own external IP.
Well yes, it resolves to the external IP of the mail server (tried with ping and nslookup) but isn't that correct? (what else should it be?)

> If this is the case then when it tries to connect it won't work. It then assumes that the address doesn't exist because it can't connect to any mailserver for that domain.
I also tried telnetting to the external IP instead of mydomain.com, from the mailserver as well as from my own location (home), both OK.

So when I send a mail to and from my domain manually (using telnet), it works, but apparently when postfix does this, it doesn't..?

Thanks a lot again, I feel I'm getting close here, would you have any further thoughts on this?

---

### Post by Ryan Dwyer on 2011-09-30
I assume vps179.myhostingprovider.com is not your Postfix server. Shouldn't your MX record resolve to your Postfix server?

I'm taking a stab in the dark here, but try adding 127.0.0.1 mydomain.com to your /etc/hosts file and see what happens. If that doesn't work, PM me your domain name and your external IP and I'll see if I can figure it out.

---

