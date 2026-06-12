---
title: "Postfix-tls for sending mail securely"
date: 2005-03-17
forum: Server Platforms
---

### Post by theantix on 2005-03-17
I would like to use my Ubuntu server for sending mail in programs like Evolution or Thunderbird, but am baffled at how to do this securely.  I've got the postfix-tls package installed, and I can check mail with imaps or pop3s using dovecot which works wonderfully.  However, for sending mail I would like some brief instructions on how to accomplish this task using the Ubuntu tools as the server and desktop and never have my mail/passwords sent via cleartext and at the same time not running an open relay either.

What I did was uncomment the postfix-tls lines at the tail end of /etc/postfix/master.cf and it now looks like this.
```
# only used by postfix-tls
tlsmgr    fifo  -       -       n       300     1       tlsmgr
smtps     inet  n       -       n       -       -       smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
587       inet  n       -       n       -       -       smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
```

I restarted postfix and according to nmap I now have both smtp and smtps ports open -- without those lines only smtp is open.  I'm not sure what else I need to do on the server end, looking over the postfix docs and configuration files are not giving me any clues to additional configuration requirements.

So I try in both Evolution and Thunderbird and I cannot seem to convince them to let me send outgoing mail even to local users on the server.  Thunderbird has configuration options on smtp for sending as "TLS" or "SSL", each gives me the same message of: 
```
Sending of Message failed.
An Error occured sending mail: Unable to connect to SMTP server myservername.  The server may be down or may be incorrectly configured.  Please verify that your Mail/News account settings are correct and try again.
```

Evolution has seemingly fewer options and allows me to enable the generic worded "Server Requires Authentication", which allows me to change the type of authentication.  No matter what I choose though, I get the same error message:
```
Error while performing operation.
Welcome response error: Unknown.
```
The fact that both supported clients cannot send mail securely in this way leads me to believe the problem likes with the postfix configuration.  Does anyone have a clue to what I am missing in the postfix setup to get this working?

---

### Post by alastair on 2005-03-17
So, what do the postfix log files say? The log files are your FIRST port of call.

I've used Postfix for a long time and the problem is almost certainly local to your config. I have never used TLS with it though - but there is more to do than just fiddling with the "master.cf" file.

e.g. main.cf is the main config.

I would check this :

/usr/share/doc/postfix/README.Debian

and :

[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

If you get stuck, browse the postfix list archives, check the FAQ and then perhaps post a question on the Postfix mailing list. It is very good.

---

### Post by BoBoB on 2005-03-18
Remember to use nmap on the server's external ip, not localhost.
It may not listen on the external interface even it it's listening on 127.0.0.1.

If you have this line in main.cf:

  mynetworks = 127.0.0.0/8

then postfix only allows connections on the local interface.

Try adding the IP addresses (or a subnet) to allow other computers to connect.

For example:

mynetworks = 127.0.0.0/8 192.168.1.0/8

The above line would also allow the computers on the 192.168.1.x subnet to connect.  Of course there is a whole bunch of other settings in main.cf that need to be configured.

If you are using portmap, ensure that ARGS in the file /etc/defaults/portmap is not limiting connections from other computers.

---

### Post by garyng on 2005-03-18
secure smtp is quote fuzzy, given my experience. I use exim4 rather than postfix but I believe the basic are the same :

1. you need to have certificate setup on the server side as otherwise, TLS just won't work.

2. there are two method to do this, either another secure port or STARTTLS on port 25.  Not all clients support STARTTLS.

try to telnet into your mail server port 25 and type "EHLO" to see what it announce. If you see STARTTLS, it should have been properly setup.

---

### Post by billycub on 2005-04-24
It took me a day to get this set up, but I think what I've done is similar to what you're asking.  The following web page helped me out:
  [http://small.dropbear.id.au/myscripts/postfixmysql.html](http://small.dropbear.id.au/myscripts/postfixmysql.html)
  
You need to install libsasl2-modules and postfix-tls since postfix authentication is tied up with SASL.  I roughly followed the instructions on the page linked above, but instead of using mysql for authentication I just used PAM, which means that any regular users on my system can authenticate using their normal system passwords.  This may or may not be what you want.  To set that up, I edited /etc/postfix/sasl/smtp.conf to read
```
  pwcheck_method: pam
``` 
and then I copied /etc/pam.d/imap to /etc/pam.d/smtp.

I also added the following to my /etc/postfix/main.cf 
```
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = myserver
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject 
``` 

With this setup, users can now use SMTP with TLS to authenticate and send mail.  The server will not relay SMTP for connections that do not authenticate.  Perfect, I think...

Hope this helps you get a bit further.

---

