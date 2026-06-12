---
title: "Password strangeness"
date: 2009-07-27
forum: Security
---

### Post by goatmonkey on 2009-07-27
This can probably be chalked up to some weird fluke or just me having a brain cramp but it's driving me nuts wondering:

I have multiple user accounts on my linux machine.  I log into one of them early in the day and everything is fine.  Log into some other account, do whatever, log out, shut down the machine.  Later the same day, I try to log into the first user account and the password is wrong.  Try different variations of the same thing, no good.  Eventually log into another account (all the other passwords work), change the password for the account from there.

Checked the auth.log, no other logins for that account since the one earlier that day and only the password changes I can account for.  Computer was off while I wasn't using it.  Not running any servers and the firewall has everything blocked as far as I know.  Ran rkhunter and chkrootkit for the hell of it with no hits aside from the usual suspicious files.

I'm fairly sure I didn't forget the password.  Is there anything else it could be?  What else can I check?

---

### Post by goatmonkey on 2009-07-31
No guesses how the password might've changed or what this can be a sign of?  Can a password be changed without the change being logged?  I wish instead of going and resetting the password I went and checked the last change time on /etc/shadow but it's a bit too late now.

---

### Post by igorzwx on 2009-07-31
"Can a password be changed without the change being logged?"

you can read a lot of such stories here:
			 		   		 		 		**[*Practical UNIX* and *Internet Security* | O'Reilly Media]("http://oreilly.com/catalog/9781565921481/")**

This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more **...**
oreilly.com/catalog/9781565921481/ - [Cached]("http://209.85.129.132/search?q=cache:S8ZqyAGhsCwJ:oreilly.com/catalog/9781565921481/+practical+internet+and+unix+security&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:oreilly.com/catalog/9781565921481/")

If your box was really hacked, log files could be removed, or "corrected".
Read the book, it offers some practical advices.

---

### Post by cariboo on 2009-07-31
The above link is not relevant, it goes to a book that is out of print. Try:

```
passwd -S <username>
```

The above command will tell you when the password was created.

---

### Post by igorzwx on 2009-07-31
"book that is out of print"

You can buy the 3rd edition here:
Practical Unix & Internet Security, 3rd Edition by Simson Garfinkel, Gene Spafford, and Alan Schwartz (Paperback - Feb 21, 2003)
[http://www.amazon.com/Practical-Unix-Internet-Security-3rd/dp/0596003234/ref=sr_1_1?ie=UTF8&s=books&qid=1249072591&sr=8-1](http://www.amazon.com/Practical-Unix-Internet-Security-3rd/dp/0596003234/ref=sr_1_1?ie=UTF8&s=books&qid=1249072591&sr=8-1)

I have the 2nd edition of this book.
On the back cover, you read: 
"Buy this book and save on aspirin"

You read this book, and relax.
I do not know why.

---

### Post by goatmonkey on 2009-07-31
I'll check out the book.  The passwd check was something I SHOULD have done but I wasn't thinking calmly at the time from having just tried a dozen variations of my password so I just logged into my admin account and changed the password so now I'll probably never actually know if it was changed or not.

If it was a hack and the logs were doctored, why leave an obvious mark like changed password?  If you have su access to doctor the logs, why bother hacking the password of a user with no admin privileges?  I'm sure the possibilities are endless but it makes me wonder.  Anything I can do to check for signs of something going on besides rkhunter and chkrootkit?

Any non-hack-related explanations for something like this other than early onset of senility?

---

### Post by cariboo on 2009-08-01
I hate to say it, but rkhunter and chkrootkit are basically useless.

I installed a rootkit on one of my test systems, and neither program detected anything suspicious.

---

### Post by x3roconf on 2009-08-01
> **cariboo907 said:**
> I hate to say it, but rkhunter and chkrootkit are basically useless.

I installed a rootkit on one of my test systems, and neither program detected anything suspicious.

What rootkit you installed?

---

### Post by goatmonkey on 2009-08-01
Should I realistically be concerned?  I realize there's a chance in everything but I'm not running any servers, the machine is behind the DSL modem's firewall, has a firewall of its own and I'm not running any servers so all the ports are closed (checked with nmap).  On top of that, the computer is off while I'm not using it.  I've been wanting to try snort and OSSEC but just reading the installation instructions make it seem like more of a server-oriented precaution.

I'm probably going to reinstall the OS anyway.  It was upgraded from 8 to 9.04 and that kind of thing always seems to come out a bit glitchy for me.  A LUKS drive doesn't seem to want to automount properly when I turn it on, etc.

---

### Post by igorzwx on 2009-08-01
"Should I realistically be concerned?"

A good question!
Take care about you sensitive information first of all.
And read that book (general guidelines).

---

### Post by cariboo on 2009-08-01
Mafix, it creates a backdoored sshd on port 11111 in my case.

---

