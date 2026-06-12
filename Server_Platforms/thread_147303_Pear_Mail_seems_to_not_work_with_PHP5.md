---
title: "Pear Mail seems to not work with PHP5"
date: 2006-03-19
forum: Server Platforms
---

### Post by chapterthree on 2006-03-19
Hey All,

I was previously running my headless server under Debian 3.1r with apache2 and php4.  I had a Pear Mail script that was running fine.

I've switched my server over to Ubuntu 5.10 with apache2 and php5, but the following Pear Mail script does not seem to work.  It seems it connects to the server, provides auth info, but doesn't do anything after that (debug info provided below).

Any ideas?

[php]<?php
// NOTE: This is the general form of my script, but not the exact script, but this is a sufficient example
include('Mail.php');

$recipients = 'joe@example.com';

$headers['From']    = 'richard@phpguru.org';
$headers['To']      = 'joe@example.com';
$headers['Subject'] = 'Test message';
    
$body = 'Test message';

$params['host'] = 'mail.example.com';
    
// Create the mail object using the Mail::factory method
$mail_object =& Mail::factory('smtp', $params);
$mail_object->send($recipients, $headers, $body);
?>[/php]

```
[19/Mar/2006 20:07:00][28565] {smtps} Server session begin; client connected from xx.18.xx.122:4620
[19/Mar/2006 20:07:00][28565] {smtps} Sent SMTP greeting to xx.18.xx.122:4620
[19/Mar/2006 20:07:00][28565] {smtps} Command EHLO localhost
[19/Mar/2006 20:07:00][28565] {smtps} Sent reply to EHLO: 250 mail.mydomain.net ...
[19/Mar/2006 20:07:00][28565] {smtps} Command AUTH CRAM-MD5
[19/Mar/2006 20:07:00][28565] {smtps} Started authentication method CRAM-MD5
[19/Mar/2006 20:07:00][28565] {smtps} Sent reply to AUTH: 235 2.0.0 Authentication successful (user webmaster@mydomain.com)
[19/Mar/2006 20:07:00][28565] {smtps} Command RSET
[19/Mar/2006 20:07:00][28565] {smtps} Command QUIT
[19/Mar/2006 20:07:00][28565] {smtps} SMTP server session end
```

---

### Post by Horndog on 2006-03-19
My experience is the same with php5 and broken scrips. I guess you have two choices. 1) revert back to php4, or 2) rewrite your scrips to be php5 compliant.

---

### Post by FeraTech on 2007-04-02
Any ideas what needs to be changed with Mail::factory scripts to be PHP5 compliant?

---

