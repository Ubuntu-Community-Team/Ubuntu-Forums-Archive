---
title: "can only send mail to locahost via postfix"
date: 2008-03-30
forum: Server Platforms
---

### Post by android6011 on 2008-03-30
I installed ubuntu server edition and followed [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) and I can connect and check my email using thunderbird, but if i try to send email, I get an error about relay access denied. I can send email to anyone @localhost but if it is any other domain I get that error.

---

### Post by Metro_Dan on 2008-03-31
did you enable server requires authentication in thunderbird?

---

### Post by android6011 on 2008-03-31
yes. i dont think its thunderbird, i think its a configuration problem with postfix but im not sure

---

### Post by Metro_Dan on 2008-03-31
> **android6011 said:**
> yes. i dont think its thunderbird, i think its a configuration problem with postfix but im not sure

I am by no means a expert, but that how-to didn't do much for me (it didn't work). I used this one [here]("http://howtoforge.com/perfect_server_ubuntu7.10_p5") on two boxes and it worked perfect.

Also make sure your ports are open (25) and not being filtered by you isp

---

### Post by android6011 on 2008-03-31
> **Metro_Dan said:**
> I am by no means a expert, but that how-to didn't do much for me (it didn't work). I used this one [here]("http://howtoforge.com/perfect_server_ubuntu7.10_p5") on two boxes and it worked perfect.

i had a similar problem when i tried that last time but i couldnt figure out if it was postfix or some other authentication causing the problem, but it must be postfix since its a fresh install

---

### Post by Metro_Dan on 2008-03-31
> **android6011 said:**
> i had a similar problem when i tried that last time but i couldnt figure out if it was postfix or some other authentication causing the problem, but it must be postfix since its a fresh install

Can you send mail out from root@localhost via the command line?

Just curious

---

### Post by android6011 on 2008-03-31
I just did everything in the perfect server setup tutorial part 5, so what ports do i need to use to connect to check mail and which ports to send mail? thanks

---

### Post by Metro_Dan on 2008-03-31
> **android6011 said:**
> I just did everything in the perfect server setup tutorial part 5, so what ports do i need to use to connect to check mail and which ports to send mail? thanks
Ports:
25 for smtp outgoing
110 for pop to check mail 
143 for IMAP

---

### Post by android6011 on 2008-03-31
> **Metro_Dan said:**
> Ports:
25 for smtp outgoing
110 for pop to check mail 
143 for IMAP

i thought one of them had to be 995 because of SSL authentication.

---

### Post by Metro_Dan on 2008-03-31
> **android6011 said:**
> i thought one of them had to be 995 because of SSL authentication.

yeah and port 995 fot ssl pop. Forgot about that one as I don't use SSL

---

### Post by android6011 on 2008-03-31
> **Metro_Dan said:**
> yeah and port 995 fot ssl pop. Forgot about that one as I don't use SSL

after doing that other tutorial, i can check my email on 110 or 995 now, but now instead of getting relay access error when sending on 25 with no authentication, i just get that the server is refusing connections

---

### Post by Metro_Dan on 2008-03-31
> **android6011 said:**
> after doing that other tutorial, i can check my email on 110 or 995 now, but now instead of getting relay access error when sending on 25 with no authentication, i just get that the server is refusing connections

yeah if you don't auth it wont allow it

---

### Post by android6011 on 2008-03-31
> **Metro_Dan said:**
> yeah if you don't auth it wont allow it

Im still trying to authenticate with a username, just not TLS or SSL

---

### Post by Mr. C. on 2008-04-01
Show your mail log messages
Show output of **postconf -n** .

---

### Post by android6011 on 2008-04-05
administrator@remove:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination =remove.com,remove, localhost.localdomain, localhost
myhostname = remove
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

---

### Post by hyperlobic on 2008-04-08
By default, postfix will not allow mail relaying.  That's a good thing so that spammers can't hijack you mail server as an open relay.  You basically have two options:  You can allow mail relaying from the network you are on, or you can enable authentication via SASL.

