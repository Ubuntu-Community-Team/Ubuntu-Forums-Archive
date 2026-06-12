---
title: "How to send outgoing emails only...through another server"
date: 2008-09-04
forum: Server Platforms
---

### Post by a.thomas on 2008-09-04
I am migrating numerous websites from a Windows Server to an Ubuntu Hardy Server. I can't seem to get the PHP mail() function to work with my setup.

Here is my setup:
I have an Ubuntu Hardy server running LAMP. 
This server does not have a domain name, just a static IP from an ISP.

I have a Windows machine that handles the SMTP email sending and receiving from our ISP. It basically just routes the emails to my users.

So here is what I want to do:
I want to send emails out using PHP's mail() function in my web pages. I have numerous forms that send out emails based on events and submissions.
I am NOT using the Ubuntu server to receive email, I just want it to send emails to the outside world. I don't want to send emails out using the Ubuntu server, I want them to be sent using my domain name (whatever.com). I believe this should be done through my SMTP server. So I would have to connect to 192.168.0.1 on port 25 and provide username and password. Then this will send the emails?

I have attempted to use Exim4 but not luck. I have looked at postfix an it seems to be robust for my needs and sendmail seems complicated.

I am new to email and a novice on Ubuntu so I may be way out of where I need to be.
I am new to this so if I didn't explain it well, ask me some questions and I will try to explain more.

Please any suggestions or help is greatly appreciated!

Thanks!

---

### Post by schettj on 2008-09-04
Use 
```

include("Mail.php");
$recipients = "thatguy@over.there.com";

$headers["From"]    = "whatever@your.domain.com";
$headers["To"]      = $recipients;
$headers["Subject"] = "This is the subject";

$body = "The Body";

$params["host"] = "my.mailhost.com";
$params["port"] = "25";
$params["auth"] = true;
$params["username"] = "username";
$params["password"] = "password";

// Create the mail object using the Mail::factory method
$mail_object =& Mail::factory("smtp", $params);

$mail_object->send($recipients, $headers, $body);
```
(In other words, do the right thing in PHP - otherwise you'll have to have sendmail installed and configured correctly to relay outgoing mail, and even then it won't work if the other server doesn't allow you to relay)

---

### Post by windependence on 2008-09-04
Well he could drop in Postfix and php will use that just like sendmail, but of course you are still correct, it will have to be configured right (not difficult for this) so that mail isn't rejected. I have several message boards using this and I get no rejections, but of course I have the domain, static IP, and PTR set up correctly.

-Tim

---

### Post by schettj on 2008-09-04
Yep, I use postfix as well on my content-server machine, but I also own/run the smtp machine, so its set up to relay correctly. If I were trying to relay through my ISP, I'm not sure it would work without auth. If you want to do that kinda stuff from within PHP its easy enough (as shown above) to just send the mail directly via the desire smtp server.

---

### Post by windependence on 2008-09-04
Yeah my mail goes directly out and isn't relayed through another smtp sever. I could never see the point of that. I mean, if you are gonna do that why have an e-mail server at all?

-Tim

---

### Post by a.thomas on 2008-09-04
> **schettj said:**
> Use 
```

include("Mail.php");
$recipients = "thatguy@over.there.com";

$headers["From"]    = "whatever@your.domain.com";
$headers["To"]      = $recipients;
$headers["Subject"] = "This is the subject";

$body = "The Body";

$params["host"] = "my.mailhost.com";
$params["port"] = "25";
$params["auth"] = true;
$params["username"] = "username";
$params["password"] = "password";

// Create the mail object using the Mail::factory method
$mail_object =& Mail::factory("smtp", $params);

$mail_object->send($recipients, $headers, $body);
```
(In other words, do the right thing in PHP - otherwise you'll have to have sendmail installed and configured correctly to relay outgoing mail, and even then it won't work if the other server doesn't allow you to relay)

OK I am trying to understand...where/what is "Mail.php"? 
EDIT: I'm sorry I forgot it was part of the PEAR mail package... whoa I feel dumb. 

I am trying to use this "Mail.php" class but am not having any luck.

I use something similar to this now...
[PHP]
//define the receivers of the email
$to = "thatguy@over.there.com";
//define the subject of the email
$subject = "This is the subject";
//define the headers to be passed. Note that they are separated with \r\n
$headers  = "From: whatever@your.domain.comm\r\n";
//define the body of the message.	
$message = "The Body";
//send the email
$mail_sent = @mail($to, $subject, $message, $headers);
[/PHP]

This looks similar to what you are explaining. Could you elaborate?

---

### Post by HermanAB on 2008-09-04
Use nullmailer.

Cheers,

Herman

---

### Post by a.thomas on 2008-09-04
> **HermanAB said:**
> Use nullmailer.

Cheers,

Herman

How will this help if Exim4 doesn't work?

---

### Post by HermanAB on 2008-09-04
Use nullmailer to forward email to your ISP mail server.  It is very easy to configure - it only does mail forwarding and is designed for exactly what you want to do.

---

### Post by a.thomas on 2008-09-04
Have any examples or guides you can share?

---

### Post by a.thomas on 2008-09-05
So I have nullmailer working and sending emails

The /var/log/mail.log
```
Sep  5 09:33:01 web nullmailer[10578]: Trigger pulled.
Sep  5 09:33:01 web nullmailer[10578]: Rescanning queue.
Sep  5 09:33:01 web nullmailer[10578]: Starting delivery, 22 message(s) in queue.
Sep  5 09:33:01 web nullmailer[10578]: Starting delivery: protocol: smtp host: 192.168.0.1 file: 1220621221.11867
Sep  5 09:33:01 web nullmailer[12416]: smtp: Failed: 550 root@web.web... Relaying denied
Sep  5 09:33:01 web nullmailer[10578]: Sending failed:  Permanent error in sending the message

```

This is repeated over and over...
also the same thing is in /var/log/mail.err

I am trying to send to multiple recipients but am not having any luck. Can someone point me in the direction for examples of using nullmailer? I am using PHP mail() like this:
[PHP]//define the receivers of the email
$to = "thatguy@over.there.com";
//define the subject of the email
$subject = "This is the subject";
//define the headers to be passed. Note that they are separated with \r\n
$headers  = "From: whatever@your.domain.comm\r\n";
//define the body of the message.    
$message = "The Body";
//send the email
$mail_sent = @mail($to, $subject, $message, $headers);  [/PHP]

---

