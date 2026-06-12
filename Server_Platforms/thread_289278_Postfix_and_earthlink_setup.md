---
title: "Postfix and earthlink setup"
date: 2006-10-30
forum: Server Platforms
---

### Post by rcpettit on 2006-10-30
I got a ubuntu 6.10 server that runs great. The only problem I'm having is getting my server to send email. I found this searching the web but no luck.
 
Do these things as root:
[LIST=1]
[*]Install [_[COLOR=#810081]postfix-tls[/COLOR]_]("http://packages.debian.org/postfix-tls") and [_[COLOR=#0000ff]libsasl2-modules[/COLOR]_]("http://packages.debian.org/libsasl2-modules").
[*]Add the following settings to /etc/postfix/main.cf:[INDENT]smtp_sasl_auth_enable = yes[/INDENT][INDENT]smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd[/INDENT][INDENT]smtp_sasl_security_options =[/INDENT][INDENT]relayhost = smtpauth.earthlink.net[/INDENT]
[*]Create /etc/postfix/sasl_passwd as follows:[INDENT]smtpauth.earthlink.net *username*@earthlink.net:*password*[/INDENT]
[*]chown root:root /etc/postfix/sasl_passwd && chmod 600 /etc/postfix/sasl_passwd.
[*]postmap /etc/postfix/sasl_passwd.
[*]/etc/init.d/postfix reload[/LIST]Voilà, all your outgoing email is now sent via smtpauth.earthlink.net.
 
But the email keeps getting sent back. Local email transfers fine from domain to domain on the servers. Also I'm using ISPconfig on the server. Any ideas.

---

### Post by MJN on 2006-10-31
Help us to help you by providing your error logs! :)

---

### Post by rcpettit on 2006-11-19
Found the answer by accident.  Needed to change
 
[COLOR=seagreen]relayhost = smtpauth.earthlink.net[/COLOR]
 
to
 
[COLOR=seagreen]relayhost = [smtpauth.earthlink.net][/COLOR]
 
Now everything is working great :)

---

### Post by MJN on 2006-11-19
Your error logs would've got us there sooner than this!

Good to see you're now sorted though.

Mathew

---

