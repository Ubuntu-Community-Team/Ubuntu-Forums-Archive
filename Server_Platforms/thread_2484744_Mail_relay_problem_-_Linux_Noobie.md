---
title: "Mail relay problem - Linux Noobie"
date: 2023-03-08
forum: Server Platforms
---

### Post by privateland on 2023-03-08
Hi folks
I recently exchanged my windows webserver box (hosting around thirty websites) for an Ubuntu server.
Aside from the cost savings, I am astonished how much power per CPU cycle is available compared to Windows server.

I also have a Windows email server running Mailenable Enterprise. Several of my websites require to send mail via the email server, and previously I did that on PHP sites using Sendmail on Windows/Apache.

I have set up Postfix on the Ubuntu server to handle that task, but despite my best efforts, I cannot get past the authentication stage on the relay server. I continually get the following error;
[INDENT][I][COLOR=#333333][FONT=&amp]"Mar 8 10:06:14 mail postfix/smtp[9392]: 24D43281F11: to=<me@myserver.co.uk>, relay=mail.myserver.co.uk[xx.xx.xx.xx]:587, delay=30, delays=0.03/0.03/30/0, dsn=4.4.2, status=deferred (lost connection with mail.myserver.co.uk[xx.xx.xx.xx] while receiving the initial server greeting)"

[/FONT][/COLOR][/I][/INDENT]
[COLOR=#333333][FONT=&amp]Curiously, there are no traces (on the email server) that any attempt to connect has been made, so I am in full head-scratching mode.

There is a lot of references to that type of error on the web, but none that appears to work. I can send mail successfully to a mailbox on the server, but when I relay using authentication, the above message always appears.

Similarly there are a few Wordpress sites on the Ubuntu server which use SMTP plugins that authorise successfully. From this I am pretty sure that Blacklists nor Firewalls, nor AV programs are the root of the problem. I have tried to use static credentials as well as hashed , but I get the same message every time.

I've copied my main.cf file below. Anyone who can shed a light on my path will be a friend for life. Perhaps my Ubuntu learning curve just plateaued ?

Cheers
John

[/FONT][/COLOR]```
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


# See [http://www.postfix.org/COMPATIBILITY_README.html](http://www.postfix.org/COMPATIBILITY_README.html) -- default to 3.6 on
# fresh installs.
compatibility_level = 3.6






# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = encrypt
header_size_limit = 4096000
smtp_tls_CApath=/etc/ssl/certs
smtp_tls_security_level = encrypt
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


smtpd_sender_restrictions = reject_authenticated_sender_login_mismatch, permit
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = rocksport.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, rocksport.uk, localhost.uk, , localhost
relayhost = [mail.meancity.co.uk]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 127.0.0.1
inet_protocols = all


#New Bit For Relay
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
smtp_sasl_security_options = noanonymous


```

---

### Post by slickymaster on 2023-03-08
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2023-03-08
**postconf -n**
is the normal way to see the actual postfix config as parsed.
I don't use authenticated SMTP, except over post 587/tcp to the server.  My gateway only accepts email from the mail server, not any other clients (servers or desktops).  

The relayhost with authentication is likely where the issue lies.  Do you have the 'transport' file setup correctly?  I haven't used that method in  ... so long that I don't remember anything about it.  [https://www.linode.com/docs/guides/postfix-smtp-debian7/](https://www.linode.com/docs/guides/postfix-smtp-debian7/) explains how to use SASL authentication, but the authentication mode will be controlled by the upstream relay, not you.

A ran a nmap scan on your server.  Do you really want the ports you have there open to the internet?  If it were me, I'd have 
SMTP 25/tcp
https  443/tcp
ssh    62022/tcp
and have all the others closed.  No way would I have http, imap, ftps, imaps, nor authenticated smtp on 587/tcp open over the internet.  I'd require a VPN to access those others. The world isn't safe anymore. It just isn't.  After you've seen 100K attempted IMAPS connections per day for a few days, perhaps you'll come to the same conclusion.  Definitely never, ever, allow password-based authentication over the internet.

ftps is handled by having ssh/scp/sftp instead, which are well secured and use ssh-keys.  Windows people often get confused into thinking that ftps is ok.

---

### Post by privateland on 2023-03-08
Hi The Fu
Thanks for taking the trouble to reply. I am using SMTP over 587 here.  My first thought was that the upstream server was responsible, but the absence of any evidence that a connection was attempted is puzzling. 
What is weird I think is that Wordpress sites can easily relay mails using authentication on the server. I guess what I need is a WP plugin for vanilla PHP :-)

I really don't need those SMTP and IMAP ports open at all on the webserver. I just opened them to rule out the firewall as the cause of the problem.
I have seen the myriad attempts at IMAP and SMTP access on my mailserver, but there are a couple of hundred mailboxes there. VPN is impractical from my perspective.
As you say though, coming from Windows background, I am not in the comfort zone with Linux :-)

Tried postconf -n too ... Thanks for that. 

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
compatibility_level = 3.6
header_size_limit = 4096000
inet_interfaces = 127.0.0.1
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = $myhostname, rocksport.uk, localhost.uk, , localhost
myhostname = rocksport.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_CApath = /etc/ssl/certs
smtp_tls_security_level = encrypt
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = encrypt

---

### Post by TheFu on 2023-03-08
Well, you don't have to open ports to the internet to have them open for localhost-only.
Also, as you can see from your **postconf -n** output, the relayhost value is empty, so you don't have that setup correctly.  postconf shows what the parser actually sees. That's important.

Wordpress - yuck.  Expect to get hacked every few weeks unless you lock it down and avoid 3rd party addons.  Where I work, we aren't allowed to have any php-based webapps on the internet.

---

### Post by SeijiSensei on 2023-03-08
If you know how to use sendmail, install that instead. It will remove Postfix.

```
sudo apt install sendmail
```

Then you just need to edit /etc/mail/sendmail.mc and add the line

```
define(`SMART_HOST',`relay_host_name')dnl
```

along with the other "defines" at the top of the file. Replace "relay_host_name" with either a fully-qualified domain name or an IP address in square brackets like [10.10.10.10]. Be sure to get those opening and closing quotation marks correct, too.

Now in the /etc/mail/ directory where sendmail.mc resides, run the command

```
m4 < sendmail.mc > sendmail.cf
```

to create a new sendmail.cf with the relay host defined. (It's the "DS" definition usually near the top of the file.) Now restart sendmail.

I did this very procedure just a few days back on a 20.04 web server that needed to send email through a companion SMTP server that handles mail for my domains.

---

