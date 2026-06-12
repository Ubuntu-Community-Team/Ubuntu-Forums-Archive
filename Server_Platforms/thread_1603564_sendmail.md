---
title: "sendmail"
date: 2010-10-22
forum: Server Platforms
---

### Post by cliftonbazaar on 2010-10-22
Hi all,

I have a Ubuntu server which is LAMP.  I have just set up the 'sendmail' function and its associated files, but when I send an email via PHP it can take up to a minute for the page to complete
```
[mail function]
; For Win32 only.
;SMTP = mail.optusnet.com.au
;smtp_port = 25

; For Win32 only.
;sendmail_from = koala@koalacomics.com.au

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =
```php code is ```

//We've added them to the database so now let's send them an email with their password 
  $to = $_POST[email]; 
  $subject = "Application form."; 
  $body = "Hi ".$_POST[traderName]."\n\n"; 
  $body .= "This is an email to say that we have recieved your application.\n"; 
  $headers = 'From: koala@koalacomics.com.au' . "\r\n" . 
    'Reply-To: koala@koalacomics.com.au' . "\r\n" . 
    'X-Mailer: PHP/' . phpversion(); 

  if(mail($to, $subject, $body, $headers)) { 
    echo("<p align=center>Message successfully sent!</p>"); 
  } else { 
    echo("<p align=center>Message delivery failed...</p>"); 
  }
```Note that the email is being sent, it simply takes a very long time for the page to load.

James

PS Another problem I am having is that I can't get email sent to my email address, for example if $_POST[email]= koala@koalacomics.com.au it won't send the email, all 3 of my other email addresses it works fine.
I have actually put all 4 of my email addresses in $_POST[email] at the one time and all email addresses receive it except for koala.

---

### Post by SeijiSensei on 2010-10-23
Are you actually running sendmail as a server daemon on the box itself?  If you enter "telnet localhost 25" at the prompt, do you get a reply?

Generally PHP will hand the message to the locally running sendmail server and let it handle delivery.  That should appear instantaneous to the user.

> PS Another problem I am having is that I can't get email sent to my email address, for example if $_POST[email]= koala@koalacomics.com.au it won't send the email, all 3 of my other email addresses it works fine.
I have actually put all 4 of my email addresses in $_POST[email] at the one time and all email addresses receive it except for koala. 

Where is the mailserver for koalacomics.com.au?  Is it supposed to be this machine itself?  Is it configured to accept mail for the domain?  If you're really using sendmail, and not Postfix which comes with Ubuntu by default, then you need to have an entry for that domain in /etc/mail/local-host-names, and koala needs to be a valid user account.  If you're using Postfix, you'll need to read the documentation.

---

### Post by cliftonbazaar on 2010-10-23
Hi and thanks for your reply,

Please note that sendmail is only used for sending email OUT not IN.  koalacomics.com.au is set up on a third party server whereas my server box is only for hosting websites and, now, trying to send emails out via PHP (just simple emails to say that a person has successfully joined my website.

> telnet localhost 25gives me 
> Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 server ESMTP Sendmail 8.14.3/8.14.3/Debian-9ubuntu1; Sun, 24 Oct 2010 08:37:49 +1030; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]


---

### Post by SeijiSensei on 2010-10-24
When you try to send an email to koalacomics, what do you see in /var/log/mail.log (or /var/log/maillog)?

---

