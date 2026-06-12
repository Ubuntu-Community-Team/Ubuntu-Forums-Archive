---
title: "Using PHP to send mail on Ubuntu Server Problem"
date: 2011-03-03
forum: Server Platforms
---

### Post by Northrop on 2011-03-03
Hello all,

I have setup a mail server on my remote Ubuntu 10.04 server using postfix.

Using Putty to SSH to the server, I can send mail, check mail, and the server accepts mail from other domains (gmail, yahoo, hotmail etc).

However, I cannot seem to send mail using PHP functions.

I have created a "test.php" file with the following contents:

[PHP]<?php mail('administrator@mysite.com', 'Subject test', 'sample message test'); ?>[/PHP]

When I run the .php file, nothing happens, and nothing logs in the mail logs, so I'm sure the server doesnt understand the mail command in PHP files, but I'm not sure how to go about fixing it.

Apache2, PHP5, postfix, and the additional necessaries are installed (this is a webserver/mailserver on 1 box)

Any ideas on what I may have missed?

---

### Post by killfall on 2011-03-03
It might be worth checking the php config file and make sure email is turned on.

---

### Post by Northrop on 2011-03-03
> **killfall said:**
> It might be worth checking the php config file and make sure email is turned on.

Thanks for the quick response.

I had edited the following line in my php.ini file to enable mail:

```
sendmail_path = /usr/sbin/sendmail -i -t
```

However, the PHP mail function still fails to function.

---

### Post by killfall on 2011-03-03
Does the address you are sending from exist?

I had an issue where the account wasn't there and so it wouldn't send.

Also it might be worth looking into pear if you are using IMAP. It's a little more complicated but works well.

---

### Post by Northrop on 2011-03-03
> **killfall said:**
> Does the address you are sending from exist?

I had an issue where the account wasn't there and so it wouldn't send.

Also it might be worth looking into pear if you are using IMAP. It's a little more complicated but works well.

The address definitely exists.  I can send mail from the server using the commandline (the mail command) to any mailing address, and the server receives mail as well.  It works, just not with PHP :D

Im using SMTP with Postfix at the moment.

---

### Post by Northrop on 2011-03-03
Hmmm i cant seem to get it up and running, so Im going to try and do a fresh install of PEAR and see if that method can get it up and going.

---

### Post by killfall on 2011-03-03
Let me know how it goes :)

---

### Post by killfall on 2011-03-03
It might be worth using

[PHP]<?php 
if(mail('administrator@mysite.com', 'Subject test', 'sample message test')){
echo 'Message Sent!';
} else {
echo 'Message Failed!';
} ?>[/PHP]

Just to get some output

---

### Post by Northrop on 2011-03-03
I tried your updated PHP code and it announces "Message Sent" but the mail is not making it to the inbox for administrator.  I checked the mail.log and the following entry was added:



Mar  4 03:47:24 webserver postfix/postdrop[10579]: warning: unable to look up public/pickup: No such file or directory

---

### Post by Northrop on 2011-03-03
SOLVED!

Thanks for the help killfall.  Your change in the PHP script helped me see when it was actually working or not.  I was seeing successful but nothing was going into the inbox.

I checked the logs and when I started Postfix it was refusing to stay running.

Sendmail was listening on port 25 already so postfix could not start correctly.  I killed sendmail process, started postfix, and the mail is now making it to my inbox.

You can check to see what is listening on what ports using:

```
netstat -anp --tcp --udp | grep LISTEN | grep 25
```

It will tell you the process ID and program name so it can be killed.

Whats weird is that I had already removed sendmail but for some reason it was still running.

---

### Post by killfall on 2011-03-04
Fantastic! Glad to hear you sorted it out :)

---