The former is only a good idea if your server and client are on the same network and the network is protected form outside users.

There are a couple of primers on using postfix with SASL.

check here:

[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)

Let me know of you still have problems and I can probably help you out.  You will need SASL installed on your system and th saslauthd daemon needs to be running.  Please note I am not a Ubuntu expert, but I've been admining Postfix on Sun servers for a long time.

You are going to have some additions to you main.cf file (probably in /etc/postfix)

you'll need something like this:

smtp_sasl_auth_enable = no
smtp_sasl_password_maps = dbm:/etc/postfix/saslpass
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetowrks, reject_unauth_destination
smtpd_sasl_auth_enable = yes

as well as telling postfix to accept SASL authenticated connections

smtpd_recipient_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_unauth_destination,


Hope that helps

---

### Post by Rizla on 2008-06-24
Not sure if anyone still monitors this, but i'm in the same boat, except i'm also trying to do this with virtual domains.

I've setup the outgoing smtp server in thunderbird and it connects using tls, shows me the certificate, etc.  But promtps for my login crednetials.  i enter the password that is used for the same account to get my emails, but it keeps rejecting it..  Is SMTP authentication different when you're trying to connect to the mail server to send mail through it?

---

### Post by Mr. C. on 2008-06-24
Start by showing the relevant log entries for the transaction, and postconf -n.  There is simply no way to debug otherwise.

---

### Post by Rizla on 2008-06-24
Here are the last two entries from my syslog:

```

Jun 24 17:57:52 host1 postfix/smtpd[5887]: warning: pool-96-237-5-34.bstnma.east.verizon.net[96.237.5.13]: SASL LOGIN authentication failed: authentication failure

Jun 24 17:58:00 host1 postfix/smtpd[5887]: warning: pool-96-237-5-34.bstnma.east.verizon.net[96.237.5.13]: SASL LOGIN authentication failed: authentication failure

```

Here's whats in my main.cf.. i know its messy because I was mashing a few tutorials together..

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = mezammi.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
readme_directory = no

#Requirements for the HELO Statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hos$
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_s$
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mezammi.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reje$
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

#Virtual Domain OCnfig
virtual_alias_domains =
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/et$
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
vicrtual_transport = virtual
transport_maps = mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql-virtual_mailbox_limit_map$
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota$
virtual_overquota_bounce = yes
content_filter = amavis:[127.0.0.1]:10024
virtual_overquota_bounce = yes
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

---

### Post by Mr. C. on 2008-06-24
**postconf -n** output, not main.cf

