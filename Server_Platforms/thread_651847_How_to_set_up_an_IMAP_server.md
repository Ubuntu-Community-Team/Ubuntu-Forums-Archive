---
title: "How to set up an IMAP server?"
date: 2007-12-28
forum: Server Platforms
---

### Post by CaptSaltyJack on 2007-12-28
I'd like to set up IMAP and SMTP servers that work completely independent of anything else.  In other words, they will run on an Ubuntu box, and users can send mail to other users on that machine, and all mail is stored on the Ubuntu box.

A couple issues come to mind: when sending emails, what will the email address be?  If it's just sitting on some box at 10.1.23.88, will email addresses be bob@10.1.23.88?

Basically I'm setting up a Chandler server at work and I want to have our own IMAP/SMTP mail system on the same box as the Chandler server.

Any help would be appreciated!

Chandler:
[http://chandlerproject.org/](http://chandlerproject.org/)

---

### Post by bmathis on 2007-12-28
Check out this link [https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer"). It should have everything that youll need. For the domain, since I'm assuming that it will be used just on your local network, you can name it anything like domain.local or simular. That way their email addresses will be [email]bob@domain.loca[/email]l.

---

### Post by CaptSaltyJack on 2007-12-28
Great, thanks!

---

### Post by HermanAB on 2007-12-28
You can use postfix or qmail, with dovecot.  They work very well together.  However, installing it is a chore and if you haven't done it before, then it can easily take you two weeks to get it to work.

Over the years, I have used sendmail, postfix and qmail and they all work reliably, but they are hard to install and maintain.

If you want to have a system that is easy to install (in about 20 minutes!) and administer and just works, with zero maintenance, then install Citadel.

Cheers,

Herman

---

### Post by bmathis on 2007-12-28
Follow the guides that I linked to should provide you with a fully working and secure (as in non-relay) server in about 20 minutes (a little bit longer if you read up on the documentation) as well... all of that and you dont have a ugly interface and a confusing "room" system as you do with Citadel... no disrespect, its just my opinion.

---

### Post by CaptSaltyJack on 2007-12-28
Thanks bmathis!  Everything works great, except:

I can only connect to the SMTP server from the Ubuntu box itself. :)  Other computers on the LAN cannot connect to port 25 of the Ubuntu server.  I know it has something to do with the Postfix config, I just can't figure it out.  Our LAN IPs are 10.1.*.*.  I set main.cf's mynetworks variable to 10.1.0.0/16.  This doesn't seem to work.

---

### Post by jtc on 2007-12-28
inet_interfaces = ?

---

### Post by CaptSaltyJack on 2007-12-28
main.cf:

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = host.censored.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = host.censored.com, localhost.censored.com, localhost, 10.1.4.93
relayhost =
#mynetworks_style = subnet
mynetworks = 127.0.0.0/8, 10.1.5.0/24, 10.1.4.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all

```

---

### Post by jtc on 2007-12-28
Well, from what I can tell the main.cf looks fine.

What respons do you get when you try to connect from another host on the LAN? A timeout? Closed connection? Any error-message?

Also, what does it say in your mail.log when another computer at the LAN is trying to connect?

---

### Post by CaptSaltyJack on 2007-12-28
I get an immediate connection refused message, which means the host is resolving and it's up, but the port is not accepting connections.  mail.log reports nothing.

---

### Post by jtc on 2007-12-28
How about syslog then? All kinds of more or less useful stuff end up there :-)

...and perhaps it is time to see if postfix is actually listening on port 25.

```
sudo netstat -tlp
```

---

### Post by HermanAB on 2007-12-28
Note that Citadel is a standard mail server that also happens to have a web interface.  You don't have to use the web interface if you don't like it.  Anyhoo, the Blue Citadel theme is quite nice.

Citadel is very old and mature and supports every mail protocol ever invented out of the box.

It uses a BerkeleyDB back end.  It is very efficient and can store 256 Terabytes of mail.  It works fine with tens of thousands of users on a single server.  Since all mail is stored in a data base, only a single copy of a message is stored.  So if the Human Resources girl sends out a .doc file to all 25000 users, then you don't have to run out to go and get another 500GB disk drive.  This is of course immensely important to a large organization.  

You can literally replace a rack full of MS Exchange servers with a single Citadel server and provide better service to the users.

Cheers,

Herman

---

### Post by CaptSaltyJack on 2007-12-28
Looks like other people have had the same issue.

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=postfix+%22can%27t+connect+to+smtp%22&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=postfix+%22can%27t+connect+to+smtp%22&btnG=Search)

It's a tough one, for sure.  It's not a firewall issue, either.  These two computers are on a LAN together, and the client can access all kinds of ports on the server, EXCEPT port 25, which works fine when the server accesses that port via localhost.

Nothing suspect in syslog, and yes, netstat shows smtp is listening.  "telnet localhost 25" works on the server, but other machines on the LAN can't connect to port 25.  This is maddening.

---

### Post by andol on 2007-12-29
Well, then I have no idea what the trouble might be.

What happens if you try to connect to the smtp-server from outside the LAN? Works then? (or is it only for internal use?)

One thing which is strange is that you get no specific error message. In my experience postfix generally gives you that. 

You LAN, is it switched or routed? If it is the later, perhaps you have some fishy rules in your router? No idea why it would have. Just a long shot.

---

### Post by HermanAB on 2007-12-29
Check the firewall rules:

$ sudo iptables -L

and flush them all if there are any:
$ sudo  iptables -F

or if you are running Firestarter, enable SMTP properly.

Also check tcpwrappers.  Specifically /etc/hosts.allow.  You either have to allow postfix explicitly, or allow all with ALL: ALL.

Cheers,

Herman

---

### Post by CaptSaltyJack on 2008-01-18
Seems to be an internal networking prob, nothing to do with Ubuntu.
Thanks!

---

