---
title: "Form email"
date: 2006-04-14
forum: Server Platforms
---

### Post by peanut butter on 2006-04-14
i have my webserver up and running and the only thing thats stopping me from convincing someone that it will work is the fact that form email dosn't work. i have no idea how to get it up and running. anyone know of a guide?

---

### Post by peanut butter on 2006-04-14
someone please help

---

### Post by zac1333 on 2006-04-15
[QUOTE=peanut butter]someone please help[/QUOTE]

Not sure exactly what you are asking.  Do you have a mail server up and running?

---

### Post by robert_pectol on 2006-04-15
A couple of years ago, I wrote a simple cgi script in perl to do this.  You're welcome to use it if you want.  You need to create an HTML form that can post data to it.  The perl script is here: [http://rob.pectol.com/myscripts/mailer.txt](http://rob.pectol.com/myscripts/mailer.txt)
It's been a while it but in glancing at it real quick, it looks like your HTML form needs 3 fields: 'quem', 'asunto', and 'mensagem'.
Quem means who, asunto means subject, and mensagem means message - I used Portuguese words when I wrote it :)

You need to have an MTA such as postfix or sendmail (postfix preferably) configured on the server in addition.  Aside from that, it should work fine.  There's not too much to it, realy.  Good luck!

---

### Post by peanut butter on 2006-04-15
[QUOTE=robert_pectol]A couple of years ago, I wrote a simple cgi script in perl to do this.  You're welcome to use it if you want.  You need to create an HTML form that can post data to it.  The perl script is here: [http://rob.pectol.com/myscripts/mailer.txt](http://rob.pectol.com/myscripts/mailer.txt)
It's been a while it but in glancing at it real quick, it looks like your HTML form needs 3 fields: 'quem', 'asunto', and 'mensagem'.
Quem means who, asunto means subject, and mensagem means message - I used Portuguese words when I wrote it :)

You need to have an MTA such as postfix or sendmail (postfix preferably) configured on the server which will process the cgi script.  Aside from that, it should work fine.  There's not too much to it, realy.  Good luck![/QUOTE]

ok i installed postfix and fowarded it to comcast's servers. so now im up and running.
i used the nm formmail script that i had installed, thanks a bunch.

---

