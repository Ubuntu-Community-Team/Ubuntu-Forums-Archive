---
title: "sending mail via php"
date: 2007-07-02
forum: Server Platforms
---

### Post by LebowskiT1000 on 2007-07-02
Total noob here...

  I am trying to get the php mail() function to work.  I can see that it is returning a sucessful boolean value, but I never get any of the emails sent.

  This leads me to believe that the problem lies with sendmail (which I believe is the only MTA I have installed).  I am trying to get the mail to sent through our company's POP server, so I set the SMTP = pop.ourdomain.com and the Send_From = [email]help@domain.com[/email].  I've restarted apache and sendmail more times than I can count and I haven't had any success.

I've spent an inordinant amout of time and I'm sure it's some simple concept that I'm just not getting or not doing.  Any thoughts?

Also, it WAS logging the errors in /var/log/mail.log but I must have done something, because it doesn't seem to be logging them anymore (or perhaps they are going to a different file).

If someone could give me some hints on how to troubleshoot this, I'd be most appreciative.  Thanks.

---

### Post by LebowskiT1000 on 2007-07-03
Ok, I figured out how to fix the problem, but I do not understand what the root problem is.

It turns out that I MUST have a $header parameter in the mail function.

What I WAS doing:

[PHP]$to = 'user@domain.com';
$subject = 'subject goes here';
$body = 'body goes here';

$success = mail($to, $subject, $body);

var_dump($success);  //this was giving me true every time.
[/PHP]

SO...what I'm doing NOW:

[PHP]$to = 'user@domain.com';
$subject = 'subject goes here';
$body = 'body goes here';
$header = 'From: me@domain.com';
$params = '-fme@domain.com';

$success = mail($to, $subject, $body, $header, $params);

var_dump($success); //still gives me true but the message actually gets to my inbox this time.
[/PHP]

What is strange about this is that I have another server on the same network that is working just fine without the $header and $params variables.  BUT the big difference is that one is Ubuntu (the one failing) and Red Hat (the other server).

I also made sure to set all appropriate information in the php.ini file (even though it says for Win32 only).  So...I'm without an explanation.  Anyone want to enlighten me?

Thanks.

---

### Post by Mr. C. on 2007-07-03
PHP on *nix uses the sendmail binary, not SMTP.

Which MTA are you using ?  postfix?  exim ?  Sendmail ?

What were there error / log message you received previously ?

MrC

---

