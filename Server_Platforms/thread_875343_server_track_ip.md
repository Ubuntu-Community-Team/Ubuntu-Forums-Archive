---
title: "server track ip"
date: 2008-07-30
forum: Server Platforms
---

### Post by matt79 on 2008-07-30
Ok here is the problem I have.:) My sister is getting married and she has sent the R.S.V.P out with a note that people could send theirs by snail mail or submit it online. I created her a web site using hardy and apache. I also created a way for people to R.S.V.P. online using PHP. The problem is after I had received some online R.S.V.P I modifid the code a little so it would work better. I found out two days later that if anyone tried to submit one online my server would say "sorry you are not invited" and it would not let them continue. Is there a way for me to look on my server and see if anyone accessed the rsvp file on those days?

---

### Post by cariboo on 2008-07-31
You could look at /var/log/apache2 access.log and error log.

Maybe you shouldn't have changed the the php :)

Jim

---

### Post by c2olen on 2008-07-31
> **cariboo907 said:**
> You could look at /var/log/apache2 access.log and error log.

Yep, unless you made another option for logging, this is probably the only way to track back your visitors. But, if they got their IP by DHCP, this will most likely not tell you anything usefull. If you have MySQL running, and logging is enabled (i don't remember if it is enabled by default) you can also take a look at the MySQL logging. I believe it is in /var/log/mysql.log

---

### Post by matt79 on 2008-07-31
> **cariboo907 said:**
> 
Maybe you shouldn't have changed the the php :)

Jim

I wish that everyday:( but I hope I can see who had access to it on the few days it was up and then trace their ip address to their state or county. Then I guess I will look at who was invited in that area and call em.
Thanks for your help guys.

---

### Post by matt79 on 2008-07-31
Well I tracked them down. There were three people who saw it. The sad part is two of them I really do not want to say anything to (they are from my dad and moms  sides of the family) As for the last person I can tell her what happened. Anyone have a good excuse I can use for the first two people?

---

### Post by c2olen on 2008-08-01
> **matt79 said:**
> Anyone have a good excuse I can use for the first two people?

Maybe you should be a man and face the consequences of your actions? :^o
But then again, who am i to judge. :-k

---

