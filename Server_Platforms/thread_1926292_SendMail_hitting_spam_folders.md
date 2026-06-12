---
title: "SendMail hitting spam folders"
date: 2012-02-16
forum: Server Platforms
---

### Post by advil0 on 2012-02-16
Hey guys,

I have a copy of XenForo installed on my Ubuntu 10.04 LTS install, under NGINX.

People receive emails from XenForo just fine under SendMail, using the -f option.  It goes to their inbox just fine and everything.

I'm setting up a custom donation page using Stripe and a SSL Certificate, and setting it up to send an email receipt upon payment, but that's hitting spam filters.

Heres my code to send the email, maybe one of you guys would know what's wrong.

```
$subject = 'Donation Receipt from Arklight';
$message = 'Thanks for donating to Arklight!

Your donation of $' . $amt . ' has been received successfully, and you have been automatically applied donator status!

Here is some info from your transaction, for your records.

Donation To:  http://www.arklight.net
E-Mail: ' . $email . '
Username: ' . $username . '
Transaction ID: ' . $charge['id'] . '
Charged To: ************' . $charge['card']['last4'] . '
Card Type: ' . $charge['card']['type'] . '
Expiration: ' . $charge['card']['exp_month'] . ' \ ' . $charge['card']['exp_year'] . '

If you have any questions, please PM advil0 on the forums.

Thanks again!';
$headers = "Reply-To: advil0@gmail.com\r\n"; 
    $headers .= "Return-Path: advil0@arklight.net\r\n"; 
    $headers .= "From: advil0@arklight.net\r\n"; 
    $headers .= "Organization: Arklight\r\n"; 
    $headers .= "Content-Type: text/plain\r\n";
    
mail($email, $subject, $message, $headers);
```

---

