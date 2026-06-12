---
title: "[SOLVED] Can't receive mail on Dovecot / Postfix server"
date: 2008-12-17
forum: Server Platforms
---

### Post by Drate on 2008-12-17
DNS:
A Record
myserver.mydomain.com points to my.public.ip.address

MX Record
priority=0
mydomain.com points to myserver.mydomain.com

postconf -n:
---------------
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 51200000
mydestination = myserver.mydomain.com myserver.com localhost.mydomain.com localhost
myhostname = myserver.mydomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 172.16.100.0/24 my.public.ip.network/24
myorigin = mydomain.com
proxy_interfaces = my.public.ip.address
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
---------------------
I can telnet into myserver.mydomain.com on ports 110, 587, and when not blocked by an isp 25.

After playing I find I can recieve messages from other people on the mydomain.com domain.  That is: a message from [email]someone@mydomain.com[/email] can be received by I still am not receiving from [email]someone@gmail.com[/email] .

Please help, I have been fighting with configurations and documentation for some time now, I would really appreciate the help.

---

### Post by MJN on 2008-12-17
Tell us your domain name or you're on your own.

Why hide it, particularly given that the DNS configuration and remote access to it is critical to pinpointing the likely problem?

Mathew

---

### Post by Drate on 2008-12-18
My domain is irrelevant to the syntactic veracity of a configuration file.

Is there is a test I should perform to confirm the DNS configuration or remote accessibility?

Yall would be saving several years from draining off my life from stress here.

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> 
proxy_interfaces = my.public.ip.address
--- cut ---
After playing I find I can recieve messages from other people on the mydomain.com domain.  That is: a message from [email]someone@mydomain.com[/email] can be received by I still am not receiving from [email]someone@gmail.com[/email] .

So you're saying that you can receive emails only locally and not from the outside, right ?

Why do you use the proxy_interfaces option ?
I've never used that. Please test without it.

Did you follow a specific howto for this or not ?
If you did, can you point us to that ?

---

### Post by albinootje on 2008-12-18
One more thing, you have mynetworks defined, but according to your posted postconf -n output you're not using it.

Here's a relevant part of my postconf -n and some more :

smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks,    reject_non_fqdn_hostname
smtpd_recipient_restrictions = permit_mynetworks,    permit_sasl_authenticated,    reject_unauth_destination,    reject_invalid_hostname,    reject_unauth_pipelining,    reject_non_fqdn_sender,    reject_unknown_sender_domain,    reject_non_fqdn_recipient,    reject_unknown_recipient_domain,    reject_rbl_client zen.spamhaus.org,    permit

---

### Post by MJN on 2008-12-18
> **Drate said:**
> My domain is irrelevant to the syntactic veracity of a configuration file.Given that it is your setup that is not working you are not really in the best position to say what is and isn't relevent.
 
The domain is completely relevent for a number of reasons:
 
- Errors can creep in (or out) when munging the configuration. I have lost count of the number of times the true cause of a problem has been hidden due to mistakes transferring the configuration to the post.
 
- Without the domain name we are unable to test remotely that the DNS is configured correctly and working. We are also unable to connect to your mail server as a 3rd party and attempt delivery.
 
Basically, without your domain name we are unable to reproduce the error that you are saying others are observing. It may prove to be of little, or no, benefit but it helps rule out potential issues which in turn helps us move towards pinpointing the cause of the problem.
 
Mathew

---

### Post by albinootje on 2008-12-18
The OP wrote :
"I can telnet into myserver.mydomain.com on ports 110, 587, and when not blocked by an isp 25."
So DNS for myserver.mydomain.com is working.

Whether the MX-record is set properly can be done by looking at the results of : host -t mx mydomain.com

Imho there's no need to try to force the OP to publish the real domainname.

---

### Post by MJN on 2008-12-18
> **albinootje said:**
> Imho there's no need to try to force the OP to publish the real domainname.I'm not trying to force him. But it is a condition of me providing help (for the reasons stated) and is therefore completely their choice.
 
I don't think that's too unreasonable.
 
The OP can PM the domain if they don't want it publically posting.
 
Mathew

---

### Post by albinootje on 2008-12-18
> **MJN said:**
> I'm not trying to force him. But it is a condition of me providing help (for the reasons stated) and is therefore completely their choice.
 
I don't think that's too unreasonable.
 


Okay, agreed.
Let's see whether the OP answers some questions first.
:)

---

### Post by Drate on 2008-12-18
Firstly, I appreciate both yall's help, I really do.

The original howto I followed was here:

