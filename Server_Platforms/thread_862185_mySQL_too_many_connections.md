---
title: "mySQL too many connections"
date: 2008-07-17
forum: Server Platforms
---

### Post by Jahoobie on 2008-07-17
We are on Ubuntu 6.06.1 LTS, and have recently started getting errors on our website stating too many concurrent connections, cannot connect to mySQL.

I have read a few threads regarding this, but none seem to apply to what is going on.  Where would I find the max connection variable to increase that, or where do I find the connection timeout?

I looked in /etc/mysql/my.cnf, but don't see anything in there that would control this.  This is causing our webserver to go down almost everyday now, and I need help!

Thanks

---

### Post by hyper_ch on 2008-07-17
did you try whether google has some answers?

---

### Post by Jahoobie on 2008-07-17
Yes, we have looked at google, with no avail.  It appears when the system crashes and we get the too many connections, or can't connect to mysql errors we have a bunch (20+) unauthenticated users connections.  They are all from the main webserver to the DB server. Port 3306 is closed to the outside world, so I don't think this is a hacking attempt.  

I really need insight on how to get this fixed.  Anyone who can help, please let me know!

---

### Post by mhmjr on 2008-07-17
Your my.cnf may not have certain variables listed. If they do not, they are simply using the default values it was compiled for. Adding the variables you wish to change and the values you wish the server to use, then restarting mysql should help. It sounds like you may gain some benefit from lowering the wait_timeout and tweak max_connections.

The syntax is simple just:
variable=value 

example:
wait_timeout=900

If you want to know what the values of these are in your running version of mysql and they are not specified in the my.cnf file, you can login to mysql as a mysql user with administrative privileges and run the command:
mysql>show variables;


Hope that helps!

-mhmjr

---

### Post by soulresin on 2008-07-17
> **Jahoobie said:**
> We are on Ubuntu 6.06.1 LTS, and have recently started getting errors on our website stating too many concurrent connections, cannot connect to mySQL.

I have read a few threads regarding this, but none seem to apply to what is going on.  Where would I find the max connection variable to increase that, or where do I find the connection timeout?

I looked in /etc/mysql/my.cnf, but don't see anything in there that would control this.  This is causing our webserver to go down almost everyday now, and I need help!

Thanks

Hi.

The variable for max connections in my.cnf is

max_connections

I believe it defaults to 100.

Before raising that, you may want to consider why so many connections
are hanging around in MySQL to make it hit the maximum.  If you're using persistent connections in your code, and they're not cleanly closing you may want to stop using persistent connections.  Or you can set

wait_timeout

in my.cnf to a sensible value of 300 or 600 seconds.

You may also want to enable slow query logging to see if there are any slow queries stacking up, causing max_connections to be hit.

You mention a number of "unauthenticated connections" which also makes me wonder if it's a reverse DNS issue.  You could try adding

skip_name_resolve

to my.cnf to see if that helps.

Also, you could grab the perl script from [http://mysqltuner.com](http://mysqltuner.com) and run it to see if it will suggest configuration changes.  It will provide the best data if MySQL has been running for 48+ hours, but it couldn't hurt.  No, I'm not the author of the script, but I work with him.  :)

---

### Post by Jahoobie on 2008-07-18
Thanks for the info!

I'm going to start with changing existing variables, and then move on to the reverse DNS if that doesn't fix it.

In the my.cnf file, is there anywhere these variables NEED to be placed?  As in, if I put them under the [mysqld] area, would it break if they are supposed to go somewhere else?

Sorry if I sounds like a newb...well, no, I'm not sorry, I am a newb.:)

---

