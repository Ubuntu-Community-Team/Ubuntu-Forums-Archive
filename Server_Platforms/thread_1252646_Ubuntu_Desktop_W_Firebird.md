---
title: "Ubuntu Desktop W/ Firebird?"
date: 2009-08-29
forum: Server Platforms
---

### Post by zkriesse on 2009-08-29
Hey everybody, here's the deal. I'm trying to load Firebird so I can have a localhost on my Ubuntu Desktop. I'm running Ubuntu Jaunty Desktop by the way. Anyway when I tried to connect to localhost this is an error I get.

 *** IBPP::SQLException ***
Context: Service::Connect
Message: isc_service_attach failed

SQL Message : -902
Unsuccessful execution caused by a system error that precludes
successful execution of subsequent statements

Engine Code    : 335544721
Engine Message :
Unable to complete network request to host "localhost".
Failed to establish a connection.
Connection refused

Any help would be appreciated.

---

### Post by the.weavster on 2009-09-06
Did you figure this out?

I want to run Firebird but I'm getting the same message.

Thanks

---

### Post by zkriesse on 2009-09-06
No I haven't figured it out yet either....

---

### Post by zkriesse on 2009-09-07
[SIZE=3]BUMP[/SIZE]....as of now I have not figured this out....PLEASE HELP!!!!!!ANYBODY!

---

### Post by borislavg on 2009-10-01
Is there any solution?
pls
tks

---

### Post by decatur-linux on 2009-10-17
For what it's worth, I have just installed Firebird and am getting the same error message.  Evidently, Firebird server is not running as a service and I don't know how to start it up.  I don't know whether or not I need to "configure" Firebird, or how to do it.  I can run **isql-fb** just fine in a terminal, but it won't let me connect to the **employee.fdb** that is installed in **examples**. I've also installed **FlameRobin** but it won't let me connect to the database either.  Help!

---

### Post by zkriesse on 2009-10-18
To those who find this thread in search of hope and solutions go here. It's a page I wrote for this very problem. It's not finished but it might help regardless. [https://help.ubuntu.com/community/UbuntuWithFirebirdDatabase](https://help.ubuntu.com/community/UbuntuWithFirebirdDatabase)

---

### Post by Temporary_Resident on 2009-10-26
Hi Zach,

Thanks for the work you put into this.  You are obviously building a web-server.  I'm looking to build a standalone system.  Are PHP or Apache necessary for a standalone local system.

For me the difficulty is opening localhost in FlameRobin (or whatever), but I presume Firebird-Classic2.1 provides that (which is why it is called a server), but I can't figure out how to start the FB classic server.  Did you get an answer?

Steve

---

### Post by zkriesse on 2009-12-31
> Hi Zach,

Thanks for the work you put into this. You are obviously building a web-server. I'm looking to build a standalone system. Are PHP or Apache necessary for a standalone local system.

For me the difficulty is opening localhost in FlameRobin (or whatever), but I presume Firebird-Classic2.1 provides that (which is why it is called a server), but I can't figure out how to start the FB classic server. Did you get an answer?

Steve 	

PHP5 and Apache are required I believe...as I've yet to finish my documentation on this I will let you know.

---

### Post by zkriesse on 2011-01-31
Ok, I'm happy to present a full fledged doc page on setting up Apache2, php5, and Firebird 2.1 on an Ubuntu Linux System. This was done on the Ubuntu 10.10 Desktop Edition. If it helps you please let me know, and if you instead find bugs in the doc then let me know that too. Hope it helps! The Doc page itself can be found here at [Firebird 2.1 on Ubuntu]("https://help.ubuntu.com/community/Firebird2.1/On/Ubuntu") ):P

---

