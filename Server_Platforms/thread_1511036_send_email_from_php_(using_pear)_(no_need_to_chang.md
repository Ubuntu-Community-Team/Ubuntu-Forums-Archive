---
title: "send email from php (using pear) (no need to change php.ini)"
date: 2010-06-16
forum: Server Platforms
---

### Post by rhythmiccycle on 2010-06-16
I host a webpage from my PC, and I was having all kinds of issues trying to get it to send e-mails

note: these steps send and receive the email through a gmail account. 

[this]("http://www.developer.com/open/article.php/10930_3782831_1/Sending-Email-with-PHP.htm") page saved me.

here are the simple steps

0. get a gmail account

1. install pear
```
sudo apt-get install php-pear
```

2. install pear packages: 
(i'm not really sure what this does, but I did it, and everything is working)
```
sudo pear install -o Mail
sudo pear install -o Net_SMTP
```

3. run php script to send email.

```

<?php

   // Include the Mail package
   require "Mail.php";

   // Identify the sender, recipient, mail subject, and body
   $sender    = "wj@wjgilmore.com";
   $recipient = "jason@example.com";
   $subject   = "Thank you for your email!";
   $body      = "I'll get back to you as soon as I can!";

   // Identify the mail server, username, password, and port
   $server   = "ssl://smtp.gmail.com";
   $username = "wj@wjgilmore.com";
   $password = "supersecret";
   $port     = "465";

   // Set up the mail headers
   $headers = array(
      "From"    => $sender,
      "To"      => $recipient,
      "Subject" => $subject
   );

   // Configure the mailer mechanism
   $smtp = Mail::factory("smtp",
      array(
        "host"     => $server,
        "username" => $username,
        "password" => $password,
        "auth"     => true,
        "port"     => 465
      )
   );

   // Send the message
   $mail = $smtp->send($recipient, $headers, $body);

   if (PEAR::isError($mail)) {
      echo ($mail->getMessage());
   }

?>

```

I hope people find this post useful

---

### Post by AboveTheLogic on 2010-06-16
Thanks for the info. I've followed those instructions but am getting the following error:
```
Failed to connect to ssl://smtp.<mydomain>.net:465 [SMTP: Failed to connect socket: fsockopen() [function.fsockopen]: unable to connect to ssl://smtp.<mydomain>.net:465 (Unknown error) (code: -1, response: )]
```

This is on Ubuntu Linux Server 9.10, trying to send mail through Exchange 2007 which is on the same LAN, no firewall or connectivity issues. I can telnet to the mail server just fine.

I've been battling this off and on for the past couple of weeks and haven't quite found my solution yet.

Perhaps I'm better off to start my own thread, but I think this is the closest I've been to getting it to work.

See attachment for exchange server security settings. If anyone has any ideas I'd love to hear them! I'm almost ready to move web services over to windows in an attempt to get phpmail() to work, but I really don't want to!!!

---

### Post by rhythmiccycle on 2010-07-23
> **AboveTheLogic said:**
> 
This is on Ubuntu Linux Server 9.10, trying to send mail through Exchange 2007 which is on the same LAN, no firewall or connectivity issues. I can telnet to the mail server just fine.


sorry for taking so long to reply. 

These steps are to send an receive emails from a gmail account not on a local host or LAN or Exchange or anything like that. I just changed the initial post; I should have been more clear to begin with. 

I'm not sure how to do what you are trying to do. I wanted to send automated emails, and I tried all types of stuff, and this way was the only way I could get to work.

---

### Post by AboveTheLogic on 2010-07-23
i ended up making a custom connector in exchange on an alternate port that is only accessible from the LAN and only accepts connections from the web server

the receive connector does not require encryption and works just fine with pear

---

### Post by rhythmiccycle on 2010-07-23
> **AboveTheLogic said:**
> i ended up making a custom connector in exchange on an alternate port that is only accessible from the LAN and only accepts connections from the web server

the receive connector does not require encryption and works just fine with pear

I'm glad to hear you got it to work.

 I just started using pear, I'm also using it to run a message board on my site. pear is pretty neat, but I don't know much about it, I just cut and past sample code and change things here and there.

---

