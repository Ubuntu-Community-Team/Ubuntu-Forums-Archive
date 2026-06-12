---
title: "Injecting Headers to Incoming mails on postfix"
date: 2010-09-16
forum: Server Platforms
---

### Post by luke7 on 2010-09-16
Hello everyone

I have following requirements:
List of 7k email addresses in text file
I need check all incoming mails and if Sender match to any of the address from the list i need inject something to header, it could be: 
X-Header: Special 
or anything like that. and after that, mail should be delivered as usual.
It's required because there is an application connecting via pop3 and downloading mails and sorting them by many rules. Once it will see my additional header it will go to correct queue. 
I know, the best here will be applying rules on app side, however there is no chance to do it automatically and creating 7k rules is really annoying. Also, i don't manage this app and i was asked if this could be done on server side.
Any ideas what is best solution for this? I believe there will be additions to Sender List from time to time.

Regards
Luke

---

### Post by Bachstelze on 2010-09-16
You can use procmail and pipe the mail to sed or a shell script.

---

