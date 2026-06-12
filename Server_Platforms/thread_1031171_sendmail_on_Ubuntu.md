---
title: "sendmail on Ubuntu"
date: 2009-01-05
forum: Server Platforms
---

### Post by jkounis on 2009-01-05
I have a LAMP server on our small office network with 5 or 6 clients. On the local web server, we have Mediawiki, Joomla, Drupal, and some other PHP applications.

These web applications usually expect the ability to send emails to users (I suppose through sendmail). However, I have not gone through the effort of setting up a mail server. Since the server is behind a firewall, it would involve some complicated setup, opening ports, and security measures to prevent the machine from being an open SMTP relay. (We get our email through the same server that hosts our website.)

Is there a simpler solution? Can I simply set up sendmail to forward through my ISP's SMTP server (mail.myisp.com)? Or must I have a local mail server set up for sendmail to work?

---

### Post by volkswagner on 2009-01-05
I have heard that sendmail is more difficult to get running than [postfix]("https://help.ubuntu.com/community/Postfix?highlight=%28postfix%29").

You can configure postfix to use your ISP's smtp server.  This is accomplished in /etc/postfix/main.cf  with the relayhost = smtp.4your.isp.com

Check out [this]("http://ubuntuforums.org/showthread.php?t=990582") thread.

Good luck

---

### Post by HermanAB on 2009-01-05
Here you go:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

Cheers,

Herman

---

### Post by jkounis on 2009-01-09
Thanks to both of you! I got it working, but configuring postfix is more complicated than I thought. The links you provided certainly helped, though.

---

### Post by bovcan on 2011-01-25
I am using always sendmail, for reciving and sending mails. For now it works just fine.

---

