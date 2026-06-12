---
title: "PHP mail() function not working on my server?"
date: 2009-08-06
forum: Server Platforms
---

### Post by SnowPunk98 on 2009-08-06
I am currently runningDebian Lenny and using Wordpress and am using the subscribe2 plugin which uses the PHP mail() function to send out Email when new posts are created. The problem is that Emails are not being sent out. 

I have posted on the subscribe2 website for help but the author is not sure why it is not working and suggests that it is a server configuration problem.

I have Apache, MySQL, PHP, etc working fine for everything else but this particular PHP mail() function isnt working. I have installed libphp-phpmailer and restarted Apache to try and fix the problem to no avail.

Can anyone tell me how I might be getting PHP mail() to work? I do not have sendmail or any SMTP server installed on my server.

---

### Post by HermanAB on 2009-08-06
Web server mail routines usually assume that you have a MTA installed.  Either install Postfix (hard) or install nullmailer (sooper simpel).  

You can find nullmailer with Google.  It only requires two configuration items: Who are you and where do you want the mail to go to.  You an use it to forward mail to your ISP mail server.

---

### Post by SnowPunk98 on 2009-08-15
This issue was caused by many things, in the end the main cause of this all was spam filtering and a lack of understanding of Exim. I ended up configuring Exim to use a smart host which resolved the issue.

---

