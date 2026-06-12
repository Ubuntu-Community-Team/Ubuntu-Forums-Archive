---
title: "Postgresql starting problem"
date: 2007-11-20
forum: Server Platforms
---

### Post by coolbeansdude51 on 2007-11-20
Hello Ubuntu Peps! 

So far I freakin love Ubuntu.  I transfered over from Fedora and its been good sailing so far.

I have had no problems so far but this one is a hard one.

I get this error whenever I use this command: createuser wifidog --pwpromptEnter

This error comes up.

createuser: could not connect to database postgres: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

I have made sure that postgresql is running multiple times.  I do a sudo /etc/init.d/postgresql-8.2 start

I know that postgresql-8.2 is there because I have use ls to see it.

Ok so how do I figure this out?

Thanks,
Coolbeansdude51

---

### Post by coolbeansdude51 on 2007-11-20
Ahh ... 

I figured it out.

I didn't have enough memory to start the program in the first place. I freed up some memory then it worked out fine.  

Thanks!
-Adam

---

