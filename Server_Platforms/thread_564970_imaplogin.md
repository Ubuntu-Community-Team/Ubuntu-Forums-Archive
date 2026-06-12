---
title: "imaplogin"
date: 2007-10-01
forum: Server Platforms
---

### Post by senejani on 2007-10-01
I have configured a mail server with the help of [this tutorial]("http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour") and it was working fine till I add a new user to mail database.
first there was Maildir problem for that user only (with sending an email to the new user, it wasn't solved, and I solved it by creating directories manually) but now all users have some problems:

first of all when I try to login via squirrelmail, I get the following in mail.log:
```
Oct  2 00:23:31 www imaplogin: Connection, ip=[::ffff:127.0.0.1]
Oct  2 00:23:31 www imaplogin: LOGIN, user=user@domain.tld, ip=[::ffff:127.0.0.1], protocol=IMAP
Oct  2 00:23:31 www imaplogin: LOGOUT, user=user@domain.tld, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0

```
and similary with thnderbird:
```
Oct  2 02:07:35 www courierpop3login: Connection, ip=[::ffff:my_ip_address]
Oct  2 02:07:36 www courierpop3login: LOGIN, user=user@domain.tld, ip=[::ffff:my_ip_address]
Oct  2 02:07:36 www courierpop3login: LOGOUT, user=user@domain.tld, ip=[::ffff:my_ip_address], top=0, retr=0, time=0
Oct  2 02:07:36 www courierpop3login: Connection, ip=[::ffff:my_ip_address]

``` 

and I think the reason of others also is this only!
I have searched a lot but I couldn't find the solution.

and one more question: Is there any easier way to add new user except adding to bank.

---

### Post by HermanAB on 2007-10-02
Hmm, here is a simpler solution: [http://www.citadel.org](http://www.citadel.org)

Easy Install takes about 20 minutes and then it just works, it is very efficient and needs zero maintenance.  It includes all the protocols you can dream of and has an excellent web interface as well.  Most people on Citadel systems  just use the web interface and quit using mail clients.

So, it is not what you asked for, but I have given up with piecemeal lego systems, since they are just a total waste of time compared to this one.

Cheers,

Herman

---

