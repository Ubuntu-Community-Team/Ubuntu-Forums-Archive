---
title: "Simple setup for enabling mail() in PHP with Postfix"
date: 2012-06-20
forum: Server Platforms
---

### Post by mogie on 2012-06-20
Hi forum!

I've been over my head with threads which never describe my simplest of needs, so I will ask it here: To be able send mail with the mail() function in PHP, using my own server. I'm not interested in setting up an IMAP/POP server, **just** to be able to send this mail from PHP..

I would expect to find some howto about this elsewhere, so do anybody know about one? :-(

As I understand from reading elsewhere, I don't need to install sendmail to enable this feature in PHP, cause postfix is a simpler and somewhat more enhanced version with sendmail implemented. 

Is this right..? 

I got port 25 open, called my ISP even to check it.

Here's some settings from my PHP.ini file:
```

SMTP	localhost	localhost
smtp_port	25	25
Path to sendmail 	/usr/sbin/sendmail -t -i
sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i 

```

My script works great on all other servers than mine. The script is good btw.

---

### Post by mogie on 2012-06-20
I found some logs in /var/mail/www-data  - actually all the mail which was sent using my script. Is it possible to find out where it's gone, which logs should I check out?

---

### Post by SeijiSensei on 2012-06-20
Start by looking in /var/log/mail.log.  It should list every transaction.

---

### Post by mogie on 2012-06-21
What should I find in /var/log/mail.log ? I cannot find anything about any mail transactions, or any errors from mail tried sent at any point the last 12 hours. It seemed like it stopped logging or something. I dont know if its sendmail and/or postfix which is logging to this spesific file..

The last lines are from yesterday:
```

Jun 20 16:34:28 lnx postfix/master[16701]: fatal: bind 0.0.0.0 port 25: Address already in use

```

After this there is nothing..

Is there something wrong with my /etc/postfix/main.cf maybe?
(I've put example.com istead of mydomain.com in it for this post)

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = lnx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = post@example.com, lnx, localhost.localdomain, localhost, lnx.example.com
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter =
inet_interfaces = all
inet_protocols = ipv4
message_size_limit = 0




```

---

### Post by SeijiSensei on 2012-06-21
> **mogie said:**
> The last lines are from yesterday:
```

Jun 20 16:34:28 lnx postfix/master[16701]: fatal: bind 0.0.0.0 port 25: Address already in use

```

Something seems to be listening on the SMTP port already.  What if you run "sudo service postfix restart" and then look at mail.log?  Does the server start, or do you get the same "address in use" error?

You didn't by any chance install both sendmail and postfix, did you?  Usually if you install one the other is removed.

You can see which process is listening on port 25 by running:

```
sudo netstat -tulpn | grep :25
```

On my server running sendmail, not postfix, I get:

```
tcp    0   0 0.0.0.0:25   0.0.0.0:*  LISTEN      12403/sendmail: acc
```

The "acc" at the end is a truncation of the way sendmail announces its listener, "sendmail: accepting connections".  The 12403 is the process ID.

---

### Post by mogie on 2012-06-21
Woo! Beautiful answer :D

Yeah. The same error comes up. 

```

Jun 21 21:26:57 lnx postfix/master[6419]: fatal: bind 0.0.0.0 port 25: Address already in use

```



this is my sudo netstat -tulpn | grep :25:
```

tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      11612/sendmail: MTA

```

Sorry, I'm a bit lazy, but what should I do? Uninstall postfix or sendmail? I like to keep it simple - just be able to send mail() thorugh PHP. That's all. As far as I know I just need postfix for this? Is not sendmail a "part" of postfix, right?
Or maybe I'll need to config sendmail another way? :-)

Update: sendmail is not installed (tried apt-get remove sendmail, and got package not installed). I even tried apt-get remove sendmail --purge, but it does not remove anything...

---

### Post by lisati on 2012-06-21
There is an [MTA]("http://en.wikipedia.org/wiki/Mail_transfer_agent") called "sendmail", and an MTA called postfix: in normal circumstances only one or the other is necessary on your system. 

One thing to be aware of is that Postfix comes with a command which it calls "sendmail" that provides compatibility for sites which might have once had the Sendmail MTA installed but now has Postfix installed.

---

### Post by SeijiSensei on 2012-06-23
Here's a guess about what's going on.

You'll notice that netstat shows a copy of postfix listening on 127.0.0.1.  However the configuration file you posted has "inet_interfaces=all".  By default, Postfix on Ubuntu listens only to the localhost interface.  It's looks like there's a running copy of Postfix with the default configuration.

Have you tried stopping Postfix with "sudo service postfix stop"?  What happens?  After you do that, does netstat still show a listener?  If so, you can try killing the listening process outright with "sudo kill -9 11612" which is the process ID reported by netstat above?  (If netstat reports a different ID this time around, use that instead.)  Use netstat to confirm that there's no longer a process listening on port 25.  Now try "sudo service postfix start"?  Does that work?

---

### Post by mogie on 2012-06-24
NICE! :-)

That did the trick. I got a bunch of mail running in now.
The 11612/sendmail: MTA was blocking and I had to use kill -9 to stop it. So I dont know exactly the source of this prosess. I hope it wont start up again and truncate the postfix service. 

Also, I need to be sure the security around the postfix prosess is at the optimal. If you see something bad in the main.cf above, please let me know.

---

### Post by SeijiSensei on 2012-06-24
Try running [FONT="Courier"]chkconfig | grep \ on[/FONT] at the command prompt.  You'll see a list of services which run at startup.  You should see postfix in the list, but nothing else that listens on port 25.  Services that launch at boot have corresponding symlinks in the /etc/rc[2-5].d/ directories; you can see them with "ls /etc/rc2.d/" although changing the symlinks manually is discouraged.  Use chkconfig or [sysv-rc-conf](http://www.linuxpowerup.com/en/Chkconfig-is-good-but-for-Ubuntu-sysv-rc-conf-is-a-better-alternative-for-enable-and-disable-services-at-startup) instead.

I'm not a postfix user, so I can't be relied upon to review your configuration for security.  If this installation of postfix is to be used solely to handle mail generated by PHP scripts, then I'd limit inet_interfaces to 127.0.0.1.  There's no reason for postfix to listen on any other interface in this application.  If you want to connect to it over a network as well, then you should permit only the listening interfaces.  You do accept connections only from 127/8 using mynetworks, but why listen for connections that should never be accepted?  If this machine is visible over the Internet, then I'd be extremely wary of letting it listen on the external interface right away.  You don't want to become an open relay.

---

### Post by mogie on 2012-06-24
I found that both sendmail and postfix are listet in sysv-rc-conf startup list with level 2-5. So, should I disable the sendmail service, or do this one run as an alternative to the postfix in some cases?

I'm sorry, but I'm unexperienced with how to configure the main.cf. I've set it to inet_interfaces = 127.0.0.1 now, but is it on mynetworks = mynetworks = 127.0.0.0/8 you mean that I've set something wrong? I dont know what that "/" means.

Again thanks for all the help to now! It's been great!

---

### Post by SeijiSensei on 2012-06-24
127.0.0.0/8 is a shorthand for the network subnet with addresses from 127.0.0.0 through 127.255.255.255.  This subnet has eight bits of network "mask," the thirty-two bit number 11111111000000000000000000000000 counting from left to right, commonly represented as 255.0.0.0, .  So the 127/8 network is distinct from the 128/8 subnet, but both 127.1.1.1 and 127.32.56.244 are in the 127/8 subnet.)  

When the operating system starts up it creates a software-only network interface called "lo" and assigns it the address 127.0.0.1.  This is commonly called the "locahost" interface.  Other applications running on the server can send packets to this address, but not machines from outside. (Nothing is impossible in the world of computer network hackery, so I suspect it's possible to exploit some arcane bug and send spoofed packets claiming to be from an address in 127/8.  I don't worry about stuff like that myself.)

So if all you want to do is send mail from a PHP application, the default installation of postfix, with a couple of tweaks, should work fine, I recommend that you purge postfix, and any residual sendmail cruft, and start with a default installation like this:

```

sudo apt-get purge sendmail sendmail-*
sudo apt-get purge postfix
sudo apt-get install postfix

```

When installed, the default server should be listening only on the localhost interface, and PHP should be able to hand it mail and have it delivered.  

Here are a couple of things to keep in mind, though.  First I'll bet the "envelope sender," the address at the very top of the message headers in the field called "Return-Path," is "www-data@something".  That's because the Apache server runs as user www-data and talks to postfix with that user's ID. This may not matter to you if you control the visible From address reported by the person's mail client.  You can do that in PHP by including the optional fourth parameter of [mail()](http://php.net/manual/en/function.mail.php) with a value like "From: [noparse]someone@example.com[/noparse]".  Like "To:" or "Subject:," "From:" is part of the message body, not the headers, and thus under the message sender's control.  

You should make sure that the Return-Path address appears as, at worst, [noparse]www-data@domain.name[/noparse],   Administrative traffic like non-delivery notices is sent to the envelope sender.  I think you can do this by setting the [myhostname]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#myhostname") directive to "domain.name".  You might also want to to force the server to [append your domain]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydomain") on mail from users with unqualified names like simply "www-data".  You should accept mail for [noparse]www-data@domain.name[/noparse] and either deliver it to a human for review, or direct it to a local mailbox for archiving and later review.

---

### Post by dbrooke on 2012-06-25
All I did to get mail() working on a fresh Ubuntu 12.04 Server install (** without Mail checked during install **) was:

apt-get install sendmail

(and then 'apache2ctl restart')

I haven't touched the default php ini file yet.

Donovan

---

### Post by SeijiSensei on 2012-06-26
Postfix is the preferred MTA for Ubuntu, so I try to adhere to that viewpoint here.  Personally, I use sendmail, too.

Sendmail will have similar issues about how the [envelope sender]("http://ubuntuforums.org/showpost.php?p=12035403&postcount=2") is set.  At a minimum, you need to add the Apache user ("www-data" on Ubuntu) to the trusted-users list in sendmail.

---

### Post by mogie on 2012-06-26
I'm stumbeling to this problem when trying:
apt-get purge sendmail-*

[Could not perform immediate config on exim4-daemon-light]("http://ubuntuforums.org/showthread.php?p=10411454")

After some Googling it seems that this is a dependence bug of some sort which I've not been able to solve yet...

Ok... now I've managed to **** up again. This time exim4 package gives med the same error as exim4-daemon-light..

---

### Post by SeijiSensei on 2012-06-26
Try purging both sendmail and exim at once with 

```
sudo apt-get purge sendmail sendmail-* exim exim-*
```

Does that help?

---

### Post by mogie on 2012-06-27
Nope, doesnt help much cause its still asking for the same thing trying to purge postfix:

```

E: Could not perform immediate configuration on 'exim4-daemon-light'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

```

```

The following packages will be REMOVED:
  courier-imap* courier-imap-ssl* courier-pop* courier-pop-ssl* postfix*
The following packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light


```

As I said, it is a reported bug like in my last post it seems to bugs.debian.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621836]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621836")

---

### Post by mogie on 2012-06-27
Hi again! I managed to solve it.

I did some trickery with aptitude, and I got to install exim4 by:

```

aptitude install exim4

# and then

apt-get purge postfix sendmail-*

```

.. with some temporary dependency errors to mdadm, rkhunter and some other maildependent services who was screaming after postfix/exim. 
In other words I did not get the same errors with apt-get as in aptitude, so I've learned that these two are completely different.

I had also another problem after doing the clean postfix install:

```

# /var/log/mail.log:
(host mx1.dest-mail.net[193.107.29.49] said: 550 Access denied - Invalid HELO name (See RFC2821 4.1.1.1) (in reply to MAIL FROM command))'
....

to=<ossecm@lnx.mydomain.com>, relay=none, delay=0.03, delays=0.03/0/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=lnx.mydomain.com type=A: Host not found)

```

I solved this by editing /etc/postfix/main.cf line:
```


# from
myhostname = lnx
# to:
myhostname = lnx.mydomain.com


```

Strangely it worked out with just my hostname before (lnx), but I wonder if it can have something to do with the reciever mail mx-server..

Hope this helps some other people too. :-)


Also now checking the startup services, "Sendmail" is no longer activated (level 2-5) - only postfix :-)
```

sysv-rc-conf

```

---

