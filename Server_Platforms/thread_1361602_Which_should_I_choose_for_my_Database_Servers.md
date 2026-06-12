---
title: "Which should I choose for my Database Servers?"
date: 2009-12-22
forum: Server Platforms
---

### Post by Nadzirun Hazim on 2009-12-22
Hey guys.
I've got a problem here.

MySQL and PostgreSQL is the two popular database servers.
But which one should I choose?

---

### Post by BkkBonanza on 2009-12-22
Well what software will you be running? Some web apps require one or the other. Mostly MySql is more commonly supported.

---

### Post by Nadzirun Hazim on 2009-12-22
Ohh. I see. Web Apps? I'm not really gonna use them much. But what about PostgreSQL? Do it have the same function as MySQL?

---

### Post by iponeverything on 2009-12-22
It does depend on what it is being used for.

Both MySql and PostgreSQL have different strengths.

---

### Post by Nadzirun Hazim on 2009-12-22
Oh. What if I want to use it for my Web Server. Which one is best?

---

### Post by hessiess on 2009-12-22
Mysql, as its available on most hosting services, (your code will be more portable).

---

### Post by BkkBonanza on 2009-12-22
A web server doesn't need a database unless you are creating or installing/running some web app - ie. forums, blog etc. Then you look at that software to determine what it will work on. If you want to run xyz application but it doesn't work on PostgreSQL then you either have to use MySql or change software.

If you are writing your own code then I'd say stick with MySql as it's installed by default on most host offerings on the web.

---

### Post by wojox on 2009-12-22
[MySQL vs PostgreSQL]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL")

---

### Post by zman121 on 2009-12-22
Well, I manage several IT teams for a really big financial institution. Our databases are managed by full-time database administrators (DBA's).  Occasionally, we acquire a new business and one of my unit's purposes is to bring them into the mainstream.

My DBAs actively dislike MySQL because it operates differently in some key ways than essentially all the mainstream relational data base management systems (RDBMS') that they are used to.  Whether Oracle, DB2, MS SQL Server, or Informix, the commercial RDBMS platforms share a common set of capabilities and try to adhere to the ANSI standard.  So even if one my my DBAs is not completely familiar with, say, Oracle, she can count on it's having the ability to do certain things in similar ways.  When working with MySQL, they are confounded by it's difference in key ways.

Postgres does not in general suffer from this sort of difference.  While it can't do everything that say DB2/UDB does, the areas in common operate very similarly.

Understand, MySQL is a fine product for storing data -- had those small businesses stayed small, the MySQL product could have served them well for many, many years.  But most didn't have full-time DBAs, and few had money.

So, if you want a product to store and retrieve data, MySQL is fine.  I recommend it all the time to small outfits that will not re-sell their software, and are not likely to grow rapidly.

But if you want to truly understand RDBMS operations, possibly to become a DBA or other professional later, go to Postgres, or get one of of the personal editions of DB2/UDB, Oracle, or MS SQL Server.

Disclosure -- I use Postgres on my home network.  But I was a part-time DBA going back to the mid '80s on Oracle.  I get very frustrated when MySQL operates "differently" than what I am used to.  And no, it's not 'buggy' -- it was designed differently.

Cheers

---

### Post by iponeverything on 2009-12-22
I would have to agree with zman121, Postgress is a better long term choice. I think the learning curve may be steeper than with MySql, but for something that is going to provide more options in the future if you need extend the features of your application, Posgress might be a better choice.

---

### Post by memilanuk on 2009-12-22
Do you fellows think the [recent hub-bub with MySQL & Oracle]("http://monty-says.blogspot.com/2009/12/help-saving-mysql.html") is going to give PostgreSQL a shot in the arm?

---

### Post by HighCommander540 on 2009-12-22
> **memilanuk said:**
> Do you fellows think the [recent hub-bub with MySQL & Oracle]("http://monty-says.blogspot.com/2009/12/help-saving-mysql.html") is going to give PostgreSQL a shot in the arm?

No, it will probably boost PostgreSQL.

---

### Post by memilanuk on 2009-12-23
Uhh... yeah.  That's what I said.

[http://www.answers.com/topic/a-shot-in-the-arm](http://www.answers.com/topic/a-shot-in-the-arm)

:lolflag:

---

### Post by Nadzirun Hazim on 2009-12-24
Sorry for the late reply guys.
I was busy for the past few days.
I read all your post. 

I want to say something about your post.

> **BkkBonaza said:**
> A web server doesn't need a database unless you are creating or installing/running some web app - ie. forums, blog etc. Then you look at that software to determine what it will work on. If you want to run xyz application but it doesn't work on PostgreSQL then you either have to use MySql or change software.
Thanks and Good point, Bonaza.
I'll run some web apps eventually. I'll just try both of em'. :)

> **wojox said:**
> [MySQL vs PostgreSQL]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL")
Thanks, Wojox. It was nice reading it.
I can see some Advantage and Disadvantages here. 
But in the end it turns out that MySQL is the world's most popular open source database. :)

> **zman121 said:**
> Well, I manage several IT teams for a really big financial institution. Our databases are managed by full-time database administrators (DBA's). Occasionally, we acquire a new business and one of my unit's purposes is to bring them into the mainstream.

My DBAs actively dislike MySQL because it operates differently in some key ways than essentially all the mainstream relational data base management systems (RDBMS') that they are used to. Whether Oracle, DB2, MS SQL Server, or Informix, the commercial RDBMS platforms share a common set of capabilities and try to adhere to the ANSI standard. So even if one my my DBAs is not completely familiar with, say, Oracle, she can count on it's having the ability to do certain things in similar ways. When working with MySQL, they are confounded by it's difference in key ways.

Postgres does not in general suffer from this sort of difference. While it can't do everything that say DB2/UDB does, the areas in common operate very similarly.

Understand, MySQL is a fine product for storing data -- had those small businesses stayed small, the MySQL product could have served them well for many, many years. But most didn't have full-time DBAs, and few had money.

So, if you want a product to store and retrieve data, MySQL is fine. I recommend it all the time to small outfits that will not re-sell their software, and are not likely to grow rapidly.

But if you want to truly understand RDBMS operations, possibly to become a DBA or other professional later, go to Postgres, or get one of of the personal editions of DB2/UDB, Oracle, or MS SQL Server.

Disclosure -- I use Postgres on my home network. But I was a part-time DBA going back to the mid '80s on Oracle. I get very frustrated when MySQL operates "differently" than what I am used to. And no, it's not 'buggy' -- it was designed differently.

Cheers
Oh, I see, that's how it works. I do understand this a bit. Thanks Zman and I also agree on this one. :)

and as a result I'll use PostgreSQL because of its features and standards. 
Thanks again guys! I really appreciate it. :popcorn:

---

