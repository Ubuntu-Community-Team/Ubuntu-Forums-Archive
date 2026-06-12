---
title: "The website of my bank is hacked..."
date: 2009-09-07
forum: The Cafe
---

### Post by mr.propre on 2009-09-07
That's the bad news. The good news is that they use Ubuntu for there servers. :lolflag:

<snip>

---

### Post by Johnsie on 2009-09-07
It's not good news if it got pwned. I use Ubuntu server on my servers :-/

---

### Post by stinger30au on 2009-09-07
i just love how they show everyones data in clear view for the world to see

---

### Post by mr.propre on 2009-09-07
> **Johnsie said:**
> It's not good news if it got pwned. I use Ubuntu server on my servers :-/

The hack was done by an SQL injection so the problem is not OS related. ;-)

---

### Post by Johnsie on 2009-09-07
I guess no operating system or web server is truly safe on the web. There will always be evil geniuses out there with too much time on their hands. I've spent a lot of time looking at how to secure my servers... but it seems impossible to cover all bases.

---

### Post by mr.propre on 2009-09-07
SQL injections are easy to block, but some developers are just idiots.

---

### Post by t0p on 2009-09-07
> **Johnsie said:**
> There will always be evil geniuses out there with too much time on their hands..

"Evil geniuses"?  LOL!

---

### Post by Viva on 2009-09-07
> **t0p said:**
> "Evil geniuses"?  LOL!

Exactly, script kiddies would be a more appropriate word:lolflag:

---

### Post by Grishka on 2009-09-07
SQL injection? amateurs.

---

### Post by orlox on 2009-09-07
> **mr.propre said:**
> SQL injections are easy to block, but some developers are just idiots.

Yup, sql injection s the simplest possible hack that can be done to a website, and is purely a very serious defect on the development of the webpage...the same thing would happen to this webpage if it were deployed on a windows or solaris server...

---

### Post by 3rdalbum on 2009-09-07
I'd often like to change my name to "; DROP DATABASE" and see what kind of havoc ensues...

> SQL injections are easy to block, but some developers are just idiots.

Exactly. I shudder when I hear about websites that actually store user passwords in cleartext, and it's even worse when they send you e-mail and at the bottom is something like: "Remember, your password is 5fa90h".

---

### Post by &#32 Greg on 2009-09-07
> **3rdalbum said:**
> I'd often like to change my name to "; DROP DATABASE" and see what kind of havoc ensues...



Exactly. I shudder when I hear about websites that actually store user passwords in cleartext, and it's even worse when they send you e-mail and at the bottom is something like: "Remember, your password is 5fa90h".

[http://xkcd.com/327/](http://xkcd.com/327/)

:D

Second best XKCD ever, after Real Programmers.

---

### Post by Sporkman on 2009-09-07
> **  Greg said:**
> [http://xkcd.com/327/](http://xkcd.com/327/)

:D

Second best XKCD ever, after Real Programmers.

The dangers of using GOTO was also pretty good. :)

---

### Post by koshatnik on 2009-09-07
> **Johnsie said:**
> I guess no operating system or web server is truly safe on the web. There will always be evil geniuses out there with too much time on their hands. I've spent a lot of time looking at how to secure my servers... but it seems impossible to cover all bases.

Locks only keep out the honest, as the saying goes. Nothing is secure, only varying levels of inconvenience. If someone wants in, they'll get in.

---

### Post by pwnst*r on 2009-09-07
nothing's truly secure unless it's unplugged, packaged, and sitting in the corner of a fogotten warehouse.

---

### Post by Sporkman on 2009-09-07
> **pwnst*r said:**
> nothing's truly secure unless it's unplugged, packaged, and sitting in the corner of a fogotten warehouse.

No - a competent intelligence agency can track down that warehouse, find that machine, start it up & install a rootkit, then return it apparently untouched to its original location. :)

---

### Post by koenn on 2009-09-07
> **koshatnik said:**
> Locks only keep out the honest, as the saying goes. Nothing is secure, only varying levels of inconvenience. If someone wants in, they'll get in.
There are also varying levels of (in)security. Having a website cracked by an attack vector that is wellknown and can simply be prevented by good coding practice is of quite a different level than, say, having your server compromized through an obscure bug noone new existed until someone found it and exploited it.

---

### Post by koenn on 2009-09-07
> **mr.propre said:**
> The hack was done by an SQL injection so the problem is not OS related. ;-)

well, ... what if it is OS related ? 

