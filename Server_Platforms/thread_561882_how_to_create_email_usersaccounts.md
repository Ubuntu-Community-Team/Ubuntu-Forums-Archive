---
title: "how to create email users/accounts"
date: 2007-09-28
forum: Server Platforms
---

### Post by demiurgen on 2007-09-28
i have followed a guide to setup the perfect server on ubuntu 7.04 at howtoforge.com.

everything was successfully installed
and all the tests also ran successfuly

but what do i do now...?

how do i set up email accounts?
is there another guide for this maybe?
how can i start to use the mail part of this perfect server??

i also installed webmin...

---

### Post by HermanAB on 2007-09-28
There are many different ways to set up email: Postfix, sendmail, exim, qmail, with cuccipop, pop3d, qpopper, dovecot, authentication, amavisd, amavisd-new, spamassassin, pop-before-smtp, clamav, maildrop, mailman, courier, squirrel, roundcube, razor, pyzor, dcc, fetchmail... the list goes on and on and that is the reason why there are so many different howto guides out there and why you'll never get a simple answer to a mail system question.

So how now?  First you have to decide what you want your mail system to do and how many users it is going to have.  If you run an ISP and need to serve millions of users, then you need sendmail, postfix or qmail.  If you serve a small business then they will want shared calendars.  If you serve a large business, then you don't want to have to run out to buy a large new disk drive each time the HR manager sends a message with a 100MB Word attachment to all 25000 people in the whole company...

So, since you still know nothing about this problem, I suggest that you start with something that is both full featured and super easy to install and there is only one system that has all those qualities, Citadel: [http://www.citadel.org](http://www.citadel.org)

Citadel can do all of the above.  It works for anything from a single user to tens of thousands of users.  It has web access, calendars, chat, discussion forums, address books and works with both web browsers and email clients.  It has an Oracle Berkeleydb database backend and stores only *one* copy of a message, even if it is sent to thousands of users.  It is very low overhead and is zero maintenance.  It installs in about 20 minutes and then it Just Works (TM).

Otherwise, if you like to tinker, then you should go to the Postfix.org web site and start reading, but be warned, setting up a Postfix (Exim or Qmail) based system for the first time will take at least a week.  Reading a few howto's on the Postfix web site should be enough to convince you to try out Citadel's 'Easy Install'...

'Hope that helps!

Herman

---

### Post by demiurgen on 2007-09-29
thank you HermanAB.

i just read about it on their website and this package gives me just what i need.

i am gonna be my boss' pet for sure if i can get this up and running ;)


:guitar:

---

### Post by HermanAB on 2007-09-29
Here is a guide I wrote a long time ago:
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

The only difficultish part is getting the spam and virus filters to work.  Follow their instructions exactly and it should be OK.  Test with the Apache GTUBE test spam ([http://spamassassin.apache.org/gtube/](http://spamassassin.apache.org/gtube/)) and EICAR test virus ([http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)), to make sure it really works.

Cheers,

H.

---

