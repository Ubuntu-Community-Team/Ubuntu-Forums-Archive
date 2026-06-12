---
title: "Postfix Email Piping"
date: 2013-01-20
forum: Server Platforms
---

### Post by benj.545 on 2013-01-20
I am trying to setup email piping on my server for a php script, but when I try to add it into postfix using the /etc/aliases file and then send an email to it, it tells me that 
> An error occurred while sending mail. The mail server responded:  5.1.1 <supporttest@mydomain.com>: Recipient address rejected: User unknown in virtual mailbox table. Please check the message recipient [email]supporttest@mydomain.com[/email] and try again.

My server runs webmin with postfixadmin installed.

I actually just discovered that if i send a message to "localhost" it lets it go through, but now i want to figure out how to get it to accept it from "mydomain.com".

Thanks for the help!

[Edit]
I believe that postfix is only setup for localhost mail and mydomain.com is a virtual domain.

---

### Post by chrisguk on 2013-01-20
**sigh**

Webmin :popcorn:

First thing, ditch webmin lol, try to understand whats going on in your own box by command line.

Here is a great guide on how to setup up sendmail with PHP apps etc.

[http://developernote.com/2012/07/how-i-configured-sendmail-for-php-on-ubuntu-server-12-04/]("http://developernote.com/2012/07/how-i-configured-sendmail-for-php-on-ubuntu-server-12-04/")

Or if you want to setup smtp why not following this guide which is very good for other things too.

[http://ubuntuforums.org/showthread.php?t=1895084]("http://ubuntuforums.org/showthread.php?t=1895084")

Hops that helps a little.

---

