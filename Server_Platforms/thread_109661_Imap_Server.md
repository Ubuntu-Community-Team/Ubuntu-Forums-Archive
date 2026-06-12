---
title: "Imap Server"
date: 2005-12-29
forum: Server Platforms
---

### Post by Rhyselsworth on 2005-12-29
Hi,
I hope this isn't a repeated question but heres what I'm trying to do.

Set up an internal IMAP mail server for clients on my network to access thier e-mail, via Outlook or whatever client they wish. The mail server will retrieve e-mails from POP3 mailboxes provided by our ISP and farm them out to each users mailbox so that they can retrieve them as above. I would like clients to be able to send to the server too, as I understand it, this would mean that; Clients send mail to the internal mail server, this then re-lays it onto our ISP's sending mail server to actually be sent. I guess this is basically what MS Exchange does. 

I have looked at these two guides that use postfix and courier, among other things: 
[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")
[http://genco.gen.tc/postfix_virtual.php]("http://genco.gen.tc/postfix_virtual.php")

Am I on the right track? Is what I want to do possible with postfix? Or is there a much simpler option?

Thanks,
Rhys

---

### Post by heimo on 2005-12-29
I'd ask that is it neccessary that your ISP relays those mails? In this scenario you could setup some program to fetch mail from pop accounts periodically, but I only see that this adds complexity. I'm using the setup described in the first link and it seems _very_ flexible (I followed those exact instructions with minor tweaks). 

So... My question is, could you just accept mail directly to that server? (I understand that there may be reason why it's not possible.) Then it could also act as a sending / relaying mail server / MTA (SMTP)*. All you would need to do is configure it to accept mail for your clients domain and make change to DNS (MX records to point to your server). You'd probably also want secondary MX (backup MX) server, but I still see this as a simpler and more reliable configuration.

If you still need the pop accounts on ISP server, you could use something like fetchmail - but I do not know if that particular program is suitable for the task. It probably is, but I haven't used it with multiple accounts and there may be better tool for this. You need to make sure that the tools you use (for fetching the mail and delivering it locally and to imap clients) support the same mail box formats (there are at least two different ways for this).


:) Good luck.

EDIT. *) You always want to make sure that you do NOT setup open relays - SMTP that accepts mail from outside to any domain (spammers love these).

---

### Post by Rhyselsworth on 2005-12-29
Thanks for the reply :)

Unfortunatley I don't think I can accept incoming mail directly to the server, since its not directly attached to the internet. It is behind a router/gateway which is assigned a dynamic IP by our ISP. Ideally your solution sounds great though. I am also looking into Fetchmail.

In the meantime I followed the same guide as you (First link); internal aliases appear to be working. That is, i can drop in a message via telnet to an address that the system recognises and that gets put into the correct maildir. I'm now working on what happens if an e-mail is recieved that is to be forwarded to a non-local address, as per the aliases table. Eg: I want root@localhost to forward to my external address. I'm getting this error in the logs though:

Dec 29 13:30:49 localhost postfix/smtp[16600]: 39E5E12C2B5: to=<my@externaladdress.co.uk>, orig_to=<root@localhost>, relay=none, delay=1241, status=deferred (Host or domain name not found. Name service error for name=mail.btclick.com type=MX: Host not found, try again)

Just checking the sending server name (mail.btclick.com) is correct. Any Ideas?

---

### Post by heimo on 2005-12-29
[quote=Rhyselsworth]
Unfortunatley I don't think I can accept incoming mail directly to the server, since its not directly attached to the internet. It is behind a router/gateway which is assigned a dynamic IP by our ISP. 
[/quote] 
Depending on the requirements of service level... It might still be possible, but I can't recommend it. I have personal experience of running mail server using dynamic public ip address (no backup MX) and it works better than expected. Yes, it sounds like something you shouldn't admit on a public forum like this. :rolleyes:

The fact that it's behind NAT (I assume your gateway is also NAS) and your server has private IP (for example 10.0.0.1 or 192.168.0.1) isn't probably problem either. You could port forward 25 from the router to your server. Those "dynamic" ip addresses are most of the time actually quite stable, even months, and you could setup some kind of automatic DNS update and have low DNS TTL (time-to-live) values. I don't even have automatic updates, I just notice when the IP has changed (because couple [hobby] web sites go down and I can's ssh into the server anymore...) and do the update to DNS manually. If uptime is of any importance, you could probably get that fixed ip address from your ISP and do it professionally. The reason I do this is that I don't want to pay any extra money (but still prefer to host my own emails).

But I perfectly understand that this may not be acceptable solution in your case.

[quote=Rhyselsworth]
Dec 29 13:30:49 localhost postfix/smtp[16600]: 39E5E12C2B5: to=<my@externaladdress.co.uk>, orig_to=<root@localhost>, relay=none, delay=1241, status=deferred (Host or domain name not found. Name service error for name=mail.btclick.com type=MX: Host not found, try again)

