---
title: "unable to open the database using sqlite3 module in python"
date: 2008-09-27
forum: Server Platforms
---

### Post by shredder12 on 2008-09-27
I am using Hardy and have already configured apache to use it. I have done some of my previous assignments using modpython and apache but this time i have to connect the web page with a database. I am using sqlite3 module to serve the purpose. I m using the following code to do it..
```

def add(req):
        req.content_type='text/html'
        conn=sqlite3.connect('/var/www/ass4/sql.db')
        curs=conn.cursor() 
        curs.execute('insert into addrs_book values("akhil","akhilvij",889839823,"Delhi")');
        x=[]
        x=curs.fetchall()
        return"""
        <html>
        <body>
        %s</body>
        </html>""" %x



```
it says  i m unable to open the database file.I gets connected the problemm is there with the "curs.execute" .
 Though when i replace the "insert.." query with the "select * from table"
it shows me the whole table.
i don't understand why it doesn't modifies the table..
I have the changed the permission of both the database and the python program to 777.but it still doesn't work.
and help in this regard will be appreciated..
thankyou..

---

### Post by lykwydchykyn on 2008-09-27
Have you tried this query in the sqlite3 client directly?  I know in some other python dbapi's if you try to execute a bad query it kills your connection.

---

### Post by shredder12 on 2008-09-28
ya i have tried and as you can see.. there is nothing wrong with the query..
well thanks for your concern...but now i have switched to mysql module...and believe me i never faced this problem in mysql...i don't know what was wrong with sqlite3 but who cares now..
newaz.. Thankyou..

---

### Post by chester000 on 2008-09-29
Hi!
I've got same problem but while using php access. I can't switch to mysql though, so if anyone could help, it'd be great.

I'm using kohanaphp project to create web applications and have to deal with sqlite3 now. I can't execute INSERT query using kohana's Pdosqlite driver, but SELECT works OK. When using mysql everything works fine, I also tried to run the application on other windows and debian systems and there was no problem with it, so I assume it's ubuntu related.

---

