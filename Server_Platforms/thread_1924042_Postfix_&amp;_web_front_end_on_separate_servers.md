---
title: "Postfix &amp; web front end on separate servers"
date: 2012-02-11
forum: Server Platforms
---

### Post by av8or on 2012-02-11
I'm fairly new to Ubuntu.  Downloaded and installed my first Ubuntu server this week and so far I'm very happy with my decision.

I set up a web server and within a very short time I had a WordPress blog up and running.  Very easy and straightforward.

What I would like to do is install another separate server that will function as an email server.  I will probably end up hosting 2-3 domains.  I would like to use the already set up and configured web server for the web frontend for email but have a separate server for email.

Is this possible?  If so, are there any guides for how to do this?  I've looked around and can't find a guide for exactly what I'd like to do.  Maybe I'm just not searching correctly.  Any help/direction is much appreciated.

Thanks!

Av8or

---

### Post by volkswagner on 2012-02-11
For hosting several domains on a dedicated mail server, you will be very happy with [Citadel]("http://www.google.com/url?sa=t&rct=j&q=citadel%20mail%20server&source=web&cd=1&ved=0CCgQFjAA&url=http%3A%2F%2Fwww.citadel.org%2Fdoku.php%2Fstart&ei=YSg3T_jtCKqI0QH-0LzJAg&usg=AFQjCNF9RTAKK9PUg-3bU8dFy1-eNXJstg").

Citadel includes it's own webmail server which also allows the Admin to manage the server.

Do you have more than one public ip address?  If you only have on public ip address you can use your main web server, setup a vhost to act as a reverse proxy to you mail server for webmail access.

---

### Post by SeijiSensei on 2012-02-12
I use [SquirrelMail]("http://squirrelmail.org/") with a standard Linux mail server running sendmail (actually [MailScanner]("http://www.mailscanner.info/")) and dovecot on the back end.  SquirrelMail can be configured to use any mail server it can see as long as the server provides SMTP and IMAP.

---

