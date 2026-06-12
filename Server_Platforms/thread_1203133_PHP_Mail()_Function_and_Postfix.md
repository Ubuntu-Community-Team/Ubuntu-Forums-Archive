---
title: "PHP Mail() Function and Postfix"
date: 2009-07-03
forum: Server Platforms
---

### Post by Drezard on 2009-07-03
I'm trying to use PHPs mail() function. Which the fourth parameter allows you to enter an email, which the mail will be sent from. I've set up (on the webserver) a Postfix MTA. But, whenever I send mail through the mail() it sends as "www-data" not the email i used as the fourth parameter. 

Any ideas on how i can send mail as the fourth parameter?

Daniel

---

### Post by seezee on 2009-07-21
i, too have experienced this problem. we are using mail only for sending out forms from our client web sites; the variable $Email is used in the php mail header to generate the From, Reply-To and Return-Path info. but when the e-mails arrive, the Return-Path is [email]www-data@*mydomain.com[/email]*, and the From and Reply-To info is blank. i've monkeyed with various .conf files and also the php to try to fix this, with no success; the best i can get is that the From header is www-data (the Apache2 user) in some of the php edits i made & later undid (experimenting with the -f flag).

besides making it harder for clients to just hit the "reply to" button in their mail clients, this may stop mail from getting thru some ISPs, so i need to fix it. and yes, i do know about header injection attacks, but, 1 step at a time.

we're running Intrepid Ibex, with Postfix/Courier/SASL/Amavisd-New/Postgrey/ClamAV. here's the relevant php:

```
$message="
Name | ".$LastName.",  ".$FirstName." ".$MI."".'.'."
E-Mail | ".$EMail."
Comments | ".$comment."
Terms | ".$terms."
";
$message = stripslashes($message);
//$sender= "From: ".$Email."\r\n";
$headers = "From: ".$Email."\r\n";
$headers .= "Reply-To: ".$Email."\r\n";
$headers .= "Return-Path: ".$Email."\r\n";
mail("address@domain.tlc","Inquiry from My Site",$message,$headers);
```

i can send further examples of config files & logs if it'll help troubleshoot this.

thanks,

--cz

---

### Post by seezee on 2009-07-21
well, solved, for me, anyway. after a day & a half of my struggling with this our other developer looked at my php & saw i had typoed the name of the variable: ```
$Email
```should be ```
$EMail
```everything works fine, except apparently we can't change the return-path. but i can live with that.

cheers,

--cz

---