increase logging for smtpd, in master.cf, for smtpd (add a -v at the end of the line that looks like:
```
smtp      inet  n       -       n       -       -       smtpd
```
make it look like:
```
smtp      inet  n       -       n       -       -       smtpd -v
```

Restart postfix and capture all relevant messages for a mail *transaction* (not just single line that says failure).

Download and run saslfinger:

[http://postfix.state-of-mind.de/patrick.koetter/saslfinger/](http://postfix.state-of-mind.de/patrick.koetter/saslfinger/)

show output.

---

### Post by Rizla on 2008-06-27
Sorry for the late reply, but I apprecaite your help.  here's just the relavent snippet from my syslog with verbose logging enabled.  Im curious to know why its using PLAIN


[/code]
Jun 27 14:22:13 host1 imapd-ssl: LOGIN FAILED, method=PLAIN, ip=[::ffff:96.237.5.13]
Jun 27 14:22:18 host1 imapd-ssl: LOGIN FAILED, user=myusername, ip=[::ffff:96.237.5.13]
Jun 27 14:22:42 host1 imapd-ssl: LOGIN FAILED, method=PLAIN, ip=[::ffff:96.237.5.13]
[/code]

**EDIT:**
CRAP i just realized that this response adn the code i posted was based on an issue I just started having as of yesterday.  I cant log in now, let alone use it as my SMTP outgoing server.  Not sure what changed.  the 'myusername' is an actual sys account on the server not a virtual user/email.  But i'm using authmysql as my authentication, shoudld I also include PAM in my smtpd.conf file?

**/EDIT:**

Another question, along the same lines.  WHen i check my mail with thunderbird.  I get prompted to examine my certificate everytime because it was generated by "localhost" rather than the DNS name of my server.  How do i go about regenerating the cert so that it has my DNS name.

Also, i have virtual domains hosted on there as well with seperate email accounts, so I'm wondering if the same can be done for the other names as far as the certificate is concerned..  No biggie, but its a bit of a nuisance.

---

### Post by Rizla on 2008-06-27
Not sure if this helps, but here's my sasl smtpd.conf file

**/etc/postfix/sasl/smtpd.conf**
```

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: mail_admin
sql_passwd: xxxpassxxx
sql_database: mail
sql_select: select password from users where email = '%u'

```

So im guessing the "plain" login parameter i saw was because saslauthd i set to plain login.

Quick question to get my head wrapped around the mail system.

the smtpd.conf file in the /etc/courier folder is the parameters for my IMAP config right?  I have POP3 configured, but I dont use that as my method for accessing email (i actually am going to disable it once i get more confortable with the works on postfix)

Here's my **/etc/courier/authdaemonrc** file

```


#authmodulelist="authpam"
authmodulelist="authpam authmysql"

```

I just added the authpam back in there, but i still cant login.

---

### Post by Mr. C. on 2008-06-27
You're trying to tackle too many things all at once.

You seem interested in learning about postfix, etc.  Why not invest a small amount of $$$ and get the excellent Book of Postfix?   It will explain all about postfix, how to put the pieces together, and build as complex a system as you might need, plus content filtering (antivirus,antispam,etc).

I gave a suggestion in the other posts about running saslfinger.

---

### Post by l8niteequine on 2008-06-30
Hi, I'm having some similar problems with postfix as before mentioned. I have set up a mail server using postfix and courier and can send mail to the local host and can receive mail. I need to be able to send email to another mail server that is on a Windows 2003 machine in the same lab but it has a different domain name. When I try to send mail to it I get the error host or domain name not found, name service error. I figured out how to get email from that machine to the linux mail server by adding the linux domain to that mail server. I would appreciate any suggestions. I've tried everything I can find by googling and on this forum. Thanks.

---

### Post by Mr. C. on 2008-06-30
Can the postfix server machine resolve the domain name of the Windows 2003 machine?

Show the log messages for the transaction that fails, and output of postconf -n.

---

### Post by l8niteequine on 2008-06-30
Here is the log from an email I tried to send:

Jun 30 16:08:53 score postfix/smtpd[32121]: connect from score.acme.cs.jmu.edu[10.0.0.253]
Jun 30 16:08:54 score postfix/smtpd[32121]: 00E985C0197: client=score.acme.cs.jmu.edu[10.0.0.253], sasl_method=PLAIN, sasl_username=brett
Jun 30 16:08:54 score postfix/cleanup[32125]: 00E985C0197: message-id=<48693D55.6070606@score.acme.cs.jmu.edu>
Jun 30 16:08:54 score postfix/qmgr[32114]: 00E985C0197: from=<brett@score.acme.cs.jmu.edu>, size=584, nrcpt=1 (queue active)
Jun 30 16:08:54 score postfix/smtpd[32121]: disconnect from score.acme.cs.jmu.edu[10.0.0.253]
Jun 30 16:08:54 score postfix/smtp[32126]: 00E985C0197: to=<administrator@acme5.cs.jmu.edu>, relay=none, delay=0.01, delays=0.01/0/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=acme5.cs.jmu.edu type=AAAA: Host not found)
Jun 30 16:08:54 score postfix/cleanup[32125]: 066F05C01AF: message-id=<20080630200854.066F05C01AF@score.acme.cs.jmu.edu>
Jun 30 16:08:54 score postfix/qmgr[32114]: 066F05C01AF: from=<>, size=2588, nrcpt=1 (queue active)
Jun 30 16:08:54 score postfix/bounce[32127]: 00E985C0197: sender non-delivery notification: 066F05C01AF
Jun 30 16:08:54 score postfix/qmgr[32114]: 00E985C0197: removed
Jun 30 16:08:54 score postfix/local[32128]: 066F05C01AF: to=<brett@score.acme.cs.jmu.edu>, relay=local, delay=0.02, delays=0.01/0.01/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Jun 30 16:08:54 score postfix/qmgr[32114]: 066F05C01AF: removed

Here is the result of postconf -n:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
inet_protocols = all
mailbox_command = 
mailbox_size_limit = 0
mydestination = score.acme.cs.jmu.edu, localhost
myhostname = score.acme.cs.jmu.edu
mynetworks = 127.0.0.0/8, 10.0.0.253
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

(Please keep in mind that I am a complete beginner with all of this) Thank you.

---

### Post by Mr. C. on 2008-06-30
The domain acme5.cs.jmu.edu does not resolve on the postfix box named **score**.  Are you running your own DNS servers?  If so, you need to add A/AAAA records for acme5.  Also take a look at wow have you setup the DNS resolver on that system (/etc/resolv.conf)?

```
$ host acme5.cs.jmu.edu.
Host acme5.cs.jmu.edu not found: 3(NXDOMAIN)

$ host cs.jmu.edu.      
cs.jmu.edu has address 134.126.20.50
cs.jmu.edu mail is handled by 5 barracuda.cisat.jmu.edu.
cs.jmu.edu mail is handled by 10 mp-cluster.jmu.edu.
```

If the host acme5 (and I presume this is the Windoze mail server) is a LAN-private box, and you are using a public DNS server, you can just add acme5 to your /etc/hosts file, or you can setup a transport map (man 5 transport) using the IP address of the acme5 box.

---

### Post by l8niteequine on 2008-06-30
I had better explain to you what I'm working on. We are setting up teams of 5 computers each with the following services: web, database, mail, dns, and firewall. The acme5 is one such team. That mail server is on windows 2003. I'm currently setting up a mail server on the scoring computer(ubuntu hardy heron) to send emails to each of the teams. I don't believe that DNS has been set up on this machine. I have tried to add the acme5 domain in several places and just tried adding it to the host file but received the same error. Do I need to set up the DNS on this computer in order to be able to send mail to the other mail servers?

---

### Post by Mr. C. on 2008-06-30
Postfix must have a working DNS, unless you disable dns lookups (with disable_dns_lookups; I'm incorrect about adding to /etc/hosts; i'd forgotten postfix won't use that unless disable_dns_lookups is yes).

Don't confuse the DNS resolver with a DNS server.  Your system's programs ask the resolver to resolve DNS queries, by using the DNS server specified in /etc/resolv.conf.  It doesn't matter where this server exists, so long as it does its job.

A DNS server responds to queries.  For those domains (zones) which it is not authoritative (fancy word for "responsible"), it can recursively resolve a query.  For those zones which it is authoritative, it replies directly with answers.

For postfix to be able to deliver to acme5.cs.jmu.edu, it looks first for the MX for that domain (an MX specifies that mail server that handles mail for a given domain).  But there is no MX.  So, it then tries to lookup an A record.  But there is no A record.  So it cannot find the mail server for that domain, and can only bounce the message.

A transport map allows you to say that, for example, all mail for a domain such as acme5.cs.jmu.edu should be relayed to another mail server; that other server can be specified either by hostname (which wouldn't work in your case until you have acme5.cs.jmu.edu defined in DNS), or by IP address.

---

### Post by l8niteequine on 2008-07-01
Thank you for your help. I can now send and receive emails.

---