[https://help.ubuntu.com/8.10/serverguide/C/email-services.html]("https://help.ubuntu.com/8.10/serverguide/C/email-services.html")

After that various docs I have found on Postfix I have been using and had made some headway.  Originally I could receive nothing, the receiving from the local domain was an improvement.

The proxy_interfaces was used as I am behind a firewall using NAT to translate my public ip to private, what I read about the proxy_interfaces option was to include it for such a configuration.

Shall I remove the mynetworks or shall I ammend it similar to what you posted?

I shall post the results of the host -t mx mydomain.com as soon as I am able.

And as to the reason for not giving the domain identity (as yet), it is because this is something I am doing for my employer and I do not feel it would be appropriate for me to post that I have a misconfigured server and give people my domain information.  Especially after getting an e-mail this morning from another domain mail server server we manage showing an attempted brute force break-in.

If it becomes absolutely critical to resolve the issue (that is, the tests required can not be performed by myself) I could consider offering the domain to one or two of you privately.

I do have the ability to test from outside networks and e-mail addresses through webmail as well as remote access to other computers and completely separate domains and networks.

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> 
The proxy_interfaces was used as I am behind a firewall using NAT to translate my public ip to private, what I read about the proxy_interfaces option was to include it for such a configuration.

Shall I remove the mynetworks or shall I ammend it similar to what you posted?

A quick reply for the moment. (Later more hopefully).

My mailservers are also using NAT but my firewall handles the port_forwarding to it. I've never used the proxy_interfaces option, but i can imagine that in your situation it is needed.

About the mynetworks, you might need it to properly configure your postfix setup in the future (see my example).
Not using it doesn't do any harm.

GL!

---

### Post by Drate on 2008-12-18
Will attempt the indicated changes before the end of the day and post again.

Test without proxy_interfaces = no change (i.e. don't need it).
Will now try to adjust mynetworks.

It would appear that after plagiarizing your indicated changes regarding the mynetworks stuff, there is no change.

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> Will attempt the indicated changes before the end of the day and post again.

Test without proxy_interfaces = no change (i.e. don't need it).
Will now try to adjust mynetworks.

Ok, I suggest you try sending an email manually to that email-server by using telnet mailserver-domain 25 to check where things go wrong.

Here's an example :
[http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)

S: 220 smtp.example.com ESMTP Postfix
C: HELO relay.example.org
S: 250 Hello relay.example.org, I am glad to meet you
C: MAIL FROM:<bob@example.org>
S: 250 Ok
C: RCPT TO:<alice@example.com>
S: 250 Ok
C: RCPT TO:<theboss@example.com>
S: 250 Ok
C: DATA
S: 354 End data with <CR><LF>.<CR><LF>
C: From: "Bob Example" <bob@example.org>
C: To: Alice Example <alice@example.com>
C: Cc: [email]theboss@example.com[/email]
C: Date: Tue, 15 Jan 2008 16:02:43 -0500
C: Subject: Test message
C:
C: Hello Alice.
C: This is a test message with 5 headers and 4 lines in the body.
C: Your friend,
C: Bob
C: .
S: 250 Ok: queued as 12345
C: QUIT
S: 221 Bye
{The server closes the connection}

(For typing it in, remove the C: part in from of the lines.)
The bold text in this example is the text you would type in.
The normal (non-bold) text is the answer from the smtp-server.

But you can also check the /var/log/syslog or /var/log/mail.log log-files on your mailserver. (Could be /var/log/syslog.0 it depends..)

---

### Post by Drate on 2008-12-18
Ooo... this looks fun, will do.

Ohkay, that was pretty much awesome.

And it worked.  I got the e-mail.

So the problem then is with the initial connection?  Perhaps a dovecot configuration issue?

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> Ooo... this looks fun, will do.

The bold text is in the original link :
[http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)

The ones with C: in front are the example lines you would type in.

---

### Post by Drate on 2008-12-18
Right, I did the test, the test worked.  I wish it hadn't.

BTW, I used port 587, 25 is blocked from the ISP I tested from.

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> Right, I did the test, the test worked.  I wish it hadn't.

BTW, I used port 587, 25 is blocked from the ISP I tested from.

Okay, if that test email didn't arrive in your mailbox, then that means that there's a delivery problem with either postfix or dovecot.

Can you check the /var/log/syslog or /var/log/syslog.0 files to see what happened with the test email ?

---

### Post by Drate on 2008-12-18
AAHHHHHHAHHAHAHAAAAAAAAAAAAAAAAAAAA!

So, the problem?  I explicity put "mydomain.com" in my mx record for godaddy (as indicicated in the original post), instead of putty "@".

Ho insanely messed up is that?  Since when is implicit preferred over explicit?

Well, either way I thank you sir, it has at least been educational.

The only thing left for me to do is figure out why I can' use secure login.  But some of that you posted looked like it might have been related, I'll see about it.  Unless you already know the secrets off hand. :)

---

### Post by MJN on 2008-12-18
> **Drate said:**
> So, the problem?  I explicity put "mydomain.com" in my mx record for godaddy (as indicicated in the original post), instead of putty "@".Now do you see why knowing the domain name was critical (nevermind just relevant) to solving the problem? The DNS misconfiguration would've stuck out like a sore thumb. ;-)

Your reasons for not wishing to divulge the domain make complete sense and would've been helpful from the outset rather than claiming it had no relevance to the issue.

> Ho insanely messed up is that?  Since when is implicit preferred over explicit?If you didn't terminate 'mydomain.com' with a dot then it will have had the origin domain appended to it i.e. mydomain.com.mydomain.com. Putting in @ means 'same as parent' and hence has given you a straight mydomain.com entry.

Mathew

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> AAHHHHHHAHHAHAHAAAAAAAAAAAAAAAAAAAA!

So, the problem?  I explicity put "mydomain.com" in my mx record for godaddy (as indicicated in the original post), instead of putty "@".

Ho insanely messed up is that?  Since when is implicit preferred over explicit?

Well, either way I thank you sir, it has at least been educational.

Cool, glad that that problem is solved.
> 
The only thing left for me to do is figure out why I can' use secure login.  But some of that you posted looked like it might have been related, I'll see about it.  Unless you already know the secrets off hand. :)
Can your clarify this ? You mean usage of SASL or https:// for webmail or SSL for imap-ssl or .. ?

---

### Post by Drate on 2008-12-18
To albinootje: I believe I have the pop3 connection working off of SSL, but SMTP did not respond to request when using the port 465 (Thunderbird indicated that port as default for smtp ssl).

In truth, even knowing for certain which levels of security to use where would be helpful.  Everything you listed, anything you listed.  I just want to make sure I put due diligence to securing this server.  I can maintain the firewall adequately well, I just need to know what other exploits to avoid.

To MJN:
I appreciate the need for information to properly diagnose the problem, and I apologized if I sounded testy in my initial response, but again, the problem was syntactic.  I offered the syntax of my MX record in the first post.  Using the term "mydomain.com" is no different than saying "gmail.com" "ubuntuforums.com" or "wxyz.com"

So you are saying if I want to be explicit in my MX record I should put "mydomain.com." ?  I'll DEFINITELY be remembering that!  :)

---

### Post by Drate on 2008-12-18
I think it's time I mark this thread as solved and start a new one regarding appropriate security measures.

---

### Post by albinootje on 2008-12-18
> **Drate said:**
> To albinootje: I believe I have the pop3 connection working off of SSL,
If you have dovecot running properly and you've enabled pop3-ssl and imap4-ssl, (See the line with "protocols =" in /etc/dovecot/dovecot.conf
then that makes sense :)

