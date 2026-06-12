---
title: "catch-all but n address?"
date: 2014-01-06
forum: Server Platforms
---

### Post by wolfgentleman on 2014-01-06
Ok, basically I want to know how to alias a postfix email in such a way as to redirects all non-registered "aliases" to one account:
virtual user "bob@example.com" receives things sent to bob@example.com and forums@example.com
virtual user "joe@example.com" receives things sent to joe@example.com and bugs@example.com
virtual user "admin@example.com" receives anything virtual user "bob@example.com" or "joe@example.com" does not such as xyz@example.com

Is there a way I can do this?

---

### Post by CharlesA on 2014-01-07
See here:
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04-p4](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04-p4)

In short, add a alias that reads:

```
@example.com                admin@example.com
```

---

### Post by wolfgentleman on 2014-01-07
> **CharlesA said:**
> See here:
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04-p4](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04-p4)

In short, add a alias that reads:

```
@example.com                admin@example.com
```

[s]Yeah, but wouldn't that redirect *everything *to that user? Or would it redirect the rest of them? Or would everything arrive in that user's inbox as well as the other aliases? I found that as a catch-all when I was going to be using just one user, but I decided to do it different... Also could I have something direct things coming from one address to multiple users?[/s] I am thinking about setting it up so that when I give someone on my site admin I can add them as a user in the mail system and maybe a unified inbox for that address? [s]Or what about one set of folders with multiple user logins? Well, that wouldn't work as I wouldn't want them replying to webmaster@, postmaster@, and {user}@...[/s] Any ideas are welcome and appreciated.

Ok, now how would I have unify the "Sent" folder amongst multiple (but not all) users, forcing a copy of all items sent - through SMTP or otherwise to the Sent folder, to prevent duplicate replies? Not a necessity but it would be nice...

---

### Post by CharlesA on 2014-01-07
I don't know if that is possible server side, or if you need to have your mail client do it for you.

---

### Post by SeijiSensei on 2014-01-08
> **wolfgentleman said:**
> Ok, now how would I have unify the "Sent" folder amongst multiple (but not all) users, forcing a copy of all items sent - through SMTP or otherwise to the Sent folder, to prevent duplicate replies? Not a necessity but it would be nice...

Messages are written to the Sent folders via IMAP connections from the clients.  You could write a script that periodically copies those messages to a global Sent folder.  I've use PHP for some tasks like this because it has good IMAP functions.  For instance, you could write a script that would identify new mail in each person's Sent folder and copy those messages to the global folder.  I've done this to rotate users' spam folders or archive old messages periodically.

Another alternative is to grab a copy of users' outbound mail while it traverses the SMTP server and write it to a common Sent folder.  I can think of ways to do this with applications like [MailScanner]("http://www.mailscanner.info/") (via it's "archive" function) but not with SMTP server software like Postfix or sendmail themselves.  That doesn't mean it isn't possible.

---

### Post by wolfgentleman on 2014-01-11
> **SeijiSensei said:**
> Another alternative is to grab a copy of users' outbound mail while it traverses the SMTP server and write it to a common Sent folder.  I can think of ways to do this with applications like [MailScanner]("http://www.mailscanner.info/") (via it's "archive" function) but not with SMTP server software like Postfix or sendmail themselves.  That doesn't mean it isn't possible.

This something like what I was thinking about... What about a mail filter, manageseive I believe it was? Although this would have done better in the [other thread]("http://ubuntuforums.org/showthread.php?t=2190319") I had... Should I reopen the other thread? Or maybe it should be merged?

---

### Post by CharlesA on 2014-01-11
Separate questions. ;)

---

### Post by wolfgentleman on 2014-02-02
Hmmm... Seems that:
```
test@example.com 123@example.com
@example.com catch-everything-else@example.com
```
is the equivalent of:
```
@example.com catch-everything-else@example.com
```
So, I reopened the thread. What do I do?
Here is my (current) MySQL table:
```

id       domain_id     source                                  destination
1        1             helpfulbatchfiles@twprogrammers.com     hbf@twprogrammers.com
2        1             co-owner@twprogrammers.com              hbf@twprogrammers.com
3        1             co-founder@twprogrammers.com            hbf@twprogrammers.com
100      1             @twprogrammers.com                      admin@twprogrammers.com
1000     4             @hawkladybeadery.com                    REMOVED@satx.rr.com

```

---

### Post by CharlesA on 2014-02-02
Uhhh. What email did you send the email to?

---

### Post by wolfgentleman on 2014-02-02
I sent it to: [email]hbf@twprogrammers.com[/email]
and received it at: [email]admin@twprogrammers.com[/email]

---

### Post by CharlesA on 2014-02-02
Does that email address actually exist or is it just an alias?

---

### Post by wolfgentleman on 2014-02-02
Here are my MySQL tables for mailserver:
virtual_aliases
```

id       domain_id     source                                  destination
1        1             helpfulbatchfiles@twprogrammers.com     hbf@twprogrammers.com
2        1             co-owner@twprogrammers.com              hbf@twprogrammers.com
3        1             co-founder@twprogrammers.com            hbf@twprogrammers.com
100      1             @twprogrammers.com                      admin@twprogrammers.com
1000     4             @hawkladybeadery.com                    REMOVED@satx.rr.com

```
virtual_domains
```

id   name
1    twprogrammers.com
2    mail.twprogrammers.com
3    mail
4    hawkladybeadery.com
5    mail.hawkladybeadery.com

```
virtual_users
```

id   domain_id      password    email
1    1              REMOVED     admin@twprogrammers.com
2    1              REMOVED     hbf@twprogrammers.com
3    1              REMOVED     beamimg-validator@twprogrammers.com

```

---

### Post by CharlesA on 2014-02-02
Hmmm.

Maybe the @ domain needs to go at the top of the aliases list ?

---

### Post by wolfgentleman on 2014-02-02
> **CharlesA said:**
> Maybe the @ domain needs to go at the top of the aliases list ?

Already tried that. Unfortunately it still doesn't work.

---

### Post by CharlesA on 2014-02-02
I found this:
[https://www.linuxquestions.org/questions/linux-server-73/postfix-catch-all-alias-problem-using-mysql-708826/](https://www.linuxquestions.org/questions/linux-server-73/postfix-catch-all-alias-problem-using-mysql-708826/)

Looks complicated tho.

---

### Post by wolfgentleman on 2014-02-02
That post told me why it was doing it. So, I looked at a way to adjust the MySQL query to use both the virtual_users.email and virtual_aliases.destination and came up with this:
MySQL virtual aliases map
```

user = mailuser
password = REMOVED
hosts = 127.0.0.1
dbname = mailserver
SELECT IFNULL(a.destination,u.email) as destination FROM virtual_aliases a INNER JOIN virtual_users u ON a.destination=u.email WHERE a.source='%s' OR u.email='%s'

```
And badabing badaboom! Working perfect!

---

### Post by CharlesA on 2014-02-02
Sweet! Nice job!

Your SQL skillz are better than mine. ;)

---

### Post by wolfgentleman on 2014-02-02
> **CharlesA said:**
> Sweet! Nice job!

Your SQL skillz are better than mine. ;)

Thanks! :D 
I had a lot of practice when I (attempted) to script my site from scratch. It didn't workout very well :-?... but hey, I really good at MySQL so I got something out of it.;)

Anyway, thanks for the help!

---

