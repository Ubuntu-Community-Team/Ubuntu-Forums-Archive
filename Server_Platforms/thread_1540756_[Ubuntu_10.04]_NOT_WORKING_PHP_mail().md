---
title: "[Ubuntu 10.04] NOT WORKING: PHP mail()"
date: 2010-07-28
forum: Server Platforms
---

### Post by senuxis on 2010-07-28
PHP mail() is not working for me. Please help.

---

### Post by cdenley on 2010-07-28
Not working how? Does the function give you a warning or error? Does it complete, but the e-mail not get sent?

---

### Post by ruffEdgz on 2010-07-28
I'm sorry to hear that PHP mail isn't working but the more information you can give, the better the diagnoses.

Here are some questions you can answer to help figure out this issue:
- Did you check your logs in /var/log/apache2/error.log?
- Can you show use how the php mail function is set up?
- Are you trying to run this as a web application or on the machine itself (cronjob, etc...)

Those are all the ones I can think of off the top of my head.

Thanks!

---

### Post by cdenley on 2010-07-28
Also, does sendmail work? Replace the bold text with your e-mail.
```

dpkg-query -S */sendmail
echo -e "To: **you@youremail.com**\nSubject: test\n\nthis is a test\n"|sendmail -t
tail /var/log/mail.log

```

---

### Post by senuxis on 2010-07-28
This is what I'm trying to do:

[PHP]$message .= "<h1 class='message'>You have successfully made your booking
            Your order number is:</h1>";
            $message .= "<br>";
            $message .= "<span class='order_no'>" . $form->order_number() . "</span>";

            $to = $_SESSION['volunteer']['email'];
            $subject = "St. Tom's Ambulance: You have successfully made your booking";
            $headers  = 'MIME-Version: 1.0' . "\r\n";
            $headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";

            if(mail($to, $subject, $message, $headers)){
                $message .= "<h2 class='message'>An email has been sent to:</h2>";
                $message .= "<span class='order_no'>" . $to . "</span>";
            }[/PHP]

This code works with Mac OS X.

@cdenley - This is result of those commands:

> Jul 28 17:38:15 ubuntu sendmail[2856]: My unqualified host name (ubuntu) unknown; sleeping for retry
Jul 28 17:39:15 ubuntu sendmail[2856]: unable to qualify my own domain name (ubuntu) -- using short name
Jul 28 17:39:16 ubuntu sendmail[2856]: alias database /etc/mail/aliases rebuilt by root
Jul 28 17:39:16 ubuntu sendmail[2856]: /etc/mail/aliases: 4 aliases, longest 10 bytes, 66 bytes total
Jul 28 17:39:16 ubuntu sm-mta[2933]: My unqualified host name (ubuntu) unknown; sleeping for retry
Jul 28 17:39:18 ubuntu sm-msp-queue[2938]: My unqualified host name (ubuntu) unknown; sleeping for retry
Jul 28 17:40:01 ubuntu sm-msp-queue[2956]: My unqualified host name (ubuntu) unknown; sleeping for retry
Jul 28 17:40:16 ubuntu sm-mta[2933]: unable to qualify my own domain name (ubuntu) -- using short name
Jul 28 17:40:16 ubuntu sm-mta[2957]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Jul 28 17:40:18 ubuntu sm-msp-queue[2938]: unable to qualify my own domain name (ubuntu) -- using short name
Jul 28 17:40:29 ubuntu sendmail[2975]: My unqualified host name (ubuntu) unknown; sleeping for retry
Jul 28 17:41:01 ubuntu sm-msp-queue[2956]: unable to qualify my own domain name (ubuntu) -- using short name
Jul 28 17:41:29 ubuntu sendmail[2975]: unable to qualify my own domain name (ubuntu) -- using short name
Jul 28 17:41:30 ubuntu sendmail[2975]: o6SGfT2L002975: from=tunji, size=53, class=0, nrcpts=1, msgid=<201007281641.o6SGfT2L002975@ubuntu>, relay=tunji@localhost
Jul 28 17:41:30 ubuntu sm-mta[2977]: o6SGfUfN002977: from=<tunji@ubuntu>, size=296, class=0, nrcpts=1, msgid=<201007281641.o6SGfT2L002975@ubuntu>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Jul 28 17:41:30 ubuntu sendmail[2975]: o6SGfT2L002975: to=tunji.g@gmail.com, ctladdr=tunji (1000/1000), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30053, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o6SGfUfN002977 Message accepted for delivery)
Jul 28 17:41:31 ubuntu sm-mta[2979]: o6SGfUfN002977: to=<tunji.g@gmail.com>, ctladdr=<tunji@ubuntu> (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=120296, relay=gmail-smtp-in.l.google.com. [209.85.229.27], dsn=5.0.0, stat=Service unavailable
Jul 28 17:41:31 ubuntu sm-mta[2979]: o6SGfUfN002977: o6SGfVfN002979: DSN: Service unavailable
Jul 28 17:41:32 ubuntu sm-mta[2979]: o6SGfVfN002979: to=<tunji@ubuntu>, delay=00:00:01, xdelay=00:00:01, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

---

### Post by cdenley on 2010-07-28
It looks like sendmail is working. Did that command send you an e-mail? That PHP code seems to work fine for me. Try this simplified code (after setting to "$to" variable), **then post the resulting lines from /var/log/mail.log**. Also tell us if it prints "success" or "failure", and whether the e-mail was sent.
[PHP]
<?php
$to="me@myemail.com";
$subject="test";
$message="this is a test";
$headers = "From: test@ubuntu.com";
if(mail($to, $subject, $message, $headers)) {
        print "success\n";
}  
else {
        print "failure\n";
}
?>
[/PHP]

---

### Post by ruffEdgz on 2010-07-28
> **cdenley said:**
> It looks like sendmail is working. Did that command send you an e-mail? That PHP code seems to work fine for me. Try this simplified code (after setting to "$to" variable), then post the resulting lines from /var/log/mail.log. Also tell us if it prints "success" or "failure", and whether the e-mail was sent.
[PHP]
<?php
$to="me@myemail.com";
$subject="test";
$message="this is a test";
$headers = "From: test@ubuntu.com";
if(mail($to, $subject, $message, $headers)) {
        print "success\n";
}  
else {
        print "failure\n";
}
?>
[/PHP]

After running that test, you might want to check your /var/log/mail.log to see if that test got to postfix/sendmail correctly.

Just another way to help diagnose the issue.

---

### Post by Ryan Dwyer on 2010-07-28
Looks like you're experiencing the same problem as here:
[http://ubuntuforums.org/showthread.php?t=623977](http://ubuntuforums.org/showthread.php?t=623977)

The solution is in the last post.

---

### Post by theneikid on 2010-12-27
Excuse me. I'm getting "failure" message.

---

