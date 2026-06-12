---
title: "Compile a separte mysql server?"
date: 2005-04-04
forum: Server Platforms
---

### Post by casualtie on 2005-04-04
I realized Ubuntu are using a local mysql server to store information or something on.
So I wonder if it would be unwise to use that mysql server on my local webserver. Or should I compile a separate myql server with apache 2.0 and php5?

-Thanks for any input

---

### Post by DJ_Max on 2005-04-05
How do you know Ubuntu is using MySQL to store data on your computer? I never read that anywhere.

---

### Post by alastair on 2005-04-05
If it's available, use it.

One MySQL database can store lots of "databases", each containing lots of tables. No problem.

---

### Post by HungSquirrel on 2005-04-05
The only time you would need to run your database server on a seperate machine is if a lot of data is being accessed by a lot of different clients.  For example, large sites running content management systems like Drupal use a seperate webserver and database server.  Ideally, the seperate database server should have as much RAM as possible.

However, these are extreme cases.  Look a the server running this forum.  Currently, the bottom part of the forum index says the following:

> Currently Active Users: 264 (80 members and 184 guests)
According to [this page](http://ubuntuforums.org/about.php), this website is run on a measly Pentium 4 2.4 Ghz machine with a mere 512 MB of RAM.  As far as I know, both the forum database and the webserver are running on the same machine, and I don't recall ever having noticed the site being sluggish!

---

### Post by DJ_Max on 2005-04-05
Ohhh, you were talking about the Ubuntu Forums. I thought you meant something else... 8) 
Disregard my first comment.

Anyhow, no need for two MySQL Servers on one machine. Unless you have do complex computation & queries.

BTW, wouldn't call a P4 measly. [-X

---

### Post by HungSquirrel on 2005-04-05
I had trouble deciphering his post.  In fact, my answer had nothing to do with his post now that I read it again...  I'm still not sure what he's asking or where he got the notion that Ubuntu stores things in a mysql db...if that's what he's saying.

---

### Post by DJ_Max on 2005-04-06
[QUOTE=HungSquirrel]I had trouble deciphering his post.  In fact, my answer had nothing to do with his post now that I read it again...  I'm still not sure what he's asking or where he got the notion that Ubuntu stores things in a mysql db...if that's what he's saying.[/QUOTE]
 Thats what I thought, it sounded like he thought Ubuntu Linux stores info in a MySQL db on your computer.?

---

