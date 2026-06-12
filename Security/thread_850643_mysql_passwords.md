---
title: "mysql passwords"
date: 2008-07-05
forum: Security
---

### Post by statistic on 2008-07-05
I spent the last hour google'ing and didn't find anybody else even asking this question so I wonder if it's just a stupid question.

So I have a multi-user system going with sql access over phpmyadmin. The question is, how can a user change their own password without giving them excessive privileges? Is there such a way? If not then a way for the user to do it over the mysql prompt would be suitable as well.

I'm hoping this answer is actually a simple one, whose solution I simply overlooked as I often do that.

Any information that would lead me in the right direction would be great.

Thanks in advance.

---

### Post by simonapnic on 2008-07-06
[http://dev.mysql.com/doc/refman/5.0/en/set-password.html](http://dev.mysql.com/doc/refman/5.0/en/set-password.html)
I believe this would help you.
This is the solution to your problem most likely.
I guess you are running MySQL 5, aren't you ?

---

