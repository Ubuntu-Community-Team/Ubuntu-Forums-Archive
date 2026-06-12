---
title: "Too many Apache2 processes"
date: 2013-05-20
forum: Server Platforms
---

### Post by juliosergio on 2013-05-20
We have a machine with Ubuntu Server installed (Release 12.04), mainly to serve Web pages by means of the Apache2 software. 
Once the service was up, however, our users complained that the site was very slow. So I checked, with "ps -A", the processes 
running on the machine, and to my amazement I found 151 processes labeled Apache2.

I thought that when the Web service was raised, only an Apache2 process instance was launched.

Do you have any comments on this?

Thanks,

   -Sergio.

---

### Post by binaryhermit on 2013-05-20
If I had to guess, and perhaps someone else could confirm this, an apache2 process gets forked to deal with each request (and then, at least theoretically, dies when the request is finished)

---

### Post by DJ_Max on 2013-05-21
Since you didn't give much details, I'm assuming you're using Prefork Apache, and have default MaxClients (150) so that sounds normal. You need to optimize and configure  MaxClients, and keepalives.

---

### Post by SeijiSensei on 2013-05-21
You might want to start more "children" as well.

Before you go down this road though, I have to ask what these sites are serving.  If it's just static HTML, then playing with the settings in Apache might help.  However if these sites use a back-end database, that might be limiting the site's performance, not Apache.  This is especially true if the database is not well-indexed so that SELECTs with complex WHERE clauses can take a long time to execute.

---

