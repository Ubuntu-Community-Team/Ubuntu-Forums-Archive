---
title: "PHP Mail() Won't Send"
date: 2009-05-04
forum: Server Platforms
---

### Post by jwwaldschmidt on 2009-05-04
I'm in the process of learning PHP (on my personal home web server), and I'm trying to get a contact form on my web server to send an email. I've got it to where the confirmation page will show, but no email ever arrives.

I've attempted to setup php-mail & php-net-smtp per [this guide]("http://ubuntuforums.org/showthread.php?t=258140"), but I've had no success at getting it working, as of yet. What do I need to do to get a functioning php contact form, that can actually send my message?

The address of the form is [jwphptest.homeip.net/report.html]("http://jwphptest.homeip.net/report.html") (It's a guide out of the Head's First PHP & MySql book)

Thanks for your help.

---

### Post by AlexDudko on 2009-05-04
Unfortunately I can't check that "guide" at the moment, but I always configured a mail server to be able to use this function.

---

### Post by nquinnathome1 on 2009-05-05
To send mail with PHP you'll need to setup a mail server on the server to handle mail; if you're using the 9.04 release you can use the dovecot-postfix package which takes most of the hard work away; search the forums for the package if you get stuck, but it's installed with
```
apt-get install dovecot-postfix
```

You can then check your mail server is running:
```

telnet localhost 25

```

If telnet connects, you've got a mail server installed and running; you will need to find proper guides for Postfix and Dovecot to understand what they are and how they work (try the Ubuntu help)

---

### Post by dldeskins on 2009-05-05
> **jwwaldschmidt said:**
> I'm in the process of learning PHP (on my personal home web server), and I'm trying to get a contact form on my web server to send an email. I've got it to where the confirmation page will show, but no email ever arrives.

I've attempted to setup php-mail & php-net-smtp per [this guide]("http://ubuntuforums.org/showthread.php?t=258140"), but I've had no success at getting it working, as of yet. What do I need to do to get a functioning php contact form, that can actually send my message?

The address of the form is [jwphptest.homeip.net/report.html]("http://jwphptest.homeip.net/report.html") (It's a guide out of the Head's First PHP & MySql book)

Thanks for your help.

I am assuming that you have a web form that you want to mail through.  If this is the case, use PHPMailer.
[http://phpmailer.codeworxtech.com/index.php?pg=sf&p=dl](http://phpmailer.codeworxtech.com/index.php?pg=sf&p=dl)

I have always had trouble with PHP Mail.  It gives no error and can change from server to server, and version to version. PHPMailer allows you to connect to an SMTP server (gmail, etc) with a regular email account and email a normal email.

Hopes this helps.

---

### Post by m3bik on 2009-05-05
You might want to make sure your IP is not listed at [http://www.spamhaus.org/pbl/index.lasso](http://www.spamhaus.org/pbl/index.lasso)

Most IP addresses assigned by an ISP do appear on that list because they should not be sending mail... Check out that site for more information.

I had this problem, so I just created a gmail.com account just for my webserver. When it tries to send mail, it connects through SMTP to smtp.gmail.com instead of just trying to send the mail itself. Works fine.

---

### Post by Kareeser on 2009-05-06
Either installing postfix, like the above poster mentioned, or simply, "sendmail". Both work.

And yes, your ISP may be blocking your SMTP port (23, I think?) to curb zombie machines. If that is the case, you may want to call in and see if they can make an exception for you.

---

### Post by nquinnathome1 on 2009-05-07
> **Kareeser said:**
> ...SMTP port (23, I think?)...

It's port 25 :)

---

### Post by Kareeser on 2009-05-08
Right, 23 is telnet.

---

### Post by rsuresh on 2009-05-15
hai  i need to know the  procedure  for  sending mails  through  a php  mail function  in linux.


and also  i need to know the changes to apply on the php.ini  file  .

can any one help me please  .

thank you in advance

---

### Post by AlexDudko on 2009-05-15
> **rsuresh said:**
> hai  i need to know the  procedure  for  sending mails  through  a php  mail function  in linux.


and also  i need to know the changes to apply on the php.ini  file  .

can any one help me please  .

thank you in advance


Perhaps, this link would be useful for you: [http://www.php.net/manual/en/function.mail.php]("http://www.php.net/manual/en/function.mail.php")

---

### Post by graphius on 2009-06-15
I was having nothing but problems sending email from my local server until I happened across ssmtp. It is in the repositories so:
 > sudo apt-get install ssmtp.
then restart the webserver
> sudo /etc/init.d/apache2 restart
and everything now works. :D

---

### Post by dbyrd on 2009-09-26
I already had an smtp mail provider on a domain I had purchased from godaddy so I used that smtp server address to send my mail. You can use PHPMailer with Gmail too, but I haven't tried it. 

This worked for me. I believe you can find PHPMailer in Synaptic. 

If you can't find PHPMailer in Synaptic the install is easy. Download it from sourceforge, extract the files. Copy the extracted folder to the PHP include folder. (If you're a minimalist just copy the two required class definition files (two .php files). Track down your PHP.ini file probably in /etc/php and read it to find the location of your PHP include folder. You'll see the folder listed as the include directory or similar. The PHPMailer "read me" file will tell you all this. 

If you use synaptic to install PHPMailer then just start mailing as this all will be setup for you. Here's an example of how to send mail from your PC with PHP using PHPMailer. (BTW if you like PHPMailer please donate some money to the author of the freeware. He is doing all of us a huge favor.)
<?php
**require("class.phpmailer.php");**

**$mail = new PHPMailer();**

$mail->IsSMTP();                      // set mailer to use SMTP
$mail->Host = "smtp.mydomain.com";  // specify main and backup server
$mail->SMTPAuth = true;             // turn on SMTP authentication
$mail->Username = "user@mydomain.com";  // SMTP username
$mail->Password = "secretpassword"; // SMTP password

$mail->From = "user@mydomain.com";
$mail->FromName = "Fname Lname or whatever";
$mail->AddAddress("somebody@somewhere.com", "Somebody's Name");
//$mail->AddAddress("ellen@example.com");                  // name is optional
$mail->WordWrap = 50;                                 // set word wrap to 50 characters
//$mail->AddAttachment("/var/tmp/file.tar.gz");         // add attachments
//$mail->AddAttachment("/tmp/image.jpg", "new.jpg");    // optional name
$mail->IsHTML(true);                                  // set email format to HTML

$mail->Subject = "Yea Mail Works";
// The body is typically passed in a variable, but this is a simple example
// $mail->Body = $myMsgBody;
$mail->Body    = "Hello Bob;<br />Getting the email setup was easier than I imagined.<br /> This is the HTML message body <b>in bold!</b> <br />";
$mail->AltBody = "Hello Bob;/nThis is the body in plain text for non-HTML mail clients";

if(!$mail->Send())
{
   echo "Message could not be sent. <p>";
   echo "Mailer Error: " . $mail->ErrorInfo;
   exit;
}

echo "Message has been sent";
?>

Once you get your test going naturally you'll want to create a function or class where you can pass a few variables to send emails.

Good luck.

---

