---
title: "Need Mail setup recommendations"
date: 2010-11-20
forum: Server Platforms
---

### Post by clay7 on 2010-11-20
Hello,

I'm configuring a server but at this time I can't send mail. I tried using the PHP mail() function and it didn't work. Webmin says I have no mail configured. 

I'll be the only user and mail recipient. I've used Squirrelmail and Roundcube before and liked them. 

**Do I need to install Postfix in order to user Squirrelmail or Roundcube?** How should I set up mail?

Here's my setup:

10.04 LTS Server edition
Webmin 1.520
Apache 2.x
MySQL 5.x
PHP 5.x

Thank you,
Clay

---

### Post by SeijiSensei on 2010-11-20
> **clay7 said:**
> **Do I need to install Postfix in order to user Squirrelmail or Roundcube?** How should I set up mail?

If you want to accept mail and store it locally, yes.  If you're happy using a remote mail server and just want Squirrelmail, no.  You can tell Squirrel to use your remote mail server.

How you should set up mail is up to you.  A few things you might want to keep in mind include how comfortable you'll be with setting up and maintaining a mail server, how you'll deal with viruses and spam, whether your ISP allows traffic to remote servers using SMTP port 25, among others.  There are a lot of threads about setting up mail servers in this forum.  I suggest reading through the ones that seem most relevant and trying what they suggest.

---

### Post by lisati on 2010-11-20
My basic setup has [LIST]
[*][Postfix]("https://help.ubuntu.com/community/Postfix") as the [MTA]("http://en.wikipedia.org/wiki/Mail_transfer_agent"), (useful for interacting with other mail servers)
[*][Dovecot]("https://help.ubuntu.com/community/Dovecot") as the [MDA]("http://en.wikipedia.org/wiki/Mail_delivery_agent"), (useful for connecting with email clients such as Evolution and Thunderbird)
[*][AmavisNew/ClamAV/Spamassassin]("https://help.ubuntu.com/community/PostfixAmavisNew") for assistance dealing with spam and malware, and 
[*]both Squirrelmail and Roundcube for webmail when I'm not using my own laptop for checking mail.
[/LIST]
In order to get the best out of Postfix, I needed to get a static IP from my ISP and ask them to unblock port 25. I also made several changes to the default configuration (e.g. use of DNSBL checking) to help reduce the amount of incoming spam.
Hope this provides some inspiration on your journey of figuring out what you need.

---

### Post by clay7 on 2010-11-20
I'll check those posts out. I forgot to mention that this is all on a dedicated, colocated server in a server warehouse, so port 25 (or others) should be open. Also, I'm fine with forwarding all mail to a gmail account, but I do need to send emails from the PHP code. Thanks!

---

### Post by lisati on 2010-11-20
There are a number of tutorials around for sending email via PHP. Which one suits you best can depend on your expectations, e.g. do you need users to fill out a form or are you just logging visits to a page?

Here are a couple of links to get you started, not necessarily in any order of preference or merit:
[http://www.webcheatsheet.com/PHP/send_email_text_html_attachment.php](http://www.webcheatsheet.com/PHP/send_email_text_html_attachment.php)
[http://email.about.com/od/emailprogrammingtips/qt/How_to_Send_Email_from_a_PHP_Script.htm](http://email.about.com/od/emailprogrammingtips/qt/How_to_Send_Email_from_a_PHP_Script.htm)
[http://www.daniweb.com/forums/thread38784.html](http://www.daniweb.com/forums/thread38784.html)

---

### Post by clay7 on 2010-11-20
Thanks lisati - my code definitely works because I've tested it on another server. My problem is that I have no mail software installed on my current server and therefore I can't send mail from a PHP script or from anywhere else. 

So, I'm trying to figure out (1) what needs to be done in order to let my PHP scripts send mail from the server, and (2) how I can setup a web-based email system on my server that I can log into to check and send emails. I should have made this more clear in my initial post--sorry.

---

### Post by SeijiSensei on 2010-11-22
Installing either postfix or sendmail in their default configurations is enough to enable you to send mail from PHP or the command line.  They're designed to listen on the localhost interface by default and not listen on any other interfaces without specific re-configuration to do so.

---

### Post by clay7 on 2010-11-22
just tried it...success!
Thank you!!

---

