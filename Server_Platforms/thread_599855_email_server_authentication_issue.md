---
title: "email server authentication issue"
date: 2007-11-01
forum: Server Platforms
---

### Post by d.j.schroeder on 2007-11-01
I have set up an email server with Courier, Postfix, MySQL, and Squirrelmail according to the Howto by flurdy.  I cannot seem to get it to authenticate users.  The only message I'm getting in syslog is "failed to authenticate" no other information is there.  Also the user gets a message from Squirrelmail "Error Unknown user or incorrect passwork.  I have checked over and over my passwords, database names, the MySQL entry for the users etc. and they look right to me.  

I know that in order to help me I probably need to post some configuration files here but I'm not sure which ones would even be helpful.  Any ideas or suggestions would be appreciated.

---

### Post by d.j.schroeder on 2007-11-01
Ok, I have looked at the mysql.log file and the request to the database is correct and when I make the same query in a terminal window it returns the correct information.  So where do I look next, it looks like mysql is set up correctly?

---

### Post by d.j.schroeder on 2007-11-01
I turned up some debugging options for imapd I can now see in syslog that authdaemon is rejecting the login attempt.  authdeamonrc is supposed to be using autmysqlrc which is what is generating the appropriate query so I still don't see what the problem is any more precisely than that I know that imaplogin is being rejected by authdaemon.

Anyone, ideas where to go next?

---

### Post by tkharris on 2007-11-02
Never mind, I'm wrong.  Not enough coffee yet.

---

### Post by bobster_b on 2007-11-06
Did you get it figured out?

I'm stuck at SMTP authentication..

Thanks, Heath

---

### Post by d.j.schroeder on 2007-11-10
No, still have the problem.  autdaemon still is rejecting everyone even though the query to mysql is correct.

---

### Post by HermanAB on 2007-11-10
In less time than re-reading the postfix howto, you can have a working system: [http://www.citadel.org](http://www.citadel.org)

Easy Install takes about 20 minutes.  Worth a try.

Cheers,

Herman

---

### Post by d.j.schroeder on 2007-11-12
Yeah, Citadel was definitely the way to go.  I bet I had 40 hours in trying to make postfix-courier-mysql-blah-blah work.  Citadel did in fact install correctly in less than 20 minutes.  It took me an additional few minutes to configure Apache so that I can still use Apache on port 80 but have Webcit for citadel accessible through a proxy.

Done and done.  Thanks for the tip.

---

### Post by frodemt on 2007-11-12
> **HermanAB said:**
> In less time than re-reading the postfix howto, you can have a working system: [http://www.citadel.org](http://www.citadel.org)

Easy Install takes about 20 minutes.  Worth a try.

Cheers,

Herman

Hi, do I have to dedicate the server to citadel or can I run multiple servers like ssh, bind, apache and mysql like I do today?

---

### Post by HermanAB on 2007-11-12
Well, Citadel has its own built-in everything for email and webmail, with absolutely every email protocol ever invented, so it uses a zoo of ports - see the web site for details.  However, I am running Apache to serve plain web pages on http port 80, together with Citadel serving secure webmail on https port 443.  So the issue merely one of intelligent port and IP address management.

Citadel is extremely efficient, because it uses BerkeleyDB as the backend, so my Dell PE750 1U garden variety servers run at about 0.2% processor load serving a few hundred users.

So yes, BIND, MySQL and Apache are compatible with Citadel.  However think about what will happen when the machine fails and you lose everything in one swell foop!

Cheers,

Herman

---

