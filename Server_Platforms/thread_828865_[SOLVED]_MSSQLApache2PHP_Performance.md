---
title: "[SOLVED] MSSQL/Apache2/PHP Performance"
date: 2008-06-14
forum: Server Platforms
---

### Post by Cubus on 2008-06-14
Hi folks,

I had the plan to move our companys webserver from Windows/Apache 1.3 to Ubuntu/Apache 2.2 due to security reasons.

The Website is served by querying an old MS-SQL Server 7.0

Now I have the Ubuntu boy set up (8.04 Server) using the php5_sybase module to connect to the MSSQL Server, but I experience mayor performance issues. On a page with many sql queries the windows box takes approx. 1.8 seconds to server the page while the linux box needs a little more than 6 seconds!

In terms of hardware the linux box has higher cpu-speed, more ram and a faster harddisk than the windows box.

I can now only image that the FreeTDS library is performing much worse than the native windows libraries.

Anyone got an idea what I can do to get at least close to the windows-box performance?

Thanks in advance

Marcus AKA Cubus

---

### Post by Cubus on 2008-06-14
Ok, heres something to add:

The page wich took so long to load had about 126 DB-Querys to run. I optimized the procedure and got down to 4 queries (wow, I did write some expensive code there but I never noticed because the windows-server did it fast enough), now the linux-server runs the page in 0.75 seconds where the windows box needs 1 second.

So, now I see the linux speed I'm used to, but still the experience tells me, MSSQL queries need more time on linux than on windows, the performance-bargain on the linux server is made in the script processing.

Well, I did work around this issue with good results, still, what can I do to get my MSSQL querys run in a similar speed on linux as on windows?

---

### Post by chris.zeman on 2008-06-16
I guess I'm confused. It sounds like the Linux box is already working faster than the Windows box from what you said.

> the linux-server runs the page in 0.75 seconds where the windows box needs 1 second.

It would take some work, but it might be worth it to transfer the data in your MS SQL Server to MySQL. Would that be an option?

Chris

---

### Post by Cubus on 2008-06-16
It does run faster now, with lesser MSSQL queries, but with time the scripts will get more complex and it might happen that there will be more querys again wich means that in time the windows box will perform better again.

Not a pressing issue right now since due to the optimized scripts everything runs fine right now.

Switching to MySQL is not an option sadly since we have other applications here wich will only run with the MSSQL server (or sybase that is)

---

### Post by windependence on 2008-06-16
> **chris.zeman said:**
> I guess I'm confused. It sounds like the Linux box is already working faster than the Windows box from what you said.



It would take some work, but it might be worth it to transfer the data in your MS SQL Server to MySQL. Would that be an option?

Chris

This was going to be my suggestion, but I figured you probably couldn't. M$ gets you so entrenched in their technology, that you can't ever get out. MSSQL performance is miserable even on Windoze, and trust me, they make sure that is where it runs the best. It's unfortunate that so many large enterprises are deploying this load of crap.

-Tim

---

### Post by Cubus on 2008-06-16
Well, we might switch to sybase one day, as our erp-system runs on either.

Thanks for your input :)

---

### Post by windependence on 2008-06-16
> **Cubus said:**
> Well, we might switch to sybase one day, as our erp-system runs on either.

Thanks for your input :)

Yeah, sorry I didn't have anything useful or more constructive to give you. I would say if you find the chance to jump off the M$ bandwagon, go for it. It's frustration when you walk into these situations where things are already firmly in place and entrenched so deeply it would be too painful to back out.

-Tim

---

