---
title: "Getting round giving users root access."
date: 2006-04-18
forum: Server Platforms
---

### Post by apjone on 2006-04-18
I recently had to put in a content filter in work, the trouble is that most of the IT people do not actually know howto use linux. This caused a problem as rules would need editing and the only person who can do that is root. So I came up with a work around:

I have 2 webforms with which to add rules
the forms are posted to text files and then validated by 2 shell scripts and then added to the rules.

These forms are password protected (htpasswd) and log username , date and originating IP. 

I think this is the best way to do it . Initail testing is positive. 

I had to use HTML, PHP and BASH but it seems better than letting a user go wild with root access.

Wh> at do you think? have you had similar chanages?

---

### Post by sxtz on 2006-04-18
sounds a lot safer than giving a windows admin your root pw. ;)

---

