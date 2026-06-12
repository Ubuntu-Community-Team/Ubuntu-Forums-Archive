---
title: "Enabling mail to be sent from server."
date: 2012-01-18
forum: Server Platforms
---

### Post by tethlah on 2012-01-18
I'm using swift to send a forum submission from a website.  I installed php-mail and sendmail on the server so it can send emails.  I added this to my php.ini:
```
sendmail_path = /usr/bin/sendmail -t -i
```
As far as I know this is the only configuration I need to do right?  Here is my error from the form:
```

Fatal error: Uncaught exception 'Swift_TransportException' with message 
'Connection could not be established with host smtp.google.com [Connection timed out #110]' 
in /home/josh/swift/classes/Swift/Transport/StreamBuffer.php:266 Stack trace: #0 
/home/josh/swift/classes/Swift/Transport/StreamBuffer.php(66): 
Swift_Transport_StreamBuffer->_establishSocketConnection() #1 
/home/josh/swift/classes/Swift/Transport/AbstractSmtpTransport.php(117): 
Swift_Transport_StreamBuffer->initialize(Array) #2 /home/josh/swift/classes/Swift/Mailer.php(79): 
Swift_Transport_AbstractSmtpTransport->start() #3 
/var/www/default/live/public_html/contact.html(124): 
Swift_Mailer->send(Object(Swift_Message)) #4 {main} thrown in 
/home/josh/swift/classes/Swift/Transport/StreamBuffer.php on line 266

```
(I added some line-breaks to try to make it easier to read.

Now, When I use the php mail() function I get no errors, but I also get no email.  If there is a log file somewhere I need to supply please feel free to ask for it, I'm not sure if there is anything other than that error that will help.  Or am I just missing a step somewhere in setting up a lamp server to be able to send out emails?

Here is my code on the form if that helps (but I'm pretty sure it wont):
[PHP]
$transport=Swift_SmtpTransport::newInstance($formHost,465,'ssl')
	->setUsername($formUser)
	->setPassword($formPass)
;
$mailer=Swift_Mailer::newInstance($transport);
$message=Swift_Message::newInstance()
	->setSubject($subject)
	->setFrom(array('webmaster@205solutions.com'=>'205solutions Inquiry'))
	->setTo($to)
	->setBody($body)
;

$location = "failed.html";
if($mailer->send($message)){$location = "thanks.html";}
header("Location: ".$location);
[/PHP]
$forHost is just smtp.google.com
I'm kind of lost, maybe I'm not even asking the right question here, but maybe this is enough for someone to help me figure out where I'm going wrong.  I'm positive my code isn't the issue because it works on other servers, so I'm pretty sure it's just the way I have the server set up that's the problem.

Installed on this server):
LAMP and OpenSSH during initial installation.
(all using apt-get):
acls
phpmyadmin
vsftpd
php-mail
sendmail (with the line I put in the php.ini, otherwise it's set up defaulted the way it installs)

Do I have everything I need to have my server able to send emails from form submissions such as the one I demonstrated?

---

### Post by SeijiSensei on 2012-01-19
> 'Connection could not be established with host smtp.google.com [Connection timed out #110]'

Google is not accepting mail sent from your IP address. This is a common situation for people sending from residential connections.  Ask your ISP if you can relay mail through one of its mail servers.

---

