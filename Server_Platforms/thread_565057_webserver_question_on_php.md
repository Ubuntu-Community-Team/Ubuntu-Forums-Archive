---
title: "webserver question on php"
date: 2007-10-01
forum: Server Platforms
---

### Post by gishaust on 2007-10-01
Hi everyone,

I have been running some scripts on my webserver and they all work well except one. I am using the mail() function in a script when I load the script it should send an email to my gmail account.
[PHP]<?php

// Your email address
$email = "me@gmail.com";
// The subject
$subject = "Enter your subject here";
// The message
$message = "Enter your message here";
mail($email, $subject, $message, "From: $email");
echo "The email has been sent.";
?>[/PHP]

My question is this following,
Does it take the information back to the webserver and then sends it to gmail? and if it does is there a port that needs to be open?

Thanks gishaust

---

### Post by p_quarles on 2007-10-01
Neither Apache nor PHP can deliver e-mail by themselves. You need to install a mail transfer agent such as sendmail or postfix.

---

### Post by gishaust on 2007-10-01
Thanks for your help 

Are there any security issues I need to know.

Gishaust

---

### Post by p_quarles on 2007-10-01
Both of the programs I mentioned are secure, but there are *always* security issues, for any and all computers doing anything. The best thing to do is to regularly check the log files for anything suspicious.

And, of course, any public server should be behind a firewall of some sort. Neither sendmail or postfix will need an inbound port open to do what you are trying to set up. 

If you're expecting a great deal of traffic on your site, you might want ot set up a spam filter. Honestly, though, I've been running a site with a similar mailing script for about a month, and have yet to receive any spam.

---

### Post by gishaust on 2007-10-01
p_quarles

Thank you so much for this relevant information. This stopped much pain and heartache.


Gishaust

---

### Post by gishaust on 2007-10-09
hello

I was just reading this advice again. I want to ask do I have to allow port  25 to be setup for tcp and not upd (i think). To let the mail out

thanks again

Gishaust

---