If you're old enough to remember Windows NT ... it was Microsoft's firs attempt at a server operating system. With their paradigm of graphical user interfaces, ease of use, etc. etc. they made a server "for human beings" :  everyone who was even the tiniest bit familiar with computers  was a potential sysadmin (if you can open explorer and find a file in Win 95, you're qualified).

Next you saw NT4 servers appear everywhere, and everyone wanted to be on the web, and you could set up a web server in 5 clicks (next, next, next, next, finish) - so a lot of people did just that. And NT4 became the most cracked server in history - because the people that ran it had no idea what they were doing, yet the operating system was designed so that the could run it regardless. 


Now, what if Ubuntu is the NT4 of this decade ? OK, it's probably better (it's Linux, after all) but it attracts the same sort of people, and it it's simple enough so that people who have (next to) no idea of what they're doing, run all sorts of servers on the internet ...

---

### Post by Viva on 2009-09-07
> **koenn said:**
> well, ... what if it is OS related ? 

If you're old enough to remember Windows NT ... it was Microsoft's firs attempt at a server operating system. With their paradigm of graphical user interfaces, ease of use, etc. etc. they made a server "for human beings" :  everyone who was even the tiniest bit familiar with computers  was a potential sysadmin (if you can open explorer and find a file in Win 95, you're qualified).

Next you saw NT4 servers appear everywhere, and everyone wanted to be on the web, and you could set up a web server in 5 clicks (next, next, next, next, finish) - so a lot of people did just that. And NT4 became the most cracked server in history - because the people that ran it had no idea what they were doing, yet the operating system was designed so that the could run it regardless. 


Now, what if Ubuntu is the NT4 of this decade ? OK, it's probably better (it's Linux, after all) but it attracts the same sort of people, and it it's simple enough so that people who have (next to) no idea of what they're doing, run all sorts of servers on the internet ...

Do wikimedia servers not run ubuntu? I don't think there will be too many ubuntu servers run by non-professionals because the ubuntu server edition is not advertised as an easy to use home server setup unlike the desktop edition. Most of the servers are still run in datacenters and managed by professionals.

---

### Post by koenn on 2009-09-07
> **Viva said:**
> Do wikimedia servers not run ubuntu? 
don't know.

> **Viva said:**
> I don't think there will be too many ubuntu servers run by non-professionals because the ubuntu server edition is not advertised as an easy to use home server setup unlike the desktop edition. Most of the servers are still run in datacenters and managed by professionals.
true, possibly. 
yet, re the OP - Dexia is one of the major banks in Belgium. Whether they were running their web server(s) themselves,  or have them in colo in a datacenter , or simply have a hosted web site, you'd think that server be run by professionals, right ? And then to fall for the oldest trick in the book ...

If you spend some time in 'Servers' or 'Security', and even in the Café, you'll see that "help my server is hacked (sic)" is not unusual. It's also not unusual to see people run web servers, remote desktops -, ssh servers, ... open to the internet, on desktop editions. These people are truely the next generation "NT4" sysadmins. 

Next, some of these wannabe sysadmins are going to think they can make some pocket money (or build even just build up some experience for their future career in IT) by helping small busines and non profits in their environment and set up servers or them, ... 
and there you go. 
deja vu all over again

---

### Post by Viva on 2009-09-07
I don't think the server is run by the same guys who coded the website. The problem lies with the latter. If they bought an unmanaged server(very unlikely), the server management is  most likely bought from an outside source. If they bought a managed server, the datacenter/host will take care of the server management who'll make sure that the server security is solid and who don't have anything to do with how the site is built. They probably outsourced the website coding and design to a cheap-*** programming company who did not bother to make sure their code is clean. More often than not, attacks like sql injection or remote file inclusion happen because of poor coding practices rather than the server security itself.

---

### Post by Mateo on 2009-09-07
Doesn't this have to be an inside job?  You can't do sql injection without knowing the database schema.  DROP DATABASE dbname only works if you know the value of dbname.

I guess it would be possible to prep for the attack by doing sql injection into the master database and getting the schema that way, although how to do that varies depending on which db server you're using.

---

### Post by Viva on 2009-09-07
> **Mateo said:**
> Doesn't this have to be an inside job?  You can't do sql injection without knowing the database schema.  DROP DATABASE dbname only works if you know the value of dbname.

I guess it would be possible to prep for the attack by doing sql injection into the master database and getting the schema that way, although how to do that varies depending on which db server you're using.

Not really, it is not very difficult to get the database schema. And you don't always have to drop a database to do the damage.

---

### Post by koenn on 2009-09-07
> **Mateo said:**
> Doesn't this have to be an inside job?  You can't do sql injection without knowing the database schema.  DROP DATABASE dbname only works if you know the value of dbname.


not necessarilly. you start with 'blind' injection, and from the results you get, you deduce where to go next.

or you try to trigger errors in the application, which usually show what server + version your running - If you see complaints from Apache+PHP, MySQL or Postgresql databases are a reasonable guess, and you know their system tables ... 

