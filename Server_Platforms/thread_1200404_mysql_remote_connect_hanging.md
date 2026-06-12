---
title: "mysql remote connect hanging"
date: 2009-06-30
forum: Server Platforms
---

### Post by belfasttim on 2009-06-30
Hi-- 

I am running a couple Ubuntu 8.1 server VPS instances on slicehost-- one is a DB server running mySQL and one is an apache 2 webserver.

For several months I've had no issues-- the DB server is bound to the webserver, so it only accepted connections from the web server, both in my.cnf and iptables.

Recently I've gotten more traffic, and I'm getting mysql connection errors in my PHP pages pretty frequently. I recently reduced the number of apache maxclients, startservers, etc. to try to deal with the server swapping to much (though I don't think that's the issue here). 

I can SSH into the web server and when I try to connect with the CLI into mySQL on the DB server, it hangs for 15-30 seconds then gives me 
"ERROR 2003 (HY000): Can't connect to MySQL server" (which would usually suggest a bad my.cnf or a dead mySQL server I think)

A few minutes later, I can connect with no problem. And the whole time, I can verify the DB server is up and accepting connections via another SSH session into that machine.

Does anyone have any ideas on this? Can this type of problem be caused by an overloaded server or insufficient memory on the web server machine? Any advice appreciated, let me know if you need more info.

---

### Post by jhannah on 2009-06-30
It sounds like you are hitting the mySQL max_connections limit. By default, this is 100 connections which can be eaten up pretty quickly if you are not fastidious about closing the connections as soon as you no longer need them in your application. To double check, look at the results of the below command as run against the mySQL server (it takes the standard '-h', '-u' and '-p' flags):

```
mysqladmin processlist
```

If you run this when you are having an issue, I expect you will see a number of stuck queries or connections that just haven't been closed. You can up the max_connections settings in your my.cnf but if you indeed are hitting this limit it's usually indicitive of the fact that your code needs to be revised, your queries need to be revised or you need a larger mySQL installation.

---

### Post by belfasttim on 2009-06-30
thank you Jon-- I've started looking into mySQL as the culprit-- and it appears I had my connections and buffers set way too high for the machine. . .I'll check the code and make sure it's closing connections.

Thanks for the advice!

---

### Post by belfasttim on 2009-07-01
More info for you Jon-- 

tonight I experienced the timeout issue again, and jumped on it-- the mysql server was just fine. I was able to ssh into the db server, connect to mysql via cli from the db server, but could not connect to the db server from the webserver via cli. (from the webserver to the DB server the error message was "ERROR 2003 (HY000): Can't connect to MySQL server on 'XX.XX.XX.XX' (110)")

I could ping the db server just fine from the webserver, so apparently the network was up and normal. 

On the webserver, running top I'd see nothing unusual except an apache process that would pop up, go to about 15% of memory, and then die. A few seconds later it would happen again. So I reloaded apache and the problem seemed to resolve.

Any thoughts on this?

Thanks!

---

