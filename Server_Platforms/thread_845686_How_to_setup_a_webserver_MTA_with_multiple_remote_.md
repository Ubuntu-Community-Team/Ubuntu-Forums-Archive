---
title: "How to setup a webserver MTA with multiple remote Gmail servers?"
date: 2008-06-30
forum: Server Platforms
---

### Post by jdmelton on 2008-06-30
I wish to set up a Hardy 8.04 web server (Apache 2.2/PHP 5) to use external
email servers. There are 3 virtual hosts on the web server machine. Each vhost
will not have any local system users. I plan to use Gmail for the email
servers and have configured one domain (so far) to use Gmail. I have set
up the MX record in DNS and pinging mail.somedomain.com returns the Google
email server.

I want to use the PHP mail function to send email from some of my domain web
pages. The domain recipient will be one of the domain users with a domain
Gmail account. I also wish to provide an optional checkbox on some forms to
let a customer send a copy to themselves as well as a domain user. And, there
are 3 different domains with different sets of users, none of which have
accounts on the actual web server. Users will read and send email from
google.somedomain.com, not from the web server.

I have spent the last couple of days searcing the web, but the closest I have
found is how to set up an email client for one user. I have read blogs and
other web pages that say this can be done with exim/postfix/sendmail.

What is the preferred way to set this up? And can someone point me to the
web resources besides the home pages and faqs for these 3 MTA's?

---

### Post by jdmelton on 2008-07-02
I have made some progress. I found this blog: [http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/](http://blog.twinklesprings.com/2008/03/27/remote-mail-delivery-for-google-apps-and-postfix-mail-server/)

Which, after some more searching on Postfix, led me to this: [http://www.debianhelp.co.uk/postfix.htm](http://www.debianhelp.co.uk/postfix.htm)

The satellite option seemed to be what I was looking for. So, I removed Exim4, installed Postfix, and selected the satellite option. When prompted for mydomains, I added the Gmail domain (somedomain.com).

Then I tried this script from the command line:

#!/usr/bin/php
<?php
mail("jdmelton@somedomain.com", "test - mailserver", "This is a test of somedomain.com command-line email from server via Gmail.\nPlease do not reply.", "From: [email]me@somedomain.com[/email]"."\n"."Reply-To: [email]me@somedomain.com[/email]");
?>

And it sent the emails. Note that I did need to use the complete username@domainname in the From: field or Google would reject the email.

So, part of my problem is solved. I can send email from the command line on my web server via Gmail for one domain. However, my website forms do not work. I also have not configured the other domains for Gmail yet.

---

### Post by windependence on 2008-07-02
Didn't you post this just recently in another thread? Forgive me if I am mistaken.

-Tim

---

### Post by jdmelton on 2008-07-02
> **windependence said:**
> Didn't you post this just recently in another thread? Forgive me if I am mistaken.

-Tim
No, not in this forum.

I did post a similar topic over at webmasterworld.

I have been answering my own post here in hopes that the information might be useful to someone else.

---

### Post by kustomjs on 2008-07-02
I am currently needing the same help on setting up with this issue
:[http://ubuntuforums.org/showthread.php?t=846548](http://ubuntuforums.org/showthread.php?t=846548)

---

