---
title: "Help with Postfix to send mail via php's mail() function?"
date: 2009-10-10
forum: Server Platforms
---

### Post by pavsid on 2009-10-10
Hi, ive been trying for the past several hours to get this to work but can't get anywhere.

I've followed the tutorial [https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix") right down to where it says;

" Next edit /etc/postfix/sasl/smtpd.conf and add the following lines: "

..but that file doesn't exist on my system, the folder does, but not the file!

Anyway, all i want to do is send emails off my server (Ubuntu Server 9.04) via PHP's mail() function.

mail() returns TRUE now that i've installed Postfix (it didn't before) but still no emails being received..

Can anybody help?

---

### Post by jph989 on 2009-10-10
I had the same problem
[http://ubuntuforums.org/showthread.php?t=1287753](http://ubuntuforums.org/showthread.php?t=1287753)
let me know if you work this out

JPH

---

### Post by t3r0 on 2009-10-10
> **pavsid said:**
> 
Can anybody help?

Hi,

Please tell a little bit more about your setup there. Is postfix configured to be a relay or a standalone mail server? are you behind a firewall? is this a home server setup or a server in some DC? if a home server, is your ISP blocking smtp? 

if the server is connected directly to internet with a public IP, then is there anything in your mail logs? 


- Tero

---

### Post by pavsid on 2009-10-10
> **t3r0 said:**
> Hi,

Please tell a little bit more about your setup there. Is postfix configured to be a relay or a standalone mail server? are you behind a firewall? is this a home server setup or a server in some DC? if a home server, is your ISP blocking smtp? 

if the server is connected directly to internet with a public IP, then is there anything in your mail logs? 


- Tero

Hi, i believe postfix is set up to be standalone server but how do i check this? i wasn't given the option on install?

Its my home server, and it's connected to the internet via a router, i have forwarded port 25 for TCP/UDP but still nothing - would that even make a difference if it's just outbound?

ISP isn't blocking port 25 afaik - i can send mail from a mail client on a pc on the network using port 25 anyway

thanks for your help

---

### Post by Bachstelze on 2009-10-10
Is your IP static or dynamic? Most mail servers will refuse mail coming from dynamic IPs as an anti-spam measure.

---

### Post by pavsid on 2009-10-10
Hi, its a static address, but i'm not trying to receive mail, i just want to send it!!

---

### Post by pavsid on 2009-10-11
Hi, on checking my mail.log file, i'm getting this every time i try to send a mail via php's mail() function:

```


Oct 11 13:42:57 ubuntuserver postfix/pickup[32274]: 65C5026C2FE: uid=33 from=<www-data>
Oct 11 13:42:57 ubuntuserver postfix/cleanup[525]: 65C5026C2FE: message-id=<20091011124257.65C5026C2FE@ubuntuserver>
Oct 11 13:42:57 ubuntuserver postfix/qmgr[10924]: 65C5026C2FE: from=<www-data@ubuntuserver>, size=1085, nrcpt=1 (queue active)
Oct 11 13:42:57 ubuntuserver postfix/smtp[527]: 65C5026C2FE: to=<myemail@address.com>, relay=mf4.spamfiltering.com[72.249.26.240]:25, delay=0.51, delays=0.07/0.01/0.42/0, dsn=4.0.0, status=deferred (host mf4.spamfiltering.com[72.249.26.240] refused to talk to me: 554 Rejected due to listing on http://www.spamhaus.org/zen/)

```

Why is it being relayed through spamfiltering.com? I'm guessing its working ok, but being rejected as spam somewhere along the path? how do i change this?

---

### Post by pavsid on 2009-10-11
Ah ha!

```
Outbound Email Policy of The Spamhaus Project for this IP range:

This IP range has been identified by Spamhaus as not meeting our policy for IPs permitted to deliver unauthenticated 'direct-to-mx' email to PBL users.

Important: If you are using any normal email software (such as Outlook, Entourage, Thunderbird, Apple Mail, etc.) and you are being blocked by this Spamhaus PBL listing when you try to send email, the reason is simply that you need to turn on "SMTP Authentication" in your email program settings. For help with SMTP Authentication or ways to quickly fix this problem click here.

See also: http://www.spamhaus.org/faq/answers.lasso?section=Spamhaus%20PBL
```

---

### Post by Bachstelze on 2009-10-11
> **pavsid said:**
> Hi, its a static address, but i'm not trying to receive mail, i just want to send it!!

When you send it, another server receives it. ;) Anyway, does your ISP have a SMTP server you can use to send mail?

---

### Post by pavsid on 2009-10-11
> **Bachstelze said:**
> When you send it, another server receives it. ;) Anyway, does your ISP have a SMTP server you can use to send mail?

Yes it does, am i best going down that route?

Today, i enabled sasl on my home server, tls certificates, smtp auth - the bleeding lot, but still came up with the same error when trying to send.

---

### Post by Bachstelze on 2009-10-11
> **pavsid said:**
> Yes it does, am i best going down that route?

Yeah, you can use ssmtp for this.

---

### Post by rnodal on 2009-10-13
Do you have a proper MX DNS record setup? 
The destination email server is treating your email as spam.

I don't think it would be smart to accept email from user@host and you seem
to be sending emails from www-data@ubuntuserver. Unless you replaced the actual domain name with ubuntuserver because of privacy.

-r

---

### Post by pavsid on 2009-10-15
> **rnodal said:**
> Do you have a proper MX DNS record setup? 
The destination email server is treating your email as spam.

I don't think it would be smart to accept email from user@host and you seem
to be sending emails from www-data@ubuntuserver. Unless you replaced the actual domain name with ubuntuserver because of privacy.