> but SMTP did not respond to request when using the port 465 (Thunderbird indicated that port as default for smtp ssl).

Quite some time ago i've read that port 465 was an unofficial Netscape related port for authenticated smtp.
Google's Gmail uses 578, so.. i'm not sure what is the official port for this.

Following the howto that you've used, configuring SASL is mentioned here : [https://help.ubuntu.com/8.10/serverguide/C/postfix.html#postfix-sasl](https://help.ubuntu.com/8.10/serverguide/C/postfix.html#postfix-sasl)

You can test the SASL availability with the "ehlo" command (see in the above mentioned link).

It should be a matter of using port_forwarding with your firewall software, and then manually give in the (465 or 578) port in the smtp-settings in thunderbird.

---

### Post by MJN on 2008-12-18
> **Drate said:**
> I offered the syntax of my MX record in the first post. No you didn't. You said:

> MX Record
priority=0
mydomain.com points to myserver.mydomain.comYou missed off the very relevent fact you had $ORIGIN set to mydomain.com. Of course, you didn't realise you had - and that's why you assumed you'd given us all we needed to know.

> Using the term "mydomain.com" is no different than saying "gmail.com" "ubuntuforums.com" or "wxyz.com"It is completely different. We can check the DNS configuration for the other domains. We can't for mydomain.com and hence we had to assume your interpretation of the config was correct (which we now wasn't the case! ;-)).

> So you are saying if I want to be explicit in my MX record I should put "mydomain.com." ? Only if you have $ORIGIN set to your domain. GoDaddy obviously do - perfectly valid and correct but it can catch the unwary out.

> I'll DEFINITELY be remembering that!  :)Good! :p

Mathew

---

### Post by MJN on 2008-12-18
> **albinootje said:**
> Quite some time ago i've read that port 465 was an unofficial Netscape related port for authenticated smtp.
Google's Gmail uses 578, so.. i'm not sure what is the official port for this.Mail related ports are rather all over the place as the demand for encrypted sessions and anti-spam techniques collided somewhat resulting in some parallel developments.

In the general sense the port options are as follows:

25 - SMTP port - Used by both clients and mail servers to submit and relay mail for delivery. TLS is optional and can be started by the sender once connected using STARTTLS. A true 'multi-purpose' port if ever there was one.
465 - SMTPS port - As above but with a TLS tunnel established before the SMTP stage. Some mail clients default to offering to use this when told to encrypt sessions but its use is not all that common - indeed was never registered with IANA to be used for this (no port was, probably partly because TLS was available post-connection on port 25).
587 - Submission port (RFC2476) - Used only by clients to submit mail for delivery. Given it is not used for inter-server delivery it does not have to be as locked down as port 25 given that access to this port is ('should') always be authenticated.

All very confusing I agree, but suffice to say that port 25 (to accept mail from external servers) and 587 (to allow your clients to connect wherever they are) are all that you really need to concentrate on for the majority of installations.

Mathew

---

