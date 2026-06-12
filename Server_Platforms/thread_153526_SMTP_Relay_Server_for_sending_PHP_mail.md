---
title: "SMTP Relay Server for sending PHP mail"
date: 2006-04-01
forum: Server Platforms
---

### Post by amitroy5 on 2006-04-01
I have a PHP script which sends mail. It is an input form. Users input some data and after they click submit it should be emailed to me. However, this does not work because I have not installed any SMTP relay server.

I have searched here and google and typed numerous phrases. Unfortunately, I have had no luck finding a solution. How can I get my PHP-based forms to send to my email? Thanks!

---

### Post by gmclachl on 2006-04-01
sudo apt-get install postfix 

 should sort it, you  may* need to alter the php.ini file as well

 *I very much doubt you will

 George

---

### Post by amitroy5 on 2006-04-01
Should I install sendmail?

[QUOTE=gmclachl]sudo apt-get install postfix 

 should sort it, you  may* need to alter the php.ini file as well

 *I very much doubt you will

 George[/QUOTE]

[QUOTE=chuckyp]Make sure you have build-essential installed to take care of most common build environments.  Then look in the directory where you un tarred the package there should be a readme with directions.[/QUOTE]

---

### Post by gmclachl on 2006-04-01
Well if you really wanted to you could, I suppose. It's a matter of personal choice, I prefer postfix. Either way you need to install a MTA be it Sendmail, Postfix or Exim 

 George

---

### Post by amitroy5 on 2006-04-01
I'm right now installing postfix. Thanks for the suggestion. However, what would be an ideal mail name? It gives localhost.localdomain. Thanks!

---

### Post by amitroy5 on 2006-04-01
Thanks! I got it to work. However, whenever an email is sent, it always delivers to the bulk mail folder. What configuration should I do to prevent this? Thanks!

---

### Post by s7eam on 2006-04-01
[QUOTE=amitroy5]Thanks! I got it to work. However, whenever an email is sent, it always delivers to the bulk mail folder. What configuration should I do to prevent this? Thanks![/QUOTE]

It can depend on what headers you send.
Check out [http://se.php.net/manual/en/ref.mail.php](http://se.php.net/manual/en/ref.mail.php)

---

### Post by vsiege on 2008-02-28
amitroy5 and all, I too have a php file that needs to send email

if I choose postfix:
1. Do you make up your mail name(you had asked this but the response isnt there)?
2. did you have to change the php.ini file?

Im running 7.10

thanks for your help

---