-r

No i don't, didn't realise i'd have to do that in order to send mail via php, but that makes complete sense now. Thanks, i'll go do some more reading....!

****EDIT****

Actually, i do have an MX DNS record set up. I have a subdomain through DynDNS and where you see www-data@ubuntuserver above it's actually sending off [email]www-data@xxxxx.gotdns.com[/email]  - i forgot i changed it to ubuntuserver above

Does that make the problem any clearer??!

---

### Post by pavsid on 2009-10-15
Ok, i've just tried sending a mail to a googlemail address and it worked! Albeit it went into my spam folder.

How can i get it to work on other email addresses? Is it still to do with this SMTP Authentication?

Please help!!

---

### Post by rnodal on 2009-10-15
> **pavsid said:**
> Ok, i've just tried sending a mail to a googlemail address and it worked! Albeit it went into my spam folder.

How can i get it to work on other email addresses? Is it still to do with this SMTP Authentication?

Please help!!

You will need to post the error logs to see why would the other email server not accept your connection. 

Here is a link to perform a couple of email server tests.

[http://www.mxtoolbox.com/](http://www.mxtoolbox.com/)

Check that you are not in a spam database. 

-r

---

### Post by AlexanderDGreat on 2009-10-16
> **pavsid said:**
> Anyway, all i want to do is send emails off my server (Ubuntu Server 9.04) via PHP's mail() function.

Hi, PHP's mail() function is horrible on my Ubuntu 9.04, I'm testing my email form on my local machine and it doesn't send everytime. I've tried, SendMail, Postfix, read a bunch of tutorials, it all failed for me. If you want to save yourself of headaches and waster hours, just download PHPMailer.

Go to this website: [http://phpmailer.worxware.com/](http://phpmailer.worxware.com/)

Download the one at the bottom: PHPMailer for PHP5/6

Then download: PHPMailer v2.3 for PHP5_6

After extracting the folder just rename it to phpMailer (take out the version no. for simplicity's sake). Cut and Paste the extracted phpMailer folder in your includes folder in your website, or what have you. Test the program, make a file sendmail.php and paste the following:


<?php
//mail($to, $subject, $message, $headers);

//Since phpMailer is OOP, we need to initialize the class - for the variables and methods
require_once("includes/phpMailer/class.phpmailer.php");

//PhpMailer has its own SMTP function, this is the magic formula
require_once("includes/phpMailer/class.smtp.php");

//Finally, we need a language for the program, it's stated in the README file
require_once("includes/phpMailer/language/phpmailer.lang-en.php"); 

//Setup the variables
$to_name = "MyFriend";
$to = "myfriendsemail@domain.com";
$subject = "Test Mail";
$message = "This is a test.";
$from_name = "MyName";
$from = "myemail@domain.com";

//Now, let's use it's Class and Methods
$mail = new PHPMailer();
$mail->IsSMTP();
$mail->Host     = "mail.domain.com";
$mail->Port     = 25;
$mail->SMTPAuth = true;
$mail->Username = "username";
$mail->Password = "secretpasswd";
$mail->FromName = $from_name;
$mail->From     = $from;
$mail->AddAddress($to, $to_name);
$mail->Subject  = $subject;
$mail->Body     = $message;

//Finally we send
$result = $mail->Send();
echo $result ? 'Sent' : 'Error';
?>

And there you go!

PS Don't forget to set your permissions of the "phpMailer" folder and the "language" folder inside it, to allow (read and execute) by "others" since www-data is defined as "others".

PPS All Credits go to Kevin Skoglund's PHP Beyond The Basics Tutorial available at Lynda.com or Amazon.com

---

### Post by rnodal on 2009-10-17
> **AlexanderDGreat said:**
> Hi, PHP's mail() function is horrible on my Ubuntu 9.04, I'm testing my email form on my local machine and it doesn't send everytime.

PHP mail function is just fine. The problem is that your ISP is probably blocking your outgoing email. 

What you have installed is a PHP client that will connect to an email server that then will relay your email.

You could have installed the package ssmtp (I believe that's the name but don't quote me on that) that allows you to configure it the same you have configured the PHP client but you will have the benefit that you could then use the regular php mail function as expected.

-r

---

### Post by AlexanderDGreat on 2009-10-17
Actually, I can send email from Evolution, using port 25, so I guess my ISP is not blocking that port. So my confusion arised when I CAN'T SEND email from a PHP script. I configured my PHP.INI:

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = sendmail -t -i

I installed sendmail with this. I've also tried postfix. By this point, I assumed the problem is on how my machine handles SMTP. Luckily, PHPMailer will not rely on my local machine's SMTP settings. After I installed PHPMailer, I was able to send email right away. Anyway, thanks for the ssmtp info, I'll also try that.

---

### Post by AlexanderDGreat on 2009-10-17
@rnodal - How do you use ssmtp? I found it in the Synaptics Package Manager.

---

### Post by rnodal on 2009-10-17
> **AlexanderDGreat said:**
> @rnodal - How do you use ssmtp? I found it in the Synaptics Package Manager.

This is from the top of my head.

Install the package, sudo apt-get install ssmtp.

Then you just configure it. I believe that there are two files that you need to configure but I cannot remember. If you look at the files that come with the package then you will see which files. If you do a google search on ssmtp I'm ptetty sure you will find a guide on how to do it.

Back to ISP. Your ISP does not block you from connecting to another server to send email via that server but when your machine tries to deliver email with your MTA then it blocks that. I'm not a networking expert so my explanation is very simple. But there is a difference between your machine connecting to a server so it accepts an email from your machine and your machine connecting to a server and request that server to send an email for you.

-r

---

