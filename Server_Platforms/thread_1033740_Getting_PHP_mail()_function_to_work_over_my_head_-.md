---
title: "Getting PHP mail() function to work over my head :-("
date: 2009-01-07
forum: Server Platforms
---

### Post by kepardue on 2009-01-07
I've had a server set up for a while now, but PHP's mail() function has never worked.  I've never needed a mail server since I use Google Apps for this particular domain, but in seeking to put just an SMTP server on there for PHP's mail() function I have run into three days of dead ends and headaches.  I've found many replies on these forums about it, but I must be missing some critical element because it just doesn't work for me.

Is there a way to easily and relatively securely make PHP's mail function work without having to go through the 15 pages of instruction to make a full blown mail server work?

Is there a book that describes a decent overview of the whole process?  I've got [Beginning Ubuntu Server Administration]("http://www.amazon.com/Beginning-Ubuntu-Server-Administration-Professional/dp/1590599233"), but that seems to be more focused on general servers and not web servers.  There's no section at all about mail in the book.

I really want to learn this stuff, but I'm running into the issue of there being so much documentation out there, with half of it being outdated, deprecated, or no longer exist and the other half written in abbreviated grammar that I have trouble interpreting.  In fact, I've probably made a mess of my whole server I've installed and tweaked with the configurations of so many different packages.

---

### Post by tubezninja on 2009-01-07
I've find that just getting postfix installed and running allows php mail() to work.

There's some documentation on getting a mail server running in our own HowTos that is current and not too hard to follow.  Here's an example:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by kepardue on 2009-01-07
Followed those instructions to the letter (inserting my domain name in the appropriate places) and it still doesn't seem to want to work.  

I did check the mail.err log.  This is what I'm receiving.

Jan  7 15:58:59 sixtus sm-msp-queue[7691]: unable to qualify my own domain name$
Jan  7 16:00:01 sixtus sm-msp-queue[7756]: My unqualified host name (sixtus) un$
Jan  7 16:01:01 sixtus sm-msp-queue[7756]: unable to qualify my own domain name$
Jan  7 16:20:01 sixtus sm-msp-queue[7895]: My unqualified host name (sixtus) un$
Jan  7 16:21:01 sixtus sm-msp-queue[7895]: unable to qualify my own domain name$
Jan  7 16:29:13 sixtus postfix/master[8229]: fatal: bind 0.0.0.0 port 25: Addre$
Jan  7 16:34:30 sixtus postfix/master[8504]: fatal: bind 0.0.0.0 port 25: Addre$
Jan  7 16:48:09 sixtus postfix/master[8624]: fatal: bind 0.0.0.0 port 25: Addre$
Jan  7 17:00:01 sixtus postfix/cleanup[6502]: fatal: open dictionary: expecting$
Jan  7 17:01:02 sixtus postfix/cleanup[6604]: fatal: open dictionary: expecting$
Jan  7 17:01:07 sixtus postfix/smtpd[6606]: fatal: open dictionary: expecting "$
Jan  7 17:02:03 sixtus postfix/cleanup[6608]: fatal: open dictionary: expecting$
Jan  7 17:02:08 sixtus postfix/smtpd[6609]: fatal: open dictionary: expecting "$
Jan  7 17:03:04 sixtus postfix/cleanup[6611]: fatal: open dictionary: expecting$
Jan  7 17:03:09 sixtus postfix/smtpd[6612]: fatal: open dictionary: expecting "$
...

Not sure if that has any particular meaning to my problem.  Like I said, I've probably foobarred everything with all the things I've been trying to do to fix this.  :(

---

### Post by kepardue on 2009-01-08
Okay, I did a apt-get --purge remove of postfix and re-walked through the resource.  It seems to work now, I'm not getting the errors in mail.err that I was previously.  However, PHP's mail function is also not working.  In /etc/php5/apache2/php.ini, I have the default settings for mail:

[mail function]
; For Win32 only.   
 SMTP = localhost
 smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = usr/sbin/sendmail -t -i

I've tried changing that parth to usr/bin/sendmail -t -i but haven't had any success with that.  Is there something in the PHP configuration that I'm doing wrong?

---

### Post by hyper_ch on 2009-01-08
go to [http://www.howtoforge.com](http://www.howtoforge.com) , search for the perfect ubuntu server howtos, install postfix as described in there.

---

### Post by kepardue on 2009-01-08
I've looked at the perfect server setup before. I could be wrong, but I think that's more complicated of a setup than I actually need.

Here's another funny thing.  I set up an extra laptop with ubuntu installing the basics, apache, php, mysql, and then postfix.  I ran through the base configuration, didn't mess with any of the SASL stuff as indicated in the link above, and ran my mail command.

To my surprise, it worked.

When I looked at the PHP.ini file, I found that the "For Win32 only" settings were in place (localhost, port 25), but the "Unix only" section, sendmail_path, was commented out.  No value in there for sendmail at all.  I have no idea how it's working in that case.

At any rate, I commented out that section, and mail now comes through on the same domain that this is on (the rest of my mail is handled with Google Apps).  I'm receiving the messages on another Google apps domain, but not on a different domain where the email *isn't* hosted with Google apps -- at least not after waiting ten minutes.

I'm sure it could be just general Internet slowness, but could the missing SASL take care of the last part?  Maybe the latter domain is blocking it somehow, but I don't see them having tighter security than Google.  I'm about to try running through the SASL part of the process on the laptop to see if things still work.  If so, I'll repeat it on the actual web server.

---