DROP DATABASE is funny in web comics, in this case they were after user names and passwords

---

### Post by Viva on 2009-09-07
I did not look at the original page, but getting the details could be as easy as a 1=1 injection.

---

### Post by Mateo on 2009-09-07
> **koenn said:**
> not necessarilly. you start with 'blind' injection, and from the results you get, you deduce where to go next.

or you try to trigger errors in the application, which usually show what server + version your running - If you see complaints from Apache+PHP, MySQL or Postgresql databases are a reasonable guess, and you know their system tables ... 

DROP DATABASE is funny in web comics, in this case they were after user names and passwords

That's still not exactly easy.  What is your method for delivering the SELECT back from the master database?  Javascript?  This would take some time to code a proper attack.  You'd have to write several scripts since mysql, mssql, oracle, don't all have a common method for storing the schema. And if this bank were big at all, it probably would be running a customized database.

I'm not defending the developers here, obviously you have to escape strings before you hit the database with them.

---

### Post by ctrlmd on 2009-09-07
thats not good news at all 

even when you use ubuntu linux as a server you might get hacked so where is the good news here :confused:

---

### Post by koenn on 2009-09-07
> **Viva said:**
> They probably outsourced the website coding and design to a cheap-*** programming company who did not bother to make sure their code is clean. More often than not, attacks like sql injection or remote file inclusion happen because of poor coding practices rather than the server security itself.
I agree the entry point is a result of bad coding. But if you see how they follow up (load files from the filesystem, possibly execute commands ...) thats sysadmin territory. Next, they apparently were able to get usernames and password hashes from the database,  and the db admin allowed remote access from any host (while access from the application account on the web server should be sufficient). That's also sysadmin stuff.


So there's an *ubuntu* sysadmin there - whether he works for the bank, the hosting provider or whatever, is irrelevant - who's "skilled" enough to run an ubuntu server installer, select "web server' in the installer dialog, and thinks that's good enough to put a web app open on the internet.

That last part is speculation, but you see my point.

---

### Post by koenn on 2009-09-07
> **Mateo said:**
> That's still not exactly easy.  What is your method for delivering the SELECT back from the master database?  Javascript?  This would take some time to code a proper attack.  You'd have to write several scripts since mysql, mssql, oracle, don't all have a common method for storing the schema. And if this bank were big at all, it probably would be running a customized database.
Like I said in a previous post, it's not that hard to get info on servers and versions (that includes database systems), from too verbose error mesages and the likes.