Just checking the sending server name (mail.btclick.com) is correct. Any Ideas?[/quote] 
I'm pretty sure I've seen this exact same error, but can't remember how to solve it. Is dns working properly on that server? You can "dig servername" solve the name to ip address? And can you telnet from that server into the 25 port of the mx (mail.btclick.com), type "helo example.com" and get a nice reply "Hello [your hostname] pleased to meet you"?

```

telnet [servername/ip] 25
helo [your domain name]
```

---

### Post by Rhyselsworth on 2005-12-29
Following your advice, yes I can telnet directly into my ISP's smtp server and get a nice hello message. After trawling through the documentation on the postfix website, I did this in my /etc/postfix/main.cf 
relayhost = [mail.btclick.com]
The addition of square brackets makes it blindly send to the server I think :-s - Although I don't really understand what it is doing. In any case it now works.

I think I'll try and get fetchmail to deliver straight to my system, however its good to hear that it is possible to use a dynamic IP. This would be even more useful for ssh admin :-)

Continuing to set up spam filter, antivirus checking and the like, thanks for all your help. :-)
Rhys

---

### Post by LordHunter317 on 2005-12-29
[QUOTE=heimo]I'd ask that is it neccessary that your ISP relays those mails?[/quote]Yes, likely.  It's almost always necessary unless you have a static IP on a non-residential block, proper DNS, etc.  Even then, it may be a good idea unless your outgoing mailvolume is large.


>  In this scenario you could setup some program to fetch mail from pop accounts periodically, but I only see that this adds complexity.Not especially. You run getmail or fetchmail on the internal SMTP/IMAP server, and it delivers to the local mailboxes.  Not a big deal.  I do it to pull all my mail accounts to one mailbox.

> You'd probably also want secondary MX (backup MX) server, but I still see this as a simpler and more reliable configuration.I'm not sure about more reliable.

> You need to make sure that the tools you use (for fetching the mail and delivering it locally and to imap clients) support the same mail box formats (there are at least two different ways for this).The mail fetch program doesn't care, as it delivers it to the local MTA for delivery.

> The fact that it's behind NAT (I assume your gateway is also NAS) and your server has private IP (for example 10.0.0.1 or 192.168.0.1) isn't probably problem either.It makes the DNS all the more complicated.

As for the OP, post your main.cf as you shouldn't have to do that.

---

### Post by Rhyselsworth on 2005-12-30
[QUOTE=LordHunter317]
As for the OP, post your main.cf as you shouldn't have to do that.
[/QUOTE]

I assume by OP you mean 'Other Problem'; It seems to all be working fine now using my ISP to relay mail. But if it interests you ill post my main.cf anyhow. I've taken most of this straight from: [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

Here goes:

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450

myhostname = dayworthMain.dwpak
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
local_recipient_maps =
mydestination =
relayhost = [mail.btclick.com]
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

masquerade_domains = mydomain.co.uk
masquerade_exceptions = root

# How long a message is left on the queue before it fails
maximal_queue_lifetime = 3d

# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s

# Maximium number of addressees per message
smtpd_recipient_limit = 30

# how many error before back off
smtpd_soft_error_limit = 3

# how many max errors before blocking it
smtpd_hard_error_limit = 20


## Security Restrictions (Should all be on one line only

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, eject_invalid_hostname, permit

# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

# Requirement for the recipient address 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

# require proper helo at connections 
smtpd_helo_required = yes

# waste spammers time before rejecting them 
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two 
# but they are needed for local aliasing 
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual

# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf

# and their user id 
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

# and group id 
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf

# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf

# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

# To Link in content filter
#receieve_override_options = no_address_mappings
content_filter = amavis:[127.0.0.1]:10024

# For Sasl Authentication
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# For TLS Encryption and certificates
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining

---

### Post by LordHunter317 on 2005-12-30
> **Rhyselsworth]I assume by OP you mean 'Other Problem' said:**
> No, I meant original poster.

> myhostname = dayworthMain.dwpakI hope the box actually thinks this is it's hostname, and has a valid entry for that in DNS or /etc/hosts

Having nothing for local delivery bothers me quite heavily as well, but assuming your virtual setup is correct, it's not an issue.

---

### Post by Rhyselsworth on 2006-01-01
Sorry its taken me so long to reply, Ive been away from the computer for a while.

When I run 'hostname' i get: 'dayworthMain', and when I run 'dnsdomainname' I get: 'localdomain'. My /etc/hosts file looks like this:

127.0.0.1 localhost.localdomain localhost dayworthMain
192.168.1.100 dayworthMain

Is this setup ok?

---

