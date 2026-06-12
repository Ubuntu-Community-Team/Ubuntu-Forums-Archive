---
title: "How to send/recieve mail with postfix/sendmail?"
date: 2008-03-10
forum: Server Platforms
---

### Post by Scooter7 on 2008-03-10
Hi,

I have a Postfix/Sendmail configuration running on my Ubuntu 7.04 server box.   I can send mail with some php code, but what I want to do is send/recieve email using my email client (Thunderbird) with my server, as well as create new email accounts on my server.   How would I go about doing this?   I'm still new to mail servers.

Thanks in advance,

---

### Post by rapiscan on 2008-03-10
Do you already have a domain pointing to your server?  Is sendmail or postfix running?

If the above are true, you should now be able to send email [email]user@mydomain.com[/email].  To the best of my knowledge, both postfix and sendmail are Mail Transfer Agents.  So they both do the same job, and you only need one running.  The Mail Transfer Agent is responsible for accepting email and delivering it to the proper user's mail file.  

The mail file is located in the directory /var/mail/ .  You can check this directory and the corresponding files to see if your email tests are properly being received.  

You now need a different server to check your mail from an email client.  There are two protocols for checking email from a server: IMAP and POP3.  Read up on both protocols and decide which is best for you.  I believe dovecot is the standard IMAP/POP3 server for Ubuntu, so once you get this running and properly configured you will be able to check your email using your preferred protocol.

---

### Post by Scooter7 on 2008-03-10
Sorry, my bad.   I think I have Postfix and Dovecot, I was confusing Sendmail with Dovecot...

I have multiple domains pointing to my server, as I host a variety of sites for people I know.

My problem is that when I send an email using my mail client, I get an email back with an error saying something about relaying for the gmail server (I've been sending my test emails from my server to my gmail account).

I'll try again though.   If you have any idea as to why I'm having the problem, please share, it'd be appreciated.

Edit: I tried sending a test email from one of my gmail accounts to my server, and I got this error message back:

> This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

     [email]vertimyst@darknet-fusion.co.cc[/email]

Technical details of permanent failure: 
PERM_FAILURE: SMTP Error (state 13): 554 5.7.1 <vertimyst@darknet-fusion.co.cc>: Relay access denied

Sending a test email from my server to my gmail account gives me a similar error:

> An error occured while sending mail.   The mail server responded: 5.7.1 <vertimyst@gmail.com>:
Relay access denied.   Please check the recipients and try again.

I can, however, send email from my server using this php code:

```
<?php
$to = "recipient@example.com";
$subject = "Hi!";
$body = "Hi,\n\nHow are you?";
if (mail($to, $subject, $body)) {
  echo("<p>Message successfully sent!</p>");
 } else {
  echo("<p>Message delivery failed...</p>");
 }
?>
```

---

### Post by Mr. C. on 2008-03-11
Gmail requires authentication to relay email from your server.  See the two posts here:

[[deleted]]([deleted])

---

### Post by Scooter7 on 2008-03-11
Your link doesn't work, it says there's no matches.

---

### Post by Mr. C. on 2008-03-11
Sorry, I didn't realize the search returned short-lived links.  Try these two posts :

[http://ubuntuforums.org/showthread.php?t=711512&highlight=google+mail+authentication](http://ubuntuforums.org/showthread.php?t=711512&highlight=google+mail+authentication) 
[http://ubuntuforums.org/showthread.php?t=507417&highlight=gmail+mrc+authentication](http://ubuntuforums.org/showthread.php?t=507417&highlight=gmail+mrc+authentication)

---

