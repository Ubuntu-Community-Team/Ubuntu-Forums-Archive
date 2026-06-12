---
title: "Email Goes to Gmail Spam"
date: 2011-09-06
forum: Server Platforms
---

### Post by unemployment on 2011-09-06
I have been in the process of making a php auto generated email template, but for some reason it keeps going to gmail's spam folder.  I have a valid rDNS, a valid mx and a valid SPF record.  I've even checked my IP and it is not blacklisted.

  
These are the headers I am using.

$boundary     = 'PHP-alt-'.$random_hash;
$x_mailer     = phpversion();
            
$headers  = "From: PitchBIG <contact@big.com>\n";
$headers .= "Reply-To: PitchBIG <contact@big.com>\n"; 
$headers .= "Return-Path: PitchBIG <contact@big.com>\n"; 
$headers .= "X-Mailer: PHP-" . $x_mailer . "\n";
$headers .= "X-Sender: PitchBIG <contact@big.com>\n";
$headers .= "X-Priority: 3\n";
$headers .= "Organization: big\n";
$headers .= "MIME-Version: 1.0\n";
$headers .= "Content-Type: multipart/alternative; boundary=" . $boundary . "\n";

A few weeks ago I changed my domain on the server from "oldsite" to "newsite" but my mail log displays...

oldsite postfix/smtp[7330]: yada yada yada

Do you know how I can stop my emails from going to gmail spam?

---

### Post by SlugSlug on 2011-09-07
try change /etc/mailname if you've not done already

---

