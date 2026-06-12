---
title: "Open source BI-like system?"
date: 2011-08-03
forum: Server Platforms
---

### Post by kristoffer_1980 on 2011-08-03
Hi,

I am looking for an opensource-software that works with debian/ubuntu. I want to count rows from a couple of MySQL-tables on a server and that way keep statistics of changes in those tables. The tables should be read something like every night, and it shows how customers and subscriptions are changing. Today there is about 10 000 rows * a couple of tables, and it would be nice if it is presented in a webpage...

Does anyone know any software for this, or where to start looking?

Thanks!

---

### Post by Lars Noodén on 2011-08-03
Sounds like a prime task to write a short script in perl or python to do that work.  To schedule it to run automatically, you can then use cron.

---

### Post by kristoffer_1980 on 2011-08-03
> **Lars Noodén said:**
> Sounds like a prime task to write a short script in perl or python to do that work.  To schedule it to run automatically, you can then use cron.

Yeah, to collect the data is the smallest problem, but I also would like a way to present the data, and also if possible to "sort" data presentation in different ways, for example:

Case 1:
Show a graph from the last year, number of subscription type X in an geographic area compared to the total possible subscriptions in the area.

Case 2:
Show a graph from the last 2 months, number of subscription type Y in the same geographic area.

Do you have some idea also there?

Thanks!

---

### Post by Lars Noodén on 2011-08-03
When you have more details, I'd ask over in [Development & Progamming](http://ubuntuforums.org/forumdisplay.php?f=310).  It's been too long since I've done that kind of work, but there are going to be several graphics modules for the programming language of your choice that will allow you to graph.  It's a matter of first extracting the data and getting several sets of X,Y coordinates to plot.

Alternately, you can have your script extract the data and then pass it on to GnuPlot or R or something like that.

---

### Post by kristoffer_1980 on 2011-08-09
Thanks, I actually ended up starting extract data to my database, and then I am going to use pChart, it seems really good, and good enough for me.
First thing I was more looking for a "system", but this way might work also, where I define some graphs to draw.

---

