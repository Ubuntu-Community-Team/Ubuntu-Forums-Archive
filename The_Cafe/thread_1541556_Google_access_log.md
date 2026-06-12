---
title: "Google access log"
date: 2010-07-29
forum: The Cafe
---

### Post by fela on 2010-07-29
If google didn't manage it's apache access log, and apache on it's servers was set so that it didn't .gz old logs and just dumped it all to one file which slowly (or rather quickly in this case), grew, how big, in gibibytes (or mebibytes), is your estimate of google's apache access log in 24 hours? ;P

My estimate's...10GiB.

---

### Post by Frak on 2010-07-29
Google doesn't use Apache, end of story.

---

### Post by RiceMonster on 2010-07-29
[img]http://1.bp.blogspot.com/_hXjhQ1_xjuQ/S8IYc35ZKgI/AAAAAAAAJNs/GBtgWgSBUyA/s1600/It%27s+over+nine+THOUSAND.jpg[/img]

---

### Post by FuturePilot on 2010-07-29
> **RiceMonster said:**
> [img]http://1.bp.blogspot.com/_hXjhQ1_xjuQ/S8IYc35ZKgI/AAAAAAAAJNs/GBtgWgSBUyA/s1600/It%27s+over+nine+THOUSAND.jpg[/img]

i c wut u did thar. 8-)

---

### Post by Bachstelze on 2010-07-29
[img]http://media.comicvine.com/uploads/2/27874/600107-oh_you_super.jpg[/img]

---

### Post by Frak on 2010-07-29
> **Bachstelze said:**
> [img]http://media.comicvine.com/uploads/2/27874/600107-oh_you_super.jpg[/img]
teehee

---

### Post by fela on 2010-07-29
OK, it's GWS log then...

PS why don't they use Apache?

---

### Post by Frak on 2010-07-29
> **fela said:**
> OK, it's GWS log then...

PS why don't they use Apache?

Google is really an engineering company. I can see Google coming up with a better solution for their own needs than using a generic project like Apache. GWS was specially designed for what Google does.

---

### Post by fela on 2010-07-29
> **frak said:**
> google is really an engineering company. I can see google coming up with a better solution for their own needs than using a generic project like apache. Gws was specially designed for what google does.

ok...

---

### Post by wolfgangmcq on 2010-07-29
Googling (;)) "Google hits per day" brings up the estimate of 320 million searches in America every day. Thus, just logging the hits on searches would make rather large server log. (Someone else can calculate it based on their logfile.) This dosen't count Google Reader, or Gmail, or any of the other plethora of other services.

---

