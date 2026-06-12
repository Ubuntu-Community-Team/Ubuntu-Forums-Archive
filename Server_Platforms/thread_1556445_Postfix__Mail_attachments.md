---
title: "Postfix / Mail attachments"
date: 2010-08-19
forum: Server Platforms
---

### Post by kgatan on 2010-08-19
Hi,
 
I need a sollution for our business how our sales people should get their excel orders to a mysql database.
 
I thought the easiest way for them would be to send csv files by mail to a specific adress on a linux server with postfix.
 
Postfix would copy the attchments to a folder where a script would import them to mysql.
 
Is it possible to do this with postfix?
Where do you set rules for specific acounts and content in postfix?

---

### Post by nickzeff on 2010-10-04
Hi!

You can do this with Postfix. You need to set up a filter which is triggered when mail is received for a particular email address. This filter can pipe the email to a script which grabs the attachment and does whatever you want with it.

I wrote a post about it on my tech blog if you're interested. Let me know if it works for you.

Cheers

[http://tech.jeffri.es/2010/09/automatic-ripping-and-saving-email-attachments-with-postfix/](http://tech.jeffri.es/2010/09/automatic-ripping-and-saving-email-attachments-with-postfix/)

---

### Post by HermanAB on 2010-10-04
You can process the attachments with procmail - that is exactly what procmail is for obviously.  The procmail scripting language is however rather arcane, but it is extremely powerful.  Google for it, there are lots of tutorials online, there is also an old one on my web site I think.

---

### Post by SeijiSensei on 2010-10-04
An alternative approach might be to create a PHP interface on the MySQL server that your colleagues could use to upload the .csv files directly.  PHP has a built-in [CSV parser](http://php.net/manual/en/function.fgetcsv.php), and a complete set of functions to talk to MySQL.  If you go the e-mail route, you might want to look into having procmail pass the attachments to a PHP script as well.  Yet another method would be to run a PHP script periodically from cron and use its IMAP client functions to retrieve pending uploads from the destination mailbox and extract the attachments, then run the parser and upload the data to MySQL.

The procmailrc and procmailex man pages are pretty clear and helpful.  Procmailex presents various examples including ones to pass an e-mail message to a script.

---

### Post by kgatan on 2010-10-04
Thanks for all the feedback!

It seams the easiest way to do it is with procmail, fetchmail and metamail.

Guide,
[http://gimpel.ath.cx/howto_fetch_proc_metamail.html](http://gimpel.ath.cx/howto_fetch_proc_metamail.html)

SeijiSensei,
In my case its easier to automate it from excel.
An excel macro exports the file to csv and mails it to the pre set adress with a press of a button.
It also makes it a kind of offline solution since it will que the mails until the user has internet access.

The server retreives the csv files from the mail and stores them in a folder.
Ah scheduled script then imports them to MySQL.


Thanks a bunch all of you!

---

