---
title: "Sending mail from server"
date: 2010-02-15
forum: Server Platforms
---

### Post by smeerbartje on 2010-02-15
Hi all, I have Ubuntu 9.04 running as my home server for downloading torrents, NZBs, samba, webserver, etc. Since my ISP does not offer static IP addresses, I want to setup a cronjon which emails the IP address every x hours.

I don't want my server to run a pop3 or smtp server, I just want to send email through my ISP's smtp server. Is this possible by default? And if not, how can I manage this?

---

### Post by jfparis on 2010-02-15
If you want to send an email you can:

**Use the mail capability of an advanced language**

You write a small script in python/php/per (or whatever else) but those three might be quicker as they provide high level libraries

**Set up your own mail server and use the mail command**

For example you install postfix. When prompted during the installation you choose "Internet with Smarthost". The smarthost will be your ISP smtp server.
I prefer the second option (more fun)

That being said this might not be the right option for you. You might want to setup a dyndns.org alias and use ddclient to update your IP when it changes. You will then be able to identify your machine from the internet by using youralias.dyndns.org and connect through http or ssh.

If you use dyndns you can still choose to install you own smtp server. You'll be able to manage your own email system and send email from the outside to [EMAIL="you@youralias.dyndns.org"]you@youralias.dyndns.org[/EMAIL]

Be careful not to configure the server as an [open relay]("http://en.wikipedia.org/wiki/Open_mail_relay") or you will be blacklisted.

---

### Post by ikehack on 2010-02-15
I agree with what jfparis said regarding scripts. Since you said you have your server setup assuming a bunch of different roles, one of which was a web server (during installation you chose LAMP I'm assuming), you may want to look into using PHP's mail() function to do your work. You see, PHP has a mail() function which is pretty straight-forward which you can use to send mail using your ISPs SMTP server, granted everything is setup correctly on the server side. Maybe if someone reads this they can help you with this. Or if you want to take a whack at it yourself, you can read up on PHP's mail() function from these links.

W3Schools: [PHP mail()]("http://www.w3schools.com/PHP/php_mail.asp")
PHP Manual: [mail() function]("http://php.net/manual/en/function.mail.php")

Hope this helps!

---

### Post by mbehamin on 2010-02-18
its simpler to use nail command. for instance 
[FONT=Courier New]nail -r "myaddress@something.com" -s "Some subject" -S smtp=some.smtp.server [EMAIL="info@company.com"]info@company.com[/EMAIL] < msg.txt[/FONT]

or you can permanently set the SMTP server in your ~/.mailrc file (or /etc/nail.rc if you want to set it system-wide), which removes the need for using the "-[FONT=Courier New]S smtp=[/FONT]..." option on the command-line:

[FONT=Courier New]set smtp=some.smtp.server[/FONT]

---

