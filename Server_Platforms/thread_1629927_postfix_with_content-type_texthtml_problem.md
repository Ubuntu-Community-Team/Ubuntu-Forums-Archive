---
title: "postfix with content-type: text/html problem"
date: 2010-11-24
forum: Server Platforms
---

### Post by singying304 on 2010-11-24
I can only use plain text to send email via my postfix, how can I use html type to send email, is it something wrong? thanks in advance

---

### Post by SeijiSensei on 2010-11-24
Are you using a mail client like Evolution or Thunderbird?  Creating a MIME-encoded message with both plain text and HTML parts is pretty complex and not something I'd be able to do manually.

---

### Post by singying304 on 2010-11-25
> **SeijiSensei said:**
> Are you using a mail client like Evolution or Thunderbird?  Creating a MIME-encoded message with both plain text and HTML parts is pretty complex and not something I'd be able to do manually.
ya, I am using Thunderbird, there a some sample code which I write to test my postfix server, but even I use gmail to view the mail, I also can't view it in html form

I try to add these header:
$headers  = 'Content-type: text/html; charset=iso-8859-1' . "\r\n";
$headers .= 'From: Birthday Reminder <birthday@example.com>' . "\r\n";

the email can output as html form, but there are also somethings wrong such as
[IMG]http://free-space.dyndns.org/mail.png[/IMG]

can't see the sender's email and there are 
Message-Id: <[EMAIL="20101125070917.31830320842@www.as-usual.com"]20101125070917.31830320842@www.as-usual.com[/EMAIL]> Date: Thu, 25 Nov 2010 15:09:17 +0800 (HKT) <- I don't know why will have this sentence.



So, how can I send mail as HTML form that can show the sender mail?

---

### Post by SeijiSensei on 2010-11-25
Every message has a Message-ID.  Look at the structure of some of your own mail using "View > Message Source" in Thunderbird.

I don't know how you're constructing this message, PHP perhaps?  If so, are you placing the headers in the fourth field of the mail() function?  I'd also get rid of the "\r" characters; just use the newline character "\n".  You have to be careful with white space and empty lines in emails to insure that the headers are parsed correctly.

---

### Post by singying304 on 2010-11-25
> **SeijiSensei said:**
> Every message has a Message-ID.  Look at the structure of some of your own mail using "View > Message Source" in Thunderbird.

I don't know how you're constructing this message, PHP perhaps?  If so, are you placing the headers in the fourth field of the mail() function?  I'd also get rid of the "\r" characters; just use the newline character "\n".  You have to be careful with white space and empty lines in emails to insure that the headers are parsed correctly.
$headers = 'From: Birthday Reminder' ."\r\n";
$headers .= "Content-type: text/html; charset=iso-8859-1";
If I put the content-type below "from", it works.


$headers = "Content-type: text/html; charset=iso-8859-1" . "\r\n";
$headers .= 'From: Birthday Reminder' . "\r\n";
but if I put the content-type in the first line, it can't work!

---