you don't have to "deliver" an SQL statement tyo the database, the application does that for you. What you try to do is insert or append additional SQL to that statement, through the input fields the application provides (or sometimes by appending them to the url you send).
Here are some good explanations : [http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

Not that I've ever done this before, but wouldn't injecting 
```
SELECT * from users;
``` give you all user accounts in a mysql database  ? Is there not an even simpler command to show you all the tables ? or all databases ?  how much more do you need ?



The really significant part isn't whether this is easy or hard, but that *good coding practise* can make injection extremely difficult, next to impossible.

---

### Post by CJ Master on 2009-09-07
> **koenn said:**
> well, ... what if it is OS related ? 

If you're old enough to remember Windows NT ... it was Microsoft's firs attempt at a server operating system. With their paradigm of graphical user interfaces, ease of use, etc. etc. they made a server "for human beings" :  everyone who was even the tiniest bit familiar with computers  was a potential sysadmin (if you can open explorer and find a file in Win 95, you're qualified).

Next you saw NT4 servers appear everywhere, and everyone wanted to be on the web, and you could set up a web server in 5 clicks (next, next, next, next, finish) - so a lot of people did just that. And NT4 became the most cracked server in history - because the people that ran it had no idea what they were doing, yet the operating system was designed so that the could run it regardless. 


Now, what if Ubuntu is the NT4 of this decade ? OK, it's probably better (it's Linux, after all) but it attracts the same sort of people, and it it's simple enough so that people who have (next to) no idea of what they're doing, run all sorts of servers on the internet ...

Hello, are we talking about a professional bank company or an indie site, here? Also, SQL interjection has nothing to do with the server itself, it has to do with the web page.

Ubuntu definitely isn't an "easy" server, there's no GUI.

---

### Post by Mateo on 2009-09-07
> **koenn said:**
> Like I said in a previous post, it's not that hard to get info on servers and versions (that includes database systems), from too verbose error mesages and the likes.

you don't have to "deliver" an SQL statement tyo the database, the application does that for you. What you try to do is insert or append additional SQL to that statement, through the input fields the application provides (or sometimes by appending them to the url you send).
Here are some good explanations : [http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

Not that I've ever done this before, but wouldn't injecting 
```
SELECT * from users;
``` give you all user accounts in a mysql database  ? Is there not an even simpler command to show you all the tables ? or all databases ?  how much more do you need ?



The really significant part isn't whether this is easy or hard, but that *good coding practise* can make injection extremely difficult, next to impossible.

Only if the name of the user table is users.  That's guess.  You first have to know where the schema is stored in the database and write a script that gets the schema.  The script has to include a delivery method back to the hacker.  SELECT * FROM table does not print the results to the Hacker's monitor.

---

### Post by koenn on 2009-09-07
> **CJ Master said:**
> Hello, are we talking about a professional bank company or an indie site, here? Also, SQL interjection has nothing to do with the server itself, it has to do with the web page.

Ubuntu definitely isn't an "easy" server, there's no GUI.
I think you mist a few posts ...

And Ubuntu server is fairly easy. to install a web server (actually a complete LAMP stack), just select webserver during the install. Very difficult indeed. 
And people migrate from ubuntu desktop to ubuntu server - so they have that 'next next finished' attitude  and apply it to servers as well. Which is not always a good idea.

---

### Post by koenn on 2009-09-07
> **Mateo said:**
> Only if the name of the user table is users. That's guess.    
It's an educated guess. It doesn't hurt to try. Ubuntu defaults to Postgresql, while mysql is the most used database for web servers. you can look up the names of the system tables in the documentation. If you've ever used mysql, you know that 'mysql' and 'users' are the tables you might be interested in. (Don't tell anybody, it's a big secret)



> **Mateo said:**
> 
You first have to know where the schema is stored in the database and write a script that gets the schema.  The script has to include a delivery method back to the hacker.  SELECT * FROM table does not print the results to the Hacker's monitor.
You don't need a delivery method. You already have a web application that is designed to write the results of your queries on the web page your looking at. 

And you don't need a script to retrieve the schema. You need an sql statement that pulls data out of a table.

---

### Post by Mateo on 2009-09-07
A login form isn't designed to return the results of a query as HTML.  It is designed to check if the username/password combo are correct, and if so to forward you to another page.  So to retrieve SQL from a webform, you absolutely have to write a delivery methods.  You have to trick the form to submit asynchronously (to bypass the site's own server code) and then handle the returned results with javascript or actionscript or something to that effect.

---

### Post by CJ Master on 2009-09-07
> **koenn said:**
> I think you mist a few posts ...

And Ubuntu server is fairly easy. to install a web server (actually a complete LAMP stack), just select webserver during the install. Very difficult indeed.

Then what? Click on next next next finish? There's still much configuration to be done.

> And people migrate from ubuntu desktop to ubuntu server - so they have that 'next next finished' attitude  and apply it to servers as well. Which is not always a good idea.

They can have that attitude if they want, they're not going to find any GUI on Ubuntu server (sans installing a gui themselves.)

---

### Post by mr.propre on 2009-09-08
:KS @ thread
Well the part of the website that was "hacked" didn't contain any important user data. They probably hacked the website inserting a query in the URL. Allot developers overlook that part.

BTW, my last name is D'haese. I lost the count how many times I saw an SQL error because of that.

---

### Post by koenn on 2009-09-08
> **CJ Master said:**
> Then what? Click on next next next finish? There's still much configuration to be done.

They can have that attitude if they want, they're not going to find any GUI on Ubuntu server (sans installing a gui themselves.)

[http://www.google.be/search?q=site%3Aubuntuforums.org+server++hacked+OR+cracked+OR+compromised&btnG=Search&meta=](http://www.google.be/search?q=site%3Aubuntuforums.org+server++hacked+OR+cracked+OR+compromised&btnG=Search&meta=)

---

### Post by koenn on 2009-09-08
> **Mateo said:**
> A login form isn't designed to return the results of a query as HTML.  It is designed to check if the username/password combo are correct, and if so to forward you to another page.  So to retrieve SQL from a webform, you absolutely have to write a delivery methods.  You have to trick the form to submit asynchronously (to bypass the site's own server code) and then handle the returned results with javascript or actionscript or something to that effect.
that's what the programmer of this Dexia website probably thought as well : that his application would behave as expected, and that all users would only do what the instructions on the sceen tell them to do. 

surprise : it only takes 1 user to try something different, and you're toast.
In this case, someone appended 'UNION ALL SELECT ... to the URL and in the screenshots the OP linked to, (link now removed) you can see the data being displayed in the browser. Easy. And so what if this does take some additional javascript. That's hardly a hurdle, is it ? 
Would you actually let your access control to a database with sensitive data (account names and cleartext passwords of your employees) depend on the assumption that there is noone out there that knows javascript ? 

Not to mention the fact that having that sort of data in the same dbms as the database that drives your public website is probably a not so clever decision.

I don't know why I should waste any more words on this while the facts speak for themselves ....

---

