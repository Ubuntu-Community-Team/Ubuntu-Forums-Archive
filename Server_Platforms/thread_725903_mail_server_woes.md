---
title: "mail server woes"
date: 2008-03-16
forum: Server Platforms
---

### Post by dsbw on 2008-03-16
So, here's this great set-up called [PostfixVirtualMailBoxClamSmtpHowto]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto") which works just beautifully right up until the dovecot configuration file.

It's outdated. 

I've now spent many hours trying to fuse the configuration suggested in the above how-to with documents on dovecote, and the many, many other how-tos for setting up a mail server. (All of which seem to contain conflicting info, or important gaps where they don't overlap.)

The closest I've gotten to success is making it possible for someone to log in successfully to the server (using plain authentication with nothing else available). If someone tries to mail that person, however, the server (looks like Postfix) rejects the e-mail:

"Recipient address rejected: User unknown in virtual mailbox table"

What would be cool if it's not a big huge deal is for someone knowledgeable to go through and correct that configuration file. (I'd do it myself but I can't find any transitional info on the dovecot site. It's like these old settings are damnatio memoriae, as if they never were. This may be entirely my own short-sightedness, since I've been worn out trying to get my server going.)

I dunno, maybe the rest of the info is out-dated too.

Maybe I should give up the virtual host notion and just create users everywhere.

It's enough to make a guy miss Mercury...

---

### Post by otake-tux on 2008-03-18
if you have less than 200 hundred users, using a database for virtual hosting is overkill and overly complex.

I suggest going by the KISS principle.  just use system accounts with no shell access.

---

### Post by HermanAB on 2008-03-18
Well, Postfix is telling you that the user is not in the virtual mailbox table and that is the problem you have to fix.  Postfix error messages are good - you should believe them.

---

### Post by dsbw on 2008-03-19
> **otake-tux said:**
> if you have less than 200 hundred users, using a database for virtual hosting is overkill and overly complex.

I suggest going by the KISS principle.  just use system accounts with no shell access.

Well, believe me, I didn't *start* using a database. I'm just trying to find something that works.

The appeal of the dovecot is that it's supposed to work on text files. (And I'm sure it does if you know WTF you're doing....)

---

### Post by dsbw on 2008-03-19
> **HermanAB said:**
> Well, Postfix is telling you that the user is not in the virtual mailbox table and that is the problem you have to fix.  Postfix error messages are good - you should believe them.

Oh, I do. It's just that I was looking right at them. (Or more correctly, looking at what I thought they were.)

So...now I'm stuck at not being able to validate. I used this guide: 

[http://howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3](http://howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3)

But when I take the POP3 test a little further and try to login:

andy@sidaris:~$ telnet localhost pop3
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
+OK Hello there.
user test
+OK Password required.
pass somereallyhardtoguessthingnoonecouldeverfigureout
-ERR Login failed.

I'm tempted to uninstall everything and start over.

---

### Post by HermanAB on 2008-03-19
Hmm, that guide is waaaay to complicated.

Go here: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

and provided that your DNS is configured right, in about 20 minutes, you should have a full featured mail system.

Cheers,

H.

---

### Post by dsbw on 2008-03-20
Wow, well, that's definitely easy. Wish I'd known about that last week. Or last year, for that matter...

Only thing that's not appropriate to my situation is that it--like a lot of the solutions I saw--defaults to setting user name to receive e-mail at all domains. So, if I host "site1.com", "sitea.net" and "sitesquared.org" and create a user "steve", he becomes "steve@site1.com", "steve@sitea.net" and "steve@sitesquared.org".

I gather there's a way around that but haven't sussed it out yet. You wouldn't happen to know, would you?

---

### Post by HermanAB on 2008-03-20
Yes, that is the way Citadel works.  It only affects login.  The solution is to use longer names and email aliases:

User: john.doe.example
Email: [email]john.doe.example@example.com[/email]
Alias: [email]john.doe@example.com[/email]
Alias: [email]jdoe@example.com[/email]

User: john.doe.nowhere
Email: [email]john.doe.nowhere@nowhere.com[/email]
Alias: [email]john.doe@nowhere.com[/email]
Alias: [email]jdoe@nowhere.com[/email]

So, tell the user his login is "john.doe.example" and his email is "john.doe@example.com" and "jdoe@example.com" and the user will be happy.

Cheers,

Herman

---

### Post by dsbw on 2008-03-21
I see. Does that mean, in your example, there's also:

[email]john.doe.example@nowhere.com[/email]

and

[email]john.doe.nowhere@example.com[/email]

?

Odd.

---

### Post by dsbw on 2008-03-21
Ooh. Looks like you can avoid crowding the other domains completely by setting the primary address....

---

### Post by HermanAB on 2008-03-21
Yup, the user name is used to log into Citadel in general, so that will be the primary email address - the actual mailbox account in Postfix terms.  Then you can create as many convenient aliases as you need and all mail addressed to the aliases will end up in the real mailbox.

Citadel is so easy to configure, that in general, if you find it difficult, then you are doing something very wrong!

Cheers,

Herman

---

### Post by dsbw on 2008-04-04
Hmmm. All my mail goes out under the same domain, regardless of where it's sent from. Any thoughts?

---

