---
title: "Mail cannot be sent from my server"
date: 2012-04-28
forum: Server Platforms
---

### Post by SirHumpty on 2012-04-28
Hi

I moved a mediawiki site to my own server. It is working fine, except that I cannot get mail to work. The mediawiki sould send mail when people register to the wiki, or when they want to reset their password. On the previous server this all worked fine.

I am not very familiar with installations like this. I've never done this before. I actually think that I messed something up while trying to install mail on the server. 

Now, when I try to register as a new user (hence testing the mail settings) I get an error:
[I]HTTP-fout 500 (Internal Server Error): Er is een onverwachte voorwaarde gevonden toen de server het verzoek wilde uitvoeren.
In the log [/I]

I have configured postfix, because at firs I noticed a message in a logfile of postfix/sendmail, that it failed to open /etc/postfix/main.cf: No such file or directory.

So I browsed the net, and found a way to create it, but it doesn't send any mail at all. Any help is kindly appreciated!

---

